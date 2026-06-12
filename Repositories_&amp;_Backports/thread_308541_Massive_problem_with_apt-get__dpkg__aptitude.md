---
title: "Massive problem with apt-get / dpkg / aptitude"
date: 2006-11-28
forum: Repositories &amp; Backports
---

### Post by robenroute on 2006-11-28
Hi there,

Running Edgy, I decided to install Quod Libet as this is my favourite music player. However, instead of using hugmenot's Edgy packages (QL 0.24), I used foxy123's Dapper packages (what was I thinking!). Of course, the installation (sudo dpkg -i ....) went kind of t!ts up and now I seem to have a corrupt apt-get database, because I can't uninstall, remove or otherwise get rid of the package called "exfalso":

```
rob@asus:~$ sudo aptitude remove -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the exfalso package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
rob@asus:~$ 

```

another attempt:

```
rob@asus:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package exfalso needs to be reinstalled, but I can't find an archive for it.
rob@asus:~$ 

```

and yet another:

```
rob@asus:~$ sudo aptitude remove exfalso
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  exfalso 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2142kB will be freed.
Writing extended state information... Done
dpkg: error processing exfalso (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 exfalso
Aborted (core dumped)
rob@asus:~$ 

```

As you can see, it all leads to absolutely nothing. Reinstalling the file isn't an option as I can't find the file on the forum any more ([this]("http://www.ubuntuforums.org/showthread.php?p=1816802#post1816802") thread). I know, sounds a bit silly, but I could swear I got it from this thread and it's not there any longer....

Help is urgently needed and much, much appreciated.

Thanks a lot, Rob

---

### Post by robenroute on 2006-11-28
Hi there,

Running Edgy, I decided to install Quod Libet as this is my favourite music player. However, instead of using hugmenot's Edgy packages (QL 0.24), I used foxy123's Dapper packages (what was I thinking!). Of course, the installation (sudo dpkg -i ....) went kind of t!ts up and now I seem to have a corrupt apt-get database, because I can't uninstall, remove or otherwise get rid of the package called "exfalso":

```
rob@asus:~$ sudo aptitude remove -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
E: I wasn't able to locate file for the exfalso package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
rob@asus:~$ 

```

another attempt:

```
rob@asus:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package exfalso needs to be reinstalled, but I can't find an archive for it.
rob@asus:~$ 

```

and yet another:

```
rob@asus:~$ sudo aptitude remove exfalso
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  exfalso 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 2142kB will be freed.
Writing extended state information... Done
dpkg: error processing exfalso (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Errors were encountered while processing:
 exfalso
Aborted (core dumped)
rob@asus:~$ 

```

As you can see, it all leads to absolutely nothing. Reinstalling the file isn't an option as I can't find the file on the forum any more ([this]("http://www.ubuntuforums.org/showthread.php?p=1816802#post1816802") thread). I know, sounds a bit silly, but I could swear I got it from this thread and it's not there any longer....

Help is urgently needed and much, much appreciated.

Thanks a lot, Rob

---

### Post by Ramses de Norre on 2006-11-28
Try this:
```
sudo dpkg --purge --force-remove-reinstreq exfalso
```

---

### Post by richardward101 on 2006-11-28
Have you tried removing in directly with dpkg?

Sorry I see you have.

---

### Post by robenroute on 2006-11-28
> **Ramses de Norre said:**
> Try this:
```
sudo dpkg --purge --force-remove-reinstreq exfalso
```

Tried that, just now:

```
rob@asus:~/Desktop$ sudo dpkg --purge --force-remove-reinstreq exfalso
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 96737 files and directories currently installed.)
Removing exfalso ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 932, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing exfalso (--purge):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 exfalso
rob@asus:~/Desktop$ 

```

Just for the record, I'm currently unable to install or remove ***any*** package, due to this issue.

Any other suggestions? Please....

---

### Post by robenroute on 2006-11-28
Anyone? Please....

There must be something I can do, because the idea of "nothing can be done" is unbearable, as it implies reinstalling Ubuntu!!!

Rob

---

### Post by Ramses de Norre on 2006-11-28
Really hacky would be to remove the package's section form /var/lib/dpkg/status, I think dpkg wont consider it installed no more then, but I'm not sure about it and I'm not in the possibility to test this method..

So if you do try this: back up your status file and don't be mad at me if you end up in a tty to restore it.. (but in the end your system can't be worse than it is now.. )

---

### Post by robenroute on 2006-11-28
> **Ramses de Norre said:**
> Really hacky would be to remove the package's section form /var/lib/dpkg/status, I think dpkg wont consider it installed no more then, but I'm not sure about it and I'm not in the possibility to test this method..

So if you do try this: back up your status file and don't be mad at me if you end up in a tty to restore it.. (but in the end your system can't be worse than it is now.. )

That sounds daring indeed. I'll give that a go tomorrow; I'll let you know how it went. Thanks for the feedback tough.

---

### Post by robenroute on 2006-11-29
Ramses, I backed up my available, available-old, status and status-old files first. Then removed the package sections in all of the 4 mentioned files. Started up Synaptic again which resulted in a notification of 1 broken package being present on the system. Removed that, and, from the command line, installed the Quod Libet packages (for Edgy, this time!) successfully.

Everyhting seems to work smoothly. Thanks a lot!

Rob

---

### Post by robenroute on 2006-11-29
Problem's been solved, see [this]("http://www.ubuntuforums.org/showthread.php?t=308544") thread, thanks to Ramses.

Rob

---

### Post by mlissner on 2007-01-05
Hey, somehow I had this problem when I tried to install mfc4800lpr (a driver for my brother mfc printer). I just did the trick with backing up the four files, and then deleting the lines in the originals that contained the faulty program...is that going to fix it and be harmless? 

I didn't have the one broken package pop up in synaptic...

Thanks

---

