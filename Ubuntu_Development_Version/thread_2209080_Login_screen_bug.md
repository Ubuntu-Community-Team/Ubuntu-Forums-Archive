---
title: "Login screen bug"
date: 2013-11-29
forum: Ubuntu Development Version
---

### Post by dannymichel on 2013-11-29
For some reason, i can't type when i need to login. It works when i do 'on-screen keyboard.

---

### Post by oldos2er on 2013-11-29
Moved to Ubuntu +1.

---

### Post by grahammechanical on 2013-11-30
It happened to me a day or two ago. I have not tested it today. I am using a previous kernel. On my machine kernel 3.12.0-4 will not accept key entry at login but kernel 3.12.0-3 will accept key entry at log in.

A development cycle or two ago I was able to get a desktop with kernel 3.0.0 but from kernel 3.0.0-1 to kernel 3.0.0-5 I could not get a desktop. This happens sometimes. By the way, I am using Nouveau. I do not know if using a proprietary video driver will make any difference.

Regards.

---

### Post by heir4c on 2013-11-30
Here also the same problem. 
I have a Azerty board (Belgium) and I can not type the password.
But when I click on the icon of the keyboard settings (The US and the BE settings are there) in the top right and I click on the option "BE Belgian" then I can type the password.

(Graphics: AMD APU E--350 , so nothing to do with graphics I think)

---

### Post by grahammechanical on 2013-11-30
> [COLOR=#000000]I click on the option "BE Belgian" then I can type the password.[/COLOR]

That is interesting. I will try that. I think it will only work if the language uses the Latin alphabet. I also have a Greek keyboard layout and I have noticed in the past that if the Greek layout was active when I logged out then the password would not be accepted because it was typed in Greek.

Regards.

Edit: Would you believe it. I rebooted to try out what was suggested and kernel 3.12.0-4 is now accepting keyboard input. Perhaps it is an intermittent issue. We will see.

Edit 2: Yes it is intermittent and yes selecting another layout works.

---

### Post by heir4c on 2013-11-30
Before, I could login but it wont accept my password because of the character 'q' in my password. 
The q on a Belgian layout (latin-be) is on the place of the a on a US layout.
So then I click on the layout-switcher and on BE Belgian and it works (Even it was already selected the BE-layout (The little white ball you see next to the selected layout)).
So, Now I could not type anything in, I had that in mind to solve the problem ( for the moment).

I think it is a bug and it will be solved with updates in the future, I think.

It's like the problem with the Update Manager who gives everytime the message that the update is failed because the internet connection, but if you click OK than he show the downloaded updates and you can do a upgrade.

---

### Post by dannymichel on 2013-11-30
This is officially a bug.

---

### Post by kansasnoob on 2013-11-30
This is also officially pre-alpha :D

But, yes, things are in a borked state right now.

---

### Post by heir4c on 2013-11-30
> **kansasnoob said:**
> This is also officially pre-alpha :D 

That's right, it's still 13.10

---

### Post by kansasnoob on 2013-11-30
> **heir4c said:**
> That's right, it's still 13.10

No, it's not. Where do you get such an idea?

There have been hundreds of updates to Trusty that you won't find in Saucy.

---

### Post by dannymichel on 2013-11-30
The thread is titled 14.04.
I think he may be confused because the splash screen still says 13.10.

---

### Post by heir4c on 2013-11-30
> **kansasnoob said:**
> No, it's not. Where do you get such an idea?

There have been hundreds of updates to Trusty that you won't find in Saucy.
I know that. 
I installed more than ones the daily build of 14.04 in recent weeks. (And in the past al the alfa and betas of the other versions)
So when I use the command:
```
lsb_release -a

```
I see it is 14.04
But when you look at the Systemsettings under "Details" you get 13.10 and also in the login screen you see 13.10.
And in the releaseSchedule you will see that this is not yet the alfa of 14.04.
[https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule](https://wiki.ubuntu.com/TrustyTahr/ReleaseSchedule)
So, "official" it is not 14.04 (for me)
You call it pre-alfa.
I call it 14.04 when the alfa is out. (of course I say that I use 14.04 on fora so people don't think I use 13.10)

---

### Post by mc4man on 2013-12-01
Put a new install on an older machine & saw this behavior on greeter screen, usually unable to type in password box. but only after using one of the gnome-session-flashback sessions

---

### Post by m_yanagisawa on 2013-12-03
Hi, I'm also troubled with similar case.
After installing Ubuntu Trusty Tahr (development branch) from daily build iso image to a desktop , I can't type password in login screen.

My keyboard is Japanese. So when login screen appers after boot, there's the sign of 'Ja' on the upper right corner. When I clicked the 'Ja', it could be changed  into 'En' :English(US). In 'En' I could type password and logged in, so I use Ubuntu Trusty Tahr now.

I don't know what should I report but my enviroments like this.

$ uname -a

Linux UTT 3.12.0-4-generic #12-Ubuntu SMP Tue Nov 26 22:38:40 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

$ locale

LANG=ja_JP.UTF-8
LANGUAGE=ja:en
LC_CTYPE="ja_JP.UTF-8"
LC_NUMERIC=ja_JP.UTF-8
LC_TIME=ja_JP.UTF-8
LC_COLLATE="ja_JP.UTF-8"
LC_MONETARY=ja_JP.UTF-8
LC_MESSAGES="ja_JP.UTF-8"
LC_PAPER=ja_JP.UTF-8
LC_NAME=ja_JP.UTF-8
LC_ADDRESS=ja_JP.UTF-8
LC_TELEPHONE=ja_JP.UTF-8
LC_MEASUREMENT=ja_JP.UTF-8
LC_IDENTIFICATION=ja_JP.UTF-8
LC_ALL=

Best recards


> **heir4c said:**
> Here also the same problem. 
I have a Azerty board (Belgium) and I can not type the password.
But when I click on the icon of the keyboard settings (The US and the BE settings are there) in the top right and I click on the option "BE Belgian" then I can type the password.

(Graphics: AMD APU E--350 , so nothing to do with graphics I think)

---

### Post by heir4c on 2013-12-04
You don't have to change to EN but click just on JA and you can type your password. 
So, I don't change my layout, I just click on the BE (in my login-screen) to confirm and it work.

---

### Post by m_yanagisawa on 2013-12-04
> **heir4c said:**
> You don't have to change to EN but click just on JA and you can type your password. 
So, I don't change my layout, I just click on the BE (in my login-screen) to confirm and it work.

Oh, I see. I was wrong, heir4c
When I click JA then I can type my password without chaning into EN.

By the way,  after log in  and then log off imediately, the next time I can type password without click the keybord sign JA.
Have this happed to anybody else?

---

### Post by philinux on 2013-12-04
Seems to be fixed today. Typed straight in without thinking of this.

Must have been yesterdays updates.

---

### Post by m_yanagisawa on 2013-12-10
Hello again!
I still have the same problem even after recent updates.

If I use ibus-mozc (Google's opensource input method for Japanese) and shutdown or reboot, then next time I can't type any passwords in login windows.
if I use Japanese or English input source then I can type in the next time login.

---

### Post by cariboo on 2013-12-10
I jailed a double post.

---

### Post by rrnbtter on 2013-12-11
Greetings,
I recently had this happen.  My solution: Boot into earlier kernel and run apt-get update && apt-get dist-upgrade. This implies that the fix is in the upgrade, it was for me. Reboot back to normal kernel.

---

### Post by thotz on 2013-12-17
Still this problems with yesterdays image and all updates :(

---

### Post by ventrical on 2013-12-17
> **mc4man said:**
> Put a new install on an older machine & saw this behavior on greeter screen, usually unable to type in password box. but only after using one of the gnome-session-flashback sessions

I installed the xubuntu-desktop yesterday and got these problems also. But works after I go to terminal and:   

sudo service lightdm restart

---

### Post by thotz on 2013-12-17
You just have to click on the time or on another icon on the welcome screen of lightdm and you are able to log in.

Made a bug report: [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1261818](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1261818)

---

### Post by leeper69 on 2013-12-17
its 14.04 I am using kdm and havent run into this but I only use english.  have you tryed opening a new sesion before typing in your password?

---

### Post by grahammechanical on 2013-12-18
It is intermittent. I got this just now and all In needed to do was click on the keyboard layout icon and then I could type in the password field. I run the daily update which required a reboot and at the login screen I could type in the password field as we are supposed to do. It is intermittent.

Regards.

---

### Post by lazaronbh on 2014-01-13
Same problem here. Kernel 3.13, last updated today..

---

### Post by prana on 2014-01-13
Same here. Added a "me too" to the bug report.

---

### Post by ventrical on 2014-01-13
Fixed here on multiple installs across several form factors. :) lol

---

### Post by Bucky Ball on 2014-01-13
> **ventrical said:**
> Fixed here on multiple installs across several form factors. :) lol

That's nice. How???

I can report I have this issue intermittently with 3.13.0-2-generic but not 3.13.0-1-generic. Not sure how this matches with everyone elses' experience ...

I haven't tried the onscreen keyboard fix, but will next time it happens. ;)

* 14.04 LTS minimal install with Xfce4.

---

### Post by ventrical on 2014-01-13
> **Bucky Ball said:**
> That's nice. How???

I can report I have this issue intermittently with 3.13.0-2-generic but not 3.13.0-1-generic. Not sure how this matches with everyone elses' experience ...

I haven't tried the onscreen keyboard fix, but will next time it happens. ;)

On my SandyBridge  I just updated  and it works. Works on nvidia based graphics also. There is one machine that is older intel graphics  based and I am about to check that. On another machine I loaded the Lubuntu alpha and installed ubuntu-desktop on that. Lightdm never worked better although problems may persist radomly .. I'll keep an eye out and report in.

---

### Post by ventrical on 2014-01-13
Ok.. on this one intel based graphics desktop I am still getting the random log-in problem . I still have to hit the Eng icon so I can login (as graham pointed out) but I noticed that  it seems that the startup sequence graphics driver jockey is having problems deciding which driver to use, or are they both basically the same thing?


edit:

ahhhh.. the 64bit/i386 thingy is something that I did. I over-installed a previously 64bit install with a fresh trusty. It kept all my previous screenshots.

 Seem to still be a major bug on some (older) and/or (newer)  machines.

---

### Post by craig10x on 2014-01-13
Yeah..i am still getting the bug on mine too...i have a 1 year old toshiba with i3 core intel and intel graphics...you have to hit En or one of the other buttons on the top panel in order to be able to type into the password field...

---

### Post by ventrical on 2014-01-13
It has become a very deceptive bug. I had thought it was solved on SandyBridge but it's back.

---

### Post by gifford on 2014-01-23
Same issue here with login. Using on screen keyboard seems to work for me. 
Have updated everything so it is still an issue.

---

### Post by prana on 2014-01-23
> **gifford said:**
> Same issue here with login. Using on screen keyboard seems to work for me. 
Have updated everything so it is still an issue.

The bug was recently triaged so it has a good chance of getting fixed by the time 14.04 is released.

[https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1261818](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1261818)

---

### Post by x-shaney-x on 2014-02-20
Two problems, to be precise, not sure if they are related:

1. When the login screen appears, I am unable to type in the password box for any users.
The only way around it has been to login as guest, logout again and then I am able to type in the boxes.

2. I am unable to disable the daft drum roll sound on the login screen.  I need to disable it because it causes my computer to hang for some reason (and has done for several ubuntu versions).
In 13.10 I disabled it by editing /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml and set "play-ready-sound" to "False" but this isn't working in Trusty.

---

### Post by cariboo on 2014-02-20
> **x-shaney-x said:**
> Two problems, to be precise, not sure if they are related:

1. When the login screen appears, I am unable to type in the password box for any users.
The only way around it has been to login as guest, logout again and then I am able to type in the boxes.

This has been covered several times, just click the language selector in the upper right corner

> 2. I am unable to disable the daft drum roll sound on the login screen.  I need to disable it because it causes my computer to hang for some reason (and has done for several ubuntu versions).
In 13.10 I disabled it by editing /usr/share/glib-2.0/schemas/com.canonical.unity-greeter.gschema.xml and set "play-ready-sound" to "False" but this isn't working in Trusty.

---

### Post by grahammechanical on 2014-02-20
As regards item 1 that is an intermittent bug that was noticed some weeks back. I had it for days and then it cleared up for days and then it came back today.

The work around is to double click an app indicator such as the keyboard icon.

As regards item 2 I do not have the login sound. I have never had that at all from the beginning of the Trusty development cycle. Sorry, I cannot help you there.

Regards.

Edit: I have just tested the login screen and I do have the drum roll. Well, I never! It is not something that I notice.

---

### Post by Doug S on 2014-02-20
> **x-shaney-x said:**
> 1. When the login screen appears, I am unable to type in the password box for any users.
The only way around it has been to login as guest, logout again and then I am able to type in the boxes.Quite by accident yesterday I found a [bug report]("https://bugs.launchpad.net/unity/+bug/1278681") about this, if people want to add to "the affects me also thing"

---

### Post by mc4man on 2014-02-21
On my couple of installs this only happens on 1 intermittently. The only real difference is on the install that it never has happened on (over a couple of months), is that on that install I had removed quiet splash $vt_handoff from boot line 
On the affected install i'm going to try removing quiet splash & see if it happens over the course of several days
( no need here for the plymouth splash as it only appears for a couple of seconds in a 9-10 sec boot

---

### Post by Doug S on 2014-02-21
> **mc4man said:**
> On my couple of installs this only happens on 1 intermittently. The only real difference is on the install that it never has happened on (over a couple of months), is that on that install I had removed quiet splash $vt_handoff from boot line 
On the affected install i'm going to try removing quiet splash & see if it happens over the course of several days
( no need here for the plymouth splash as it only appears for a couple of seconds in a 9-10 sec bootFor unrelated reasons, I had removed quiet splash yesterday. For my case it made no difference.

---

### Post by mc4man on 2014-02-21
> **Doug S said:**
> For unrelated reasons, I had removed quiet splash yesterday. For my case it made no difference.

How about the $vt_handoff option?

---

### Post by Doug S on 2014-02-22
> **mc4man said:**
> How about the $vt_handoff option?I did not play around with vt_handoff. I didn't find it in "grub" only in "grub.cfg" and I didn't want to go as far as messing with "grub.cfg", however I will if we think there will value added in such a test.

---

### Post by mc4man on 2014-02-22
> **Doug S said:**
> I did not play around with vt_handoff. I didn't find it in "grub" only in "grub.cfg" and I didn't want to go as far as messing with "grub.cfg", however I will if we think there will value added in such a test.

I don't think so. Here just removing quiet splash from /etc/default/grub & updating grub   then shows a boot line without vt_handoff, whether it actually uses no clue.
On my affected install doing that I haven't gotten the greeter screen where I can't type in password box yet though probably not a long enough test.
(does it happen to you every time or just sporadically? 

The only other thing I did to the install where this has never, ever happened is I adjusted 2 of the templates  to prevent grub from adding gfxmode, though that was to 'fix' a really obscure issue with video display *after* login. Recently that problem has disappeared so I returned the templates to orig. & still haven't seen issue with greeter screen

For reference - 
[http://ubuntuforums.org/showthread.php?t=2189519&p=12856863&viewfull=1#post12856863](http://ubuntuforums.org/showthread.php?t=2189519&p=12856863&viewfull=1#post12856863)

---

### Post by Doug S on 2014-02-22
> **mc4man said:**
> does it happen to you every time or just sporadically?No. All of my 14.04 computers are VM's on my Ubuntu server 12.04 host. I'll cut and paste a note I made on the bug report I referred to a few posts above: For me, and typically, this issue only occurs once per host computer  re-boot and thereafter I can start the guest VM without issue.
Additionally, I would say maybe one in 20 times, and usually after some big update or something, the issue will occur without the host computer having been re-booted.

---

### Post by Burkey on 2014-03-03
Not sure how to report this.. but this morning I updated and now, my login screen keyboard input is disabled until I go and pull down the language menu and click "English(US)" as the input again.

My system is set to Australia location but only has English(US) as the available option anyway, so I am not even changing my language, just clicking the option that is already selected.

Don't know how to identify what update I am on btw.  It is 14.04...

---

### Post by Bucky Ball on 2014-03-03
Yep, known bug which seems fixed for most of us. How long have you been testing 14.04 LTS? If a recent install, suggest you do updates and see if that fixes. I keep all the way up to date as I'm testing, not using this as a stable install, and don't mind breakages, with:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

The problem has gone away here (for about two weeks or more now). Not to say it won't return when I do the next update. Haven't used 14.04 for about five days so when I update I may have the problem again, too. Will report that later this afternoon.

(PS: Also in Australia. ;))

---

### Post by Burkey on 2014-03-03
Hi Bucky, thanks for replying.  This is a new install, just done yesterday from yesterdays "daily" build.  I updated it last night, was ok, updated this morning and the issue has started... so depending if you updated this morning before work, you may or may not regress!

ps: Aussie! Aussie! Aussie!!!

---

### Post by Bucky Ball on 2014-03-03
I'll boot into 14.04 and have a fiddle a bit later and report back ... ;)

But as I say, this issue was there, went away, sounds like it might be back. If it is, I'll see if I can dig up the bug report/thread and supply links. The good news is, it is a known issue and not just you so no doubt will be fixed again pretty soon if it has returned.

---

### Post by Bibek on 2014-03-03
This issue has been persistent with my install. I did an install about a week ago and have been keeping it up to date but the issue still persists. The funny thing now is that sometimes the keyboard works and sometimes it doesn't on the login screen.

---

### Post by Bucky Ball on 2014-03-03
> **Bibek said:**
> The funny thing now is that sometimes the keyboard works and sometimes it doesn't on the login screen.

Exactly. This has been the issue all along. It is unpredictable. :-k

---

### Post by thiebaude on 2014-03-03
Yep, same thing happens to me, its weird but it seems if I wait a few seconds then I can log in,lol

---

### Post by craig10x on 2014-03-03
I've had it all along on my installation of 14.04...you know what it is... when i do Updates and then re-boot, it works...otherwise you always have to click something on the top panel in order to be able to type in the password log in field...
very strange behavior, indeed  :-k

---

### Post by Burkey on 2014-03-03
I actually saw it once on 13.10 but I cannot for the life of me remember what was causing it.  It is however related to the languge/input settings somehow.

Hopefully by raising awareness in threads like this it gets resolved once and for all.

---

### Post by d-cosner on 2014-03-03
Still have the log in bug here too....

---

### Post by x-shaney-x on 2014-03-04
Yep, same here.  It will be ok after one reboot then comes back the following reboot.

---

### Post by mc4man on 2014-03-04
I've got 2  14.04 installs, both put up within the last 2 weeks. The install where grub is configured on never sees this, the other does so intermittently.
This is the same as seen with the  2 prior installs.
(probably has nothing to do with but for whatever reason that's the way it's been for last couple of months..

---

### Post by ventrical on 2014-03-04
nVidia GeForce 210/218 = yes to bug. 
SandyBridge = no to bug.
ATi HD 5450 = yes to bug.

 Looks like it is still random as earlier Intel graphics have this bug too.

---

### Post by Doug S on 2014-03-04
Here is another [thread about]("http://ubuntuforums.org/showthread.php?t=2206782") this.
More importantly, is the [related bug report]("https://bugs.launchpad.net/unity/+bug/1278681"), please click on and add yourself as "effected by this bug report" so the heat will increase.

By the way, on my system behavior with respect to this issue is the same. After a host re-boot, the issue happens once per 14.04 VM guest startup, subsequent re-boots of each VM guest are fine.

For this comment from above:```
Yep, same thing happens to me, its weird but it seems if I wait a few seconds then I can log in,lol
```I waited 10 minutes on a first time logon, it didn't make a difference.

---

### Post by cariboo on 2014-03-04
I found if the cursor is flashing in the password box, it doesn't work, if the cursor doesn't flash it works. I'm using a GeForce 210 here with the nvidia-331 driver.

---

### Post by mc4man on 2014-03-04
> **Doug S said:**
> Here is another [thread about]("http://ubuntuforums.org/showthread.php?t=2206782") this.
More importantly, is the [related bug report]("https://bugs.launchpad.net/unity/+bug/1278681"), please click on and add yourself as "effected by this bug report" so the heat will increase.

Don't think this is a unity bug, possibly unity-greeter

---

### Post by thiebaude on 2014-03-05
When I had the log on screen bug on both desktop and laptop I was still using the older log on screen but ever since I have installed the gtk3 log on screen for both desktop and laptop I don't have that bug anymore.

---

### Post by Krishna_Manohar on 2014-03-06
I have recently upgraded from 13.10 to 14.04. This is the problem I am facing.

Everytime I login, the screen becomes too dark, (is this due to xbacklight I had in my 13.10 ?) and as soon as I increase the brightness to one more point, the brightness gets normal. And after all this, I am unable to enter the password (the cursor hangs and doesn't blink).

I have to suspend and start again to get things normal.
Please note that I am completely updated and upgraded to the latest versions. (confirmed this using software updater application as well as from terminal sudo apt-get update && upgrade)
Please let me know if you have solutions to any of the above problems or if you need anymore information.
Laptop: Lenovo G460 dual booting Ubuntu 14.04 and Win
Thanks, 
KM

---

### Post by deadflowr on 2014-03-06
You suffer from what is describe in this thread
[http://ubuntuforums.org/showthread.php?t=2209080](http://ubuntuforums.org/showthread.php?t=2209080)

---

### Post by monkeybrain20122 on 2014-03-06
After booting into the login screen, try enter password and nothing happens. Cannot type anything into the box. It works after clicking some random icon on the top bar (for example volume)

---

### Post by Doug S on 2014-03-07
Yes, there seems to be approximately one new thread per day on this one.
Please go to the [bug report]("https://bugs.launchpad.net/unity-greeter/+bug/1278681") and click on the "this bug effects me" (are whatever it says) , so that the heat will be turned up.

---

### Post by monkeybrain20122 on 2014-03-07
> **Doug S said:**
> Yes, there seems to be approximately one new thread per day on this one.
Please go to the [bug report]("https://bugs.launchpad.net/unity-greeter/+bug/1278681") and click on the "this bug effects me" (are whatever it says) , so that the heat will be turned up.

Just did.

---

### Post by Krishna_Manohar on 2014-03-07
Thanks. Updating today fixed the problem. Everything is great and fine now.

---

### Post by craig10x on 2014-03-07
Really? I still have it...if you re-booted right after doing updates, it will work for that one time...but try re-booting again and see if you are still able to log in without hitting one of the icons on the top panel...

---

### Post by craig10x on 2014-03-07
Yeah...it's been with us for quite some time...you will probably find it works if you re-boot after doing updates...but then try re-booting again and you will see the problem remains...everyone who notices it should add themselves on the bug by hitting the "this effects me too" as was just mentioned...

---

### Post by HereInOz on 2014-03-07
I have noticed that if you turn on the On-Screen Keyboard, then you are able to type in your password with the computer keyboard.  If you close the On-Screen keyboard, then reboot, the problem is there again.  Turn on the On-Screen keyboard, and the problem goes away.

---

### Post by cariboo on 2014-03-07
Merged similar threads

---

### Post by d-cosner on 2014-03-08
craig10x has described the problem as I am seeing it. For example, after the updated cups packages arrived I could log on normally, after that the problem returned. It must have something to do with services starting.

---

### Post by jaspreet on 2014-03-10
Just installed 14.04 daily build yesterday. Right after the system boots and shows the login screen, I can see the cursor in password field but I am unable to type anything. I tried explicitly clicking the mouse in the password field and typing but not working. Then I did a couple of clicks here and there on the screen, e.g. click on accessibility icon etc. clicked back on the password field and I could type in now. Anybody seen a similar issue?

---

### Post by Iowan on 2014-03-10
Moved to Ubuntu+1

---

### Post by cariboo on 2014-03-10
Merged another one.

---

### Post by Doug S on 2014-03-14
The [bug report]("https://bugs.launchpad.net/unity-greeter/+bug/1278681") has been set to "Fix Released", but for me the behavior is exactly the same (i.e. NOT fixed). If others can confirm/deny, I'll put the bug report back to "confirmed" (if appropriate).

---

### Post by 23dornot23d on 2014-03-14
I had the bug on a initial clean install of the 64 bit tonight ........ but about 20 minutes after the install was completed and I
found I could not type in at the login ........

I updated / upgraded and a new version of lightdm loaded in ........

So I stopped lightdm ........

Re-started the new one and the login worked ok after that .......... so it fixed it for me ......... and I have also
logged fully out and back in again and its still working alright for me now.

---

### Post by Doug S on 2014-03-14
O.K. never mind... The person that set the report to "Fix Released" has set it back to "Confirmed".

@23dornot23d: I do not know about your case, but thanks for chiming in.

---

### Post by 23dornot23d on 2014-03-14
Seems that the login problem is intermitent - as its worked 3 or 4 times on the trot ......

But it did stop working at one point ........ so I stopped lightdm and restarted it again.

---

### Post by forcecore on 2014-03-15
Is this bug similar, i have installed from mini.iso and on both laptop and virtualbox it is same:
1:login screen 2:after entering password it stays that way. Is there a fix?
Edit: guest login is same
edit 2: looks like this is maybe exact bug, what do you think? [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826)

---

### Post by Doug S on 2014-03-15
> **forcecore said:**
> Is this bug similar, i have installed from mini.iso and on both laptop and virtualbox it is same:
1:login screen 2:after entering password it stays that way. Is there a fix?
Edit: guest login is same
edit 2: looks like this is maybe exact bug, what do you think? [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826)I do not think what you are experiencing is the same as this thread has been referring to. I tried to login as "guest" on my computer and did get your 2nd screen shot, for about 2 seconds only though. Your issue does seems similar to that bug report you referenced.

---

### Post by deadflowr on 2014-03-15
> **forcecore said:**
> Is this bug similar, i have installed from mini.iso and on both laptop and virtualbox it is same:
1:login screen 2:after entering password it stays that way. Is there a fix?
Edit: guest login is same
edit 2: looks like this is maybe exact bug, what do you think? [https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826)

Funny enough I helped some one the other day with something like this.
That seems like what happens when the ubuntu.desktop file is missing in /usr/share/xsessions.

You enter your password and it hangs like that because there is no file to read to execute the action.

---

### Post by forcecore on 2014-03-15
What specific package is missing to get it back? or it is just temporary bug?? with 13.10 everything was ok 100%.

---

### Post by Doug S on 2014-03-15
Are you saying you do not have that file? The file is part of the package ubuntu-session. Here is what I get on my computer:```
doug@doug-desktop:~$ [COLOR=#ff0000]ls -l /usr/share/xsessions[/COLOR]
total 20
-rw-r--r-- 1 root root 231 Mar 12 14:18 gnome-classic.desktop
-rw-r--r-- 1 root root 216 Mar 13 17:47 gnome.desktop
-rw-r--r-- 1 root root 279 Mar 11 08:30 gnome-fallback-compiz.desktop
-rw-r--r-- 1 root root 310 Mar 11 08:30 gnome-fallback.desktop
-rw-r--r-- 1 root root 213 Mar 13 17:47 [COLOR=#ff0000]ubuntu.desktop[/COLOR]
doug@doug-desktop:~$ [COLOR=#ff0000]dpkg -S xsessions/ubuntu.desktop[/COLOR]
[COLOR=#ff0000]ubuntu-session[/COLOR]: /usr/share/xsessions/ubuntu.desktop
doug@doug-desktop:~$ [COLOR=#ff0000]dpkg -l | grep ubuntu-session[/COLOR]
ii  [COLOR=#ff0000]ubuntu-session[/COLOR]                                        3.9.90-0ubuntu12                                    all          Ubuntu session
```

---

### Post by deadflowr on 2014-03-15
Historically, it WAS part of gnome-session, but with trusty they now have ubuntu-session.

As Doug S pointed out.

---

### Post by forcecore on 2014-03-15
Thank ou Doug S, ubuntu-session was missing, my issue solved now.

---

### Post by Doug S on 2014-03-15
> **forcecore said:**
> Thank ou Doug S, ubuntu-session was missing, my issue solved now.So, we have to wonder, why was ubuntu-session missing for you? If I understand your first post on this thread, they were fresh installs from the mini iso. I don't know if it will help, but I made an entry on that [bug report]("https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1283826") you referred to.

---

### Post by d-cosner on 2014-03-15
The status on this bug is high now.

---

### Post by gifford on 2014-03-16
I continue to have the problems as well. Updates are done daily but it still persists most of the time. My work around is to right click the login box or to click on the keyboard in the panel.
I did post on this in another thread but it seems this one has superseded it.

---

### Post by craig10x on 2014-03-16
4 weeks to final release and an obvious bug like this is still not fixed yet?  doesn't look like they even have anyone assigned to it... :confused:

---

### Post by d-cosner on 2014-03-16
I have to agree with you my friend. This bug has been around for some time, you would think it would have more priority considering the final release is approaching. Other than this bug 14.04 is awesome!

---

### Post by craig10x on 2014-03-16
Absolutely...in fact, the only bugs i have at this point are that i get the grub screen when i first boot up (even though i am not dual booting) and the log-in screen bug that this thread is about...otherwise, 14.04 is AWESOME and it even fixed the stability problem i mentioned on another thread that i have had with my quad core sandy bridge computers for the last 3 years on ubuntu (with stream radio, you tube videos and playing mp3s)...but that i suspect was fixed with a change in the kernel itself which seems to handle multi core sandy bridge cpu's in a smoother manner...

Looking forward to the release (hopefully by then this bug will be fixed and re-installing will get rid of the grub screen for me)... :D

---

### Post by d-cosner on 2014-03-16
You mentioned the grub screen, are you getting like a purple frame when you first start the system?

---

### Post by craig10x on 2014-03-16
I get the purple colored grub screen (you know, the one you would initially see if you had a dual boot set up and where you would select the system you wanted to enter)...it does the 10 second countdown and then proceeds as normal to the log in (greeter) page...

I didn't have this on my original 14.04 set up...but then i cleaned installed 13.10 and upgraded from it and that's when i started getting this....i think it was around the time that grub was updated on 14.04...
I am hoping when i re-install using the re-upgrade option on the iso when 14.04 is released, that it corrects that...if not, i may do a clean install...grub is not something i like to mess with ;)

---

### Post by d-cosner on 2014-03-17
Got an update this morning for lightdm, was hoping the login bug might be fixed but it only worked one time.... Oh well, maybe next time.

---

### Post by muktupavels on 2014-03-17
I have attached test packages for unity-greeter in this bug report - [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1278681](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1278681).

---

### Post by craig10x on 2014-03-17
I'm surprised that only about 20 or so have reported this bug...i would imagine this affects everyone...or does it not?  Might help if more check in to the report and at least hit the "this affects me too" button...
Though again, i am surprised the developers haven't noticed this and assigned someone to it...unless it affects only a small percentage of us?  
I must say i am a but puzzled about this...

---

### Post by muktupavels on 2014-03-17
Did you test package from that bug report?

Also I there is another bug report - [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1255558](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1255558) and many duplicates.

---

### Post by craig10x on 2014-03-17
Thanks...wasn't aware of all those duplicate bug reports on it...and with all those reports and reporters...still no one assigned...

---

### Post by mc4man on 2014-03-17
> **craig10x said:**
> Thanks...wasn't aware of all those duplicate bug reports on it...and with all those reports and reporters...still no one assigned...
Well if affected then try the .deb attached to the one report & see if it fixes. (there is also a request to merge what is 'in' the attached .deb's
At least here in a fresh install a couple of days ago, while in the first 5 restarts I got the bug 3 times, since then there has been no sign of it so I've no basis to try/comment on the changes.
(now while the bug did stop right after removing quiet splash from boot line & preventing grub from setting a gfxmode likely not related, more likely happenstance.

---

### Post by sdowney717 on 2014-03-17
yeah, that's weird.
been like this most of the time.

right click so copy paste menu shows .

maybe I need to left click the field, but the focus is not on the password field. which is where people will type just like me. And when it does not work get frustrated...

---

### Post by ajgreeny on 2014-03-17
Alternatively you can just click in the language selection icon at top right.

---

### Post by sdowney717 on 2014-03-17
Hi, I just verified a left click wont do it. 
Must right click the password field to type it in.

---

### Post by craig10x on 2014-03-17
that's what this thread has been all about:
[http://ubuntuforums.org/showthread.php?t=2209080](http://ubuntuforums.org/showthread.php?t=2209080)

it's been there for months....over 100 people reported i think but they still don't have anyone assigned to it yet...hope it gets fixed by final release...

---

### Post by sdowney717 on 2014-03-17
If it is not, it is an embarrassing usability bug.
I think they will fix it as it affects all people.

---

### Post by cariboo on 2014-03-17
Merged another one.

---

### Post by Chanath on 2014-03-17
The Lightdm login problem is still there. The only way I can get it working is by right clicking the empty box, and then try to write my password. Sometimes it works with one try , sometimes 2 tries are needed. Would Ubuntu devs ever think of getting rid of this problem?:(

---

### Post by bcschmerker on 2014-03-18
On an eMachines®/Acer® EL1210-09 with both a 600W Shuttle® PSU retrofit and an EVGA® GeForce® 8400 GS™ half-height video display adapter, the Login screen on UbuntuGNOME® 14.01a2 and 14.02b1 has occasionally failed to appear despite X starting during boot.  It appears that having two or more graphics processing units (I have both the planar GeForce® in the nVIDIA® MCP78S chipset plus an nVIDIA® GT218 Rev. 2) is a factor - I actually had to bounce between both GPU's with monitors to get a login screen.  Additionally, the two-GPU problem may be exacerbating known issues with both GNOME® Shell and GNOME® Settings Daemon.  How does one work arund these issues when one is unable to disable the planar GPU?

---

### Post by craig10x on 2014-03-18
You can hit the En button on the top and then close it and that will let you type the password also...yeah, it is kind of embarrassing that over 100 have reported it and no one is even assigned to fixing it...and besides, don't the developers notice it???  Very strange indeed... :shock:

---

### Post by monkeybrain20122 on 2014-03-18
> **craig10x said:**
>  besides, don't the developers notice it???  Very strange indeed... :shock:
Not if they all auto login. :P

---

### Post by muktupavels on 2014-03-18
If you are affected by password bug go to this bug report - [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1278681](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1278681)

1) Download attached .deb from comment #10 or #11
2) Install it **sudo dpkg -i unity-greeter_14.04.4-0ubuntu2_*.deb**
3) Test it and report if that package has fixed bug or not.
4) If you want you can reinstall original package - **sudo apt-get install unity-greeter=14.04.4-0ubuntu1**

The fix is only about removing some code (I think that part simply is not needed and are causing this bug). So when testing pay attention if there is no regressions with test package.

---

### Post by ajgreeny on 2014-03-18
> **albertsmuktupavels said:**
> If you are affected by password bug go to this bug report - [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1278681](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1278681)

1) Download attached .deb from comment #10 or #11
2) Install it **sudo dpkg -i unity-greeter_14.04.4-0ubuntu2_*.deb**
3) Test it and report if that package has fixed bug or not.
4) If you want you can reinstall original package - **sudo apt-get install unity-greeter=14.04.4-0ubuntu1**

The fix is only about removing some code (I think that part simply is not needed and are causing this bug). So when testing pay attention if there is no regressions with test package.
As reported at the launchpad bug, I have installed your updated package on my 64 bit ubuntu in a VirtualBox VM and the problem is solved for me.  The first two times in logged in there was a minor graphic glitch, but that has now disappeared.

Great job!  Many thanks.

---

### Post by ajgreeny on 2014-03-18
In Ubuntu with unity this bug seems now to be solved with an updated package available from the bug report page at [https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1278681](https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1278681) (posts 10 & 11, depending on architecture).

It is all now working great on my machine, as are all the other versions of the *ubuntu family that I've tried.

---

### Post by craig10x on 2014-03-18
Someone mentioned in the other thread on this bug that it has been triaged...so it probably will get fixed through the normal channels by release...
@monkeybrain20122: hmmm...good point ;) that's true...but by now i think they must be well aware of it from all the reports and the huge quantity of reporters...

---

### Post by philinux on 2014-03-18
Seems fixed here. Just had a major upgrade of 230 mbs. I've not update this laptop for a couple of days.

All running smooth.

---

### Post by craig10x on 2014-03-18
@philinux: well, one of the weird quirks about the bug is that the log in usually works if you re-boot right after doing updates...but just for that one time...try re-booting a few times and see if it continues to work...that's the best way to check... ;)

I also had those upgrade/updates this morning, but other then the initial re-boot, it still isn't fixed here (i tried re-booting again)...

---

### Post by cariboo on 2014-03-18
I've merged threads again. Can we please keep the discussion of this problem down to one thread.

---

### Post by Doug S on 2014-03-18
Installing the .deb from post [#10]("https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1278681/comments/10") of the [bug report]("https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1278681") resolves this issue for me. I tested it before and after several times on two computers. Everything was up to date before the .deb was applied and the issue persisted until the .deb was installed.

---

### Post by sdowney717 on 2014-03-18
I cant just click and install. Has to be done in terminal?

---

### Post by sdowney717 on 2014-03-18
Does install this way

```
scott@scott-P5QC:~/Downloads$ sudo dpkg -i unity-greeter_14.04.4-0ubuntu2_amd64.deb
[sudo] password for scott: 
(Reading database ... 375769 files and directories currently installed.)
Preparing to unpack unity-greeter_14.04.4-0ubuntu2_amd64.deb ...
Unpacking unity-greeter (14.04.4-0ubuntu2) over (14.04.4-0ubuntu1) ...
Setting up unity-greeter (14.04.4-0ubuntu2) ...
Processing triggers for libglib2.0-0:amd64 (2.39.91-0ubuntu3) ...
Processing triggers for man-db (2.6.6-1) ...
scott@scott-P5QC:~/Downloads$ 

```

---

### Post by ajgreeny on 2014-03-19
And I installed it with gdebi, one of the packages that I always add to my *ubuntu installations; it makes life very easy with just a double click on the .deb packages, is much smaller than the software centre, which I never use, much preferring synaptic, and sorts out dependencies for me very quickly.

---

### Post by d-cosner on 2014-03-21
I think an update has fixed the greeter! I have rebooted 3 times since the update and have been able to log on normally.

---

### Post by craig10x on 2014-03-21
@d-cosner: don, was it today's updates?...i still have the bug but haven't run my morning's updates yet...if so, i will have to try re-booting a few times after i get today's batch...

---

### Post by craig10x on 2014-03-21
Update: yes i believe don is right...there was an update for "unity greeter" in this morning's updates and afterwards, i re-booted several times (you could never tell from the first re-boot after updates because it always worked then but not after that) and i have no trouble typing in my password without resorting to the "trick" we were using...

So, looks like it was fixed today...everyone should check it out :D

---

### Post by Mateusz Stachowski on 2014-03-21
Yes this should be fixed now.

> unity-greeter (14.04.5-0ubuntu1) trusty; urgency=medium

  * New upstream release:
    - Don't focus windows that set override-redirect. This was causing a
      gnome-screensaver window to get focus when it shouldn't. (LP: [#1255558]("https://bugs.launchpad.net/ubuntu/+source/unity-greeter/+bug/1255558")) 

---

### Post by gifford on 2014-03-23
Has now been working for me after updates and several reboots and start ups.

---

