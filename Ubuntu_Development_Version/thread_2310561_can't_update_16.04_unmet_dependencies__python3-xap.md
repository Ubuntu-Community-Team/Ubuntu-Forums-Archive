---
title: "can't update 16.04 unmet dependencies:  python3-xapian1.3 : Depends: libxapian-1.3-5"
date: 2016-01-20
forum: Ubuntu Development Version
---

### Post by pixelro on 2016-01-20
```
sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 python3-xapian1.3 : Depends: libxapian-1.3-5 but it is not installed
E: Unmet dependencies. Try using -f.

sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libxapian-1.3-5
Suggested packages:
  xapian-tools
The following NEW packages will be installed:
  libxapian-1.3-5
0 upgraded, 1 newly installed, 0 to remove and 35 not upgraded.
1 not fully installed or removed.
Need to get 0 B/619 kB of archives.
After this operation, 2.529 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 290431 files and directories currently installed.)
Preparing to unpack .../libxapian-1.3-5_1.3.4-0ubuntu3_amd64.deb ...
Unpacking libxapian-1.3-5 (1.3.4-0ubuntu3) ...
dpkg: error processing archive /var/cache/apt/archives/libxapian-1.3-5_1.3.4-0ubuntu3_amd64.deb (--unpack):
 trying to overwrite '/usr/share/xapian-core/stopwords/dutch.list', which is also in package libxapian-1.3-4 1.3.3-0ubuntu2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin (2.21-0ubuntu5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libxapian-1.3-5_1.3.4-0ubuntu3_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

:|

---

### Post by slickymaster on 2016-01-20
[https://bugs.launchpad.net/ubuntu/+source/xapian1.3-core/+bug/1536093](https://bugs.launchpad.net/ubuntu/+source/xapian1.3-core/+bug/1536093)

---

### Post by pixelro on 2016-01-20
> **slickymaster said:**
> [https://bugs.launchpad.net/ubuntu/+source/xapian1.3-core/+bug/1536093](https://bugs.launchpad.net/ubuntu/+source/xapian1.3-core/+bug/1536093)

thanks! ):P

---

### Post by pixelro on 2016-01-20
[FONT=arial]ok, so 

```
[COLOR=#333333]dpkg -P libxapian-1.3-4 1.3.3-0ubuntu2[/COLOR]
[COLOR=#333333]apt-get -f install
```

fixed it, solved. thanks asavah[/COLOR][/FONT]

---

### Post by tokyobadger on 2016-01-20
Thanks to pixelro for pasting the fix here and to slickymaster for the bugs.launchpad link. Saw pixelro's paste before I'd refreshed bugs.launchpad so now the reference to asavah makes sense

Fixed it for me too - maybe pixelro can mark the thread as "solved"

---

### Post by jackkerouac on 2016-01-20
> **pixelro said:**
> [FONT=arial]ok, so 

```
[COLOR=#333333]dpkg -P libxapian-1.3-4 1.3.3-0ubuntu2[/COLOR]
[COLOR=#333333]apt-get -f install
```

fixed it, solved. thanks asavah[/COLOR][/FONT]

Thanks! Awesome.

---

### Post by PaulW2U on 2016-01-20
> **slickymaster said:**
> [https://bugs.launchpad.net/ubuntu/+source/xapian1.3-core/+bug/1536093](https://bugs.launchpad.net/ubuntu/+source/xapian1.3-core/+bug/1536093)
Always comforting to know that others are seeing the same bugs/problems :)

---

### Post by Cavsfan on 2016-01-20
> **pixelro said:**
> [FONT=arial]ok, so 

```
[COLOR=#333333]dpkg -P libxapian-1.3-4 1.3.3-0ubuntu2[/COLOR]
[COLOR=#333333]apt-get -f install[/COLOR]
```[COLOR=#333333]

fixed it, solved. thanks asavah[/COLOR][/FONT]

This did not fix it for me. I had to manually install libxapian-1.3-5 and that fixed it.

```
cavsfan@cavsfan-le-beast:~$ [COLOR=#ff0000]sudo dpkg -P libxapian-1.3-4 1.3.3-0ubuntu2[/COLOR]
(Reading database ... 250782 files and directories currently installed.)
Removing libxapian-1.3-4 (1.3.3-0ubuntu2) ...
Purging configuration files for libxapian-1.3-4 (1.3.3-0ubuntu2) ...
dpkg: warning: ignoring request to remove 1.3.3-0ubuntu2 which isn't installed
Processing triggers for libc-bin (2.21-0ubuntu5) ...
cavsfan@cavsfan-le-beast:~$ ud2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
[COLOR=#ff0000]The following packages have unmet dependencies:
 python3-xapian1.3 : Depends: libxapian-1.3-5 but it is not installed[/COLOR]
E: Unmet dependencies. Try using -f.
cavsfan@cavsfan-le-beast:~$ [COLOR=#ff0000]sudo apt-get install libxapian-1.3-5[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  xapian-tools
The following NEW packages will be installed:
  libxapian-1.3-5
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by tokyobadger on 2016-01-21
Hmm - updated 2x today and libxapian-1.3-5 was included both times, clearly some lingering issues, but at least no errors

---

