---
title: "A decent Calendar"
date: 2007-12-04
forum: The Cafe
---

### Post by wakeboarder on 2007-12-04
I can't figure this one out.

How come Google can build a Calendar app that rocks in no time and the entire Linux/OSS community haven't been able to build one single calendar in all these years worth the name?

Yeah yeah I know about Evolution, Lightning etc but I just hate them...poor functionality, lots of bugs, etc etc

---

### Post by Whiffle on 2007-12-04
Have you tried Kontact?  I've got it setup to sync my calender between 2 computers via ssh, it syncs with my treo, and does a nice job with email too.

---

### Post by mali2297 on 2007-12-04
Have you tried **cal**?

Feature list:
> 
    -1      Display single month output.  (This is the default.)

     -3      Display prev/current/next month output.

     -s      Display Sunday as the first day of the week.  (This is the
             default.)

     -m      Display Monday as the first day of the week.

     -j      Display Julian dates (days one-based, numbered from Jan-
             uary 1).

     -y      Display a calendar for the current year.


Screenshot:
```

   december 2007
må ti on to fr lö sö
                1  2
 3  **4**  5  6  7  8  9
10 11 12 13 14 15 16
17 18 19 20 21 22 23
24 25 26 27 28 29 30
31

```

It is ultra-stable, it hasn't failed me once.

---

### Post by bruce89 on 2007-12-04
5 minutes:
[PHP]#include <gtk/gtk.h>

int
main (int *argc, char **argv)
{
	GtkWidget *window;
	GtkWidget *calendar;
	
	gtk_init (&argc, &argv);
	
	window = gtk_window_new (GTK_WINDOW_TOPLEVEL);
	gtk_container_set_border_width (GTK_CONTAINER (window), 6);
	
	calendar = gtk_calendar_new ();
	gtk_container_add (GTK_CONTAINER (window), calendar);
	gtk_widget_show  (calendar);
	
	gtk_widget_show  (window);
	
	gtk_main ();
	return 0;
}[/PHP]

---

### Post by Nano Geek on 2007-12-04
> **wakeboarder said:**
> I can't figure this one out.

How come Google can build a Calendar app that rocks in no time and the entire Linux/OSS community haven't been able to build one single calendar in all these years worth the name?

Yeah yeah I know about Evolution, Lightning etc but I just hate them...poor functionality, lots of bugs, etc etcProbably Google can build a calender like that due to the fact that they pay millions of dollars to I'm guessing hundreds of developers to make their software.

---

### Post by Incense on 2007-12-04
> **Whiffle said:**
> Have you tried Kontact?  I've got it setup to sync my calender between 2 computers via ssh, it syncs with my treo, and does a nice job with email too.

+1

---

### Post by igknighted on 2007-12-04
If you like google's calender so much, why not use it?  Even if you're not always online, you could use google-gears to still use your calender.  Not sure if gears is ready for the calender yet though, but if it isn't it should be soon.

---

### Post by Crashmaxx on 2007-12-04
> **igknighted said:**
> If you like google's calender so much, why not use it?  Even if you're not always online, you could use google-gears to still use your calender.  Not sure if gears is ready for the calender yet though, but if it isn't it should be soon.

+1

That's what I use, its the best way I've found.

---

### Post by notwen on 2007-12-04
Have you looked into [Rainlendar]("http://www.rainlendar.net/")?

---

### Post by smartboyathome on 2007-12-04
I use Sunbird with the google calendar extention and the ics feed. It works like a charm, and i have an anywhere, anytime calendar.

---

### Post by EmilyRose on 2007-12-04
I can't get the google calendar extention to install cause' it says I need vs 0.7 but the one in the repos is 0.5 and doesn't find any updates...

---

### Post by pt123 on 2007-12-16
there is a how to install on this thread:
[http://ubuntuforums.org/showthread.php?t=278206](http://ubuntuforums.org/showthread.php?t=278206)

---

