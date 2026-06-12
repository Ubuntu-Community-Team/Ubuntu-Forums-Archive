---
title: "server will only boot with keyboard and monitor connected"
date: 2008-04-29
forum: Server Platforms
---

### Post by Jeztastic on 2008-04-29
Hi,

I am running a PIII Compaq deskpro EN server.

I am attempting to make it headless, however, the damn thing will not boot properly without the monitor hooked up. Obviously, this is a real pain in the ****. Especially as if I am working in the cli and then want to run x, x will not start unless I run upstairs and switch the monitor on!

Is this something which is likely fixable in the bios? I don't want to start poking around in there unless I know there's a point to it, as I am prone to breaking things.

Any other suggestions?

Thanks,

Jez

---

### Post by kerry_s on 2008-04-29
ubuntu as a server is not the best choice. try debian or another distro, preferably 1 known to be reliable.
[http://distrowatch.com/search.php?category=Server&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Server&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

---

### Post by Brazen on 2008-04-29
I would almost guarantee the problem is with the BIOS.  You may need to update the BIOS.  I've had plenty of Ubuntu 6.06 servers work just fine without keyboard, monitor, or mouse.

---

### Post by Jeztastic on 2008-04-29
Thanks Brazen, will give the bios a try soon. I hope I don't have to update - that will be a real pain!

I also suspect it's not an OS issue, as the problem occurs at boot.

kerry_s, is this a known Ubuntu bug? What will Debian do differently.

---

### Post by teaker1s on 2008-04-29
look for bios section that states halt on boot, you need to set so it ignores missing keyboard

---

### Post by Dr_Snapid on 2008-04-29
Some bios have a submenu called 'errors' or 'halt on' with 'keyboard, none' etc as options. If your bios is like this, choose none.

Others have 'halt on keyboard' etc as actual menu items, you need to disable all the 'halt on' options, so the system boots regardless of errors.

I have never yet seen a bios without these options in one form or another, have a look, they will be there.

I dont know why someone suggested ubuntu isnt reliable, but since they didnt elaborate I have no reason to believe that. Ubuntu is as stable as any other distribution if you ask me, it's usually the programs, not the OS that cause problems when it comes to linux.

---

### Post by Jeztastic on 2008-04-29
Thanks you all very much, will check this out.

---

### Post by Jeztastic on 2008-04-29
> **kerry_s said:**
> ubuntu as a server is not the best choice. try debian or another distro, preferably 1 known to be reliable.
[http://distrowatch.com/search.php?category=Server&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Server&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

Having re-read this post, I don't think the poster was suggesting Ubuntu is unreliable - just that it's not the best server choice. I have heard that before, however I am a Linux n00b and I am familiar with Ubuntu, so...

I am curious as to why you don't think it's a good choice Kerry...

Jez

---

### Post by Brazen on 2008-04-29
> **Jeztastic said:**
> Having re-read this post, I don't think the poster was suggesting Ubuntu is unreliable - just that it's not the best server choice. I have heard that before, however I am a Linux n00b and I am familiar with Ubuntu, so...

I am curious as to why you don't think it's a good choice Kerry...

Jez

He's just spreading FUD.  There are advantages and disadvantages to all distros.  The LTS releases of Ubuntu make fine servers ( at least Ubuntu 6.06 Server LTS does, I've yet to find out if 8.04 is, since it's only been out a week).

---

### Post by lazyart on 2008-04-30
This is a limitation of the hardware.  I've run some of these in the past and they are business class desktops.  There is no option to boot without the keyboard (you don't need a monitor though).  A friend of mine once cut off a keyboard connector and soldered something together to fool the box into thinking a keyboard was connected when just the stub was plugged in.

---

### Post by Brazen on 2008-04-30
> **lazyart said:**
> A friend of mine once cut off a keyboard connector and soldered something together to fool the box into thinking a keyboard was connected when just the stub was plugged in.

Now THAT is freaking *awesome!*

---

### Post by Jeztastic on 2008-04-30
> **lazyart said:**
> This is a limitation of the hardware.  I've run some of these in the past and they are business class desktops.  There is no option to boot without the keyboard (you don't need a monitor though).  A friend of mine once cut off a keyboard connector and soldered something together to fool the box into thinking a keyboard was connected when just the stub was plugged in.

That's a real pain. I can't find an option to disable the keyboard.

As for the monitor - it really won't boot properly without looking for the monitor. I also can't start X from the cli without the monitor on - it hangs looking for it, so dunno if that's an Ubuntu problem.

---

### Post by kerry_s on 2008-04-30
> **Jeztastic said:**
> That's a real pain. I can't find an option to disable the keyboard.

As for the monitor - it really won't boot properly without looking for the monitor. I also can't start X from the cli without the monitor on - it hangs looking for it, so dunno if that's an Ubuntu problem.

try debian-> [http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-netinst.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-netinst.iso)

ubuntu's still young as far as distro's go, debian has been around alot longer, they have been there and done that already. 

just check the server stuff you want when it comes to the package selection part, if you leave the desktop checked it will install gnome. i usually go lighter, so i install X on my own with a light wm. (example X install: apt-get install xorg jwm )

if you want the fancy installer use "installgui" or "expertgui" use the "f*" keys to see your options, expert mode gives more control of the install but can be tricky. it's up to you.

---

### Post by Jeztastic on 2008-05-01
> **kerry_s said:**
> try debian-> [http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-netinst.iso](http://cdimage.debian.org/debian-cd/4.0_r3/i386/iso-cd/debian-40r3-i386-netinst.iso)

ubuntu's still young as far as distro's go, debian has been around alot longer, they have been there and done that already. 

just check the server stuff you want when it comes to the package selection part, if you leave the desktop checked it will install gnome. i usually go lighter, so i install X on my own with a light wm. (example X install: apt-get install xorg jwm )

if you want the fancy installer use "installgui" or "expertgui" use the "f*" keys to see your options, expert mode gives more control of the install but can be tricky. it's up to you.

Thanks, I will definitely consider that when I next do this. I have another Deskpro kicking about, just need someone who wants a server to try it on!

I am actually learning a lot this way, as it's stopped me being lazy and VNCing into the gui all the time. I am currently using X forwarding to get round switching on X on the server. This solution is a lot more convenient and elegant, I am now ready to put the monitor back in the loft where it belongs!

---

