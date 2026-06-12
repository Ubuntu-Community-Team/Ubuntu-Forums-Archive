---
title: "Half-baked OS with non-intuitive methods"
date: 2008-03-10
forum: Testimonials &amp; Experiences
---

### Post by pmsagdeo on 2008-03-10
This OS is turning out to be more trouble than it seems worth.  Here are the basic problems:

1. Video resolution does not stick.  I end up having to reboot the machine more than once, every other time practically, when I want to use it to get it to show the set screen resolution.  It somehow like to boot up in 800x600 more often than not.  The config file correct.  

2. Cannot write DVDs.  Destroyed half-a-dozen of them before surrendering to this stupid behavior.

3. Cannot run programs in the working directory without having to type the entire path in the command.  How weird can it get?  Some paths are too long to have to type again or to scroll to and then make changes carefully.  

Hope someone has figured out the solutions to the above.  If not, I am done with Linux for now.  Thanks.

pmsagdeo

---

### Post by freebeer on 2008-03-10
You'd be best off to post your questions in another area.  Testimonials and Experiences aren't really the right place to look for help.

If typing long paths are an issue, then you can either CD to the directory you want, and work from there without the need for the full path, you can add the path to your PATH$, or you can use a wonderful feature called auto-complete to help you.

---

### Post by hyperair on 2008-03-10
1. You probably got the wrong video driver installed. What graphics card are you using?
2. Can't help you there. Personally I've had hardly any problems with this, but a good dvd burner program is K3B.
3. Have you tried "./program"? "." refers to the current directory. ".." refers to the parent directory. 

Also I honestly think you'd get more help if you posted with a more positive title than "Half-baked OS with non-intuitive methods". Geez, just because you don't know how to use it, it suddenly becomes non-intuitive and half-baked is it? Ubuntu isn't another Windows. It's a whole different OS altogether. If you're not willing to learn how to use a new OS perhaps you'd be better off just sticking with Windows and all its nonsense.

---

### Post by Niteowler on 2008-03-10
My video resolution will change on me about once in every 10 to 15 boots.  I have the right card driver too.  Weird but it does happen.  My ide dvd rom won't even mount to use dvd's or cd's.  I have some wonky going on with my motherboard though.

---

### Post by Laplace's Daemon on 2008-03-11
As hyperair mentioned, you can reference the current directory with the '.', so a call to a program in the current directory would be ./a.out.

Alternatively, you can avoid this all together by adding the following line to your .bashrc file (or type it in the terminal to see how it works):

```
export PATH=${PATH}:.
```

A bit of explanation: PATH is the variable that tells bash what directories to look in for the program names you type in.  In PATH, each directory is separated by a colon, and they are searched in the order that they are presented.  The command given above tells bash to look in the current directory for the command if it cannot be found in any of the other path directories.

---

### Post by steveneddy on 2008-03-11
> **pmsagdeo said:**
>  I am done with Linux for now.  Thanks.



You're welcome.

Come again.

Is this a cry for help?

A support issue needs to be in the proper section of the forums.

I just want to make sure that you want help or are you telling us that you are leaving?

There are thousands of Ubuntu users out there, worldwide, that learned the OS. Most Ubuntu users that were successful came to these forums and asked questions and read a lot until they had a good understanding of the issue.

You don't give us any specs from your PC and bash the Ubuntu community telling us that the OS we choose to use and **help you with for free** is too hard for you.

Ubuntu Linux is not Windows. It doesn't act like Windows nor does one control it like Windows.

At this time you have 8 posts, none of them threads asking for support of your video driver, for instance.

I see that you have an ATI card. Did you search the forums for ATI video related issues?

Before you post a thread bashing, work through the issues. **You aren't the first person with the same issues and you won't be the last.**

A quick search may have found the correct thread that would have helped you with all of your issues.

I hope that you get your issues resolved. This is a great OS and an even better community.

---

### Post by hyper_ch on 2008-03-11
> **pmsagdeo said:**
> 1. Video resolution does not stick.  I end up having to reboot the machine more than once, every other time practically, when I want to use it to get it to show the set screen resolution.  It somehow like to boot up in 800x600 more often than not.  The config file correct.
Works fine for me

> **pmsagdeo said:**
> 
2. Cannot write DVDs.  Destroyed half-a-dozen of them before surrendering to this stupid behavior.
Works fine for me

> **pmsagdeo said:**
> 
3. Cannot run programs in the working directory without having to type the entire path in the command.  How weird can it get?  Some paths are too long to have to type again or to scroll to and then make changes carefully.
How do you run them in the working dir? I guess you just do
```

executable.ext

```

> **pmsagdeo said:**
> 
Hope someone has figured out the solutions to the above.  If not, I am done with Linux for now.
If that stops you using Linux, you really should consider returning to Windows as it seems unlikely you'll get used to (or want to get used to) Linux at all...

---

### Post by Antman on 2008-03-11
> **pmsagdeo said:**
> 
If not, I am done with Linux for now.  Thanks.


Ubuntu is NOT the end nor the beginning of Linux. There are MANY linux distros. If  Ubuntu doesn't fit the bill, try another.

Check here: [www.distrowatch.com]("http://www.distrowatch.com")

Enjoy,

Ant

---

### Post by pmsagdeo on 2008-03-15
Video resolution won't stick.  A definite limitation.  Having to boot the machine twice every other time is a drag, no matter how you look at it.  If Windows did it, people will scream all sorts of things about it.

DVD writer still does not work.  Not just for me, for many others.  Just look at the forums. This, after doing a clean install of Ubuntu twice and trying two different programs under GNOME.  

That the OS cannot default to current directory without a ./ every single time, and/or needs PATH for all directories in which one has executables, is a limitation. Eventually the PATH statement may get too long.  

I started using computers when command line was the rule, not the exception.

One of the computer magazines just compared a few OSs, and called Ubuntu, and by extension, Linux in general, a BEAST, and gave it the lowest rating.  I can see why.   I tried SuSE 10.3 and abandoned it before trying Ubuntu.  The difference in usability is marginally in favor of Ubuntu.  

Well, I will stop complaining now.  I have multiple Windows machines that work fine for 99.99999% of my needs.  I will toy with Ubuntu in my spare time.  Maybe even I can learn to like it eventually if I can write DVDs and not have to reboot it to see the screen resolution I have set

---

### Post by vexorian on 2008-03-15
Looks like your hardware is half baked, and none of what you posted is due to being unintuitive but due to bad hardware support. 

Linux programs don't really got working directory dependencies usually, but if you need to you just need to make a desktop launcher or a script. You are certainly making a whole big deal on this one, sounds like you've never used Unix? Did you stay trapped in a box for ages or what? Since you say that you started using PC when terminals were a rule, so I find it very hard to believe you never learned any Unix.


> That the OS cannot default to current directory without a ./ every single time
And this is by far a lot more intuitive solution to me than the ambiguous MS style. it is the default for most unix based OSes, in this case MS' OSes are the minority, get used to typing the path. When you get used to it you find out it is better anyways.


> One of the computer magazines just compared a few OSs
You are starting to sound like a troll. But I will ignore that fallacy of authority just in case.


> DVD writer still does not work Install k3b and report bugs instead of complaining. Cause this behavior is not the norm, my computer writes DVDs just fine, unfortunately it doesn't on windows :( , of course, I could go mad and say that windows is a half baked OS, but I know better than that and there are always speficities about a problem.


> Well, I will stop complaining now. I have multiple Windows machines that work fine for 99.99999% of my needs.I take it all you do with your computers is browse a very small set of web pages then.


--
If you had graphic card issues, wait for the ATI OS drivers to go mainstream or make sure you got nvidia before trying Linux, don't blame FLOSS out of the mistakes and negligence of hardware developers which even by the year 2008 did not think of making standard specs for their hardware pieces and don't bother releasing theirs.

---

### Post by Cresho on 2008-03-15
Like yourself, I was having issues as well.  As time went on, I realized something was missing.  My Ubuntu..it is like a cup of coffee.  You drink it and after a while, it just calls you even though sometimes it may taste like ashtray or dirt.  My Ubuntu!!!  yum!

In any case, I tried it in the 5 series, went back to windows.  Then I came back to it at 6 and 7.  I cannot believe it has been almost 2 plus years.  My! Time flies but my Ubuntu tastes ......excellent.

I became desperate so I decided to buy my hardware that was either hackable or more Ubuntu friendly.  As of this witting, I cannot spend a day without a cup of.....Ubuntu....at least for an hour.

---

