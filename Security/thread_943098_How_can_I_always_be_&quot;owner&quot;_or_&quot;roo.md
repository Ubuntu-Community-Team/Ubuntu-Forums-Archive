---
title: "How can I always be &quot;owner&quot; or &quot;root&quot;???"
date: 2008-10-09
forum: Security
---

### Post by Albertkinng on 2008-10-09
I'm the only one using my netbook, and it's a nightmare everytime I want to install something. Always a popup windows saying that I'm not the owner... I need to be root or something to be able to do everything I need. how can I swith to the owner and do whatever I want with Ubuntu? please help. right now I can even install a package on my netbook, and it seems everyone can but me! I'm new in UBUNTU. thanx for your time in advance.:confused:

---

### Post by BLTicklemonster on 2008-10-09
The answer is out there, I just don't remember where it is. I did that once, but went back, because I enjoy knowing every time I enter my password that I'm secure.

Someone will be along with the answer soon (unless I can find it first).

[http://php.8ez.com/drsmall/blog/?p=187#comment-1094](http://php.8ez.com/drsmall/blog/?p=187#comment-1094)

---

### Post by SunnyRabbiera on 2008-10-09
Using root as your standard account is a very bad idea.
What applications are you trying to install?

---

### Post by doas777 on 2008-10-09
> **Albertkinng said:**
> I'm the only one using my netbook, and it's a nightmare everytime I want to install something. Always a popup windows saying that I'm not the owner... I need to be root or something to be able to do everything I need. how can I swith to the owner and do whatever I want with Ubuntu? please help. right now I can even install a package on my netbook, and it seems everyone can but me! I'm new in UBUNTU. thanx for your time in advance.:confused:

first read this: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

seriously, you don't need to run as root. once you get used to it, running as a limited user with sudo capability is the best of both worlds.

but linux is about choice.

BTW you don't want to own everything. if you do, ubuntu won't work. it's not a security thing. running as root is a better idea than going crazy with chown.

Thanks aysiu. I'll keep that in mind in future

---

### Post by Albertkinng on 2008-10-09
well, I want to install Flash 10 , I already got flash 9 but something wrong because I can press a botton to enter to my account page (its a shockwave flash page for monitoring the flow of telephone calls on radio) With my old Powerbook I just enter the site and everything was normal, I write my name and my password and press login and I was there... but now with my new netbook with ubuntu, I can enter the page write my name and pass but when I try to press the botton its like it cant be press, it doesnt do anything... so I was thinking maybe it has to be something with flash, and I found a newer version and when I was ready to install it, it wont let me even opening "Synaptic" a small utility for instalations... anyway.. this are the apps that I want to install: Audacity, Gimp, Flash 10. thanx in advanced.

---

### Post by jerome1232 on 2008-10-09
How are you installing packages? Generally if you need to be root to do something you just prepend your command with 'sudo' or 'gksudo' if it's a graphical app.

If you open add/remove... or synaptic to install packages they should automatically ask you for your password and then let you install with about 2 clicks no problem.

edit: Gimp is installed by default, Audacity can be installed from the repos, Flash ten I'm pretty sure there's a repo you can add for that let me find it. ```
sudo apt-get install audacity
```

---

### Post by Albertkinng on 2008-10-09
it wont let me use Synaptic it tells me Im not the owner... and I am! lol

---

### Post by doas777 on 2008-10-09
> **Albertkinng said:**
> it wont let me use Synaptic it tells me Im not the owner... and I am! lol

is your launcher for synaptic using gksu (so it will prompt you for password and allow operation as root)?

just right click your menu bar and select "Edit Menus". on the left select Administration under System. in the right pane select 'Synaptic Package Manager' and right click. select properties.

where it says "Command:" what do you have there? it should start with 'gksu'. mine is 'gksu /usr/sbin/synaptic'

if you don't have 'gksu' at the beginning of the command, add it. 
then just try to start synaptic and see if it prompts for your password.

---

### Post by Albertkinng on 2008-10-09
it says gksu like u! let me see if it works now...

---

### Post by shualuntan on 2008-10-10
> **Albertkinng said:**
> it says gksu like u! let me see if it works now...
it is worth to read

---

### Post by kerry_s on 2008-10-10
learning to use sudo takes time, it's worth learning though.

1 of the first things i do is add my most common root programs to use nopasswd in the sudoers file.

example:
user ALL=NOPASSWD: /usr/sbin/synaptic, /usr/bin/nautilus, /usr/bin/gedit, /etc...

then i change the launchers to use sudo, create the scripts i use, etc...

---

### Post by Albertkinng on 2008-10-10
Thanx everybody now I can still use my netbook and install whatever I want without being the ROOT user, so you were right its better like this, I'm really getting use to Ubuntu, and I know that with your help I will understand more and more in the long run... so... I really apreciate allyour help.:guitar:

---

