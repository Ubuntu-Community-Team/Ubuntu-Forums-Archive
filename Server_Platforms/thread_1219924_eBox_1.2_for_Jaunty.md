---
title: "eBox 1.2 for Jaunty?"
date: 2009-07-22
forum: Server Platforms
---

### Post by hambone79 on 2009-07-22
I started using the eBox platform on my 9.04 server a while back and I really like it. The only problem is that the version that is in the repositories is an old version (0.12) and there doesn't appear to be a repository for the newer version (1.2).

Does anyone know where I can obtain the newer version (1.2) for Jaunty without downgrading Ubuntu?

---

### Post by foolano on 2009-07-22
We are finishing the tests of eBox platform 1.3 for 9.04. It should be available from the eBox PPA in a few days.

---

### Post by hambone79 on 2009-07-22
eBox 1.3 is a development release isn't it? I was looking for 1.2 since it is the latest stable release.

---

### Post by tjwallace on 2009-08-03
Any update on this?  I would love to run ebox on my jaunty server.

---

### Post by deejross on 2009-08-08
I was just looking for an answer to this and i read somewhere that this was the PPA for eBox 1.2 for Jaunty:

```
    deb http://ppa.launchpad.net/ebox/1.2/ubuntu jaunty main 

```

I'm still waiting for Jaunty to install so I'll try it when it's done

---

### Post by tjwallace on 2009-08-08
> **deejross said:**
> I was just looking for an answer to this and i read somewhere that this was the PPA for eBox 1.2 for Jaunty:

```
    deb http://ppa.launchpad.net/ebox/1.2/ubuntu jaunty main 

```

I'm still waiting for Jaunty to install so I'll try it when it's done

Not sure if 1.2 will work for Jaunty but 1.3 will...
```
deb http://ppa.launchpad.net/ebox/1.3/ubuntu jaunty main
```

---

### Post by deejross on 2009-08-08
Yea, they don't have a repository for the 1.2 version of eBox on Jaunty. So I guess we're either stuck with a really old version in the Ubuntu repos (0.12) or an alpha quality one (1.3). I would use Hardy if I could, but Hardy doesn't have any drivers for my new HP server, so I can't even install Hardy.

---

### Post by janascii on 2009-08-10
Could you add the Hardy repository and try installing from there?  Its kind of a long shot, but I'd give it a try if I were in your situation.

---

### Post by deejross on 2009-08-10
Actually, I haven't tried that. When I get my hands on the server again, I'll give it a shot.

---

### Post by slochewie on 2009-09-18
FYI and bump.... 

I just tried to use the Hardy ppa in Jaunty. Didn't work for me. Came back saying there were a bunch of unmet dependencies.

---

### Post by deejross on 2009-09-18
To be honest, I ran out of time and patience trying to get this to work. I ended up installing CentOS over the Ubuntu server install. Turns out that I didn't even need eBox, as it supplies all the gui tools I needed.

Jaunty on the server is a disaster. I can't even get Samba to work properly with Mac OS X Leopard clients. On top of all that, there were other issues I was having with it. I would have gone back to Hardy, but again, my server's hardware wasn't supported by it.

Long story short, avoid installing Ubuntu Server on a real server at all costs. It will save you time and energy. Just go with Red Hat or CentOS instead.

---

### Post by Roasted on 2009-11-08
> **deejross said:**
> To be honest, I ran out of time and patience trying to get this to work. I ended up installing CentOS over the Ubuntu server install. Turns out that I didn't even need eBox, as it supplies all the gui tools I needed.

Jaunty on the server is a disaster. I can't even get Samba to work properly with Mac OS X Leopard clients. On top of all that, there were other issues I was having with it. I would have gone back to Hardy, but again, my server's hardware wasn't supported by it.

Long story short, avoid installing Ubuntu Server on a real server at all costs. It will save you time and energy. Just go with Red Hat or CentOS instead.

Sorry about your luck. Not to throw a kidney punch in here, but our Jaunty Server has worked pretty much flawlessly since day one.

---

### Post by deejross on 2009-11-08
Well, I had forgotten about this thread until you said something. A month and a half ago, I was having all kinds of problems getting Mac OSX clients to work with Samba. The strange thing is, it wouldn't work with Ubuntu or CentOS. I searched EVERYWHERE for an answer. Other forums, IRC, calling people I know that might have an idea, and everything else. Bottom line is, I couldn't get Mac OSX clients to authenticate to Samba, regardless of distribution and version. It turned out to be a problem with Mac OSX clients, and the fix is completely undocumented. In fact, I couldn't find any documentation on the subject at all. 

My problem was that I was connecting to Samba shares from the Mac using:
```
smb://server/share
```
However, to make this work on a mac, you need to swap smb for cifs:
```
cifs://server/share
```
I tried this as a last resort, thinking it would never work, but it did. I don't understand why Mac treats the smb protocol differently than cifs, all I can tell is that Mac clients seem to work just like Windows clients when using cifs.

---

### Post by Roasted on 2009-11-09
Not to throw a second kidney punch to the situation, but I have a mac running 10.4, and I connect using smb://server/share...

What mac version are you running? What OS on the server? What did you use to install samba? etc etc

---

### Post by deejross on 2009-11-09
I tried it with CentOS 5.3 and Ubuntu 9.04 using Mac OS X Leopard (10.5.8) clients. My initial searching lead me to a lot of forums from people saying that Leopard really screwed up file sharing compared to Tiger. I didn't have a Tiger client to test it with, as I only had Leopard clients.

As far as Samba goes, I used whatever came packaged. I tried everything from simple file sharing (using the Share tab in Nautilus' folder properties window) to hand-written smb.conf files, all with the help of Samba experts in the #samba room of IRC and nothing worked. Specifically, allowing guest access failed in all cases unless you completely disabled authentication in Samba. Then, you had to use Share security, as User security would always fail to authenticate against a valid user. Again, this was all using smb://. I basically reinstalled Ubuntu 9.04 and used the simple file sharing method, which worked when I used cifs:// from the clients.

---

