---
title: "Getting X Windows to run on Sun Ultra Server 1"
date: 2007-12-14
forum: Sun Sparc Users
---

### Post by wililupy on 2007-12-14
Hello All,

I am having a few problems running gdm on my Sun Ultra Server 1. Yes it is that old, and I was tired of running Solaris on it, so I figured I would try to run Ubuntu on it and use it to perform all my remote administration on my Solaris servers. This is where I ran into problems. 
I first tried to install Gutsy on the server, but ran into an issue where it couldn't detect the CDROM drive after booting up into the kernel. Switching to another Terminal and typing modprobe esp didn't work, esp wasn't a valid device, sucks to see that the Ubuntu community decided to quit supporting this device with this release. So I went back into the past and pulled out Dapper, which worked like a champ. I was able to install with no hiccups. I then tried to install the regular ubuntu desktop, logged in, ran sudo apt-get install ubuntu-desktop and let it download and start setup over night. 
I came in this morning, system was asking for the video card. It has a Sun TurboXGX 13W3 video card. After a little research, found that the Suncg6 driver "should" work with it. So I setup my monitor and everything and thought, cool this is going to work. 
Reboot the machine after all was said and done, and boom, got a nice pretty screen saying gdm disabled. So I read the logs and found that the resolution on my screen was set to high. I guess the driver for my video card doesn't support 24 bits. So I dumbed it down to 16. Still no joy. So I go extreme, 1, and still the same error:

SUNCG6(0): Given depth (1) is not supported by this driver
UnloadModule: "suncg6"
Screen(s) found, but none have a usuable configuration.

I am using a Sun GDM-5410 monitor that is more than capable.

Any help would be greatly appreciated.

Thanks,
Luke

---

### Post by zanderred on 2007-12-14
hi, ubuntu use's gnome this may be to much for you're graphics card have you tryed xubuntu

---

### Post by wililupy on 2007-12-17
I had Gnome running under Solaris 9, so I know that it can handle Gnome, but I just use Exceed 10 to perform remote administration via GUI. Otherwise, I will use command line when I have to.

---

