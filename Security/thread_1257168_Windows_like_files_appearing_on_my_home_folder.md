---
title: "Windows like files appearing on my home folder"
date: 2009-09-03
forum: Security
---

### Post by DouglasCaixeta on 2009-09-03
Suddenly, in my HOME folder, appears 2 strange files, with the following name:

c:\NOSO072009BETA3ba.log

\WINDOWS\system32\drivers\etc\hosts

I don't have Wine, I don't use Wine or any windows programs.

This files seems to me, like windows virus, trying to do something with my system. Cause inside the file "\WINDOWS\system32\drivers\etc\hosts" there is a bunch of IP and hosts of banks. 

I don't know what is happening, but if my bank IP is inside this file, means that the system should not allow me to enter in this site, right? 

So, its like a phishing thing. I know that won't work on Linux, but I wanna know why this file was created.

Does any one has an idea?

---

### Post by cdenley on 2009-09-03
Probably some script did an automated attack trying to change your hosts file so domains will resolve to a different IP, and assumed you would be using windows. This would be useful for them if they pointed a domain to the IP of a server they control. They can then spoof a website to trick you into providing sensitive information. Linux does use a hosts file, but it is located at /etc/hosts.

Attackers should not be able to create files, so you have been compromised in some way. Do you run any servers?
```

sudo netstat -tlnp

```

---

### Post by DouglasCaixeta on 2009-09-03
I have been compromised??

Here is the output:

```
Conexões Internet Ativas (sem os servidores)
Proto Recv-Q Send-Q Endereço Local          Endereço Remoto         Estado       PID/Program name
tcp        0      0 127.0.0.1:7634          0.0.0.0:*               OUÇA       2550/hddtemp    
tcp        0      0 127.0.0.1:631           0.0.0.0:*               OUÇA       2901/cupsd      
tcp6       0      0 ::1:631                 :::*                    OUÇA       2901/cupsd  
```

As far as I know, I don't run any servers.

I'm running clamav here. I will post the results when it's done.

I'm wondering how did I get infected. The only thing that I have done that could compromise my system was using an infected usb pen drive.

Here is the content of my /etc/hosts

```
127.0.0.1	localhost
127.0.1.1	os
```

---

### Post by DouglasCaixeta on 2009-09-03
Clamav done.

```
----------- SCAN SUMMARY -----------
Known viruses: 617781
Engine version: 0.95.1
Scanned directories: 28793
Scanned files: 175136
Infected files: 4
Data scanned: 12510.52 MB
Data read: 46673.45 MB (ratio 0.27:1)
Time: 3547.434 sec (59 m 7 s)
```

But now I don't know which are those 4 files.
I'm running again with -i parameter.

---

### Post by DouglasCaixeta on 2009-09-03
> **DouglasCaixeta said:**
> Clamav done.

```
----------- SCAN SUMMARY -----------
Known viruses: 617781
Engine version: 0.95.1
Scanned directories: 28793
Scanned files: 175136
Infected files: 4
Data scanned: 12510.52 MB
Data read: 46673.45 MB (ratio 0.27:1)
Time: 3547.434 sec (59 m 7 s)
```

But now I don't know which are those 4 files.
I'm running again with -i parameter.

The 4 files was:

/usr/share/doc/nautilus-clamscan/examples/clam.cab: ClamAV-Test-File FOUND
/usr/share/doc/nautilus-clamscan/examples/clam.exe: ClamAV-Test-File FOUND
/usr/share/doc/nautilus-clamscan/examples/clam.zip: ClamAV-Test-File FOUND
/usr/share/doc/nautilus-clamscan/examples/clam.exe.bz2: ClamAV-Test-File FOUND

So I still don't know which is this virus, or trojan, or whatever, and how he manage to create those files.

If he is a windows virus, how he is running in my linux system? How he create those files? What he is doing now?

---

### Post by cdenley on 2009-09-03
> **DouglasCaixeta said:**
> The 4 files was:

/usr/share/doc/nautilus-clamscan/examples/clam.cab: ClamAV-Test-File FOUND
/usr/share/doc/nautilus-clamscan/examples/clam.exe: ClamAV-Test-File FOUND
/usr/share/doc/nautilus-clamscan/examples/clam.zip: ClamAV-Test-File FOUND
/usr/share/doc/nautilus-clamscan/examples/clam.exe.bz2: ClamAV-Test-File FOUND

So I still don't know which is this virus, or trojan, or whatever, and how he manage to create those files.

If he is a windows virus, how he is running in my linux system? How he create those files? What he is doing now?

It is not a windows virus. Either you previously enabled "remote desktop" and allowed someone to control your computer (doesn't appear to be enabled at the moment), or an attacker used a cross-platform exploit for something such as a firefox plugin to create that hosts file. The file itself is harmless in your situation. The problem is you don't know for sure what else could have been done. You must have done something wrong to get compromised by an automated script like that. Do you have all security updates installed? Either that, or maybe you just extracted the file from some type of archive without realizing the /windows/system32/drivers/etc/hosts file was in it.

---

