---
title: "Ubuntu server stats on mobile phone (Android / WM)"
date: 2011-07-21
forum: The Cafe
---

### Post by viulian on 2011-07-21
I needed to keep an eye on the MRTG graphs of my server (Ubuntu 9 / 10) but I found nothing that would work the way I wanted. 

Please check below some screenshots:

[IMG]http://hex.ro/wp/wp-content/uploads/2011/07/two_widgets.jpg[/IMG] [IMG]http://hex.ro/wp/wp-content/uploads/2011/07/two_widgets_adw_5rows.jpg[/IMG] [IMG]http://hex.ro/wp/wp-content/uploads/2011/07/settings.jpg[/IMG]

The widget I've created works for Android 1.6+ (I've coded a similar one as a Today Screen plugin for Windows Mobile 6.1).

Having the widgets displaying MRTG graphs involves configuration of the server so that 1. MRTG graphs are generated periodically and 2. the size of the graphs has to be hand "crafted" for them to appear crisp on the mobile phone.

I'll describe the Android widget below (since Android is more popular now than WM6.1, but they both work in similar way):

[LIST]
[*]Refreshes automatically each 15m, 30m, 1h or 2h (configurable), also on each network reconnect (WiFi/3G/GSM/..) or manually, upon request.
[*]Displays the time when the last successful update (what I hate most about other widgets - no date of last update - do I have stale data or not ?).
[*]Comes in two different layouts to fit all type of phone screen resolution.
[/LIST]

The advantage of always downloading upon "network reconnect" is that I tend to check the home screen whenever I leave areas with no signal. Having the widget updating then saves me time of asking it to refresh once I get the signal back. This means that sudden network reconnects might trigger a lot of updates. In future I will add a limit - but for now it is not there.

Links:
[URL="http://hex.ro/wp/projects/image-monitor-for-android/"]
Home page for Android widget[/URL]
[Home page for WM6.1 plugin]("http://hex.ro/wp/projects/mrtg-today-screen-plugin-for-wm-6-1/")

I hope that some sysadmins will find it useful (or at least reassuring that everything looks normal) :)

---

