---
title: "Weather Forecast For Ubuntu"
date: 2011-05-31
forum: The Cafe
---

### Post by huios on 2011-05-31
Hi, I have searched for a solution for weather forcasts via the weather applet in Ubuntu 10.10 without success.
I live in the Sydney NSW Australia region and the applet keeps telling me that
 "[COLOR=Purple]Forecast not currently available for this location.[/COLOR]" 
If I set my location to several other areas in Australia it works fine. I note that it is sourcing info from the BOM.gov.au site, but does not seem to talk to the /NSW page.  My assumption is that either there is a bug that does not translate the correct info to the right area when I use preferences, or if the applet uses a look up table, that is broken?
I would appreciate any help in resolving this problem but admit to having very limited skills with command line stuff not knowing even how to navigate to various directories and files. :(
Any help much appreciated.
thanks in advance,
huios

---

### Post by screaminj3sus on 2011-05-31
For anyone using in ubuntu 11.04 you can remove indicator-complete from the panel and add the regular gnome 2 clock to the panel instead which has integrated weather.

There's plenty of indicators available as well, such as my-weather-indicator and indicator-weather. I prefer the gnome 2 one though.

---

### Post by Rodney9 on 2011-06-01
I'm using 10.4.2 and the Gnome weather applet for Brisbane, Australia only shows conditions, no forecast.

When you click on Forecast you get "Forecast not currently available for this location." every time.

I wish there was [BOM]("http://www.bom.gov.au/index.shtml") applet for Gnome

---

### Post by huios on 2011-06-01
> **Rodney9 said:**
> I'm using 10.4.2 and the Gnome weather applet for Brisbane, Australia only shows conditions, no forecast.
 
When you click on Forecast you get "Forecast not currently available for this location." every time.
 
I wish there was [BOM]("http://www.bom.gov.au/index.shtml") applet for Gnome
 Thanks for the reply Rodney. You have exactly the same problem I have exept that you are in QLD.  If for example you tell the applet you are in Perth, you should then get a forcast from [www.bom.gov.au/WA]("http://www.bom.gov.au/WA") couse that's no help to we persons on the East coast.

---

### Post by Rodney9 on 2011-06-01
I think it may be a bug, as I searched the locations.xml with Bless hex editor and found it is using the correct metar and co-ordinates for Brisbane ?

---

### Post by dcstar on 2011-12-06
> **huios said:**
> Hi, I have searched for a solution for weather forcasts via the weather applet in Ubuntu 10.10 without success.
I live in the Sydney NSW Australia region and the applet keeps telling me that
 "[COLOR=Purple]Forecast not currently available for this location.[/COLOR]" 
.........

This has just been fixed in the **libgweather** package which will now be rolled out to various Ubuntu distros (I hope).

It is currently in the 11.10 Proposed Repository.

[https://bugs.launchpad.net/ubuntu/+source/libgweather/+bug/629646](https://bugs.launchpad.net/ubuntu/+source/libgweather/+bug/629646)

---

