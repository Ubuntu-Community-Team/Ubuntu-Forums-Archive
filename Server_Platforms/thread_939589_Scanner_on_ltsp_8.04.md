---
title: "Scanner on ltsp 8.04"
date: 2008-10-06
forum: Server Platforms
---

### Post by jackbert on 2008-10-06
Hello
(Sorry for mistakes, I'm not English)

I installed ubuntu 8.04 in ltsp mode, all work fine.

I try to detect a usb scanner, it works on the server (i can scan from xscane) but it doesn't work from clients (the scanner it doesn't see as a scanner).

I do this :
- I edit /opt/ltsp/i386/etc/lts.conf
```
[default]
XINETD_SERVICES = "saned"
LOCALDEV=True
```

- I put the privilege for my user
```
jack@srv-ltsp:~$ id
uid=1000(jack) gid=1000(jack) groupes=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),105(scanner),107(fuse),109(lpadmin),115(admin),1000(arno)
```

I rebuild the ltsp image and restart my clients
```
/opt/ltsp/i386/etc/lts.conf
```

But when I plug the scanner on my clients, xsane says that It does't find peripheral
dmesg from the client in graphic (I think it's the scanner??)
```
[145773.415815] usb 6-3: reset high speed USB device using ehci_hcd and address 2
[148326.084096] usb 6-3: reset high speed USB device using ehci_hcd and address 2
```

when i do "scanimage -L" and "sane-find-scanner", it returns that it doesn't find any peripheral

I forgot something???

Thanks
Jack

---

### Post by jackbert on 2008-10-07
Hello

I try to dell the repertory /opt/ltsp/i386/ and rebuild it with the command "ltsp-build-client" but nothig change when I reboot the client :(:(

Have you got any idea to detect the scanner on the client???
It works on the server but not see on the client...

If you have any way to give me, because I don't no anymore what I have to do..
:wink:

Thanks Jack

---

### Post by jackbert on 2008-10-10
up :)
jack

---

### Post by srangelov on 2009-01-25
I created a similar post, but for Ubuntu 8.10. No solution yet:
[http://ubuntuforums.org/showthread.php?t=1046302]("http://ubuntuforums.org/showthread.php?t=1046302")

---

### Post by dejuren on 2009-01-27
Take a look here - [http://www.k12ltsp.org/mediawiki/index.php/Scanners](http://www.k12ltsp.org/mediawiki/index.php/Scanners) 
This information looks like what you need.

---

### Post by srangelov on 2009-02-01
Hi dejuren,

Thanks for the post.

I checked your link but it didn't help me. I actually did not even try it, because there is no sane.d directory in /opt/ltsp/i386/etc/ . So except for assigning static address to client I wouldn't be able to do anything else from that instructions. And I decided not to try them.

Today I figured it out with the help of a friend.

I checked ownership and group of scanner and it was:
```
ls -l /dev/bus/usb/001
total 0
crw-rw-r--  1 root root 189,  0 2009-01-29 21:54 001
crw-rw-r-+ 1 root root 189, 22 2009-02-01 13:59 023

```

023 is the scanner

I identified two combinations as a solution:
A. Change group to Scanner, or
B. Change permissions for Others to Read and Write

I think A. is the best.

---

### Post by srangelov on 2009-02-02
I noticed that this solution is only temporary. After a restart the permissions are set to root again. I guess it is the way it should be. 

I will be grateful if someone provides a permanent solution. Thank you.

---

