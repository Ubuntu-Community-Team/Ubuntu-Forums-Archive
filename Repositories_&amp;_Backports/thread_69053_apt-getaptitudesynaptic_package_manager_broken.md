---
title: "apt-get/aptitude/synaptic package manager broken"
date: 2005-09-25
forum: Repositories &amp; Backports
---

### Post by striketh on 2005-09-25
Hello. Out of the blue, apt-get and aptitude started showing segmentation faults no matter what I do. Also, synaptic package manager will crash after starting.

I can run the synaptic package manager in a terminal and it will start, however it spits out a bunch of errors. I can still get updates with the synaptic package manager despite all these problems. I however am unable to edit the repositories it uses from within the program itself. As soon as I click on "Repositories" the window opens and immediatly closes. Any help would be appreciated.

> W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by manicka on 2005-09-25
The servers are down, just be patient

---

### Post by heimo on 2005-09-25
Some Ubuntu repository mirrors are down at the moment. You can 1) wait, 2) edit /etc/sources.list using *gksudo gedit /etc/apt/sources.list *and change every "broken" http -> ftp

---

### Post by striketh on 2005-09-25
Ok..however, I still have the problem with apt-get and aptitude showing the segmentation faults. Are those also related to the sites being down?

---

### Post by heimo on 2005-09-25
[QUOTE=striketh]Ok..however, I still have the problem with apt-get and aptitude showing the segmentation faults. Are those also related to the sites being down?[/QUOTE]

Unrelated. I believe some version of Synaptic had this problem - I don't know about current status. Mine (on Breezy) doesn't segfault. 

EDIT: apt-get and aptitude? Not Synaptic?
EDIT2: (reread your messages) Oh... Could you give more details - exactly after what does it segfault?

---

### Post by striketh on 2005-09-25
[QUOTE=heimo]Unrelated. I believe some version of Synaptic had this problem - I don't know about current status. Mine (on Breezy) doesn't segfault. 

EDIT: apt-get and aptitude? Not Synaptic?
EDIT2: (reread your messages) Oh... Could you give more details - exactly after what does it segfault?[/QUOTE]

If I try to do any command regarding apt-get or aptitude I get a seg fault.

gandalf@dhcppc0:~$ aptitude search realplayer
Segmentation fault
gandalf@dhcppc0:~$

gandalf@dhcppc0:~$ apt-get search realplayer
Segmentation fault
gandalf@dhcppc0:~$

(just using realplayer as an example to show the seg fault)

---

### Post by heimo on 2005-09-25
Uh... that's bad. Do you have any other versions of dpkg in /var/cache/apt/archives?
 ```
ls /var/cache/apt/archives/dpkg
``` 

Does dpkg work? You could try to reinstall dpkg using dpkg... :D (That's always fun, and dangerous.) ```
sudo dpkg -i /var/cache/apt/archives/dpkg_(what ever version).deb
``` 

:-/ :-\

---

### Post by striketh on 2005-09-25
[QUOTE=heimo]Uh... that's bad. Do you have any other versions of dpkg in /var/cache/apt/archives?
 ```
ls /var/cache/apt/archives/dpkg
``` 

Does dpkg work? You could try to reinstall dpkg using dpkg... :D (That's always fun, and dangerous.) ```
sudo dpkg -i /var/cache/apt/archives/dpkg_(what ever version).deb
``` 

:-/ :-\[/QUOTE]

dpkg works. How would I go about reinstalling using dpkg?

---

### Post by heimo on 2005-09-25
I'm not sure what is causing your problems, but I'd probably try to reinstall apt and aptitude from /var/cache/apt/archives (if you still have those packages in cache), using dpkg -i as shown above. Before that, you could try to run dpkg --configure -a to make sure that no packages are partially installed.

---

### Post by striketh on 2005-09-25
[QUOTE=heimo]I'm not sure what is causing your problems, but I'd probably try to reinstall apt and aptitude from /var/cache/apt/archives (if you still have those packages in cache), using dpkg -i as shown above. Before that, you could try to run dpkg --configure -a to make sure that no packages are partially installed.[/QUOTE]

That seems to have worked for me. No more error. Thanks. But one has to wonder how that came about in the first place.

---

