---
title: "mount windows network FS"
date: 2009-07-30
forum: Server Platforms
---

### Post by wvw on 2009-07-30
Hello

I run Ubuntu 8.04 Desktop and on a separate machine I run a dedicated ubuntu 8.04 server. From my desktop I can mount a network FS using the option under places. I see the network FS is mounted using gvfs in a folder in my home directory.

However I am trying to mount that exact same network FS using my server, but for the life of me it doesn't want to mount. I have tried the -t smb option with no luck. I have also read up on the gvfs from google but it seems this option is more meant for Desktop than Server? I had a look on my server at apt-get install fuse-gvfs-* with nothing to display. The closest I get is fuse-gvfs. I also had a look at apt-get install samba-gvfs but see many options under samba 'cept the one I am looking for.

Can someone please assist by telling what option I can use to mount a windows FS from the network to my server?

Thanks
wvw

---

### Post by littlegreiger on 2009-07-31
You should be able to do it, you'll need to install smbfs though. Then from there you can use the command```
sudo mount -t smbfs [windows share] [local mount point] -o user=[username],password=[password]
```just replace all the things in []'s.
Here's an example to help you. Let's say that I have a windows computer named "WINPC" with a share called "FILESHARE" that is accessible with user "USER1" and password "SECRET" and you want to mount it to /mnt/windows. You can mount this by running
```
sudo mount -t smbfs //WINPC/FILESHARE /mnt/windows -o user=USER1,password=SECRET
```
And like usual you have to have the mount dir created before you run that command.

---

### Post by wvw on 2009-08-02
Hello Littlegreiger

Thanks for all your help :) I never realised I didn't have smbfs installed until after I read your post. Really silly of me!

Now everything is working :)

Regards
wvw

---

