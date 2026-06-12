---
title: "Antivirus for Linux?"
date: 2004-12-23
forum: Server Platforms
---

### Post by tleroy on 2004-12-23
While I trust my friends in other forums, I just wondered what a large group of Linux users think about whether antivirus software is needed for Linux.  If so, what are some good, free Antivirus products?  If not now, do you think viruses for Linux will become more prevalent as Linux gets more popular?

Sincerely,

---

### Post by nemin on 2004-12-24
[QUOTE=tleroy]While I trust my friends in other forums, I just wondered what a large group of Linux users think about whether antivirus software is needed for Linux.[/QUOTE]
No, I don't think antivirus software is needed for linux boxes, except on mailservers to filter out windows viruses :)
[QUOTE=tleroy]
If not now, do you think viruses for Linux will become more prevalent as Linux gets more popular?
[/QUOTE]
I think it's likely linux will become more interesing to viruswriter when it becomes more popular. Though, the risk of linux viruses will be less compared to windows viruses. For example, since linux users usually read mail with their own user account, opening a virus won't be destructive for the whole system, simply because the user has no write access to it.

---

### Post by Smash on 2004-12-24
You don't need an antivirus, but you can install Clamav to stay completely safe  :p 

```
sudo apt-get install clamav
```

---

### Post by ubuntu_demon on 2004-12-24
see :

AntiVirus
[http://www.ubuntuforums.org/showthread.php?t=5875](http://www.ubuntuforums.org/showthread.php?t=5875)

you'll only need antivirus if you want to scan emails / networks in order to prevent windows machines from getting infected.

---

### Post by tleroy on 2004-12-26
Thanks for the feedback folks!  :)

---

### Post by jadm5000 on 2004-12-27
[QUOTE=Smash]You don't need an antivirus, but you can install Clamav to stay completely safe  :p 

```
sudo apt-get install clamav
```[/QUOTE]
 oh god after using Windows forEVER and constantly getting ANYTHING off the web screwing it up - this answer makes me VERY happy, im a newbie so i wasnt sure myself!
ty!

---

### Post by taygan on 2004-12-29
If you're going to run clamav you should run the 0.80 version which can be found in the backports repository..  The earlier versions overload the clamav servers and they've asked everyone to update to the rotating servers that 0.80 uses.

see this thread:
[http://www.ubuntuforums.org/showthread.php?t=8474&highlight=clamav](http://www.ubuntuforums.org/showthread.php?t=8474&highlight=clamav)

---

### Post by oiaohm on 2005-01-09
[http://www.rootkit.nl/projects/rootkit_hunter.html](http://www.rootkit.nl/projects/rootkit_hunter.html) RootKit Hunter and chkrootkit detect most linux viruses and Rootkit Hunter gives about 99.9 percent cover against root breach by software.  Yep better than most windows antivirus systems.

Now this is a problem most users have with linux is that a Virus and a hacker breaking into the system come under the name of a rootkit.

Now Clamav makes a good free email scanner to protect windows machines from windows viruses from the linux email servers and fileservers.

At this point I don't know of any virus that effect linux other than windows/dos viruses running in side wine/dosemu/dosbox running in the users accounts.  So Rootkit Hunter wiht chkrootkit(just like any antivirus scanner you can get incorrect answers from time to time)would be my linux recommended antivirus system.

This will change Part of ubuntu someone sould create a tool called anti-virus that controls Clamav, rootkit hunter, chkrootkit and aide.  To get past all of this a virus will have to be really good and really new.

Now a new linux user will have a little bit of trouble getting use to the software due to no good front ends I know of.

---

### Post by tleroy on 2005-01-12
Thanks folks!  :)

---

### Post by ubuntu UsER on 2005-01-13
You can also use Klamav, graphical front-end to Clamav :)
It is for KDE, but you can try it on Gnome :)
[http://klamav.sourceforge.net/](http://klamav.sourceforge.net/)

---

### Post by Danilo on 2005-01-13
[QUOTE=nemin]Though, the risk of linux viruses will be less compared to windows viruses. For example, since linux users usually read mail with their own user account, opening a virus won't be destructive for the whole system, simply because the user has no write access to it.[/QUOTE]
That's mostly not the point. Regular users can usually open outgoing Internet connections, and receive incoming Internet connections on ports larger than 1023: quite sufficient means for viruses to reproduce themselves, infect other machines, etc.  I really couldn't care less that my "whole system" is preserved if a virus trashes *just* my home directory.

So, on desktop, they'll be as much a treat as anywhere (including Windows). The only thing that will stop them (and that is stopping them now) is **diversity**: diverse architectures means having to use different machine instructions, diverse software means that not many will use one single vunerable program and/or service. Another big reason is that Unixey programmers are generally more security-conscious, and are more pragmatic: if they're not sure they can make something safe, they just don't make it. That's the big difference in applications such as e-mail clients (scriptability? uhm, someone might like it, but be very careful!).

After all, imagine a buffer overflow being found in jpeg6b library used on every free system out there: it would be a mere task of pointing you at the specially crafted JPEG image (browser, eog, any tool) to get your computer "infected". (This is the diversity point: if we had dozens of JPEG libraries, it would be hard to get larger effect; OTOH, this allows one single library to be better reviewed, so it's not all bad.)

---

### Post by J. S. Jackson on 2005-01-17
[QUOTE=nemin]Though, the risk of linux viruses will be less compared to windows viruses. For example, since linux users usually read mail with their own user account, opening a virus won't be destructive for the whole system, simply because the user has no write access to it.[/QUOTE]

Although I suspect that the great majority of WindowsXP users run with administrator rights most of the time - this falls under the category of user error.

It's a risky thing to do, but as you know, uninformed users will often click through dire warnings, and disable security features, for the sake of convenience.  I don't think MS can be blamed for that?

I've seen numerous people completely disable firewalls in order to get things, such as file transfers over IM, to work.  Making it harder to accomplish such a thing does not discourage a determined user.  They will simply click through any warnings neccesary to achieve their purpose.

My wife does it all the time - click, click, click, apply, ok, ok, install, run, ok.  All in 5 seconds.   8-[

---

### Post by Rule on 2005-01-17
[QUOTE=J. S. Jackson]I've seen numerous people completely disable firewalls in order to get things, such as file transfers over IM, to work.  Making it harder to accomplish such a thing does not discourage a determined user.  They will simply click through any warnings neccesary to achieve their purpose.

My wife does it all the time - click, click, click, apply, ok, ok, install, run, ok.  All in 5 seconds.   8-[[/QUOTE]

[IMG]http://www3.telus.net/ra11le/smilies/werd.gif[/IMG]

---

### Post by nocturn on 2005-01-18
[QUOTE=J. S. Jackson]Although I suspect that the great majority of WindowsXP users run with administrator rights most of the time - this falls under the category of user error.

It's a risky thing to do, but as you know, uninformed users will often click through dire warnings, and disable security features, for the sake of convenience.  I don't think MS can be blamed for that?
[/QUOTE]

There's a difference in attitude and history.
First of, Windows (even XP) was built on a system/methods that were designed for single-user operation.  Access controls and multi-user features were fitted on this base later (the opposite of *nix).  MS still has to work arround a lot of the problems this retro-fitting introduces.

Secondly, if you do a windows install, it defaults to insecure settings, it recommends the user to run with admin rights.  Linux does not do this.
Most distros (especially Ubuntu) install with safe defaults.
Remeber, the purpose of MS product is to be easy, so everyone can set up something complex like a webserver or kerberos without knowing the tech.  


> 
I've seen numerous people completely disable firewalls in order to get things, such as file transfers over IM, to work.  Making it harder to accomplish such a thing does not discourage a determined user.  They will simply click through any warnings neccesary to achieve their purpose.


Yes and no.  On my networks, user need to ask me tho enable this (they have no admin rights on machines, and certainly not on the firewall - a seperate machine -).
I make it work, and everyone is happy, yet security is not sacrificed.

A system like windows that pops up a dialog like 'allow connection from 232.323.767.343 to port 56677?  Yes - no' is bound to mess up because every user (execpt a techie) will hit yes.

---

### Post by J. S. Jackson on 2005-01-18
> Secondly, if you do a windows install, it defaults to insecure settings, it recommends the user to run with admin rights. Linux does not do this.

It's certainly a problem.  MS has always put convenience of the user, above security.  However, a properly configured XP machine is quite secure, it's just that the great majority of windows users have no clue how to set it up... and that's partly MS's fault for not forcing them into secure settings, and partly the user's fault for not educating himself a bit.  But surely MS should bear the brunt of the blame, since they know that most of their users are not computer literate, and will accept the defaults without question.

Another factor that plays into this is how computers have been marketed the last few years.  Basically it's like this:  "Whoopie! Get on the Internet! play games! chat with friends! Download MP3's for Free! send emails! HAVE FUN!!1!"

And so people consider a computer as something like an interactive television or a Nintendo...  And people who know NOTHING about computers go out and buy one, but they don't realize that computers are FAR from secure, and far from idiot proof at this point in time.

---

### Post by nocturn on 2005-01-18
[QUOTE=J. S. Jackson]It's certainly a problem.  MS has always put convenience of the user, above security.  However, a properly configured XP machine is quite secure, it's just that the great majority of windows users have no clue how to set it up... and that's partly MS's fault for not forcing them into secure settings, and partly the user's fault for not educating himself a bit.  But surely MS should bear the brunt of the blame, since they know that most of their users are not computer literate, and will accept the defaults without question.[/QUOTE]

In addition, because of the single-user no password heritage of windows there are few good tools arround to make it easier to run as a normal user yet drop to admin when needed.
Linux has tools like su and sudo which are extremly powerful.  Windows is created with the full-screen-login dogma.

On Linux, I remotely log in with my userID, up to root and install a program without interfering the local user on that system.
On windows,  this is a lot more complex and puts of many users.

---

### Post by nocturn on 2005-01-18
[QUOTE=Danilo]That's mostly not the point. Regular users can usually open outgoing Internet connections, and receive incoming Internet connections on ports larger than 1023: quite sufficient means for viruses to reproduce themselves, infect other machines, etc.  I really couldn't care less that my "whole system" is preserved if a virus trashes *just* my home directory.
[/QUOTE]

I agree that for you that can be true.  Still with your system not compromised, restoring to normal operations is as simple as restoring your home directory from backup (you do have backups, right?).
On Windows, you'll have to do a complete reinstall, which is a lot of work, and your personal data is still trashed. 

Also, a Linux system can have multiple users (even at the same time - thin clients -).  Other users' data is not affected by trashing your home.

---

### Post by marlena4084 on 2007-05-15
> **ubuntu_demon said:**
> see :

AntiVirus
[http://www.ubuntuforums.org/showthread.php?t=5875](http://www.ubuntuforums.org/showthread.php?t=5875)

you'll only need antivirus if you want to scan emails / networks in order to prevent windows machines from getting infected.


[photosynthesis Debt Consolidation Paris Hilton Yahoo Britney Spears](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

