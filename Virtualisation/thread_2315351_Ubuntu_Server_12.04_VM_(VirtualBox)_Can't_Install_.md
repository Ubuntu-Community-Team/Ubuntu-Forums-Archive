---
title: "Ubuntu Server 12.04 VM (VirtualBox): Can't Install DHCP server"
date: 2016-02-27
forum: Virtualisation
---

### Post by Pandorachaos on 2016-02-27
Hello all,

I'm new to Ubuntu and Linux in general, so I'm having a bit of trouble installing the DHCP server on my Ubuntu Server 12.04 VM using VirtualBox.

I typed in the command: sudo apt-get install dhcp3-server .   It wasn't installed, and I received the message that:

The following packages have unmet dependencies:  dhcp3-server : Depends : isc-dhcp-server but it is not going to be installed  E:  Unable to correct problems, you have held broken packages.

So, I typed in:  sudo apt-get install isc-dhcp-server  .  I received a similar message stating:

The following packages have unmet dependencies:  isc-dhcp-server : Depends : libcap2 (>= 2.10) but it is not installable.  (Same 'E' message as above).

So, being new to Linux, I am now at an impasse.  I would also like to state that this is for a college class as a lab assignment.  My first step was to install the DHCP server, but I haven't been able to.

Any help would be greatly appreciated :)

Thanks in advance!

---

### Post by gordintoronto on 2016-02-28
First you need to get rid of the broken packages error.

---

### Post by ecaep on 2016-02-29
Pandorachaos use the following command to determine the broken packages are, and then install any that are missing.

sudo apt-get check

Let me know if you have any further questions or other issues come up.

---

### Post by slickymaster on 2016-02-29
*Moved to the ***Virtualisation*** sub-forum*

---

### Post by Pandorachaos on 2016-03-05
Sorry for the delay (busy week) and thanks to slickymaster for moving this to the correct forum.  I found out that I could install DHCP on my desktop version of Ubuntu 12.04 (I had a VM as a client and one as the server), so I ended up just installing another VM with desktop edition to use as a server.  This corrected my issue, and I was able to turn it in.

I already deleted the server VM that gave me issues, but I did try installing another server edition before I decided to install the desktop edition (to serve as my server), and had the same problems.  Right now I'm working on another assignment, so when I do get time, I'll reinstall another server edition and try the sudo apt-get check and try to install the broken/missing packages so that maybe I'll be able to resolve this in the event that another person has similar issues.

Thanks gordintoronto and ecaep for the replies!

---

### Post by MAFoElffen on 2016-03-06
Note: The "clean" option only clears out the local repository of retrieved package files, but only removes package files that can no longer be downloaded... That is also incomplete as a solution because is will still leave the packages there half-installed
```

sudo apt-get autoclean
sudo apt-get install -f

```
the second command should try to install the dependencies and fix broken packages. Pay attention to the last 5 lines of output. There should be a message saying something like:
```

x upgraded, x newly installed, x to remove and x not upgraded.

```
If if fixed the packages, but did not install it, it will show in that line... If so, tell me and there would be more to do to resolve that.

I install dhcp on Ubuntu Server with this command:
```

sudo apt-get install isc-dhcp-server

```
That is the parent package. For instructions, refer to page 46 of the [Ubuntu Server Guide]("https://help.ubuntu.com/lts/serverguide/serverguide.pdf").

So what may be easier is to remove what you did, and install with that command...
```

sudo apt-get remove dhcp3-server

```
The config file is at /etc/dhcp/dhcpd.conf... If you have any questions, just ask.

Are you setting this lab up for other VM's?

---

### Post by Pandorachaos on 2016-06-01
Ok sorry, now I'm back.  I made it through the class since the techs at our school set up VMWare on the cloud with Ubuntu 12.04, so I just used that for the rest of the semester.  But, I still would like to get this solved.

So I installed another VM the same way I did before.

> [COLOR=#000000]ecaep[/COLOR][COLOR=#000000][INDENT]**Re: Ubuntu Server 12.04 VM (VirtualBox): Can't Install DHCP server**
Pandorachaos use the following command to determine the broken packages are, and then install any that are missing.

sudo apt-get check

Let me know if you have any further questions or other issues come up.[/INDENT]
[/COLOR][COLOR=#000000][INDENT]

I did this and it outputted:

```
Reading package lists . . . done
Building dependency tree
Reading state information . . . done
```

[/INDENT]
[/COLOR]
[COLOR=#000000]> [INDENT][B]MAFoElffen
Re: Ubuntu Server 12.04 VM (VirtualBox): Can't Install DHCP server
[/B]Note: The "clean" option only clears out the local repository of retrieved package files, but only removes package files that can no longer be downloaded... That is also incomplete as a solution because is will still leave the packages there half-installed[/INDENT]
Code:
sudo apt-get autoclean
sudo apt-get install -f
the second command should try to install the dependencies and fix broken packages. Pay attention to the last 5 lines of output. There should be a message saying something like:
Code:
x upgraded, x newly installed, x to remove and x not upgraded.[INDENT]If if fixed the packages, but did not install it, it will show in that line... If so, tell me and there would be more to do to resolve that.[/INDENT]
[INDENT]

Running these two commands produced the same as above code with the end giving me:

```
0  upgraded, 0 newly installed, 0 to remove and 107 not upgraded.
```[/INDENT]
[/COLOR]

This WAS to be set up with another client VM running Ubuntu 12.04 desktop edition.

Thanks MAFoElffen for the help.  I really appreciate all of the posts.

---

