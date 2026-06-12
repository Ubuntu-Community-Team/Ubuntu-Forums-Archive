---
title: "Ubuntu 64bit enormously faster than 32bit"
date: 2009-12-30
forum: The Cafe
---

### Post by hyperdude111 on 2009-12-30
Full Article - [http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

[IMG]http://1.bp.blogspot.com/_FJH0hYZmVtc/Szuj0o3ZS4I/AAAAAAAAFIk/5KG3ACPSJwk/s1600-h/Desk+1_30.png[/IMG]

An article on phoronix.com investigates with some detail the differences between the 32, 32 PAE and 64 bit linux kernels. The results were conclusive, 64bit was faster on all accounts and by a vast margin. 
They finish the article with this statement:
> By far though exhibiting the best performance was the Ubuntu 64-bit kernel that often ended up being leaps and bounds better than the 32-bit kernel. Unless you have technical or business reasons for not migrating to 64-bit Linux with compatible hardware, there is no reason to stick around with a 32-bit kernel and worrying about physical address extension. 

To run your own benchmarks with the phoronix suite follow this link [http://www.phoronix-test-suite.com/](http://www.phoronix-test-suite.com/)

---

### Post by Crunchy the Headcrab on 2009-12-30
I've always used 64bit and never had a problem with it.

---

### Post by Skripka on 2009-12-30
Ubuntu optimized for a 30 year old CPU is far slower, on the same hardware and on the same tests, than Ubuntu optimized for CPUs post-2003.  

Who ever woulda thunk?

PS-In case anyone is keeping track, this is the FIRST benchmarking article by Phoronix that has ANY real meaning-that I can remember.

---

### Post by blueshiftoverwatch on 2009-12-30
> **Skripka said:**
> Ubuntu optimized for a 30 year old CPU is far slower, on the same hardware and on the same tests, than Ubuntu optimized for CPUs post-2003.  

Who ever woulda thunk?
:)

---

### Post by alakazam on 2009-12-30
Do you know if I can run a 64bit iso (ubuntu)? :confused:

---

### Post by Crunchy the Headcrab on 2009-12-30
> **alakazam said:**
> Do you know if I can run a 64bit iso (ubuntu)? :confused:
Judging from the specs in your sig, yes.

---

### Post by blueshiftoverwatch on 2009-12-30
> **alakazam said:**
> Do you know if I can run a 64bit iso (ubuntu)? :confused:
According to your signature your CPU is an Intel Core 2 Duo, which all utilize the x86_64/amd64 (64 bit) instruction set. So yes, you can.

---

### Post by alakazam on 2009-12-30
cheers guys :popcorn:

---

### Post by 3Miro on 2009-12-31
Some benchmark some time ago gave 64-bit an average of small improvement for everyday apps.

For my purposes, I have to use 64-bit (sientific computing gets a huge boost from 64-bit).

If your computer supports it and you don't have one of the few 64-bit driver problems (or a very good reason not to use 63-bit), you should go with 64-bit.

---

### Post by xuCGC002 on 2009-12-31
> **alakazam said:**
> cheers guys :popcorn:
in fact, it'll utilize all 4GB of your RAM.

---

### Post by Psumi on 2009-12-31
Too bad I can't install 64-bit on my IBM ThinkPad ;)

---

### Post by HappyFeet on 2009-12-31
I'll never use 32bit again. 64bit rocks.

---

### Post by lisati on 2009-12-31
*Sighs.* Wish I'd used 64-bit when I reinstalled on my laptop. Got 64-bit server going on one of my desktops.

---

### Post by dhysk on 2009-12-31
Ya I did some testing back in April because I had 4GB or ram and couldn't use it all with the standard install.  I found using phorionix that the 64bit was a bit faster.  However I also ran the systems each normal 32 bit install, than the 32bit with PAE, and then 64bit.  All in all i went with 64 bit.  Why, well it did post the best numbers so it was faster.  However was VERY minimal between 32 bit PAE and 64 bit under normal use.  I kept 64 bit because after installing it 3 times I didn't want to do it again.

That being said 64 bit still has some compatibility issues and even with things that come with a 64 bit version can be flaky.  All in all I'm glad I stuck with it.


System:
Intel Core2Duo E8400 3.0GHZ
2 x2GB sticks of Corsair XMS RAM
9800GTX video card
500GB Maxtor HD

---

### Post by HappyFeet on 2009-12-31
> **dhysk said:**
> things that come with a 64 bit version can be flaky.  

What's flaky? Mine has been rock solid.

---

### Post by Linuxforall on 2009-12-31
Been on x64 since the day Ubuntu launched it and have never regreted, except for 3rd party stuff like Skpye, Flash etc nothing has been even close to flaky, everything works better and quicker than x32. Now with flash x64, even thats a big time boost over its x32 counterpart.

---

### Post by dhysk on 2009-12-31
whats been flaky?  Peripherals mostly, like my cannon scanner /printer a few games like x-plane.  However with a little more work I was able to get them to work just not as easy as when I was using the 32 bit.  Also things like the cario-dock also seams to be flaky as well but doable.  All in all I've like 64 bit.

---

### Post by Exodist on 2009-12-31
I been running 64bit Ubuntu since 5.04.

---

### Post by dyslexia on 2009-12-31
I have 32pae installed, tried to get the 64bit kernel by copying it from a vanilla 64-bit install, afraid of conflcts, so I renamed some of the libraries...

is there an easy way to download a 64 bit kernel if you are currently running 32 bit?

---

### Post by lisati on 2009-12-31
> **dyslexia said:**
> I have 32pae installed, tried to get the 64bit kernel by copying it from a vanilla 64-bit install, afraid of conflcts, so I renamed some of the libraries...

is there an easy way to download a 64 bit kernel if you are currently running 32 bit?

Might be easier and safer to backup your data and do a fresh install.......

---

### Post by dyslexia on 2009-12-31
I have about 15 different snapshots of my 6 gb system as it's evolved over the last three months.

I have two 10 gb "test" areas where I test installs of different releases.

the 64 bit kernel and libraries came from a "fresh install".

I deleted it, but it still might be fun to play with the kernel... will probably get rid of the 64 bit stuff I have if no easy upgrade is found.

Should just be the kernel + libraries.

---

### Post by dyslexia on 2009-12-31
so, I don't even have to do a back-up to do a "fresh install".... but it's a waste of time.

should be an easy way to download & install a 64 bit kernel.... some apt-get or other...

...and yes, a back-up before doing THAT would definitely be in order...

---

### Post by benmoran on 2009-12-31
It's good to see more and more people moving out of the stone age :).

---

### Post by iamfreeman on 2009-12-31
what are the limitatations to using the 64bit version.

---

### Post by insane_alien on 2009-12-31
> **iamfreeman said:**
> what are the limitatations to using the 64bit version.

well, you encounter hardware limitations before software limitations. you can't use more than 16Exabytes of memory on a single machine(a few billion times more than can currently be jammed into a a typical machine.) thats about it really. thelimitations that exist are many orders of magnitude larger than 32 bit limitations which are becomingvery restrictive as our need for processing power multiplies.

---

### Post by linuxrollup on 2009-12-31
I've been using 32-bit Ubuntu for ages and it was only yesterday I set up a dual-boot (XP and Ubuntu Jaunty x64) and I noticed how much faster 64-bit was over 32-bit Ubuntu.

---

### Post by Paqman on 2009-12-31
> **iamfreeman said:**
> what are the limitatations to using the 64bit version.

Occasionally you might find some 3rd party software that isn't available in a 64-bit version. Adobe seems to be particularly bad for this.

---

### Post by Zoot7 on 2009-12-31
"Number Crunching" is always going to be faster with the 64bit OS due to the fact that the vast majority of CPUs these days are 64bit anyway, and can't use their ALU to the full capacity if you're using a 32bit OS.

---

### Post by Skripka on 2009-12-31
> **dyslexia said:**
> so, I don't even have to do a back-up to do a "fresh install".... but it's a waste of time.

should be an easy way to download & install a 64 bit kernel.... some apt-get or other...

...and yes, a back-up before doing THAT would definitely be in order...

My friend.

ALL of your apps and software are compiled for either i386 or amd64.  You CANNOT just load a different CPU-architecture kernel and expect ANYthing other than headaches. 

Reinstall is all you can do to go from 32bit->64bit.

---

### Post by MichealH on 2009-12-31
> **HappyFeet said:**
> I'll never use 32bit again. 64bit rocks.

I have been using M$ 7 x64 for about 2 weeks now *hangs head in shame* but on x86 I found that 64 bit is faster and less delicate as the first BSOD I had was on x86 after 4 days and I haven't had one on x64 yet!

> **HappyFeet said:**
> What's flaky? Mine has been rock solid.

Yup as I said above 64-bit is the way forward cant wait for 128-bit to come out in Win 8/9 I will be racing for a 128 bit processor BUT M$ may not support 32 bit apps on 128 bit Windows :(

---

### Post by Skripka on 2009-12-31
> **MichealH said:**
> 
Yup as I said above 64-bit is the way forward cant wait for 128-bit to come out in Win 8/9 I will be racing for a 128 bit processor BUT M$ may not support 32 bit apps on 128 bit Windows :(

You'll be waiting a VERY LONG time to use your 128bit processor then.  3rd party apps and drivers don't even fully support 64bit on Windows yet.  Do you know how long it will be after Win8/9 come out to wait for 128bit apps and drivers?

---

### Post by Ylon on 2009-12-31
Will we be ever able to see an 128Bit OS with microkernel?

Now, that would quite interesting benchmark to see ;)

---

### Post by iamfreeman on 2010-01-03
well it just seems that a 64bit system should be so much greater, but even using windows, it is hard to find 64bit programs. true, alot of software is showing up on the market that does offer a 64bit option, but most dont. so if you have a x64 system, but most of the software is 32bit what is the true effect?

---

### Post by TironN on 2010-01-03
> **iamfreeman said:**
> well it just seems that a 64bit system should be so much greater, but even using windows, it is hard to find 64bit programs. true, alot of software is showing up on the market that does offer a 64bit option, but most dont. so if you have a x64 system, but most of the software is 32bit what is the true effect?

The question isn't how many can't. As long as some do there is an advantage!

Plus I can't wait until 128bit so I can stick in 340282366920938463463374607.431768211 Terabytes of RAM. :P

---

### Post by siimo on 2010-01-03
I will keep using 32bit until I upgrade my computer with more than 4GB memory or if 32bit was dropped from being mainstream - which would probably not happen for at-least another decade.

---

### Post by murderslastcrow on 2010-01-03
I think 1 Terabyte would suffice. XD

I wish I'd known about 64-bit before my HP Tablet melted like everyone elses'. It was all in the news and everything, and I didn't realize that 64-bit was better until I installed it for a friend. =_=

---

### Post by gnomeuser on 2010-01-03
> **iamfreeman said:**
> what are the limitatations to using the 64bit version.

In the base system none what so ever, however Flash doesn't have a stable 64bit port (I would argue they don't have a stable anything so who cares) and Skype doesn't have a 64bit port. For this multilib and the current CPU designs allow you to run 32bit applications seamlessly so effectively no downside.

---

### Post by cascade9 on 2010-01-03
> **MichealH said:**
> Yup as I said above 64-bit is the way forward cant wait for 128-bit to come out in Win 8/9 I will be racing for a 128 bit processor BUT M$ may not support 32 bit apps on 128 bit Windows :(

That is quite likely, but read what microsoft said about 16 bit on 64 bit windows (server 2003 and XP_64)- 

> The x64-based versions of the Microsoft Windows Server 2003 operating systems and Microsoft Windows XP Professional x64 Edition do not support 16-bit programs, 16-bit processes, or 16-bit components. However, these 64-bit versions of Windows may recognize some 16-bit installers and automatically convert the 16-bit installer to a 32-bit installer.

[http://support.microsoft.com/kb/896458](http://support.microsoft.com/kb/896458)

By the time that 128bit CPUs come out (2011, at the earliest, and porbably more like early 2013) I would guess that there will eb far more 64 bit programs...and hopefully a lot of the 32bit versions will automatically convert to 64 bit installers.

---

### Post by hyperdude111 on 2010-01-03
> **iamfreeman said:**
> well it just seems that a 64bit system should be so much greater, but even using windows, it is hard to find 64bit programs. true, alot of software is showing up on the market that does offer a 64bit option, but most dont. so if you have a x64 system, but most of the software is 32bit what is the true effect?

It's not even using windows, in this case it's mostly using windows. Linux has a higher percentage of poplar apps ported to 64, however in windows 64bit is less common because of their less technically minded user base. Also because most 32bit windows apps install out of the box on 64 windows. 

In linux about 90% of the popular apps have 64bit ports. Even adobe released a second version of the flash port last month. In comparison windows does not have a 64 bit flash port.

---

### Post by hobo14 on 2010-01-03
> **murderslastcrow said:**
> I think 1 Terabyte would suffice. XD


For now ;)

Don't forget that once upon a time: "**640K should be enough for anyone**"

---

