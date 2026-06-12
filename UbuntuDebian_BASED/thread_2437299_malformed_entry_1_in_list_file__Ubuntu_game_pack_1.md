---
title: "malformed entry 1 in list file  Ubuntu game pack 18.04"
date: 2020-02-21
forum: Ubuntu/Debian BASED
---

### Post by rick-919 on 2020-02-21
I recieved this error when attempting to update software on a clean install

e malformed entry 1 in list file/etc/apt/sources.list.d/cuda.list
e malformed entry 1. in list file/

This is a Dell desktop a fresh install on a clean drive. 

Thanks in advance

---

### Post by howefield on 2020-02-21
What is the output of..

```
cat /etc/apt/sources.list.d/cuda.list
```

---

### Post by guiverc on 2020-02-21
The directory `[COLOR=#000000]/etc/apt/sources.list.d/` is empty on a clean or fresh install of Ubuntu, or official flavor of Ubuntu.[/COLOR]

[COLOR=#000000]Ubuntu game pack is terminology used by UA Linux, and I'm unfamiliar with whether or not it puts anything in that directory, but otherwise a user on your system with `sudo` privilieges has added the incorrectly formatted `cuda.list` file on to your system post-install.


[/COLOR]

---

### Post by rick-919 on 2020-02-21
it returns no such file or directory

---

### Post by guiverc on 2020-02-21
> **rick-919 said:**
> I recieved this error when attempting to update software on a clean install
e malformed entry 1 in list file/etc/apt/sources.list.d/cuda.list
e malformed entry 1. in list file/


All responses are based on information you provided, which is more accurate when you provide exact information.  The messages you provided are inconsistent (error messages are consistent, not missing spaces some times, using fullstops only some times) so it's best to copy & paste the detail rather than I'm guessing re-type.

If there is no such file or directory; correct howefield's command based on your provided initial output which is what it was based on. Either the initially provided detail was incorrect, or you or someone with `sudo` access has changed it since you posted.

---

### Post by rick-919 on 2020-02-21
I apparently didn't do something correctly. In any event using copy and past this is the return.  My apologies and just to clarify  this is a fresh install and was found when attempting to check for updates.

cat /etc/apt/sources.list.d/cuda.list


Studio-XPS-8100:~$ cat /etc/apt/sources.list.d/cuda.list
deb [http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64](http://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64) bionic

Thank for y'all's  help grealty appreciated

---

### Post by deadflowr on 2020-02-22
The entry is missing the component aspect.
Source list entries require 4 parts, the archive type (deb), the location (the url) the distribution (bionic), 
and the component (in Ubuntu this is sometimes main, or universe and generically can be called something like stable, or unstable)
You need to find out what it is and try adding it to the end of the line of
*deb [http://developer.download.nvidia.com...ntu1804/x86_64](http://developer.download.nvidia.com...ntu1804/x86_64) bionic*

More on sources.lists here: [https://wiki.debian.org/SourcesList]("https://wiki.debian.org/SourcesList")

Edit; Of course something seems off in how you are doing it, did you follow the cuda guide here:
[https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#ubuntu-installation]("https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html#ubuntu-installation")

---

### Post by rick-919 on 2020-02-22
I didnt do anything. It was just as it installed. Steam was the only thing that updated. It's when I went to check for updates is when I found the error

---

### Post by deadflowr on 2020-02-23
> I didnt do anything. It was just as it installed. 
I don't know what to take from that.
What was installed and how was it installed?

---

### Post by guiverc on 2020-02-23
If it was just installed, you're install has to be illegitimate, as the directory [COLOR=#000000]/etc/apt/sources.list.d/ is empty on a new installation.  Any files found in there are added by `sudo` authorized users after installation. 

[/COLOR]I would look at the files in that directory (ls -ltrh /etc/apt/sources.list.d/) and you can see the date/time of when the file was there if you're talking about a Ubuntu install.  If you're talking about a non-Ubuntu (eg. UA Linux with 'ubuntu' game pack) then I don't know what's there, as I'm only familiar with Ubuntu and Debian.

eg. If you're talking about this ([https://ualinux.com/en/ubuntu-gamepack](https://ualinux.com/en/ubuntu-gamepack))  that is UA Linux, and not Ubuntu.

---

### Post by rick-919 on 2020-02-23
I got the iso from this site [https://ualinux.com/en/ubuntu-gamepack](https://ualinux.com/en/ubuntu-gamepack), used Rufus to put on a flash drive and installed it using the defaults. I wasn't aware that it wasnt Ubuntu. Very confusing world for a noobie.  I think at this point I will re download and re install and see what happens.

Thanks to all for trying Greatly apprecited

---

### Post by deadflowr on 2020-02-23
*Thread moved to **Ubuntu/Debian BASED***

I know nothing of ualinux, or any of it's distributions, so can't help.
Sorry

---

