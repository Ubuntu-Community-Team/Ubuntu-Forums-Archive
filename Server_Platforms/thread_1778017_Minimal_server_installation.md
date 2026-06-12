---
title: "Minimal server installation"
date: 2011-06-08
forum: Server Platforms
---

### Post by kb1uab on 2011-06-08
Hi all,

I'm hoping I get some good feedback on this as there are alot of others probably looking to do the same.

I'm using older hardware (iPaq P3 866, 512MB, 300GB) and looking to build a basic unit to use for a home network.

The questions are valid.

What would be the best release to use (speed, reliability, etc.), should I be going with older?
Would I be able to implement Samba, LAMP, Apache, etc. (after exiting GUI, still working on CLI)
What are the benefits of using a newer release (security, options, etc.), will these effect performance?

I tried using the Minimal install ISO for 11.04, but it would hang on boot, I did install 10.10, and it ran ok but after one restart it would exit back to login continuously, another time I couldn't get the task bars.

Please advise.

---

### Post by jramshu on 2011-06-08
Are you using the server edition or desktop edition?

I have 10.10 Server Edition on a pretty old Compaq and it works fine. 
My specs:
Presario 6025RSH
AMD Athlon(tm) XP 1800+ 
512 MiB RAM
NVCrush11 [GeForce2 MX Integrated Graphics]
BIOS: 686Y4 v2.13 (05/20/2002)

EDIT: LAMP is Linix, Apache, mySql, PHP

---

### Post by Joe of loath on 2011-06-08
For a server, use the release with the longest support. Currently that's 10.04. Updates are no fun when you don't have full physical access to the machine.

Simply install using the 10.04 server disk, and you're sorted. I run a busy forum on a cheap Ubuntu 10.04 VPS with 512mb of RAM, and usage never goes above half that.

---

### Post by kb1uab on 2011-06-08
Ah, another point of interest. What are the key differences between Desktop and Server? I know I can do a desktop install and then add the packages I want (same as in server) so whats the BIG reason for server?

---

### Post by Joe of loath on 2011-06-08
The server version has a slightly modified kernel, designed for throughput etc. It also comes with all the server packages needed on the disk. The Desktop version comes with a GUI, loads of desktop packages, and a universal kernel designed with power consumption more in mind.

A server with all the desktop packages will usually run slower, since it has to run the GUI and all its dependent programs on boot.

---

### Post by memilanuk on 2011-06-08
All the extraneous desktop stuff that are not generally pertinent to servers are not installed.  Less space used for 'fluff', more space for data, in theory.  Also less opportunity for some obscure security flaw in some desktop widget to result in a compromised system.  Finally, the kernel installed in the server version has some optimizations for use under heavy load, multiple users, etc.

In practical terms, though... very few if any home users are going to stress their system enough to where the kernel optimizations are of any value to them, and with hard drive space and processor power as cheap as it is... the 'expense' of all the desktop 'fluff' is negligible (for the purposes of a home user) as well.  If you have a reasonable firewall installed and setup the services that you do offer up to your home network properly... the likelihood of a security compromise from a desktop feature is pretty minimal also.  The server install is somewhat 'cleaner' as there are less things to keep an eye on during upgrades, etc.

In the end, some people just like to get their geek on and wallow in the command line ;) - not at all a bad thing, but easily doable from a desktop install as well.

---

### Post by Joe of loath on 2011-06-08
I'm not sure, Ubuntu + Gnome can use 300mb of RAM, and if you only have 512mb to start with, you haven't got much left. My CLI install of Debian uses about 30mb of RAM, and that's with apache and nfs. I'm sure Ubuntu server isn't far off.

---

### Post by collisionystm on 2011-06-08
> **kb1uab said:**
> Hi all,

I'm hoping I get some good feedback on this as there are alot of others probably looking to do the same.

I'm using older hardware (iPaq P3 866, 512MB, 300GB) and looking to build a basic unit to use for a home network.

The questions are valid.

What would be the best release to use (speed, reliability, etc.), should I be going with older?
Would I be able to implement Samba, LAMP, Apache, etc. (after exiting GUI, still working on CLI)
What are the benefits of using a newer release (security, options, etc.), will these effect performance?

I tried using the Minimal install ISO for 11.04, but it would hang on boot, I did install 10.10, and it ran ok but after one restart it would exit back to login continuously, another time I couldn't get the task bars.

Please advise.


Just use Zentyal.

[www.zentyal.com](www.zentyal.com)

---

### Post by snowpine on 2011-06-08
The Ubuntu Server Guide will get you started in the right direction, highly informative:

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

---

### Post by kb1uab on 2011-06-08
Ah, I do remember seeing someone explaining the streamlined kernel for server usage, its benefits are obvious. And I do agree that in the home environment, with a proper firewall deployment, either solution is a viable option.

I want to stick with using Ubuntu, as I have a couple of other servers running 10.10 with robust hardware. I just want the challenge with older hardware, and didn't know if it was a hopeless feat.

---

### Post by tgalati4 on 2011-06-09
I have an old machine running dapper drake desktop that morphed into a server.  So if you are comfortable installing and running desktop ubuntu, then install it and install the services that you want.  For home use, there's not a lot of performance difference between desktop and server.  When you are not using the desktop, just log out or restart a session in terminal mode.  The destktop windows use about 10% of cpu cycles.  The bigger issue is 24/7 power consumption.  Depending on your power rates, running a 60 watt machine 24/7 can add up to several hundred dollars over a year.  With that expense, you will be looking at low-power servers in the future.  For a headless server, you can pull out the video card and save 10 to 15 watts.  That adds up over a year.

Some differences:  interrupt tick is 100 Hz in server and 250 Hz in desktop--that give you a more responsive mouse and keyboard.  The scheduling is different, but I don't remember what they are set to at the moment.  There may be some drivers/modules that are enabled in the server to work with RAID cards and other enterprise stuff that you wouldn't find in a desktop.

---

### Post by Lars Noodén on 2011-06-09
> **tgalati4 said:**
> ...The bigger issue is 24/7 power consumption.  Depending on your power rates, running a 60 watt machine 24/7 can add up to several hundred dollars over a year.  With that expense, you will be looking at low-power servers in the future.  For a headless server, you can pull out the video card and save 10 to 15 watts.  That adds up over a year...

+1 on the power saving. Anyway, it's not a server if it has a graphics card. ;)

---

### Post by Joe of loath on 2011-06-09
What do you do about integrated graphics, then? :p

---

### Post by Lars Noodén on 2011-06-09
> **Joe of loath said:**
> What do you do about integrated graphics, then? :p

See the definition in post #[12](http://ubuntuforums.org/showpost.php?p=10919759&postcount=12). :P

---

### Post by kb1uab on 2011-06-09
Hi all, thanks for the input. I was really hoping this was going to be a topic that I could get some input on, and it seems I have.

The machine is an old Compaq iPaq c500 that I changed the processor to a PIII 866. The c500 board uses onboard video with shared memory (the P versions had 4MB on board :( )

I installed 11.04 and it boots gui fine, runs ok, a little slow. My big problem now is that the cli is distorted. To make things more interesting, every now and then its ok. Urrrr, I need the terminal, as I'm trying to learn it. Soooooo, I had 10.10 in it, but it did some strange things (I've noticed this on some other machines as well).

All I'm looking to do is have this thing work. I figure its a small machine, and probably will be good on power consumption. Right off it will be used for Samba and print server, as it only has one drive. Its to support the wifes work so I don't catch flack when I'm playing with the other servers. hehe. So with that said, it will be a dedicated system that I can SSH or VNC into, serve files, host printers, and run rsync operations. Thats basically all I want it for.

The only other use it might get put into (and I cant remember the name of the package) is for audio output. I have a detached garage and I was thinking of having the unit there with an audio feed to outdoors. Since it would always be on, might as well have it serving that purpose too, rather than another machine running.

I know this is off subject, but it is part of the additional plan above. I figure I can simply control the parallel port to toggle outputs (power amp on/off, change input, volume up/down), any input on that? Would it be worth, or does anyone know, if an IR signals can be recorded via serial and then applied to buttons in a program?

Yes, I'm crazy.:D

---

### Post by Joe of loath on 2011-06-09
Yes, you can control the serial/parallel ports using C or Python. Python is much easier to learn and use, so I suggest using that :p

---

### Post by tgalati4 on 2011-06-09
Mpd will play music and it can be controlled remotely through  several clients.

apt-cache search mpd

Switch graphics to "pci" in BIOS will normally shut off integrated chip.

---

### Post by kb1uab on 2011-06-09
I wish it was that easy, the board is a flexATX, no slots, all onboard, so I'm finding it strange that I cant fix this video issue, and I didn't have it in the previous version. Looking like and issue with GRUB setting the video mode.

GRUB is 1.99, and uses the /etc/default/grub file I believe to set the mode (there is no menu.lst in this release). I've tried 640x480 and 800x600 but both are still distorted (white background, garbled letters

---

### Post by tgalati4 on 2011-06-09
Typically in BIOS you can change the video RAM (since it is shared) to 16MB or 32MB, that may help.

---

### Post by kb1uab on 2011-06-09
Nope, the only thing mentioned in BIOS is Palette snooping, and that makes no difference. Very vanilla, like i said, it DID work a couple of times, maybe it doesn't like the font. Its in 11.04, the minimal installer iso wouldnt boot either on this machine, would hang, display a strange color bar, then strobe the screen. GUI works perfect, it just wont work in terminal.

Been bouncing around in Gnome fine, but playing with the GRUB config seems to be making some differences, good or bad, they are differences.

---

### Post by kb1uab on 2011-06-10
Well, I installed 10.04.02 LTS and everything works fine, so I guess I'll run with this.

I setup the desktop as well (I know, I know) and have one question on it, when I'm ready to deploy the unit and let her run, I set the auto start after power loss (in case power is out long enough for UPS to go down) but, I won't want the desktop to start, so, does this look like it is correct?

To disable X and start text-only (there is billions of ways, here is one of them) :
start console
sudo update-rc.d -f gdm remove

To get it back:
sudo update-rc.d gdm defaults

If you want to go to X from cli:
startx

---

### Post by dozycat on 2011-06-10
I have an AMD Semptron with 512 Mb of ram, with ubuntu 10.04 32 bits with xfce and works great.

---

### Post by kb1uab on 2011-06-10
Oh, but now I have the infamous no panels on startup. I can Alt-F1, run terminal, and pkill gnome-panel and they come back, but I have to do this every reboot. Any advice on this one? 10.04.2

---

