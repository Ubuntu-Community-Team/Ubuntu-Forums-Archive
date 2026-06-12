---
title: "How do I prevent Grub command-line boots?"
date: 2011-05-18
forum: Security
---

### Post by perspectoff on 2011-05-18
The ability to manually boot using the Grub command-line constitutes a big security risk in Linux, IMO.

Any OS can be booted in this manner from a PXE-LAN, USB, or CD/DVD drive, circumventing BIOS-imposed boot restrictions. (Once a foreign OS is booted, of course, it can be used to access any part of an unencrypted hard drive.)

Placing passwords or locking menu items (in the Grub configuration files) does not prevent a user from booting manually using commands entered at the grub command-line.

As it stands now, when presented with the Grub menu (or after bringing up a hidden Grub menu with the "ESC" key), a user only needs to hit "c" to enter the Grub command-line mode to facilitate any type of bootup whatsoever. (They can then enter manually the Grub commands to boot an OS on any device.) This is extremely insecure and allows any passerby to boot the computer with a few keystrokes and a bootable USB drive.

How do I configure Grub so that it will require a password in order to enter the command-line mode (and thereby restrict boot options to the menu, which can then be password protected/locked) ?

---

### Post by bodhi.zazen on 2011-05-18
You will get a variety of opinions, but I am a firm believer you are spinning your wheels with such things.

IMO you need to restrict physical access.

I advise you worry more about physical access and less about bios and grub passwords.

Although I understand your concerns, there is no substitute for restricting access. This is why the industry standard is keep servers in locked rooms and both restrict and log who has physical access.

---

### Post by perspectoff on 2011-05-18
> **bodhi.zazen said:**
> You will get a variety of opinions, but I am a firm believer you are spinning your wheels with such things.

IMO you need to restrict physical access.

I advise you worry more about physical access and less about bios and grub passwords.

Although I understand your concerns, there is no substitute for restricting access. This is why the industry standard is keep servers in locked rooms and both restrict and log who has physical access.

Security is always important and it is unusual to see people advocate against it. See this excellent PC World article about the scenario I am describing:

[http://www.pcworld.com/article/114727/lock_down_your_pc.html](http://www.pcworld.com/article/114727/lock_down_your_pc.html)

In our datacenter there are many IT consultants each of which works on a different server. It is very difficult to hide some servers (that they shouldn't be accessing) in a locked closet while they work on others.

---

### Post by bodhi.zazen on 2011-05-18
> **perspectoff said:**
> I think that is somewhat of an ostrich-head-in-the-sand answer.

It is ?

> The recent Amazon EC2 cloud hack against Sony proves that. Server OS instances are often hosted within virtual machines in cloud locations to which physical access cannot always be restricted.

Furthermore, database and corporate information theft is often accomplished as an inside job by a disgruntled employee who already has (or managed to get) physical access to the server hardware.

Logging an instance of bootup to an external USB drive (through Grub)  would not identify the thief, anyway.

Sure, security cameras on every server could identify the thief, right? 

Not every facility can afford to implement for every server the type of physical access restrictions depicted in the "Mission Impossible" movie, though.

You see, the problem is still one of physical access. Sure bios and grub passwords will slow down casual intruders, but, not inside jobs or professional crackers.

What makes you leap from locks on doors to "Mission Impossible"? Locks on doors are trivial and very cost effective. Of course the locks need to be proportional to the value of the data you are protecting. So if you are running servers for the CIA, yep you need Mission Impossible.

You need an approach to security that is proportional to the value of the data.

In the case of physical access, ie booting the server and accessing it via grub that means physical security and bios / grub passwords offer trivial, at best, security. In the rare instance of accessing a virtual machine from a remote location, such as KVM or VPS, then you would add in network security, such as IP tables, TCPwrapper, strong passwords, ssh + keys, VPN, https, NIDS, etc.

If you want to password protect grub2 , see 

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

As you can see, that can be circumvented in several ways, one of several methods is to simply boot a live CD.

In the case where one has access to the boot menu in the first place, that implies they have access to boot a live CD (or flash drive).

---

### Post by perspectoff on 2011-05-18
> **bodhi.zazen said:**
> It is ?



You see, the problem is still one of physical access. Sure bios and grub passwords will slow down casual intruders, but, not inside jobs or professional crackers.

What makes you leap from locks on doors to "Mission Impossible"? Locks on doors are trivial and very cost effective. Of course the locks need to be proportional to the value of the data you are protecting. So if you are running servers for the CIA, yep you need Mission Impossible.

You need an approach to security that is proportional to the value of the data.

In the case of physical access, ie booting the server and accessing it via grub that means physical security and bios / grub passwords offer trivial, at best, security. In the rare instance of accessing a virtual machine from a remote location, such as KVM or VPS, then you would add in network security, such as IP tables, TCPwrapper, strong passwords, ssh + keys, VPN, https, NIDS, etc.

If you want to password protect grub2 , see 

[http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)

As you can see, that can be circumvented in several ways, one of several methods is to simply boot a live CD.

In the case where one has access to the boot menu in the first place, that implies they have access to boot a live CD (or flash drive).

The computers already have hard drive access password-protected (and the password stored in the BIOS). If a hard drive is removed from the computer, it cannot easily be accessed by merely plugging it into another computer whose BIOS does not have the correct password.

I also have no computer whose BIOS does not already restrict booting from a PXE-LAN, CD/DVD, or USB drive. Without a password, Grub allows circumvention of these BIOS restrictions, as stated in the OP. I'm just trying to figure out how to set the password.

I've read sections of the Grub Manual that deals with adding passwords to menu items and to recovery menu items. I just can't figure out how to enable a password for the command-line (and for manually editing the menu in real-time).

---

### Post by bodhi.zazen on 2011-05-18
[QUOTE=perspectoff;10832880]No that's rubbish./QUOTE]

Well, I think you are running against the limitations a software solution can offer against a physical access problem and taking your frustration out on me.

I completely understand what you are wanting to do, and, if there were a solution to what you are wanting, I would give it to you gladly, not to mention it would be widely deployed (limiting physical access is a hassle and has limitations).

As there is no such software solution we are all stuck limiting physical access. Harsh reality, but one you will have to come to grips with (unfortunately).

We are all entitled to our own opinions of course, and I find BIOS passwords are trivial to circumvent. YMMV and it sort of depends on your user case. If you want to slow down casual intruders, sure use them, but don't fool yourself into believing that the offer much, if any, protection against anything more then a casual intruder.

Good luck to you, perhaps someone will offer you to a solution to an age old problem.

---

### Post by perspectoff on 2011-05-19
Well, for Grub Legacy I sorted it out from a single post of Ubuntu Forums from 2007 (good thing Ubuntu Forums hasn't erased the archives).

[http://ubuntuforums.org/showthread.php?t=7353](http://ubuntuforums.org/showthread.php?t=7353)  (Post #7)

I had overlooked an option at the top of menu.lst that says "password." Uncommenting that option forces Grub Legacy to require a password in order to enter the command line (and also to edit menu item commands in real-time).

Any menu item with "lock" in it also then requires a password to access. I had read the Grub Legacy Manual 20 times before but could never sort it out.

For Grub 2 the solution is also fairly simple, once I found it in the Grub2 Manual here:

 [http://www.gnu.org/software/grub/manual/grub.html#Security](http://www.gnu.org/software/grub/manual/grub.html#Security)

Basically, edit the /etc/grub.d/40_custom file:

 sudo gedit /etc/grub.d/40_custom

and add the lines:

     set superusers="user1"
  #  password_pbkdf2 user1 grub.pbkdf2.sha512.10000.biglongstring
     password user1 unencryptedpasswordhere

where "user1" will be the user with permission to access the Grub2 command-line (or menu editing functions) and unencryptedpasswordhere will be the password required to access the Grub2 command-line. (The commented line is if a pbkdf2 encrypted password will be used).

Then, as usual:
 sudo update-grub

No need to move my servers to Fort Knox.

Problem solved.

---

### Post by bodhi.zazen on 2011-05-19
Glad you got it sorted, why not use simply use encryption (LUKS)?

---

### Post by perspectoff on 2011-05-21
So, the steps I have taken to limit access and prevent unauthorized bootups of my computers (that are in locations where it is not feasible/reasonable to lock them away in a vault) are these:

1 ) Set a BIOS supervisor/administrator password.

2 ) Set a Hard Drive password (through a BIOS utility/setting) which gets stored on a chip in the hard drive (able to be reset only by resoldering the hard drive). That way the hard drive can only be used in conjunction with a BIOS which has the password. If the hard drive is removed from the computer, it is not easily used in another computer.

3 ) In the BIOS, disable booting from any device except the hard drive.

4 ) Set passwords for Grub (Grub2 and/or Grub Legacy) so that the Grub command-line can not be used to manually boot from any device other than the hard drive.

5 ) Use only password-protected user accounts. Disallow root login.

6 ) When using a GUI-desktop, use screensavers that require the user password in order to return to the screen. (Not used with kiosk-mode computers).

7 ) Restrict USB access to specific users (optional).

8 ) Encrypt highly sensitive folders/drives (optional) and restrict user access by setting privileges. Set a root superuser password and disallow root access to highly sensitive encrypted folders. 

These precautions are now standard on every computer that is used in our organization in kiosk mode, as well as on computers that are (necessarily) located in high-traffic areas.

(In addition, of course, any computer connected to the network (LAN or WAN) also has the usual network security precautions, firewalls, proxies, network monitoring, etc.)

Other basic (and relatively simple) recommendations are welcomed.

---

