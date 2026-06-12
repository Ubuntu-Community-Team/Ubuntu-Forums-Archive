---
title: "Why are the Software Center and Software Updater separate?"
date: 2015-06-26
forum: Ubuntu, Linux and OS Chat
---

### Post by kyle-kuhn on 2015-06-26
I have no idea where to put this, so I put it here.
I've been using Ubuntu since 11.04 (only now getting forum account for some reason), and the one things that has irked me is how the software updater and software center are two different applications. I sit there and I've thought that it would seem more intuitive to integrate the updater into the software center, would it not? It would certainly seem like it should be like that since the software center already shows update progress. What do you all think of this idea? Is there any motive for keeping the two separate?

---

### Post by vasa1 on 2015-06-26
I like a program that does one thing and does it well. The aims of the software center and the updater don't overlap, IMO, and so I'm comfortable with them being separate.

I'm not sure I'm right about this but I think the software updater is common to all *buntu flavors whereas the software center isn't.

I also read somewhere (?) that the Software Center is being reworked extensively.

---

### Post by v3.xx on 2015-06-26
> Is there any motive for keeping the two separate?
Nope, its a good idea.  Guess thats why its part of my package manager.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

---

### Post by kagashe on 2015-06-26
In old versions there was only Synaptic. I use to click on Reload and it was updating, then I use to click on Mark all upgrades and click on Apply and it use to download the upgraded packages and upgrade after the download. But the updates were not automatic.

Then Software Updater was developed basically to automatically get the updates and ask you to download and install them.

Software Centre has been developed in the later versions of Ubuntu.

Apart from the update/upgrade of existing software on your machine you may need to add new software. Software Centre is basically meant for adding new software. Before Software Centre we were doing it through Synaptic.

If you want you can  install Synaptic and have a feel of old days and use it if you like and disable automatic updates.

Kamalakar

---

### Post by ajgreeny on 2015-06-26
> **kagashe said:**
> In old versions there was only Synaptic. I use to click on Reload and it was updating, then I use to click on Mark all upgrades and click on Apply and it use to download the upgraded packages and upgrade after the download. But the updates were not automatic.

Then Software Updater was developed basically to automatically get the updates and ask you to download and install them.

Software Centre has been developed in the later versions of Ubuntu.

Apart from the update/upgrade of existing software on your machine you may need to add new software. Software Centre is basically meant for adding new software. Before Software Centre we were doing it through Synaptic.

If you want you can  install Synaptic and have a feel of old days and use it if you like and disable automatic updates.

KamalakarAnd that's exactly how I have always done things!

I don't like and do not use software-centre or the software-updater; it has always been synaptic for me and it is the first package I add to my systems after installing a new OS.

---

### Post by grahammechanical on 2015-06-26
What we are discussing here are just different front ends to apt-get and other system functions.

And there exists a bit of integration between these tools already because they all access the software sources lists. For example, Software Centre>History>Updates will show all the updates whether done by the apt-get update command or the Update Manager. Software and Updates will run apt-get update if we change the software sources by adding or removing a PPA.

There is always a kind of tug of war between making Ubuntu simple for the user and also giving the user access to all the functionality of Linux. Synaptic Package Manager is an example of a utility that does it all. And, as with a lot of things, Synaptic is easy to use once you know what you are doing. Even then you will notice that it will make use of Update Manager and Software & Updates to communicate with the user.

If we have one and only one over-reaching utility that does away with the need to do things another way, what happens when that utility breaks? How do we re-install the utility that does all the installing and removing of software when it itself is broken and needs re-installing and there is of other method to doing it?

Sometimes, it is better to have several small utilities than one very complicated utility even though there is overlap between the utilities. 

Regards.

---

### Post by steveo314 on 2015-06-26
Bloatware. On main stream commercial OSs they're seperate are they not? Apple has done it for years. Android does it. Windows is on the thin line of doing it. Ubuntu is trying to stray from Debian more and more and get closer to commercialization. I hope the day never comes when you have to pay for Ubuntu.

---

### Post by mikodo on 2015-06-26
> **steveo314 said:**
> Bloatware. On main stream commercial OSs they're seperate are they not? Apple has done it for years. Android does it. Windows is on the thin line of doing it. Ubuntu is trying to stray from Debian more and more and get closer to commercialization. I hope the day never comes when you have to pay for Ubuntu.
Mark has repeatedly stated that Ubuntu will always be free to use. Ubuntu depends heavily on the open source community for it's very being. Like the linux kernel, Debian,and community devs and people who volunteer their time in making it better. To stray too far from it being available to the community would be suicide. Canonical/Ubuntu are committed to other revenue streams versus selling the distro to the users. If part of the revenue stream is going to be the Software Center, so be it. For me, it just sits there. I don't use it.

---

### Post by deadflowr on 2015-06-26
I don't know if it still holds but it used to be that if the user's package list was busted or broken, then the software center would crash when it was opened.
On the other hand, the update manager/software updater would at least run, then tell you something about broken package count or something.
Merging the two would mean that those somewhat helpful outputs from the update manager wouldn't be seen (since to see them you would need to open the software center which of course would not open), and users would fumble about, in possibly comically misguided directions, trying to fix it without any clue as to how or why.

---

### Post by vasa1 on 2015-06-26
> **mikodo said:**
> ... For me, it just sits there. I don't use it.
When I last used Ubuntu, I simulated uninstalling it but doing so would bring down the house. Now I'm on Lubuntu which has a lighter software center and this one can be uninstalled.
```
07:18 AM ~ $ apt-get purge -s lubuntu-software-center
NOTE: This is only a simulation!
      apt-get needs root privileges for real execution.
      Keep also in mind that locking is deactivated,
      so don't depend on the relevance to the real current situation!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  lubuntu-software-center*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Purg lubuntu-software-center [0.0.8-0ubuntu1]
07:18 AM ~ $ 

```

---

### Post by wildmanne39 on 2015-06-26
I personally like the updater the way it is. I do not use software center, I use the terminal or synaptic.

---

### Post by mikodo on 2015-06-27
> **vasa1 said:**
> 
```
07:18 AM ~ $ apt-get purge -s lubuntu-software-center

```

I don't know what I am doing wrong.

Actually, I'm happy with it sitting there for now. But, for in the future, if it becomes something I don't want, I'll try again, (somehow).

```
mikodo@mikodo:~$ sudo apt-get purge -s xubuntu-software-center
[sudo] password for mikodo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xubuntu-software-center
mikodo@mikodo:~$ sudo apt-get purge -s ubuntu-software-center
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-software-center
mikodo@mikodo:~$ 
```

---

### Post by deadflowr on 2015-06-27
Ubuntu's software center is called simply software-center.
But I do not know what xubuntu uses...

---

### Post by mikodo on 2015-06-27
I guess it's called the same in Xubuntu as in Ubuntu.

Thanks.
> mikodo@mikodo:~$ sudo apt-get purge -s software-center
[sudo] password for mikodo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  software-center*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Purg software-center [13.10-0ubuntu4.1]
Edit:

Looking in Synaptic for "software center" in Xubuntu 14.04 on my main  and only install now, shows many dependencies. As not really knowing a  sniff about package management, I would never try purging software  center in this install.

I could test purging it, in a test install but, like I said earlier, I'm  fine with it just sitting dormant in the OS so, why make trouble?

---

### Post by Copper Bezel on 2015-06-27
Yeah, I don't see any reason to merge them simply because it's trendy. Apple, Android, and Microsoft do all integrate their updater into the software stores, and I could see the Software Center providing a front-end for the updater in one of its tabs or just a toolbar button to launch it, but I wouldn't want the full software center automatically launching itself every time there was a security update. The software center is meant to be a big, visible, browsable, user-facing app, while the updater is a small GUI utility front-end for technical stuff that has nothing to do with UX. I just don't see a real connection here.

---

### Post by kyle-kuhn on 2015-06-27
> **grahammechanical said:**
> What we are discussing here are just different front ends to apt-get and other system functions.
If we have one and only one over-reaching utility that does away with the need to do things another way, what happens when that utility breaks? How do we re-install the utility that does all the installing and removing of software when it itself is broken and needs re-installing and there is of other method to doing it?


That makes some sense, if the Software Center isn't working, the Software Updater can still work.

---

