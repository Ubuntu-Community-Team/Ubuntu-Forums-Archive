---
title: "Mounting CIFS share with specific permissions"
date: 2012-04-02
forum: Server Platforms
---

### Post by spynappels on 2012-04-02
Hi All,

I have a question which probably has a simple answer, but for the life of me I cannot get it to work the way I want.

I'm trying to mount a Samba share on a server and am having some problems with permissions.

There is a Buffalo Terastation in our office which different users have access to from various Windows clients. There is no username or password set on the shared drive, we all just have individual folders in the share directory. Not secure, but it works for what we need.

I'm trying to mount my folder on an Ubuntu server to use it as a target for a rsync backup job, but I've hit a permissions problem. I mount the folder using ```
sudo mount /media/buffalo
``` and my /etc/fstab entry is ```
//<ip-address>/share/<folder_name> /media/buffalo cifs noauto,rw 0 0
``` The folder is mounted correctly and appears in df -h as expected, but my normal user cannot write to it. Root can, but I'd rather not run my backup as root if I do not need to.

Is there another option to mount the shared folder with 777 like permissions, or mount it as another user?

I tried to replicate this on my 11.10 desktop and have the same issue, however, if I navigate to the share through the file browser, I have full read/write access.

Any suggestions?

---

### Post by darkod on 2012-04-02
Since the share is open, I think all you need to add in /etc/fstab in the options field (just before noauto and don't leave space, all options are separated by comma), should be:
user=guest

Also, I am not sure you can mount a folder directly. It has to be a share. So, you can only do //ip/share, not //ip/share/folder1 or //ip/share/folder2, etc.

---

### Post by spynappels on 2012-04-02
> **darkod said:**
> Since the share is open, I think all you need to add in /etc/fstab in the options field (just before noauto and don't leave space, all options are separated by comma), should be:
user=guest

Also, I am not sure you can mount a folder directly. It has to be a share. So, you can only do //ip/share, not //ip/share/folder1 or //ip/share/folder2, etc.

Hi, thanks for the reply. I tried both of those and it has made no difference to the permissions.

---

### Post by Morbius1 on 2012-04-02
If you are the only user take possession of the mounted partition:
> //<ip-address>/share/<folder_name> /media/buffalo cifs noauto,rw,[COLOR=Blue]**uid=1000**[/COLOR] 0 0Or you can use dir_mode / file_mode to give everyone access:
> //<ip-address>/share/<folder_name> /media/buffalo cifs noauto,rw,[COLOR=Blue]**dir_mode=0777,file_mode=0666**[/COLOR] 0 0You'll have to admit the Nautilus way is a lot easier.

Note: I agree with the above comment about trying to mount a subfolder within a share. Just mount the share.

---

### Post by spynappels on 2012-04-02
Ok, setting the dir and file settings did the trick, along with mounting the share rather than a folder on the share.

> **Morbius1 said:**
> You'll have to admit the Nautilus way is a lot easier.


That is true, but the server does not have a GUI so....

---

