---
title: "ubuntu 12.04 beta failed to boot after installing dropbox"
date: 2012-04-11
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by puat133 on 2012-04-11
Hi all,

I just installed dropbox from dropbox site since the one in ubuntu ppa is not working. Every thing goes fine, until I turned off my laptop. After I turned it on again, when I try to boot from any boot session option (either Unity-Gnome-Fallback), the screen goes blinking for seconds, and it throw me back again to login screen. I captured the error message as below

```

speech-dispatcher disabled; edit /etc/default
* Stopping save kernel messages
* Starting the Winbind daemon winbind

saned disabled; edit /etc/default/saned
                                  Starting

ERROR: Module ssb does not exist in /proc/modules

```
[IMG]http://dl.dropbox.com/u/20522912/2012-04-11%2007.19.05%5B0%5D.jpg[/IMG]
Any help please...
:confused:

---

### Post by puat133 on 2012-04-11
bump..:confused:

---

### Post by Elfy on 2012-04-11
*Thread moved to **Ubuntu +1 (Precise Pangolin)**.*

---

### Post by puat133 on 2012-04-12
No answer..?:rolleyes::rolleyes:

---

### Post by puat133 on 2012-04-13
No answer?? :confused::confused:

---

### Post by shadowfirebird on 2012-04-13
Sorry, all I can say of my own knowledge is that I'm on 12.04, using Dropbox, and it didn't happen to me.

I know that that's not good news for you.  Good luck...

---

### Post by cariboo on 2012-04-13
If you purge the dropbox package you installed, will your system boot to a desktop?

---

### Post by puat133 on 2012-04-15
Thanks for the replies. I've purge the dropbox installations, and nothing happen. After that, I've looked some workarounds similar to this issue, and try the solutions, and again, nothing happen.

Frustrated with this, I reinstall the precise Pangolin, but  without erasing the old installation, and I can recover most of my installed programs/packages.

Should I mark this thread as SOLVED??):P

---

### Post by puat133 on 2012-04-15
shadowfirebird, Dropbox that you are installed is from ubuntu source/ppa, or you downloaded it from dropbox site? 

What happened to me was, I installed dropbox from ppa, and it is not working, (http_proxy issue). I decide to purge it, and replace with installation from dropbox site, and it is work fine. But after that, the ubuntu are failed to boot with errors I mentioned earlier. ;);)

---

### Post by kuvanito on 2012-04-15
this is not a PP issue neither dropbox,they both work in harmony
check your HD and do a clean install of PP,get your iso from the daily builds,use the latest one and use unetbootin to create your bootable usb,ofcourse this will have to be done in another machine.not hing wrong with PP and dropbox.....

---

### Post by bobandiara on 2012-04-16
I think there is no need to download Dropbox from its site on Ubuntu 12.04. It is available on the official repos!:grin:

(At least a "sudo apt-get install nautilus-dropbox" solved the problem for me, maybe it works for you too.)

---

### Post by puat133 on 2012-04-16
> **bobandiara said:**
> I think there is no need to download Dropbox from its site on Ubuntu 12.04. It is available on the official repos!:grin:

(At least a "sudo apt-get install nautilus-dropbox" solved the problem for me, maybe it works for you too.)

Mine is not working, and give this result
```


XXX@XXX-N148P-N208P-N218P-NB28P:~$ dropbox start -i
Starting Dropbox...
Dropbox is the easiest way to share and store your files online. Want to learn more? Head to http://www.dropbox.com/


Error: Trouble connecting to Dropbox servers. Maybe your internet connection is down, or you need to set your http_proxy environment variable
The installation of Dropbox failed.

```
):P

---

