---
title: "security issues............................................ ......."
date: 2008-07-03
forum: Security
---

### Post by ettercap on 2008-07-03
hello every 1
i use windows xp on my pc at home and daily i get around 3-4 
port-scanning attempts ......
my anti virus detects and blocks it.......

now i have ubuntu in my laptop ..........
as far as i know there are hardly any viruses for linux...
how do i make my linux laptop secure.....
are there any 3rd party tools available please help......

i even found this link helpful....

[http://www.builderau.com.au/program/linux/soa/10-things-you-should-do-to-a-new-Linux-PC-before-exposing-it-to-the-Internet/0,339028299,339274586,00.htm](http://www.builderau.com.au/program/linux/soa/10-things-you-should-do-to-a-new-Linux-PC-before-exposing-it-to-the-Internet/0,339028299,339274586,00.htm)

---

### Post by lisati on 2008-07-03
Have a look here: [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338), in particular here: [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by spike_strip on 2008-07-03
Ubuntu is a very safe OS—as are most Linux/UNIX systems, it is M$ that is un-secure. 

There is nothing to worry about! 

I have been using Linux/UNIX for about six years now. 

Once; I received an e-mail with an attachment that I did not know...clicked on the attachment, and one day later I was reinstalling my Linux system, after a complete system crash. I believe I received a worm in that e-mail... can not prove it, and people will argue that what I have described is not even possible.

---

### Post by HermanAB on 2008-07-03
Stop fretting and enjoy your nice Ubuntu system.

In general you can click away on anything and everything with wild abandon.

---

### Post by ettercap on 2008-07-05
sorry if this sounds a bit rude....
but
u guys say that it is impossible/verydifficult to crack a box running ubuntu/linux...............

---

### Post by kevdog on 2008-07-05
crack a box is something else  -- that would imply authentication problems, buffer overflows, faults in listening daemons.  You are not immune to that.

---

### Post by brian_p on 2008-07-05
> **ettercap said:**
> sorry if this sounds a bit rude....
but
u guys say that it is impossible/verydifficult to crack a box running ubuntu/linux...............

In your first post you said you wanted a secure Ubuntu box. You'll get it by keeping your software up to date. Sounds too simple, doesn't it? But essentially that's all you need to do.

---

### Post by hyper_ch on 2008-07-05
maybe adding that if you install servers you should also take precautions on securing those...

---

### Post by Canis familiaris on 2008-07-05
You are quite secure. Only do not type any command blindly, say if someone posted in a forum. You should have some little idea about it.

---

### Post by brian_p on 2008-07-05
> **hyper_ch said:**
> maybe adding that if you install servers you should also take precautions on securing those...

Well, sticking with the default configuration is safe but reading the docs and understanding the changes you make is a must if you want to alter them. Having cups accept printing from the internet could lead to 10,000 copies of the firestarter manual being dumped on your network - and we wouldn't want that, would we?

And I'd still say keep the server software up to date.

---

### Post by ettercap on 2008-07-13
people............i asked how do i detect portscanning attempts ???????????????????

---

### Post by aysiu on 2008-07-13
> **ettercap said:**
> people............i asked how do i detect portscanning attempts ??????????????????? And it was already answered. Have a look at the second link in this reply, specifically the Firewall section: > **lisati said:**
> Have a look here: [http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338), in particular here: [http://ubuntuforums.org/showthread.php?t=765421](http://ubuntuforums.org/showthread.php?t=765421)

---

### Post by azr on 2008-07-14
If you have more time to play around i would also suggest using gaurddog - which has the policy anything not allowed is forbidden. This very conservative policy might ease your fears; especially when it stops you doing safe things you normally do, before you've configured it properly. 

Though i have a question: 
Is this not overkill for a home pc?

---

### Post by kevdog on 2008-07-14
If you need to detect portscans, then you need probably to at least set up a firewall that logs such activity.  You could then peruse the logs, or write a small shell script to fish out the activity you want to look at.

---

