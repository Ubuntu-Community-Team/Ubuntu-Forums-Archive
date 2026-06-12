---
title: "md5 sum mismatches"
date: 2005-06-14
forum: Repositories &amp; Backports
---

### Post by ubuntu_demon on 2005-06-14
just to inform you guys about md5 sum mismatches on these packages from us.archive.ubuntu.com :

icewm-common
libcairo (needed for the firefox backport)

Let's post all those mismatches in this thread.

I think we just have to wait a bit.

---

### Post by pietro_spina on 2005-06-14
mismatch for

automake1.4
indent

for me...

and feel free to lock/purge or otherwise "moderate" my mismatch thread.... :-)
[http://www.ubuntuforums.org/showthread.php?t=41216](http://www.ubuntuforums.org/showthread.php?t=41216)


waiting patiently... ... ... :-\"

---

### Post by gmc on 2005-06-14
You can add iptraf and nmap to that list too.

G.

---

### Post by michellembrodeur on 2005-06-14
its been about 5 days now, when will the servers be fixed so we don't get the md5sum error.

not even any official word fromt he devs of this distro.

---

### Post by ubuntu_demon on 2005-06-14
here's a solution :

[http://www.ubuntuforums.org/showpost.php?p=210104&postcount=5](http://www.ubuntuforums.org/showpost.php?p=210104&postcount=5)

[quote=Xian]
The 'us.archive.ubuntu.com' mirrors are acting flaky this weekend. Replace each instance of them in your /etc/apt/sources.list with the 'archive.ubuntu.com' prefix instead. Then do an 'apt-get update' session and you should be back on track.
[/quote]

I think those who are from the us should put the "us part" back in after this is fixed

---

### Post by michellembrodeur on 2005-06-14
[QUOTE=demon666_nl]here's a solution :

[http://www.ubuntuforums.org/showpost.php?p=210104&postcount=5](http://www.ubuntuforums.org/showpost.php?p=210104&postcount=5)



I think those who are from the us should put the "us part" back in after this is fixed[/QUOTE]

didn't work for roommate or myself.

---

### Post by ubuntu_demon on 2005-06-14
[QUOTE=michellembrodeur]didn't work for roommate or myself.[/QUOTE]
 which packages ?

---

### Post by ksmith on 2005-06-14
EDIT: Changing mirrors fixed this, thanks.


------------------------------------------------------------------------------------------------------

Another mismatch:

```
kcs@xorb:~$ sudo apt-get install xmms

...

The following NEW packages will be installed:
  libglib1.2 libgtk1.2 xmms
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.

...

Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-9_amd64.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
kcs@xorb:~$

```

---

### Post by bored2k on 2005-06-14
[QUOTE=ksmith]Another mismatch:

```
kcs@xorb:~$ sudo apt-get install xmms

...

The following NEW packages will be installed:
  libglib1.2 libgtk1.2 xmms
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.

...

Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2_1.2.10-9_amd64.deb  MD5Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
kcs@xorb:~$

```[/QUOTE]
 You are using US.archive.ubuntu. Edit your sources.list and remove the us from the http !

---

### Post by RadixLecti on 2005-07-08
This got me thinking.. what archives are there? 
Which would be the closest to use for a person living in Sweden?

---

### Post by Fexx on 2005-07-08
doesnt work. I have removed the .us part but still tries to get from the .us. even tho its removed in the source apt file and also did the sudo apt-get update.

---

### Post by Fexx on 2005-07-08
Trying to update firefox.. have to use the smart feature for it. since it does a remove of mozillia-firefox and installs firefox.

[http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)  seems like a needed file.

Any offical news on the this md5 mismatch problems?

---

### Post by psychicdragon on 2005-07-08
I got a md5sum mismatch for
psutils 1.17-17

---

### Post by jfdill_2 on 2005-07-08
I just got one for dpkg-dev from US mirror, entered it into bugzilla for dpkg-dev not sure if that was the right place.

Taking the "us" out of the entry for main in sources.list worked for me:

diff -r1.2 sources.list
3c3
< deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
---
> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary main restricted

Don't forget to do:

apt-get update

---

### Post by bjtuna on 2005-07-09
I've got an md5sum mismatch for libvcdinfo and links

---

