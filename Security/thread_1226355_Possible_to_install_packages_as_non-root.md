---
title: "Possible to install packages as non-root?"
date: 2009-07-29
forum: Security
---

### Post by lastexyle on 2009-07-29
Hello,

My place of work (a library) wants to have some machines available for the public to use for various activities like web browsing, word processing, or pretty much anything legal. All of the user's data is to be cleared after they're done using the machine. Obviously, Linux sounds like a great solution, but it's proving much more difficult than I originally expected. The reason for this is that users are supposed to be able to essentially have full control over the machine to install whatever programs they feel like during their session. I've looked into a number of ways but so far they all have problems:

Union Filesystem: This would work great until someone got smart and figured out the remount option on the mount command.

Virtualization: Too much overhead, the computers we're using for this are getting up their and I don't think they can handle a full fledged virtual machine running.

OS-Level Virtualization: This initially seemed promising, but apparently there's no way to properly run X on the virtualized OS. Forwarding over SSH, even though it's still on the same machine, seems too clunky for stuff like streaming video. The software I tried also required the host AND the virtualized OS to have their own separate IP addresses on the main network, which could get kinda messy.

The above solutions all seem to have unsolvable and unacceptable flaws so I got to thinking: is it possible to set up synaptic to install software to a user-writable directory that then takes precedence over the standard system locations? This would solve the main problem, and probably be more secure as well.


Thanks.

---

### Post by juancarlospaco on 2009-07-29
See ZeroInstall.

Disable asking password for sudo.

install Lethe.

*Guest account on Ubuntu is freezed, but can not install anything.*
:)

---

### Post by lastexyle on 2009-07-30
Thanks, but Zero Install doesn't look user friendly enough for our clients. I'm trying for the Add/Remove programs app or something similar in ease of use. As far as I can tell Lethe is just using aufs so a clever user can still just use sudo mount -o remount,rw /ro

---

### Post by cdenley on 2009-07-30
I think the only solution would have to be a hardware one. Perhaps you can use a SSD with a read-only switch. Then you would have to physically lock the computer to prevent anyone from flipping the switch and rebooting.

---

### Post by The Cog on 2009-07-31
How about running the machine from a live CD? There are ways to make a bootable CD customised to your liking. Then a simple reboot is assured to bring the machine back to your default condition. You can remove the hard disk. And however clever they are, they can't make permanent changes to the device.

There must be a way to do a network boot of an image too, but I don't know about doing that.

---

