---
title: "LXC awesome, but how can we run multiple GUI desktops?"
date: 2015-03-31
forum: Ubuntu, Linux and OS Chat
---

### Post by DuckHook on 2015-03-31
I've recently started playing around with LXC and am blown away by it&#8213;from the little that I so far know of it that is. Until [this]("http://ubuntuforums.org/showthread.php?t=2261630&p=13211681#post13211681") recent thread (thanks ian-weisser ):P), I didn't even know of its existence! Now, I've gotten as far as installing both a privileged and an unprivileged CLI container, downloading CLI apps and beginning the exploration process. Conceptually, it's an amazing environment replicating the good in a VM (sandboxing, security, snapshots) while avoiding much of the bad (heavily degraded performance, duplicated resources, wasted space).

I've also always wanted to run multiple instances of complete desktop environments on the other TTYs of a typical Ubuntu install. Containers should be almost ideal for what I'm trying to do. So, I would <Ctrl>+<Alt>+<F1> and start an instance of Lubuntu, <Ctrl>+<Alt>+<F2> for Xubuntu, <Ctrl>+<Alt>+<F3> for Kubuntu, <Ctrl>+<Alt>+<F4> for a pure CLI, etc. So far, the pure CLI is a piece of cake and runs like a champ. But I don't know how to get an X11 session running. It should be possible in principle, and [this]("http://unix.stackexchange.com/questions/18003/linux-lxc-deploying-images-with-tiniest-possible-x11") StackExchange thread claims that it's been done. But, like so many things Linux, the instructions in above thread are maddeningly obscure, incomplete and almost impossible for a non-guru to understand, much less follow. Googling has not helped.

Has anyone here ever succeeded in doing the above? Does anyone share my enthusiasm for it? Any sites or blogs with simple step-by-step instructions I can be pointed to? As always, your input and suggestions are deeply appreciated.

Some references for the curious:

[https://linuxcontainers.org/lxc/getting-started/](https://linuxcontainers.org/lxc/getting-started/)
[https://help.ubuntu.com/community/LXC](https://help.ubuntu.com/community/LXC)
[https://help.ubuntu.com/lts/serverguide/lxc.html](https://help.ubuntu.com/lts/serverguide/lxc.html)
[https://www.stgraber.org/2013/12/20/lxc-1-0-blog-post-series/](https://www.stgraber.org/2013/12/20/lxc-1-0-blog-post-series/)

**Cautionary note**

It is very apparent to me that LXC is, if not bleeding-edge, then awfully close to being so. There are no GUI config tools (to my limited knowledge), no how-tos beyond the very basics, and you are pretty much on your own trying to dive any deeper than the superficial level. Compared to the ease of installing a VM, getting LXC to run is a little like assembling a transmission. Newbies could be quickly overwhelmed, so approach with a realistic set of expectations.

---

### Post by grahammechanical on 2015-03-31
I have succeeded in running Unity 8 in LXC. And I was able to login to the Unity8 session at the LightDM login screen. But I claim no credit. I followed a tutorial by Nick Skaggs, a Canonical engineer with responsibilty for QA.

[https://wiki.ubuntu.com/Unity8inLXC](https://wiki.ubuntu.com/Unity8inLXC)

From there I managed to set up another container and install Ubuntu into it but I could not work out how to login to it as a running OS. I was able to access what was in the container but I did not get very far in using LXC as an alternative to a VM. Which is what I would very much like to do. I would like to indentify the scripts that Nick used and butcher them so that I can run other installs and not just Unity8.

I think that part of the problem is LXC is seen very much as a server thing and not so much as an alternative to a VM on the desktop. And there is now an LXD. It is all beyond me.

Regards.

---

### Post by DuckHook on 2015-03-31
> **grahammechanical said:**
> ...It is all beyond me.If you think it's beyond *you*, imagine the effect on an idiot like *me*.

But I did find [this]("http://www.linuxquestions.org/questions/linux-virtualization-and-cloud-90/outputting-x-display-from-inside-an-lxc-container-4175448081/").

If I understand properly, the author of that thread is leveraging a built-in remote display manager in Ubuntu (that I didn't even know existed), but instead of using it to access a physically remote xsession, is "fooling" it to display a resident container on an unused tty by using the NAT IP address of the container. The remote display manager doesn't know the difference, so displays the container contents just like a remote desktop. Verrrry slick... *if* I can get it to work.

...and the very first problem I run into is... the only lightdm.conf file I can find in my whole filesystem is /etc/init/lightdm.conf and it does not look at all like a classical config file (with headers and variables defined beneath each header). Rather, it is very script-like with all sorts of tabbed lines and codespeak and I really don't want to mess with it. Perhaps lightdm.conf has changed drastically from 12.04 (when his thread was written) to 14.04, but it's this sort of stuff that makes figuring out LXC so awful.

Will report on progress as (when? if?) it occurs.

---

### Post by grahammechanical on 2015-03-31
As one idiot to another, that is an interesting link. I will get back to it tomorrow. It is time for bed right now. There are other lightdm files around and things do move around from on version of Ubuntu to another. Tomorrow I will load up my vivid install of unity8 in LXC and have a nose around. Nick Scaggs wiki page says that lightdm needs to be modified.

Also, Linux loads on tty1. Ubuntu runs on tty7 and if we install Ubuntu Desktop Next the lightdm login screen will be in tty7 but when the switch is made to Mir and Unity8 it runs on tty8.

Regards.

EDIT: the place to look is /usr/share/lightdm/lightdm.conf.d/

And we either edit 50-unity-greeter.conf  It has

> [SeatDefaults}
greeter-session=unity-greeter

Or 50-ubuntu.conf.   It has

> [SeatDefaults]
user-session=ubuntu

Or we create our own text file. The Unity8 in LXC install as in that folder 55-unity8.conf which contains

> [SeatDefaults]
user-session=unity8-mir
unity-compositor-command=unity-system-compositor.sleep
session-wrapper=lightdm-unity8-session

It is the last line the interest me. I guess it puts the unity8 session as an option in the lightdm login screen. I am also guessing it would be in a text file such as this that we put some command to start ubuntu or whatever flavour we are experimenting with.

I have noticed that the different flavours that I have installed also have their own text file in /lightdm.conf.d. So, Ubuntu Gnome has a 60-gnome.conf. And Xubuntu,Lubuntu and Kubuntu have similar texts files. They are the equivalent of 50-ubuntu.conf but for that flavour as the user-session=

---

### Post by DuckHook on 2015-04-01
I'm soon going down for my beauty sleep too. So a brief report before turning in:

1. After creating new container, went through the whole apt-get install lubuntu-desktop routine.
2. Then tried the "easy" step in the linked thread: Xorg -terminate -query 192.168.1.12 :1   #subbing proper IP address
3. No joy. But getting closer. System tries switching to tty8 (good thing) but just black screen followed by dropped signal to monitor(s).
4. Ctrl + Alt + F7 gets back to host. No damage done.
5. Can ssh into container, so it's not damaged either.
6. After three or four minutes, tty8 clears, display flickers, output spits out to terminal.

Will post output tomorrow along with container Xorg.0.log but too sleepy now. Am hopeful. Two steps forward, one step back. Will try your settings tomorrow too.

---

### Post by DuckHook on 2015-04-02
Further update:

Still no joy. A lot of small irritations and one  real killer. Tried both privileged and unprivileged containers  using all combos of sudo and no sudo, but no go. It's easy to get to a  console just using lxc-console, but that's not the objective.

However,  trying to run VBox concurrently with LXC completely blew up in my face.  System went into total freeze. Could not SSH or REISUB. No alternative  but to pull the plug. Luckily, no lost work, but just asking for file  and system corruption. Not good. Am not nearly as enthusiastic as before  and approaching this technology with a newfound sense of sobriety.

---

### Post by grahammechanical on 2015-04-02
Well, the first day of the fourth month really took me for an April fool. I thought I would install unity8 in lxc and poke around in it. I tried two fresh installs, one of 15.04 and one of 14.04. And I did not get what I wanted. Unity8 is not doing very well at the moment. And those lightdm config files that I reported on are no longer installed. It is as if lxc has been especially modified or complied just for unity8. The first of the month was a disappointing day and I had such high hopes.

I am now on a fresh install of 15.04 with plain but not so simple lxc. I installed Ubuntu in a container easily enough for there is a template in /usr/share/lxc/templates/ that does the work. In fact that folder has templates for all kinds of distros but not for the flavours of Ubuntu. And I cannot workout how to modify the Ubuntu template to install a flavour. It points to the Ubuntu archives and all the flavours use the same archives. So, how does it download Ubuntu and not some other flavour?

Of course the big issue remains. How to use a container as if it was a VM.

---

### Post by DuckHook on 2015-04-02
@ grahammechanical

Two further links that could be useful.

[https://github.com/ustuehler/lxc-desktop](https://github.com/ustuehler/lxc-desktop)

... if it works, it's almost like cheating. Keep in mind that I am not remotely a Git-level user, but as far as I can tell, the author has created a Debian source package and uploaded it to Git. Cloning this package from Git and installing it should yield a privileged container that starts up in the next available tty (likely F8). According to the author, it is "dead" simple (he used a more piquant expression) to get this up and running. After my last misadventure, I'm not doing this on anything other than my experimental box, which is currently lying in pieces on the assembly table, so won't get around to it until next week at the earliest.

If it works, it will be a no-brainer, but strangely unfulfilling. Will have arrived at destination without really taking care of the itch, if you know what I mean. Part of the motivation in undertaking this was to figure out what is happening...

...which led me to this:

[http://ghanima.net/doku.php?id=wiki:lxc:deinlxc](http://ghanima.net/doku.php?id=wiki:lxc:deinlxc)

Far more intricate and obscure, but has the huge advantage of being implemented inside a VM as a proof of concept. I might just tackle this first, but have to work up the nerve.

If someone else works up the nerve first, please post results and any pitfalls we could look out for/avoid.

**Second thoughts**

It is worth noting that the first link carries a further danger for the unwary: since I for one don't know this author from Adam, I need to think *really* carefully about running a Debian source package he has put together (and especially under sudo). The gurus are no doubt aware of this danger. ...so a reminder to all us mortals.

---

### Post by grahammechanical on 2015-04-03
The software centre has ubuntu-dev-tools. It is described as "a collection of useful tools that Ubuntu developers use to make their packaging work a lot easier." So, I think that ubuntu-dev-tools is safe.

One of the things it does is "pull-debian-source." So, I guess it pulls in lxc-desktop. There are those who say that getting to the top of mount Everest is no fun if you go up by escalator. But if I am going to use Linux Containers to run multiple development versions as if using a VM, then I do not want a lot of messing around.

P.S. I hope that this is not another example of an expert saying how easy it is to do without seeing things from the ignorant persons perspective.

---

### Post by grahammechanical on 2015-04-03
Well, I must have prostrate trouble as it is not as easy as the developer says. First, we need git installed. Then running

```
dpkg-buildpackage -uc -us
```

gives this error

> dpkg-buildpackage: warning: build dependencies/conflicts unsatisfied; aborting
dpkg-buildpackage: warning: (Use -d flag to override.)


using the -d flag gives this

> dh clean
make: dh: Command not found
debian/rules:3: recipe for target 'clean' failed
make: *** [clean] Error 127
dpkg-buildpackage: error: fakeroot debian/rules clean gave error exit status 2


If you cannot take a joke, you should not have joined. :)

EDIT: I am a little bit further along. Before running the commands to download and build lxc-desktop run these two commands

```
sudo apt-get install git
sudo apt-get install dh-make
```

I am not yet able to say that lxc-desktop works as it is supposed to work.

---

### Post by grahammechanical on 2015-04-03
Well, I go a lot further this time. I have made a list of the instructions. And when I start the container I get this
> 
sudo lxc-info --name Ubuntu
Name:           Ubuntu
State:          RUNNING
PID:            10014
IP:             10.0.3.151
CPU use:        1.96 seconds
BlkIO use:      30.29 MiB
Memory use:     47.08 MiB
KMem use:       0 bytes
Link:           vethMB58AT
 TX bytes:      2.79 KiB
 RX bytes:      7.48 KiB
 Total bytes:   10.26 KiB

But this is the bit that I am not yet seeing

> Within a few seconds you should get a graphical Ubuntu Desktop login screen on the next available virtual terminal.

And I tried to install Xubuntu into a container and it failed because there is not an LXC template for Lubuntu.

---

### Post by grahammechanical on 2015-04-08
I finally give up on this. I have been working my way through it and every time I think I am making progress there is a failure.

I tried with vivid vervet as the host and I was able to install vivid into a container using lxc-desktop but after starting the container and switching to tt8 I get a black screen with a flashing cursor and nothing else.

I tried with 14.04.2 and when I tried to create a container with vivid in it using lxc-desktop the container failed to create.

I tried with the standard lxc-create command and I succeeded in creating the container but after starting the container and switching to tty 8 I got the same black screen with a flashing cursor.

I have confirmed that LightDM, Compiz, Ubuntu desktop and Unity are all installed. As It will not be possible to install the flavours because there are no LXC templates for the flavours and I cannot get this stuff to work any way I have decided that enough is enough.

Regards.

---

### Post by ventrical on 2015-04-09
@grahammechanical

  I thought we did something similar to this when we were experimenting with unity8. I know the thread is in development version, (I'll  have to look it up ) :) but as I recall I was just using a startx command and I was able to switch from razorqt to xmonad to unity8 desktops .. all running in parallel.

  I'll see if I can dig it up.
Regards

---

### Post by ventrical on 2015-04-09
Wow... I found it.

[http://ubuntuforums.org/showthread.php?t=2248940&page=4&p=13156204#post13156204](http://ubuntuforums.org/showthread.php?t=2248940&page=4&p=13156204#post13156204)

and here is the whole thread..

[http://ubuntuforums.org/showthread.php?t=2248940](http://ubuntuforums.org/showthread.php?t=2248940)

---

### Post by ventrical on 2015-04-09
I am absolutely stunned. It is working now better than ever. I am running ubuntu-unity on F7 and razorQT on F1 in parallel. I can run youtube in FF on razor and when I switch to unity session it is changed in a flash to that desktop. I will test to see if they are running concurrently.

Regards..

*yes*!!! They are running concurrently!!!  When I switch to ubuntu-unity and can work in that desktop while yotube is running video in FF on razorQT desktop. All it does is switch the audio over to unity-desktop and then , switches it back to razorQT when I switch back to tty1.

So .. in a sense .. who needs lxc? :)

  I am so glad I read this thread. It seems like a lot of bugs have been ironed out from original. So , basically, with the methods nad links I posted, one can have a virtual KVM on one machine!!

Regards..

---

### Post by ventrical on 2015-04-09
I am running only a dual core on a Motherboard that is i7 compatible but I have 16GB of ddr3 memory. It is using a lot of processor resource, about 80% on each core and the heat came up to about 40 degrees C but it is running really stable so I will second this process to my quad cores for better efficiency.

---

### Post by ventrical on 2015-04-09
I was able to load the Mate desktop alongside the unity desktop.

Just changed the code in .xinitrc file


```

exec mate-session

```

It seems much more stable than razorqt desktop.

---

### Post by grahammechanical on 2015-04-09
@ventrical

I am not sure we are discussing the same subject. The idea here was to use LXC as a lower resource alternative to a VM. To have each development flavour in it own container which we can switch into from a host OS of Ubuntu LTS.

Unity8 in LXC does this by having a login screen option and I was hoping to subvert some of the Unity8 in LXC scripts to do the same with the development versions of Ubuntu and the flavours. Uniy8 in LXC uses zsync to update the image. But I did not get very far. It overloads my brain.

I had already messed with LXC itself and although I could set up containers with Vivid in them I could not switch into the container and see a working desktop.

Something called LXC-Desktop was supposed to do all this. The instructions although simple did not work because there were dependencies not installed on my system. I worked all that out, wrote up notes on all of it to form the basis of a wiki page but I still had the same problem of switching to a tty and finding a running version of Ubuntu. 

The value of LXC is that the OS in the container will use libraries from the host OS. So, it will use all the kernel stuff and Xserver, etc, without needing all that installed or running in the OS in the container. This reduces the load in system resources. I guess that LXC is meant for server systems where applications can be  run on LInux without needing a GUI or desktop environment.

Regards.

---

### Post by grahammechanical on 2015-04-09
Did I say that I was giving up? Well, Ventrical's interest has caused me to try again. I am on 14.04.2 and using lxc-desktop. After pre-installing certain packages without which we get error  Issues I used the instructions here

[https://github.com/ustuehler/lxc-desktop](https://github.com/ustuehler/lxc-desktop)

This command will create a Linux Container called "container" which will hold the OS as the host OS. In this case it is trusty.

```
https://github.com/ustuehler/lxc-desktop
```

This command will start the container

```
sudo lxc-start -n container -d
```

And then switching to tty8 I get a login screen for trusty. This is the first ime I have had this happen. The user name is ubuntu and the password is ubuntu but this can be changed if we want. Ubuntu 14.04 in this container does not have any applications installed. The Launcher has File Manager, Ubuntu Software Centre and System Settings. So, it is indeed a minimal installation.

Now to make this really useful I need to be able do this with vivid and then all the flavours of ubuntu (both release and development versions), And that could be easy or it could be hard.

Anyway I can now switch between 14.04 on tty7 (the host) and 14.04 on tty8 (the container). It is a starting point. Instructions available. Just ask in this thread.

P.S. Although the default user is Administrator it does not have permission to install any software or even to set up a new user account. There are LXC commands that can be used in the host to do this. Just need to work out how.

Regards.

---

### Post by ventrical on 2015-04-09
I had installed the unity8 lxc on this very PC long ago and have updated dilligently but I keep getting an error when I try to log in .... can't log in to os .. or something. I am going to read up. Thanks for your info . I am going to check it out.

Regards..

---

### Post by ventrical on 2015-04-09
> **grahammechanical said:**
> Did I say that I was giving up? Well, Ventrical's interest has caused me to try again. I am on 14.04.2 and using lxc-desktop. After pre-installing certain packages without which we get error  Issues I used the instructions here

[https://github.com/ustuehler/lxc-desktop](https://github.com/ustuehler/lxc-desktop)

This command will create a Linux Container called "container" which will hold the OS as the host OS. In this case it is trusty.

```
https://github.com/ustuehler/lxc-desktop
```

This command will start the container

```
sudo lxc-start -n container -d
```

And then switching to tty8 I get a login screen for trusty. This is the first ime I have had this happen. The user name is ubuntu and the password is ubuntu but this can be changed if we want. Ubuntu 14.04 in this container does not have any applications installed. The Launcher has File Manager, Ubuntu Software Centre and System Settings. So, it is indeed a minimal installation.

Now to make this really useful I need to be able do this with vivid and then all the flavours of ubuntu (both release and development versions), And that could be easy or it could be hard.

Anyway I can now switch between 14.04 on tty7 (the host) and 14.04 on tty8 (the container). It is a starting point. Instructions available. Just ask in this thread.

P.S. Although the default user is Administrator it does not have permission to install any software or even to set up a new user account. There are LXC commands that can be used in the host to do this. Just need to work out how.

Regards.

 I followed the link you provided and got these errors:

```

ventrical@ventrical-MS-7798:~$ dpkg-buildpackage -uc -us
tail: cannot open ‘debian/changelog’ for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1
ventrical@ventrical-MS-7798:~$ sudo dpkg -i ../lxc-desktop_*_all.deb
dpkg: error processing archive ../lxc-desktop_*_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ../lxc-desktop_*_all.deb
ventrical@ventrical-MS-7798:~$ sudo -i
root@ventrical-MS-7798:~# sudo dpkg -i ../lxc-desktop_*_all.deb
dpkg: error processing archive ../lxc-desktop_*_all.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ../lxc-desktop_*_all.deb
root@ventrical-MS-7798:~# dpkg-buildpackage -uc -us
tail: cannot open ‘debian/changelog’ for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1
root@ventrical-MS-7798:~# sudo apt-get -f install


```

but I am using vivid 15.04.  That may explain that.

Regards..

---

### Post by grahammechanical on 2015-04-09
I had failures with vivid as the host. Much better result with 14.04.2. This is what we need pre-installed before installing lxc-desktop

```
sudo apt-get install git
sudo apt-get install dh-make
sudo apt-get install lxc
```

Then to install lxc-desktop

```
git clone https://github.com/ustuehler/lxc-desktop && cd lxc-desktop
```

We end up in the lxc-desktop directory 

```
sudo apt-get install ubuntu-dev-tools
sudo dpkg-buildpackage -uc -us
sudo dpkg -i ../lxc-desktop_*_all.deb
```

We are asked if we asked if we want to enable PulseAudio TCP protocol. Say no as that fails for some reason and mutes the Host OS. 

```
sudo apt-get -f install
```

This is optional to speed up the creation and updating of the host system and desktop containers using apt-cacher-ng(8), simply install the lxc-desktop-cache
package.

```
sudo dpkg -i ../lxc-desktop-cache_*_all.deb
```

That will produce this error

> dpkg: dependency problems prevent configuration of lxc-desktop-cache:  lxc-desktop-cache depends on apt-cacher-ng; however:  Package apt-cacher-ng is not installed.

dpkg: error processing package lxc-desktop-cache (--install):  dependency problems - leaving unconfigured Errors were encountered while processing:
 lxc-desktop-cache

But apt-cacher-ng will be installed by this command:

```
sudo apt-get -f install
```

Now we can create a container. This will create a container called "container" and it will have the same OS as the Host. 

```
sudo lxc-create -n container -t ubuntu-desktop
```

-n = container name.  -t = template. It calls the lxc-ubuntu-desktop template in /usr/share/lxc/templates/

To start a container

```
sudo lxc-start -n container -d
```

the -d tag is important as it loads a lxc-desktop daemon that does all the work. Without it the terminal in the Host will not get back to prompt.

The desktop should immedialy switch to tty8 with a login screen User name is ubuntu. password is ubuntu.

To stop the container

```
sudo lxc-stop -n container
```

To destroy the container

```
sudo lxc-destroy -n container.

This should create a container with Vivid inside it called uvivid

[code]sudo lxc-create -n uvivid -t ubuntu-desktop -- --d ubuntu -r vivid -a amd64
```

--d = distribution  -r = release  -a = architecture

this will start such a container

```
sudo lxc-start -n uvivid
```

Tomorrow I will see if I can do all this with Debian Jessie.

Regards.

---

### Post by ventrical on 2015-04-10
Ok.. thanks Graham. I'll try and get to all that a little later :)

Regards..

---

### Post by grahammechanical on 2015-04-10
I am about to test installing vivid in a container and then Debian Jessie. If I work out the correct commands. I will post them here.

Update:

I can use lxc-desktop to install the same OS as on the host. In my case trusty and a large number of trusty packages are installed. But I cannot get lxc-desktop to install vivid or another distribution.

I can use plain lxc to install Vivid and Debian Jessie but it seems as if I have empty containers. I do not see a large number of packages being downloaded and installed.

I tried a little bit of hacking on a couple of the templates but it gave errors and did not produce the desired result. 

Regards.

---

### Post by ventrical on 2015-04-10
> **grahammechanical said:**
> I had failures with vivid as the host. Much better result with 14.04.2. This is what we need pre-installed before installing lxc-desktop

```
sudo apt-get install git
sudo apt-get install dh-make
sudo apt-get install lxc
```

Then to install lxc-desktop

```
git clone https://github.com/ustuehler/lxc-desktop && cd lxc-desktop
```

We end up in the lxc-desktop directory 

```
sudo apt-get install ubuntu-dev-tools
sudo dpkg-buildpackage -uc -us
sudo dpkg -i ../lxc-desktop_*_all.deb
```

We are asked if we asked if we want to enable PulseAudio TCP protocol. Say no as that fails for some reason and mutes the Host OS. 

```
sudo apt-get -f install
```

This is optional to speed up the creation and updating of the host system and desktop containers using apt-cacher-ng(8), simply install the lxc-desktop-cache
package.

```
sudo dpkg -i ../lxc-desktop-cache_*_all.deb
```

That will produce this error



But apt-cacher-ng will be installed by this command:

```
sudo apt-get -f install
```

Now we can create a container. This will create a container called "container" and it will have the same OS as the Host. 

```
sudo lxc-create -n container -t ubuntu-desktop
```

-n = container name.  -t = template. It calls the lxc-ubuntu-desktop template in /usr/share/lxc/templates/

To start a container

```
sudo lxc-start -n container -d
```

the -d tag is important as it loads a lxc-desktop daemon that does all the work. Without it the terminal in the Host will not get back to prompt.

The desktop should immedialy switch to tty8 with a login screen User name is ubuntu. password is ubuntu.

To stop the container

```
sudo lxc-stop -n container
```

To destroy the container

```
sudo lxc-destroy -n container.

This should create a container with Vivid inside it called uvivid

[code]sudo lxc-create -n uvivid -t ubuntu-desktop -- --d ubuntu -r vivid -a amd64
```

--d = distribution  -r = release  -a = architecture

this will start such a container

```
sudo lxc-start -n uvivid
```

Tomorrow I will see if I can do all this with Debian Jessie.

Regards.

@grahammechanical

Thanks for no bifurcation :) It worked very well here. I am impressed that it worked and is running concurrently with F7 ubuntu-desktop. A few strange anomolies.

1.I got llvmpipe on the 'container'.

2. It is bare bones but I found that you can use terminal and download programs like firefox and gnome-screenshot. Unity Dash does not seem to have anything in it but I am able to lock programs to launcher once I run them from terminal. I am going to try and switch that hdd to a faster system with 16GBddr3 ram and see what happens :)

Regards..

---

### Post by ventrical on 2015-04-10
I switched that drive into another tower and it will not jockey over to the Sandy Bridge graphics. Most likely I would have to destroy the container and make a new one.

Regards..

---

### Post by grahammechanical on 2015-04-10
Ah! It has Xterm? I know it does not have Gnome terminal and when I tried to install it through the software centre I got the not sufficient authorisation error. Although the default user is set up as Administrator. which is weird. I guess that the pkexec file does not allow software centre to access the internet. Or something like that.

I got myself in a mess trying to add a new user from the host OS. The new user was added but not the home folder for the user. So, no login for that user.

Regards.

---

### Post by ventrical on 2015-04-11
Now it will not let me login. I just get the unity login screen but no mouse. I guess it was a one time deal. I'll have to look at it more.


Regards..

---

### Post by ventrical on 2015-04-11
> **grahammechanical said:**
> Ah! It has Xterm? 

Ok..back on line here.
Yes. Ctrl+Alt + T ... then you can ..

```

sudo -i
sudo apt-get install gnome-terminal

```

after which when you press Ctrl +Alt +T you will get gnome terminal and not xterm and you can lock it to launcher.

---

### Post by grahammechanical on 2015-04-11
I am about to try another experiment. I am going to edit a couple of templates to see if I can use lxc-desktop to install vivid and one of the flavours. Based upon my previous record it will surely fail.

Update: Failure!. It installed trusty again. The method defaults to installing the same OS as on the host or the latest LTS. I also tried commenting out the lines in the template that I thought set the default to LTS. But then the script would not run.

I have one more idea for today.

Update 2: It almost worked. But editing /etc/lsb-release and changing the references from trusty to vivid and the the references to 14.04.2 to 15.04 I hoped to fool the installer into think that the host was vivid. The process had hits with the vivid repositories instead of the trusty repositories but then the template failed with 

> lxc_container: lxccontainer.c: create_run_template: 1125 container creation template for uvivid1 failed
lxc_container: lxc_create.c: main: 271 Error creating container uvivid1


I think that I am on the right track. Later to day I may try reinstalling 14.04.2 and starting with a fresh OS to make sure that my editing of the templates is not causing confusion.

Update 3: This is becoming discouraging. Editing /etc/lsb-release is key and so is deleting the automatically made backup that nautilus does. And the process also seems to create the container with vivid in it. The vivid repositories are accessed. Lots of packages are downloaded and unpacked and configured but near the end is this error

[QUOTE]Package lxcguest is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'lxcguest' has no installation candidate
lxc_container: lxccontainer.c: create_run_template: 1125 container creation template for uv1 failed
lxc_container: lxc_create.c: main: 271 Error creating container uv1



Who cares if it does not have a guess account? I am fast running out of inspiration.

---

### Post by grahammechanical on 2015-04-13
_End of term report_

1) Using plain lxc and its lxc-download template will allow the selection of distribution (Ubuntu), release (vivid) and architecture (amd64) but it installs Ubuntu minimal without a desktop environment. It is possible to access the container and install ubuntu-desktop (and other desktops, presumably) but after starting the container and switching to tty8 (the next available console) there is no working desktop.

2a) The utility lxc-desktop will create a container with Ubuntu and a DE and a UI (unity) and when the container is started it will present a working desktop on tty8. But it uses the lxc-ubuntu template and that defaults to installing the same OS as the host OS or the latest LTS release. This is no good if we want to test the development release.

2b) I have had no success in editing a couple of relevant templates and lsb-release to force lxc-desktop to either install Ununtu vivid or a flavour of Ubuntu. Which would be useful for testing the development release.

_Further experimentation next term_

3a) Using lxc-ubuntu as a pattern create templates for the flavours, e.g., lxc-xubuntu; lxc-lubuntu, etc. But change the defaults to the development release.

3b) Using lxc-ubuntu-desktop as a pattern create templates that have other desktops as default and not ubuntu-desktop.

End of report

---

### Post by SurfaceUnits on 2015-04-14
How is this different from tty sessions?

[https://mostlylinux.wordpress.com/troubleshooting/ttysessions/](https://mostlylinux.wordpress.com/troubleshooting/ttysessions/)

---

### Post by grahammechanical on 2015-04-14
> 
[LIST=1]
[*]Start the GUI by typing this command:startx -- :#Replace **#** with a number from **1** through **6**, using **1** for the first TTY GUI session you create, **2** for the second TTY GUI session you create, and so on.
*Note that in Ubuntu and its derivatives, **startx &#8212; :0** is reserved for use by the system for the default GUI session.*
[/LIST]


Think about it for a moment. You may get a desktop with a user interface but it will be the same release as you already have on tty7. And what is more you may be running a UI as root and can damage the OS.

The idea behind this thread was to get different versions and releases of Ubuntu running in Linux containers so that if the OS was Ubuntu+Unity we could switch between Xubuntu and Lubuntu and the others just by starting a container and switching to tty8.

Imagine running an LTS release of Ubuntu but being able to run also development versions of Ubuntu and all the flavours without dual booting. And doing this just by switching to tty8 or tty9 or tty10 and back to tty7 to get back to the host OS.

Keep also in mind that the OS in the container is using libraries from the host but the container OS has very limited ability to alter things on the host OS. There is at least one developer that does not like the idea of proprietary software like Google Chrome running on his OS. So, he runs it in a container. There is better security that way.

[https://www.stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/](https://www.stgraber.org/2014/02/09/lxc-1-0-gui-in-containers/)

This link has a video

[http://www.flockport.com/run-gui-apps-in-lxc-containers/](http://www.flockport.com/run-gui-apps-in-lxc-containers/)

See Linux Containers (LXC) as a possible way of installing another Linux distribution without installing it to another partition and dual booting. The problem as far as I can see is that Linux containers have been developed for use on server systems and the developers have not given much thought to running desktops in LXC. And even less thought to running anything but the Ubuntu derivative of Ubuntu and not the other derivatives.

Regards.

---

### Post by ventrical on 2015-04-16
> **grahammechanical said:**
> I am about to try another experiment. I am going to edit a couple of templates to see if I can use lxc-desktop to install vivid and one of the flavours. Based upon my previous record it will surely fail.



Who cares if it does not have a guess account? I am fast running out of inspiration.

Ditto.

Bravo for your efforts  to work on this one. What discourages me is the bandwidth it uses to set up(each) the container  and when it rolls over to llvmpipe on perfectly good working graphics adapter then I have second thoughts at testing.

 I agree with some of your findings , ie; startx vs lxc container but the startx option is a lot faster but then it is only running DEs concurrently and not a whole distribution.  it's like chopping wood but no chips are flying :)

Regards..

---

### Post by grahammechanical on 2015-04-18
I have had a measure of success with lxc-desktop. I can now switch between Ubuntu desktop on tty7, Xubuntu desktop on tty8 and Lubuntu desktop on tty9. There is a limited set of applications but it should be possible to open a terminal to install stuff.

I have not tested using utopic as the host but vivid my attempts with vivid as the host failed. So, I am back on trusty 14.04.2 as the host. We take advantage of default working of lxc-create to install in the container the same OS as the host.

We edit the template at /usr/share/lxc/templates/lxc-ubuntu-desltop and change this

packages="ubuntu-desktop $packages" 

to 

packages="xubuntu-desktop $packages"

we save the file as lxc-xubuntu-desktop and set the properties to enable execute as a program. Then this command we create a container called xu1 with trusty xubuntu desktop it.

```
sudo lxc-create -n xu1 -t xubuntu-desktop
```

Follow the same method to create a lxc-lubuntu-desktop and this command will create a container called lu1 with trusty lubuntu desktop.

```
sudo lxc-create -n lu1 -t lubuntu-desktop
```

These commands will start the containers

```
sudo lxc-start -n xu1 -d
```

```
sudo lxc-start -n lu1 -d
```

The -d switch is important as the container does not detach from the terminal and it gets messy trying to stop the container. It should be possible to do the same with the other flavours as well. And even modify the template to install more packages than just the desktop package.

The original vision was to run the development releases of Ubuntu and its flavours in Linux containers. This is a start. Who knows what will happen if I upgrade the OS in the  containers to utopic and then to vivid and on to wcodename. That I will have to try. I cannot see any other way of doing it. 

I am not being prejudiced but Debian has recorded systemd as being incompatible with lxc. Not sure if this is fixed or we need to wait until the next ubuntu development cycle but it may be the reason why this experiments fail with vivid as the host OS.

[http://sudo lxc-start -n lu1 -d](http://sudo lxc-start -n lu1 -d)

Regards.

---

### Post by bmullan2 on 2015-05-05
The way I do this with LXC is by using x2go (x2go.org) or guacamole (guac-dev.org).
x2go is the easiest to setup & use. 
Create your container using lxc-create, start it detached (lxc-start -n my-container -d) 
Attach to the container so you can install a desktop & x2go 'server-side' using lxc-attach -n my-container
sudo apt-get update && sudo apt-get upgrade -y
sudo apt-get install (pick a desktop - xfce & mate both work very well)
install the x2go ppa:   sudo add-apt-repository ppa:2go/stable
answer yes
then follow the x2go.org web page instructions to install the x2goserver:   [http://wiki.x2go.org/doku.php/doc:installation/x2goserver]("http://wiki.x2go.org/doku.php/doc:installation:x2goserver")

when you are done in the container you might want to reboot the container (sudo shutdown -r now)

Lastly, install the x2go client in your Ubuntu "host".

sudo add-apt-repository ppa:2go/stable
answer yes
sudo apt-get update
sudo apt-get install x2goclient

that's it

if your LXC container is running you just need its IP address (sudo lxc-ls -f  will tell you)

run x2goclient

the gui client is easy to use once you have set up a profile 1 time... its very simple

Here is a very recent article which had screen shots etc.

[http://www.unixmen.com/x2go-an-open-source-remote-desktop-solution-for-linux/](http://www.unixmen.com/x2go-an-open-source-remote-desktop-solution-for-linux/)

NOTE:   when accessing lxc containers OR other servers on the same LAN ... in the x2go client "connection" tab slide the slider ALL the way to the right.
            that slider tells x2goserver how much compression to use in sending the client the desktop image.   On the same LAN or connecting to a container there is NO need for any compression.

brian

---

### Post by bmullan2 on 2015-05-05
I'd also mentioned guacamole.   guacamole is an HTML5 remote desktop so the only client you need is an HTML5 compatible browser.
On the server there is a little more setup required because there is a web-server component that needs to be configure.   Its not too 
difficult though.    

Guacamole ([www.guac-dev.org](www.guac-dev.org)) like x2go will need a desktop other than gnome3 or unity so again in the container you will need to install something like xfce or mate

Assuming you get the container configured correctly for guacamole then you just point your browser to the IP of the container plus the guacamole Port number
and you will be able to log into the container based desktop.

---

### Post by SurfaceUnits on 2015-05-11
[h=1]A thorough introduction guide to Docker containers[/h]
[http://www.linuxcompatible.org/news/story/a_thorough_introduction_guide_to_docker_containers.html](http://www.linuxcompatible.org/news/story/a_thorough_introduction_guide_to_docker_containers.html)

---

### Post by ventrical on 2015-10-15
Just reading through these old forums notes - gemstones in the rough. I have put this in the library at the U+1 wiki because it will come in handy as we are now using LXD in snappy-ubuntu-core (and also on snappy-personal) It dos not work on snappy-personal as of yet but I have had some initial success with snappy-core in that I can get graphical htop and midnight commander working in a container. LXD is built upon LXC structure and uses lxc commands and so during the next development cycle of XX  with convergence then all of this research may come in handy to run containers 'n desktops in snappy-core.

Regards..

---

### Post by DuckHook on 2016-02-24
I just happened upon this old thread by chance and was blown away by the progress that grahammechanical and ventrical have made. I had no idea that they went so far as to actually succeed in implementing what I had, frankly, given up on.

I hope the mods don't treat this as a necro-post, because I don't think it is. Though the thread has been hibernating for a few months, its subject matter is still topical and very useful to many users who have certain needs.

I will be trying to implement grahammechanical's procedures in the next couple of weeks and will report back on progress, but in the meantime, this is my contribution by way of a use-case synopsis.

Unlike grahammechanical, my motivation wasn't to try out new versions. In that sense, my needs are simpler and I don't have to try fitting in newer kernels/libraries/infrastructure into LXC. I was primarily motivated by three needs:

1. I sometimes have to run an old version of gnuCash alongside the latest version due to a database incompatibility that the app developers have never resolved. Since gnuCash is a mission-critical app for me, it is essential that I have concurrent access to both versions. My workaround prior to LXC was to run the old pinned version of gnuCash on Ubuntu 12.04 within a VM, while running an up-to-date gnuCash on the host OS in the normal manner. While this works well on my main box, it really bogs down on anything older than modern powerful HW.

2. In order to effectively contribute to this forum, it is useful to have different 'buntu flavours running in tandem. Again, while this is possible with VMs, it incurs the same resource hit as #1 above.

3. I have never liked the idea of running browsers on my main OS. The browser is the single biggest security hole in all systems and even with an apparmor profile installed, it doesn't feel like sufficient security in depth. Yet again, the VM solution is too resource-intensive for some machines.

Not least, I am an inveterate tinkerer and just incurably curious about LXC. If it's capable of delivering on all of the items it promises, then it will replace my VMs for most use-cases.

One forum member asked what's the difference between a container and a TTY Session: the TTY session cannot solve any of the above issues because it is incapable of either multi-version app support, instantiating different flavours of desktops, or sandboxing. A VM solves all of these requirements but is so resource-intensive that I can't run more than one VM in most of my old boxes without overtaxing the CPU and panicking the kernel, with attendant risk of data corruption. On some really old boxes, it is a bad idea to run any VM at all. Besides, I've always had trouble invoking TTY GUI sessions. They either refuse to launch, crash or yield buggy performance due to conflicting environment variables and who knows what else.

Other forum members suggest tapping into containers through various forms of Remote Desktop server-client setups. This is a proven way to access containers, but manipulating a desktop through a window or a browser feels claustrophobic. Especially so on a laptop in which the native resolution is already just 1200 x 800. We want to be able to <CTRL>+<ALT>+<F8> into a magnificent full screen desktop and then simply <CTRL>+<ALT>+<F7> to switch back. And all of those extra TTYs sitting around going to waste: it seems a shame leaving them idle.

Anyway, starting to ramble, but those are my use-cases for trying to implement full desktop GUIs on unused TTYs.

---

### Post by naisanza on 2016-04-29
You'll still want LXC, because LXC isolates changes to your host system within the container. Running a separate X Session does not. At least that's to my knowledge of LXC

---

### Post by naisanza on 2016-04-29
> **SurfaceUnits said:**
> How is this different from tty sessions?

[https://mostlylinux.wordpress.com/troubleshooting/ttysessions/](https://mostlylinux.wordpress.com/troubleshooting/ttysessions/)

File modifications are to the host system and not isolated or containerized

---

### Post by ventrical on 2016-08-01
> **grahammechanical said:**
> I have had a measure of success with lxc-desktop. I can now switch between Ubuntu desktop on tty7, Xubuntu desktop on tty8 and Lubuntu desktop on tty9. There is a limited set of applications but it should be possible to open a terminal to install stuff.

I have not tested using utopic as the host but vivid my attempts with vivid as the host failed. So, I am back on trusty 14.04.2 as the host. We take advantage of default working of lxc-create to install in the container the same OS as the host.

We edit the template at /usr/share/lxc/templates/lxc-ubuntu-desltop and change this

packages="ubuntu-desktop $packages" 

to 

packages="xubuntu-desktop $packages"

we save the file as lxc-xubuntu-desktop and set the properties to enable execute as a program. Then this command we create a container called xu1 with trusty xubuntu desktop it.

```
sudo lxc-create -n xu1 -t xubuntu-desktop
```

Follow the same method to create a lxc-lubuntu-desktop and this command will create a container called lu1 with trusty lubuntu desktop.

```
sudo lxc-create -n lu1 -t lubuntu-desktop
```

These commands will start the containers

```
sudo lxc-start -n xu1 -d
```

```
sudo lxc-start -n lu1 -d
```

The -d switch is important as the container does not detach from the terminal and it gets messy trying to stop the container. It should be possible to do the same with the other flavours as well. And even modify the template to install more packages than just the desktop package.

The original vision was to run the development releases of Ubuntu and its flavours in Linux containers. This is a start. Who knows what will happen if I upgrade the OS in the  containers to utopic and then to vivid and on to wcodename. That I will have to try. I cannot see any other way of doing it. 

I am not being prejudiced but Debian has recorded systemd as being incompatible with lxc. Not sure if this is fixed or we need to wait until the next ubuntu development cycle but it may be the reason why this experiments fail with vivid as the host OS.

[http://sudo lxc-start -n lu1 -d](http://sudo lxc-start -n lu1 -d)

Regards.

I am just bumping this as it may be helpful to get working alternate desktop in container.

[https://ubuntuforums.org/showthread.php?t=2271655&page=4&p=13267669#post13267669](https://ubuntuforums.org/showthread.php?t=2271655&page=4&p=13267669#post13267669)

---

### Post by ventrical on 2016-08-23
I was working on a problem in General help and I tired an experiment with .xinitrc. I was able to run firefox and one of the arcade games in a standalone terminal (probably lots more stuff too).  So now that this is working with Xorg I am wondering why we need containers?

[https://ubuntuforums.org/showthread.php?t=2334790&p=13535124#post13535124](https://ubuntuforums.org/showthread.php?t=2334790&p=13535124#post13535124)

Regards..

---

### Post by ventrical on 2017-04-07
> **DuckHook said:**
> I just happened upon this old thread by chance and was blown away by the progress that grahammechanical and ventrical have made. I had no idea that they went so far as to actually succeed in implementing what I had, frankly, given up on.

I hope the mods don't treat this as a necro-post, because I don't think it is. Though the thread has been hibernating for a few months, its subject matter is still topical and very useful to many users who have certain needs.

I will be trying to implement grahammechanical's procedures in the next couple of weeks and will report back on progress, but in the meantime, this is my contribution by way of a use-case synopsis.

Unlike grahammechanical, my motivation wasn't to try out new versions. In that sense, my needs are simpler and I don't have to try fitting in newer kernels/libraries/infrastructure into LXC. I was primarily motivated by three needs:

1. I sometimes have to run an old version of gnuCash alongside the latest version due to a database incompatibility that the app developers have never resolved. Since gnuCash is a mission-critical app for me, it is essential that I have concurrent access to both versions. My workaround prior to LXC was to run the old pinned version of gnuCash on Ubuntu 12.04 within a VM, while running an up-to-date gnuCash on the host OS in the normal manner. While this works well on my main box, it really bogs down on anything older than modern powerful HW.

2. In order to effectively contribute to this forum, it is useful to have different 'buntu flavours running in tandem. Again, while this is possible with VMs, it incurs the same resource hit as #1 above.

3. I have never liked the idea of running browsers on my main OS. The browser is the single biggest security hole in all systems and even with an apparmor profile installed, it doesn't feel like sufficient security in depth. Yet again, the VM solution is too resource-intensive for some machines.

Not least, I am an inveterate tinkerer and just incurably curious about LXC. If it's capable of delivering on all of the items it promises, then it will replace my VMs for most use-cases.

One forum member asked what's the difference between a container and a TTY Session: the TTY session cannot solve any of the above issues because it is incapable of either multi-version app support, instantiating different flavours of desktops, or sandboxing. A VM solves all of these requirements but is so resource-intensive that I can't run more than one VM in most of my old boxes without overtaxing the CPU and panicking the kernel, with attendant risk of data corruption. On some really old boxes, it is a bad idea to run any VM at all. Besides, I've always had trouble invoking TTY GUI sessions. They either refuse to launch, crash or yield buggy performance due to conflicting environment variables and who knows what else.

Other forum members suggest tapping into containers through various forms of Remote Desktop server-client setups. This is a proven way to access containers, but manipulating a desktop through a window or a browser feels claustrophobic. Especially so on a laptop in which the native resolution is already just 1200 x 800. We want to be able to <CTRL>+<ALT>+<F8> into a magnificent full screen desktop and then simply <CTRL>+<ALT>+<F7> to switch back. And all of those extra TTYs sitting around going to waste: it seems a shame leaving them idle.

Anyway, starting to ramble, but those are my use-cases for trying to implement full desktop GUIs on unused TTYs.

I just wanted to bump up this post as per recent developments about how lxc containers will also be tested with snappy as it may come in as a handy thumbnail for those who want to keep testing it.

Regards..

---

### Post by DuckHook on 2018-01-14
Bumping to keep this thread relevant, although it may be superseded by: [https://ubuntuforums.org/showthread.php?t=2331353](https://ubuntuforums.org/showthread.php?t=2331353)

---

