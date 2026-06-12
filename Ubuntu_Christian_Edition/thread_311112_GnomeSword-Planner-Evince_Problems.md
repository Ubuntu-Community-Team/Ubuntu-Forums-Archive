---
title: "GnomeSword-Planner-Evince Problems"
date: 2006-12-02
forum: Ubuntu Christian Edition
---

### Post by Darrious on 2006-12-02
I can't install any programs because of this.

I'm having problems with gnomesword. I do apt-get remove and this is the out put 

```

Darrious:/home/Darrious/Desktop#sudo apt-get remove gnomesword
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  planner evince gnomesword
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  evince gnomesword planner
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 14.2MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 100862 files and directories currently installed.)
Removing evince ...
Segmentation fault (core dumped)
dpkg: error processing evince (--remove):
 subprocess post-removal script returned error exit status 139
Removing gnomesword ...
Segmentation fault (core dumped)
dpkg: error processing gnomesword (--remove):
 subprocess post-removal script returned error exit status 139
Removing planner ...
Segmentation fault (core dumped)
dpkg: error processing planner (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 evince
 gnomesword
 planner
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I tryed apt-get autoremove and that did not work either. 
I will have to reinstall edgy or somehow get rid of Ubuntu CE and just install the programs.

---

### Post by mhancoc7 on 2006-12-03
I cannot replicate this error. I am not sure what is going on with this. Please let me know if you get anywhere with this.

Jereme

---

### Post by Darrious on 2006-12-03
Well I went into Synaptic and then I reinstalled every program. I tried to remove them at first but it said that there was a problem with removing them. Some sort of script error.

Now when I try to 
```
sudo apt-get install <app>
```

I'm guessing it installs it half-way. I did a test to install gftp. When I type in gftp in the terminal it says this.

```
Darrious:/home/Darrious# gftp
gFTP Error: Cannot find master config file /usr/share/gftp/gftprc
Did you do a make install?

```

---

### Post by Darrious on 2006-12-03
Oh, one more thing I forgot to mention. Even after all this trouble.

GnomSword is not even installed. So I try to get rid of something that is not installed. I do not really mean that it is not installed. I just mean that it is not working.

---

### Post by Darrious on 2006-12-03
Hey!!!

It finally works. I just reinstalled everything but planner. Although I did remove, reinstall, unistall and do all other things before it finally worked.

Umm...

Thanks for the help..:D

---

### Post by doobit on 2006-12-05
FYI there was a problem with the US repositories yesterday. Some of them were offline. I had to change to the main repositories to do updates. Might be related.

---

### Post by Darrious on 2006-12-05
That might have been the problem. But then again...

It wasn't yesterday that I was having the problem. It was yesterday that I reinstalled them and now nothing is wrong with Ubuntu. GnomeSword is actually on there and it works.

---

