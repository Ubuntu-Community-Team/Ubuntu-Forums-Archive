---
title: "Share with us your Focal installation/Upgrade Experience"
date: 2020-04-25
forum: Ubuntu, Linux and OS Chat
---

### Post by cariboo on 2020-04-25
Focal Fossa was released April 23, 2020, so it's time for a new poll. Please tell us about your experience upgrading, or doing a fresh install of Focal.

Keep in mind that this thread is only for your experience, if you are having problems, please create a thread in the support forums.

The previous poll can be found here:

[https://ubuntuforums.org/showthread.php?t=2429400](https://ubuntuforums.org/showthread.php?t=2429400)

---

### Post by sudodus on 2020-04-25
Fresh installs in two different computers, one 'whole drive' and one 'something else' alias manual partitioning alongside another Ubuntu flavour.

Both installed systems work well, but I haven't tested any really advanced stuff yet (except persistent live using mkusb, which also works).

---

### Post by Frogs Hair on 2020-04-25
Ubuntu Budgie Win 10 EasyBCD dual boot was a breeze. (legacy Motherboard)

---

### Post by TheFu on 2020-04-25
System Setup
* KVM host 16.04
* Desktop 20.04 install
* ISO from NFS server
* LVM backed KVM storage 10G
* SPiCE display
* Network Bridge
* 1 vCPU
* 2GB RAM
* Using virt-manager on remote system to install and run this GuestVM.

Press install on the **default Ubuntu Desktop** iso:
* Took about a minute to see screen
* 3:30 - ISO check finished
* Adv Features - LVM2, no encryption.
* Choose to upgrade and install drivers, media codecs during install
* Full Gnome3 install (not minimal)
* 10:40 done; Reboot;  11 min for a huge desktop install is nice!

1st reboot
* Screen is blank about 3min; give up.
* forced a reboot to recover; No idea what happened to require that.

2nd reboot:
* Ubuntu logo displayed in about 10 sec; 
* login box around 50sec
* desktop took about 15 sec from password entered

Connected Nextcloud... don't know why
Livepatch doesn't have a clear **NO! **option.  interface is too minimal.

Asked to install Updates at the end.  Thought I&#8217;d already had those applied during the install?  Nothing updated.  Why show the screen?

Annoying error popups every 5 min or so.  No button to get more information about the error.  dmesg has lots of apparmor messages.
Top says:
```
   1721 tf        20   0 3754632 391748 103212 R  33.3  19.2   2:26.17 gnome-shell                              
```
33% of the CPU and 20% of the RAM for just gnome-shell when nothing was going on.  Scary.

The LVM setup uses MBR partitioning on a clear field, wipe everything, install?  Why not GPT?  That is embarrassing in 2020.

Then it was clear why I&#8217;m not a fan of Gnome.  Wiped the install.   Grabbing the Mate install.

Overall, it was faster than expected, but gnome did lag a bit.  2G RAM is what i normally give to desktop VMs.

**20.04 Server install**:
* A little over 6 minutes to install (1st reboot)
* Love the new installer.  No surprises with storage or networking.
* Surprised that snaps were installed for LXD and 2 core needs without any request. Those things must be removed without impacting functionality 
* install is using 2.1G of disk
* RAM use is acceptable: 
```
$ free -h
              total        used        free      shared  buff/cache   available
Mem:          1.9Gi       133Mi       1.1Gi       0.0Ki       772Mi       1.7Gi
Swap:            0B          0B          0B
```
* Still need to remove pkgs, install our packages and get backups going
* i didn't use ZFS, but was tempted
* [S]visudo isn't working on the server:
```
visudo: /etc/sudoers: Permission denied
```
Permissions are fine 440.  All I&#8217;ve done was to purge nano. My userid is in the sudo group.  sudoedit and other sudo commands are working, but not visudo. vim.basic is the symlinked editor Hummm.[/S]
* the visudo issue was a stupid admin problem.  $ **sudo visudo** is the command.  ;)

---

### Post by Morbius1 on 2020-04-25
I don't want to start a big fight here. I'm just relaying some information.

If you downloaded and installed ubuntu server 20.04 you may be thinking to yourself What The ****

It turns out there are two isos you can download:

** The one that shows up when you search for it: [https://releases.ubuntu.com/20.04/](https://releases.ubuntu.com/20.04/)

** And the one available only if you have the special decoder ring: [http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/](http://cdimage.ubuntu.com/ubuntu-legacy-server/releases/20.04/release/)

The first one will install fun things like cloud-init and a bridge to an interocitor and the second one will install what used to be called the "alternative iso" and it's what you may be more familiar with if you use Ubuntu Server at home.

---

### Post by inundated on 2020-04-25
Installed Ubuntu 20.04 twice, on a USB HDD each time...the second time because the USB HDD fell to the floor, hit the floorboard and died (ouch!).

Not a single problem...smooth sailing, and worked both times.

I am doing it on a USB HDD because my main distro is Linux Mint 19.3 on this laptop. 

A small caveat - I tried to use the USB stick to "install alongside" on the laptop, but it said it couldn't write and dumped out. But the laptop is already dual booting with Linux Mint 19.3 and Windows 10, so I'm sure that requires more of a specific installation to account for that. So, until I figure out how to get Linux Mint, Ubuntu AND Windows 10 triple booting, I'll stick with the USB HDD for Ubuntu.

---

### Post by Irihapeti on 2020-04-25
I did fresh installs on two machines at home: my router and my desktop PC. The router had no problems (other than one caused by my own stupidity :oops: ) and the desktop needed a minor workaround. Also updated a couple of VMs without much difficulty, which are working as expected.

---

### Post by SantaFe on 2020-04-26
So far I've avoided the Clean Install with yet another flawless upgrade.  As usual I disabled the added PPA's before upgrading then adding them back one by one.

---

### Post by ajgreeny on 2020-04-26
I've been running VMs of Xubuntu Focal for a long time now with no real problems, so now was the moment to add a full install on my laptop and desktop as dual boot with Xubuntu Bionic on both machines.

I have only added it so far on the laptop and it has been absolutely brilliant so far.  It takes me a while to set everything up as I normally have it, my Xubuntu settings being fairly majorly changed from the default look; I have for example a vertical panel on the left hand side of the screen stuffed full of launchers.  It took me a while to figure out how to make that panel transparent as it's done differently in Xfce-4.14 compared to Xfce-4.12. 
You now have to choose to use a single colour background, click on the colour block icon, the on the + next to the colours, then move the alpha slider to the far left; not nearly as intuitive as it was.
There are also some changes needed in the conky configuration files to get a transparent background, but both those are nothing to do with the Xubuntu OS itself which is again my # 1 OS..

All good so far with no real difficulties that can not be dealt with quickly and easily.

---

### Post by rpessoa on 2020-04-26
This was my first time upgrading Ubuntu (18.04) desktop.

I had to repeat it 3 times. On each attempt I had problems. On the third time, I finally managed to fix everything, but I am still testing it to see if everything is working properly.

I am still waiting for the AMD GPU driver and my USB Wifi is working, but needs to be activated each time.

At the end, I am glad that I did the upgrade! :)

obs: the installation of Ubuntu 20.04 on my Raspberry Pi was so smooth... way better and faster than Raspbian.

---

### Post by jdeca57 on 2020-05-04
After reading that relatively negative review on Distrowatch I decided to upgrade (by force) a 19,10 Laptop and see for myself. It works flawless (not that I tested a lot) but there is no problem with wireless and the system boots fast. Seems that the reviews on Distrowatch aren't that reliable.

---

### Post by TheFu on 2020-05-04
Lest we forget that every new OS has some pain points. Differences can seem painful when they are just different. Humans often need some time to get used to new/different things.  People forget the pain when going from Win95 ---> 98 --> 2000 ---> XP ---> Vista.  Win2000 was painful.  Vista was even worse.  There weren't any drivers and old 32-bit drivers didn't work anymore.

The last week, I've seen that some ssh X11 related default options changed that prevented X11 forwarding from working - you know - **ssh -X....** commands.  Had to modify the /etc/ssh/sshd_config to have this:
```
X11UseLocalhost no
```
Seems the default is "yes" now.  That was a minor problem, now that it is solved.

Moved my HOME from a 16.04 Lubuntu install to a 20.04 Mate install.  Mate doesn't like that at all. Any graphics related anything, even opening a terminal requires 90-120 seconds.  Thinking it was conflicting settings, I **mv ~/.config  ~/.config-old**, logged out and logged in again.  That didn't help. Still painfully slow.  Created a new userid, logged out, logged in and everything under Mate was faster, as expected.  Mate is seeking settings outside the ~/.config/ area?  Really?  Fine.  installed fvwm ... logged out, selected the other WM and logged in.  All is blazingly fast now.

Time to make a backup and setup automatic, daily, versioned, backups.  People in these forums know how I am about that.  I have the stock Mate installed, minimal install for Ubuntu and only have a few non-OS installed stuff added. ssh, fail2ban, rsync, fvwm.  Need to add rdiff-backup, gem, cpanm, and lshw, so all the information about the current install can be captured to be included in the backups.  Modify the backup script for the old system (where HOME came from), so it points at the new 20.04 machine, regulus.  Setup the ssh keys for the pulled backups verify the ssh works from the server to this new client - all seems good.  Run the script.  BAM!  
```
Couldn't start up the remote connection by executing

    ssh -C backups@romulus rdiff-backup --server
```
On 20.04, rdiff-backup is v2.0.0
On 16.04, the version is v1.2.8.
These are incompatible for a number of reasons, mainly because they changed from python2 to python3, which includes a different serialization method.  It is far beyond just a check that v2.0.0 != v1.2.8.  So, I need to come up with a way to create backups.  But there are about 13 other systems here dependent on v1.2.8, so changing all of those to a newer release really isn't an option.

None of these things are "bad".  It is the price of progress. Even the ssh changes are there probably to improve default security levels for things that most people never use - because they don't know any better.  Some times differences are just a hassle.  Netplan is still a hassle, sometimes. Same for PulseAudio and Systemd-everything and snaps.  Someday, I hope a snap package will work for my needs, but alas, I use /tmp/ for .... temporary files ALL-THE-TIME and constrained snaps block that access.  I need to create a script that de-constrains snaps.

At this point, I've installed the Server 20.04 about 4 times.  Gnome3 Ubuntu about 4 times, the Ubuntu-Mate 3 times - once with ZFS - ouch!  I'm not ready for that.

---

### Post by sudodus on 2020-05-05
> **TheFu said:**
> The last week, I've seen that some ssh X11 related default options changed that prevented X11 forwarding from working - you know - **ssh -X....** commands.  Had to modify the /etc/ssh/sshd_config to have this:
```
X11UseLocalhost no
```
Seems the default is "yes" now.  That was a minor problem, now that it is solved.


Thanks for sharing your experiences with 20.04 LTS :-)

I have a question about **ssh -X**

Both in my current main bionic system and in a new freshly installed focal system I have

```
X11UseLocalhost yes
```

by default. Both systems have openssh-server and X11 forwarding works in both directions via **ssh -X**.

Maybe I misunderstand what you wrote. Do you want X11 forwarding or do you want to prevent it?

Please explain what should work and in which case.

---

### Post by TheFu on 2020-05-05
> **sudodus said:**
> Thanks for sharing your experiences with 20.04 LTS :-)

I have a question about **ssh -X**

Both in my current main bionic system and in a new freshly installed focal system I have

```
X11UseLocalhost yes
```

by default. Both systems have openssh-server and X11 forwarding works in both directions via **ssh -X**.

Maybe I misunderstand what you wrote. Do you want X11 forwarding or do you want to prevent it?

Please explain what should work and in which case.

Perhaps it is a 16.04 <---> 20.04 compatibility thing?  Skipped 18.04 desktops.  The only change was that 1 line on the 20.04 box, restart sshd and  started working.  I’m still in the mode of using 16.04 desktops (X11 server) to connect into 20.04 X11 clients.

---

### Post by Dennis N on 2020-05-08
15 days after the release date, my Ubuntu 19.10 Virtual Machine's Software Updater informed me that a new release was available. Before accepting the invitation, I made sure the system was up to date. My upgrade procedure is to use Virt Manager to create a clone of 19.10, then update the clone with it's Software Updater. Why: Should the upgrade have a problem, I then have my original 19.10 installation to fall back on while I investigate. But it went without a hitch, there were no post-upgrade fixes needed, except re-selecting the correct display resolution and upgrading some gnome-shell extensions that were not up to date.

_Highlights_:

_Cloning_: This was my first time cloning a VM with separate shared data disk used by other VMs. I found that the clone process wanted to clone the data disk along with the OS disk. The solution was to remove the data disk from 19.10's hardware configuration before cloning. After finishing, add the data disk back to both. 

_Flatpaks and Snaps_: Previously installed Flatpaks and Snaps were carried over intact to 20.04 by the upgrade. This was my first OS upgrade involving any Flatpaks, and it was uncertain how they would be treated.

That's all.

---

### Post by TheFu on 2020-05-09
Dennis, be careful accessing the same VM storage concurrently from 2 running VMs.  
> Attaching a shared disk to multiple guests that are not cluster-aware is likely to cause data corruption because their reads and writes to the disk are not coordinated.

---

### Post by Dennis N on 2020-05-09
> **TheFu said:**
> Dennis, be careful accessing the same VM storage concurrently from 2 running VMs.

Right. I'm aware of this concurrent sharing problem, but I only run one VM at a time.

---

### Post by Erik1984 on 2020-05-12
Upgrade **K**ubuntu 19.10 --> 20.04 worked quite well. Only thing I had to fix was reinstalling Cantata and mpd. The default music player is (again) replaced. And that is fine but less fine that Cantata was removed during the upgrade. But as I said, easy thing to restore as it's still in the repository.

---

### Post by mortalkorona on 2020-05-14
Here are 2 of my **Ubuntu 20.04 LTS (Focal Fossa)** experiences/journal/tutorials.

.................................................................................................................................

**2) Laptop Maker:** Lenovo

**3) Laptop Model:** IdeaPad s400u

**[COLOR=#008000]It works![/COLOR]**


[COLOR=#8b4513]**[SIZE=4]* Installing on machine with UEFI.[/SIZE]**[/COLOR]
[My Laptop Lenovo IdeaPad journey in wrestling against BIOS/UEFI issues.]("https://ubuntuforums.org/showthread.php?t=2443177&p=13956424#post13956424")

.................................................................................................................................

**2) Laptop Maker:** Asus

**3) Laptop Model:** x55sr

[COLOR=#008000]**It works!**[/COLOR]


**[COLOR=#8b4513][SIZE=4]* Installing on machine without UEFI.[/SIZE][/COLOR]**
[Laptop COMPATIBILITY List. - page 179]("https://ubuntuforums.org/showthread.php?t=1543006&page=179")

When booting **LiveCD/USB** stick this Error will occurr.
```

Missing parameter in configuration file. Keyword: path

gfxboot.c32: not a COM32R image

```
To go around that Error do this:

[LIST]
[*]Press **TAB** key.
[*]Type **live** then press **ENTER** key.
[/LIST]

---

### Post by sudodus on 2020-05-14
> **mortalkorona said:**
> ...

**[COLOR=#8b4513][SIZE=4]* Installing on machine without UEFI.[/SIZE][/COLOR]**
[Laptop COMPATIBILITY List. - page 179]("https://ubuntuforums.org/showthread.php?t=1543006&page=179")

When booting **LiveCD/USB** stick this Error will occurr.
```

Missing parameter in configuration file. Keyword: path

gfxboot.c32: not a COM32R image

```
To go around that Error do this:

[LIST]
[*]Press **TAB** key.
[*]Type **live** then press **ENTER** key.
[/LIST]

Please tell us which tool you used to make the live drive, when you had the problem '[FONT=Courier New]**gfxboot.c32: not a COM32R image**[/FONT]'. It looks like an old problem, that affected some extracting tools (it was squashed in the Ubuntu Startup Disk Creator version bundled with Ubuntu 16.04 LTS). Has it popped up again in Unetbootin? or some other tool?

---

### Post by mortalkorona on 2020-05-15
> **sudodus said:**
> Please tell us which tool you used to make the live drive, when you had the problem '[FONT=Courier New]**gfxboot.c32: not a COM32R image**[/FONT]'. It looks like an old problem, that affected some extracting tools (it was squashed in the Ubuntu Startup Disk Creator version bundled with Ubuntu 16.04 LTS). Has it popped up again in Unetbootin? or some other tool?

[SIZE=4]@sudodus[/SIZE]

I followed this tutorial when creating my **LiveCD/USB stick** with **[COLOR=#daa520]Ubuntu Startup Disk Creator[/COLOR]** using an **[COLOR=#8b4513]old Lubuntu[/COLOR]** install based on [COLOR=#daa520]**Ubuntu 14.something LTS**[/COLOR] I think.
[https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview](https://ubuntu.com/tutorials/tutorial-create-a-usb-stick-on-ubuntu#1-overview)



[LIST]
[*]My Windows gaming machine couldn't detect my USB stick which I previously had tried and failed to install [COLOR=#0000ff]**Qubes OS**[/COLOR] with (recommended by Edward Snowden). Which also meant that my **Ubuntu guest VMs** on **VirtualBox** couldn't detect and write to that USB stick.
.
[*]Also I didn't want to risk my Windows gaming machine messing with partitions.
.
[/LIST]

The only working machine I had at home at that time which could detect and repair that **[COLOR=#0000ff]Qubes OS[/COLOR] LiveCD/USB stick** was with my old trusty Lubuntu.

**How to Repair a Corrupted USB drive in Linux**
[https://www.maketecheasier.com/repair-corrupted-usb-drive-linux/](https://www.maketecheasier.com/repair-corrupted-usb-drive-linux/)

---

### Post by DuckHook on 2020-05-26
It's been a mixed bag.

As expected, the virgin installs gave me the least problems, though they were not entirely trouble-free either. Servers, whether upgrades or new installs, went without any hitches; desktops were a different story:

[list=1]
[*]My older AMD GPU will only run the Radeon driver. Noticeably more lag and choppy graphics than with Bionic. Surprising and disappointing.
[*]Irritating defaults like pulseaudio ignoring last setting and always defaulting to USB, 
[*]Bug in Totem or associated library makes videos so choppy as to be unplayable. Using VLC as workaround. It works nicely.
[*]4K video no longer 60Hz. Only 30Hz offered by default. No doubt these are limitations unique to my GPU/Monitor/cabling/EDID config, but still disappointing given that I could run 60Hz in Bionic. Partially worked around by creating custom ~/.xprofile but this causes periodic screen tearing and shifting (no such problems in Bionic).
[*]Both pluses and minuses in app changes: GIMP is finally a coordinated app instead of silly separate windows, LibreOffice has bugs, GnuCash has changed its default config location, Rhythmbox has nerfed UI that does not allow importing tracks, etc.
[*]Focal notably boots faster than Bionic
[*]Allows ZFS root installs natively which is pretty cool.
[/list]
The upgrades were more problematic. Unfortunately, a lot more. To set the stage, prior to upgrading, I tried to back out as many customizations as I could remember. The system was as close to a default state as 2+ years of power usage would allow.

[list=1]
[*]Pulseaudio problems. All output redirected to one audio sink. Finally solved by nuking ~/.config/pulse and rebuilding one from scratch.
[*]KVM problems. All inherited VMs hung at shutdown necessitating being killed, then destroyed. Finally solved by purging and reinstalling the whole virt-manager stack. This then broke custom seabios resolutions.
[*]Some VMs have migrated well, others not so well.
[*]Scanner and printing either acted oddly or stopped working altogether. Solved by purging old printers and reinstalling from scratch.
[*]Some apps came out well, others, not so well, still others, very poorly. Wonky post-upgrade behaviour from a number of apps including LibreOffice, Signal, Rhythmbox.
[*]LXD containers migrated nicely, which is pleasantly surprising. Was expecting more problems.
[/list]
Altogether, neither more nor less problematic than past upgrades. The first point release should fix many of the worst bugs; fewer of the non-critical but still irritating ones.

---

### Post by roboticforest on 2020-06-09
Greetings all,

My experience so far has been mixed. Currently I'm extremely frustrated and lost. I can't find any answers online to any of the problems I've been having. Google, DuckDuckGo, and StackExchange aren't giving any helpful results. So, with that said, here's my general experience so far:

Like I did with 12.04 and 16.04 I ran 20.04 off of a flash drive for some days. Everything was working fantastically. I'm not perfectly happy with the new GUI, but that's not a deal breaker. Running LibreOffice, Firefox, installing Chrome, and a bunch of other software I normally use, all went really well. Generally, I was happy with 20.04 and figured that I would figure out ways to tweak the GUI after it was installed. First though, I wanted to try out my new printer and get it working in the sandbox that is a live CD.

However, the only thing I *couldn't* do on the live CD was get my printer working. I've needed a printer for a long time and was finally able to buy one, so I bought a printer that was evaluated as working out of the box for Ubuntu 20.04, but while I could do simple prints with only the generic defaults on the live CD I couldn't scan. I never got it fully working, There were MANY problems getting the printer drivers installed (literal days of internet searches and frustration), and finally an important part of the installation requires a reboot (which I can't do on a live CD), so I had to wait until Ubuntu was properly installed to try again.

The installation process of Ubuntu itself went fine. No errors or hiccups. It actually installed much faster than I remember 16.04 installing, and the boot up process is so dang fast that if my HDD weren't encrypted I could blink and miss it!

Ubuntu itself hasn't been stable though... and I can't find fixes to any of the problems I'm having. I can't get the printer drivers installed at all. My entire computer keeps locking up and needing to be hard booted. I can't kill frozen processes! If my wifi cuts out (and it is daily and intermittent) then everything dies with it. I even lost my GUI for a few days and I have no idea why it broke, or why it eventually came back.

I need help fixing this. I *need* this computer stable again. Where can/should I post more details about the issues I'm having? I saw that there is a General Help sub-forum here. Is that the best place for me to go, or is there somewhere else that is more appropriate to the kinds of troubles I've mentioned? Sorry, but this is my first post on this website and I don't know my way around it yet.

---

### Post by sudodus on 2020-06-09
> **roboticforest said:**
> ...

I need help fixing this. I *need* this computer stable again. Where can/should I post more details about the issues I'm having? I saw that there is a General Help sub-forum here. Is that the best place for me to go, or is there somewhere else that is more appropriate to the kinds of troubles I've mentioned? Sorry, but this is my first post on this website and I don't know my way around it yet.

(Until somebody suggests something better) I agree that it is a good idea to

- start a thread in the [General Help sub-forum](https://ubuntuforums.org/forumdisplay.php?f=331).

- An alternative might be the [Hardware sub forum](https://ubuntuforums.org/forumdisplay.php?f=332) (due to the issues with the printer).

-o-

- You can also ask a question at [AskUbuntu](https://askubuntu.com/). Please be aware that AskUbuntu is focused on single questions and straight answers. The Ubuntu Forums are more open to discussion of various aspects of a problem or feature.

---

### Post by ActionParsnip on 2020-06-10
DigitalOcean image. Works great. No problems whatsoever :)

---

### Post by roboticforest on 2020-06-12
> **sudodus said:**
> (Until somebody suggests something better) I agree that it is a good idea to

- start a thread in the [General Help sub-forum]("https://ubuntuforums.org/forumdisplay.php?f=331").

- An alternative might be the [Hardware sub forum]("https://ubuntuforums.org/forumdisplay.php?f=332") (due to the issues with the printer).

-o-

- You can also ask a question at [AskUbuntu]("https://askubuntu.com/"). Please be aware that AskUbuntu is focused on single questions and straight answers. The Ubuntu Forums are more open to discussion of various aspects of a problem or feature.

Thank you. I'll probably try the hardware forum then.

I've already made a post on AskUbuntu about my wifi card, and I have a friend trying to help me out as well. I'm not sure what we can really do about it if it's a driver problem though, but we're looking around.

---

### Post by Frantic_Earthling on 2020-06-13
I have an Asus laptop G750JZ with the following specs:

i7 Intel® Core™ i7-4710HQ CPU @ 2.50GHz × 8 
RAM 16 Gb
GeForce GTX 880M/PCIe/SSE2
HD 1 Tb  
SSD 250 Gb

I have been running a dual-boot system with Win10 Pro and Ubuntu 18.04 LTS.

I have just made a fresh install of 20.04 LTS, erasing (on purpose) my old 18.04 install.

I did not choose the “something else” option, as I was presented right from the start with the option to install over the old version.

The install went flawlessly.

My dual boot works fine. 

To top it all, my Brother printer MFC-J4625DW was automatically recognized. I only had to install the scanner part manually but was still impressed by the automatic recognition of the printer.

Many thanks to the folks at Canonical!

---

### Post by yetimon_64 on 2020-06-16
I still haven't done a Focal install for myself yet, but my first 2 installs of Xubuntu Focal for another person have gone very well. 

No dual booting involved just single Xubuntu Focal installs on 2 old laptops, an Asus laptop circa 2008 and a Lenovo laptop circa 2012. Everything is working very well on these older laptops. The Asus is only a 2 GB RAM machine and is a bit slow, but still usable, with Xubuntu (Lubuntu would have been a better choice but the user is new to any Linux installations so I decided on one release/flavor for both machines); the Lenovo with 4 GB of RAM is very smooth and fast with Xubuntu on it.

---

### Post by exploder on 2020-08-18
Clean install on an older HP desktop and about a six month old HP laptop. The desktop machine had no problems, the laptop had issues with the kernel relating to the onboard sound. Installing the mainline kernel 5.8.1 solved the problem but there are some harmless kernel errors on boot. The next point release should fix it right up and the laptop is perfectly usable now. I expected problems with a laptop that new.

---

### Post by maestrobwh1 on 2020-09-13
Upgraded to kernel 5.7.1  using mainline.

Thinkpad 11E with Intel core M-5Y10C, and Windows 10 was snappier on this machine than either Ubuntu, Kubuntu, or Linux Lite using 5.4.

Now with 5.7.1, boot time is cut in half an overall desktop experience is significantly better.

---

### Post by metacell on 2020-09-28
First I did an upgrade from Xubuntu 18.04 to 20.04, and sound disappeared. I solved it by googling and then typing "sudo alsa force-reload" every time I started up my computer!
Then I did a clean installation with Xubuntu 20.04, and sound worked like normal.

The partitioning tool still needs some work. If you choose to let Ubuntu partition the drive, you can select LUKS encryption, but you can't choose the size of your swap partition. A tiny swap partition is created automatically (1 GB swap on my 8 GB RAM system). I had to google for some time before I realised I could create a swap file manually after installation.
If, on the other hand, you do manual partitioning, the installer automatically creates an ext4 partition inside your LUKS partition. There's no way to create a swap partition inside the same LUKS partition.
This is far too complicated for the casual user who just wants to encrypt their whole drive! For example, hibernation doesn't work if your swap isn't at least as big as your RAM.

Selecting proprietary drivers for my nVidia card during install, caused the installer to exit with an error message later on. Fortunately, I could easily switch to proprietary drivers after install.

Ubuntu is an incredibly powerful system, but there are still a lot of bugs and kinks to straighten out.

---

### Post by CelticWarrior on 2020-09-28
> [COLOR=#000000]This is far too complicated for the casual user who just wants to encrypt their whole drive! For example, hibernation doesn't work if your swap isn't at least as big as your RAM.[/COLOR]


The casual user neither creates anything outside the installer's workflow nor uses hibernation, a foreign concept in any modern OS, including Windows, since many years ago.

---

### Post by metacell on 2020-09-29
> **CelticWarrior said:**
> The casual user neither creates anything outside the installer's workflow nor uses hibernation, a foreign concept in any modern OS, including Windows, since many years ago.

Windows 10 still [supports]("https://support.microsoft.com/en-us/windows/shut-down-sleep-or-hibernate-your-pc-2941d165-7d0a-a5e8-c5ad-8c972e8e6eff") hibernation. It's very useful on laptops.

---

### Post by gourmetsaint on 2020-10-08
Newbie to Linux and converted from Windows Server 2019 using desktop installer on a server with 128Gb ram, 4 x 200Gb SAS SSDs and 8 x 4Tb SAS HDDs.
Chose ZFS and installed on 1st SSD. Copied 1st SSD partition map to 2nd SSD. Attached matching partitions to give mirrored bpool and rpool.
Created RAIDZ2 dpool on 8 x HDDs. Partitioned last2 SSDs identical small part1 and balance part2. Added mirror log to dpool using pair of part1 and striped cache on pair of part2.

Going well. No file errors. Have samba shares on dpool filesets mounted under /mnt. Dedicated separate fileset for media files with 1M recordsize. Plex Server installed and working. Great learning experience.

---

### Post by blackbird34 on 2020-10-09
I upgraded on KDE Neon from the Ubuntu 18.04 LTS base to the 20.04LTS base when it was offered during the summer. It went perfectly.

---

### Post by Dennis N on 2021-05-02
These upgrades were done 24 Apr 2021
Now is the window when the 3-year full support period ends for some flavors, so time is of the essence.

_Upgrade Ubuntu MATE 18.04 LTS to 20.04.2 LTS_
I used Software Updater, which has been offering this upgrade for some time. Full support will now be ending. This upgrade worked and required no post-upgrade adjustments at all. The requirements were to be fully upgraded before beginning, to disable PPAs, and stop xscreensaver daemon from running. The PPAs will be automatically disabled if you don't do it yourself, but failing to disable xscreensaver will stop the installation and required user action before it proceeds.
_Upgrade Ubuntu 18.04 LTS to 20.04.2 LTS_
This OS has 2 more years of support, but I decided to upgrade now while I was at it. Also 20.04 has some usability improvements over 18.04 I wanted. Again, I relied on Software Updater. The same requirements for upgrading as above were in effect. I also recommend to disable any gnome-shell extensions. I had one instance in the past where failing to do this resulted in failure to boot to the Desktop. Today's upgrade worked successfully, but after upgrading it was necessary to remove an extension no longer available and find a replacement, and to upgrade a few others. The gnome-shell theme I had in 18.04 did not theme the shell correctly and I had to find a new theme. The applications all upgraded nicely. Just minor issues. 

In summary, these LTS upgrades were a success.

---

