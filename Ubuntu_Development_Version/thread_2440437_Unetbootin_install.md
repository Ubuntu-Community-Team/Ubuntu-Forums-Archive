---
title: "Unetbootin install"
date: 2020-04-10
forum: Ubuntu Development Version
---

### Post by cookiecruncher on 2020-04-10
Hi. I am attempting to install Unetbootin (under Ubuntu 20.04 beta) but it fails. See below. I have installed the ppa, etc.

```

# apt install unetbootin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unetbootin : Depends: libqt4-network (>= 4:4.5.3) but it is not installable
              Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installable
              Depends: libqtgui4 (>= 4:4.5.3) but it is not installable
              Recommends: extlinux but it is not going to be installed
              Recommends: gksu but it is not installable or
                          kdesudo but it is not installable
E: Unable to correct problems, you have held broken packages.



```

---

### Post by slickymaster on 2020-04-10
Install it from the [Ubuntu PPA]("https://launchpad.net/~gezakovacs/+archive/ubuntu/ppa"):
```
sudo add-apt-repository ppa:gezakovacs/ppa
sudo apt-get update
sudo apt-get install unetbootin
```

---

### Post by Redalien0304 on 2020-04-10
Tried PPA on Ubuntu 20.04 got 
```
craig@craig-latitude-E6500:~$ sudo apt-get install unetbootinReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 unetbootin : Depends: libqt4-network (>= 4:4.5.3) but it is not installable
              Depends: libqtcore4 (>= 4:4.7.0~beta1) but it is not installable
              Depends: libqtgui4 (>= 4:4.5.3) but it is not installable
              Recommends: extlinux but it is not going to be installed
              Recommends: unetbootin-translations but it is not going to be installed
              Recommends: gksu but it is not installable or
                          kdesudo but it is not installable
E: Unable to correct problems, you have held broken packages. 
```

---

### Post by slickymaster on 2020-04-10
The package for 20.04. has already been published and built without issues

[ATTACH=CONFIG]285485[/ATTACH]

[ATTACH=CONFIG]285486[/ATTACH]

---

### Post by dargaud2 on 2020-05-12
Same problem here with 20.04. Can't install unetbootin

---

### Post by sudodus on 2020-05-12
I just tested in a fresh Xubuntu 20.04 LTS persistent live drive (fully up to date). And it does not work to install Unetbootin. So I can only suggest that you try another tool for the same purpose. The following tools work for me

- In Ubuntu: [mkusb](https://help.ubuntu.com/community/mkusb) (It works in all flavours of Ubuntu)
- In Windows: [Rufus](https://rufus.ie)

Edit: mkusb works in Groovy too.

---

### Post by chilewskirbuu on 2020-09-03
@ sudodus @ COOKIECRUNCHER, I was having similar errors except mkusb, unetbootin, startup disk creator did not work for me either the only thing that did was Rufus with Xubuntu 16 LTS for UEFI installs. (unetbootin worked but couldnt find initrd and vmlinuz didnt want to dig into that atm)
 I found Threads being there is some Write boot error with older ubuntu Version for UEFI along my travels Seems to be the cause of the issue Yet i still have this error with all UEFI install up to Ubuntu 20 again rufus is only that i can get to work.

---

### Post by sudodus on 2020-09-03
> **chilewskirbuu said:**
> @ sudodus @ COOKIECRUNCHER, I was having similar errors except mkusb, unetbootin, startup disk creator did not work for me either the only thing that did was Rufus with Xubuntu 16 LTS for UEFI installs. (unetbootin worked but couldnt find initrd and vmlinuz didnt want to dig into that atm)
 I found Threads being there is some Write boot error with older ubuntu Version for UEFI along my travels Seems to be the cause of the issue Yet i still have this error with all UEFI install up to Ubuntu 20 again rufus is only that i can get to work.

If you are willing to help me with testing, we can debug the problem with mkusb. In that case I will start by asking you about details in your particular case. Just let me know,

- yes (I want to debug the problem with mkusb) or
- no (I am happy with the solution using Windows and Rufus).

---

### Post by chilewskirbuu on 2020-09-03
@ sudodus, The boot device installs by default to EXT4(thru Startup Disk creator by default i tried to Format usb stick to FAT32 then install Via Startup disk Creator defaulted back to EXT4, Rufus allow the Option to Change Format Type Fat32, EXT4 etc.) I didnt spend much time with mkusb as i am lazy and i want auto install with easy click option lol...,if mkusb has this option since you and others seem to be able to install i have seen maybe i missed option to change boot format mode, surprisingly Unetbootin went to fat32 but was missing things as posted. Maybe this option change can help set user @COOKIECRUNCHER with mkusb i drno :) Funny thing is i ran into this exact same error with unetbootin when trying to install but forget how i worked around it to install to the usb boot stick if i remeber will post :) but unetbootin is just too much trouble my utter computer laziness so i cheated and used rufus :)
Umm maybe it was sudo apt-get -f install if your missing dependencies

---

### Post by sudodus on 2020-09-03
@chilewskirbuu,

I read this as "no (I am happy with the solution using Windows and Rufus)."

---

