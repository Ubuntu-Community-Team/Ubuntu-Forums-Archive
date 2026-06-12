---
title: "Installing Desktop from 13.04 Server"
date: 2013-01-31
forum: Ubuntu Development Version
---

### Post by mrfelker on 2013-01-31
Because I  have a RAID setup so I had to get the  Server ISO and then use command like 'sudo apt-get install aptitude and the aptitude  ubuntu-gnome-desktop I  happen to like Gnome 3 but  the pre-kKDE 4.10 is nice as well. Install synpatic for that stuff.  

I use the last   kernel 3.6 for raring in order to install VMware WS without a giant hassle.  

I like this OS very much.

I find that I need need to do as 'sudo aptitude update and sudo ap[titude dist-upgrade every day and keep up with the devs.  When it falls apart  I'll  just get another daily build land start again.

---

### Post by zika on 2013-01-31
> **mrfelker said:**
> Because I  have a RAID setup so I had to get the  Server ISO and then use command like 'sudo apt-get install aptitude and the aptitude  ubuntu-gnome-desktop I  happen to like Gnome 3 but  the pre-kKDE 4.10 is nice as well. Install synpatic for that stuff.  

I use the last   kernel 3.6 for raring in order to install VMware WS without a giant hassle.  

I like this OS very much.

I find that I need need to do as 'sudo aptitude update and sudo ap[titude dist-upgrade every day and keep up with the devs.  When it falls apart  I'll  just get another daily build land start again.Carefull with dist-upgrade... Watch what is going to be removed (if any) before hitting Y...
Example:
```
:~$ sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  lightdm-remote-session-uccsconfigure ubuntu-desktop unity
The following packages will be upgraded:
  compiz compiz-core compiz-gnome compiz-plugins compiz-plugins-default
  libcompizconfig0 libdecoration0
7 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 6,177 kB of archives.
After this operation, 5,281 kB disk space will be freed.
Do you want to continue [Y/n]? 
```

---

### Post by ibjsb4 on 2013-01-31
If that happens with a dist-upgrade, what happens with a standard upgrade?  
Worst?

---

### Post by grahammechanical on 2013-01-31
We are about half way through the development cycle. It is the time when we see more visual changes as we update daily than earlier on in the cycle. The login screen now says 13.04. Design is becoming more important in Ubuntu and so it should be interesting to see what comes down from the repositories for Ubuntu between now and 14.04 release day.

Regards.

---

### Post by paul_in_london on 2013-01-31
> **ibjsb4 said:**
> If that happens with a dist-upgrade, what happens with a standard upgrade?  
Worst?

This might help:

[http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade](http://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade)

If you're not sure and apt-get dist-upgrade (or aptitude full-upgrade) wants to remove stuff run apt-get upgrade (or aptitude safe-upgrade) instead.

It's also worth bearing in mind that if you're going to install a DE/WM you'd probably be better off starting with the mini.iso instead of the server iso:

[http://askubuntu.com/questions/111092/what-is-the-difference-between-minimal-desktop-server-editions/111099#111099](http://askubuntu.com/questions/111092/what-is-the-difference-between-minimal-desktop-server-editions/111099#111099)

[http://askubuntu.com/questions/44185/is-using-ubuntu-minimal-any-different-from-server](http://askubuntu.com/questions/44185/is-using-ubuntu-minimal-any-different-from-server)

You'll find the latest minimal netboot (mini.iso) images here:

[http://archive.ubuntu.com/ubuntu/ubuntu/dists/raring/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/raring/main/installer-i386/current/images/netboot/)

[http://archive.ubuntu.com/ubuntu/ubuntu/dists/raring/main/installer-amd64/current/images/netboot/](http://archive.ubuntu.com/ubuntu/ubuntu/dists/raring/main/installer-amd64/current/images/netboot/)

---

### Post by ibjsb4 on 2013-01-31
> you'd probably be better off starting with the mini.iso instead of the server iso

[http://ubuntuforums.org/showthread.php?p=12395977#post12395977](http://ubuntuforums.org/showthread.php?p=12395977#post12395977)

---

### Post by paul_in_london on 2013-01-31
From this page:

> only on the "server install": linux-server kernel and modules

> only on the "command-line install": linux-generic kernel, modules and restricted modules + acpi, acpid and language-pack-en
 
> ...you may wish to also try the MinimalCD as a base starting point

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

> While the minimal system installed using the Ubuntu Server image is undoubtedly a genuine minimal system as known and loved by minimalist lovers, there is a slight differences in the package package selection compared to the Minimal CD. In fact, Minimal CD pulls in 7 extra packages during installation, which I (@Oxwivi) personally deem them to be all but redundant. But for the information freaks (like myself) who will have nagging doubts if the details are not known, the seven in question are: daemon, dictionaries-common, discover, discover-data, language-pack-gnome-en, language-pack-gnome-en-base, libdiscover2, mpt-status, wamerican and wbritish.

[http://askubuntu.com/questions/203122/how-do-i-do-a-minimal-install-without-an-internet-connection](http://askubuntu.com/questions/203122/how-do-i-do-a-minimal-install-without-an-internet-connection)

The other aspect to consider is that (by default) the "Minimal" install will give you a kernel optimised for desktop use:

> The Server Edition uses the Deadline I/O scheduler instead of the CFQ scheduler used by the Desktop Edition.

> Preemption is turned off in the Server Edition

> The timer interrupt is 100 Hz in the Server Edition and 250 Hz in the Desktop Edition

> The Server Edition is optimized for i686 processors while the Desktop Edition is optimized for both the i586 and i686

> Virtualization is better supported in the Server Edition through the enabling of IPC namespaces, and the Xen hypervisor

> Multiple routing tables for the IPv6 protocol are also supported in the Server Edition

[http://askubuntu.com/questions/44185/is-using-ubuntu-minimal-any-different-from-server](http://askubuntu.com/questions/44185/is-using-ubuntu-minimal-any-different-from-server)

---

### Post by paul_in_london on 2013-01-31
> **Cheesemill said:**
> Not true. A minimal server installation won't have anything on it that you don't choose. Apache and everything else you mentioned are optional extras that you can choose if you want to.

[B][COLOR="Red"]Also the Desktop and Server versions now use identical kernels as well.
[/COLOR][/B]
For a package and memory comparison for the different minimal installs check out my post [here]("http://ubuntuforums.org/showpost.php?p=12156448&postcount=10").

I stand corrected. I didn't realise that, by default (i.e. ignoring the advanced cli option which gives a choice of kernels), the server and desktop installs now use identical kernels. 

@Cheesemill - thanks for the post about the package set differences. :-)

[http://ubuntuforums.org/showthread.php?t=1978444](http://ubuntuforums.org/showthread.php?t=1978444)

[http://askubuntu.com/questions/122493/why-is-12-04-removing-the-server-kernel-flavour](http://askubuntu.com/questions/122493/why-is-12-04-removing-the-server-kernel-flavour)

---

