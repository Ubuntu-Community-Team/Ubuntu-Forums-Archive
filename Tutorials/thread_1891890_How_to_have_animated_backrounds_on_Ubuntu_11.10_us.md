---
title: "How to have animated backrounds on Ubuntu 11.10 using xwinwrap"
date: 2011-12-06
forum: Tutorials
---

### Post by Firezap on 2011-12-06
I got all of this info scattered from all over the Internet, and one thing is common, its older...So here is how to set it up (with the ability to still see the original desktop, like folders and files..) Doing this will allow you to have live backgrounds. 

Before you start, you should install some cool screen savers, due to the fact we will use them as your background. So run this in terminal:
```
sudo apt-get install xscreensaver xscreensaver-gl-extra xscreensaver-data-extra
```When thats done, we need to get xwinwrap installed. You can get it here:[ http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap]("http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap")
Direct link: [http://tech.shantanugoel.com/resources/downloads/shantz-xwinwrap.zip](http://tech.shantanugoel.com/resources/downloads/shantz-xwinwrap.zip)
Just install the debs files from the zip, easy enough right?:)

Okay, xwinwrap is kinda hard to understand so I got the code for you...

```
xwinwrap -ni -argb -fs -o 0.4 -s -st -sp -b -nf -- /usr/lib/xscreensaver/glsnake -window-id WID -delay 10000
```The -o 0.4 part is the transparency, the lower the number the more transparent. When its set we can see through the screen saver so we can see the desktop still. The part here that says  /usr/lib/xscreensaver/glsnake, is are screen saver file directer. Point it to another path and you will have different backgrounds. You can preview what you have by running the screensaver program we installed earlier.:)
You have to have opengl for this, so if you can not run compiz, this may not be a good idea. I am not responsible if your computer blows up and burns your house down.:lolflag:
Oh, if you want you can save the code as a startup script so you can have it on as soon as you log in as well.:P Hope it works good for you, and spares you the headache I had figuring this out. If the screen saver goes above your window your using, just grab it so it is on top again. Remember, this program is older and not really updated that much...Watch the Youtube video in the sources, it is a great example of what it will look like.


                                                                           Sources:
[http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap](http://tech.shantanugoel.com/projects/linux/shantz-xwinwrap)
[http://www.youtube.com/watch?v=AwbMnKpB3Tc&feature=related](http://www.youtube.com/watch?v=AwbMnKpB3Tc&feature=related)
[http://www.khattam.info/howto-video-wallpaper-on-ubuntu-10-04-lucid-lynx-2010-02-15.html](http://www.khattam.info/howto-video-wallpaper-on-ubuntu-10-04-lucid-lynx-2010-02-15.html)

---

### Post by |Anthony| on 2011-12-21
I wrote a frontend for xwinwrap, but haven't tested it in 11.10 yet. Maybe you could test it for me? It's called [VDesk - Visual Desktop]("http://gnome-look.org/content/show.php/VDesk+-+Visual+Desktop?content=141678") and you can find it at gnome-look.

---

### Post by Firezap on 2011-12-26
Sorry for the late reply, I installed the program and it ran just fine, great job. :P It makes things easier for many people wanting live wallpapers without having to mess around with terminal.

---

### Post by |Anthony| on 2011-12-29
> **Firezap said:**
> Sorry for the late reply, I installed the program and it ran just fine, great job. :P It makes things easier for many people wanting live wallpapers without having to mess around with terminal.
Great! Glad it works in Unity. After I made that comment, I found a post on [noobslab]("http://www.noobslab.com/2011/10/vdesk-animation-wallpapers-for-ubuntu.html") about VDesk on 11.10

---

### Post by vpharry on 2011-12-31
Thanks a lot... will try it out when I am free

---

### Post by dancer_69 on 2012-01-28
Thanks, this is really cool.
And working fine with compiz so far.

---

### Post by Bobhuber on 2012-01-28
You want an animated desktop. Check this out > [http://community.electricsheep.org/](http://community.electricsheep.org/)
Be sure and check out the samples page . 
Install electric sheep along with the other files that firezap listed above then use xwinwrap with this command. 

xwinwrap -ni  -fs -s -st -sp -b -nf -- /usr/lib/xscreensaver/electricsheep -window-id WID 

Works in 11.10 with or without Gnome 3 and all the previous versions of Ubuntu that I have tried. 
Note : This creates a fully animated desktop . Not just a screensaver that electric sheep was originally designed for.

---

### Post by prismctg on 2012-02-01
thnx :)

---

### Post by greggc2006 on 2012-06-24
Just tried it(Vdesk) on 12.04 with Gnome-shell 3.4 and it's working here too.

---

