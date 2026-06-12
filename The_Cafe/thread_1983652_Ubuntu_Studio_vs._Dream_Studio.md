---
title: "Ubuntu Studio vs. Dream Studio"
date: 2012-05-20
forum: The Cafe
---

### Post by Uncle Spellbinder on 2012-05-20
[Ubuntu Studio](http://ubuntustudio.org/) and [Dream Studio](http://dream.dickmacinnis.com/forum/node/2201) seem quite similar. 

Aside from the 3 obvious differences (*XFCE for Ubuntu Studio, Unity for Dream Studio and the simi-rolling release schedule for Dream Studio*), are there any real differences between the two distros? 

Any advantages of one over the other?

---

### Post by CaptainMark on 2012-05-22
I was wondering the same thing, all I can tell from distrowatch and websites is that dreams logo looks slightly better :P

then again theyre are both just ubuntu with some extra multimedia software installed, neither are exactly ground breaking

---

### Post by Rodney9 on 2012-05-22
Ubuntu Studio have a lowlatency kernel installed by default

---

### Post by forrestcupp on 2012-05-22
It looks to me like Ubuntu Studio is focused on audio work, and Dream Studio focuses on a lot of types of artistic work. I think "Studio" is the main thing that is similar, and that they have different visions.

> **Rodney9 said:**
> Ubuntu Studio have a lowlatency kernel installed by default

I wondered about that.

---

### Post by grahammechanical on 2012-05-22
Someone must be doing something right. We started with Linux distributions and now we are getting Ubuntu distributions. The poll on their home page made me laugh.

"What would you like to see next from Dream Studio?"

Answers? A KDE version and a XFCE version.

Which goes completely against this stated policy:

> To this end we aim to stay as close to stock Ubuntu as possible.

Regards.

---

### Post by codingman on 2012-05-22
I don't exactly see the point in either, you can do the uses of both with plain ubuntu, only you would need to install the multimedia stuff on it.

---

### Post by CaptainMark on 2012-05-22
agreed, i love to see diversity and innovation in the linux world, I dont see the point in people who just slap some of their favourite apps onto a standard install and hey presto johnbuntu stevebuntu, whogivesashitbuntu

---

### Post by Lucradia on 2012-05-23
Dream Studio looks too much like a MacOS Mimic >_>

[http://dream.dickmacinnis.com/forum/sites/default/files/images/intro%20screen.png](http://dream.dickmacinnis.com/forum/sites/default/files/images/intro%20screen.png)

^ Without white windows.

---

### Post by forrestcupp on 2012-05-23
I don't know about Dream Studio, but Ubuntu Studio is a lot more than slapping some of their favorite apps into a distro. They also set up the system for you with things that are necessary for recording audio, like a realtime kernel, configuring Jack, etc. That's the kind of thing a sound engineer needs, but doesn't want to have to worry about doing manually. Ubuntu Studio does all of the setting up for you so you can just install it and start doing your job.

I haven't looked into it a lot, but Dream Studio doesn't seem quite as necessary. It *does* give you Gimp 2.8 without you having to set up PPAs, though.

---

### Post by macinnisrr on 2012-06-29
Dream Studio also has a lowlatency kernel by default, although it is also a PAE kernel (supports x86 systems with up to 64GB of RAM). Both include many lowlevel tweaks (like realtime audio permissions) that aren't easy for newbies (as most creative folks are) to do themselves.

It's for these reasons that both distributions exist apart from stock Ubuntu.

Dream Studio also addresses several issues that content creators have with Ubuntu proper (and Ubuntu Studio), aside from mere package selection. Namely:

1. The Ubuntu community knows that non-tech people find words like "GNU/Linux" strange and meaningless. That's why it's not listed in their name like thousands of other distros. Dream Studio agrees and thinks "Ubuntu" is just as weird. Especially when attempting to appeal to creative types, marketing is huge. Look at Apple.

2. Ubuntu's release cycle is good for them. With LTS releases, enterprise users get the stability they need to get things done, and with 6 month regular releases, developers and casual users get to test often - helping the community as a whole sort out bugs, which is also to the advantage of LTS users (as they get newer software on upgrade which has also been widely tested). For creative users, we want the newest features in our software (video and audio effects, plugins, and updates to major software suites like GIMP and Ardour) with a stable base. In Ubuntu, LTS releases don't backport enough, and rarely add new projects, and regular releases often break things like video hardware and user interfaces on upgrade - not to mention that upgrading your entire system every 6 months just to be able to use a couple new features is a supreme pain in the ***. Dream Studio addresses both issues by being a semi-rolling release.

3. Cinelerra, although ugly, is the most professional video editing app for Linux. Unfortunately it hasn't been available in any of the Ubuntu repos (not even restricted) for at least the last 6 releases. It's supposedly due to licensing, though I don't really understand what the exact issue is, and it's in debian-multimedia. Dream Studio includes Cinelerra, and many, many other packages that aren't in the stock Ubuntu repos for various reasons.

Ubuntu Studio is a fantastic distribution which collects packages from the stock Ubuntu repositories, tweaks the base system so users don't need to much around with the command line, and is released at the same time as Ubuntu. It has the advantage of being officially supported by Ubuntu.

Dream Studio is a highly-polished (read: marketable) software suite designed specifically for multimedia content creation. Dream Studio is built on Ubuntu due to its reliablity (especially in LTS releases), ease of customization, large support base, extensive third-party software support, focus on usability and heavy development. To this base is added multimedia specific system tweaks by default, more packages than are (or in some cases can be) included in Ubuntu's repositories, newer versions of multimedia packages than those in Ubuntu's repos (officially released stable versions according to the developer are often included in Dream Studio before they are even in Ubuntu testing versions), and pretty branding. All this is default and requires no setup on the part of end users.

While it's correct that you can use Ubuntu and may not need either Dream Studio or Ubuntu Studio. In the case of Ubuntu Studio, the audio tweaks (lowlatency kernel, rt permissions, etc.) alone would take you 30 mins. to set up on a stock Ubuntu system, and then you'd need to install all the packages you wanted to use for actually making noise on top of that. To create Dream Studio you'd need to do the above and add the extra repositories (many are the stable release repositories for the application teams themselves - meaning they are stable and get same day releases in both source code and Dream Studio).

Not only that, but both projects save the user the time of downloading a bunch of similar apps just to find out which works the best. Saying that either is pointless is like saying that Ubuntu is pointless because you *could* just download gentoo and compile all the same programs yourself, or to be less hyperbolic, you could just download Debian, add the Ubuntu repos, and install all the same software. Sure you could, but why when you can just use Ubuntu?

Why use Ubuntu when you can just use Ubuntu Studio?
Why use Ubuntu Studio when you can just use Dream Studio?

DickMacInnis (I can't put my first name here apparently, it's a naughty word)

P.S. Dream Studio's poll is part of a skunkworks project. Desktops other than Unity are entirely unsupported and are only for testing.

---

### Post by Lucradia on 2012-06-29
> **macinnisrr said:**
> P.S. Dream Studio's poll is part of a skunkworks project. Desktops other than Unity are entirely unsupported and are only for testing.

I really dislike Unity though :| (Yes, I did spend time with it for over a week, and I hated every bit of it.)

---

### Post by jack_spratt on 2012-07-24
> The Ubuntu community knows that non-tech people find words like "GNU/Linux" strange and meaningless

Non-tech people also find the concept of digital freedom strange and meaningless, but that doesn't mean it's any less vital to their lives, or that they shouldn't learn what it means in order to stand up and support it.

However I take your point about the importance of marketing. It is extremely important. Just don't throw out the baby with the bathwater please.

I'm glad both distros exist, there are differences between them, choice and variety are good for the users and freedom, I suggest people try them out before stating one or other or both are redundant.

Also props to Dream Studio for interacting with the community in this thread :)

---

### Post by Artemis3 on 2012-07-25
> **macinnisrr said:**
> 3. Cinelerra, although ugly, is the most professional video editing app for Linux. Unfortunately it hasn't been available in any of the Ubuntu repos (not even restricted) for at least the last 6 releases. It's supposedly due to licensing, though I don't really understand what the exact issue is, and it's in debian-multimedia.

[http://ubuntuforums.org/showthread.php?t=1619131](http://ubuntuforums.org/showthread.php?t=1619131)

debian-multimedia is not an official Debian repository, and is no different to adding the cinelerra ppa. As a matter of fact, for the third time, they changed their domain, it is now "deb-multimedia" and people must update their sources.list (again).

Against Dream Studio the first issue is, of course, Unity; or more precisely, the bloated gnome3 running behind. Dream Studio being separate will also lag behind ubuntu(studio) releases, just like Mint. You can instead keep an Ubuntu LTS with a few updated apps just fine, aside from backports there are PPAs (like Cinelerra's), to avoid endangering your production machine every few months.

Please do not underestimate the amount of memory and cpu/gpu wasted by the use of gnome3/kde4, it gets in the way of production. With xfce, compositing can be disabled and that is that.

---

### Post by bobguerra on 2012-12-17
> **CaptainMark said:**
> agreed, i love to see diversity and innovation in the linux world, I dont see the point in people who just slap some of their favourite apps onto a standard install and hey presto johnbuntu stevebuntu, whogivesashitbuntu

[COLOR=Sienna]***:guitar:[SIZE=3]I like using Bobuntu[/SIZE]***[/COLOR]:guitar:

---

