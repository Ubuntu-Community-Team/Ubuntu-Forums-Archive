---
title: "Kubuntu Studio?"
date: 2016-08-11
forum: Ubuntu Studio
---

### Post by estelledarwin on 2016-08-11
Hello
is it possible to have Ubuntu Studio with KDE?

---

### Post by mook765 on 2016-08-11
You may add the studio components to kubuntu.
Use these commands
```
sudo apt-get install linux-lowlatency
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins
sudo apt-get install ubuntustudio-video
sudo apt-get install ubuntustudio-graphics
sudo apt-get install ubuntustudio-photography
sudo apt-get install ubuntustudio-publishing
sudo apt-get install ubuntustudio-look
```
to add the desired components

---

### Post by estelledarwin on 2016-08-12
thank you, I already done that ;-)
I like US and not XFCE. I've tried to install KDE on US but it doesn't work, so I've got the idea to install Kubuntu and after all the components of US and  it works
but now the V16.04.1 is here and I wonder how can I do to install it ?
And to install all the future versions?
If Kubuntu Studio exist, it would be so much easier ;-)

---

### Post by Bucky Ball on 2016-08-12
It does exist if you make it so. Install Kubuntu and then ubuntustudio-desktop. :)

Whatever you have installed at upgrade, doesn't matter. It's all going to get upgraded. The main points before upgrading to 16.04 are to fully update/upgrade the current release and install first, disable any PPAs you have installed manually and, if you can, disable or remove any third-party drivers you have installed for video (and other hardware where applicable). 

In your current situation, installing all of this individually:

```
sudo apt-get install linux-lowlatency
sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins
sudo apt-get install ubuntustudio-video
sudo apt-get install ubuntustudio-graphics
sudo apt-get install ubuntustudio-photography
sudo apt-get install ubuntustudio-publishing
sudo apt-get install ubuntustudio-look
```

... is not necessary and bit of a waste of time as it would all be dragged in if you install ubuntustudio-desktop only. Doing so is pretty much the equivalent of installing Ubuntu Studio. What you end up with by doing it this way, though, is a very bloated system with all of the default apps of whatever the original flavour was plus all the default apps that come with Ubuntu Studio, many of which you will probably never want or use.

If you are into audio, install ubuntustudio-audio. There are UStudio 'bundles', as you know, for other media areas. Might be a better way to go. Good luck however you do it. :)

---

### Post by estelledarwin on 2016-08-12
thank you but like I said : I have already installed Kubuntu 16.04 and after all the parts of US :-)
My question is : how can I do to get to K16.04 to K16.04.1 ?
And how can I upgrade the future version ? K 16.10, etc ?
I'm afraid to lost all my softs and parameters if I install K16.04.1 upon K160.4 :-/
That's why I asked if is would be possible tu have directly a KubuntuStudio ;-)

---

### Post by CrocoDuck on 2016-08-12
> **Bucky Ball said:**
> 
Whatever you have installed at upgrade, doesn't matter. It's all going to get upgraded. The main points before upgrading to 16.04 are to fully update/upgrade the current release and install first, disable any PPAs you have installed manually and, if you can, disable or remove any third-party drivers you have installed for video (and other hardware where applicable). 


I think this answers your question. As you have installed packages from the Ubuntu repos, upgrade is gonna upgrade them all. I have stopped using Ubuntu 4 years ago (I am on Arch now), so maybe wait for someone else to confirm. Anyway, I have been using Ubuntu for many years before and I would not advise to make a version advancement upgrade. The fact is that they always broke my system, even if vanilla Ubuntu. Maybe things changed now but I don't know. As you are on a LTS release I would just keep on doing regular package updates. This will keep your system updated without troubles.

If you like KDE and audio software you might be interested in the [KXStudio project]("http://kxstudio.linuxaudio.org/index.php").

---

### Post by mook765 on 2016-08-12
@BuckyBall
Sorry,I think that your suggested method is going to bloat the system more.
Installing ubuntustudio-desktop will install just more, for example it will install the ubuntustudio-desktopenvironment.That is something you don't really need, when you want to run in kde.

@estelledarwin
To install kde on ubuntustudio is also possible. after installing  kde (plasma-desktop) you would have to go to Setting > Session and Startup and tick the checkbox for plasma-desktop. after your next login you would be asked which desktop-environment you want to use in the session. I tried that too, and it took some time to find out why nothing happened after installation off plasma-desktop.

If you find your system bloated, it is always possible to remove unused components (packages).


[**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=2040149")

---

### Post by estelledarwin on 2016-08-12
@Mook765
that's what I've done and everything works perfetcly ;-)
Just a thing : I come from a "Window world". W10 push me to quit Microsoft and go to GNU/Linux. I've installed a lot of distros (Ubuntu, Kaos, Mageia, Manjaro, etc) but I fell in love with US 16.04 so I'm a beginner in the "Linux world" 
my problem is not to install US (it's ok), my problem is a question : how can I make to upgrade my system ?

EDIT : sorry, I'm french and sometimes I don't understand every sentences...

---

### Post by Bucky Ball on 2016-08-12
> **estelledarwin said:**
> 
My question is : how can I do to get to K16.04 to K16.04.1 ?
And how can I upgrade the future version ? K 16.10, etc ?

> **Bucky Ball said:**
> Whatever you have installed at upgrade, doesn't matter. It's all going to get upgraded. The main points before upgrading to 16.04 are to fully update/upgrade the current release and install first, disable any PPAs you have installed manually and, if you can, disable or remove any third-party drivers you have installed for video (and other hardware where applicable).

... as Crocoduck quoted. Just upgrade to 16.04 as you normally would. You're not going to lose anything. ALWAYS backup personal data and anything else valuable before proceeding with a release upgrade.

---

### Post by mook765 on 2016-08-12
To upgrade from 16.04 to 16.04.1 just open the terminal.
Then you enter the command```
sudo apt update
```This command will check for available updates.
With the command```
apt list --upgradable
```you can see what is going to be updated, this command is optional.
At least you enter the command```
sudo apt upgrade
```This command will install the available updates to the system.
You are done...:)
You may check your version with the command```
lsb_release -a
```
You should not do a release-upgrade to 16.10.
16.04 is a LTS-release with 5 years support. 16.10 will have much shorter support-time ( I think it's 9 month )
The next LTS-release will be 18.04.See this links:
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

P.S. My French is bad, but your English is quiet good. Let Google translate for you...

---

### Post by estelledarwin on 2016-08-12
> **mook765 said:**
> 
With the command```
apt list --upgradable
```

I didn't know this command !!!!
I've written it and Konsole says : 
```
[FONT=monospace][COLOR=#18B218]python3-distupgrade[/COLOR][COLOR=#000000]/xenial-updates,xenial-updates 1:16.04.15 all [upgradable from: 1:16.[/COLOR]
04.14]
[COLOR=#18B218]ubuntu-release-upgrader-core[/COLOR][COLOR=#000000]/xenial-updates,xenial-updates 1:16.04.15 all [upgradable fr[/COLOR]
om: 1:16.04.14]
[COLOR=#18B218]ubuntu-release-upgrader-gtk[/COLOR][COLOR=#000000]/xenial-updates,xenial-updates 1:16.04.15 all [upgradable fro[/COLOR]
m: 1:16.04.14][/FONT]
```
[FONT=monospace]woaw !
the daily update doesn't ask me to upgrade
I got a "test partition" and I will test this
thank you my lord ;-)

[/FONT]

---

### Post by Bucky Ball on 2016-08-12
Preferable is:

```
sudo apt update
sudo apt full-upgrade
```

... as

> full-upgrade performs the function of upgrade but will remove
           currently installed packages if this is needed to upgrade the
           system as a whole.

See 'man apt' in a terminal for more info on the apt commands and what they do. ;)

---

### Post by estelledarwin on 2016-08-12
ok
thanks guys :popcorn:

---

