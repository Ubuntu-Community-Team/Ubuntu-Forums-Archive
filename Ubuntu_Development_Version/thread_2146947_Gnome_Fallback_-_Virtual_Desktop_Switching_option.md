---
title: "Gnome Fallback - Virtual Desktop Switching option?"
date: 2013-05-20
forum: Ubuntu Development Version
---

### Post by epikvision on 2013-05-20
I'm on gnome-fallback mode just to get more synapse-oriented (giving myself a break from unity), and what bothered me is the apparent lack of a  desktop switcher or some shortcut to do it.  I only have one box at the bottom-right corner, not the typical 4 boxes for desktop switching.  

I am also unaware of a keyboard shortcut that would allow me to move around.  Just as, in Unity, Super+S brings up the virtual screens and Ctrl+Alt+<Arrow Keys> moves between the screens, is there a similar way to do this in Gnome-Fallback?

Why is gnome-fallback called the way it is?  Why can't it be gnome-classic?

---

### Post by grahammechanical on 2013-05-20
It is called Fall-back because that is what is it, a fall back mode which the OS falls back to for computers that do not have the hardware to run Gnome shell in 3D mode. In Ubuntu 12.04 the fall back mode is Unity 2D. But in 12.10 and later Ubuntu uses something called llvmpipe to give a 3D session. This means that there is no fall back mode in Ubuntu any more and this is true also for Gnome 3 Shell. Which is why Gnome developers are no longer supporting the fall back mode.

[http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html](http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html)

The way to get something of look of Gnome Fall-back but not necessarily the functionality is through Gnome Extensions.

[http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html](http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html)


Regards.

---

### Post by zika on 2013-05-20
> **grahammechanical said:**
> It is called Fall-back because that is what is it, a fall back mode which the OS falls back to for computers that do not have the hardware to run Gnome shell in 3D mode. In Ubuntu 12.04 the fall back mode is Unity 2D. But in 12.10 and later Ubuntu uses something called llvmpipe to give a 3D session. This means that there is no fall back mode in Ubuntu any more and this is true also for Gnome 3 Shell. Which is why Gnome developers are no longer supporting the fall back mode.

[http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html](http://www.webupd8.org/2012/11/fallback-mode-classic-session-to-be.html)

The way to get something of look of Gnome Fall-back but not necessarily the functionality is through Gnome Extensions.

[http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html](http://www.webupd8.org/2013/02/a-quick-look-at-new-gnome-classic.html)


Regards.
I'm very happy with gnome-session-fallback (no effects) from 3.8...

---

### Post by jbicha on 2013-05-20
> **epikvision said:**
> 
Why is gnome-fallback called the way it is?  Why can't it be gnome-classic?

The developers that made it called it GNOME Fallback. Now that those developers have created something new in GNOME 3.8 called GNOME Classic, we can't use that name anymore.

Anyway, new developers are involved with Fallback and it will probably be renamed Flashback soon: [https://live.gnome.org/GnomeFlashback](https://live.gnome.org/GnomeFlashback)

---

### Post by pfeiffep on 2013-05-20
> **epikvision said:**
> I'm on gnome-fallback mode just to get more synapse-oriented (giving myself a break from unity), and what bothered me is the apparent lack of a  desktop switcher or some shortcut to do it.  I only have one box at the bottom-right corner, not the typical 4 boxes for desktop switching.  

I am also unaware of a keyboard shortcut that would allow me to move around.  Just as, in Unity, Super+S brings up the virtual screens and Ctrl+Alt+<Arrow Keys> moves between the screens, is there a similar way to do this in Gnome-Fallback?

Why is gnome-fallback called the way it is?  Why can't it be gnome-classic?
I'm not certain that my reply addresses your queries.....
I started using Ubuntu (12.10) on an ancient laptop that was unable to effectively support unity because it was extremely sluggish. I installed gnome session fall back and was pretty happy with the responsiveness and functionality. 

When I moved onto my more modern computer I simply duplicated the experience but on a much faster 64 bit machine. When I tried Unity I discovered that it ran perfectly on my HP tower, but I really didn't prefer the functionality (or at least my perception). I have since installed the cinnamon add on to Ubuntu 13.04 and found that I like it's presentation and functionality just great.

Cinnamon for Raring is available in the software center - I have no knowledge concerning availability for previous versions ... I did try in for Saucy (13.10) and it didn't work. I'm not too concerned because Saucy is development for now.

---

### Post by epikvision on 2013-05-20
Ok, so far, I would like to know how I can have 4 virtual desktop options.  I'm just limited to one.  

[http://imgur.com/eWfNYbY](http://imgur.com/eWfNYbY)

---

### Post by kuvanito on 2013-05-20
> **epikvision said:**
> Ok, so far, I would like to know how I can have 4 virtual desktop options.  I'm just limited to one.  

[http://imgur.com/eWfNYbY](http://imgur.com/eWfNYbY)

How did you install fallback?
I did a sudo apt-get install gnome-session-fallback
then at my login I choose fallback (no effect) and that gives 4 virtual desktops not just one

---

### Post by epikvision on 2013-05-20
> **kuvanito said:**
> How did you install fallback?
I did a sudo apt-get install gnome-session-fallback
then at my login I choose fallback (no effect) and that gives 4 virtual desktops not just one

It was available by default.  Perhaps, this is a bug?

---

### Post by Buntu Bunny on 2013-05-21
In Precise I have what's labelled, Gnome Classic (no effects). If I right click the workspace changer on the panel, it gives me preferences which allow me to set the number of virtual desktops. You cannot do that?

---

### Post by epikvision on 2013-05-22
> **Buntu Bunny said:**
> In Precise I have what's labelled, Gnome Classic (no effects). If I right click the workspace changer on the panel, it gives me preferences which allow me to set the number of virtual desktops. You cannot do that?

Checking out gnome-fallback (no effects), I noticed it comes with 4 virtual desktops by default. On gnome-fallback, I had to right-click the workspace changer for more virtual desktops. At least it worked. :-)  Now, I'm free to use synapse without unity. Thanks!

Now, the question is how can I switch between the virtual desktops exclusively with the keyboard. Super+S does something bizarre, and Super+Control+Left, Right won't take me switch me around as it would in Unity.

---

### Post by zika on 2013-05-22
> **epikvision said:**
> Checking out gnome-fallback (no effects), I noticed it comes with 4 virtual desktops by default. On gnome-fallback, I had to right-click the workspace changer for more virtual desktops. At least it worked. :-)  Now, I'm free to use synapse without unity. Thanks!

Now, the question is how can I switch between the virtual desktops exclusively with the keyboard. Super+S does something bizarre, and Super+Control+Left, Right won't take me switch me around as it would in Unity.Ctrl-RAlt+{<- or ->}... ?

---

### Post by Buntu Bunny on 2013-05-22
> **epikvision said:**
> Now, the question is how can I switch between the virtual desktops exclusively with the keyboard.

Zika is correct. ALT+CTRL+arrow key. 

I was going to suggest too, that you try Xfce for the fun of it. It's as comfortable to use as the old Gnome desktop,plus, it's still supported!:p

---

### Post by epikvision on 2013-05-22
> **Buntu Bunny said:**
> Zika is correct. ALT+CTRL+arrow key. 

I was going to suggest too, that you try Xfce for the fun of it. It's as comfortable to use as the old Gnome desktop,plus, it's still supported!:p
Nope, alt+control+arrow key doesn't work.  I think this is a bug.

So, just to clarify, Gnome Fallback is no longer supported?

---

### Post by epikvision on 2013-05-22
Come to think of it, gnome fallback [not gnome fallback (no effects)] is quite buggy. I have no problems with desktop switching in Gnome Fallback.

---

### Post by Buntu Bunny on 2013-05-22
> **epikvision said:**
> So, just to clarify, Gnome Fallback is no longer supported?

They dropped Fallback support with the release of Gnome 3.8. Details [here]("http://ubuntulook.com/2012/11/08/fallback-mode-classic-session-to-be-dropped-from-gnome-3-8/")

---

### Post by epikvision on 2013-05-23
> **Buntu Bunny said:**
> They dropped Fallback support with the release of Gnome 3.8. Details [here]("http://ubuntulook.com/2012/11/08/fallback-mode-classic-session-to-be-dropped-from-gnome-3-8/")

I'll consider trying out xubuntu, but what's the closest desktop environment to Gnome Fallback?  The more minimal, the better.

---

### Post by Buntu Bunny on 2013-05-23
> **epikvision said:**
> I'll consider trying out xubuntu, but what's the closest desktop environment to Gnome Fallback?  The more minimal, the better.

I would say Xfce, which is the desktop that comes with Xubuntu. To me, it's about as close to Gnome Fallback as you can get. For screenshots and more information, you can check out the [Xubuntu website]("http://xubuntu.org/screenshots/"). You can download and install just the Xfce desktop from [Xfce.org]("http://www.xfce.org/").  You'll get the choice of an Xfce or Xubuntu session at login.

---

### Post by ibjsb4 on 2013-05-23
> **Buntu Bunny said:**
> They dropped Fallback support with the release of Gnome 3.8. Details [here]("http://ubuntulook.com/2012/11/08/fallback-mode-classic-session-to-be-dropped-from-gnome-3-8/")

I asked this question in the 13.10 forum and gnome fallback (or classic, whatever you want to call it) is still there.  I been hearing the story of classic being dropped since classic came out :)

---

### Post by ibjsb4 on 2013-05-23
Wait a minute, this is ubuntu +1 .. Duhhhh :)

---

