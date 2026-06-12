---
title: "virtualbox ose install thru synaptic (on hardy) destroyed my ubuntu install?"
date: 2008-07-27
forum: Virtualisation
---

### Post by spydirweb on 2008-07-27
I'm not sure, at all, what exactly just happened to my computer...  I'm going to give some exposition first, though.

I decided I was going to make a VM install of XP pro.  I was going to try parallels workstation, but the trial version wasn't running right at all for me.  A quick search on the problem I had said I'd have to downgrade my kernel, so I just googled up another VM solution.  I figured either VMWare or virtualbox and was leaning to VB because it's free.  I work at a tigerdirect retail store, so I set up synaptic to install all the virtualbox packages I'd figure I'd need. namely virtualbox-ose, virtualbox-ose-guest-modules-* (the generic names one that then loaded the ones for my kernel), virtualbox-ose-guest-utils, and virtualbox-ose-modules-* (same as guest mod's).  I then ran down to my store, picked up an OEM install disc since it'll probably only ever be on this system, and got back to a finished install.  Synaptic wanted to reboot, so I did.

Once the reboot was done it seems like SOMETHING in the install process destroyed X11, or at least my module loads.  nvidia kernel module is no where to be found even though it claims it's installed, and I'm forced to use vesa right now at 800x600, on a 22 inch wide screen so I feel like my eyes are going to die.  If I modprobe nvidia I get "FATAL: Error running install command for nvidia" and changing xorg.conf to nv does nothing, either.  I tried doing a reinstall of the nvidia drivers, linux-headers, and linux-restricted-modules to no avail.

I'm trying to avoid having to reinstall ubuntu (also because it appears as if my 8.04 disc is screwed because it's failing going from step 3 to 4 of the install... even though the "check integrity" thing says its fine, but that's a completely different problem), and I'd like to at least get this all set back up properly.  I have NO idea what happened, and I have NO idea how to fix it.  I'm pretty *long list of curse words* off right now at this whole situation, because this SHOULD NOT have happened.  I've tried searching virtualbox's forums, ubuntu forums, and general google stuff.  I'm not sure I'm just not using the right search words or what but all i can find is people talking about their problems after getting it all installed, not the actual act of it screwing up your entire system.

I'm currently going to see if I can't get at least a reinstall up, but once it's done I still want to try to get a VM up.  I'm guessing I'm going to do vmware-server this time, but I'd like to understand what the hell happened to my system so I don't repeat the same mistake.  Any ideas or "well there's your problem!" advice is GREATLY appreciated.

---

### Post by sengines on 2008-07-27
> **spydirweb said:**
> Once the reboot was done it seems like SOMETHING in the install process destroyed X11

you can try at terminal

sudo nvidia-settings and overwrite settings and then at terminal again

sudo nvidia-xconfig --no-logo and reboot so you wont get the nvidia
splash screen at boot


If that didnt work, post back

For virtualbox go to the site virtualbox.org and download deb package
when installing make sure you have details opened because it will ask
if you want to install headers, yes and hit enter and follow directions.

give permission to vbox user
system->admin->users and groups

then click on manage groups

scroll down all the way to the bottom where you'll see vboxusers

click PROPERTIES and click the box next to your username (or all of them if you want)

then restart your computer and try again and it should work! 
[http://ubuntuforums.org/showthread.php?t=456724](http://ubuntuforums.org/showthread.php?t=456724)

---

### Post by spydirweb on 2008-07-27
> **sengines said:**
> you can try at terminal

sudo nvidia-settings and overwrite settings and then at terminal again

sudo nvidia-xconfig --no-logo and reboot so you wont get the nvidia
splash screen at boot


If that didnt work, post back



did you read?

> If I modprobe nvidia I get "FATAL: Error running install command for nvidia" and changing xorg.conf to nv does nothing, either. 

if the nvidia kernel module cannot be loaded, 1. nvidia-settings won't work, because it doesn't see... itself. 2. nvidia-xconfig won't make a difference because the module...can't be loaded. it'll just keep defaulting back to vesa.  I tried both of these suggestions prior, and it was to no avail.  Thanks for the attempt but it didn't do much.

I'm actually trying to uninstall the nvidia drivers now so I can try reinstalling, see if it does anything.  I did also go back and try reinstalling again... seems like partman is failing on me.  Something's up with my harddrives it appears.  In other words, trying to install this VM was a bad choice on my part.  Whenever I have a neat idea for something to do on a day off I always end up screwing things up way, way worse then they were.

---

### Post by sengines on 2008-07-27
It's a lot to cover, I had the same problem, but I couldn't see anything just monitor cannot display this res or something like that and vbox is actually the best one i've tried.

Suggestions:
I would start with a ubuntu minimal install with xorg, synaptic, build-essential, linux-headers, compiled nvidia drivers, gdm but if you can't, try the following.

Solution:
So nvidia module not installed, linux headers not installed?

First go to nvidia site and write down location of pkg2.run package
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
 
ctrl + alt + f3 for terminal ctrl + alt + f7 to go back

sudo killall gdm or whatever display manager is running if any

uname -r to check what linux headers version you have
(eg) linux-headers-2.6.2.19

at terminal, sudo apt-get install linux-headers-2.6.2 etc


wget [http://nvidiasite.pkg2-run](http://nvidiasite.pkg2-run) package

sudo sh packacge.sh

do you want to compile headers (no)

install 32 bit libraries? yes just in case you want to install other stuff later.

do you want to configure nvidia-xconfig? no

at terminal sudo nvidia-xconfig --no-logo 

sudo reboot

good luck, it's easier if I could do it myself but its easy on the third attempt, keep trying :)

---

### Post by sawjew on 2008-07-27
I presume you are using Ubuntu as the host OS and you are intending to run Windows as a guest OS in Virtualbox?

If that is correct then you do not need the virtualbox-ose-guest-utils or virtualbox-ose-guest-modules-* installed.  You only need to install the guest packages if you are running the Ubuntu as the guest OS inside Virtualbox.

I think that you are having a conflict between the guest modules graphics driver and your nvidia drivers.  You need to remove the guset modules and guest utils and then you may need to reset your drivers to use the nvidia drivers by running ```
sudo dpkg-reconfigure xserver-xorg
``` 

I don't know much about nvidia drivers but once you have removed the VB guest modules you should be able to get your drivers working properly.

---

### Post by spydirweb on 2008-07-27
ok, using envy, i was able to at least get X11 back to normal.  Although now I'm also discovering that my sound drivers are no longer here, and I can assume a lot, lot more.  depmod -a turns up nothing new, either.  It's obvious that somehow my virtualbox install seriously messed up the linux-headers package, and even though I've reinstalled it it appears as if something along the way of this attempt at a VM install, or the fixing process, has lost a lot more then I was hoping for.  I'm still at a lose for how virtualbox's module setup could of wreaked so much havoc on the rest of my system.

Does anyone know of a way to go back and "track" what package install/uninstalls have happened on a system?  I'm wondering if I can't find the EXACT packages that I installed, and see what they did to at least alleviate some of this process.

---

### Post by spydirweb on 2008-07-27
> **sawjew said:**
> 
I don't know much about nvidia drivers but once you have removed the VB guest modules you should be able to get your drivers working properly.

yeah, you presumed right, ubuntu as host and windows as guest.

I already tried your idea though, and well before going thru any more steps I removed all the virtualbox packages I did have installed in hopes that it might do something.  Now I just gotta try and figure out what else I have to install now...

---

### Post by meg23 on 2008-11-04
I had the same problem after installing virtualbox on hardy. It screwed up my graphics card and my wireless card. I had to reinstall to get any sort of function back to my computer. I have a feeling it has something to do with kernel modules that have to be installed.

---

### Post by theDaveTheRave on 2008-11-05
I seem to be having a similar problem.

I was going to test out virtualbox prior to creating a dual boot on my works desktop.

Plan was to have ubuntu and then virtualbox the XP that is on the other partition.

However, I installed the virtualbox (same stuff as spydirweb installed).

I did the <system restart> as suggested.

result.

No usb config - external mouse and keyboard don't function (but do appear in an <lsusb>.

Ethernet is broken, I only get the loopback when I do an <ifconfig> nothing else!

my /etc/network/interfaces file is still the same as it was.

so I decided to de-install all the <virtualbox> stuff I had previously installed, but still no luck.

I have 4 hours to sort this, or I'll go mad.

I don't particularly want to have to do a re-install, but if I have to I will.

I did get an error message (can't remember what I was doing though) that stated the following.

> 
can't access acpi events in
/var/run
ensure acpid.socket is running
acpid subsystem is working
acpid daemon is working


I've done a hunt on this and there seems to be no other people with this issue. I did read problems around getting USB support to work for virtualbox, but I got the impression that was a problem with USB support within the virtual machine?

I don't know what to do next

Maybee a good moment to do a clean install to Intrepid! :guitar:

I'd like to find out what went wrong first though, as I would like to have virtualisation on my desktop, eventually!

thanks in advance for you advice /  help.

the first thing I need to get back is networking, then I will be able to cut and paste any commands, and get screen shots!

Dave

---

### Post by theDaveTheRave on 2008-11-05
Dear all

so I got home and booted into a "rescue" system on my laptop.

did an upgrade to Ibex.

and everything is seemingly back to how it should be!

I am very relieved.

but now I have a bunch of questions regarding qemu setup (this seems to come as standard with Intrepid), so I'm off to hunt the forums

:guitar:

Dave

---

