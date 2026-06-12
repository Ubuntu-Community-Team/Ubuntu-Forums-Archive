---
title: "The Ultimate Ubuntu Speed Tips Thread!"
date: 2007-05-28
forum: The Cafe
---

### Post by Mazza558 on 2007-05-28
Well, everyone here will probably know a tip or tweak that boosted their Ubuntu installation that little bit. Since these are all spread out around the forums, it would be nice to have somewhere where a new user could come and find some tips/tweaks all in one place. 

There's only 2 rules here:

-No linking to massive, multiple page articles with hundreds of tweaks on - try and post directly into the thread, and if you have to link, only link to the most effective tweak/tip you found.

-Don't suggest REALLY risky tips/tweaks such as editing complicated .conf files unless it is easy to restore things if everything goes wrong.


Well, my tweaks are all related to Beryl use:

1.) Beryl often doesn't use the correct refresh rate for monitors with rates higher than 60hz,  so it is advised to turn off the "detect refresh rate" option in "general options" - then you can set the correct refresh rate further down. This should solve any lagginess in terms of Beryl.

2.) Turn off "Sync to Vblank" in the "general settings" area

3.) Turn off all closing animations in Beryl if things seem to lag when closing things.

---

### Post by fuscia on 2007-05-28
use openbox.

---

### Post by aysiu on 2007-05-28
> **fuscia said:**
> use openbox.
Or IceWM or Fluxbox.

Metacity's a drag.

---

### Post by fuscia on 2007-05-28
> **aysiu said:**
> Or IceWM or Fluxbox.

Metacity's a drag.

flwm is pretty rockin', as well.

---

### Post by Mazza558 on 2007-05-29
Anyone else?

---

### Post by Ebuntor on 2007-05-29
> **Mazza558 said:**
> 
Well, my tweaks are all related to Beryl use:

1.) Beryl often doesn't use the correct refresh rate for monitors with rates higher than 60hz,  so it is advised to turn off the "detect refresh rate" option in "general options" - then you can set the correct refresh rate further down. This should solve any lagginess in terms of Beryl.

2.) Turn off "Sync to Vblank" in the "general settings" area

3.) Turn off all closing animations in Beryl if things seem to lag when closing things.

Whoa, those tweaks made one heck of a difference! Not sure which tweak did it (maybe all of them) but I can actually use the cube option without lagging. Works perfectly.

Thank you :D

---

### Post by shen-an-doah on 2007-05-29
[Using Rox filer with fluxbox](http://forums.debian.net/viewtopic.php?p=26103&sid=7c0fbaf03f4205db4023e5c8a25c4163#26103)

---

### Post by happy-and-lost on 2007-05-29
May just be a random tweak related to my hardware or particular setup, but I found that switching to the low-latency kernel (it's in the repos) smoothed things out consierably, especially Compiz.

---

### Post by urukrama on 2007-05-29
Not using Beryl makes a big difference as well.

---

### Post by munkyeetr on 2007-05-29
Use Swiftfox instead of Firefox.

---

### Post by edmondt on 2007-05-29
> **Mazza558 said:**
> 
1.) Beryl often doesn't use the correct refresh rate for monitors with rates higher than 60hz,  so it is advised to turn off the "detect refresh rate" option in "general options" - then you can set the correct refresh rate further down. This should solve any lagginess in terms of Beryl.


That made everything smooth! :) VSYNC also works wonders, but I already know that one :D

---

### Post by kerry_s on 2007-05-29
1.Use Opera

2. Use a dns cache-> [http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)

3. Fix hosts file->
sudo gedit /etc/hosts

127.0.0.1	localhost hostname
127.0.1.1	hostname

4. Block ipv6->
sudo gedit /etc/modprobe.d/bad_list

alias net-pf-10 off

5. Use OpenDNS->
sudo gedit /etc/dhcp3/dhclient.conf

with dnsmasq>
prepend domain-name-servers 127.0.0.1, 208.67.222.222, 208.67.220.220;

without dnsmasq>
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

6. Startup tweaks->
sudo gedit /etc/rc.local

sudo -u user find /home/user/.opera ! -type d | xargs cat > /dev/null &
sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
sudo -u user find /usr/share/firefox ! -type d | xargs cat > /dev/null &
sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
echo 1000 > /proc/sys/dev/rtc/max-user-freq &
echo "base=0x98000000 size=0x8000000 type=write-combining" >| /proc/mtrr &

Replace all "user" with your account name.

7. Uninstall any applications/programs you don't use.

---

### Post by happy-and-lost on 2007-05-29
> **kerry_s said:**
> 
6. Startup tweaks->
sudo gedit /etc/rc.local

sudo -u user find /home/user/.opera ! -type d | xargs cat > /dev/null &
sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
sudo -u user find /usr/share/firefox ! -type d | xargs cat > /dev/null &
sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
echo 1000 > /proc/sys/dev/rtc/max-user-freq &
echo "base=0x98000000 size=0x8000000 type=write-combining" >| /proc/mtrr &

Replace all "user" with your account name.


Would you mind elaborating on this, what it is and what it's actually doing?

---

### Post by BLTicklemonster on 2007-05-29
> **urukrama said:**
> Not using Beryl makes a big difference as well.

lmao

I second the remarks about icewm and fluxbox. E17 is amazing, too. Lots of eye candy, but hardly uses any resources.

---

### Post by ThinkBuntu on 2007-05-29
I think these tips are hardly constructive if they instruct users to ditch their current desktop environment. GNOME comes installed, so there will be the most demand amongst desktop-related tips for quickening GNOME and GTK+ apps. Many of us like having menus and icons in fixed locations. 

I worked with Fluxbox for a while, and while lightning-quick, it's a real pain to have to navigate through the same menus no matter what you're doing. I'll gladly ditch 50px of screen real-estate (a top and a bottom panel, or a thicker bottom KDE panel) and a bit of RAM/processor speed for the sake of usability and my work habits.

---

### Post by Mazza558 on 2007-05-29
> **ThinkBuntu said:**
> I think these tips are hardly constructive if they instruct users to ditch their current desktop environment. GNOME comes installed, so there will be the most demand amongst desktop-related tips for quickening GNOME and GTK+ apps. Many of us like having menus and icons in fixed locations. 

I worked with Fluxbox for a while, and while lightning-quick, it's a real pain to have to navigate through the same menus no matter what you're doing. I'll gladly ditch 50px of screen real-estate (a top and a bottom panel, or a thicker bottom KDE panel) and a bit of RAM/processor speed for the sake of usability and my work habits.

Agreed. Now we've seen the desktop environment tweaks, it's time to focus more on the GNOME desktop environment.

---

### Post by kerry_s on 2007-05-29
> **happy-and-lost said:**
> Would you mind elaborating on this, what it is and what it's actually doing?

```
sudo -u user find /home/user/.opera ! -type d | xargs cat > /dev/null &
sudo -u user find /usr/lib/firefox ! -type d | xargs cat > /dev/null &
sudo -u user find /usr/share/firefox ! -type d | xargs cat > /dev/null &
sudo -u user find /home/user/.mozilla/firefox ! -type d | xargs cat > /dev/null &
```

Cache's firefox and opera settings for faster first start.

```
echo 1000 > /proc/sys/dev/rtc/max-user-freq &
echo "base=0x98000000 size=0x8000000 type=write-combining" >| /proc/mtrr &
```

Faster response settings.

---

### Post by mjgrim on 2007-05-31
> **ThinkBuntu said:**
> I think these tips are hardly constructive if they instruct users to ditch their current desktop environment. GNOME comes installed, so there will be the most demand amongst desktop-related tips for quickening GNOME and GTK+ apps. Many of us like having menus and icons in fixed locations. 

I worked with Fluxbox for a while, and while lightning-quick, it's a real pain to have to navigate through the same menus no matter what you're doing. I'll gladly ditch 50px of screen real-estate (a top and a bottom panel, or a thicker bottom KDE panel) and a bit of RAM/processor speed for the sake of usability and my work habits.

I think no one suggested to leave Gnome. they only suggested to replace metacity (which does sucks) - it's not the same thing. You can replace metacity, stay in Gnome, and enjoy all worlds.

---

### Post by urukrama on 2007-05-31
> **mjgrim said:**
> I think no one suggested to leave Gnome.

Actually, I would have. If you want something very fast, leave gnome behind and use one of the Window managers: Openbox, fluxbox or IceWM.

---

### Post by regomodo on 2007-05-31
> **shen-an-doah said:**
> [Using Rox filer with fluxbox](http://forums.debian.net/viewtopic.php?p=26103&sid=7c0fbaf03f4205db4023e5c8a25c4163#26103)

Just tried that. I couldn't get those sources to work properly

EDIT: sources were ok. The rest of the instructions seem to be too old. I.e** apt-get install rox-filer** not **rox-desktop**. Also, a lot of the instructions refer to things that don't exist or already exist but shouldn't

---

### Post by shen-an-doah on 2007-05-31
> **regomodo said:**
> Just tried that. I couldn't get those sources to work properly

EDIT: sources were ok. The rest of the instructions seem to be too old. I.e** apt-get install rox-filer** not **rox-desktop**. Also, a lot of the instructions refer to things that don't exist or already exist but shouldn't

Ah, yeh. I forgot I had to fiddle with it a bit.

There's [this](http://community.fluxbuntu.org/index.php?topic=78.0) instead. That's from a link in the Fluxbuntu wiki.

---

### Post by anaconda on 2007-06-01
If you dont have dual core CPU, change to i386 kernel!

---

### Post by Lord Illidan on 2007-06-01
> **anaconda said:**
> If you dont have dual core CPU, change to i386 kernel!

what?? If you have more than 1 gig of RAM i386 won't even detect it!

---

### Post by LightB on 2007-06-01
> **anaconda said:**
> If you dont have dual core CPU, change to i386 kernel!

Wrong.

---

### Post by anaconda on 2007-06-01
> **Lord Illidan said:**
> what?? If you have more than 1 gig of RAM i386 won't even detect it!

No no no.. that is not what I meant.

I was talking about changing the "linux-image-2.6.20-16-generic" to "linux-image-2.6.20-16-386", kernel (the Dapper line of kernels instead of the generic kernels..)

The generic kernel in my home machine wrongly  thought that my 1 core 2600MHz intel processor had 2 cores, and when I changed the kernel to one that supports only 1 core the speed improvement was noticeable  (386 kernel didn't try to split the processes between 2 processors anymore, when there is only one processor..)

And I got this suggestion from ubuntuforums.. :)

And the RAM limitation is with all 32-bit kernels (also the generic kernel) and I think it is 4GB not 1GB.

---

### Post by Lord Illidan on 2007-06-01
That's different. Use the 386 kernel if the generic is not working. I use the generic, and it works well.

On the forum I found that the 386 kernel (designed for older processors) does not detect 1 gb of RAM. You should use the 686 kernel.

---

### Post by Mazza558 on 2007-10-21
Just followed a few of these tweaks, they're excellent:

[http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed]("http://tvease.net/wiki/index.php?title=Tweak_ubuntu_for_speed")

Be cautious about the concurrency one, it broke the HAL for me until I reverted it.

---

### Post by LanDan on 2007-10-21
> **Lord Illidan said:**
> what?? If you have more than 1 gig of RAM i386 won't even detect it!

what are you talking about?

landan@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3364       3205        159          0         99       2743
-/+ buffers/cache:        362       3002
Swap:         1937          0       1937

randall@ubuntu:~$ uname -r
2.6.22-14-generic


generic is 386 right? or am i mistaking here

---

### Post by Scruffynerf on 2007-10-22
Tweaks that I've followed:

OpenOffice: 
Disable Java. It loads in half the time (Tools -> Options -> Java (Deselect the checkbox.)

Ubuntu/Gnome:

Install read-ahead from the repo's
When boots, press Esc on grub, then 'e' to edit the grub. Select the row containing the boot info and press 'e' to edit the line. add in the word "profile" (sans quotes) to the last line. and then boot. The first time it will take ages, but after that there will be a noticable speed improvement.

Set concurrency to shell:
```
sudo gedit /etc/init.d/rc
CONCURRENCY=shell
```

Adjusting Swap:
```
sudo gedit /etc/sysctl.conf
vm.swappiness=20
```

Additionally, I found this link on TheeMan's pages for Ubuntu Ultimate to be a huge help: [http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html]("http://ubuntusoftware.info/Howto_tweak_ubuntu_ultimate.html")

---

