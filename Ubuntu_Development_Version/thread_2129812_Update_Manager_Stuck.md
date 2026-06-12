---
title: "Update Manager Stuck"
date: 2013-03-27
forum: Ubuntu Development Version
---

### Post by craig10x on 2013-03-27
This morning when the Update Manager came up to notify me there was updates, i started the updates, and half through the install, the progress bar just froze and nothing else happened...
I tried re-booting and ran it again but it stops around mid range...

What could i do to get it straightened out? :confused:  anyone else having this problem?

Apparently, the packages were downloaded, but it is stuck at the point where it is supposed to start installing them...

It says: Installing Updates...
Applying Changes

and when i look at the "details" section is says:

Extracting templates from packages: 100%
Preconfiguring Packages

That's the point the software updater froze at...

---

### Post by dino99 on 2013-03-27
its the most buggy app i've never seen, and its not very new  :mad:
(i'm a synaptic fan, no need to explain why :P)

---

### Post by craig10x on 2013-03-27
I know what you mean...i was able to get it straightened out as i recall once having this problem when running linux mint and their software updater froze on me...this is what they told me to do...
I went into the terminal and ran: [COLOR=#232323][FONT=Georgia]sudo apt-get upgrade

[/FONT][/COLOR]Once i did that, it was fixed and it installed most of the packages...then i went back to "update manager" and it brought up a "partial upgrade" installed that and now
the "software updater" is back to normal again :)

---

### Post by cariboo on 2013-03-27
In a case like this you may to try running:

```
sudo apt-get -f install
```

just in case there are missing dependencies.

---

### Post by craig10x on 2013-03-27
Thanks for the tip...cariboo907...i will make note of that... ;)

I did get it working using the sudo apt get upgrade command as i noted in my 2nd post above...but then i wound up doing a partial upgrade in software manager...next time it happens , i will try your
suggestion first...

Can't really single this problem out to development as it has sometimes (though rarely) happened to me on regular releases of both linux mint and ubuntu...

---

### Post by cariboo on 2013-03-27
I also use synaptic for package management, and a couple of time over the last couple of weeks after doing an update it could find some of the packages, running update a second time solved the problem.

---

### Post by dino99 on 2013-03-27
note: each updating/upgrading tool built & use its own index. Is well known that apt-get & aptitude indexes often conflict. I does not mean its the same with update-manager, but who knows.

---

### Post by grahammechanical on 2013-03-27
I run Update Manager on full screen to see the new way information is displayed. I hit an problem just now. The screen blinked out of existence but downloading and installing continued. I tried running a new instance of Update Manager but it could not get control. I guess the first instance of Update Manager was still working behind the scenes. After a while I was able to run an update through the terminal and my system is up to date.

I wonder if this has anything to do with the problem?

[http://www.bbc.co.uk/news/technology-21954636](http://www.bbc.co.uk/news/technology-21954636)

Regards

---

### Post by dino99 on 2013-03-27
As we now have upstart-monitor, it could be usefull to list the processes & narrow down that issue.

---

### Post by balloons on 2013-03-27
Typically I'm using the command line or USC. On my non-dev (aka, stable) boxes though, they are all run via the update manager and it works fine. I think many of these issues crop up when the update-manager gets partial upgrades, archive state issues, etc during the dev cycle. All worth trying to track down and file bugs upon (the software should handle this properly!), but that's my wild guess as to what's happening.

---

### Post by Seb71 on 2013-03-27
> **grahammechanical said:**
> I run Update Manager on full screen to see the new way information is displayed. I hit an problem just now. The screen blinked out of existence but downloading and installing continued. I tried running a new instance of Update Manager but it could not get control. I guess the first instance of Update Manager was still working behind the scenes. After a while I was able to run an update through the terminal and my system is up to date.

I wonder if this has anything to do with the problem?

[http://www.bbc.co.uk/news/technology-21954636](http://www.bbc.co.uk/news/technology-21954636)

Regards
Don't think so. I have the problem you describe for a few weeks now.

---

### Post by Gyokuro on 2013-03-27
Sometimes it could help to kill the Update Manager and do a clean up via sudo apt-get clean in a terminal. If something goes wrong or do not work you get a detailed information what went wrong or do not work and you get a hint what broke - for my taste all this GUI tools are hiding too much of this important information (it's fine for user to keep their system up to date but could be a nightmare for advanced user). I have to admit that I'm not using all this GUI tools and do all updates via CLI tools and I wrote a nice shell script which backup the system package database before I update anything.

---

### Post by Frogs Hair on 2013-03-27
I had a similar problem and  I logged out and shut down. Upon restart I ran  and login ran the following commands with success. The package that failed to configure was Gnome Sudoku. :confused: ```
 sudo dpkg --configure -a  
``` ```
sudo apt-get update
``` ```
sudo apt-get upgrade
```

---

