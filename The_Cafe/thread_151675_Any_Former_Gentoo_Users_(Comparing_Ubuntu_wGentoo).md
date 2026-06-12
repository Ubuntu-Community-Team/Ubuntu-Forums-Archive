---
title: "Any Former Gentoo Users (Comparing Ubuntu w/Gentoo)"
date: 2006-03-28
forum: The Cafe
---

### Post by sclough on 2006-03-28
Now I know that Gentoo and Ubuntu or totally different distros.  I use Gentoo as I am a programmer and I like the power and flexibility.  I also prefer to run things as fast as possible (who doesn't?) so I like the ability to compile everything for a specific chip with -O3 and to not build things in binaries that I never use.

That being said, Gentoo can also get time consuming.  Decent updates can require recompiling virtually everything and that takes quite a bit of time.  Anyway, I have heard some users say that the Gentoo speed benefits aren't as great as one would think.  The machine I'm currently using as my primary desktop is a 2.4Ghz Celeron with 512mb RAM.  Not a powerhouse by anybody's definition but it's pretty speedy with Gentoo.  In fact, Open Office runs as fast on this machine as I've every seen it run.  (It also takes a lot of time to compile).

Anyway, to get to the point, a friend of mine currently needed a new computer and I installed Ubuntu on it for him to save him the whole Windows virus/spyware mess.  I was impressed by the polish of the distro.  It was a little slow (Open Office in particular was practically unusable), but this was also on a 1Gz box with only 256 or so of RAM, so it shouldn't be expected to be too snappy.

Are there any former Gentoo users who can comment on the performance differences going to Ubuntu?  I like the idea of something that just works and requries a good bit less time than Gentoo does.  The reason I posted this in the Dapper forum is because I'm considering installing Dapper.  I have been using Gnome 2.14 and I'm hooked on it and would prefer to stay with it over going back to 2.12.  Thanks for any help.

---

### Post by taurus on 2006-03-28
I am not a former Gentoo user because I still have Gentoo on my computers at home and in the office.  If you need to upgrade something with emerge, run it from a window and minimize it so you don't have to look at it.  Then, continue with your work!!!  

On the other hand, if you want a quick and easy distro to play with, then go for Ubuntu.  Of course, I wouldn't recommand newbies to start out with Gentoo because their heads will spin so fast they don't even know what hits them...  So, if you are not comfortable with typing in all those commands, then take the easy way out--Ubuntu!!!

---

### Post by paul cooke on 2006-03-28
wrong forum, please take this to the Ubuntu Cafe forum... :)

---

### Post by sclough on 2006-03-28
[QUOTE=taurus]I am not a former Gentoo user because I still have Gentoo on my computers at home and in the office.  If you need to upgrade something with emerge, run it from a window and minimize it so you don't have to look at it.  [/QUOTE]

I do typically open a terminal, minimize it and let it run.  In fact, I'm quite impressed with how well the box runs with the compiler pegging the processor.  I did configure the scheduler for desktop workloads though.

I was most interested in what the performance differences were between Dapper and a "normal" (does that exist?) Gentoo system.  If they are close enough, I just may give Dapper a whirl for my primary box.  Do you see a big difference between Gentoo and Ubuntu as far as normal desktop performance?

---

### Post by elsupermang on 2006-03-28
I found Gentoo boots up so slooooooooow, it took over a minute to boot Gentoo with a minimal Gnome desktop, while Ubuntu takes something like 35-40s. That's what really ticked me off after i spent a day compiling everything and Gentoo was really not any faster then other distros I tried. The apps started like half a second faster, but when the rest is so slow to start, who cares.

---

### Post by supenguin on 2006-03-28
I used to use Gentoo. I haven't really noticed much of a performance difference. This is pretty typical desktop use - email, chat, mp3's, web browsing, Open Office. Some programs would take a little longer to start up with one distro, some with the other. I think it was just because different packages were compiled with different options.

---

### Post by mega on 2006-03-28
I used gentoo, the config file update process in it was annyoing, it would really break things every once and a while, speed does not seem much different

I prefer ubuntu breezy,  and now dapper, although dapper is heavy into updates, 5-10 sometimes 20 packages a day get updated

---

### Post by Barrakketh on 2006-03-28
[QUOTE=supenguin]I used to use Gentoo. I haven't really noticed much of a performance difference.[/quote]
For most things you wouldn't.  However, at least in Breezy there are many packages that have SSE/MMX disabled, some of those applications could benefit from -O2 or -O3.  You're not really going to notice GNOME running any faster, but things like mencoder, lame, or XViD are *very* noticeable.  Dapper seems to fix many of those problems.  Thankfully, apt makes it fairly easy to fix (though I do my package building in a chroot jail) in cases where some optimizations could be made.

One of the things that made me switch from Gentoo was that there were a few packages that were masked as testing (even though they had been that way for a couple of months) and required me to unmask them and their dependencies.  When I started my World of Warcraft binge I wasn't using Gentoo hardly at all, and I came back to the prospect of having to deal with updating everything and managing those masked packages and their dependencies...ugh.

---

### Post by vendetta red on 2006-03-28
I have used Gentoo in the recent past (2006.0) and I enjoyed it for the learning experience. Other than that I must agree with previous posts, Ubuntu boots faster than optimized Gentoo ever did on my system, and compiling everything from source to run things a fraction of a second faster just wasn't worth the wait.

---

### Post by johnnymac on 2006-03-28
I was a huge Gentoo user for a long time, but I moved over to ubuntu for ease of use.  Gentoo is great for those custom server jobs....or systems that have next to no resources available.  But really...as a workstation or a productivity environment...no way - it takes entirely too long to get working.  This guy whos running Ubuntu has his head in the right place......quick, fast and easy!

---

### Post by Alibloke on 2006-03-28
I moved from Gentoo to Debain (and then on to Ubuntu) mainly because Gentoo's update process using emerge was awful especially if I had customised some config file somewhere.  Now I'm a huge apt fan, much less hassle and Ubuntu just works.  It was nice to know that packages were tailored to my system, but now I've got an AMD64 it's pretty tailored as it is.  I never really saw a huge difference in speeds except perhaps OO.org - but then again I installed the binary version in Gentoo as I couldn't be bothered to wait a few days for it to finish compiling.

All I can say is yay Ubuntu;)

---

### Post by psylence on 2006-03-28
Used Gentoo since 2004.0 til a few months ago...  I miss the flexibility of not having libs I don't use, but I could care less now that I can install apps in 5 seconds.  I got tired of maintaining my system, I shouldn't have to care, bad software makes you maintain it, good software just works.  I realize you don't need to maintain either if you do not update, but who wants to stay in the past?

Not to mention Gentoo's incredibly slow time to update (read: stabilize) to new versions of Gnome and KDE.  It's literally pathetic compared to Ubuntu.  I could care less about the reasons, I just want to use it, and Ubuntu lets me without huge unmaskings of unstable packages.

---

### Post by sclough on 2006-03-29
Thanks for all the thoughts.  I have my Gentoo system running well, but sounds like I might need to back it up and try Dapper here soon.  Thanks for all the thoughts.  Being a programmer, Gentoo really appeals to me, but having other things in life that demand time, if I could get about the same performance from Ubuntu's slick packing and update I'd give it a whirl.  Now I just need to figure out how to replace that Ubuntu logo with the Gnome foot :-k

---

### Post by syadnom on 2006-03-29
i was once a hardcore gentoo ricer.  in fact, i just started getting into 'gentoo' when the project was enoch linux.  was with gentoo right up til breezy came out.  quite frankly, i got over the fad of custom compiled programs.  even more i got sick of borked config files that emerge should have been able to manage but instead left up to me.  subtle changes messing up a program that was functioning verry well.  

gentoo is a great learning OS, i teaches linux basics well and gets a person comfortable with the command line.  

on the other hand, the OS should just work and one shouldn't have to 'work' on the OS to get the OS to work!  plug and play functionality is a must and gentoo has failed to fork a binary system that runs in parallel with the 'core' system.  some others have tried to do it(vidalinux) but without support of the gentoo devs it wont happen.  gentoo is in a constant state of flux and a binary counterpart will fail unless it is part of the plan. 

anyway, i find ubuntu dapper quite fast and friendly.  i have a 3.6Ghz P4 HT with 2Gig'O'Ram so i cant feel any difference in speed between gentoo and ubuntu.  i did run breezy on a athlonxp 1600 that once ran gentoo and breezy was a bit slower.  dapper is quite fast in comparison so i dont believe their is a real noticable performance difference.

hope this isnt too long winded for you.

---

### Post by djlosch on 2006-03-29
i did the gentoo route before i landed on ubuntu.

it just takes waaay too much time that i really just dont have.  i would prefer to have a compiled machine with only the stuff i need, but every time i ran a big emerge, something broke.  between all the admin i had to do, it didnt matter how much time i saved with 'faster running programs'... it was all effectively lost.  not the same in ubuntu.  besides, my OO.o in breezy takes about 2-8 seconds to be open to an edit window and the splash to be closed.

is ubuntu better overall? without a doubt
is ubuntu easier? without a doubt
is gentoo faster when sitting there doing a specific task? without a doubt.
is gentoo faster overall? hell no

---

### Post by tom-ubuntu on 2006-03-30
[QUOTE=djlosch]i did the gentoo route before i landed on ubuntu.

it just takes waaay too much time that i really just dont have.  i would prefer to have a compiled machine with only the stuff i need, but every time i ran a big emerge, something broke.  between all the admin i had to do, it didnt matter how much time i saved with 'faster running programs'... it was all effectively lost.  not the same in ubuntu.  besides, my OO.o in breezy takes about 2-8 seconds to be open to an edit window and the splash to be closed.

is ubuntu better overall? without a doubt
is ubuntu easier? without a doubt
is gentoo faster when sitting there doing a specific task? without a doubt.
is gentoo faster overall? hell no[/QUOTE]
Good summary which applies exactly to me aswell. Or in a short sentence: Gentoo consumes just way to much maintenance time.

---

### Post by halfvolle melk on 2006-03-30
[QUOTE=sclough]I like [...] to not build things in binaries that I never use.[/QUOTE]
I didn't see this mentioned above, might have missed it, but you could pop in the install CD and type 'expert' and only install the stuff you need/want. That can increase perfomance a great deal.

---

### Post by sclough on 2006-03-30
[QUOTE=halfvolle melk]I didn't see this mentioned above, might have missed it, but you could pop in the install CD and type 'expert' and only install the stuff you need/want. That can increase perfomance a great deal.[/QUOTE]

Thanks, I didn't know about that option.  I'll definitely try that.

---

### Post by otake-tux on 2006-03-30
I used gentoo for a full year.  After that I switched to ubuntu but I always come back to gentoo every 3 or 4 months.  See gentoo would be the ideal operating system if one did not have a life.  Life gets in the way of configuring.  Gentoo is faster than anyother distro I have used and I don't know what some poeple are talking about regarding boot up speed.  In my experience gentoo has always booted up everything faster than ubuntu.  But the diffrences are small.  The way I see it, gentoo is great if you take a week off from work, install it and cnfigure it and never update again untill you get another week off from work.

---

### Post by sclough on 2006-03-30
I'm in that stage where after two or three weeks (I lose count) I have Gentoo pretty much where I want it.  I'm just not looking forward to the maintenance when I want to update something so I'm considering Ubuntu since it seems very slick and much less maintenance.  Other than Linux, my other preference is OSX and I guess Ubuntu seems to be trying to be the OSX of Linux in that "it just works."

---

### Post by nouse66 on 2006-03-31
[QUOTE=psylence]
Not to mention Gentoo's incredibly slow time to update (read: stabilize) to new versions of Gnome and KDE.  It's literally pathetic compared to Ubuntu.  I could care less about the reasons, I just want to use it, and Ubuntu lets me without huge unmaskings of unstable packages.[/QUOTE]

I used Gentoo for several years and switched to (K|U)buntu this week for basically that same reason.  Portage was great but package updates just got slower and slower.
That and I wanted to mess with apt :)

---

### Post by sclough on 2006-04-03
Well, I archived off my gentoo install so I could go back if need be, and fired up dapper.  So far so good.  Things are a little slower, but not really miserable.  Open Office is one place where I see the biggest difference.  I do like how polished and easy things are.  The geek side of me missed building everything myself with Gentoo's execellent built system, but the rest of me enjoys using something that pretty much just works.  The only thing that bugs me is when dragging windows Metocity doesn't repaint very quickly and it looks sloppy.  It did it in Gentoo, but it's worse in Ubuntu.  I know this has been a pretty steady complaint about metocity.  Are there better window managers to plug into Gnome?  (It seems like I remember a lot of people used to use sawfish).  For that matter, does Ubuntu support that or do they try to keep Gnome one size fits all.

One post here mentioned running the install in expert mode.  I could not find that.  When I booted the CD, you could hit F6 to enter more options and I put expert in the list, but they were really only kernel options and it was ignored.  Specifically, since I don't know what all Ubuntu does by default yet, are there some obvious things I could disable/remove that would make things a little quicker?

---

### Post by mega on 2006-04-03
If your hardware supports it, switch to xgl+compiz it fixes the metacity issues

if not, upgrade? It really is worth it, it's much much better than stock dapper with metacity

---

### Post by sclough on 2006-04-03
I haven't really looked into it since I was under the impression that it was still alpha level.  What are the hardware requirements?  I'm running Dapper on a 2.4Ghz Celeron with 512mb RAM.  Not earth shattering, but not too pitiful.

---

### Post by Nutterpc on 2006-05-30
I used to be myself inot Gentoo too in a really big way, and am still involved a bit to this day

I found Ubuntu to catch my eye, installed it, tried it, fell in love

It very soon displaced windows, I've never looked back at doing the "full ditch" of MS :)

---

### Post by Sushi on 2006-05-30
Gentoo is a kick-*** distro. It's a great learning-experience and great OS overall. That said, it's not for everyone. But for some, it's perfect.

So, the answer to the age-old question "Which is better: Gentoo or Ubuntu?" is "it depends". They are different, with different goals and objectives. But that does not mean that one is overall superior to the other.

---

### Post by papangul on 2006-05-30
The most significant quality I found out of gentoo is that it is rock-solid in stability, like debian stable; performancewise I don't find much difference between Gentoo and Ubuntu. With the release of Dapper, stability and performance are non-issues(compared to gentoo), The only point is if somebody is a developer/programmer he is likely to prefer Gentoo.

The most negetive aspect of gentoo is that there are some issues with it's upgrade process. One has to know the system like the back of his hand to upgrade flawlessly.

Now that Ubuntu has matured, improving immensely in the departments of speed, stability, responsiveness, it's going to provide a very wothy alternative for Gentoo users.

---

### Post by pksings on 2006-08-09
I too am a former Gentoo user.  I switched from Gentoo mostly because updates kept breaking things, mostly apache/php but lot's of other stuff too, I went months ripping CD's to find out that it wasn't encoding the files at all, just deleting the .wav after creating the target directory for the finished encoded file. I had close to 100 empty directories of what should have been hundreds of.ogg files of my CDs. Some update had whacked oggenc. That was the last straw. I was also unable to sync my Palm with my desktop for over two years, always hoping the next update would fix it but it never did. During that same time period I was running Ubuntu 4 and then 5 on my laptop, no update ever broke anything and everything just worked, even my Palm. I hated to switch my working email/spam filter setup, it was doing a great job, but I finally had enough and switched. 

I really loved the Gentoo community, great forums, I learned a lot too. But after a while I longed for a distro that had as good as or better package system but didn't have to compile everything, even on my dual-cpu box it got really old. 

Ubuntu is not as fast, Gentoo was greased lightning. But it's not so much slower that I care, it's fast enough, and later this year when I upgrade it will be even faster. I love the package management system, it just works. Everything I need just works.  Up until Dapper I never had a problem. (I had a couple with it's install). It is and probably will remain my distro of choice, I love the integration and with the fine addition of "Automatix" it's just so easy to running right. 

Thank you to everyone who contributes, this is awesome!

PK

---

