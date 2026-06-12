---
title: "hang on boot"
date: 2008-02-14
forum: Virtualisation
---

### Post by bossa on 2008-02-14
Hi All

I have started to experience a no go when trying to boot any Linux distros in VMware. Previously I had PCLinuxOS and Hardy running and have currently XP. Now when ever I try to boot everything just stops at boot (Live CD).

PCLinuxOS : Stops at probing SCSI devices
GOS : rejecting I/O to offline device

Sometimes they boot if I select Linux 2.6 but when trying for a second time they all refuse to boot fully?
XP is running fine.
Any ideas?

---

### Post by bossa on 2008-02-15
Here are a couple of screens from PCLinuxOS and Mandriva live CD on boot
[[IMG]http://img183.imageshack.us/img183/5232/10872127oh0.th.png[/IMG]](http://img183.imageshack.us/my.php?image=10872127oh0.png)
[[IMG]http://img142.imageshack.us/img142/9404/69133303ps5.th.png[/IMG]](http://img142.imageshack.us/my.php?image=69133303ps5.png)
[[IMG]http://img142.imageshack.us/img142/6965/29468167su1.th.png[/IMG]](http://img142.imageshack.us/my.php?image=29468167su1.png)

---

### Post by fjgaude on 2008-02-15
I can't think of anything other than: do you have enough real disk space for what you are doing? Memory?

---

### Post by bossa on 2008-02-15
Hi fjgaude
I have plenty of real space approx 50 gigs and 2gigs of ram . I even freed up some  and tried a new burnt LinuxMint and I'm getting this:

[[IMG]http://img165.imageshack.us/img165/1914/62936919di8.th.png[/IMG]](http://img165.imageshack.us/my.php?image=62936919di8.png)

---

### Post by bossa on 2008-02-15
Well I completely  uninstalled VMware re installed it and Bobs your uncle ....same problem :confused:. Wiil try XP again to see if this is just a Linux thing. The distros work in Virtualbox but I dont like the fact you cant have fullscreen.

---

### Post by bossa on 2008-02-15
Well I can confirm that XPPro boots and installs no problem at all ...just the Linux distro that dont work....downer:confused:

---

### Post by bobdougal on 2008-02-19
I had a similar problem. I fixed it by:

[LIST=1]
[*]Stop the VM


[*]Edit the .vmx file for that virtual machine


[*]Change the line [FONT="Courier New"]scsi0.virtualDev = "buslogic"[/FONT] to
[FONT="Courier New"]scsi0.virtualDev = "lsilogic"[/FONT]
(or add that line if it is absent.)


[*]When you restart the virtual machine, it will mention the change, just click Ok, and it should work.
[/LIST]

cheers

bob

---

