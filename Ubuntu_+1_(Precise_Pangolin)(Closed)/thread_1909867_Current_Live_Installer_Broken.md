---
title: "Current Live Installer Broken?"
date: 2012-01-16
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by quaeritate on 2012-01-16
I ended up with quite a broken 12.04 install so I decided to format and start again with the daily-live image. Unfortunately it always seems to get stuck quite early on with the message "Removing conflicting operating system files...". I have just updated to my iso to the latest daily and still have the same problem.

I have had a search around and can't find anything. Is anyone else having this problem? Should I just keep updating the daily ISO each day until it works?

---

### Post by effenberg0x0 on 2012-01-16
> **quaeritate said:**
> I ended up with quite a broken 12.04 install so I decided to format and start again with the daily-live image. Unfortunately it always seems to get stuck quite early on with the message "Removing conflicting operating system files...". I have just updated to my iso to the latest daily and still have the same problem.

I have had a search around and can't find anything. Is anyone else having this problem? Should I just keep updating the daily ISO each day until it works?

I found a couple mentions via [Google]("https://www.google.com/search?client=ubuntu&channel=fs&q=removing+conflisting+operating+system+files&ie=utf-8&oe=utf-8#sclient=psy-ab&hl=pt-BR&safe=active&client=ubuntu&hs=XDl&channel=fs&source=hp&q=%22removing+conflicting+operating+system+files%22&pbx=1&oq=%22removing+conflicting+operating+system+files%22&aq=f&aqi=&aql=&gs_sm=e&gs_upl=15037l19679l0l20065l4l4l0l0l0l1l319l1017l0.1.2.1l4l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=853b1743cff9b146&biw=1201&bih=744"). UbuntuForums also has threads about it. Launchpad [Bug #186711]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CCAQFjAA&url=https%3A%2F%2Fbugs.launchpad.net%2Fbugs%2F186711&ei=1QAUT8KlOY_rtgeYt_yQAg&usg=AFQjCNGAGlNwb-U96vWNN6TkVqrcjzd-UA&sig2=n3v_kXMgyPgrpCVpqWf9Pw&cad=rja") seems very similar to what you are describing.

---

### Post by meborc on 2012-01-16
Chris from the Linux Action Show also noted he had troubles with the daily on Sunday

Check the awesome episode at [http://www.jupiterbroadcasting.com/15756/linux-rocks-ces-las-s20e02/](http://www.jupiterbroadcasting.com/15756/linux-rocks-ces-las-s20e02/)

---

### Post by quaeritate on 2012-01-17
> **effenberg0x0 said:**
> I found a couple mentions via [Google]("https://www.google.com/search?client=ubuntu&channel=fs&q=removing+conflisting+operating+system+files&ie=utf-8&oe=utf-8#sclient=psy-ab&hl=pt-BR&safe=active&client=ubuntu&hs=XDl&channel=fs&source=hp&q=%22removing+conflicting+operating+system+files%22&pbx=1&oq=%22removing+conflicting+operating+system+files%22&aq=f&aqi=&aql=&gs_sm=e&gs_upl=15037l19679l0l20065l4l4l0l0l0l1l319l1017l0.1.2.1l4l0&bav=on.2,or.r_gc.r_pw.,cf.osb&fp=853b1743cff9b146&biw=1201&bih=744"). UbuntuForums also has threads about it. Launchpad [Bug #186711]("https://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CCAQFjAA&url=https%3A%2F%2Fbugs.launchpad.net%2Fbugs%2F186711&ei=1QAUT8KlOY_rtgeYt_yQAg&usg=AFQjCNGAGlNwb-U96vWNN6TkVqrcjzd-UA&sig2=n3v_kXMgyPgrpCVpqWf9Pw&cad=rja") seems very similar to what you are describing.

Yeah, I googled and found those links, however they relate to hardy.

Looking around this forum is seems that the daily can be broken and not install. I have just managed to install the latest daily, however I did have to do it disconnected from the Internet. It hung on contacting the time server otherwise.

---

### Post by meborc on 2012-01-17
when i find a daily that works i save the iso somewhere safe so that when things go bad i can reinstall and upgrade from that image

---

### Post by jppr on 2012-01-17
This works [http://cdimage.ubuntu.com/daily-live/](http://cdimage.ubuntu.com/daily-live/) 
I did just fresh installation and system works fine

---

### Post by GeorgeVita on 2012-01-17
Installing Lubuntu PP on EeePC Netbook from the latest daily live .iso over existing Lubuntu OO, I noticed 3 possibly wrong points:

1. following the installation procedure, the window "choose a photo for login" was bigger that the vertical screen size hiding the "back" and "continue" buttons under the panel. Undecorating window (right click menu icon at top left of window) made buttons visible (screen size is 1024x600).

2. as there is no CD drive, the installation began using a LiveUSB (or LiveSDHC) memory. After a while without any action, a useless window appeared reporting "new media attached" regarding the same LiveUSB media. This is possibly done after re-triggering all peripherals.

3. a second swap partition created automatically! Install option was "Erase Ubuntu and reinstall".

Have you noticed any of the above?

G

---

### Post by kansasnoob on 2012-01-17
> **GeorgeVita said:**
> Installing Lubuntu PP on EeePC Netbook from the latest daily live .iso over existing Lubuntu OO, I noticed 3 possibly wrong points:

1. following the installation procedure, the window "choose a photo for login" was bigger that the vertical screen size hiding the "back" and "continue" buttons under the panel. Undecorating window (right click menu icon at top left of window) made buttons visible (screen size is 1024x600).

2. as there is no CD drive, the installation began using a LiveUSB (or LiveSDHC) memory. After a while without any action, a useless window appeared reporting "new media attached" regarding the same LiveUSB media. This is possibly done after re-triggering all peripherals.

3. a second swap partition created automatically! Install option was "Erase Ubuntu and reinstall".

Have you noticed any of the above?

G

I don't know about the rest but #3 is a known issue:

[https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507](https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507)

---

### Post by GeorgeVita on 2012-01-17
> **kansasnoob said:**
> I don't know about the rest but #3 is a known issue: [https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507](https://bugs.launchpad.net/ubuntu/+source/partman-auto/+bug/782507)
Thanks, I bypassed/fixed using option "Something else" > manual partitioning
G

---

### Post by quaeritate on 2012-01-22
I am certain part of my problems have been to do with the fact that the official New Zealand Ubuntu mirror has not been updated in at least 10 days.

---

### Post by jerrylamos on 2012-01-22
Today's daily, Sunday 22 Jan install hung at "configuring target system".

Rebooted, tried install again just the same way, worked O.K.  ?

This is an Acer Aspire notebook with Windows 7 and Narwhal installed with the new Precise installed alongside.  The Precise replaces an Ocelot, supposedly all up to date, however running update-grub trashed grub requiring a boot-repair.

Anyway, precise up and running.  Now for some Alpha update breakage...

Jerry

---

