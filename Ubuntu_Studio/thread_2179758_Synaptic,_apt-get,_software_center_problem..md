---
title: "Synaptic, apt-get, software center problem."
date: 2013-10-09
forum: Ubuntu Studio
---

### Post by Tristan_Williams on 2013-10-09
Here lately, i have not been able to install any software that i don’t already have the repo for. I can try to add a repo, and sometimes it even tells me it successfully added the repo, but it never does. I am stuck.

sudo apt-get install openscad --> do you want to continue [y/n] --> install these packages without verification? [y/n]

after answering yes it gets stuck at "0% [Waiting for headers] [Waiting for headers]"
i try to exit and its still stuck. terminal closes but apt-get still goes on. 

so i then decide ill just do it from synaptic (after rebooting because i cant exit from apt-get and cant stop it with htop)
once in synaptic, i find my package, mark for installation, and confirm that i want to install the other related packages.

upon clicking "Apply all Marked Changes" i get a dialogue box. The only part of the dialogue box that catches my attention says:

"10 new packages will be held back and not upgraded"

I go on and click "apply", at which point, it gets stuck with a dialogue box saying "downloading package file" but never making any progress.


Now for the software center. 

I find openscad, click install, and software center says "requires installation of untrusted packages". 
I click the "repair" button (5 times because the dialogue box appears 5 times)

After this, the software center informs me that it failed to download repository information.

I should also state that install.sh is not working either.



I have no idea what to do because i cant install anything anymore.
Please help

---

### Post by ian-weisser on 2013-10-09
Open a terminal.
Enter the following command. The system will prompt you for your password. Paste the entire response here (it may be long).
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by Tristan_Williams on 2013-10-09
should I redirect stdout to file or just copy/paste from shell?

---

### Post by Tristan_Williams on 2013-10-09
Ok i ran the command and this is what i got:

```
tristan401@tristan401-Vostro-220-Series:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for tristan401: 
Err http://repo.steampowered.com precise Release.gpg                                                                                                        
  Connection failed
Err http://extras.ubuntu.com raring Release.gpg                                                                                                             
  Connection failed
Ign http://repo.steampowered.com precise Release                                                                                                            
3% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]

```

It is stuck at that last line, and makes no progress past 3%

---

### Post by ian-weisser on 2013-10-10
1) Do you have any other network issues? Or have you knowingly installed a proxy?

2) Open your Software Sources control panel (1).
In the 'Ubuntu Software' tab, select a different mirror.
In the 'Other Software' tab, disable the repository: [http://repo.steampowered.com](http://repo.steampowered.com) (just disable, not delete)


3) Try **sudo apt-get update && sudo apt-get upgrade** again.


To open Software Sources:
a) It's a menu option in Software Center
b) It's the 'repositories' menu option in Synaptic
c) It's the software-properties-gtk command in a terminal

---

### Post by Tristan_Williams on 2013-10-10
I think i remember installing some sort of proxy related software. How would i go about uninstalling that? 
I have no idea what its name was or the package it came from.

Anyways i followed your steps and this was the output.

```

tristan401@tristan401-Vostro-220-Series:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for tristan401: 
E: Could not get lock /var/lib/apt/lists/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/lib/apt/lists/
tristan401@tristan401-Vostro-220-Series:~$ 

```

So i rebooted because htop was of no help trying to kill the previous apt-get.

I ran the code again and this is what i got:

```

tristan401@tristan401-Vostro-220-Series:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for tristan401: 
0% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]

```

so now it does less than before... Does it matter which mirror i choose?

---

### Post by jejeman on 2013-10-10
> Does it matter which mirror i choose? Yes, stick to main.

---

### Post by Tristan_Williams on 2013-10-10
Ok. I changed from "Server for united states" to "Main Server"

Then i disabled the steampowered repo. 

It is still getting stuck as soon as i enter my sudo password. 

If i did have a proxy (i may or may not have installed one, i cant quite remember) how would i go about disabling it or removing it? I have tried doing it through /etc/apt/apt.conf but that file does not exist on my computer and the apt.conf.d folder has no proxy related files or settings.

---

### Post by ibjsb4 on 2013-10-10
I don't think its proxy.

[http://en.wikipedia.org/wiki/Proxy_server](http://en.wikipedia.org/wiki/Proxy_server)

Try:

```
sudo apt-get -f install
```

Look for errors.

---

### Post by Tristan_Williams on 2013-10-10
I ran the command "sudo apt-get -f install"

output:
```

tristan401@tristan401-Vostro-220-Series:~$ sudo apt-get -f install
[sudo] password for tristan401: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  jsvc libcommons-daemon-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
tristan401@tristan401-Vostro-220-Series:~$ 

```

Im not sure that this "jsvc libcommons-daemon-java" package is any of the problem...

Basically at this point, **i can't perform any sort of installation** (even from debs or install.sh scripts) **or perform any updates, or upgrades**.

sudo apt-get update (or upgrade / install / autoremove / autoclean) always gets stuck looking for headers. 



This is becoming a major problem as there is software i need for various projects i have going which are my only income.

---

### Post by ibjsb4 on 2013-10-10
Enter these commands (one line at a time) in terminal.
```

sudo -i
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get update
```

Got that idea from here.

[http://fumerf.blogspot.com/2013/03/ubuntu-not-updating-0-waiting-for.html](http://fumerf.blogspot.com/2013/03/ubuntu-not-updating-0-waiting-for.html)

Their way deletes the directory, my way saves it as backup.

---

### Post by Tristan_Williams on 2013-10-10
Im not sure if this will be of any help, but its worth a try.

Here is the list of repos currently listen by synaptic:

Canonical Partners
Canonical Partners(source code)
Independent
Independent(source code)
[http://repo.steampowered.com/steam/](http://repo.steampowered.com/steam/)
[http://ppa.launchpad.net/chrysn/openscad/ubuntu](http://ppa.launchpad.net/chrysn/openscad/ubuntu)
[http://ppa.launchpad.net/pmcenery/ppa/ubuntu](http://ppa.launchpad.net/pmcenery/ppa/ubuntu)
[http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu)
[http://archive.getdeb.net/ubuntu](http://archive.getdeb.net/ubuntu)
[http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu](http://ppa.launchpad.net/minecraft-installer-peeps/minecraft-installer/ubuntu)

Most of those also have a duplicate entry with "source code" added at the end.
[http://ppa.launchpad.net/chrysn/openscad/ubuntu](http://ppa.launchpad.net/chrysn/openscad/ubuntu) has two "source code" duplicates

Do you notice anything in there that could be causing this problem... i have done research on google and through this forum and other people seem to have this problem once or twice but i have not found any sort of solution yet


Edit:

I followed those commands and at the "apt-get update" it gets stuck like always
```

tristan401@tristan401-Vostro-220-Series:~$ sudo -i
[sudo] password for tristan401: 
root@tristan401-Vostro-220-Series:~# cd /var/lib/apt
root@tristan401-Vostro-220-Series:/var/lib/apt# mv lists lists.old
root@tristan401-Vostro-220-Series:/var/lib/apt# mkdir -p lists/partial
root@tristan401-Vostro-220-Series:/var/lib/apt# apt-get update
0% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]

```



Edit again:

When i go to software center, i go to the software i want (i know the problem isnt fixed im just constantly checking in hope) and it gives me a "not found" message

---

### Post by ibjsb4 on 2013-10-10
Please post the output of:

```
cat /etc/apt/sources.list
```

---

### Post by Tristan_Williams on 2013-10-10
I left the previous apt-get running. This is what it says so far:

```

Err http://extras.ubuntu.com raring Release.gpg                                                                 
  Connection failed
Err http://archive.getdeb.net precise-getdeb Release.gpg                                                        
  Connection failed
Err http://archive.canonical.com raring Release.gpg                                                             
  Connection failed
Err http://archive.ubuntu.com raring Release.gpg                                                                
  Connection failed
Err http://ppa.launchpad.net raring Release.gpg                                                                 
  Connection failed
Ign http://extras.ubuntu.com raring Release                                                                     
Ign http://archive.getdeb.net precise-getdeb Release                                                            
Ign http://ppa.launchpad.net raring Release                                                                      
Ign http://archive.canonical.com raring Release                                                                  
Err http://archive.ubuntu.com raring-updates Release.gpg                                                         
  Connection failed
Err http://archive.ubuntu.com raring-security Release.gpg                                                        
  Connection failed
14% [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers] [Waiting for headers]

```


So i guess something is causing me to not be able to connect to any sources???

---

### Post by Tristan_Williams on 2013-10-10
The output of cat /etc/apt/sources.list

```

tristan401@tristan401-Vostro-220-Series:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu-Studio 13.04 _Raring Ringtail_ - Release i386 (20130424)]/ raring main multiverse restricted universe

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://archive.ubuntu.com/ubuntu raring main restricted
deb-src http://archive.ubuntu.com/ubuntu raring multiverse restricted universe main #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu raring-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-updates multiverse restricted universe main #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu raring universe
deb http://archive.ubuntu.com/ubuntu raring-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://archive.ubuntu.com/ubuntu raring multiverse
deb http://archive.ubuntu.com/ubuntu raring-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb http://archive.ubuntu.com/ubuntu raring-security main restricted
deb-src http://archive.ubuntu.com/ubuntu raring-security multiverse restricted universe main #Added by software-properties
deb http://archive.ubuntu.com/ubuntu raring-security universe
deb http://archive.ubuntu.com/ubuntu raring-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu raring partner
deb-src http://archive.canonical.com/ubuntu raring partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu raring main
deb-src http://extras.ubuntu.com/ubuntu raring main
deb http://archive.ubuntu.com/ubuntu raring-proposed universe main multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu raring-proposed universe main multiverse restricted #Added by software-properties
tristan401@tristan401-Vostro-220-Series:~$ 


```

---

### Post by Tristan_Williams on 2013-10-10
Could this be the problem/solution?
[http://askubuntu.com/questions/88992/what-to-try-when-apt-get-install-xxx-results-in-connection-failed](http://askubuntu.com/questions/88992/what-to-try-when-apt-get-install-xxx-results-in-connection-failed)



Edit:

I will answer my own question... No thats not the answer, it may or may not be the problem.
When i go through with the "Select best server" button it takes 20 minutes running tests just to inform me that there is no suitable server, and that my internet connection is the problem (its not)

---

### Post by Tristan_Williams on 2013-10-11
Ok now i dont know whether to be mad or happy... Somehow, everything works perfect now. 5 minutes ago it was more broke than ever, and now it works fine. And i didnt even change anything since it wasnt working. 

Oh well i wont question it...

Edit: 

Spoke too soon. It in fact does not work...

---

### Post by ian-weisser on 2013-10-11
1) You mentioned that install.sh doesn't work either. Can you explain?

> **Tristan_Williams said:**
> I think i remember installing some sort of proxy related software. How would i go about uninstalling that? 
I have no idea what its name was or the package it came from.

2) Do you recall why you installed it?

Take a look at the three methods of redirecting apt http requests shown [https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy](https://help.ubuntu.com/community/AptGet/Howto#Setting_up_apt-get_to_use_a_http-proxy)
3) Did you set up a file /etc/apt/apt.conf sometime in the past? 

4) Do you recall any changes you made around the time apt downloads stopped working?

---

### Post by Tristan_Williams on 2013-10-11
No i don&#8217;t recall why I installed the proxy.

Changes i made prior to this problem would include:

1) trying to install OpenSCAD. That's when i discovered the problem.

2)I Recently installed Conky

3) I recently had a proxy related problem with firefox, in which i had to select the "no proxy" option because there was some sort of system proxy keeping me from doing anything on Firefox / Chromium.

I have tried deleting the Environment variables for all proxy's and tried unsetting them, also i have tried removing it with dconf

When i run "env | grep proxy" i get no results.

---

### Post by ian-weisser on 2013-10-14
Here are three ways to set up a proxy. Check if you did any of them: [http://askubuntu.com/questions/150210/how-do-i-set-systemwide-proxy-servers-in-xubuntu-lubuntu-or-ubuntu-studio](http://askubuntu.com/questions/150210/how-do-i-set-systemwide-proxy-servers-in-xubuntu-lubuntu-or-ubuntu-studio)

Here is a fourth way: [http://askubuntu.com/questions/134867/proxy-configuration-change/134902](http://askubuntu.com/questions/134867/proxy-configuration-change/134902)

---

