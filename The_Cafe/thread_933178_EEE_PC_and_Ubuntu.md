---
title: "EEE PC and Ubuntu"
date: 2008-09-29
forum: The Cafe
---

### Post by Aetheric on 2008-09-29
So I got an eee PC 900 with XP on it. And I love it to bits, after I ripped out the Microsoft crap and put Eeebuntu on it. But I have a niggling problem...

Eeebuntu seems slow. And I get only about 2 hours on the battery with the screen brightness turned down to nothing and the wireless turned off. I really, really need to max out the battery life above all else and I will only be using it for a bit of Internet surfing and a lot of typing.

So I have a choice - fix Eeebuntu, or find another distro that is more lightweight. I'm not sure what I should be looking for though, and I'm not sure what distros work on the EEE PCs. So here I am, begging for the collective expertise of the Ubuntu community.

---

### Post by Johnsie on 2008-09-29
You could try being bleeding edge and puttinging Intrepid Ibex on it.  Intrepid seems to work alot better on my eepc than hardy or hardy with eee scripts. They are developing Intrepid to be eeepc friendly.

---

### Post by kerry_s on 2008-09-29
[http://www.canonical.com/projects/ubuntu/nbr](http://www.canonical.com/projects/ubuntu/nbr)

---

### Post by Aetheric on 2008-09-29
The netbook remix annoys me for some reason.

I'll look up Intrepid, it might suit my tastes.

I've heard some good things about Damn Small Linux, can anyone advise me on that?

---

### Post by uberdonkey5 on 2008-09-29
shame you didn't get the Xandros pre-install - apparently battery last for 3-3.5 hrs (not sure on mine cos I use it so intermittently). I was thinking intrepid would be a bit heavy for job? According to bench marking:

[http://www.liliputing.com/2008/09/whats-the-best-linux-distro-for-the-eee-pc-901.html](http://www.liliputing.com/2008/09/whats-the-best-linux-distro-for-the-eee-pc-901.html)

ubuntu 8.10 performs better than Xandros, Fedora and Mandriva for many things, but nothing on battery power. Earlier articles on alternate distros suggest the fan often works harder on other distros such as ubuntu, Mepis, Mandriva. Maybe thats what saps the power.

If you are using the Eee PC in the car you can get an adapter for charging it. The power cable fitting is pretty standard so there are probably other options for recharging. Maybe you can even get a spare battery, or buy a battery which lasts longer:

[http://www.lithium-batteries.net/laptop/asus/eee-pc-battery.html](http://www.lithium-batteries.net/laptop/asus/eee-pc-battery.html)

see this for an energy saving distro of ubuntu (wattOS), though not sure how compatible it will be with eee pc (may be a hassle setting it up).

[http://www.downloadsquad.com/2008/07/12/wattos-light-weight-ubuntu-based-linux-distro/](http://www.downloadsquad.com/2008/07/12/wattos-light-weight-ubuntu-based-linux-distro/)

---

### Post by Technoviking on 2008-09-29
Using the netbook remix on my sons eeepc 900, and he loves it.

---

### Post by wolfen69 on 2008-09-29
[Pupeee linux]("http://www.puppylinux.org/wiki/hardware/general/eeepc") is awesome. runs super quick.

---

### Post by t0p on 2008-09-29
I've installed Ubuntu 8.04.1 on my eeepc 4G - the full distro, not some sawn-off version.  To install it, I followed the instructions at [www.pendrivelinux.com]("http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/").

Then I did the various tweaks described on the [eeeuser.com wiki]("http://wiki.eeeuser.com/getting_ubuntu_8.04_to_work_perfectly?s=ubuntu%20eee%20riceeey"), to fix some problems like the eeepc not shutting down properly,  fixing compiz so windows can be dragged beyond the top of the screen, setting smaller fonts and icons... loads of stuff.  The easiest way to make ubuntu work properly is to download and run [the RiceeeyTweak script]("http://eee.ricey.co.uk/files/eee/RiceeeyTweak.sh").

I'd advice all ubuntu enthusiasts to install it on their eeepcs.  It makes the little notebooks so more usable...

---

### Post by mrtomcef on 2008-09-30
When I'm using the battery on my Asus Eee, I always run PowerTop. I believe I installed it by typing this: > sudo apt-get install powertop

---

### Post by Mr.Auer on 2008-09-30
On Ubuntu 8.04 and Eee pc 701, Gnome power manager doesnt shut down when battery is critical.

The fix is to use Gkrellm to launch a shutdown script instead, explained here:

[http://forum.eeeuser.com/viewtopic.php?pid=352258](http://forum.eeeuser.com/viewtopic.php?pid=352258)

"

Well I am no expert but this works for me smile

1) enable shutdown command for normal users - type:

Code:

sudo visudo

and add

Code:

%admin ALL=(root) NOPASSWD: /sbin/shutdown

at the end of the file. Make sure there is also a empty line (i.e., press enter twice after typing the above) at the end of the file. Save and quit - the program visudo will check that the file is ok and warn you if you made a mistake.

WARNING - do not edit the sudoers file without visudo (e.g., wit nano or vim etc) as this could cripple your system.

now create a new file called battlow_shutdown.sh

Code:

vim battlow_shutdown.sh

and put the following in it:
Code:

#! /bin/sh

#
# Shell to shutdown the computer in $argv$1 seconds if on battery power.
# 30 seconds before shutdown we check for ac again. If present shutdown aborts.
#

if [ $# -eq 0 ]
then
   exit
fi
instances=`ps -e | grep "battlow*" | wc | awk '{print $1}'`
if [ "${instances}" -gt 2 ]
then
   exit
fi

time_in=$argv$1
time=`echo ""|awk '{if('$time_in'>30){print '$time_in' - 30};if('$time_in'<=30){print 0}}'`
state=`cat /proc/acpi/battery/BAT0/state | grep charging | awk '{print $3}'`
if [ "$state" = "discharging" ]; then
   xmessage -button ok -center "Please attach AC adapter to prevent automatic shutdown in '$time_in' seconds!" &
   sleep $time
   state=`cat /proc/acpi/battery/BAT0/state | grep charging | awk '{print $3}'`
   if [ "$state" = "discharging" ]; then
      xmessage -button ok -center "Shutting down in 30 seconds!" &
      sleep 30
      sudo shutdown -h now
   fi
fi

make the file executable:

Code:

chmod +x battlow_shutdown.sh

now put it in /usr/bin:

Code:

cp battlow_shutdown.sh /usr/bin

now right click on the battery section of gkrellm and go to the battery->setup tab click on the 'Alerts' button. Add the following to the alarm command:

Code:

battlow_shutdown.sh 300

in the same area of gkrellm 'low warn' is set to 15, 'low alarm' to 10.

That should be all.
"

I have an Eee pc 701, and I installed Ubuntu-eee Hardy on it, and got the custom kernel for Celeron. That enables cpu frequency scaling, and improved boot time and battery time significantly. I get about 3 hours from the battery...

[http://www.ubuntu-eee.com/wiki/index.php5?title=Main_Page](http://www.ubuntu-eee.com/wiki/index.php5?title=Main_Page)

Custom kernel thread:
[http://forum.eeeuser.com/viewtopic.php?id=32303](http://forum.eeeuser.com/viewtopic.php?id=32303)

"I've just finished producing the first version of a set EeePC-optimized kernel and modules for Ubuntu 8.04 (hardy) as .deb packages.

These packages contain the following features:

    * Kernel optimized for Pentium-M processors.
    * Extra and unnecessary kernel modules and features have been stripped out.
    * The 40-wire UDMA patch has been applied to ata_piix.ko (much faster I/O throughput.) (See [http://lkml.org/lkml/2008/4/20/283](http://lkml.org/lkml/2008/4/20/283))
    * The Elantech touchpad driver port has been applied to psmouse.ko. (See [http://forum.eeeuser.com/viewtopic.php?id=30685](http://forum.eeeuser.com/viewtopic.php?id=30685))
    * The eeepc-acpi module is included
    * The madwifi modules are included (madwifi-hal-0.10.5.6 branch)
    * The eeepc-linux overclocking module is included (v0.2)
    * The uvcvideo module is included (svn r215)

These packages have been customized from the linux-image-2.6.24-19-generic and linux-ubuntu-modules-2.6.24-2.6.24 source packages to become
linux-image-2.6.24.19-eeepc and linux-ubuntu-modules-2.6.24-19-eeepc

    Update 2008-06-11:
    The linux-image-eeepc packages are now available with a debian repository!
    To get the kernel packages (and updates) all you need to do is: sudo apt-get install linux-eeepc linux-headers-eeepc

    Update 2008-06-20:
    The website's been redesigned to have more information, packages, faqs, etc

    Update 2008-08-12:
    A public read-only git repository is now available for accessing the source code, including all original patches and customized code:
    git://www.array.org/ubuntu-hardy.git
    git://www.array.org/ubuntu-hardy-lum.git
    git://www.array.org/ubuntu-hardy-meta.git

Repository setup and download instructions can be found online at:
[http://www.array.org/ubuntu/](http://www.array.org/ubuntu/)

    Disclaimer:

    I am not a kernel developer, nor am I an ubuntu or .deb developer. This might possibly break your EeePC. 
    I only produced these packages as a proof of concept. I've never actually done this before yikes
    I offer no guarantee that these packages will a) solve a problem, b) cause multiple problems, or c) do absolutely nothing useful at all.

Good luck! tongue"

Im using his kernel, and it improved both boot time and responsiveness on the 701, and now I can manually downclock the cpu too when Im on battery.

---

