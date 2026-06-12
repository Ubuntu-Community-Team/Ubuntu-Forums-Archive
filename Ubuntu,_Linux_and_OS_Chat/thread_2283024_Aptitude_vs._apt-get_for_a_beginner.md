---
title: "Aptitude vs. apt-get for a beginner"
date: 2015-06-18
forum: Ubuntu, Linux and OS Chat
---

### Post by papakota on 2015-06-18
Hello!
Is it true that aptitude is more aggressive than apt-get and it's better to stick with apt-get for a Ubuntu **beginner**?

---

### Post by slickymaster on 2015-06-18
Have a read at this thread on the subject: [http://ubuntuforums.org/showthread.php?t=2240291](http://ubuntuforums.org/showthread.php?t=2240291)

---

### Post by QIII on 2015-06-18
One way in which they differ is in how they manage dependencies.

Aptitude flags dependencies and removes them when you uninstsall.  Apt-get requires you to also issue the autoremove command.

Because of that difference, you should use one or the other consistently to avoid heartburn-inducing dependency problems.

---

### Post by VMC on 2015-06-18
I now use '***apt***' exclusively, from reading this **[blog]("https://mvogt.wordpress.com/2014/04/04/apt-1-0/")**. When *aptitude* was included with ubuntu I used it, then when removed I used *apt-get*. Apt makes life simple.
From 'apt' man page:
> The apt command is meant to be pleasant for end users and does not need
       to be backward compatible like apt-get(8)

---

### Post by ajgreeny on 2015-06-18
And I make a lot of use of synaptic which used to be the default package manager in Ubuntu but is no longer installed, having been overtaken by software-centre.  It is always the first package I add after installing the OS.

Personally I NEVER use software-centre; it's always synaptic or apt-get for me, and I admit, mostly synaptic.  Synaptic is much more flexible and informative than USC and can even be used to lock versions of packages, install alternative versions if they exist, search in many ways for the packages you need and show dependencies, and it can fix any broken packages you may have.  You can even set it to carry out the installations in a terminal window so you can see exactly what is going on at the time.

---

### Post by papakota on 2015-06-18
Thank you all for your replies! 
Okay, I'm gonna stick with apt-get unless I have **a very good reason** to use aptitude. Of course, before I do that, I'll double-check on that to be on a safe side.

---

### Post by oldos2er on 2015-06-18
aptitude does have a nice ncurses interface lacking in apt-get, if you're into such things. I find these days apt-get does everything I need.

---

### Post by papakota on 2015-06-18
Thanks!

---

### Post by monkeybrain20122 on 2015-06-18
> **ajgreeny said:**
> 

Personally I NEVER use software-centre; it's always synaptic or apt-get for me, and I admit, mostly synaptic.  Synaptic is much more flexible and informative than USC and can even be used to lock versions of packages, install alternative versions if they exist, search in many ways for the packages you need and show dependencies, and it can fix any broken packages you may have.  You can even set it to carry out the installations in a terminal window so you can see exactly what is going on at the time.

Same here. However just want to say that "sudo apt-get upgrade" doesn't respect pinning in synaptic. Pinned packages in synaptic will get upgraded by running the command in the terminal. To pin packages in such a way that they are honoured by apt-get cmd one has to edit /etc/apt/preferences.

---

### Post by cooleryawner on 2015-06-19
Apt-get is good to learn for beginner. Also, according to the help page in terminal , Apt-get has super cow powers!

---

### Post by Bucky Ball on 2015-06-19
*Thread moved to **Ubuntu, Linux and OS Chat**.*

As ajgreeny, apt-get and Synaptic for me. :)

I use a mini install and install Synaptics. I haven't had Software Centre even installed in years. gdebi deals with .debs for me.

---

### Post by PaulW2U on 2015-06-19
I've always used aptitude because I like using the terminal and like aptitude's ncurses interface. It gives you a colourful display of the actions that it's going to take.

One user on another forum told me **not** to use it under any circumstances while knowledgeable and respected users here have recommended its use without reservation.

I guess the choice of package manager is a personal thing like the choice of your desktop wallpaper. Whatever works for you.

Just make sure you know what it's going to do to your system when you hit 'ok' or whatever. ;)

---

### Post by monkeybrain20122 on 2015-06-19
I have tried aptitude a while back. TBH I don't really see what the big deal is (Apparently Debian users like to make a big deal out of it). The only apparent advantage that I know is that it keeps track of packages installed as dependencies so aptitude remove would remove these packages as well, but you can do the same with with apt-get autoremove.

But I prefer synaptic over the command line tools because of the easy search functions,  ease to browse packages by categories with descriptions and I often don't know or remember the exact names of the packages I want to install.

---

### Post by Bucky Ball on 2015-06-19
> **monkeybrain20122 said:**
> ... I often don't know or remember the exact names of the packages I want to install.

I can relate to that. :)

Yes, love Synaptic.

---

### Post by ajgreeny on 2015-06-19
> **monkeybrain20122 said:**
> I have tried aptitude a while back. TBH I don't really see what the big deal is (Apparently Debian users like to make a big deal out of it). The only apparent advantage that I know is that it keeps track of packages installed as dependencies so aptitude remove would remove these packages as well, but you can do the same with with apt-get autoremove.

But I prefer synaptic over the command line tools because of the easy search functions,  ease to browse packages by categories with descriptions and I often don't know or remember the exact names of the packages I want to install.
Agreed, and in my recent installations of synaptic the default for package removal has been "Completely remove" which as I understand it, is the same as running autoremove later and the same as using aptitude.

---

### Post by monkeybrain20122 on 2015-06-19
> **ajgreeny said:**
> Agreed, and in my recent installations of synaptic the default for package removal has been "Completely remove" which as I understand it, is the same as running autoremove later and the same as using aptitude.

Don't think completely remove and autoremove are the same thing, AFAIK the former means removing config files. In synaptic there is a separate category called "Autoremove" or "Autoremovable" it will show up if you have something that can be autoremoved.

---

### Post by ajgreeny on 2015-06-20
> **monkeybrain20122 said:**
> Don't think completely remove and autoremove are the same thing, AFAIK the former means removing config files. In synaptic there is a separate category called "Autoremove" or "Autoremovable" it will show up if you have something that can be autoremoved.
Silly me!

Of course, you are correct.  I was thinking far too quickly to make sure I was right.

---

### Post by oldos2er on 2015-06-21
Yep, Synaptic's "completely remove" is the equivalent of *sudo apt-get purge ...*

---

### Post by mikodo on 2015-06-21
> **papakota said:**
> Thank you all for your replies! 
Okay, I'm gonna stick with apt-get unless I have **a very good reason** to use aptitude. Of course, before I do that, I'll double-check on that to be on a safe side.

A good choice for a beginner, I believe. I started using aptitude after using apt for a while, and found it has more commands than I was ever going to use. When "apt-get autoremove" was incorporated, I was happy to go back to apt. It seems when ever I am following 'reliable sources' for package management in Ubuntu, I invariably see apt suggested. That is not always true with aptitude. Works for me.  :) 

You can always go to aptitude in the future as you become more experienced in package management. But like what was said by QIII, don't mix and match them in one install unless, you have progressed to an advanced knowledge of P. management.


On Synaptic. 

Use it all the time too. Is the first app I install also. Things were mentioned about it in your thread, that I didn't know about, even after years of using it.

I just found this [Ubuntu Official Documentation]("https://help.ubuntu.com/community/SynapticHowto") page. duh!

---

### Post by monkeybrain20122 on 2015-06-22
Another reason to recommend synaptic for beginners over the command line is that people who cut and paste commands without understanding can get themselves into big troubles when trying to improvise.

There was a thread where some guy tried to remove wine and ended up uninstalling half of his OS by typing 
```
sudo apt-get remove wine*
```

Apt-get uses regular expressions where the "*" is not a wild card like in bash.

---

