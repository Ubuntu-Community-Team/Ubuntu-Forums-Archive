---
title: "[SOLVED] My hypothesis of why companies won't offer n*x support. Read and leave opini"
date: 2006-05-25
forum: The Cafe
---

### Post by RavenOfOdin on 2006-05-25
Okay, I've been thinking about this for a couple of days now, and I've also been looking at numerous threads or opinions from people who raise the perhaps deserved objection that major companies must support Linux and/or release software for such in order for it to become more mainstream.  I have come to realize that just maybe this is not the fault of companies in question, but of the GPL itself. Here is why I think so:

I dealt with two companies in the past six months with regard to Linux software. These were Comcast and Linksys.  The former offers an unofficial forum for Linux users to get support - albeit that not explicitly given by Comcast, and a work-around of law -  the latter offers code for many pieces of their hardware, released under the GPL.

Please note that when I say, "I have dealt with", I mean that I use the services of both on my Linux box (High Speed Internet and Wireless.) 

The GPL in and of itself is an open-ended license, which allows for freedom on the end of the small user, but doesn't give businesses much of a choice.  It contains both a passage relating to "implied warranty" and fees. I believe the correct statement of these is as follows:

[quote=General Public License]
without even the implied warranty of merchantability and/or fitness for a particular purpose
[/quote]

[quote=General Public License]
You may charge a fee for the physical act of transferring the material, and you may at your option offer warranty protection in exchange for a fee.
[/quote]

No business which relies on a proprietary model is going to do anything that will not get them any asset in return.  Even though a bigger user base (in the case of Comcast services) or possible payment via other services (as in Linksys) is an asset, we run up against the fact that Linux/UNIX software is not at this time made and released by either company.  Therefore, the license is not binding in that regard, and the only recourse Comcast has to keep users happy is an unofficial forum - which does not run afoul of the "disclaiming all proprietary interest" section of the GPL; it is as the old saying goes "No skin off their back."

This is underscored since the only way they could make such a thing official would be to approach the software designers (in this case, Linus and the kernel development team) and ask for an agreement of exclusivity.

In two ways, they run into a brick wall:

1) To make an interface - perhaps for a network control application, or custom firewall a la Earthlink Total Access, the possibilities are endless - suitable for use with . . .say . . .KDE, they would have to approach Trolltech and/or KDE e.V. 

And I'm not even counting the possibilities of a GTK/GNOME application interface.  

In short order, they'd wind up in a cluster [censored].

2) Exclusivity defeats the spirit of the GPL.

Thus, their only recourse is to not offer official support in any way. No tech support, no email support, nothing.

Sorry if I seem a little long winded, I'm just a little tired of people saying "Why doesn't company X or Y start offering support for Linux?"

If the companies themselves don't offer software that is explicitly released under the GPL, the gesture is meaningless at best and a lawsuit waiting to happen at worst. Certainly those that actively contribute should hold to the terms (of the GPL), but where does the line between "our software" and "their invention" get crossed?

I'm not saying we couldn't use more companies jumping on the band wagon either, I'm just saying that maybe in a way which is compatible with their business model they are respecting our own.

In addition to the opinions on my (admitted rambling) idea:

What do y'all think of the GPL in its current form, and could it be worded to provide businesses with more options other than simply "going unofficial"? Does anyone that has familiarity with the LGPL know if these options are instead provided under it?

---

### Post by BoyOfDestiny on 2006-05-25
Erm, I didn't read through the whole post since the premise is flawed. Nothing is stopping companies from releasing binary non-gpl'd drivers. 

The problem is that some drivers may not work with certain distro/kernels. Thus LSB type of things are "needed"... 

Check in Ubuntu, there is fglrx and and nvidia's 3d driver. Neither are even open source, let alone GPL'd.

Frankly, if these companies would at least provide a spec, smart folks will build the drivers. They've done some amazing stuff considering reverse-enginnering etc...

If you mean software wise, they can use whatever. If they want to take and not give back, keep it closed etc. BSD is their friend. Ask MS or Apple.

As for their business model? I rather they change their's. I've had enough of phone home closed crap. Treating users like thieves, charging exorbitant amounts for non-portable software... Bah and humbug... Fine, if they want to do that they can. They just have to choose another license...

---

### Post by aysiu on 2006-05-25
I might be speaking out of my ***, so someone correct me if I'm wrong, but the GPL applies to Ubuntu and Linux, but I don't think it applies at all to software written *for* Ubuntu or Linux.

Plenty of hardware vendors provide Linux drivers... that are closed source. Plenty of software companies provide Linux ports... that are closed source.

Off the top of my head, I believe NVidia and Samsung provide closed source drivers (again, correct me if I'm wrong), and Opera, Skype, and Adobe all provide Linux ports that are closed source.

---

### Post by BoyOfDestiny on 2006-05-25
Yes Aysiu, you are right. 100%.

For the OP, you might find this of interest.

[http://www.linux-watch.com/news/NS5423433687.html](http://www.linux-watch.com/news/NS5423433687.html)

"Novell Inc. has come up with a faster way to deliver Linux hardware drivers, and driver updates, to Linux users.

With the new driver process, users can get drivers independently of kernel updates, and vendors can more easily develop and deliver device drivers for Novell's SUSE Linux Enterprise products. In addition, the new Linux process enables hardware and software vendors to provide their products' Linux drivers and driver updates to customers directly, while still being integrated with SUSE's YaST operating system setup and configuration tool."

Note: Not an endorsement on my part

One more thing, just decided to check on the GTK toolkit:

"GTK+ is free software and part of the GNU Project. However, the licensing terms for GTK+, the GNU LGPL, allow it to be used by all developers, including those developing proprietary software, without any license fees or royalties."

[http://www.gtk.org/](http://www.gtk.org/)

---

### Post by nalmeth on 2006-05-25
Perhaps the point should be more towards "why companies won't go open-source, and offer support".

As stated, there's no one stopping companies from allowing us to use their closed-source product's, except their own interest's.

---

### Post by prizrak on 2006-05-26
I think there are a few issues and in a sense the OP's premise is correct (it is not correct factually but could be correct perceptually (is that even a word?)).
1) Companies don't really understand the GPL - alot of companies do not take the time to read the GPL and find out what it's actually about they just know that it allows anyone to modify the software provided they give back to the community. It is possible that this misconception stopped many developers.

2) There are plenty of solutions for Linux - many companies create Linux hard/software, however it tends to be more on the server side because Linux on servers is huge.

3) Too insignificant of a market - when it comes to broadband providers they don't need to bother with any special Linux support because just about all of the modems have an ethernet port. There is also much less reason to offer desktop Linux support as 99% of Linux users are "geeks" (I include myself in there) and the other 1% has a "geek" to provide support. 

4) Costs - The cost of creating Linux programs tends to be higher than for Windows because VB developers are a dime a dozen. Such is not the case for other languages especially if you are talking about someone with experience. Even small applications tend to be more difficult for Linux as there is often a choice of at least GTK+ and QT involved (there are other GUI tools of course). This should be changing since Java is getting extremely popular and Mono should also help with .Net portability. 
Linux support for companies such as Comcast is more difficult as Windows only has one possible interface (well there are replacement shells but it ships with only one) as opposed to Linux that comes with at least KDE or GNOME and each distro sets them up the way they want to. This makes giving directions more difficult and of course requires a more knowledgeable person to write documentation (I bet just about anyone here could write a guide for Comcast for Windows). 

5)FOSS competition - Most FOSS users don't like the idea of non-free software (be it cost or freedom) and as a result almost anything ported to Linux is likely to be cloned by someone in the FOSS world. It is of course much easier to reverse engineer something that runs natively on the OS than something that doesn't (at least my knowledge dictates that but I could easily be wrong).

6) Risk vs Reward - Linux usage on the desktop is too small a percentage of the total market to justify dealing with all the issues mentioned above. Basically companies are not sure that their profit will cover their expense when it comes to Linux support/development.

Things ARE changing of course the LSB creates a common base to develop for and test against for companies to create software. Companies such as Canonical (Ubuntu), Novell (SuSE), Linspire, and Mandriva make it easier for end users to run Linux. Companies such as EmperorLinux and System86 (did I get that right?) make it possible to buy Linux preloaded machines that are guaranteed to work with any of the distributions that are listed as choices. However the process is slow but it is going.

---

### Post by 3rdalbum on 2006-05-27
Has Novell developed a binary driver interface for Linux?

That was going to be one of my Edgy Wishlist items. If the interface has been GPL'ed, let's get it into Ubuntu as quickly as possible. It's my contention that a few companies would start writing drivers if they didn't require the end user to recompile the kernel.

---

### Post by [S|G] on 2006-05-27
I'm going to side with  aysiu and BoyOfDestiny. Not everything for *nix is open-source and GPL. There are alternative free licenses, such as the LGPL. There are closed-source programs and drivers (nvidia drivers, java runtime environment).

I personally use not only a closed source, but also commercial software on my ubuntu desktop: Zend Studio, which is a great tool to develop PHP applications. Companies can (and do) sell linux applications: zend, vmware, cedega... those are all non-free, non-gratis stuff.

There are, however, other reasons that companies do not develop for linux. First, windows users outnumber linux users by far and companies are interested in reaching for the most users they can. You can notice that clearly if you consider skype for linux (another closed-source application). Skype, after being acquired by ebay, slowed the development of the linux version to a near-halt (not to say that they completely stopped it) because they want to make a profit. And profit is where most users are. They can afford to lose two users to keep a hundred happy.

Another reason is that people are used to windows. By people I also mean programmers. What is the proportion of windows programs released in comparison to linux programs? Nearly every one learn to program in a windows environment, and they get used to it. They have their user base, their customers. They don't want to learn to do things in a different way, and usually don't have a reason to do so if not for their own ideals. This will change as linux users increase in number. 

At last, but not least, we have a very big (and I mean VERY big) factor: Microsoft. You either play with them or you're against them. At least this seems to be their politics. They have enough power to take your bigger-than-average software house (bigger than average is needed otherwise you wouldn't even have been noticed) out of the market. If you're powerful enough, they offer you a deal. They give you competitive advantages in the OS that most people in the world uses. All this for keeping your hands out the linux and mac world. Tempting, to say the least.

The linux world is changing, however. More users are joining us every day. Here in Brazil the government is incentivating development of linux software, as well as making it easier and cheaper for computers manufactures to sell computers with a free OS installed. They pay less taxes than they would if they shipped a commercial OS on them. I believe that the linux market is still going to grow a lot.

And, more users mean more customers. So maybe soon they'll turn their eyes to linux users.

---

