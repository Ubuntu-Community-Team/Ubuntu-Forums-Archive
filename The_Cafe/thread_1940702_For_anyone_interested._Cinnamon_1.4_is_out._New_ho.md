---
title: "For anyone interested. Cinnamon 1.4 is out. New hot corner behaviour."
date: 2012-03-14
forum: The Cafe
---

### Post by philinux on 2012-03-14
[http://www.webupd8.org/2012/03/cinnamon-14-released-with-new-hot.html](http://www.webupd8.org/2012/03/cinnamon-14-released-with-new-hot.html)

---

### Post by z06steve on 2012-03-14
Thanks, just updated and looks great!

---

### Post by forrestcupp on 2012-03-14
Looks nice. I wish Gnome Shell would make it easy to change the hotcorner positions.

---

### Post by BrokenKingpin on 2012-03-14
meh

---

### Post by Linuxratty on 2012-03-14
Does it work with Compiz?

---

### Post by Copper Bezel on 2012-03-15
It's Shell, so no, it's Mutter-based. (For that matter, it's Shell pretending to *be* Compiz.)

---

### Post by MarkC3pO on 2012-03-15
It's not really Shell. Cinnamon is a fork of Gnome Shell and Muffin is a fork of Mutter.

---

### Post by forrestcupp on 2012-03-15
> **MarkC3pO said:**
> It's not really Shell. Cinnamon is a fork of Gnome Shell and Muffin is a fork of Mutter.

True, but it still uses Muffin rather than Compiz.

---

### Post by MarkC3pO on 2012-03-15
> **forrestcupp said:**
> True, but it still uses Muffin rather than Compiz.
Where did I say it used Compiz? :confused:

---

### Post by forrestcupp on 2012-03-15
> **MarkC3pO said:**
> Where did I say it used Compiz? :confused:

You didn't. But the person you appeared to be replying to was replying to someone who asked if Cinnamon can use Compiz. If you were refuting what Copper Bezel was saying, I was just clearing up that the main point of what he was saying is still true.

---

### Post by Linuxratty on 2012-03-15
> **Copper Bezel said:**
> It's Shell, so no, it's Mutter-based. (For that matter, it's Shell pretending to *be* Compiz.)

Oh bummer.

---

### Post by Dry Lips on 2012-03-15
Wow! I really didn't expect Cinnamon to become this good in such a short time. I've been thinking that they need at least a year to get their act together, but the new release is actually quite usable. I've been thinking about going KDE, but the new Cinnamon release has made me reconsider this.

---

### Post by forrestcupp on 2012-03-15
> **Dry Lips said:**
> Wow! I really didn't expect Cinnamon to become this good in such a short time. I've been thinking that they need at least a year to get their act together, but the new release is actually quite usable. I've been thinking about going KDE, but the new Cinnamon release has made me reconsider this.

Is it becoming easier to customize? I tried the last release, and I had to edit a bunch of code to customize anything at all. And some things were so scattered all over the place with different files that I never could figure out how to do it without serious bugs. I'm talking about something that should be easy to do, like make the task bar and icons in the task bar slightly bigger so you can actually see what you're doing.

That's the biggest downside I saw about it. If they can add a few more settings to customize simple things, it'll be pretty awesome.

---

### Post by Dry Lips on 2012-03-15
> **forrestcupp said:**
> Is it becoming easier to customize? I tried the last release, and I had to edit a bunch of code to customize anything at all. And some things were so scattered all over the place with different files that I never could figure out how to do it without serious bugs. I'm talking about something that should be easy to do, like make the task bar and icons in the task bar slightly bigger so you can actually see what you're doing.

That's the biggest downside I saw about it. If they can add a few more settings to customize simple things, it'll be pretty awesome.

First of all there was a few bugs with the former release that seemingly has disappeared. I haven't used cinnamon 1.4 that much yet, but there are quite a few new interesting features. Now you can even edit the panel, which is a big plus. 

So yes, they are definitively on the right track, but YMMV; there might still be bugs that I haven't encountered in the brief period that I've used it.

---

### Post by MarkC3pO on 2012-03-15
> **forrestcupp said:**
> Is it becoming easier to customize? I tried the last release, and I had to edit a bunch of code to customize anything at all. And some things were so scattered all over the place with different files that I never could figure out how to do it without serious bugs. I'm talking about something that should be easy to do, like make the task bar and icons in the task bar slightly bigger so you can actually see what you're doing.

That's the biggest downside I saw about it. If they can add a few more settings to customize simple things, it'll be pretty awesome.

It's in the theme's css file. /.themes. I was able to enlarge the panel and system tray icons. [http://img845.imageshack.us/img845/3008/screenshotat20120315183.png](http://img845.imageshack.us/img845/3008/screenshotat20120315183.png) The rest isn't too obvious but I don't know css.  There needs to be an easier way but for now, making themes with larger icons could do. Any idea how to enlarge the rest?

---

### Post by orange2k on 2012-03-16
I've ran the install procedure:

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
```

but I'm getting this message in the terminal:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cinnamon
```

Am I doing something wrong?

I'm running Ubuntu 12.04 beta...

---

### Post by forrestcupp on 2012-03-16
> **MarkC3pO said:**
> It's in the theme's css file. /.themes. I was able to enlarge the panel and system tray icons. [http://img845.imageshack.us/img845/3008/screenshotat20120315183.png](http://img845.imageshack.us/img845/3008/screenshotat20120315183.png) The rest isn't too obvious but I don't know css.  There needs to be an easier way but for now, making themes with larger icons could do. Any idea how to enlarge the rest?

I don't know what it's like now, but in the last release, you had to edit at least one css *and* javascript file to get it to actually work right. If you only edit the obvious place in the css, it would make it bigger *below* the screen, so you also had to edit a javascript file to make the screen smaller so the larger panel would fit on your screen. Even then, doing that screwed things up so that a maximized window would be behind the panel. I was so frustrated with searching through so many code files that I gave up before I got that one figured out. I never figured out how to make the icons larger and fit in the panel correctly.

In my opinion, something like that isn't ready to use. I don't want to have to program my own DE to be able to use something. But that was 1.3 and not 1.4. Hopefully it's getting better.

---

### Post by Copper Bezel on 2012-03-16
Frankly, those are just the symptoms of an ambitious hack. A couple of folks working in their spare time to fork something as big as Gnome (and not for minor functionality tweaks, but to do really unusual things with it) is going to result in a bit of a mess that requires a little more cleanup on the user's end.

---

### Post by MarkC3pO on 2012-03-16
> **forrestcupp said:**
> 

In my opinion, something like that isn't ready to use. I don't want to have to program my own DE to be able to use something. But that was 1.3 and not 1.4. Hopefully it's getting better.

The tutorial doesn't even mention javascript. It says all the formatting is in the css. 
Anyway, it's better than what you describe. The maximized window moves down out of the way when I switch to the edited theme. 

I'm going to try to figure the rest out so people don't have to edit them themselves.


ETA: 

[Linux Deepin]("http://www.linuxdeepin.com/") has a highly customized Gnome Shell with a large panel and panel icons. The app overlay has smaller icons and is set up a bit differently with the categories on the left instead of way over to the right. 

[[IMG]http://img441.imageshack.us/img441/3384/screenshotat20120311203.png[/IMG]]("http://img818.imageshack.us/img818/3384/screenshotat20120311203.png")

[IMG]http://www.linuxdeepin.com/templates/linuxdeepin2/images/download_01en.jpg[/IMG]

---

### Post by forrestcupp on 2012-03-16
> **MarkC3pO said:**
> The tutorial doesn't even mention javascript. It says all the formatting is in the css. 
Anyway, it's better than what you describe. The maximized window moves down out of the way when I switch to the edited theme. 
Are you talking about editing a theme? I'm not talking about creating/editing a theme, but actually changing how Cinnamon works. But if the tutorial was specifically for making the panel larger, either the tutorial was incomplete, or they changed things in 1.4. It used to not be possible to change that completely in the theme's css without editing one or two of Cinnamon's javascript files, too. Then if you switch to another theme with a standard size panel, everything was screwed up.

I know they were working toward using proportions rather than pixel sizes so everything is linked together. Maybe they got that working a little better in this release.

---

### Post by MarkC3pO on 2012-03-16
> **forrestcupp said:**
> 

I know they were working toward using proportions rather than pixel sizes so everything is linked together. Maybe they got that working a little better in this release.

The panel hight was in pixels, which I doubled but the icons I enlarged were in em. I have no clue what that is. 

e.g. ```
.system-status-icon {
    icon-size: 2.14em;
```Maybe if I just changed *every* icon-size setting to 2.14 that'd work.

ETA: and yes, I'm talking about editing themes until you can do it graphically. It will save others' the headache. Isn't this what free software is about? I just need to hit the css books,.

ETA2:  I can't get the launcher icons to change. Maybe that's what you need the js for.  Feel free to laugh at my latest attempt.

---

### Post by forrestcupp on 2012-03-16
I don't remember what "em" is, but I know that is for proportions instead of pixel sizes. That's what I was talking about. The problem is that some parts use pixels and some parts use em.

So when you changed the pixel height of the panel, maximized windows don't go behind the panel? I don't think I ever figured out how to fix that. I ended up just setting everything back to default because you can't have the bottom part of your window behind the panel.

I had to edit the js file to shrink the desktop space so that the larger part of the enlarged panel wouldn't be pushed off of the bottom of the screen instead of raising it up, like you would want. I don't think there was a tutorial at all when I messed with it.

Maybe they worked some of that stuff out with the new version to make it easier to customize. I don't still have Cinnamon installed, so I couldn't tell you the names of all of the files I had to edit.

---

### Post by MarkC3pO on 2012-03-16
Now I see. Some of it has to do with where the panel is. There is no problem when the panel is at the top. When on the bottom, it goes below the screen edge.  Maximized windows don't go behind the panel when at the top or the bottom.

---

### Post by forrestcupp on 2012-03-17
Yeah, my panel was at the bottom. I didn't think about your panel being at the top. That wouldn't have been affected in the same way. I wonder if your actual desktop screen got pushed below the screen and you just didn't know it. I guess not, though if maximized windows don't go below the screen.

---

### Post by MarkC3pO on 2012-03-17
I just double checked. It shrinks the maximized window so that it fits below the top panel and the bottom of the screen. I still have scroll bars and I opened "find" in Firefox. Neither are below the actual screen.  It must be a relic of Gnome Shell's top panel-centric design. 

Maybe in 1.4.x or 1.5?  Anyway, its still more customizable than its parent. ;)

---

### Post by Copper Bezel on 2012-03-17
Not to spark an argument, but how so? I can resize my panel in Shell just fine, and not piece by piece, either. (One of the first things I tweaked was to take it down to 20 px.)

---

### Post by MarkC3pO on 2012-03-17
> **Copper Bezel said:**
> Not to spark an argument, but how so? I can resize my panel in Shell just fine, and not piece by piece, either. (One of the first things I tweaked was to take it down to 20 px.)

You're reducing it by 5 px though. That's easier.  Try putting it on the bottom at 50px.

ETA: Also, you can drag the applets around and put them where you want them, change hot corners, manage desktop effects, move panels and such things as that. That's what I meant by "more customizable."

---

### Post by ojdon on 2012-03-17
Can't wait for a Precise version!

---

### Post by Copper Bezel on 2012-03-17
[QUOTE=MarkC3pO]You're reducing it by 5 px though. That's easier. Try putting it on the bottom at 50px.

ETA: Also, you can drag the applets around and put them where you want them, change hot corners, manage desktop effects, move panels and such things as that. That's what I meant by "more customizable."[/QUOTE]
Fair enough. So it can be customized in the ways that Gnome 2 could, instead of the ways that Shell can.

---

### Post by forrestcupp on 2012-03-17
> **Copper Bezel said:**
> Not to spark an argument, but how so? I can resize my panel in Shell just fine, and not piece by piece, either. (One of the first things I tweaked was to take it down to 20 px.)

So are you talking about Cinnamon or Gnome Shell? The experience I was talking about was in Cinnamon 1.3. Also, making it smaller probably wouldn't be as noticeably buggy as making it larger.

---

### Post by Copper Bezel on 2012-03-17
I was making a specious argument to belittle Cinnamon in light of the fact that Gnome Shell does allow the panel to be resized (including the objects it contains.)

---

### Post by MarkC3pO on 2012-03-17
> **Copper Bezel said:**
> I was making a specious argument to belittle Cinnamon in light of the fact that Gnome Shell does allow the panel to be resized (including the objects it contains.)

The text and icons won't scale.. It's just not noticeable when you only make it slightly smaller. At first I thought the FF icon scaled but then I realized the top and bottom aren't cut off like they are in the default panel.

---

### Post by forrestcupp on 2012-03-18
> **Copper Bezel said:**
> I was making a specious argument to belittle Cinnamon in light of the fact that Gnome Shell does allow the panel to be resized (including the objects it contains.)

Lol. Ok. I'm not going to argue about that. I'm a Gnome Shell user, too. I tried out Cinnamon without meaning to be too serious about it, saw that it wasn't ready for real use, and went back to using Gnome Shell.

But to be fair, Gnome Shell has been in development a lot longer than Cinnamon, and they've done a lot of good work in the little time they've been working on it. Someday, it may be a real contender.

---

### Post by MarkC3pO on 2012-03-18
> **forrestcupp said:**
> Lol. Ok. I'm not going to argue about that. I'm a Gnome Shell user, too. I tried out Cinnamon without meaning to be too serious about it, saw that it wasn't ready for real use, and went back to using Gnome Shell.

But to be fair, Gnome Shell has been in development a lot longer than Cinnamon, and they've done a lot of good work in the little time they've been working on it. Someday, it may be a real contender.

Now I'm really confused. If you don't think Cinnamon is ready, how on Earth can you use Gnome Shell? Editing the panel isn't any easier.  :confused:  Maybe you'd be better off using Cinnamon with the dock.

---

### Post by Copper Bezel on 2012-03-18
Edit: Scrubbed.

---

### Post by forrestcupp on 2012-03-18
> **MarkC3pO said:**
> Now I'm really confused. If you don't think Cinnamon is ready, how on Earth can you use Gnome Shell? Editing the panel isn't any easier.  :confused:  Maybe you'd be better off using Cinnamon with the dock.

Because you don't really use the panel in Gnome Shell; you use the Dash. The only reason I tried to edit the panel in Cinnamon is because the default was so small it was hard on the eyes. I don't have a problem with the defaults in Gnome Shell.

Also, there are a heck of a lot more extensions for Gnome Shell than there are for Cinnamon.

---

### Post by Buntu Bunny on 2012-08-10
> **orange2k said:**
> I've ran the install procedure:

```
sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
sudo apt-get update
sudo apt-get install cinnamon
```

but I'm getting this message in the terminal:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package cinnamon
```

Am I doing something wrong?

I know this is way later, but I had this problem as well. So for anybody else wondering what to do...

I had to run these two a second time...

```
sudo apt-get update
```

and then 

```
sudo apt-get install cinnamon
```

again. Downloaded just fine then.

---

### Post by BigSilly on 2012-08-10
Cinnamon was rotten for me on Ubuntu, but just great on Mint. :-s

---

### Post by pierceTN on 2012-08-10
> **MarkC3pO said:**
> The tutorial doesn't even mention javascript. It says all the formatting is in the css. 
Anyway, it's better than what you describe. The maximized window moves down out of the way when I switch to the edited theme. 

I'm going to try to figure the rest out so people don't have to edit them themselves.


ETA: 

[Linux Deepin]("http://www.linuxdeepin.com/") has a highly customized Gnome Shell with a large panel and panel icons. The app overlay has smaller icons and is set up a bit differently with the categories on the left instead of way over to the right. 

[[IMG]http://img441.imageshack.us/img441/3384/screenshotat20120311203.png[/IMG]]("http://img818.imageshack.us/img818/3384/screenshotat20120311203.png")

[IMG]http://www.linuxdeepin.com/templates/linuxdeepin2/images/download_01en.jpg[/IMG]


does linuxdeepin os have the same "core" as ubuntu?  

Pierce

---

### Post by Jakin on 2012-08-10
I had tried Cinnamon 1.4 a month or so- ago. I like its look, its simplicity; but it far from has the functions i want. 
I suspect i'll need to wait quite awhile before it does.

---

### Post by MadmanRB on 2012-08-10
> **Copper Bezel said:**
> I was making a specious argument to belittle Cinnamon in light of the fact that Gnome Shell does allow the panel to be resized (including the objects it contains.)

Yes it can do it... after installing several extensions that is

---

