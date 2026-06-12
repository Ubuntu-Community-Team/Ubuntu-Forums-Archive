---
title: "Ubuntu rage- I've had enough"
date: 2009-03-08
forum: Testimonials &amp; Experiences
---

### Post by rotogenray on 2009-03-08
No really, really- I used to love Ubuntu. Its the first thing I got to actually work on my computer with any level of decency. debian was a nightmare, fedora just felt weird, openSUSE was rigid, but ubuntu worked, it worked simply and beautifully from the getgo.

And for someone switching from windows XP, its all I was really looking for.

There were some problems, sure, but I overlooked them. But months have gone by and I've not been able to fix the thing and the computer- which is almost new- isn't preforming anywhere near up to par.

Apparently it won't detect my video card- which is built into the motherboard. My computer is an HP Pavillion a1632x with an AMD Athalon 64 X2 dual core processor 3800. My graphics card is NVIDIA GeForce 6150 LE.

Ubuntu is "unable to find a valid framebuffer device" so it runs in low graphics mode, which is an acceptable 1280X1024, but it runs like its an old POS instead of a barely 3 year old dual core computer.

There is ONE other person who has this problem and ZERO people who have the answer. So I set out to find out how to fix it myself. I screwed with xorg, which didn't do much good. I activated and messed with the framebuffer (which is kind of hard), which improved the graphics while the system started up until I logged in- then it couldn't find it again. I tried the drivers for my graphics card, each of which caused the system to not even allow me to log in. I put another graphics card in my computer which ubuntu didn't detect and couldn't see no matter what I did. I reinstalled the OS, for the hell of it, and after pulling my hair out for weeks over this I'm done.

I have had enough.

I just want a linux distro that will detect my hardware... and where people can at least, if they don't know, point you in the general direction of the answer. I've received very little help on this issue and thats a small part of what peeves me off about the whole ordeal.

[http://ubuntuforums.org/showthread.php?p=6499691](http://ubuntuforums.org/showthread.php?p=6499691)
[http://ubuntuforums.org/archive/index.php/t-1032043.html](http://ubuntuforums.org/archive/index.php/t-1032043.html)
[https://answers.launchpad.net/ubuntu/+question/61712](https://answers.launchpad.net/ubuntu/+question/61712)

So... I guess I'll be putting fedora on here... and live with the horrible dependancy nightmares and package mismanagement associated with that.

---

### Post by RichardLinx on 2009-03-08
Why do people insist on these tantrums? So Ubuntu didn't work and your moving onto Fedora and posting this on a forum filled with Ubuntu fanboys is going to achieve..?

I'll mention one thing, if Fedora is able to detect your graphics card and install a wprking driver for it then there's no reason why, after "months" of trying to get it to work in Ubuntu you couldn't get it to work by now. Either you didn't put much effort in or you spent "months" on the issue and your puny brain couldn't come up with a solution.

Please, don't take offense at this it was pure satire. This is an example of some of the replies you can expect to see in the coming minutes.

---

### Post by BGFG on 2009-03-08
> **rotogenray said:**
> 

Apparently it won't detect my video card- which is built into the motherboard. My computer is an HP Pavillion a1632x with an AMD Athalon 64 X2 dual core processor 3800. My graphics card is NVIDIA GeForce 6150 LE.

Ubuntu is "unable to find a valid framebuffer device" so it runs in low graphics mode, which is an acceptable 1280X1024, but it runs like its an old POS instead of a barely 3 year old dual core computer.

with that.

Had enough, but rather than just install fedora and be done with it, why not post my problem in detail in the cafe masked as a rant so that an experienced user will chime in with the age old: 'No, please don't leave! here, lets fix this together'.

I'm no old sage but here goes:
my setup is a Dell inspiron 531, Athlon X2 4000, GeForce 6150SE nForce 430 on board. Currently using 180.35 in Ubuntu 64bit.
Try the 180.x series drivers. link below.

[http://ubuntuforums.org/showthread.php?t=1089231](http://ubuntuforums.org/showthread.php?t=1089231)

And please, Don't leave!!!

---

### Post by rotogenray on 2009-03-08
> **RichardLinx said:**
> Why do people insist on these tantrums? So Ubuntu didn't work and your moving onto Fedora and posting this on a forum filled with Ubuntu fanboys is going to achieve..?

I'll mention one thing, if Fedora is able to detect your graphics card and install a wprking driver for it then there's no reason why, after "months" of trying to get it to work in Ubuntu you couldn't get it to work by now. Either you didn't put much effort in or you spent "months" on the issue and your puny brain couldn't come up with a solution.

Please, don't take offense at this it was pure satire. This is an example of some of the replies you can expect to see in the coming minutes.

I have grievances! And FYI ubuntu is still on my computer, so if YOU have a solution, feel free to offer one.

I worked passively on it for a while. Really, at first, it didn't bother me. But then my screen wouldn't refresh unless I scrolled on the page or dragged the window around, and I wanted desktop effects with linux but was let down there.

I looked deep within the recesses of the internet to find a set of instructions on how to screw with the framebuffer that were fairly complex in nature. Theres my effort, which wasn't sucessful, lets see YOUR puny brain come up with anything better!

---

### Post by rotogenray on 2009-03-08
> **BGFG said:**
> Had enough, but rather than just install fedora and be done with it, why not post my problem in detail in the cafe masked as a rant so that an experienced user will chime in with the age old: 'No, please don't leave! here, lets fix this together'.

I'm no old sage but here goes:
my setup is a Dell inspiron 531, Athlon X2 4000, GeForce 6150SE nForce 430 on board. Currently using 180.35 in Ubuntu 64bit.
Try the 180.x series drivers. link below.

[http://ubuntuforums.org/showthread.php?t=1089231](http://ubuntuforums.org/showthread.php?t=1089231)

And please, Don't leave!!!

I don't hate ubuntu, I even recommend it. But it was askin for it like a redheaded step child.

sure, we'll say it was that... really this was just cathardic

I'll give it a shot...

---

### Post by zenithdave on 2009-03-08
The 61xx range of on-board Nvidia range of chips are a total nightmare but its not the fault of Ubuntu.

I have a 6100 and had to resort to a really old driver but at least i have a decent resolution now with a few minor video artifacts.


Have a search for 'nvidia ubuntu 6100 video problems'

Closed drivers are the problem

---

### Post by Skripka on 2009-03-08
We all distro hop sooner or later, and for various reasons.

---

### Post by BGFG on 2009-03-08
> **zenithdave said:**
> The 61xx range of on-board Nvidia range of chips are a total nightmare but its not the fault of Ubuntu.

I have a 6100 and had to resort to a really old driver but at least i have a decent resolution now with a few minor video artifacts.


Have a search for 'nvidia ubuntu 6100 video problems'

Closed drivers are the problem

That's so wierd, Mine works pristinely. Only time it gave a problem was when i messed with the refresh rate. Outside of that, it's been perfect.

---

### Post by Vince4Amy on 2009-03-08
Well just switch to Fedora if that's what you're going to do. I only used Kubuntu for ONE version and that was 6.06 and after that I didn't like it and switched back to other distros, but I didn't go round on this forum and create threads saying that I was doing so.

> So... I guess I'll be putting fedora on here... and live with the horrible dependency nightmares and package mismanagement associated with that.

Really I suggest you switch back to Windows or whatever you were using before because you're not researching obviously, if you're just going to assume misinformation like that, then you will not have much chance getting the system to work anyway since you're slamming it before you've even tried it. There is no Dependency nightmares or Package Mismanagement in Fedora and I've used Red Hat based distros a lot over the course of 8 years of using Linux. The Only shortcoming are which pretty much any dependency handling distro has.

---

### Post by zenithdave on 2009-03-08
> **BGFG said:**
> That's so wierd, Mine works pristinely. Only time it gave a problem was when i messed with the refresh rate. Outside of that, it's been perfect.

So many variables so little time ;)
Possibly a regional thing like wireless channels 12-13 being switched off in the EU?

---

### Post by BGFG on 2009-03-08
> **zenithdave said:**
> So many variables so little time ;)
Possibly a regional thing like wireless channels 12-13 being switched off in the EU?

So little time indeed. I think I have good Linux juju :)
The wireless channels crap out nvidia drivers ?

---

### Post by RichardLinx on 2009-03-08
> **rotogenray said:**
> I have grievances! And FYI ubuntu is still on my computer, so if YOU have a solution, feel free to offer one.

I worked passively on it for a while. Really, at first, it didn't bother me. But then my screen wouldn't refresh unless I scrolled on the page or dragged the window around, and I wanted desktop effects with linux but was let down there.

I looked deep within the recesses of the internet to find a set of instructions on how to screw with the framebuffer that were fairly complex in nature. Theres my effort, which wasn't **sucessful**, lets see YOUR puny brain come up with anything better!

Why would I need to? I'm not the one winging about not being able to get my graphics card to work. I don't care to offer tech support to someone who whines about there problem in the community cafe, especially when they say they've put in months of effort and it's just a simple driver issue. I see you haven't even tried downloading the driver. > I'll give it a shot 
Yet you've put in so much effort. Yeah right.

PS: You made a spelling error.;)

---

### Post by zenithdave on 2009-03-08
> **BGFG said:**
> So little time indeed. I think I have good Linux juju :)
The wireless channels crap out nvidia drivers ?

No sorry 2 different issues i have on 2 seperate machines but the wireless is fixed, was down to regional configuration and i wonder if video refresh rate could be linked in that area?

---

### Post by BGFG on 2009-03-08
What driver are you currently using and on what architecture ? have you tried 180.37 yet ?

---

### Post by Rocket2DMn on 2009-03-08
Moved to Ubuntu Testimonials & Experiences.  Please keep it civil.

---

### Post by stchman on 2009-03-08
> **rotogenray said:**
> No really, really- I used to love Ubuntu. Its the first thing I got to actually work on my computer with any level of decency. debian was a nightmare, fedora just felt weird, openSUSE was rigid, but ubuntu worked, it worked simply and beautifully from the getgo.

And for someone switching from windows XP, its all I was really looking for.

There were some problems, sure, but I overlooked them. But months have gone by and I've not been able to fix the thing and the computer- which is almost new- isn't preforming anywhere near up to par.

Apparently it won't detect my video card- which is built into the motherboard. My computer is an HP Pavillion a1632x with an AMD Athalon 64 X2 dual core processor 3800. My graphics card is NVIDIA GeForce 6150 LE.

Ubuntu is "unable to find a valid framebuffer device" so it runs in low graphics mode, which is an acceptable 1280X1024, but it runs like its an old POS instead of a barely 3 year old dual core computer.

There is ONE other person who has this problem and ZERO people who have the answer. So I set out to find out how to fix it myself. I screwed with xorg, which didn't do much good. I activated and messed with the framebuffer (which is kind of hard), which improved the graphics while the system started up until I logged in- then it couldn't find it again. I tried the drivers for my graphics card, each of which caused the system to not even allow me to log in. I put another graphics card in my computer which ubuntu didn't detect and couldn't see no matter what I did. I reinstalled the OS, for the hell of it, and after pulling my hair out for weeks over this I'm done.

I have had enough.

I just want a linux distro that will detect my hardware... and where people can at least, if they don't know, point you in the general direction of the answer. I've received very little help on this issue and thats a small part of what peeves me off about the whole ordeal.

[http://ubuntuforums.org/showthread.php?p=6499691](http://ubuntuforums.org/showthread.php?p=6499691)
[http://ubuntuforums.org/archive/index.php/t-1032043.html](http://ubuntuforums.org/archive/index.php/t-1032043.html)
[https://answers.launchpad.net/ubuntu/+question/61712](https://answers.launchpad.net/ubuntu/+question/61712)

So... I guess I'll be putting fedora on here... and live with the horrible dependancy nightmares and package mismanagement associated with that.

Did you try going to System--->Administration--->Hardware Driver?  There will be an entry to enable the nvidia driver.

According to the package manager the 6150LE has been supported since the pre 100 drivers.

---

### Post by RaiCoss on 2009-03-08
> **stchman said:**
> Did you try going to System--->Administration--->Hardware Driver?  There will be an entry to enable the nvidia driver.

According to the package manager the 6150LE has been supported since the pre 100 drivers.

I had this problem too with my pc's onboard GeForce 7050. Try the 177 drivers, the 180's don't work.

---

### Post by gtrtx on 2009-03-08
I've been using Ubuntu for quite some time and I've always used NVIDIA cards as they seem to have the best 3d support in linux. 

There have been several occasions that the drivers have been troublesome to get installed but I usually do manage it. 

This last time I used envyng from the repos and installed the 180.11 driver. Works great. 

You might give that a shot. It's worked great for me on several occassions when the Hardware Drivers method has failed.

Good Luck!

---

