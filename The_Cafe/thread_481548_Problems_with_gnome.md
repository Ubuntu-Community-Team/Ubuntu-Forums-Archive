---
title: "Problems with gnome"
date: 2007-06-22
forum: The Cafe
---

### Post by praxis22 on 2007-06-22
Sorry about the l33t speak, I'd like to swear but this is a family friendly forum :) 

My apologies in advance for the length.

Gnome is crap. Not in any spectacular way, "in a silent way" (If Miles Davis will forgive me) It's taken me a while to get here, and I didn't always hold such a low opinion of it, let me explain. 

I first encountered Gnome many years ago, I've even rolled it out on a Sun network, integrated into dtlogin on Solaris 8, hand-rolled. This was way before Sun started shipping it with Solaris 10. I always viewed it as a overly complicated yet competent desktop framework, and a worthy alternative to CDE, which I've always had an irrational hatred off, simply on account of it's clunkiness.

Added to this it's been a strange week, I've been wrangling old versions of Solaris, and being vexed, frustrated and bemused by AIX, with which I've been fighting running battles for the past few days. Then Ubuntu snuffed it. It actually told me quite out of the blue, that my boot device's UUID didn't exist, and promptly threw me into the initramfs shell. At first I thought this odd, but it turned out to be a useful experience, as I worked out not only what happened, (a kernel update had decided to change the underlying device structure, so that /dev/hd* became /dev/sd* thus removing the device pointed to by the UUID) I also recover from it, and subsequently worked out why my ubuntu install always hard locked when it booted into the splash screen, (ATI card/64bit issues, though the 32 bit splash works fine) during this I installed a program into windows (I'm a Sims2 addict, sue me) :) that allowed me to mount ext2fs partitions natively so I no longer had to use a ubuntu boot CD. Much was accomplished.

Inspired by this new found success, I also managed to get beryl fully working, and began futzing about with themes, etc. It was at this point that my screensaver corrupted. One moment it's working fine, the next it's scrambling the picture, even in the little preview window. I experimented, and discovered it was peculiarly sensitive to the -zoom option. I should perhaps say at this point that I'm using the GLslideshow binary. with -zoom 79 all is well & clear, with -zoom 80 or above it corrupts. I figure this to be an aberration of some kind, and set about "fixing" it. 

It was at this point that I began to understand just how really bad Gnome is. Not in a badly programmed or designed way, more as a matter of philosophy. This came to a head last night when I stayed up until 3am beating my head against an invisible brick wall. All the more surprising as I never thought to find it there. I was half thinking it must be me.

What I couldn't get my head around at first, was, "but, this is UNIX.." It didn't irk me that I had to hand edit text files, nor that I had to hunt for the information, that is par for the course. What did irk me is that having edited the text files the application then chose to ignore my settings, but that's another matter entirely. As the hour grew late, I settled for hacking the cosmos screensaver, as that would at least simply display my images, without moving, fading or anything else. It was only once I'd stepped away from the keyboard and went to join the wife in bed, that it dawned on me. 

What I was actually fighting with was not so much a badly written program, but deliberate policy on the part of the people who shepherd Gnome, and the unstated, but implicit idea that "we know best", or perhaps more crucially, "we made that choice for you." Which, on a UNIX platform, is anathema. To the extent that even where choice exists, (such as the switches you can apply to GLslideshow) the Gnome user setting give you no means to change or invoke them. Then there is the strange discovery that there exists any slideshow application in the world, (in this case the non GL variant used in the cosmos app) that has no switches other than where to source it's images. Not even a switch to alter the speed/duration.

During this discovery process, I had many small epiphanies, like finding open bugs in the Debian bug list all about  how it was considered "unfriendly"  to force people to actually edit text files by hand to get the a screensaver to behave. Or finding other people butting their heads up against the same problem, who were being told they were being unreasonable, "It's just a screensaver, get a grip."

Yes, there are work arounds, I could use F-spot, I could, and did, hand edit files, read the FAQ, or the maintainers page. I could also fork the application. As I was going to bed I was pondering doing just that. But the more I thought about it, the more annoyed I got, as it would mean I'd constantly have to be patching the thing each time gnome was updated, etc. I wasn't willing to put up with this crap from Sony, etc. why was I cutting Gnome so much slack.

Then, from the depths, I recalled a thread I had read where Linus rants on the gnome list about this very thing, I thought he was overreacting when I first read it. But after last night, I finally understand the rage.  

"Gnome sucks Donkeys, I have proof!" to paraphrase Wayne & Garth. It sucks and sucks hard! Like I said, it took me by surprise as I never expected to find a wall there, I spent several hours being told in no uncertain terms that, "you can't because we don't think you should, we made that choice for you, sit down shut up, and like it."

Only I don't, and since I wont suffer such crapness from the likes of Sony, or pay double the price for a currant bun for no reason, I'm not taking it from Gnome either. I'm going to finish typing this, swallow my pride, and irrational hatred of *DE trash Gnome and install KDE.

"Begone foul beast of the pit! Do not darken my door again." 

You may now flame me, commiserate, or tell me to get a grip, etc.

---

### Post by hessiess on 2007-06-22
its your system, do what you want with it!

gonme being crap is YOUR opinion you don't haft to make super long posts expressing this.

gnome works perfectly for lots of people, if you don't like it that's your problem;)

---

### Post by praxis22 on 2007-06-22
I'm dyslexic too, (really) only I use the in-line spell checker that comes with firefox 2.0, what's your other excuse? :P

---

### Post by forrestcupp on 2007-06-22
OK, Get a grip.

For one, Gnome is a free DE.  You don't have to pay for it.  You have to pay for Sony products, so you have a right to expect more out of them.

Also, you will find some kind of problem with KDE or anything else you use.  I've never seen any software that is perfect.  If you can't accept that, you won't be satisfied with anything.

Aside from all of that, I just switched to KDE, and I like it a lot.  I have had some problems with it, but I still like it.

---

### Post by SoulinEther on 2007-06-22
> **forrestcupp said:**
> OK, Get a grip.

For one, Gnome is a free DE.  You don't have to pay for it.  You have to pay for Sony products, so you have a right to expect more out of them.

Also, you will find some kind of problem with KDE or anything else you use.  I've never seen any software that is perfect.  If you can't accept that, you won't be satisfied with anything.

Aside from all of that, I just switched to KDE, and I like it a lot.  I have had some problems with it, but I still like it.
I have no idea where I'm coming from. But it sounded good at first, so I'll roll with it.

Free or not free, if you design a product for an environment that goes against the enviornment's, or to a lesser extent the users', norms and expectations, you're a problem. And you're an even bigger problem when you've become popular... that means you're immigrating an outside environment and .. sort of merging it with the original one. I'm talking about Windows and Mac OS merging with Linux.

ELIMINATE THE GNOMES! THEY'RE EVERYWHERE!

Ok, while you (same you from above, not *you* forrestcupp) might not be a problem, you're certainly not contributing to the environment users expect.

I too dislike some of the "It works how we think it should work, and that's that" aspects of GNOME. KDE is almost like a polar opposite, though my computer FREQUENTLY tells KDE "You'll run as fast as I can run, and that's that"... so that doesn't work that well for me either.

Xfce works for me. Plus, XScreensaver gives me a choice to adjust setttings, so I'm happy, hehe.

---

### Post by Chilli Bob on 2007-06-23
Get a grip dude! It's just a screensaver. (That goes for Linus too!)

Seriously, why do people think Gnome or any other program has to do everything THEY want it to. Gnome works perfectly for most people, it provides the environment the average desktop user (read "Windows convert") needs or wants.  Gone are the days when every Linux user wants to fine tune their system at a level verging on obsessive compulsion. If you and others want that kind of customisability and control, then what the hell are you doing in Ubuntu in the first place? It's designed for Linux noobs!  That kind of rant was like a Windows fanboy bitching because a few things are slightly different to what they are used to.

(Dons asbestos trousers and prepares for ***-flaming)

Hmmm, can't say *** OR ****.  Oh well, you know what I mean.

---

### Post by macogw on 2007-06-23
The first third is nothing to do with GNOME

The 2nd part: Okay, you can't have 2 OpenGL things going at once.  It's EITHER GL screensaver OR GL desktop (Beryl/Compiz).   You can't have both.  That's not GNOME's fault at all, so I have no idea why that's in there.

F-Spot?  What's that to do with GNOME and screensavers?  Why's it being mentioned all randomly?  It just appears in your post completely out of place.  There's nothing at all mentioned about photo organization anywhere else, so I'm confused.  Did a paragraph comparing to Picasa/iPhoto/gThumb/kFlickr/DigiKam randomly disappear or something?

The OP isn't making any sense.

---

### Post by 23meg on 2007-06-23
[QUOTE=praxis22]
What I was actually fighting with was not so much a badly written program, but deliberate policy on the part of the people who shepherd Gnome, and the unstated, but implicit idea that "we know best", or perhaps more crucially, "we made that choice for you."[/QUOTE]

[QUOTE=praxis22]
I spent several hours being told in no uncertain terms that, "you can't because we don't think you should, we made that choice for you, sit down shut up, and like it."[/QUOTE]

[http://ubuntuforums.org/showpost.php?p=2698299&postcount=26](http://ubuntuforums.org/showpost.php?p=2698299&postcount=26)
[http://ubuntuforums.org/showpost.php?p=1314185&postcount=17](http://ubuntuforums.org/showpost.php?p=1314185&postcount=17)

---

### Post by bonzodog on 2007-06-23
/me coughs loudly and points to Xfce.

Xfce is in my educated and 10 yrs of linux experience, one of the best complete DE's I Have come across.

It even now has its own compositor to do eye candy, should you want it, and of course uses gtk for drawing all it's applications.

Xfce is way ahead of gnome, I just wish someone would build a DM for xfce that uses the basic gtk toolkit to draw login windows.  Gdm is still hefty in that it depends on gconf and a whole bunch of gnome libs just to handle logins.

---

### Post by praxis22 on 2007-06-23
I liked my original title better :)** "Gnome is teh sux0r!!!**

I'm not having problems with Gnome, well, not technical problems anyway. My problems, such as they are, are more philosophical in nature. I've yet to gank Gnome, but I'm now doing the KDE  thing, KDM and all. I'm guessing that since the mod moved the thread here, they understood that too. I was in a sense venting my frustration after a hard week at the code face. I'm a UNIX admin by trade, so contrary to what many may think I do actually know what I'm doing :P

I actually use Xubuntu on my laptop, (an ageing Sharp Mebius) since it doesn't have enough RAM to run Gnome, and it is indeed rather spiffy. I've also got XFCE4 installed on my desktop too, but thanks for the tip all the same. :) I am actually thinking of going back to my roots, and seeing if I can't find the fvwm 1.24r source anywhere. With Beryl, that should be a lot of fun :)

As to why I use Ubuntu at all? "it just works" I actually have a Sun Ultra60 SPARC desktop to my left, (under a Dell GX240 and a water purifier) that has Solaris 10 on it, but my desktop is actually a lot faster :)  I have installed/used other distributions in the past. Previously I built my wife a Gentoo box when she asked, (she's a geek too, programmer.) but she installed so much crud into it, she ran /usr out of space. Women! :P

I was hoping my argument was a little more nuanced, if slightly random :) Though to be honest, it is in the nature of the beast that is Linux/UNIX to be very configurable. I realise that the average Windows refuge will have no idea that this is the case, and Canonical/Ubuntu are doing stirling work in bringing those users an experience that masks the complexity, etc. My issue was more one of control. 

This is of some concern I would think, to people who are trying to push Gnome as a viable alternative to Windows. Because to the "average" end user, the Desktop environment, is the computer. Simply stated, the default XP slideshow screensaver is actually more configurable than the Gnome variant. However the really irksome thing, to me, as a user,  is that GLslideshow as provided by Gnome is not user configurable, as compared to the same GLslideshow as provided with Xscreensaver.  You can dig deeper, and find more, which I did, hence seeing people work around the issue, by using the F-Spot image viewer as a slideshow screensaver, etc. 

But at it's base, I was "bitching" about a lack of control, and hence a lack of choice, which to me as a UNIX admin, is actually rather a fundamental failing. But this is what you get for doing what all the "cool kids" are doing :P

---

### Post by ComplexNumber on 2007-06-23
**praxis22**
you don't have to use the 'default' applications that come with the desktop. that's another beauty of linux - if you don't like it, use a different one. for example, i don't have the gnome snapshot tool in my menu - i use Desktop Data Manager instead and it serves me fine.

---

### Post by praxis22 on 2007-06-23
Aha! Forum staff...

I have a totally unrelated question to ask :)

Does the little sun icon next to your handle and mine, mean what I think it does? Namely that we're in the same timezone? If not, how come we're the only two with it, and everyone else looks like they have a small white disc, (moon?) next to their handles.

Also, while I'm at it, sorry for posting in the wrong forum, had I know there was a "cafe" I'd have posted it here. It was part rant/part vent, part "bleat in the night" looking for any kind of solution. 

However, back on topic, anyone aggrieved by the apparent arbitrariness of decisions made higher up and further away should find this suitably amusing  The gnome-screensaver maintainer feels the ire of rabid ubuntu users:

[http://bugzilla.gnome.org/show_bug.cgi?id=316654](http://bugzilla.gnome.org/show_bug.cgi?id=316654)

Kudos to 23meg for that.

---

### Post by ComplexNumber on 2007-06-23
> **praxis22 said:**
> Aha! Forum staff...

I have a totally unrelated question to ask :)

Does the little sun icon next to your handle and mine, mean what I think it does? Namely that we're in the same timezone? If not, how come we're the only two with it, and everyone else looks like they have a small white disc, (moon?) next to their handles.

Also, while I'm at it, sorry for posting in the wrong forum, had I know there was a "cafe" I'd have posted it here. It was part rant/part vent, part "bleat in the night" looking for any kind of solution. 

However, back on topic, anyone aggrieved by the apparent arbitrariness of decisions made higher up and further away should find this suitably amusing  The gnome-screensaver maintainer feels the ire of rabid ubuntu users:

[http://bugzilla.gnome.org/show_bug.cgi?id=316654](http://bugzilla.gnome.org/show_bug.cgi?id=316654)

Kudos to 23meg for that.
the sun icon means that a person is logged in. someone who has moon is either not logged in or invisible(to a member). moderators can also see a cloud, and that tells us that the person is invisible.

---

### Post by needtolookatascreenshot on 2007-06-23
> **praxis22 said:**
>  

However, back on topic, anyone aggrieved by the apparent arbitrariness of decisions made higher up and further away should find this suitably amusing  The gnome-screensaver maintainer feels the ire of rabid ubuntu users:

[http://bugzilla.gnome.org/show_bug.cgi?id=316654](http://bugzilla.gnome.org/show_bug.cgi?id=316654)

Kudos to 23meg for that.
Actually, it's more disgusting then amusing. 
A bunch of rather idiotic users blindly attacking someone who has the courtesy to provide his work for free to them.

Never mind that there are good reasons for the change from xscreensaver to gnome-screensaver, that have been explained again and again.

Never mind that it has been stated again and again that the option aren't missing because that's the way it's supposed to be but simply because they aren't implemented yet in gnome-screensaver.

As I said, a rather disgusting spectacle.


P.S.: 
Instead of staying awake till three in the morning and instead of writing longwinded rants on forums, I'd recommend the following the next time around:
sudo apt-get install xscreensaver

---

### Post by praxis22 on 2007-06-23
> **needtolookatascreenshot said:**
> Actually, it's more disgusting then amusing. 
A bunch of rather idiotic users blindly attacking someone who has the courtesy to provide his work for free to them.

P.S.: 
Instead of staying awake till three in the morning and instead of writing longwinded rants on forums, I'd recommend the following the next time around:
sudo apt-get install xscreensaver

Yes, I feel quite sorry for the guy, one moment he's dealing with polite geeks, the next he's got "user complaints" I've got users myself so I know how he feels :)

Though I do have Xscreensaver installed, I did this the first time I encountered the issue, but it stopped working, and no matter what I tried it refused to obey. I suppose  it was just a red rag to a bull, I'm not used to having UNIX/Linux tell me no. It's so much easier with servers than desktops, you rarely have to worry about X at all. 

I wrote it long form, more as a way to express my frustration, and so I could explain why I was so distracted to my wife. Had I known there was such a thing as an "off-topic" forum I would have posted it there. I was half hoping somebody would say, "you're an idiot do it like this" But in attacking the problem like I did, I stumbled across other stuff, and just got hacked of with Gnome. 

That said, the KDE screensaver (slide show) just locked out on me, I could see the cursor and move it fitfully, but I had to restart X to get out of it. Ah well. I guess I shall press on with compiling this new screensaver, and see what that does.

---

### Post by needtolookatascreenshot on 2007-06-23
> **praxis22 said:**
> Yes, I feel quite sorry for the guy, one moment he's dealing with polite geeks, the next he's got "user complaints" I've got users myself so I know how he feels :)
Nope, it's not "user complaints", it's simply mindless and insulting bashing of someone who does a lot of work for those people who attack him for free. 

But the worst is that they, like you in your first post, don't even have the courtesy to do the 2 minutes research it would take to find out that:
a) There are good reasons for replacing xscreensaver with gnome-screensaver
b) The options are not left out as a policy decision but are simply not implemented yet.

---

### Post by praxis22 on 2007-06-23
> **needtolookatascreenshot said:**
> Nope, it's not "user complaints", it's simply mindless and insulting bashing of someone who does a lot of work for those people who attack him for free. 

But the worst is that they, like you in your first post, don't even have the courtesy to do the 2 minutes research it would take to find out that:
a) There are good reasons for replacing xscreensaver with gnome-screensaver
b) The options are not left out as a policy decision but are simply not implemented yet.

Spoken like a man who also has to take this kind of flak? :)

Like I said, this really isn't about a screensaver, I actually did read the FAQ, and did research, and find out how others had got around the issue, but in doing so I became disgruntled with the overall lack of control, I realise that Gnome is written for the Average Joe, and that as an admin I should probably be using the non-newbie version. But I'd just never butted heads with it before, I never gave it a thought, it's just a Display Environment.

I just expected that when you apply the appropriate switch to the config file with vi, that it should do as you tell it or fail in some interesting yet informative way. It did neither.  Apparently this is by design, and that's what really irked me.

---

### Post by praxis22 on 2007-06-24
Call me sore loser, but I decided I wasn't going to let it lie :)

I downloaded the source for the screensaver, hacked it to suit, and then installed it, and told the screensaver to use that, it now behaves as I want it to :P

---

