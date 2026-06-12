---
title: "Only thing on install 20.04 checked was Powershell but can't get it to work."
date: 2020-10-01
forum: Server Platforms
---

### Post by Raymond Day on 2020-10-01
Never used Powershell but wanted to try it out and looks like you just do the command ```
pwsh
``` but mine just don't work.

I did make a link to my old /root folder and renamed the new install /root to /root~

So I uninstalled Powershell and installed it again.

Here is the command line doing this.

```
root@rayday:~# snap install powershell --classic
snap "powershell" is already installed, see 'snap help refresh'
root@rayday:~# snap remove powershell --classic
error: unknown flag `classic'
root@rayday:~# snap remove powershell
powershell removed
root@rayday:~# snap install powershell --classic
powershell 7.0.3 from Microsoft PowerShell&#10003; installed
root@rayday:~# pwsh
cannot create user data directory: /root/snap/powershell/137: Not a directory
root@rayday:~# pwsh
cannot create user data directory: /root/snap/powershell/137: Not a directory
root@rayday:~# cd /root/snap/powershell/137
root@rayday:~/snap/powershell/137# ls -l
total 0
root@rayday:~/snap/powershell/137# pwd
/root/snap/powershell/137
root@rayday:~/snap/powershell/137#
```

All is working good now and it's only been installed a little over 24 hours now.

The folder is there it's saying "Not a directory" but it is but has nothing in it.

It my be that I moved the /root folder it looks like this:

```
lrwxrwxrwx   1 root root    34 Sep 30 12:05 root -> /media/WD-10TB-2/USBdisk2-3TB/root
drwx------   7 root root  4096 Sep 30 11:24 root~
```


-Raymond Day

---

### Post by LHammonds on 2020-10-01
Powershell....on Linux?  hmmm....thought that was just a Windows thing.  I've used Windows for ages but never found the need to learn Powershell.

---

### Post by ameinild on 2020-10-01
Yeah, apparently it's a thing - Microsoft has a package archive, where among other things you can install Powershell. I have fiddled a bit with it on Windows, but I don't really see the advantage over Bash scripting on Linux. 

However, the main difference is that Powershell is object oriented, so commands are not "just" streams and characters on the screen, but objects with certain properties.

Still, I don't believe it offers something extraordinary over Bash and/or Python for practical uses.

---

