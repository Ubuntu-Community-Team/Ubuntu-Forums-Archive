---
title: "Gnome-Shell"
date: 2012-02-08
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by bmbaker on 2012-02-08
Latest update from ricotz/testing ppa which upgrades gnome-shell to 3.3.5 causes most of the base extensions to show errors in looking glass! I just downgraded gnome-shell to the last version gnome-shell_3.3.4+git20120206.c63fe5ee-0ubuntu1~12.04~ricotz0_amd64.deb to keep extensions wking. and disabled the ppa.

---

### Post by mdhollis on 2012-02-08
Same here.  The app menu and workspace indicator extension still work but that's about it..............

---

### Post by williammanda on 2012-02-08
Is this the proper ppa for the next gnome version for precise:

deb [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu) precise main

---

### Post by bmbaker on 2012-02-08
yes this has a up to date 3.3.4 version of gnome-shell 

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

you can add the ppa by typing this in a terminal

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install gnome-shell mutter gnome-shell-extensions gnome-tweak-tool

```

---

### Post by williammanda on 2012-02-08
I get and error for the extemsions

william@CI5:~$ sudo apt-get install gnome-shell mutter gnome-shell-extensions gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-shell-extensions

---

### Post by cariboo on 2012-02-08
> **williammanda said:**
> I get and error for the extemsions

william@CI5:~$ sudo apt-get install gnome-shell mutter gnome-shell-extensions gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-shell-extensions

If you look at the list of files, you'll see that gnome-shell-extensions is not available in that ppa.

---

### Post by Harry33 on 2012-02-08
> **williammanda said:**
> I get and error for the extemsions

william@CI5:~$ sudo apt-get install gnome-shell mutter gnome-shell-extensions gnome-tweak-tool
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnome-shell-extensions

That is because in official Precise repos there is no such package.
You can find gnome-shell-extensions from additional PPA's.
These are not official, so use them at your own risk.

---

### Post by mdhollis on 2012-02-08
The extensions are included in the ricotz/testing ppa that I am using. Most of them are broken after some updates today. I'm sure it will be resolved shortly.

---

### Post by Bobhuber on 2012-02-08
> **mdhollis said:**
> The extensions are included in the ricotz/testing ppa that I am using. Most of them are broken after some updates today. I'm sure it will be resolved shortly.
I loaded everything from the web8 PPA. All of it seems to be working fine.

---

### Post by mdhollis on 2012-02-08
> **Bobhuber said:**
> I loaded everything from the web8 PPA. All of it seems to be working fine.

Yeah it got to the point that gnome-shell wouldn't even run until I purged the gnome3 and ricotz/testing ppa's.  My issue is definitely related to these ppa's..........not precise.

---

### Post by pferraro on 2012-02-09
> **bmbaker said:**
> yes this has a up to date 3.3.4 version of gnome-shell 

[https://launchpad.net/~gnome3-team/+archive/gnome3](https://launchpad.net/~gnome3-team/+archive/gnome3)

you can add the ppa by typing this in a terminal

```
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install gnome-shell mutter gnome-shell-extensions gnome-tweak-tool

```

You don't need to install mutter to run gnome-shell.

---

### Post by hugmenot on 2012-02-09
Normally it’s enough to run something like this

```
sudo sed -i -e's/3.3.4/3.3.5/' {/usr,~/.local}/share/gnome-shell/extensions/*/metadata.json 
```

But this time they changed the JS API for the extensions and some of the extensions throw errors related to that. But the third-party extensions work.

---

### Post by bmbaker on 2012-02-09
> **pferraro said:**
> You don't need to install mutter to run gnome-shell.

True but if your gonna run gnome-shell from ppa's you might as well run it the way its intended :-)

---

### Post by cariboo on 2012-02-09
> You don't need to install mutter to run gnome-shell.

Mutter is the window manager that gnome-shell uses, without it, nothing will work.

---

### Post by prusswan on 2012-02-09
when is this actually going into the dist?

---

### Post by jbicha on 2012-02-09
GNOME Shell 3.4 will show up in the normal Ubuntu repositories in May or June. In other words, Ubuntu 12.04 will include GNOME Shell 3.2, not 3.4. I explained a bit about the reasoning in my [blog]("http://ubuntuforums.org/jeremy.bicha.net/2012/02/01/gnome-versions-for-ubuntu-1204").

You don't need to install mutter manually; installing gnome-shell will install mutter for you as it's a required dependency.

---

### Post by hugmenot on 2012-02-10
Jeremy, the mixing of components is a bit problematic. In some areas they’ve moved on to new systems and we are stuck with the old tech.

For instance, the new media-keys stuff is in gnome-settings-daemon, but we have the old one, so we cannot set keyboard shortcuts in gnome-control-center now.

The g-s-d issue is the most grave. I don’t get putting up with the inconsistencies is better than just ficing unity-greeter.

---

### Post by hugmenot on 2012-02-10
Also, using Gnome3 PPA and even ricotz/testing gives a much better experience in Gnome Shell. At least for me, because I much prefer vanilla or maybesligtly stracciatella Gnome.

---

### Post by hugmenot on 2012-02-10
Jeremy, will you put g-s-d 3.4 into the PPA for the people who don’t care for Unity?

---

