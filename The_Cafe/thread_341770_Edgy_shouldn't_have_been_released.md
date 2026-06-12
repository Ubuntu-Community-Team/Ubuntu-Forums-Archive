---
title: "Edgy shouldn't have been released"
date: 2007-01-19
forum: The Cafe
---

### Post by curvedinfinity on 2007-01-19
Heya,
I have been using Ubuntu as my main OS since 6.06 was released. I was a huge fan, but the latest release, 6.10, has caused more problems than it has solved for me.

Ubuntu is supposed to be the Windows-killer; the Linux that is usable by humans; the one I can finally recommend to Mom and Pop. I'm a power-user, and I couldn't get 6.10 to work. How is any of that supposed to happen with this quality of a release? A release is supposed to be stable, 6.10 is not even close.

Let me list what happened:

I want to give 6.10 a try after a wonderful time with 6.06. I decide to do an upgrade so I don't lose my data, and at that, through the GUI. An hour later ... everything's fine, so I reboot.

The computer boots up, but there is no gnome only an ugly blue and grey screen telling me something was messed up, leading me into the terminal.

So, considering I was left with a brick of a computer, I decided to install 6.10 from scratch.

(an hour later)
The 32 bit LiveCD hard-locked after about a minute

Alright, so I'll try the 64 bit version ... 

(an hour later)
The LiveCDs had no support for mapper installations via the GUI (I had a dmraid array in 6.06.1 and I installed mainly with the gui)

Ok ... I'll live without my RAID ...
--So, I installed a non-raid 64 bit version because that was my only option

First things are first ... booting up ...
The boot splash was grey-scale. Not a big deal, I can live with it.

Once into gnome ... alright .. everything is working ... until ...
In about 2 minute intervals I would not be able to use my input devices in different ways:
case 1:
I could move the mouse, but the buttons did not do anything
The keyboard did nothing to applications
To fix, I could press alt-tab or ctrl-alt-bksp or, oddly enough, click the clock/calendar in the top-right
case 2:
Same as above, but only fixed by manually restarting gnome w/ ctrl-alt-f1

Ok ... ok, this is going to be annoying, but at least I have a computer ...

After about 30 minutes, the computer would completely freeze. I can tell because the Gnome widgets stop updating (like the clock).

Just for reference (because I'm sure someone is going to ask), my comp's specs:
2.6 GHZ Pentium D
1 GB ram
X200 chipset
Geforce 7600 GT

Looking at a poll in the forums, it seems like about three quarters of the people who have installed edgy have had some kind of problem, and at least half have had a serious problem. This OS is definitely not release quality, and I definitely won't be sticking with Ubuntu if a trend like this continues in its releases. For the time being, I won't be recommending it either.

I'm now going to experiment with some other distros, just so I know whats out there. If I don't find any that especially stand out, I'll be installing 6.06 again. That would be quite a disappointment though, considering I'll have to reinstall everything and get it back to the way I like it -- for absolutely no reason, and with an incredibly buggy "upgrade" to blame.

I hope this stirs up some attention, as Ubuntu definitely needs some change.

---

### Post by kerry_s on 2007-01-19
Wow, sounds like you had some really bad luck with edgy. Edgy works fine for me, i guess it just depends on the hardware, i built mine 100% linux compatible from the start. Hopefully feisty will be alot better than edgy, just got to be patient. Since your going to try other distro's put PClinuxOS ( [http://distrowatch.com/index.php?distribution=pclinuxos&month=all&year=all](http://distrowatch.com/index.php?distribution=pclinuxos&month=all&year=all) ) on that list it's dirt simple  and has 3 versions to choose, i have grandma using minime on the laptop. Anyways good luck to you.

---

### Post by richbarna on 2007-01-19
Did you eliminate all reasons for these problems, such as a bad iso or a bad burn, your problems sound to me that they are xserver related, I have experienced keyboard, graphic and mouse problems with many distros that I have tested, some just needed a xorg or xfree86 reconfigure, others just needed the iso to be burnt at X4 or X8.

Only suggestions by the way. with these sort of problems I would normally (in the past) do a basic "server" install and then apt-get/aptitude the xserver and the DM after. I know it shouldn't be necessary to do it this way, but it did work.

---

### Post by rai4shu2 on 2007-01-19
Edgy messed up my video, but at this point I've wrestled with xorg.conf many many times in the past. Actually, every distro I've ever tried screws up my video (including Dapper), so I don't think I'd be using Linux if that kind of thing stopped me.

I'm very much looking forward to the improvements they plan to have in xserver. :)

I'm using a nVidia 7600 GT, here by the way.

---

### Post by ComplexNumber on 2007-01-19
after an initial bumpy ride (mainly sound problems) and some dependency hell in synaptic, edgy isn't too bad.

---

### Post by allix on 2007-01-19
I'm sorry to hear that you've had such a terrible experience with edgy. Personally I think edgy works much better that dapper and everything else, with the exception of OO.o-fonts.

> How is any of that supposed to happen with this quality of a release? A release is supposed to be stable, 6.10 is not even close.

Edgy was supposed to be a cutting edge version where lots of things were expected to break, this was decided even before development began. For a stable distro dapper is the way to go. And if you want even more stable, try debian etch. :)

> Looking at a poll in the forums, it seems like about three quarters of the people who have installed edgy have had some kind of problem, and at least half have had a serious problem. 

Isn't this expected? I mean, people do come to these forums to get help with various problems. 

> I'm now going to experiment with some other distros, just so I know whats out there. If I don't find any that especially stand out, I'll be installing 6.06 again. That would be quite a disappointment though, considering I'll have to reinstall everything and get it back to the way I like it -- for absolutely no reason, and with an incredibly buggy "upgrade" to blame.

Like I said, you should try debian etch, maybe even the latest Fedora and openSuse. All of them are great IMO. I recommend you create a separate /home partition, if you haven't already. That way you can keep all your settings and documents when switching between distros and versions. :)

---

### Post by curvedinfinity on 2007-01-19
All I can say is that with 6.06, my install, even with dmraid, Just Works. The only nitty-gritty things I had to do were minor and optional.

With 6.10, much less than that could be said. -- To get the system even fully functional will take hours of research and screwing with stuff, probably with a couple more reinstalls yet because I'd have messed something up. I have no clue where to even start looking for solutions, and I don't really want to. I'd much rather have a working computer sans some new things.

---

### Post by graabein on 2007-01-19
Weird thread title man...

---

### Post by Nonno Bassotto on 2007-01-19
I had no problem with edgy, I'm sorry you had. It is a safe thing to remove all apps installed by deb files or external repositories before upgrading, and then reinstalling them. Consider doing this in the next upgrade, maybe you'll be more lucky.

You realize that the fact that 3/4 of the people voting in that poll say they had problems with edgy doens't absolutely mean that 3/4 of the people had problems with edgy, do you? I mean, of course if you have a problem you go on the forum and try to solve, and as soon as you see such a poll you want to vote there.

---

### Post by curvedinfinity on 2007-01-19
> **allix said:**
> 
Like I said, you should try debian etch, maybe even the latest Fedora and openSuse. All of them are great IMO. I recommend you create a separate /home partition, if you haven't already. That way you can keep all your settings and documents when switching between distros and versions. :)

I think you are right in that there are many better solutions for me. -- But I simply want to point out this website:
[http://www.ubuntu.com/ubuntu](http://www.ubuntu.com/ubuntu)

states:
"Ubuntu is a free, open source Linux-based operating system that ... [adds] a clear focus on the user and usability (it should "Just Work", TM) ..."

Given that, it would be ironic to move elsewhere for a lack of something that is a focus of Ubuntu.

Edit:
And yes, I realized that the group of people who would vote on that poll would not include many users who didn't have problems.

That being said, there are more than a thousand votes on it, and for an OS that couldn't have more than tens of thousands users, that is still pretty aweful.

---

### Post by Kateikyoushi on 2007-01-19
There were similar threads when it was released, it is not an LTS release, dapper was late so they about half the time what was put into dapper to create edgy. Despite all that I belive edgy built the base for feisty and the two releases a year are necessary or at least package upgrades are.

You can't make everything perfect for everyone, as for me even betas worked fine on both my machines.

---

### Post by rai4shu2 on 2007-01-19
It's not ironic at all. Once you get the system installed, Edgy is actually more usable than Dapper.

---

### Post by risby on 2007-01-19
> **curvedinfinity said:**
> 
The 32 bit LiveCD hard-locked after about a minute

Alright, so I'll try the 64 bit version ... 

Once into gnome ... alright .. everything is working ... until ...

Just for reference (because I'm sure someone is going to ask), my comp's specs:
2.6 GHZ Pentium D


I don't understand how a 64bit operating system could work at all on a 32bit CPU system. What am I missing here?

---

### Post by sloggerkhan on 2007-01-19
My experience with edgy isn't that it shouldn't have been released, but the live CD shouldn't have been if that makes any sense.

On my comp, and a number of comps around my dorm, the live cd does not work without serious tweaking. 

Now I don't know that your problems are live CD related... Once I thought my computer was hanging on boot and went to fix it only to discover that having some USB device (forget what) cause a big delay in booting.

Now the thing I have discovered with edgy is that all the annoying things off a default live CD install that are a huge pain actually have solutions (which should have implemented automatically) and that once you find them, it's a great release.

On mine, I have to use a special boot line off the CD in order to get to the console and modify my xorg.conf to install so I can than change my menu.lst file in grub and install a graphics card driver and wireless drivers, among a plethora of other tasks. But now that I figured out exactly what to do for each little bit, I have what seems to be my most stable Ubuntu ever.

---

### Post by curvedinfinity on 2007-01-19
Pentium D is an EMT64 processor, which is essentially AMD64. AMD64 processors can be used with 32 bit OSes.

---

### Post by Tux Aubrey on 2007-01-19
Weren't you just a tad hasty?  I mean a self proclaimed "power user" who attacks a version upgrade with this mind-set:

> The computer boots up, but there is no gnome only an ugly blue and grey screen telling me something was messed up, leading me into the terminal.

So, considering I was left with a brick of a computer, I decided to install 6.10 from scratch.

Seems just slightly , um under-powered.

Were you using the beta binary nVidia drivers by any chance?  Beryl?

Now both of those things have messed up both a dist-upgrade and a kernel update for me, landing me at "an ugly blue and grey screen telling me something was messed up".

Yes, I did panic a bit, but not being a power user, I got onto the forums from another machine and asked for help.  I think it was tseliot who gave me three fairly simple commands to enter into the terminal and I was back in business.  I also learnt why it happens sometimes.

I now have a recovery strategy for when it happens again (pessimist me).

None of this turns me off Ubuntu though - I had some real horror stories with Windows and I like to learn this stuff.

By the way, other than this, edgy has been a dream for me.  No instability and faster than dapper.  Oh - and maybe you should avoid Feisty Fawn.  I don't think it will be a LTS release.

---

### Post by allix on 2007-01-19
> **curvedinfinity said:**
> I think you are right in that there are many better solutions for me. -- But I simply want to point out this website:
[http://www.ubuntu.com/ubuntu](http://www.ubuntu.com/ubuntu)

states:
"Ubuntu is a free, open source Linux-based operating system that ... [adds] a clear focus on the user and usability (it should "Just Work", TM) ..."

Given that, it would be ironic to move elsewhere for a lack of something that is a focus of Ubuntu.

I don't see the irony, Ubuntu HAS succeded with making their distro extremly usable. You said it yourself, "All I can say is that with 6.06, my install, even with dmraid, Just Works. " ;)
And if 6.06 works, why not continue using it? I waited a long while before upgrading, and did so only because the newer xorg ati-drivers worked better.

---

### Post by STREETURCHINE on 2007-01-19
this is a strange post you move from 6.06 dapper the stable version with long term support,
go to the cutting edge called edgy 6.10 and then complain you have some problems'
go back to dapper it is a good distro,
ask some questions about edgy and solve the problems.i have both dapper and edgy,out of the two edgy has been more of a problem but with the help of a lot of good people have it running and i use it more than dapper now,
this sort of post is counter productive and does you no good..:-k

---

### Post by Kateikyoushi on 2007-01-19
> **curvedinfinity said:**
> I'm now going to experiment with some other distros, just so I know whats out there. If I don't find any that especially stand out, I'll be installing 6.06 again.

Let off some steam and think about how do you benefit the most, install something else and hope it just works, or try to repair it which might actually teach you something.
What happens if at your next upgrade that distro breaks ?

---

### Post by curvedinfinity on 2007-01-19
> **Tux Aubrey said:**
> Weren't you just a tad hasty?  I mean a self proclaimed "power user" who attacks a version upgrade with this mind-set:



Seems just slightly , um under-powered.

Were you using the beta binary nVidia drivers by any chance?  Beryl?

Now both of those things have messed up both a dist-upgrade and a kernel update for me, landing me at "an ugly blue and grey screen telling me something was messed up".

Yes, I did panic a bit, but not being a power user, I got onto the forums from another machine and asked for help.  I think it was tseliot who gave me three fairly simple commands to enter into the terminal and I was back in business.  I also learnt why it happens sometimes.

I now have a recovery strategy for when it happens again (pessimist me).

None of this turns me off Ubuntu though - I had some real horror stories with Windows and I like to learn this stuff.

By the way, other than this, edgy has been a dream for me.  No instability and faster than dapper.  Oh - and maybe you should avoid Feisty Fawn.  I don't think it will be a LTS release.

I'm no linux expert, but I'm definitely a power user. I'm a C++ dev by day. But just because I'm a power user doesn't mean I'll put up with having to tweak things to get an OS working in the first place.

Oh and also, another point for everyone:

The 6.10 release is above the 6.06 release in the downloads section of the website. What kind of user would pick the older one given that there is no recommendation to use 6.06 over 6.10? There was never a "cutting edge, this might mess up, so download the 6.06 if you have a critical system" warning. -- No, the cutting edge, unstable set of criteria are for alpha and beta releases. Edgy is a final release. Given that it is, it should meet Ubuntu's goals, and a user (such as myself), should expect to find what was advertised.

---

### Post by Aetherius on 2007-01-19
I know what I'm about to say isn't very helpful but...

I have been using....

Dapper Flight 3 -> Release
&
Edgy Eft Knot 3 -> Release
&
Feisty Fawn Herd 2.....

Not once have I had any form of system devastation, excepting minor hiccups that were solved in 10 minutes by myself.... or 15 minutes on this forum!

(having said this, most of those minor hiccups were probably caused by my malignant tinkering)

Aeth.

EDIT: Oh, i forgot about the time in edgy alpha when messed up xorg updates occured :D fun fun breakage

---

### Post by anaconda on 2007-01-19
Sounds like BAD luck.
I haven't had any problems using&installing edgy. Actually it has worked better than Dapper in all aspects, and the fact that edgy has newer programs in its repositories is a big plus..

The only reason I am still using Dapper (at work) is that the undocumented features of samba don't work anymore with edgys newer kernel... So I wont ever be able to change to edgy at work...

---

### Post by eXisor on 2007-01-19
I also give edgy the  thumbs up.

It does better than dapper on all my boxes.

---

### Post by fuscia on 2007-01-19
if edgy hadn't been released, i would not be as happy as i am. is that really what you want for me? i had trouble with the update, myself, and had to do a clean install, but i'm just an impatient end user. edgy, aside from a few goofy problems, has been great for me. if you want stable, go back to dapper. if you want entertainment, stick with edgy.

---

### Post by Biggus on 2007-01-19
Hmm I don't have much in the way of perspective, because I've only ever used 6.10, but it installed perfectly on my box, and has ran perfectly, without crashing once, ever since.

I'm now using it for all sorts of wacky stuff I wouldn't have considered using my previous OS for. In ten years of using Windows, the best use I put it to was playing Sid Meirs 'Pirates'. Now, I'm actually running an mp3 server, a SSH server, and an Apache server, all with a level of stability I wouldn't actually have considered possible on a home PC.

Personally, I am loving it very much indeed.

---

### Post by MetalMusicAddict on 2007-01-19
curvedinfinity. Best way for this not to happen to someone else is for you to get involved in development of Ubuntu.

---

### Post by prizrak on 2007-01-19
Umm ok, you are missing quite a bit here.
For one Edgy was said to be buggy from the beginning and Canonical actually said that if you want stability just stick with Dapper. 

I never had any problems with Edgy I didn't cause, in fact I'm running Feisty Herd2 right now and it's as stable as any other release I have used (that is to say solid). 

In the future to avoid losing your data you should create a separate /home partition and don't format it when you reinstall. 

If you want your gramma to use Ubuntu install Dapper for her I doubt she will care much for upgrading to the latest and greatest.

---

### Post by Rhapsody on 2007-01-19
I'm on the verge of agreeing here. I've had only two problems with Edgy Eft, but they're both pretty big and I don't see much in Edgy Eft to make up for either.

First, the system locked when trying to mount hdb1 (apparently trying to fsck it after 143 mounts without checking), so I told the installer not to mount it and later fscked it myself. This is pretty minor, and I'll probably have it nicely mounted on boot soon.

Second, I have no sound! I've been missing all sound in Edgy Eft for over a week now! Everything appears to be working correctly, the sound card and speakers are fine (a live CD produced sound), previous releases (Breezy and Dapper) had no problems at all, but I can't get any sound out of the OS or any application. I've made a [topic](http://ubuntuforums.org/showthread.php?t=341177) about it, but got no working solutions.

---

### Post by saulgoode on 2007-01-19
Was not Edgy Eft one of the normal "six month cycle" releases? My understanding was that one of the main goals for creating Ubuntu (and not just supporting Debian directly) was to provide stabilized releases derived from Debian unstable every six months. Has there been a change in this goal and now certain releases of Ubuntu are to be considered "unstable"? Or was Edgy an anomaly that hopefully won't recur? (Assuming that, as some are suggesting, Edgy does not meet stability expectations.)

Granted, it is possible for any product to have versions which are "dogs" released and to expect perfection is not reasonable. But, in my opinion, the original poster raises some valid concerns: is meeting a six-month release cycle more important than producing a stable release? If certain Ubuntu releases (for example, every other one) are considered "unstable" or "testing" then hasn't Ubuntu sacrificed something that it originally criticized Debian for (i.e., long intervals between stable releases)?

---

### Post by K.Mandla on 2007-01-19
For what I've seen, a six-month cycle works fine. Dapper got two extra months for final flair, and Edgy made a leap to some new stuff that had to be in place in two months less. 

Edgy isn't "unstable;" I think calling it that is a misnomer. Calling it a "development" release would be more accurate, since a lot of changes were put into place, and they haven't had the time to mature like Dapper had.

---

### Post by daynah on 2007-01-19
I had a lot of problems with Edgy also, more problems than I had with Breezy. I installed it on my laptop because I had heard that the majority of the updates were for people who are all into code (aka not me) and though that's very important, the only things that the end users would really notice about Edgy were going to be pretty graphics (they were! I miss those...) and the power management and wifi.

I couldn't get on the internet using wifi and I had to keep my laptop plugged in at all times.

Now I've used linux for a while. I know right after you do an update, everything's a little wonky and you gotta really try to make it work... it's like puberty in a way... just give it some time and the squeeky voice will work itself out. I looked on the forums, tried so many ways. Close to two months with a power and ethernet cord on my back I realize, this relationship isnt working and I go back to Dapper and let the Fiesty devs know details of exactly what happened.

Man that power managment screen looked like it would have done some cool stuff if it would have worked... I'm so jealous of all the laptops it worked on...

**Edgy is a very love/hate thing. **True, it isn't "unstable." Isn't it correct, that "unstable" means it crashes and what not, and I don't think Edgy does that. I think Edgy just randomly spits in some people's faces. Hopefully Fiesty will be more of a lady.

Maybe a tally of how many computers are using which version will give us more of an idea of which version people enjoy. I mean... I would think you'd use the version you prefer.

---

### Post by macogw on 2007-01-19
> **curvedinfinity said:**
> 
Looking at a poll in the forums, it seems like about three quarters of the people who have installed edgy have had some kind of problem, and at least half have had a serious problem. This OS is definitely not release quality, and I definitely won't be sticking with Ubuntu if a trend like this continues in its releases. For the time being, I won't be recommending it either.

Well, I can tell you that those polls were from an upgrade (not fresh install) within the first 2 days at which point everyone was saying/doing "sudo dist-upgrade" which doesn't work properly instead of using the GUI.  I was one of them, and my computer half-upgraded, then I used the GUI upgrade and it fixed it.  I went with just using the GUI on my second computer, and it worked perfectly.

Re: Daynah's Feisty comment
Even when it crashes, the whole thing doesn't go.  "Gksu" apps don't load without adding "dbus-launch" to the command and the Beryl beta that's in it is messed up because it won't work with the current Python.  That's all I've seen so far.

---

### Post by Somenoob on 2007-01-19
Edgy worked properly on my machine, but some sort of unknown lag that interrupted every now and then got me to switch back to Dapper.

---

### Post by lamalex on 2007-01-19
hahah i havnt had a single issue that i wouldnt have had with any distro (freaking broadcom wireless) but that was easily solved. Edgy runs great for me!

---

### Post by qamelian on 2007-01-19
> **rai4shu2 said:**
> It's not ironic at all. Once you get the system installed, Edgy is actually more usable than Dapper.

I agree. I had far fewer problems with Edgy then I did with Dapper. I couldn't install Dapper from either the Desktop CD or Alternate CD and had to do a dist-upgrade from Breezy to get it installed. Dapper 6.06.1 that was released later installs fine from both CDs. Edgy went on with no problem and the only thing I had to setup was my wireless card. which was a snap the bcm43xx-fwcutter. My card didn't work very well in Dapper, which annoyed me as if worked fine in Breezy. Dapper aged well though and the issues I had with it were all resolved except for some really annoying sound issues that also carried over to Edgy, but seem to be resolved in Feisty.

---

### Post by wesley_of_course on 2007-01-19
> **kerry_s said:**
> Wow, sounds like you had some really bad luck with edgy. Edgy works fine for me, i guess it just depends on the hardware, i built mine 100% linux compatible from the start. Hopefully feisty will be alot better than edgy, just got to be patient. Since your going to try other distro's put PClinuxOS ( [http://distrowatch.com/index.php?distribution=pclinuxos&month=all&year=all](http://distrowatch.com/index.php?distribution=pclinuxos&month=all&year=all) ) on that list it's dirt simple  and has 3 versions to choose, i have grandma using minime on the laptop. Anyways good luck to you.

Wesley here ;   kerry_s  , I  am extremely interested in how oyu did it !

The Linux , I'm in the process now and its an undertaking to say the least ! Thank You 

I apologize , not trying to hijack the thread . Just curious as so many others might be , Thanks again.

No problems with Edgy so far.

---

### Post by kogber on 2007-01-19
I think that curvedinfinity has a valid point in that there should be some notation on Ubuntu downloads pages (and i guess in the actual distro filename) stating that Edgy is a "development" release and Dapper is a "stable" release.  The various issues with the Edgy Live cd, which are prominent and widespread, indicate that Edgy is not suitable for the casual user.  Better to have a reliable Honda than a BMW that you have to bring back to the dealer every week cause another toy broke.

I have run into some minor issues, but nothing major.  Stating that a distro should not have been released, just because you have had problems, is not the most objective thing to say.

---

### Post by tagra123 on 2007-01-19
> **saulgoode said:**
> Was not Edgy Eft one of the normal "six month cycle" releases? My understanding was that one of the main goals for creating Ubuntu (and not just supporting Debian directly) was to provide stabilized releases derived from Debian unstable every six months. Has there been a change in this goal and now certain releases of Ubuntu are to be considered "unstable"? Or was Edgy an anomaly that hopefully won't recur? (Assuming that, as some are suggesting, Edgy does not meet stability expectations.)

Granted, it is possible for any product to have versions which are "dogs" released and to expect perfection is not reasonable. But, in my opinion, the original poster raises some valid concerns: is meeting a six-month release cycle more important than producing a stable release? If certain Ubuntu releases (for example, every other one) are considered "unstable" or "testing" then hasn't Ubuntu sacrificed something that it originally criticized Debian for (i.e., long intervals between stable releases)?

Amen!

---

### Post by reyfer on 2007-01-19
I'm sorry, maybe I'm just imagining things, but I remember reading on the release notes *before* getting Edgy something about Edgy being cutting edge, and if you wanted more stability you should stick with Dapper? So the note about the stability was there from the start.

And I was using Kubuntu Dapper and upgraded to Edgy without a glitch, and my system is as stable as can be. Still have had no real problems whatsoever, some annoyances that were solved with help from this forum, but that's it. Curiously enough, I had more issues with Dapper than Edgy :D

---

### Post by SunnyRabbiera on 2007-01-19
Well there is a reason why its called edgy, it can easily break if yiou are not careful...
stick to dapper, simple

---

### Post by spockrock on 2007-01-19
umm remember that dapper was pushed back two months because of gnome if I am not mistaken.  That meant if edgy were to be released, then it would be have to be out in 4 months.

Edgy was released in 4 months.

I am sorry to hear about your edgy problems but edgy has been 110% stable for me.

---

### Post by macogw on 2007-01-20
> **kogber said:**
> I think that curvedinfinity has a valid point in that there should be some notation on Ubuntu downloads pages (and i guess in the actual distro filename) stating that Edgy is a "development" release and Dapper is a "stable" release.  The various issues with the Edgy Live cd, which are prominent and widespread, indicate that Edgy is not suitable for the casual user.  Better to have a reliable Honda than a BMW that you have to bring back to the dealer every week cause another toy broke.

I have run into some minor issues, but nothing major.  Stating that a distro should not have been released, just because you have had problems, is not the most objective thing to say.
Edgy ceased to be development in _October_.  _Get your facts right!_  Dapper is Long Term Support (LTS) meaning 3 years of updates.   Edgy is normal, so it gets a year and a half.  **EDGY IS NOT UNSTABLE OR DEVELOPMENT**.  The only development version going on right now is FEISTY.  Look at my user info at the top of this post.  See that?  I have the Feisty alpha installed.  THAT is unstable.  You know how I tell it is unstable?  When I click on the "Login Window Properties" and enter my password, nothing happens.  When I go to "add/remove" that app crashes.  When I try to open the Beryl settings, it crashes.  THAT is unstable.  "My wireless card was supported, but the drivers aren't in this one" is NOT unstable.  There is a huge difference.

Edgy IS suitable for the casual user, provided that user has Linux-compatible hardware.  That is the one VERY IMPORTANT provision.  Most Edgy problems were caused by upgrading within the first 2 days using the command line.  After those first 2 days, the upgrade problems were fixed, notices were put out saying to use the GUI, and now all is well.  Fresh installs work fine if your hardware is good.

---

### Post by EdThaSlayer on 2007-01-20
I had problems with Edgy Eft(Firefox constantly crashing and stuff and the whole GNOME system going really slow) but I just reinstalled Dapper Drake and everything was stable once again!

---

### Post by durant1958 on 2007-01-20
I've got 6.10 installed on one of my backup PC's and my Toshiba Laptop ( With built-in Broadcom wireless IIRC. ) both of those installs worked just fine.

I started out with 6.06 on my main system, but I ran headlong into the "It's Long Term Support, but we won't ever update the Firefox to 2.x." issue.  I won't use and can't recommend an OS where the developers have made choices that freeze a key application, such as Firefox or OO.o,   at a specific revision level. ](*,) 

My main system runs openSUSE 10.1 now, and it's quite nice and stable.  I will look forward to the next LTS release for Ubuntu / Kubuntu, maybe the developers will make different choices.  One can always hope.

---

### Post by slimdog360 on 2007-01-20
edgy works great for me. Ive got beryl running all the time and it doesnt even crash.

---

### Post by xpod on 2007-01-20
Same as slimdog on this machine.:D 

I`ve now in fact installed Edgy on 3 pc`s around the house  and never had a problem with any of them.
Mabey a couple of user issues along the way but never much more than that:D

---

### Post by sartic on 2007-01-20
It should be called beta or even alpha. Tried many mobo's livecd won't work, alternate cd can not handle non english keyboard (example croatia). When u have installed on your system; many freezing and slowness on start. Initial update is larger than 6.06.1. Many wlan works perfectly in 6.06.1 but no in.... Please stop calling thise release STABLE!!!
And developers please make new install width all updates and call it 6.06.2 LTS STABLE ;)

---

### Post by taurus on 2007-01-20
Move to Testimonials.

---

### Post by sartic on 2007-01-20
Why did u moved this message?????????=?? from forum that talks about installing?

---

### Post by rev_b on 2007-01-20
> **sartic said:**
> It should be called beta or even alpha. Tried many mobo's livecd won't work, alternate cd can not handle non english keyboard (example croatia). When u have installed on your system; many freezing and slowness on start. Initial update is larger than 6.06.1. Many wlan works perfectly in 6.06.1 but no in.... Please stop calling thise release STABLE!!!
And developers please make new install width all updates and call it 6.06.2 LTS STABLE ;)

In [http://ubuntuforums.org/showthread.php?t=286209](http://ubuntuforums.org/showthread.php?t=286209) 

> Also note that Edgy 6.10 is considered a development platform for testing new ideas,and technology. Use of this version,and coming versions there after are at your own risk...First Time Linux/Ubuntu users are advised to use dapper,and not edgy as their frist step into Linux.  

So for a start, your milleage may vary, you've been warned, and so on...  As a "development platform" you can't complain if it doesn't work in all systems.

I don't share your experience, I've so far installed Edgy in 2 PC's and tried the LiveCd on a noteboot and it works fine. Alternate CD install handles portuguese (pt) keyboard just fine, no complains. The only problem I got in the installation is that the nv driver shipped in the livecd doesn't work with my Geforce 7900GT and I had to start it in safe graphics mode and after installation, edit the xorg.conf to use vesa instead, to get to the desktop. It does work fine in my other PC, with a Geforce 4 MX440.

---

### Post by aysiu on 2007-01-20
After a brief exchange with Taurus, we've decided the Cafe is best--in fact, I've merged it with this other, similar thread. In any case, it is certainly not an Absolute Beginner support thread.

---

### Post by ~LoKe on 2007-01-20
> edg·y     /&#712;&#603;d&#658;i/ Pronunciation Key - Show Spelled Pronunciation[ej-ee] Pronunciation Key - Show IPA Pronunciation
–adjective, edg·i·er, edg·i·est.
1.	nervously irritable; impatient and anxious.
2.	sharp-edged; sharply defined, as outlines.

It wasn't meant to be a stable release.  6.06 is the LTS distribution, and should be used over the next.

---

### Post by saulgoode on 2007-01-20
> **~LoKe said:**
> It wasn't meant to be a stable release.  6.06 is the LTS distribution, and should be used over the next.

Your point is all well & good (as is [Brunellus's](http://ubuntuforums.org/showthread.php?t=286209)), but shouldn't the [download page](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download) somehow reflect that view -- rather than the innocuous message, "If you would like to benefit from the latest Ubuntu features, this is the release for you"?

---

### Post by sartic on 2007-01-20
> **saulgoode said:**
> Your point is all well & good (as is [Brunellus's](http://ubuntuforums.org/showthread.php?t=286209)), but shouldn't the [download page](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download) somehow reflect that view -- rather than the innocuous message, "If you would like to benefit from the latest Ubuntu features, this is the release for you"?

Yeap, the problem is that they still use 'stable' word. Example: [http://www.ubuntu.com/support/faq](http://www.ubuntu.com/support/faq)

---

### Post by ~LoKe on 2007-01-20
The thing is, Edgy **is** stable.  Regardless of which distribution you're using, someone will always have a problem.

---

### Post by sartic on 2007-01-20
> **~LoKe said:**
> The thing is, Edgy **is** stable.  Regardless of which distribution you're using, someone will always have a problem.

You mix word installable and stable... Stable means that works 4 many systems after install, and installable means it will work 4 some systems. I can not accept that stable 4 Ubuntu means that widthout changing min. requirments. All systems that failed 6.10 r using 6.06.1 superb. That's why 6.06.1 is stable and .... I hope that Feisty will be my new favourite.

---

### Post by 454redhawk on 2007-01-20
> **curvedinfinity said:**
> 
Edgy shouldn't have been released

 the latest release, 6.10, has caused more problems than it has solved for me.


I hope this stirs up some attention, as Ubuntu definitely needs some change.

Because YOU had a problem it should not have been released?

Get a grip. EDGY works just fine for MANY THOUSANDS of people.

Ubuntu is not a Windows killer. The Ubuntu team could CARE LESS what happens with windows.
It does not even enter into the equation.

Also, EDGY was and IS a development release. You should be thanking the team for releasing it and letting us all try the latest stuff. They dont call 6.06 LTS for nothing. If you want stable then you should be using 6.06.

Quit your crying.

---

### Post by Polygon on 2007-01-20
the only thing bad about edgy for me was that the installer did not properly edit the /etc/fstab file for my /home partiton which i didnt format, and used across dapper/edgy

turns out the problem was that edgy uses UUID's instead of just the /dev/whatever path, and since the installer forgot or didnt add the UUID for my /home partiton, fsck always complained during boot up, but i was able to fix it manually

and also, camera support was borked for me, but some guy posted in his blog on how to fix it and now that works too.

---

### Post by darrenrxm on 2007-01-20
You should try mint linux. All I had to do was sudo envy to get the graphics drivers to work (Geforce 6600GT). But when I upgraded the kernel it broke the xserver. :( Still haven't been able to fix it.

---

### Post by aysiu on 2007-01-20
> **454redhawk said:**
> 
Ubuntu is not a Windows killer. The Ubuntu team could CARE LESS what happens with windows.
It does not even enter into the equation. I think Mark Shuttleworth would beg to differ:
[https://launchpad.net/ubuntu/+bug/1](https://launchpad.net/ubuntu/+bug/1)

By the way, based on what I've seen, most of the complaints about Edgy are from upgrades from Dapper--not a fresh install. I did a fresh install of Edgy, and it works fine.

---

### Post by Kernel Sanders on 2007-01-20
My only complaint with Edgy is that it didnt detect my ATI graphics card correctly. I have an ATI Radeon 9600XT 256mb graphics card. Edgy gave me 1024x768 screen resolution, with a refresh rate of 61Hertz. My display was weird to say the least. It should have been 1280x1024 with a refresh rate of 75 hertz

I looked into fixing it, but there were lots of confusing instructions for a noob like me :( Just look: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I almost cried at reading that :frown:

---

### Post by Rhapsody on 2007-01-20
> **aysiu said:**
> By the way, based on what I've seen, most of the complaints about Edgy are from upgrades from Dapper--not a fresh install. I did a fresh install of Edgy, and it works fine.

Ironically, I heard about all those problems and made a fresh install so I'd have none. I've now been without any sound for eight days, and no indication from the system itself that I even have a problem. Given that silence is known to drive me up the wall, this is computing hell for me.

---

### Post by SZF2001 on 2007-01-20
Meh, I'm not sure what everyone's problem is.

My computer is a PoS... So I have to run Xubuntu for it. No problem, right?

Used the alternative, have updated (like needed), ran automatix, got rid of some programs that came with automatix but I didn't want, found out there was a trash bin which is awesome, and there. I'm all set.

Edgy is fine...

---

### Post by Severa on 2007-01-20
Edgy is unstable? WTF? I must be extremely lucky then...

Last month I wiped WinXP off my computer (Biostar M7NCD motherboard, Athlon 2600+, 512MB RAM, GeForce FX 5900 XT) and clean installed Edgy 6.10, my VERY FIRST dive in Linux. 

Worked like a charm out of the box. Loaded up all my pics and music and took off. 

Couple of days ago I got the LiveCD of Feisty (yeah I know it's beta, I'm a stay at home mom so I have free time when the kiddos are at school) and installed it. Other than the 'right after time zone screen goes all wonky bug' which I fixed with Ctrl-Alt-F1/Ctrl-Alt-F7, it's been smooth sailing. Hell I even managed to install Beryl the other day. (thanks to you guys on this wonderful forum ):P )

---

### Post by saulgoode on 2007-01-20
> **454redhawk said:**
> Also, EDGY was and IS a development release. You should be thanking the team for releasing it and letting us all try the latest stuff. They dont call 6.06 LTS for nothing. If you want stable then you should be using 6.06.

Development releases should NEVER appear on a download page UNLESS it is made abundantly clear that the release is intended for those interested in its development. Since no such qualification is provided on the Ubuntu download, one would be quite justified in assuming that Edgy is NOT a development release and that any lapses in its functionality reflect just as poorly on Ubuntu as they would if they appeared in Dapper.

---

### Post by qamelian on 2007-01-20
> **saulgoode said:**
> Development releases should NEVER appear on a download page UNLESS it is made abundantly clear that the release is intended for those interested in its development. Since no such qualification is provided on the Ubuntu download, one would be quite justified in assuming that Edgy is NOT a development release and that any lapses in its functionality reflect just as poorly on Ubuntu as they would if they appeared in Dapper.
There is a reason why you would assume that Edgy is not a development release: as noted several times already, Edgy is not a development release. Edgy is a stable release...it just isn't a Long Term Support release. The only current development release is Feisty Herd 2. Soon after it reaches RC (Release Candidate) stage, it will also be released as a stable, but not Long Term Support, release. After this a new development release cycle will begin.
Or to put it another way, there are currently 3 stable releases that are supported: Breezy Badger, Dapper Drake, and Edgy Eft. Only one of these, Dapper Drake, is a Long Term Support release, but all 3 are Stable releases. There is currently only one Development release and that is Feisty Fawn.

---

