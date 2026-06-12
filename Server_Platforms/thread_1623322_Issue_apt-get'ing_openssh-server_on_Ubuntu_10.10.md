---
title: "Issue apt-get'ing openssh-server on Ubuntu 10.10"
date: 2010-11-16
forum: Server Platforms
---

### Post by pdohara on 2010-11-16
Hello,
I am attempting to setup an Ubutu server for mercurial. I was attempting to install the openssh-server using apt-get when I get the error:
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed.  This may mean that you have
requested an impossible situation ot if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of incoming.
The following information may help to resolve the situation:
 
The following packages have unmet dependencies:
 openssh-server : Depends: openssh-client (= 1:5.1p1-6ubuntu2) but 1:5.5p1-4ubuntu4 is to be installed
E: Broken packages

```
I assume (from the version numbers) that the issue is that I have a newer version of the client installed than what I need. Before I backout the client is there a way to work with this version of the client and still install the server? If I get the server source can I create a package from that for this version of the client? Not sure I will do that but I like to know what my options are.
 
BTW, I did not install the client it was installed when I installed the OS.
 
Pat O

---

### Post by CharlesA on 2010-11-16
Try this:

```
sudo apt-get install -f 
```

Haven't had any problems installing openssh-server in Maverick.

---

### Post by FuturePilot on 2010-11-16
It sounds like you may have some issue with your software sources. 5.1p1-6ubuntu2 is the version from 9.10 and 5.5p1-4ubuntu4 is the version from 10.10.

---

### Post by cinohpa on 2010-11-16
So try removing your ssh client and installing again. See if you still get version 5.1p1?

I also use open-ssh server on all of my maveric machines with no install problems or special configuration to install. ssh client is in all of the ubuntu distros. 

Did you recently install maveric? Did you try upgrading or actually reinstalling?

---

### Post by wojox on 2010-11-16
> **CharlesA said:**
> Try this:

```
sudo apt-get install -f 
```

Haven't had any problems installing openssh-server in Maverick.

If that don't work, do an update and an upgrade:

```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by pdohara on 2010-11-19
Thanks for all the reply's.
 
I did try install -f.
 
I did do an update and upgrade.
 
When those things did not work I decided to go back to 10.04 and all was well.  I am working from behind a Proxy server, though I was able to setup that authentication.  It does not matter to me which version of Ubuntu I am using so the step back is fine.
 
Pat O

---

### Post by TheFr00n on 2010-11-29
I have the same problem - cannot get openssh server to install under 10.10. I get an error message about there being no install candidate.

As I write this I am burning a 10.04 iso, because while it had its issues, at least everything worked in 10.04.

---

### Post by mErchamion on 2011-04-27
I am having the same problem here. Updating and upgrading did not work it out. Any Ideas? Please help!

---

### Post by rubylaser on 2011-04-27
What does your /etc/apt/sources.list look like?  And, I always install openssh-server by just
```
sudo apt-get install ssh
```

---

### Post by lagerratrobe on 2011-06-18
This is still a major pain in the butt. Cannot install openssh-server because of "Depends: openssh-client (= 1:5.5p1-4ubuntu4) but 1:5.5p1-4ubuntu5 is to be installed".  Cannot remove openssh-client ("sudo apt-get -f purge openssh-client" does nothing).

This problem is on a machine with a vanilla 64-bit install from CD, with standard repo sources in sources.list, and with "update" and "upgrade" run after installation.

Suggestions to use "-f", or "install ssh" are frankly useless.  

Please provide some sort of advice to help diagnose nature of problem and troubleshoot it.

---

### Post by lagerratrobe on 2011-06-18
One solution to this mess is to download the .deb file for the matching version of openssh-server, openssh-server_5.5p1-4ubuntu5_amd64.deb.

Then install using dpkg: sudo dpkg -i openssh-server_5.5p1-4ubuntu5_amd64.deb

That seemed to do the trick for me.

---

### Post by chenmingyang007 on 2011-08-23
I met this error too. Finally I find the problem lay in my source list. I was not using the update sources associated with ubuntu 10.10. The URLs in file sources.list should contain the word "maverick"(i.e., the code name for Ubuntu 10.10). 

   After deleting the whole content in sources.list , executing "sudo apt-get update" and "sudo apt-get upgrade", I did "sudo apt-get remove openssh-client", and finally uninstalled openssh-client.
 
  Then I searched the ubuntu 10.10 update sources on web and copied them to sources.list. After executing "sudo apt-get update", "sudo apt-get upgrade",  "sudo apt-get install ssh" in order, I installed openssh-server successfully!!!

---

### Post by metal4life on 2011-09-02
If your current version of openssh-client isn't compatible with the  openssh-server you're trying to install, you should be able to remedy  this fairly easily through Synaptic.  You can do this by forcing the  package version to an earlier one that matches.

After finding and selecting your openssh-client package in Synaptic, click the **Package **menu and select **Force Version**.   You should then be able to access a pull-down menu where you can select  openssh-client_1:5:5p1-4ubuntu4 (maverick meerkat).  Downgrade to that  version and then try installing openssh-server again.

I had the same issue and this worked for me.

---

