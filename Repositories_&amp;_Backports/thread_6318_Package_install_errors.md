---
title: "Package install errors"
date: 2004-11-27
forum: Repositories &amp; Backports
---

### Post by xethm55 on 2004-11-27
I have tried to install varius packages using both synaptic and apt-get.  however when they are installing i usually get an error, such as the following (from synaptic):

dpkg error (1)  .....
samba

or something like that.  i do not know how to paste and copy text from the synaptic window.  I someone would please tell me what i am doing wrong i would appreciate it.

---

### Post by coyote721 on 2004-12-16
Hi, 
  I am getting the same error. Samba:
  Depends: samba-common but 3.0.7-1ubuntu6.2 is to be installed
  The Samba install is looking for an earlier version of samba-common and will not install. When you try to remove samba-common synaptic wants to remove ubuntu-desktop and smb-client. This didn't sound like a good idea. Does anyone know of a  work around? Thanks!

---

### Post by jak on 2004-12-19
I'm having this problem, im unsure if its the same but it seems related.

```
(Reading database ... 83218 files and directories currently installed.)
Removing samba ...
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--remove):
 subprocess pre-removal script returned error exit status 102
Errors were encountered while processing:
 samba

```

Can anyone help?

---

### Post by calamari on 2004-12-22
Hi,

I'm receiving a very similar error.  The strange thing is that samba used to be installed a few weeks ago (I successfully transferred some files from my laptop) and when I tried to use it today, it wasn't working.. it wasn't even installed!  I went to Synaptic and when I tried to install samba (3.0.7-1ubuntu6) I got this error:

```
Setting up samba (3.0.7-1ubuntu6) ...
update-rc.d: warning: /etc/rc2.d/S91samba is not a link to ../init.d/samba
update-rc.d: warning: /etc/rc3.d/S91samba is not a link to ../init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/S91samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102

```

EDIT:  I just noticed that I didn't originally install samba, it was smbclient.  Now I can't remove samba (same error as jak is getting).. 

Jeff

---

### Post by richbayliss on 2005-01-14
I fixed this.

I removed the rc2.d/K09samba file, and made a new softlink to init.d/samba

then 'sudo apt-get -f install'

worked for me  8)

---

### Post by MikeBee on 2005-01-22
I had this problem too. Once I removed '/etc/rc2.d/samba' and '/etc/rc3.d/samba' links are relinked them both to '../init.d/samba' by 'sudo ln -s ../init.d/samba /etc/rc2.d/samba' and 'sudo ln -s ../init.d/samba /etc/rc3.d/samba' then ran 'sudo apt-get -f install' it worked fine.

---

### Post by thebrade on 2006-06-30
just wanted to say thanks! I had this problem too and mikebee's solution worked...

---

### Post by cneil on 2006-07-13
Thanks! This helped me too.  However, my files were called K09samba.

---

### Post by jamaas on 2006-07-13
Worked for me too, thanks

Jim

> **cneil said:**
> Thanks! This helped me too.  However, my files were called K09samba.

---

### Post by zombified on 2006-07-14
This worked for me, with one minor exception:

The name of each of the files in both /etc/rc2.d and /etc/rc3.d were not "samba" they were "S91samba".

---

### Post by ashyanbhog on 2006-08-21
worked here too :) 

files were K09samba.

---

### Post by wwwluckyro on 2006-11-17
It does not work for me. What to do?

> lucky@lucky-desktop:~$ sudo ln -s ../init.d/samba /etc/rc2.d/K09samba
ln: creating symbolic link `/etc/rc2.d/K09samba' to `../init.d/samba': File exists
lucky@lucky-desktop:~$ sudo ln -s ../init.d/samba /etc/rc3.d/K09samba
ln: creating symbolic link `/etc/rc3.d/K09samba' to `../init.d/samba': File exists
lucky@lucky-desktop:~$ 


Thanks

---

### Post by SyL on 2007-05-01
> **wwwluckyro said:**
> It does not work for me. What to do?



Thanks


First delete the current /etc/rcX.d/K09samba links

---

### Post by pylot5120 on 2007-05-15
> **coyote721 said:**
> Hi, 
  I am getting the same error. Samba:
  Depends: samba-common but 3.0.7-1ubuntu6.2 is to be installed
  The Samba install is looking for an earlier version of samba-common and will not install. When you try to remove samba-common synaptic wants to remove ubuntu-desktop and smb-client. This didn't sound like a good idea. Does anyone know of a  work around? Thanks!


[bread build baking Skin care Cash Advance](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

