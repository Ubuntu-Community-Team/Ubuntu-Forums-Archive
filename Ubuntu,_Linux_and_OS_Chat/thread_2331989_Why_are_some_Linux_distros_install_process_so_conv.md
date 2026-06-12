---
title: "Why are some Linux distros install process so convoluted?"
date: 2016-07-27
forum: Ubuntu, Linux and OS Chat
---

### Post by ardouronerous on 2016-07-27
I tried installing Puppy LInux and Damn Small Linux via VirtualBox just to give them a try, and I can tell you, my experience was less than pleasant, the install procedure had me going in circles, it wasn't that clear, there was no guides to help you along, unfortunately, I got so frustrated, I basically had a rage quit.

Why are some Linux distros install procedures  so convoluted? Are they trying to make novice computer users rage quit? This is the reason why Ubuntu and it's other derivatives  are so popular, and the other distros are left in the dust, Ubuntu follows the concept of KISS (Keep It Simple Stupid).

Even Linus Torvalds said, when he tried installing Debian back in 2007, he found the install procedure too difficult and never installed it.

Note: the title is misleading, Linus never mentions Ubuntu, only Debian.
[video=youtube;qHGTs1NSB1s]https://www.youtube.com/watch?v=qHGTs1NSB1s[/video]

---

### Post by buzzingrobot on 2016-07-27
Torvalds was right about Debian's installer back then. Thoroughly obtuse and painful.

Certain things must be done to get any new OS installed. The most obvious is creating partitions to host the OS. If someone has never been exposed to partitioning, it's all a bit scary. (And the Windows installer only exposes partitioning if a user deliberately clicks on a euphimized label.  It never actually deals with partitions in clear language, IIRC.)

Partitioning automagic in an installer is possible because the installer makes certain assumptions that deliberately limit the alternatives to something it can handle. 

Going beyond that to offer an installer that includes a full range of partitioning options is going to get complex pretty quickly.  Things like GPT vs MBR, UEFI vs legacy BIOS, LVM,  Secure Boot or not, etc., have to be dealt with and there is every chance the user will have no clue what they're all about.

---

### Post by grahammechanical on 2016-07-27
I can remember when I first tried Linux many years ago. It was SuSE. I had to select the applications I wanted. And for every possible application there was a choice of 4 or 5 alternatives. And I had no idea of what I was looking at. It put me off Linux.

With Ubuntu we accept the choice the developers make as to the default set of applications. I am happy with that situation. Others like to have more control. When I first found Ubuntu (2007) it was called "Linux for Humans." We do not say that any more but I would say that is what makes the difference.

Regards.

---

### Post by ardouronerous on 2016-07-27
> **grahammechanical said:**
> When I first found Ubuntu (2007) it was  called "Linux for Humans." We do not say that any more but I would say  that is what makes the difference.

I hope Puppy Linux and Damn Small Linux gets there act together and use  the KISS principal, I'd like at least one of them to became a 'Legacy Linux  for Humans' distro,  because I have a Pentium II in my closet and I'd like to  breath new life into it.

> **grahammechanical said:**
> With Ubuntu we accept the choice the developers make as to the default set of applications.

Well, while I agree that the developers' choice of Ubuntu's default set of applications is logical and practical, like most of what I need is already preinstalled, but I must say, I am critical with Ubuntu's choice of software center, the GNOME Software Center, it's buggy, I can't install .deb files with it and it sometimes crashes.

---

### Post by gnosoz on 2016-07-27
The hidden beauty of linux is the quantity of distros and the possibility of personalization.

Ubuntu is the most commercial one, the one that has the pros of a userfriendly configuration and the mighty power of a linux core and capabilities.
As someone before me said, the developpers make assumptions in order to allow you easy configuration but if you need every drop of power or to use old hardware then you must personalize the system.
 
Some distros like Slackware are mile behind in terms of automation (they are starting now with a package manager like aptitude) but if you like total control or you wish to develop your skills quickly then that is the way to go.
Mind you, keyboard shy people will find this distro impossible to use: installing packages requires understanding of make, understanding of connected packages and requirements, any problem or malfunction will require you get your sudo hat on and start munching configuration files.
 
Originally Slackware was intended as the most unix like distro is the pure example of KISS (Keep it simple stupid) but I must admit this seems to apply more to the structure rather than usage!!
 
Given that this distro requires enormous skills to setup and run in first place, I would venture to say machines running it are also the ones which are usually most secure, best configured and fastest.
(if you don’t have the skills you keep needing to format it so is always safe eheheh)
 
As an example the server running Slackware website is (news valid today) a Pentium III, 600 MHz, with 512 megabytes of RAM…..
 
There are some amazing distro outside and one per each person or requirement, should not complain for some being too complex as some might like them that way :)

---

### Post by QIII on 2016-07-27
Just so long as one does not make the mistake of generalizing all Ubuntu users as "beginners using a beginner system" who are ignorant and sloppy.

Everything available to the Slackware user is available to the Ubuntu user and many of us are as adept as the best users of Slackware.

---

### Post by gnosoz on 2016-07-27
Apologies but there is amisunderstanding I never intended as such!
After all as a Xubuntu user myself how could I! :)
What I intended is that Ubuntu can practically run out of the box with little intervention from user therefore making it the right first step from a windows machine whilst a user installing a distro like slackware would certainly experience issues like audio / screen / wifi or other hidden funny complications which requires manual intervention therefore "putting off" casual users. 
this was appropriately called earlier as rage quit during install already hehehe :)

I totally agree with your point and it can be fully personalized & streamlined as required and all programs running for other distrubutions are portable for ubuntu or have their own .deb pkg. 
"mind the gap" though as this would still requires the person to phisically touch config files like in other distros. 
Ubuntu can be as powerful as any other distribution, possibly thanks to the extensite testing can even prove as a safer choice? 

Ubuntu has more developpers, more users, more testers and this surelly means great or better overall reliability

---

### Post by QIII on 2016-07-27
Sorry, no.  :)  Not saying you in particular.  I edited my post!

Just referring to a common misconception about Ubuntu.

---

### Post by gnosoz on 2016-07-27
ehehe no hard feelings either way :)
Easy to understand why there is misconception.

If you have a distros one with plenty cool graphics and GUI whilst others which are more spartan in looks...people do not understand the base for both system is the same.

---

### Post by howefield on 2016-07-27
> **ardouronerous said:**
> I tried installing Puppy LInux and Damn Small Linux via VirtualBox just to give them a try, and I can tell you, my experience was less than pleasant, the install procedure had me going in circles, it wasn't that clear, there was no guides to help you along, unfortunately, I got so frustrated, I basically had a rage quit.

So, basically you started badly and then fell away.

---

### Post by buzzingrobot on 2016-07-27
> **QIII said:**
> 

Everything available to the Slackware user is available to the Ubuntu user and many of us are as adept as the best users of Slackware.

Very true.

Slackware today is almost identical to the Slackware I used "back then", and it's representative of how all distros worked at the time:  No dependency resolution, few binary packages, add drivers by reconfiguring and recompiling the kernel, etc.

Before you could be a user, you had to play Amateur Engineer.

I could still do all those things on Ubuntu or any other modern distribution. But, why?

---

### Post by QIII on 2016-07-27
> **buzzingrobot said:**
> But, why?

Prove your "geek cred"?  :)

---

### Post by montag dp on 2016-07-27
There seems to be some confusion here about the difference between simplicity and convenience, or at least what is typically meant by those terms.  Ubuntu is "simple" in that it is easy for someone with limited experience and knowledge to use. That doesn't make the system simple, though; in fact, it is quite the opposite. All those conveniences require abstraction layers on top of the core that make it harder to understand what the system is actually doing or change the behavior. That's fine and probably preferred by most users. However, others like the system itself to be simple so that they can learn and be in full control of it. There's nothing wrong with that, and it's still just as valid an approach today as it was 15 years ago, even if it's not for most people. (EDIT: And I also am not saying that one can't do those same things with Ubuntu, so don't take it that way.)

I think it is also worth mentioning that there is a continuum of simplicity-convenience in computing, where Windows/Mac/smartphones inhabit one end and do-it-yourself Linux and BSDs inhabit the other end. Ubuntu is somewhere in the middle. So if you think you really just want the most convenient system, you are wrong because you are already here using Ubuntu. Others simply fall more on the do-it-yourself end of the spectrum than you do. I say live and let live; there's no reason to put other people down because they have different preferences than you or put other distros down because they cater to those people. 

My 2 cents.

---

### Post by uNoubu8a on 2016-07-27
With the knowledge I possessed a few years ago I had attempted, and failed, several time to install and use Debian.  I tried Slackware and had no issues.  Perhaps it was simply due to me being lucky in finding the right how-to's and read.me's when needed, not sure :)

If you don't know something then anything can be difficult.  My wife doesn't care to know how to install *any* operating system.  And I am sure she may very well be caught in circles no matter how intuitive something is made.  I am sure that their will be documentation etc. available to demystify any installation and once it becomes easy, it stops being hard :p

---

### Post by ardouronerous on 2016-07-27
> **howefield said:**
> So, basically you started badly and then fell away.

If an installation is difficult, isn't simple and straightfoward, then I don't bother, I'll find something easier to install, there are other alternative out there, and apparently, that is Linus Torvald's thinking as well;

[http://www.aboutlinux.info/2007/07/interview-linus-torvalds-says-he-has.html?m=1](http://www.aboutlinux.info/2007/07/interview-linus-torvalds-says-he-has.html?m=1)
> So the only major distribution I’ve never used has actually been Debian, exactly because that has traditionally been harder to install. Which sounds kind of strange, since Debian is also considered to be the “hard-core technical” distribution, but that’s literally exactly what I personally do not want in a distro. I’ll take the nice ones with simple installers etc, because to me, that’s the whole and only point of using a distribution in the first place.

---

### Post by yoshii on 2016-07-27
I used to use Puppy Linux a lot and it *can* be simple if that particular version of Puppy Linux is made nicely.  
There are so many different variants of Puppy Linux out there, not all of them play nice anymore.  

But generally, the Puppies based upon Ubuntu are pretty easy to deal with.  
I still keep a couple of Puppies around to help with some technical stuff.

---

### Post by oldos2er on 2016-07-27
While you can install Puppy to a hard disk, it's main purpose is to be run from CD/DVD or USB, so I imagine that's why its install process is a bit of an afterthought. Damn Small is sort of the same story; more of a system rescue thing than a desktop distro.

---

### Post by mastablasta on 2016-07-28
> **oldos2er said:**
> While you can install Puppy to a hard disk, it's main purpose is to be run from CD/DVD or USB, so I imagine that's why its install process is a bit of an afterthought. Damn Small is sort of the same story; more of a system rescue thing than a desktop distro.

+ 1 and this would explain why there was not much though put into the install process.

the old chrunchbang had it doen quite well. simepl install, then script (it could be options table) to install what you want or just install all if oyu dont' know what is all about.

the new Red hat installer is also not bad.

---

