---
title: "Display problems"
date: 2012-11-25
forum: Testimonials &amp; Experiences
---

### Post by Orange Kingdom on 2012-11-25
Setup a modern display properly with a resolution of 1920x1200.
It still stucks at 1024x768.
I installed 12.10 and there was NO option to change the display resolution. Oh man, feels like 1998.
Such a basic thing is obviously too difficult for the Ubuntu developers.
I tried Mint 14 and guess what. The same issue.
I even tried to install the Nvidia driver. I had to kill X in order to install (friendly way of installing a driver). When i logged in after a reboot it respawns the login screen and was unable to use Ubuntu/Mint. Pfff. Three hours later no functional system.
:(

---

### Post by snowpine on 2012-11-25
I looked at your post history and see it's only been 5 hours since you asked for help with your display resolution question. Please be patient and somebody will help you shortly, the people who **volunteer** here answering questions have jobs/families/hobbies, and we are in different time zones, but most questions get answered within a day or two. :) I would help you myself but I am not an Nvidia expert.

Your statement that Ubuntu has "NO option to change the display resolution" is absurd. (Assuming you are using Unity desktop) just tap the Super/Windows key and type "display resolution"--you'll find it! ;)

---

### Post by QIII on 2012-11-25
I'm sure someone who is good with nVidia will help you shortly.

ATI works fine.

---

### Post by MadmanRB on 2012-11-25
Did installing the drivers help any?
The current release of Ubuntu 12.20 seems very bad when it comesx to proprietary drivers, its what we get for not having jockey anymore.
Yeah congratulations for getting rid of something useful Ubuntu, now that its locked away installing drivers is ten times harder now then they used to be.

---

### Post by ibjsb4 on 2012-11-25
> **MadmanRB said:**
> its what we get for not having jockey anymore.
Yeah congratulations for getting rid of something useful Ubuntu, now that its locked away installing drivers is ten times harder now then they used to be.

[http://packages.ubuntu.com/quantal/jockey-gtk](http://packages.ubuntu.com/quantal/jockey-gtk)

..:confused:

---

### Post by MadmanRB on 2012-11-26
> **ibjsb4 said:**
> [http://packages.ubuntu.com/quantal/jockey-gtk](http://packages.ubuntu.com/quantal/jockey-gtk)

..:confused:

Well its there, but its not as direct as it used to be, it needs the icon notification back for installing drivers.

---

### Post by deadflowr on 2012-11-26
This sounds more like a monitor issue than a driver issue.
When linux can't read or isn't able to read the EDID from the monitor it sets the default display size at 1024X768, or 800x600, as these are common display that will run on almost all monitors.
You'll know if you look at your xorg logs, or your xsession-error logs.

---

### Post by mastablasta on 2012-11-26
yes it seems that hardware that is ment to work in windows and has manufacturers support for windows work's well (a surprise?) in windows. but it doesn't work so well in other OS (for exmaple linux).
 
according to OP it should work in linux as well. and probably it would if it received same amount of linux support from the manufacturer as it has for windows.
 
also use LTS release for less new features (such as new driver install interface) and more stability (such as well established old driver install jockey interface).

---

### Post by robert shearer on 2012-11-26
> **mastablasta said:**
>  (for **exmaple** linux).

Old Canadian respin of Ubuntu 7.15 AKA 'floppy foliage' :-)

---

### Post by sffvba[e0rt on 2012-11-27
Lets do the support in the support section shall we?

*Thread **closed**.*

404

---

