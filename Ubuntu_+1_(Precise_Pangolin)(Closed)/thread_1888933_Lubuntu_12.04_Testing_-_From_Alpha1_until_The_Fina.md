---
title: "Lubuntu 12.04 Testing - From Alpha1 until The Final Release"
date: 2011-11-30
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by amjjawad on 2011-11-30
[COLOR=Red][B][U]Please Note:

[/U][/B]This thread has nothing to do with [this one]("http://ubuntuforums.org/showthread.php?t=1870442"). The other thread for **suggestions and idea**. This one is for _**sharing Testing Results**_ with everyone over here. Please don't get confused.

 [/COLOR]
[CENTER]
[IMG]http://upload.wikimedia.org/wikipedia/commons/thumb/2/27/Lubuntu_logo.svg/320px-Lubuntu_logo.svg.png[/IMG]
[/CENTER]



[LEFT]Hi everyone,

One day or less to go for the first Alpha Release of Lubuntu 12.04.



[U][SIZE=4][B]From Julien Lavergne (Lubuntu Developer)
[/B] [/SIZE][/U]
> Hi,

The 1st Alpha of Lubuntu 12.04 is planned for Thurday. We started the
ISO testing for Alpha 1, so if you want to help, you can join the
testing process :smile:

If you know how to use a virtual machine (Virtualbox) and how to install
Lubuntu, you can help ! :smile: You can follow the steps on this wiki page :
[https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures) .

We uses a new ISO tracker to collect the results : [http://91.189.93.73]("http://91.189.93.73/") .
There are 4 ISOs that you can test : Live CD (Desktop) and Alternate
ISO, both on i386 and amd64. All need to be tested, to be able to
publish an Alpha 1.

To be short, just download the ISO, run it into VirtualBox, check the
testcase on the page of the ISO, and report the result.

You don't need any technical knowledge, and if you have questions, you
can ask on #lubuntu or #ubuntu-testing.

Thanks in advance ! :smile:

Regards,
Julien LavergneI asked him some Qs and here is the answers:

> [QUOTE][COLOR=Blue]I was unable to open this: [http://91.189.93.73]("http://91.189.93.73/")
        Site is blocked by my ISP and anyway it doesn't seem a valid IP         address anyway.[/COLOR]     Ah :sad: but it's temporaly, the site should be available on a real DNS     adress for Alpha 2 (          [http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)).     Still, the ISOs are available in          [http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/)     is people just want to have a look.
    
    > [COLOR=Blue]Another thing: I understand testing in  Virtual Machines         (VirtualBox) is SAFE but will that be the same  as testing on         real installation?[/COLOR]      Not  exactly, because the hardware on the virtual machine is generic.     You  can test many things on a vm, but it's nice to test it also on a      real hardware.
    
    However, for Alpha 1, it's not important to test it on real      hardware. It's still very early in the cycle. It's more critical for      Beta ISO for example.
    
    Regards,[/QUOTE]
_[SIZE=4]**What do I have to do?**[/SIZE]_
ALL what you need to do is follow the instructions on the above Email from Julien and share your feedback and/or your test results with everyone here. This thread will be active from 1st of Dec, 2011 until the final release day (26th of April, 2012).

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule](https://wiki.ubuntu.com/PrecisePangolin/ReleaseSchedule)



[/LEFT]

---

### Post by shiva.n on 2011-11-30
I was trying to help with ISO testing Lubuntu. I got stuck with 64 bit desktop ISO no booting in Virtualbox. It hangs at either Checking battery state or trying to start CUPS. Im sure Im missing something silly, but stuck here for now.

Ubuntu user since Jaunty but first time enthusiastic tester, with quite some spare time in my hands. Help/directions much appreciated.

Cheers

---

### Post by amjjawad on 2011-11-30
> **shiva.n said:**
> I was trying to help with ISO testing Lubuntu. I got stuck with 64 bit desktop ISO no booting in Virtualbox. It hangs at either Checking battery state or trying to start CUPS. Im sure Im missing something silly, but stuck here for now.

Ubuntu user since Jaunty but first time enthusiastic tester, with quite some spare time in my hands. Help/directions much appreciated.

Cheers

Hi,

If you are having problems booting Lubuntu 12.04 (by the way, the Alpha 1 release is not yet available) then I'd suggest:

1- Checking MD5SUM
2- Burn the LiveCD using low speed (4x or 8x) OR try to create LiveUSB using UNetbootin.

For more information about above, check my signature - Lubuntu One Stop thread :)

---

### Post by jerrylamos on 2011-12-01
Alpha 1 CD live O.K.  Tried installing and running: black screen.  No desktop.  Ctrl-Alt-F1 gets command line O.K.

This is Thinkpad T40 runs Lubuntu Pangolin fine as upgraded from Ocelot.  ATI Radeon mobility 7500 I think.

Tried stopping and starting lightdm.  No go on the desktop.

Tried startx, complained it couldn't find fglrx.  It's there, same place as in the upgrade.

Tried nomodeset on linux line at boot.  No help.

Tried apt-get update & apt-get upgrade.  No help.

Looked on the Pangolin forum there's a couple things to try.  Haven't looked at launchpad bugs yet, too late tonight.

Jerry

---

### Post by jerrylamos on 2011-12-02
Alpha 1 new install from daily build, updated, still black screen.
It will run command line from Ctrl-Alt-F1.
No way to report ubuntu-bug because ubuntu-bug depends on a running desktop.  Of course the bug is the desktop doesn't run.
Tried driver "vesa" and driver "ati" no luck. 
ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
It does display briefly the Lubuntu start screen while booting up.
It does display the Lubuntu screen when shutting down.

This is from another partition, an Ocelot install upgraded to precise.

Jerry

---

### Post by cariboo on 2011-12-02
@jerrylamos, you can use apport from the command line. Have a look at this [wiki]("https://help.ubuntu.com/community/ReportingBugs") page, and scroll down to TIps and tricks.

---

### Post by jerrylamos on 2011-12-02
> **cariboo907 said:**
> @jerrylamos, you can use apport from the command line. Have a look at this [wiki]("https://help.ubuntu.com/community/ReportingBugs") page, and scroll down to TIps and tricks.

Followed your pointer and filed bug #899341.  Trying to add comment with attachnment .xsession-errors but launchpad isn't doing "Post Comment".  Oops, xsession-errors is not filed as readable.  Fixed that.  Also sent Xorg.0.log.

Thanks, Jerry

---

### Post by shiva.n on 2011-12-02
Nice one jerrylamos. I wasnt sure if I was doing everything right in Virtualbox. I dont have an extra machine to test this, and am a newbie to Ubuntu testing. So I was holding back on creating a bug.

However I was able to get one good fresh install of Lubuntu 12.04 on a VM. I am not able to reproduce that!

---

### Post by shiva.n on 2011-12-02
Ok I am a bit all over the place with lubuntu now. I had  precise-desktop-amd64.iso from 20111129, which I was trying to use for ISO testing.

Now I was trying to zsync with alpha1, and it errors out. 


shiva@Arrakis:~/Downloads$ zsync [http://cdimage.ubuntu.com/lubuntu/releases/12.04/alpha-1/precise-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.04/alpha-1/precise-desktop-amd64.iso)
-------------------- 0.0% 11.3 kBps         
-------------------- 3.2% 11.3 kBps         TA   
#------------------- 8.7% 7.2 kBps         ETA  
##------------------ 12.6% 10.2 kBps         TA   
#######------------- 35.8% 7.2 kBps         ETA  
#################### 100.0% 366.0 kBps DONE      

Bad line - not a zsync file? "3&#54288;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;3&#65533;&#65533;&#65533;"

---

### Post by cariboo on 2011-12-02
> **shiva.n said:**
> Ok I am a bit all over the place with lubuntu now. I had  precise-desktop-amd64.iso from 20111129, which I was trying to use for ISO testing.

Now I was trying to zsync with alpha1, and it errors out. 


shiva@Arrakis:~/Downloads$ zsync [http://cdimage.ubuntu.com/lubuntu/releases/12.04/alpha-1/precise-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.04/alpha-1/precise-desktop-amd64.iso)
-------------------- 0.0% 11.3 kBps         
-------------------- 3.2% 11.3 kBps         TA   
#------------------- 8.7% 7.2 kBps         ETA  
##------------------ 12.6% 10.2 kBps         TA   
#######------------- 35.8% 7.2 kBps         ETA  
#################### 100.0% 366.0 kBps DONE      

Bad line - not a zsync file? "3&#54288;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;3&#65533;&#65533;&#65533;"

You have to add .zsync to the end of your command eg:

zsync [http://cdimage.ubuntu.com/lubuntu/releases/12.04/alpha-1/precise-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/lubuntu/releases/12.04/alpha-1/precise-desktop-amd64.iso.zsync)

---

### Post by jerrylamos on 2011-12-02
Bryce Harrington looked at the launchpad bug and found xorg was working O.K.  He suspected the window manager - openbox is it for lubuntu?

Downloaded the alternate install version (still fits on one CD) and installed that.  It's working.  If I get energetic I'll try another install of the live CD version to see if it was a fluke or persistent.

Usual lubuntu questions, trying to import bookmarks (I've a couple hundred) from Firefox.  I copyh them from one install to the next into firefox from the .json files.  Chromium doesn't understand bookmarks exported from firefox as far as I can tell?

Somehow Chromium wants me to install Firefox, import my bookmarks, then Chromium can copy them???

All I want is flashplayer, on Firefox a simple copy of libflashplayer.so  into the appropriate plugin folder.  

Ubuntu forums says to use synaptic to get lubuntu-restricted-extras.  That's beem downloading and churning for quite a while!

What happened to the KISS principle?

Jerry

---

### Post by shiva.n on 2011-12-03
Thankyou. I am dumb. Thats my excuse :)

> **cariboo907 said:**
> You have to add .zsync to the end of your command eg:

zsync [http://cdimage.ubuntu.com/lubuntu/releases/12.04/alpha-1/precise-desktop-amd64.iso.zsync](http://cdimage.ubuntu.com/lubuntu/releases/12.04/alpha-1/precise-desktop-amd64.iso.zsync)

---

### Post by shiva.n on 2011-12-03
> **jerrylamos said:**
> Bryce Harrington looked at the launchpad bug and found xorg was working O.K.  He suspected the window manager - openbox is it for lubuntu?

Jerry

Lubuntu uses LXDE. I dont think its got any openbox in it.

If I remember right Crunchbang is the Ubuntu flavor that comes with openbox.

I havent used Lubuntu before, but an very interested in it since Ubuntu with Unity has become too bloated for my liking. So I am keen to get my hands dirty with lubuntu 12.04 testing. But I gotta get to a successful install to begin with I guess!

---

### Post by amjjawad on 2011-12-03
> **shiva.n said:**
> Lubuntu uses LXDE. I dont think its got any openbox in it.

LXDE is the Desktop Environment.
Openbox is the Window Manager.

[http://en.wikipedia.org/wiki/LXDE](http://en.wikipedia.org/wiki/LXDE)
[http://en.wikipedia.org/wiki/Openbox](http://en.wikipedia.org/wiki/Openbox)

[http://en.wikipedia.org/wiki/Lubuntu](http://en.wikipedia.org/wiki/Lubuntu)

---

### Post by jerrylamos on 2011-12-03
Thinkpad T40 lubuntu A1 install from CD live gets "black screen" as noted in my previous comment.    

Bryce Harrington looked at the launchpad bug and concluded xorg was running O.K. He suspects the window manager, I think it's openbox.  

So I downloaded an "alternate" install to a different partition which went O.K. (didn't time it, seemed slow).  Screen works normally.

I'll do an MD5 check on the CD live image and try another install later today hopefully.  Maybe the "black screen" was a fluke although there was no indication of any trouble during the install. 

Jerry

---

### Post by jerrylamos on 2011-12-03
My black screen bug isn't reproducable.  
Installed lubuntu pangolin A1 from alternate.  Worked fine.
On original CD whose install had the problem, checkd CD for defects.  None.
Re-installed lubuntu pangolin A1 from CD Live.  Working fine this time....

With my background going back to Dapper Drake spring 2006 was it, I'm a lot more comfortable with lubuntu than with unity-3D tablet type desktop.  Fancy with lots of functional limitations and very low information density for the amount of real estate used.

Now I did remove chromium, which automatically installed firefox, Saved about 25,520 bytes.  After a number of attempts to use chromium I still find it quite awkward example handling my couple hundred bookmarks.  Chromium can't even read a firefox backup .json file.

Also, firefox flashplayer simply copy in libflashplayer.so into the right plugin folder.  Chromium flashplayer have to install restricted-extras takes quite a while and brings in a bunch of stuff I will never use...

So I'm happy.

Jerry

---

### Post by ranch hand on 2011-12-03
> **shiva.n said:**
> Thankyou. I am dumb. Thats my excuse :)
Good excuses are really hard to get.  When you have a good one hang on to it.

---

### Post by amjjawad on 2011-12-13
My turn now.

Downloaded the daily build (08-12) for 32-bit machines.

Test done on this machine:

Motherboard: Intel Corporation
CPU: Intel(R) Pentium(R) 4 CPU 3.06GHz
Cache: 1MB L2
RAM: 242MB
Graphics: RC410 [Radeon Xpress 200]
HDD: Seagate IDE 80GB
Multimedia: IXP SB4x0 High Definition Audio Controller
Network Adapter: RT2561/RT61 rev B 802.11g

Installed on a Multi-Booting System:

[IMG]http://i40.tinypic.com/qprlv5.jpg[/IMG]

During booting: everything was fine. Try Lubuntu without installation worked without any problems. I booted twice and success is 100% in each tires.

During installation: despite the fact that I'm using low RAM, the Live Session worked. However, I selected "Try without installation" then my PC got disconnected from the power so installed again by choosing "Install" directly.

After installation: simply, it did not work. Black Screen with a loop that I couldn't understand. I've seen some lines but couldn't read anything. However, I was able to access the CLI with Alt+F2

If I'm not mistaken, there is a thread and a bug with the same issue.

---

### Post by amjjawad on 2011-12-13
> **shiva.n said:**
> Ok I am a bit all over the place with lubuntu now. I had  precise-desktop-amd64.iso from 20111129, which I was trying to use for ISO testing.

Now I was trying to zsync with alpha1, and it errors out. 


shiva@Arrakis:~/Downloads$ zsync [http://cdimage.ubuntu.com/lubuntu/releases/12.04/alpha-1/precise-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/releases/12.04/alpha-1/precise-desktop-amd64.iso)
-------------------- 0.0% 11.3 kBps         
-------------------- 3.2% 11.3 kBps         TA   
#------------------- 8.7% 7.2 kBps         ETA  
##------------------ 12.6% 10.2 kBps         TA   
#######------------- 35.8% 7.2 kBps         ETA  
#################### 100.0% 366.0 kBps DONE      

Bad line - not a zsync file? "3&#54288;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;3&#65533;&#65533;&#65533;"


When I was testing Lubuntu 11.10 Beta 2, one of the team member advised to use the daily build iso (download and install it) rather than just upgrading via zsync. I'm not sure if the same applies on Alpha Release or not? I just asked that on the mailing list.

---

### Post by amjjawad on 2011-12-22
Forgot to update this :(

Some replies:

> Yes just keep using zsync to keep the ISO up to date, even if you only do it once a week it will still save bandwidth.

> this is inconsistent with my experience. the first time i used zsync     was with alpha. first i downloaded (http!) the daily iso, but     realized i wanted alpha. so then i zsync'd the alpha in the     directory with the iso. it read the .zsync, then checked the iso and     only updated the difference. i've even gone from ubuntu->lubuntu     and vice versa this way. i've NEVER had to download the whole thing     again. that being said, i'm totally hooked on zsync now. that and     the resumes work out really well. never http again!


> 
[http://ubuntuforums.org/showpost.php?p=11334389&postcount=4](http://ubuntuforums.org/showpost.php?p=11334389&postcount=4)

You seldom, actually almost never, need to DL an entire new iso - but you will have to burn a new disc!

---

### Post by kansasnoob on 2011-12-22
I notice a lot of talk here about using zsync, is this helpful:

[http://ubuntuforums.org/showpost.php?p=11334389&postcount=4](http://ubuntuforums.org/showpost.php?p=11334389&postcount=4)

Or is it just confusing?

---

### Post by jerrylamos on 2011-12-22
> **kansasnoob said:**
> I notice a lot of talk here about using zsync, is this helpful:

[http://ubuntuforums.org/showpost.php?p=11334389&postcount=4](http://ubuntuforums.org/showpost.php?p=11334389&postcount=4)

Or is it just confusing?

Being of simple mind, kinda confusing.  I just have a script in a folder example Downloads:
```
#! /bin/bash
sudo zsync http://cdimage.ubuntu.com/cdimage/daily-live/current/precise-desktop-i386.iso.zsync
echo "checksum O.K.?"
read temp
exit #
```
then use unity (or, I think, pcman) folder browser, double click on it, select run in terminal.

If all goes O.K. then can from unity file browser copy it to USB.
Or to a folder example /boot/iso or if you're really lucky it might fit on a CD.

It'll boot from the USB or /boot/iso using /etc/grub.d/40_custom file in this case on my /dev/sdb1:
```
#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries. Simply type the
# menu entries you want to add after this comment. Be careful not to change
# the 'exec tail' line above.
menuentry "Pangolin ISO sdb1" {
set isofile="/iso/precise-desktop-i386.iso"
loopback loop (hd1,1)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}
```
then do sudo update-grub and the .iso can be booted & run.

If you really want to live dangerously (me) you can do an install after booting the .iso by issuing in terminal:

sudo umount -l -r -f /dev/sdb1

No promises.  Just what I do.  Back up often...

Jerry

---

### Post by amjjawad on 2011-12-23
I have no idea what happened but I decided to re-install Lubuntu 12.04 32-bit again and ... it worked perfectly :)
I'm not sure what happened? I used the same CD, same partition (sda9) after formatting it of course on the same machine and same everything ... it did not work before but it does now. WOW :)

Anyway, I did:

```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo apt-get dist-upgrade
```

I need to use "zsync" but will do that later ... I need to log off now.

The LiveCD worked perfectly. Try Lubuntu without installation worked perfectly.


[B]Edit:
[/B]
```
Distributor ID:	Ubuntu
Description:	Ubuntu precise (development branch)
Release:	12.04
Codename:	precise
```

```
3.2.0-6-generic

```

---

### Post by amjjawad on 2011-12-23
> **kansasnoob said:**
> I notice a lot of talk here about using zsync, is this helpful:

[http://ubuntuforums.org/showpost.php?p=11334389&postcount=4](http://ubuntuforums.org/showpost.php?p=11334389&postcount=4)

Or is it just confusing?

Hi :)

I sent a reply to your email on the mailing list regarding "zsync". Waiting for your reply :)

Thanks!

---

### Post by amjjawad on 2012-01-01
Update your system and you'll get the new wallpaper :)

---

### Post by jerrylamos on 2012-01-02
First time booting a new install I put in my own wallpaper, in this case my wife in a bathing suit at a beach in Australia.  My view, save the CD space that wallpapers take.

Jerry

---

### Post by loukingjr on 2012-01-10
hope this is the correct thread. 

I just installed Lubuntu 12.04 in VirtualBox 4.1.8 and everything works except I can't logout. it just hangs. I have to reboot. I do have autologin set if that makes any difference.

---

### Post by amjjawad on 2012-01-12
> **loukingjr said:**
> hope this is the correct thread. 

I just installed Lubuntu 12.04 in VirtualBox 4.1.8 and everything works except I can't logout. it just hangs. I have to reboot. I do have autologin set if that makes any difference.

Log out or Shutdown you mean?
I honestly never tired log out on VirtualBox, I just close it if I want to shut it down but not sure what you are trying to do thus I asked :)

IMHO, Auto Login has nothing to do with this.

---

### Post by loukingjr on 2012-01-12
> **amjjawad said:**
> Log out or Shutdown you mean?
I honestly never tired log out on VirtualBox, I just close it if I want to shut it down but not sure what you are trying to do thus I asked :)

IMHO, Auto Login has nothing to do with this.
I meant log out. It shuts down and restarts just fine. I do a lot of themeing and sometimes with certain DEs to change a cursor for example, you have to log out instead of restarting for whatever reason. It's also a little quicker to see changes is all.

---

### Post by amjjawad on 2012-01-12
> **loukingjr said:**
> I meant log out. It shuts down and restarts just fine. I do a lot of themeing and sometimes with certain DEs to change a cursor for example, you have to log out instead of restarting for whatever reason. It's also a little quicker to see changes is all.

Ok, thanks for explaining. Actually, as I mentioned earlier, I have never logged out while using Lubuntu on VirtualBox. In fact, I used it for very few times.

Have you checked Launchpad? just in case someone has reported that as a bug? or a google search maybe?

---

### Post by loukingjr on 2012-01-12
> **amjjawad said:**
> Ok, thanks for explaining. Actually, as I mentioned earlier, I have never logged out while using Lubuntu on VirtualBox. In fact, I used it for very few times.

Have you checked Launchpad? just in case someone has reported that as a bug? or a google search maybe?
I have but I'll try a little more thoroughly. danke.

---

### Post by amjjawad on 2012-01-20
Hello Everyone,

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

After  running the above commands on Lubuntu 12.04 (No, I'm not testing the  daily iso, this installing was done 2 weeks or more), I logged out to  check the wallpaper and it's ALL black now with light gray bar at the  top. I can't see anything but these two colors + the mouse cursor. That  is all.

I rebooted my machine and same thing happened. Automatic Login is  enabled in my case so I had to log out to see that. So, for me, I have  no problem but not sure if someone with Automatic Login disabled if  he/she can login or not?

Thanks!

---

### Post by loukingjr on 2012-01-20
I just updated this morning and unlike before when I couldn't log out at all, now I get the same gray and black screen as was mentioned. I too am set to auto login and not going to change it to see what happens. :lol:

---

### Post by GeorgeVita on 2012-01-20
> **amjjawad said:**
> ... I logged out to  check the wallpaper and it's ALL black now with light gray bar at the  top. I can't see anything but these two colors + the mouse cursor. That  is all.


This problem exists 19 hours ago, just after "finishing unity greeter" ([read this thread]("http://ubuntuforums.org/showthread.php?t=1911498")). Possibly works to Ubuntu and not Lubuntu...

A simple workaround is: type your password and press <Enter>
It is a "blind" process but works!

G

---

### Post by loukingjr on 2012-01-20
> **GeorgeVita said:**
> This problem exists 19 hours ago, just after "finishing unity greeter" ([read this thread]("http://ubuntuforums.org/showthread.php?t=1911498")). Possibly works to Ubuntu and not Lubuntu...

A simple workaround is: type your password and press <Enter>
It is a "blind" process but works!

G
yes, that works. :D

---

### Post by amjjawad on 2012-01-20
> **GeorgeVita said:**
> This problem exists 19 hours ago, just after "finishing unity greeter" ([read this thread]("http://ubuntuforums.org/showthread.php?t=1911498")). Possibly works to Ubuntu and not Lubuntu...

Actually the wallpaper has changed few days ago and it was black and still can see LightDM but it's worse now so yes, it's worse for the last hours I guess.

> A simple workaround is: type your password and press <Enter>
It is a "blind" process but works!

I tried that but did not work but it's ok as long as I have automatic login enabled :)

---

### Post by GeorgeVita on 2012-01-20
> **amjjawad said:**
> ...I tried that but did not work but it's ok as long as I have automatic login enabled :)
For my case: only one user, login using password
You must not press any key while booting, normal procedure has selected the only username, waits for the password, type in careffuly, press <Enter>.
In case of mistake it asks for the username, so this is more difficult to synchronize.

Another problem that I have: double click to drag and drop is not working
for moving a window, neither to adjust volume or a window slider
(on EeePC 1000h, touchpad)

G

---

### Post by amjjawad on 2012-01-20
> **GeorgeVita said:**
> For my case: only one user, login using password
You must not press any key while booting, normal procedure has selected the only username, waits for the password, type in careffuly, press <Enter>.
In case of mistake it asks for the username, so this is more difficult to synchronize.

Yes, I tried that again and it worked. However, I hope our devs will fix that soon :)

> 
Another problem that I have: double click to drag and drop is not working
for moving a window, neither to adjust volume or a window slider
(on EeePC 1000h, touchpad)

G

Lubuntu 12.04 32-bit here and I don't have such issue but what do you mean by "double click to drag and drop" ?

---

### Post by amjjawad on 2012-01-20
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/918401](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/918401)

---

### Post by GeorgeVita on 2012-01-20
> **amjjawad said:**
> ... what do you mean by "double click to drag and drop" ?

Assume that you want to move a window (not maximized) or an icon on the Desktop area. Using mouse you can: move cursor at the top (title) of window or over the icon, hold down the left button and move mouse. 

The same can be done with the touchpad (pressing the left button and moving finger) or with double tap at the touch pad, hold the finger down at second tap and scroll finger. Both ways should move the window/icon/etc.

Lubuntu 11.10 works, recent 12.04 no.

The same feature is needed to scroll the slider of the volume control (move cursor at the slider, tap, tap and hold finger, scroll it up or down) or to select text using 1 finger.

Also **pushing the power button logout/shutdown menu is not appearing (EeePC)**

As I can test Lubuntu 12.04 to more than 1 PCs, can you remind the terminal command for upgrading from the 11.10 to the recent testing 12.04? This will help me to determine if an issue is generic or h/w specific.

G

---

### Post by amjjawad on 2012-01-20
> **GeorgeVita said:**
> Also **pushing the power button logout/shutdown menu is not appearing (EeePC)**

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#I_want_to_bind_the_power-button_to_change_computer_state.2C_how_do_I_do_it.3F](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#I_want_to_bind_the_power-button_to_change_computer_state.2C_how_do_I_do_it.3F)

The devs team, as far as I can remember, they said they will do it on Lubuntu 12.04 but looks like it's not done as of now but we still have time until the final release :)

> As I can test Lubuntu 12.04 to more than 1 PCs, can you remind the terminal command for upgrading from the 11.10 to the recent testing 12.04? This will help me to determine if an issue is generic or h/w specific.


I never do upgrades, always fresh new installation. As per our Wiki, this is all what I know: [https://help.ubuntu.com/community/Lubuntu#Upgrading_from_11.04](https://help.ubuntu.com/community/Lubuntu#Upgrading_from_11.04)

I have no idea if it's possible to upgrade a stable version (11.10) to a non-stable version (12.04).

We had a discussion over the mailing list and it's been agreed that the best way to test is to do a fresh install every now and then because it's very important to test the installer and how well the system will go. For me, I don't have time for that so I'm messing around with an installed Lubuntu 12.04 and just update/upgrade it. With Alpha2 maybe, I'll do that. Using zsync will be handy in that case.

---

### Post by nm_geo on 2012-02-27
Thought I might place this here as well.  During testing of the Lubuntu precise isos i386 & amd64 both dated 20120225.  Not able to get a bootable Flash Drive the versions are still on 

[http://iso.qa.ubuntu.com/](http://iso.qa.ubuntu.com/)

The following bug is 

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/941206](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/941206)

If you have some time please download and test the Live session if you will and add to the bug or provide input.

---

### Post by GeorgeVita on 2012-02-27
> **nm_geo said:**
> ... Lubuntu precise isos i386 ... 20120225.  Not able to get a bootable Flash Drive 

Just tested, cannot boot neither directly from .iso (using grub2 "loopback").
+1 "bug affects me" but it is already in "confirmed" status.
G

---

### Post by nm_geo on 2012-02-28
Today's respin of the current live isos 20120227 have resolved the bug .. 

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/941206](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/941206)

It has been marked as fixed in release.  kansasnoob and I are back to testing the Lubuntu releases.

---

### Post by jerrylamos on 2012-02-28
> **GeorgeVita said:**
> Just tested, cannot boot neither directly from .iso (using grub2 "loopback").
+1 "bug affects me" but it is already in "confirmed" status.
G

Just booted .iso 20120228 direct from hard drive O.K.

Jerry

---

### Post by nm_geo on 2012-02-29
lubuntu-artwork 0.25 fixes the black background problem in an installed Lubuntu precise desktop amd64.  You can now go back to lubuntu-default themes nice white backgrounds.

---

### Post by boswbr25 on 2012-03-02
Hi all,

I just downloaded the Beta iso today and have been running it all evening trying every possible way I can think of to test performance and I cannot seem to find anything wrong.

I just wanted to applaud the development team for putting together such a solid OS.  I have only tested a few other time but it has never gone this smooth.  I wasn't previously a permanent Lubuntu user but I have to say there will be a permanent partition set up for this. 

My biggest compliment is something that I never usually use on other distros.  The Lubuntu Software Center.  I am normally a terminal user and have always found the GUI to just slow things down but this one is really smooth.  Love that I can put the programs I want to install into 'App Basket' and install all at once.

Sorry if this is the wrong forum for this message, but I just wanted to say thanks for all the hard work and I'm hoping this is a place where the team will get the message.

~Boz~

---

### Post by GeorgeVita on 2012-03-02
**Lubuntu 12.04 beta1**, clean & single installation, updated, checked before/after updates, with/without extra language support packages. 


[SIZE="3"]1[/SIZE]. **lxkeymap** is not running! [COLOR="Red"]>>>[/COLOR] [**edit: Bug#945603**]("https://bugs.launchpad.net/ubuntu/+source/lxkeymap/+bug/945603") [COLOR="red"]<<<[/COLOR]

Lubuntu beta1, clean & single installation, updated, checked before/after updates, with/without extra language support packages. 

From terminal the output is:
```
g@gLuPPb1:~$ lxkeymap 

** WARNING **: Trying to register gtype 'GMountMountFlags' as enum when in fact it is of type 'GFlags'

** WARNING **: Trying to register gtype 'GDriveStartFlags' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/lxkeymap", line 628, in <module>
    window = LxkeymapWindow()
  File "/usr/bin/lxkeymap", line 86, in __new__
    new_object.finish_initializing(builder)
  File "/usr/bin/lxkeymap", line 156, in finish_initializing
    self.config.set('Global', 'Variant', self.variant_current[0])
IndexError: list index out of range
g@gLuPPb1:~$ 

```

Can anybody test it?
From a terminal window: lxkeymap
or from desktop: menu > Preferences > Lxkeymap
or from desktop: menu > Preferences > Keyboard and Mouse > Keyboard > lxkeymap button

**edit:**
[SIZE="3"]2[/SIZE]. Network connection icon is missing or not well-drawn. Sometimes is OK, most times not shown but restores when connected. Test it with and without wireless (or when wireless is off). See attachment:
[ATTACH]213588[/ATTACH]

[SIZE="3"]3[/SIZE]. "wishlist"
3a. Add a visual sign like  [hourglass]("http://en.wikipedia.org/wiki/Hourglass")) after clicking an application button (ex. chrome browser). Useful when using an older PC.

3b. Copy PrtScrn button (or ALT-PrtScrn) data to clipboard AND add a notification for the action done. Now PrtScrn creates a .png file into home folder but there is none notification about this. Also I couldn't find a way to include the pointer (as in the above attached capture). Clipboard is not used and a graphics application (mtPaint, gimp) cannot "paste" it directly.


Thanks,
George

---

### Post by zeroseven0183 on 2012-03-04
I upgraded my Lubuntu to 12.04 (32-bit) Beta earlier. It's a virtual machine running via Virtualbox where my host OS is Ubuntu 11.10 64-bit. After installing the upgrades, it required me to restart the guest machine, but would not boot to the desktop but only to grub.

I have the latest version of Virtualbox. If I can provide the logs, I will but it's showing some information about my laptop.

Any ideas?

---

### Post by nm_geo on 2012-03-04
> **GeorgeVita said:**
> **Lubuntu 12.04 beta1**, clean & single installation, updated, checked before/after updates, with/without extra language support packages. 


[SIZE=3]1[/SIZE]. **lxkeymap** is not running!

Lubuntu beta1, clean & single installation, updated, checked before/after updates, with/without extra language support packages. 

From terminal the output is:
```
g@gLuPPb1:~$ lxkeymap 

** WARNING **: Trying to register gtype 'GMountMountFlags' as enum when in fact it is of type 'GFlags'

** WARNING **: Trying to register gtype 'GDriveStartFlags' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/lxkeymap", line 628, in <module>
    window = LxkeymapWindow()
  File "/usr/bin/lxkeymap", line 86, in __new__
    new_object.finish_initializing(builder)
  File "/usr/bin/lxkeymap", line 156, in finish_initializing
    self.config.set('Global', 'Variant', self.variant_current[0])
IndexError: list index out of range
g@gLuPPb1:~$ 

```Can anybody test it?
From a terminal window: lxkeymap
or from desktop: menu > Preferences > Lxkeymap
or from desktop: menu > Preferences > Keyboard and Mouse > Keyboard > lxkeymap button
<snip>

Thanks,
George

Sorry George, I would have answered sooner but I have been working on mini.iso installs with non-pae kernel.  Yes the lxkeymap is borked for the moment. I will let qa.lubuntu know or you could start a bug on launchpad

---

### Post by GeorgeVita on 2012-03-06
> **nm_geo said:**
> ... lxkeymap is broked for the moment...
Trying to report it I found [bug#945603]("https://bugs.launchpad.net/ubuntu/+source/lxkeymap/+bug/945603").

> **GeorgeVita said:**
> 
[SIZE="3"]2[/SIZE]. **Network connection icon is missing or not well-drawn.** Sometimes is OK, most times not shown but restores when connected. Test it with and without wireless (or when wireless is off). See attachment:
[ATTACH]213588[/ATTACH]

Network Manager applet still has problems (appears, disappears, etc). This is included into "System Tray" applet. I faced this problem using 4 PCs. I cannot find the appropriate package to "apport-" the bug. Applet name found using:

Right Click on lower panel > Panel Settings (mismatched window title "Panel Preferences") > Panel Applets > **System Tray**

Regards,
George

---

### Post by cefn on 2012-03-09
I raised an issue with LXPanel, Compiz and Lubuntu Precise Pangolin 12.04 at this LXDE.org thread. 

[http://forum.lxde.org/viewtopic.php?f=23&t=31612](http://forum.lxde.org/viewtopic.php?f=23&t=31612)

---

### Post by nm_geo on 2012-03-19
I meant to add this message to this thread.. Oh well now it is on two of them.
Just did a fresh install of Lubuntu 12.04 Desktop i386 iso and we have a non-pae kernel.  

Linux tester-Latitude-D620 3.2.0-19-generic #30-Ubuntu SMP Fri Mar 16 16:26:45 UTC 2012 i686 i686 i386 GNU/Linux

Date seems strange but it was zsynced today 20120319.. 

Need some Pentium M testers now.

Installed size 1.85gb

---

### Post by jerrylamos on 2012-03-20
I'll give it a whirl on Pentium M.  Now where did I put that .iso.....

I think "Starks" has a Pentium M haven't seen a posting from him lately.

Jerry

---

### Post by kansasnoob on 2012-03-20
If I'm looking right, and I may not be, it appears that only the live images are now non-pae, but the alternate images are pae. Can anyone else confirm this?

---

### Post by GeorgeVita on 2012-03-20
Lubuntu daily build (i386, Live, 19-Mar-2012 16:55) installed/running fine on Pentium-4.

**[COLOR="Red"]lxkeymap[/COLOR]** crashed again!

G

---

### Post by kansasnoob on 2012-03-20
I tested both 20120319 i386 images. The Live CD is perfect but the alt CD hangs with a "No kernel modules found" error. I'll wait for the next build and test it to be sure the mirrors have had time to sync all updates.

---

### Post by jerrylamos on 2012-03-20
> **nm_geo said:**
> Just did a fresh install of Lubuntu 12.04 Desktop i386 iso and we have a non-pae kernel.  

Need some Pentium M testers now.

Installed size 1.85gb

Just zsync'd today and installed (direct boot of .iso from hard drive).  

Thinkpad T40: Intel(R) Pentium(R) M processor 1500MHz

jerry@ThinkPad-T40:~$ cat /proc/version

Linux version 3.2.0-19-generic (buildd@vernadsky) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu3) ) #30-Ubuntu SMP Fri Mar 16 16:26:45 UTC 2012

So it's a generic with no pae in sight.

/dev/sda10       6039488 1770160   3962540  31% /

Size is 1770160 do note I removed chromium then synaptic automatically installs firefox.

Running clean now.  I expect some pcmanfm foibles shortly.

Jerry

---

### Post by wojox on 2012-03-20
hmmm, Lubuntu Daily on my asus eeepc 900 says it doesen't have enough disk space to install. 

I have an internal 4GB ssd and an external 4GB ssd currently running Arch Linux with my root mounted on internal drive and home on the external drive. 

I guess I need Alternate or mini.iso?

edit: nevermind I found a bug report on this. [Ubiquity should have a command line option to override the free space check]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/775124")

---

### Post by jerrylamos on 2012-03-20
Since lubuntu iso zsync to today correctly installed "generic" I thought I'd try regular pangolin i.e. unity.

Zsync'd pangolin unity.  Incorrectly installed "generic-pae".  

I rebooted back to lubuntu generic much better match, in my opinion, to this Thinkpad T40 Pentium M no pae flag.

Jerry

p.s. I suppose I could try mini-iso last time I did I got generic.  More work than I want to do and more chances for fumble finger.  Regular lubuntu easy to install & customize, my opinion.

---

### Post by amjjawad on 2012-03-22
> **boswbr25 said:**
> Hi all,

I just downloaded the Beta iso today and have been running it all evening trying every possible way I can think of to test performance and I cannot seem to find anything wrong.

I just wanted to applaud the development team for putting together such a solid OS.  I have only tested a few other time but it has never gone this smooth.  I wasn't previously a permanent Lubuntu user but I have to say there will be a permanent partition set up for this. 

My biggest compliment is something that I never usually use on other distros.  The Lubuntu Software Center.  I am normally a terminal user and have always found the GUI to just slow things down but this one is really smooth.  Love that I can put the programs I want to install into 'App Basket' and install all at once.

Sorry if this is the wrong forum for this message, but I just wanted to say thanks for all the hard work and I'm hoping this is a place where the team will get the message.

~Boz~

Your message has been received ;)
Thank you so much for your nice words and thanks for choosing, testing and using Lubuntu :)

---

### Post by amjjawad on 2012-03-22
> **kansasnoob said:**
> If I'm looking right, and I may not be, it appears that only the live images are now non-pae, but the alternate images are pae. Can anyone else confirm this?

Confirmed. The NON-PAE Kernel is the default now for Lubuntu 12.04. We discussed that on the last meeting on IRC.

I read that discussion on the mailing list and it was you who reported that Xubuntu will go NON-PAE by default as well, right? :)

---

### Post by amjjawad on 2012-03-22
Hello everyone, it's been ages I didn't login due to Real Life issues.

**[COLOR="Red"]1) Lubuntu 12.04 by default will go NON-PAE Kernel while Ubuntu 12.04 is PAE.[/COLOR]**

2) 20-03-2012 daily image 32 bit - LiveUSB - Installed on two different machines, one laptop (Core Due @1.86GHz and 512MB RAM - ASUS F3F) and one PC (P4 @3GHz with 512MB RAM). So far, I did not do many tests but the only thing I did try was Lubuntu Software Center (not a fan of Software Centers at all but I'd like to help my team to test it) and it never ever launched. I tried many times but it crashes once I try to run it. Did anyone noticed that?

---

### Post by jerrylamos on 2012-03-22
> **amjjawad said:**
> Confirmed. The NON-PAE Kernel is the default now for Lubuntu 12.04. We discussed that on the last meeting on IRC.

Yep, installed late lubuntu on Pentium M (no pae flag) and got generic not generic-pae.  Just right.

Also installed the same lubuntu on AMD Dual-Core Processor E-350 which has tons of flags (giggle), also got generic not generic-pae.  It's got 2 GB memory.  Ran fine.

flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm constant_tsc nonstop_tsc extd_apicid aperfmperf pni monitor ssse3 cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch ibs skinit wdt arat npt lbrv svm_lock nrip_save pausefilter

Jerry

---

### Post by kansasnoob on 2012-03-23
> **amjjawad said:**
> Confirmed. The NON-PAE Kernel is the default now for Lubuntu 12.04. We discussed that on the last meeting on IRC.

I read that discussion on the mailing list and it was you who reported that Xubuntu will go NON-PAE by default as well, right? :)

Yep, did a bunch of testing and worked with Colin Watson to get the alternate images working also:

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/961218](https://bugs.launchpad.net/ubuntu-cdimage/+bug/961218)

Looks great to me ;)

---

### Post by GeorgeVita on 2012-03-26
> **GeorgeVita said:**
> Trying to report it I found [bug#945603]("https://bugs.launchpad.net/ubuntu/+source/lxkeymap/+bug/945603").
[B]Lubuntu Beta 2 just checked, 
[/B]> lxkeymap still crashing
> [Bug#945603]("https://bugs.launchpad.net/ubuntu/+source/lxkeymap/+bug/945603") remains Confirmed, Undecided, Unassigned

Above means that "foreign" keyboards cannot be used!

G

---

### Post by teh603 on 2012-03-26
> **amjjawad said:**
> Confirmed. The NON-PAE Kernel is the default now for Lubuntu 12.04. We discussed that on the last meeting on IRC.

I read that discussion on the mailing list and it was you who reported that Xubuntu will go NON-PAE by default as well, right? :)So for those of us who weren't on the IRC chat, does this mean that we have to use the 64-bit version if we're using hardware that would otherwise require the PAE kernel? Or am I missing something?

---

### Post by amjjawad on 2012-03-26
> **teh603 said:**
> So for those of us who weren't on the IRC chat, does this mean that we have to use the 64-bit version if we're using hardware that would otherwise require the PAE kernel? Or am I missing something?

I'm afraid you misunderstood my post.
It has nothing to do with 32-bit or 64-bit at all :)
Lubuntu's Kernel, by default, is a Non-PAE Kernel. I'm not a developer but AFAIK (As Far As I Know), it's a compilation option that you can add later on. So, you can add/install PAE support after you install Lubuntu.

Lubuntu Non-PAE will work on PAE Hardware AFAIK but the other way around will not. Having that said, if Lubuntu will follow Ubuntu's Steps, some users will no longer be able to boot from the LiveCD of Lubuntu 12.04 and can't install Lubuntu after that.

There are some users until now with Non-PAE Processors and we can't just ignore them and forget about them :)

---

### Post by amjjawad on 2012-03-26
> **kansasnoob said:**
> Yep, did a bunch of testing and worked with Colin Watson to get the alternate images working also:

[https://bugs.launchpad.net/ubuntu-cdimage/+bug/961218](https://bugs.launchpad.net/ubuntu-cdimage/+bug/961218)

Looks great to me ;)

You are the testing master, what can I say? :)

Your help and support is highly appreciated ;)

Thank you!

---

### Post by teh603 on 2012-03-26
> **amjjawad said:**
> I'm afraid you misunderstood my post.
It has nothing to do with 32-bit or 64-bit at all :)
Lubuntu's Kernel, by default, is a Non-PAE Kernel. I'm not a developer but AFAIK (As Far As I Know), it's a compilation option that you can add later on. So, you can add/install PAE support after you install Lubuntu.Fair enough. I'd rather ask and seem stupid, than not ask and be stupid. 64-bit Lubuntu runs wicked fast anyway so there's not much point in me not making the full switch.

Especially since I just found a GTK text editor (Geany) which has all the "killer app" features that I needed from Kate, plus having built-in word count.

> Lubuntu Non-PAE will work on PAE Hardware AFAIK but the other way around will not. Having that said, if Lubuntu will follow Ubuntu's Steps, some users will no longer be able to boot from the LiveCD of Lubuntu 12.04 and can't install Lubuntu after that.

There are some users until now with Non-PAE Processors and we can't just ignore them and forget about them :)Fair enough. I've actually got one of those hoary non-PAE laptops in my backup office, and being able to migrate to Lubuntu will breathe a bit more life back into it than Kubuntu was. But considering it couldn't even boot Win XP SP3, even Kubuntu is a huge step, resource- intensive as it is.

---

### Post by nm_geo on 2012-03-26
Iso testing is going extremely well for the Lubuntu 12.04 amd64 Desktop and the alternate amd64 iso (d-i) as well. The early spins on the Beta2 testing have been almost bug free.

---

### Post by amjjawad on 2012-03-26
> **teh603 said:**
> Fair enough. I'd rather ask and seem stupid, than not ask and be stupid.
There is nothing called "stupid" question at all IMHO. A question is a question and we are all here to ask questions and answer questions so feel free to ask whatever you want :)

> Fair enough. I've actually got one of those hoary non-PAE laptops in my backup office, and being able to migrate to Lubuntu will breathe a bit more life back into it than Kubuntu was. But considering it couldn't even boot Win XP SP3, even Kubuntu is a huge step, resource- intensive as it is.
Lubuntu is way faster than Kubuntu and Windows XP.

All the best with breathing new life into your old machine and if you need anything, we are here ;)

---

### Post by amjjawad on 2012-03-26
> **nm_geo said:**
> Iso testing is going extremely well for the Lubuntu 12.04 amd64 Desktop and the alternate amd64 iso (d-i) as well. The early spins on the Beta2 testing have been almost bug free.

Lubuntu 12.04 RC, right? that is good to know :D

---

### Post by jerrylamos on 2012-03-26
20120325 Beta 2 candidate installed clean on this Thinkpad T40.  Responsive.  Quick.

Other 3 test pc's installed ubuntu 20120325 with varying degrees of install complications.  One clean, other two generated launchpad bugs.

Only 1 of the 4 has sound working, an Acer Aspire 5253.  Other 3 no sound.  I can briefly get sound on one of them by deleting the contents of .pulse, however as soon as I crank up the system test for sound it goes quiet again.  Yes there's a launchpad bug.

Jerry

---

### Post by teh603 on 2012-03-26
> **amjjawad said:**
> Lubuntu is way faster than Kubuntu and Windows XP.

All the best with breathing new life into your old machine and if you need anything, we are here ;)Well, Kubuntu is still faster than Windows Vista or 7. When XP first came out it ran pretty fast, but after installing a few service packs and all those drivers, and then updating those drivers and probably picking up some "unprotected port" malware it would slow way down.

I mainly keep the old Winbook bouncing around for showing off these days, since its battery hasn't worked in three or four years and it can't boot from USB. I suppose I should get it refurbished one of these days...

---

### Post by nm_geo on 2012-03-26
> **amjjawad said:**
> Lubuntu 12.04 RC, right? that is good to know :D

Well they are really the early spins of the Beta 2 Lubuntu 12.04. We are testing them a little early and there were no respins today.  I hope to get the (3) Lubuntu Alternate isos tests done this afternoon after I change to my testing hard drive.  

Alternates
[http://cdimage.ubuntu.com/lubuntu/daily/current/](http://cdimage.ubuntu.com/lubuntu/daily/current/) 

Desktops
[http://cdimage.ubuntu.com/lubuntu/daily-live/current/](http://cdimage.ubuntu.com/lubuntu/daily-live/current/) 

You never know when someone needs those.

---

### Post by jerrylamos on 2012-03-26
12.04 lubuntu Beta 2 candidate as usual pcmanfm crash. Pcmanfm window open in backround doing nothing.  Firefox window in foreground completely hid pcmanfm window. Reported same to launchpad.

Jerry

---

### Post by teh603 on 2012-03-26
Where's the best place to file a bug to get modemmanager added to the default loadout? Its of critical importance to those of us who use cell modems and other mobile broadband stuff, and not having it caused me a fair bit of confusion and google work.

---

### Post by jerrylamos on 2012-03-26
> **teh603 said:**
> ...I've actually got one of those hoary non-PAE laptops in my backup office, and being able to migrate to Lubuntu will breathe a bit more life back into it than Kubuntu was.

I've got lubuntu Beta 2 candidate up on a non-pae IBM Thinkpad T40 1.5 GHZ Pentium M.

User response really sparkles compared to the Unity-3D on my faster pc's.

Yes, lubuntu doesn't look like a "smartphone" but it's got all the function I need and can add whatever else too.

Fun.

Jerry

---

### Post by kansasnoob on 2012-03-30
Julien Lavergne has requested that we try a testing version of PCManFM:

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605/comments/21](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605/comments/21)

It's in this PPA:

[https://launchpad.net/~lubuntu-dev/+archive/staging](https://launchpad.net/~lubuntu-dev/+archive/staging)

All should be forewarned that the use of packages from any PPA can result in breakage, worst case scenario being the need to reinstall ;)

Currently installing the PPA and just updating also updates some unrelated artwork and theme packages so I'm debating what might be the best way to test this :confused:

---

### Post by nm_geo on 2012-03-30
I am using that new pcmanfm and it seems to be working well. I ran it through the qa testing on the Lubuntu Testing page with the instructions Julien prepared.  

> **kansasnoob said:**
> Julien Lavergne has requested that we try a testing version of PCManFM:

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605/comments/21](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605/comments/21)

It's in this PPA:

[https://launchpad.net/~lubuntu-dev/+archive/staging]("https://launchpad.net/%7Elubuntu-dev/+archive/staging")

All should be forewarned that the use of packages from any PPA can result in breakage, worst case scenario being the need to reinstall ;)

Currently installing the PPA and just updating also updates some unrelated artwork and theme packages so I'm debating what might be the best way to test this :confused:

---

### Post by kansasnoob on 2012-03-31
> **nm_geo said:**
> I am using that new pcmanfm and it seems to be working well. I ran it through the qa testing on the Lubuntu Testing page with the instructions Julien prepared.

OK, so we'd want to:

```
sudo apt-add-repository ppa:lubuntu-dev/staging
```

```
sudo apt-get update
```

```
sudo apt-get install pcmanfm
```

```
sudo apt-add-repository -r ppa:lubuntu-dev/staging
```

```
sudo apt-get update
```

Is that correct?

Then is there a specific set of pcmanfm tests to perform?

I'm a bit off my feed here :redface:

---

### Post by kansasnoob on 2012-03-31
Aha, maybe answered my own question:

[http://testcases.qa.ubuntu.com/Applications/Pcmanfm](http://testcases.qa.ubuntu.com/Applications/Pcmanfm)

---

### Post by kansasnoob on 2012-03-31
Based on this bug:

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605)

I wonder if we should add one test case, something like:

1. Close pcmanfm

2. Open synaptic

3. Search for 'xfce4-screenshooter' and mark it for installation.

4. Click on Custom Filters > Marked Changes and deselect 'xfce4-panel'.

5. Then complete the installation of that package, close synaptic, and be certain that you do not get a crash report as reported in this bug:

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605)

Does that make any sense?

---

### Post by nm_geo on 2012-03-31
I ended up adding the ppa to source list as per the manual instructions.  I tried the newer add ppa but it did not complete for me so I went old school..

I have tried everything I can think of to crash the pcmanfm and about the only thing that even causes it to shutdown is sticking a flash-drive in and then just pulling it out without unmounting it That will close the pcmanfm but it is not really a crash.

I have opened pcmanfm and left it open and updated with Update Manager which I never do on an install I want to keep working. I do not like "Update Manager" to automated for me. No crash.

I have tried the same with Synaptic with pcmanfm open or closed it has never shown a crash.

Adding more tests might be a good idea but until I find one that has an issue I really would not know what to add. Julien might have a idea on that one.

When you run pcmanfm and "Open as Root" note that the address bar background is not yellow. We have a bug on that.    
> **kansasnoob said:**
> OK, so we'd want to:

```
sudo apt-add-repository ppa:lubuntu-dev/staging
``````
sudo apt-get update
``````
sudo apt-get install pcmanfm
``````
sudo apt-add-repository -r ppa:lubuntu-dev/staging
``````
sudo apt-get update
```Is that correct?

Then is there a specific set of pcmanfm tests to perform?

I'm a bit off my feed here :redface:

---

### Post by amjjawad on 2012-04-01
> **teh603 said:**
> Well, Kubuntu is still faster than Windows Vista or 7.
My first and last time using Kubuntu was with 10.04 and that is all. It was just one time :)

> When XP first came out it ran pretty fast, but after installing a few service packs and all those drivers, and then updating those drivers and probably picking up some "unprotected port" malware it would slow way down.
XP is very fast after clean fresh install. After that, as you posted exactly :)

> it can't boot from USB.

[http://ubuntuforums.org/showthread.php?t=1844755](http://ubuntuforums.org/showthread.php?t=1844755)
Section G > 6
Plop Manager :)

---

### Post by amjjawad on 2012-04-01
> **kansasnoob said:**
> Julien Lavergne has requested that we try a testing version of PCManFM:

[https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605/comments/21](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/963605/comments/21)

It's in this PPA:

[https://launchpad.net/~lubuntu-dev/+archive/staging](https://launchpad.net/~lubuntu-dev/+archive/staging)

All should be forewarned that the use of packages from any PPA can result in breakage, worst case scenario being the need to reinstall ;)

Currently installing the PPA and just updating also updates some unrelated artwork and theme packages so I'm debating what might be the best way to test this :confused:

What that new PCManFM? I'm lost :(

---

### Post by amjjawad on 2012-04-01
Hello everyone,

If I want to file a bug against LXPanel, where do I have to do that? under what package? Desktop Settings?

There is a bug that is really annoying since 11.10 and I don't know if there is a bug or not? I already informed Julien but I don't remember I filed a bug so I think it's pointless to keep talking about it without a bug and I do hope I'm not to late :(

Thanks!

---

### Post by Elfy on 2012-04-01
> **amjjawad said:**
> Hello everyone,

If I want to file a bug against LXPanel, where do I have to do that? under what package? Desktop Settings?

There is a bug that is really annoying since 11.10 and I don't know if there is a bug or not? I already informed Julien but I don't remember I filed a bug so I think it's pointless to keep talking about it without a bug and I do hope I'm not to late :(

Thanks!

[https://launchpad.net/ubuntu/+source/lxpanel/+bugs](https://launchpad.net/ubuntu/+source/lxpanel/+bugs)

```
ubuntu-bug lxpanel
```if necessary

---

### Post by amjjawad on 2012-04-01
> **forestpiskie said:**
> [https://launchpad.net/ubuntu/+source/lxpanel/+bugs](https://launchpad.net/ubuntu/+source/lxpanel/+bugs)

```
ubuntu-bug lxpanel
```if necessary

Thanks a lot :)

[https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/970758](https://bugs.launchpad.net/ubuntu/+source/lxpanel/+bug/970758)

---

### Post by amjjawad on 2012-04-01
For those who are not on the mailing list:

> On Sun, Apr 1, 2012 at 4:30 PM, Julien Lavergne wrote:
Hi,

I added a bunch of patches in libfm and pcmanfm to fix some issues, especially the nasty mount / umount / random-when-I-do-nothing crash (see [https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/838489](https://bugs.launchpad.net/ubuntu/+source/pcmanfm/+bug/838489)).

Before uploading it to precise, please give it a try to confirm or not the bugs you reported against pcmanfm. It's available in lubuntu-staging PPA, be sure to update pcmanfm AND libfm.

If you can confirm that a bug who reported is gone, please add a note in the bug report, so I can close it after the upload.

Thanks :)

Regards,
Julien Lavergne

---

### Post by kansasnoob on 2012-04-01
> **amjjawad said:**
> For those who are not on the mailing list:

This is what nm_geo and I have been discussing, I'm going to run a fairly comprehensive set of tests today and I'll report the results at Launchpad, directly to Julien, and the mailing lists, as well as here :)

I'm just playing catch up here, I encountered some hardware/optical-media problems toward the end of iso-testing. That combined with non-puter things like broken mowers, sick animals, and other general life issues have been eating my lunch :cry:

---

### Post by marinara on 2012-04-01
W: Failed to fetch [http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

I wanna test, but apt-get update is failing.  Please tell me if it's only my pc

---

### Post by Elfy on 2012-04-01
> **marinara said:**
> W: Failed to fetch [http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

I wanna test, but apt-get update is failing.  Please tell me if it's only my pc
That PPA appears to only have karmic and lucid

[http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/](http://ppa.launchpad.net/ubuntu-boot/staging/ubuntu/dists/)

---

### Post by marinara on 2012-04-01
i figured it out, i was adding the wrong repo

---

### Post by kansasnoob on 2012-04-01
I know nm_geo also mentioned a problem and I believe he uses 64 bit exclusively while I use 32 bit, but I also noticed a problem in the command I posted in post #82, which was copied from Lubuntu documentation. The command I posted was:

"sudo apt-add-repository ppa:lubuntu-dev/staging"

But according to official Ubuntu it should be:

"sudo add-apt-repository ppa:lubuntu-dev/staging"

Still I'm wondering if it's not a 64 bit issue :confused:

Believe me, I'm looking into this as quickly as I can :redface:

Tried both .................. no difference on i386 ;^)

---

### Post by kansasnoob on 2012-04-01
> **marinara said:**
> i figured it out, i was adding the wrong repo

Cool :D

---

### Post by kansasnoob on 2012-04-02
I'm convinced we're good to go with pcmanfm version 0.9.10-0ubuntu2~ppa2 :) 

I've done a lot of testing, most recently installing (but not updating) the actual Beta 2 (not the current daily). I then first installed Firefox using synaptic and got the expected pcmanfm crash report. I then imported my .mozilla profile. When I opened Firefox the first time I got yet another pcmanfm crash report.

Then I installed the new "testing" pcmanfm using these steps:

[http://ubuntuforums.org/showpost.php?p=11806965&postcount=82](http://ubuntuforums.org/showpost.php?p=11806965&postcount=82)

I then installed all available updates - NO pcmanfm crash report \\:D/

Since there was a kernel upgrade included I rebooted and then continued to install desired apps using both synaptic and LSC ........... still no crash report =D>

I then ran through all of the test cases shown here:

[http://testcases.qa.ubuntu.com/Applications/Pcmanfm](http://testcases.qa.ubuntu.com/Applications/Pcmanfm)

No real problem, just two minor issues:

#1: As nm_geo has stated previously we don't get a yellow address bar as described in test case pfm-006.

#2: In test case pfm-003 where it says in step #6; "click on Delete Bookmark Item", it should say "click on Remove from Bookmarks".

So I think we're good to go :guitar:

---

### Post by loukingjr on 2012-04-02
I just updated my 12.04 install and suddenly drop shadows stopped working in xcompmgr. transparency still works.

any thoughts?

---

### Post by kansasnoob on 2012-04-02
> **loukingjr said:**
> I just updated my 12.04 install and suddenly drop shadows stopped working in xcompmgr. transparency still works.

any thoughts?

I'm clueless, xcompmgr is not even part of the default installation.

---

### Post by loukingjr on 2012-04-02
yes, I added it.

---

### Post by marinara on 2012-04-04
Did you know that the final version of Lubuntu 12.04 is ready for
testing?  This is a great time to test your favorite application on
the next Lubuntu, so to make sure it works for you.
It's easy.
1.  Use Synaptic Package Manager to install virtualbox.  
2.  Launch virtualbox, and create a new virtual machine, after you
download one of the ISO files for Beta 2.
3.  Test your favorite application.

64 bit and 32 bit beta iso's here:
 [http://thesii.org/lubuntu-12.04-beta2-desktop-amd64.iso](http://thesii.org/lubuntu-12.04-beta2-desktop-amd64.iso)
 [http://thesii.org/lubuntu-12.04-beta2-desktop-i386.iso](http://thesii.org/lubuntu-12.04-beta2-desktop-i386.iso)

Less than 400 megabytes of ram? use these to install Lubuntu beta
 [http://thesii.org/lubuntu-12.04-beta2-alternate-amd64.iso](http://thesii.org/lubuntu-12.04-beta2-alternate-amd64.iso)
 [http://thesii.org/lubuntu-12.04-beta2-alternate-i386.iso](http://thesii.org/lubuntu-12.04-beta2-alternate-i386.iso)


Lubuntu's QA coordinator has asked that I point advanced users towards 
[https://wiki.ubuntu.com/Testing/ISO/Procedures](https://wiki.ubuntu.com/Testing/ISO/Procedures)
or [https://wiki.ubuntu.com/Testing/Laptop/Procedures](https://wiki.ubuntu.com/Testing/Laptop/Procedures) for laptops
so we can keep a record of your testing work.

**the final release of Lubuntu is on April 26th, the above ISO's are for testing only

---

### Post by marinara on 2012-04-04
anyone else having the screensaver come on, even if you tell it not to come on for like 45 minutes?

---

### Post by amjjawad on 2012-04-04
> **marinara said:**
> Did you know that the final version of Lubuntu 12.04 is ready for
testing?

Mate, you are confusing new comers here :D
Please edit your post and write "Beta 2 version" instead of "final version" as this is NOT the final, the final stable version will be on 28th of April ;)

> 
Less than 400 megabytes of ram? use these to install Lubuntu beta
 [http://thesii.org/lubuntu-12.04-beta2-alternate-amd64.iso](http://thesii.org/lubuntu-12.04-beta2-alternate-amd64.iso)
 [http://thesii.org/lubuntu-12.04-beta2-alternate-i386.iso](http://thesii.org/lubuntu-12.04-beta2-alternate-i386.iso)


I have personally installed Lubuntu 11.10 from a LiveCD on a machine with less than 256MB of RAM and it worked but yes, the installation was dead slow. Usually, if you have above 256MB, it is ok to use the LiveCD. 400MB is okay if you ask me. This is as per a real personal experience :)

---

### Post by amjjawad on 2012-04-04
Thought to share this as long as testing is still on the go :)

I have installed Lubuntu 12.04 Beta 2 - 32bit version from LiveUSB on Asus F3F Laptop (Core Due @1.86GHz - 512MB RAM) into another USB Drive with 4GB as a total size.

Installation done successfully. "apt-get update && apt-get upgrade" done successfully. "lubuntu-restricted-extras" installed successfully as well.

I have booted from that USB on two different machines:
1- Asus F3F Laptop
2- Lenovo G570 - Core i5 2nd generation with 4GB RAM

Both booting worked perfectly.

Kindly see the attached screenshot :)

I was helping someone, that is why I did that test and I thought to share the result with you :)

---

### Post by jerrylamos on 2012-04-04
Lubuntu 12.04 all zsync'd up to today 20120404

Install gets into a couple of minutes of "copying files" then ubiquity crashes and vanishes back to desktop.  Will not install.  Tried several times.

Wrote bug #973608.

Ubiquity deliberately wiped out the grub config.  This is a triple boot so there are still two valid ubuntu's but grub nor grub rescue can get to them.

Ubiquity development presumes install will "never fail" so it wipes out grub config until very late in install.  Search Launchpad for ubiquity to see that "never fail" is a wrong assumption.

With live CD which doesn't need grub on the hard drive I followed
[https://help.ubuntu.com/community/Boot-Repair&#65279;](https://help.ubuntu.com/community/Boot-Repair&#65279;) 
which is a bit involved, downloading boot-repair and installing onto the live CD.  

It worked!  The other two partitions are now bootable again.

One's this lubuntu installed at Alpha time and now updated to beta 2 - thousands of files copied.  Install fails after a couple minutes of copying?!

The other is a Lucid Lynx which I use to bail out the "unstable" development environment.

Now I do have a lubuntu on another laptop, early Beta 2 install O.K. and some ubuntu Beta 2 unity-2D's (I'm NOT into Ubuntu-3D fuzzy foggy semi-transparent did I suddently lose my reading glasses and hieroglyphics finger touch size?? instead of applet size). 

Jerry

---

### Post by nm_geo on 2012-04-04
Just did a clean install of the Lubuntu precise-Desktop amd64 from today's daily current build 20120404.  Everything all okay.  Installed on sda10 where there was a previous install grub installed in same partition. Updated clean as well.

---

### Post by ranch hand on 2012-04-05
> **loukingjr said:**
> yes, I added it.
I can't be of any help, just wondered why you added it.

Seems to be a rather limited tool that is fairly heavy on resources.

It is still around though so it must be good for something, I am just wondering what you want to use it for.

---

### Post by NHclimber on 2012-04-05
> **jerrylamos said:**
> Ubiquity deliberately wiped out the grub config.  This is a triple boot so there are still two valid ubuntu's but grub nor grub rescue can get to them.

Ubiquity development presumes install will "never fail" so it wipes out grub config until very late in install.  Search Launchpad for ubiquity to see that "never fail" is a wrong assumption.

I too cannot understand why 'upgrade' == 'grub-install'.  Even 'fresh install' shouldn't necessarily mean bootloader install.

---

### Post by ranch hand on 2012-04-05
> **NHclimber said:**
> I too cannot understand why 'upgrade' == 'grub-install'.  Even 'fresh install' shouldn't necessarily mean bootloader install.
You will get a bootloader install most times when there is a grub-common upgrade.

I use custom entries and all my grub installs use the same XX_custom file.  To keep track of what install is currently handling boot loading I use the same grub background as the wallpaper for each install.

Update/upgrading usually takes place, here, 2 installs at a time (chroot) and many times my first clue that there has been a change is when the menu comes up on the screen when I go check the other installs.

---

### Post by teh603 on 2012-04-05
Ok, got a small problem. I got a bunch of fonts that I use for graphic design work- ebook covers and the like- and no graphic tool to install them. Anyone got a recommendation, or mind passing a bug upstream to get one written? Cause installing fonts thru the command prompt sucks.

---

### Post by Rodney9 on 2012-04-05
> **teh603 said:**
> Ok, got a small problem. I got a bunch of fonts that I use for graphic design work- ebook covers and the like- and no graphic tool to install them. Anyone got a recommendation, or mind passing a bug upstream to get one written? Cause installing fonts thru the command prompt sucks.

Open Pcman hit control H and add a folder called  ```
.fonts
``` then copy your fonts into that folder.

Then open Terminal, copy this code ```
sudo fc-cache -f -v 
```into it and hit enter, this will update all your fonts for the system.

Rodney

---

### Post by teh603 on 2012-04-06
Ok, that worked, but why can't we make a tool to automate this? Don't forget Bug #1.

I'd write something myself, but I'm about as hard on code as Groo the Wanderer is on ships.

---

### Post by NHclimber on 2012-04-06
Just wanted to drop a line and say thanks for supporting non-pae machines. I think I'll leave Lubuntu on this laptop :)

---

### Post by NHclimber on 2012-04-06
> **ranch hand said:**
> You will get a bootloader install most times when there is a grub-common upgrade.

I use custom entries and all my grub installs use the same XX_custom file.  To keep track of what install is currently handling boot loading I use the same grub background as the wallpaper for each install.

Update/upgrading usually takes place, here, 2 installs at a time (chroot) and many times my first clue that there has been a change is when the menu comes up on the screen when I go check the other installs.

That's an interesting way to workaround needless bootloader installs.

My point is that the grub2 bootloader may not have been installed originally.  The installer used to ask if you wanted to install the bootloader -- the lack thereof is a bug [https://bugs.launchpad.net/ubuntu/precise/+source/ubiquity/+bug/690926](https://bugs.launchpad.net/ubuntu/precise/+source/ubiquity/+bug/690926) -- so automatically installing the bootloader on an update is a bug too.

Also, some special kernel command line switches may have been necessary to even boot other installations. Automatically installing a bootloader potentially blows these away (for example, if the original /boot is not even mounted).

---

### Post by kansasnoob on 2012-04-10
Do we have a how-to for reconfiguring lightdm from password required to auto-login yet?

I'm examining this because "/etc/lightdm/lightdm.conf" is almost empty with a password required install:

```
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu
```

I'm installing from live now to check the difference with an auto-login "/etc/lightdm/lightdm.conf".

I remember this being mentioned once on the mailing list but I was clueless at the time and so far I haven't been able to google the info I'm looking for.

---

### Post by kansasnoob on 2012-04-10
> **kansasnoob said:**
> Do we have a how-to for reconfiguring lightdm from password required to auto-login yet?

I'm examining this because "/etc/lightdm/lightdm.conf" is almost empty with a password required install:

```
[SeatDefaults]
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu
```

I'm installing from live now to check the difference with an auto-login "/etc/lightdm/lightdm.conf".

I remember this being mentioned once on the mailing list but I was clueless at the time and so far I haven't been able to google the info I'm looking for.

Considerably more populated with auto-login set:

```
[SeatDefaults]
autologin-guest=false
autologin-user=john
autologin-user-timeout=0
autologin-session=lightdm-autologin
greeter-session=lightdm-gtk-greeter
user-session=Lubuntu

```

I need to make some comparisons with Ubuntu which uses 'unity-greeter'.

Note: john is a phony username that I used only for this test.

---

### Post by kansasnoob on 2012-04-10
This is Ubuntu with auto-login:

```
[SeatDefaults]
autologin-guest=false
autologin-user=actual_username
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter

```

I guess the only difference is the greeter?

---

### Post by kansasnoob on 2012-04-10
> **kansasnoob said:**
> This is Ubuntu with auto-login:

```
[SeatDefaults]
autologin-guest=false
autologin-user=actual_username
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter

```

I guess the only difference is the greeter?

Using Ubuntu's gui tool to change to password required looks like this:

```
[SeatDefaults]
autologin-guest=false
autologin-user=
autologin-user-timeout=0
autologin-session=lightdm-autologin
user-session=ubuntu
greeter-session=unity-greeter

```

Now I need to try a new install of Ubuntu w/o selecting auto-login ............ I'm gaining :)

---

### Post by kansasnoob on 2012-04-10
No noticable difference in Ubuntu:

```
[SeatDefaults]
user-session=ubuntu
greeter-session=unity-greeter

```

So, again, do we have a how-to page?

---

### Post by kansasnoob on 2012-04-11
Thought I'd bump this again.

Does Lubuntu have a how-to page for lightdm?

---

### Post by loukingjr on 2012-04-11
> **ranch hand said:**
> I can't be of any help, just wondered why you added it.

Seems to be a rather limited tool that is fairly heavy on resources.

It is still around though so it must be good for something, I am just wondering what you want to use it for.
strictly for eyecandy, it allows transparency in conky and normally one would have drop shadows. I have plenty of resources.

---

### Post by ranch hand on 2012-04-11
> **loukingjr said:**
> strictly for eyecandy, it allows transparency in conky and normally one would have drop shadows. I have plenty of resources.
Thank you very much.

Hadn't caught the connection with Conky.  Probably my fault.

While I like some limited transparency in my panel(s) it just bugs me else where.  Like to see it on other folks installs but causes me eye strain.

Have learned something new today though and will keep it in mind.  Never know when it may come in very handy.   Thanks.

---

### Post by loukingjr on 2012-04-11
> **ranch hand said:**
> Thank you very much.

Hadn't caught the connection with Conky.  Probably my fault.

While I like some limited transparency in my panel(s) it just bugs me else where.  Like to see it on other folks installs but causes me eye strain.

Have learned something new today though and will keep it in mind.  Never know when it may come in very handy.   Thanks.
you're welcome. I'm just used to drop shadows. I don't use transparency except in screen shots. looks nice. :)

---

### Post by nm_geo on 2012-04-11
Thanks for getting the bump up kansas.

I did catch a bug last night testing the Lubuntu desktop  amd64 current build 20120410 with my trusty persistent USB. Yeah you know it was ubiquity migration assistant most likely. Anyway I will hit the 20120411 spin later tonight and see if there has been an improvement.  Install failed on full drive install test and resized (along side), however, the manual test installed clean.
Who knows?
here be the bug..

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/978554](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/978554)

---

### Post by kansasnoob on 2012-04-11
> **nm_geo said:**
> Thanks for getting the bump up kansas.

I did catch a bug last night testing the Lubuntu desktop  amd64 current build 20120410 with my trusty persistent USB. Yeah you know it was ubiquity migration assistant most likely. Anyway I will hit the 20120411 spin later tonight and see if there has been an improvement.  Install failed on full drive install test and resized (along side), however, the manual test installed clean.
Who knows?
here be the bug..

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/978554](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/978554)

I last tried 20120408 i386 and no problems.

That said, while continual testing is always good, we know many changes will take place in the next several days. I notice PhillW put up an unexpected call for testing which I personally think is just ridiculous.

We're due for release on the 26th. Recently some official testing has begun quite early, I'd expect about the 19th or 20th, but even that is largely worthless because none of the devs seem to work weekends.

I plan on going full blown testing on the 23rd, until then we should be able to get straight answers to questions, like mine about update notifications - which I swear don't work (including no notification to restart after a kernel upgrade), or even how to edit lightdm :confused:

It's hard not to be a bit jaded when the head honchos seem to be more concerned with frilly-dillies and meetings than they are with the actual nuts-n-bolts :(

---

### Post by nm_geo on 2012-04-12
Agreed +1

Caribou had that early testing listed along with Phil in the latest sticky note too, and I wonder why? Well there is a new kernel in the current daily so that is a fairly good reason.

Anyway, as you know I hate ubiquity and desktop iso installs, but you also know most new users will not use the d-i alternate install that I prefer. So I test the stuff new users will try first and that danged Bug on the full disk install repeated tonight on the 20120411.1 spin.  That sucker will create a real problem for anyone who decides to over-write a single windoz HDD because they will not get a working OS after the crash.  It is now marked Hot and I think it is for sure.

Tomorrow I guess I will test the Lubuntu i386 full drive and the amd64 full drive iso tests only with the latest spins.  IMHO it is getting late for this kind of Bug.. :confused:

If I find enough USB drives, I might do a few full drive tests on Xubuntu and Ubuntu to see if the Bug exists on those flavors too.  Dang I better get zync up and working on the Xubuntu isos. 
Out

---

### Post by kansasnoob on 2012-04-12
Sorry about the grouch-itude but I sometimes like a one-legged man in a butt kicking contest ;)

This is of course not true at all, but it's easy to get frustrated.

Just don't burn yourself out before the crucial iso testing the week of the 23rd. I'm dropping Ubuntu testing altogether just because I can't do both Lubuntu and Ubuntu iso-testing.

---

### Post by nm_geo on 2012-04-12
> **kansasnoob said:**
> Sorry about the grouch-itude but I sometimes like a one-legged man in a butt kicking contest ;)

This is of course not true at all, but it's easy to get frustrated.

Just don't burn yourself out before the crucial iso testing the week of the 23rd. I'm dropping Ubuntu testing altogether just because I can't do both Lubuntu and Ubuntu iso-testing.

Yeah, I totally agree but right now I am chasing a Bug. I am just going to do some entire drive installs today. My plan is to try all the amd64 for Lubuntu, Ubuntu and Xubuntu, I will zsync those as soon as new spins arrive. Then maybe move to full drive installs on  i386 Lubuntu and Xubuntu. Wow I am getting lots of flavors in my isos folder.

Trying to narrow down the ubiquity migration-assistant Bug, it may be a flavor specific bug or maybe my hardware.

---

### Post by jerrylamos on 2012-04-12
> **kansasnoob said:**
> Sorry about the grouch-itude but I sometimes like a one-legged man in a butt kicking contest ;)

This is of course not true at all, but it's easy to get frustrated.

Just don't burn yourself out before the crucial iso testing the week of the 23rd. I'm dropping Ubuntu testing altogether just because I can't do both Lubuntu and Ubuntu iso-testing.
I'm still hanging in there.  I don't do a whole lot of different tests, principally several installs this week on a bunch of pc's and do what an ordinary user would do, write launchpad bugs, internet video, spread sheet, word processor, endless installing of the same things all over again aptitude, gparted, samba, synaptic, flashplugin, zsync, wallpaper, no lock on screensaver (!!), cut FULL BRIGHT down, even firefox on the lubuntu's, firefox bookmarks, ... what am I forgetting.

Do note thare are still Pentium M non-pae for sale in the marketplace.  Mine just did an install and am setting it up.  Runs nicely on lubuntu.

Thinkpad R31 won't install lubuntu, ubiquity window disappears during copying, wrote a bug and have a couple other people find the same thing on different hardware.

ubuntu used to be a breath of fresh air, neat, fast, easy, efficient, capable.  Now Shuttleworth and crew are headed full speed to pseudo smartphone pseudo ipad it's all about eye candy, clutter, and more and more actions to do the same thing, and faster and faster and bigger and bigger memory and fancier and fancier features just to run all that @#$% just like Microsoft and Apple.

At least they gave in and made ubuntu-2D available, for how long?  Speaking of how long, lubuntu and xubuntu?

At the moment I'm still testing whatever ubuntu throws over the fence with a rock tied to it principally because of the forums.  We'll see.

Jerry

---

### Post by amjjawad on 2012-04-12
> **kansasnoob said:**
> Thought I'd bump this again.

Does Lubuntu have a how-to page for lightdm?

[https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LightDM_in_Lubuntu_12.04](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LightDM_in_Lubuntu_12.04)


If you have so much bookmarks, I suggest to bookmark LOST (Lubuntu One Stop Thread) and I mean Page#1 - Post #1 which will give you link to the main sites/places for Lubuntu ... OR ... just bookmark this: [https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)

If something is missing in the Wiki, contact Chris, he's the coordinator of the Wiki Team :)

---

### Post by cariboo on 2012-04-12
@jerrylamos, you could make your life a lot easier, if you used [Oneconf]("https://wiki.ubuntu.com/OneConf"), or use the following command:

```
dpkg --get-selections > installed-software
```

to create a list of installed software, then when you do a fresh install:

```
dpkg --set-selections < installed-software
```

followed by:

```
dselect
```

You will have to install dselect, as it isn't installed by default. Once you have created the ***installed-software*** file, you can move it to your other computers via network, or sneaker-net..

---

### Post by kansasnoob on 2012-04-12
> **amjjawad said:**
> [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LightDM_in_Lubuntu_12.04](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LightDM_in_Lubuntu_12.04)


If you have so much bookmarks, I suggest to bookmark LOST (Lubuntu One Stop Thread) and I mean Page#1 - Post #1 which will give you link to the main sites/places for Lubuntu ... OR ... just bookmark this: [https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)

If something is missing in the Wiki, contact Chris, he's the coordinator of the Wiki Team :)

Thanks, I had looked and somehow just kept missing the bit about lightdm. Sometimes two pair of eyeballs are better than one.

---

### Post by teh603 on 2012-04-12
> **amjjawad said:**
> [https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LightDM_in_Lubuntu_12.04](https://help.ubuntu.com/community/Lubuntu/Documentation/FAQ/Guides#How_to_enable_automatic_logon_in_LightDM_in_Lubuntu_12.04)


If you have so much bookmarks, I suggest to bookmark LOST (Lubuntu One Stop Thread) and I mean Page#1 - Post #1 which will give you link to the main sites/places for Lubuntu ... OR ... just bookmark this: [https://help.ubuntu.com/community/Lubuntu/Documentation](https://help.ubuntu.com/community/Lubuntu/Documentation)

If something is missing in the Wiki, contact Chris, he's the coordinator of the Wiki Team :)I'm getting a lot of Internal Server Error messages from the sub-pages off the wiki.

And one thing that is missing is a section on how to manually install fonts, at least until we can get a graphical font manager.

---

### Post by amjjawad on 2012-04-13
> **kansasnoob said:**
> Thanks, I had looked and somehow just kept missing the bit about lightdm.

At your service ;)

> Sometimes two pair of eyeballs are better than one.
Ditto :)

---

### Post by amjjawad on 2012-04-13
> **teh603 said:**
> I'm getting a lot of Internal Server Error messages from the sub-pages off the wiki.

What sub-pages are showing error messages?

You can directly report that by sending to Lubuntu Mailing List: [https://wiki.ubuntu.com/Lubuntu/ContactUs](https://wiki.ubuntu.com/Lubuntu/ContactUs)

> And one thing that is missing is a section on how to manually install fonts, at least until we can get a graphical font manager.

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

Or just use Google :)
It shouldn't be different because after all Lubuntu and Ubuntu are both sharing the same core and repositories. However, if you are having some problems, please let us know :)

I personally don't need to install font, I just do "install lubuntu-restricted-extras" and that is all.

In case the Wiki Page for Fonts that I posted above will do the job then it is totally pointless to re-mention that on Lubuntu Wiki, again, because both systems are sharing the same core system and it is just the DE which is different + the default programs.

---

### Post by nm_geo on 2012-04-13
Tested the 20120412 yesterday's daily precise-desktop-amd64 on Ubuntu, Xubuntu and Lubuntu on Live Flash Drives yesterday and completed all three entire disk installs with no bugs.  So I marked the Ubiquity Bug #978554 invalid now as it appears to be fixed in the new spins.  I will take a little break and start back on the 23rd and hit the Lubuntu amd64 testing again might throw in Xubuntu amd64 testing if I have time.

---

### Post by teh603 on 2012-04-13
> **amjjawad said:**
> What sub-pages are showing error messages?

You can directly report that by sending to Lubuntu Mailing List: [https://wiki.ubuntu.com/Lubuntu/ContactUs](https://wiki.ubuntu.com/Lubuntu/ContactUs)
I'll have to remember that. Every single link I clicked on was generating one, though, so it was prolly really big.
> I personally don't need to install font, I just do "install lubuntu-restricted-extras" and that is all.

In case the Wiki Page for Fonts that I posted above will do the job then it is totally pointless to re-mention that on Lubuntu Wiki, again, because both systems are sharing the same core system and it is just the DE which is different + the default programs.Maybe put a link to that page on the wiki, then?

Anyway, I do have to install fonts because I have to do my own ebook covers in GIMP, and I don't always do them at home with the Kubuntu desktop PC.

---

### Post by kansasnoob on 2012-04-13
> **teh603 said:**
> I'll have to remember that. Every single link I clicked on was generating one, though, so it was prolly really big.
Maybe put a link to that page on the wiki, then?

Anyway, I do have to install fonts because I have to do my own ebook covers in GIMP, and I don't always do them at home with the Kubuntu desktop PC.

IMHO our Lubuntu how-tos are not very "search-able" via a search engine. I think a lot of that is due to "age".

We're young in a net-search way so quite often things default to "ubuntu", and even if you use quotes to focus the search specifically on "lubuntu" many things seem to play hide-n-seek :(

But the longer we're alive the easier these searches will become, so it's also good for all of us to keep asking repetitive questions because each question pushes the correct answer closer to the top of the search profile :D

---

### Post by teh603 on 2012-04-13
Or we could start a great big wiki re-write. Have Lubuntu-specific pages where they're needed, links to Ubuntu pages were those will do, prune dead links and orphan pages, stuff like that?

---

### Post by cariboo on 2012-04-13
> **teh603 said:**
> Or we could start a great big wiki re-write. Have Lubuntu-specific pages where they're needed, links to Ubuntu pages were those will do, prune dead links and orphan pages, stuff like that?

+1 to this suggestion.

---

### Post by kansasnoob on 2012-04-13
> **teh603 said:**
> Or we could start a great big wiki re-write. Have Lubuntu-specific pages where they're needed, links to Ubuntu pages were those will do, prune dead links and orphan pages, stuff like that?

That, I think, is a matter of man-power. Lubuntu is a great distro, as is Xubuntu, but our resources are limited ......... and I'm NOT talking financial!

We need more people that are willing to test, document, etc. And I'm sure that the devs (in our case Julien) would love to see some additional qualified help.

I think we're pretty good though, not quite perfect but very good ;)

---

### Post by jerrylamos on 2012-04-13
Tried another install on Thinkpad R31.  ubiquity window disappeared about the time the second slide show frame should have displayed.  Updated launchpad bug #978489 with .xession-errors and Xorg.0.log.

This is from lubuntu on the same pc, as updated endlessly from lubuntu alpha.

Jerry

p.s. VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)

---

### Post by teh603 on 2012-04-13
> **kansasnoob said:**
> We need more people that are willing to test, document, etc. And I'm sure that the devs (in our case Julien) would love to see some additional qualified help.
I'm willing to write articles and instructions and upload screenshots, but I'm not very good with the command prompt.

---

### Post by Elfy on 2012-04-13
> **teh603 said:**
> Or we could start a great big wiki re-write. Have Lubuntu-specific pages where they're needed, links to Ubuntu pages were those will do, prune dead links and orphan pages, stuff like that?

> **kansasnoob said:**
> That, I think, is a matter of man-power. Lubuntu is a great distro, as is Xubuntu, but our resources are limited ......... and I'm NOT talking financial!

We need more people that are willing to test, document, etc. And I'm sure that the devs (in our case Julien) would love to see some additional qualified help.

I think we're pretty good though, not quite perfect but very good ;)

> **teh603 said:**
> I'm willing to write articles and instructions and upload screenshots, but I'm not very good with the command prompt.

We are trying to push the community wiki - if you want some help - help us - bigger team - quicker result :)

If you do IRC then come see us in #ubuntu-wiki and #ubuntuforums

---

### Post by marinara on 2012-04-14
couldn't agree more.  Ubiquity fails all the time on real hardware, and the wiki needs some reorganization.

---

### Post by marinara on 2012-04-14
oh and there is a lightdm autologin tutorial on the help.ubuntu.com lubuntu wiki

---

### Post by jerrylamos on 2012-04-14
No go.  Tried lubuntu 12.04 install 20120413 (latest one) on Thinkpad R31 minimized window after all inputs done and copying started.   At about the same time as usual the panel tab for install disappeared.

Does not appear to be a visible x problem with the window.

Jerry

---

### Post by kansasnoob on 2012-04-14
> **jerrylamos said:**
> No go.  Tried lubuntu 12.04 install 20120413 (latest one) on Thinkpad R31 minimized window after all inputs done and copying started.   At about the same time as usual the panel tab for install disappeared.

Does not appear to be a visible x problem with the window.

Jerry

I don't quite understand what you're saying. Are you manually minimizing a window at some point during the installation? Not sure what you mean by "inputs"?

I see 20120414 i386 is now available on the qa tracker so I'll give one a spin to see what happens.

---

### Post by jerrylamos on 2012-04-14
> =kansasnoob;11844547]I don't quite understand what you're saying. Are you manually minimizing a window at some point during the installation? Not sure what you mean by "inputs"?

I see 20120414 i386 is now available on the qa tracker so I'll give one a spin to see what happens.

Sorry about my mis-communication.  On install, after I had inputted (keyed in) everything install asked for and copying had begun, I minimized the window to see if x display of the slide show had anything to do with install "dropping out",  Hopefully install would have continued to the restart message.

No go, the install panel tab stayed awhile, then disappeared.  About 20% of the expected bytes were in the partition so it stopped pretty early.

Jerry

---

### Post by cariboo on 2012-04-14
@jerrylamos, are you documenting the problems you run into, and entering the results [here]("http://iso.qa.ubuntu.com/qatracker/milestones/204/builds/15393/testcases"), if not, all your hard work testing iso's really isn't doing a lot of good. Just installing the iso without using the test cases, and reporting bugs, doesn't get the attention of the right people. By using the test cases, and reporting bugs the chances of your bug reports getting quick attention are much higher.

---

### Post by andrewabc on 2012-04-14
> **jerrylamos said:**
> Sorry about my mis-communication.  On install, after I had inputted (keyed in) everything install asked for and copying had begun, I minimized the window to see if x display of the slide show had anything to do with install "dropping out",  Hopefully install would have continued to the restart message.

No go, the install panel tab stayed awhile, then disappeared.  About 20% of the expected bytes were in the partition so it stopped pretty early.

Jerry

Are you using livecd or liveusb?
Maybe try whatever you are not using to see if same problem?

---

### Post by amjjawad on 2012-04-15
> **teh603 said:**
> Or we could start a great big wiki re-write. Have Lubuntu-specific pages where they're needed, links to Ubuntu pages were those will do, prune dead links and orphan pages, stuff like that?

Sigh, Lubuntu Wiki Team is very small team. We are doing our best but if truth to be told, each and everyone of us are doing many things at the same time and sometimes, it gets harder than it seems.

I admit that Lubuntu Wiki Pages needs more care and work but, again, we are short in resources but we are doing our best and we are still standing :)

---

### Post by amjjawad on 2012-04-15
> **kansasnoob said:**
> That, I think, is a matter of man-power. Lubuntu is a great distro, as is Xubuntu, but our resources are limited ......... and I'm NOT talking financial!

We need more people that are willing to test, document, etc. And I'm sure that the devs (in our case Julien) would love to see some additional qualified help.

I think we're pretty good though, not quite perfect but very good ;)

+1 and ditto to every word :D

---

### Post by amjjawad on 2012-04-15
> **teh603 said:**
> I'm willing to write articles and instructions and upload screenshots, but I'm not very good with the command prompt.

Don't underestimate your abilities even if what you are willing to do is little because that would be the beginning. 

If you really want to help Lubuntu in anyway, just let me know ;)

---

### Post by amjjawad on 2012-04-15
> **cariboo907 said:**
> @jerrylamos, are you documenting the problems you run into, and entering the results [here]("http://iso.qa.ubuntu.com/qatracker/milestones/204/builds/15393/testcases"), if not, all your hard work testing iso's really isn't doing a lot of good. Just installing the iso without using the test cases, and reporting bugs, doesn't get the attention of the right people. By using the test cases, and reporting bugs the chances of your bug reports getting quick attention are much higher.

Very valuable note but is that mentioned anywhere on our Wiki? I mean Ubuntu in general?

---

### Post by cariboo on 2012-04-16
> **amjjawad said:**
> Very valuable note but is that mentioned anywhere on our Wiki? I mean Ubuntu in general?

Probably not, but there are quite a few changes coming in QA and with the U+1 testing team wiki's.

I'm in the process of creating a new sticky for the QQ dev cycle, I'll be sure to mention it. :)

---

### Post by Elfy on 2012-04-16
> **amjjawad said:**
> Sigh, Lubuntu Wiki Team is very small team. We are doing our best but if truth to be told, each and everyone of us are doing many things at the same time and sometimes, it gets harder than it seems.

I admit that Lubuntu Wiki Pages needs more care and work but, again, we are short in resources but we are doing our best and we are still standing :)

> **forestpiskie said:**
> We are trying to push the community wiki - if you want some help - help us - bigger team - quicker result :)

If you do IRC then come see us in #ubuntu-wiki and #ubuntuforums

As was said - you are not alone ;)

---

### Post by jerrylamos on 2012-04-16
> **cariboo907 said:**
> @jerrylamos, are you documenting the problems you run into, and entering the results [here]("http://iso.qa.ubuntu.com/qatracker/milestones/204/builds/15393/testcases"), if not, all your hard work testing iso's really isn't doing a lot of good. Just installing the iso without using the test cases, and reporting bugs, doesn't get the attention of the right people. By using the test cases, and reporting bugs the chances of your bug reports getting quick attention are much higher.
I don't have any showstoppers at the moment so I'm not anxious for quick attention.  I put my bugs out on Launchpad where I assume someone in ubuntu decides what's important enough to be worked on or not.  Last time I tried the test cases failed on the first step of the first one, I think it was checkbox-qt audio didn't, some other people having audio trouble as well, now running O.K.

When's the next development release start?

Jerry

---

### Post by kansasnoob on 2012-04-16
> **jerrylamos said:**
> No go.  Tried lubuntu 12.04 install 20120413 (latest one) on Thinkpad R31 minimized window after all inputs done and copying started.   At about the same time as usual the panel tab for install disappeared.

Does not appear to be a visible x problem with the window.

Jerry

It looks like I'll finally have time to check this out today, with the latest available image of course, but I just wanted to ask a couple of questions:

1: You are talking about the live .iso right? I know you boot using grub 2 whereas I use actual discs, but I want to be sure we're testing the same general image.

2: Are you first booting to the live DE and then beginning the installation or choosing install from the initial boot menu?

3: When you say, "minimized window after all inputs done and copying started", do you mean that you manually minimized the installation window? If so why?

Additionally, the more detail you can add about exactly what steps you performed leading up to the installer crashing or stopping will help the rest of us testers immensely ;)

---

### Post by kansasnoob on 2012-04-16
> **marinara said:**
> couldn't agree more.  Ubiquity fails all the time on real hardware, and the wiki needs some reorganization.

When you say, "Ubiquity fails all the time on real hardware", we really need much more detailed info. That will help those of us that do a lot of iso-testing to try and reproduce the exact steps leading up to the crash or failure ;)

---

### Post by nm_geo on 2012-04-16
> **kansasnoob said:**
> When you say, "Ubiquity fails all the time on real hardware", we really need much more detailed info. That will help those of us that do a lot of iso-testing to try and reproduce the exact steps leading up to the crash or failure ;)

In the last iso tests I ran 20120414 all installed on hardware none of the isos failed.  I installed Lubuntu precise amd64, i386 and some alternates as well.  I would also question that statement as well, I even installed the amd64 versions of Ubuntu and Xubuntu with no issues. I did have a ubiquity bug earlier prior to that date but it has not showed up in recent spins. All those tests are archived on the iso-tracker.

---

### Post by NHclimber on 2012-04-16
> **kansasnoob said:**
> When you say, "Ubiquity fails all the time on real hardware", we really need much more detailed info. That will help those of us that do a lot of iso-testing to try and reproduce the exact steps leading up to the crash or failure ;)
I really respect all the effort you have put into making this Ubuntu release awesome.  On this point though, I have to take exception with your point-of-view.

There's nothing inaccurate about the statement,  "Ubiquity fails all the time on real hardware" and that fact has nothing  to do with the quality of bug reports on Launchpad.

Lubuntu is the *only* iso that has successfully installed on any machine I have (and am willing to risk).

Since 22-Mar, I have reported a fatal crashing bug in Ubiquity that prevents install from the amd64 desktop iso. As I can reproduce it at will, there are 3 duplicates of the same bug (latest is #973450):
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/973450](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/973450)
[https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/965719](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/965719)
[https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/962455](https://bugs.launchpad.net/ubuntu/+source/partman-base/+bug/962455)
The most recent two (965719 from the 26th March and 973450) are both on the qa iso tracker. (Note: I didn't assign the original bug to partman-base - Colin did).

Despite this bug having been commented on by 2 ubu devs, I had to debug the source of the crash myself despite the fact that simply loading the offending binary into gdb was sufficient to uncover the source of the crash. It will be interesting to see if this crash gets fixed prior to release.

Since 26-Mar (which was my first attempt at installing from the amd64 alternate iso), every attempt to install from the alternate iso results in the debian-installer hanging -- or rather, that's what most users will think that experience it.

That's bug# 975198 ([https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/975198](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/975198)).
It's been on the qa iso tracker since the 10th of April.

Despite the fact that it's a fatal hang, that bug has not even been triaged yet. So again, I debugged the hang myself to discover that it's because a necessary HID driver is not included on the alternate iso so keyboard input is impossible.

Something else to consider about bugs relating to "real hardware":  the apport stack backtrace that runs on bugs in Launchpad automatically marks bugs as 'Invalid' where a stack backtrace could not symbolically be resolved from the repositories.  I would be willing to bet a substantial sum that there are a lot of *valid* bugs which magically disappear this way and thus never get triaged, much less resolved.

---

### Post by kansasnoob on 2012-04-16
> **nm_geo said:**
> In the last iso tests I ran 20120414 all installed on hardware none of the isos failed.  I installed Lubuntu precise amd64, i386 and some alternates as well.  I would also question that statement as well, I even installed the amd64 versions of Ubuntu and Xubuntu with no issues. I did have a ubiquity bug earlier prior to that date but it has not showed up in recent spins. All those tests are archived on the iso-tracker.

The last images I tried were on the 13th and I only encountered one minor bug with the Ubuntu image. When I say "minor" I mean extremely nit-picky :redface:

In fact it's more of a "gosh I wish they'd change this design" thing than a bug.

That's why I'm requesting more info about how to try and reproduce these installer failures.

Slightly OT but did you see these:

[http://ubuntuforums.org/showthread.php?t=1959675](http://ubuntuforums.org/showthread.php?t=1959675)

[http://ubuntuforums.org/showpost.php?p=11847760&postcount=103](http://ubuntuforums.org/showpost.php?p=11847760&postcount=103)

Your opinion matters to me :D

---

### Post by amjjawad on 2012-04-16
> **cariboo907 said:**
> Probably not, but there are quite a few changes coming in QA and with the U+1 testing team wiki's.

I'm in the process of creating a new sticky for the QQ dev cycle, I'll be sure to mention it. :)

Yes, that would be great, thanks a lot :)
It is very important IMHO because I for one wasn't aware of that until few months ago!

So, I guess we will expect a better and a smoother process when testing 12.10 :)

All the best!

---

### Post by amjjawad on 2012-04-16
> **forestpiskie said:**
> As was said - you are not alone ;)

Yeah, kind of a relief but in the same time, little bit sad :(

Maybe if we could explain how things are working on the Wiki Area, that might help new comers? sometimes, even for me, I find it hard to deal with Wiki Pages not in term of formatting only but everything like organization, etc etc.

IMHO, rather than creating new pages, updating, etc ... we need a page to explain how everything is working when it comes to a Wiki Page/Area. I'm sure they are MANY who would love to help but when they face the fact that Wiki Pages/System is not that friendly and hard to find some easy help about it, they will be demotivated.

I don't know, I have lots of ideas but not sure how to start or put that in words :(

---

### Post by amjjawad on 2012-04-16
> **jerrylamos said:**
> When's the next development release start?

Jerry

[https://wiki.ubuntu.com/QReleaseSchedule](https://wiki.ubuntu.com/QReleaseSchedule)

---

### Post by nm_geo on 2012-04-16
> **kansasnoob said:**
> The last images I tried were on the 13th and I only encountered one minor bug with the Ubuntu image. When I say "minor" I mean extremely nit-picky :redface:

In fact it's more of a "gosh I wish they'd change this design" thing than a bug.

That's why I'm requesting more info about how to try and reproduce these installer failures.

Slightly OT but did you see these:

[http://ubuntuforums.org/showthread.php?t=1959675](http://ubuntuforums.org/showthread.php?t=1959675)

[http://ubuntuforums.org/showpost.php?p=11847760&postcount=103](http://ubuntuforums.org/showpost.php?p=11847760&postcount=103)

Your opinion matters to me :D

I really like that write-up.

[http://ubuntuforums.org/showpost.php?p=11847760&postcount=103](http://ubuntuforums.org/showpost.php?p=11847760&postcount=103)

I have not done any mini-iso installs in the last two months , but it is always a good option and I think your links and explanation are good.

---

### Post by amjjawad on 2012-04-16
> **nm_geo said:**
> I have not done any mini-iso installs in the last two months , but it is always a good option and I think your links and explanation are good.

I have done a mini-iso installation few days ago and the result was amazing. It was a long process as I had to disconnect the HDD, connect it to another machine, etc etc.

[http://ubuntuforums.org/showpost.php?p=11832431&postcount=152](http://ubuntuforums.org/showpost.php?p=11832431&postcount=152)

Oh yes, that 1999 or 1998 machine is working until now despite the current condition :D

---

### Post by Elfy on 2012-04-16
> **amjjawad said:**
> ...

I don't know, I have lots of ideas but not sure how to start or put that in words :(

Then come speak to us - there's a link in my sig if you don't normally IRC - if you do #ubuntu-wiki

---

### Post by amjjawad on 2012-04-16
> **forestpiskie said:**
> Then come speak to us - there's a link in my sig if you don't normally IRC - if you do #ubuntu-wiki

IRC is not my cup of tea. I did force myself to use it and like it but, I failed.
Is there any other way?

---

### Post by kansasnoob on 2012-04-17
> **amjjawad said:**
> Very valuable note but is that mentioned anywhere on our Wiki? I mean Ubuntu in general?

Short answer, yes. From the [Ubuntu home page]("http://www.ubuntu.com/") scroll to the bottom and click on Community > Get involved:

[ATTACH]216178[/ATTACH]

That will take you to:

[http://www.ubuntu.com/community/get-involved](http://www.ubuntu.com/community/get-involved)

Scroll down and click on "Testing" and you'll end up here:

[https://wiki.ubuntu.com/Testing](https://wiki.ubuntu.com/Testing)

Scroll down to:

> How do I get involved?

   1. Read about the activities performed by the Ubuntu Testing team. 

and click on "activities". That will take you here:

[https://wiki.ubuntu.com/Testing/Activities](https://wiki.ubuntu.com/Testing/Activities)

I do only iso-testing and I've done a poor job of keeping up with some of the changes at the [QA tracker]("http://iso.qa.ubuntu.com/") but I try :D

---

### Post by kansasnoob on 2012-04-17
> **amjjawad said:**
> IRC is not my cup of tea. I did force myself to use it and like it but, I failed.
Is there any other way?

I'm in the same boat :(

I generally blame my vision, and while that's partly true, the greatest hurdle is "speed". Things simply move too fast on IRC .......... sometimes I'm quick, but more often I'm slow as molasses in January.

Another thing is "mailing lists". I find that if I'm involved in too many projects I end up spending so much time just parsing through emails that I have no time to actually get anything done.

I used to be a multi-tasking fool, but now I'm just a fool :lolflag:

Ultimately I recommend finding what you're comfortable with and concentrating on that. I know recently I've overwhelmed my self at times and then I just end up doing a lousy job at everything, and I get grouchy, start biting at people, etc ........... and I especially hate being that way :oops:

---

### Post by amjjawad on 2012-04-17
> **kansasnoob said:**
> I'm in the same boat :(

I generally blame my vision, and while that's partly true, the greatest hurdle is "speed". Things simply move too fast on IRC .......... sometimes I'm quick, but more often I'm slow as molasses in January.

Another thing is "mailing lists". I find that if I'm involved in too many projects I end up spending so much time just parsing through emails that I have no time to actually get anything done.

I used to be a multi-tasking fool, but now I'm just a fool :lolflag:

Ultimately I recommend finding what you're comfortable with and concentrating on that. I know recently I've overwhelmed my self at times and then I just end up doing a lousy job at everything, and I get grouchy, start biting at people, etc ........... and I especially hate being that way :oops:

As always, I've been there too and still so we are in the same page and you are not alone :)

---

### Post by nm_geo on 2012-04-17
> **amjjawad said:**
> As always, I've been there too and still so we are in the same page and you are not alone :)

You guys are a mess.. ):P

Kansas we ain't got time for IRC :p

amjjawad as busy as you are you ain't got time for IRC either :p

Hey I got a full set of Lubuntu Desktop amd64 iso tests in last night 7 tests in all. I ain't got time for IRC  :lolflag: 
I do agree that we should all find our niche and do our best with it. Like kansas mine is iso-testing also like him I do get irritated with users who will not listen.  My computer and the isos always listen and never argue.. That be my niche.. I am so looking forward to the next big testing run starting on the 19th. However, I think few new Bugs will be found (perhaps I will be wrong).

---

### Post by kansasnoob on 2012-04-17
> **nm_geo said:**
> You guys are a mess.. ):P

Kansas we ain't got time for IRC :p

amjjawad as busy as you are you ain't got time for IRC either :p

Hey I got a full set of Lubuntu Desktop amd64 iso tests in last night 7 tests in all. I ain't got time for IRC  :lolflag: 
I do agree that we should all find our niche and do our best with it. Like kansas mine is iso-testing also like him I do get irritated with users who will not listen.  My computer and the isos always listen and never argue.. That be my niche.. I am so looking forward to the next big testing run starting on the 19th. However, I think few new Bugs will be found (perhaps I will be wrong).

Don't burn yourself out before the critical testing during the week of the 23rd ;)

---

### Post by nm_geo on 2012-04-17
> **kansasnoob said:**
> Don't burn yourself out before the critical testing during the week of the 23rd ;)

Yeah, I know but then I read where so-and-so had a failed iso install and I find all my testing stuff and start checking to see if it's their hardware or a common problem. I am trying to leave them alone.. but is is like an addiction.. HELP ME.. :p

---

### Post by kansasnoob on 2012-04-17
> **nm_geo said:**
> Yeah, I know but then I read where so-and-so had a failed iso install and I find all my testing stuff and start checking to see if it's their hardware or a common problem. I am trying to leave them alone.. but is is like an addiction.. HELP ME.. :p

You'll notice I asked for more info. I tried an Lubuntu live i386 install this AM and had no problem, it was a manual install - reusing an existing partition - on real hardware and I encountered no problem at all.

I sort of think if we ask for more info and hear nothing we should just disregard that statement. Launchpad does it ;)

---

### Post by nm_geo on 2012-04-17
> **kansasnoob said:**
> You'll notice I asked for more info. I tried an Lubuntu live i386 install this AM and had no problem, it was a manual install - reusing an existing partition - on real hardware and I encountered no problem at all.

I sort of think if we ask for more info and hear nothing we should just disregard that statement. Launchpad does it ;)

Agreed +1  I state I did seven installs on hardware with no issues and then I read that "ubiquity always falls" Always..
Makes me feel like they do not believe what we say.. The i386 and the amd64 Lubuntu Desktop completed clean and guess what they were all ubiquity installs.  That is why I need to test isos and applications and only visit forum ever now and then to gain information.. Don't get me wrong I will always do an alternate install when I want to keep the version,, Ubiquity and the migration assistant are not my favorite tools.

---

### Post by marinara on 2012-04-19
hey i need some help.  I have installed precise, i noticed in lubuntu precise that there is no 'software sources'  app under the preferences menu.

Is this intentional, or an omission?  Should I file a bug.
I searched the mailing list 
I'd ask on the mailing list but I've been kinda shooting my mouth off on the list 
and i have to lay low for at least 12 hours

---

### Post by jerrylamos on 2012-04-19
> **nm_geo said:**
> In the last iso tests I ran 20120414 all installed on hardware none of the isos failed. 
Invariably at some time during development since Dapper Drake, install doesn't/won't work on one or another of my now five test pc's: a tower, a netbook, a notebook Pentium M, a 2005 Thinkpad 512 MB 1 GHZ, a wide notebook.  So I write launchpad bugs.  Some get a number of "affects me", some get fixed, most usually (not always) get fixed by RC time.

At the moment Xbuntu and Lubuntu won't install on the Thinkpad with faiures about 1/3 of the way through "copying files".  Yes there's launchpad bugs written. I'm not a developer, but the syslog seems to indicate some Python problem.  Precise Alpha Lubuntu installed fine and is still running updated on another partition.

Jerry

---

### Post by nm_geo on 2012-04-19
> **jerrylamos said:**
> Invariably at some time during development since Dapper Drake, install doesn't/won't work on one or another of my now five test pc's: a tower, a netbook, a notebook Pentium M, a 2005 Thinkpad 512 MB 1 GHZ, a wide notebook.  So I write launchpad bugs.  Some get a number of "affects me", some get fixed, most usually (not always) get fixed by RC time.

At the moment Xbuntu and Lubuntu won't install on the Thinkpad with faiures about 1/3 of the way through "copying files".  Yes there's launchpad bugs written. I'm not a developer, but the syslog seems to indicate some Python problem.  Precise Alpha Lubuntu installed fine and is still running updated on another partition.

Jerry

I understand Jerry.  I encountered a regressive Bug on the 20120418 spins last night.  The migration of documents and settings (Ubiquity) had it earlier in the cycle too.  Strangely, I could do a manual (something else) install and it was clean. Trying full drive and re-size both failed on the same error and both amd64 and i386 flavors of Lubuntu precise.

Hopefully the Pre-release spins will be clean again soon. 

[https://bugs.launchpad.net/bugs/985358](https://bugs.launchpad.net/bugs/985358)

I guess that is why we iso-test.
Out

---

### Post by sudodus on 2012-04-19
> **marinara said:**
> hey i need some help.  I have installed precise, i noticed in lubuntu precise that there is no 'software sources'  app under the preferences menu.

Is this intentional, or an omission?  Should I file a bug.
I searched the mailing list 
I'd ask on the mailing list but I've been kinda shooting my mouth off on the list 
and i have to lay low for at least 12 hours
I find 'Lubuntu Software Center' and 'Synaptic' under the 'System Tools' menu. I hope you find it too, otherwise something is wrong with your installation ;-)

---

### Post by kansasnoob on 2012-04-19
> **marinara said:**
> hey i need some help.  I have installed precise, i noticed in lubuntu precise that there is no 'software sources'  app under the preferences menu.

Is this intentional, or an omission?  Should I file a bug.
I searched the mailing list 
I'd ask on the mailing list but I've been kinda shooting my mouth off on the list 
and i have to lay low for at least 12 hours

Intentional, from far upstream. You must now either go to Update Manager > Settings or Synaptic > Settings > Repositories.

---

### Post by MG&amp;TL on 2012-04-19
Or, from Lubuntu Software Centre, Preferences, Open Software Sources.

---

### Post by ranch hand on 2012-04-19
> **marinara said:**
> hey i need some help.  I have installed precise, i noticed in lubuntu precise that there is no 'software sources'  app under the preferences menu.

Is this intentional, or an omission?  Should I file a bug.
I searched the mailing list 
I'd ask on the mailing list but I've been kinda shooting my mouth off on the list 
and i have to lay low for at least 12 hours
Go to Synaptic>Settings>Repositories and you will find the same thing.

---

### Post by jerrylamos on 2012-04-19
Got totally frustrated with trying Lubuntu Precise install see Launchpad Bug #978481.  Getting tired of precise B2 lubuntu zsync and install failures every day.

Well, maybe it's my hardware or how I install?  Let me try a test:

Downloaded brand new Linux Mint 12 LXDE.  Flew right through install running great. Polished.  

My hardware and my keyboard/mouse fingers are fine!  Now Mint 12 LXDE is based on 3.0.0-12 stable ubuntu so I expected it would run and it does.

Jerry

---

### Post by sudodus on 2012-04-20
> **jerrylamos said:**
> Got totally frustrated with trying Lubuntu Precise install see Launchpad Bug #978481.  Getting tired of precise B2 lubuntu zsync and install failures every day.

Well, maybe it's my hardware or how I install?  Let me try a test:

Downloaded brand new Linux Mint 12 LXDE.  Flew right through install running great. Polished.  

My hardware and my keyboard/mouse fingers are fine!  Now Mint 12 LXDE is based on 3.0.0-12 stable ubuntu so I expected it would run and it does.

Jerry

Jerry, I know how it feels. I'm trying to get some response about the bug that makes mplayer2 useless in my 32-bit computers. I get only machine response or adminstrative response. Who cares if Lubuntu's only video player works or not?! (Yes, vlc can be installed and works, but why deliver something that doesn't work in many of the target computers with older 32-bit cpus?)

I am using rsync and I test it versus the md5sum (with small scripts), and it has not failed yet. Does the zsync download/upgrade fail sometimes for you?

Sudden

---

### Post by jerrylamos on 2012-04-20
> **sudodus said:**
> Jerry, I know how it feels. I'm trying to get some response about the bug that makes mplayer2 useless in my 32-bit computers. I get only machine response or adminstrative response. Who cares if Lubuntu's only video player works or not?! (Yes, vlc can be installed and works, but why deliver something that doesn't work in many of the target computers with older 32-bit cpus?)

I am using rsync and I test it versus the md5sum (with small scripts), and it has not failed yet. Does the zsync download/upgrade fail sometimes for you?

Sudden

First paragraph, I don't know if mplayer2 works on Linux Mint 12 LXDE 32bit but it might be worth a whirl.  Very quick and polished on my older laptops.  Mint 12 is based on stable Ubuntu at Ocelot level so is very familiar.  

Second paragraph, I've been using zsync no problem.  It does a checksum which works.  When I was using rsync I did an exec that would do an md5sum which isn't necessary with zsync.

I've been using Ubuntu since Dapper Drake Beta.  Lately Ubuntu's entire direction is "pseudo touch screen tablet look and feel" with all the attendant limitations and high speed exotic advanced feature requirements. Straightforward fast efficient capable are not on the plate. There are other fish in the sea.

Jerry

---

### Post by nm_geo on 2012-04-20
> **sudodus said:**
> Jerry, I know how it feels. I'm trying to get some response about the bug that makes mplayer2 useless in my 32-bit computers. I get only machine response or adminstrative response. Who cares if Lubuntu's only video player works or not?! (Yes, vlc can be installed and works, but why deliver something that doesn't work in many of the target computers with older 32-bit cpus?)

I am using rsync and I test it versus the md5sum (with small scripts), and it has not failed yet. Does the zsync download/upgrade fail sometimes for you?

Sudden

I rarely try to watch a DVD on my Dell D620, but I saw your Bug and thought perhaps I am spending too much time installing isos.  So I plugged in a movie a local production made. It plays on one of my i386 installs so the mplayer seems to work on my hardware.  Of course, I can run and test 64 or 32 bit kernels on this laptop.

The Lubuntu philosophy (low resource impact) generally decides the players that are chosen for the iso, but if you find a player that will not work with your hardware.  I would say "just make it your way" find one that works.  

As to the other question, I zysnc six or seven isos daily during Beta2 and Pre-release testing and they all complete well. Sometimes I start up 2 or 3 at the same time more than my wifi likes ..:p

---

### Post by teh603 on 2012-04-21
> **jerrylamos said:**
> I've been using Ubuntu since Dapper Drake Beta.  Lately Ubuntu's entire direction is "pseudo touch screen tablet look and feel" with all the attendant limitations and high speed exotic advanced feature requirements. Straightforward fast efficient capable are not on the plate. There are other fish in the sea.
Dunno. I'm sure someone could do a pseudo touch screen or an actual touch screen interface for Ubuntu, and do it better than Unity. It'd be an ambitious project, though. Modern programmers just can't write code without trying to push the limits of modern hardware.

---

### Post by MG&amp;TL on 2012-04-22
> **teh603 said:**
>  Modern programmers just can't write code without trying to push the limits of modern hardware.

...on the Lubuntu testing thread. :P

I like unity, personally, even for my desktop (gasp!) but that's personal choice.

---

### Post by jerrylamos on 2012-04-22
> **MG&TL said:**
> ...on the Lubuntu testing thread. :P

I like unity, personally, even for my desktop (gasp!) but that's personal choice.
That's the point, choices.

I'd like to keep choices open and Lubuntu alive vs. the overwhelming complexity and requirements for ever faster ever bigger ever $$$ ever Compiz growth.

So if someone likes a lot of eye candy and huge finger sized icons meaningless (to me) chewing up screen they can "choose" it.

Some of the rest of us prefer efficient, light, fast, low overhead, I can read program names in a sorted list a whole lot faster than trying to figure out "what does that icon mean?", ...  

Now I do run Unity wait - wait - wait - because since Dapper Drake I'm in the habit of testing whatever ubuntu throws over the wall with a rock tied to it.

Right now Ubuntu Lubuntu Xubuntu won't install on one of my favorite laptops, fails during the copy files step (bugs written).  Just to see if the hardware and my setup was O.k. tried installing Linux Mint LXDE.  ZOOM!  No problem.  Sparkles.  No big Purple Splotch like something spilled on the floor (your choice).  Mint's based on Oneiric haven't tried Oneiric on the laptop since I'm tired of beating my head on the wall with ubuntu.

Interesting contrast, last lubuntu that would install was Alpha, now current with thousands of updates, a bit sluggish methinks, or boot Mint LXDE fresh install zoom.

Some of my showstoppers on Launchpad get fixed by release some don't.  I'll see.

Jerry

---

### Post by kansasnoob on 2012-04-22
> **MG&TL said:**
> ...on the Lubuntu testing thread. :P

I like unity, personally, even for my desktop (gasp!) but that's personal choice.

+1!

In my case I like Unity in certain scenarios (with screens up to about 19"), and in other scenarios I prefer a more "win 98ish" look with only a bottom panel, so what?

It gets old having people bash Unity or any other DE (or distro)! I don't go to the Mint or Fedora forums and trash their distro just because I prefer Ubuntu :)

If Ubuntu and/or it's derivatives really make someone mad they should just go away, no need for a nasty break-up ;)

---

### Post by kansasnoob on 2012-04-22
> **jerrylamos said:**
> That's the point, choices.

I'd like to keep choices open and Lubuntu alive vs. the overwhelming complexity and requirements for ever faster ever bigger ever $$$ ever Compiz growth.

So if someone likes a lot of eye candy and huge finger sized icons meaningless (to me) chewing up screen they can "choose" it.

Some of the rest of us prefer efficient, light, fast, low overhead, I can read program names in a sorted list a whole lot faster than trying to figure out "what does that icon mean?", ...  

Now I do run Unity wait - wait - wait - because since Dapper Drake I'm in the habit of testing whatever ubuntu throws over the wall with a rock tied to it.

Right now Ubuntu Lubuntu Xubuntu won't install on one of my favorite laptops, fails during the copy files step (bugs written).  Just to see if the hardware and my setup was O.k. tried installing Linux Mint LXDE.  ZOOM!  No problem.  Sparkles.  No big Purple Splotch like something spilled on the floor (your choice).  Mint's based on Oneiric haven't tried Oneiric on the laptop since I'm tired of beating my head on the wall with ubuntu.

Interesting contrast, last lubuntu that would install was Alpha, now current with thousands of updates, a bit sluggish methinks, or boot Mint LXDE fresh install zoom.

Some of my showstoppers on Launchpad get fixed by release some don't.  I'll see.

Jerry

But Linux Mint LXDE is currently based on Oneiric! Did Oneiric run on the same machine?

If Ubuntu just makes you that mad why not give it a rest?

Sheesh.

---

### Post by abyrne on 2012-04-22
Latest Lubuntu 12.04 Live-Image installs perfectly on an AcerPower FH (common business desktop). Checkbox ran cleanly, lest one failed test with the colored bars and static...

---

### Post by nm_geo on 2012-04-22
Okay this the Lubuntu 12.04  testing thread right?  :P

Just an update on the recent RC testing Lubuntu has been testing really well with a few minor bugs.

---

### Post by teh603 on 2012-04-23
Ok, minor issue here. I accidentally clicked on "don't show any more notifications of this type," and now I'm not seeing the notifier to tell me when I've got an internet connection or not. Does anyone know how to re-enable these notifications?

---

### Post by as2000 on 2012-04-24
Ok have Lubuntu precise installed on my Eee pc netbook and it works pretty good. The software center however is very slow in operation. It does work, but slow gathering updates and overall operation.

---

### Post by teh603 on 2012-04-24
> **as2000 said:**
> Ok have Lubuntu precise installed on my Eee pc netbook and it works pretty good. The software center however is very slow in operation. It does work, but slow gathering updates and overall operation.Software Center is junk. I've never been able to install anything with it. Just use Synaptic or the terminal.

---

### Post by jerrylamos on 2012-04-24
> **teh603 said:**
> Software Center is junk. I've never been able to install anything with it. Just use Synaptic or the terminal.

Hmmm...sounds like another case of "ubuntu Unity pseudo tablet eye candy".

And you're right, we do have choices like apt-get and synaptic.  First thing I do on a ubuntu install is ditch the "software center" hieroglyphic and install synaptic, synaptic is no longer included, it's not a feature of a pseudo tablet.

Synaptic's even useful for finding and deleting leftover "linux image" and "header" files that update - upgrade left laying around.

And of course I use synaptic to set software sources - I like partners I don't like "unknown" sources and update get sets to "never" since I use aptitude.

I presume the "tablet" philosophy is hard disks are so big and memory is so big clutter doesn't matter, ergo nobody needs to clean up.

Choices!  I can still do things the "linux" way and others can do things "pseudo tablet".

Enjoy.

Jerry

---

### Post by Mathor on 2012-04-24
> **jerrylamos said:**
> Hmmm...sounds like another case of "ubuntu Unity pseudo tablet eye candy".

And you're right, we do have choices like apt-get and synaptic.  First thing I do on a ubuntu install is ditch the "software center" hieroglyphic and install synaptic, synaptic is no longer included, it's not a feature of a pseudo tablet.

Synaptic's even useful for finding and deleting leftover "linux image" and "header" files that update - upgrade left laying around.

And of course I use synaptic to set software sources - I like partners I don't like "unknown" sources and update get sets to "never" since I use aptitude.

I presume the "tablet" philosophy is hard disks are so big and memory is so big clutter doesn't matter, ergo nobody needs to clean up.

Choices!  I can still do things the "linux" way and others can do things "pseudo tablet".

Enjoy.

Jerry

Maybe I'm crazy, as I'm currently using 10 gb of my tb harddrive. I'm obsessive over retaining space even though I don't necessarily need to be, but that's just part of good computing practices.

---

### Post by teh603 on 2012-04-24
> **jerrylamos said:**
> Hmmm...sounds like another case of "ubuntu Unity pseudo tablet eye candy".
If I want pseudo-tablet (or real tablet for the red Dell Duo), I have Kubuntu 64-bit with the Plasma Netbook interface.

---

### Post by cariboo on 2012-04-24
> **jerrylamos said:**
> Hmmm...sounds like another case of "ubuntu Unity pseudo tablet eye candy".

And you're right, we do have choices like apt-get and synaptic.  First thing I do on a ubuntu install is ditch the "software center" hieroglyphic and install synaptic, synaptic is no longer included, it's not a feature of a pseudo tablet.

Synaptic's even useful for finding and deleting leftover "linux image" and "header" files that update - upgrade left laying around.

And of course I use synaptic to set software sources - I like partners I don't like "unknown" sources and update get sets to "never" since I use aptitude.

I presume the "tablet" philosophy is hard disks are so big and memory is so big clutter doesn't matter, ergo nobody needs to clean up.

Choices!  I can still do things the "linux" way and others can do things "pseudo tablet".

Enjoy.

Jerry

This is getting a long way off topic, we know you don't have the hardware to run Unity 3D properly, you don't have to mention it in every post in this Lubuntu thread.

---

### Post by Guilden_NL on 2012-04-24
I am looking for where a list of known bugs is kept.  Have read through this thread and only see references to individual bug reports.

Sorry if it's obvious, but I can't seem to locate one.

I have a laptop with Meerkat and one on 11.04 that I want to bring up to date.  The tower that I am writing this on was the most involved Linux install since 1994, and I don't want to replicate that mess, so am very interested in a comprehensive bug list. (This was a clean install to Lubuntu 11.10)

Thanks for your consideration.

---

### Post by sudodus on 2012-04-24
> **Guilden_NL said:**
> I am looking for where a list of known bugs is kept.  Have read through this thread and only see references to individual bug reports.

Sorry if it's obvious, but I can't seem to locate one.

I have a laptop with Meerkat and one on 11.04 that I want to bring up to date.  The tower that I am writing this on was the most involved Linux install since 1994, and I don't want to replicate that mess, so am very interested in a comprehensive bug list. (This was a clean install to Lubuntu 11.10)

Thanks for your consideration.
You can find bug-lists at [[COLOR="black"][COLOR="Red"]_https://launchpad.net/_[/COLOR][/COLOR]]("https://launchpad.net/")

If you create a user ID and start using it, you can read and write bugs for many things including the Ubuntu flavours.

*Edit: My general advice to avoid bugs is to backup your personal data and make clean installs of the new version 12.04 LTS a few weeks after the official release*.

---

### Post by jerrylamos on 2012-04-24
> **teh603 said:**
> If I want pseudo-tablet (or real tablet for the red Dell Duo), I have Kubuntu 64-bit with the Plasma Netbook interface.

Any idea how ubuntu support is holding up for Kubuntu?  Certainly seems to be a bunch of Kubuntu fans.

Jerry

---

### Post by sudodus on 2012-04-24
> **jerrylamos said:**
> Any idea how ubuntu support is holding up for Kubuntu?  Certainly seems to be a bunch of Kubuntu fans.

Jerry
I hope and think it will be on the same level as [LX]ubuntu :-)
By the way, have you tested the 'low fat KDE + Openbox'? I needs much less memory and makes the computer faster than the full Kubuntu.

---

### Post by jerrylamos on 2012-04-24
> **Guilden_NL said:**
>   The tower that I am writing this on was the most involved Linux install since 1994, and I don't want to replicate that mess...Maybe I'm getting brainwashed - I do a lot of installs for this development testing on  On 4 of my 5 pc's lately with precise ubuntu and lubuntu install goes through fine, like a breeze to me on Beta 2.  

Now any Alpha can be another matter I'm getting set for 12.10 Quetzal hang on to my hat.  Precise install fails on my Thinkpad R31 on lubuntu, xubuntu, ubuntu - it's easy enough to set up but boom the install window vanishes.  Bug written.  Well, lubuntu 11.10 Oneiric Ocelot installs fine on the R31 so I can use the R31 O.K. at close to current level.

Join the fun.

Jerry

---

### Post by MG&amp;TL on 2012-04-24
Hi, teh603, I'm assuming you're referring to Lubuntu Software Centre?

If so, we're planning to make a vala version (which should be a lot quicker) but we're waiting for a particular library to mature so we can use it without it crashing all of the time. Sorry!

---

### Post by Guilden_NL on 2012-04-24
I've had an account on Launchpad since, well...its launch. 

I took a little time to search it while multitasking, and here's the link:
[https://launchpad.net/ubuntu/+milestone/ubuntu-12.04]("https://launchpad.net/ubuntu/+milestone/ubuntu-12.04")  From memory, looks like more than I remember in Meerkat (when I last checked before updating).

@jerrylamos,
I started with Ubuntu back on Dapper and have installed clean on somewhere around 30 different systems since.  For whatever reason Lubuntu 11.10 Final Release clean installs caused more problems for me than all other Ubuntu installed combined.  I spent approximately 20 hrs just getting it running on this tower alone which ran Natty/Gnome just fine.  I came >thisclose< to giving up on Lubuntu and heading somewhere else.  But I hung in there and got it up and running.  I confess to running RHEL on all of my servers because that's what I use for my work architectures, but have stayed with Ubuntu for all of our laptops/desktops at home.  I have to say, there wasn't a single clean install of Lubuntu 11.10 in the bunch, and none of the problems were related to the desktop, everything was down to the core 11.10 versions having issues.  My HW runs from a 2004 Toshiba Satellite laptop with 1 GB of RAM all the way to this 24 core tower with 96Gb of RAM and a few terabytes of RAID disc.  So it wasn't just one system.

Ah well, now that I have the bug list, I will follow it for a few weeks before taking the plunge.

---

### Post by teh603 on 2012-04-24
> **MG&TL said:**
> Hi, teh603, I'm assuming you're referring to Lubuntu Software Centre?

If so, we're planning to make a vala version (which should be a lot quicker) but we're waiting for a particular library to mature so we can use it without it crashing all of the time. Sorry!I'm talking about the whole thing. I've never been able to get it work; not the regular Ubuntu one, and not the Kubuntu one either.

---

### Post by amjjawad on 2012-04-24
> **teh603 said:**
> I'm talking about the whole thing. I've never been able to get it work; not the regular Ubuntu one, and not the Kubuntu one either.

I don't like Software centers but will never use "junk" on that. There are many are killing themselves to make these "junk" as good as possible so if we don't have a feedback or a suggestion to make things better, I would suggest NOT to use "junk" to show our appreciation :)

---

### Post by amjjawad on 2012-04-24
I'm going to miss this thread ... I had great time here and we discussed a lot of issues here ... few days to go and a new thread (maybe - not sure yet) is waiting ... hope all will go will with Lubuntu 12.04 and with all the other variants.

6 months and all of us have done a great job indeed. No exception, everyone did something and for that, thanks a lot for everything you have done :)

I feel bad because I haven't done much this time. Things were crazy for the last 6 months and I do hope the next 6 months will be better :)

Time passed so quickly ... your contributions are highly appreciated, thanks a lot on behalf of Lubuntu Team :)

For those who are masters in Testing, you may have a new student that will seek your help sooner or later so be ready :D

---

### Post by jerrylamos on 2012-04-24
> **amjjawad said:**
> I'm going to miss this thread ... I had great time here and we discussed a lot of issues here ... few days to go and a new thread (maybe - not sure yet) is waiting ... hope all will go will with Lubuntu 12.04 and with all the other variants... :D

I expect some precise bugs for the first week or two after "release".  Meanwhile I'll be watching for pre-Alpha Quetzal, replace precise with q_____ in sources.list and update/upgrade....usually works until around Alpha time when the @#$%& hits the fan.

Jerry

---

### Post by nm_geo on 2012-04-24
> **jerrylamos said:**
> Any idea how ubuntu support is holding up for Kubuntu?  Certainly seems to be a bunch of Kubuntu fans.

Jerry

You might want to give this a read Jerry.

[http://www.phoronix.com/scan.php?page=news_item&px=MTA4NTM](http://www.phoronix.com/scan.php?page=news_item&px=MTA4NTM)

---

### Post by kansasnoob on 2012-04-25
> **amjjawad said:**
> I'm going to miss this thread ... I had great time here and we discussed a lot of issues here ... few days to go and a new thread (maybe - not sure yet) is waiting ... hope all will go will with Lubuntu 12.04 and with all the other variants.

6 months and all of us have done a great job indeed. No exception, everyone did something and for that, thanks a lot for everything you have done :)

I feel bad because I haven't done much this time. Things were crazy for the last 6 months and I do hope the next 6 months will be better :)

Time passed so quickly ... your contributions are highly appreciated, thanks a lot on behalf of Lubuntu Team :)

For those who are masters in Testing, you may have a new student that will seek your help sooner or later so be ready :D

You've done a lot my good friend :)

I very much hope you'll take time to open a thread just like this in QQ Ubuntu +1 :D

---

### Post by amjjawad on 2012-04-25
> **kansasnoob said:**
> You've done a lot my good friend :)

I'm not happy for what I've done which is little :( but thanks a lot for your very nice words :)

> I very much hope you'll take time to open a thread just like this in QQ Ubuntu +1 :grin:

I will do my best and I do hope this time, I can take a better role in testing but that will require some help from you and others :D

I'm now ... well, have lots of plans but I can't put that on paper or start working on them. I don't know what is wrong.

I will send you a message later :)

---

### Post by amjjawad on 2012-04-25
Before this thread goes off, I mean locked, I want to ask about something.

Everyone knows on the release day and the days after that (say for the first week), there will be HUGE LOAD on the servers and downloading the iso won't be that easy like any other day. It's no secret.

Now, there was a discussion on **[Lubuntu Group on Facebook]("https://www.facebook.com/groups/lubuntu.official")** between other members and myself about New Fresh Installation VS Updating/Upgrading.
I understand in order to NOT put more load on the servers, it's much better to do:

```
sudo apt-get update && sudo apt-get upgrade
```My Two Qs are:

1- Will that be 100% enough and give 100&% the same result of installing the new ISO?
*I think the answer is yes but I'm in doubt so forgive me for asking something like that* :oops:

2- Is  ```
sudo apt-get dist-upgrade
``` needed? 
From my humble experience, I've never managed to upgrade the Kernel to a newer version unless I do "dist-upgrade" and I don't know of any other way to do that?!
Is there any other way? 

So, as a summary and in 1,2 and 3, what are the steps that one needs to do if and only if he/she has already installed Lubuntu for testing (say Beta or any other version) so there is no need to install the new ISO?

Thanks :)

Edit:
**Note that:**
Update Manager will update the Kernel but sudo apt-get upgrade for me, never updated my Kernel to a newer version.

---

### Post by nm_geo on 2012-04-25
> **amjjawad said:**
> Before this thread goes off, I mean locked, I want to ask about something.

Everyone knows on the release day and the days after that (say for the first week), there will be HUGE LOAD on the servers and downloading the iso won't be that easy like any other day. It's no secret.

Now, there was a discussion on **[Lubuntu Group on Facebook]("https://www.facebook.com/groups/lubuntu.official")** between other members and myself about New Fresh Installation VS Updating/Upgrading.
I understand in order to NOT put more load on the servers, it's much better to do:

```
sudo apt-get update && sudo apt-get upgrade
```My Two Qs are:

1- Will that be 100% enough and give 100&% the same result of installing the new ISO?
*I think the answer is yes but I'm in doubt so forgive me for asking something like that* :oops:

2- Is  ```
sudo apt-get dist-upgrade
``` needed? 
From my humble experience, I've never managed to upgrade the Kernel to a newer version unless I do "dist-upgrade" and I don't know of any other way to do that?!
Is there any other way? 

So, as a summary and in 1,2 and 3, what are the steps that one needs to do if and only if he/she has already installed Lubuntu for testing (say Beta or any other version) so there is no need to install the new ISO?

Thanks :)

Edit:
**Note that:**
Update Manager will update the Kernel but sudo apt-get upgrade for me, never updated my Kernel to a newer version.

First amjjawad I want to echo what kansas said, you are the first and most important part of the Lubuntu Team and you have done lots of good work.

1.) If you update & upgrade your precise 12.04 will be as good if not better than the final release iso. There might be some fixes you get that were not in the Final Iso spin.

2) If you already have the precise 12.04 you do not need to "sudo apt-get dist-upgrade"

3) When a new kernel becomes active it should be installed with the regular update & upgrade.  If you want to test a kernel that is not in the iso build we can go through that process later.

Again let me state that you IMHO are doing more good for Lubuntu than any of the testers.):P

---

### Post by jerrylamos on 2012-04-25
If you really want the latest kernel try
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
(better back up etc).  Tried it today, it works, still has my kernel wireless bug though.
I've been using zsync which also cuts down on server load by only downloading the differences in the .iso's.

I've had some problems (!) with apt-get and prefer
sudo aptitude update
sudo aptitude safe-upgrade
On occasion a kernel isn't loaded, then I do
sudo aptitude full-upgrade

Now in development I'll update/grade and after a while despite cleanup disk usage grows so I do a zsync new install.  Cleans things up nicely.

Been doing installs lately to test RC....going well except for the aforementioned wireless bug and lubuntu-xubuntu-ubuntu install failures on Thinkpad R31, bugs written.

Have fun,

Jerry

---

### Post by MG&amp;TL on 2012-04-25
Yes, please do one for the Quetzal.

Go, amjjawad, go!

---

### Post by amjjawad on 2012-04-25
> **nm_geo said:**
> First amjjawad I want to echo what kansas said, you are the first and most important part of the Lubuntu Team and you have done lots of good work.
Your words mean a lot to me and it's a huge relief because I was feeling so bad but I think this is a huge push and motivation so I won't let you guys down :)

> 1.) If you update & upgrade your precise 12.04 will be as good if not better than the final release iso. There might be some fixes you get that were not in the Final Iso spin.
Thank you for your reply. If truth to be told, I have never upgraded, I always do fresh new installation because most of my friends here and other users always recommend that. However, I'm very much willing to try the upgrade this time.

But, how is that some fixes that I might get which aren't in the final iso?


> 2) If you already have the precise 12.04 you do not need to "sudo apt-get dist-upgrade"
To put that on another words, and please correct me if I'm wrong, if I have 12.04 installed already (say Beta2), then to get 12.04 stable, I don't need to do "dist-upgrade", just apt-get upgrade, right?


> 3) When a new kernel becomes active it should be installed with the regular update & upgrade.  If you want to test a kernel that is not in the iso build we can go through that process later.
I'm sorry if I didn't explain that better. I'm not interested to test new Kernels, I was taking about upgrading the kernel say from:
3.2.0-20 >> 3.2.0-23

I have never managed to do that unless I do dist-upgrade because apt-get upgrade doesn't give me the latest Kernel.


> Again let me state that you IMHO are doing more good for Lubuntu than any of the testers.):P

Again, this means A LOT to me and I appreciate that but that doesn't mean I'm better, you guys are doing a HUGE and a GREAT job and I must learn from you sooner or later to join the testers group :)

Thank you!

---

### Post by amjjawad on 2012-04-25
> **MG&TL said:**
> Yes, please do one for the Quetzal.

Go, amjjawad, go!

As if I have another choice or as if I can resist that? :D you know me ;)

Good to see you because it's been ages!

I will do that when the sub-forum be ready :)

---

### Post by amjjawad on 2012-04-25
> **jerrylamos said:**
> If you really want the latest kernel try
[http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
(better back up etc).  Tried it today, it works, still has my kernel wireless bug though.

Thanks a lot for your advice but I always prefer to be in the safe side when it comes to Kernels. I use whatever available on the repositories which I can get by simple update/upgrade.

:)

---

### Post by PaulW2U on 2012-04-25
> **amjjawad said:**
> I will do that when the sub-forum be ready :)

I deleted Windows XP from my netbook this morning and installed Lubuntu 12.04. It's given the netbook a new lease of life and will prove very useful when I get everything set up the way I want and have all my programs installed. I'm very pleased to report that sound, video, wi-fi, and mobile broadband all worked perfectly without any fiddling around.

I doubt if I'll get involved in testing the next release but I'll certainly be following it's development ready for a possible upgrade in October.

---

### Post by amjjawad on 2012-04-25
Ok, on my ASUS F3F Laptop which is a test laptop, I just did:

```
uname -r
```shows:
```
3.2.0-23-generic
```I then did:
```
sudo apt-get update && sudo apt-get upgrade
```then rebooted

then:
```
uname -r
```which STILL shows:
```
3.2.0-23-generic
```I know there is no newer Kernel because:

```
sudo apt-get dist-upgrade
```doesn't show newer Kernel *(for example: 3.2.0-24-generic) *but ... generally, this is what I use to get newer one and I mean dist-upgrade whenever there is newer one available. I have always done that and "apt-get upgrade" never did.

From what I can tell so far, the final stable release of 12.04 will use: 3.2.0-23-generic.

---

### Post by amjjawad on 2012-04-25
> **PaulW2U said:**
> I deleted Windows XP from my netbook this morning and installed Lubuntu 12.04. It's given the netbook a new lease of life and will prove very useful when I get everything set up the way I want and have all my programs installed. I'm very pleased to report that sound, video, wi-fi, and mobile broadband all worked perfectly without any fiddling around.
I'm glad to know that :D
Thanks for choosing and using Lubuntu and thanks for your feedback!

This is what we (Lubuntu Team) want. We do our best to make many users as happy as possible by making almost everything as good as possible. Nothing is prefect and NO OS has it all but we listen and care :)

> I doubt if I'll get involved in testing the next release but I'll certainly be following it's development ready for a possible upgrade in October.

If you ever want to get involved, please check this: [https://wiki.ubuntu.com/Lubuntu/GettingInvolved](https://wiki.ubuntu.com/Lubuntu/GettingInvolved)

If you want to contact us at anytime, please: [https://wiki.ubuntu.com/Lubuntu/ContactUs](https://wiki.ubuntu.com/Lubuntu/ContactUs)

---

### Post by MG&amp;TL on 2012-04-25
> **amjjawad said:**
> As if I have another choice or as if I can resist that? :D you know me ;)

Good to see you because it's been ages!

I will do that when the sub-forum be ready :)

That is a fair point....I know how obsessive you are. :P

It has indeed been ages, I shall drop you an email.

---

### Post by jerrylamos on 2012-04-25
New kernel?  Depending on how adventurous you are, there's

linux-image-3.4.0-999-generic_3.4.0-999.201204250500_i386.deb

on 

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

I just tried it and it works fine for what I did, except for my Aironet wireless bug which is still there.  Workaround is to plug a Realtek card into the notebook.

Jerry

---

### Post by teh603 on 2012-04-25
> **PaulW2U said:**
> I deleted Windows XP from my netbook this morning and installed Lubuntu 12.04. It's given the netbook a new lease of life and will prove very useful when I get everything set up the way I want and have all my programs installed. I'm very pleased to report that sound, video, wi-fi, and mobile broadband all worked perfectly without any fiddling around.

I doubt if I'll get involved in testing the next release but I'll certainly be following it's development ready for a possible upgrade in October.Good to hear everything works. I've found most netbooks have fairly simple hardware that doesn't require a lot of screwball drivers- the Dell Duo being one of the notable exceptions with its whacked-to-hell BIOS and wonky touchscreen.

---

