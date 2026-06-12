---
title: "does Kubuntu 9.04 64-bit have any shortcomings compared to 32-bit?"
date: 2009-10-08
forum: The Cafe
---

### Post by Screwdriver0815 on 2009-10-08
Hi,

the discussion about Windows 8 128-bit brought it to my mind: why the hell do I still use a 32-bit operating system, while I have an AMD Athlon X64 Dual Core processor in my machine? ](*,)

So I am now in something like a dilemma because this 32-bit system is running great but I want to use all the computing power in my machine now.

Because I do not want to wipe my good running system and get one which has issues, I would not face with 32-bit, I would like to ask, if there are any known shortcomings of Kubuntu Jaunty 64-bit, compared to 32-bit?

One I know (and it is solved) is the flash-plugin. Are there more?

- Nvidia graphics driver: are they the same quality?
- codecs and multimedia stuff: is it the same or are there any limitations in terms of quality or usability?
- software: is all the software in the repos as it is for the 32-bit version?

any answer, which helps me out of my misery (also answers to the question "should I go for 64-bit?") would be very much appreciated. :) :guitar:

Thanks in advance!

---

### Post by chris200x9 on 2009-10-08
> **Screwdriver0815 said:**
> Hi,

the discussion about Windows 8 128-bit brought it to my mind: why the hell do I still use a 32-bit operating system, while I have an AMD Athlon X64 Dual Core processor in my machine? ](*,)

So I am now in something like a dilemma because this 32-bit system is running great but I want to use all the computing power in my machine now.

Because I do not want to wipe my good running system and get one which has issues, I would not face with 32-bit, I would like to ask, if there are any known shortcomings of Kubuntu Jaunty 64-bit, compared to 32-bit?

One I know (and it is solved) is the flash-plugin. Are there more?

- Nvidia graphics driver: are they the same quality?
- codecs and multimedia stuff: is it the same or are there any limitations in terms of quality or usability?
- software: is all the software in the repos as it is for the 32-bit version?

any answer, which helps me out of my misery (also answers to the question "should I go for 64-bit?") would be very much appreciated. :) :guitar:

I've never had a problem

---

### Post by Tibuda on 2009-10-08
> **Screwdriver0815 said:**
> - Nvidia graphics driver: are they the same quality?
yes
> - codecs and multimedia stuff: is it the same or are there any limitations in terms of quality or usability? 
yes
> - software: is all the software in the repos as it is for the 32-bit version? 
Almost all FOSS software in the repos are available for 64bit, because when you have the source all you have to do is compile it in 64bit. You'll only have problems with some third party closed software, but even those can work with ia32-libs like Skype and the stable Flash player.

---

### Post by Eddie Wilson on 2009-10-08
No problems here with 64 bit Ubuntu or Kubuntu. The distros that do not put out a 64 bit version are still living in the pass and they will be left behind.

---

### Post by Screwdriver0815 on 2009-10-08
so do you all mean, I should go for it? :mrgreen:

I have tested it in a virtualbox today and one thing confused me a little bit:

I have installed the kubuntu-restricted-extras package and after that uninstalled the flashplugin, because I found a howto which uses the flash 10-alpha and this required to remove the flashplugin which is delivered with kubuntu-restricted-extras (which did not work anyway). After that, KPackageKit showed the kubuntu-restricted-extras package as not installed, but apt-get said that it is installed... I had no possibility to test the codecs-stuff and therefore don't know if it all works like in 32-bit. Thats why I am a little bit scared that I will run into trouble with the multimedia stuff...

thanks for your answers so far!

---

### Post by Eddie Wilson on 2009-10-08
I've had not problems with the Kununtu restricted extras for 64 bit. Of course I've never installed it inside a virtual machine before. That may have something to do with it.

---

### Post by keiichidono on 2009-10-08
I use Ubuntu 9.04 x86_64 and it works just fine. I'm using the alpha flash plugin from adobe and it bugs up maybe once a week but it's okay for me. Go for it.

---

### Post by afrodeity on 2009-10-08
I'm using Ubuntu 8.04 64bit and its hell. I'm probably going to have to duel boot with an Ubuntu 9.04 32bit system and reinstall software. You really only need 64bit if you want more than 4GB ram. There are no real gains as far as I can see, and 64bit results in huge problems with libraries and dependencies. I guess it's just early days.

---

### Post by NoaHall on 2009-10-08
Ehm. You are very very wrong. 64 bit is stable, usable, and there is no problem that can't be fixed in less than 5 minutes.

---

### Post by keiichidono on 2009-10-08
> **afrodeity said:**
> I'm using Ubuntu 8.04 64bit and its hell. I'm probably going to have to duel boot with an Ubuntu 9.04 32bit system and reinstall software. You really only need 64bit if you want more than 4GB ram. There are no real gains as far as I can see, and 64bit results in huge problems with libraries and dependencies. I guess it's just early days.

Why the bloody hell are you going to use an old release and complain about 64bit when you can install Jaunty? Install Jaunty 64bit and stop spreading FUD.

---

### Post by Screwdriver0815 on 2009-10-08
so guys... I did it :biggrin:

hell, this thing is fast!

no problem at all with the codecs so far, no problem with the flashplugin (I use the one which comes with kubuntu-restricted-extras).

and it is fast, like a lightning. Boottime is just half of the 32-bit and also the networktraffic is much faster.

So, good decision. 64-bit FTW!!

The next thing will be: migrating the Laptop to Karmic 64-bit when it is released. I'll never go back to 32-bit :guitar:

---

### Post by starcannon on 2009-10-08
> **afrodeity said:**
> I'm using Ubuntu 8.04 64bit and its hell. I'm probably going to have to duel boot with an Ubuntu 9.04 32bit system and reinstall software. You really only need 64bit if you want more than 4GB ram. There are no real gains as far as I can see, and 64bit results in huge problems with libraries and dependencies. I guess it's just early days.
My experience was similar; indeed my 64bit install eventually self destructed and I went back to 32bit at that point. I keep /home on a separate partition, so it was no big deal to switch back.

---

### Post by oldos2er on 2009-10-08
> **Screwdriver0815 said:**
>  no problem at all with the codecs so far, no problem with the flashplugin (I use the one which comes with kubuntu-restricted-extras).:guitar:

 You might want to consider installing 64-bit flash: [http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938](http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938)

---

### Post by Screwdriver0815 on 2009-10-08
> **oldos2er said:**
> You might want to consider installing 64-bit flash: [http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938](http://ubuntuforums.org/attachment.php?attachmentid=128822&d=1253131938)
whats the advantage of this?

BTW: I just did a test on the peacekeeper Browser-Benchmark site. In 32 bit, the Konqueror was not very good: 724 points. In 64 Bit it performs better: 988 points. Yes, I know that there are faster browsers but it shows that 64 bit is better because its faster :D

---

### Post by oldos2er on 2009-10-09
> **Screwdriver0815 said:**
> whats the advantage of this?
 :D

 Aside from the fact that's it's 64-bit, it's been very stable for me--moreso than 32-bit flash running under 64-bit Ubuntu.

---

### Post by Spike-X on 2009-10-10
> **afrodeity said:**
> I'm using Ubuntu 8.04 64bit and its hell. I'm probably going to have to duel boot with an Ubuntu 9.04 32bit system and reinstall software. You really only need 64bit if you want more than 4GB ram. There are no real gains as far as I can see, and 64bit results in huge problems with libraries and dependencies. I guess it's just early days.

Sure it is, you're using a release that's a year and a half old!

I'm running Jaunty 64-bit, and I haven't had a single problem with it so far.

---

### Post by doorknob60 on 2009-10-10
Definitely upgrade to 64 bit, it shouldn't give you any problems. One thing I'd recommend though, since 9.10 is going to be released soon, and upgrading to 64 bit requires a clean install, is to either install the 9.10 beta, or wait until it comes out officialy. No point in clean installing 9.04 so soon before 9.10 comes out, IMHO. EDIT: A little late, oh well, enjoy your 64 bit goodness :D

---

### Post by Screwdriver0815 on 2009-10-10
> **doorknob60 said:**
> Definitely upgrade to 64 bit, it shouldn't give you any problems. One thing I'd recommend though, since 9.10 is going to be released soon, and upgrading to 64 bit requires a clean install, is to either install the 9.10 beta, or wait until it comes out officialy. No point in clean installing 9.04 so soon before 9.10 comes out, IMHO. EDIT: A little late, oh well, enjoy your 64 bit goodness :D
thanks anyway :D

I was thinking the same, either installing the karmic beta or wait until the release.
But I could not wait, I needed it :D and I read some release notes that for example KPackageKit is broken in Karmic Beta... and so on. I did not want to have trouble - I just wanted to enjoy speed :D Thats why the Jackalope runs now in 64 Bit on the machine :guitar:

A bad thing about fast things is that you adopt yourself to the speed. Now, after 1 day I get used to it. Maybe in a week it is normal for me... its a pitty

---

### Post by sloggerkhan on 2009-10-10
no problems if you're used to ubuntu.

---

### Post by afrodeity on 2009-10-11
> **starcannon said:**
> My experience was similar; indeed my 64bit install eventually self destructed and I went back to 32bit at that point. I keep /home on a separate partition, so it was no big deal to switch back.

I wish /home on separate partition was an option in the installer? Or has this been changed in newer releases?

I'm very tempted to simply install jaunty 32bit. But maybe I should wait for karma 64 official release, in less than a month?

I think the main problem for me is that not all available software for the ubuntu universe is progressing at the same speed, wish there was a better way of tracking what was available and in what state for which version and to have a better system for upgrading from one release to the next. I really don't want to have to destroy my system every 6 months. Its okay if you a geek and but if you just trying to get things done, it becomes a huge time sink. Any thoughts?:(

---

### Post by Screwdriver0815 on 2009-10-11
> **afrodeity said:**
> I wish /home on separate partition was an option in the installer? Or has this been changed in newer releases?

I'm very tempted to simply install jaunty 32bit. But maybe I should wait for karma 64 official release, in less than a month?

I think the main problem for me is that not all available software for the ubuntu universe is progressing at the same speed, wish there was a better way of tracking what was available and in what state for which version and to have a better system for upgrading from one release to the next. I really don't want to have to destroy my system every 6 months. Its okay if you a geek and but if you just trying to get things done, it becomes a huge time sink. Any thoughts?:(
my experience is that you have the same amount of software for 64 bit as for 32 bit available. Nothing missing yet.

The package management automaticly devides the 64 bit or 32 bit packages depending on the system you have installed.

If you want speed, go for 64 bit! :D

an seperate /home folder can be created by manually partioning the HDD. So its not like a button in the installer. I know, Debian has this option in the installer, but Ubuntu not... don't know why.

You don't need to destroy your system every 6 months. 
You also could try to do an upgrade via the update manager. But as I never do that, I can not say how this works. Or you don't install a new version and wait for the LTS in April 2010 :D Jaunty is supported until October 2010.

---

