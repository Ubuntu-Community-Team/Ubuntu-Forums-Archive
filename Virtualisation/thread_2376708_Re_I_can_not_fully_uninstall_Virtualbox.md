---
title: "Re: I can not fully uninstall Virtualbox???"
date: 2017-11-05
forum: Virtualisation
---

### Post by tulsamike3434 on 2017-11-05
[CENTER]This Is what happens...[/CENTER]
```
dpkg -l | grep virtualbox


```


```


pi  virtualbox-ext-pack                           5.0.40-0ubuntu1.16.04.1                      all          extra capabilities for VirtualBox, downloader.
rc  virtualbox-qt                                 5.0.40-dfsg-0ubuntu1.16.04.1                 amd64        x86 virtualization solution - Qt based user interface



```

.Can someone please help as soon as it updated id broke EG.....

[http://oi63.tinypic.com/2573xj6.jpg](http://oi63.tinypic.com/2573xj6.jpg)
[CENTER]Thank you for your time 
Have a Blessed day...
[/CENTER]

P.S. i am running 16.04 LTS

---

### Post by ajgreeny on 2017-11-05
What do you see if you try ```
sudo apt-get purge virtualbox-qt virtualbox-ext-pack
```
Removing virtualbox alone may not remove those two packages; you will either have to remove them separately, or perhaps try ```
sudo apt-get autoremove
``` which should remove them as they are both dependent on the actual virtualbox package which you may have already removed.

EDIT:
If I remember correctly the **rc virtualbox-qt** in your output means it is removed but its configuration remains, and **pi virtualbox-ext-pack** means it is part installed.
This still means you can run the purge command above and it should do the trick.

---

### Post by tulsamike3434 on 2017-11-05
> **ajgreeny said:**
> What do you see if you try ```
sudo apt-get purge virtualbox-qt virtualbox-ext-pack
```
Removing virtualbox alone may not remove those two packages; you will either have to remove them separately, or perhaps try ```
sudo apt-get autoremove
``` which should remove them as they are both dependent on the actual virtualbox package which you may have already removed.

EDIT:
If I remember correctly the rc virtualbox-qt in your output means it is removed but its configuration remains, and pi virtualbox-ext-pack means it is part installed.
This still means you can run the purge command above and it should do the trick.

I think it worked! here was the output form your command that you showed me witch I am very thankful for!!!
```

sudo apt-get purge virtualbox-qt virtualbox-ext-pack

```


```



Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kbuild libgsoap8 libvncserver1 linux-headers-4.4.0-93
  linux-headers-4.4.0-93-generic linux-headers-4.4.0-96
  linux-headers-4.4.0-96-generic linux-image-4.4.0-93-generic
  linux-image-4.4.0-96-generic linux-image-extra-4.4.0-93-generic
  linux-image-extra-4.4.0-96-generic module-assistant
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  virtualbox-ext-pack* virtualbox-qt*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 129 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 423732 files and directories currently installed.)
Removing virtualbox-ext-pack (5.0.40-0ubuntu1.16.04.1) ...
/var/lib/dpkg/info/virtualbox-ext-pack.prerm: 4: /var/lib/dpkg/info/virtualbox-ext-pack.prerm: vboxmanage: not found
dpkg: error processing package virtualbox-ext-pack (--purge):
 subprocess installed pre-removal script returned error exit status 127
Removing virtualbox-qt (5.0.40-dfsg-0ubuntu1.16.04.1) ...
Purging configuration files for virtualbox-qt (5.0.40-dfsg-0ubuntu1.16.04.1) ...
dpkg: warning: while removing virtualbox-qt, directory '/usr/lib/virtualbox' not empty so not removed
Processing triggers for menu (2.1.47ubuntu1) ...
Errors were encountered while processing:
 virtualbox-ext-pack
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

Have a Blessed day ajgreeny!!! 

```
dpkg -l | grep virtualbox
```


```
pi  virtualbox-ext-pack                           5.0.40-0ubuntu1.16.04.1                      all          extra capabilities for VirtualBox, downloader.
```

Poop still got 1 pesky lil booger to remove. Quick question when I use...

 ```
sudo apt-get autoremove
```

How will it know if I am talking about VBOX and not any other packages?

P.S. Thank you for all your help! It is greatly appreciated!


If I use ...


```

sudo apt-get autoremove
```

```


  
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 virtualbox-ext-pack : Depends: virtualbox (>= 5.0.40-dfsg-0~) or
                                virtualbox-5.0 but it is not installed
                       Depends: virtualbox (< 5.0.40-dfsg-z) or
                                virtualbox-5.0 but it is not installed
E: Unmet dependencies. Try using -f.



```


And if I use ...

```
sudo apt-get -f autoremove
```


```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  virtualbox virtualbox-dkms virtualbox-qt
Suggested packages:
  vde2 virtualbox-guest-additions-iso
The following packages will be REMOVED:
  kbuild linux-headers-4.4.0-93 linux-headers-4.4.0-93-generic
  linux-headers-4.4.0-96 linux-headers-4.4.0-96-generic
  linux-image-4.4.0-93-generic linux-image-4.4.0-96-generic
  linux-image-extra-4.4.0-93-generic linux-image-extra-4.4.0-96-generic
  module-assistant
The following NEW packages will be installed:
  virtualbox virtualbox-dkms virtualbox-qt
0 upgraded, 3 newly installed, 10 to remove and 0 not upgraded.
Need to get 22.1 MB of archives.
After this operation, 503 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.
```

That looks like it's going to remove more than I need?

---

### Post by #&amp;thj^% on 2017-11-05
What dose this show from the terminal:
```
uname -r
```

---

