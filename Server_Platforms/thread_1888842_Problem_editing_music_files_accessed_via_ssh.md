---
title: "Problem editing music files accessed via ssh"
date: 2011-11-30
forum: Server Platforms
---

### Post by bigoten on 2011-11-30
Hi,

I have recently set up a SheevaPlug at home, to use as my own file server (Ubuntu server 9.04). I mounted an external drive on it.

I can connect to it using ssh in terminal from anywhere in the network. 

I also connect to it in Nautilus using sftp. It seems like I can read/write on the mounted external drive (at points it is slow, but OK). I tried copying, pasting, and editing text documents, it works fine.

However, I cannot for instance edit tags of music files in the mounted drive. I tried  using EasyTag. First of all EasyTag does not seem to show the mounted sftp location under the directory tree. I managed to access it via /home/USER/.gvfs. Secondly, it becomes veeeeery slow, practically non-responsive. And once I eventually open a tag and edit it, saving it leads to an error:
"Can't write tag in file 'xxxxx'!
(Operation not supported)"

I still tried other tag editing software in Ubuntu Software Center, but for all I always fail to find the sftp location under the directory tree given in the program.

My questions: 

1. How can I add an entry to the directory tree **globally**, so that it appear as a location option within any application under Ubuntu? I tried adding a bookmark for the sftp address in Nautilus, but this has no effect with applications as EasyTag.

2. Why can't I save the edited tags of music files in EasyTag? Am I asking for something impossible? Or can this be done using other program?

Can anyone suggest something?
Thank you,
bigoten

---

### Post by volkswagner on 2011-11-30
You can create a more permanent mount point.

Create a directory such as /home/user/sheeva.

```
mkdir /home/yourusername/sheeva
```

Install smbfs and smbclient

```
sudo apt-get install smbfs smbclient
```

You can get some info by running:

```
smbclient -L sheevahostnameORipaddress
```

Then mount your share:

```
sudo mount -t cifs //192.168.xxx.xxx/sharename /home/username/sheeva -o username=yourusername,password=xxxxxxxxx,domain=workgroup
```


Change the above information to reflect your environment.

---

### Post by bigoten on 2011-11-30
Hi volkswagner,
thanks for replying.

I think I did not fully understand your suggestion. I installed smbfs and smbclient on my client PC (right?). I should add that I am not on my home network.

I tried to run the smbclient command, but it always gave an error. I tried something like 
smbclient -L ipaddress
or
smbclient -L ipaddress/userinserver
but no good.

Mounting did not work either. I am also not sure which username and password I should use (I thought the ones from my client account).

Can you be a little more precise on this?

Thanks in advance!

bigoten

---

### Post by bigoten on 2011-12-16
Eventually I solved my problem using sshfs. This page was useful for me:
[http://stevenmcmurry.com/node/75](http://stevenmcmurry.com/node/75)

---

