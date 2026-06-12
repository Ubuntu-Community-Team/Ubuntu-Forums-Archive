---
title: "gksudo / kdesu vs. sudo - what can be done?"
date: 2006-04-25
forum: The Cafe
---

### Post by gingermark on 2006-04-25
I would be shocked if this hasn't been discussed before, so my apologies, but I couldn't dig up much searching. If indeed this has been chewed over many times then a link to the relevent thread(s) would be most appreciated.

On the Ubuntu Wiki there is a page called [RootSudo](https://wiki.ubuntu.com/RootSudo), and one paragraph of this page reads:
> **NEVER** use sudo to start graphical programs. You should always use gksudo or kdesu to run such programs, otherwise new login attempts may fail.
I would be interested to know why this can happen, but that's not the point of this thread. 

It seems to me that in almost every guide one will come across ```
sudo gedit something
```
And sure, we know that in the case of gedit, sudo works. But surely gksudo should be used, if only to encourage it's use for other graphical applications. As a Kubuntu user, I see this regularly when someone will instruct another user to ```
sudo kate something
``` instead of ```
kdesu kate something
```
I myself have been a victim of the .ICEauthority login problem, and I can vouch that "sudo kate" is a bad idea.

This is such a prevalent problem through the guides, and on these forums, and I think it all comes back to "sudo gedit". It leads to high-profile members of the community giving out commands that could cause other problems for new users, or at the very least further encourage the misuse of sudo with other graphical applications.

Am I wide of the mark? Do you think this is a minor issue, or not really one at all? Have I misunderstood the issue? And assuming I've got it right, surely this is something that needs correcting on a forum-wide scale?

---

### Post by aysiu on 2006-04-25
It's generally a good idea to use *gksudo* or *kdesu* for graphical applications, but I've never seen adverse permissions side effects from *sudo gedit*.

*sudo kate*, however, is deadly, and often just plain doesn't work.

---

### Post by gingermark on 2006-04-25
[QUOTE=aysiu]It's generally a good idea to use *gksudo* or *kdesu* for graphical applications, but I've never seen adverse permissions side effects from *sudo gedit*.
*sudo kate*, however, is deadly, and often just plain doesn't work.[/QUOTE]
I'm not saying that 'sudo gedit' causes a permissions problem, but it encourages users to use sudo with other graphical apps that can cause problems.

---

### Post by aysiu on 2006-04-25
[QUOTE=gingermark]I'm not saying that 'sudo gedit' causes a permissions problem, but it encourages users to use sudo with other graphical apps that can cause problems.[/QUOTE] My honest opinion--people (including me) say ```
sudo gedit
``` because they're just too lazy to type that extra *gk* in front. I'll try to be better about it in the future myself. I can't speak for others.

It's the same mistake I make with general terminal commands. I often say, "Type this" instead of "Copy and paste this."

---

### Post by gingermark on 2006-04-25
I'm not having a go at you aysiu :) 

But I think this is a major issue. When editing a sources.list file (for example) if you are told to
```
gksudo gedit /etc/apt/sources.list
sudo apt-get update
```
then I think people will pick up quite quickly that one is for graphical apps, and one is for the command line.

But if sudo is used for both there is no chance for a new user to pick up the distinction - or even be aware the gksudo command exists. And I think this can lead to login problems further down the line for new users.

But seriously, am I making too much of this? :)

---

### Post by aysiu on 2006-04-25
[QUOTE=gingermark]
But seriously, am I making too much of this? :)[/QUOTE] In a sense, yes; in a sense, no.

Yes, in that there aren't that many people with .ICEauthority files screwed up.

No, in that it's not *that* much trouble to correct, and if you can correct it, why not?

---

### Post by aysiu on 2006-06-24
I've changed my mind since two months ago.

I'm now with gingermark on this.

It's good to send a consistent message to users: *gksudo* and *kdesu* with graphical applications.

If you don't get into that habit, you could easily end up like [this](http://www.ubuntuforums.org/showthread.php?t=181867) or [this](http://archlinux.org/pipermail/arch/2006-February/008674.html).

---

### Post by Kvark on 2006-06-24
Sudo can **** up your account and make it impossible to log in? Isn't that a very serious bug?!

And if it isn't a bug, how could a problem this serious possibly be considered normal?

---

### Post by aysiu on 2006-06-24
[QUOTE=Kvark]Sudo can **** up your account and make it impossible to log in? Isn't that a very serious bug?!

And if it isn't a bug, how could a problem this serious possibly be considered normal?[/QUOTE]
Kvark, it's only if you use *sudo* with graphical applications.

**Bad** (sudo with graphical applications): ```
sudo kwifimanager
``` ```
sudo firefox
``` **Good** (graphical sudo with graphical applications): ```
kdesu kwifimanager
``` ```
gksudo firefox
```

**Also good** (sudo with terminal applications): ```
sudo aptitude update
``` ```
sudo nano /etc/X11/xorg.conf
``` Of course, it's not a good idea to run Firefox as *sudo*, but that's for security access purposes, not functional security.

---

### Post by Kvark on 2006-06-24
[QUOTE=aysiu]Kvark, it's only if you use *sudo* with graphical applications.[/QUOTE]
Yes I understood that the risk is only there with graphical applications. But that it only happens in some cases is no excuse to have a serious bug in sudo.

---

### Post by aysiu on 2006-06-24
[QUOTE=Kvark]Yes I understood that the risk is only there with graphical applications. But that it only happens in some cases is no excuse to have a serious bug in sudo.[/QUOTE]
But that's not a bug, really. The only "bug" is people telling other people to *sudo graphicalapp* all the time instead of *kdesu graphicalapp* or *gksudo graphicalapp*.

That's like saying it's a bug that changing ownership of the entire filesystem renders it useless... well, you're not supposed to change the ownership of the entire filesystem.

Likewise, you're not supposed to use *sudo* with graphical applications.

---

### Post by Irony on 2006-06-24
I'd say this is a serious problem as when you start out using Ubuntu you are not likely to realise the difference. I've been using Ubuntu for about a year and didn't appreciate the difference until recently; fortunately I never typed sudo nautilus for root nautilus.

I did wonder why though I had to type gksudo nautilus, its just that I was never adventurous enough to try sudo nautilus.

---

### Post by aysiu on 2006-06-24
It's a serious problem, but it's not a bug.

The serious problem is that people tell other people to use the wrong command!

---

### Post by Kvark on 2006-06-24
If someone types sudo chown -r / or whatever the command is then they want to change ownership of the entire filesystem to so they only get exactly what they want.

When someone types sudo kate they want to run kate as root so they should get exactly that.

Or are you saying that sudo is supposed to prevent login? That it is an intentional feature? In that case I think the "disable login" feature should be removed or at least moved to a separate lockmeout command.

---

### Post by Irony on 2006-06-24
Here's an example which I used yesterday (it didn't work);

[PHP]irony@ubuntu:~$ sudo sh /mnt/hda8_Stuff/downloads/google/GoogleEarthLinux.bin[/PHP]

This launched a graphical installer, does this mean I should have used;

[PHP]
irony@ubuntu:~$ gksudo sh /mnt/hda8_Stuff/downloads/google/GoogleEarthLinux.bin[/PHP]

It didn't mess anything up and I ended up simply do a non-root install;

[PHP]
irony@ubuntu:~$ sh /mnt/hda8_Stuff/downloads/google/GoogleEarthLinux.bin[/PHP]

---

### Post by aysiu on 2006-06-24
*sudo* is meant to allow you to run terminal applications with root privileges.

*gksudo* and *kdesu* are meant to allow you to run graphical applications with root privileges.

The only reason people do stuff like ```
sudo kate
``` is other people constantly instructing them to do ```
sudo gedit
```

---

### Post by aysiu on 2006-06-24
> **Irony]Here's an example which I used yesterday (it didn't work) said:**
> irony@ubuntu:~$ sudo sh /mnt/hda8_Stuff/downloads/google/GoogleEarthLinux.bin[/PHP]

This launched a graphical installer, does this mean I should have used;

[PHP]
irony@ubuntu:~$ gksudo sh /mnt/hda8_Stuff/downloads/google/GoogleEarthLinux.bin[/PHP]

It didn't mess anything up and I ended up simply do a non-root install;

[PHP]
irony@ubuntu:~$ sh /mnt/hda8_Stuff/downloads/google/GoogleEarthLinux.bin[/PHP]
No, because shell scripts are not graphical applications. Within the script itself, there may be something that launches a graphical window later, though.

---

### Post by Irony on 2006-06-24
I figured it was something like that because it didn't mess up ICE.

GoogleEarth is pretty amazing.

---

### Post by gingermark on 2006-06-24
[QUOTE=aysiu]*sudo* is meant to allow you to run terminal applications with root privileges.

*gksudo* and *kdesu* are meant to allow you to run graphical applications with root privileges.

The only reason people do stuff like ```
sudo kate
``` is other people constantly instructing them to do ```
sudo gedit
```[/QUOTE]

Reading back through this thread I realise that initially my point might not have been as well expressed as it could have been, but of course this is the crux of it.

It's not about whether "sudo gedit" *works* or not, it's about making the distinction to new users between which is used for graphical applications (even if from the terminal) and which is used for terminal commands.

I honestly think we need a sticky (not this thread) that explicitly states this, and encourages more experienced users to hand out consistant commands.

---

### Post by aysiu on 2006-06-24
gingermark, I apologize.

You were right. I was wrong. You weren't making too big a deal about it at all.

A consistent message and good practice is what matters. And old users should really encourage new users to use the proper *sudo* command.

---

### Post by Martian on 2006-06-24
When I try
```
gksudo gedit
``` I get a
```
(gedit:11480): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```

I've been using ```
sudo gedit
``` all along...  Something broken?

---

### Post by aysiu on 2006-06-25
No, it's a false error, and there's already been a bug report filed on it that the developers have labeled as low priority.

More details [here](http://www.ubuntuforums.org/showpost.php?p=1177379&postcount=9).

---

### Post by aysiu on 2006-06-25
[QUOTE=gingermark]
I honestly think we need a sticky (not this thread) that explicitly states this, and encourages more experienced users to hand out consistant commands.[/QUOTE] Well, I don't have the power to make stickies, but I did type up a document explaining everything, and hopefully people will take heart when issuing commands, but I can't keep explaining it over and over again... so... this document:

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by brady618 on 2006-11-19
Okay, this thread is a bit old but it's the only one I could find that somewhat pertains to my problem.  I recently did a fresh install of Edgy and began to load all of my old programs onto it.  I use gnome with Enlightenment as the window manager, btw.  Recently I've been needing to change some configuration files to make everything as it was in Dapper, but all of a sudden my sudo gedit stopped working.  When I use gedit to open a file, it works, but I am unable to save.  According to this thread sudo gedit is wrong, though, and I tried gksudo gedit /.../.../..., but it only yeilds this

(gedit:8282): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

and nothing opens.

I've been with Ubuntu for about 9 months, and am therefore relatively new, and have no idea how to work around this.  I tried gksudo thunar to open the file manually, but couldn't even see the file!!  Sudo and gksudo still work, to my understanding, I just can't open text files with them anymore.  (The file I'm trying to get to is /usr/share/applications/gnome-screensaver-preferences.desktop).  Sudo gedit worked for a while after installing Edgy, but perhaps I messed it up from using it so frequently.  I wish I had known earlier that gksudo was the correct command.  People need to start using the correct commands, cuz as a newbie I know that we mostly cut-and-paste, and I have no idea if my system is messed up or what now.  I'd hate to have to do a total re-install just to fix this minor bug.  Is there something I'm overlooking?  Any help would be greatly appreciated.

---

### Post by darkhatter on 2006-11-19
I think they should go back to root and users, and force everyone to remember 2 passwords, sudo is causing a lot of problems for me ](*,)

---

### Post by aysiu on 2006-11-19
> **darkhatter said:**
> I think they should go back to root and users, and force everyone to remember 2 passwords, sudo is causing a lot of problems for me ](*,)
I think you should use Mepis, then, especially since you're already on KDE according to your profile.

Mepis is now Ubuntu-based, uses the same repositories, has KDE as a default desktop environment, and has a separate root user and regular user.

---

### Post by darkhatter on 2006-11-19
> **aysiu said:**
> I think you should use Mepis, then, especially since you're already on KDE according to your profile.

Mepis is now Ubuntu-based, uses the same repositories, has KDE as a default desktop environment, and has a separate root user and regular user.

I read though the wiki and found a way to hack it back to normal so I'm good.

---

### Post by deanlinkous on 2006-11-19
I just add a gksudo application launcher to my panel so I can drag and drop a file onto it for root privys.

Also keep a gksudo nautilus launcher.

---

### Post by Corvillus on 2006-12-24
I think that the main difference between gksu/gksudo/kdesu and sudo is the fact that the graphical commands actually put you in a full root environment whereas sudo uses the current user's environment. Basically, gksu/kdesu make you root, just like a login shell would. sudo on the other hand makes your uid and gid 0 (root) but everything else is yours (like your home directory) The problem with this is that you'll get root owned junk in your home directory instead of in root's where it belongs (which can lead to problems with any applications that dump configuration junk in your home directory, not just graphical ones).

For people who have used other non-sudo administrated Linux distros, it's similar to the reason why you should use su - instead of su.

You can also use ```
sudo -H <command>
``` instead of ```
sudo <command>
``` to force the command to use root's home directory. You can also add the always_set_home flag to sudoers to make -H implied with every sudo execution.

---

### Post by aysiu on 2006-12-25
You're on the right track, but it actually works the opposite way. If you use *sudo* with graphical applications, you get root-owned junk in your /home directory. *gksudo* or *kdesu* will use root's configuration files, not the user ones.

---

### Post by spockrock on 2006-12-25
hmm....this is a good tidbit of knowledge, I am gonna start using gksudo for graphical apps.

---

### Post by aysiu on 2006-12-25
> **spockrock said:**
> hmm....this is a good tidbit of knowledge, I am gonna start using gksudo for graphical apps.
Read more here:
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Corvillus on 2006-12-25
> You're on the right track, but it actually works the opposite way. If you use sudo with graphical applications, you get root-owned junk in your /home directory. gksudo or kdesu will use root's configuration files, not the user ones.

I thought that's what I did say in the first paragraph of my previous post, but I may not have been as clear as I should have been, but to clarify

gksu/gksudo/kdesu/sudo -H all use the target user's (root's) home directory.
sudo by itself uses the current user's home directory by default (although this default can be changed as explained in the following paragraph).

Adding always_set_home to the end of the Defaults line in sudoers makes sudo always use the target user's (root's) home directory instead of the invoking user's. (I wonder if this should be made a default setting for Ubuntu, since it makes all of these user substitution commands behave consistently and as a result there isn't the usability issue of people wondering which command to use in which situation. The only real downside to this is that when using sudo before a command, people would have to remember that ~ refers to /root instead of /home/invokinguser)

---

### Post by coldstatue on 2007-07-06
sudo gedit had me using sudo all over the place. And yes, I do have some things in my home directory that should not be there.

glad I stumbled onto this thread!

Thanks!

---

### Post by nooblot on 2008-07-04
ooopps

I definitely did "sudo nautilus" before...since 7.04...what did i mess up ?
What can I do to check if I f**k anything up ?

thanks

---

### Post by K.Mandla on 2008-07-04
Closed for necromancy. Start a new thread in a support forum if you have questions about that command.

---

