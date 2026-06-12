---
title: "Blank screen after fresh install of 12.04 Alpha"
date: 2011-12-28
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by PatrickD-52761 on 2011-12-28
Hello everyone,

I just installed 12.04 Alpha on an older computer (Dell Dimension 4500 with 1 GB of RAM and a 2.4ghz Intel Processor), and when I rebooted, I got a blank screen with a flashing cursor.

Technically, when I rebooted, my monitor showed the purple Ubuntu screen, at one point it had "Waiting on Network Configuration..." showing, and then the monitor shut off.

I can use CTRL+ALT+F1 to F6 and get into a text terminal (CLI). CTRL+ALT+F7 shuts the monitor off, and CTRL+ALT+F8 shows the black screen with a blinking cursor.

The video card is an older ATI Rage 128 Ultra (4x AGP).

I'm interested in any suggestions (even suggesting booting with 11.04 or 11.10) for getting this working. As of right now, I've only tried apt-get update/dist-upgrade, and lspci which shows the ATI Rage 128 Ultra video card. 

Thanks, and have a great day:)
Patrick.

---

### Post by howefield on 2011-12-28
Thread moved to the "*Ubuntu +1 (Precise Pangolin)*" forum.

---

### Post by effenberg0x0 on 2011-12-28
Since you upgraded Ubuntu release and, more importantly, the kernel version, I'm sure you also reinstalled your video drivers right? 

If that is the case, the information you provided is not enough for anyone to help you. Switch to another VT, copy information such as dmesg, lspci, xorg's log to a temporary file and upload it to here, so people can have a glimpse of what may be happening there.

---

### Post by OGpmpdog on 2011-12-28
> **PatrickD-52761 said:**
> Hello everyone,

I just installed 12.04 Alpha on an older computer (Dell Dimension 4500 with 1 GB of RAM and a 2.4ghz Intel Processor), and when I rebooted, I got a blank screen with a flashing cursor.

Technically, when I rebooted, my monitor showed the purple Ubuntu screen, at one point it had "Waiting on Network Configuration..." showing, and then the monitor shut off.

I can use CTRL+ALT+F1 to F6 and get into a text terminal (CLI). CTRL+ALT+F7 shuts the monitor off, and CTRL+ALT+F8 shows the black screen with a blinking cursor.

The video card is an older ATI Rage 128 Ultra (4x AGP).

I'm interested in any suggestions (even suggesting booting with 11.04 or 11.10) for getting this working. As of right now, I've only tried apt-get update/dist-upgrade, and lspci which shows the ATI Rage 128 Ultra video card. 

Thanks, and have a great day:)
Patrick.

Hi!

I had the same issues a few weeks back.
[http://ubuntuforums.org/showthread.php?t=1890045](http://ubuntuforums.org/showthread.php?t=1890045)


I wanted to save time from installing oneiric, and then updating to precise.  I wanted to learn.

I had to boot into recovery network root, and do initial software upgrades from there.

Afterwards, I removed and reinstalled nvidia drivers...VOILA! Subsequent boot was successful into Light DM.

FYI...this is probably an ongoing issue with graphics cards more than 3 years old...I have a newer production machine, with a card less than 1 year old; Precise installation was flawless.

Good Luck

---

### Post by PatrickD-52761 on 2011-12-28
> **effenberg0x0 said:**
> Since you upgraded Ubuntu release and, more importantly, the kernel version, I'm sure you also reinstalled your video drivers right? 

If that is the case, the information you provided is not enough for anyone to help you. Switch to another VT, copy information such as dmesg, lspci, xorg's log to a temporary file and upload it to here, so people can have a glimpse of what may be happening there.

I did a clean install (using the Alternate CD and choosing "Use Entire Drive". I've also booted up an 11.10 Live CD and got the same results (monitor shuts down before I get to the language selection pane/option pane). 

In my dmesg on the 12.04 boot, I'm getting something along the lines of unity_support_t: freeing invalid memory. So, I'm going to check to make sure that my memory sticks are both seated properly--and that BIOS recognizes them both. It could end up being something simple like they need to be switched around, or one isn't seated completely.

I'm also looking at upgrading the video card. Especially since the Rage 128 series has been around longer than my son.

> Hi!

I had the same issues a few weeks back.
[http://ubuntuforums.org/showthread.php?t=1890045](http://ubuntuforums.org/showthread.php?t=1890045)


I wanted to save time from installing oneiric, and then updating to precise. I wanted to learn.

I had to boot into recovery network root, and do initial software upgrades from there.

Afterwards, I removed and reinstalled nvidia drivers...VOILA! Subsequent boot was successful into Light DM.

FYI...this is probably an ongoing issue with graphics cards more than 3 years old...I have a newer production machine, with a card less than 1 year old; Precise installation was flawless.

Good Luck

Thanks for the link. I'm going to look into some of those options as well. One thing that I should note is that the installation completed successfully, and I'm able to boot into the console (TTY). And I'm able to install and update (well I think I can, I'm able to update at least). I'm also able to stop and start the lightdm service (although starting it shuts down my monitor, as it doesn't work).  So it's not an "ubuntu" or "linux" issue, but simply a LightDM/Unity/XServer/whatever it is now, issue.


Have a great day:)
Patrick.

---

### Post by effenberg0x0 on 2011-12-28
This is not a PP-related problem, but more likely a "How do I install my video Driver (ATI R128)" problem. You would probably receive better help in doing it at "General Help": It's unlikely to find the typical "How to do xyz step-by-step" tutorial writer in here. But as they saw your mention to PP, they moved you here.

I have no idea if this card uses xserver-xorg-video-ati, fglrx, catalyst, etc. But considering its discontinued and there's a xorg driver for it, it probably is the best bet. I would try:

sudo service lightdm stop
sudo killall -s KILL X
sudo apt-get remove --purge gdm nvidia* fglrx* xserver-xorg-video-ati
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.$(date +%y-%m-%d_%H:%M)
sudo apt-get install --reinstall xserver-xorg-video-r128 lightdm lightdm-gtk-greeter
sudo apt-get update && sudo apt-get upgrade
sudo reboot now

Keep in mind these are very generic instructions. Google probably knows a lot more than me on this.

If you drop to console again, with no GUI, the only way people can understand what is going on there and possibly help is if you copy the contents of dmesg and /etc/X11/xorg.0.log to your next post. 

sudo cat /var/log/Xorg.0.log > ~/my_xorg_log.txt
sudo cat /var/log/dmesg > ~/my_dmesg.txt

---

### Post by PatrickD-52761 on 2011-12-28
> **effenberg0x0 said:**
> This is not a PP-related problem, but more likely a "How do I install my video Driver (ATI R128)" problem. You would probably receive better help in doing it at "General Help": It's unlikely to find the typical "How to do xyz step-by-step" tutorial writer in here. But as they saw your mention to PP, they moved you here.

I have no idea if this card uses xserver-xorg-video-ati, fglrx, catalyst, etc. But considering its discontinued and there's a xorg driver for it, it probably is the best bet. I would try:

sudo service lightdm stop
sudo killall -s KILL X
sudo apt-get remove --purge gdm nvidia* fglrx* xserver-xorg-video-ati
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup.$(date +%y-%m-%d_%H:%M)
sudo apt-get install --reinstall xserver-xorg-video-r128 lightdm lightdm-gtk-greeter
sudo apt-get update && sudo apt-get upgrade
sudo reboot now

Keep in mind these are very generic instructions. Google probably knows a lot more than me on this.

If you drop to console again, with no GUI, the only way people can understand what is going on there and possibly help is if you copy the contents of dmesg and /etc/X11/xorg.0.log to your next post. 

sudo cat /var/log/Xorg.0.log > ~/my_xorg_log.txt
sudo cat /var/log/dmesg > ~/my_dmesg.txt

You're most likely right about the subject matter. And at the time I posted the original message, I hadn't tried older versions. I've solved the problem though, by replacing the video card with an ATI Radeon 9550, which was in my mythbuntu box. Everything works out of the box now.

I started out in "Installation and Upgrade" and was moved here (most likely as you mentioned because I posted that I was running 12.04). As far as the "How do I ....", I expected that it would install the driver for me (as the card is older, and not rare). But, I also realize that the card is obsolete, and there are limits to what can be packaged on the CD/DVD.

Anyhow, no matter. I have the issue solved. I'll be waiting my new graphics card for my mythbuntu box now. And until then, the onboard graphics work pretty decently.  

Have a great day, and thank you everyone for your suggestions. :)
Patrick.

---

