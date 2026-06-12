---
title: "Couple of annoying (minor) Virtualbox problems"
date: 2008-02-05
forum: Virtualisation
---

### Post by ssc351 on 2008-02-05
Hi everyone,

I have 2 annoying problems with running virtualbox seamless 1.5.4.

First of all, copy and paste does this "ŸŸ"  so if I am in ubuntu or my VM, I can't use the ctrl+C to copy nor the ctrl+V to paste because this is what happens.

Next,

The seamless function in VB is slightly annoying, if I hit the "show desktop" icon in my Windows VB, it brings up the windows desktop and my Ubuntu desktop disappears, I can get it back by simply mousing over to the top of the screen and clicking.  
Secondly, every now and then the seamless VB will just turn black on the desktop.  In other words, my desktop background goes from a picture to a black page.

See the attached screenshots of the desktop.

---

### Post by ssc351 on 2008-02-11
bump

---

### Post by fjgaude on 2008-02-11
VMware server, the free one, permits copy and paste both ways. It doesn't have seamless desktop, but close to it.

Each VM have their features. I do believe that VMware is more stable.

---

### Post by H_out on 2008-03-02
> First of all, copy and paste does this "ŸŸ" so if I am in ubuntu or my VM, I can't use the ctrl+C to copy nor the ctrl+V to paste because this is what happens.

I used to have this problem, too.  I'm running Xubuntu 7.10.  I got rid of the problem by enabling a clipboard manager.  "ClipMan" runs in my xfce panel and manages everything I copy-paste.  I can paste between Xubuntu and my virtual machine without any problems.  I think Ubuntu has some simple clipboard managers in the repository you could try.  Or check the Gnome panel options for a clipboard manager item you can add. Also, make sure your clipboard function (in settings for your virtual machine) is set to bi-directional.

> The seamless function in VB is slightly annoying, if I hit the "show desktop" icon in my Windows VB, it brings up the windows desktop and my Ubuntu desktop disappears, I can get it back by simply mousing over to the top of the screen and clicking.
Secondly, every now and then the seamless VB will just turn black on the desktop. In other words, my desktop background goes from a picture to a black page.

Seamless mode has a weird requirement of needing atleast 1 window open (non-minimized) in virtual Windows in order to work properly.  That's why when you show desktop (in other words, minimize all), your VB blacks out.  What I suggest is installing a simple program...maybe some kind of clock that's always running in your virtual Windows that stays on your desktop and is hidden from your taskbar.  That way, you'll always have a window open in your virtual Windows.  I personally don't run seamless, so I can't suggest a specific program, sorry.

Hope these suggestions work!

---

### Post by Sasa Sijak on 2008-03-02
I have that copy/paste problem too. Anybody have a solution to this in Ubuntu? It is very annoying!

---

### Post by H_out on 2008-03-02
> I have that copy/paste problem too. Anybody have a solution to this in Ubuntu? It is very annoying!

...did you already try a clipboard manager?  For Gnome users, there is "glipper", available in the repository.

---

