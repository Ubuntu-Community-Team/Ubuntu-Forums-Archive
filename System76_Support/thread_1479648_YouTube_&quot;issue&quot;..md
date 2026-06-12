---
title: "YouTube &quot;issue&quot;."
date: 2010-05-10
forum: System76 Support
---

### Post by juelze on 2010-05-10
So, I've had this happen a few times and just wondering if it's a limitation of Ubuntu.  Take this link for example:

[http://www.autoblog.com/2010/05/10/video-motor-trend-pits-lexus-lfa-against-nissan-gt-r-in/#continued](http://www.autoblog.com/2010/05/10/video-motor-trend-pits-lexus-lfa-against-nissan-gt-r-in/#continued)

I can't play the embedded video on that page, but if I right click on it and choose "Play in YouTube" I can play it just fine.  Is there a reason why I can't play the video from that page?

-Juelze

---

### Post by robtg on 2010-05-10
Juelze: The YouTube video plays fine for me.  What happens when you click on the "play" arrow on the video?

-Rob

---

### Post by mcallenSchmee on 2010-05-10
Can you play the video by hitting the space bar or using tab to select the play button?

---

### Post by juelze on 2010-05-11
I didn't try hitting tab or spacebar, but when I click on the play arrow on top of the video, or the play button on the the bottom tool bar (underneath the video) nothing happens.

---

### Post by mcallenSchmee on 2010-05-11
I think that might be [this bug]("https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407") where flash does not detect mouse clicks. The third workaround on that page worked for me.

---

### Post by juelze on 2010-05-11
> **mcallenSchmee said:**
> I think that might be [this bug]("https://bugs.edge.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407") where flash does not detect mouse clicks. The third workaround on that page worked for me.

Are you referring to this workaround?

"WORKAROUND 3: Open a terminal and enter:
$ gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
Then add: export GDK_NATIVE_WINDOWS=1 before the last line of text"

---

### Post by mcallenSchmee on 2010-05-11
Yes. Flash couldn't detect mouse clicks randomly on some videos(but I could play videos using the space bar or using tab to select the play button). Adding that line to the text file solved the problem for me.

---

### Post by juelze on 2010-05-11
One thing I forgot to mention is I'm running 10.04 64bit (Meerkat Ion) so I'm not sure if that makes a difference or not.  Thanks again for taking your time to help me though!

---

### Post by robtg on 2010-05-11
Juelze:  I am running Adobe's pre-release 64-bit Flash plug-in for Firefox; maybe that's why it's working for me.  I tried it out of desperation because I had the same problem I think you're having (Flash doesn't detect mouse clicks) on my ISP's web mail portal.   Using the 64-bit plugin fixed that.

Check this out:

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

-Rob

---

### Post by juelze on 2010-05-11
> **robtg said:**
> Juelze:  I am running Adobe's pre-release 64-bit Flash plug-in for Firefox; maybe that's why it's working for me.  I tried it out of desperation because I had the same problem I think you're having (Flash doesn't detect mouse clicks) on my ISP's web mail portal.   Using the 64-bit plugin fixed that.

Check this out:

[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html#install)

-Rob

That fixed it!  Thanks everyone!

---

### Post by isaacullah on 2010-05-17
Hi all,

   I just wanted to pop in on this solved thread to say that I had independently found the same solution to work for me. Indeed, installing the pre-release version of Flash worked like a charm.

Cheers,

Isaac

---

### Post by AmadeusOK on 2010-05-17
I'm also having issues with You Tube. When I click on the full screen button I get the same small but screen but blank. What can I do?

---

### Post by thomasaaron on 2010-05-18
AmadeusOK, did you try the fixes mentioned above?

---

### Post by AmadeusOK on 2010-05-18
I've just installed libflashplayer.so in /usr/lib/mozilla/plugins and also in /usr/lib/firefox/plugins but nothing changes. Fullscreen still doesn't work.

---

### Post by AmadeusOK on 2010-05-18
It took a while but it's finally working. 

:)

---

