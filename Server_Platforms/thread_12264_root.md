---
title: "root"
date: 2005-01-23
forum: Server Platforms
---

### Post by Gezzer on 2005-01-23
how do i get in to root
i know that im in sudo root but how do i get in to root

i wish to change a few things that can only be done via root

any help, cheers ...

---

### Post by Buffalo Soldier on 2005-01-23
Go to [http://ubuntuguide.org/](http://ubuntuguide.org/) there are guides for:
- How to set/change/enable root user password?
- How to allow root user to login into GNOME?
- How to switch to root user in Terminal mode?

It's nice if before posting questions on the user forum to:

a) checking whether anyone has posted the same question on the same forum.
b) checking the documentation the the specific GNU/Linux distribution their using.
c) searching the WWW using seach engine
d) searching on other [www.tldp.org/](www.tldp.org/) (The Linux Documentation Project), which has many How-Tos, Guides, FAQs and MANuals.
e) checking the documentation for the specific application/software. Such as checking at [www.gnu.org/software/grub/manual/grub.html](www.gnu.org/software/grub/manual/grub.html) for GRUB related problems.

Here is a list of links that I found helpful in my experience as a newbie. Some are specific to UbuntuLinux while others can be applied to most GNU/Linux distribution in general.

[www.ubuntulinux.org/support/documentation/](www.ubuntulinux.org/support/documentation/)
[ubuntuguide.org/](ubuntuguide.org/)
[www.gnome.org/learn/](www.gnome.org/learn/)
[www.gnu.org/software/grub/manual/grub.html](www.gnu.org/software/grub/manual/grub.html)
[www.tldp.org/](www.tldp.org/)
[easylinuxguide.com/](easylinuxguide.com/)
[www.linuxforums.org/](www.linuxforums.org/)
[www.linuxquestions.org/](www.linuxquestions.org/)
[www.linux.org/lessons/beginner/toc.html](www.linux.org/lessons/beginner/toc.html)

---

### Post by mattjs on 2005-01-26
I have a similar problem (after trashing my ubuntu and re-installing for reasons i wont go into...).

I would like to do a graphical log in as root through the GDM Greeter.  This is possible as you would expect but requires more than simply allowing the login with root from the Gnome Configuration applet as described here:
[http://ubuntuguide.org/#setchangeenablerootpassword](http://ubuntuguide.org/#setchangeenablerootpassword)

The is a minor one or toe line change required to the PAM configuration in an /etc/pam.d/* file or files to achieve this.

(Whilst I realise the security need for it an root login is disabled in Debian and derivatives dey default I am a developer and find sudo a constant annoyance.  In reality if one is constantly running root shells (xterms) one might as well just log in as root.  Provided acces to the machine or desktop is secure, remote X XDM XGDM whatever is disabled, and Remote Desktop sharing in the latest Gnome (ie VNC there is little difference in security.  (And any errant application run from a sudo bash will be just as damaging)...).

But anyway I sould like to find out what this pam change is to get it working I had the info form a site online and it working before but have forgotten the changes ...

Any Gurus around who really do know it all!?

Cheers in advance,
Matthew.

---

### Post by )-pAchamAma-( on 2005-05-06
You have to change the GDM Configuration file: /etc/gdm/gdm.conf.
In section [security] change value AllowRoot to AllowRoot=true.   ;-)

---

