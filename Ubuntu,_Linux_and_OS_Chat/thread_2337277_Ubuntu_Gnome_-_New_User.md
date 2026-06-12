---
title: "Ubuntu Gnome - New User"
date: 2016-09-16
forum: Ubuntu, Linux and OS Chat
---

### Post by ray42 on 2016-09-16
Hello All

Been using Linux mint, I love it. But I found Ubuntu Gnome which is also fabo.

I assume this is supported here?

If so what is there to watch out for, what do I need to read. I prefer shortened info where it is available.

---

### Post by TheFu on 2016-09-16
Zero beans! Wow. Never seen that before. Welcome to our forums. Join in. Read and ask away!

Linux isn't just a GUI.  The GUIs can be swapped at will. They are just programs like any other. Find the one you like and use it.  Must be 50 different DEs/WM to pick from, each with a loyal following.  [http://www.ubuntu.com/about/about-ubuntu/flavours](http://www.ubuntu.com/about/about-ubuntu/flavours) explains about the different flavors.  Some only have 3 yrs of support in their LTS version, so be aware of that.

To what level do you wish to learn this stuff?  For example, my Mom used Linux for years just by pointing and clicking. I did all maintenance for her from 4 states away. That provides about 10% of what a computer can do, sorta like Windows. OTOH, if you want to go deeper to unlock the other 90% of the power, then learning the command line/shell/CLI is how to unleash that.  Plus, the CLI doesn't change much over decades and the same commands I use today are either identical or nearly identical as those I learned in 1993. No need to learn a new OS every 3 yrs because some GUI designer wants to make their mark ... cough .... unity. ;)  Or you can move to a new GUI every few months, if that is your joy.  Completely up to you!

So, when folks ask me how to Learn Linux, I always ask their purpose and computing background. Learning to be a Linux admin is different from learning to be a Security Specialist or a programmer or an end-user who just wants to print boarding passes from the airlines. ;)  Completely up to you, but there are 2 articles that provide a nice overview to people coming into the Linux family:  [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) - read just the first 4 articles linked there. Should take less than 45 min total.

---

### Post by pauljw on 2016-09-16
I don't know what your machine specs are, but it you have at least 4G memory and a quad-core processor you might consider installing virtualbox and then you can learn most any OS that you want.  My laptop came with 8G of RAM and an 8 core i7 processor.  I would create vm's with 4G of RAM, 4 processors and 30G hard drive space.  These perform as well as an installed host environment unless you're trying to play games as the video is lacking.  If you are just doing normal system use things i.e. surfing the web, dealing with email, chatting on irc and various other educational things, you would be hard pressed to tell the difference from your host system.

My host is a 14.04LTS system which is fully supported until 2019.  I have no intention to upgrade, but I use 16.04LTS daily in a vm and have no issues what so ever.  I also have a PC-BSD vm and several other linux distros which allows me to experiment and learn each environment without jeopardizing my stable host system.

Just something to think about...  :)

---

### Post by TheFu on 2016-09-16
@pauljw .... a few corrections.

14.04 is NOT fully supported until 2019.  Only the core programs are. Any 3rd party programs get community support, which often ends after 9, 18, 36 months.  There is a command to let you see end-of-support for every package. On my 14.04 desktop:
```
$ ubuntu-support-status
Support status summary of 'lubuntu':

You have 203 packages (8.2%) supported until February 2015 (9m)
You have 12 packages (0.5%) supported until June 2017 (9m)
You have 148 packages (6.0%) supported until May 2017 (3y)
You have 1702 packages (68.8%) supported until May 2019 (5y)

You have 99 packages (4.0%) that can not/no-longer be downloaded
You have 310 packages (12.5%) that are unsupported

```

The GUI isn't the OS.  You can use whatever GUI you like, but be aware that settings used by the different GUIs can conflict and cause issues. The easy way to avoid that is to either use the **guest** account which gets created/wiped at every login or to create a new userid for each different DE - desktop environment - you play with.  

Not really an issue, just a suggestion - Linux VMs don't need 4 vCPUs or 4GB of RAM. In fact, often providing too many resources like that will make a VM SLOWER.  Linux isn't Windows and doesn't only install the specific kernel based on the number of CPUs it sees at install-time.  Changing the RAM and vCPUs to be the minimum needed for the use of the VM will make both the guestVM and the hostOS more responsive.  1 vCPU and 2G of RAM is usually all that is needed on a 5yr old or newer system for very good desktop performance. We're talking C2D or better CPUs. I think you'll be surprised. Having more resources available to do other things ... like run that development web server, is a good thing, perhaps?

Lastly, if you are running a Linux hostOS, perhaps using KVM would make more sense than vbox?  KVM is built into the kernel and the GUI performance using QXL video drivers is very good.

Just something else to think about. ;)

---

### Post by pauljw on 2016-09-16
yeah, whatever, there're always choices.  my choices work for me.  i've also read that the command you refer to: "ubuntu-support-status" is not actively updated and returns inaccurate results.  my personal experience has been that my vm's enjoy the additional resources.  i also have used kvm, i find vbox to be easier to use, perhaps due to it being what i have the most experience with.  i started with vmware in 2006, then switched to vbox and that's what i prefer.  

thanks for the corrections, always nice to have those with so much knowledge keeping me informed.

---

### Post by ray42 on 2016-09-17
Hi All

Intermediate user. Long time Windows user. 50/50 now.

I like to do everything that I can do in windows, so not too much difficulty in achieving that with Mint. Mint seems more akin to Windows in as much as it feels fiddly. Am I being smooched or is Gnome really as good as it feels, easy and smooth?
[COLOR=#000000]
TheFu, yes I have tested about 6 of the popular distros to date. Is it not really a good idea to use [/COLOR][COLOR=#000000]16.04LTS then, should I switch to [/COLOR][COLOR=#000000]14.04LTS[/COLOR][COLOR=#000000]? I have heard to stay away from Wine, are the others OK then?

[/COLOR]Oh yes, and how do I sort out the screensaver on Gmone?

```
System:    Kernel: 4.4.0-36-generic x86_64 (64 bit)
                 Desktop: N/A Distro: Ubuntu 16.04 xenial


Machine:   System: Medion (portable) product: E6227 v: 1.0
                 Mobo: Medion model: E6227 v: 1.0
                 Bios: American Megatrends v: 207 date: 04/03/2012


CPU:       Dual core Intel Core i3-2350M (-HT-MCP-) cache: 3072 KB
                flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 9179


Info:      Processes: 257 Uptime: 17 min Memory: 1433.6/3845.9MB
             Init: systemd runlevel: 5 Gcc sys: 5.4.0
             Client: Shell (bash 4.3.461) inxi: 2.2.35 

```

---

### Post by TheFu on 2016-09-17
I don't know anything about gnome. Don't use it. Haven't tried it in a few years.  Using a Core i3-5015U right now.  Don't know what good the rest of the info it.

Should you use 16.04.x or 14.04?  I don't know. Only have 1 system on 16.04 and that was to get new hardware supported. If that wasn't needed, it would probably still be running 14.04.x to increase the compatibility of data files on my other 14.04.x desktop. Plus I have a personal issue with systemd. It doesn't work the way I like, so avoiding it until it gets passed alpha level code (clearly my opinion is different from all the distro builders).  The same guy wrote Pulse-Audio and it has been about 10 yrs and still doesn't work right out of the box.  Just sayin.

All my other systems are on 14.04. Might move the main desktop to 16.04.x before Thanksgiving. Don't plan to move the others until next year at the earliest. They are servers, where stability is more important than "new."  Plus, those systems don't need to connect to external web-apps that change every week, so a few of them will probably stay on 14.04.x until 2018 or 2019.  Desktops interact with the world much more and having the newer GUI programs could be important.

Sorry I'm not any real help.

---

### Post by kurt18947 on 2016-09-17
I use ubuntu-gnome daily. I have a few extensions found here that I consider mandatory:

```
extensions.gnome.org
```

Everyone works a little differently so what works for me may not work for you.
It isn't as easy to create launchers in Ubuntu-gnome as it was in the gnome 2 or Xubuntu releases but .desktop files can serve the same purpose and there's an extension to help organize .desktop files and make them accessible. If you want to get a taste of the different 'flavors', installing to a live USB or DVD is one method. Although for me, an Ubuntu-Gnome fresh install is pretty spartan. A few extensions and a few packages from the repositories to replace what Gnome has removed in their effort to 'simplify' the UI makes it usable for me.

---

### Post by ray42 on 2016-09-18
> **kurt18947 said:**
> I use ubuntu-gnome daily. I have a few extensions found here that I consider mandatory:
```
extensions.gnome.org
```.

Yes thx, I have stumbled on this myself. Yes 1 or 2 are needed to make it nice. I'm lovin Gnome so far.

So what is essential reading for Gnome, as I found there seemed to be a high level of techy knowledge in Mint to make it great, or perhaps that was just me?

Anyhow Gnome seems simpler. I hope it proves so when the 'Sugar' hits the fan, and it gets corrupted or messed up by the monkey using it, i.e. me!

Perhaps I should find out what I had been doing with the Mint OS so that I can ask what is needed to replicate those features, that is of course if they are really needed?

---

### Post by TheFu on 2016-09-18
Backups.  Daily, versioned, backups.  If you do this, then you are just a restore away from most solutions.

---

### Post by ray42 on 2016-09-18
Doh! That is so obvious! Excellent advice.#-o

---

