---
title: "CAREFUL: Firefox 3.0.10 upgrade may not complete fully!"
date: 2009-04-28
forum: The Cafe
---

### Post by Kareeser on 2009-04-28
Hey guys,

Quick message out there to not upgrade to 3.0.10, which was released earlier today into the repos.

For some reason, the upgrade locks up the computer, and does not complete. Firefox is unusable afterwards as /usr/lib/firefox-3.0.10/firefox.sh is **completely empty**.

I thought it was just me, but [reports are coming in now](http://ubuntuforums.org/showthread.php?t=1142163) that other peoples' updates were botched.

This is significant in that Ubuntu by default only comes with one browser! I had no clue this was so significant until I simply had no browser to use. Heh.

YMMV!

Workaround:
Install the package "firefox-3.5" and run with /usr/bin/firefox-3.5

---

### Post by FuturePilot on 2009-04-28
By any chance using Ext4?

---

### Post by Icehuck on 2009-04-28
I just upgraded before reading this post and I thought, "Oh Crap!"  Though it looks like my upgrade completed just fine.

---

### Post by Sef on 2009-04-28
>  		By any chance using Ext4? 	

I use ext4, and it upgraded just fine for me.

---

### Post by kostkon on 2009-04-28
I don't think that there is a widespread problem, only the usual small number of cases where for some reason the update manager crashed during the update or Firefox is not loading because it wasn't restarted etc...

---

### Post by Kareeser on 2009-04-28
Okay... I'm glad others updated properly. I was hoping that this wouldn't be another "Python-2.6 is borked!"-like occurance :)

Looks like the two cases (mine and the other thread linked) are the only two so far.

May have been because we were both running firefox during the upgrade.

---

### Post by pwnst*r on 2009-04-29
way to jump the gun.

---

### Post by ghindo on 2009-04-29
I had no troubles.  Have you considered filing a bug report?

---

### Post by hanzomon4 on 2009-04-29
Had/have? troubles 3.5 segfaults before it even starts

---

### Post by lisati on 2009-04-29
Different repos? Different config on your system?
I'm currently on a machine using 8.10, XFCE, and a freshly updated FF 3.0.10, haven't noticed any problems so far.

---

### Post by vkm2 on 2009-04-29
Yes, I am having this problem. Using 8.04LTS and Gnome, Synaptic updated Firefox to 3.0.8 yesterday, and then firefox became unusable. Today there was a 3.0.9 update but it is still unusable. Clicking on the firefox icon brings up nothing.

Help!

> **Kareeser said:**
> Hey guys,

Quick message out there to not upgrade to 3.0.10, which was released earlier today into the repos.

For some reason, the upgrade locks up the computer, and does not complete. Firefox is unusable afterwards as /usr/lib/firefox-3.0.10/firefox.sh is **completely empty**.

I thought it was just me, but [reports are coming in now](http://ubuntuforums.org/showthread.php?t=1142163) that other peoples' updates were botched.

This is significant in that Ubuntu by default only comes with one browser! I had no clue this was so significant until I simply had no browser to use. Heh.

YMMV!

Workaround:
Install the package "firefox-3.5" and run with /usr/bin/firefox-3.5

---

### Post by lovinglinux on 2009-04-29
I was running Firefox during the update, I'm using ext4 and everything is fine.

---

### Post by samjh on 2009-04-29
> **FuturePilot said:**
> By any chance using Ext4?

Ext4 here, and no problem with the update.

---

### Post by Saint Angeles on 2009-04-29
> **lovinglinux said:**
> I was running Firefox during the update, I'm using ext4 and everything is fine.
same here... thank god!

---

### Post by Irihapeti on 2009-04-29
Just upgraded with no problems. Having read the other messages, I closed Firefox first just to be safe. Running 8.04 here.

The first time I clicked on the Firefox icon, a small window came up very briefly in the middle of the screen, and then nothing further happened. The second time, Firefox launched. I've seen this happen on a number of occasions and have no idea what it's about.

---

### Post by Yashiro on 2009-04-29
People complain after every Firefox update.

---

### Post by Pasdar on 2009-04-29
Ext4 32Bit here, no problem after upgrade.

---

### Post by darrenn on 2009-04-29
Works fine for me did you close firefox before you tried to upgrade?

---

### Post by Pasdar on 2009-04-29
PS: Whenever I see that firefox is about to be updated, I close Firefox just before it finishes download of updates (after which it will install). I advice you to do the same.

---

### Post by Orlsend on 2009-04-29
> **Yashiro said:**
> People complain after every Firefox update.

Thats so True.

I Upgraded today, I am on Jaunty and have no Troubles...

---

### Post by Giant Speck on 2009-04-29
> **Yashiro said:**
> People complain after every Firefox update.
 
Yes, but normally people compain about Firefox's performance, not whether or not it installed correctly in the first place.

---

### Post by Dai Bando on 2009-04-29
I had no problems at all, but I did follow the instructions and rebooted Firefox.

---

### Post by Dale61 on 2009-04-29
I saw that there was a FF update, so started the download, then closed FF until it had finished.

Restarted - no problems.

---

### Post by SuperSonic4 on 2009-04-29
Working perfectly on the 32bit laptop and 64bit desktop. Both using ext4

---

### Post by Kareeser on 2009-04-29
Correct. Since the update breaks firefox by freezing the computer, the package is not fully installed, and the script /usr/lib/firefox-3.0/firefox.sh is empty.

As Firefox is the only browser installed by default on Ubuntu, if it's broken, a lot of people are going to be stumped with a non-working browser.

---

### Post by pwnst*r on 2009-04-29
> **Kareeser said:**
> Correct. Since the update breaks firefox by freezing the computer, the package is not fully installed, and the script /usr/lib/firefox-3.0/firefox.sh is empty.

As Firefox is the only browser installed by default on Ubuntu, if it's broken, a lot of people are going to be stumped with a non-working browser.

except it's only you and a few people so far.  you should work for the media.

---

### Post by BGFG on 2009-04-29
Just checked, 3.0.10 fine here. i use Shiretoko though. May have been your repo or an update manager bug.

---

### Post by Ubudireh on 2009-04-29
Just thought i would drop a quick note here to mention that I, too, had the same trouble (EXT3, I think).  Am about to try the fix and see what happens.

Hmm.  Did try to get the install package as suggested, but was told i need to fix my dpkg problem first (see [http://ubuntuforums.org/showthread.php?p=7177952](http://ubuntuforums.org/showthread.php?p=7177952) for the rest of my boggle).  So, i seem to be going in circles here: can't get fix it without the dpkg thing sorted, but can't get that done since there's a problem with something else.

---

### Post by speedwell68 on 2009-04-29
It updated fine here.  I always close all applications when running the update manager, I just think it is a good idea to do so.  There is no logic or prior knowledge behind me closing all apps it is just something I do.

---

### Post by Kareeser on 2009-04-29
> **pwnst*r said:**
> except it's only you and a few people so far.  you should work for the media.

Case-in-point, note the third person who's experienced a problem.

To quote an esteemed FCC chairman:
> Gentlemen, we got 20 calls about the David Hyde-Pierce incident. And as you know, one call equals a billion people, which means 20 billion people were offended by this. Needless to say, something must be done.

I jest, but in truth, imagine what would happen if the UK hadn't established quarantine and eradication practices for the cows with mad cow disease.

Imagine today if instead of warning you about Swing Flu, your government decided to cross their fingers and hope for the best.

It's a crude analogy, but it kinda works.

---

### Post by nm4m on 2009-05-01
Firefox 3.0.10 is broken here.  Was running 8.10 64bit, all was well.  Upgraded.  For those who are belittling the problem, consider that folks without a browser, and not much experience, can't come up here to post, now can they?

Did all the standards;
rebooted
chown in the .mozilla directory
deleted the .mozilla directory
uninstalled firefox
reinstalled firefox
uninstalled firefox and flash
reinstalled firefox and flash
tried running firefox in safe mode

Nothing has worked.  I have Opera on here from a previous install, so I at least have that browser.

All else seems to be fine so far, but admittedly haven't dug too hard.  Thurderbird still works.

Open office still works.  Pidgin works fine.  

I'm sure it will be something querky since it is only impacting a few.  It will take some time to find it, but sure it will work out.

Now, where did I put the book marks?  Got to import my morning reading material (comics). 

Good evening.

Dave 
NM4M

---

### Post by nm4m on 2009-05-01
Just noticed that if I click on the left side of the screen that comes up when I start Firefox, sections of it come up very malformed.

As an example.  Furthest to the left is the File menu.  When I click on the blank screen, all the way to the left, the complete left edge of the window highlights, and a menu goes across the top of the complete gnome screen with the choice for the menu.

This keeps happening, moving left to right for the various menus.  File, Edit, Tools Bookmarks, and so on.  Interesting.  Everything else displays fine, but Firefox is completely borked.  Wild.

Dave 
NM4M

---

### Post by adamlau on 2009-05-02
You can always try my portable 3.0.10 PGO (w/o Java) builds: [http://ubuntuforums.org/showthread.php?t=1137488](http://ubuntuforums.org/showthread.php?t=1137488)

---

### Post by Capt2836 on 2009-05-02
> **Kareeser said:**
> Okay... I'm glad others updated properly. I was hoping that this wouldn't be another "Python-2.6 is borked!"-like occurance :)

Looks like the two cases (mine and the other thread linked) are the only two so far.

May have been because we were both running firefox during the upgrade.

On my system (Asus EeePC1000/Linux running Easy Peasy from SDHC card) the Firefox 3.0.10 update has definitely not gone well.

System runs fine until I try to run Firefox 3.0.10  - then get an alert whilst trying to load Firefox, home page does not load correctly (but is OK when press "Home" icon). After this, various systems will not work - Update Manager hangs whilst loading, Terminal will not load, Synaptic will not load, "File Manager" will not load various folders (File System etc).

I cannot remember whether Firefox was running or not, but suspect that it was not as I am also a Windows suffer and thus well used to shutting everything possible before upgrading!

---

### Post by nm4m on 2009-05-02
I need to find out how to load a previous version of firefox.  I need to get it back online.  

Thanks

Dave
NM4M

---

### Post by Kareeser on 2009-05-02
nm4m, have you tried uninstalling firefox completely?

```
sudo apt-get purge firefox-3.0
sudo apt-get install firefox-3.0
```

Note that the package is "firefox-3.0", NOT "firefox", that is only the meta-package.

---

### Post by nm4m on 2009-05-02
Interesting stuff.  Thanks much for suggesting it.  I played with it quite a bit.  Purging and reinstalling.  At one point got an error about realplayer, in the terminal window, concerning plugin.  I then went through and manually removed all of the realplayer files throughout the computer (locate realplay, delete all the files in the list manually, then sudo updatedb, and locate realplay and nothing showed up).

But still get a blank screen.  It has to be something with my display and the new firefox.  I can click on parts of the window when firefox is open and it shows the listing of the menus across the top of the whole gnome desktop.  But I can never see anything inside the frame of the firefox window.

Been playing with Linux for a long time, and haven't seen anything like this. 

Thanks for the shot though.

Dave 
NM4M

---

### Post by visionaire on 2009-05-03
No problem for me,i'm in Hardy

---

### Post by hotweiss on 2009-05-03
3.0.10 is working for me perfectly. 3.0.09 was causing my system to freeze.

---

### Post by nm4m on 2009-05-05
Seems to be some problems out there.  None of these were a fix for me.

[https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/360923](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/360923)

Dave
NM4M

---

### Post by XubuRoxMySox on 2009-05-05
Small issue... my ScribeFire add-on won't work. But other than that no problems.

---

### Post by skiffler on 2009-05-06
I too have a problem with 3.0.10. I upgraded (online) from 8.04 to 9.04 (via 8.10). Firefox generally fine until I click on any streaming media (anything on the BBC site for instance). It starts streaming video but there is no sound and then, after about 20 secs Firefox closes itself. I've purged and reinstalled but nothing changes. I'm no Linux expert unfortunately but had no problems prior to Jaunty upgrade. Something's happened somewhere.

---

### Post by skiffler on 2009-05-06
Interesting...

I noticed that Epiphany came as part of Jaunty. I launched it, went to the BBC site and tried to play some streaming video and after a few seconds that too closed, so it seems that the problem is not to do with Firefox at all, but is a more deep routed problem. Before heading off elsewhere, would anyone have any ideas of where to start looking?

---

