---
title: "All frustrated and ..."
date: 2007-03-03
forum: The Cafe
---

### Post by keith11 on 2007-03-03
Well, tonight I am very frustrated. I downloaded five good applications from gnome-files and this was one of the first attempts to download something which is NOT in the Ubuntu Edgy repositories, and well, I couldn't install all five applications. VERY disappointing. Each of those applications, namely gnomad2, mail-notification, note-case, wyneken, and one more which I don't remember had some dependencies, so I tried to apt-get install those dependencies. I didn't find almost all of the files I needed for those applications, mostly libraries, in the repostories, I tried to install the libraries from the internet and well, they were dependent on some more. Entangled in this vicious circle, I ended up failing even after installing all dependencies and got nothing but errors. Kind of very disappointing. I understand Ubuntu is free and all, but well...nevermind. I like Ubuntu, but I like it when it performs, after all wasn't that the whole idea behind switching from Windows XP (I don't like Windows bashing and I don't think it is a horrible OS, but Ubuntu seemed better)? So basically, the conclusion tonight for me is, if you are using Linux (I won't say Ubuntu in particular because the errors I got can well be experienced on other distros too), you should forget about installing applications that are good but which are not in the repositories.

---

### Post by PrinceArithon on 2007-03-03
Those errors could have been caused by anything really.  Mostly the errors like that are caused from bad files, meaning when you downloaded the libraries they may have lost something during the download...it can be a mess yes.  I do understand your frustration.  I went through that same type of hell when I used Fedora and SuSe.

---

### Post by Gerard Barberi on 2007-03-03
[Notecase]("http://packages.ubuntulinux.org/edgy/x11/notecase"), [gnomad2]("http://packages.ubuntulinux.org/edgy/x11/gnomad2"), and [Mail-notification]("http://packages.ubuntulinux.org/edgy/gnome/mail-notification") are in the Universe repositories.  Make sure they are [enabled.]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

I'm sorry, but I couldn't find  wyneken.

---

### Post by ramjet_1953 on 2007-03-03
I have had great success just doing a seach for the app that I want as a DEB file by typing into Google <application> deb.

It is amazing how many people are making deb packages today and are posting them.

What I am basically saying Keith, is perhaps a little bit of lateral thinking, before getting frustrated, if at first you don't succeed.

Regards,
Roger :cool:

---

### Post by Tomosaur on 2007-03-03
Ahh good old dependency hell :P

Yes, it's annoying, but such is life. Stick to the repositories (as has been stated, some of those programs are, in fact, there - you just need to enable the correct repositories) for most things. For those programs where you need to download from the internet - do everything in an organised manner. Don't try compilation and such until you KNOW the dependencies are all satisfied - because it leads to more frustration and a horrible mess in your home folder.

---

### Post by karl1 on 2007-03-06
I'm the developer of Wyneken. I don't personally use Ubuntu, but know several people who have gotten Wyneken successfully installed on Ubuntu. This particular thread isn't necessarily the place to work through getting Wyneken working, so if you would, please file a bug at:

[http://sourceforge.net/tracker/?group_id=108028&atid=649328](http://sourceforge.net/tracker/?group_id=108028&atid=649328)

Once you post there, I will be notified and will personally help you out in getting Wyneken installed. 

Before you do that though, please have a look at:

[http://www.99b.org/wyneken/?q=node/2](http://www.99b.org/wyneken/?q=node/2)

which contains the Ubuntu installation instructions for Wyneken. Let me know if you still have problems as I would like to certainly improve the user experience of Linux as a whole and keep people from having experiences like you've had.

Best Regards,
Karl Abbott
Wyneken Developer

---

### Post by H.E. Pennypacker on 2007-03-06
Dependency hell!

It's caused by the stubborn nature of many Linux developers who do not want to hard link those dependencies.  Hard linking is not something you'd do ideally, but at least the users don't have to  track dependencies all over the Internet.  For as long as developers stay away from hard linking, this is how it will be.

It is a shame Linux does not see this an obstacle.  I don't even see this being addressed anway.  Tons of people are tired of dependency hell, but nothing is ever done about it, because change is a difficult thing.

---

### Post by keith11 on 2007-03-08
> **karl1 said:**
> I'm the developer of Wyneken. I don't personally use Ubuntu, but know several people who have gotten Wyneken successfully installed on Ubuntu. This particular thread isn't necessarily the place to work through getting Wyneken working, so if you would, please file a bug at:

[http://sourceforge.net/tracker/?group_id=108028&atid=649328](http://sourceforge.net/tracker/?group_id=108028&atid=649328)

Once you post there, I will be notified and will personally help you out in getting Wyneken installed. 

Before you do that though, please have a look at:

[http://www.99b.org/wyneken/?q=node/2](http://www.99b.org/wyneken/?q=node/2)

which contains the Ubuntu installation instructions for Wyneken. Let me know if you still have problems as I would like to certainly improve the user experience of Linux as a whole and keep people from having experiences like you've had.

Best Regards,
Karl Abbott
Wyneken Developer

I appreciate your response here and no, I wasn't trying to get help in this thread.:) I was just getting relieved of the frustration I had and knew many people would have gone through this at least once. I have been able to install wyneken finally.

Please don't get me wrong, I do like Ubuntu, but I think comparing it with a system like WIndows Vista is going a little too far given the kind of spectrum of bugs and problems end users face while using linux in general. Is there anyone who has all his hardware working with any distro of linux, the hardware being an mp3 player, a usb tablet, video cards, etc? Forget about hardware, how many people have advancements like beryl and compiz working fully in sync with their systems with very less memory footprint. I always thought linux was the epitome of the implementation of efficient coding, but call it either the stubbornness of the developers or the lack of realization that to truly compete with a system like vista you need much more that what is there right now, that I just don't see it happening. Linux was developed even before Windows was and then I would assume linux should have been in the place of windows, not the other way around. Isn't it? If anything has to be built to compete a desktop system, well, build one which exactly does it, without any complications. Not everyone has time to LEARN the intricacies of the operating system and probably they don't even require to do so and an operating system which expects its users to spend months configuring every little thing and even then not ending with success, well, how fair is it to market it as a desktop OS?! I love linux, but I am not a blind follower of it. If there are shortcomings, they have to be fixed, be it windows or linux.

---

### Post by watson540 on 2007-03-08
hey guess what. in the linux world we call people like you TROLLS. problem exists between keyboard and chair

---

### Post by keith11 on 2007-03-08
> **karl1 said:**
> I'm the developer of Wyneken. I don't personally use Ubuntu, but know several people who have gotten Wyneken successfully installed on Ubuntu. This particular thread isn't necessarily the place to work through getting Wyneken working, so if you would, please file a bug at:

[http://sourceforge.net/tracker/?group_id=108028&atid=649328](http://sourceforge.net/tracker/?group_id=108028&atid=649328)

Once you post there, I will be notified and will personally help you out in getting Wyneken installed. 

Before you do that though, please have a look at:

[http://www.99b.org/wyneken/?q=node/2](http://www.99b.org/wyneken/?q=node/2)

which contains the Ubuntu installation instructions for Wyneken. Let me know if you still have problems as I would like to certainly improve the user experience of Linux as a whole and keep people from having experiences like you've had.

Best Regards,
Karl Abbott
Wyneken Developer

I appreciate your response here and no, I wasn't trying to get help in this thread.:) I was just getting relieved of the frustration I had and knew many people would have gone through this at least once. I have been able to install wyneken finally.

Please don't get me wrong, I do like Ubuntu, but I think comparing it with a system like WIndows Vista is going a little too far given the kind of spectrum of bugs and problems end users face while using linux in general. Is there anyone who has all his hardware working with any distro of linux, the hardware being an mp3 player, a usb tablet, video cards, etc? Forget about hardware, how many people have advancements like beryl and compiz working fully in sync with their systems with very less memory footprint. I always thought linux was the epitome of the implementation of efficient coding, but call it either the stubbornness of the developers or the lack of realization that to truly compete with a system like vista you need much more that what is there right now, that I just don't see it happening. Linux was developed even before Windows was and then I would assume linux should have been in the place of windows, not the other way around. Isn't it? If anything has to be built to compete a desktop system, well, build one which exactly does it, without any complications. Not everyone has time to LEARN the intricacies of the operating system and probably they don't even require to do so and an operating system which expects its users to spend months configuring every little thing and even then not ending with success, well, how fair is it to market it as a desktop OS?! I love linux, but I am not a blind follower of it. If there are shortcomings, they have to be fixed, be it windows or linux.

---

### Post by keith11 on 2007-03-08
> **watson540 said:**
> hey guess what. in the linux world we call people like you TROLLS. problem exists between keyboard and chair

If you had read my other posts here, you wouldn't use the word "Trolls", but anyways, your comment was just a redundant one and served no purpose of  "discussion".

---

### Post by watson540 on 2007-03-08
im sorry i didnt take the time to read your other posts, but i just call it like i see it. you trolled, and then you got your answer, you just didnt have your universe and multiverse enabled. no need to bash ubuntu though because of it

---

