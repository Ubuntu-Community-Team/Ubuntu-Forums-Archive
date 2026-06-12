---
title: "[How-To] Get lightning working with Thunderbird 3.0"
date: 2009-12-21
forum: Ubuntuzilla
---

### Post by michael37 on 2009-12-21
So, let's say you just downloaded Thunderbird 3 using Ubuntuzilla and you want to get Lightning (the greatest calendar extension) working.  Mozilla Addons site now provides [Lightning 1.0b1 version]("https://addons.mozilla.org/en-US/thunderbird/addon/2313") of Lightning which is considering current stable version. You may also consider [Provider for Google Calendar]("https://addons.mozilla.org/en-US/thunderbird/addon/4631") which integrates your Thunderbird with online Google Calendar.

ALTERNATIVELY, if you want to perform manual installation, follow the following steps.  
[LIST]
[*]Point your browser to [http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/linux-i686/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1/linux-i686/)
If you are in US, consider going into en-US directory.
[*]Right-click the link named **lightning.xpi** and choose "Save Link As..." to download and save the file to your hard disk, let's say to Desktop.
[*]Right-click the link named **gdata-provider.xpi** and choose "Save Link As..." to download and save the file to your hard disk, let's say to Desktop.
[*]In Mozilla Thunderbird, open Add-ons from the Tools menu, and select Extensions icon.
[*]Click the Install button, and locate/select the files you downloaded and click "OK".
[*]Restart Thunderbird.
[*]Set up your Google Calendar login and enjoy read/write support from within **Thunderbird tabs**.
[/LIST]

[SIZE="1"]Source: Inspired by [Lightning/Calendar blog]("http://weblogs.mozillazine.org/calendar/").[/SIZE]

---

### Post by nanotube on 2009-12-21
Thanks for this howto! I'm sticky-ing it for the time being - at least until lightning 1.0 makes release.

---

### Post by michael37 on 2009-12-21
Thunderbird 3 with tabs and with Calendar and Tasks in tabs looks totally awesome.

[IMG]http://farm4.static.flickr.com/3115/3094292059_b099806f0b.jpg[/IMG]

Courtesy of [this wonderful review]("http://ascher.ca/blog/2008/12/09/thunderbird-3-beta-1-a-platform-for-innovation-shapes-up/").

Can't wait for the Lightning 1 release.

---

### Post by qva5 on 2009-12-21
Instruction you gave helped me a lot. Thanks!
 
However I was not able to start Google Provider right away. For some strange reason first I needed to install  xpi file for Google Provider Extension from en-US subdirectory. 

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/linux-i686/en-US/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/linux-i686/en-US/)

---

### Post by michael37 on 2009-12-21
> **qva5 said:**
> Instruction you gave helped me a lot. Thanks!
 
However I was not able to start Google Provider right away. For some strange reason first I needed to install  xpi file for Google Provider Extension from en-US subdirectory. 

[http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/linux-i686/en-US/](http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/linux-i686/en-US/)

Curious.  It works for me.  Are you saying that one gdata-provider.xpi (non-localized, the one that I showed) was not enough and you replaced it with another gdata-provider.xpi (localized for US)?

---

### Post by qva5 on 2009-12-22
> **michael37 said:**
> Curious.  It works for me.  Are you saying that one gdata-provider.xpi (non-localized, the one that I showed) was not enough and you replaced it with another gdata-provider.xpi (localized for US)?

Indeed... twiece I have tried to install non-localize gdata-provider.xpi, but each time the extension has been shown as disabled and below it a information about something missing has been displayed.

---

### Post by el cameleon on 2010-01-07
I got exactly same problem, gdata-provider is disabled because Thunderbird claims that a component is missing?! I use last nighty build of lightning, I don't know if it could be related...

---

### Post by qva5 on 2010-01-08
> **el cameleon said:**
> I got exactly same problem, gdata-provider is disabled because Thunderbird claims that a component is missing?! I use last nighty build of lightning, I don't know if it could be related...

Have you tried installing components from [http://releases.mozilla.org/pub/mozi...ux-i686/en-US/]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/linux-i686/en-US/") ?

---

### Post by el cameleon on 2010-01-08
> **qva5 said:**
> Have you tried installing components from [http://releases.mozilla.org/pub/mozi...ux-i686/en-US/]("http://releases.mozilla.org/pub/mozilla.org/calendar/lightning/releases/1.0b1rc1/linux-i686/en-US/") ?
Thanks, I have updated lightning with the one available and now it works!

---

### Post by PDA1 on 2010-01-12
Works very well.

Tell me, is the calendar I see in Thunderbird 3.0 linked directly to Google calendars under my gmail account name?

---

### Post by qva5 on 2010-01-13
> **PDA1 said:**
> Works very well.

Tell me, is the calendar I see in Thunderbird 3.0 linked directly to Google calendars under my gmail account name?


It all depends on a way you configure your Lightning. 

When you attach new google calendar, you can insert private url(get it from google calendar site) pointing to your calendar.

---

### Post by michael37 on 2010-01-26
Major update to the OP since Lightning 1 is now available via Add-ons.

---

### Post by michael37 on 2010-01-26
Sorry for multiples.  Upgrading to Thunderbird 3.0.1 is recommended for everyone, and especially Lightning 1 users.

---

### Post by qva5 on 2010-01-28
> **michael37 said:**
> Major update to the OP since Lightning 1 is now available via Add-ons.

Great news;)

I haven't got any major issues with previous version of Lighting add-on, but having stable version feels much much better.

---

### Post by michael37 on 2010-01-28
> **qva5 said:**
> Great news;)

I haven't got any major issues with previous version of Lighting add-on, but having stable version feels much much better.

Glad it makes you feel better.  You are running the same exact code, just named differently :D

---

### Post by qva5 on 2010-01-30
> **michael37 said:**
> Glad it makes you feel better.  You are running the same exact code, just named differently :D

You can call me prudent man;)

---

### Post by Levis 1 on 2010-06-17
No. Thunderbird is a separate email client.... ussed to feed your emails  from email providers. If you are using gmail, igoogle has an  application for emails from google.

---

### Post by zebraneo on 2010-10-03
I just wanted to thank everyone your great

---

