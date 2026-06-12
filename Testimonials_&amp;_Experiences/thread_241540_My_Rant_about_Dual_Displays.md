---
title: "My Rant about Dual Displays"
date: 2006-08-22
forum: Testimonials &amp; Experiences
---

### Post by kpurcell on 2006-08-22
Let me start by saying that I've been a long time Windows user and have recently switched, first trying Ubuntu 5 then 6 and then I went to a couple of other distros before coming back to Ubuntu (but using KDE cuz I like it better).

I recently found the powers of Linux over windows when I was struggling with downloading a driver in Windows and then on a whim rebooted to Linux and it came down the pipe with no problems.  Since that day I have not looked back, reformatting and totally removing windows from my day to day PC.

HOWEVER, ....

I use a laptop that is sometimes not connected to an external display (at home) and sometimes I want to connect it to an external display (at work).  This makes my work so much easier.  And sometimes I use this laptop for presentations.  Have to connect to a projector via the USB port (its the only cable we have wired to where I can connect).

Dangit!  I cannot get this thing to work.  I was close today.  Finally I could see stuff on both screens.  But why the heck does Linux think that when I have a CRT connected I want that to be the default display.  I could not get it to change.  I'm in KDE so I went to display in System settings and told it that the first display was my laptop with the manufacturer name and everything.  I then told it what my external CRT is on display 2.  It still assusme the CRT is the 1st.  I switched em so the CRT is configure as 1 with the right resolution and the laptop is configure as 2 with the right resolution.  It still thinks the CRT is the laptop display and  .....

YOu get the idea.

Why does this have to be so hard.  In windows I right click the desktop.  Tell it to extend to my external display hit apply and joila!  I'm good to go.  The first time I had to do a little tweaking to get the resolutions the way I wanted, but from then on it just works.

Why can't we get this functionality in Linux?  Surely some great programmer out there has used a laptop to connect to an external display and knows how to do this.  Come on!!!

Sorry for my rant.

Other than this I'm very pleased and have learned a lot.  But this one feature is very important to me and I'm not sure I want to have to do do my work on a single display when I know I can do it in Windows, albeit slower, with more security holes, and with expensive software.

Thanks for listening and please don't flame me.  Just needed to get this off my chest.  And yes I've read so many howtos that I'm going berzerk.

---

### Post by DoctorMO on 2006-08-22
As far as I know, Linux has some issues with display detection it's currently built into the xorg server in a rather fundermental way. this can be seen by the way xwindows only reports the first monitor to any discovery programs trying to find out what your using.

It's all ugly too, to be honest it needs work. a situation which is only made worse because the graphics card drivers which exist for xorg must be made to work with things like DDB and allow correct detection. and some of them don't or the monitors don't support any form of detection. I'd say the industry is a in a bit of a mess too.

I just hope that things improve and the xorg team start making things with duel, laptop and complex displays in mind (although it's dificult because xwindows protocalls where designed to work over networks too, unlike windows gui which can't make very good thin clients)

---

### Post by reacocard on 2006-08-22
The current Xorg just doesn't allow much config during runtime. If you set everything up in your xorg.conf it should work very well though, at least for the CRT. This is one of the biggest weaknesses of the current xorg, and one i would love to see abolished, being a laptop user as well.

---

### Post by daou on 2006-08-24
There are issues with CRT defaulting to primary display. Especially with the nVidia drivers (I don't have experience with the ATI drivers).

The issue has been talked about in [this thread]("http://www.nvnews.net/vbulletin/showthread.php?t=54638") for a while now.

I found a way around it with Xinerama. Right now I'm running with a CRT and an LCD, LCD forced to primary.

---

