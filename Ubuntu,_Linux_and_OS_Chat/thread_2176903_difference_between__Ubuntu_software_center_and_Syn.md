---
title: "difference between  Ubuntu software center and Synaptic package manager"
date: 2013-09-26
forum: Ubuntu, Linux and OS Chat
---

### Post by nashtrik on 2013-09-26
I shall be grateful if someone enlightens me with the difference between ubuntu software center and synaptic package manger,which is the better of the two and how to use the synaptic package manager. I would also like to know whether installing a software with the synaptic package manager sometomes results in either incomplete files/codecs or a lot of unnecessary ones at other times..? Thanks...):P:p:KS

---

### Post by philinux on 2013-09-26
A simple search gets this.

[http://askubuntu.com/questions/25724/what-is-the-difference-between-ubuntu-software-centre-and-synaptic-package-manag](http://askubuntu.com/questions/25724/what-is-the-difference-between-ubuntu-software-centre-and-synaptic-package-manag)

[http://ubuntuforums.org/showthread.php?t=1954120](http://ubuntuforums.org/showthread.php?t=1954120)

---

### Post by slickymaster on 2013-09-26
Both of them are frontends to the same package management system, **apt**, but Synaptic is more powerful than Software Center.

---

### Post by philinux on 2013-09-26
Also it was mooted that SC would replace synaptic. That seems to be not happening.

---

### Post by oldos2er on 2013-09-26
Synaptic has a fairly extensive help section, F1 will open [file:///usr/share/synaptic/html/index.html](file:///usr/share/synaptic/html/index.html) in your default browser.

---

### Post by ibjsb4 on 2013-09-26
Synaptic loads faster.

---

### Post by vasa1 on 2013-09-26
Anyone seen [http://ubuntu-discourse.org/t/initial-release-of-app-grid/960](http://ubuntu-discourse.org/t/initial-release-of-app-grid/960) ?

---

### Post by deadflowr on 2013-09-26
The software center installs and removes programs and packages.
Synaptic installs, removes, and maintains the packages.(updating, fixing broken packages, etc,etc)
The software center is built for simplicity.
Synaptic is a more robust build.

The software center is for ease of use, installing a package is made simple by just clicking on install and letting it do its thing, with little explanation on what is happening.
Synaptic gives you a detailed look at every step as to what will be done, such as if other packages will be installed as well, or if packages need to be removed.

Synaptic is great if want to install a lot of packages at once.
The software center is great at installing one package at a time.

The software center has great and very informative reviews.
Synaptic has very generic information on a program/package.

---

### Post by vasa1 on 2013-09-26
> **deadflowr said:**
> ...
The software center has great and very informative reviews.
....
Looks like things have improved since I last used the software center early after 12.04 was released. At that time, the "reviews" didn't appear to be of much use at all.

---

### Post by deadflowr on 2013-09-26
> **vasa1 said:**
> Looks like things have improved since I last used the software center early after 12.04 was released. At that time, the "reviews" didn't appear to be of much use at all.

Yeah, take a program like cryptkeeper.
With 12.04 it has a gsettings problem.
The first review explains what you need to do to get it to work.

I'm not sure how synaptic handles that.

And the fact that if 10 reviews say the program doesn't work, then the chances I'll waste my time trying to install it can go into other ventures.

---

### Post by philinux on 2013-09-26
Moved to ubuntu Linux and OS chat.

---

### Post by javi-brainfull on 2013-09-27
For me the main difference between Synaptic and Software Center (and the only single reason why I sometimes use the later) is that you can buy software on SC.

SC would be great for people not remotely interested in package dependencies or the inner working of package managers, as Synaptic shows a lot of packages for libraries that can be confusing... that is, it would be great if SC wasn't sooooo slow.

---

### Post by su:bhatta on 2013-09-27
> **javi-brainfull said:**
> For me the main difference between Synaptic and Software Center (and the only single reason why I sometimes use the later) is that you can buy software on SC.

SC would be great for people not remotely interested in package dependencies or the inner working of package managers, as Synaptic shows a lot of packages for libraries that can be confusing... that is, it would be great if SC wasn't sooooo slow.

 Don't know if its me or something, I use both, and have not found SC to be lacking in speed! But I've been using from May this year only. Earlier on when I tried out 10.10 Maverick & Natty, I didn't venture into Synaptic, hence can't say.

But yes, Synaptic is far more thorough and it's more useful than SC . Linux kernels can be installed and deleted with Synaptic, so its kind of more powerful too, if I may put it that way!

Also, another point of difference is, Synaptic is not only restricted to Ubuntu, but works in parent Debian also, where as SC is developed for & by Ubuntu only.

 As per Debian website: Synaptic: Synaptic is a Gtk+ based Frontend to the Debian package manager. It provides the same functionality as the aptitude utility plus more...([https://wiki.debian.org/Synaptic](https://wiki.debian.org/Synaptic))

 And, as per Launchpad: SC: You can easily find and install software, and purchase commercial software. You can rate and review software...([https://launchpad.net/software-center&#8206;](https://launchpad.net/software-center&#8206;))

---

### Post by grahammechanical on 2013-09-27
@nashtrik

So, you want to know which is better of the two? Do you know how to use Synaptic Package Manager? No? Do you know how to use the Ubuntu Software Centre? Yes? If so then the better utility is the one that you know how to use.

In one sense the software Centre has replaced Synaptic because from 12.10 onwards Synaptic is not part of the default installation of Ubuntu. To use it we have to install it through the Software Centre or the terminal.

Whether we use apt-get in a terminal, Synaptic Package Manager or Ubuntu Software Centre the results are pretty much the same. If there is a problem with incomplete files/codecs or a lot of unnecessary ones, as you put it, then the same problem will be there in all three methods of installing/removing stuff.

There are times when it is advantageous to use either of the three methods but for ordinary users the Software Centre and the Update Manager should be sufficient. That reminds me. Synaptic combines updating the OS with installing software.

Regards.

---

### Post by stalkingwolf on 2013-09-27
I have always found SC to be slow. and multiple installs even slower. I have never had synaptic install updates with software i was installing. maybe i just didnt notice.

---

### Post by deadflowr on 2013-09-27
> [COLOR=#000000]Also, another point of difference is, Synaptic is not only restricted to Ubuntu, but works in parent Debian also, where as SC is developed for & by Ubuntu only.[/COLOR]

Software center is available in debian.
[http://packages.debian.org/sid/software-center](http://packages.debian.org/sid/software-center)

Upstream is not a one-way street all the time.

---

### Post by su:bhatta on 2013-09-27
> **deadflowr said:**
> Software center is available in debian.
[http://packages.debian.org/sid/software-center](http://packages.debian.org/sid/software-center)

Upstream is not a one-way street all the time.

I'm glad you shared that one ! I wasn't aware !

Maybe because it's available in sid, and i use wheezy!

 P.S. : Its there in Wheezy also, just didn't bother with it & used Synaptic in Debian always!
This is a nice read: [http://askubuntu.com/questions/193616/why-is-the-software-center-in-the-debian-repositories](http://askubuntu.com/questions/193616/why-is-the-software-center-in-the-debian-repositories)

---

### Post by Copper Bezel on 2013-09-28
> **ibjsb4 said:**
> Synaptic loads faster.
As much as I really do think the switch to a simpler and more broadly informative front-end with a lot of discoverability as the default for routine package installation was an entirely sensible and good one, this post made me spittake, and I thank you. = )

---

