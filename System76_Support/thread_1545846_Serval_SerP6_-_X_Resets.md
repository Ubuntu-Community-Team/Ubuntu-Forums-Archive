---
title: "Serval SerP6 - X Resets"
date: 2010-08-04
forum: System76 Support
---

### Post by isantop on 2010-08-04
Some users have reported X Resets after reinstalling Ubuntu on SerP6 Serval Professionals. This is caused by a limitation of the Proprietary Nvidia Driver. To remedy this problem:

[LIST]
[*]Go to System > Admin > Hardware Driver and disable the nVidia driver -- if it's installed. Do not reboot the machine. Close System > Admin > Hardware Drivers.

[*]Goto System > Administration > Software Sources and open the "Other Software" tab. 

[*]Click on Add,  then paste the following into the "APT line" field: ```
ppa:ubuntu-x-swat/x-updates
```  And click Add Source. Close Softare Sources and choose "Reload" when prompted.

[*]Now go back to System > Administration > Hardware Drivers. Re-enable the nVidia driver.

[*]Reboot your machine.
[/LIST]



EDIT: It has been brought to my attention that certain other Nvidia Machine may benefit from this fix. If your machine has an Nvidia GPU, I'd try it out. You may also need to reboot after trying this.

---

### Post by bk7777` on 2010-08-08
I have been working and trouble shooting my Lepard system as it relates to lockups.  The OS has been reloaded multiable times and we left it running without the nvidia driver for days and the system seemed to be solid and doing what I want with exception of some of the desktop screen functions.
 
I decided to call system76 and they made me aware of this thread and I installed as stated above.  However the system locks up again.
 
It installed fine however I did not have the NVidia driver already installed.  The thread did not make reference if that was required.
 
I tried to install the nvidia driver after the fact but it now fails to install and again the system is locking up.
 
Assuming the nvidia driver should have been installed prior to this patch.  I need a step by step procedure on how to remove the patch, reinstall the nvidia driver and the patch again.
 
Thanks,
Brian
 
P.S.  What do I have to do to get the system76 driver install back?  It has been missing since the 1st reload of the OS.

---

### Post by thomasaaron on 2010-08-09
I've modified the instructions a little. Try them that way.

---

### Post by bk7777` on 2010-08-10
Tom,  I did exactly as you stated between the e-mails and this forum.  once finished and rebooted system locked up within 10 min.
 
I have attached the log.tar file for your review.  It was created right after the crash.  Like I stated above uptime was about 10 min.
 
Now let me state for the record.  The best experence I have had to date with the system would stay up for days was with no nvidia driver.
 
I have been watching DVDs, mkv, full 1080/24P m2ts files with no nvidia driver and having no issues.
 
with the nvidia driver loaded it has locked up closing miro.  coming out of screen saver many times, twice watching .avi files and when there is a lot if network traffic like moving files between computers over wired network.
 
I get worried and feel the system may not be 100% due to so many lock ups requiring hard power offs.  I would like to run some integrity checks.  OS as well as hardware.  Looking for recomendations on what do use for hardware checking.  I tried Grub to do memory test and get an error message. (did not write it down).
 
Is there a hard drive integrity test?  
How about OS file checking with checksums.
 
I am prepared to run the system thru full diags as required.
 
Thanks,
Brian

---

### Post by thomasaaron on 2010-08-10
If you don't mind, let's handle this either through email or through the forums. Doesn't matter to me which.

All of my help is on vacation this week, and I'd like to be as efficient as possible.

Please go to System > Preferences > Appearance > Visual Effects, and select None. Let's see if you still have resets with that configuration.

---

### Post by bk7777` on 2010-08-14
Tom,
 
I have posted a new thread titled "[[COLOR=#000000]It's offical my Leopard Extreme is a lemon[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1552742")"  I have also left you a voice mail and will be sending out e-mails to you all at S76 before you get back on Monday.
 
My problem at least for the moment is not the NVIDIA driver as you will see in the post.
 
Thanks,
Brian
 
](*,)

---

### Post by thomasaaron on 2010-08-16
Replied to your email this morning. Sounds less like a lemon and more like a loose memory card... possibly a bad memory card.

---

### Post by BillD1 on 2010-08-21
isantop,

I've had my SerP6 for about a month now and frequently experience what is probably the X server reset you mention in this thread. I'm at the desktop and get dumped briefly to a black screen and then to the login screen. This occurs quite frequently. Less frequent is a locked up condition with occasional flicker on the display.

When you mention disabling the Nvidia driver, the Hardware Drivers dialog indicates the Nvidia accelerated graphics driver (version current) is being used. I have some questions:

1) Your initial post indicates this problem occurs after reinstalling Ubuntu. Can this problem occur without reinstalling Ubuntu? I have not reinstalled it.

2) Is disabling the driver achieved by clicking the Remove button? I'm being cautious about 'remove' and 'disable'.

3) Are the two problems I describe caused by the Nvidia driver issue?

---

### Post by PabloH on 2010-08-22
> **BillD1 said:**
> isantop,

I've had my SerP6 for about a month now and frequently experience what is probably the X server reset you mention in this thread. I'm at the desktop and get dumped briefly to a black screen and then to the login screen. This occurs quite frequently. Less frequent is a locked up condition with occasional flicker on the display.

When you mention disabling the Nvidia driver, the Hardware Drivers dialog indicates the Nvidia accelerated graphics driver (version current) is being used. I have some questions:

1) Your initial post indicates this problem occurs after reinstalling Ubuntu. Can this problem occur without reinstalling Ubuntu? I have not reinstalled it.

2) Is disabling the driver achieved by clicking the Remove button? I'm being cautious about 'remove' and 'disable'.

3) Are the two problems I describe caused by the Nvidia driver issue?

If you want to work around the x-reset without uninstalling the driver: Login for the first time after booting and immediately log back out. Then log back in again. No more resets.

---

### Post by isantop on 2010-08-23
Those are some excellent questions. My answers are below:

> **BillD1 said:**
> 1) Your initial post indicates this problem occurs after reinstalling Ubuntu. Can this problem occur without reinstalling Ubuntu? I have not reinstalled it.

2) Is disabling the driver achieved by clicking the Remove button? I'm being cautious about 'remove' and 'disable'.

3) Are the two problems I describe caused by the Nvidia driver issue?

1) I've never seen it happen without reinstalling Ubuntu, but it is possible.

2) Yes, to disable the driver, you use the "Remove" button. Once you do, the open source driver will take over, so you will not lose your graphics.

3) I can't be sure without more information, but it does sound like it. I'd go ahead and try the fix, as performing it shouldn't hurt the system at all.

---

### Post by BillD1 on 2010-08-24
I've gone through the Nvidia driver removal and re-installation shown at the top of this thread. I'll report back if this improves stability.

BTW, when I said I have not re-installed Ubuntu, I realized later that I did install Kubuntu. That caused nothing but trouble with the Nvidia driver. On boot it would fail to load. A low (very low) resolution desktop  would result. I carefully undid the Kubuntu install, package by package. I don't remember the reset problem before the Kubuntu experiment, but I hadn't had my serval very long when I loaded Kubuntu. Maybe that round trip caused a problem.


Well, it's been a few days since I removed and then re-installed the Nvidia driver. So far, so good. No X server resets or lockups. I've even spent a fair amount of time in Firefox playing an online MMORPG game that almost always resulted in a reset. No problems occurred.

---

### Post by jamiekrug on 2010-08-25
I've followed the instructions at the top of this thread for my brand new SerP6, but had an X reset shortly after rebooting. I have the base Ubuntu 10.04 64-bit install, as it arrived from System76.

My NVIDIA X Server Settings shows NVIDIA Driver Version 256.44.

Any other ideas would be much appreciated, as this is obviously a quite frustrating situation.

Thanks!

PS: A friend received a SerP6 the same week as me, and has experienced the same problem both before and after the suggested fix at the top of this thread.

---

### Post by crichell on 2010-08-25
Hi Jamie,

We ask if users re-installed Ubuntu because this fix is applied in our manufacturing. Previously, it seemed that only users who re-installed were encountering the issue.

---

### Post by crichell on 2010-08-25
This bug may be the culprit.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772)

Is Firefox being used whenever the crash occurs?

---

### Post by jamiekrug on 2010-08-25
Hi Carl,

Nope, like I said, Ubuntu 10.04 exactly as it was shipped to me. My friend is in the same boat. We've both tried the updated driver from ppa:ubuntu-x-swat/x-updates and we're both still seeing X resets :( Thanks in advance for any other ideas!

---

### Post by jamiekrug on 2010-08-25
Carl: No, Firefox was not being used. I've primarily used Google Chrome, but the last time I had a reset I was just using Terminal (with Chrome open too, I believe).

---

### Post by crichell on 2010-08-25
Jamie: please run this command and tell me if your output is similar.

```
cat /var/log/auth.log | grep FAILED

```

```
Aug 24 15:53:16 system76-pc login[2147]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 24 15:53:18 system76-pc login[2147]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 24 15:53:22 system76-pc login[2147]: FAILED LOGIN (3) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 24 15:53:24 system76-pc login[2147]: FAILED LOGIN (4) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 24 15:53:27 system76-pc login[2147]: FAILED LOGIN (5) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 24 16:37:36 system76-pc login[1303]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 25 11:55:43 system76-pc login[1306]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 25 11:55:46 system76-pc login[1306]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 11:55:49 system76-pc login[1306]: FAILED LOGIN (3) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 11:55:53 system76-pc login[1306]: FAILED LOGIN (4) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 11:55:56 system76-pc login[1306]: FAILED LOGIN (5) on '/dev/tty2' FOR 'UNKNOWN', Error in service module

```

Notice the failed login is on /dev/tty2

The date and time appear to coincide with the crash. I'm anxiously awaiting another crash now :-).

Your "Enter" key pattern tipped me off.

[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/529230](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/529230)

---

### Post by crichell on 2010-08-25
I can confirm. A crash that just occurred and the following errors are reported in auth.log.

```
Aug 25 16:18:32 system76-laptop login[2277]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 25 16:18:36 system76-laptop login[2277]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 16:18:39 system76-laptop login[2277]: FAILED LOGIN (3) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 16:18:42 system76-laptop login[2277]: FAILED LOGIN (4) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 16:18:45 system76-laptop login[2277]: FAILED LOGIN (5) on '/dev/tty2' FOR 'UNKNOWN', Error in service module

```

After logging in again gdm is moved to vt8.

---

### Post by jamiekrug on 2010-08-25
Here's my output:

```
$ cat /var/log/auth.log | grep FAILED
Aug 23 11:08:17 jkrug-serval login[2168]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 23 11:08:20 jkrug-serval login[2168]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 23 11:08:23 jkrug-serval login[2168]: FAILED LOGIN (3) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 23 11:08:25 jkrug-serval login[2168]: FAILED LOGIN (4) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 23 11:08:28 jkrug-serval login[2168]: FAILED LOGIN (5) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 23 20:47:33 jkrug-serval login[2563]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 25 10:17:38 jkrug-serval login[2864]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 25 10:17:42 jkrug-serval login[2864]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 10:17:45 jkrug-serval login[2864]: FAILED LOGIN (3) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 10:17:48 jkrug-serval login[2864]: FAILED LOGIN (4) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 10:17:51 jkrug-serval login[2864]: FAILED LOGIN (5) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
```

---

### Post by PabloH on 2010-08-26
> **crichell said:**
> I can confirm. A crash that just occurred and the following errors are reported in auth.log.

```
Aug 25 16:18:32 system76-laptop login[2277]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 25 16:18:36 system76-laptop login[2277]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 16:18:39 system76-laptop login[2277]: FAILED LOGIN (3) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 16:18:42 system76-laptop login[2277]: FAILED LOGIN (4) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 25 16:18:45 system76-laptop login[2277]: FAILED LOGIN (5) on '/dev/tty2' FOR 'UNKNOWN', Error in service module

```

After logging in again gdm is moved to vt8.

Interesting, it would explain why I never get the x-reset crash since I started logging in, immediately logging out and then logging back in again every time I start/reboot the computer.

---

### Post by crichell on 2010-08-26
I think we have found the problem and the solution. In our manufacturing image we are adjusting grub so that the Plymouth splash screen looks nicer when you boot your laptop. This adjustment causes GDM to start on vt2. Please follow these directions to reverse our grub add-in and report your result.

From a terminal run:

```
gksu gedit /etc/default/grub &

```

Find the portion that reads:

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
GRUB_GFXMODE=1024x768
GRUB_GFXPAYLOAD_LINUX=1024x768
```

Change it to:

```
# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480
#GRUB_GFXMODE=1024x768
#GRUB_GFXPAYLOAD_LINUX=1024x768
```

Save and close. Then from a terminal run:

```
sudo update-grub
```

Reboot and that's it! Please let us know your results.

---

### Post by jamiekrug on 2010-08-26
Carl,

I've applied these changes and will report back if I see another X reset. However, I'd also like to point out that the last command in your message is slightly off.

Change this:

```
sudo grub-update
```

To this:

```
sudo update-grub
```

This does make sense, as the bug reported is related to Plymouth. I was just about to try to find a generic/base version of /etc/grub/default just as a shot in the dark ;-) Here's hoping! Thanks!

---

### Post by jamiekrug on 2010-08-26
I'm sorry to say that the changes to /etc/default/grub (and update-grub) did not help. I had an X reset just a few minutes after my next reboot. Once again, both resets tonight occurred when I pressed the Enter key again.

Here's my [FONT="Courier New"]`cat /var/log/auth.log | grep FAILED`[/FONT] results for today:

```
Aug 26 20:26:24 jkrug-serval login[2978]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 26 20:26:59 jkrug-serval login[2978]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 26 20:27:03 jkrug-serval login[2978]: FAILED LOGIN (3) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 26 20:27:06 jkrug-serval login[2978]: FAILED LOGIN (4) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 26 20:53:16 jkrug-serval login[2735]: FAILED LOGIN (1) on '/dev/tty2' FOR 'UNKNOWN', Authentication failure
Aug 26 20:53:18 jkrug-serval login[2735]: FAILED LOGIN (2) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 26 20:53:22 jkrug-serval login[2735]: FAILED LOGIN (3) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 26 20:53:26 jkrug-serval login[2735]: FAILED LOGIN (4) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
Aug 26 20:53:28 jkrug-serval login[2735]: FAILED LOGIN (5) on '/dev/tty2' FOR 'UNKNOWN', Error in service module
```

Everything after 20:27:06 was after the grub changes and after a complete reboot.

---

### Post by bhegeman on 2010-08-26
I've been suffering the same symptoms as Jamie. Just applied the suggested fix from Carl and no new resets yet. I'll follow up in a day or two, but this looks promising. Thanks!

UPDATE: Like Jamie, no luck with the /etc/default/grub updates -- still getting X resets

---

### Post by jamiekrug on 2010-08-26
I found a grub.ucf-dist file in my /etc/default/ directory, which appears to be the original/default distribution version. I've copied that to /etc/default/grub and ran update-grub again. We'll see if this one works...

UPDATE: No love, X reset shortly after reboot, with distro /etc/default/grub in use.

---

### Post by PabloH on 2010-08-27
Well I just did it. I will let chrome ferment here a bit and then hit enter a bunch of times and see if it happens... 


(Presses enter a bunch of times. X-resets. Logs back in. Restarts Chrome... Restores session.)

Nope no love... x rebooted and I restored chrome. Back to logging out and back in again to keep it from happening. I was thinking it had something to do with Plymouth back before we went down that Nvidia road. I found some related bugs in the pre-release that they said they fixed. I posted about it on an old thread somewhere on this site.

The only time I remember this problem is when I have to restart the machine after an update-- usually I just let it hibernate.

---

### Post by PabloH on 2010-08-27
This bug is similar and Plymouth related (if not the same):

Read all the duplicate bugs and you will see what I mean.

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/532047](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/532047)

From the bug:

*** A temporary workaround is to disable the plymouth-splash upstart job ***

sudo mv /etc/init/plymouth-splash.conf /etc/init/plymouth-splash.conf.disabled

I will try this and see if it works.

---

### Post by PabloH on 2010-08-27
So I did the above. I hit enter for two hours inside chrome, terminal, etc-- no issues. Then I went back to this windows to post about my success... hit enter trying to type out a message to post this... crashed. Used to it happened right away, now it seems to take a bit longer.

---

### Post by DomIncollingo on 2010-08-27
Another solution to the X reset problem is to downgrade the nVidia driver.  I was having regular X resets on my serp6 for several weeks.  So I tried downgrading my nVidia driver from the recommended version to version 173.  Since I downgraded to version 173, I have gone five and a half weeks without an X reset.

---

### Post by crichell on 2010-08-27
Thanks everyone for your feedback. I'm now seeing the same results on our lab Serval. Back to booting on vt2 this morning.

---

### Post by jamiekrug on 2010-08-30
Carl,

Can you explain what "booting on vt2" means? Also, how can I check this prior to an X reset, if possible?

I'm using my Serval laptop on a regular basis as of today (finally found time to sync files from old laptop), and I had a long stretch without a reset. I was going to post this reply, but then finally had another reset :(

Others have mentioned logout/login as a workaround, so I'm hoping I can confirm this via log files? I also hope to find a much more permanent/acceptable fix ;-)

Any big concerns with using the NVIDIA version 173 driver instead of current, as a potential workaround?

Thanks,
Jamie

---

### Post by DomIncollingo on 2010-08-31
Jamie,

I've been using version 173 of the nVidia driver for 6 weeks now.  I thought it solved my problems with the X resets.  But just yesterday, X reset itself!  So I guess it really didn't solve the problem.  But at least it made it almost 6 weeks without an X reset.

Next time I buy a Linux laptop, I think I'll avoid nVidia!

Dom

---

### Post by jamiekrug on 2010-08-31
Dom,

Thanks for that update. Ironically, most folks will tell you not to buy anything but an nVidia card for a Linux machine, as they've historically had the best driver support. I've had great experience with nVidia and Ubuntu for the past 4 years.

Also confusing is the fact that I've been running the nVidia drivers on a Dell Vostro 1510 laptop for a couple years, including on Ubuntu 10.04, 64-bit, since it was released. I've never had an X reset.

What is it about the System76 Serval that is awaking this really annoying bug??? It must be something related to the hardware or a unique configuration. If it was simply an Ubuntu 10.04 and/or nVidia driver issue, I surely would have seen this on my Dell over the past 4 months.

Best,
Jamie

---

### Post by crichell on 2010-09-01
Hi Jamie, sorry it took a while to get back to you.

> 
Can you explain what "booting on vt2" means? Also, how can I check this prior to an X reset, if possible?

By vt I mean Virtual Terminal. So it appears that the issue is Ubuntu starting GNOME on vt2 which then spontaneously logs out and restarts on vt7. GNOME should start on vt7.

To check where GNOME starts press CTRL + ALT + vt# (F1, F2, F3, etc.). If GNOME is on a vt you will see your desktop otherwise you see a text login.

This is a known bug. What's strange is that the bug was fixed in Lucid and seems to have re-surfaced.

---

### Post by jamiekrug on 2010-09-01
Carl,

Thanks for the Ctrl+Alt+F[#] trick. So, here are my results...

Whenever I've done a fresh boot, I logout and then login again, as this seems to be the only dependable workaround for the X resets.

That said, after a logout/login, it seems my X session is running on VT8. When I tried Ctrl+Alt+F7, I saw the following on a text-only screen:

```
(process:516) GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
[OK]
```

tty1 through tty6 give me a text login screen. tty8 (Ctrl+Alt+F8) gets me back to my GNOME session.

Now, after a reboot, without a logout/login, I see the same warning on tty7, but my GNOME session is on tty2, which seems to be what you expected, and when we can expect an X reset :(

Now, regarding this being a known bug, why is this only a problem on my Serval laptop, while my Dell Vostro with the same nVidia drivers on Ubuntu 10.04 64-bit has never had this issue?

Thanks again for any help! I'm SO ready for this issue to disappear :P

---

### Post by jamiekrug on 2010-09-01
GNOME booted to VT1 this time, not VT2. It's been 30 minutes without an X reset, but I'm not sure I want to risk it just to test. I have work to do too ;-)

UPDATE: Yup, X reset shortly after. After logging in again, I'm back on VT8. Still seeing that same error message for VT7, and the expected text login on VT1 through VT6.

---

### Post by jamiekrug on 2010-09-03
FYI, it seems [bug #625239]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/625239") is my best option for this--best I can tell??? So I've posted a summary of my experience there (first post is comment 15).

---

### Post by reid_rsv869 on 2010-10-14
So...I stopped having these resets, certainly a huge improvement since my video card was replaced, and then I've had four in the last week.  ARG.  

I've reviewed the thread but, correct me if I'm wrong, I don't see any resolution.

What's the latest on this bug.

Reid

---

### Post by DomIncollingo on 2010-10-18
Will this problem be resolved with an upgrade to Maverick?  Or will I have to log out and then log back in (following a reboot) for as long as I own the SerP6?  :(

---

### Post by isantop on 2010-10-18
We're not seeing any issues with Maverick's X server on the Serval. All users are clear to upgrade.

We do have a bug report for this one, which does include a fix for Lucid users. The bug report is here: [https://bugs.launchpad.net/system76/+bug/636026](https://bugs.launchpad.net/system76/+bug/636026)

---

