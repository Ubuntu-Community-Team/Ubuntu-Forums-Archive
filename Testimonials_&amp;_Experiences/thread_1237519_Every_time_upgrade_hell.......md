---
title: "Every time upgrade hell......"
date: 2009-08-11
forum: Testimonials &amp; Experiences
---

### Post by donpedrodos on 2009-08-11
Today i thought nothing can go wrong to update from 8.10 to 9.04.
I waited a long time, to see that most isues are corrected...but i was SO wrong.

I upgraded to 9.04 without basic OS no problems.

But than hell broke loose....aMSN...doesn't function anymore....and the the hell with amarok2...the newly amarok ...doesn't want to play any MP3...and YES i checked the Inet for solutions but all of them don't make a difference.

This makes a big underline that Linux/Ubuntu is still not ready for a basic click and go user. This kind of things pushes people away from something that everyone calls out to be a good and stable OS, that can replace Windows in an instance.....forget it!

I think it is time that developers look also more in some basic applications everyone uses on the OS.
Let me say..the basic OS is good, but some application that everyone uses, and as example Amarok, get broken after every update.
My question is ... WHY?
Is there not a developer that will notice this?
How wel is testing done before you say the word to upgrade to a next version of the OS.

Amarok is already a longtime favorite of many Ubuntu users, but if the onderlying OS afer an update breaks it up every update, this is not the way.

Again i need hours of tweaking and searching the forums to find a solution...WHY?

I know not al software that is "in the free" can be tested by the developers, but some main applications could be tested for its functioning on the update OS.

Going to downgrade Amarok again, wich going to be also a pain in the *** again...but we will see.

I won't go back to Windows, but other people won't make he step to try Ubuntu if these problems with upgrades keep popping up...sorry.

Going back to my strugle to get things working like before ..... hope to find solutions that shouldn't be needed to find.

---

### Post by drs305 on 2009-08-11
donpedrodos,

I can't really tell if you are looking for help or just expressing your opinion. 

If you are looking for help, was this a clean install or online upgrade? Upgrade to me usually means updating the current release rather than a clean install, but the term is used loosely.

If the former, did you re-enable the codecs? I find it helpful to save a list of installed packages before doing a clean install so I can restore things more easily. This can be achieved via Synaptic or switches with dpkg.

---

### Post by donpedrodos on 2009-08-11
I updated a current release 8.10 to 9.04 today after a long time of waiting to do it or pass.
I already made several of this kind of updates, but it looks that everytime i update it needs a lot of extra energy to get things going again.

I also know your trick to make a backup via the Synaptic, but do i realy need to do this every new release?
Is that the trick to avoid this kind of hustle?
I there a kind of 'failsafe updateway' to keep everything up and running?

This is for 90% of users who are used to Windows, the "click and go OS", not workable. The people don't want an application to stop functioning after an update.
 
I like that people try an other OS and advice them to give Ubuntu a shot.
Most of them are not a computernerd as me, so for them is it the 'killing nail' to go directly back to Windows or MAC.

If we want people to stick with the 'better OS' like Ubuntu still is for me, this is something that must to be thougth of in the future.

Looks like the 'backwards compatibility' is not what it supose to be.
There is still a lot of work to be done to keep the non computernerds stick to an OS like this.

And on the question if i need help, maybe ... but i also was making a statment about how an update fails to workout fine.

Thanks for the responce.

BTW, I ran Windows XP for many years and NEVER had to do a clean install, but Ubuntu maybe going to be the one that NEEDS a fresh install ALWAYS?

---

### Post by donpedrodos on 2009-08-15
For the people who want Amarok 1.4 back and up and playing you MP3 like before, [go here for instructions how to]("http://www.ubuntugeek.com/howto-install-amarok-1-4-in-ubuntu-jaunty.html").

After doing so overhere, Amarok is back as if it was never away from my Ubuntu install.

But people of the new and 'bad' Amarok 2, pls try to find out the reason why the new Amarok will not play out of the box on many Ubuntu Jaunty installs.

One solved....some to go...................

---

### Post by presence1960 on 2009-08-15
I am not a fan of the upgrade process and if you do a search of the threads on here you will see a large amount of threads about upgrades going wrong. I am sure some of it has to do with not removing packages that were not installed thru synaptic or apt-get. But the fact remains there are a lot of problems with the upgrade process for whatever reason(s). This is not to say that every upgrade will have problems. I prefer a clean install and you can save your installed packages to a file. then after the install put that file in your home directory and run a command and all the packages will be reinstalled for you. do this:

To replicate your packages selection on another machine (or restore it if re-installing), you can run this:

```
dpkg --get-selections > ~/my-packages
```


This will save a file called my-packages in your home directory. Make a backup of it, install the fresh release, then restore the file "my-packages" to new home partition and run this code in the terminal:

```
sudo dpkg --set-selections < my-packages && sudo apt-get dselect-upgrade
```


It will download and install all the programs for you, except those that you installed manually, if they are not in the new repository.

---

### Post by donpedrodos on 2009-08-18
Another one working again...aMSN!

Before i was getting the message about the TKCXImage bla bla bla, yes that famouse message that aMSN spits out at many users.

The solution was to not use "./configure" but "sudo ./configure"

The past days i was compiling, as everyone, with "./configure" and al the time it came back with the famouse error.

This is also mentioned in the INSTALL file how to compile aMSN for your system.
But then i put on my nasty shoes and tried a new not normal way for compiling with "sudo ./configure".
And that did the trick.
It is not clear to me why in this instance you MUST use the "sudo" right, because nothing is yet installed, but it works in this case.

Hope i helped some people with this info.

---

### Post by dmizer on 2009-08-18
First, any time you've compiled something you'll have to compile it again after every update. That's why you use repositories instead of compiling your own software.

Second, upgrading from 8.10 to 9.04 is like upgrading from Windows XP to Windows Vista. Would you expect to have trouble in Windows when doing that kind of upgrade?

---

### Post by slakkie on 2009-08-18
> **dmizer said:**
> First, any time you've compiled something you'll have to compile it again after every update. That's why you use repositories instead of compiling your own software.

Second, upgrading from 8.10 to 9.04 is like upgrading from Windows XP to Windows Vista. Would you expect to have trouble in Windows when doing that kind of upgrade?

I don't agree with the second part. Upgrading from LTS to LTS could be considered upgrading from XP to Vista, but 8.10 to 9.04 is just an intermittent upgrade. A Service Pack if you will.

Regarding compiling, if you need to use sudo for a simple configure script then you are doing something wrong. Configure doesn't need root privs, only the make install needs those rights.


Correct procedure would be:

```

./configure --options
make
make test
sudo make install # or sudo checkinstall make install

```

---

### Post by Tamlynmac on 2009-08-18
> dmizer
Second, upgrading from 8.10 to 9.04 is like upgrading from Windows XP to Windows Vista. Would you expect to have trouble in Windows when doing that kind of upgrade?

Not to mention, I don't recall anything in the Ubuntu agreement that mandates upgrading. It's a choice not a requirement. No one is forced to upgrade and I've noted recently, that quite a few of the forum members that are still running 8.04.

I maintain a separate used HDD just for the purpose of upgrading. Of course even prior to that I use the live cd to assure basic functionality. With all the available options to assure system upgrade functionality, seems illogical just to assume.

Why not take a few simple precautions prior to upgrading. Perhaps, it may reduce the need to complain. Then again maybe not.

I do find it odd, that when ranting many can't help but compare Ubuntu to Windows. I wonder if that's an indicator that Ubuntu is becoming popular enough to spawn those types of remarks. Amazing, a free OS being compared to Windows. I'm impressed.

Can't help but consider the future of Ubuntu. When it's already being compared to the OS with the largest market share. Canonical should be extremely proud, every time a comment is expressed comparing Ubuntu to Windows. Such a comment implies that the need to compare - exists. ;-)

Just my $0.02

---

### Post by Methuselah on 2009-08-19
I believe the difference between adjacent Ubuntu releases is far greater than that between windows service paks.
This is what determines the comparative effect on one's system not some simple 1:1 correspondence based on release timing. 
I've never had upgrade problems but I'm going start following the procedure of making a separate home partition and doing a fresh install.

---

### Post by donpedrodos on 2009-08-19
Just to be clear, Ubuntu never going to be 'a windows' OS and more important, I don't want that.

Like i mentioned before, i did many upgrades from version to version, without any problems.

And people are right to say "you don't HAVE to upgrade".
But the problem is, support will finaly finish for a release, so nothing else to do than upgrade.
And my idear is to do it in an early stage, to avoid even more 'nasty' things.

And Ubuntu made it very easy to upgrade from one version to an other next version, it is a click of a button and everything goes by itself.
Again, I don't compile many applications anyway, because i also know that they will be broken.
But applications that more ore less everyone uses that get broken, is a little odd to me.

Application in the ADD/REMOVE APPLICATION that have a popularity 4/5 star, shouldn't get broken, they are used worldwide by many users.

Forget me, because i'm not afraid of computers and software, but consider people that are not so driven by computer stuff.
The problems they encounter are to much for them, even if they installed the offered software via the ADD/REMOVE APPLICATIONS.

And @slakkie, i still don't know why it wouldn't compile normaly with the './configure'. As i explained, compiling with './configure' was giving me the well known TKCImage error, but after using 'sudo ./configure' it compiled and runs like a baby.

It took some time, but 99% of all problems are solved...but it took some time to find solutions for some of them.

The next thing to try is a fresh install, to see if problems that i encountered are cleared on the spot that way.
BTW, a seperate HOME partition is already in place here for some time.

---

### Post by HappyFeet on 2009-08-19
> **donpedrodos said:**
> 
The next thing to try is a fresh install

Great idea. ;)

---

### Post by craig10x on 2009-08-19
What  should fix your Amarok 2.0  (if you haven't already downgraded) is this terminal command:
   
sudo apt-get install libxine1-ffmpeg

After i installed Ubuntu 9.04 on my new Toshiba Laptop (clean install and i had it wipe out windows)....i added Amarok, which was 2.0 of course, and couldn't hear any audio for the mp3s and streaming radio...

I looked around on yahoo search and found an article about the problem....simply adding that plug in through the terminal, solved the problem instantly :P

---

### Post by donpedrodos on 2009-08-21
I already downgraded with succes back to Amarok 1.4, see some posts back.
The GUI of the new Amarok 2 is completly reworked and was also not my thing.
I think i going to stick for a long time with Amarok 1.4, because i can control it better than the new and 'improved' Amarok 2.

And about that lib, it was already installed on my system, but it didn't do the trick to make MP3 sound.

---

### Post by Matt05 on 2009-08-22
> **donpedrodos said:**
> 
This makes a big underline that Linux/Ubuntu is still not ready for a basic click and go user. This kind of things pushes people away from something that everyone calls out to be a good and stable OS, that can replace Windows in an instance.....forget it!


I agree w.r.t. Ubuntu but I disagree w.r.t. Linux as a whole.  The problems you are experiencing are due to Canonicals release policy of 6 months.  This generates a large number insufficiently tested versions which nobody can really support.

Before Ubuntu appeared Linux used to be slightly difficult to install but then it would just work.  Ubuntu changed that in that the install experience is really easy and the look is polished.  I still remember how happy I was to see 6.10 install on my notebook and wifi and sleep/suspend worked out of the box.

But then 7.04, 7.10 (with a half-baked pulseaudio system) came out and 8.04 and 8.10 (with kernel issues) and having to support 4 half-baked systems in parallel overloaded the volunteers and Canonical.

What can you do?  If you want to stay with Ubuntu you can go LTS, wait for a year and pray that it works.  You can switch to Debian which is actually tested/stable/working but hard to install for click and go users (i.e., if you need closed source firmware you are on your own).  The last time I looked at SuSE is a while ago but install was easy, look polished, and at that time more stable than Ubuntu is today.

Canonical: Please stop re-labeling Debian/testing as production systems.  If you insist on the insane 6 months release cycle, label the releases "testing", "developer" or similar.  This way new users will understand that they are expected to be able to fix things on their own.  Otherwise you give a bad name not only to the Ubuntu brand but to Linux in general.  That would be very sad.

---

### Post by mdsmedia on 2009-08-22
> **Matt05 said:**
> I agree w.r.t. Ubuntu but I disagree w.r.t. Linux as a whole.  The problems you are experiencing are due to Canonicals release policy of 6 months.  This generates a large number insufficiently tested versions which nobody can really support.

Before Ubuntu appeared Linux used to be slightly difficult to install but then it would just work.  Ubuntu changed that in that the install experience is really easy and the look is polished.  I still remember how happy I was to see 6.10 install on my notebook and wifi and sleep/suspend worked out of the box.

But then 7.04, 7.10 (with a half-baked pulseaudio system) came out and 8.04 and 8.10 (with kernel issues) and having to support 4 half-baked systems in parallel overloaded the volunteers and Canonical.

What can you do?  If you want to stay with Ubuntu you can go LTS, wait for a year and pray that it works.  You can switch to Debian which is actually tested/stable/working but hard to install for click and go users (i.e., if you need closed source firmware you are on your own).  The last time I looked at SuSE is a while ago but install was easy, look polished, and at that time more stable than Ubuntu is today.

Canonical: Please stop re-labeling Debian/testing as production systems.  If you insist on the insane 6 months release cycle, label the releases "testing", "developer" or similar.  This way new users will understand that they are expected to be able to fix things on their own.  Otherwise you give a bad name not only to the Ubuntu brand but to Linux in general.  That would be very sad.
I'm really not sure what you're talking about. I installed 9.04 Alpha on my desktop (now running Arch Linux), upgraded it through Betas to the release version and it was fine. I only installed it on my HP notebook because I was comfortable with it on my desktop (play system). I've since bought a new Toshiba notebook and 9.04 works fine on it too.

I don't claim that 9.04 is perfect on every system, but it's still better on all 3 of mine than any version of Windows.

If you want perfection, as has been stated in other posts, you won't get it with any OS, but if you have a system designed for Windows, Windows will probably have more chance of working well on that system. If you then try a Linux distro on that system, you might have some luck with it. I've been lucky with Ubuntu on all of mine. If Ubuntu doesn't work too well, try another distro, but don't complain about Ubuntu not working on your system, at least not to Ubuntu users. Complain to the hardware manufacturers.

---

### Post by presence1960 on 2009-08-22
> **mdsmedia said:**
> 

If you want perfection, as has been stated in other posts, you won't get it with any OS, but if you have a system designed for Windows, Windows will probably have more chance of working well on that system. If you then try a Linux distro on that system, you might have some luck with it. I've been lucky with Ubuntu on all of mine. If Ubuntu doesn't work too well, try another distro, but don't complain about Ubuntu not working on your system, at least not to Ubuntu users. Complain to the hardware manufacturers.

+1

A lot of people really don't understand the role of hardware in their system and the relationship between hardware & software. I for the most part avoid these discussions because I feel like I am doing this ](*,)

But yes you are correct. Some hardware does not work in any linux OS because the hardware manufacturers give no support and/or refuse to release the code for their drivers. Definitely not Ubuntu's or any other Linux distros fault. I consider it miraculous that they have found ways to make most hardware work with the Linux kernel. So yes complain to the manufacturer of the hardware that does not work not to Linux!

---

### Post by HappyFeet on 2009-08-22
> **Matt05 said:**
> 
What can you do?  If you want to stay with Ubuntu you can go LTS, wait for a year and pray that it works.

You are speaking as if your experience is universal. I can assure you it is not. After 40+ installs of ubuntu, (on many types of hardware) I have not experienced any problems worth noting. 

Do people have problems? Sure. But if ubuntu was as bad as you seem to believe, no one would use it.

---

