---
title: "Cannot access repository."
date: 2007-01-07
forum: Repositories &amp; Backports
---

### Post by amhow2 on 2007-01-07
I'm using xubuntu 6.10 and I cant access any repositories. I always get the message [I]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/I] 
My internet connection works fine, I'm using it now. I've tried a few different things, such as changing mirrors and ones in different countries. I read that someone said that the 6.10 repositories were empty and switching to the 6.06 ones worked but this doesn't work either. I've noticed that it serches for language specific packages so I even tried switching the default language to US English, but still no joy. The problem is the same when i try it through either Synaptic "Add/Remove programs". 
This is getting really frustrating and any help would be really appreciated! This is only my second day using Linux so as little command line work as possible would be great :)

---

### Post by bapoumba on 2007-01-07
Hello,
please open a terminal (in accessories menu), run : **cat /etc/apt/sources.list** and paste the complete output.

---

### Post by ingo on 2007-01-07
Have you ever been able to access repositories? Have you actually enabled any repositories in synaptic or adept?

---

### Post by amhow2 on 2007-01-07
## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper main restricted
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-updates main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper universe multiverse
# deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse

It seems changes i make in the "Software sources" interface arent always reflected here, I can't write to the .list file with mousepad, and unfortuneately i have no idea how to edit it in the terminal.

I've just installed xubuntu 2 days ago and haven't been able to access the repository at all.

---

### Post by bapoumba on 2007-01-07
Okay,

1- please open the terminal again, and run **sudo nano -B /etc/apt/sources.list**.
nano is a small text editor, the -B option will backup your file with an ~ extension.

2- Remove all the **#** at the beginning of each **deb** line. The # turns the line into a commentary. Leave the other ones. For ex :
```
...
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
[COLOR="Red"]#[/COLOR] deb http://au.archive.ubuntu.com/ubuntu/ edgy universe
...
```
Just take out the red one, not the ones from above, the above lines are real comments ;-)

3- Proceed for every deb line.

4- Then CTRL + O will save the file (same name) and CTRL + X  will exit nano.

5- **sudo apt-get update** or **sudo aptitude update**
Are there any other errors ? If so, paste again your modified source.list file.

---

### Post by amhow2 on 2007-01-07
It comes back with

---

### Post by amhow2 on 2007-01-07
It comes back with "E: The update command takes no arguments"

The list now reads

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse

---

### Post by ingo on 2007-01-07
Hi,

at least your sources.lst file is now in order in that you enabled the repositories. They were disabled by default because during the install you had no access to the internet. You could have done this using the GUI of adept, but this is just fine. 

So when do you get 

> It comes back with "E: The update command takes no arguments"

Have you tried **sudo apt-get install update** on the shell? That should do the trick.

---

### Post by amhow2 on 2007-01-07
> **ingo said:**
> Hi,

at least your sources.lst file is now in order in that you enabled the repositories. They were disabled by default because during the install you had no access to the internet. You could have done this using the GUI of adept, but this is just fine. 

So when do you get 



Have you tried **sudo apt-get install update** on the shell? That should do the trick.
Sorry that was just a typing error on my part. When i enter "sudo aptitude update" it comes back with  "Could not connect to archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/universe Translation-en_AU      
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy Release                                      
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy-backports/multiverse Translation-en_AU    
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0). - connect (113 No route to host)"  And it just goes on and on like that

---

### Post by bapoumba on 2007-01-07
Well, there is still the au.ubuntu repositories giving you errors. Please paste again the complete output to **cat /etc/apt/sources.list**.

What kind of router do you have ? have you enabled DHCP ?
Also paste the output to those 3 commands :
```
cat /etc/resolv.conf
cat /etc/network/interfaces
ifconfig
```

---

### Post by amhow2 on 2007-01-07
> **bapoumba said:**
> Well, there is still the au.ubuntu repositories giving you errors. Please paste again the complete output to **cat /etc/apt/sources.list**.

What kind of router do you have ? have you enabled DHCP ?
Also paste the output to those 3 commands :
```
cat /etc/resolv.conf
cat /etc/network/interfaces
ifconfig
```
**cat etc/apt/sources.list returns** 
"## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper main restricted
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-updates main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper universe multiverse
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) dapper-updates universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy universe main multiverse

" ** cat /etc/resolv.conf returns** "nameserver 192.168.1.1"        

**cat /etc/network/interfaces returns**  
"auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
address 10.1.1.2
netmask 255.0.0.0
gateway 10.1.1.1

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp"

**ifconfig returns**
"eth0      Link encap:Ethernet  HWaddr 00:0F:20:22:90:71  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:20ff:fe22:9071/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10581 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3891185 (3.7 MiB)  TX bytes:2017764 (1.9 MiB)
          Interrupt:10 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:366 (366.0 b)  TX bytes:366 (366.0 b)"

Im using a netgear router (WGT634U) with DHCP enabled.

---

### Post by bapoumba on 2007-01-07
1- edit again your sources.list (**sudo nano -B /etc/apt/sources.list**) and remove all the **au.** from the reposiroties. For ex :
deb [http://**au.archive](http://**au.archive)**.ubuntu.com/ubuntu/ edgy universe becomes :
deb [http://**archive](http://**archive)**.ubuntu.com/ubuntu/ edgy universe

And so on. (same as before, CTRL+O to save, CTRL + X to exit)

2- edit your /etc/network/interfaces (**sudo -B nano /etc/network/interfaces**) and remove :
```
address 10.1.1.2
netmask 255.0.0.0
gateway 10.1.1.1
```

so that the line for eth0 (which I suppose is the one connected to internet) looks like :
```
auto eth0
iface eth0 inet dhcp
```

note : in my interfaces file, the auto eth0 is in second line, it may not be important, I do not know. My router has the same DNS address as yours. Works for me, should work for you.

3- either reboot or 
```
sudo ifdown eth0
sudo ifup eth0
```
(I am not a network wiz, I know reboot will do it).

4- **sudo apt-get update** or **sudo aptitude update**
Do you still get errors ?

---

### Post by amhow2 on 2007-01-07
**sudo aptitude update** returns:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
0% [Connecting to archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                                     
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out

---

### Post by bapoumba on 2007-01-07
[http://ubuntuforums.org/showthread.php?t=283712]("http://ubuntuforums.org/showthread.php?t=283712")
You may want to check this thread, in particular post #10 :
[http://ubuntuforums.org/showpost.php?p=1709298&postcount=10]("http://ubuntuforums.org/showpost.php?p=1709298&postcount=10")
about D-link router.

edit : [http://ubuntuforums.org/showthread.php?t=282034]("http://ubuntuforums.org/showthread.php?t=282034")
Here is another one.

---

### Post by amhow2 on 2007-01-07
> **bapoumba said:**
> [http://ubuntuforums.org/showthread.php?t=283712]("http://ubuntuforums.org/showthread.php?t=283712")
You may want to check this thread, in particular post #10 :
[http://ubuntuforums.org/showpost.php?p=1709298&postcount=10]("http://ubuntuforums.org/showpost.php?p=1709298&postcount=10")
about D-link router.

edit : [http://ubuntuforums.org/showthread.php?t=282034]("http://ubuntuforums.org/showthread.php?t=282034")
Here is another one.
Great! It worked right away! :) Thanks heaps for all of your help! I was dreading going back to XP! I guess what it said was true, "Look around the forums, everything has been answered before", only problem is I never know what to look for :D Thanks again!

---

### Post by bapoumba on 2007-01-07
Welcome, nice to know you got it working. Enjoy :)

---

### Post by HeXaDeC on 2007-01-17
Thank-you from me too...........worked right away. ;) 

after lots of ](*,) .........good way to learn though. :D

---

