---
title: "Just not impressed with Breezy"
date: 2005-11-17
forum: The Cafe
---

### Post by Apostata on 2005-11-17
I switched over to (K)Ubuntu from Libranet earlier this year, and I immediately liked the stability of Hoary:  I liked Synaptic as an updater, I liked the default selection of applications, and the distro as a whole.

However, Breezy is another issue.  There are two unresolved bugs that I find troubling:  I cannot reboot, and my clock/timezone is stuck at UTC.  Needless to say that these are two pretty basic things you'd want in an operating system:  the ability to reboot and having the correct time.

Regarding the first problem, please see this link (and there are many others): [http://www.ubuntuforums.org/showthread.php?t=75314]("http://www.ubuntuforums.org/showthread.php?t=75314")

Regarding the second, please see this link (and there are many others):[http://www.ubuntuforums.org/showthread.php?t=53411&highlight=timezone+problem]("http://www.ubuntuforums.org/showthread.php?t=53411&highlight=timezone+problem")

Note:  there are some people who have managed to solve their timezone issues, but I have followed every prescription to no avail.  All of my email comes in (and goes out) timestamped 5 hours later than it should, even though KDM shows the correct time.

  Perhaps I'm whining, but I just don't think Breezy is nearly as well-conceived (and cooked) as Hoary, which makes me wonder how much scrutiny/testing is done before a new release happens.  Adept may be a sufficient replacement for Synaptic, but the interface looks like something from 3 years ago and I'm not impressed with it's lack of advanced search features.

  Sorry - had to get this off my chest.  I just want the bloody thing to work.

---

### Post by bin on 2005-11-17
Timezone prob:-

You're using KDE - first off I'd open a terminal and do 
sudo tzconfig
- follow the prompts - this *may* not make a difference.......but.......

KDE is a bit like winders in this respect - you need to make sure your local time is the same as the timezone time. That may not make sense until you right click on the clock and see the difference by selecting Local time and timezone time. What I have found is that once the timezone is set correctly and the time in there is right, then selecting local time, then timezone, then back to local, puts it all right.

Simple:confused: :confused: :confused:

Power thing:-
use adept to install sysv-rc-conf
sudo sysv-rc-conf 
make a note of levels for apm then switch it off at all levels.

You might also want to try the 686 kernel which you can install via adept

HTH

in light

bin

---

### Post by sciurus on 2005-12-13
I had the kubuntu time problem for a while as well and was frustrated that none of the solutions here would fix it. I seem to have solved it with /etc/timezone; see my post in the thread you mentioned.

---

### Post by Apostata on 2005-12-14
[QUOTE=sciurus]I had the kubuntu time problem for a while as well and was frustrated that none of the solutions here would fix it. I seem to have solved it with /etc/timezone; see my post in the thread you mentioned.[/QUOTE]

Thanks for the response, sciurus.

I managed to address this issue recently by upgrading to KDE 3.5.0.  It's still not totally solved as, for some reason, the system time is still UTC even though my user time is correct (the reason being that my email is tagged at roughly 5 hours later than my timezone).  I know there's a solution out there, but it's just a PIT(f)A to spend this much time addressing things that I take for granted in (I hate to say it) WinXP.

---

### Post by prizrak on 2005-12-14
I think the time issue is only with Kubuntu as it works perfectly well with Ubuntu. For the reboot problem I was having issues myself and found this to be a fix that works
Go to the terminal and type in 
> sudo gedit /boot/grub/menu.lst
In there find the line that looks like this
> /vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash 
Note: you might have a 386 kernel and the "root=/dev/hda3" might be different. 
What you have to do is add the part in bold to your line, it should work after that. 
> /vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash **reboot=h** 
Note: to test, shutdown the machine. Then start it again, and then restart.
Hope this helps, I do agree that some things broke in Breezy randomly

---

### Post by Apostata on 2005-12-14
Thanks for the suggestion prizrak - no luck.

I think my only choice (since I run the default 386 kernel) is to upgrade to 686 - I'm guessing that this could fix it.

[starts searching for a how-to]

[Found One]("http://www.ubuntuforums.org/showthread.php?t=75071&highlight=upgrade+386+686+kernel").

---

### Post by prizrak on 2005-12-14
[QUOTE=Apostata]Thanks for the suggestion prizrak - no luck.

I think my only choice (since I run the default 386 kernel) is to upgrade to 686 - I'm guessing that this could fix it.

[starts searching for a how-to]

[Found One]("http://www.ubuntuforums.org/showthread.php?t=75071&highlight=upgrade+386+686+kernel").[/QUOTE]
You welcome, upgrading is actually easy just type 
> apt-get install linux-686
It should install everything you need (did on my machine, they you chose it from GRUB. Once successful you can hunt down all the 386 left overs and get rid of them.

---

### Post by erikpiper on 2005-12-14
By the way- a 686 kernel is faster, and as prizrak said, easy. You dont HAVE to get rid of anything...

---

### Post by prizrak on 2005-12-15
[QUOTE=erikpiper]By the way- a 686 kernel is faster, and as prizrak said, easy. You dont HAVE to get rid of anything...[/QUOTE]
True you don't, but I don't tend to keep the old kernel once I'm sure the new one is working :)

---

### Post by gord on 2005-12-15
keeping the old kernel could save your life one day ;)... well not your life... your um.. installation.

---

### Post by Kvark on 2005-12-15
Guess thats what you get with a new version, a couple new features and a couple new bugs. :neutral:

Try typing "sudo reboot" in CLI. If that worked then add an icon to the menu that executes the command "gksudo reboot" when you click on it.

---

### Post by prizrak on 2005-12-15
[QUOTE=gord]keeping the old kernel could save your life one day ;)... well not your life... your um.. installation.[/QUOTE]
Just don't break the current kernel :) Besides there is restore mode anyways and with Ubuntu installing a kernel is a Breeze ;)

---

