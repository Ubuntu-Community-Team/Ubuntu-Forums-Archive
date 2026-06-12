---
title: "RPM to DEB install of VMware 2 beta2 broken"
date: 2008-04-20
forum: Virtualisation
---

### Post by Chibana on 2008-04-20
I'm not sure if this is the right forum category.  This post might be better in a forum more related to apt.  I made the mistake of trying to install VMware 2 beta 2 using the RPM package and converting it to DEB via "alien --scripts -d".  That part worked.  Then I installed it with "dpkg -i".  That also seemed to work, but VMware didn't work.  I thought I successfully uninstalled vmware-server via aptitude.

However, today I ran synaptic to get the updates that are available, and it immediately failed with an error message and kicks me out of the program.  So, I tried aptitude.  It's complaining about a broken install of this version of VMware, and to try to reinstall it first.  I did that.  Now, when I try to uninstall via aptitude, I get this error:

Removing vmware-server ...
[: 62: remove: bad number
shift: 62: can't shift that many

dpkg: error processing vmware-server (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Press return to continue.

I have no idea what to do.  I've Googled on "can't shift that many", and haven't found any help there.  There has to be some way to tell apt to drop this package from it's database or force an uninstall.  I've read the man page and still have not found anything to clear this up.  Until I get this cleared up, I am unable to install any updates, or use synaptic/apt for anything.

Any help would be greatly appreciated!

[EDIT:]  I probably should also add that this system is Kubuntu 7.10 on AMD64.

---

### Post by Chibana on 2008-04-25
I fixed it. Just like almost everything else in UNIX, the data for this system is just in some text files in /var/lib/dpkg. I ran "grep -r vmware-server *" in this directory and found the files I need to edit or delete. This package was referenced in the "status" and "available" files. I made a backup of the /var/lib/dpkg directory, just in case. Then I simply edited those files and deleted the entries for this package. I also deleted the files in the info directory that started with "vmware-server". I then ran synaptic, and the problem was gone. It's like vmware-server was never (incorrectly) installed via the apt system. I was able to successfully get the few updates that were available.

---

### Post by rafalmag on 2008-04-27
Thank you Chibana, I had the same problem with vmware-server. Now everything works fine.

---

### Post by quip on 2009-01-15
Just wanted to say that thanks also, as I too had the same problem, and the fix mentioned works.

---

### Post by uzi09 on 2009-01-21
geez, there should be some sort of a warning.

i had the same problem too...somehow i feel like the remenents are still there, we just wiped it off apt's list though :S.

based on what it said in status, it pointed to a lot of config files in /etc/vmware -- i just deleted the whole directory as well and am going to try to install it through the tar files and this tutorial:
[http://www.howtoforge.com/how-to-install-vmware-server-2-on-an-ubuntu-8.04-desktop](http://www.howtoforge.com/how-to-install-vmware-server-2-on-an-ubuntu-8.04-desktop)

EDIT:
also got these lines come up during re-install:

```
The file /etc/init.d/vmware that this program was about to install already 
exists. Overwrite? [yes] yes

The file /etc/init.d/vmware-core that this program was about to install already
exists. Overwrite? [yes]

The file /etc/init.d/vmware-mgmt that this program was about to install already
exists. Overwrite? [yes]

The file /etc/init.d/vmware-autostart that this program was about to install 
already exists. Overwrite? [yes]
```

---

### Post by Dedoimedo on 2009-01-22
The simplest way is to install using the archives.
Not the easiest, but less errors and issues.
Dedoimedo

---

### Post by bodhi.zazen on 2009-01-22
> **Dedoimedo said:**
> The simplest way is to install using the archives.
Not the easiest, but less errors and issues.
Dedoimedo

What Dedoimedo said.

Alien should be used as an absolute LAST resort, because, well as has been indicated in this thread, it will over write lib ...

---

