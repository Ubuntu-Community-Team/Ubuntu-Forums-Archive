---
title: "The Three Best Linux Media Centers"
date: 2009-06-07
forum: The Cafe
---

### Post by jdeslip on 2009-06-07
I thought ubuntuforums folks might like this article.  (Also hopefully this is not a double post / as I accidentally posted in howto section which is held and should be rejected)

Original Article (With Pics): [http://www.berkeleylug.com/?p=204](http://www.berkeleylug.com/?p=204)
Digg it: [http://digg.com/linux_unix/The_Three_Best_Linux_Media_Centers](http://digg.com/linux_unix/The_Three_Best_Linux_Media_Centers)



Let me first start off by saying that someone is likely going to be very angry at me for omitting program x, y, z or Miro. Please express that anger in the comments below. The three media centers I list are my favorites. All of them integrate easily with MythTV by adding a simple menu item, and each work greats with remotes and looks good on your TV. MythTV itself might qualify in this category. However, I find Myth makes a good OS (mythbuntu) and PVR (with a great web interface), but I think it is fairly awful at organizing your media and playing web vids. So, I leave it out of the media center category. I personally run a Mythbuntu system with the following three media centers installed on top of MythTV to organize my local media and watch web content.

XBMC

xbmc

This media center was designed for the original XBox hardware. However, it has since been ported to Linux, Apple and Windows (and other game systems). It has an extremely beautiful interface.  XBMC indexes the music and videos on your hard drive or networked drives and plays them back with a lot of elegance. It is easy to configure your remote control and video playback utilizes VDPAU on nvidia cards. So, you get amazing performance during playback (HD video uses less than 10% of your CPU). Beyond playing back your media, XBMC has a ton of plugins ([http://www.xbmczone.com/](http://www.xbmczone.com/)) that let you play online content like streaming video (ex. CBS), podcasts (ex. The Onion, Game Trailers), grab subtitles for movies etc&#8230; It has a MythTV frontend plugin which is great if you have a MythTV backend somewhere on your network like me &#8211; it is pretty new, though, and I find it a little clunky compared to a real MythTV frontend. The one killer plugin that is missing is a Hulu plugin, though. This is the main reason I spend more time in Boxee.

Benefits:

    * Open Source
    * Beautiful Interface (Though more complex than Boxee)
    * Great Plugins
    * Very Customizable
    * MythTV Frontend
    * DVD/CD Playback

Downsides:

    * No Hulu Plugin
    * Less Intuitive than Boxee

Boxee

boxee

Boxee is media center that was broken off of XBMC. Basically it is XBMC plus a cleaned up interface, a social network and a few more key plugins. While much of Boxee is open source &#8211; these additions are closed source, which prevents XBMC from taking advantage of the Boxee developers work. This is pretty lame of the Boxee team, but they are trying to turn Boxee into a business; so, there you have it. The social network aspect of Boxee lets your friends see what you are watching/listening to and lets you recommend shows or songs to your followers. The main reason to use Boxee over XBMC is the Hulu app based on Mozilla (and a few other apps that are missing in XBMC). It is also generally a bit simpler to use. When I installed it on Ubuntu, my MCE remote immediately worked. Its media indexing system is not very good, however. Your files have to be named in a particular way because it does not read metadata, and even after this, it still fails to index a lot of my music. Apparently metadata indexing is coming in a future release - which should fix the problem. I also don&#8217;t like having to login to my username on each launch and there is no VDPAU playback yet.  Overall, though, I spend more time in Boxee than either of the other two examples because it is clean and the plugins are awesome.

Benefits:

    * Based on XBMC code &#8211; (So improvements there should eventually come to Boxee)
    * Beautiful Easy Interface
    * Great Plugins Capability
    * Hulu Plugin in Particular
    * DVD/CD Playback

Downsides:

    * Not Very Customizable
    * No MythFrontend
    * Indexing Sucks
    * Closed Source Chunks
    * No VDPAU (Yet)

Moovida

main_moviesalt

Moovida is an open-source media center from Fluendo the makers of the legal Linux gstreamer codecs. The interface is once again extremely beautiful and it works great with remotes once you get it working. However, I initially had trouble setting my MCE remote up.  The indexing system on Moovida is the best of the three media centers on this list. So, if you just want to play back local media, this is probably your best choice. While there is a plugin system, only a few plugins have been written so far. And, there is currently no Mozilla or Hulu integration. I really haven&#8217;t used Moovida as much as XBMC or Boxee, but I am going to keep a close on eye on its development over the next little while to see if it gets more impressive addons.

Benefits:

    * OpenSource
    * Supported by a great company
    * Beautiful Interface
    * Best Media Indexer

Downsides:

    * No DVD Player (At least I couldn&#8217;t find it)
    * Not Very Many Plugins Yet
    * No Hulu Plugin in Particular

And there you have it.  Try them out and set up a great media center.

---

### Post by Troublegum on 2009-06-15
Hi jdeslip,


great post. I've tried xbmc and moovida over the weekend. What kept me from trying boxee is the need to register an account. 


I've got some points to add:

[LIST]
[*]moovida does have a dvd player, it is well hidden. 
Go to devices & shares -> attached devices -> dvd
[*]xbmc lets you choose the webservice it uses to retrieve information about your movies. I have a lot of german movies, and I named the files using the german titles. So I told xbmc to use "filmstarts.de" as webservice. That way I get the information in german, too.
[*]the xbmc interface requires a lot of clicks on the remote to get you where you want. Moovida's interface is much cleaner. However, I think the font size in moovida is too small. I had a hard time reading the menus from 3 or 4 metres away.
[*]Another great plus about xbmc is that it supports lcdproc/LCDd to display information on an LCD display. My pc-case has a built-in vfd-display (two lines with 16 digits each). When navigating through the menu, xbmc displays where I am and what's selected. When playing media, xbmc displays the media title and the playback time. So it is possible to select and play music without turning on your monitor. That's great. :)
[/LIST]

Can you tell a little bit more about boxee? Maybe make some screenshots? Do you know if it can use lcdproc/LCDd?

---

### Post by LADmaticCA on 2009-06-15
^^ I saw this video yesterday. It provides some good pluses and minuses between xbmc and boxee:  [http://www.youtube.com/watch?v=r1JwI0dhpAg](http://www.youtube.com/watch?v=r1JwI0dhpAg)

---

### Post by Sef on 2009-06-16
Moved to community cafe.

---

### Post by Sublime Porte on 2009-06-16
No Geexbox?

---

### Post by OliW on 2009-06-24
Boxee supports VDPAU now.

While I really like it, I really hope they make it interface with MythTV soon.

---

### Post by NightwishFan on 2009-06-24
I like Elisa, however it seems to be less complete then the others.

---

### Post by .Maleficus. on 2009-06-24
> **NightwishFan said:**
> I like Elisa, however it seems to be less complete then the others.
Elisa is now known as Moovida.  [http://www.moovida.com/](http://www.moovida.com/)


Edit:  Pretty nice post OP, my only recommendation would be to put links (to the projects) in it.

---

### Post by Maheriano on 2009-06-24
What's the easiest way to install XBMC on my machine?

---

### Post by NightwishFan on 2009-06-24
Oh wow, did not know that, thanks. :D

---

### Post by geoken on 2009-06-24
Is there a central repository for XBMC themes? I always wanted to try it but I don't like the default theme and I have never been able to find a place where I can browse through other themes.

---

### Post by Sealbhach on 2009-06-24
Boxee still haven't done a 64-bit version. :mad:

.

---

### Post by praveesh on 2009-06-24
What a hulu plugin is? What is it's use?

---

### Post by jdeslip on 2009-06-24
Ya, Boxee just released a new version yesterday.  Nice upgrade it seems.  MLB.TV plugin now too.

---

### Post by Maheriano on 2009-06-24
> **praveesh said:**
> What a hulu plugin is? What is it's use?
If you go to [www.hulu.com](www.hulu.com) and are living in the USA, it lets you watch lots of user-submitted videos online. You can watch movies, television shows, all kinds of things. It's like YouTube for commercial content. The plugin lets you watch it all from the application's interface.
Unfortunately they check the IP before the page loads so if you're in Canada it doesn't work.

---

### Post by praveesh on 2009-06-24
> **Maheriano said:**
> If you go to [www.hulu.com](www.hulu.com) and are living in the USA, it lets you watch lots of user-submitted videos online. You can watch movies, television shows, all kinds of things. It's like YouTube for commercial content. The plugin lets you watch it all from the application's interface.
Unfortunately they check the IP before the page loads so if you're in Canada it doesn't work.

OK understood

---

