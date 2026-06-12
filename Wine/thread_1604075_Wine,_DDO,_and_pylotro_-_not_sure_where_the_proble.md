---
title: "Wine, DDO, and pylotro - not sure where the problem lies"
date: 2010-10-23
forum: Wine
---

### Post by brndndvr on 2010-10-23
Hey,
I've been trying to get dungeons and dragons online to work on my new ubuntu system and have hit a snag that I'm not sure how to address.

I followed the WineHQ instructions on how to get the game up and running and seem close to getting it to work.  When I run the patch option, I occasionally get this message:

  	 	 	 	p { margin-bottom: 0.08in; }  "Downloading client_surface.dat-7704......................................
 ..
 ........................................
 ...................................
 ..............
 ..........................................
 Failed!
 Failed!
 Failed to download data: Unknown win32 error: 12007
 ***** Finished ***"**

I've had it happen twice with different .dat files.  When I try to log in, all I get is a screen that says "output" and a blank screen.  It only gives me the option to abort.  has anyone run into a similar problem or have any ideas how to fix this?

---

### Post by brndndvr on 2010-10-23
Here's a few screenshots of what happens:

In the first shot, it's my launcher.  Everything appears to be working fine.  I get the news updates, I can scroll down and choose the server I want, and I am able to enter my account info and password with no problems.

In the second shot, I am showing what happens when I hit 'log in'.  I'm hoping someone is able to help me figure out why I'm getting such a weird window after I log in...

---

### Post by brndndvr on 2010-10-23
This may also be important, but after a couple hour of googling for a fix, I've decided I need a break to rest my eyes.  If someone could PLEASE help me, I'd appreciate it greatly.

In the pylotro launcher underneath my log in information, there's a box that says this:

"initialising, please wait...
available languages checked
fetched details from GLS data centre
Realm list obtained
World queue configuration read"

No matter how long I wait, the launcher never finishes initialising.

I remember reading somewhere about how the first time I try to launch it, it will fail, but it does this every time and never makes any progress.

---

### Post by buzzmandt on 2010-10-24
I have problems with the current update that are now all fixed, but not the same problems as you have here.

first really need to know what your video card is and that you have the proprietary drivers installed, it's a must have.

Second and very important is that you copied the installed files from a windows installation.  thats the game files that end up in windows/program files folder and not the files that the ddo downloader save to the comp.  linux cant install the game from ddo installer. 

third,  if you havent already you should add the [www.winehq.com](www.winehq.com) repository to your sources. just go to [http://www.winehq.com](http://www.winehq.com) and follow the instructions for ubuntu

next, again if you haven't already, from terminal run
```
sudo apt-get update && sudo apt-get install winetricks
```

once you have winetricks installed in terminal just type 
```
winetricks
```

in the selection field select vcrun2005 vcrun2008 and d3dx9.  You can multiselect them and install them at the same time.  

now run winecfg from terminal and set windows version: windows 2000, On the audio tab set hardware acceleration: emulated and on the graphics tab set vertex shader support none, everything else should work default.

I have ddo/pylotro running on 4 laptops with intel video on each and 1 desktop with a nvidia fx5600 and it runs really good. the only real difference is that all of my comps are kubuntu, not much different under the hood so we should be good there.

I'm loving this game and will try to help you all i can. lemme know sumpin

---

### Post by brndndvr on 2010-10-24
Just wanted to say thank you so much for being willing to help.  I love the game, but don't want to shell out a lot of $$ just to play it on windows.  Plus, I like the idea of ubuntu a whole lot more than windows..I'm trying to learn how to use it so I can get away from the windows crap.  

I'm buried in homework and my senior research project so I probably won't get to trying any of this for another day or two, but I just want you to know your advice hasn't gone unnoticed.  Once I get a chance, I'll let you know what's up after I try all your ideas

**EDIT**
Graphics card info:
NVIDIA - GeForce FX5200  Memory = 128 MB  (Not top of the line, but this should do the job, shouldn't it?)

The proprietary drivers actually weren't installed, so i took care of that this evening.  DDO still isn't working, but now when I try to load up supertux I get a black screen that says something like "this video mode can't be displayed"  Why would installing my proprietary driver do this?!

---

### Post by brndndvr on 2010-10-25
When I tried installing winetricks, I got this message:

"Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package winetricks is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'winetricks' has no installation candidate
bandjforever@devries:~$ winetricks
winetricks: command not found"

Any idea what to do next? I feel so lost :confused:

---

### Post by buzzmandt on 2010-10-25
copy/paste this into terminal
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```
then do
```
sudo apt-get update && sudo apt-get install winetricks
```

lemme know if that works

---

### Post by brndndvr on 2010-10-26
Thanks, buzzmandt!
Those copy/paste things seem to be working.  I am installing vcrun2005 vcrun 2008 and d3dx9 as I type.  I'll update this once it's done and I try loading the game. 

I followed the instructions from wineHQ as best I could and it doesn't talk at all about installing winetricks or vcrun or any of that stuff (at least I didn't see it)  Is the website out of date perhaps?

**EDIT**
So I just logged in and everything is now working.  Thank you so much! 
However, the game is extremely choppy and hard to play.  I'm going to play around with the graphics settings and try to figure out what type of settings I need.  Buzz, what kind of settings are you using?

I think there's only 512 megs of ram under the hood of this desktop, would adding another 512 or 1 gig help with the choppiness?

---

### Post by buzzmandt on 2010-10-26
def not good. My lowest spec machine that runs ddo/linux is slightly better than what you have. It runs a little chopy in outside areas, but inside dungeons and buildings it runs fine.  it has about 1.5 g memmory and an nvidia 5500 fx w/256 megs vid mem. also it is a 2400+ athlon (which i think is around 1.8 ghz but not sure).

memory is dirt cheap (I think another 512 at least would be in high order) and a 6000 series gt runs around 50 bucks last i checked. still would be less than a microsoft license and then should run ddo fine and u can still keep the awesomeness that is linux.

also i posted an updated thread into winehq appdb for ddo a few days ago, so far it hasn't been approved (but also not denied, so i think the maintainer just hasn't bothered with looking at it yet). I have the winetricks instructions in it.

My other computers that run ddo/linux are all laptops with around the same specs, about 2ghz with 2 gigs ram and intel mobil 4 series graphics.

Also, one last side note, they all ran ddo very choppy under lucid, but under maverick with the new xorg they all run ddo great. judge that last statement on your own, just telling my experience of it. but i still think you need to up your system just a bit.

-buzz

PS, winehq now has my test data, [http://appdb.winehq.org/objectManager.php?sClass=version&iId=21734](http://appdb.winehq.org/objectManager.php?sClass=version&iId=21734)

---

### Post by brndndvr on 2010-10-26
I noticed that when I was playing, while i was in the bars the game wasn't so choppy, but once i got out into the world, it got a lot worse.  It will work passably if I put the resolution to 800X600, but I will probably at least get some more ram in there when I get a chance.  
My system is running maverick, so i'm thinking I just need to up my specs a bit, but hey, when you spend $40 for a computer, monitor, keyboard, and speakers (like I did), it's not a big deal to up the specs :)

I know I already said this, but thanks so much for your help.  I was starting to think ddo was a lost cause on this system after failing to get it installed after following winehq's tutorial to the "T"

If winehq needs any testimonials to verify that your walkthrough works, I'd be happy to say that it does indeed work wonderfully.

---

### Post by buzzmandt on 2010-10-26
if you want you can follow the link to the wine appdb post i posted and comment on it. glad it's working for you, send me a private message on your character name if you're on argonnessen, that's where i be. good luck and see you in stormreach :)

---

