---
title: "Rationale behind utilizing the linux kernel instead of the opensolaris kernel"
date: 2006-12-16
forum: The Cafe
---

### Post by user1397 on 2006-12-16
I was discussing in some irc channel a few days ago about the linux and opensolaris kernels.  the name _[nexenta]("http://www.nexenta.com/index.php")_ (a GNU/opensolaris distro based on ubuntu) even reached my ears, and the person arguing for the opensolaris kernel had very convincing statistics and stuff (sorry but I did not bookmark them, so I don't remember what they are) about how opensolaris is faster and more stable than linux.  I was utterly confused...I had a mentality that linux was the best for servers and stability, but this guy was basically convincing me that it was otherwise.

what I want to know, is the people's opinions here in the forums, of why the linux kernel is always preferred before other kernels, like the BSD kernel or the opensolaris kernel.

after all, the opensolaris and BSD kernels are "free-er" than the GPL'D linux kernel, plus opensolaris is backed by Sun Microsystems, one of the biggest competitors of Microsoft, and already a friend of ubuntu.  

wouldn't bug #1 be easier to reach using opensolaris for ubuntu's kernel?

---

### Post by Polygon on 2006-12-16
im confused, you can get a more "free" license other than the gpl? doesn't the gpl let you use it and modify it and distribute it any way you want? how can you get more free then that?

---

### Post by user1397 on 2006-12-16
> **Polygon said:**
> im confused, you can get a more "free" license other than the gpl? doesn't the gpl let you use it and modify it and distribute it any way you want? how can you get more free then that?well opensolaris uses the _[CDDL]("http://www.opensolaris.org/os/licensing/opensolaris_license/")_ license, which according to the guy I was discussing this stuff about, is a little more flexible in its terms than the _[GPL]("http://www.gnu.org/licenses/gpl.txt")_

---

### Post by vayu on 2006-12-16
Whether any of the three OSs you mentioned are better than any of the others is not a universally agreed point. 

BSD license is more free because you can use the code add your own stuff and make it proprietary.  In other words you are less restricted to use it commercially for your own.

---

### Post by user1397 on 2006-12-16
> **vayu said:**
> Whether any of the three OSs you mentioned are better than any of the others is not a universally agreed point. 

BSD license is more free because you can use the code add your own stuff and make it proprietary.  In other words you are less restricted to use it commercially for your own.ah, thanks for clearing that up for me.  

and good point, no 100% agreement can be made, but we can look at pros and cons.

as I see it, the linux kernel is a huge (and genius) batch or ordering of code, that was and is developed by many people, and Linus Torvalds afaik, has the rights to the kernel by himself.

On the other hand, solaris (and opensolaris) was made and is supported by Sun Microsystems, a huge company, which has brought the Java language, OpenOffice.org, and the open-source solaris kernel to us free of charge, and is a potential competitor of Microsoft (and competing against Microsoft for the desktop OS market IS ubuntu's # 1 bug, according to [http://launchpad.com](http://launchpad.com))

---

### Post by prizrak on 2006-12-16
> **erik1397 said:**
> ah, thanks for clearing that up for me.  

and good point, no 100% agreement can be made, but we can look at pros and cons.

as I see it, the linux kernel is a huge (and genius) batch or ordering of code, that was and is developed by many people, and Linus Torvalds afaik, has the rights to the kernel by himself.

On the other hand, solaris (and opensolaris) was made and is supported by Sun Microsystems, a huge company, which has brought the Java language, OpenOffice.org, and the open-source solaris kernel to us free of charge, and is a potential competitor of Microsoft (and competing against Microsoft for the desktop OS market IS ubuntu's # 1 bug, according to [http://launchpad.com](http://launchpad.com))

Linux OS's are made, maintained and developed for by Novell, RedHat, IBM, Sun, etc.... Those are all big companies with a good amount of pull in the market.

---

### Post by 3rdalbum on 2006-12-16
If Ubuntu used the OpenSolaris kernel, lots of people would complain about not being able to get 3D acceleration with ATI cards.

Also, lots of people's Winmodems and wireless cards wouldn't be able to work.

I'm sure the OpenSolaris kernel is good, but Linux has higher performance. I read that they tested Ubuntu Server against Solaris and Ubuntu came out on top.

---

### Post by kripkenstein on 2006-12-16
> **erik1397 said:**
> 
after all, the opensolaris and BSD kernels are "free-er" than the GPL'D linux kernel


Some argue that the CDDL, used by OpenSolaris, is 'free-er' than the GPL. The difference isn't much, though. Now BSD is certainly more free, but at the cost of not getting back changes from people who use your code - and this is one of the **major** reasons why Linux succeeded so much - when people modified it, they had to GPL their code, which let the kernel advance very fast. So, this is one reason why, historically, Linux has succeeded more than the BSDs. Also, people are more giving of their time to a GPL project, I think. With BSD, you can have doomsday scenarios like Microsoft taking your work and giving nothing back (as happened with BSD network code, it is said, and as Apple did with BSD, but at least they do give other things back to the OSS community). This can't happen with GPL.

> 
 plus opensolaris is backed by Sun Microsystems, one of the biggest competitors of Microsoft, and already a friend of ubuntu.  


This brings us to the major problem with OpenSolaris - it is **new**. Sun open-sourced it only in the very recent past, compared to Linux. Had Sun opened it in the 90's, we may very well all have been running Ubuntu with a Solaris kernel right now. So yes, Sun are a friend of Ubuntu, and a successful company, but they weren't always as OSS-friendly as they are now.

So, Solaris went open very late in the game, and has a **lot** of catching up to do - mainly in the device driver area. Sadly since it is CDDL, it can't just incorporate Linux drivers (which are GPL). If Sun were to GPL OpenSolaris, that might help out in this matter. Otherwise, they need to redo what took Linux years of hard work - to get it to run on almost any hardware you can buy. There is a good reason why it is said that "Linux runs on more hardware, out of the box, than any other operating system" - more than Windows, even :)

Aside from that, OpenSolaris seems to be an excellent kernel. The benefits may not matter **all** that much to the typical desktop user, though (a bit more stability, a bit more performance - both are nice, but not crucial), so there is no immediate urgent push to use OpenSolaris. Still, Nexenta is a nice project to watch.

And the OSS community does need options in the kernel area. For example, if Linux remains GPL version 2, and Sun decide to release OpenSolaris under GPL version 3 (which they have hinted at), then perhaps OpenSolaris will suddenly gain a lot of supporters. I may be one of them, assuming of course that by then OpenSolaris can support all of my hardware.

---

### Post by migla on 2006-12-16
The freedom to restrict other peoples freedom, as with the BSD license, is not necessarily more freedom, or at least not necessarily better freedom. It gives more freedom to the developer, yes, but less freedom to everyone else.

---

### Post by user1397 on 2006-12-16
> **migla said:**
> The freedom to restrict other peoples freedom, as with the BSD license, is not necessarily more freedom, or at least not necessarily better freedom. It gives more freedom to the developer, yes, but less freedom to everyone else.ah...good point.  it's all about relative perceptions...

---

### Post by user1397 on 2006-12-16
> **kripkenstein said:**
> Some argue that the CDDL, used by OpenSolaris, is 'free-er' than the GPL. The difference isn't much, though. Now BSD is certainly more free, but at the cost of not getting back changes from people who use your code - and this is one of the **major** reasons why Linux succeeded so much - when people modified it, they had to GPL their code, which let the kernel advance very fast. So, this is one reason why, historically, Linux has succeeded more than the BSDs. Also, people are more giving of their time to a GPL project, I think. With BSD, you can have doomsday scenarios like Microsoft taking your work and giving nothing back (as happened with BSD network code, it is said, and as Apple did with BSD, but at least they do give other things back to the OSS community). This can't happen with GPL.



This brings us to the major problem with OpenSolaris - it is **new**. Sun open-sourced it only in the very recent past, compared to Linux. Had Sun opened it in the 90's, we may very well all have been running Ubuntu with a Solaris kernel right now. So yes, Sun are a friend of Ubuntu, and a successful company, but they weren't always as OSS-friendly as they are now.

So, Solaris went open very late in the game, and has a **lot** of catching up to do - mainly in the device driver area. Sadly since it is CDDL, it can't just incorporate Linux drivers (which are GPL). If Sun were to GPL OpenSolaris, that might help out in this matter. Otherwise, they need to redo what took Linux years of hard work - to get it to run on almost any hardware you can buy. There is a good reason why it is said that "Linux runs on more hardware, out of the box, than any other operating system" - more than Windows, even :)

Aside from that, OpenSolaris seems to be an excellent kernel. The benefits may not matter **all** that much to the typical desktop user, though (a bit more stability, a bit more performance - both are nice, but not crucial), so there is no immediate urgent push to use OpenSolaris. Still, Nexenta is a nice project to watch.

And the OSS community does need options in the kernel area. For example, if Linux remains GPL version 2, and Sun decide to release OpenSolaris under GPL version 3 (which they have hinted at), then perhaps OpenSolaris will suddenly gain a lot of supporters. I may be one of them, assuming of course that by then OpenSolaris can support all of my hardware.ah, you just informed me a lot more about this subject...looks like I'm gonna have to agree with you now :P

---

### Post by deanlinkous on 2006-12-17
if solaris goes GPLv3 then solaris is what I will be running!

---

### Post by MaximB on 2006-12-17
I've downloaded it but sadly it has no live cd/dvd :( , so I didn't install it YET.
but it's new and it has a LONG way to do in terms of programs support.
if windows runs 99% of the programs and Linux runs 20% (without wine) then opensolaris runs less then 5%. (it's all my guesses).
so even if the Kernel is the best and the hardware support is perfect you still need software support as well.

---

### Post by kripkenstein on 2006-12-17
> **MAXDDARK said:**
> I've downloaded it but sadly it has no live cd/dvd :( , so I didn't install it YET.
but it's new and it has a LONG way to do in terms of programs support.
if windows runs 99% of the programs and Linux runs 20% (without wine) then opensolaris runs less then 5%. (it's all my guesses).
so even if the Kernel is the best and the hardware support is perfect you still need software support as well.

Linux programs that don't access the kernel directly should work fine under Nexenta. For example Nexenta runs GNOME and all its apps. This is similarly to how BSD can run Linux apps (the devs do need to do some work, but it is reasonable). And anyhow Linux distributions are so different that a program needs to not be too 'tied in' to one specific setup (of directories, for example) anyhow, which helps running it on other types of systems.

So, I think that the main issue is device drivers in the kernel, Nexenta can or will soon run most Linux apps.

---

### Post by kripkenstein on 2006-12-17
Btw, one other OpenSolaris issue: OpenSolaris has a fixed binary API, and it allows binary drivers - unlike Linux. This is in fact one of the reasons Sun chose the CDDL for OpenSolaris instead of the GPL.

Should OpenSolaris gain any significant market share this might be useful for it, if vendors start producing drivers (which they are generally happier to do when they can remain closed-source). However, it brings with it all the disadvantages of closed-source drivers, which may be bad for it in the long run.

So it is unclear how this will play out. However, people who don't mind binary drivers (something that Ubuntu is moving closer to, with Feisty and binary graphics drivers) may find OpenSolaris more to their liking than the Linux kernel.

---

### Post by IYY on 2006-12-17
> after all, the opensolaris and BSD kernels are "free-er" than the GPL'D linux kernel, plus opensolaris is backed by Sun Microsystems, one of the biggest competitors of Microsoft, and already a friend of ubuntu.

It is not correct to say that these kernels are free-er. They do give you more immediate freedoms, but do not implement any mechanism to ensure that those freedoms will remain. While FreeBSD itself can be modified and redistributed, a large company like Microsoft could take the BSD licensed code, make large modifications to it (breaking compatibility with the rest of the world), making their own programs run on it but not on other distributions. Now, the rest of the world switches to the Microsoft FreeBSD, FreeBSD is destroyed and the code is no longer free.

Such a thing can not happen with the GPL. It ensures that no matter what happens to the code, it will always remain Free.

---

### Post by MaximB on 2006-12-17
one thing I do not get , why hardware companies are afraid to release open sourced drivers for their hardware that you bought ? it's not like they loosing something , it can only profit them.
cuz hardware unlike software is hard to pirate. (well , you can steal it from the store but that's something else ;)).

---

### Post by maniacmusician on 2006-12-17
> **MAXDDARK said:**
> one thing I do not get , why hardware companies are afraid to release open sourced drivers for their hardware that you bought ? it's not like they loosing something , it can only profit them.
cuz hardware unlike software is hard to pirate. (well , you can steal it from the store but that's something else ;)).
releasing open source drivers would mean revealing the specifications of their cards, which would mean other companies would be able to copy their cards. and probably lead to them losing profit.

---

### Post by agurk on 2006-12-17
> **deanlinkous said:**
> if solaris goes GPLv3 then solaris is what I will be running!
Your reasoning is not unique, and it does put some pressure on the Linux kernel devs, whether they'd like to admit it or not. Taking the back seat by refusing to even participate in the GPL3 process doesn't impress me, at least. GNU/Linux or GNU/Solaris, that is the question, and I'm sure a lot of folks will be attracted to the latter, for technical or ideological reasons. Interesting times.

---

