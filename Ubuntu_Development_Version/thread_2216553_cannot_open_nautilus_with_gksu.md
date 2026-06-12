---
title: "cannot open nautilus with gksu"
date: 2014-04-12
forum: Ubuntu Development Version
---

### Post by ventrical on 2014-04-12
Opening nautilus with gksu gives error:

```

ventrical@ventrical-MS-7798:~$ gksu nautilus

(nautilus:2363): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))
ventrical@ventrical-MS-7798:~$ 

```

Also will not open in root.

(on two boxes so far)

---

### Post by ventrical on 2014-04-12
I went to a trusty install that hasn't been updated of about three weeks and root is working just fine. This is a major bug this late in the cycle!!  What would I file the bug against (not being able to use root, nautilus.. etc ?? )

---

### Post by coffeecat on 2014-04-12
You might want to delay that bug report, at least until some others have commented. gksu nautilus is working just fine in my Trusty system, fully updated only a few hours ago. If I sudo -i in a terminal I can open a root nautilus as well, albeit with a bit of system grumbling about being unable to open usershare directory /var/lib/samba/usershares.

---

### Post by pfeiffep on 2014-04-12
+1> **coffeecat said:**
> You might want to delay that bug report, at least until some others have commented. gksu nautilus is working just fine in my Trusty system, fully updated only a few hours ago. If I sudo -i in a terminal I can open a root nautilus as well, albeit with a bit of system grumbling about being unable to open usershare directory /var/lib/samba/usershares.

My Dell laptop launches _**gksu nautilus**_ just fine.
> pfeiffep@Pete-dell:~$ uname -a
Linux Pete-dell 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
pfeiffep@Pete-dell:~$ 
pfeiffep@Pete-dell:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04 LTS
Release:    14.04
Codename:    trusty


---

### Post by grahammechanical on 2014-04-12
It is working fine here. I had to install gksu to test it. I have had this trusty running for months and I thought that I had already installed gksu. May be not.

Regards.

---

### Post by rrnbtter on 2014-04-12
Greetings,
No issue here with two systems. Right or wrong, I've never used gksu, I  use sudo nautilus, but both work fine. I do get the system grumbles with  sudo however.

---

### Post by ventrical on 2014-04-12
Just updated these :

```

The following packages will be upgraded:
  libc-bin libc-dev-bin libc6 libc6-dbg libc6-dev multiarch-support
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 11.3 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y

```

and now it's working (on one of the affected machines).

  I am not sure what solved it but I'll mark the thread as solved .

---

### Post by ventrical on 2014-04-12
Hey .. thanks all of you for chiming in , Much appreciated.

---

### Post by QDR06VV9 on 2014-04-12
> **ventrical said:**
> Hey .. thanks all of you for chiming in , Much appreciated.
I was faced with yesterday also.
BUt what worked for me was."sudo -i" and then "nautilus"
After that works as advertised.

---

### Post by pfeiffep on 2014-04-12
When I booted my 64 bit HP desktop pc apport reported that Nautilus failed and a report would be sent.

Where (what directory) is the data located on my pc that was sent? I suspect this was a one off (since a reboot didn't reproduce the symptoms.
I really want to investigate further.

gksu nautilus is working also

---

### Post by grahammechanical on 2014-04-12
> [COLOR=#000000]apport reported that Nautilus failed and a report would be sent.[/COLOR]

Apport is enabled by default in development versions. I doubt very much that Apport would send a report with out our agreement. We have to confirm that the crash should be reported and we usually get a warning that some of the logs may contain stuff like passwords. We have to accept this contain, only then, as I understand it does Apport login to Launchpad and give us the opportunity to report a bug.

Regards.

---

### Post by pfeiffep on 2014-04-12
I did agree - and I found **/var/crash/_usr_bin_nautilus.0.crash** which contained
> Title: nautilus crashed with SIGABRT in g_assertion_message()
UpgradeStatus: No upgrade log present (probably fresh install)
_MarkForUpload: True

I did 'approve' the send, however it was dead ended - nothing launched in Launchpad.

---

### Post by mc4man on 2014-04-12
> **pfeiffep said:**
> I did agree - and I found **/var/crash/_usr_bin_nautilus.0.crash** which contained

I did 'approve' the send, however it was dead ended - nothing launched in Launchpad.

One of the more useful things to do when using dev versions is to ck. the changelogs, in the case of latest apport - 
> apport (2.14.1-0ubuntu2) trusty; urgency=medium

  * etc/apport/crashdb.conf: Disable Launchpad crash/kernel reports for
    the final release. Only report to [http://errors.ubuntu.com](http://errors.ubuntu.com) from now on.

---

### Post by Cavsfan on 2014-04-13
Everything working great here! Not even a warning in terminal with "gksu nautilus". System all up to date.
I'm impressed. :)

---

### Post by QDR06VV9 on 2014-04-14
Here it is again after full updates.
```
 gksu gedit

** (gksu:26771): CRITICAL **: fcntl error

** (gksu:26771): WARNING **: Lock taken by pid: -1. Exiting.
me@me-Aspire-M3300:~$ gksu nautilus

** (gksu:26773): CRITICAL **: fcntl error

** (gksu:26773): WARNING **: Lock taken by pid: -1. Exiting.
```
So have we determined if this is a bug?

---

### Post by Cavsfan on 2014-04-14
> **runrickus said:**
> Here it is again after full updates.
```
 gksu gedit

** (gksu:26771): CRITICAL **: fcntl error

** (gksu:26771): WARNING **: Lock taken by pid: -1. Exiting.
me@me-Aspire-M3300:~$ gksu nautilus

** (gksu:26773): CRITICAL **: fcntl error

** (gksu:26773): WARNING **: Lock taken by pid: -1. Exiting.
```
So have we determined if this is a bug?

I get no errors with either one:

```
cavsfan@cavsfan-MS-7529:~$ gksu nautilus
^C
cavsfan@cavsfan-MS-7529:~$ gksu gedit
cavsfan@cavsfan-MS-7529:~$ 

```

---

### Post by QDR06VV9 on 2014-04-14
> **Cavsfan said:**
> I get no errors with either one:

```
cavsfan@cavsfan-MS-7529:~$ gksu nautilus
^C
cavsfan@cavsfan-MS-7529:~$ gksu gedit
cavsfan@cavsfan-MS-7529:~$ 

```
This is going on two machines as of now acer 5750 Intel
And Acer tower M3300 Nvidia:confused:
Past couple of days I've been thinking it is hardware related!

---

### Post by QDR06VV9 on 2014-04-14
So this is the strangest thing I have seen to date!:confused:
I took the hard drive out of the acer laptop and plugged it in to a Lenovo B-570
And it works correctly(gksu gedit or gksu nautilus). My question Why?
Have not tried the tower hard drive yet but I suspect the same results.

---

### Post by QDR06VV9 on 2014-04-14
And then replaced the hard dive back to accer 5750 intell i3 Quad core,
Bear in mind this was the machine the install was done on.
And back to fail opening anything using the gksu command.
Have two other hardives(for this lappy) with other OS's installed that just sing perfectly.
Sounds Buggy to me.
I have seen this error "WARNING **: Lock taken by pid: -1 Exiting" Before but never using those gksu commands

---

### Post by Cavsfan on 2014-04-14
That is indeed ironic and strange! I remember the last time I used **gksudo gedit** before I seen this thread I got a bunch of warnings in terminal.

But no output whatsoever in terminal now. :confused: I'm not usually the one without problems.

---

### Post by QDR06VV9 on 2014-04-14
> **Cavsfan said:**
> That is indeed ironic and strange! I remember the last time I used **gksudo gedit** before I seen this thread I got a bunch of warnings in terminal.

But no output whatsoever in terminal now. :confused: I'm not usually the one without problems.
I have always seen those errors due to themes or icons Using the sudo command!:D
But I guess it is my turn this time for the problems>LOL
Thats Ok my shoulders are broad.;)

---

### Post by Cavsfan on 2014-04-14
> **runrickus said:**
> I have always seen those errors due to themes or icons Using the sudo command!:D
But I guess it is my turn this time for the problems>LOL
Thats Ok my shoulders are broad.;)

Good thing lol!

They are the same or one would logically think they were since they are symlinked. ;)

```
cavsfan@cavsfan-MS-7529:~$ ls -l /usr/bin/gksudo 
lrwxrwxrwx 1 root root 4 Oct  2  2012 [COLOR=#0066cc]/usr/bin/gksudo[/COLOR] -> [COLOR=#009933]gksu[/COLOR]
```

---

### Post by QDR06VV9 on 2014-04-14
Ok that one hurt my head!(not hard to do).:p
But My problem comes from disabling zeitgeist after undoing what I did, and a reboot all is good again!
This thing with Zeitgeist bothers me greatly though. (data gathering):frown:
Seems we live in an age where everybody wants to snoop.

---

### Post by Cavsfan on 2014-04-14
> **runrickus said:**
> Ok that one hurt my head!(not hard to do).:p
But My problem comes from disabling zeitgeist after undoing what I did, and a reboot all is good again!
This thing with Zeitgeist bothers me greatly though. (data gathering):frown:
Seems we live in an age where everybody wants to snoop.

Oh noz! I had no idea about **zeitgeist**. Here I go removing that pesky little critter. 
It's pretty amazing the snooping, I know what you mean. The social networking sites track you whether you have a login to them or not.
I use Disconnect on Chromium and Ghostery on Firefox. Collusion on Chromium also blocks tracking sites.
People have even developed add-ons in Firefox to block the 3 biggest snooping sites. Not sure if I can mention all of them on here or not. 
So, I won't. But it's amazing what Collusion shows how sites feed sites you are not even on after you've done some surfing.

---

### Post by QDR06VV9 on 2014-04-14
> **Cavsfan said:**
> Oh noz! I had no idea about **zeitgeist**. Here I go removing that pesky little critter. 
It's pretty amazing the snooping, I know what you mean. The social networking sites track you whether you have a login to them or not.
I use Disconnect on Chromium and Ghostery on Firefox. Collusion on Chromium also blocks tracking sites.
People have even developed add-ons in Firefox to block the 3 biggest snooping sites. Not sure if I can mention all of them on here or not. 
So, I won't. But it's amazing what Collusion shows how sites feed sites you are not even on after you've done some surfing.
If you are using unity at all removing Zeitgeist will leave you with broken stuff!
I do not use unity  and from raring to trusty my method of disabling or crippling Zeitgeist has not been a problem till a couple of days ago.

---

### Post by cariboo on 2014-04-14
Zeitgeist doesn't phone home with any user information, it's only there to help make it easier for you to repeat an action the you do often. it can be configured in System Settings->Security & Privacy. See [this]("http://en.wikipedia.org/wiki/Zeitgeist_(software)") Wikipedia article. A little bit of paranoia is a good thing, but this is getting ridiculous.

---

### Post by mc4man on 2014-04-15
This has actually been going on for a while on new installs, initally a root nautilus brower will fail with error in orig. post.
(probably dozens of reports about. - 
> ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))
At least here does start working at some point, maybe restarts, maybe something else.

Just did a fresh install (took forever as 04/13 amd64 image was uninstallable due to a policykit/dbus issue
Finally went with 04/14 i386 which did install & see the same deal, gksudo nautilus fails on that error (I also have nautilus-pkexec which also fails.

Got it going after several attempts & restarts though maybe it was running something else successfully with gksudo that did the trick
(in this case gksudo gedit worked, then gksudo nautilus & nautilus-pkexec started working.

---

### Post by QDR06VV9 on 2014-04-15
With all due respect privacy is never ridiculous! Nor would I classify it paranoia.
There are plenty who feel the same. 
Thanks for the info though.
@mc4man Thanks for the comfirmations on the gksu and gksudo.
Regards

---

### Post by Cavsfan on 2014-04-15
So I guess I am fortunate that I have absolutely no problems with gksu or gksudo nautilus/gedit. I think I'll just leave this install as is.

```
cavsfan@cavsfan-MS-7529:~$ ls -ld /var/log/installer | awk '{ print $6 " " $7 " " $8 }'
Mar 10 10:38

```

I have another partition about 40GB I might install Trusty on after final release just because.

Went to reinstall zeitgeist-core and it's already there. I'm pretty sure it jumped back on here by itself. But, from what cariboo907 said I'm not going to worry about it.

I don't use Unity unless I have to so that would not be an issue for me. So I'm good to go. :)

I have been able to stay on Trusty all day and it's acting like an LTS should.

---

### Post by ventrical on 2014-04-15
> **mc4man said:**
> This has actually been going on for a while on new installs, initally a root nautilus brower will fail with error in orig. post.
(probably dozens of reports about. - 

At least here does start working at some point, maybe restarts, maybe something else.

Just did a fresh install (took forever as 04/13 amd64 image was uninstallable due to a policykit/dbus issue
Finally went with 04/14 i386 which did install & see the same deal, gksudo nautilus fails on that error (I also have nautilus-pkexec which also fails.

Got it going after several attempts & restarts though maybe it was running something else successfully with gksudo that did the trick
(in this case gksudo gedit worked, then gksudo nautilus & nautilus-pkexec started working.


 it's working ok , off and on .. and after todays update .. but  then this behaviour fist started I noticed an apport box in the top left hand corner after updates from 3 days ago. Still persistent. I go to report it an it goes nowhere.

Not sure if it has any thing related to original bug.

---

### Post by mc4man on 2014-04-15
> **ventrical said:**
> it's working ok , off and on .. and after todays update .. but  then this behaviour fist started I noticed an apport box in the top left hand corner after updates from 3 days ago. Still persistent. I go to report it an it goes nowhere.

Not sure if it has any thing related to original bug.
Apport reporting to launchpad for crashers has been disabled for 14.04, now they go to some db
This report is a catchall for such issues (it doesn't mention gksudo nautilus but many of the dupes do
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1286766](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1286766)

After being without any ubuntu install for several days now have a 14.04 i386 where as mentioned gksudo nautilus initially failed, now is ok.
If the amd64 image from today will install then I'll start over with that & maybe see exactly what enables it to work again.

---

### Post by ventrical on 2014-04-15
> **mc4man said:**
> Apport reporting to launchpad for crashers has been disabled for 14.04, now they go to some db
This report is a catchall for such issues (it doesn't mention gksudo nautilus but many of the dupes do
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1286766](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1286766)

After being without any ubuntu install for several days now have a 14.04 i386 where as mentioned gksudo nautilus initially failed, now is ok.
If the amd64 image from today will install then I'll start over with that & maybe see exactly what enables it to work again.

 I am not sure if this is of any help but it first started after I tried an experiment to try and drag and drop some executable files from /nautilus/filesystem/firefox/firefox. I was just seeing if I could find a way to past an executable file (shortcut) to the desktop. After doing this it told me the <firefox> link was broken so I deleted it and then tried gksu nautilus and that's when it started to deny access. It's working now though. <amd64> I just did a fresh install i386 on Dell Latitude so I'll check it there too.

---

### Post by ventrical on 2014-04-15
Fresh install from yesterdays 32bit .iso Ubuntu..

gksu nautilus

busted.

```

-Latitude-D810:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1d.0 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV370/M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller
03:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
annadip@annadip-Latitude-D810:~$ 

```

---

### Post by ventrical on 2014-04-15
Seems what solves it is just enter :

sudo nautilus

it will not ask for password but will bring up nautilus... then you can quit and gksu nautilus will work.

---

### Post by cariboo on 2014-04-15
DId you document what you did to break gksu?

---

### Post by ventrical on 2014-04-15
> **cariboo907 said:**
> DId you document what you did to break gksu?

Make  startup USB with SDC from trusty-desktop-i386.iso 2014/04/14.
Install trusty to i386 form factor (this case a Dell Latitiude).
Remove USB pen drive/reboot.
sudo apt-get install synaptic
sudo apt-get update
sudo apt-get dist-upgrade
Use Ubuntu Software Center to download ubuntu-unrestricted-extras
reboot

Login: Ctrl+Alt+t and enter-
gksu nautilus

apt will remind you that gksu is not installed.

sudo apt-get install gksu

gksu nautilus..... authentication window asks for password- Enter PSWD> (at this point  a blank pop-up comes ups then it dies ,window closes, and leaves the usual error message in terminal.) Ctrl +c and exit gksu.

Run:

sudo nautilus

Works beautiful. Close nautilus window. Then:

gksu nautilus

Works as normal .

The scary thing about this  is that after the gksu first fail and then you try 'sudo nautilus' it does not ask for password so I would have to ask if this bug is a security risk.

Regards..

---

### Post by mc4man on 2014-04-15
```
The scary thing about this  is that after the gksu first fail and then you try 'sudo nautilus' it does not ask for password so I would have to ask if this bug is a security risk.
```
If that was the same terminal then you were already authenticated

I think the failure of gksudo nautilus is  likely par for the new install course. I'm going to try once again to get back a 14.04 amd64 install so will see if it occurs there, assuming it does install.
(running sudo nautilus, while not advised, could be ok once or twice. Just make sure that root doesn't own any files in your home directory.

---

### Post by ventrical on 2014-04-15
> **mc4man said:**
> ```
The scary thing about this  is that after the gksu first fail and then you try 'sudo nautilus' it does not ask for password so I would have to ask if this bug is a security risk.
```
If that was the same terminal then you were already authenticated

I think the failure of gksudo nautilus is  likely par for the new install course. I'm going to try once again to get back a 14.04 amd64 install so will see if it occurs there, assuming it does install.
(running sudo nautilus, while not advised, could be ok once or twice. Just make sure that root doesn't own any files in your home directory.


 I assumed this. (already authenticated)

 Also, I understand about the 'sudo nautilus'. Most of my installs are experimental and I understand the risk. Thanks for your reminders:)

---

### Post by ventrical on 2014-04-15
> **mc4man said:**
> ```
The scary thing about this  is that after the gksu first fail and then you try 'sudo nautilus' it does not ask for password so I would have to ask if this bug is a security risk.
```
If that was the same terminal then you were already authenticated

I think the failure of gksudo nautilus is  likely par for the new install course

 I am going to  assume that the 'gksu' program has a bug.

---

### Post by ventrical on 2014-04-15
I just hopped over to another machine .

```

ventrical@ventrical-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82Q963/Q965 HECI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DM Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HO (ICH8DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101/6102 single-port PATA133 interface (rev b1)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22A IEEE-1394a-2000 Controller (PHY/Link) [iOHCI-Lynx]
ventrical@ventrical-desktop:~$ 

```

This is 64bit install and the bug is back there again. I opened terminal, run gksu nautilus a window opens and closes and then:

```

ventrical@ventrical-desktop:~$ gksu nautilus

(nautilus:2061): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))
ventrical@ventrical-desktop:~$ 



```

---

### Post by mc4man on 2014-04-15
Don't think it's gksu, just some nonsense with nautilus 

Fresh 14.04 amd64 install just now.
Installed gksu, ran command, failed
Added my ppa, updated nautilus to a pkexec enabled one, ran gksudo nautilus, failed, ran nautilus-pkexec, failed on same error
Installed dconf-editor, ran command to open root nautilus, failed
Ran dconf-editor thru gksudo, closed dconf-editor
Now nautilus can be opened as root, both gksudo & pkexec work

It's if nautilus can't get a root gui display until some other root gui has be opened (that also would be satisfied with sudo nautilus 
> 
doug@doug-Lenovo-IdeaPad-Y510P:~$ gksudo nautilus

(nautilus:4988): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))
doug@doug-Lenovo-IdeaPad-Y510P:~$ nautilus -q
doug@doug-Lenovo-IdeaPad-Y510P:~$ gksudo nautilus

(nautilus:8091): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))
doug@doug-Lenovo-IdeaPad-Y510P:~$ nautilus-pkexec

(nautilus:8140): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(nautilus:8140): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))
Aborted (core dumped)
doug@doug-Lenovo-IdeaPad-Y510P:~$ gksudo dconf-editor

** (dconf-editor:8159): WARNING **: dconf-schema.vala:330: Unknown property on <schema>, extends
doug@doug-Lenovo-IdeaPad-Y510P:~$ nautilus-pkexec
doug@doug-Lenovo-IdeaPad-Y510P:~$  Working ^

---

### Post by QDR06VV9 on 2014-04-15
> **ventrical said:**
> Make  startup USB with SDC from trusty-desktop-i386.iso 2014/04/14.
Install trusty to i386 form factor (this case a Dell Latitiude).
Remove USB pen drive/reboot.
sudo apt-get install synaptic
sudo apt-get update
sudo apt-get dist-upgrade
Use Ubuntu Software Center to download ubuntu-unrestricted-extras
reboot

Login: Ctrl+Alt+t and enter-
gksu nautilus

apt will remind you that gksu is not installed.

sudo apt-get install gksu

gksu nautilus..... authentication window asks for password- Enter PSWD> (at this point  a blank pop-up comes ups then it dies ,window closes, and leaves the usual error message in terminal.) Ctrl +c and exit gksu.

Run:

sudo nautilus

Works beautiful. Close nautilus window. Then:

gksu nautilus

Works as normal .

The scary thing about this  is that after the gksu first fail and then you try 'sudo nautilus' it does not ask for password so I would have to ask if this bug is a security risk.

Regards..
I'll be watching to see if it sticks for a day or so, At the beginnig of your post i had commented there about "sudo -i" then "nautilus" but it did not stick for me.
I like mc4man's lead on nautilus not consitanly grabing root.

---

### Post by ventrical on 2014-04-15
> **runrickus said:**
> I'll be watching to see if it sticks for a day or so, At the beginnig of your post i had commented there about "sudo -i" then "nautilus" but it did not stick for me.
I like mc4man's lead on nautilus not consitanly grabing root.

I think thats where it is too.

---

### Post by zika on 2014-04-16
Does it work with```
sudo -H
```and does```
rm ~/.gksu.lock
```help?

---

### Post by QDR06VV9 on 2014-04-16
Here is what i get with "sudo -H"
```
usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user]
            [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p
            prompt] [-u user] file ...
me@me-Aspire-M3300:~$ sudo -H nautilus
[sudo] password for me: 

** (nautilus:9501): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

** (nautilus:9501): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

(nautilus:9501): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Initializing nautilus-open-terminal extension


```
Yes the Nautilus opened in root,
 then after "rm ~/.gksu.lock"
I then issued sudo gedit
```
sudo gedit

** (gedit:9699): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

** (gedit:9699): WARNING **: Can't load fallback CSS resource: Failed to import: The resource at '/org/gnome/adwaita/gtk-fallback.css' does not exist

** (gedit:9699): CRITICAL **: file log.c: line 980: unexpected error: Error calling StartServiceByName for org.gnome.zeitgeist.Engine: GDBus.Error:org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /usr/bin/zeitgeist-daemon: Success (g-dbus-error-quark, 23)
^Cme@me-Aspire-M3300:~$ 


```
Complete fail so then i issued "gksu gedit" It was trying to start admin privileges then nothing fails, with nothing in the terminal See Attachment.
Ventrical had this earlier also so I close the terminal via <control+c> 
Then I issued "sudo -i" then "gedit" worked! (second attachment)
There just seems to me like focus is being lost.

---

### Post by ventrical on 2014-04-16
Pretty well the same thing here.  Whats happening is that this bug has become random. It will be there on some hard-boots and disappear on others, both 32bit and 64bit.

```

ventrical@ventrical-desktop:~$ sudo -H nautilus
[sudo] password for ventrical: 

(nautilus:2239): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(nautilus:2239): GLib-GObject-WARNING **: invalid cast from 'GtkMessageDialog' to 'NautilusWindow'
**
ERROR:nautilus-window.c:2116:nautilus_window_get_slots: assertion failed: (NAUTILUS_IS_WINDOW (window))
ventrical@ventrical-desktop:~$ sudo gedit
ventrical@ventrical-desktop:~$ sudo nautilus

(nautilus:2290): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2290): GLib-CRITICAL **: Source ID 114 was not found when attempting to remove it

(nautilus:2290): GLib-CRITICAL **: Source ID 115 was not found when attempting to remove it

(nautilus:2290): GLib-CRITICAL **: Source ID 116 was not found when attempting to remove it
ventrical@ventrical-desktop:~$ gksu nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:2309): GLib-CRITICAL **: Source ID 98 was not found when attempting to remove it

(nautilus:2309): GLib-CRITICAL **: Source ID 100 was not found when attempting to remove it
ventrical@ventrical-desktop:~$ 

```

---

### Post by Cavsfan on 2014-04-17
After installing the final release ISO today I got the errors the first time I entered this but after that first time I got no errors with gksu or gksudo nautilus or gedit.

```
cavsfan@cavsfan-desktop:~$ gksudo gedit /etc/grub.d/05_debian_theme 

(gedit:7039): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```

So, it appears to fix itself after the first time.

EDIT: I take that back I got the error again after saving a text file **gksudo gedit /etc/default/grub**. It was OK until I saved it then it gave the error.

---

### Post by ewlinux on 2014-04-17
Strangest thing. I also had this issu while trying to get nautilus-gksu to work. The thing that solved it for me, was to install "Samba". So now it works to launch nautilus with gksu from terminal, and it also works to open as administrator from the right-click menu. gksu gedit also works fine... Seems to be solved for me.

---

