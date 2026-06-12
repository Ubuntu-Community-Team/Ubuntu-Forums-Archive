---
title: "Ubuntu + Mezzo"
date: 2005-07-15
forum: The Cafe
---

### Post by Sasayaki on 2005-07-15
Those of you who follow Symphony OS ([http://www.symphonyos.com/](http://www.symphonyos.com/)) are well aware of Symphonys' Mezzo desktop system, which is neither KDE nor Gnome, and focuses extensively on ease of use. This seems to fit perfectly with the Ubuntu philosophy of ease of access, as easier access means easier use. Although it's only in Alpha phase right now, it has had three Alpha releases thus far and by all accounts the fourth will be almost release quality. Follow the above-mentioned link and check out some of their desktop screenshots, or the very lazy may click [http://www.symphonyos.com/screenshots/a4-ss2.png](http://www.symphonyos.com/screenshots/a4-ss2.png) 

So, I ask- given that Mezzo does so very nicely follow the Ubuntu philosophy, does the Ubuntu team have any plans to incoperate the Mezzo desktop into Ubuntu, as an optional metapackage perhaps, or even as the main implimentation? If this was done, it is my opinion that Ubuntu's ease of use would skyrocket (beyond its' already lofty level). Thoughts?

---

### Post by SGC on 2005-07-15
IMHO Mezzo seems to be a little bit complicated than the current desktops, And I think with Mezzo you will not be able to add stuff like superkaramba or gDesklet

---

### Post by zeroK on 2005-07-15
[QUOTE=SGC]IMHO Mezzo seems to be a little bit complicated than the current desktops, And I think with Mezzo you will not be able to add stuff like superkaramba or gDesklet[/QUOTE]
 Esp. since this looks like a combination of Rox, FVWM and gDesklets/Superkaramba. Not really my taste.

---

### Post by poofyhairguy on 2005-07-15
Mezzo is pretty new...

---

### Post by Wolki on 2005-07-15
[QUOTE=SGC]IMHO Mezzo seems to be a little bit complicated than the current desktops, And I think with Mezzo you will not be able to add stuff like superkaramba or gDesklet[/QUOTE]

That's because they already have the desktop applets built right into the system. Why use gDesklets when you have the Mezzo desklets?

And it's not complicated, but different. Everything that's different seems more complicated while you'er not used to it yet. There are horrible things wrong with computing today, while people are working on improvements most of these are radically different from what we know today. There's Mezzo, there's Gnome: Project Topaz, and - even more radically different - the Archy project which basically seems to drop the mouse again (!) in favor of keyboard commands (and yes, it's pretty well thought out, and the mopuse will have a use in later versions but not for what we use it today). Thing is, you can't make something better and still keep it the same.

As for Mezzo on Ubuntu, the Symphony developers have said that they will likely offer Mezzo for use on other systems. But since it's so new and will probably be in alpha for quite some time, don't expect a well working Ubuntu version for quite some time. 

>  Esp. since this looks like a combination of Rox, FVWM and gDesklets/Superkaramba. Not really my taste.


Not quite.it's based on the idea that the edges are the most valuable place on the screen, and puts all things important to normal use there (Computer settings, Programs, Files, ans - possibly - Trash). It also removes hierarchical menus like the Start button or Applications Menu because they are hard to use (meaning it's easy to make errors when using your computer fast, like moving your mouse a little too far and accidentally going into a different submenu. While it's based on rox and fvwm with desklet-type stuff, it's more than the sum of its parts :)

There's some info on the design of Mezzo here: [http://homepage.mac.com/jasonspisak/Mezzo/Menu3.html](http://homepage.mac.com/jasonspisak/Mezzo/Menu3.html)

---

### Post by super on 2005-07-15
looks interesting, maybe i'll add it to my already huge collection of DEs and WMs.

---

### Post by bgstratt on 2005-07-15
I burned a copy the other night and tried it a little....I like the thought of the corners being prime real estate for menus, more or less, I didn't like the fact that the entire background becomes the menu though.  I'll have to play with it some more to see what I really think though, but so far, they have some good ideas, but I don't know if they are really all that great.

---

### Post by super on 2005-07-15
Just wanted to say that I really think distro's and users should pay more attention to FVWM (which i understand that mezzo is based on). IMHO it ranks as one of the best pieces of software in the open source world. It's customizability, efficiency, and functionality are incredible. Symphony's Mezzo desktop is just an example of the almost limitless potential of FVWM.

---

### Post by maruchan on 2005-07-15
super, specifically what about fvwm makes it so great? Can you give any examples? I look at screenshots and don't see anything particularly great about it, but I'm willing to try it if it's really that good.

---

### Post by super on 2005-07-15
@ maruchan

i guess it really depend on what the user prefers. For example FVWM can be configured to use mouse strokes, so when (in my setup) i hold the right-mouse button and make a line (imaginary) from left to right, FVWM moves me to the desktop on the immediate right of my current desktop (and vice-versa: right to left moves me left) I find this useful and saves time. i don't know any other WM that supports this. (i could be wrong.)

also i can use FVWM (along with ImageMagick) to draw thumbnails when i minimize (or iconify) my programs. so i use a script in FVWM to invoke ImageMagick when i click the minimize button. The image gets copied to an engage (the best dockbar for linux) folder and appears as a thumbnail in engage which can then restore the app when i select it. i don't know any other WM that supports this. (again i could be wrong.)

plus there are a myriad of other things that it does that i simply find more convenient. But I think that the biggest thing it has going for it is it's flexibility. It is similar to linux itself in than it can be whatever you want it to be.

but hey, it's all about what you like, no?

GO Mezzo!

(love the avatar btw. very chillin)

---

### Post by maruchan on 2005-07-15
Hm...not to derail the thread, but is there an install howto somewhere? Sounds cool to me.

---

### Post by super on 2005-07-15
@maruchan

the package is in universe i think, but if you add this to your sources.list

deb	[http://noxa.de/~sbeyer/debian/fvwm](http://noxa.de/~sbeyer/debian/fvwm) unstable main
deb-src	[http://noxa.de/~sbeyer/debian/fvwm](http://noxa.de/~sbeyer/debian/fvwm) unstable main

and install "fvwm-unstable" and accompanying modules you will get the tranclucency patch already applied to FVWM. (yay  \\:D/ )

you can find some good configs at guistyles.com
[http://oceanic.wsisiz.edu.pl/~slabosz/wordpress/?page_id=9](http://oceanic.wsisiz.edu.pl/~slabosz/wordpress/?page_id=9)

and the FVWM forums
[http://fvwm.lair.be/](http://fvwm.lair.be/)

@anybody else
has anyone tried symphony yet? what did you think of it?

 (feeble attempt to get post back on topic  ;-) )

---

### Post by senectus on 2005-08-03
FVWM aside, this mezzo concept is wild!

I love it.. conceptually Ubuntu could really get into this and make a HUGE impact on the "New User" or "Less Adept User" fronts.
I understand that many of the better skilled guys and Dev's may not like it.. but this sort of innovation is just what many PC users need to make their computing experience a happier/easier one.

I wonder how hard it would be to make it look "Ubuntu slick" with all the apps Ubuntu normally has.

I may have to play with the concept I think.. :-D

---

### Post by UbuWu on 2005-08-03
It will probably installable in Ubuntu soon, from the website:

> 1. If the little bit of info on the Debian Core Consortium is true (and I have no inside knowledge of this) we would have true compatibility with Progeny, Linspire, and Xandros along with other members of the consortium as well as with the core Debian. I am hoping to hear more from Ian in the coming days about the DCC if he chooses to let me know some more, though, if he does, I may be asked to keep some or all of it quiet until any official announcement from the major players there.
2. The compatibility road goes both ways and this would also mean that the Mezzo Desktop Environment and Symphony OS systems would be available as components which could be installed easily on these other distros.


---

### Post by Freddy on 2005-08-03
I think mezzo and SymphanyOS can be a great thing but it's not really there yet. With this alpha4/beta release, we should more be able to see if the wait for a stable version is gonna be worth it, as of now there's not that much to do with the system for a enduser like me but its' allways fun to play around with new things = )

/Freddan

---

### Post by ubuntu_demon on 2005-08-04
cool stuff!

here's the whitepaper :
[http://homepage.mac.com/jasonspisak/Mezzo/MezzoGreypaper.pdf](http://homepage.mac.com/jasonspisak/Mezzo/MezzoGreypaper.pdf)

here are the ui "laws" :
[http://www.symphonyos.com/laws.html](http://www.symphonyos.com/laws.html)

We can learn from most of this laws and the whitepaper!

I thought a bit about it. I don't want mezzo but something very close to mezzo but implemented in gnome or on top of gdm/gnome. Then we can still have project utopia (for example automount) and Ubuntu developers can build on their previous work.

[quote=super]
i guess it really depend on what the user prefers. For example FVWM can be configured to use mouse strokes, so when (in my setup) i hold the right-mouse button and make a line (imaginary) from left to right, FVWM moves me to the desktop on the immediate right of my current desktop (and vice-versa: right to left moves me left) I find this useful and saves time. i don't know any other WM that supports this. (i could be wrong.)
[/quote]

I want this in gnome! This is a bit related : "Live Updating Workspace Switcher" see :
[http://blogs.gnome.org/search/seth?q=cairo&submit=Search](http://blogs.gnome.org/search/seth?q=cairo&submit=Search)

I want the other stuff from there also. I want a hardware accelerated desktop like mac OS X has.

from the laws :

> 
5.Configuration gluttony must be stopped. Thank god for open source. There comes a point at when the UI is hidden, drilled, stacked and nested so much, just because there is a knob or button for everything. This has to stop. UI is about making decisions to help the user, not about weaving a rope to hang themselves with, or smoke when they get frustrated.


I agree but advanced settings should be accesible for power users. I would be happy for an advanced users tweak app.

gnome-app-install is also improving. Ubuntu is very cool and will be super very cool :-D

I also want all the goals implemented that are currently  here : [http://udu.wiki.ubuntu.com/UbuntuDownUnder/BreezyGoals](http://udu.wiki.ubuntu.com/UbuntuDownUnder/BreezyGoals) :-P

Well I want a lot :-P. But people are talking about all this stuff so if we wait for a while things like this will hapen!

a bit offtopic -> maybe breezy will have some slick transparancy  :
[http://www.ubuntuforums.org/showthread.php?t=54239](http://www.ubuntuforums.org/showthread.php?t=54239)

---

### Post by Knome_fan on 2005-08-04
[QUOTE=ubuntu_demon]cool stuff!
I thought a bit about it. I don't want mezzo but something very close to mezzo but implemented in gnome or on top of gdm/gnome. Then we can still have project utopia (for example automount) and Ubuntu developers can build on their previous work.
[/quote]
Ehm, to get the project utopia stuff it doesn't need to be build on gnome and starting it with gdm won't help anyway.

But what I really wanted to say, yesterday the new alpha was released. I think it has already been mentioned, but just to remind you, the CD you can download is a LiveCD, so anyone who is interested in this project, just get the LiveCD and play around.

I tried it yesterday for the first time and it's a really innovative and exciting project. Well worth downloading the LiveCD imho.

---

### Post by Kerberos on 2005-08-04
Downloading it at the mo, gonna give it a try.  Looks pretty much like what I keep moaning people should do so it'd be rude not to.

---

### Post by ubuntu_demon on 2005-08-04
[QUOTE=Knome_fan]Ehm, to get the project utopia stuff it doesn't need to be build on gnome and starting it with gdm won't help anyway.
[/QUOTE]

As far as I know project utopia isn't possible with fvwm (yet). Correct me if I'm wrong I've never used fvwm.

[http://wiki.linuxquestions.org/wiki/Project_Utopia](http://wiki.linuxquestions.org/wiki/Project_Utopia)

> 
...The project seems to be most closely associated with Gnome...


Also I want those UI improvements in gnome because gnome has nice and easy config apps.

[QUOTE=Knome_fan]
But what I really wanted to say, yesterday the new alpha was released. I think it has already been mentioned, but just to remind you, the CD you can download is a LiveCD, so anyone who is interested in this project, just get the LiveCD and play around.

I tried it yesterday for the first time and it's a really innovative and exciting project. Well worth downloading the LiveCD imho.[/QUOTE]

I'll try it this weekend.

---

### Post by Knome_fan on 2005-08-04
[QUOTE=ubuntu_demon]As far as I know project utopia isn't possible with fvwm (yet). Correct me if I'm wrong I've never used fvwm.

[http://wiki.linuxquestions.org/wiki/Project_Utopia](http://wiki.linuxquestions.org/wiki/Project_Utopia)
[/QUOTE]

Well, first off other projects, for example KDE are now also using at least parts of project utopia (HAL in this case).
As for fvwm, or symphony OS, they could use existing projects like ivman (which essentially does what gnome-volume-manager does), write their own volume-manager, or simply use gnome-volume-manager. Afaik Mandriva uses it even for its KDE desktop as at least according to some Mandriva devs it doesn't have many gnome deps anyway. 

So there isn't really a need for using gnome proper I think.

---

### Post by ubuntu_demon on 2005-08-04
[QUOTE=Knome_fan]Well, first off other projects, for example KDE are now also using at least parts of project utopia (HAL in this case).
As for fvwm, or symphony OS, they could use existing projects like ivman (which essentially does what gnome-volume-manager does), write their own volume-manager, or simply use gnome-volume-manager. Afaik Mandriva uses it even for its KDE desktop as at least according to some Mandriva devs it doesn't have many gnome deps anyway. 

So there isn't really a need for using gnome proper I think.[/QUOTE]
 -gnome has the best implementation for project utopia
-I like gnome
-most Ubuntu users like gnome
-al lot of prior Ubuntu development was done with gnome in mind

I prefer gnome above fvwm until/if :
-if gnome applications run perfectly in fvwm and look good 
-if there are good and easy config apps in fvwm
-until fvwm project utiopia's implementation is at least as good as gnome's implementation

---

### Post by Knome_fan on 2005-08-04
[QUOTE=ubuntu_demon]-gnome has the best implementation for project utopia
-I like gnome
-most Ubuntu users like gnome
-al lot of prior development was done with gnome in mind

I have nothing against fvwm if/when :
-if gnome applications run perfectly in fvwm and look good 
-if there are good and easy config apps in fvwm
-when fvwm project utiopia's implementation is at least as good as gnome's implementation[/QUOTE]
?
Did I do something wrong?
I don't really know what you are trying to say, but I get the impression you somehow think you need to justify yourself. Rest assured, I did in no way want to attack you, I just wanted to point out that SymphonyOS from what I know doesn't have to be based on gnome to take advantage of the great stuff in Project Utopia, that's all. 

/me is confused

---

### Post by ubuntu_demon on 2005-08-04
[QUOTE=Knome_fan]?
Did I do something wrong?
I don't really know what you are trying to say, but I get the impression you somehow think you need to justify yourself. Rest assured, I did in no way want to attack you, I just wanted to point out that SymphonyOS from what I know doesn't have to be based on gnome to take advantage of the great stuff in Project Utopia, that's all. 

/me is confused[/QUOTE]
 No you didn't do anything wrong. I just wanted to have a good discussion :)

I'll rephrase my prior post (I had to leave in a bit of a hurry :-P)

---

### Post by qalimas on 2005-08-04
It looks a lot different, I'm sure new users would love it.  I'm going to download the alpha, the screenshots don't please me enough :P

---

### Post by super on 2005-08-04
MEZZO looks freakin' awesome and i'm most definitely gonna be checking it out!  :grin: 

i'll attempt to try to give some answers to some of the question in the thread:

> As far as I know project utopia isn't possible with fvwm (yet). 
this is accurate but,
> As for fvwm, or symphony OS, they could use existing projects like ivman (which essentially does what gnome-volume-manager does), write their own volume-manager, or simply use gnome-volume-manager. 
this is also accurate. in my case i stick 'gnome-volume-manager' in my FVWM exec sequence and VOILA!! automount works like a charm. i'm sure the same would be true in MEZZO

> -if gnome applications run perfectly in fvwm and look good  
they do. again, i run the 'gnome-settings-deamon' when FVWM starts and all my gtk apps and fonts look the same as in GNOME. the fact that GNOME is so modularized and allows me to do this is evidence of the genius that GNOME developers have.  :grin: 

> -if there are good and easy config apps in fvwm
WHAT! FVWM not hard to configure!
just joking.  :-P  
i would say this is the biggest turn-off for people looking to use FVWM. if i were to print my .fvwm2rc file it would probably be about 25 pages. but i guess thats the nature of the beast!  :-P 

at least with MEZZO the most of the work is already done for you!

now if you'll excuse me i've got a MEZZO livecd to check out!  :cool:

---

### Post by ubuntu_demon on 2005-08-05
super: that's good to hear :)

Like I said I've never tried fvwm. I'll try the livecd this weekend too.

I still think easy configuration is important. 

And I would prefer something like mezzo integrated in/on top of gnome. I forgot to mention another reason why I would prefer that : a lot of people use gnome and like it

---

