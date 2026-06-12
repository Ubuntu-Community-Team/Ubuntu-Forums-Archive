---
title: "Viruses Suck"
date: 2007-07-24
forum: The Cafe
---

### Post by swoll1980 on 2007-07-24
Viruses Suck :mad:

---

### Post by Al3xK3aton on 2007-07-24
People who manage to get a virus while using Linux suck. People who manage to get a virus while using a live-CD double-suck.

---

### Post by starcraft.man on 2007-07-24
Ummm, is this "viruses suck" thing a revelation you just made? I don't see why this is in the forum. Did you get one on Ubuntu (I ask, but I doubt it)? Anyway, if you want help say more about your problem.

---

### Post by myoungf1 on 2007-07-24
> **starcraft.man said:**
> Ummm, is this "viruses suck" thing a revelation you just made? I don't see why this is in the forum. Did you get one on Ubuntu (I ask, but I doubt it)? Anyway, if you want help say more about your problem.

I totally agree with this.  I have never had a virus or malware or spyware with using Ubuntu but if you have been unlucky please use the forums to explain your problem so we can help and also learn from your experience.

---

### Post by Al3xK3aton on 2007-07-24
Advice: Don't use Wine, it just makes you susceptible to Windows viruses.

---

### Post by %hMa@?b&lt;C on 2007-07-24
this does not belong in absolute beginner talk.  would a mod please move to community cafe or something.

---

### Post by swoll1980 on 2007-07-24
evertime i boot on to ubuntu it opens a bunch of browers they all go to this web address [http://blog.myspace.com/lane97](http://blog.myspace.com/lane97)  and they just keep opening I have to hard stop it there is no way to fix this because all my resources are sucked up and computer freezes

---

### Post by swoll1980 on 2007-07-24
also the ubuntu is running in a virtualbox on xp i don't know if that makes a difference. i just tried to go into the terminal before i logged on and did command "sudo aptitude remove firefox " (figureing if I had no firefox id be able to figure this out but it told me I have no permission

---

### Post by asmoore82 on 2007-07-24
Wow, yea... WINE should be a tool for a few laughs ... not a way of life.

a quick fix would be to give wine a blank slate while saving your old wine stuff ...

```
~ $ mv .wine .fubar-wine
```
in a failsafe term.

---

### Post by starcraft.man on 2007-07-24
> **swoll1980 said:**
> evertime i boot on to ubuntu it opens a bunch of browers they all go to this web address [http://blog.myspace.com/lane97](http://blog.myspace.com/lane97)  and they just keep opening I have to hard stop it there is no way to fix this because all my resources are sucked up and computer freezes

I've never heard of this particular problem. The first thing that pops to mind is some sort of browser exploit through Firefox hit you and is now doing this (this didn't likely target Ubuntu at all and simply co-opted your browser by targeting a Firefox vulnerability). Since you can't do anything except reset my advice is to restore a snapshot (if you took one with the VM, most support this feature.) In the event you don't have a snapshot, reinstall Ubuntu into the VM from scratch. Those are the two easy options that require the least effort and are full proof.

If you don't mind the terminal, then try the following. Reboot the vm and push escape when it says its loading to get to GRUB, choose to boot into recovery mode (second option).  You will log in as root on the terminal, then issue this command:

```
sudo aptitude purge firefox
```
This will dump firefox in entirety. Then reinstall with:

```
sudo aptitude install firefox
```

If that fails, reinstall the VM (like I said before), it is the easiest way to a clean install. When you get back into Ubuntu, install [no script]("https://addons.mozilla.org/en-US/firefox/addon/722"). It is a snap to filter that will prevent 99% of exploits that take advantage of javascript to execute, it also blocks most XSS (Cross Site Scripting). Ad block plus is also useful, not as important but has its uses in protection.

That should do it. Hope that helps.

---

### Post by bodhi.zazen on 2007-07-24
> **Al3xK3aton said:**
> Advice: Don't use Wine, it just makes you susceptible to Windows viruses.

That is FUD

[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

---

### Post by starcraft.man on 2007-07-25
> **bodhi.zazen said:**
> That is FUD

[http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss](http://os.newsforge.com/article.pl?sid=05/01/25/1430222&from=rss)

Oi, I mised that one, good save bodhi.

---

### Post by swoll1980 on 2007-07-25
that worked good thanks.

---

### Post by lisati on 2007-07-25
"your computer is no longer stoned"

---

