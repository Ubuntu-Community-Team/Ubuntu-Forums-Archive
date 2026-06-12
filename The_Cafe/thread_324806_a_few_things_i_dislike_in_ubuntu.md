---
title: "a few things i dislike in ubuntu"
date: 2006-12-24
forum: The Cafe
---

### Post by brazzmonkey on 2006-12-24
hi all,
i just wanted to share about a few things that are bugging me in ubuntu. that doesn't mean i don't like it (nor use it), that only means a few things would need to be improved to get closer to the perfect system. some are bugs, some are only stuff that could be better. btw i'm using kubuntu 6.10, so a few remarks only apply to kubuntu. let's start :

- i'd like repos to be updated more often : kernel is still 2.6.17 whereas official vanilla is 2.6.19. kernel is a sensitive component so i can live with an older version rather than a cutting-edge buggy one. but i think there are a few packages that deserve more frequent updates. for instance, kerry (kde beagle frontend) got very much better lately, but the available version in repos is not updated. i installed it from debian repos. same for OOo 2.1. i'd like to know why some well working packages are not up-to-date in repos (or will only be available for next ubuntu release). you may think it's a matter of reliability (read : stability), but i'm pretty sure vanilla stuff i what is most stable ot there.

- laptop management, though it's already good, could be better. i have the feeling that laptops market share is costantly growing, and care should be taken to get things working properly on these machines. power management is something mystical to me, and i don't quite always understand how ubuntu manages these features...

- a few annoying bugs, although there are well-known, are not corrected. for instance, this monitor powersaving bug in kubuntu (settings are not saved, values reset to default ones upon reboot)

- many users need to search the forums or any available resource to get numpad enabled at boot time or when x starts. this is really stupid imho. this should be enabled by default, rather than installing numlockx and manually editing conf files.

- more intuitive network management is required, especially on the wifi side.

- multi-monitors shouldn't be such a hassle to configure. this is not an ubuntu issue, this is more like xorg issue. x (video display in general) should be something easy, straightforward to set up, not to say it should not require any special configuration from the user. i  never found a linux distro that was able to set up x correctly once and for all. i am sure this is a major issue for any user that comes from m$ world, and is used to get (display) working without further action. when it comes to user friendliness, take xorg.conf and imagine its contrary : you get it !

- adept_manager is crap (sorry devs !). i use it but i don't like it at all. it's not configurable, ergonomy is weird, it's just bad.

- boot time is too long (it's much better that it used to be though). same applies to suspend and resume (but i'm glad enough they work !)

ok, that should be it for today. note that i'm not an unhappy user, i only wish some few things would improve in the near future, so that it'd help linux (and ubuntu) spread. i think i've spent too much time to get a (almost perfectly) functional system in the past few weeks. and yes, i do report bugs when i'm sure they're not already reported and they're worth to be.

oh, and many thanks to devs, and merry christmas to you all !

---

### Post by dbbolton on 2006-12-24
> - many users need to search the forums or any available resource to get numpad enabled at boot time or when x starts. this is really stupid imho. this should be enabled by default, rather than installing numlockx and manually editing conf files.

i thought the same thing, but then i said "all i have to do is press one key. it takes half a second. what is wrong with me ?"

:)

---

### Post by Chimes on 2006-12-24
> **brazzmonkey said:**
> 
- i'd like repos to be updated more often : kernel is still 2.6.17 whereas official vanilla is 2.6.19. kernel is a sensitive component so i can live with an older version rather than a cutting-edge buggy one. but i think there are a few packages that deserve more frequent updates. for instance, kerry (kde beagle frontend) got very much better lately, but the available version in repos is not updated. i installed it from debian repos. same for OOo 2.1. i'd like to know why some well working packages are not up-to-date in repos (or will only be available for next ubuntu release). you may think it's a matter of reliability (read : stability), but i'm pretty sure vanilla stuff i what is most stable ot there.


You'd like repositories to be updated more often? Why don't you help out and make it happen? Or is it not *that* important to you? ;) 

Just kidding. But how do you expect someone to respond to that? "Wow, he's right, we've been updating repositories too slowly for no reason. Why did we spend all that time playing foosball when we could've been updating packages? I didn't know people actually cared about that kind of stuff! I'll get right on that!" :p 

Honestly, the people who are working on ubuntu are working on it as much as they care to work on. And having the latest packages, in all honestly, is really not important unless it's a server package. If you want the latest version of a package so bad, you can always get it from the application's site.

Yeah, it'd be nice to have all the repos be recent, but it's not a priority, and it shouldn't be. I would rather have more people working on the next version of ubuntu than on keeping repositories split-second up-to-date. 

> laptop management, though it's already good, could be better. i have the feeling that laptops market share is costantly growing, and care should be taken to get things working properly on these machines.

This is a valid concern. One you might investigate further.

>  power management is something mystical to me, and i don't quite always understand how ubuntu manages these features...

Have you tried posting questions of this nature on the forum?

> a few annoying bugs, although there are well-known, are not corrected. for instance, this monitor powersaving bug in kubuntu (settings are not saved, values reset to default ones upon reboot)

Is that because the settings are hard to fix or because people are being lazy? I suspect that it's because they're hard to fix.

> many users need to search the forums or any available resource to get numpad enabled at boot time or when x starts. this is really stupid imho. this should be enabled by default, rather than installing numlockx and manually editing conf files.

This is also a valid concern, but do you expect Canonical to re-release Edgy just to fix the numpad thing?

> more intuitive network management is required, especially on the wifi side.

This is a very complicated issue involving new hardware, uncooperative or uncaring businesses, driver blobs, tough protocols to work with, and the difficulty of coding drivers. I agree with you, I just think that it isn't going to be an easy, or sometimes it isn't going to be a possible, thing to do.

> boot time is too long (it's much better that it used to be though). same applies to suspend and resume (but i'm glad enough they work !)

Why is it that everyone notices boot time so much? Everyone whines and whines so much about boot time but don't give a damn about the excess seconds they waste when running and starting other programs during all of their session. The time spent on booting, (which you can predict and spend doing something else), is in total, much less than the time wasted on processing sloppy code during runtime. 

Ah well. If it's what people notice, I suppose it's what needs to be worked upon.

> note that i'm not an unhappy user, i only wish some few things would improve in the near future, so that it'd help linux (and ubuntu) spread.

Why is the spread of linux and ubuntu so important? :confused: 

It's a good desktop, but if it's that good, it'll spread on it's own.

And if it "needs help" to spread fast enough, maybe it's not in a position to serve the needs of those other users in the first place.

Let them use Windows. While I do believe linux package developers should strive for improvement of their work, I do not believe they are under an obligation to do so in a way that will bring linux to mainstream appreciation.

---

### Post by Tomosaur on 2006-12-24
> **Chimes said:**
> 
Why is the spread of linux and ubuntu so important? :confused: 

It's a good desktop, but if it's that good, it'll spread on it's own.

And if it "needs help" to spread fast enough, maybe it's not in a position to serve the needs of those other users in the first place.

Let them use Windows. While I do believe linux package developers should strive for improvement of their work, I do not believe they are under an obligation to do so in a way that will bring linux to mainstream appreciation.

Currently, the personal computer market is stagnant, lacks innovation, and is at the behest of Microsoft who use threats to make money.  Name one recent innovation from Microsoft. Can't think of one? Ok, now try Apple? Got a whole bunch? Thought so. So why is the desktop computer saturated with Microsoft products? Because there's no choice. Most PCs come with Windows installed - most users are ignorant that anything other than Windows or OSX exist. Linux is an excellent operating system. Yes, it has problems, which can be solved - but they will NEVER be solved unless Linux gains a greater market share, and forces real innovative competition to take place again. Many linux advocates, particularly the old guard, really couldn't care less about Linux growing in popularity, but in terms of technology and personal computing, the next few years have immense potential. The danger is of Microsoft once again keeping the majority market and crippling innovation yet again, which is only bad for the end user. 

There are also a bunch of ethical reasons - but these are mostly interested in getting rid of Windows dominance rather than making Linux a more appealing option.

Most commercial sofware released is either a more modern version of an already existing product, or a game. This is no way to advance the industry as a whole. Real interesting products generally come from small startups and are either shunted aside by already established big players, or absorbed by another company who generally just forgets about it. Google and Apple are the two vendors releasing anything truly new - and Apple keeps everything locked down, while Google's stuff is generally under-marketed.

---

### Post by neowolf on 2006-12-24
One thing that annoys me about Ubuntu is the **stupid**, **stupid** idea of packaging all restricted kernel modules into one package, this means that if you update the nvidia driver the restricted-modules package and the new kernel module fight with other to get loaded into the kernel and you have to mess about with /lib/modules to get the damn X server to work again :mad:

---

### Post by meng on 2006-12-24
More than just a few things there!

Repositories: want newer versions of software? perhaps check out Debian etch, or (if repo SIZE is not a major concern) PCLinuxOS
Laptop management: I agree, it's improving slowly though.
Numlock: I just installed numlockx, I don't know about these configuration files you mentioned.
Network management: I agree, but I've always found Windows networking to be rather unintuitive also.
Multi-monitors: a common problem, but you overstate the significance by suggesting that any MS user cares about this. It's a minority of users that work with multiple monitors; of course, for those who do, it may be very important to the individual.
Adept: I don't use KDE, can't comment. Synaptic is ok, and command line is great.
Boot time: Soon enough it will be streamlined to the point where the computer is ready before you switch it on!!! But have you checked out Windows boot times lately? Ugly!

Thanks for the input.

---

### Post by insane_alien on 2006-12-24
boot times? its linux you don't need to reboot. just leave your computer on. i do and it hasn't slowed down. oh and if the numlock is enabled by default in the distro how is that going to affect laptop users like myself. i don't want to have to turn it off all the time. and option would be good so that you can click a box and it'll be on or off when you boot. default off i hope.

---

### Post by banjobacon on 2006-12-24
> **Chimes said:**
> 
Why is the spread of linux and ubuntu so important? :confused: 

[https://bugs.launchpad.net/distros/ubuntu/+bug/1](https://bugs.launchpad.net/distros/ubuntu/+bug/1)

---

### Post by macogw on 2006-12-24
alsaconf doesn't exist in the Ubuntu repos.  I downloaded a Debian version.  I don't know why, but apparently nobody using Ubuntu will ever have a sound card that requires configuration (yeah, that thing where my computer randomly doesn't have any sound, that's just my imagination)

insane_alien, you shouldn't leave your laptop on all the time.  The heat can shorten your battery and hard drive lives to 2 or 3 years when they could otherwise last 5+ if the computer's only on for a few hours a day.

Regarding network management:  this is being dealt with in Feisty.  They are making network roaming much easier by having network managers installed by default.

Regarding packages:  join MOTU and help package up newer versions.

---

### Post by tseliot on 2006-12-24
> **brazzmonkey said:**
> - i'd like repos to be updated more often : kernel is still 2.6.17 whereas official vanilla is 2.6.19. kernel is a sensitive component so i can live with an older version rather than a cutting-edge buggy one. but i think there are a few packages that deserve more frequent updates. for instance, kerry (kde beagle frontend) got very much better lately, but the available version in repos is not updated. i installed it from debian repos. same for OOo 2.1. i'd like to know why some well working packages are not up-to-date in repos (or will only be available for next ubuntu release). you may think it's a matter of reliability (read : stability), but i'm pretty sure vanilla stuff i what is most stable ot there.
Distros such as Arch Linux and Fedora are kept up-to-date at the cost of a bit of stability. You could try them.

I don't discuss Ubuntu's policy but I would really like to see Openoffice  updated to the latest version ;)

> **brazzmonkey said:**
> - multi-monitors shouldn't be such a hassle to configure. this is not an ubuntu issue, this is more like xorg issue. x (video display in general) should be something easy, straightforward to set up, not to say it should not require any special configuration from the user. i  never found a linux distro that was able to set up x correctly once and for all. i am sure this is a major issue for any user that comes from m$ world, and is used to get (display) working without further action. when it comes to user friendliness, take xorg.conf and imagine its contrary : you get it !
Xorg 7.3 will make it easier :mrgreen:  

> **brazzmonkey said:**
> - adept_manager is crap (sorry devs !). i use it but i don't like it at all. it's not configurable, ergonomy is weird, it's just bad.
I beg to differ. I think it's a matter of taste.

---

### Post by tseliot on 2006-12-24
> **neowolf said:**
> One thing that annoys me about Ubuntu is the **stupid**, **stupid** idea of packaging all restricted kernel modules into one package, this means that if you update the nvidia driver the restricted-modules package and the new kernel module fight with other to get loaded into the kernel and you have to mess about with /lib/modules to get the damn X server to work again :mad:
Actually you can blacklist a module of the restricted-modules in /etc/default/linux-restricted-modules-common

Then you can use your own modules.

---

### Post by Tomosaur on 2006-12-24
> **insane_alien said:**
> boot times? its linux you don't need to reboot. just leave your computer on. i do and it hasn't slowed down. oh and if the numlock is enabled by default in the distro how is that going to affect laptop users like myself. i don't want to have to turn it off all the time. and option would be good so that you can click a box and it'll be on or off when you boot. default off i hope.

Believe it or not, some linux updates do actually require you to reboot. Just not nearly as many updates as Windows.

---

### Post by macogw on 2006-12-24
> **Tomosaur said:**
> Believe it or not, some linux updates do actually require you to reboot. Just not nearly as many updates as Windows.

They're generally the ones that install an updated kernel.

---

### Post by brazzmonkey on 2006-12-25
a few things regarding your comments :

- numlock : yes it's just a matter of pressing a button, but every people i know uses a num pad as a num pad. sometimes before logging in you just forget you have to enable num lock, then, because of that you get your password wrong, have to re-type it, etc. just a matter of a few econds, i know, but very irritating, though. and i personally had to edit a kdm conf file to get numlockx start with kdm. i knew how to do it, but surely many newbies spend quite some time trying to have num pad activated at startup. i don't say it should be enabled by default, i only think this is the kind of stuff that should be intuitively configurable.

- regarding frequent repo updates, i reckon it's hell of a work. but some popular stuff (office suites, desktop stuff...) should be kept up-to-date. and yes i com from gentoo, then archlinux, and i used to have (nearly) latest stuff. gentoo is for geek, arch is simply amazing but i couldn't afford configuring my whole laptop, especially in terms of connectivity.
my opinion is that arch is a really good dektop distro, but i don't think it's really suitable for a laptop. i never had a problem with arch, except once but i was the culprit.
i'm just a linux user, i don't have any particular computer skills, but if i can help without speding more than a few hours per months, i'll do it.

boot time is something that matters when you have a laptop. leaving your computer on while not using it is just plain stupid, period.

@Chimes : i can help packaging if it doesn't eat my time and if you tell me how to easily do it. about laptop power management, yes, i could investigate this one but i suppose this should a new thread. maybe soon. and yes, i posted questions, but they are still unanswered and i'm not the kind of guy that floods a forums (though i suppose flooding this one would be a challenge).
about network management, i never said it was easy, and i appreciate what has already been achieved. but there's still room for improvements.
linux is getting ready for desktop. but not for widespread use. this could be another thread too (i guess there already are such threads in these forums, probably nearly trolling ones). whether or not linux should be widespread is another matter.

@meng : well i suppose x configuration and multi-monitor stuff only express the very same idea : this is a pain. just as configuring the new mouse i got for christmas.

you may think i have become lazy since i got this laptop, truth is i have been getting busy. i don't have time to "geek" anymore, at least as much as i used to. i just need things to work, and this is the main reason i came to ubuntu. i'm just surprised how some apparently simple features are a pain to set up... and so far i'm just sure that i'm not as productive as i could be if i were using windows. but this is probably a matter of time...

---

### Post by glabouni on 2007-01-18
> **dbbolton said:**
> i thought the same thing, but then i said "all i have to do is press one key. it takes half a second. what is wrong with me ?"
:)

and then i figure out it a press of one key each login, which tends to add up to a huge pile of seconds over a few years. especially if you take into account all the failed login attempt because you failed to remember to press that key before trying to log in.

there's two way to fix this in a satisfying manner:
1 - respect the BIOS setting "boot up num lock".
2 - give the user the choice to "enable/disable num lock at boot" in system preferences. I understand this has been in kde for quite some time.
2b - offer choice during installation procedure.

enjoy my mathematics mastery :mrgreen:

---

### Post by daynah on 2007-01-18
I fixed my numlock so long ago I really don't remember how I did it. I just... followed a simple guide and I don't even notice that it's not on. And currently, I having failing hardware (memory grrr) so my computer is constantly being rebooted... it would get very annoying if I hadn't of had numlock on  automatically.

Command line is very, very easy. 98% of the time you'll just follow guides on the forums. That's one of the wonderful things about Linux... free, and good, support!

Regarding the importance we place on spreading Ubuntu, I also think that as Ubuntu becomes better it will spread itself. Virtue is its own reward. But remember that most of the people using Ubuntu do not know how to create programs or really do any advanced coding work... but we want to help! So the only way we can think of helping is to spread the news of the hard work you developers have been doing.

BrazzMonkey, You're on Edgy... do you realize that there's another version of Ubuntu out there that's more, well "Fiesty?" If you must be on the cutting edge, maybe you could try that. From what I hear, the betas haven't been that bad. I tried Edgy on my laptop, but I liked both Dapper's power management and it's wifi management better. To help the project, I also politely told the developers why I preferred Dapper's laptop handling over Edgy, though I was in the minority. They respected my opinion because it was an important issue, that I fixed on my own, because I took time to wait and make sure it really was a problem and not just me being nitpicky, and because I submitted it in a thread already made for that purpose (how did you like the laptop management).

[FONT="Comic Sans MS"]But remember, when you complain things not "getting done" to your liking... Generally, the people who are working on this project called "Humanity towards others" are just bums like you and me. They're just sittin' around, trying to make a better os so that we're not pidgeon holed. They have other jobs; they have families, and they have other interests. The majorty of the people working on all those programs in those repos do not get paid for that work. They're just doing it for you. What an ultimate charity project. So, even though I know we all eagerly await the next release of our favorite programs because we love them so much, let us be careful not to bite the hand that feeds and remember that this Linux distribution is what it is only because of a whole lot of really nice and kind bums taking thousands of hours out of their lives to make our lives better.[/FONT]

---

### Post by evolvedlight on 2007-01-18
Ok. I agee with the stuff about adept. I hate it. I press go and it crashes, i've never had it work a single time.

Microsoft does innovate, sorry dude. Windows Home Server - yup. No new technology, but a user-friendly approach. Much more user-friendly than making one with Linux, for example. 

Steve

---

