---
title: "Just put the forcepae option after the &quot;--&quot; entry on the installer command line"
date: 2014-04-15
forum: Ubuntu Development Version
---

### Post by sudodus on 2014-04-15
I started testing ***Lubuntu*** Trusty final with a Pentium M CPU with ***forcepae***, and it works. It runs live, and I can install it.

But the forcepae boot option is ***not automatically added*** in [SIZE=3]**[FONT=courier new]/etc/default/grub[/FONT]**[/SIZE]

which I suspect will cause problems to upgrade to a new kernel, when the next kernel version will be released.

Should I report it as a bug to Launchpad? In that case, against what package?

I think it will also affect ***Xubuntu*** (and I think people will try Xubuntu with forcepae in computers with Pentium M and more than 512 MB RAM).

---

### Post by sudodus on 2014-04-15
I tried to install the low latency kernel, and yes, it complains, that there 'This kernel does not support a non-PAE CPU'.

And apport was started automatically, so here we go with the bug report #1307862

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307862](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307862)

If you own a computer with a Pentium M or Celeron M CPU please add ***affects me too*** to the bug report!

---

### Post by sudodus on 2014-04-15
I tested this solution:

***Add forcepae into /etc/default/grub when installing with forcepae***

and of course run ***sudo update-grub*** afterwards to get it into **/boot/grub/grub.cfg**.

And after doing that manually I could install the other kernel (in this case the low-latency kernel). My Thinkpad T42 with Pentium M works with both kernels.

So I suggest that this will be done ***automatically*** for the benefit of all users including the refugees from XP :-)

---

### Post by sudodus on 2014-04-16
Good news about forcepae, that should be entered into a wiki page

-----
*Colin Watson* wrote 40 minutes ago:     #8

[I][B]Just put the forcepae option after the "--" entry on the installer command line and it will be copied to the target system.

[/B][/I]The "--" entry defines the boundary between options which are specific to the installer and ones that are copied to the target system.

*sudodus* wrote 18 minutes ago:     #9

This is new and positive information

I did not know the function of -- and I think many people need to be informed about it.

See this link for the 'whole story'

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1307105)
-----

I have tested, and I can confirm that it works :-)

---

