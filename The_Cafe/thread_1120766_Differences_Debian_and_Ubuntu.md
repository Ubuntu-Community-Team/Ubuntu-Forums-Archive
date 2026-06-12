---
title: "Differences Debian and Ubuntu?"
date: 2009-04-09
forum: The Cafe
---

### Post by Vaporize on 2009-04-09
Heey i've just installed Debian next to my Ubuntu installation cause I know that's what Ubuntu is based on and well, Ubuntu has a pretty installer and a different theme but in anything else they look kinda similar.
 What are the actual differences between Debian and Ubuntu?

---

### Post by LowSky on 2009-04-09
Different Repos (although the share alot of the same software)
Ubuntu customizes Gnome, so the menus will be different and so will some pop up notifications
Ubuntu uses Firefox, Debian uses Swiftfox (modified Firefox)
Debian will run on more type of hardware not just 386/AMD64/PPC like Ubuntu

that what I can think of right now, try this
[http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Debian](http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Debian)

---

### Post by Vaporize on 2009-04-09
Hmm there seems to be not too much difference which is kinda :\. Ubuntu seems to be more noob friendly though and more eyecandy though. And Debian doesn't have firefox in it's repositorys which will be a downside to most people. Debian has iceweasel btw.

---

### Post by lykwydchykyn on 2009-04-09
> **LowSky said:**
> 
Ubuntu uses Firefox, Debian uses Swiftfox (modified Firefox)

Debian uses iceweasel, not swiftfox.  I believe you can get the firefox branding if you add the non-free repositories.

Biggest differences boil down to the installer, the out-of-the-box configuration, and the development cycle.  Debian makes a stable release every couple of years with no set schedule (it's done when it's done) and every release is supported with security updates for three years.  This means that Debian stable tends to be behind the curve for up-to-date packages, but much more mature, stable, and conservative in its selection.  I personally prefer it for situations where I want to set up something simple and not have to touch it for a few years, like a server or a kiosk.

---

### Post by anaconda on 2009-04-09
Debian has a root user by default... Which I think is a GOOD thing.

And debian has different versions. You can choose stable, which will be really really stable, or you can choose a rolling release debian (I think it is called debian testing) or the debian unstable, which will have all the new programs.

Ubuntu has the BEST forums. so if you need help you will almost always find a solution from these forums.

---

### Post by jamvaru on 2009-04-09
My sound card didn't work with debian 5.0.0, yet it did with Ubuntu 8.10.  I'll have to check out the newer debian releases

My gripe:

I tried to run debian disks on Ubunty and they said "this must not be a debian disk"  blech...

how lame is that?

meaning... downloaded .iso's of the 5.0 release and ubuntu couldn't add it to it's repository list.  tried old 4.01 dvd's... same problem. It couldn't recognize anything but the ubuntu installer disk as a valid "debian" disk.  (disc)

anyway, i'm happy that ubuntu is reaching out to the world with their free mailers but really, this is rediculous, and nobody can tell me where the cd/dvd's are for the ubuntu release... (no broadband here)

what are you supposed to do if you have no broadband?  seems like if they want de, er, ubuntu to be competitive with windows they need to be more up front about getting things done right...

at least debian software works with debian installations, and they have lots and lots of it available on dvd/cd's

seems like ubuntu is more geeky than debian, meaning stuck on being techie instead of user friendly, though they say otherwise...  ubuntu is the most, er, less geeky of the distributions?

---

### Post by snowpine on 2009-04-09
> **jamvaru said:**
> 
My gripe: 
I tried to run debian disks on Ubunty and they said "this must not be a debian disk"  blech...

how lame is that?

meaning... downloaded .iso's of the 5.0 release and ubuntu couldn't add it to it's repository list.  tried old 4.01 dvd's... same problem. It couldn't recognize anything but the ubuntu installer disk as a valid "debian" disk.  (disc)


If you want to install Debian, you should burn the .iso to a CD, then reboot the computer to the CD and run the Debian installer. You can't just add Debian repositories to your existing Ubuntu install.

---

### Post by LowSky on 2009-04-09
> **jamvaru said:**
> 
anyway, i'm happy that ubuntu is reaching out to the world with their free mailers but really, this is rediculous, and nobody can tell me where the cd/dvd's are for the ubuntu release... (no broadband here)

what are you supposed to do if you have no broadband?  seems like if they want de, er, ubuntu to be competitive with windows they need to be more up front about getting things done right...

seems like ubuntu is more geeky than debian, meaning stuck on being techie instead of user friendly, though they say otherwise...  ubuntu is the most, er, less geeky of the distributions?

Cant find Ubuntu disks? 
[https://shipit.ubuntu.com/](https://shipit.ubuntu.com/)

Also Microsoft/Apple do not give you that many 'free' applications. I think people confuse how free works. Your not paying for any of it (unless you donate or develop it), so please understand that all freedom does come with responsibilities, and with Ubuntu that means if you want free updates you need a decent internet connection!

All Linux is geeky, Ubuntu is not as bad as you mentioned.

---

### Post by Cretin_Yes on 2009-04-09
> **anaconda said:**
> Debian has a root user by default... Which I think is a GOOD thing.

Ubuntu also has a root user - it's just not usable until you set a password with passwd

---

### Post by tjwoosta on 2009-04-09
> Heey i've just installed Debian next to my Ubuntu installation cause I know that's what Ubuntu is based on and well, Ubuntu has a pretty installer and a different theme but in anything else they look kinda similar.
What are the actual differences between Debian and Ubuntu?


like you said,
debian is what ubuntu is based on

ubuntu uses debian packages (.deb) and debian package management systems(synaptic and apt-get)

basically everything is the same except different repositories and artwork, as well as some UI differences to be more newcomer friendly

if you like ubuntu but you want a lighter weight and more minimal distro, you should definatly give debian a try


i have three old machines that wont run ubuntu anymore because not enough ram (since the end of gutsy) but i can easily install debian with basicaly the same DE and everything looks and runs just like ubuntu, except lighter and faster


if you are a distro hopper like i was, you will soon see that the differences between distro's are not quite as vast as you might imageine

any distro can be made to look and feel exactly like any other distro   (its all about which DE/WM and apps you choose)

---

### Post by NightwishFan on 2009-04-09
Ubuntu is based on Debian unstable I believe. It freezes package versions from Debian, and develops them with Ubuntu specific modifications.

I believe you can add debian repositories in Ubuntu, as well.

As for other differences, Ubuntu has it's own default software designed to make some non free components more usable.

---

### Post by Twitch6000 on 2009-04-09
> **tjwoosta said:**
> like you said,
debian is what ubuntu is based on

ubuntu uses debian packages (.deb) and debian package management systems(synaptic and apt-get)

basically everything is the same except different repositories and artwork, as well as some UI differences to be more newcomer friendly

if you like ubuntu but you want a lighter weight and more minimal distro, you should definatly give debian a try


i have three old machines that wont run ubuntu anymore because not enough ram (since the end of gutsy) but i can easily install debian with basicaly the same DE and everything looks and runs just like ubuntu, except lighter and faster


if you are a distro hopper like i was, you will soon see that the differences between distro's are not quite as vast as you might imageine

any distro can be made to look and feel exactly like any other distro   (its all about which DE/WM and apps you choose)


Okay with what you just said I have a funny question that is going to light a fire,but I am ready to ask anyways...

If what you said is true which we know it is basically everyone who hs posted has said it, then why is Ubuntu a full distro?

Yes why is Ubuntu being called a Full Distro and Not Linux Mint?

Lets look at a few things here -

Ubuntu is to Debain as Mint is to Ubuntu.

However I have noticed their is a community edition of Mint that is based on debain <.<.(thats beside the point)


However Looking at Ubuntu in recent years it has made less and less changes.

While Mint on the other hand makes changes every release.

So  again why is one called a distro and the other not?

I find both are just spin offs of well debain lol.

Anyways... here come the flames from over 1000 fanboys... going to deny this with fud fud and much more fud.

---

### Post by NightwishFan on 2009-04-09
Well, no flaming here, but Ubuntu has obligations to consider when trying to gain commercial adoption. Just think about that.

BTW: I am huge Debian fan as well.

---

### Post by Twitch6000 on 2009-04-09
> **NightwishFan said:**
> Well, no flaming here, but Ubuntu has obligations to consider when trying to gain commercial adoption. Just think about that.

BTW: I am huge Debian fan as well.

Good Point,however I read on the Mint site the makers of Mint are also hoping to go into the desktop market.That is a one reason why they put codecs in be default.

This still does make it much different from Debian if at all,because look at Debian trying to be a all around distro from all ends.. 

I mean they are now supporting freebsd lol.

---

### Post by NightwishFan on 2009-04-09
Mint will need to make sure they are legally in their rights to distribute of course. I do not agree with all these patent laws, but they are what make open source so great in comparison. :popcorn:

---

### Post by Twitch6000 on 2009-04-09
> **NightwishFan said:**
> Mint will need to make sure they are legally in their rights to distribute of course. I do not agree with all these patent laws, but they are what make open source so great in comparison. :popcorn:

Now here is where I could be wrong,but I believe the main dev of Mint is in Ireland,making them have to follow Irish laws.

So I think it might be legal for them to do what they have been doing.

Ofcourse do not quote me on this lol.

---

### Post by NightwishFan on 2009-04-09
I am not sure how that works. My guess is:

I live in the United States, I am sure if Mint is used here, it would have to follow US law. If not then it is potentially illegal to distribute.

This is all supposition, if I am wrong correct me.

---

### Post by Skripka on 2009-04-09
> **LowSky said:**
> Different Repos (although the share alot of the same software)
Ubuntu customizes Gnome, so the menus will be different and so will some pop up notifications
Ubuntu uses Firefox, Debian uses Swiftfox (modified Firefox)
Debian will run on more type of hardware not just 386/AMD64/PPC like Ubuntu

that what I can think of right now, try this
[http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Debian](http://polishlinux.org/choose/comparison/?distro1=Ubuntu&distro2=Debian)

Actually...Ubuntu will not run on i386 hardware, only 486 CPUs and above.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by swoll1980 on 2009-04-09
> **Twitch6000 said:**
> 



However Looking at Ubuntu in recent years it has made less and less changes.

While Mint on the other hand makes changes every release.

So  again why is one called a distro and the other not?



To say Ubuntu doesn't change is inaccurate. I bet you Mint 7 will boot in 20 seconds, and have a new notification system... Just a hunch. Debian is the one that doesn't change anything.

---

### Post by Twitch6000 on 2009-04-09
> **swoll1980 said:**
> To say Ubuntu doesn't change is inaccurate. I bet you Mint 7 will boot in 20 seconds, and have a new notification system... Just a hunch.

Uhmm you realize how long it took for them to finally work on speed to right?

As for the new notification system I wouldn't be surprised to see it on mint,but I also wouldn't be surprised not to see it aswell.

As for the boot time,I think since it is still going to be based on 8.10 the boot speed will not be as fast.

---

### Post by NightwishFan on 2009-04-09
Debian is so rock solid though. :popcorn:

I find Ubuntu to implement quite a few new things though. It makes my life easier and it has the most support available. Besides I like this community.

---

### Post by BXL on 2009-04-09
Ubuntu is the user friendly flavor of Debian.

---

### Post by Vaporize on 2009-04-09
So the big difference is that Ubuntu is stupid proof. But well as said before Debian is very stable also.
 I think the big difference between Ubuntu and Debian is it's promotion strategies. Ubuntu really presents itself as linux for everyone while i think debian just promotos itself as another linux distribution. 
Most people will choose their os on popularity not on functionality. 
Like windows, (Don't start the linux/windows flame now it's just to draw a contrast) have you ever seen their installation? I wouldn't call that user friendly but their fanbase is huge.
Funny how most people won't choose for the best but the most widely used.
Not that Debian is better than Ubuntu but anyhow i'm going completely of topic

---

### Post by andrewsomething on 2009-04-09
Re: Ubuntu is to Debian as Mint is to Ubuntu

The main difference here that makes the above statement not entirely true is that Ubuntu completely rebuilds the binaries from Debian. So it is not tied to a specific Debian release. AFAIK Mint is tied to specific Ubuntu releases. They then add their own repository on top of the Ubuntu repository. Although I've never heard anyone claim that Mint isn't a real distro, that might be what who ever said that to you was referring to.

Besides making installing and some other tasks more friendly, the main thing Ubuntu does is fill a gap in the Debian release cycle. For many Debian stable is very stale. The packages tend to be quite out dated compared to their upstream versions. Debian Testing and Unstable work as rolling releases. Generally Testing is 10 days behind Unstable, but there are other factors that sometimes stop packages moving to Testing (i.e. timing large scale transitions to all move into Testing at once). Changes happen constantly and there is no guarantee that you're system will not break. Though a lot of people will run Debian Testing. Using Unstable is more or less like running the development version of Ubuntu. And running Stable is more like running a LTS version of Ubuntu. The six month release cycle of Ubuntu allows there to be something in the middle. It gives us a good compromise between a having stable release and up-to-date packages.

I use and love Ubuntu, but one of the main reasons I do so is its Debian base.

---

