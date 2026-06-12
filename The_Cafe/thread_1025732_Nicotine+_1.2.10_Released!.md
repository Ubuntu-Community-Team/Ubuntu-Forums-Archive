---
title: "Nicotine+ 1.2.10 Released!"
date: 2008-12-30
forum: The Cafe
---

### Post by OffHand on 2008-12-30
It took a while but here it is... a new version of Nicotine+. This release addresses a huge amount of bug fixes and enhancements. Happy New Year...Enjoy!

[http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)

---

### Post by Eisenwinter on 2008-12-30
Thanks for the heads up, I will upgrade straight away.

---

### Post by RiceMonster on 2008-12-30
Sweet. Should be in the Arch repos soon. I'm actually using nicotine+ right now.

---

### Post by pt123 on 2008-12-30
[http://www.nicotine-plus.org/wiki/NicotineOnDebian](http://www.nicotine-plus.org/wiki/NicotineOnDebian)
seems to list old packages.

GetDeb.net doesn't have Nicotine

---

### Post by OffHand on 2008-12-30
> **pt123 said:**
> [http://www.nicotine-plus.org/wiki/NicotineOnDebian](http://www.nicotine-plus.org/wiki/NicotineOnDebian)
seems to list old packages.

GetDeb.net doesn't have Nicotine

As explained in this thread: [http://ubuntuforums.org/showthread.php?t=1002303](http://ubuntuforums.org/showthread.php?t=1002303)


If you want to use the most current version, take the one on the N+ website and run it from source. The other option is to wait till someone makes a deb, but running from source is too easy.

---

### Post by IcKY99 on 2009-01-01
> **OffHand said:**
> As explained in this thread: [http://ubuntuforums.org/showthread.php?t=1002303](http://ubuntuforums.org/showthread.php?t=1002303)


If you want to use the most current version, take the one on the N+ website and run it from source. The other option is to wait till someone makes a deb, but running from source is too easy.

i've downloaded Nicotine 1.2.9 from the terminal, and it installed in my applications menu neatly, i downloaded this new version from the website. is there anyway to overwrite 1.2.9 with the new version so it will be in my applications menu. 1.2.9 wont let me change the settings but 1.2.10 will

---

### Post by OffHand on 2009-01-02
> **IcKY99 said:**
> i've downloaded Nicotine 1.2.9 from the terminal, and it installed in my applications menu neatly, i downloaded this new version from the website. is there anyway to overwrite 1.2.9 with the new version so it will be in my applications menu. 1.2.9 wont let me change the settings but 1.2.10 will

1) Download Nicotine+ from here:

[http://www.nicotine-plus.org/](http://www.nicotine-plus.org/)

2) Extract it to your home folder

3) Open your terminal

4) cd nicotine+-1.2.10 (or wherever you have installed it)

5) ./nicotine

6) You can make a launcher using this path: /home/username/nicotine+ folder/nicotine  (do this with System > Preferences > Main Menu)

---

### Post by OffHand on 2009-01-07
Just a little bump in case anyone missed this thread :D

---

### Post by IcKY99 on 2009-01-07
thanks it worked perfectly! one less thing i have to worry about in ubuntu, audacity is my next problem haha

---

### Post by OffHand on 2009-01-07
> **IcKY99 said:**
> thanks it worked perfectly! one less thing i have to worry about in ubuntu, audacity is my next problem haha

Good to hear! Drop by in the nicotine room sometime. Loads of Linux nerds there  ;)

---

### Post by mrgnash on 2009-01-09
Meh, it crashes as soon as I perform a search. Deleted.

---

### Post by OffHand on 2009-01-09
> **mrgnash said:**
> Meh, it crashes as soon as I perform a search. Deleted.

Too bad, but it looks like you don't want any help to solve the issue so better luck next time. Too be honest I think it is a local problem... 1.2.10 has been thoroughly tested.

---

### Post by justoffthecoast on 2009-01-19
> **mrgnash said:**
> Meh, it crashes as soon as I perform a search. Deleted.

Having the same problem here with 1.2.9 and 1.2.10...I upgraded from 1.2.9 to 1.2.10 hoping that would fix the issue, but no luck. Once I initiate a search, the program begins freezing sporadically (stops responding but starts again if I wait a few minutes...unfortunately it usually doesn't take long for it to freeze again). After freezing and un-freezing for several minutes, it totally locks up and I have to kill and re-open the program.

At first I thought I was getting flooded with connections following a search, but the last time it happened, search results had basically stopped coming in and I was down to 17 connections from a peak of 921. Any suggestions?

---

### Post by OffHand on 2009-01-19
> **justoffthecoast said:**
> Having the same problem here with 1.2.9 and 1.2.10...I upgraded from 1.2.9 to 1.2.10 hoping that would fix the issue, but no luck. Once I initiate a search, the program begins freezing sporadically (stops responding but starts again if I wait a few minutes...unfortunately it usually doesn't take long for it to freeze again). After freezing and un-freezing for several minutes, it totally locks up and I have to kill and re-open the program.

At first I thought I was getting flooded with connections following a search, but the last time it happened, search results had basically stopped coming in and I was down to 17 connections from a peak of 921. Any suggestions?

Can you please launch N+ from the command line and see if it leaves any traces?

---

### Post by justoffthecoast on 2009-01-19
> **OffHand said:**
> Can you please launch N+ from the command line and see if it leaves any traces?

```
Nicotine supports "psyco", an inline optimizer for python
code, you can get it at http://sourceforge.net/projects/psyco/
Enabling RGBA
X11/GTK RGBA Bug workaround: Setting default colormap to RGB
X11/GTK RGBA Bug workaround: Restoring RGBA as default colormap.
```

---

### Post by kk0sse54 on 2009-01-19
I'll give some positive feedback, great release, nice that there's been a lot of new features added :). Now to see if I can get it to work in NetBSD...

---

### Post by kk0sse54 on 2009-01-19
*deleted* double post

---

### Post by OffHand on 2009-01-20
> **justoffthecoast said:**
> ```
Nicotine supports "psyco", an inline optimizer for python
code, you can get it at http://sourceforge.net/projects/psyco/
Enabling RGBA
X11/GTK RGBA Bug workaround: Setting default colormap to RGB
X11/GTK RGBA Bug workaround: Restoring RGBA as default colormap.
```

Hmmmm.... that has nothing to do with the stuff you are experiencing. 

I don't have a lot of time now but maybe you could try a clean profile. Just rename .nicotine to .nicotine.old and start N+ again.

---

### Post by OffHand on 2009-01-20
> **C!oud said:**
> I'll give some positive feedback, great release, nice that there's been a lot of new features added :). Now to see if I can get it to work in NetBSD...

Good to hear not everyone has issues with this release  :)

---

### Post by OffHand on 2009-01-20
Please contribute to the N+ by posting bug reports...

[Current issues and requests]("http://www.nicotine-plus.org/report/1")

[Make New Bug Report]("http://www.nicotine-plus.org/newticket")

Thanks in advance!

---

### Post by justoffthecoast on 2009-01-20
It definitely seems like my problem was stemming from getting flooded by too many connections. I set a minimum bitrate to search for, specified that I only wanted results from users with a free slot and started searching for specific albums rather than artists. N+ hasn't locked up since!

---

### Post by OffHand on 2009-01-21
> **justoffthecoast said:**
> It definitely seems like my problem was stemming from getting flooded by too many connections. I set a minimum bitrate to search for, specified that I only wanted results from users with a free slot and started searching for specific albums rather than artists. N+ hasn't locked up since!

Glad to hear it works properly now. The dev(s) are aware of [this problem]("http://www.nicotine-plus.org/ticket/364").

---

### Post by Eisenwinter on 2009-01-22
I'm having a weird problem also.

This problem didn't start with the switch to 1.2.10, though, it has been happening since 1.2.9.

Whenever a file finishes downloading, the next file gets downloaded at insanely low speeds.
I'm talking about 0.x to 1.x KB/s speeds.

When I restart N+, the file is downloaded at higher speeds again (8+ KB/s, varies depending on the user's upload speed).

Is anyone else experiencing this?

---

### Post by OffHand on 2009-01-22
> **Eisenwinter said:**
> I'm having a weird problem also.

This problem didn't start with the switch to 1.2.10, though, it has been happening since 1.2.9.

Whenever a file finishes downloading, the next file gets downloaded at insanely low speeds.
I'm talking about 0.x to 1.x KB/s speeds.

When I restart N+, the file is downloaded at higher speeds again (8+ KB/s, varies depending on the user's upload speed).

Is anyone else experiencing this?

Send me a pm on N+ and we can test it on my connection. My connection is pretty bad *** and stable.

---

### Post by SomeGuyDude on 2009-01-22
Arch with Compiz, jacks my CPU usage to 70% and freezes every few seconds when searching for files. Not incredibly pleased.

---

### Post by OffHand on 2009-01-22
> **SomeGuyDude said:**
> Arch with Compiz, jacks my CPU usage to 70% and freezes every few seconds when searching for files. Not incredibly pleased.

We have [fixed]("http://www.nicotine-plus.org/ticket/284#comment:3") the issue. We will release a new version very soon! Stay tuned....

---

### Post by SomeGuyDude on 2009-01-22
> **OffHand said:**
> We have [fixed]("http://www.nicotine-plus.org/ticket/284#comment:3") the issue. We will release a new version very soon! Stay tuned....

Staying tuned! But your site won't load.

---

### Post by OffHand on 2009-01-22
> **SomeGuyDude said:**
> Staying tuned! But your site won't load.
Yes, it does.

p.s. don't hold your breath. release can take a couple of days  ;)

---

### Post by OffHand on 2009-01-23
We have released a [new version!]("http://ubuntuforums.org/showthread.php?t=1048422")

---

