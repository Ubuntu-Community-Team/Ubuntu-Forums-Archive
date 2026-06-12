---
title: "Who wants to help me with a Launchpad Project?"
date: 2010-05-03
forum: The Cafe
---

### Post by tom.swartz07 on 2010-05-03
Hey guys!

Im just starting out and getting to dig in to Launchpad a lil bit. I have decided to create a project on Launchpad that is dedicated to providing a source for small one off, single purpose scripts to help improve the user experience in Ubuntu.

For example, one script would allow a user to run a daemon in the background that periodically updates their background to a real-time image of the Earth. Another script would allow them to easily install x64 Flash on their computer.


As such, I am not amazingly well versed in the rigors of Launchpad and project management, and I am hoping that I could find a few members that are willing to join in with me in this project!


Please let me know if youre interested, or even if you think its a terrible idea...
Ill provide more information as necessary.

[https://launchpad.net/codemonkey](https://launchpad.net/codemonkey)

---

### Post by Sam on 2010-05-03
> **tom.swartz07 said:**
> For example, one script would allow a user to run a daemon in the background that periodically updates their background to a real-time image of the Earth.

Hey, I made this some years ago... With xplanet. I remember it fetched a satellite image of the clouds (it was updated every couple hours). Also it handled the day/night sides.
So I had a almost perfect view of the earth from space, with day/night sides and clouds in almost real time! ;)

I may have it one some backup somewhere, I'll check later this day.

---

### Post by tom.swartz07 on 2010-05-03
> **Sam said:**
> Hey, I made this some years ago... With xplanet. I remember it fetched a satellite image of the clouds (it was updated every couple hours). Also it handled the day/night sides.
So I had a almost perfect view of the earth from space, with day/night sides and clouds in almost real time! ;)

I may have it one some backup somewhere, I'll check later this day.

Really? I was inspired by a post on OMG!Ubuntu! that featured a view of the earth. The image was grabbed from opentopia.com, I just wrote up a little script that updated it every 5 minutes or so...

Maybe we could compare notes!

---

### Post by Penguin Guy on 2010-05-03
Not sure what kind of scripts you mean, but I've got a whole collection of small bash and python scripts and I'm pretty new to Launchpad as well. I've added you as a friend on Ubuntu Forums and I'll post an archive of my scripts when I get the time. You can find me on Launchpad [here]("https://launchpad.net/~joshbrown").

---

### Post by tom.swartz07 on 2010-05-03
> **Penguin Guy said:**
> Not sure what kind of scripts you mean, but I've got a whole collection of small bash and python scripts and I'm pretty new to Launchpad as well. I've added you as a friend on Ubuntu Forums and I'll post an archive of my scripts when I get the time. You can find me on Launchpad [here]("https://launchpad.net/~joshbrown").

Sweet deal! 2 heads are better than one, I guess!

---

### Post by Sam on 2010-05-03
Ok I found it. You can download the script and the day/night earth images [here](http://www.2shared.com/file/l010zXqw/xplanet.html). Have a look to see how it works, it's quite simple. You need to enhance it a bit, eg set the output directory (now you have to run the script from its directory), etc. You also need to use the output image as background (the script just generate the image). Ask me if you have questions.

Here are some output examples. The clouds are up to date, so you can compare with your local weather website, it should match. ;)

[[IMG]http://img504.imageshack.us/img504/1279/xplanetusa.th.png[/IMG]](http://img504.imageshack.us/img504/1279/xplanetusa.png) [[IMG]http://img709.imageshack.us/img709/8973/xplanetasia.th.png[/IMG]](http://img709.imageshack.us/img709/8973/xplanetasia.png) [[IMG]http://img7.imageshack.us/img7/927/xplanetafrica.th.png[/IMG]](http://img7.imageshack.us/img7/927/xplanetafrica.png)

---

### Post by tom.swartz07 on 2010-05-03
> **Sam said:**
> Ok I found it. You can download the script and the day/night earth images [here](http://www.2shared.com/file/l010zXqw/xplanet.html). Have a look to see how it works, it's quite simple. You need to enhance it a bit, eg set the output directory (now you have to run the script from its directory), etc. You also need to use the output image as background (the script just generate the image). Ask me if you have questions.

Here are some output examples. The clouds are up to date, so you can compare with your local weather website, it should match. ;)

[[IMG]http://img504.imageshack.us/img504/1279/xplanetusa.th.png[/IMG]](http://img504.imageshack.us/img504/1279/xplanetusa.png) [[IMG]http://img709.imageshack.us/img709/8973/xplanetasia.th.png[/IMG]](http://img709.imageshack.us/img709/8973/xplanetasia.png) [[IMG]http://img7.imageshack.us/img7/927/xplanetafrica.th.png[/IMG]](http://img7.imageshack.us/img7/927/xplanetafrica.png)

Wow! thats pretty neat- the version I have posts the image flat (like a map) across the desktop.

This is from a while ago... but its the way that it looks!
[IMG]http://lh5.ggpht.com/_tORug_uHNu4/S2HF281EUFI/AAAAAAAAAM8/YxSg_cmYWP0/s800/Screenshot.png[/IMG]

---

### Post by Sam on 2010-05-03
Using the globe it's possible to render the stars in the background and if the field of view is large enough you may see the moon passing by.

---

### Post by DeadSuperHero on 2010-05-03
It would be cool if there were a way to have one that is actually animated and slowly moves in a fluid motion.

But of course, such things require dirty, dirty hacks.

---

### Post by Penguin Guy on 2010-05-03
Hey, well here are some of my scripts (including, coincidentally, some that work with the background :D). All are written in either Bash or Python.

---

### Post by Sam on 2010-05-03
> **DeadSuperHero said:**
> It would be cool if there were a way to have one that is actually animated and slowly moves in a fluid motion.

But of course, such things require dirty, dirty hacks.

You can actually run some (any?) X application in the background.

You must run metacity (or disable compiz background, I haven't tested it yet):
```
metacity --replace &
```

Disable nautilus' background handling:
```
gconftool-2 --set /apps/nautilus/preferences/show_desktop --type bool false
```

Then run xplanet in the root window:
```
xplanet -vroot
```

It does not have an automatic rotation around the planet. It's probably possible, but I don't know the application enough.


Bonus: to impress your friends run the GL matrix screensaver:
```
/usr/lib/xscreensaver/glmatrix -root
```

---

### Post by Penguin Guy on 2010-05-08
I've just made a group for Launchpad, you can find it [here]("http://ubuntuforums.org/group.php?groupid=771").

EDIT: Looks like there's a new thread [here]("http://ubuntuforums.org/showthread.php?t=1499303").

---

