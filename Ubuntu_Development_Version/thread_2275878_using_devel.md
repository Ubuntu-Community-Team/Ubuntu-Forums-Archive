---
title: "using /devel/"
date: 2015-04-29
forum: Ubuntu Development Version
---

### Post by ventrical on 2015-04-29
I have been doing this for quite some time now before the next cycle begins.

Here's so far:

```

Hit http://ca.archive.ubuntu.com devel-backports/restricted Translation-en     
Hit http://ca.archive.ubuntu.com devel-backports/universe Translation-en       
Fetched 263 kB in 14s (17.6 kB/s)                                              
Reading package lists... Done
W: Conflicting distribution: http://archive.canonical.com devel Release (expected devel but got precise)
W: Conflicting distribution: http://security.ubuntu.com devel-security Release (expected devel-security but got vivid)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel Release (expected devel but got vivid)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel-updates Release (expected devel-updates but got vivid)
W: Conflicting distribution: http://ca.archive.ubuntu.com devel-backports Release (expected devel-backports but got vivid)
ventrical@ventrical-luntiy-betatest:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  ca-certificates libnm-glib-vpn1 libnm-glib4 libnm-util2 network-manager
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 1,178 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://ca.archive.ubuntu.com/ubuntu/ devel-updates/main libnm-util2 amd64 0.9.10.0-4ubuntu15.1 [134 kB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ devel-updates/main libnm-glib-vpn1 amd64 0.9.10.0-4ubuntu15.1 [14.4 kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ devel-updates/main libnm-glib4 amd64 0.9.10.0-4ubuntu15.1 [84.7 kB]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ devel-updates/main ca-certificates all 20141019ubuntu0.15.04.1 [191 kB]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ devel-updates/main network-manager amd64 0.9.10.0-4ubuntu15.1 [754 kB]
Fetched 1,178 kB in 4s (290 kB/s)      

```

---

### Post by zika on 2015-04-29
As I wrote (at least) once before that gives credit and shows how nicely apt evolved in a very robust mechanism of resolving contradictory requests...
Is it not easier just to check (let me say manually) contents of Ubuntu archive?
Upgrades You've got are Vivid upgrades You'd get without introducing devel into whole process.

---

### Post by ventrical on 2015-04-29
As I wrote once before, (several times) I have more than several different hard-drives and various form factors that are just sitting statically so it is no waste for me to change the /viivid/ to /devel/ because  it is more convenient for me to just log in to that install and just run:

```

sudo apt-get update
sudo apt-get dist-upgrade


```

I know it is early but in several cycles I used this process and when upgrades were available that pertained to the next cycle they were downloaded and installed. Of course there is  ubuntu.info template but I have been successful in installing that after the fact.

Regards..

---

### Post by zika on 2015-04-29
Yes. I do have only one install and I do all my work on it (plus backup) and that forces me to be on my toes and prepare each change and pay for each and every mistake. That is the difference of how we see testing... ;)
I did answer in this thread only because the title is what it is. :) I, simply put, do not see that that is the way to &#8222;use /devel/&#8220;... Even if it existed... 8)

---

### Post by ventrical on 2015-04-29
> **zika said:**
> Yes. I do have only one install and I do all my work on it (plus backup) and that forces me to be on my toes and prepare each change and pay for each and every mistake. That is the difference of how we see testing... ;)
I did answer in this thread only because the title is what it is. :) I, simply put, do not see that that is the way to „use /devel/“... Even if it existed... 8)

> 
That is the difference of how we see testing... :wink:


This is not about how you assume  "we" see testing and the difference thereof. It is about a process I use prior to the official release of the named development cycle (which is Mark Shuttleworth's naming convention). I have been doing this since 11.10 and it has always worked to get early files and tool chains and that keeps me on my toes:)

Regards..

---

### Post by grahammechanical on 2015-04-29
With me it is curiosity. I do not see it as a hardship to change the repositories to the next development release every six months. Or to wait until the second or third week of the new development cycle to get an ISO image and put in a fresh install.

So, I have an install of vivid on vivid repositories and an install of vivid on devel repositories and as of today they both get the same small number of updates. But that may change.

I think the situation would be the same if I knew the new code name and changed the repositories to that code name. I expect at first to get the same updates as vivid but then to get more and different updates as the two code bases diverge.

I just hope that we do not have to wait until after the online summit for things to get moving. Oh, one more thing. I am curious to see if this naming convention continues with the Ubuntu that will be built on Snappy Personal.

Regards.

---

### Post by dino99 on 2015-04-29
> **grahammechanical said:**
> 

 if I knew the new code name and changed the repositories to that code name.

WW is out and hiden [http://old-releases.ubuntu.com/releases/4.10/](http://old-releases.ubuntu.com/releases/4.10/) :shock::shock:

but you might get something new next week with a newer WW  :p

---

### Post by ventrical on 2015-04-29
> **grahammechanical said:**
> With me it is curiosity. I do not see it as a hardship to change the repositories to the next development release every six months. Or to wait until the second or third week of the new development cycle to get an ISO image and put in a fresh install.

So, I have an install of vivid on vivid repositories and an install of vivid on devel repositories and as of today they both get the same small number of updates. But that may change.

Regards.

Precisely my point! However, from what I read, 'apt-get' is supposed to be replaced with 'snappy' with 'snappy' being the new command but of course that is for Ubuntu-Core testing. I have been experimenting with snappy on local kvm. It loads up and all but there are very few apps .. etc.. just some basic commands to tell you about what apps are loaded and snappy core info .. etc..

Regards..

---

### Post by Elfy on 2015-04-29
> **ventrical said:**
> Precisely my point! However, from what I read, 'apt-get' is supposed to be replaced with 'snappy' with 'snappy' being the new command but of course that is for Ubuntu-Core testing. I have been experimenting with snappy on local kvm. It loads up and all but there are very few apps .. etc.. just some basic commands to tell you about what apps are loaded and snappy core info .. etc..

Regards..

I think you'll find that apt-get is not going anywhere for a good while.

---

### Post by ventrical on 2015-04-29
> **Elfy said:**
> I think you'll find that apt-get is not going anywhere for a good while.

ahem .. :) 

> 
Since this is a snappy system, the old mechanisms for package install and updates don't work!
    $ apt-get update
Ubuntu Core does not use apt-get, see 'snappy --help'
$ sudo apt-get install docker
Ubuntu Core does not use apt-get, see 'snappy --help' 
   OK, we're not in Kansas any more :)
  Let's go ahead and see if there is an updated system for us. The  update&#8208;versions command will check the store for newer versions of any  installed components. If you are fully up to date, you will see the same  versions listed which are currently installed:


[https://developer.ubuntu.com/en/snappy/tutorials/using-snappy/](https://developer.ubuntu.com/en/snappy/tutorials/using-snappy/)

Regards..

---

### Post by Elfy on 2015-04-29
ahem

" elfy: only what I've been saying, that it shouldn't affect flavors unless they choose to adopt it"

"if it hurts flavors in any direct way, that's a bug"

Regards ...

Ubuntu might use this new way - doesn't mean anyone else will.

---

### Post by ventrical on 2015-04-29
Ok elfin Lord of the Rings :)  I am curbing my enthusiasm. ;)

Regards..

---

### Post by Elfy on 2015-04-29
Not got a problem with enthusiasm - it is early in the cycle :)

I will though - always try and remind everyone that there is more to *Ubuntu* than Ubuntu and phones ;)

---

### Post by ventrical on 2015-05-04
Policykit no longer a registered authentication agent.

```

Unpacking policykit-1 (0.105-8ubuntu3) over (0.105-8ubuntu2) ...
Processing triggers for dbus (1.8.12-1ubuntu5) ...
Processing triggers for man-db (2.7.0.2-5) ...
Setting up libpolkit-gobject-1-0:amd64 (0.105-8ubuntu3) ...
Setting up libpolkit-agent-1-0:amd64 (0.105-8ubuntu3) ...
Setting up libpolkit-backend-1-0:amd64 (0.105-8ubuntu3) ...
Setting up dnsmasq-base (2.72-3ubuntu0.1) ...
Setting up policykit-1 (0.105-8ubuntu3) ...
PolicyKit daemon disconnected from the bus.
We are no longer a registered authentication agent.
Processing triggers for libc-bin (2.21-0ubuntu4) ...
ventrical@ventrical-luntiy-betatest:~$ 

```

---

### Post by grahammechanical on 2015-05-06
My vivid install on devel repositories has just received an updated base-files packages. This means that it has rolling over into Wily Werewolf

> graham@sdb1-Uplus1:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Wily Werewolf (development branch)
Release:    15.10
Codename:    wily


This was the case at the start of the last development cycle.

Regards.

---

### Post by ventrical on 2015-05-06
> **grahammechanical said:**
> My vivid install on devel repositories has just received an updated base-files packages. This means that it has rolling over into Wily Werewolf



This was the case at the start of the last development cycle.

Regards.

As which was the same case for me. I then switched  it over to /wily/.

Regards..

---

