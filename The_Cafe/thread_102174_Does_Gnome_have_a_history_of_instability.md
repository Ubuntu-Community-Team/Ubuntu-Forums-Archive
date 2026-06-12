---
title: "Does Gnome have a history of instability?"
date: 2005-12-11
forum: The Cafe
---

### Post by YourSurrogateGod on 2005-12-11
Atleast 2 or 3 times a week, some part of the gnome desktop crashes. It just stops working, I run alot of apps, but I would expect some functionality to slow down, not crash entirely. Anyone else have this problem? Which desktop environment have you found to be the most stable in your experience?

---

### Post by az on 2005-12-11
Rock solid here.

What version are you running?

---

### Post by aysiu on 2005-12-11
[QUOTE=YourSurrogateGod]Which desktop environment have you found to be the most stable in your experience?[/QUOTE] XFCE

---

### Post by 23meg on 2005-12-11
I've found Gnome to be the most stable; I've not had any problems with Gnome-shipped apps so far. You should try to isolate your problems by running the apps from terminal, watching your logs and posting bug reports / question threads; they may not be directly Gnome related.

---

### Post by arnieboy on 2005-12-11
[QUOTE=YourSurrogateGod]Atleast 2 or 3 times a week, some part of the gnome desktop crashes. It just stops working, I run alot of apps, but I would expect some functionality to slow down, not crash entirely. Anyone else have this problem? Which desktop environment have you found to be the most stable in your experience?[/QUOTE]
which apps are crashing? Could you be more specific?

---

### Post by YourSurrogateGod on 2005-12-11
[QUOTE=azz]Rock solid here.

What version are you running?[/QUOTE]
2.10.0

---

### Post by YourSurrogateGod on 2005-12-11
[QUOTE=arnieboy]which apps are crashing? Could you be more specific?[/QUOTE]
Nautilus seems to be the biggest offender in this instance. Whenever I'm doing alot of copying from my linux partition to my external hard drive and from my windows partition to my linux partition (I just leave this to run until it's done) nautilus sometimes just seezes up(sp?) (for lack of a better word.) The progress bars are no longer working (the ones that display the progress of the file transfer) and I have to start over.

---

### Post by YourSurrogateGod on 2005-12-11
[QUOTE=aysiu]XFCE[/QUOTE]
Thanks, I've tried it, but didn't fancy it too much and went back to gnome. I've had some problems with it and managed to resolve it, but it just wasn't my thing.

---

### Post by Lovechild on 2005-12-11
I run the development version of GNOME and it's just peachy so far.

but if you do encounter reproducable crashes, please file bugs, I've written up a short guide explaining the steps:

[http://ubuntuforums.org/showthread.php?t=100738](http://ubuntuforums.org/showthread.php?t=100738)

---

### Post by arnieboy on 2005-12-11
[QUOTE=YourSurrogateGod]Nautilus seems to be the biggest offender in this instance. Whenever I'm doing alot of copying from my linux partition to my external hard drive and from my windows partition to my linux partition (I just leave this to run until it's done) nautilus sometimes just seezes up(sp?) (for lack of a better word.) The progress bars are no longer working (the ones that display the progress of the file transfer) and I have to start over.[/QUOTE]
If I were you, I might want to look into swap overloading. How much physical memory (RAM) do u have on your computer and what is the size of your swap space?

---

### Post by az on 2005-12-11
[QUOTE=YourSurrogateGod]2.10.0[/QUOTE]
Can you upgrade to breezy?  It has the current stable version of Gnome.

---

### Post by YourSurrogateGod on 2005-12-11
[QUOTE=arnieboy]If I were you, I might want to look into swap overloading. How much physical memory (RAM) do u have on your computer and what is the size of your swap space?[/QUOTE]
I'll monitor that.

---

### Post by YourSurrogateGod on 2005-12-11
[QUOTE=azz]Can you upgrade to breezy?  It has the current stable version of Gnome.[/QUOTE]
I'm reluctant to do that since 6.04 will be out in some time...

---

### Post by 23meg on 2005-12-11
[QUOTE=YourSurrogateGod]I'm reluctant to do that since 6.04 will be out in some time...[/QUOTE]
It has about five months to go out of six; quite a while. If that's the only thing keeping you back, go ahead and upgrade.

---

### Post by YourSurrogateGod on 2005-12-11
[QUOTE=23meg]It has about five months to go out of six; quite a while. If that's the only thing keeping you back, go ahead and upgrade.[/QUOTE]
I just might.

---

### Post by KiwiNZ on 2005-12-11
I will agree with Azz on this I had Gnome instability with Hoary and dropped it in favour of Suse 10.
I have now installed Breezy and have experienced no issues with Gnome at all.
In fact I am in love with Breezy *sigh*

---

### Post by YourSurrogateGod on 2005-12-11
[QUOTE=KiwiNZ]I will agree with Azz on this I had Gnome instability with Hoary and dropped it in favour of Suse 10.
I have now installed Breezy and have experienced no issues with Gnome at all.
In fact I am in love with Breezy *sigh*[/QUOTE]
Never knew this. I'll try 5.10 when winterbreak starts.

---

### Post by benplaut on 2005-12-11
i've found that XCFE, flux, and openbox are the most stable. Least stable are, in order, e17, KDE 3.3, KDE 3.4-3.5, and gnome it somewhere in the middle

---

### Post by Perfect Storm on 2005-12-11
Same here Gnome is rock solid on my machine and fast too.

---

### Post by YourSurrogateGod on 2005-12-11
[QUOTE=Artificial Intelligence]Same here Gnome is rock solid on my machine and fast too.[/QUOTE]
Maybe it's the newer 2.12 version that you're running in combination with 5.10... like I said, I'll upgrade during the upcoming winter break.

---

### Post by Lovechild on 2005-12-11
GNOME 2.10 was indeed problematic for some people I can't recall the issue specifically since I'm normally on the development branch and thus I never encounter bugs in the stable product. Besides 2.10 is what.. 9 months old now, that's ancient history... no god I love open source.

---

### Post by prizrak on 2005-12-11
Nautilus just sux on file transfers, it appears to freeze all the time when I do network transfers. It's still working in the background though, I have remedied that problem by using Midnight Commander from the command line for transfers. I'm also playing with Gnome Commander (both are in the repos) but haven't done network transfer yet.

---

### Post by Lovechild on 2005-12-11
[QUOTE=prizrak]Nautilus just sux on file transfers, it appears to freeze all the time when I do network transfers. It's still working in the background though, I have remedied that problem by using Midnight Commander from the command line for transfers. I'm also playing with Gnome Commander (both are in the repos) but haven't done network transfer yet.[/QUOTE]

Have you filed a bug.. you know if it's not in bugzilla it doesn't exist.

---

### Post by JimmyJazz on 2005-12-11
I've had alot of issues with Gnome also.  I've found XFCE to be much more stable but I still like Gnome for alot of stuff.

---

### Post by YourSurrogateGod on 2005-12-11
Hmm... now nautilus is going nuts with the CPU, using it up completely. What's the command on restarting that nautilus?

---

### Post by erikpiper on 2005-12-11
killall nautalis

nautalis

(right?)

---

### Post by YourSurrogateGod on 2005-12-11
[QUOTE=erikpiper]killall nautalis

nautalis

(right?)[/QUOTE]
Ahh... killall, need to remember that. Thanks.

---

### Post by prizrak on 2005-12-11
[QUOTE=Lovechild]Have you filed a bug.. you know if it's not in bugzilla it doesn't exist.[/QUOTE]
Hmm didn't think of it, could you point me to the bugzilla for Gnome? (Also I kinda figured the issue was mostly with the fact that I run on a Wi-Fi connection)

---

### Post by prizrak on 2005-12-11
[QUOTE=erikpiper]killall nautalis

nautalis

(right?)[/QUOTE]
You don't need to type nautilus again it restarts on its own (which sucked when I was trying to get it to NOT w/o restarting Gnome with a no-desktop parameter)

---

### Post by Lovechild on 2005-12-12
[QUOTE=prizrak]Hmm didn't think of it, could you point me to the bugzilla for Gnome? (Also I kinda figured the issue was mostly with the fact that I run on a Wi-Fi connection)[/QUOTE]

And just for your, and everyone elses, enjoyment I wrote a guide some time ago:

[http://ubuntuforums.org/showthread.php?t=100738](http://ubuntuforums.org/showthread.php?t=100738)

---

### Post by prizrak on 2005-12-12
[QUOTE=Lovechild]And just for your, and everyone elses, enjoyment I wrote a guide some time ago:

[http://ubuntuforums.org/showthread.php?t=100738](http://ubuntuforums.org/showthread.php?t=100738)[/QUOTE]
THX, filed :)

---

