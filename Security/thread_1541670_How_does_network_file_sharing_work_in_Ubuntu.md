---
title: "How does network file sharing work in Ubuntu?"
date: 2010-07-29
forum: Security
---

### Post by espressobeanie on 2010-07-29
How does network file sharing work in Ubuntu? Is it only enabled for the Public folder? Or does it vary by folder permission settings, specifically in that folder's 'Properties' and allow others access the folders? 

I'm asking because someone at my work may have had a complete breach of their personal files in the /home/ directory from their folder permission settings. I want to know if regardless of everyone having access permission to the folder, if they need to drag it to the Public folder for it to be network shared.

---

### Post by cariboo on 2010-07-29
Linux uses samba to share files, as Windows doesn't play well with networking with other operating systems.

There is a good howto [here]("http://ubuntuforums.org/showthread.php?t=202605").

IF you are sharing with other Linux based systems, I would suggest using NFS, There is a howto [here]("https://help.ubuntu.com/community/SettingUpNFSHowTo").

I use both as I have have a mixed network of both Windows and Linux.

---

### Post by bodhi.zazen on 2010-07-29
> **espressobeanie said:**
> How does network file sharing work in Ubuntu? Is it only enabled for the Public folder? Or does it vary by folder permission settings, specifically in that folder's 'Properties' and allow others access the folders? 

I'm asking because someone at my work may have had a complete breach of their personal files in the /home/ directory from their folder permission settings. I want to know if regardless of everyone having access permission to the folder, if they need to drag it to the Public folder for it to be network shared.

The short answer is no, by default nothing is available as a share.

Longer answer - By default there are no services on a default installation of Ubuntu. You would need to install a server such as samba, NFS, FTP, ssh, etc for any files to be available on the network.

Your users should know if he or she enabled some forum of network sharing. If you are not sure, look for running services such as samba or nfs or scan the box.

Any of these commands will work on the box in question

```
netstat -an | grep LISTEN | grep -v ^unix 
netstat -ntulp
sudo lsof -i -n -P
```

---

### Post by espressobeanie on 2010-07-29
Thanks for the clarification bodhi. I wasn't sure if it was something that simple to share an entire folder structure through basic file permissions and enable network sharing or whether you need to set it as a share through a package like samba.

---

