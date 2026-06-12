---
title: "upgrade to studio not working"
date: 2011-04-03
forum: Ubuntu Studio
---

### Post by srlake314 on 2011-04-03
Hey Im looking at the great post 
"Ubuntu Studio Upgrade from Ubuntu"
The full upgrade/installing packages enter the following line in the terminal:

sudo aptitude update && sudo aptitude...etc.

I get sudo: aptitude: command not found?

I cant even get passed the first instruction without getting an error.

I would love to upgrade but I'm finding it become more difficult to use Ubuntu from the start.

Help before I switch back to win 7.

---

### Post by ailo.at on 2011-04-03
aptitude is a program, and it seems it is not installed. The default command line program to handle debian packages on Ubuntu is apt.
To use apt instead of aptitude, replace "aptitude" with "apt-get".

So, "sudo apt-get update.." etc.

---

### Post by ailo.at on 2011-04-03
That wiki page is a little outdated. I did some minor editing on it just now, but it is still a little confusing. For beginners especially.

To get the Ubuntu Studio audio packages it is enough to just do:

```
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins
```While installing jackd, make sure to choose yes for realtime privilege.

Once everything is installed, make sure you - the user, is a member of audio group.

In a terminal do:

```
sudo adduser <username> audio
```Reboot.

---

### Post by srlake314 on 2011-04-04
it said that ubuntustudio-plugins wasnt found?

Not sure what that was about?

I have though done all the other commands and they seemed to work ok.

---

### Post by srlake314 on 2011-04-04
keeps asking for cd (ubuntu studio).  Wow Linux really hates me.  
Round and round I go do this, doesnt work, do this, doesnt work.

---

### Post by Pablo_F on 2011-04-04
> keeps asking for cd (ubuntu studio)

When you install software via apt (apt-get, aptitude, synaptic, software center...) you do from the repositories that are enabled in some special files (/etc/apt/sources.list and any file inside /etc/apt/sources.list.d/). These are your software sources.

For some reason, you have the CDROM enabled as a software source but, as you have internet connection, you shouldn't. You can disable it either by manually editing /etc/apt/sources.list or, easier, through Software -> Edit -> Software Sources. Then reload (or "sudo apt-get update" in the terminal).
> 
it said that ubuntustudio-plugins wasnt found?

The package is called "ubuntustudio-audio-plugins"

Synaptic Package Manager is a graphical front-end for apt-get that you can find under System -> Administration. The search tool is very useful (for example, search for "ubuntustudio"). 

Cheers, Pablo

---

### Post by srlake314 on 2011-04-04
I have done as said, and I will let you know if I have any further errors!

Thanks!

Sean

---

