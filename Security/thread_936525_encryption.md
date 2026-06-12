---
title: "encryption"
date: 2008-10-02
forum: Security
---

### Post by Anditsu on 2008-10-02
Hello Ubuntu user, I just got a new labtop and wanted to know the best way to encryption Ubuntu. Any nice how too's would be great too

Anditsu

---

### Post by nubdora on 2008-10-02
Encrypting the system on installation:

[http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04](http://www.howtoforge.com/encrypting-the-system-manually-upon-installation-ubuntu8.04)

---

### Post by arkticcool on 2008-10-02
If you've already installed Ubuntu, you can use Truecrypt to create an encrypted disk. This won't encrypt your entire disk, but will create a sepeart disk where you can keep all the files you need to encrypt. Go to Applicatoins > Add/Remove Programs and search for Easy Crypt. This is the GUI for truecrypt, which will need to be installed as well. It will tell you how.

---

### Post by amac777 on 2008-10-03
I recommend EncFS, which lets you encrypt the files within certain folders.

HOWTO here:
[http://ubuntuforums.org/showthread.php?t=148600&highlight=encfs](http://ubuntuforums.org/showthread.php?t=148600&highlight=encfs)

also, there are some gui front ends available as well (although I don't use them because it's already really easy from the command line).

---

### Post by hyper_ch on 2008-10-03
if you want full disk encryption either use the automatic full disk encryption option on the alternate cd or follow my howto in the link posted by nubdora.

Full disk encryption is the most convenient one, as everything gets encrypted. If you don't use full disk encryption you will need to know yourself where and what to encrypt. However full disk encryption also requires you to have a backup. E.g. the initalizing sectors of your harddisk may fail and you can't uncrypt your data anymore. This can happen anytime - so you really must have an (encrypted) backup.

Actually you should always have backups anyway ;)

---

### Post by whitefort on 2008-11-01
/* contents edited out of existence by poster, due to excessive stupidity content! */

---

### Post by ashmew2 on 2008-11-01
> **whitefort said:**
> 
Big_Bouncy_Bertha.jpg

:lolflag:

+1 for TrueCrypt

---

### Post by amac777 on 2008-11-01
> **whitefort said:**
> Secondly, while the files inside that folder are encrypted, their NAMES and even the file types are fully visible.  So while the actual contents of the files can't be accessed, if you have a folder of .jpgs with names like Big_Bouncy_Bertha.jpg, your secrets won't be so secret!

Under EncFS, meta data such as datestamp of last modification and approximate filesize is visible, but what you said about the filenames under EncFS being fully visible is *not* true. Here is what the files in my encrypted directory look like:

```
computer:~/.crypt$ ls
5U5NxX,LCWQyFslMlL5gfx1ucprNIrKVG4D
czKC7CxVnNesJUMBW,Ir0PgfKSg2saCiEzjiS33gQZPR0,
I18sTzlDQSQKG6vai83145g1
ih3,2eLs6CaTfis4114yUcr,4zgz-Ur6EkD
MrUgBlgBiJdLbWzxNGXV9FsV
MxsynB-Ua,zJ6RrNrP5gm1gJ
o2C6sb0ngnXlkhp7GpVlAGaq
rLB9dA5MBpzupdmgxpzs0It9
XwHUDdcp,MW0eb0dCG5VFY3UJ64VN,puK0-
yo2YPjkLlF0AU0

```

So filenames (and extensions) are not visible under EncFS.

---

### Post by kevdog on 2008-11-01
No one encryption method is the "perfect solution" so to say that True Crypt is the ideal solution is just ludicrous.  Please acknowledge the pros and cons of your statements.  I guess you weren't around during the transition between True Crypt3 and 4.  Hmm seems like anything encrypted under v3 is not compatible with version 4.  Could that happen again in the future? Likely.

---

### Post by whitefort on 2008-11-01
> **amac777 said:**
> what you said about the filenames under EncFS being fully visible is *not* true.

I set up the encrypted folder following the Ubuntu page instructions.

When I unmount Private, if I try to look inside it, I just see the message:

"THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA - Run mount encfs_private to mount it again"

Fair enough.

However, when I then look in .private I see ALL my files and folders, with names like pgp_keys, tax-return_0708, and all my jpegs, even if none of them are called big_bouncy_bessie.  I can't open them, but they have *exactly* the same names as the original files.

And, in fact, if you look at [[COLOR="Blue"]the Ubuntu page[/COLOR]]("https://help.ubuntu.com/community/EncryptedPrivateDirectory"), you'll see this is listed as a bug at the bottom of the page.  Follow [[COLOR="Blue"]that link[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/264977"), and you'll see that this seems to be a frequently criticised feature.

So, if your method works, maybe you should post a tutorial on how you set it up - your way is clearly better than the 'official' Ubuntu instructions. (I'm being serious here, BTW, not sarcastic)

And to KevDog, perhaps I should explain that the 'IMO' at the end of my post stands for 'in my opinion'?

---

### Post by amac777 on 2008-11-01
> **whitefort said:**
> So, if your method works, maybe you should post a tutorial on how you set it up - your way is clearly better than the 'official' Ubuntu instructions. (I'm being serious here, BTW, not sarcastic)

My "method" is using EncFS. :popcorn:

I'm not an expert on Ibex, but according to the bug link and information that I've seen about it, 8.10's encrypted directory uses another encryption tool called ecryptfs. (Not encfs.) Filename encrypting is still a planned feature for ecryptfs.

---

### Post by whitefort on 2008-11-01
> **amac777 said:**
> 8.10's encrypted directory uses another encryption tool called ecryptfs.

Oops...  Ok.  My bad.

I'm going to edit out my original post (on grounds of stupidity), and go bang my head on the desk for a while!

(I still prefer truecrypt, though)

---

