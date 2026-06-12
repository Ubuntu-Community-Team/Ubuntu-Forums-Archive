---
title: "Just some general whining..."
date: 2008-06-01
forum: Testimonials &amp; Experiences
---

### Post by danson on 2008-06-01
So I went ahead and did the upgrade from gutsy to heron last night.  As with past upgrades, I ran into the same problems.  Things that worked don't after the upgrade.  Here are my pet peeves, but they basically boil down to 'it worked before, and now it's broke' --

1. video driver changes.  I've got an ATI video card in my laptop.  I use the proprietary driver because the open source driver doesn't (or at least hasn't) supported big desktop mode or clone mode.  With the upgrade, I was stuck at 800x600 resolution until I restarted several times and went through the 'fix X-server' procedure.  I'll find out if big desktop works tomorrow when I get my laptop back to work.  It worked before the upgrade, it should have worked just as well after.

2. wireless changes.  I've got a Broadcom wireless card in my laptop.  Every upgrade requires that I jump through hoops to get it running again.  I did the upgrade over my wireless network, but the upgrade didn't install the parts to make the Broadcom card continue to work.  Instead, the card was left non-functional, and to turn on the proprietary driver meant I needed to download another package. Kind of a pain, since the upgrade broke my ability to use my wireless network.  So I have to go find a cable and get plugged in.  It worked before the upgrade, it should have worked just as well after.

3. xscreensaver removed.  I thought just about everyone knows that xscreensaver is better than either gnome-screensaver or kde-screensaver.  I had it installed and properly configured, but the upgrade removed it.  Not just disabled it, but removed it from my system.  At least, the upgrade didn't remove the configuration files, so it was just a matter of reinstalling the package, but again, it worked before the upgrade, it shouldn't have been removed and should have just worked. 

Just getting this off my chest.  The video and wireless are pretty critical pieces for me, I always put off doing the upgrades because I know I'll have to spend a few hours fixing things that weren't broke.

---

### Post by danson on 2008-06-01
Another nit -- I opened a document with Open Office 2.4, and it whined about not having java installed.  Java is installed, I've got lots of Java, but still, I had to go find it for Open Office.  It worked before...

---

### Post by ke4ram on 2008-06-01
Probably security issues. Just to write this reply required another login (I just logged in 3 minutes ago). They are so busy protecting us from ourselves they don't have the time to actually make things work,,, better! Just reading their security stickys is enough to make one wonder about the free and open ideals of Linux. Just downloaded 52 new updates. All appeared to be fixing security issues. Of course it locked up about 2/3 through. 99.999% of problems I encounter are security/permissions issues. Yes, I boot up as root, gasp!, in order to locate and fix things fast. What happens if I crash it... I just reload it. I write down everything I do to get something to work because I know as long as this security mindset prevails things will probably not work on an upgrade/update. I found it mind boggling that I had no choice on loading AppArmor. At least in Fedora you are still given the option. Ubuntu is a damn fine platform but the security folks are rapidly taking the fun out of it. I have been online since the first compuserve (text based) in the 1980's. Back then computers were a lot of fun and no one worried too much on security issues unless you were a corporation or government. Since that time until now I have gotten one worm. 25 years. All the computer retailers/manufactures are in trouble. Why? Because the fun is gone and fewer people want the hassle. 
Just write everything you do and upgrade as little as possible. If it works don't can it simply to have the latest UNLESS you absolutely need the latest to do what you want done.  

Have a nice day

---

### Post by ke4ram on 2008-06-01
Had to login a third time to post the above.

---

### Post by danson on 2008-06-02
I agree.  I don't need the latest all the time, I just keep hoping one of these upgrades will fix some annoying issues.  Having to restart X to use dual screen or clone screen is annoying, especially since Windows does this so well.  I had hopes that the new Screen and Monitor applet would finally take care of this, but not for me.  I had to install the proprietary ATI driver again to get dual screen working, and the applet doesn't do anything.

Another issue is that now I have to explicitly turn off the Synaptic touch pad on my laptop if I want to use an external mouse.  That didn't have to be done before, I used to be able to use either one with no trouble.  Now the external mouse doesn't work right if the touch pad is on.

Another problem, and I know this isn't an Ubuntu problem necessarily, is that Evolution continues to suck.  I keep hoping that one day it will work well with Exchange, but not yet.

---

### Post by Pjotr123 on 2008-06-02
Upgrade woes.... A clean installation, with previous formatting, is always the best. For every operating system under the sun.

I think that a clean reinstall of Ubuntu 8.04 will probably cure all these problems that you have now.

Greetz, Pjotr.

---

### Post by chadeldridge on 2008-06-02
As for the broadcom card it wont, ubuntu still hates those things.  I have 3 laptops and all 3 have a different flavor of that same wireless card.  Best bet is to just make sure you have the files local for either fwcutter or the ndiswrapper.  I keep them handy, cause every singe time you reinstall or format, you are going to need them.  How about getting those drivers just setup to auto install like everything else.  Its been years now and still no joy on that.

:-p

---

### Post by wpshooter on 2008-06-02
> **Pjotr123 said:**
> Upgrade woes.... A clean installation, with previous formatting, is always the best. For every operating system under the sun.

I think that a clean reinstall of Ubuntu 8.04 will probably cure all these problems that you have now.

Greetz, Pjotr.

I second that !!!

---

### Post by danson on 2008-06-02
I've spent a couple of hours today trying to get Evolution to work.  It starts, gets new mail, then has errors that make it unusable.  Looks like I'm deep into this bug:

[https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/34199](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/34199)

It's been open for over 2 years with no resolution.

I found another broke thing, VirtualBox won't work.  It seems to start, but then trying to open a VM it says "VirtualBoxKernel driver not installed." etc.  I thought I'd run Outlook inside a VM to at least get mail while I puzzle out the Evolution problems, but no joy here either...

Looking back over this thread, I sound pretty negative, but really, the OS is running well overall.  I really don't want to do a full reinstall, it's take quite a while to get my software and configuration to where it is today, and I hate to lose all of that.

---

### Post by danson on 2008-06-02
The fix for VirtualBox was pretty easy, I just needed to install the kernel drivers via Synaptic.  Still, it worked before, so I'm not sure why the kernel drivers were removed during the upgrade.

---

### Post by danson on 2008-06-02
So the new network app is irritating.  There are a couple of flaws over the previous version.  Just to be clear, I'm talking about /usr/bin/network-admin.

First, the entrance to this app changed. In the previous version, I'd start it and it would detect that I'd started it as a non-root user, so it would prompt me for a password.  The focus was on the password box, so all I had to do was type in my password and hit enter, then I was into the app and able to edit.  Now starting the app brings it up immediately, but now I have to click the "Unlock" button to do anything.  The app is useless without unlocking, and the point of accessing it is to do something.  Clicking the "Unlock" button brings up a dialog to enter my password, so really, it is the exact same functionality other than now I have to click an extra button to get into the app.

Second, and I don't think this is necessarily a new bug since I see it on my wife's laptop with gutsy, is that it doesn't remember the settings for my wireless card.  My wireless router is set for WPA2, so I've set that in the network-admin app along with the password.  Neither of the settings are remembered, the app always comes up with WPA and the password is blank.

To get around this, I've written a script and a few configuration files.  The script is pretty simple, it just copies the appropriate file to the right place, then restarts networking.  I put these files in ~/bin. Here's the script:

-------

#!/bin/bash
case $1 in
    home)
    sudo cp ./interfaces-home /etc/network/interfaces
    sudo cp ./resolv.conf-home /etc/resolv.conf
    sudo /etc/init.d/networking restart
        ;;
    work)
    sudo cp ./interfaces-work /etc/network/interfaces
    sudo cp ./resolv.conf-work /etc/resolv.conf
    sudo /etc/init.d/networking restart
        ;;
    *)
        echo $0 home\|work
        ;;
esac

-------


Then the two files, one for my home network, and one for work.

This one for home sets up both eth0 (wired) and eth1 (wireless) interfaces.

interfaces-home file contents:

-------

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet static
address 192.168.99.7
netmask 255.255.255.0
gateway 192.168.99.1

iface eth1 inet static
address 192.168.99.6
netmask 255.255.255.0
gateway 192.168.99.1
wpa-psk 94292f8d8ce41907c34e84fd21e6980c32b3ac997c621c2cfa3dcf15b73b2b7a
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid myssid

auto eth1

-------


And the associated resolv.conf-home file:

-------

nameserver 4.2.2.1
nameserver 4.2.2.2

-------


This one for work is a little simpler since it's a dhcp managed network.

interfaces-work file contents:

-------

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp

auto eth0

-------



The associated resolv.conf-work just has the work nameservers listed.

Now I just run the script to change networks instead of using network-admin.  This is easier, and more user friendly, which is an odd thing to say when discussing an Ubuntu installation. :)

---

### Post by danson on 2008-06-04
> **danson said:**
> I've spent a couple of hours today trying to get Evolution to work.  It starts, gets new mail, then has errors that make it unusable.  Looks like I'm deep into this bug:

[https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/34199](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/34199)

It's been open for over 2 years with no resolution.



A possible fix for this one... I ran across this excellent page:

[http://mad-scientist.us/evolution.html](http://mad-scientist.us/evolution.html)

This gives instructions to easily download the latest Evolution code and build it from scratch.  So far so good, I've had Evolution running for about an hour without error, which is about 59 minutes longer than I was able to run with the Ubuntu release version.  The latest that shows up in synaptic is 2.22.1, using the nifty make file from the link above gets me 2.23.4.  This version is considerably more stable than 2.22.1, at least so far.

heh... I feel like I'm running Gentoo again...!

---

### Post by danson on 2008-06-04
Darn.  About an hour and a half, and the Evolution calendar is having problems.  So the "fix" of building from scratch helped some, but not completely.

---

### Post by danson on 2008-06-05
After running the compiled-from-source version of Evolution, I can say that it is at least usable.  I restarted it 3 times yesterday.  The problem seems to be in the calendar rather than the email, although some messages were unavailable due to the 'lost connection to back-end process' error.  I should mention I'm using Evolution to connect to an MS Exchange server.

---

### Post by danson on 2008-06-05
Uh oh, another negative.  I tried to play a DVD last night.  Not a problem before the upgrade, but now playing a DVD is so choppy as to be useless.  I'll need to investigate further on this one.

The scripts I made for switching from my home network to the network at work work much better than the network-admin tool.  I should have done this years ago!

---

### Post by danson on 2008-06-05
I noticed the Pidgin "upgrade" right away too, but hadn't got around to doing anything about it until yesterday.  In case you don't know, there has been a lot of controversy about the Pidgin developers changing the functionality of the text entry box so it's no longer manually resizable.  This irritated a LOT of people, but they refuse to change it back.  I use Pidgin every day, and yes, not being able to resize the box is really annoying.  The Pidgin project was forked, and a new project named "funpidgin" was formed to pay more attention to users wants and needs.  Actually, they are changing the name to "Carrier".  The link is

[http://funpidgin.sourceforge.net/](http://funpidgin.sourceforge.net/)

I forgot to write down my steps for installing this.  There are instructions for installation on the funpidgin website.  You have to uninstall your previous Pidgin and a few libraries, then download and install the deb file.  The text area will still be non-resizeable, but go to Tools - Plugins and check the "Entry area manual sizing" checkbox.  Now the text area is resizeable.

There is a bit of weirdness in all of this, the forked Pidgin appears identical to the old one.  There is nothing on it that says funpidgin or carrier or whatever, so it may not be immediately obvious that you've actually installed anything new.

---

### Post by ukripper on 2008-06-05
As said many times - "Don't break what is working!". There was no need for an upgrade when things were fine for you in Gutsy.

---

### Post by danson on 2008-06-05
> **ukripper said:**
> As said many times - "Don't break what is working!". There was no need for an upgrade when things were fine for you in Gutsy.

Oh, I definitely agree.  However, not all things were working fine.  Evolution did not work fine in Gutsy.  There were continuing issues with the ATI video driver that I'd read were much better in Heron (maybe that's true for some, but not true for me).  In general, the Ubuntu upgrades have been great, each time, performance has improved, the apps themselves are better, the general fit and polish is nicer, so I really haven't seen a reason not to upgrade, other than I figure I'll have to fiddle with video and wireless to get it running correctly again.  All these other issues are a surprise to me and not what my history of using Ubuntu would suggest.

---

### Post by danson on 2008-06-05
I realized I'm using this forum more as a blog than soliciting assistance.  I'll move my commentary elsewhere.

---

### Post by ukripper on 2008-06-06
> **danson said:**
> I realized I'm using this forum more as a blog than soliciting assistance.  I'll move my commentary elsewhere.

Great! Why don't you create a blog instead?

---

### Post by hyper_ch on 2008-06-06
> **chadeldridge said:**
> As for the broadcom card it wont, ubuntu still hates those things.
It's not ubuntu hating those, it's those hating ubuntu...

---

### Post by 23meg on 2008-06-06
> **danson said:**
> I realized I'm using this forum more as a blog than soliciting assistance.  I'll move my commentary elsewhere.

This forum is not for soliciting assistance in the first place. That's what the support forums are for.

---

### Post by zugu on 2008-06-06
2 years after I bought my Nvidia 7600 video card, Ubuntu is still not able to correctly detect it and provide me with a list of sane screen resolutions to choose from.
I find this extremely unacceptable, to the point where Ubuntu makes me sick.

---

### Post by stchman on 2008-06-06
> **zugu said:**
> 2 years after I bought my Nvidia 7600 video card, Ubuntu is still not able to correctly detect it and provide me with a list of sane screen resolutions to choose from.
I find this extremely unacceptable, to the point where Ubuntu makes me sick.

I have a 7600GT video card and have been able to use it successfully since Edgy (over a year).  I don't know what you are doing.

---

### Post by terabyte1 on 2008-06-07
Hand on heart - I always send for the latest version of Ubuntu and Kubuntu from Canonical - it might take some time - but I'm sure it is safe and hasn't been  corrupted as I dowloaded it from some mirror... I don't just have this machine - my Main one, but there are several waiting in the wings - well ok, my loft - set up with an Ubuntu Server and sporting Apache, PHP5 and Mysql and a couple of other boxes using other distros for mucking around with. I really love Ubuntu - I even have clothing suitably printed with Ubuntu Logos and captions when going to the Gym (sad I am this 66 year old)!:lolflag:


Enjoy!

terabyte1:guitar:

---

### Post by danson on 2008-06-08
Another WTF... I noticed today that Acroread isn't a choice anymore to open a pdf with.  I know that Acroread is not free software and is not supported by Ubuntu.  However, the  upgrade UNINSTALLED it.  This just pisses me off.  I installed it on purpose, much like xscreensaver, and since it's not part of the standard Ubuntu distribution, it should be obvious that I installed it myself.  Clearly, the upgrade uninstalled it specifically.  This sort of disregard for user installed apps reminds me of the way Microsoft would do it.  I really don't expect this sort of behavior from Linux distributions.

---

### Post by danson on 2008-06-08
> **23meg said:**
> This forum is not for soliciting assistance in the first place. That's what the support forums are for.

I've been posting comments to my blog here:

[http://danson.grafidog.com/search/label/Ubuntu%20Hardy%20Heron](http://danson.grafidog.com/search/label/Ubuntu%20Hardy%20Heron)

My comments there seem to be in a more positive tone than here for some reason... :)

---

### Post by ukripper on 2008-06-08
> **stchman said:**
> I have a 7600GT video card and have been able to use it successfully since Edgy (over a year).  I don't know what you are doing.

+1 on that. I have the same card over 2 years and never had any problem using under ubuntu.

---

### Post by hyper_ch on 2008-06-09
> **terabyte1 said:**
> Hand on heart - I always send for the latest version of Ubuntu and Kubuntu from Canonical - it might take some time - but I'm sure it is safe and hasn't been  corrupted as I dowloaded it from some mirror...

Even shipped discs may have a defect ;) but you can securly download the images using bittorrent. That will ensure that the download is not corrupted. Then just burn it at low speed and before actually using it, check the cd for defects.

---

