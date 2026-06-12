---
title: "Ubuntu GNOME vs Debian GNOME"
date: 2017-08-07
forum: Ubuntu, Linux and OS Chat
---

### Post by Gottier on 2017-08-07
Doesn't have to be GNOME necessarily, but wondering if there is a comprehensive list of the differences between Debian and Ubuntu. I know Ubuntu is some sort of derivative of Debian, but what are the major/minor differences?

I've played around with a quite a few distros in Virtualbox, but I always liked Ubuntu for Unity. Now that Unity is going away (or is it), makes me wonder what makes Ubuntu special.

1) I am a web dev, and use LAMP, git, node, firefox, chrome, sublime text 2, filezilla, dropbox, sqlyog thru wine, veracrypt, windows thru virtualbox, autossh, android studio, etc.
2) I don't really play games, listen to music, horse around, etc.
3) I am familiar with apt (apt-get), and it's easy. I'm not a novice to the command line, but certainly not a bash guru or anything.
4) I really wish Ubuntu was staying with Unity. I like it the best.
5) Been using Ubuntu on and off since 2006. For the last 2 or 3 years it's my only operating system. It's unfortunate to think that the desktop environment meant so much to me ... but it does. I don't really like GNOME. Xubuntu is nice for my laptop, but kind of clunky for my desktop. LXDE is like Windows 98 (ugly to me). Not much experience with KDE, budgie. Cinnamon is really hard to see for my old eyes. 

What to do?

---

### Post by Bucky Ball on 2017-08-07
I doubt Unity is going anywhere. A lot of people like it so no doubt it will survive as a desktop environment you can install like any other. I also don't doubt that there will be a 'spin' of Ubuntu which uses Unity, if anyone is bothered to get it together and produce one.

Ubuntu is no longer using Unity as it's default desktop environment. That is all. It won't go up in a puff of smoke, never to be seen again. Too popular for that. People are already discussing what will happen and what they might make happen with Ubuntu and Unity if you have a dig around. ;)

---

### Post by sonicwind on 2017-08-07
I recently bookmarked this article: [http://www.datamation.com/open-source/debian-vs.-ubuntu.html](http://www.datamation.com/open-source/debian-vs.-ubuntu.html)

---

### Post by Gottier on 2017-08-07
> **sonicwind said:**
> I recently bookmarked this article: [http://www.datamation.com/open-source/debian-vs.-ubuntu.html](http://www.datamation.com/open-source/debian-vs.-ubuntu.html)

I had seen that article, but it's rather vague. Seems impossible that those are the only differences, and if they are, that's pretty sad. The article links to a repo where Unity is supposedly forked, but commit activity is almost non-existent. There's must be somebody doing an official Unity flavor, but I haven't found the info. 

Since looking at that article, I went over and took a look at the Debian installation process on youtube. Where Ubuntu has different flavors, Debian offers to select desktops during installation. There's no Unity though.

---

### Post by vocx on 2017-08-07
> **sonicwind said:**
> I recently bookmarked this article: [http://www.datamation.com/open-source/debian-vs.-ubuntu.html](http://www.datamation.com/open-source/debian-vs.-ubuntu.html)
That's a nice read.

I will rehash an old saying: Ubuntu is an ancient African word that means "I can't configure Debian".

I've never used Debian but I am one of those that generally has the idea that "Debian is for experts, and Ubuntu is for beginners". I honestly don't know if this applies today, but my gut feeling is that it still does. Ubuntu is where you go to get your first taste of Linux and free software. Debian is where you go when you consider yourself a hacker, and ready to carry the banner of free software.

Obviously, "Ubuntu" does not mean what I stated above. It does mean something in a few African languages, but it's about community. [https://en.wikipedia.org/wiki/Ubuntu_(philosophy)](https://en.wikipedia.org/wiki/Ubuntu_(philosophy))

I don't know if there is an exhaustive list of differences between the two, but I feel the point is moot. It's more about the environment surrounding the users. Debian is meant for more advanced users so they should be able to research and solve issues by themselves, while Ubuntu holds your hand a bit more, giving you things like proprietary drivers nicely packaged and ready to use. Also, Debian is a bit more community driven, while Ubuntu, being a product of Canonical, is developed in a more centralized fashion. Debian puts a lot of emphasis on the spirit of free software, while Canonical may use their dictator powers to stir Ubuntu in the direction they feel best.

> **Gottier said:**
> Doesn't have to be GNOME necessarily, but wondering if there is a comprehensive list of the differences between Debian and Ubuntu. I know Ubuntu is some sort of derivative of Debian, but what are the major/minor differences?

I've played around with a quite a few distros in Virtualbox, but I always liked Ubuntu for Unity. Now that Unity is going away (or is it), makes me wonder what makes Ubuntu special.

1) I am a web dev,...

What to do?

I find it hilarious that you basically chose Ubuntu for Unity, given it was heavily criticized for it. Honestly, if your main use is web development, I believe Debian and Ubuntu should basically behave the same. Maybe one program will not be installed by default here and there, and a configuration file is in a different location here and there, but for the most part everything will be the same.

A big difference that I could note is about the release schedule. Debian is this big monolitic environment, where they release one version, say Jessie, and it will live for many years. Packages will be updated, but after many years, you will nominally still use that version of Debian. Ubuntu, on the other hand, has the scheduled releases, that make a snapshot of the programs and kernel at one point, and keep that version for some time, and then you get a new version and so on. So, in my mind Ubuntu is more structured, it has these milestones that more or less define the environment. The LTS versions are really good in this aspect, as they give confidence to users.

So, in my mind Ubuntu is just a more structured and more user friendly version of Debian, but they both behave essentially the same.

---

### Post by cariboo on 2017-08-07
I use Rassbian, which is a variant of Debian for the Raspberry PI, there is a gui, but I've never used it. I run everything from the command line. If you are an experienced Ubuntu user, you should have no problem running Debian.

---

### Post by vocx on 2017-08-07
> **Gottier said:**
> **I had seen that article, but it's rather vague. Seems impossible that those are the only differences, and if they are, that's pretty sad**. The article links to a repo where Unity is supposedly forked, but commit activity is almost non-existent. There's must be somebody doing an official Unity flavor, but I haven't found the info...
Umm, what? Are you saying you were expecting a big difference between Debian and Ubuntu? There isn't, that's the point.

In my mind Unity and Gnome are just skins, the internals are the same. When Ubuntu transitions back to Gnome in 18.04, I think the Unity desktop will still be available in the normal Ubuntu repositories. I don't think it will simply evaporate without trace. So, you should probably be able to install it again. Now, about maintenance, that's a different story. It is free software. If a group of users cares enough about that piece of software, they will just take it and continue development and maintenance.

Remember, Unity is in fact based on Gnome 3. Maybe you don't like Gnome 3 now, but maybe with enough tweaks it could eventually work just like Unity works now.

> **cariboo said:**
> I use Rassbian, which is a variant of Debian for the Raspberry PI, there is a gui, but I've never used it. I run everything from the command line. If you are an experienced Ubuntu user, you should have no problem running Debian.
You are right. I also use Raspbian. I guess that means I use Debian as well. I think it's the LXDE environment that is installed; I'm not even sure. There are no major differences with Ubuntu. The apt system works the same, the directories and configuration files are where they are supposed to be. "If you are an experienced Ubuntu user, you should have no problem running Debian."

Now I wonder about the major differences between Raspbian and actual Debian. Mmm.

---

### Post by cariboo on 2017-08-07
> **vocx said:**
> Now I wonder about the major differences between Raspbian and actual Debian. Mmm.

One big one I've found so far is setting a static ip address. On the raspberry pi it has to be set in /etc/dhcpcd.conf. Setting it in /etc/netwoek/interfaces just doesn't work.

---

