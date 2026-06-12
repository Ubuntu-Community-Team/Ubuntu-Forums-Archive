---
title: "is this a concern."
date: 2016-04-25
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2016-04-25
Hey All,

Are these items a risk Mir & Snap(py) to privacy or is this just an overblown article.
Are theses in all versions of Ubuntu 16.04.

[http://www.networkworld.com/article/3060673/linux/popular-desktop-linux-distro-ubuntu-has-potentially-serious-privacy-flaw.html](http://www.networkworld.com/article/3060673/linux/popular-desktop-linux-distro-ubuntu-has-potentially-serious-privacy-flaw.html)

[http://mjg59.dreamwidth.org/42320.html](http://mjg59.dreamwidth.org/42320.html)

Thanks

---

### Post by QIII on 2016-04-25
Don't use Snap packages on your desktop...

:)

I agree with the author that if Snap packages are not secure on the desktop, Canonical should not market it that way -- they should, in fact, warn people.

---

### Post by poorguy on 2016-04-25
How does one determine if a package being downloaded is a Snap package. 
Is there a list or are the packages marked as a Snap package.

---

### Post by grahammechanical on 2016-04-25
Ubuntu 16.04 is still using the X server which it is admitted has potential security flaws that require the X server to be replaced with something else. There are, as far as I know two offered replacements that are under construction. Compositors based on the Wayland protocol and Mir which is being developed by Canonical/Ubuntu developers.

So, as to your second question, Mir is not in desktop Ubuntu 16.04. The Ubuntu phone & tablet OS is based on Ubuntu 15.04 code and using Mir & Unity 8, which is a version of Unity written to run on MIr.

Snap packaging is an evolution of the Click packaging used on the Ubuntu phone OS. Click packaging is itself a development of Debian packaging that is used on Ubuntu desktop. There are security features built into the packaging process of both Click & Snap which if not complied with by the app developer will prevent an app from being accepted in the app store.

Snappy Ubuntu core is a version of Ubuntu where the kernel is a snap and the OS is snap and all the apps are snaps. It does not have a desktop environment or a user interface. I have experimented installing a version of Ubuntu called Ubuntu Personal. It comes as an image file (personal_x86.img) & not as an installable ISO. It ran on MIr & had the Unity 8 user interface that is on the Ubuntu phone. And it was also snappy Ubuntu core. And it is very secure. But the experiment did not progress. There are as yet no builds of personal_x86.img built on 16.04 code.

If you are interested in understanding the principles of snappy Ubuntu core and any Ubuntu desktop distribution that may in future be built on it, then you can read about it here.

[https://developer.ubuntu.com/en/snappy/](https://developer.ubuntu.com/en/snappy/)

If we download applications from untrusted sources then we run a risk that we are installing code that has the potential to put security and privacy at risk. This is true with deb packages & rpm (RedHat) packages as it is with Click & Snap packages. I doubt very much if Matthew Garret's snap app would have been accepted into any Ubuntu snap store. And do not forget. His experiment was done with a distribution using the X server.

Personally, I will feel much more secure using Ubuntu Personal + Mir + Unity 8 + snaps then I would running any distribution built on Fedora and using the X server.

I will feel more secure using Firefox as a snap packaged application than I do using it as an X application packaged as a deb. Which is what we do now. The quicker applications get packaged as snap and we use them on 16.04, the safer we will all be.

Regards.

---

### Post by grahammechanical on 2016-04-25
If you want to see what snap apps are at present available on Ubuntu 16.04 then run this command

```
snap find
```

This is what you will see
> 
graham@sdb7-Dev:~$ snap find
Name                   Version                  Summary
audovia                3.2.1                    Database application for making music using JFugue MusicStrings
canonical-dragon       0.7.1                    The gadget snap for the dragonboard
canonical-i386         3.1                      The gadget snap for generic i386 systems
canonical-pc           3.1                      AMD64 generic package
canonical-pc-linux     4.4.0-18+20160419.13-26  The ubuntu-core kernel snap
canonical-pi2          3.2                      Raspberry Pi 2 support package
go-example-webserver   16.04-4                  Minimal Golang webserver for snappy
hello-world            6.0                      Hello world example
http                   4.6692016                HTTPie in a snap
links                  2.12-1                   Web browser running in text mode
moon-buggy             1.0.51.9                 Drive a car across the moon
nmap                   7.12SVN-0.4              Nmap ("Network Mapper") is a free and open source utility for network discovery and security auditing
notes                  0.0.8~snap3.gita80fd1c   Note-taking application, write down your thoughts
shout                  0.53.0                   A self hosted web IRC client
sshtron                1.0                      multiplayer Tron via ssh
tmux                   2.3bump1                 tmux
tor-middle-relay       0.2.7.6-6                Essential infrastructure node for Tor network
ubuntu-calculator-app  2.1+snap3                Ubuntu Calculator application for the Unity 7 desktop
ubuntu-clock-app       3.6+snap3                Ubuntu Clock application for the Unity 7 desktop
ubuntu-core            16.04+20160419.20-55     The ubuntu-core OS snap
xkcd-webserver         16.04-5                  Show random XKCD compic via a build-in webserver
yacas                  1.4.2                    Yet Another Computer Algebra System

At present, if you want to install a snap app you have to use a command. For example,

```
sudo snap install ubuntu-calculator-app
```

to remove a snap app

```
sudo snap remove ubuntu-calculator-app
```


Not all those snap apps are suitable for a desktop GUI.

Regards.

---

### Post by montag dp on 2016-04-25
These security concerns are not really a problem with snap packaging, but rather with X11.  They already exist in the current package format.  The articles do not make this very clear, but I think the main point is that, for now, snap packages on the desktop are not really more secure than debs, despite the claims to that effect.  They're not less secure either, though.  At least, that's what I have gathered from all this.

---

### Post by poorguy on 2016-04-25
Hey All,

Sounds as though more research is needed on this before anything is really known. It sure seems to sound like maybe some are jumping to fast to criticize before knowing what is happening or going to happen.

The good I have read about any of this was some thought the time to upgrade or move into the new release would be closer to the 16.04.1 release or until all of this could be implemented properly.

I am going to have to read the link grahammechanical posted to try and understand this better.
I guess we wait and see what Canonical & Ubuntu developers decide to do on this.

Thanks for the replies it does make better sense the way it is explained here.

Thanks.

---

