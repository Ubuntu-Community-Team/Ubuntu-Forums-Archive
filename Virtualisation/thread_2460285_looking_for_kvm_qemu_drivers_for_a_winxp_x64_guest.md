---
title: "looking for kvm qemu drivers for a winxp x64 guest"
date: 2021-04-06
forum: Virtualisation
---

### Post by busternoob on 2021-04-06
installed qemu and kvm.
starting out migrating my old winxp x64 box.
seems like the newr drivers dont support pre-win7.
i downloaded a a virtio cdrom image and got into my vm.
installed several *.inf files in xp folders.
fixed my inverted mouse but theres no "friendly agent" to help me set up.
i have xp asking for several drivers and would like to get a good video driver for my widescreen.

---

### Post by CharlesA on 2021-04-06
XP x64 didn't have very good driver support, so it's unlikely you'll find a driver that works.

You could have a read here, but it's probably only related to XP x86.
[https://pve.proxmox.com/wiki/Windows_XP_Guest_Notes](https://pve.proxmox.com/wiki/Windows_XP_Guest_Notes)

With all that said.. XP has been end of life for years and if you really need to use it, you should restrict it from network/internet access.

---

### Post by rsteinmetz70112 on 2021-04-06
FYI a lot of Win 7 drivers will in fact work with XP, but you have to test them yourself, of course Win 7 is also EOL and those drivers are disappearing.
This is not an endorsement of using XP or win 7.
BTW you can still migrate a legit win 7 install to Win 10 and run most everything from win XP. 
In many cases you can use a Windows 7 or 8 key to activate Windows 10
Not really sure what anyone still needs XP.

---

### Post by busternoob on 2021-04-09
sorry actually the guest agent is loaded in task manager.
its a couple other drivers i still need i guess.
i dont really know what i'm doing just learn as i go.
i guess the guest agant allows alot of external terminal commands affecting the guest using the "virsh" or something.
oddly i keep getting performance increases by stumbling around.
twice i adandoned the machine to build a new one around the cow file and both times i got faster better runninng vm.
todays boost was created when i needed to swap out the 2nd drive i parked the vhds on and it buggered all the paths.

i do still need to know what to do about video. running 1024x768 on standard VGA, would prefer 1360x768.
i have two cheepo radeon gpu, one is onboard the other is a pcie X600.
i assume i can create a 2nd physical machine using the vm with the 2nd gpu and serve mouse and kb somehow?

---

### Post by busternoob on 2021-04-10
and good news i found something call RedHat QXL driver that loaded up in xp64.
i was able to select 1360x768 adn shes running real good now. 
nearly realistic performance as when xp was running on hardware.
i dont remember the package it came in but will post here when i relocate that.
and yes the whole reason for the vm migration is to take xp offline, this 
way i can come back regularly to look for things or info i need to export from it.


the driver from device manager property sheet:
Redhat QXL GPU
9/22/2015
version 6.1.0.10024

---

### Post by CharlesA on 2021-04-10
Glad you got your issue resolved. Please be sure to mark the thread as Solved from the Thread Tools menu.

---

### Post by busternoob on 2021-04-18
well sorry its not actually resolved.
the RdHat QXL driver and the the guest agent are all that loaded.
still looking for drivers that work for xp64 : cdrom audio pci

---

### Post by annajane on 2021-04-23
did you find drivers from linux-kvm. org

---

### Post by busternoob on 2021-04-24
sorry for the delay, yes i tried several of the virtio versions from there.
that site links to fedora site then to github.
none of them has an x64 folder under xp only x86.
i tried tinkering with the win7 and win2k3 x64 versions to no luck yet.

---

