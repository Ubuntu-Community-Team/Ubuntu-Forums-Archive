---
title: "Server with minimal gui"
date: 2012-05-21
forum: Server Platforms
---

### Post by Nick_C on 2012-05-21
What is the preferred method of getting a basic but functional gui on Ubuntu Desktop?  Trying to avoid the normal desktop bloat and just have the sort of components that you would normally expect to use on a server.

Hopefully not starting automatically but something that can be run with startx when it is required.

Does Xubuntu desktop selection from tasksel just install a simple  Xfce desktop without all the additional crap and bloat?

Thanks,
  Nick

---

### Post by roelforg on 2012-05-21
Ubuntu Server + lxde
Got it to work smooth in under 256mb ram on a p2

---

### Post by Nick_C on 2012-05-21
Well I now know one way that doesn't achieve this.  Used tasksel to install xubuntu desktop, which I thought might give us a minimal desktop, unfortunately not it comes with Games and all sorts of associated bloatware.

---

### Post by roelforg on 2012-05-21
> **Nick_C said:**
> Well I now know one way that doesn't achieve this.  Used tasksel to install xubuntu desktop, which I thought might give us a minimal desktop, unfortunately not it comes with Games and all sorts of associated bloatware.

Like i said, start guiless, add a de (lxde is the lightest imo) and go from there.

---

### Post by Nick_C on 2012-05-21
> **roelforg said:**
> Ubuntu Server + lxde
Got it to work smooth in under 256mb ram on a p2

Not too worried about memory footprint, with most modern machines the memory used becomes irrelevant.  Seem to recall that I had tried LXDE before and:
aptitude install lubuntu-desktop
installed all sorts of bloatware again, that is if I have remembered this correctly.

Nick

---

### Post by roelforg on 2012-05-21
> **Nick_C said:**
> Not too worried about memory footprint, with most modern machines the memory used becomes irrelevant.  Seem to recall that I had tried LXDE before and:
aptitude install lubuntu-desktop
installed all sorts of bloatware again, that is if I have remembered this correctly.

Nick

I was thinking in the
sudo apt-get install lxde
on ubuntu server direction

---

### Post by Cheesemill on 2012-05-21
> **Nick_C said:**
> Well I now know one way that doesn't achieve this.  Used tasksel to install xubuntu desktop, which I thought might give us a minimal desktop, unfortunately not it comes with Games and all sorts of associated bloatware.
Yep, you end up with a standard Xubuntu installation. If you just want the Xfce GUI without any of the associated Xubuntu applications then just do:
```
sudo apt-get install xfce
```
not what you have done which is
```
sudo apt-get install xubuntu-desktop
```

---

### Post by mattfrog on 2012-05-21
May I also suggest Openbox or the like if you do prefer a GUI for servers :P

---

### Post by roelforg on 2012-05-21
> **mattfrog said:**
> May I also suggest Openbox or the like if you do prefer a GUI for servers :P

I don't want to nitpick, but isn't openbox only a wm?
I think the op wants a simple and light de.

---

