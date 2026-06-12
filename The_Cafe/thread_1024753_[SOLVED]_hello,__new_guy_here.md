---
title: "[SOLVED] hello,  new guy here"
date: 2008-12-29
forum: The Cafe
---

### Post by busemans on 2008-12-29
hey guys,  no intro area so i just thought i would post here.  sorry if its wrong but someone will move it if it is.  

i am totally new to non windows anything.  i bought a pc from a guy who said it crashed on him so he bought a laptop since he traveled alot.  sounded weird but ok.  got it home and tried to load xp and nothing.  tried for a few days and got tired of it.  swapped a running/loaded hd into the pc and it gave me the same error as the one that came in the machine.  uh oh,  not a good sign.  went on a trip for christmas and my brother gave me ubuntu 8.10 and said that should take care of all my trouble.  when i got home i tried to load it and got a message about not being able to load the description map and it would not run past the password section.  reloaded it a bunch and ran it without having to load the password and have no troubles.  it is super cool but i don't know how to do anything in this os. (not that i knew how to do alot in windows,  i just followed the prompts)  everything runs but it all runs very slow and choppy.  the screen saver jerks across the screen like it is working very hard.  the computer is an hp and has a p4 2.6 and 2gs of memory so i would imagine it should be super smooth.  
a buddy gave me a module to load but i can't figure out how to load it.  i have it on the desktop for now, in its little package and have tried loading with the synaptic package manager and something else (cannot think of hte name) but have gotten nothing.

in the future,  i would like to load this onto my toshiba with dual core procs and all the cool junk but i think that is along way off as i can't even get a video card driver to load right now.



ok,  now a bit about me.  
my name is jason and i love video games and cars.  i have tons of video game systems and am building an 82 320i bmw right now with possible use in scca autocrossing as its future.  i used to race an 89 325i and won two years in a row in dsp for my region but it got old knowing i was probably going to win again so i sold it and bought this 82 to work up.  right now it is running the bmw m10 4 cylinder with long tube header and two barrel weber carb in place of hte fuel injection.  i have a bmw m20 6 cylinder waiting for some parts from europe so i can drop it in place and then will run it with, probably, 3 two barrel weber carbs and headers running out like an old school hot rod.  

sorry,  you can tell what i really love doing by my descriptions.

i live in south texas and am on the computer anytime i am not working and the weather isn't good for working on the cars.

---

### Post by Grant A. on 2008-12-29
Welcome to the wonderful world of Ubuntu GNU/Linux! :KS

---

### Post by Clark76 on 2008-12-29
Welcome to the club;)

---

### Post by cdwillis on 2008-12-29
Welcome to Ubuntu

It sounds like you might have a problem with the driver for your video card, if you can give us some information about the video card we can help you out :)

---

### Post by Delever on 2008-12-29
Welcome,

This is usual way to enable video drivers:
[http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-8.10-nvidia](http://www.howtoforge.com/enabling-compiz-fusion-on-ubuntu-8.10-nvidia)

So it should be simple! If there are problems, I suggest first doing a search (you would be surprised how many people have identical problems), then ask in beginners section on these forums.

Also, I suggest learning few basic things about system, because it is different than Windows.

---

### Post by Swagman on 2008-12-29
Actually it sounds like he's running it from the live cd.

Ok.. Just in case you **HAVE** installed Ubuntu.. Your password... which will be asked for EVERY admin event is the same one you used to log in with.

---

### Post by Delever on 2008-12-29
Yeah, in any case, I found good tutorial in How To Forge:

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10](http://www.howtoforge.com/the-perfect-desktop-ubuntu-8.10)

It seems to cover everything.

---

### Post by busemans on 2008-12-29
i tried searching but i must have been to vague in my wording because it brought up pages of things and not to many had to do with video cards and their drivers.

the only beginners area i found was a read only section.  is there a normal area for us new guys where we can ask all the annoying and bothersome questions out of the way of the mainstream areas?

i have open the pschocats.net manual and the absolute beginner's guide in other tabs but if they stick like the other stuff i have read then i will have tons of trouble continuously until i just take the copmuter somewhere to have someone load xp onto it.  computer manual reading is so hard for me to follow.  if i can't do it hands on then i am usually in trouble.

---

### Post by busemans on 2008-12-29
> **Swagman said:**
> Actually it sounds like he's running it from the live cd.

Ok.. Just in case you **HAVE** installed Ubuntu.. Your password... which will be asked for EVERY admin event is the same one you used to log in with.

not running from the cd.  got passed that part.  and it is the same password for every admin operation i try to run

---

### Post by earthpigg on 2008-12-29
edit: post did not apply :)

---

### Post by Elanorea on 2008-12-29
Hi there jason, welcome to the UBUNTU CLUB...

I'M helen i'm also new here and i just done my profile.

I hope we can become freinds =)

---

### Post by Swagman on 2008-12-29
> **busemans said:**
> not running from the cd.  got passed that part.  and it is the same password for every admin operation i try to run

That sounds very borked !!

Try opening a terminal..

Look up at the top left of the screen.. Applications > Accessories >Terminal

And copy & paste this into it

```


sudo apt-get update


```

---

### Post by busemans on 2008-12-29
hi helen,  i try to be friends with everyone


swagman,  i'll give it a shot.


and just to clarify for everyone.  the pc is running off the hd at this time.  it took many tries of wiping the hd and reloading but it finally starts and runs.  it is just very jerky when scrolling or using anything that involves video (screensavers and the like are jerky)

---

### Post by Swagman on 2008-12-29
> **busemans said:**
> hi helen,  i try to be friends with everyone


swagman,  i'll give it a shot.


and just to clarify for everyone.  the pc is running off the hd at this time.  it took many tries of wiping the hd and reloading but it finally starts and runs.  it is just very jerky when scrolling or using anything that involves video (screensavers and the like are jerky)

This just doesn't sound right.

The ubuntu installer should've just obliterated anything that was already on the drive with the click of a mouse button

ie: Choosing **"Use entire disc"**

In this screenshot of the partitioner they are resizing a windows partition to fit ubuntu on it.

You said you just installed ubuntu on it as the only O/s so you  would choose use entire disc. (or thats the impression I got.. Please correct me if I'm wrong)

[img]http://www.techotopia.com/images/5/52/Ubuntu_disk_partitioning_screen.jpg[/img]

---

### Post by busemans on 2008-12-29
ok, the terminal listed a lot of hits on web sites and then:reading package lists... done.

i tried running hte screensaver (that is my test mule to see how the video card is doing) and it is still jerky and choppy.  i am trying to read through the web pages i have found for beginners so hopefully that will help me out.

---

### Post by busemans on 2008-12-29
i did indeed use entire disk.  i wanted nothing of hte original stuff on the disk to cause any issues

---

### Post by Swagman on 2008-12-29
Kewl.. We're getting somewhere.

Now.. Go into System > Administration > Hardware Drivers

[edit to dig out an old screeny]

The screenshot below states no proprietry drivers in use.. Thats because I tried a command myself before asking someone else to use it and it reset my drivers lol.
If you look driver 177 is selected and a reboot is being asked for.

[IMG]http://i261.photobucket.com/albums/ii45/Outcast_Aussie/hardwarescreeny.jpg[/IMG]

---

### Post by busemans on 2008-12-29
i get:

no proprietary hardware drivers are in use on this system.

only.  none of the other things in your screen shot show up on my screen

i went to appearance (for the heck of it) and tried to change the visual effects to normal or extra and i get the message:

desktop effects could not be enabled

---

### Post by busemans on 2008-12-29
i have an intel 82845g/gl integrated chipset.  not an nvidia card though.  in the long run,  is this going to make a difference for what we are doing?  i would think that since it is the motherboard video stuff that the os would've picked it up from the get go

---

### Post by Swagman on 2008-12-29
Are you using onboard graphics or card ?

[edit] 

entered whilst you were typing.

Ok.... looks like onboard.. Your chipset might have been dropped with 8:10.. Not sure.. I'm going to have to pass you over to anyone who can help you out with that one.

---

### Post by busemans on 2008-12-29
onboard

---

### Post by Delever on 2008-12-29
Seems like unlucky graphics card :/

[http://ubuntuforums.org/showthread.php?t=985498](http://ubuntuforums.org/showthread.php?t=985498)

---

### Post by Swagman on 2008-12-29
This is why I handed over the help to someone else.

I was sure I had read somewhere that the minimum (graphics) chipset bar had been raised but couldn't remember the details (I'm running a GT8800).

I didn't want to lead a potential Ubuntu convert down the garden path.

So basically..  Owners of that chipset should use 8:04 Hardy Heron.

To the new guy.. This is NOT a bad downgrade.

---

### Post by busemans on 2008-12-29
ok,  8.04 and i will be back in action.  i don't do anything but use the computer for forums and rare sizing of pictures.  i just like to have decent graphics while i am "talking" to everyone on the net.

---

### Post by cespinal on 2008-12-29
Good luck with Ubuntu Hardy!!! 

Just keep in mind that more than downgrading, you are just tailoring ubuntu to your pc :D 

Cheers

---

### Post by busemans on 2008-12-29
i wish i knew how to tailor it to my pc.

you guys think if i put a video card into this pc then i can just stay with 8.10 and be okaly dokaly?  it seems easier to throw a video card in then it is to change operating systems

---

### Post by busemans on 2008-12-29
ok guys,  i finished putting 8.04 on and everything works now.  even in the highest graphics setting everything is super smooth and beautiful.  thanks for everyone's help who tried!!!!  now,  this pc is windows free and if all is as nice as it is now in a week or two,  i will stealthily change over the wife's while she is at work.  she loves when i do things like that to her.

one time i did some secret body work to her bmw.  she was not happy.  or when i changed the head on her car while she was shopping.  super surprised on that too.

---

### Post by earthpigg on 2008-12-30
> **busemans said:**
> it seems easier to throw a video card in then it is to change operating systems...

...i will stealthily change over the wife's while she is at work.  she loves when i do things like that to her.

one time i did some secret body work to her bmw.  she was not happy.  or when i changed the head on her car while she was shopping.  super surprised on that too.

lol, ya it sounds like she loves that stuff.

[this ]("http://gnome-look.org/content/show.php/NotXP?content=73782")may help you be stealthy.

screenshots [here]("http://images.google.com/images?hl=en&q=NotXP&um=1&ie=UTF-8&sa=N&tab=wi").


also, in the case of ubuntu it is definately **_not _**easier to throw a video card in than install any given version of ubuntu... especially since you already have it installed ;)

edit: please understand that i am not to blame when she throws her keyboard at you.

---

### Post by Swagman on 2008-12-30
Excellent.

I'm pleased you got it sorted.

You can do all the updates... Just don't click the New distribution available button at the top.

---

