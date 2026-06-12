---
title: "A hand for wicd"
date: 2007-03-21
forum: The Cafe
---

### Post by Ripfox on 2007-03-21
I am at my local coffee house surfin' away thanks to wicd. This has made life so much easier...NWM never worked right, but this little program is the bomb. Just a big up, no connection to open wireless networks and all the trouble before was a deal breaker.

---

### Post by SishGupta on 2007-03-21
The network manager in edgy is 0.6.3 i think and yeah, that version doesn't work that hot. When i used edgy on my laptop I always upgraded to 6.4 (the latest).

That said, give network manager another shot when feisty comes out as it is more integrated into th e networking component of gnome.

Its cool that wicd works well for you though.

---

### Post by Ripfox on 2007-03-22
Yea...used the one in feisty. Still doesn't work right, but maybe it's due to the alpha version of 
Feisty (running it on my desktop currently with wireless usb device)

Just spins its wheels...wicd connects automatically.

All is well :)

---

### Post by rahulthewall3000 on 2007-03-29
The NVM in feisty sucks, there is no need of it. WICD rocks!
Praise be the generous soul who programmed this beautiful software !

Cheers
Rahul

---

### Post by Mateo on 2007-03-29
could you explain what it is?  a google search of "'wicd' comes up with some television station.

---

### Post by darthchaosofrspw on 2007-03-30
> **Mateo said:**
> could you explain what it is?  a google search of "'wicd' comes up with some television station.

[http://compwiz18.blackhole.cx/wicd/wb](http://compwiz18.blackhole.cx/wicd/wb)

---

### Post by NeoTaoistTechnoPagan on 2008-10-20
Sorry to revive this old thread, but the latest version of Wicd 1.5.3 had me running back to NWM on both my Ubuntu & Gentoo systems. It really is just not the same anymore. The .conf files are now a different format and since upgrading it - nothing worked right.

NTTP

---

### Post by beercz on 2008-10-20
I find wicd is working really well for me - and I am using Intrepid

---

### Post by Polygon on 2008-10-20
only problem i ever had with NM is that it could not connect to WPA networks....motsly becuase i was using a SVN version =)

the intrepid version is nice however.

---

### Post by gn2 on 2008-10-20
I'm using [WICD 1.4.2]("http://cid-a097623d1ac4df74.skydrive.live.com/self.aspx/Public/wicd|_1.4.2-1-all.deb") on Ubuntu 8.04 and it's flawless.

---

### Post by billgoldberg on 2008-10-20
> **gn2 said:**
> I'm using [WICD 1.4.2]("http://cid-a097623d1ac4df74.skydrive.live.com/self.aspx/Public/wicd|_1.4.2-1-all.deb") on Ubuntu 8.04 and it's flawless.

That version sucks on my computer.

Older versions really worked well, that's over now.

---

### Post by imdano on 2008-10-20
> **NeoTaoistTechnoPagan said:**
> Sorry to revive this old thread, but the latest version of Wicd 1.5.3 had me running back to NWM on both my Ubuntu & Gentoo systems. It really is just not the same anymore. The .conf files are now a different format and since upgrading it - nothing worked right.

NTTPThe .conf file format hasn't changed, they just moved to a different directory.  There were problems with the upgrade process though. The old /etc/init.d/wicd file was getting left behind for a lot of people which would keep the daemon from starting at boot, and a lot of people didn't realize that /opt/wicd/tray.py had been replaced by wicd-client.  Other than those issues 1.5.3 really should behave much better than 1.4.2.  What kind of problems were you having?

edit: Same question to you billgoldberg.

---

### Post by Majorix on 2008-10-20
I am using Wicd (I think it is the latest) on my Arch install. NetworkManager applet didn't work for me and it is usually not easy to set a static ip system with NM; unlike with Wicd. If nobody releases a better applet or guys over at NM make a decent software I will go on with Wicd.

---

### Post by bionnaki on 2008-10-21
I used wicd for a little while. Connection at boot-up worked and my connection was reliable. However, I was not able to hop onto a different network on the fly whatsoever. I would have to either stop/restart ath0 via commandline or reboot. 

any suggestions for earlier versions of wicd that can handle this?

---

### Post by myusername on 2008-10-21
mine does that just fine...NWM could NEVER do this. it would freeze for like 10 minutes before dropping connection. wicd works flawlessly

---

### Post by gn2 on 2008-10-21
> **bionnaki said:**
> I used wicd for a little while. Connection at boot-up worked and my connection was reliable. However, I was not able to hop onto a different network on the fly whatsoever. I would have to either stop/restart ath0 via commandline or reboot. 

any suggestions for earlier versions of wicd that can handle this?

1.4.2 can do that on my Asus F9E laptop with Ubuntu 8.04.

There's a link to the Wicd 1.4.2 .deb in my previous post.

---

### Post by oofnik on 2008-10-21
Don't mean to hijack, but I have a question pertaining to Wicd 1.5.3. I installed Wicd to replace NetworkManager because I had enough of the stupid Gnome keyring popup on boot. I use my fingerprint reader to log in, and I could not get the keyring manager to go away.

Anyway, is it possible to configure Wicd to transparently connect to SSIDs of the same name but different MAC addresses? My university has dozens of unsecured access points with the same name all around campus, but Wicd treats them as individual networks and I have to check "Automatically connect to this network" for each new AP it discovers. Is there a way around this?

---

### Post by imdano on 2008-10-21
> **oofnik said:**
> Anyway, is it possible to configure Wicd to transparently connect to SSIDs of the same name but different MAC addresses? My university has dozens of unsecured access points with the same name all around campus, but Wicd treats them as individual networks and I have to check "Automatically connect to this network" for each new AP it discovers. Is there a way around this?If you select the "Use these settings for all APs with this essid" (or something worded similarly, don't have my Linux box around to check) checkbox in the advanced settings dialog for one of the APs the settings you have for that particular AP should be set globally.  If it doesn't work correctly let me know and I'll try fix it before we release 1.5.4.

---

### Post by gn2 on 2008-10-21
> **imdano said:**
> ~   If it doesn't work correctly let me know and I'll try fix it before we release 1.5.4.

Are you the Wicd developer Dan O'Reilly?
If so I'd just like to say thanks for a simply outstanding application. :)

Do you have a link for an archive of older versions to download?

---

### Post by SomeGuyDude on 2008-10-21
> **imdano said:**
> If you select the "Use these settings for all APs with this essid" (or something worded similarly, don't have my Linux box around to check) checkbox in the advanced settings dialog for one of the APs the settings you have for that particular AP should be set globally.  If it doesn't work correctly let me know and I'll try fix it before we release 1.5.4.

Throw in support for wired PEAP connections if possible. I have to use a wpa_supplicant script and then comment out the lines whenever I'm going to go out and use the wireless, then before I wire in back in my room I have to uncomment the lines and reboot.

I've been using Wicd for over a week now and it's absolutely perfect for the most part, but that one feature would make things a lot easier for us college students. Gnome's network-manager seems to have that feature down pat.

---

### Post by doorknob60 on 2008-10-21
> **gn2 said:**
> Are you the Wicd developer Dan O'Reilly?
If so I'd just like to say thanks for a simply outstanding application. :)

Do you have a link for an archive of older versions to download?

Look at his Forum name, 'imdano'... imdano=imdanoreilly=I'm Dan O'Reilly :-D

Anyways, here you can find old versions: [http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460)

---

### Post by gn2 on 2008-10-21
> **doorknob60 said:**
> Look at his Forum name, 'imdano'... imdano=imdanoreilly=I'm Dan O'Reilly :-D

Anyways, here you can find old versions: [http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460](http://sourceforge.net/project/showfiles.php?group_id=194573&package_id=229460)

Yep, that's what I thought too.

Thanks for the link :)

---

### Post by imdano on 2008-10-21
> **doorknob60 said:**
> Look at his Forum name, 'imdano'... imdano=imdanoreilly=I'm Dan O'Reilly :-DYep :)

> **SomeGuyDude said:**
> Throw in support for wired PEAP connections if possible. I have to use a wpa_supplicant script and then comment out the lines whenever I'm going to go out and use the wireless, then before I wire in back in my room I have to uncomment the lines and reboot.

I've been using Wicd for over a week now and it's absolutely perfect for the most part, but that one feature would make things a lot easier for us college students. Gnome's network-manager seems to have that feature down pat.That's on the TODO list.  As a workaround for now you can try having wpa_supplicant launch as a preconnection script (just make sure to use -B so it runs in the background).

---

### Post by SomeGuyDude on 2008-10-21
> **imdano said:**
> Yep :)

That's on the TODO list.  As a workaround for now you can try having wpa_supplicant launch as a preconnection script (just make sure to use -B so it runs in the background).

That's what I'm doing at the moment, though it borks my wireless so I have to disable the script whenever I want to pull out the wire.

No joke, though, Wicd is the only reason I'm on Arch right now. I could never get things working right using just the normal scripts and for some reason network-manager always screwed up, so I couldn't get my wireless and that's a dealbreaker for me. I'm willing to accept a lot of stuff not working right out-of-the-box, but I need wireless (so I can, y'know, find ways to fix everything else).

Friend suggested Wicd and whammo, I got my wireless working. Now I'm 12 days of Arch and lovin' it. So here's to an excellent app! :guitar:

---

### Post by oofnik on 2008-10-24
> **imdano said:**
> If you select the "Use these settings for all APs with this essid" (or something worded similarly, don't have my Linux box around to check) checkbox in the advanced settings dialog for one of the APs the settings you have for that particular AP should be set globally.  If it doesn't work correctly let me know and I'll try fix it before we release 1.5.4.

Ah, I didn't even see that option. Works perfectly. Thanks for this awesome software! :)

---

### Post by markackerman8@gmail.com on 2008-11-13
Hello guys,

Wicd rocks but a little unstable with wpa1/2, ie quits often after 1-2hrs.

I tried 1.5.4 but that gave me SERIOUS problems with wpa1/2 so happily back to the earlier version...1.5.3

others beware

any fixes to the stability issue??

Mark

---

### Post by imdano on 2008-11-13
It'd be nice if you could file a bug and provide logs re: 1.5.4 issues.

Losing your connection after 1-2 hours is almost certainly a driver/router issue, not something wicd is doing.  Once you actually establish a connection wicd just monitors it's status, it has no role in keeping it up (though it will try to connect you again if the connection is lost).

---

