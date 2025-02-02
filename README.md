# Calendar Date Range Picker [![](https://jitpack.io/v/JoshHalvorson/calendar-date-range-picker.svg)](https://jitpack.io/#JoshHalvorson/calendar-date-range-picker)

I made this calendar picker for work and thought it'd make an excellent standalone view, this is also my first published library so if you feel like it, please leave any feedback/issues, or submit a PR if you add something cool! There's definitely some things I want to add in the future and plan on updating this a bit. Thanks for checking it out!

UI by [Sabrina Hong](https://www.linkedin.com/in/uiuxsabrina)

Be sure to check the [wiki](https://github.com/JoshHalvorson/calendar-date-range-picker/wiki) before contributing and let me know if you have any questions!

## Usage

### Installation

Add the jitpack repository to your root build.gradle

```Gradle
allprojects {
  repositories {
    ...
    maven { url 'https://jitpack.io' }
  }
}
```

Then add the dependency to your app build.gradle

```Gradle
dependencies {
  implementation 'com.github.JoshHalvorson:calendar-date-range-picker:0.1.1'
}
```

### Code

Currently you can add the view through xml like so
```Xml
<dev.joshhalvorson.calendar_date_range_picker.calendar.CalendarPicker
  android:id="@+id/calendarPicker"
  android:layout_width="wrap_content"
  android:layout_height="wrap_content"
/>
```
and everything should be good to go.

Then in your view code you can get the selected dates by calling ```getSelectedDates()```

```Kotlin
binding.getDateRangeButton.setOnClickListener {
  val selectedDates = binding.calendarPicker.getSelectedDates()

  if (selectedDates != null) {
    val firstDate = DateFormat.getDateInstance().format(Date(selectedDates.first))
    val secondDate = DateFormat.getDateInstance().format(Date(selectedDates.second))
    ...
  }
}
```

This will return a ```Pair<Long, Long>``` with the two dates in millis for you to convert however you like.

You can also adjust the attributes through code, just make sure you call `calendar.initCalendar()` to apply your changes to the view!

```Kotlin
binding.calendarPicker.eventDotColor = Color.CYAN
binding.calendarPicker.dayTextColor = Color.RED
...
binding.calendarPicker.initCalendar() // REFRESHES CALENDAR AFTER CHANGING ATTRIBUTES
```

You can use `calendar.addEvents(vararg events: Calendar)` if you need to mark important dates or show an event on specific dates (thanks @Xpjay 👍).

```Kotlin
binding.calendarPicker.addEvents(
  Pair("event  1", Calendar.getInstance()),
  Pair("event  2", Calendar.Builder().setDate(2021, 8, 12).build()),
  Pair("event  3", Calendar.Builder().setDate(2020, 8, 11).build()),
  Pair("event  4", Calendar.Builder().setDate(2021, 2, 1).build()),
  Pair("event  5", Calendar.Builder().setDate(2021, 11, 8).build()),
)
```

The [sample](https://github.com/JoshHalvorson/calendar-date-range-picker/tree/main/sample) directory has some activity code and the xml for creating and using the calendar.

### Attributes

Most of the attributes for the calendar are for changing the colors, almost every element's color can be changed, as well as a couple drawables. I wanted this to be pretty customizable while still having a fairly material feel to it. Here are all the attributes you can change:

```Xml
<dev.joshhalvorson.calendar_date_range_picker.calendar.CalendarPicker
    android:id="@+id/calendarPicker"
    android:layout_width="wrap_content"
    android:layout_height="wrap_content"
    app:dayTextColor="@color/..."
    app:yearTextColor="@color/..."
    app:firstSelectedDateTextColor="@color/..."
    app:secondSelectedDateTextColor="@color/..."
    app:selectedDateCircleColor="@color/..."
    app:highlightedDatesBackgroundColor="@color/..."
    app:highlightedDatesTextColor="@color/..."
    app:titleColor="@color/..."
    app:nextMonthButtonColor="@color/..."
    app:previousMonthButtonColor="@color/..."
    app:yearSelectButtonColor="@color/..."
    app:yearSelectButtonIconColor="@color/..."
    app:yearSelectButtonTextColor="@color/..."
    app:dateRangeTextColor="@color/..."
    app:daysOfWeekTextColor="@color/..."
    app:eventDotColor="@color/..." 
    app:nextMonthButtonIcon="@drawable/..."
    app:previousMonthButtonIcon="@drawable/..." />
```

## Images

Day mode            |  
:-------------------------:|
 <img src="https://i.imgur.com/6ODEBrn.png" width="300">   <img src="https://i.imgur.com/xAjuITC.png" width="300"> | 
 
 Night mode            |  
:-------------------------:|
 <img src="https://i.imgur.com/3OVPrfx.png" width="300"> <img src="https://i.imgur.com/Zw7l8Ee.png" width="300"> | 
