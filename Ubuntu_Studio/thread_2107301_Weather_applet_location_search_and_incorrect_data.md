---
title: "Weather applet location search and incorrect data"
date: 2013-01-21
forum: Ubuntu Studio
---

### Post by Inoki on 2013-01-21
Hi all,

does anybody have the same problem, that when they want to search for a location in the weather applet of XFCE 4.10 in Ubuntu Studio they get no results for their search?

When attempting to use a proxy and determine the location automatically it still shows incorrect results.

---

### Post by ttoine on 2013-01-21
Hi,

There is the same problem in Ubuntu 12.04 and Unity with the Weather Indicator. Maybe it is just a temporary bug, or maybe it is since the 12.10 release.

---

### Post by Inoki on 2013-01-30
Is there any solution to this? I've tried also numerous dock applications, but all of them provide inaccurate weather data.

I've tried the normal Ubuntu weather-indicator, wrong data.
Docky, wrong data.
XFCE weather applet, wrong data.
my-weather-indicator doesn't work under XFCE.

---

### Post by ttoine on 2013-01-31
I think that it is just broken. Maybe you can fill a bug on launchpad against this package ?

---

### Post by Cheesehead on 2013-01-31
The search dialog is already a known bug: See [http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin) for the fix plan.

Incorrect location is a different problem entirely.
What incorrect location does it show?
What correct location should it show?

If I recall correctly, xfce4-weather-plugin uses your IP address to estimate location. If your ISP has the wrong location associated with that IP address (and many ISPs do), then that's a complaint against your ISP.

You can easily check (or refute) the ISP-reports-wrong-location theory by using any common IP address locator service (example: [http://www.ipaddresslocation.org/](http://www.ipaddresslocation.org/) ).

---

### Post by Inoki on 2013-02-01
> **Cheesehead said:**
> The search dialog is already a known bug: See [http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin) for the fix plan.

Incorrect location is a different problem entirely.
What incorrect location does it show?
What correct location should it show?

If I recall correctly, xfce4-weather-plugin uses your IP address to estimate location. If your ISP has the wrong location associated with that IP address (and many ISPs do), then that's a complaint against your ISP.

You can easily check (or refute) the ISP-reports-wrong-location theory by using any common IP address locator service (example: [http://www.ipaddresslocation.org/](http://www.ipaddresslocation.org/) ).

Thanks for the answer. When I set it to autodetect using proxy it shows "none, Slovakia" and totally different degrees in Celsius than it supposed to, so supposedly a problem with the ISP. It should be showing "Bratislava, Slovakia" and correct degrees.

The trouble is this happens also with Docky and other applications. Weather seems overall broken.

---

### Post by Inoki on 2013-02-18
I just talked to a person over at Google+, who is using Xubuntu 12.10, I'm using Ubuntu Studio 12.10, his weather applet is working, mine is not.

Could this be a result of different kernels / tweaks in the system?

Ubuntu Studio uses lowlatency kernels, whereas the default one a slightly different one, not sure if this has any impact, if there are major differences, or if this has any impact whatsoever, but a reasonable clarification would be most welcomed.

---

### Post by jejeman on 2013-02-18
This is not defenetly kernel issue.
For me it works on ubuntu studio 12.10.
I'm not at that PC anymore, so I can't look for details.
However on Ubuntu 12.04 weather indicator was off, so I just changed the servise provider.

---

### Post by Inoki on 2013-02-18
> **jejeman said:**
> This is not defenetly kernel issue.
For me it works on ubuntu studio 12.10.
I'm not at that PC anymore, so I can't look for details.
However on Ubuntu 12.04 weather indicator was off, so I just changed the servise provider.

Well if anybody could guide me through the process of how the provider can be changed in XFCE 4.10 I'd be very grateful.

---

