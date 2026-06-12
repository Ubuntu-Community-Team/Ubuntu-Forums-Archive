---
title: "keep xfce and remove Gnome for my wife - how to do safely?"
date: 2014-11-08
forum: Ubuntu Studio
---

### Post by DVD-R on 2014-11-08
Hi All,
I'm setting up Studio based on 12.04 repositories, and I've got the xfce desktop the way my wife likes it.
But tonight I accidentally rebooted into Gnome and it took an hours worth of fiddling to get back into xfce.
It kept wanting to automatically startup in Gnome even though I selected Studio.
My wife will be using this and I don't want to freak her out with that happening to her.
Need to remove Gnome so that only xfce desktop is the only option.

Any suggestions on how to remove Gnome safely?
perhaps there is a thread with this topic already... you could point me too?
I couldn't find one by searching.
Thanks!

---

### Post by TheFu on 2014-11-09
Xfce is based on Gnome2, isn't it?
DEs are installed per system, not per userid.

On the login screen, click the gear, select the DE you/she wants. The last selected will be used next login. 

I hope it is this easy, but don't know that I understand the real issue.

---

### Post by oldrocker99 on 2014-11-09
If you're looking for a lightweight desktop, may I recommend MATE. It's a desktop that is a fork of GNOME 2.3, which was the much-missed default on Ubuntu back a few years ago:[http://wiki.mate-desktop.org/download](http://wiki.mate-desktop.org/download). I find it more full-featured than XFCE (as much as I like that little mouse), and pretty damn lightweight. I've been using it since Mint 12, whn it was first released, but I came back to Ubuntu, finding Mint to be annoying to me. If you want to, there's a Ubuntu MATE distro, [url]https://ubuntu-mate.org/download/[/b] which is not quite yet official, but likely, and available. It doesn't include all the multimedia apps of Ubuntu  Studio, of course, but all those apps are in the Ubuntu repositories.

And, by the way, it's pronounced MAH-tay, not Mayte, or especially not mah-TAY. It is named after the Argentinian caffeinated herb, the way Java is named after the caffeinated coffe bean.;)

---

### Post by DVD-R on 2014-11-10
Thanks for the responses.
Got the desktop she wants and she's just moving over to Linux so I need to make it easy for her.
Got XFCE all setup  for her just the way she likes it.
Only problem is there are other desktops installed.
If she accidentally boots up into another desktop she will just get frustrated trying to get back to XFCE.
I know I'm going to have to un-install the other desktops in the system.
Just thought someone would already dealt with this and might give some advice on how to go about removing the other desktops without taking out too much.

I may just have to start removing stuff and I guess I can always re-install in terminal mode if I remove too much.

---

### Post by DVD-R on 2014-11-10
Ok.... I got it.
I removed gnome-shell and gnome-fallback
Now the desktop options for gnome classic and gnome 2D are gone.
Cookin with GAS!!!!  :-]

---

### Post by pizzalover1974 on 2014-11-15
Look in Ubuntu software centre..find GNOME that was installed...click UNINSTALL button. Restart PC.

---

