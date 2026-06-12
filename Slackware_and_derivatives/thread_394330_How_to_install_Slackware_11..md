---
title: "How to install Slackware 11."
date: 2007-03-26
forum: Slackware and derivatives
---

### Post by jseiser on 2007-03-26
Ive been googling all day to find out how to 100% install slackware.  I am downloading iso 1, and i see that there are alot available.  How many do i need?  I would like to download the least possible and build my system up.  I have ubuntu on a 250 HD with a 1GB swap, will the instalation detect the right partition and install to the it?  Once i put the cd in, what should i expect?  I know for a fact i dont want kde, is there a way to download and run xfce from the get go? I understand its a text based install but will it ask me questions the whole way through or do i need to tell it what i want it to do?

---

### Post by Kujen on 2007-03-26
Honestly did you even look at slackware's site? You're gonna have to put a little more effort in if you wanna run a distro like slackware. (Not trying to be a dick, but it's the truth.)

[http://www.slackware.com/install/](http://www.slackware.com/install/)
[http://www.slackware.com/config/](http://www.slackware.com/config/)

---

### Post by bonzodog on 2007-03-27
Right, Slackware has 4 disks in set.

Disc One is the core distro, with Xfce, twm, and fluxbox I think.

Disc two is **just** KDE.

Discs three and four are the package sources.

So, essentially, you only need disc one.

A good idea BEFORE you install slack is to set up and write the Partitons. I often used the DiskDrake partitioner, but you can also use GParted.

I recommend you select the Expert Install, which allows you to select individual packages, one by one. to make it slightly easier, it starts out with the recommended install packages already selected, and any vital packages are greyed out, so you cannot accidentally deselect packages that would break the system.

This way, I built a Slack system with just Windowmaker on it, and only the tools I needed. It was FAST, as I did away with a lot of boot options in the process.

---

### Post by jseiser on 2007-04-02
thanks. that the part i didnt get, i dont want kde so cd one is all i need.  I have a 30gb partition , a 200 for the /home and like 2 for a swap.  What you are saying is i need to clear the whole drive and then re-partition it for how i want slack to use it? because i want the same partition set-up so would i need to really do that?

---

### Post by bonzodog on 2007-04-03
No, if you already have the partitions set-up then you don't need to go through it again.

Just tell slackware what to use as root, swap, and /home.

---

