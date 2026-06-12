---
title: "Why is everything slowing down?"
date: 2014-04-11
forum: The Cafe
---

### Post by Tristan_Williams on 2014-04-11
I've been in the Linux world for about 3 years. I used to be learning stuff left and right, configuring and tinkering things.
I used to have to reinstall every 2 or 3 weeks because I broke so many things while I was learning.

All of the sudden (within the last month or two) I have just stopped. I have a stable system, I don't tinker or learn anything new anymore.
I think the biggest thing I've done in a while is install LibreOffice, and that was a while ago.

Is there something I should do to fix this, or am I just done learning?

---

### Post by SeijiSensei on 2014-04-11
Try building a server and learning how to configure web services, DNS, email, etc.  You'll find there's a lot more to learn than just the desktop.

---

### Post by coldraven on 2014-04-11
Try running the "top" command in a terminal to see if some program or process is hogging your CPU. Press Q to quit top.
```
top
```

---

### Post by sudodus on 2014-04-11
If you want a challenge:

Make a USB drive that can boot as many computers as possible: 32-bit as well as 64-bit Intel and AMD computers running with old style BIOS as well as UEFI in secure mode with all bells and whistles. I think a tutorial thread or a wiki page describing such a system would be quite popular.

It is fairly straight-forward to make systems that run in 32-bit as well as 64-bit Intel and AMD computers running with old style BIOS. I managed to make an installed system that runs in 64-bit Intel and AMD computers running with old style BIOS as well as UEFI but not in secure mode. See this link[URL="https://help.ubuntu.com/community/In.../UEFI-and-BIOS"]

[/URL][https://help.ubuntu.com/community/In.../UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")[URL="https://help.ubuntu.com/community/In.../UEFI-and-BIOS"]
[/URL]

---

### Post by SeijiSensei on 2014-04-11
> **coldraven said:**
> Try running the "top" command in a terminal to see if some program or process is hogging your CPU. Press Q to quit top.
```
top
```

He wasn't talking about his computer "slowing down" but the pace of change in Ubuntu and Linux.

---

### Post by tgalati4 on 2014-04-11
When you reach the edge of knowlege, then it's your responsibility to expand it.  Try creating something new and exciting and sell it to Google or Facebook.

---

### Post by mattlach on 2014-04-11
If you want to force yourself to learn more, take Gentoo Linux out for a spin.

That's what forced me to learn and be comfortable with the terminal.

---

### Post by Tristan_Williams on 2014-04-12
> **mattlach said:**
> If you want to force yourself to learn more, take Gentoo Linux out for a spin.

That's what forced me to learn and be comfortable with the terminal.

That's probably what I'll do.
Either Gentoo or LFS

---

### Post by sam-c on 2014-04-12
> **Tristan_Williams said:**
> I've been in the Linux world for about 3 years. I used to be learning stuff left and right, configuring and tinkering things.
I used to have to reinstall every 2 or 3 weeks because I broke so many things while I was learning.

All of the sudden (within the last month or two) I have just stopped. I have a stable system, I don't tinker or learn anything new anymore.
I think the biggest thing I've done in a while is install LibreOffice, and that was a while ago.

Is there something I should do to fix this, or am I just done learning?
====================================
a- Too much Change not always in end user interest, Like Cellphones that worked fine that now barely work!
b- Security, so much double and treble securty that it becomes a Problem in Itself.
Thanx
Uncle Sam

---

### Post by sam-c on 2014-04-12
android is based on gentoo linux
Uncle Sam

---

### Post by codingman on 2014-04-12
There is way more than just a basic desktop system. Ubuntu isn't exactly the most easily customized distribution, try Arch too, I haven't had much luck with Gentoo, but LFS is cool too, just a large stepdown from Ubuntu.

---

### Post by jbaerboc on 2014-04-14
> **Tristan_Williams said:**
> I've been in the Linux world for about 3 years. I used to be learning stuff left and right, configuring and tinkering things.
I used to have to reinstall every 2 or 3 weeks because I broke so many things while I was learning.

All of the sudden (within the last month or two) I have just stopped. I have a stable system, I don't tinker or learn anything new anymore.
I think the biggest thing I've done in a while is install LibreOffice, and that was a while ago.

Is there something I should do to fix this, or am I just done learning?

I can understand completely where you're coming from. I have been a dual-boot distro-hop-a-holic for the last 6+ years and always had fun trying to figure out how to do this or that. But now a days I'm happy with my stable install and aside from the ocasional WINE game install I need to tweak I don't find myself doing much else.

For me half the reason is that Linux has developed so much since my earlier days with it that I install it and don't really have anything left to get working. To me that's an awesome plus!

---

### Post by sammiev on 2014-04-14
> **Tristan_Williams said:**
> I've been in the Linux world for about 3 years. I used to be learning stuff left and right, configuring and tinkering things.
I used to have to reinstall every 2 or 3 weeks because I broke so many things while I was learning.

All of the sudden (within the last month or two) I have just stopped. I have a stable system, I don't tinker or learn anything new anymore.
I think the biggest thing I've done in a while is install LibreOffice, and that was a while ago.

Is there something I should do to fix this, or am I just done learning?

Try the latest minimal installation iso and open box. Should keep you busy for a while.

---

### Post by angry_johnnie on 2014-04-15
Learn to code.  It'll make everything exciting again :)

---

### Post by QIII on 2014-04-15
Put a couple of different distros in VMs.  Learn them all.

Get a copy of the Linux Bible.  Go through every page.  Try to break your installations on purpose.  Put them back together.  If you completely bork a VM, reinstall and see what you learned.

---

### Post by Tristan_Williams on 2014-04-16
> **sammiev said:**
> Try the latest minimal installation iso and open box. Should keep you busy for a while.

Thanks, but that's what I'm running right now.
I've installed and uninstalled it 100+ times, each time building something different. 

But yes I would definitely recommend this to everyone else. It's just that I've done it so many times

---

### Post by Old_Grey_Wolf on 2014-04-16
It depends on why you want to keep learning.

[INDENT]For me, it was to keep current on technology for my job as a system engineer. About 2007, I was hearing things about cloud computing. In 2009, I decided to do a hands-on investigation of it. I had some extra computers at home I could use for the learning project. I ended up creating my own private cloud or IaaS using the KVM hypervisor and Eucalyptus. Ubuntu 9.04 made that easier as it allowed me to set up the basic system in one weekend. To make the cloud work the way I wanted, I had to build VMs for DNS, LDAP, Email server, and so forth. About six months later when the company did a proposal for a Cloud computer contract, I was one of the few system engineers that actually had hands-on experience regarding the subject. That was enough to keep me financially very well employed until I retired a little over a year ago.[/INDENT]

Are you wanting to learn for personal home computer use, a future career, a current career, or something else?

---

### Post by Tristan_Williams on 2014-04-16
> **Old_Grey_Wolf said:**
> Are you wanting to learn for personal home computer use, a future career, a current career, or something else?

I would love to have a future career in the Linux field.

---

### Post by sammiev on 2014-04-16
[This]("http://ubuntuforums.org/showthread.php?t=2210339") maybe an option.

---

