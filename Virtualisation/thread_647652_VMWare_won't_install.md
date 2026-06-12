---
title: "VMWare won't install"
date: 2007-12-22
forum: Virtualisation
---

### Post by CCBalla10 on 2007-12-22
ok...so i tried installing vmware server today and i'm getting this error..
 ```
E: /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_i386.deb: subprocess pre-installation script returned error exit status 1

```

what am I doing wrong?

---

### Post by fjgaude on 2007-12-22
If you have Gutsy or Feisty, you can install using Synaptic, and that gets all the dependencies for you. It has worked for me several times on many machines.

---

### Post by CCBalla10 on 2007-12-23
> **fjgaude said:**
> If you have Gutsy or Feisty, you can install using Synaptic, and that gets all the dependencies for you. It has worked for me several times on many machines.

that is what i'm trying to do...and this is the error i'm getting back

---

### Post by hkazemi on 2008-01-27
I wanted to install VMWare Server and also ran into this problem.  Here's how it happened and how I fixed it.

I first found VMWare on Ubuntu install instructions for Feisty 7.04 with comments saying it also works for Gutsy 7.10.
[http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto](http://www.howtoforge.com/ubuntu_feisty_fawn_vmware_server_howto)
The first two comments are important, to use 'sudo rm /etc/vmware' and to use 'sudo ./vmware-install.pl'.
(It is also noted at [http://ubuntuforums.org/showthread.php?t=204641](http://ubuntuforums.org/showthread.php?t=204641) that 'sudo perl vmware-install.pl' works.)
I downloaded the VMware-server-1.0.4-56528.tar.gz file from vmware.com and the following
[http://knihovny.cvut.cz/ftp/pub/vmware/](http://knihovny.cvut.cz/ftp/pub/vmware/)
[http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update115.tar.gz)
About the vmware-any-any patch:
[http://communities.vmware.com/message/76957](http://communities.vmware.com/message/76957)

Just after I launched vmware-install.pl, I learned that Vmware Server was available in a gusty-commercial repository.  At this point I canceled the vmware-install.pl with Ctrl-Z.  I did this because I prefer to install via Synaptic if at all possible.

Repository information:
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

I ran the Synaptic package manager and tried to add the gusty-commercial repository, but I got errors when trying to reload/update the repository list. Error: Could not download all repository indexes.

At [http://ubuntuforums.org/showthread.php?t=667698](http://ubuntuforums.org/showthread.php?t=667698) I found that the repository name had changed from:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy-commercial main

to:
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

After fixing that, I tried to install Vmware thru Synaptic, but got a warning about a previous Vmware install and soon after an error:
E: /var/cache/apt/archives/vmware-server_1.0.4-1gutsy2_i386.deb: subprocess pre-installation script returned error exit status 1

Searching for an answer brought me to this thread.

I then tried to reinstall using the vmware-install.pl script I had canceled before.  When I tried to re-start the command line I got the error describe at [http://tipotheday.com/node/7](http://tipotheday.com/node/7) :

"You get this error when trying to install VMware Server after having had the VMware Player installed -- in my case it was on Ubuntu after using the vmware-player package from the repository.

The error looks like this:
mshade@gobot:~/vmware/vmware-server-distrib$ sudo ./vmware-install.pl
A previous installation of VMware software has been detected.

Failure

Execution aborted.

It's finding files in /etc/vmware leftover from the previous installation. You can do either of the following commands to fix:
mv /etc/vmware /etc/vmware.bak
OR
rm -rf /etc/vmware

You may need to elevate privileges by prefacing the command with sudo or becoming root with su.

Rerun vmware-installer.pl and all should be well."

So now, neither vmware-install.pl nor Vmware via Synaptic was working.  I ran 'rm -rf /etc/vmware', then tried installing Vmware via Synaptic and it worked!

---

