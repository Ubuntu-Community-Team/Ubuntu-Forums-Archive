---
title: "GIMP 2.6 released!"
date: 2008-10-01
forum: The Cafe
---

### Post by bash on 2008-10-01
GIMP 2.6 has been release contain quite a few new features or updates and some changes to the UI. 

Head on over to the [release notes](http://gimp.org/release-notes/gimp-2.6.html) to get a pictured overview of what changed.


Downloads:

Just a general warning: It could possibly blow up your computer and convince the LHC to end the world.

Ubuntu 8.04 Hardy:

Head on over to [GetDeb](http://www.getdeb.net/search.php?keywords=gimp) and download all the needed packages from there. (If your confused in what order to install the .debs check out [Kaseas post](http://ubuntuforums.org/showpost.php?p=5895943&postcount=49))

Ubuntu 8.10 Intrepid:

Thanks to c-korn if you want you can now try it out. Just add this PPA to your sources:

```
deb http://ppa.launchpad.net/c-korn/ubuntu intrepid main
deb-src http://ppa.launchpad.net/c-korn/ubuntu intrepid main
```

---

### Post by Nano Geek on 2008-10-01
Nice :guitar:

---

### Post by Mazza558 on 2008-10-01
Nice to see they've added a way to have it all in one window now.

---

### Post by klange on 2008-10-01
... wow. After reading that, I can't wait to see what they'll squeeze into 2.*8*.
Amazing improvements. Too bad we won't get this in Intrepid...
Love how they made the look optionally Photoshop-y. Should help a lot with converts who have been... um... you know.

---

### Post by aaaantoine on 2008-10-01
Reading the notes, I think that GIMP 2.6 would make a great candidate for post-freeze entry into the Intrepid repositories.

---

### Post by bash on 2008-10-01
Someone who knows the deal should file a Feature Freeze examption. I don't know what exactly is needed or I would do it.

---

### Post by smartboyathome on 2008-10-01
> **aaaantoine said:**
> Reading the notes, I think that GIMP 2.6 would make a great candidate for post-freeze entry into the Intrepid repositories.

It won't happen. Intrepid still uses GIMP 2.4.7, which means that 2.6 would introduce too many bugs to be accepted. If Intrepid were using one of the 2.5 builds, then it might be able to happen, but as it is, I doubt we will get it in Intrepid. It might make it into Intrepid updates or backports though.

---

### Post by cookieofdoom on 2008-10-01
I'm looking for a debian file. I'll post here if I find one. Getdeb doesn't have it up yet last I checked.

---

### Post by plun on 2008-10-01
PPA

[https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive)

32 bit seems to be ready...:)

---

### Post by smartboyathome on 2008-10-01
> **plun said:**
> PPA

[https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive)

32 bit seems to be ready...:)

Installing now on Intrepid. :D

---

### Post by danbuter on 2008-10-01
Just in time to NOT be included in Intrepid!!!   :guitar:

---

### Post by cookieofdoom on 2008-10-01
> **plun said:**
> PPA

[https://launchpad.net/~c-korn/+archive](https://launchpad.net/~c-korn/+archive)

32 bit seems to be ready...:)

That seems to be only for Intrepid. Hopefully he'll add a Hardy version soon.

---

### Post by Vadi on 2008-10-01
c-korn actually does a lot of the getdeb packages (like 60%), as you see on the application pages. I heard there was a bug with the plain 2.6, so they're applying a patch or something. But it'll be up there soon.

Edit: it's built for 8.04 in getdeb, just needs QA and then it'll be released.

---

### Post by 2cute4u on 2008-10-01
It still doesn't have a history brush.  :(

That's a Major disapointment, since it's probably  the most requested feature.

---

### Post by steeleyuk on 2008-10-01
> **2cute4u said:**
> It still doesn't have a history brush.  :(

That's a Major disapointment, since it's probably  the most requested feature.

Other than the interface... :)

---

### Post by Twitch6000 on 2008-10-01
This is great news :D.

---

### Post by Vadi on 2008-10-01
Gimp up on getdeb: [http://www.getdeb.net/search.php?keywords=gimp](http://www.getdeb.net/search.php?keywords=gimp)

---

### Post by bash on 2008-10-01
Added the download links for both Hardy and Intrepid to the first post, so lazy people don't need to roam around the thread. ;)

---

### Post by meho_r on 2008-10-01
They say:

> With the empty image window acting as a natural main window, the default window hints for the Toolbox and Docks have been changed to Utility window. This enables window managers to do a much better job of managing the GIMP windows, including omitting the Toolbox and Docks from the taskbar and ensuring that the Toolbox and Docks always are above image windows. 

But I still have 3 windows in Taskbar. And Toolbox and Docks are not above main window. Am I missing something? :confused:

---

### Post by Vadi on 2008-10-01
I think you can dock them in somehow. I only had 2 windows though.

---

### Post by bruce89 on 2008-10-01
I'll have a go PPAing this tomorrow for at least Intrepid.

---

### Post by CarpKing on 2008-10-01
> **meho_r said:**
> I still have 3 windows in Taskbar. And Toolbox and Docks are not above main window. Am I missing something? :confused:

Try turning Desktop Effects off.  Last I tried Compiz didn't support the "Utility" window hint.  If you notice, there's a note near the bottom of the release notes saying that it is only known to work under Gnome, by which they probably mean Metacity.

---

### Post by niccholaspage on 2008-10-01
Awesome! Gimp is awesome and now 2.6 comes out. Can't want after I install all these .debs!

---

### Post by pbhj on 2008-10-01
> **smartboyathome said:**
> It won't happen. Intrepid still uses GIMP 2.4.7, which means that 2.6 would introduce too many bugs to be accepted. If Intrepid were using one of the 2.5 builds, then it might be able to happen, but as it is, I doubt we will get it in Intrepid. It might make it into Intrepid updates or backports though.

I'm pretty sure that Gimp uses an even = stable, odd=unstable (or rather dev.) release numbering scheme.

So the next stable version after 2.4.7 (in August 2008) is 2.6.0 (in Oct 2008).

I can't see how a numbering jump automatically means more bugs?

---

### Post by Twitch6000 on 2008-10-01
I finally got through using gimp and well it is alot easier to find things now.

One question though how to install more brushes for ubuntu O.O?

Also how to make it use the new combined windows feature I wanna try that out lol.(I know I won't use it long as I am too use to the separate windows)

---

### Post by niccholaspage on 2008-10-01
Well Gimp 2.6 just released. Though it shouldn't have that much bugs. I downloaded the debs from getdeb.net and installed them and Gimp is awesome. And it comes with GEGL.
Heres the introduction on the Release Notes page:
> 
    GIMP 2.6 is an important release from a development point of view.   It features changes to the user interface addressing some often   received complaints, and a tentative integration of GEGL, the graph   based image processing library that will eventually bring high   bit-depth and non-destructive editing to GIMP. 



---

### Post by bruce89 on 2008-10-01
> **pbhj said:**
> So the next stable version after 2.4.7 (in August 2008) is 2.6.0 (in Oct 2008).

I can't see how a numbering jump automatically means more bugs?

As you can see from 2.4.7, there have been 7 bugfix releases in the 2.4 series. Evidently, 2.4.0 wasn't perfect, so why would 2.6.0 be?

---

### Post by klange on 2008-10-01
> **CarpKing said:**
> Try turning Desktop Effects off.  Last I tried Compiz didn't support the "Utility" window hint.  If you notice, there's a note near the bottom of the release notes saying that it is only known to work under Gnome, by which they probably mean Metacity.

That we don't. Might be a good time to add it... I'll bug the guys.

---

### Post by Kaseas on 2008-10-01
Sorry for the newb question, but now that I got all the .deb files from getdeb, how do I install them? I know how to install one, but you apparently need them all due to dependancies.

Edit: NVM. I figured it out :D

Edit2: Now how do I get it to display in one window? I'm still getting 3 seperate ones.

---

### Post by klange on 2008-10-02
> **Kaseas said:**
> Now how do I get it to display in one window? I'm still getting 3 seperate ones.

You're still going to have three windows because nothing really handles the windows perfectly as sub-windows, but if you're running Metacity (or Compiz from git as of this morning), the toolbox, etc. will float above the main window, and the main window will size the image to better fit this set up.

---

### Post by TreverT on 2008-10-02
Any idea when/if the new version will turn up in the software repositories backported to Gutsy?  I still haven't had the time/weeks to waste chasing problems to upgrade to Hardy, but I use Gimp all the time and the new versions sounds fantastic.  I tried manually installing the version listed on that GetDeb page but even after DLing all the parts, it still fussed that there were dependencies missing and after wasting a half hour mucking with it, I gave it up.  Would love to be able to get the new version via the nice simple "Add/Remove" if it's ever going to be included... any ideas?

---

### Post by Polygon on 2008-10-02
i doubt its ever going to be in the backports for gusty.

---

### Post by meho_r on 2008-10-02
> **CarpKing said:**
> Try turning Desktop Effects off.  Last I tried Compiz didn't support the "Utility" window hint.  If you notice, there's a note near the bottom of the release notes saying that it is only known to work under Gnome, by which they probably mean Metacity.

I noticed that about Gnome, but didn't realize that it has to do with Compiz. Thanks.

---

### Post by Xiong Chiamiov on 2008-10-02
> **bruce89 said:**
> As you can see from 2.4.7, there have been 7 bugfix releases in the 2.4 series. Evidently, 2.4.0 wasn't perfect, so why would 2.6.0 be?
Y'know, *buntu's not based off Debian-stable...

---

### Post by pbhj on 2008-10-02
> **bruce89 said:**
> As you can see from 2.4.7, there have been 7 bugfix releases in the 2.4 series. Evidently, 2.4.0 wasn't perfect, so why would 2.6.0 be?

I didn't say that it was going to be perfect. But 2.4.7 ain't perfect either. What I was countering was the idea that 2.6.0 necessarily had more bugs than 2.4.7 - I'm sure both have many bugs :D

The risk averse will want to wait at least until 2.6.1 I'm sure - indeed I think the getdeb packages are on their second package due, I assume, to a glitch in the tarball as gimp.org puts it. Strangely the tarball isn't 2.6.0.1.

---

### Post by lukjad on 2008-10-02
Thanks! Installed.

---

### Post by Chame_Wizard on 2008-10-02
will add:P

---

### Post by ounas on 2008-10-02
Thanks works a treat :popcorn:

---

### Post by smartboyathome on 2008-10-02
> **pbhj said:**
> I didn't say that it was going to be perfect. But 2.4.7 ain't perfect either. What I was countering was the idea that 2.6.0 necessarily had more bugs than 2.4.7 - I'm sure both have many bugs :D

The risk averse will want to wait at least until 2.6.1 I'm sure - indeed I think the getdeb packages are on their second package due, I assume, to a glitch in the tarball as gimp.org puts it. Strangely the tarball isn't 2.6.0.1.

Ubuntu doesn't like to risk it though, and I said "if Intrepid didn't use 2.5" because I knew that there is an odd-even release schedule, and Ubuntu only uses the latest stable up to feature freeze.

---

### Post by mrgnash on 2008-10-02
I don't really like the interface changes, which is why I didn't upgrade to 2.5 long ago... but the stuff under the hood makes it hard to put it off now that 2.6 is out.

---

### Post by Bou on 2008-10-02
> **CarpKing said:**
> Try turning Desktop Effects off.  Last I tried Compiz didn't support the "Utility" window hint.  If you notice, there's a note near the bottom of the release notes saying that it is only known to work under Gnome, by which they probably mean Metacity.

According to this [thread]("http://forum.compiz-fusion.org/showthread.php?t=9884"), it might be fixed in upcoming versions of Compiz. At least I understood that.

---

### Post by Hells_Dark on 2008-10-02
I didn't understand how to have just one window.. is it really possible ?
Edit : well, ok, we just can't.

Nice new version btw !

---

### Post by mooney79 on 2008-10-02
Sorry, kind of a noob here. Im trying to install Gimp 2.6.0. I downloaded the "gimp_2.6.0-1~getdeb1_i386.deb" for ubuntu 8.04. When i run the package installer I get "Error: dependency is not satisfiable: gimp-data". Any advice?

---

### Post by klange on 2008-10-02
> **Bou said:**
> According to this [thread]("http://forum.compiz-fusion.org/showthread.php?t=9884"), it might be fixed in upcoming versions of Compiz. At least I understood that.
Indeed it is.


> I didn't understand how to have just one window.. is it really possible ?
This sort of functionality really needs to be considered in GTK... QT has it.

---

### Post by smartboyathome on 2008-10-02
> **WindowsSucks said:**
> This sort of functionality really needs to be considered in GTK... QT has it.

GTK has it, look at Inkscape. It is just the choice of the GIMP developers that the interface is the way it is.

---

### Post by klange on 2008-10-02
> **smartboyathome said:**
> GTK has it, look at Inkscape. It is just the choice of the GIMP developers that the interface is the way it is.

You're confusing docking with subwindows, of course you can slap an interface into one window in GTK... (also, GTK itself does not have a docking system)

---

### Post by Paqman on 2008-10-02
> **mooney79 said:**
> Sorry, kind of a noob here. Im trying to install Gimp 2.6.0. I downloaded the "gimp_2.6.0-1~getdeb1_i386.deb" for ubuntu 8.04. When i run the package installer I get "Error: dependency is not satisfiable: gimp-data". Any advice?

You need to feed it the package gimp-data (and in fact a few other packages) first. Normally the package manager handles these dependencies automatically by grabbing the required packages from the repos. Since you're installing this manually you need to sort the dependencies yourself.

Grab _all_ the packages under Gimp 2.6 in GetDeb. Install the libraries like GEGL first, working your way up to Gimp itself.

---

### Post by CarpKing on 2008-10-02
> **WindowsSucks said:**
> if you're running Metacity (or Compiz from git as of this morning), the toolbox, etc. will float above the main window, and the main window will size the image to better fit this set up.

Awesome!  Any chance you could get the Ubuntu devs to pull whatever Compiz patches that takes into Intrepid?

---

### Post by Kaseas on 2008-10-02
> **TreverT said:**
> Any idea when/if the new version will turn up in the software repositories backported to Gutsy?  I still haven't had the time/weeks to waste chasing problems to upgrade to Hardy, but I use Gimp all the time and the new versions sounds fantastic.  I tried manually installing the version listed on that GetDeb page but even after DLing all the parts, it still fussed that there were dependencies missing and after wasting a half hour mucking with it, I gave it up.  Would love to be able to get the new version via the nice simple "Add/Remove" if it's ever going to be included... any ideas?

> **mooney79 said:**
> Sorry, kind of a noob here. Im trying to install Gimp 2.6.0. I downloaded the "gimp_2.6.0-1~getdeb1_i386.deb" for ubuntu 8.04. When i run the package installer I get "Error: dependency is not satisfiable: gimp-data". Any advice?

You just need to install these in the proper order. Download all the .deb packages, and install in the following order:
libbabl
libgegl
libgimp
gimp
gimp-python
gimp-gnomevfs
gimp-libcurl
gimp-data

---

### Post by Hairy_Palms on 2008-10-02
Just Figured id post this here, in the 2.5.x dev series you could make the dialogs and toolbox transient to the picture window, they removed the option in the preferences dialog, but the functionality is still there, so if you run this command and restart gimp 2.6.0 then it should work
```
echo "(transient-docks yes)" >> ~/.gimp-2.6/gimprc
```

---

### Post by Kaseas on 2008-10-02
> **Hairy_Palms said:**
> Just Figured id post this here, in the 2.5.x dev series you could make the dialogs and toolbox transient to the picture window, they removed the option in the preferences dialog, but the functionality is still there, so if you run this command and restart gimp 2.6.0 then it should work
```
echo "(transient-docks yes)" >> ~/.gimp-2.6/gimprc
```

Doesn't seem to be working.

---

### Post by rocknrolf77 on 2008-10-02
gegl is so much faster. It's a joy to sharpen pictures and use other plugins. I feel like having a new super fast computer =D>

---

### Post by bruce89 on 2008-10-02
> **WindowsSucks said:**
> (also, GTK itself does not have a docking system)

Indeed, but GTK+ was supposed to be a simple widget library. See the [Gnome Devtools Library]("http://library.gnome.org/devel/gdl/stable/") for dock widgets.

---

### Post by mog538 on 2008-10-02
I really like the sound of these changes, the arrangement of windows always especially frustrated me!

---

### Post by pbhj on 2008-10-03
> **pbhj said:**
> The risk averse will want to wait at least until 2.6.1 I'm sure.

Actually it's quite buggy, haven't tested exhaustively but the only bit of GEGL that works for me is the gaussian blur shown in the screenshots. I've found a few bugs already and I've barely used it, just looked around.

Also, based on what people were saying I was expecting a great change in the UI. The only changes appear to be that they've taken the menu from the tools dock window and left a blank space; and removed all but one of the panel (application bar) entries. 

In practice this appears to mean that there's no way to quickly raise the tools and layers windows (at least not in KDE4) as they don't appear on the panel, if they get obscured by another window you have to lower/minimise that window, weird.

I was expecting something like the Inkscape system where you have dockable tools, layers, etc., that can be docked, minimised or ripped off for use on a second monitor. Indeed I spent a few minutes trying to drag-dock the tools window to the main image window.

---

### Post by carusoswi on 2008-10-04
I never do enough of this stuff to remember how.  I downloaded the six packages from the Getdeb page all to one directory.  I then extracted the files to the same location.  What do I do now?  Or have I messed things up already?  Sorry to be so dense.
Thanks for any assistance.

Caruso

> **Kaseas said:**
> You just need to install these in the proper order. Download all the .deb packages, and install in the following order:
libbabl
libgegl
libgimp
gimp
gimp-python
gimp-gnomevfs
gimp-libcurl
gimp-data

---

### Post by carusoswi on 2008-10-04
Nevermind.  Figured it out.  For the rest of you who might be challenged like me, here is what I did.  I right clicked on the un-extracted packages, just as they were downloaded.  Then, I clicked on 'open with gdebi package installer'.  I tried to follow the order shown by kaseas, but couldn't really correlate the package names to the file names he lists.  Instead, I just started trying to use gdebi to install the packages, starting from the bottom of the list as they appeared in my directory.  If I received an error message concerning dependencies, I just abandoned that package and moved on to another until I found the next one that would install.  I kept following this hit or miss approach until I had installed all the packages, and it worked for me.  

Prior to figuring this out, I know I broke my old version of Gimp, so I used the Synaptic Package Manager to uninstall it.

Also, during my hit or miss install, there were several warnings that older versions of certain files were already installed.  I dismissed these warnings and installed the package files, anyway.  Since Gimp seems to be working, I guess what I considered to be the logical decision with regard to this 'older version already installed' messages was the right decision.

It's working, so, now I have to go play with it.

Caruso

> **carusoswi said:**
> I never do enough of this stuff to remember how.  I downloaded the six packages from the Getdeb page all to one directory.  I then extracted the files to the same location.  What do I do now?  Or have I messed things up already?  Sorry to be so dense.
Thanks for any assistance.

Caruso

---

### Post by Polygon on 2008-10-04
the correct way to install it is to do it all at once

put them all in a new folder, then cd to it in a terminal, then

cd /<foldernamehere>

sudo dpkg -i *.deb

and it will upgrade all of them at once so you wont get dep errors

---

### Post by carusoswi on 2008-10-04
> **Polygon said:**
> the correct way to install it is to do it all at once

put them all in a new folder, then cd to it in a terminal, then

cd /<foldernamehere>

sudo dpkg -i *.deb

and it will upgrade all of them at once so you wont get dep errors

LOL, Polygon, where were you when I needed you, LOL.  I am going to copy your advice into my Ubuntu tips folder for next time.  Thanks.
The only good lesson I learned from this is that I'm reaching that point in Ubuntu where I don't get so frustrated over things.  A couple of years ago, I would have thrown my hands up (and powered my computer off) in disgust because I couldn't figure this out in Ubuntu.

My way, I know, wasn't pretty, but I got there.

Thanks again for the tip.

I've played with the new version for a couple of minutes.  Not certain I have the hang of the one window deal, yet.  I still have my tools off in another window separate from the image, although I notice that the menus are no longer together with the tools, but reside in that 'empty' window that pops up when you open the application.

The separate windows never really bothered me that much in previous versions once I spent enough time with Gimp to know what was going on, but I am excited about some of the new features listed for this new version.

My photo editing 'suite' in Ubuntu includes CS2 in Wine, Lightzone (great little piece of software, IMO), UFRAW (I really like this - an upgrade to my DSLR firmware had caused me to rediscover UFRAW's usefulness), and of course, GIMP which, for my first couple of years in Ubunut, I pretty much ignored.  I wasn't familiar with the interface, the tools were a little different and I couldn't find them as easily as I could in PS.

But time takes its toll on even the most rock-stubborn minds, and I now have a much greater appreciation for the GIMP.  It doesn't perform quite as smoothly as PS, but, on my system, it is much faster at opening files than either PS or (well, this goes without saying) Lightzone (which is dog slow at this).

And, of course, GIMP and UFWAW have the added value of being open source which, naturally appeals to the philosophy which I embrace.  I almost never use PS anymore.

Caruso

---

### Post by mooney79 on 2008-10-05
> **Paqman said:**
> You need to feed it the package gimp-data (and in fact a few other packages) first. Normally the package manager handles these dependencies automatically by grabbing the required packages from the repos. Since you're installing this manually you need to sort the dependencies yourself.

Grab _all_ the packages under Gimp 2.6 in GetDeb. Install the libraries like GEGL first, working your way up to Gimp itself.

Thanks Paqman. Got everything installed now.

---

### Post by twodayslate on 2008-10-05
> **WindowsSucks said:**
> You're still going to have three windows because nothing really handles the windows perfectly as sub-windows, but if you're running Metacity (or Compiz from git as of this morning), the toolbox, etc. will float above the main window, and the main window will size the image to better fit this set up.

WTF. I need compiz to have Gimp in [one window](http://gimp.org/screenshots/alternative-2-6-ui-layout-example-two.jpg)?

---

### Post by Twitch6000 on 2008-10-05
> **twodayslate said:**
> WTF. I need compiz to have Gimp in [one window](http://gimp.org/screenshots/alternative-2-6-ui-layout-example-two.jpg)?

Uhh if so then it still doesn't work for me :(..

---

### Post by klange on 2008-10-05
> **twodayslate said:**
> WTF. I need compiz to have Gimp in [one window](http://gimp.org/screenshots/alternative-2-6-ui-layout-example-two.jpg)?

Did you even read my post? Or did you see "compiz" and jump to conclusions? As far you can be considered, it *won't* work in Compiz. If you use Gnome without Compiz, it'll work.

---

### Post by twodayslate on 2008-10-05
> **WindowsSucks said:**
> Did you even read my post? Or did you see "compiz" and jump to conclusions? As far you can be considered, it *won't* work in Compiz. If you use Gnome without Compiz, it'll work.You said nothing works perfectly. Metacity and compiz, you said sorta works. Unless I completely misunderstood you...

I am using Normal visual effects. So is there anyway to make GIMP one window?

---

### Post by klange on 2008-10-05
> **twodayslate said:**
> You said nothing works perfectly. Metacity and compiz, you said sorta works. Unless I completely misunderstood you...

I am using Normal visual effects. So is there anyway to make GIMP one window?
The picture you linked to is not actually one window. In Gnome under Metacity, you should only see one window in the taskbar. In Compiz, we show them all because our fix was a last-minute thing.
What they need to do is add docking to the left and right of the image window like Inkscape has...

---

### Post by twodayslate on 2008-10-05
> **WindowsSucks said:**
> The picture you linked to is not actually one window. In Gnome under Metacity, you should only see one window in the taskbar. In Compiz, we show them all because are fix was a last-minute thing.
What they need to do is add docking to the left and right of the image window like Inkscape has...

That cleared it up. Thank you, I understand now. 

One windowed GIMP only works in Metacity. That sucks...

---

### Post by picpak on 2008-10-05
> **twodayslate said:**
> One windowed GIMP only works in Metacity. That sucks...

That's sad news for Openbox users. :(

---

### Post by klange on 2008-10-05
I'm surprised they haven't done image window docking yet, if you look at the "GIMP UI Brainstorm" (an official blog of mockups they've been sent), it has to be the most popular idea yet.

---

### Post by cardinals_fan on 2008-10-05
> **picpak said:**
> That's sad news for Openbox users. :(
It's even worse news for all us tiling window manager users.  We desperately **need** a one-window GIMP, because those silly little panes get in the way.

---

### Post by kpkeerthi on 2008-10-06
> **Mazza558 said:**
> Nice to see they've added a way to have it all in one window now.

Not yet. They have just removed the menubar that used to appear on the Toolbox.

This [screenshot]("http://www.gimp.org/screenshots/alternative-2-6-ui-layout-example-two.jpg") might give you an illusion that toolbox, toolbox options and layers  windows are all within one image window. But actually they are not - The image window has just been backgrounded and the other three windows 'float' on top it. In other words, there are four separate floating windows like in older GIMP releases. :)

---

### Post by fuhrysteve on 2008-10-08
2.6 just hit the Intrepid Repositories!!
[http://packages.ubuntu.com/intrepid/gimp](http://packages.ubuntu.com/intrepid/gimp)

---

### Post by niccholaspage on 2008-10-08
Cool!
Anyone who would like to check if they have the ubuntu repo one, open synaptic manager, and type gimp and than you can check if it says ubuntu by the version number.(Intrepid only.)

---

### Post by TreverT on 2008-11-10
> **Kaseas said:**
> You just need to install these in the proper order. Download all the .deb packages, and install in the following order:
libbabl
libgegl
libgimp
gimp
gimp-python
gimp-gnomevfs
gimp-libcurl
gimp-data

OK, I'm trying to manually install Gimp 2.6 in my Gutsy 7.1 system.  I've got Gimp 2.6 DLed and unpacked, and have the INSTALL instructions open.  I just downloaded and installed the libbabl DEB package, first on the list above.  However, when I run ./configure in the Gimp directory, I get this error:

```
checking for BABL... configure: error: Package requirements (babl >= 0.0.22) were not met:

No package 'babl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables BABL_CFLAGS
and BABL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

Apparently the DEB package isn't installing properly into my Gutsy system?  Anyway, whatever it is, it is borking the Gimp install right off the bat, before I can even move on to any of the other packages.  Any help is welcomed!  (But talk in simple terms, I'm still very much a newbie)

---

### Post by saulgoode on 2008-11-10
My understanding of Debian/Ubuntu packages is that if you intend to compile a program, and that program depends on another project's package, then you must load the -dev package for that other project. In other words, look for a package such as 'libbabl-dev.deb' (it will probably also have some version numbers and maybe the word "ubuntu" in the package name).

Likewise for 'libgegl', et alia.

---

### Post by NeoZiggy on 2009-02-09
Thank you so very much for this guide!
I was scared when I saw that it wanted to remove ubuntu-desktop along with GIMP. Since I didn't see any problems listed, I ventured forth.
After installing all the dependencies and GIMP 2.6, I reinstalled ubuntu-desktop (If you try to reinstall it before installing the new version of GIMP, it will ask to reinstall the old GIMP again).
It sounded like it is needed, can anyone explain further on why it gets removed, but more importantly if it really needs to be installed again?

---

