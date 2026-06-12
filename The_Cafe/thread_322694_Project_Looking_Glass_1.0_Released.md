---
title: "Project Looking Glass 1.0 Released"
date: 2006-12-20
forum: The Cafe
---

### Post by kejar31 on 2006-12-20
I thought it was dead but not only is it at 1.0 it also has Ubuntu packeges. Anyone try it out??

[http://www.osnews.com/story.php/16781/Project-Looking-Glass-1.0-Released](http://www.osnews.com/story.php/16781/Project-Looking-Glass-1.0-Released)

[https://lg3d-core.dev.java.net/binary-builds.html](https://lg3d-core.dev.java.net/binary-builds.html)

---

### Post by Mr. Picklesworth on 2006-12-21
I lost my first reponse here... it may be rather telling that I am having a far more stable and 6x faster desktop experience on a computer that's less than a quarter the power of the one I was just using for Looking Glass.

Installing it was the first part.
For some reason, the downloaded packages crashed the gui depackage program. Not Looking Glass's fault; I did it via the command line, and once I figured out the correct order to install the packages, it worked.
Added itself nicely to the list of Sessions, all was good.

Logging in was fast!
I was greeted by a pretty nice desktop background which fluidly moved around as I moved the pointer, a funny looking dock thing, a ginormous Sun Java logo that did a funny animation along with my pointer, and that's about it... A pretty nice, simple desktop.
I am going to excuse the ugly appearance, since this is very early days and default themes seem to always look awful.

It all looked rather neat, and was running quickly enough at this point. My fears regarding "What the heck? A 3D desktop environment running through a virtual machine or even mentioning Java as its platform... are they nuts?!" were gradually subsiding.

It was weird to navigate. If I brought the pointer anywhere near the top left of the screen, a file manager would materialize showing me icons in Desktop. Kind of weird...
At the bottom left of the dock thing, I found a menu!
Opened it (just by hovering over it, again) and it unfolded rather smoothly. The first thing I tried out was Demos. This section had some really cool examples of items for a 3D desktop; a bunch of physics objects, some balls, a Newton's Cradle... neat stuff. All of these were full 3D directly on the desktop, and could be minimized just like any other app. (In Looking Glass's case, pretty weirdly; more on that later). These were really neat examples, and they show the potential for stuff like this. However, I still must wonder "Why?". Most of the 3d demos were pretty useless, while the "3d web browser" looks pretty 2D to me (just in a 3D window).

Okay, enough of those! I moved onto some more useful apps; I went over the Firefox, ready to post "I did it!" here. I noticed that the menu in Looking Glass is not based on my menu in Gnome at all. I suppose that's safe since Gnome or any other desktop trying to load Looking Glass's 3D stuff would be disastrous (but great if it ever did work), however it also meant that all of my apps were missing from this menu. Firefox was there, though.
Anyway, I loaded Firefox and it opened. Windowed apps here are pretty cool; the windows are full 3d, you can flip them to expose notes at the back (which you can write, and I imagine would be pretty handy, though I haven't tried much to be totally sure of their usefulness yet; adding notes to the back of the window for a particular document in GIMP would be amazing, but unlikely... I'm willing to be very surprised, though).

Then I tried to use Firefox. I noticed that upon loading Firefox, the system had slowed to a crawl. The pointer was impossible to control (very sluggish), and key input had at least a 2 second delay. Upon minimizing Firefox, it all went back to the usual acceptable speed. *Very weird*. Essentially, I could not actually use - with any kind of speed - any "normal" 2D programs.

Another weird thing is the image quality here. Everything 2D within a window was blurry, though the desktop itself was not. This is probably a combination of drivers and *the problem* with 3D desktops. I had hoped that, being the big daddy of 3d desktops, Looking Glass would have overcome this... sadly, it has not. Window contents are, for me at least, blurry / hard to read.

I would have checked out the settings, such as screen resolution, to see if maybe it's all been set wrong, but none of those utilities seem to be here yet.

Anyway, the story of minimizing! Minimizing was a trial because of the sluggishness when I had Firefox open (by the way, this same sluggishness happened with the 3D browser demo so it's not just Firefox). I did it in the end, and it minimized. Minimized programs get a 3D preview in the dock thing, which I guess is rather cute but also kind of cluttery. I bet that'll be configurable some day. (Hopefully the whole dock will be removable, actually...)
I made the mistake of middle clicking on one of those previews, only to close Firefox and lose that message I told you about earlier. A new desktop has to be learned so it's not really their fault, but a bit of a weird way to do it. The problem I was having was that I just could not figure out how to unminimize Firefox!

I hate gestures, but my fiddling with them did show some interesting functionality. I can throw a window over to the right side of the screen, and fun stuff like that.

As I said earlier, those 3d objects that work on the desktop act in an identical way to everything else when minimized or moved to the side :)

There are some nice "fancy" effects, for example moving the pointer off a windowed app makes it fade away based on how far away the window is.


All in all, I think it's a neat idea but this is still very early days. It seems like it will be a long time before I'll be using Looking Glass, but I wish them luck in reaching that stage.
This project is already intriguing and has some neat ideas, but it needs a lot more polish and some better application support.

If I had to unify all this, I'd say that Looking Glass is being constrained too much by the 2D desktop world. The things that killed it were 2D programs, while the 3D programs ran fine. The only problem is that those 3D programs don't do much; they bounce around, but they currently serve little purpose. Some day maybe they will; maybe an HTML page will be interpreted into a 3-dimensional world instead of a 2-dimensional page; after all, half the point of HTML is to be read in numerous ways.
Maybe GUIs never needed to be 3D; maybe our heads prefer 2D interfaces and once we end up working in 3D it all ends up befuddled. We don't know for sure, though, since few have actually tried a full-on 3D desktop; maybe this whole other dimension will some day produce more than just potential prettiness and actually offer a new kind of organization.

Stable or not, Looking Glass is a very worthy experiment that could perhaps pave the way for even better, faster things to come.


For now, I'll stick with my 2D desktop and watch with much interest and with due appreciation for those who are taking on the challenge to revolutionize the desktop interface.
As someone said in the comments for that article, there is a lot going into simplifying desktops with stuff like voice recognition. That, too, is a very noble effort. In fact, I have to agree that voice recognition seems a lot more useful than a 3d desktop. However, it takes great dedication to take anything this far, and these guys clearly want to see stuff that's new; they want things pushed forward, and I would love to see it happen. (Just so long as it works in the end).

---

### Post by d3v1ant_0n3 on 2006-12-21
I've been watching PLG with interest for a while, but was never able to get it running. Installing now:D

---

### Post by talkingwires on 2006-12-21
Cool! I thought this was just a one-off tech demo, and didn't know people were still working on turning it into a real desktop environment. I'll hafta give it a whirl...

**Edit** - This thread probably shouldn't be in the Feisty forum.

---

### Post by deadlydeathcone on 2006-12-21
First, I must comment that the Ubuntu packages are of a very high quality - they even set up a separate gdm session!

As far as the project goes, after using it's simultaneously one of the most stupid and awesome things I've tried in a while.

---

### Post by elanthis on 2006-12-21
> Then I tried to use Firefox. I noticed that upon loading Firefox, the system had slowed to a crawl. The pointer was impossible to control (very sluggish), and key input had at least a 2 second delay. Upon minimizing Firefox, it all went back to the usual acceptable speed. Very weird. Essentially, I could not actually use - with any kind of speed - any "normal" 2D programs.

What hardware and drivers do you use?  I believe LG requires the same driver features that AIGLX/XGL/Compix require for running regular X apps.  If you can't run AIGLX or XGL with decent speed, LG is going to be just as big of a problem if running regular X apps.

---

### Post by Abandon on 2006-12-21
> **kejar31 said:**
> I thought it was dead but not only is it at 1.0 it also has Ubuntu packeges. Anyone try it out??

Yes I did. Installing as easy as can be, just download the 3 files and sudo dpkg -i filenames and log in with gdm and use looking glass in stead of Gnome.

I don't think it looks pretty. It is not fast en responsive like Gnome is. There are almost no programms visible in the menu, but ok..it's nice to play with. But after a few minutes it was over with the fun, I'm a Gnomer!

Made a picture [here]("http://www.digiplace.nl/pivot/entry.php?id=604").

---

### Post by apoclypse on 2006-12-21
There is no reason why compiz/beryl couldn't steal some ideas from LG. In-fact a lot of the suggestions/wishlists in the their respective forums (more beryl than compiz though) suggest stuff that looking glass already has, like window titles on the side, flippable windows, etc. I particularly like how the minimized windows look, you can see everyting without having to unminimize a window. That would be great to see in any desktop environment, though osx does something similar but not as cool. One thing I like about LG is the intergration. Thats what makes osx so great the fact that the widgeting system and the windows manager work together and everything is consistant. In-order to have that in linux, the DE devs are going to have to start supporting the composite extension throughout their desktop, not just the window manager. I see KDE doing this first as QT pretty much provides this type of functionality out of the box. I'm not sure if gtk can do it to, though I know they support cairo. Another reason I say KDE will reach this goal first is because they have a better history of intergration than gnome, a huge example is something as complex and robust as konquerer. 

Take note however, that I'm a gnome user and wouldn't touch KDE due to their over-abundance of UI elements. There is just way too much going on and thats just not pretty. I'm doubtful that this will change with KDE4 as there still isn't a clear KDE HIG for 4.

---

### Post by d3v1ant_0n3 on 2006-12-21
I had a play. And it's...strange. Very unintuitive, kinda ugly, and slow as hell on my machine.

Some nice ideas, but very clumsy.
I like the fact that it makes a new GDM session for it tho.

---

### Post by GarethMB on 2006-12-21
> **d3v1ant_0n3 said:**
> I had a play. And it's...strange. Very unintuitive, kinda ugly, and slow as hell on my machine.

Some nice ideas, but very clumsy.
I like the fact that it makes a new GDM session for it tho.

That's pretty much what I'd say too. It's a bit sluggish for me with my crappy graphics board. But I think some of its features would be good for usablity. Font's are awful for me, as I don't use GDM so they're not configured.

---

### Post by Zerocool10482 on 2006-12-21
I've install the debs but how do I run the program. Sorry I'm a newbie.:confused:

---

### Post by d3v1ant_0n3 on 2006-12-21
> **Zerocool10482 said:**
> I've install the debs but how do I run the program. Sorry I'm a newbie.:confused:


Logout. Select 'Project Looking Glass' from the sessions menu. Login. Get confused.

---

### Post by Cheizzz on 2006-12-21
I just checked it out (props for the installation, went perfectly!), but that moving background makes me feel sick. I cant work with this for more than a quarter of an hour, or I'l be vomiting at my monitor! :(

---

### Post by Sirin on 2006-12-21
Looks like Compiz finally has some competition. The 3D Linux desktop wars has now begun. Who shall win? Novell or Sun? ONLY TIME WILL TELL. :p

---

### Post by rado_london on 2006-12-21
Hey I downloaded the deb files but the JDK one found some error. Anyone knows why?
Here is the error:
rado@ubuntu:~$ sudo dpkg -i Desktop/lg3d_jdk1.6.0_i686.deb 
(Reading database ... 117638 files and directories currently installed.)
Unpacking lg3d-jdk (from Desktop/lg3d_jdk1.6.0_i686.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing Desktop/lg3d_jdk1.6.0_i686.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/share/lg3d-jdk/jre/lib/i386/server/libjvm.so')
Errors were encountered while processing:
 Desktop/lg3d_jdk1.6.0_i686.deb

Anyone knows how to fix it?

---

### Post by lyceum on 2006-12-21
are there any screen shots?

---

### Post by prizrak on 2006-12-21
A Java based 3D desktop.... Wonderful.....

---

### Post by riven0 on 2006-12-21
I don't know if this is just me or what, but I couldn't type in the terminal. Trying to browse with firefox made the mouse all jumpy, too. And why are the backgrounds so blurry? 

Other than that, I think its a good concept... just needs a lot more work to make it usable.

---

### Post by d3v1ant_0n3 on 2006-12-21
> **riven0 said:**
> I don't know if this is just me or what, but I couldn't type in the terminal. Trying to browse with firefox made the mouse all jumpy, too. And why are the backgrounds so blurry? 




See I thought that was just me :p

---

### Post by Phatfiddler on 2006-12-21
Trying it out now...I'll post my results.  I have compiz running smoothly with AIGLX so maybe it will be decently fast.

ATI mobility 7500
1.5Ghz M processor
512 MB RAM

---

### Post by Phatfiddler on 2006-12-21
Can't get past the login screen...I get the "logged in less than 10 seconds" error.  I'll see if I can post the error report.

EDIT:  Error report
```

error opening the security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy

Could not init font path element /usr/share/fonts/X11/URW
Could not init font path element /usr/share/fonts/X11/Speedo
Could not init font path element /usr/share/fonts/X11/TrueType
Could not init font path element /usr/share/fonts/X11/uni: unscaled
Could not init font path element /opt/kde3/share/fonts
Could not init font path element /var/lib/defoma/x-ttcidfont-conf .d/dirs/TrueType

Xlib: connection to ":0.0" refused by server
Xlib: no protocol specified

/usr/bin/xhost: unable to open display 0
```

I checked for the security file it complained about, but apparently the location /usr/X11R6/lib/X11/xserver/ doesn't even exist on my PC.  Maybe that's why it can't find the SecurityPolicy;)

---

### Post by soze on 2006-12-21
I can't install any of the three packages. 
```
sudo dpkg -i lg3d_jdk1.6.0_i686.deb
(Reading database ... 242330 files and directories currently installed.)
Unpacking lg3d-jdk (from lg3d_jdk1.6.0_i686.deb) ...
dpkg: error processing lg3d_jdk1.6.0_i686.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d_jdk1.6.0_i686.deb

```

The other two packages give similar errors.

---

### Post by Phatfiddler on 2006-12-21
Nevermind, i fixed the problem

sudo apt-get remove lg3d*

---

### Post by gmclachl on 2006-12-21
Has anyone managed to get looking glass running with dual monitors. I installed the packages just fine, but when i try to select the Looking Glass session I just end up with a blank screen. 

George

---

### Post by paridoth on 2006-12-22
> **Phatfiddler said:**
> Can't get past the login screen...I get the "logged in less than 10 seconds" error.  I'll see if I can post the error report.

EDIT:  Error report
```

error opening the security policy file /usr/X11R6/lib/X11/xserver/SecurityPolicy

Could not init font path element /usr/share/fonts/X11/URW
Could not init font path element /usr/share/fonts/X11/Speedo
Could not init font path element /usr/share/fonts/X11/TrueType
Could not init font path element /usr/share/fonts/X11/uni: unscaled
Could not init font path element /opt/kde3/share/fonts
Could not init font path element /var/lib/defoma/x-ttcidfont-conf .d/dirs/TrueType

Xlib: connection to ":0.0" refused by server
Xlib: no protocol specified

/usr/bin/xhost: unable to open display 0
```

I checked for the security file it complained about, but apparently the location /usr/X11R6/lib/X11/xserver/ doesn't even exist on my PC.  Maybe that's why it can't find the SecurityPolicy;)

got the exact same problem, to bad because i wanted to check it out

---

### Post by rado_london on 2006-12-22
> **soze said:**
> I can't install any of the three packages. 
```
sudo dpkg -i lg3d_jdk1.6.0_i686.deb
(Reading database ... 242330 files and directories currently installed.)
Unpacking lg3d-jdk (from lg3d_jdk1.6.0_i686.deb) ...
dpkg: error processing lg3d_jdk1.6.0_i686.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d_jdk1.6.0_i686.deb

```

The other two packages give similar errors.

I cant do it either](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by Bloch on 2006-12-22
I am writing this now from Looking Glass.
I have Dapper 6.06 on a mediocre system - Celeron 2.4GHz (the cheaper one with only 128MB cache) and a 64MB Nvidia graphics card.

It's usable, but too slow to be practical. There is a lag between mouse movement and the movement of the cursor, as in java-based games. But the fonts and everything is beautiful.  

I'm still figuring it out - is there no file browser built-in? I have to start all programs from the terminal. Looking Glass comes supplied with ots own applications plus starters for firefox, but there is no general gnome / debian menu.

Give it a try - I didn't think my computer would be up to it.

---

### Post by progster on 2006-12-22
Running looking glass at the moment, though I like the idea I'm not liking the experience. 

I find the entire desktop counter-intuitive, it took me 5 minutes to get my application back after I somehow dragged it to the site. All in all the pretty 3D effects don't add any use to me,   at best they annoy me. I think a 3D desktop is a good idea, but I doubt SUN did any usability research for their desktop...


That's my 2 cents

---

### Post by aidanr on 2006-12-22
> **paridoth said:**
> got the exact same problem, to bad because i wanted to check it out

i got the same thing, you can still check it out though, just open a terminal and type the following

```
cd /usr/share/lg3d
./bin/lg3d-dev
```

also try

```
./bin/lg3d-app
./bin/lg3d-app -f
```

the -f switch is fullscreen

---

### Post by gbadger on 2006-12-23
Installation went smoothly for me. Lg3d was very choppy until I made the following changes to my xorg.conf. I have an nvidia 6600gt and beta drivers installed since I'd previously been running beryl.

Added this section:

```

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

and added:

```

Option "RenderAccel" "true" 

```

To the Device section

---

### Post by Shampyon on 2006-12-23
> **rado_london said:**
> I cant do it either](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

> Preconfiguring packages ...
lg3d-java3d failed to preconfigure, with exit status 1
(Reading database ... 132772 files and directories currently installed.)
Unpacking lg3d-java3d (from .../lg3d-java3d_1.5.0_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/lg3d-java3d_1.5.0_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/lg3d-java3d_1.5.0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Same here... the other two parts of the package install fine for me. It's just the lg3d-java3d bit that fails.

---

### Post by Shampyon on 2006-12-24
One of the error messages I got said that it couldn't install the core because lg3d-java3d wasn't installed. I tried installing it by itself, before installing the other two components, and got this error:
> sudo dpkg -i lg3d_java3d*.deb
(Reading database ... 132828 files and directories currently installed.)
Unpacking lg3d-java3d (from lg3d_java3d_1.5.0_i686.deb) ...
dpkg: error processing lg3d_java3d_1.5.0_i686.deb (--install):
 subprocess pre-installation script returned error exit status 1
Errors were encountered while processing:
 lg3d_java3d_1.5.0_i686.deb

The results of my fglrxinfo, in case it's relevant:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700/X550 Series Generic
OpenGL version string: 2.0.6011 (8.28.8)

---

### Post by Mr. Picklesworth on 2006-12-24
Try it in the last possible order (there are three packages you can start with) and tell us what happens.

---

### Post by darkhatter on 2006-12-24
I'm running it on windows and it runs very good, like I can't tell I'm running a 3d desktop using java

---

### Post by Shampyon on 2006-12-25
> **Mr. Picklesworth said:**
> Try it in the last possible order (there are three packages you can start with) and tell us what happens.

I've tried, and unfortunately the order doesn't seem to matter. No matter which comes first and which ;last, I get the  > dpkg: error processing lg3d_java3d_1.5.0_i686.deb (--install):
 subprocess pre-installation script returned error exit status 1

error. And without lg3d_java3d, the core won't install. Damn :(

---

### Post by darkhatter on 2006-12-25
is it possible to run apps that I have installed on my computer with it, cause on the windows version I couldn't get any of my apps to run. or even show up.

---

### Post by Shampyon on 2006-12-30
Still can't get it to install. Still hitting the same error. Can't find any fixes elsewhere. All the other "error exit status 1" that I've found online refer to other apps, such as the Mozilla Flash plugin, but they all seem to have similar solutions: making a directory. Could it be that lg3d_java3d_1.5.0_i686.deb is trying to install to a directory that doesn't exist, and isn't trying to make a new appropriate directory?
Or do I just have a broken lg3d_java3d_1.5.0_i686.deb package and need to re-download it?

---

### Post by BLTicklemonster on 2006-12-30
The repositories are dead, and the java debs won't install.

---

### Post by neowolf on 2006-12-30
I see why some people might like it, but its just a useless proof of concept thing, the desktop works better in 2D for the current generation of software IMO.

---

### Post by BLTicklemonster on 2006-12-30
Reiterating...

these are dead, or at least I can't get to them:

```
## LG3D repsoitories
#deb http://javadesktop.org/lg3d/debian stable contrib
#deb http://javadesktop.org/lg3d/debian testing contrib
deb http://javadesktop.org/lg3d/debian unstable contrib
```

and this won't even load

[http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian)

of course you see they can't spell repositories (that list came from their website) so God knows why their debs won't install, lol.

I can use archive manager to extract all the files, but even then I wouldn't know what to do with them.

---

### Post by K.Mandla on 2006-12-30
It worked fine for me. I downloaded the debs last night and installed via *sudo dpkg -i *.deb*.

[center][[IMG]http://img412.imageshack.us/img412/3305/lgscreen00yf4.th.jpg[/IMG]](http://img412.imageshack.us/my.php?image=lgscreen00yf4.jpg) [[IMG]http://img412.imageshack.us/img412/7605/lgscreen01wu1.th.jpg[/IMG]](http://img412.imageshack.us/my.php?image=lgscreen01wu1.jpg) [[IMG]http://img412.imageshack.us/img412/1368/lgscreen02xn8.th.jpg[/IMG]](http://img412.imageshack.us/my.php?image=lgscreen02xn8.jpg)[/center]

Runs great, even on my lame video card.

---

### Post by BLTicklemonster on 2006-12-30
You know, that looks familiar... I actually did have something like that in windows a few years ago. 

I installed from the .bin file, and can't find the install directory, lol. 

Oh well, no biggie, I'd probably like it less than beryl anyway.

---

### Post by gjtoth on 2006-12-30
> **d3v1ant_0n3 said:**
> Logout. Select 'Project Looking Glass' from the sessions menu. Login. Get confused.

I tried this and there is no selection like this in the Sessions menu.  How did you get it there?

---

### Post by K.Mandla on 2006-12-30
I've been starting it from a command line, with this: 

```
/usr/share/lg3d/bin/lg3d-app -f
```

I don't use a login manager, so I didn't bother with the GDM part.

---

### Post by BLTicklemonster on 2006-12-30
```
bill@bill-desktop:~$ /usr/share/lg3d/bin/lg3d-app -f
bash: /usr/share/lg3d/bin/lg3d-app: No such file or directory
bill@bill-desktop:~$ 

```

:(

---

### Post by gjtoth on 2006-12-30
> **BLTicklemonster said:**
> ```
bill@bill-desktop:~$ /usr/share/lg3d/bin/lg3d-app -f
bash: /usr/share/lg3d/bin/lg3d-app: No such file or directory
bill@bill-desktop:~$ 

```

:(

try ~/lg3d/bin/lg3d-app-full

It takes a few seconds to open... be patient.

---

### Post by BLTicklemonster on 2006-12-30
lmao, no, that wasn't the problem. the problem was, it installed to my desktop, So I have to path it there instead of /usr/share.

And it loaded up quickly enough. Now what do I do?

---

### Post by gjtoth on 2006-12-30
> **BLTicklemonster said:**
> lmao, no, that wasn't the problem. the problem was, it installed to my desktop, So I have to path it there instead of /usr/share.

And it loaded up quickly enough. Now what do I do?

Play.  ;)

---

### Post by BLTicklemonster on 2006-12-30
(RUNS BETTER IN FLUXBOX, BTW :) )

Wild stuff. OH, and thanks, dude!

---

### Post by Shampyon on 2007-01-01
I quit trying to use the Ubuntu versions and tried the generic Linux megabundle. It installed, and I can start it using this command:
> **gjtoth said:**
> ~/lg3d/bin/lg3d-app-full

It starts up inside Gnome, though, so it chugs a bit, but at least now I can see what it's like. It's damn cool.

---

### Post by KuriKai on 2007-01-01
I get this erro when trying to start it :(
```
dave@dave-desktop:~$ /usr/share/lg3d/bin/lg3d-app -f

Starting up Project Looking Glass...

Could not init font path element /usr/share/fonts/X11/URW, removing from list!
Could not init font path element /usr/share/fonts/X11/Speedo, removing from list!
Could not init font path element /usr/share/fonts/X11/truetype, removing from list!
Could not init font path element /usr/share/fonts/X11/uni:unscaled, removing from list!
Could not init font path element /opt/kde3/share/fonts, removing from list!
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/usr/bin/xhost:  unable to open display ":0"
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

```

---

### Post by oldroger on 2007-01-04
> **KuriKai said:**
> I get this erro when trying to start it :(
```
dave@dave-desktop:~$ /usr/share/lg3d/bin/lg3d-app -f

Starting up Project Looking Glass...

Could not init font path element /usr/share/fonts/X11/URW, removing from list!
Could not init font path element /usr/share/fonts/X11/Speedo, removing from list!
Could not init font path element /usr/share/fonts/X11/truetype, removing from list!
Could not init font path element /usr/share/fonts/X11/uni:unscaled, removing from list!
Could not init font path element /opt/kde3/share/fonts, removing from list!
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/usr/bin/xhost:  unable to open display ":0"
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

```

Don`t know about the font story - same for me. But the line

"Xlib: connection to ":0.0" refused by server"

comes from the X server, because seemingly you need display rights for root to start the desktop.

So type in

```
xhost + local:root
```

and start the application you want, e.g.

```
./bin/lg3d-app -f
```

BTW in some of the application bash files in lg3d/bin xhost is used the wrong way (ubuntu uses a strange syntax!! - "```
xhost + localhost
```" has to be replaced with "```
xhost + local:
```").

But I`m still not able to log in over session manager. The  "Xlib: connection to ":0.0" refused by server" thing again, but haven`t figured out where to set the display rights yet.

And I think the right fonts could be nicer then the now used ones. Looking through some forums, suse users have them loaded in the xorg.conf, but I even haven`t them on the machine.

And yes! I tried the ubuntu downloads. Better success with the generic linux bundle on ubuntu?

---

### Post by kuja on 2007-01-04
I tried it a couple weeks ago. If only it weren't ... ugly in every aspect, and didn't have that terribly annoying cursor, and had some higher quality wallpapers, I'd think about using it ... probably wouldn't though.

---

### Post by Lucho on 2007-01-06
oops, double post

---

### Post by Lucho on 2007-01-06
Well, I installed Looking Glass on my installation of DreamLinux 2.2 MultiMedia
Edition. I added the lines to my sources.list, did the apt-get thang, and... :-k 
 
  To be honest, it installed without a hitch, and from GDM it boots up fine. *But*,
(and you knew that was coming, right? :rolleyes: ) This desktop is still just a proof
of concept toy, not a fully-functional desktop. Performance is acceptable, but sluggish,
and I don't appreciate having my apps refuse to un-minimize; does anybody else have
problems with minimized apps?

     About the wallpaper: As someone who only uses my own material, I don't like the
selection. However, it's blurry because it's a very small image blown up huge. Do a right-
click on that funky task bar and you'll see it's true size. And that your desktop is 
panoramic ;) 

  All in all, a fun toy for parties:cool: :-k

---

### Post by truthfatal on 2007-01-10
I was expecting it to be more sluggish after reading this thread...
But It wasn't unacceptably slow on my Sempron 2600+ (1024MB Ram) considering what it's doing.

I don't know what was causing it to 'drop' my keyboard, but I imagine it will be fixed in future releases. I could probably use this DE once it gets its kinks worked out.

There is a lot of Kinks though....

---

### Post by bernardfrancois on 2007-01-10
I just installed it on ubuntu dapper for amd64, but it doesn't seem to work.

If I try to start it as a session while logging in, I only see the mouse cursor and a brown background.
When I start it in a terminal after logging in, I get the following error:
```

Java 3D WARNING : reported GLX version = 1.2
WARNING: Unable to load display configuration
SEVERE: Unhandled exception, see /var/tmp/lgserver.log for details.

```

In that log file I see there's a NullPointerException:
```

java.lang.NullPointerException: Canvas3D: null GraphicsConfiguration
...

```

I added an "Extensions" section in my xorg.conf file, making the configuration of my video card look like this:
```

Section "Device"
    Identifier     "NVIDIA Corporation NV28 [GeForce4 Ti 4800 SE]"
    Driver         "nvidia"
    Option "RenderAccel" "true"
EndSection

Section "Extensions"
    Option "Composite" "Enable"
EndSection

```

When I start it now (still from command line), I get the same error, but this time in a java window with two tabs (Message and Trace).
In the Message tab, I get the following text:
```

A severe error occured !
You should save your work as quickly as possible.
Looking Glass may be able to continue to work, but no guarantee...
Please report the error using the crash reporter : 
http://pinaraf.robertlan.eu.org/LG3D/crash_reporter

Unhandled exception, see /var/tmp/lgserver.log for details.

```
The exception tab shows the same NullPointerException.

A few months ago I tried to install XGL, but it failed to work. Maybe I messed up too much?
Note that I don't have any performance problem with OpenGL applications.

---

### Post by floke on 2007-01-11
Have just tried Looking Glass. Couldn't install from the repos due to dependency issue (?!?) so had to use the Debian binaries from the website. Anyway, had a play and guess what? It's a joke. I'm left with one outstanding question....why?

---

### Post by bernardfrancois on 2007-01-11
Apparently, with the last xorg update, my nvidia driver got broken. Re-installing it with the envy script made it work again. Now I'm using project looking glass.
Sometimes it freezes for a few seconds, a problem I also have with netbeans, because I 'only' have 512mb ram.

It's has some nice ideas, but it's a bit clumsy to use. But I'll check out the tutorials at [https://lg3d.dev.java.net/tutorial/](https://lg3d.dev.java.net/tutorial/) .

---

### Post by Balachmar on 2007-01-14
I can't install it from either the repos or the debs.
I get the same install error as some others here. About some preconfigure thing failing. How did the rest install it? I really want to avoid having to install stuff without using the package manager.

---

### Post by Shampyon on 2007-01-16
I tried the debs and the repos, and they failed on mine. I used the generic linux megabundle, and that worked for the most part :P

---

### Post by bernardfrancois on 2007-01-19
The best way to install it is to use the ubuntu .deb packages. They will also appear in Synaptic (as lg3d-core, lg3d-java3d, and lg3d-jdk).

Before installing anything, make sure your video cards supports 3d accelleration and the driver is properly installed. You can test this by running an OpenGL screensaver or game and see if it works fluently.

---

### Post by laxmanb on 2007-01-20
It seems great as a proof of concept thing!! best of luck to the developers! 

hopefully there'll be better themes and wallpapers soon...

i would so like to try this... but i can already imagine the way this would work on my 810i and 256MB RAM...

---

### Post by finferflu on 2007-02-05
Hopefully it will be *fast*!
It's too exceedingly unacceptably sloooow (on a P4, 2.6 GHz, 512Mb RAM), I can't enjoy such a slow desktop. Moreover, xterm does not work, the words that I type don't appear, and everything I open likes to crash...

It's only at its first stage, granted, but I can't take any slowness when I use a computer (I mean, I don't want to compromise performance with cosmetics).

My 2 &#8364;cents.

---

### Post by fuscia on 2007-02-05
> **bernardfrancois said:**
> Before installing anything, make sure your video cards supports 3d accelleration and the driver is properly installed. You can test this by running an OpenGL screensaver or game and see if it works fluently.

wouldn't this be simpler?

*glxinfo | grep "GLX version"*

should get *GLX version: 1.3*, if you're good to go, unless i'm mistaken (not sure if 'or better' counts).

---

### Post by Rodneyck on 2007-02-10
Here's another piece on Looking Glass...

[http://linux.wordpress.com/2007/02/10/opensuse-installing-and-running-looking-glass-3d](http://linux.wordpress.com/2007/02/10/opensuse-installing-and-running-looking-glass-3d)

---

