---
title: "Will Convert ALL Desktops To Ubuntu While Windows In Virtualbox Pros &amp; Cons?"
date: 2010-03-08
forum: Virtualisation
---

### Post by AlexanderDGreat on 2010-03-08
Hi, we currently have a mix of Ubuntu 9.04, 9.10 and Windows XP. We're still stuck with Windows XP because our supplier has a program that only runs in it and they're using a strict IE-based app.

Now because we only use basic office computing like typing, Internet, printing, file sharing, email, and Intranet CMS, I want to replace ALL Windows computers, approx. 12 workstations with Ubuntu because it's more stable and secure. I will just install Virtualbox with Windows XP, lock it, and reinstall accdg. to our supplier's needs.

My experience with Ubuntu is 7 months. Can I ask for your opinion on my BOLD move? What do you think are the PRO's and CON's of my situation? Are there things I should know ahead?

Thank you so much for reading my post. I hope you can give any enlightenment. :)

---

### Post by sikander3786 on 2010-03-08
> **AlexanderDGreat said:**
> Hi, we currently have a mix of Ubuntu 9.04, 9.10 and Windows XP. We're still stuck with Windows XP because our supplier has a program that only runs in it and they're using a strict IE-based app.

Now because we only use basic office computing like typing, Internet, printing, file sharing, email, and Intranet CMS, I want to replace ALL Windows computers, approx. 12 workstations with Ubuntu because it's more stable and secure. I will just install Virtualbox with Windows XP, lock it, and reinstall accdg. to our supplier's needs.

My experience with Ubuntu is 7 months. Can I ask for your opinion on my BOLD move? What do you think are the PRO's and CON's of my situation? Are there things I should know ahead?

Thank you so much for reading my post. I hope you can give any enlightenment. :)

It will be a very bold move I appreciate.

The first thing is to check out your application in Virtual Box Environment. Does it work perfectly well?

You can easily do all your daily tasks like you mentioned typing, Internet, printing, file sharing, email, and Intranet CMS equally well with Ubuntu.

Switching to Ubuntu will surely reduce the costs and hours of maintenance that Windows takes.

So I think the best way around will be to check out Virtual Boxed Windows XP on 1 PC. Try it out for one week or so (because getting to some issues takes some time) and if every thing goes well, you could switch to Ubuntu.

Just make a note that I have switched nearly 20 PCs to Ubuntu. 15 of them in my Internet Cafe, 2 at home and 3 in my office. And that was never a wrong move.

Regards.

Sikander.

---

### Post by coldraven on 2010-03-08
If your XP boxes are OEM you need to save a couple of files before formatting the hard drives. Otherwise when you run XP in Virtualbox it will not activate*.
You need /windows/system32/wpa.dbl and if it exists the wpa.bak files.
Keep them safe somewhere!
Just copy them into your virtual machine.
You may have to read this as well [http://www.virtualbox.org/manual/ch09.html#changedmi](http://www.virtualbox.org/manual/ch09.html#changedmi)

I have not tried this but have a look [http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

This does not apply if you have COA versions of XP

*It works but only for 30 days

---

### Post by AlexanderDGreat on 2010-03-08
> You can easily do all your daily tasks like you mentioned typing, Internet, printing, file sharing, email, and Intranet CMS equally well with Ubuntu. I totally agree, yet EVEN MORE!

> Switching to Ubuntu will surely reduce the costs and hours of maintenance that Windows takes. - another AMEN. What we used to do in our IT dept. is to go to the office EARLY Monday morning to scan the Windows computers, update databases of antiviruses, and disk-defrag hds. What a way to start the week, huh? Ironically, they're all wasted because by Wednesday someone inserted a USB stick with a nasty new worm virus.

> So I think the best way around will be to check out Virtual Boxed Windows XP on 1 PC. Try it out for one week or so (because getting to some issues takes some time) and if every thing goes well, you could switch to Ubuntu.

Just make a note that I have switched nearly 20 PCs to Ubuntu. 15 of them in my Internet Cafe, 2 at home and 3 in my office. And that was never a wrong move.

This shows you know your stuff well. I also agree. Thanks for those insights sikander3786, it gave me hope!

> If your XP boxes are OEM you need to save a couple of files before formatting the hard drives - @coldraven - thanks for these insights as well, nope they're not OEM, we assemble our own workstations. :)

---

### Post by coldraven on 2010-03-09
What made me change from Windows?
This did!     [http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html](http://www.cs.auckland.ac.nz/~pgut001/pubs/vista_cost.html)

It's quite long but very informative, maybe save that for the weekend and read it whilst drinking a celebratory glass of Champagne. With the money you will save you'll be able to buy a whole case!
Good luck for your Linux based future  :D

---

### Post by mkvnmtr on 2010-03-09
I run Virtual Box on Ubuntu- I have run XP and several Linux distros. One thing to note. I use IPBlock -IPList on my host and like it. It will stop connections on the guest XP.Thus you can block many connections from known malware sites on your venerable windows guests. Check it out,

---

