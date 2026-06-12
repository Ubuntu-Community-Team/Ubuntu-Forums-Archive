---
title: "lan dns without internet access"
date: 2009-10-01
forum: Server Platforms
---

### Post by grcunning on 2009-10-01
In my computer networking class I have the option of doing a project where I set up a dns server for our classroom network. The problem is that this network is totally separate from the school network and we aren't allowed to connect it to the internet. I want all the machines to ping each other by name instead of ip using dns instead of host files on all 20 computers. I read on a site somewhere that you cannot do this. Is this correct? Is there some way I can do this using dns? Can I just set up dns and not put in anything for forwarders? The machine in question is using Ubuntu 9.04.

---

### Post by stlsaint on 2009-10-01
put them all on the local lan and they can ping one another.

---

### Post by grcunning on 2009-10-01
they can all ping each other just fine, using ping 192.168.2.100, etc. What I want to do is set up dns so I can use ping mac1, ping server1, etc.

---

### Post by stlsaint on 2009-10-01
ahh...well have you tried to isntall the DNS server via cd...its gonna be hectic but i wouldnt call it in possible...you may have to get alot of packages and dependencies but if your willing to work i think its possible... see here about [BIND9]("https://help.ubuntu.com/community/BIND9ServerHowto") DNS.

you may be looking at downloading packages and depends. on a seperate system and manually installing on the machines yourself. Like i said i have never done this so i dont know all the schematics on it but with no internet it may be looking grim!! Honestly with no internet....doubt you will be as effective as you want...but dont take my word...research on dig some more!! =)

---

### Post by grcunning on 2009-10-01
The instructor let me hook it up just long enough to grab bind9 and a couple of howto's. I unplugged it from the internet and put it back on the local lan, and set it up with this howto:
[http://ubuntuforums.org/showthread.php?t=236093](http://ubuntuforums.org/showthread.php?t=236093)
The howto has you set up forwarders, which I cannot do.
It wasn't working, and I was just wondering if there was something special I had to do because I cant use forwarders and the root servers aren't available.
I just don't want to spend a bunch of time troubleshooting my named.conf.local and zone files just to find out later that it can't be done.

---

