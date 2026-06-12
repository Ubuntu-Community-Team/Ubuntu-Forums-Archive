---
title: "Fix the Ubuntu Desktop"
date: 2013-06-03
forum: Ubuntu, Linux and OS Chat
---

### Post by jlholmes21 on 2013-06-03
**BEFORE I BEGIN I WILL SAY I DO TEND TO RAMBLE ON A BIT IN PLACES BUT PLEASE READ ALL OF IT. THANKS! I ALSO APOLOGISE IF I SEEM RUDE BUT I GUESS THAT IS JUST MY WRITING STYLE.**

A few days ago Mark Shuttleworth marked the first ever bug as fixed. The bug, Microsoft has a majority market share, is marked as fixed although it really isn't. Mark's reasoning is that the concept of what the PC stands for is entirely different today to what it was in 2004. In a way he is correct to say that but it doesn't mean the bug is fixed. The desktop and the mobile environment are still different. The mobile gives me an environment to easily click install applications from a software center and swipe my fingers across the screen to get things done... **THAT ISN'T THE DESKTOP**. The desktop is my keyboard and my mouse, **NOT A TOUCH SCREEN**. I can understand we are moving to a world in which desktops and mobiles are, in a way, the same market but we shouldn't be moving to a world where we think they are the same.

Now I'm going onto some Ubuntu specific things as that is partly to do with this entire rant. I love the fact that Canonical want to move Ubuntu into the mobile space with an OS built for phones and tablets but can you not slap that onto my desktop as well. My desktop is my desktop, not my mobile device. With the development of Ubuntu Touch we have seen Mir come along. On Ubuntu Touch this isn't an issue, the system is new and it will grow along with Mir but the issue is on the desktop. XOrg is the current system we use on the desktop and (eventually) Wayland will replace it but if Canonical throw Mir into the mix on the desktop we could see an environment with 3 different graphics servers (or whatever the term is for them) and for the Linux desktop that is bad. You have got everything at the moment designed to use XOrg but if we are going to be replacing that, having both Mir and Wayland will cause problems. Some people will use Wayland and others will pick up Mir... then what... We have a split in  the community of the replacement and that will slow up redevelopment of applications to use the new system and then the Linux desktop as a whole suffers from the decision to take something from the mobile space and stick it into the desktop space. [B]KEEP THEM SEPARATE!
[/B]
Now lets move onto Ubuntu itself. I like Unity, the desktop environment works well and the *majority* of things are nicely integrated... *notice the keyword of that sentence*. You'd think that after all this time even the default applications would use the Unity menu bar instead of wasting desktop space. There are several default applications that do not support the Unity menu bar yet you continue to ship them with Ubuntu. The one great thing about the open source community is the fact it is open source, why not change the source code yourself so it actually *fully supports the product* you are shipping instead of actually ruining part of my experience. It would take one developer a day or two to make sure the applications either support the features it should or be replaced. The Unity menu bar was just an example but you get the idea and if you don't I'm basically saying to make sure you ship the software that supports the key part of your product.

Now the Ubuntu Software Center. Like many great ideas it is appallingly executed. I'd love to be able to head into the USC and just speedily install the applications I need and then let the software updater do the rest but you seem to be focusing on some old school idea of not changing things that aren't broken. It reminds me of my Dad who would still use XP for the rest of his life if developers didn't ditch it because of that magical thing called money. If a new stable version of a package comes out why isn't it put into the USC for the current stable and LTS release instead of waiting for the next release to finally release it. This is where distributions like Arch have an advantage. I'm not asking you to go entirely rolling release on the situation and make sure we get the latest kernel the moment it is out and packaged but if an application, GIMP for example, gets a new stable version it should be straight into the repository (and USC with that) for the support releases as soon as you can get it in their. Building and updating packages wouldn't even take that long and you easily make an extra job or two out of it to take the work load off of people that could be needed elsewhere in your development. You wouldn't do that in the mobile environment though. You wouldn't wait to put in a stable package for a piece of software for Ubuntu Touch, it would be in there ASAP... so why not on the desktop? I'll let you answer that one.

Now the most important bit. Actually getting Ubuntu out into the world. If you can create this wonderful environment on the mobile and the desktop and keep them what they actually are you will have much more chance of getting bigger OEMs to actually focus more on shipping Ubuntu devices instead of being like Dell or HP at the moment and shipping a system or two every so often but not doing it how it should be done. System76 are the perfect example of a company that ship Ubuntu correctly, they produce systems that are designed to run Linux and not just Windows boxes that are tweaked to run Linux better. You need to up your game. If you can provide this perfect (or as close to it as humanly possible) system that you want to, more OEMs will pick it up and then take more time to ship better Ubuntu systems. If you can tick off the things I've mentioned above you are already doing large parts of the job. You are providing a system that ships the latest packages, you are providing an integrated experience and the users that are switching will find it easier to work with. And you are providing a system that is fit for the desktop.

Now I will just conclude it all for those who prefer the easier read. Don't make the mobile and desktop one. Yeah the line is already blurred but this issue can be fixed. Keep up the work in the mobile space but don't let that destroy the desktop as they are still both separate despite what people think. Make sure the Ubuntu desktop ships ready to be competitive, integrated and up to date. Keep pushing to overtake Microsoft instead of marking this unfixed bug as fixed. I've said it before and I will say it again, the desktop and the mobile markets aren't the same or together, they may do similar thing but they are different. Keep that in mind when you make your decisions and you are more likely to be successful.

I'm going to leave that here. I could go on for hours ranting about one little thing within the entire world of Ubuntu or even Linux as a whole but again if we work one step at a time we will continue to move forward.

---

### Post by castrojo on 2013-06-03
>  It would take one developer a day or two to make sure the applications either support the features it should or be replaced. The Unity menu bar was just an example but you get the idea and if you don't I'm basically saying to make sure you ship the software that supports the key part of your product.

There's been a bunch of work to make Firefox and Libreoffice use the global application menu. It's not as easy as you say it is, certainly not a day!

> You wouldn't wait to put in a stable package for a piece of software for Ubuntu Touch, it would be in there ASAP... so why not on the desktop? I'll let you answer that one. 

Click packages will fix this: [https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037074.html](https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037074.html)

> Now I will just conclude it all for those who prefer the easier read. Don't make the mobile and desktop one. Yeah the line is already blurred but this issue can be fixed. Keep up the work in the mobile space but don't let that destroy the desktop as they are still both separate despite what people think.

If anything I think working on mobile has improved the desktop experience quite a bit. You don't really go into any detail as to why having the same OS on three form factors is a bad idea.

---

### Post by MadmanRB on 2013-06-03
Actually concerning unity, it is really progressing if you use Ubuntu 13.04 as more apps can now use the globalmenu.
And as for mobile and the future, well yes unity will be altered to fit both touchpads and desktops.
It will change yes but as far as we know the changes that are to be made will work both ways.
Unity next is still fresh and new so it will take time, thus why I think the current unity development branch will still be around for 14.04.
We wont see the mobile stuff fully take overt till at least 14.10 or 15.04.

---

### Post by jlholmes21 on 2013-06-03
[SIZE=2][FONT=arial]> There's been a bunch of work to make Firefox and Libreoffice use the global application menu. It's not as easy as you say it is, certainly not a day!

Some of the default apps still don't support the Unity Global Menu yet they are all Open Source. Why not rewrite the source to support it

> Click packages will fix this: [https://lists.ubuntu.com/archives/ub...ay/037074.html]("https://lists.ubuntu.com/archives/ubuntu-devel/2013-May/037074.html")

What about all the things in the USC already. I was also talking about making sure we get the latest packages into the repositories once they are released instead of having to wait on them

> If anything I think working on mobile has improved the desktop experience quite a bit. You don't really go into any detail as to why having the same OS on three form factors is a bad idea.

I was talking about how the two devices are just the same operating system slapped onto both. Like how Microsoft did the Surface Pro and normal desktops and laptops. Exactly the same OS on two different devices that need two different type of systems on them. Ubuntu Touch is good and has benefited the desktop but making them too integrated is also bad as the line between desktop OS and mobile (phone/tablet) OS just disappears and that is why I am partly against the way things are being done at the moment. Keep similarities between both of them if it benefits the user experience on both but don't make the same thing just slapped onto the devices differently.[/FONT][/SIZE]

---

### Post by castrojo on 2013-06-03
> **jlholmes21 said:**
> [SIZE=2][FONT=arial]
Some of the default apps still don't support the Unity Global Menu yet they are all Open Source. Why not rewrite the source to support it

That's what we've been doing!

> What about all the things in the USC already. I was also talking about making sure we get the latest packages into the repositories once they are released instead of having to wait on them

We do have a backports process, the thing is it doesn't scale, there's not enough people to do this, which is why we want to simplify packaging, it needs to be automated. 

> 
I was talking about how the two devices are just the same operating system slapped onto both. Like how Microsoft did the Surface Pro and normal desktops and laptops.

Yeah but this isn't what we're doing. 

> Keep similarities between both of them if it benefits the user experience on both but don't make the same thing just slapped onto the devices differently.

Ubuntu Touch isn't the same interface on all three form factors, it's the same OS, but not the same UI. They share similar elements, but when you're phone is in phone mode it's a phone, when it's docked to a screen with a keyboard it would act like Unity does today.

---

### Post by Cheesehead on 2013-06-03
> **jlholmes21 said:**
> I can understand we are moving to a world in which desktops and mobiles are, in a way, the same market but we shouldn't be moving to a world where we think they are the same.

All the development discussion I have seen agrees with you on this already. I haven't seen anybody pushing its-all-the-same. Instead, the work is about "how do we make application Foo's experience great on all platforms," recognizing fully that the UI is different on each.


> **jlholmes21 said:**
> You have got everything at the moment designed to use XOrg but if we are going to be replacing that, having both Mir and Wayland will cause problems. Some people will use Wayland and others will pick up Mir... then what... We have a split in  the community of the replacement and that will slow up redevelopment of applications to use the new system and then the Linux desktop as a whole suffers from the decision to take something from the mobile space and stick it into the desktop space.

Mir discussion at the most recent Ubuntu Developer Summit included specifically how to prevent precisely such a split.
This seems more relevant to any group of similar or competing projects, and not really relevant to grafting something from environment A into environment B.


> **jlholmes21 said:**
> Now the Ubuntu Software Center. Like many great ideas it is appallingly executed.

Roll up your sleeves and contribute. Your improvements and polish are welcome. Everyone will benefit.


> **jlholmes21 said:**
> If a new stable version of a package comes out why isn't it put into the USC for the current stable and LTS release instead of waiting for the next release to finally release it. This is where distributions like Arch have an advantage. I'm not asking you to go entirely rolling release on the situation...

Well, yes. Yes you are. You're asking for a (caveated) rolling release.
And the developers created one for you. The development release is rolling.
It's untested. It will have bugs. It will introduce bugs...but a real rolling release is untested and introduces bugs.

The specific answer to your question is that users of the package have not asked for a backport. If you ask for a new release to be backported, it will be added. Just ask for it. Backporters won't waste their time on packages nobody has asked for. Would you? (Backporters Team welcomes new volunteers, by the way!)


> **jlholmes21 said:**
> If you can provide this perfect (or as close to it as humanly possible) system that you want to, more OEMs will pick it up and then take more time to ship better Ubuntu systems. If you can tick off the things I've mentioned above you are already doing large parts of the job.

Seems very much in line with Ubuntu's goals and strategy....Your most important bit seems to be that Ubuntu's goals and strategy are on course?


> **jlholmes21 said:**
> I could go on for hours ranting about one little thing within the entire world of Ubuntu or even Linux as a whole but again if we work one step at a time we will continue to move forward.

I recommend viewing some of the mir and touch developer meetings on the ubuntuonair youtube channel - you'll get a much clearer idea of the current issues and potential benefits.

---

### Post by jlholmes21 on 2013-06-03
I fell that either the way I have written it or you have looked at my post has cause you to miss what I was trying to get at. Other distributions have shown how to do some of the things I outlined, like the packages, a lot of them have community driven packaging by either developers or just enthusiasts who help to maintain that distribution. It feels that this could be missing here as a lot of software in the USC comes with a message in the description section saying "updates maybe be provided by the community". This is something that needs to be picked up on. You could automate it, doesn't seem like a bad idea if you can keep a system up all the time building packages and updating the repositories.

The other thing you didn't seem to notice or respond about was the XOrg/Wayland/Mir situation. X will eventually be replaced, originally it was just Wayland but if Mir does actually (and I think it can) become a viable replacement for Mir how do you plan to distribute it? Do you plan to replace X on the desktop the moment Mir becomes stable and usable or will you hold out until Mir has its proprietary drivers and developers port their software to it or you provide an X.Mir system that has been the topic of discussion a few times albeit more with Wayland than Mir. This change is going to be a big change and it feels like you are going to give us Mir by default the moment it is ready rather because you are going to be using it on the tablet, phone and the desktop.

---

### Post by MadmanRB on 2013-06-03
> **jlholmes21 said:**
> [SIZE=2][FONT=arial]

Some of the default apps still don't support the Unity Global Menu yet they are all Open Source. Why not rewrite the source to support it[/FONT][/SIZE]
Already happening, sure some of it is not entirely native but its getting better

---

### Post by Cheesehead on 2013-06-03
> **jlholmes21 said:**
> X will eventually be replaced, originally it was just Wayland but if Mir does actually (and I think it can) become a viable replacement for Mir how do you plan to distribute it? Do you plan to replace X on the desktop the moment Mir becomes stable and usable or will you hold out until Mir has its proprietary drivers and developers port their software to it or you provide an X.Mir system that has been the topic of discussion a few times albeit more with Wayland than Mir. This change is going to be a big change and it feels like you are going to give us Mir by default the moment it is ready rather because you are going to be using it on the tablet, phone and the desktop.

You are essentially accusing developers of hubris - of their assuming that mir is perfect, mir should replace X at first opportunity, X and Wayland should be removed from the repos, and breakage should be loftily ignored. 

This was discussed a lot at the Ubuntu Developer Summit (UDS), on the Ubuntu-devel mailing list, and a couple other places I have seen. Nobody is talking about making X or Wayland unavailable. Everybody is talking about extensive testing, measured phase-ins including trial versions and opt-ins for early-adopters, using the whoopsie-daisy and errors.ubuntu.com infrastructure to ensure a good experience for most users.

Again, the discussions and planning are open and available online. Please look at them!

---

### Post by castrojo on 2013-06-03
> **jlholmes21 said:**
> Other distributions have shown how to do some of the things I outlined, like the packages, a lot of them have community driven packaging by either developers or just enthusiasts who help to maintain that distribution. 

We have community driven packaging and enthusiasts that do this very thing! It's a scale issue, we don't have enough people to maintain a backport/package for every single piece of software in the archive.

---

### Post by bmullan on 2013-06-04
> **jlholmes21 said:**
> [SIZE=2][FONT=arial]

Some of the default apps still don't support the Unity Global Menu yet they are all Open Source. Why not rewrite the source to support it

What about all the things in the USC already. I was also talking about making sure we get the latest packages into the repositories once they are released instead of having to wait on them

I was talking about how the two devices are just the same operating system slapped onto both. Like how Microsoft did the Surface Pro and normal desktops and laptops. Exactly the same OS on two different devices that need two different type of systems on them. Ubuntu Touch is good and has benefited the desktop but making them too integrated is also bad as the line between desktop OS and mobile (phone/tablet) OS just disappears and that is why I am partly against the way things are being done at the moment. Keep similarities between both of them if it benefits the user experience on both but don't make the same thing just slapped onto the devices differently.
[/FONT][/SIZE]

>>"Why not rewrite the source"" ... 
>> it ISopen source... you can start with what ever application you have time to address.   Let us all know which ones you've fixed.   Seriously, it is open source but time is not freely available to many developers to just work on any previous/past work just "whenever"... file a bug against their code to make sure the problem gets tracked and hopefully eventually corrected by someone associated with the app.


>> "what about getting latest packages into the repositories"
>> packages have to be tested by "someone".    There are over 40,000 already in the Ubuntu Repositories... I am sure any help you can give in this area would be welcome also.

>> "Exactly the same OS on two different devices"... 
>> it may appear that way on the surface (the UI) but underneath one is ARM cpu based the other Intel/AMD.   Graphics support is different.   All applications have to be rebuilt for ARM and then tested.   Front/Back Camera's need to  be supported, tilt/rotate need to be supported.    In other words there are alot of differences.   I think its actually a good thing that the User experience on the tablet/mobile device appears the same as the desktop except use of fingers instead of mouse.   That similarity means lower user learning time.

---

