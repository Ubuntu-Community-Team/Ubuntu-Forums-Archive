---
title: "Finally got a GUI setup on arch!"
date: 2009-11-02
forum: The Cafe
---

### Post by Nerd King on 2009-11-02
Christ it's hard work! I've managed quite successfully to get CLI up and running but until now no luck with GUI. Finally I've installed Gnome and KDE on there. Gotta admit gnome-vanilla is pretty damn ugly, so I guess we should appreciate how good the ubuntu guys make our version look! KDE though is a different beast, and out-of-the-box it looks gorgeous. I'm tweaking it of course, but I must admit, this little baby could find itself on my triple boot.

---

### Post by NoaHall on 2009-11-02
Hehe, how long since you started on Arch? got mine up on the first day.

---

### Post by mivo on 2009-11-04
What troubles had you run into with setting up the GUI? The [Beginner's Guide]("http://wiki.archlinux.org/index.php/Beginners_Guide") features a section dealing with the various DEs and how to install them. I still refer to it. :) The LXDE package seems a little half-baked currently, but installing Xfce4 worked beautifully out of the box (for an older laptop). With Midori, Mousepad, the calendar app and htop running, RAM usage was at 69 MB. And I hadn't even tweaked anything yet. :)

---

### Post by ZankerH on 2009-11-04
If you like KDE4 on arch, you might want to look into KDEmod (and chakra project).

---

### Post by handy on 2009-11-04
Installing Arch is hard work if:

You don't follow The Beginners Guide to the letter. (done finished)

You don't know how to follow really good instructions. (al la The Beginners Guide)

You happen to be one of the very few that have a lack of hardware support.

You happen to have some kind of unusual setup desire & you haven't looked in the Arch wiki for a solution.

You looked in the Arch wiki for a solution, found none & haven't yet searched for the answer in the Arch forum.

You haven't after all else failing posted the question in the Arch forum.

---

### Post by mikeize on 2009-11-04
dang!  from the title of the thread, I thought you meant there was like, an "install wizard" for Arch now.  :lolflag:

good luck to you!

-mikeize

---

### Post by handy on 2009-11-04
> **mikeize said:**
> dang!  from the title of the thread, I thought you meant there was like, an "install wizard" for Arch now.  :lolflag:

good luck to you!

-mikeize

The [**_Chakra project_**]("http://chakra-project.org/") may be what you are referring to/looking for?

Though most Arch users would say it is not a good way for an initiate to install Arch, as you don't learn how Arch works, the way you do, do if you install Arch the old fashioned way... :)

---

### Post by Pasdar on 2009-11-04
> **handy said:**
> The [**_Chakra project_**]("http://chakra-project.org/") may be what you are referring to/looking for?

Though most Arch users would say it is not a good way for an initiate to install Arch, as you don't learn how Arch works, the way you do, do if you install Arch the old fashioned way... :)

Does the "chakra" give the users the same installation options it does to those installing arch via terminal?

---

### Post by dragos240 on 2009-11-04
Well. I say it's pretty easy to set up an arch system. I love it. Every bit of it.

---

### Post by snowpine on 2009-11-04
> **Pasdar said:**
> Does the "chakra" give the users the same installation options it does to those installing arch via terminal?

Chakra has a simplified graphic installer similar to Ubuntu (last time I checked).

---

### Post by Eisenwinter on 2009-11-04
It's really easy.

Just download xorg, then run "Xorg -configure" as root.

This should detect your graphics card and set up X properly, which will save you some time editing the config file by yourself.

I still prefer to use the open source radeon driver, so I have to get an extra package called ati-dri, and change the driver parameters in xorg.conf.

---

### Post by Dimitriid on 2009-11-04
> **handy said:**
> Installing Arch is hard work if:

You don't follow The Beginners Guide to the letter. (done finished)

You don't know how to follow really good instructions. (al la The Beginners Guide)

You happen to be one of the very few that have a lack of hardware support.

You happen to have some kind of unusual setup desire & you haven't looked in the Arch wiki for a solution.

You looked in the Arch wiki for a solution, found none & haven't yet searched for the answer in the Arch forum.

You haven't after all else failing posted the question in the Arch forum.

Aye, there was not a single issue I couldn't resolve following this exact troubleshooting path. Maybe add the arch irc channel on freenode.

---

### Post by Muppeteer on 2009-11-04
I agree that people shouldn't install Chakra just because it's easier. I first switched to arch over a year ago, and while following the instructions, it was very easy. And now i'm comfortable with how Arch works and could probably install it without needing the manual.

---

### Post by Pasdar on 2009-11-04
For some people, like me, its not an issue of whether I can install it. I know I can, I can even install Gentoo. The question is whether it can be done fast, without too many troubles and whether the OS provides enough advantages over the one I'm using now to even consider installing it in the first place.

From the benchmarks at Phoronix I conclude its not worth my time. Spending a day installing it while there is minimal to no difference in speed between the two (Arch and Ubuntu).

---

### Post by Skripka on 2009-11-04
> **Pasdar said:**
> 
From the benchmarks at Phoronix I conclude its not worth my time. Spending a day installing it while there is minimal to no difference in speed between the two (Arch and Ubuntu).

The thing to remember is that regardless, Phoronix benchmarks of linuxes are by-and-large worthless.  Especially when they are comparing a fixed and a rolling release--that are not even using the same kernel (nevermind that all the packages are different versions).  I'm about to say the same thing in the Gentoo Vs. Ubuntu benchmarks thread....

Throw in some text blurbs, and some bar graphs and BAM you have enough column inches to keep your website looking alive and running.

---

### Post by mivo on 2009-11-04
> **Pasdar said:**
> Spending a day installing it while there is minimal to no difference in speed between the two (Arch and Ubuntu).

The time spent on the initial installation may be the same, or Arch may even take you a couple extra hours (in exchange for a cleaner, slimmer and better performing system that you know inside out), but consider that Arch is a rolling release distro, so you don't have to do this every six months like with Ubuntu (we all know how well the dist upgrade works ...).

You'll spend much more time on installing and re-installing Ubuntu over a period of time. This was one of the reasons why I switched my desktop to Arch.

---

### Post by handy on 2009-11-04
Like a broken record I say:

Arch is by far the easiest system to maintain I have come across in 24 years of being addicted to computers.

Most users find the installation process to be fun.

Without The Beginners Guide it would not be fun for most users, particularly on their first install.

On my machine, my Arch setup is much faster than Ubuntu, or any other system I have tried on it, including OS X.

---

### Post by handy on 2009-11-04
> **Pasdar said:**
> Does the "chakra" give the users the same installation options it does to those installing arch via terminal?

Read the link supplied in the post before you posted the above?

---

### Post by wojox on 2009-11-04
Chakra takes 99% of the fun out of it.

---

