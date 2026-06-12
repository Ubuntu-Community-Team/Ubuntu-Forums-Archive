---
title: "Ubuntu's Multimedia Capabilities..."
date: 2007-05-05
forum: The Cafe
---

### Post by Mazza558 on 2007-05-05
In my opinion, Ubuntu is pretty mature as far as a work platform, as seen in the other thread "Do you work with Ubuntu". 

I think that Ubuntu's media capabilities out-of-the-box are not quite as mature.

How well did things work out-of-the box for you in terms of media?

---

### Post by runningwithscissors on 2007-05-05
Don't care much for multimedia and not an Ubuntu user.

So, just wasting some database space.

---

### Post by litemotiv on 2007-05-05
i'm missing:

[ ] Yes, watching videos or DvDs worked with a little of effort on my part.

(which is the one i would choose)

---

### Post by igknighted on 2007-05-05
I think that we are adding complexity with this "codec buddy" thing.  What if users have non-gstreamer based apps that they use (like amarok)?  What about the various degrees of legality in various locations?  I think the best solution is what we already had rather than this odd child codec grabber.  It did nothing for me, but I set up stuff the old way and (shockingly) it works fine.  After all, there was always automatix for those who wanted it.  If there was anything that needed to be added all I can think of is a "restricted codecs" metapackage for those who want to blanket install everything common.

---

### Post by gvoima on 2007-05-05
Yeah I agree, keeping things the way they were is better. Ubuntus out-of-the-box multimedia cabapilities are good as long as they are not proprietary codecs.

But I still have troubles with DVD menus and Totem, that should be fixed :P
otherwise everything works great with gstreamer with me..

---

### Post by igknighted on 2007-05-05
> **gvoima said:**
> Yeah I agree, keeping things the way they were is better. Ubuntus out-of-the-box multimedia cabapilities are good as long as they are not proprietary codecs.

But I still have troubles with DVD menus and Totem, that should be fixed :P
otherwise everything works great with gstreamer with me..

Well, I think you mean to say that totem should be axed, it's such a PITA... Mplayer should be the default for videos, it is much better.  Either that or Gxine (or VLC)

---

### Post by starcraft.man on 2007-05-05
I never had any trouble with Ubuntu's multimedia, i made sure to install all the codecs I needed manually :)

---

### Post by AndyCooll on 2007-05-05
I disagree with nearly everything that has been posted so far. I like Totem, and I like codec-buddy and think it's a good idea.

For the newbie codec-buddy helps them quickly get up and running. This is the group of users the app is aimed at, and this group of users are more than likely going to use the default media apps initially too. From my own experience I know that newbies are grateful for any help they can get, this is why EasyUbuntu and Automatix have been so successful.

In a perfect world we wouldn't have need for proprietary codecs. However the reality is that for the vast majority of Ubuntu users, this isn't a perfect world. And indeed for many newbies they're not interested in whether the codec is proprietary or not.

You personally may want to argue for a different default media player, but you ain't ever going to get mplayer Gxine, VLC or whatever until they _don't_ come with proprietary codecs ...and then of course newbies will want codec-buddy for that app!

Most users who have moved to Amarok have moved beyond the basics (for whom codec-buddy is aimed at) and will now now know how to install additional software, i.e as it was before. So Ubuntu has lost nothing but gained an extra help tool if you want it.

Codec-buddy doesn't simply install the codec without any user interaction. When you install a codec with codec-buddy there is a great big warning informing you that you need to consider the legality of installing the codec. You have to click on this and accept (or not). Of course with the old method there's no such warning (other than knowing it in your head).

I use Amarok and Totem and install all codecs myself, I prefer it that way. However, I remember when I first started out and how grateful I was for Automatix helping me to get up and running. 

Apps like this enable newbies to overcome one extra hurdle in coming to appreciate Ubuntu. While the rest of us can stick with our tried and trusted methods. We need to get off our Ivory Towers for a few moments and think of users who don't yet have the knowledge we have gained.

:cool:

---

### Post by deadguy87 on 2007-05-09
Till i read about the need to install the restrictive package I was dumb founded. It didn't take much work though. I just hope that dell included the documentation to enable most media playback with Ubuntu-Dell computers or that will just be a lost cause

---

### Post by jiminycricket on 2007-05-09
> **igknighted said:**
> I think that we are adding complexity with this "codec buddy" thing.  What if users have non-gstreamer based apps that they use (like amarok)?  What about the various degrees of legality in various locations?  I think the best solution is what we already had rather than this odd child codec grabber.  It did nothing for me, but I set up stuff the old way and (shockingly) it works fine.  After all, there was always automatix for those who wanted it.  If there was anything that needed to be added all I can think of is a "restricted codecs" metapackage for those who want to blanket install everything common.

I think Amarok has an option to use gstreamer.

---

### Post by ceelo on 2007-05-09
No formats that I use worked, but all I did was install totem-xine, libxine-extracodecs and libdvdcss and I was good to go. :D

I found xine easier to set up than gstreamer, personally.

---

