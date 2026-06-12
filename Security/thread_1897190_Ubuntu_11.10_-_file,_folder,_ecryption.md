---
title: "Ubuntu 11.10 - file, folder, ecryption?"
date: 2011-12-18
forum: Security
---

### Post by candtalan on 2011-12-18
I have been using Ubuntu 10.04.3 and GNU Privacy Assistant - pretty much as an encryption novice. I am moving to Ubuntu 11.10 however, I seem to find that gpa and in fact any (?) encryption does not appear to be available in 11.10 (repos whatever?), which I find a bit odd.

The obvious searches yield results which at first seem useful but do not seem to be useful for 11.10 (even when 11.10 is mentioned)

I guess any sort of good encryption would be ok for me, not necessarily gpa. (The objective is to put the encrypted files up onto a non encrypted web store).

I would like to move to Ubuntu 11.10 though.

I would be grateful for help here.
tia

---

### Post by DanR01 on 2011-12-19
Hi

GPA is not in the repos. I'm currently trying to compile it from source and running into a lot of errors. 

If I manage to get it working I'll post a guide here. 

Dan

---

### Post by candtalan on 2011-12-19
> **DanR01 said:**
> Hi
GPA is not in the repos. I'm currently trying to compile it from source and running into a lot of errors. 
If I manage to get it working I'll post a guide here. 
Dan

Thanks Dan!

---

### Post by DanR01 on 2011-12-20
I managed to get GPA version 0.7.5 working on 11.10 but not the most recent version which gave me multiple errors. 

First I had to build the dependencies:

libgpg-error-1.9
libassaum-2.0.2
gpgme-1.3.1

gpgme-1.3.1 had to be compiled with the following flags: --disable-g13-test

Then download the gpa tar, extract, configure with --enable-maintainer-mode 

make && sudo make install

If you get an error about large file support try configuring gpgme with the additional flag --disable-largefile  

All packages available via the GnuPGP website. Good luck!

Dan

---

### Post by kiwire on 2012-01-01
i got gpa 0.9.0-1 (gnupg 2.0.17 working)
I downloaded the deb file and installed it.There was a dependcy error.So i went to the software center and it downloaded gpgsm 2.0.17.Then i tired to run it and it gave me a gpgme error.So i went to synaptic package manager and dled libgpgme++2 (4.7.3) ,python-pyme 0.8.1-2,python gpgme(0.1+bzr2090820-3)

---

### Post by ottosykora on 2012-01-04
is there the seahorse available for 11.10?

I have no idea since still on 11.04 so far.

But was using seahorse plugin for file encryption until now.

---

### Post by ottosykora on 2012-01-05
is there some ppa where seahorse for 11.10 could be obtained?

---

### Post by Ms. Daisy on 2012-01-05
Looks like seahorse for 11.10 got deleted from the repositories.
[http://www.ubuntuupdates.org/packages/show/360783](http://www.ubuntuupdates.org/packages/show/360783)

Another thread may give you more information:
[http://ubuntuforums.org/showthread.php?t=1861219](http://ubuntuforums.org/showthread.php?t=1861219)

---

### Post by ottosykora on 2012-01-05
OK, many thanks, seems that will still wait some time before I upgrade to oneiric...

strange, that devs try to take care of so many unimportant things , but leave essential thigs simply 'for furture'.

---

### Post by 0011235813 on 2012-01-05
Have you tried cryptkeeper? Works fine for me... The Unity bug must have been fixed.

---

### Post by ottosykora on 2012-01-06
> **0011235813 said:**
> Have you tried cryptkeeper? Works fine for me... The Unity bug must have been fixed.

but this is for the encr fs, not something for the gpg if I undertand it right?

Are there no other usable front ends for gpg for ubuntu /deb around?

---

### Post by 0011235813 on 2012-01-07
> **ottosykora said:**
> but this is for the encr fs, not something for the gpg if I undertand it right?
 
Are there no other usable front ends for gpg for ubuntu /deb around?
 
I'm not sure if I understand you correctly, you want to make an encrypted/password protected folder right? Tell me if I'm misunderstanding this here...

---

