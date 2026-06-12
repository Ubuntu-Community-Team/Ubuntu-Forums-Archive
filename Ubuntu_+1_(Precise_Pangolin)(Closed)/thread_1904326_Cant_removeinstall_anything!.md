---
title: "Cant remove/install anything!"
date: 2012-01-04
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by zehsebas on 2012-01-04
Helleu Ubuntu&#347;

I cant install and remove any apps from the Ubuntu software center. 
The error i get is; An unhandlable error occured; 
ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true

Details;
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


Secondly;
I cant accept the TFF licence agreement. I simply cant press OK.

I heard about installing mts-corefronts. But that program tells me its already installed.
Please help me guys.


Cheers.

---

### Post by effenberg0x0 on 2012-01-04
> **zehsebas said:**
> Helleu Ubuntu&#347;

I cant install and remove any apps from the Ubuntu software center. 
The error i get is; An unhandlable error occured; 
ttf-mscorefonts-installer msttcorefonts/accepted-mscorefonts-eula select true

Details;
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


Secondly;
I cant accept the TFF licence agreement. I simply cant press OK.

I heard about installing mts-corefronts. But that program tells me its already installed.
Please help me guys.


Cheers.

1.Are you running Ubuntu 12.04 Precise Pangolin Alpha? 
```

$ lsb_release -a

```2.Are you running the latest packages?
```

$ sudo apt-get update && sudo apt-get upgrade

```3.Have you tried manually installing the package?```

$ sudo apt-get install ttf-mscorefonts-installer

```4.And, in case it fails, have you tried removing and installing again (a) or reinstalling (b) the package?  
a)```

$ sudo apt-get remove --purge ttf-mscorefonts-installer 
$ sudo apt-get install ttf-mscorefonts-installer

```...or...
b)```

$ sudo apt-get install --reinstall ttf-mscorefonts-installer

```5.If still it fails, is anything else installable? Ex., a calculator:
```

$ sudo apt-get install galculator

```

---

### Post by spacecheck on 2012-01-04
> I cant accept the TFF licence agreement. I simply cant press OK.A sharp eye from a recent post reminded to use the tab to get to and activate the "Ok" button for java license.  Perhaps you can use tab to highlight your button and then hit "enter"?

Good luck!

---

### Post by cariboo on 2012-01-04
Can you add/remove applications using the command line or synaptic?

---

### Post by zehsebas on 2012-01-04
Removing the program manualy;

sebastiaan@Sebastiaan-Ubuntu:~$ sudo apt-get remove --purge ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-mscorefonts-installer*
0 upgraded, 0 newly installed, 1 to remove and 71 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing ttf-mscorefonts-installer (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
sebastiaan@Sebastiaan-Ubuntu:~$ 


----
I used the Galculator code, and it worked.
Also Tabbing worked! i could finally accept terms.
I think the Galculator also installed the fonts.

Im testing right now.

---

### Post by zehsebas on 2012-01-04
Okay!
After installing the Galculater, it forced to install the FFT-Font.
and now everything works! 

Thanks alot!

---

### Post by MacUntu on 2012-01-04
I'd download the deb from Launchpad, do a `dpkg -i --force-all foo.deb`, purge it, and then reinstall it from the repos.

Edit: or not. :D Please mark your thread as solved using the "Thread Tools" link.

---

### Post by josephmills on 2012-01-04
there are a couple of ways to find things on your computer one of the most powerful was is the command find. Here is a short description 
1)```
sudo find <name of directory or / for root> 
```
2)we then declare what we are looking for in this case a name ```
sudo / -name 
```
3) then we pick what we are looking for say all tty files ```
sudo find / -name *tty 
``` the * is a wild card more about [Find command](http://mywiki.wooledge.org/UsingFind)
then there is the locate command this is simple and there are options but you can look them up a simple locate would be ```
locate <name of whatever>
``` 
hope that this helps

---

### Post by effenberg0x0 on 2012-01-04
> **zehsebas said:**
> Removing the program manualy;

sebastiaan@Sebastiaan-Ubuntu:~$ sudo apt-get remove --purge ttf-mscorefonts-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-mscorefonts-installer*
0 upgraded, 0 newly installed, 1 to remove and 71 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing ttf-mscorefonts-installer (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 ttf-mscorefonts-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
sebastiaan@Sebastiaan-Ubuntu:~$ 


----
I used the Galculator code, and it worked.
Also Tabbing worked! i could finally accept terms.
I think the Galculator also installed the fonts.

Im testing right now.

I doubt it. Please try 
sudo dpkg-reconfigure ttf-mscorefonts-installer
If you get errors, try:
sudo apt-get install --reinstall ttf-mscorefonts-installer

---

