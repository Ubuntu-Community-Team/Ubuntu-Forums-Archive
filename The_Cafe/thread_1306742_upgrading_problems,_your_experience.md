---
title: "upgrading problems, your experience"
date: 2009-10-30
forum: The Cafe
---

### Post by renebs on 2009-10-30
Hi,

I posted, here on the Community Cafe this [thread]("http://ubuntuforums.org/showthread.php?p=8188925") a day ago. It basically stated the typical problem one might face when he/she upgrade/install a new (ubuntu) distro version (btw the thread was moved to Installation/Upgrade, I believe it's not supposed to be there, I haven't had a problem installing ubuntu 9.10)

So, I want to list here what kind of problem I faced and others might as well and, hopefully, get feedback on how *you* would manage to solve this kind of problem (it all boils down to minimizing the time required to have your system running as before). 

When considering to move to a new distro, it has been quite  useful to me to have:
1) Backup 
2) /home on different partition
3) Install the new distro on a different partition (if you have the space) instead of updating 
--- why? If something doesn't work the way supposed to, you will still have your working environment within your old distro installation

I may or may not do:
4) Create NEW username for your new distro.
--- Why? many config folders/files (most of the time starting with . and written to $HOME) are Software version specific and may start giving random errors that may be a pain to find out why.

OK. Now, I would like to ask about 4) above. Instead of following that rule, I used the same username I had with 8.10 when upgrading to 9.10 and, therefore all my configuration files where used in 9.10.

BUT, when I go to use F-spot, for example, my database and configuration files are not being read. Also beagle's database had to be reconfigured. And other problems as well. 
*With Compiz: I had to reconfigure all the corner/displays shortcuts I like to use on Gcompiz, that in itself takes about 10min, until I remember the correct plugin I used and so forth).
*With gpodder, my config rss feeds where lost as well. 

So my question is, if you do a fresh install how do you keep your configuration files organized so that you don't have to use a lot of time to make your new distro running the way it's supposed to? How do you do it?

---

### Post by grizato on 2009-10-30
Here's a method I found on the forum:

*Copy **all** the files in your /home/(user)/ directory onto a flash drive or something.

*Get Karmic, same username(prefferably the same password) and then, when It's all up and running either:
  *Boot into another OS(puppy linux is what I use for those kida       stuff) and swap your old files with the new ones and then reboot int Karmic.
  *Manually do it inside the OS(not recommended but may work).

I think that would just about do you. I did the [same thing once ]("http://tecky-junk.blogspot.com/2009/09/ubuntu-cpu-bug-with-fix.html")the other way around so I think this may work.:p

---

### Post by renebs on 2009-10-30
I kinda of done this, without knowing it. Instead of login in inside GDM (graphical interface) I did login over the terminal (by pressing CTRL+ALT+F2), moved my DOT folders to another place. Logged in (over the GDM) and later moved the dot folder back to $HOME root. 

Thanks for the advice anyway. My big regret is the F-spot database... 

> **grizato said:**
> Here's a method I found on the forum:

*Copy **all** the files in your /home/(user)/ directory onto a flash drive or something.

*Get Karmic, same username(prefferably the same password) and then, when It's all up and running either:
  *Boot into another OS(puppy linux is what I use for those kida       stuff) and swap your old files with the new ones and then reboot int Karmic.
  *Manually do it inside the OS(not recommended but may work).

I think that would just about do you. I did the [same thing once ]("http://tecky-junk.blogspot.com/2009/09/ubuntu-cpu-bug-with-fix.html")the other way around so I think this may work.:p

---

### Post by Hyporeal on 2009-10-30
I think the location of f-spot config files was moved in Karmic.

Jaunty: ~/.gnome2/f-spot/
Karmic: ~/.config/f-spot/

Maybe this is the problem. I performed an upgrade (not a fresh install), which migrated my f-spot files flawlessly.

---

### Post by renebs on 2009-11-02
> **Hyporeal said:**
> I think the location of f-spot config files was moved in Karmic.

Jaunty: ~/.gnome2/f-spot/
Karmic: ~/.config/f-spot/

Maybe this is the problem. I performed an upgrade (not a fresh install), which migrated my f-spot files flawlessly.

That worked. Thanks.

---

