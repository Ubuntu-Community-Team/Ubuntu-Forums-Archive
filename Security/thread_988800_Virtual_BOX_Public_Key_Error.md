---
title: "Virtual BOX Public Key Error"
date: 2008-11-20
forum: Security
---

### Post by gangsta.mostwanted on 2008-11-20
Hi Friends, 

I recently moved one of my machine from Window Vista to Ubuntu. now I have to install Virtual Box as I have to run some software om Windows.. My virtual box is working guest host is working fine but I have seen few problems... Just wondering if you guys know how to fix these issues..

1: I am getting Virtual BOX public key error
"W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DCF9F87B6DFBCBAE"

2: My sound driver on the Ghose machine is not working.

In this case my Host is: Ubuntu Hardy
 and Guest is :          Window XP

XP is working fine with the only exception that its sound is not working. I have also checked the properties to make sure that sound is enabled. but still its not working...

Appreciate your help..
Cheers,
Mukesh

---

### Post by undadecor on 2008-11-20
For your first problem I would try running the following in the Terminal:
```
wget -q http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc -O- | sudo apt-key add -
```
and then
```
sudo apt-get update
```

---

### Post by gangsta.mostwanted on 2008-11-21
@ undadecor 

I really appreciate your help... thanks a lot... 

I tried your code but I got another error while running update..... here is the error..

W: GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) hardy Release: The following signatures were invalid: BADSIG DCF9F87B6DFBCBAE Sun Microsystems, Inc. (xVM VirtualBox archive signing key) <info@virtualbox.org>

any suggestions on this... 

also when I gun Virtual box it consumes 80% of CPU power... is that normal or something wrong with my system....

Thanks,
Mukesh

---

### Post by AdrianTM on 2009-04-21
Same problem here, I get the BADSIG error.

---

### Post by Jellyffs on 2009-11-11
Hi,

I had the same issue. What worked for me, considering that I already had the key was:

```
sudo rm -f /var/lib/apt/lists/partial/*
```

It's all smoothie fluffy now.

Alex.

---

### Post by cariboo on 2009-11-11
To get sound working, install the Guest additions, available under the Devices menu when you have a vm running.

---

### Post by burkeerr on 2009-11-26
I had this error and this worked for me as well
```
sudo rm -f /var/lib/apt/lists/partial/*
```

---

### Post by Doin on 2010-03-08
```
sudo rm -f /var/lib/apt/lists/partial/*
``` worked indeed, thanks a lot.

---

### Post by chopp3r on 2010-05-27
To add the key properly into aptitude, run the following in your terminal:
```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```This command was taken from the [VitualBox download site]("http://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions").

---

### Post by JEBB on 2010-09-20
Chopp,
Thanks.  I couldn't recognize that terminal cmd. at the linked site, but I put in what you gave us and the problem is gone.

---

