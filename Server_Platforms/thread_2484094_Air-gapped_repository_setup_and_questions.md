---
title: "Air-gapped repository setup and questions"
date: 2023-02-17
forum: Server Platforms
---

### Post by nahebm on 2023-02-17
I've got a couple of Ubuntu servers (20.04) that I have a base O/S on, and now I need to update them.  They're Nvidia DGXs.  
A former co-worker set up a repository on a remote machine (CentOS 7).  The entries in /etc/apt/sources.list on these servers are:

deb [allow-insecure=yes] [http://ourcompany.com/apt-mirror/archive.ubuntu.com/ubuntu/](http://ourcompany.com/apt-mirror/archive.ubuntu.com/ubuntu/) focal main restricted universe multiverse
deb [allow-insecure=yes] [http://ourcompany.com/apt-mirror/archive.ubuntu.com/ubuntu/](http://ourcompany.com/apt-mirror/archive.ubuntu.com/ubuntu/) focal-updates main restricted universe multiverse
deb [allow-insecure=yes] [http://ourcompany.com/apt-mirror/archive.ubuntu.com/ubuntu/](http://ourcompany.com/apt-mirror/archive.ubuntu.com/ubuntu/) focal-security main restricted universe multiverse
deb [allow-insecure=yes] [http://ourcompany.com/files/Nvidia/ubuntu/](http://ourcompany.com/files/Nvidia/ubuntu/) /

I looked at the directories on this repository server, and they exist, and they're populated with files as expected.  I'm unable to use these to update my systems.
I tried doing 'apt-get clean' then 'apt-get update'.  I do see a few Err: entries in that 'apt-get update' output, but it's mostly Ign:, Get: and one Hit:
When it gets to the Nvidia repository, it outputs "The following signatures couldn't be verified because the public key is not available; the repository 'http://ourcompany.com/files/Nvidia/ubuntu/ Release' is not signed.
After that, I try to install anything (i. e. apt-get install ntpd), and the output from that says nothing to install.

Several questions:
1) The sources.list with allow-insecure=yes - is that the right syntax?
2) Is there some flag I can use to work around that 'public key is not available' message (i. e. --nogpg in RHEL/CentOS)?
3) I've used other unixes frequently, but I'm relatively new to Ubuntu.  I've tried 'apt-get install <package>' and 'apt install <package>' but these don't work.  When I do an 'apt list | grep -v installed', I do see a bunch of the Nvidia packages/.debs that are in that repository.  Am I just using the wrong commands?

Any guidance someone could provide would be welcome.  I'll do my best to self-correct and note my corrective actions in this ticket for posterity.
Thanks,
Mike

---

### Post by slickymaster on 2023-02-17
Thread moved to **Server Platforms** for a better fit

---

