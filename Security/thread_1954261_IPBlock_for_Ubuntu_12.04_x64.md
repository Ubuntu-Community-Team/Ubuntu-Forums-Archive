---
title: "IPBlock for Ubuntu 12.04 x64?"
date: 2012-04-07
forum: Security
---

### Post by terrykiwi83 on 2012-04-07
Have been looking at setting up some IPFilters for my system, I have come across IPBlock here ([http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html](http://www.ubuntugeek.com/ipblock-graphical-ip-blocker.html)).

However it is for an older Ubuntu release, does anyone know of an update or something similar with a nice GUI?

BTW the Transmission blocklist is not an option as I don't use Transmission. Mainly Deluge and QBBittorrent.

Cheers

---

### Post by starz677 on 2012-06-02
Please dont tell me ipblock wont work on ubuntu 12.04 ?

---

### Post by BoogeyOfTheMan on 2012-07-20
Bump

I am looking for an answer to this question as well.

---

### Post by azharahs on 2012-07-21
If you can't find a package for your version of Ubuntu, you can always download the source and compile it from there for your system. It can be found at [http://sourceforge.net/projects/iplist](http://sourceforge.net/projects/iplist)

I have two different headless Ubuntu servers that I've installed it on this way, and it works great.  (Had to compile from source to remove the GUI.)

---

### Post by dodo3773 on 2012-07-21
[QUOTE=azharahs] (Had to compile from source to remove the GUI.)[/QUOTE]

What make options did you change to remove the gui? Iplist / ipblock comes with a cli version. It is provided with the package. I don't ever use the gui as I wrote a simple bash wrapper to start it and send the log to stdout so this has me a little interested. Also, have you written a script to change out and update lists? Or do you just do it in the config file? 


For the rest of the posters in this thread: I am downloading an x64 Ubuntu 12.04 iso and I will load it up in VirtualBox and walk you guys through the build process. May be a couple of hours wait. Will let you know.

---

### Post by dodo3773 on 2012-07-21
Note: You probably don't need to install the "checkinstall" package. I had installed it to build it from source but I realized it was much simpler then that. 

```

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
sudo apt-get install checkinstall
sudo apt-get install libnetfilter-queue1
wget http://sourceforge.net/projects/iplist/files/iplist/0.29/iplist_0.29-1~squeeze_amd64.deb

```

Now just navigate to it in your file manager and double click it to open it with Ubuntu Software Center. Install it.

Now open it like this:
```

sudo ipblock -g

```

 Remove the lists in the "Lists" tab. Add / import some new ones from:
 [http://www.iblocklist.com/lists.php](http://www.iblocklist.com/lists.php)
 
 After that enable it and you should be good to go.

---

### Post by Walkingcedar on 2012-08-07
:KS:popcorn:Thank you so much for being one of those who solved this issue. I do notice that I have to leave the terminal open, in order for the program to stay open. I did notice that if I close the terminal, the program closes. If I reopen the terminal, then the program, it immediately is enabled, already. Again. Thanks. I will do this on all of my 12.04 devices.

---

### Post by dodo3773 on 2012-08-07
> **Walkingcedar said:**
> :KS:popcorn:Thank you so much for being one of those who solved this issue. I do notice that I have to leave the terminal open, in order for the program to stay open. I did notice that if I close the terminal, the program closes. If I reopen the terminal, then the program, it immediately is enabled, already. Again. Thanks. I will do this on all of my 12.04 devices.

Your welcome. It's the same for all programs that you start in a terminal. You can create a script or do "sudo ipblock -g & disown". Also, you can backround and disown processes in the terminal by typing these commands: "ctrl+z" "bg" "disown". In that order. Or if you want to you can use the bash wrapper I created (not that big a fan of the java gui). 

ipblockbash.sh
```

#!/bin/bash

trap 'ipblock -d' 0
ipblock -s 
tail -Fq /tmp/ipblock.log 2>/dev/null 

exit

```

---

