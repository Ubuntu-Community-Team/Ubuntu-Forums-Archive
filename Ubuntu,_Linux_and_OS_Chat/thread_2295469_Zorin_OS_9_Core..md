---
title: "Zorin OS 9 Core."
date: 2015-09-18
forum: Ubuntu, Linux and OS Chat
---

### Post by poorguy on 2015-09-18
hey all,

since zorin os 9 core is ubuntu based is canonical the developer of the distro and are they who keep it up to date. it seems to work right out of the box and also has the same apps already installed that linux mint comes with. i like the desktop better than linux mint. it is also has support until 2019. i was just curious about it because you don't read alot about it as with other linux distros.

the poorguy

---

### Post by QIII on 2015-09-19
No.  Zorin is *based* on Debian/Ubuntu, but it's not Debian and it's not Ubuntu and Canonical does not maintain it.

Zorin is developed and maintained by a group in Ireland.

Have a look [here]("http://zorinos.com/").

---

### Post by v3.xx on 2015-09-19
Its standing well to the test of time.  I think it was 2009 when I first heard of it.  Its got a windows like layout, makes it popular.

---

### Post by poorguy on 2015-09-19
it does have a windows layout and i can see why it would be a good choice for people who were coming from windows to linux. it navigates easily and it does come with alot of software on the install. it also doesn't seem to require much to run it i have it on a (1.8 ghz core 2 duo e4300) and (4 gb of ddr2 ram) (nvidia 8400gs pcie) graphics card and it flies.

the poorguy

---

### Post by v3.xx on 2015-09-19
Are you running compiz?

---

### Post by poorguy on 2015-09-19
no.
should i.

---

### Post by v3.xx on 2015-09-19
I like compiz for the eye candy.  I don't know how well it will perform on yours.  You can switch between the two to test it out.  What are you running?

```
update-alternatives --get-selections | grep x-window-manager
```

---

### Post by poorguy on 2015-09-19
> **v3.xx said:**
> I like compiz for the eye candy.  I don't know how well it will perform on yours.  You can switch between the two to test it out.  What are you running?

```
update-alternatives --get-selections | grep x-window-manager
```

as for distro zorin os 9 core 32 bit.

as for hardware 1.8 ghz e4300 core2duo / 4.0 gb ddr2 ram 800 mhz fsb / nvidia geforce 8400 gs pcie graphics card / 80 gb hard drive.  pulled it out of some rich persons trash can and it needed a new power supply and a new os.  it runs fast as hell for what it is. it was sitting in the corner of my work shop and i decided to install zorin os 9 core. it is only 32 bit as that is all the motherboard will support.
when i tried to install 64 bit anything it would install and finish and then upon reboot it would post and boot up and then lookup. checked the motherboard for bad capacitors and couldn't find any it just won't run 64 bit os but that is ok cause i ain't got no problems with 32 bit.

the poorguy

---

### Post by v3.xx on 2015-09-19
> got no problems with 32 bit
Hehe, got no problems with it either, just started running 64 bit last year :)

I don't think you understand, by entering the above code in terminal will output the name of your current running window manager.  I suspect its metacity.  I run Mate desktop which uses marco window manager (a variation of metacity), as shown in the output.

```
m14@m14:~$ update-alternatives --get-selections | grep x-window-manager
x-window-manager               auto     /usr/bin/marco
```

This is a bit dated, but still good reading
[https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity)
and if you wish to try compiz
[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

You may have a GUI in your menu for switching between the two window managers.

If not already loaded, the command is..
```
sudo apt-get install compiz compizconfig-settings-manager
```

Compiz can bork the desktop with certain plugins or a combination there of.  So don't try to load everything at once :)

---

### Post by night_sky2 on 2015-09-19
I also prefer a Redmond-style layout when it comes to desktop computing but there nothing that Zorin OS can offer me that Linux Mint doesn't already.

---

### Post by poorguy on 2015-09-20
yeah you are right i wasn't sure of what you were asking.
i will have to do some reading from the supplied links and see what happens.
yeah zorin really doesn't offer anymore than mint it is just another distro that i had apparently created when i first was trying out linux and decided to install it on this old desktop and play around on it.

the poorguy

---

