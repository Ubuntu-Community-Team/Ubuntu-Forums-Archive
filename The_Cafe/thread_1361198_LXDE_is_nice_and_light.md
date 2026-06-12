---
title: "LXDE is nice and light"
date: 2009-12-21
forum: The Cafe
---

### Post by chessnerd on 2009-12-21
I was recently having issues with Xubuntu using too much memory (by my picky standards) on my old system. I killed all the services I could, removed start-up programs, got rid of unused applications, replaced the current applications with lighter weight ones, and still the system used over 150 MB of memory when idle and over 320 when browsing the web with several tabs open. If I opened a package manager on top of that my system would slow to a crawl. 

Since I was already using Xubuntu I was at a loss to figure out how to lighten the load when I remembered LXDE. I had tested it out a while back and decided to give it another go. After set-up and a reboot it used 93 MB of RAM when idle and the swap was empty. You can't get much lighter than that.

So, I decided that I would make it not just the default desktop environment, but the only one. I removed all of the XFCE and Xubuntu packages and then, voila! I had a great, lightweight, unofficial Lubuntu system.

Honestly, I thought the whole XFCE vs LXDE thing was like a fuel-efficient debate between a Ford Taurus and a Chevy Cobalt. In the end, the difference is nominal. Now I see that it's a debate between a Taurus and a Prius.

---

### Post by NoaHall on 2009-12-21
How about Arch though?

---

### Post by Psumi on 2009-12-21
What *DM Do you recommend for LXDE? WDM?

---

### Post by chessnerd on 2009-12-21
> **NoaHall said:**
> How about Arch though?

I was planning on installing Arch on that computer before college started up, but I just don't have the time to do all the research at the moment. Next summer I'll probably take the time to configure an Arch system that will actually be really light-weight and custom for just that desktop.

For now this was really more of an "I should use LXDE over XFCE" moment than an "I should use Arch over Ubuntu" moment. If/when I do set up an Arch system it will probably run LXDE.

> **Psumi said:**
> What *DM Do you recommend for LXDE? WDM?

Default is Openbox and that is what the LXDE site recommends, however it can use any WM you want. I've only been working with it for a couple of days so I haven't even thought about switching window managers.

---

### Post by NoaHall on 2009-12-21
> **chessnerd said:**
> I was planning on installing Arch on that computer before college started up, but I just don't have the time to do all the research at the moment. Next summer I'll probably take the time to configure an Arch system that will actually be really light-weight and custom for just that desktop.

For now this was really more of an "I should use LXDE over XFCE" moment than an "I should use Arch over Ubuntu" moment. If/when I do set up an Arch system it will probably run LXDE.

It's a "in" joke, don't worry :)
And I agree, LXDE is pretty nice, but I still prefer Gnome.

---

### Post by snowpine on 2009-12-21
Please don't judge Xfce based on Xubuntu. :)

[http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

---

### Post by Psumi on 2009-12-21
> **chessnerd said:**
> Default is Openbox and that is what the LXDE site recommends, however it can use any WM you want. I've only been working with it for a couple of days so I haven't even thought about switching window managers.

I said *DM, NOT WM.

*DM is the thing that you login with: GDM, SLIM, XDM, WDM, etc.

---

### Post by dragos240 on 2009-12-21
I have a slow computer that has 124 mb of ram (not even 128 ). I have XFCE on it. It's very fast, very efficient. I love it :)

---

### Post by koleoptero on 2009-12-21
If I had so few resources I'd go for an openbox only installation with a panel like tint or fbpanel.

---

### Post by chessnerd on 2009-12-21
> **snowpine said:**
> Please don't judge Xfce based on Xubuntu. :)

[http://distrowatch.com/weekly.php?issue=20090427#feature](http://distrowatch.com/weekly.php?issue=20090427#feature)

Very interesting. What is it that Xubuntu adds that makes it so much more resource hungry? 

Is it just panel stuff to make the interface look more Gnome-like or is it other usibility things that I take for granted because I have only used a non-Xubuntu XFCE version on LiveCD before?

I might just want to install XFCE (not xubuntu-desktop) and see if that works any better. I am starting to see that LXDE is a bit harder to work with in some areas. Nothing terrible, but if I can get XFCE to work as well as LXDE then I would probably switch back.

> **Psumi said:**
> I said *DM, NOT WM.

*DM is the thing that you login with: GDM, SLIM, XDM, WDM, etc.

My bad, I had to leave and read that pretty hastily. :( 
The system is still using GDM from Xubuntu, but I am probably going to switch it to SLiM when I get the time.

---

### Post by crimesaucer on 2009-12-21
> **Psumi said:**
> I said *DM, NOT WM.

*DM is the thing that you login with: GDM, SLIM, XDM, WDM, etc.

Slim is good if you want an actual login with passwords, but most people in Arch that use xfce4 just login with "startx".

```
x:5:once:/bin/su USERNAME -l -c "/bin/bash --login -c startx >/dev/null 2>&1"
```

This is added into the /etc/inittab file where the other *DMs are:

```

# Example lines for starting a login manager
#x:5:respawn:/usr/bin/xdm -nodaemon
#x:5:respawn:/usr/sbin/gdm -nodaemon
#x:5:respawn:/opt/kde/bin/kdm -nodaemon
#x:5:respawn:/usr/bin/slim >& /dev/null
x:5:once:/bin/su USERNAME -l -c "/bin/bash --login -c startx >/dev/null 2>&1"

```


..... of course "USERNAME" is your log in name.



As for Arch and xfce4, it was faster for me than xubuntu was, and the time to install it and learn it wasn't that bad (this was back in mid 2007 before the live cd and easier documentation).

---

### Post by HappyFeet on 2009-12-21
> **NoaHall said:**
> How about Arch though?

Why not do Linux From Scratch?

---

### Post by HappyFeet on 2009-12-21
> **koleoptero said:**
> If I had so few resources I'd go for an openbox only installation with a panel like tint or fbpanel.

I agree. Openbox is a good choice for low spec systems.

---

### Post by Psumi on 2009-12-22
> **crimesaucer said:**
> Slim is good if you want an actual login with passwords, but most people in Arch that use xfce4 just login with "startx".

```
x:5:once:/bin/su USERNAME -l -c "/bin/bash --login -c startx >/dev/null 2>&1"
```

This is added into the /etc/inittab file where the other *DMs are:

```

# Example lines for starting a login manager
#x:5:respawn:/usr/bin/xdm -nodaemon
#x:5:respawn:/usr/sbin/gdm -nodaemon
#x:5:respawn:/opt/kde/bin/kdm -nodaemon
#x:5:respawn:/usr/bin/slim >& /dev/null
x:5:once:/bin/su USERNAME -l -c "/bin/bash --login -c startx >/dev/null 2>&1"

```


..... of course "USERNAME" is your log in name.



As for Arch and xfce4, it was faster for me than xubuntu was, and the time to install it and learn it wasn't that bad (this was back in mid 2007 before the live cd and easier documentation).

Sorry, that's why I don't use arch.

---

### Post by XubuRoxMySox on 2009-12-22
LXDE works awesomely and has mind-bending speed on Debian Squeeze, but it's buggy as all get out with Ubuntu on my machines. In fact LXDE has been alot less buggy for me on non-Ubuntu-based distros I experimented with. I call it "*the Buntu Barrier*."

I've learned that LXDE takes much of its code from Xfce... and I wonder if, when LXDE matures, it'll be little different from Xfce.

Xubuntu Karmic flies sweetly on an older Dell that alot of kids share. I might switch it back to LXDE if an update slows it down or something. But it won't be a 'Buntu if I do. Prob'ly Debian Squeeze (my "main" OS at home). 

Keep an eye on the Lubuntu project. It has alot of promise. Hopefully they can break the Buntu Barrier.

-Robin

---

### Post by edwardp on 2009-12-22
I currently have Xubuntu installed, but have used LXDE with prior Linux distros I've used.

If I install the LXDE packages, will it cause anything else (defaults) on the system to change, e.g. file managers or something else (I know both GUI's use different file managers).  This would be installed on the K6-2 desktop system specified in the sig below.

Thanks in advance.

---

### Post by crimesaucer on 2009-12-22
I've never installed LXDE for linux. 


I have tried their file manager called PCManFM and I didn't like it. What I didn't like was that PCManFM had no trash can, thumbnails didn't show thumbnail pictures of jpg images, png images, or movie files, and the gtk looked cheap compared to thunar..... but it was very quick to open.


> **Psumi said:**
> Sorry, that's why I don't use arch.


Well, I find that editing a config file in Arch is no more complicated than editing your Ubuntu repository list. What I mean is that there's a wiki guide for both that clearly explains what needs to be uncommented, and all that's needed from the user would be to open the file while in sudo or gksu, and then do a simple "copy + paste" from the wiki guide. (basically just add that one line of code to the section where your other *DMs already were)


Then again, when I used to use xubuntu I did most of my installing from the Ubuntu wiki page: [http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)


And I also found many a page on Ubuntu Forums or some other ubuntu/debian related website that would have me in my /etc directory tweaking different conf files. This made moving to Arch (and their wiki guides) very easy for me. I don't see what most the hype is about. Arch is as easy as Ubuntu once you get to know it, and Ubuntu can be as complicated and as minimal as Arch once you really explore Ubuntu and tweak it out and customize it to your liking.


And please don't take my last couple of posts as one of those "try Arch" posts, I only mentioned that login code because I would guess that there's an easy way to configure Ubuntnu to login without a *DM for minimal Ubuntu installs running xfce4 or lxde.

---

### Post by XubuRoxMySox on 2009-12-22
> **edwardp said:**
> I currently have Xubuntu installed, but have used LXDE with prior Linux distros I've used.

If I install the LXDE packages, will it cause anything else (defaults) on the system to change, e.g. file managers or something else (I know both GUI's use different file managers). 

Short answer is yes. PCManFM would be the "default" file manager, for example, but you can change that. Nothing would prevent you from using whatever apps you wish, but LXDE works best with Openbox as the Window Manager. I've had better luck with Wicd as the network manager, but others say Gnomes Network manager is better for them. Your mileage may vary.

-Robin

---

