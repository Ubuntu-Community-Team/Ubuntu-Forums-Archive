---
title: "Why is ubuntu tweak not installed by default?"
date: 2011-08-09
forum: The Cafe
---

### Post by josephellengar on 2011-08-09
Yeah, what the title says. Ubuntu tweak should really be installed by default. It is far superior to computer janitor and most of those packages that Canonical uses for similar functionality.

---

### Post by idoitprone on 2011-08-09
> **josephellengar said:**
> Yeah, what the title says. Ubuntu tweak should really be installed by default. It is far superior to computer janitor and most of those packages that Canonical uses for similar functionality.


ubuntu tweak is not officially supported by canonical i believe. I know it sometimes breaks the systems by removing necessary files sometimes

---

### Post by Bart92 on 2011-08-09
> **idoitprone said:**
> ubuntu tweak is not officially supported by canonical i believe. I know it sometimes breaks the systems by removing necessary files sometimes

Jep

---

### Post by josephellengar on 2011-08-09
> **Bart92 said:**
> Jep

Oh, I guess I'll stop using it then.

---

### Post by Duncan Williams on 2011-08-09
more likely to break other distros using ubuntu 11.04 as base.
Should be fine in straight natty install.

---

### Post by nomko on 2011-08-09
Ubuntu Tweaks is not a tool for starters or so called newbies due to the fact that many settings can be changed which is very harmful to a smooth running system. If the user doesn't have the proper knowlegde the user can damage his Ubuntu setup. Another reason for not using Ubuntu Tweak is the fact that it allows the user to add PPA's which cannot be checked by the right management system of Linux (Ubuntu). Therefore it is possible to add PPA's which can contain harmfull software or allows the user to install software which can corrupt Ubuntu. 
 
My advise: if it is not needed, don't install it. Most of the options Ubuntu tweak offers can also be found in Gconf-editor or by tools which can be found in the correct (Ubuntu) rtepository.
 
And i totally agree with idoitprone, Ubuntu Tweak is prone to mess up a whole system.

---

### Post by Duncan Williams on 2011-08-11
personally I wouldn't use it.
bleachbit your sys once a week instead...

---

### Post by nomko on 2011-08-11
> **Duncan Williams said:**
> 
bleachbit your sys once a week instead...
 
Bleachbit is a tool which can make your system corrupt by removing more files than needed. I have bad experiences with bleachbit.
 
If you want to clean your system (and what can there be cleaned under Linux compared to Windows???), use these commands:
 
```
sudo apt-get autoclean
```
 
```
sudo apt-get autoremove
```
 
And another tool which can be trusted is deborphan (with the GUI interface tool). Deborphan removes unneeded files such as library files. Never had any bad experiences with using deborphan.

---

### Post by Duncan Williams on 2011-08-12
Well each to there own.
I have personally been using bleachbit in normal and administrative mode. probably 3-4 times a week for the last 6 months.
It does a lot more than delete a few files and I am yet to have a problem.
It definitely assists in privacy matters as in removing most details from your general and online use.
Also frees up usually between 50mb and 1.5gig.

I was a bit worried at first but tend to trust it now.

But I would not like someone to use it and break their installation.
So `use with care' and `be aware'

---

### Post by Segofam on 2011-08-12
> **nomko said:**
> Ubuntu Tweaks is not a tool for starters or so called newbies due to the fact that many settings can be changed which is very harmful to a smooth running system...Ubuntu Tweak is prone to mess up a whole system.

I use it to get rid of those annoying extra choices you get when you go to pick which OS you want to boot into. It is very good for that, but if you mess with it too much, it will wreak havoc on your system..I know :-/

> **nomko said:**
> If you want to clean your system (and what can there be cleaned under Linux compared to Windows???), use these commands:
 
```
sudo apt-get autoclean
```
 
```
sudo apt-get autoremove
```
 
And another tool which can be trusted is deborphan (with the GUI interface tool). Deborphan removes unneeded files such as library files. Never had any bad experiences with using deborphan.

Do you have any commands for deleting unused boot choices in Grub?

Scott.

---

### Post by westie457 on 2011-08-12
> **Segofam said:**
> 

Do you have any commands for deleting unused boot choices in Grub?

Scott.

Hello, by unused boot choices do you mean the older kernels (something like 2.6.22-35)?

Do not know the command to use however it can be done with Synaptic.
All you do is search for 'linux-headers' and mark the ones you do not want for complete removal and click apply. As they are removed Grub is automatically updated to reflect the changes.

Having said all that it is a good idea to have one earlier kernel in the list as a fall-back boot option in case an update causes problems.

---

### Post by nomko on 2011-08-12
> 
Do you have any commands for deleting unused boot choices in Grub?

Scott.

If you want to use Ubuntu tweak for it, be my guest! But don't start complaining when Ubuntu tweak messed up your system just by installing it!

---

### Post by nomko on 2011-08-12
> **westie457 said:**
> Do not know the command to use however it can be done with Synaptic.

It think it is this command:
```
sudo update-grub 
```

---

### Post by Elfy on 2011-08-12
> **nomko said:**
> It think it is this command:
```
sudo update-grub 
```

This would just update grub with the existing kernels - you need to remove them, removing them will also cause update-grub to run. 

As to the original post - why should ubuntu tweak be installed by default ... I've never used it, nor needed to. 

Much the same as myriad other apps that aren't installed by default :)

---

### Post by josephellengar on 2011-08-12
> **westie457 said:**
> Hello, by unused boot choices do you mean the older kernels (something like 2.6.22-35)?

Do not know the command to use however it can be done with Synaptic.
All you do is search for 'linux-headers' and mark the ones you do not want for complete removal and click apply. As they are removed Grub is automatically updated to reflect the changes.

Having said all that it is a good idea to have one earlier kernel in the list as a fall-back boot option in case an update causes problems.

If you do mean older kernels, I wouldn't remove them. I always keep a few old kernels on my system because I actually have had to use them on occasion when my system refused to boot for whatever reason.

---

### Post by Elfy on 2011-08-12
You can set grub2 to only show a specific number of kernels - [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

Look for the limiting entries 

or look into grub customiser.

Though with the latest grub the older kernels are all in a sub-menu and only visible if you go into that menu.

---

### Post by Nylo on 2011-09-22
I have been using Ubuntu Tweak since it came out and had never had an issue.  In fact this is the first time I have heard of this.  I’m currently managing three computers using Linux and not one issue.

---

### Post by uRock on 2011-09-22
I wouldn't want it installed by default. This sounds more like a topic for [http://brainstorm.ubuntu.com/](http://brainstorm.ubuntu.com/)

---

