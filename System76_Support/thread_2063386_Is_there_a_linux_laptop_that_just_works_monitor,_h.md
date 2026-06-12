---
title: "Is there a linux laptop that just works? monitor, hibernate, sleep :-("
date: 2012-09-26
forum: System76 Support
---

### Post by whatislinux on 2012-09-26
I dreamed of a linux laptop that just worked. I got the latest gazelle professional. I was a fool.

1. It does not hibernate. That's fine. I should have read the page more carefully. It should have been clear from the feature list explicitly mentioning suspend that I wouldn't be able to hibernate.

2. If I plug a monitor in via HDMI, I get really high kworker cpu usage and the mouse is really really laggy.

3. It often wakes from sleep with a black screen. I have a functioning mouse cursor, but I can't see the desktop. I resort to switching to a terminal(ctrl-alt-f1) and restarting the desktop manager. Losing everything I was working on and defeating the purpose of a sleep function.

Is there another offering from system 76 not be plagued with linux issues like this?

4. This is unrelated to linux: I got a matte display because I didn't like reflective glossy displays. For some reason the frame around the display is a glossy and reflective surface.

---

### Post by OrangeCrate on 2012-09-27
Ubuntu Certified Hardware:

[http://www.ubuntu.com/certification/desktop/](http://www.ubuntu.com/certification/desktop/)

---

### Post by Ubun2to on 2012-09-27
1. Hibernate is disabled by default due to it being inconsistent-some people have it working perfectly, others usually get failures for resuming from hibernate. I personally love hibernate, as I can swap the batteries out without shutting down, but I rarely do things that I can't save and then shut down to swap the battery. But, until I can get hibernate to cooperate with me, I'm leaving it disabled.
Also, hibernate on Windows 7 is currently buggy as well. (Unrelated, but I just thought I'd bring it up.) Although it is reliable in bringing the desktop back up, it makes my computer slower than molasses, and I have to wait about a minute before it responds when I click stuff for about an hour. It's like the hard drive is spinning at 1200 RPM trying desperately to pull the processes off the drive and back into the RAM (which obviously can't be true, given that mine spins at 7200 RPM). Think about ice cream-sometimes, they freeze it so cold, you have to wait 20 minutes for it to thaw enough just to be able to put in the scooper. This is basically what it does to the drive, only for an hour, and it is still slightly slower after that until I reboot.
2. Currently, System76 does not have any GPUs on their laptops, and Intel HD graphics are handled by the CPU, so the CPU gets the short end of the stick in this case.
But, a laggy mouse is weird in any case-they don't use much processing power to begin with.
3. Not waking from Suspend properly is something Ubuntu has always struggled in (in my experience when I installed it on my friends' laptops), like WiFi and GPU drivers.
4. The frame around the display is basically unchangable unless you do it by taking it apart and reassembling it. When they meant display, they meant screen.

---

### Post by cprofitt on 2012-09-27
I currently have a Lenovo T500 and a Lenovo W520 and both work with all function buttons, LCD brightness, etc.

I have not tried hibernation as I either sleep or shutdown.

I am in the market to replace my T500 and currently looking at the T530.

I had a System76 Gazelle and it worked as well (with the System76 drivers installed), but I returned it due to issues with the battery life and the overly warm palm rest on the left hand side.

My money would be getting a Lenovo, but take a look at the list posted above of certified laptops.

---

### Post by snowpine on 2012-09-27
Ubuntu is not the only Linux, you could try a distribution (such as Debian, Slackware, or CentOS) that is designed more for stability?

---

### Post by OrangeCrate on 2012-09-27
> **cprofitt said:**
> I currently have a Lenovo T500 and a Lenovo W520 and both work with all function buttons, LCD brightness, etc.

I have not tried hibernation as I either sleep or shutdown.

I am in the market to replace my T500 and currently looking at the T530.

I had a System76 Gazelle and it worked as well (with the System76 drivers installed), but I returned it due to issues with the battery life and the overly warm palm rest on the left hand side.

**My money would be getting a Lenovo**, but take a look at the list posted above of certified laptops.

+1

@OP - For what it's worth, I just bought this one from Costco. Good specs, solid build, for not a lot of money. A good value IMO, considering the 90 day no questions asked return policy, the fact that Costco extends the computer warranty an additional year, and they offer free technical support through their concierage service.

[http://www.costco.com/Lenovo-G570-Laptop-with-Intel%C2%AE-Core%E2%84%A2-i5-2450M-2.5GHz-Processor.product.100007837.html](http://www.costco.com/Lenovo-G570-Laptop-with-Intel%C2%AE-Core%E2%84%A2-i5-2450M-2.5GHz-Processor.product.100007837.html)

---

### Post by isantop on 2012-09-27
> **whatislinux said:**
> 1. It does not hibernate. That's fine. I should have read the page more carefully. It should have been clear from the feature list explicitly mentioning suspend that I wouldn't be able to hibernate.

Hibernate is disabled in Ubuntu. It's not something we really have any control over, but hibernate is a hackish solution to a problem that no longer really exists.

> **whatislinux said:**
> 2. If I plug a monitor in via HDMI, I get really high kworker cpu usage and the mouse is really really laggy.

This sounds like a software glitch, as I can't replicate it here in the shop.

> **whatislinux said:**
> 3. It often wakes from sleep with a black screen. I have a functioning mouse cursor, but I can't see the desktop. I resort to switching to a terminal(ctrl-alt-f1) and restarting the desktop manager. Losing everything I was working on and defeating the purpose of a sleep function.

This is caused by a bug within Ubuntu; any laptop running Ubuntu will experience this problem. It's caused by Ubuntu failing to resume properly when the lid is opened (It's not handling the resume trigger properly under certain suspend conditions). You can work around this issue in the meantime by suspending with the menu entry or by using the Fn+F4 hotkey. The system will always resume properly when suspended using these methods. 

> **whatislinux said:**
> 4. This is unrelated to linux: I got a matte display because I didn't like reflective glossy displays. For some reason the frame around the display is a glossy and reflective surface.

That is by design; the screen itself, however, should be matte. We don't have matte display bezels.

---

### Post by ufugu on 2012-09-27
I have the same machine, and suspend resumes perfectly 100% of the time with Gnome Shell or Xubuntu.  System76 has suggested in the past that it can be fixed with kernel updates, but FWIW it really seems to be related to Unity.

---

### Post by Ubun2to on 2012-09-27
> **ufugu said:**
> I have the same machine, and suspend resumes perfectly 100% of the time with Gnome Shell or Xubuntu.  System76 has suggested in the past that it can be fixed with kernel updates, but FWIW it really seems to be related to Unity.

Unity is actually just a plugin of Compiz, so it could be a problem going all the way back to Compiz.
Also, my desktop runs Unity and has 0 problems with waking from sleep (except if the kernel manages to panic, and I have to attempt to force a shut down, but that only happened once due to a glitchy package).

---

### Post by BillyAlt on 2012-10-04
I might be a bit late to the party here, but I believe I can tell you why your mouse lags with HDMI.

HDMI is a bit infamous for input lag. The longer the cable, the more noticeable the lag becomes. I'd advise not going much longer than 3 feet.

Might not necessarily be your problem, but it's a thought.

---

### Post by Rich_S on 2012-10-06
I get the black screen with an error message when resuming my Gazelle from sleeping with the lid closed too.

I just rub my finger on the touchpad and wait 10-15 seconds and the GUI screen comes back every time.

---

### Post by joe4ska on 2012-10-09
> **snowpine said:**
> Ubuntu is not the only Linux, you could try a distribution (such as Debian, Slackware, or CentOS) that is designed more for stability?

System76's drivers will only work with Official Ubuntu based distributions. IE Xubuntu, Ubuntu Studio, Kubuntu, Lubuntu.

Even distributions that should be technically compatible like Peppermint OS or Ubuntu Gnome Shell Remix are not compatible.

You can use other distributions it just means more legwork getting some of the hotkeys webcam and other features working. I've tried several on my Lemur-Ultra as I love distrohop.

---

### Post by snowpine on 2012-10-09
> **joe4ska said:**
> System76's drivers will only work with Official Ubuntu based distributions. IE Xubuntu, Ubuntu Studio, Kubuntu, Lubuntu.

Even distributions that should be technically compatible like Peppermint OS or Ubuntu Gnome Shell Remix are not compatible.

However, you can use other distributions it just means more legwork getting some of the hotkeys webcam and other features working.

I did not realize that; I personally would not buy hardware that locked me into using a particular operating system... buyer beware I suppose.

---

### Post by joe4ska on 2012-10-09
Well, in my case the only drivers it provides is hotkeys for the backlight. and a driver for the media card reader.

If i'm using Fedora or Sabayon for instance I just add xbacklight to my packages and use that to control backlight from the terminal, I then create hotkeys. 

For the media card i'm sure I can easily install packages that enable it but I never use it anyway.

I don't feel locked in at all. It just means I need to take extra steps when I venture away from Ubuntu.

---

### Post by Ubun2to on 2012-10-09
> **snowpine said:**
> I did not realize that; I personally would not buy hardware that locked me into using a particular operating system... buyer beware I suppose.

Wrong. They will fix your hardware regardless of whether you have OSX, Windows, Arch Linux, Unix, FreeBSD, even OS/2.

They just don't provide software side support for non-Canonical backed distros. Why? Well, consider the fact that there are thousands of distros out there. Now, consider how many of them are only used by one or two people. Is it really economically sustainable for a small company like System76 to hire thousands of employees to support distros that will likely never be used by any System76 customers? No. Even when you don't provide support for the defunct distros, someone can easily throw together a distro and publish it in less than an hour, so it would be ridiculous constantly hiring and firing workers that you can't even pay.
Not even big companies like HP and Dell could afford to do this without firing half their staff.

---

### Post by joe4ska on 2012-10-10
Yep, and I should mention I've installed Arch, Fedora, Gentoo... just about every major distribution and they all worked as expected. It's just a matter of extra research for the other distributions. With a lot less hassle than my Apple laptop and desktop in the past.

I'd buy another System76 laptop in a heartbeat.

---

### Post by isantop on 2012-10-10
> **Ubun2to said:**
> Wrong. They will fix your hardware regardless of whether you have OSX, Windows, Arch Linux, Unix, FreeBSD, even OS/2.

They just don't provide software side support for non-Canonical backed distros. Why? Well, consider the fact that there are thousands of distros out there. Now, consider how many of them are only used by one or two people. Is it really economically sustainable for a small company like System76 to hire thousands of employees to support distros that will likely never be used by any System76 customers? No. Even when you don't provide support for the defunct distros, someone can easily throw together a distro and publish it in less than an hour, so it would be ridiculous constantly hiring and firing workers that you can't even pay.
Not even big companies like HP and Dell could afford to do this without firing half their staff.

This. You can even install DOS on it, and if the hardware fails, we'll fix it for you. 

We don't set up any locks to prevent other OSs from being isntalled. We don't develop the System76 driver for any non-Ubuntu OSs, but then it usually only provides small fixes for things like Hotkeys, card readers, cameras, etc. We don't do any testing on other OSs, but you're free to install whatever you want.

---

### Post by screaminj3sus on 2012-10-21
> **whatislinux said:**
> I dreamed of a linux laptop that just worked. I got the latest gazelle professional. I was a fool.

1. It does not hibernate. That's fine. I should have read the page more carefully. It should have been clear from the feature list explicitly mentioning suspend that I wouldn't be able to hibernate.

2. If I plug a monitor in via HDMI, I get really high kworker cpu usage and the mouse is really really laggy.

3. It often wakes from sleep with a black screen. I have a functioning mouse cursor, but I can't see the desktop. I resort to switching to a terminal(ctrl-alt-f1) and restarting the desktop manager. Losing everything I was working on and defeating the purpose of a sleep function.

Is there another offering from system 76 not be plagued with linux issues like this?

4. This is unrelated to linux: I got a matte display because I didn't like reflective glossy displays. For some reason the frame around the display is a glossy and reflective surface.

#3 is a known bug with the intel driver, that afiak is now finally fixed with the latest precise updates and in 12.10. I suffered that issue on my asus laptop, not a system76 specific issue. Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/966744](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/966744)

#1 is an ubuntu issue, ubuntu totally disables hibernate by default. You need to edit a policykit setting to get the hibernate option available at all. [http://pauljoyceuk.com/codex/2012/howto-make-ubuntu-12-04-hibernate-successfully/](http://pauljoyceuk.com/codex/2012/howto-make-ubuntu-12-04-hibernate-successfully/).

---

### Post by BBQdave on 2012-10-23
> **whatislinux said:**
> Is there another offering from system 76 not be plagued with linux issues like this?

Not sure what you stated are Linux issues.

I tested a Toshiba C655 -at the store- with a Fedora Linux live CD. Everything went well with the test. Purchased the machine, paying a little MicroSuck tax... wiped the hard drive - that is to say never booted Windoze, installed Fedora 16 and everything works.

Now to qualify this, I use suspend and shutdown. I am currently running F17 without issue. This machine is my main work and play device, could not be happier :)

Not trying to rain on System76, I think they have solid hardware. Just not sure about Ubuntu and additional drivers and such... Perhaps it is appealing to have solid hardware with a LTS release, but inexpensive solid hardware and an annual upgrade -Fedora on a Toshiba Satellite- is appealing too :D

---

### Post by isantop on 2012-10-24
> **BBQdave said:**
> Not sure what you stated are Linux issues.

I tested a Toshiba C655 -at the store- with a Fedora Linux live CD. Everything went well with the test. Purchased the machine, paying a little MicroSuck tax... wiped the hard drive - that is to say never booted Windoze, installed Fedora 16 and everything works.

Now to qualify this, I use suspend and shutdown. I am currently running F17 without issue. This machine is my main work and play device, could not be happier :)

Not trying to rain on System76, I think they have solid hardware. Just not sure about Ubuntu and additional drivers and such... Perhaps it is appealing to have solid hardware with a LTS release, but inexpensive solid hardware and an annual upgrade -Fedora on a Toshiba Satellite- is appealing too :D

What kernel is Fedora using? Most of the problems we saw were with 3.2.0

---

### Post by screaminj3sus on 2012-10-24
> **isantop said:**
> What kernel is Fedora using? Most of the problems we saw were with 3.2.0
f17 is currently on 3.5.x, its planned to get an update to 3.6. Not sure which one it was released with, but probably newer than 3.2.

---

### Post by BBQdave on 2012-10-24
> **isantop said:**
> What kernel is Fedora using? Most of the problems we saw were with 3.2.0

Fedora 17 up to date:

Kernel Linux 3.6.2-4.fc17.x86_64
with GNOME 3.4.2

---

### Post by Mikeb85 on 2012-10-25
I've got a ThinkPad T530.  It works flawlessly with both openSUSE 12.2 and Ubuntu 12.10 - it sleeps and wakes up instantly when the lid is opened/closed, all the function keys work, the battery indicator on the outside of the machine works perfectly, the WIFI connects within 5-10 seconds of waking up, etc...  Only thing that doesn't work on either is the fingerprint reader, but I knew that when I bought the machine.

---

### Post by screaminj3sus on 2012-10-29
I'd just like to add, I got my new system76 lemur ultra delivered today :). Suspend and Hibernate works fine out of the box (well... as out of the box as hibernate can possibly work in ubuntu, I had to use the polkit tweak to enable it obviously).

In fact every single thing I've tried works out of the box, such as the all of the keyboard hotkeys, the system76 guys did a great job IMO.

---

