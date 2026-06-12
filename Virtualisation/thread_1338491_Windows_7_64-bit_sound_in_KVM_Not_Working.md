---
title: "Windows 7 64-bit sound in KVM Not Working"
date: 2009-11-26
forum: Virtualisation
---

### Post by dmgub on 2009-11-26
I'm running Ubuntu Server 9.10 64-bit, with ubuntu desktop (Gnome) installed.
Trying to run Windows 7 Ultimate 64-bit VM in KVM.
Windows-7 installs, and comes up. Networking works. Screen works pretty well if I use the "-vga std" option.
I am using the version of KVM/QEMU that installs with Ubuntu 9.10, plus used apt-get to fetch the packages for virt-manager.
kvm --version yields "QEMU PC emulator version 0.11.0 (qemu-kvm-0.11.0)"
uname -r yields "2.6.31-14-server".
I'm starting Windows 7 with command line:
kvm -vga std /var/lib/libvirt/images/<image> -boot c -m 5120

Sound does not work.  Windows-7 does not detect any sound hardware.

At one point, Win 7 seemed to find a "Multimedia Controller" in Windows Device Manager. The controller was marked not working. On scanning for suitable drivers, no suitable drivers were found. Now, for some reason, Windows isn't seeing the Multimedia Controller at all.
Per the article at: 
   [http://brainmindinstrev.blogspot.com/2009_04_01_archive.html](http://brainmindinstrev.blogspot.com/2009_04_01_archive.html)
  I tried downloading the ES1370 legacy driver, but it would not install in Windows (Windows just said it was an out-of-date driver).
I also tried experimenting with -soundhw sb16, but that seemed to make no difference.

The underlying hardware is a Dell M6400 with Intel HDA chipset, CPU is   [FONT=&quot]Intel Core 2 Duo T9900[/FONT]. Sound works well in the Ubuntu 9.10 host OS in which KVM is running (e.g. can play radio channels).
[FONT=&quot][/FONT]
How do I get KVM sound working with Win7 64-bit?

Thanks!

---

### Post by l3dweeb on 2009-11-26
I have pretty similar install and situation. It's an AMD Phenom-II 4-core
with a Realtek ALC889A Codec. I have Ubuntu 9.10 w/KVM and Windows 7
ultimate. I just started looking at it, but I thought I'd at least post that
someone else has the same issue. I'll post again if I find anything

---

### Post by l3dweeb on 2009-11-26
Update: I solved the problem on my machine. 

Initially, there was no sound device located. clicked on the yellow exclamation point
issue icon in the lower-right tray and clicked on the selection to troubleshoot.
It finished saying that it may have found additional hardware not previously detected.
I then looked at device manager, and now there was a sound device that was not
working. I clicked on it, and told it to update the driver. It did that, and now it works.
BTW, I am using ES1370 device model in KVM.

Hope you have similar success.

---

### Post by dmgub on 2009-11-27
l3dweeb, glad you had success. Still no luck for me.
I specified "-soundhw es1370" on the kvm command line.
In Windows, there was no yellow exclamation point in lower right-hand tray for me. However, on opening Device Manager, under "Other Devices" it shows "Multimedia Audio Controller" with yellow exclamation point. Attempted to update driver, I get "Device Driver software was not installed successfully" (I think it could not find the right driver in Windows update or on pre-installed driver folders).

So - still doesn't work. Anyone got any suggestions??

Thanks.

P.S. Tried with ac97, same result as es1370.
Tried with the other ones - GUS, adlib, sb16, cs4231a - in those cases (unlike ac97 and es1370) no sound card or multimedia controller was found by Device Manager at all.
BTW - Internet Access was working fine inside the Windows VM all this time, I can browse the web from IE8 for instance.

---

### Post by skliarie on 2009-12-08
In my case the device manager said: "The drivers for this device are not installed", and "Update Driver..." button not able to find the appropiarte driver.

Could be it is because I use Evaluation version of Windows 7?

BTW, there is a bug on the issue:
[https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/419182](https://bugs.launchpad.net/ubuntu/+source/kvm/+bug/419182)
but looks like most of the problem lies with Windows 7.

Also, there is a question on superuser.com on that:
[http://superuser.com/questions/39506/driver-for-ensoniq-audiopci-es1370-on-windows-7/80408](http://superuser.com/questions/39506/driver-for-ensoniq-audiopci-es1370-on-windows-7/80408)

---

