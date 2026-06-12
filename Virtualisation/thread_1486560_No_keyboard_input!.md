---
title: "No keyboard input!"
date: 2010-05-18
forum: Virtualisation
---

### Post by The WHAM Burglar on 2010-05-18
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Although almost self explanatory; after the auto install of vmware tools no
input
from the keyboard can be detected by Ubuntu. This effectively renders
Ubuntu useless as I cannot log in, in addition is exhibited only by the
Ubuntu virtual machine.

The version of Ubuntu in question: ubuntu-10.04-desktop-i386.
VMWare Workstation version: VMware Workstation 7.0.1 build-227600

Youtube video:
[http://www.youtube.com/watch?v=OVkY0mDa0eI](http://www.youtube.com/watch?v=OVkY0mDa0eI)


-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFL8hjUMiSrPaXCPwQRCLxVAQDLPc/dqLEp9foCELJPv/Apf0cnshVsN1dG
2kccVcxxlQEAuNOM9YT/TgmLY0cJRfU3ib6ZK+OJYMYtqyR2r389vqo=
=WiNw
-----END PGP SIGNATURE-----

---

### Post by phrostbyte on 2010-05-18
This should solve your problem:
[http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/)

On an unrelated note, your GPG signature seems to be invalid.

---

### Post by The WHAM Burglar on 2010-05-18
-----BEGIN PGP SIGNED MESSAGE-----
Hash: SHA256

Sadly that does not help due to the fact that the menu with the option
&#8216;console login&#8217; does not display. Is there another way that I am not
aware of?

My PGP public key can be found at keyserver.noreply.org by keyID:
0xCDC5A14E

-----BEGIN PGP SIGNATURE-----
Version: (N/A)
Charset: utf-8

wlcDBQFL8iixMiSrPaXCPwQRCByrAP4lTTscm3dVHv0Rgae3c7NaQJVTmqAMlb31
d2ujtipqfwD/YVCmX32BWW4J620KP2A0PSk7KsFnpFyQqtw4wVI5Oew=
=6SGD
-----END PGP SIGNATURE-----

---

### Post by The WHAM Burglar on 2010-05-18
Attempting to try other keyboards has messed up the GNOME tool bar rather badly, see below:
[IMG]http://farm4.static.flickr.com/3486/4618070798_984040443e.jpg[/IMG]

Full size link
[http://farm4.static.flickr.com/3486/4618070798_04cb828629_o.png](http://farm4.static.flickr.com/3486/4618070798_04cb828629_o.png)

Being that this limits what menus I can access, well, I seem to be stuck at the login prompt effectively locked out of the operating system.

---

### Post by rbarryza on 2010-07-13
I had the same problem with VMWare Workstation 7.0.1 and Ubuntu 10.04 as Guest OS.  I got around it in the end by using the Universal Access Preferences menu (icon is a little man in a circle on the task bar on the login screen - on top of "Session" on your screenshot).  Click on the icon, then click on "Universal Access Preferences".  On the menu that pops up, enable the on-screen keyboard.  Click "Close", then restart the VM.  The login screen will now come up with an on-screen keyboard.  Use that to type your password.  Once logged in, my kb worked.  I then followed the instructions here:

[http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/)

to fix it permanently.

---

### Post by The WHAM Burglar on 2010-07-17
> **rbarryza said:**
> I had the same problem with VMWare Workstation 7.0.1 and Ubuntu 10.04 as Guest OS.  I got around it in the end by using the Universal Access Preferences menu (icon is a little man in a circle on the task bar on the login screen - on top of "Session" on your screenshot).  Click on the icon, then click on "Universal Access Preferences".  On the menu that pops up, enable the on-screen keyboard.  Click "Close", then restart the VM.  The login screen will now come up with an on-screen keyboard.  Use that to type your password.  Once logged in, my kb worked.  I then followed the instructions here:

[http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/](http://reformedmusings.wordpress.com/2010/04/24/keyboard-issues-with-ubuntu-lucid-10-04-and-vmware-workstation-7-0/)

to fix it permanently.

Why that is the same link posted 68 days ago! What a coincidence that the link is also for a different distro of Ubuntu and a different version of VMWare rendering it utterly useless because I was using ubuntu-10.04-desktop-i386! Who would have thunk it? Perhaps someone who could: comprehend the English language, compare user interfaces and compare numbers. 
Good grief.

---

