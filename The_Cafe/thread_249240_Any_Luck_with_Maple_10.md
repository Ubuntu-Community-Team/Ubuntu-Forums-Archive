---
title: "Any Luck with Maple 10?"
date: 2006-09-02
forum: The Cafe
---

### Post by Clytemnestra on 2006-09-02
Has anyone here been able to run Maple 10 on Dapper?  I have to use Maple for school, so I want to know how well the Linux version works (Maple's OS requirements page only mentioned RPM-based distros, so I am unsure :frown:).  Thank you for any help you can give me.  I am currently running Kubuntu Dapper 32-bit on a dual-core machine.

---

### Post by hizaguchi on 2006-09-02
I've not tried it yet, but the Linux version should work.  There's also an open source alternative, Maxima.  The syntax is a little different, but it can handle alot of the same work.

---

### Post by mips on 2006-09-02
[http://www.physics.drexel.edu/liki/index.php/Debian_Sysadmin](http://www.physics.drexel.edu/liki/index.php/Debian_Sysadmin)

---

### Post by roderikk on 2006-09-02
You could also try to use Octave with its GUI interface KOctave. This is almost the same as Matlab but some slight differences. It can even read m files, and almost all the syntax is compatible. I always use it for my university work.

---

### Post by taurus on 2006-09-02
I am still waiting for our copy to arrive so as soon as it does, will let you know if I can install it on Dapper (32bit) or not...

---

### Post by Clytemnestra on 2006-09-02
Hi. Thanks for the responses so far.
Unfortunately, I don't have the choice of using one of the open source programs that works like Maple. My whole class uses Maple, and my professor wants to see our work done in Maple. :( It would have saved me a lot of money!
Also, I forgot to mention this earlier: I've been looking on Maple's download site, and there only appear to be packages for Redhat SUSE and Mandriva. If I download one of them, will I be able to install it on Ubuntu somehow? Or should I consider getting the Windows version and running it through WINE? If you want to see what installers they have, this is the link:

[http://www.maplesoft.com/products/maple/systemreq/index.aspx](http://www.maplesoft.com/products/maple/systemreq/index.aspx)

Thanks for your help. ;)

---

### Post by zachtib on 2006-09-02
> **Clytemnestra said:**
> Hi. Thanks for the responses so far.
Unfortunately, I don't have the choice of using one of the open source programs that works like Maple. My whole class uses Maple, and my professor wants to see our work done in Maple. :( It would have saved me a lot of money!
Also, I forgot to mention this earlier: I've been looking on Maple's download site, and there only appear to be packages for Redhat SUSE and Mandriva. If I download one of them, will I be able to install it on Ubuntu somehow? Or should I consider getting the Windows version and running it through WINE? If you want to see what installers they have, this is the link:

[http://www.maplesoft.com/products/maple/systemreq/index.aspx](http://www.maplesoft.com/products/maple/systemreq/index.aspx)

Thanks for your help. ;)

I had to use Maple 10 for school as well and the native linux version ran flawlessly.  I had a CD with a .bin installer.  Have you tried insatlling the .rpm with alien?

---

### Post by taurus on 2006-09-02
When you purchase a copy of Maple, it comes with Windows, Linux, and OSX!!!  You just run the installer and if it has the wrong permission, then you just copy the installer to your harddrive and change the permission and then run it!

Otherwise,

```
sudo aptitude update
sudo aptitude install alien
alien <filename>.rpm
sudo dpkg -i <filename>.deb

```

---

### Post by cong06 on 2007-10-05
I have a windows version installed, but it doesn't work through wine...is there a way to fix that?
do I need to reinstall it through Linux with a CD for it to work?

---

### Post by cong06 on 2007-10-28
Ok. so I've noticed that you need to have the maple folder in the same directory path as when it was originally installed. I haven't messed around with it too much...

I wonder if there's some way to edit it's view of that path so when it's in Linux it can find its self...

Kinda annoying that it uses Absolute paths instead of Relative paths like most programs...

---

