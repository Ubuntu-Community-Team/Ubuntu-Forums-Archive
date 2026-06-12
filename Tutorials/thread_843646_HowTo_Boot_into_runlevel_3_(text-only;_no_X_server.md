---
title: "HowTo: Boot into runlevel 3 (text-only; no X server)"
date: 2008-06-28
forum: Tutorials
---

### Post by rbalsdon on 2008-06-28
[B]Starting a Desktop Install without GDM
Ubuntu 8.04 Hardy[/B]

----

Hi Everyone,

This took me quite a while to get working (I couldn't find anything on the web) so I thought I'd post here. Stopping and starting the X-server is easiest done with the service commands (sudo /etc/init.d/gdm stop) and (sudo /etc/init.d/gdm start) but I would rather be able to choose from grub (when the computer is booting) whether or not to start the graphics.

**Intro**

"Why would you ever want to do this?" is a very good question which I'll not go into in detail here. I use it on a laptop that I'd like to have start and stop very quickly and with minimal resource use but still have to option of getting into gnome if I want.

Booting into a different runlevel is usually done by adding the number at the end of the kernal command in grub (more on these terms in a few) but this doesn't seem to work in Ubuntu; it will always get into runlevel 2.

**Runlevels**

A runlevel is used to tell the OS how far up you want it to boot. Generally, we use runlevel 1 for debugging/recovery mode, runlevel 3 for normal text (no graphics mode) and runlevel 5 for normal with graphics. Runlevels 0 and 6 are when the computer is shutting down/restarting. Runlevels 2 and 4 are user-defined and used for doing crazy stuff without modifying the standard 1,3 and 5 runlevels.

Ubuntu uses runlevel 1 for text mode, as expected, but uses runlevel 2 for full graphical mode. This leaves no room in between for the text mode but the runlevels 3 to 5 are still available to us. Relating to the above paragraph: in Ubuntu, runlevels 2 to 5 are all used as runlevel 5.

In a more hands-on explanation, we can say that the different runlevels refer to different folders filled with scripts that are called at boot and start up all the different programs that need to be started. Runlevel 1 will have only a few scripts but runlevel 2 will have all of them.

We have to then modify runlevel 3 to be text-only and update the boot script somehow to point it to runlevel 3 instead of runlevel 2.

**Step 1: Changing Runlevel 3 to Text-Only**

Load up a terminal/console if one isn't already by clicking on  Applications->Accessories->Terminal.

The folders that refer to the different runlevels are called /etc/rcX.d where X is the runlevel so enter and list the runlevel 3 folder by typing in

```
cd /etc/rc3.d
ls
```

Look for the script that says gdm, it should be S30gdm. If you're running KDE, this might be S30kdm (untested). Remove this script by calling

```
sudo rm S30gdm
```

**Step 2: Making Runlevel 3 Accessible from GRUB **

I had to modify the rc-default script to do this. This is extremely dangerous and could make your computer "unbootable". An error can be recovered from using the Live CD so it wouldn't be the end of the world but just be careful to copy exactly and you'll be fine.

Open up the rc-default script by typing in

```
sudo gedit /etc/event.d/rc-default
```

The script should look like this:

```
# rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

start on stopped rcS

script
	runlevel --reboot || true

	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
	elif [ -r /etc/inittab ]; then
	    RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
	    if [ -n "$RL" ]; then
		telinit $RL
	    else
		telinit 2
	    fi
	else
	    telinit 2
	fi
end script
```

**If your script doesn't look like above, stop here** because I can't guarantee my modifications to work.  We're going to add a new elif statement to look for the word text and boot into runlevel 3. Change your script (copy/paste) to look like the following

```
# rc - runlevel compatibility
#
# This task guesses what the "default runlevel" should be and starts the
# appropriate script.

start on stopped rcS

script
	runlevel --reboot || true

	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
	elif grep -q -w -- "-s\|text\|S" /proc/cmdline; then
	    telinit 3
	elif [ -r /etc/inittab ]; then
	    RL="$(sed -n -e "/^id:[0-9]*:initdefault:/{s/^id://;s/:.*//;p}" /etc/inittab || true)"
	    if [ -n "$RL" ]; then
		telinit $RL
	    else
		telinit 2
	    fi
	else
	    telinit 2
	fi
end script
```

**Double-check** that everything's exactly identical and move on.

**Step 3a: Booting into Text-Mode Once**

Reboot your computer and enter the GRUB menu. This should be done automatically but in some installs, you have to push the ESC key while a timer's counting down.

The GRUB screen will give you a few different options, none of which should have changed. To give you an idea of the screen we're looking for, mine lists the following:

[I]Ubuntu 8.04, kernel 2.6.24-19-generic
Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
Ubuntu 8.04, memtest86+[/I]

Highlight the default (should be the very top) option and press the 'e' key for edit (once). Again to make sure we're on the same page, mine lists the following:

[I]root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=21c38426-84f0-4946-bee7-318074de0787 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet[/I]

Highlight the kernel (second) option and push the 'e' key again. Type in "text" at the end (after splash) so that it looks like this:

*kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=21c38426-84f0-4946-bee7-318074de0787 ro quiet splash text*

Note that your UUID and kernel version may be different and you should not change it. Just add the word "text" to the end of whatever's there. Press the 'b' key to boot into text mode.

**Step 3b: Booting into Text-Mode Always**

Load up a terminal/console if one isn't already by clicking on  Applications->Accessories->Terminal.

Load up the GRUB config by typing in:

```
sudo gedit /boot/grub/menu.lst
```

Near the bottom of this file, you'll see a list of all the different boot options of the GRUB menu. To give a good idea of what you're looking for, one of mine looks like this:

[I]title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=21c38426-84f0-4946-bee7-318074de0787 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet[/I]

You might have quite a few of these if you've been following different kernel updates; edit the very top one of these. Add the word "text" to the end of the kernel line, exactly as described in Step 3a so that the above example would look like this:


[I]title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=21c38426-84f0-4946-bee7-318074de0787 ro quiet splash text
initrd		/boot/initrd.img-2.6.24-19-generic
quiet[/I]

**Step 4: Running the Graphical Interface While in Text-Only Mode**

If you're running in text and want to see the graphics stuff again, there are two different ways to go.

To see the nice login screen like Ubuntu normally boots into , type in:

```
sudo /etc/init.d/gdm start
```

You may have to swap gdm with kdm if you're using KDE (untested). If you just want to see Gnome/KDE (skipping the login part), type in

```
startx
```



RB

---

### Post by unutbu on 2008-07-02
```
grep -q -w -- "-s\|text\|S" /proc/cmdline
```
I'm trying to figure out what the "-s\|" and "\|S" mean. Can you explain?

---

### Post by tormod on 2008-08-08
> **unutbu said:**
> ```
grep -q -w -- "-s\|text\|S" /proc/cmdline
```
I'm trying to figure out what the "-s\|" and "\|S" mean. Can you explain?

That will accept "-s" or "text" or "S".

---

### Post by unutbu on 2008-08-08
Yes, thanks. It seems to me the script above should not try to test for "-s" and "S" twice. Perhaps the script should use this instead:

```
	if grep -q -w -- "-s\|single\|S" /proc/cmdline; then
	    telinit S
	elif grep -q -w -- "text" /proc/cmdline; then
	    telinit 3
```

---

### Post by tormod on 2008-08-08
Yes, absolutely. I think it must have been a copy-and-paste without understanding the details of the grep pattern.

---

### Post by pegaso_l on 2009-02-09
Hi,

I think it is not required to remove gdm from /etc/rc3.d

I followed the initial protocol without removing gdm from rc3.d and it worked fine. 

Additionally, I checked if gdm mode was listed running the lsmod command and I did not find it there, so I suppose gdm is not running.

BTW, thanks for the script change, very helpful for rookies like me.

---

### Post by tormod on 2009-02-09
This whole thread is now obsolete: There is a boot option "text" that will inhibit gdm from starting. So just add "text" to the kernel line in grub, and the machine will boot up completely except starting gdm.

---

### Post by unutbu on 2009-02-09
Thank you tormod! I did not know about the "text" boot option.
I looked in /etc/event.d/rc-default and did not find "text" being handled there. Do you know how it works or where I can find documentation on it?

Also, for those interested in controlling runlevels at boot time
there is also this guide:
[http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml](http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml)
which describes a slightly more versatile method of selecting any runlevel.

---

### Post by tormod on 2009-02-09
> **unutbu said:**
> Thank you tormod! I did not know about the "text" boot option.
I looked in /etc/event.d/rc-default and did not find "text" being handled there. Do you know how it works or where I can find documentation on it?


It is dealt with inside /etc/init.d/gdm, with the disadvantage that if you have booted with "text" you can not run "sudo /etc/init.d/gdm start" to start X... But "startx" will work for the logged-in user.

---

### Post by momneedshelp on 2009-08-23
I'm sorry about raising this thread from the dead, but if I just add "text" behind the kernel, doesn't that mean I have to manually edit GRUB every time a new kernel arrives? And given that I have updates set on automatic installation, I will not even know immediately if a new kernel (booting into X and gdm) has arrived.

I use this PC as a server and guest PC, so it must boot into init 3 as text mode but allow me to start gdm. Besides, I often prefer doing things visually even in the server when piping stuff through ssh is too complicated with all the permission failures. I use the latest 32bit Ubuntu as of the date of this message.

When I used to use Sidux it was as simple as setting the default runlevel in smxi, it's changing one number after smxi has loaded. 60 seconds, done. Unfortunately I do not know what happens behind the scenes and what smxi does, which, even more unfortunately isn't available for Ubuntu.

Isn't there a more standardized way of setting the default runlevel for Ubuntu _permanently_ without being so scary as this inital howto.

There's an option "no graphical login manager" in /Administration/Services/, but it comes with a stark warning when trying to uncheck it. Will I be able to start gdm from the boot terminal after unchecking it? Not being able to return to gdm means for me reinstalling and losing all my settings.

Cheers, Mom

---

### Post by unutbu on 2009-08-23
momneedshelp, welcome to the forums.

Let's see. You have installed Jaunty server edition. 
You have gdm and X installed, so I assume you have augmented the server with these X applications, and have probably also run
```

sudo apt-get ubuntu-desktop
```

This way, when you log in as a normal user, you get a GNOME desktop, yes?

If the above assumptions are true, then you have essentially installed the Jaunty desktop edition. (The desktop edition can run server applications just like the server edition).
If you turn off or remove the monitor, you could call it a server :)

When you wish to log in graphically, for your own purposes, or have a guest who wishes to log in, you could just turn on the monitor and have the gdm login window already there. 

Does this sound acceptable? If so, you do not have to mess with runlevels at all.

If this is not what you want, please describe what your ideal solution looks like.

---

### Post by tormod on 2009-08-23
> **momneedshelp said:**
> I'm sorry about raising this thread from the dead, but if I just add "text" behind the kernel, doesn't that mean I have to manually edit GRUB every time a new kernel arrives? And given that I have updates set on automatic installation, I will not even know immediately if a new kernel (booting into X and gdm) has arrived.
You should edit the #kopt= line in /boot/grub/menu.lst, and then run update-grub. update-grub will add the #kopt parameters to the "kernel" lines, so this happen when you upgrade kernels as well.

> I use this PC as a server and guest PC, so it must boot into init 3 as text mode but allow me to start gdm.
To be able to start gdm even if you have booted with "text", I suggest this modification of /etc/init.d/gdm (which I also will try to push into Karmic):
        ```
if grep -wqs text /proc/cmdline[COLOR="Red"] && [ "$2" != "force" ][/COLOR]; then
```
You can then start gdm, even if "text" was used, with:
**sudo /etc/init.d/gdm start force**

---

### Post by lswb on 2009-08-23
You might take a look here for some more ideas:

[http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml](http://lwasserm.freeshell.org/ubuntu/runlevel3.shtml)
[http://lwasserm.freeshell.org/ubuntu/editrl.shtml](http://lwasserm.freeshell.org/ubuntu/editrl.shtml)

---

### Post by momneedshelp on 2009-08-23
Unutbu, tormod and lswb, thank you for replying.  Sorry, forgot to specify that I'm using a manually stripped down Desktop Ubuntu which I'm using as a server as well (opensim), I assumed that would be clear as I had made a reference to an up and running GDM.

As I was trying different approaches from the hints here in the last hours and some more searches on the web,  I was getting deeper into the mess:-) with not being able to boot up at all ?! and ended up just backing up with the LiveCD and  reinstalling from scratch.

In the end, that panel option at /System/Administration/Services/uncheck Graphical login manager did the job! I just unchecked after reinstall given I had nothing to lose (anymore) and it booted into the CLI without modifying anything in the GRUB. And when I want a Desktop, "sudo start gdm" then just launches Gnome, I have set it on automatic login, so I'm very happy. We have a score!

---

### Post by n4clh on 2010-01-14
With the new and fancy 9.10 distro, you can also setup in Grub2

Edit the /etc/default/grub (sudo) file and locate the line
GRUB_CMDLINE_LINUX="" location  and add the word 'text' inside the quotes per suggestion above.
be sure to run  sudo update-grub  before rebooting.

you can then use your system in level3 .  If you wish to run graphics you can simply run 'startx' - I installed xfce4 desktop and run 'startxfce4'  

Best...

---

### Post by frenchn00b on 2010-01-15
**Run-level 2, how to boot in text mode or using .xinitrc :**

The nuts-n-bolts method

Using your favourite text editor create a file named autologinfred.c and type in this short C program:


[B]#include <unistd.h>
int main() {
execlp( "login", "login", "-f", "fred", 0);
}[/B]

The execlp system call invokes the command "login -f fred" and replaces the current processing context with this invocation. The man page for login describes the action of the -f argument. Compile this tiny C program using the GNU C-compiler:

$ gcc -o autologinfred autologinfred.c

Gain root privileges (using su) and copy the executable to a public directory:

# cp autologinfred /usr/local/sbin/

Now take a look at /etc/inittab. This is the configuration file is used by init, the very first process started when Linux initialises. You should observe lines similar to the following:

1:2345:respawn:/sbin/mingetty tty1
2:2345:respawn:/sbin/mingetty tty2
3:2345:respawn:/sbin/mingetty tty3

The exact contents of /etc/inittab differ from distribution to distribution. On Debian systems one sees:

1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3

Edit the line beginning with "1:2345" so that it reads as follows:

1:2345:respawn:/sbin/getty -n -l /usr/local/sbin/autologinfred 38400 tty1

The above will cause the user fred to be logged in automatically on the first virtual console. On some GNU/Linux distributions (like RedHat) /sbin/agetty must be used instead. The -l <alternative login> argument to getty substitutes the default /sbin/login program with the one we compiled earlier. The -n tells getty to not prompt for a user ID.
Initiating the desktop on login

If we reboot, the init process will automatically login the user fred on the first virtual console and a command shell will by started. User fred must still type in the startx command to initiate the graphical desktop. Can we automate this too?

If fred's login shell is /bin/bash, the first commands to be executed will always be listed in the file, ~fred/.bash_profile. We can add the startx command here but this causes problems, since the .bash_profile will be used in other situations such as when one is logging into a second virtual console or when opening an xterm. Instead we append the following lines:

[B]
if [ -z "$DISPLAY" ] && [ $(tty) == /dev/tty1 ]; then
  startx
fi
[/B]

---

### Post by lswb on 2010-01-15
> **frenchn00b said:**
> Run-level 2, how to boot in text mode or using .xinitrc :[/B]

The nuts-n-bolts method
....


Apparently you have never tried this on any recent ubuntu distributions.

---

### Post by dtcostelloe on 2010-01-20
Greetings all,

I apologize if this question doesn't really belong here ... but it's directly about runlevel stuff.

My question:  From a command prompt in Ubuntu Server v9.10, how do you find out what runlevel you are running at?

I've installed XAMPP for my class at school, and I want it to automatically start.  I've found a thread (albeit quite outdated) that lists using the following command:

egrep :initdefault: /etc/event.d/rc-default

This gives me an error, "file not found" "directory not found"

As it turns out, "/etc/event.d" as a directory, doesn't exist at all.

So, anyone know how to find out what my default run level is?  I need to know so I can put the start and stop commands to auto-load XAMPP at startup.

Thanks a bunch for all your replies / help.

---

### Post by lswb on 2010-01-20
I run 9.04, not 9.10, but I think that the runlevel command must have been included with 9.10 for compatibility with programs that use sysv style initscripts.

Try "runlevel" in a terminal and see what it returns, then "man runlevel" for the details. The normal output is 2 characters separated by a space, the first is the previous runlevel ('N' is returned if there has been no change since boot) and the 2nd is the current runlevel.

---

### Post by dtcostelloe on 2010-01-20
Thanks, that did the trick:

N 2

Runlevel 2 - which means I need to start my LAMPP services from the "/etc/rc2.d" directory.

Worked flawlessly, thanks!

---

### Post by jharris1993 on 2010-02-22
I am experiencing a very similar problem:
 
I have a "server" running Ubuntu 9.10 Desktop that I use as my main file store - running four 1T drives as a RAID-10 array with Samba, Apache, SWAT, etc. running to help administer and use it.
 
It was running Fedora 10.  (Because - at the time - Ubuntu would not even *install* with my 4-port eSATA card in place.)  I went to update to Fedora 12 - and it was a mess...
 
I discovered that Ubuntu 9.10 would support my RAID setup natively - so I wiped the system clean and installed Ubuntu. (I generally prefer Ubuntu anyway.)
 
The way my system was originally set up was that it would give me a GRUB menu list for 5 seconds - and the menu list had two options: Fedora X.x.x.x (graphical), and Fedora X.x.x.x (console).
 
Most of the time, I would run my server in console mode so that there wasn't the memory and processor overhead caused by the GUI.
 
Why?  I'm running this beast on an ancient Dell Optiplex GX-110 desktop with a 700Mhz P3 and a max of 512 megs of RAM that I scavanged out of a dumpster somewhere - along with just about everything else I use.
 
Unfortunately I cannot yet afford the luxury of the fancy bleeding-edge AMD 256 bit processors with 18 cores running at XXXThz.  I gotta make do with what I can get, and that's why I like Linux.  You don't have to be running bleeding-edge hardware to get the sluggish performance of an IBM XT.  However, since I *am* running on cruft - I like to be nice to it and only run the heavyweight stuff when I absolutely need it.
 
This way, I could default into console mode 99% of the time, saving the overhead of the GUI for those times when I REALLY needed it.
 
=========================================
 
However. . . . . . . 
 
With 9.10 I have noticed some really annoying new "features"
1. It appears that there is no way to get a GRUB startup menu. Even if I **WANT** it.
2. Passing a kernel parameter (I was using " --3") absolutely does not work. I did not know about "text", and I have not yet tried it.
 
There seems to be some confusion here as to what works and does not work.
 
At the risk of sounding annoyed, Ubuntu spends a lot of time championing that they are "all about giving the user choices" OK, I wanna make a choice - start up with a GRUB boot menu or not. I wanna make another choice - Graphical startup or console startup. At this point it appears that I have about as much choice as a MAC user! Maybe even less. . . .
 
The reason I raise this is that the original reason I was attracted to Ubuntu was both it's ease of use, AND it's flexibility, without ramming some particular style or philosophy down my throat the way Fedora loves too.
 
Is there a way I can release these extremely restrictive defaults so that I can make my system behave the way *I* want it to, and not the way *SOMEONE ELSE* wants it to?
/rant :-)
 
Thanks in advance for any help you folks can provide.
 
p.s. **PLEASE** suggest to whoever spins these distro's that locking down the startup process like this is the fast boat to Linux Obscurity.
 
What say ye?
 
Jim

---

### Post by mjames.c2l on 2011-05-05
I'm a habitual redhat-fedora-centos user, just installed ubuntu 11 on a test machine and have just wasted an hour trying to get it to boot to run level 3 instead of gdm (or 2 with no gdm as it is on ubuntu - why change that i have to ask?? oh, and why was there no root password?!? had to sudo edit the shadow file!) 

I've tried half dozen of the "solutions" google threw up and it's still booting to graphic login which is frankly painful (pc is from noah's ark, it's a bit slow but will do for test server.)

one hour is about one hour longer than it should take, so resorted to flaunting my ignorance and asking here?

ubuntu 11.04 - how do i boot to run level 3 (or ubuntu's equivalent) ?

thanks in advance.

---

### Post by tormod on 2011-05-05
> **mjames.c2l said:**
> 
ubuntu 11.04 - how do i boot to run level 3 (or ubuntu's equivalent) ?

thanks in advance.
Ubuntu does not use "run levels" although some compatibility is provided for packages installing scripts in /etc/rc*.d.

If you want to prevent gdm (and X) from starting, add "text" to the boot options.

I noticed I also had to use "set gfxpayload=text " in grub.cfg to keep my text console happy on some hardware.

---

### Post by tormod on 2011-05-05
> **mjames.c2l said:**
> oh, and why was there no root password?!? had to sudo edit the shadow file!)
Oh, and you should strictly speaking use "sudo vipw -s" to edit that file. But it is simpler to use "sudo passwd root" to set a root password.

---

### Post by mjames.c2l on 2011-05-06
Thanks for the quick reply tormod, i've just tried that and still no joy, this is exactly what i tried

changed /etc/default/grub to:

GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""

ran update-grub

rebooted -> gui login

changed to 

GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX="text"

ran update-grub

rebooted -> gui login

this is the default menu section of grub.conf (after 1st update)

menuentry 'Ubuntu, with Linux 2.6.38-8-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod part_msdos
    insmod ext2
    set root='(/dev/sda,msdos1)'
    search --no-floppy --fs-uuid --set=root a6036b89-17ac-4d8c-952c-5647021ead6d
    linux    /boot/vmlinuz-2.6.38-8-generic root=UUID=a6036b89-17ac-4d8c-952c-5647021ead6d ro   text
    initrd    /boot/initrd.img-2.6.38-8-generic
}

where i can see the update-grub has changed the linux boot params to "text" but this is still booting to gui

anything in that lot look suspicious? or is there something else i need to do?

---

### Post by mjames.c2l on 2011-05-06
actually don't worry about it, i noticed the restart option wasn't actually restarting the pc so i shut it down and now it won't boot up at all, just hangs on a black screen.

i think ubuntu11 was just a bit too optimistic for an old dog of a pc.

---

### Post by tormod on 2011-05-06
> **mjames.c2l said:**
> now it won't boot up at all, just hangs on a black screen.
Maybe because you did not change the gfxpayload as I suggested?
> i think ubuntu11 was just a bit too optimistic for an old dog of a pc.
My 11.04 installation runs on a ~2003 laptop with AMD 1GHz CPU and 256 MB RAM (-16MB for shared graphics)...

---

### Post by Flywaver on 2011-10-26
I am reopening an old thread...I tried to reboot without the GUI and it failed!

Here are my GRUB lines:
```
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX="text"
set gfxpayload="text"
```

Yet, it still loads up gnome shell with all it's fancy GUI! :(

Edit: I even ran sysv-rc-conf and set lightdm to level 3 and same for x11-common, rebooted in recovery mode and I still have the GUI! :(

---

