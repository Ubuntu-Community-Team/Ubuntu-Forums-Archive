---
title: "apt-get asking for Ubuntu Server CD?"
date: 2008-04-22
forum: Server Platforms
---

### Post by garfonzo on 2008-04-22
I just installed 7.10 server the other day onto my soon-to-be home file/sprint server. Once everything was installed, I did an:
```

apt-get update

```
at which point it started to download stuff as per normal. But then, at item 10 of things to download, it started failing. Almost like I had physically unplugged the ethernet chord. 

So today I tried to:
```

apt-get install nmap

```
for security stuff and it asked for the Ubuntu Server Install CD. Has anyone run into this before? I'm relatively new to this so be patient. 

I tried doing some pinging but could only get a response from computers on my LAN, not beyond (like from google or something). However, my main desktop has the same ping response (can ping lan comps but not beyond the lan). How can I tell if my new server is actually "seeing" the internet? 

Cheers,

Garfonzo

---

### Post by xc3RnbFO8P on 2008-04-23
delete

---

### Post by wormser on 2008-04-23
If you installed server then you probably do not have a GUI.  You need to edit the sources.list file.

```
sudo nano /etc/apt/sources.list
```At the top comment out the CD-rom and uncomment main, universe and the multiverse repositories.  If you are unsure about what to comment out then post the file.
 
Then you need to update apt.

```
sudo apt-get update
```

Pinging is a good method to test your internet connection.  You might have a DNS issue.  Try pinging by domain name and ip address.  4.2.2.2 is a good address to ping.  If the name does not work then it is a DNS issue.

---

### Post by garfonzo on 2008-04-23
> **wormser said:**
> If you installed server then you probably do not have a GUI.  You need to edit the sources.list file.

```
sudo nano /etc/apt/sources.list
```At the top comment out the CD-rom and uncomment main, universe and the multiverse repositories.  

Correct, no GUI.

Now, is there any way to check that the server has a working internet connection to the world? I've not really messed around with things too much, but, if I had a GUI I would open Firefox and hit a few websites to determine that my connection is working. Is there a way to do this on a GUI-free server?

---

### Post by wormser on 2008-04-23
> **garfonzo said:**
> Correct, no GUI.

Now, is there any way to check that the server has a working internet connection to the world? I've not really messed around with things too much, but, if I had a GUI I would open Firefox and hit a few websites to determine that my connection is working. Is there a way to do this on a GUI-free server?

Did you ping sites or try downloading with apt-get?  If the apt-get update worked then you are online.

```
ping ubuntuforums.org
```

and by ip

```
ping 91.189.94.186
```

---

### Post by garfonzo on 2008-04-23
> **wormser said:**
> Did you ping sites or try downloading with apt-get?  If the apt-get update worked then you are online.

```
ping ubuntuforums.org
```

and by ip

```
ping 91.189.94.186
```

Well I guess I'm online because I downloaded "beep" with apt-get. However, not that I am too concerned since my server appears to be online, but, I can't ping anything. Even my computer that I know is online (I'm typing from it) is unable to ping anything. Odd.

---

### Post by wormser on 2008-04-23
> **garfonzo said:**
> Well I guess I'm online because I downloaded "beep" with apt-get. However, not that I am too concerned since my server appears to be online, but, I can't ping anything. Even my computer that I know is online (I'm typing from it) is unable to ping anything. Odd.

Your network might be blocking icmp ping requests.

---

