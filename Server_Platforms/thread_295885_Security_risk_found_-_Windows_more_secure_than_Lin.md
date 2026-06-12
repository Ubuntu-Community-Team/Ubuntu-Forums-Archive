---
title: "Security risk found - Windows more secure than Linux?"
date: 2006-11-08
forum: Server Platforms
---

### Post by Linux O)o_O7 on 2006-11-08
I have found a breach of security that did not exist in previous Ubuntu OS I had tried out last year.

[https://www.grc.com/port_1024.htm](https://www.grc.com/port_1024.htm)

This port is displayed as closed to the whole world wide web for all to try and hack, it even bypasses my router firewall and opens this port for use and this port scan shows it as closed.

You may tell me there is no risk but personally I like to remain stealth to port scanners and all nasties alike.

Please fix it. Even P2P does not do this to me.


[http://64.233.183.104/search?q=cache:x3S6jsXEcMEJ:boudicca.tux.org/mhonarc/ma-linux/2000/2000-Mar/msg00753.html+linux+port+1024&hl=en&gl=uk&ct=clnk&cd=4](http://64.233.183.104/search?q=cache:x3S6jsXEcMEJ:boudicca.tux.org/mhonarc/ma-linux/2000/2000-Mar/msg00753.html+linux+port+1024&hl=en&gl=uk&ct=clnk&cd=4)

This is a six year old security problem? 

It is time to discuss whether Microsoft is correct when it says their software is more secure and superior.

Do viruses exist for Linux?

---

### Post by Linux O)o_O7 on 2006-11-08
Are there really more vulnerabilities with Linux than Microsoft?


[http://www.bindview.com/Services/RAZOR/Advisories/2001/adv_LkIPmasq.cfm](http://www.bindview.com/Services/RAZOR/Advisories/2001/adv_LkIPmasq.cfm)

---

### Post by Linux O)o_O7 on 2006-11-08
I am now in the process of installing additional firewalls!

---

### Post by Linux O)o_O7 on 2006-11-08
It won't allow me to because my Ubuntu doesn't like KDE and there are tons of conflicts.

Qt GUI Library (Threaded runtime version), Version 3
This is the Trolltech Qt library, version 3. It's necessary for applications that link against the libqt-mt.so.3, e.g. all KDE3 applications.

This means dependencies for firewalls I can use with ease cannot be installed?

If you know of a commercial strengh firewall for Linux one that banks and governments use please tell me.

---

### Post by ner0tic on 2006-11-08
> **Linux O)o_O7 said:**
> It won't allow me to because my Ubuntu doesn't like KDE and there are tons of conflicts.

Qt GUI Library (Threaded runtime version), Version 3
This is the Trolltech Qt library, version 3. It's necessary for applications that link against the libqt-mt.so.3, e.g. all KDE3 applications.

run kubuntu.

---

### Post by Pri0n on 2006-11-08
> **Linux O)o_O7 said:**
> I have found a breach of security that did not exist in previous Ubuntu OS I had tried out last year.

[https://www.grc.com/port_1024.htm](https://www.grc.com/port_1024.htm)

This port is displayed as closed to the whole world wide web for all to try and hack, it even bypasses my router firewall and opens this port for use and this port scan shows it as closed.



Are you concerned because its showing that port as closed instead of being stealthed?

If so, do you have a service running on port 1024 by any chance?  You can find out either by using netstat (netstat -l) or by scanning your machine with nmap.

A quick workaround to "stealth" this port, is to use port forwarding on your router, and forward to an invalid (null) IP address anything incoming the Internet port 1024.

i.e. set up a rule that says to take any packets coming to port 1024, and send it to an invalid IP address (one not in use on your router/network).  It should now show it as stealthed.



> 
I am now in the process of installing additional firewalls!


Won't make much of a difference if they all use the same ruleset.  You only need one firewall with the default rule: Deny all.  Again, you need to find out why your port 1024 is showing as being closed (instead of stealthed). 


> 
Are there really more vulnerabilities with Linux than Microsoft?

[http://www.bindview.com/Services/RAZ...v_LkIPmasq.cfm](http://www.bindview.com/Services/RAZ...v_LkIPmasq.cfm)


Affected Platforms:
Linux 2.0, Linux 2.2, and possibly other systems


PS: Going on a Linux forum and stating that Linux may be more insecure than Windows and then quoting a 5.5 year old vulnerability borders a bit on trolling. [-X

---

### Post by Orwell on 2006-11-08
> **Pri0n said:**
> 


PS: Going on a Linux forum and stating that Linux may be more insecure than Windows and then quoting a 5.5 year old vulnerability borders a bit on trolling. [-X


Well said.
What WAS secure 5 years ago? Are you trying to win followers back to Redmond? Never! :mad:

---

### Post by Chayak on 2006-11-08
You want what the government uses?  It's simple really, they don't connect to the internet save through a secure managed link.  If you want the same equipment [Taclane]("http://www.gdc4s.com/content/detail.cfm?item=f3f0ef4c-cced-46b2-937e-69c42fd1fe3b") Then again it won't help you much as you don't have the means to generate keys nor another taclane to connect to.  If you want to model your system off of really secure military system, put it in a vault and don't connect it to the internet, only classified government networks.

Otherwise, take some Prozac and see a therapist for paranoia issues

---

### Post by Linux O)o_O7 on 2006-11-10
It may come to that yet ner0tic.
 
Pri0n I checked for that and nothing shows up running using this port.

It was NOT secure 5 or more years ago that is the whole point and seems there is still the same or similar security problem. (That no one so far in this thread apart from me experiences? Or cares about?) I only just found out about it myself that some service I don't use and I didn't install or give permission to is showing closed ports to any port scanners. 

YOU KNOW THE BEST PART? IS THAT PORT 1024 IS MARKED AS A MICROSOFT USED PORT. MOST COMMON USE UNDER WINDOWS. 


Chayak Prozac is already in the water and you have it! So many people take it the pollution is in drinking water.

Of course if you think I am paranoid that is fine by me, I don't care what any one thinks and you are allowed to think as you please. 

You may want to try those mind altering suicidal government-pharma sponsored psycho drugs they force kids to take. :mrgreen: 

You know the only other time I had closed or unstealthed ports was when I was using buggy software. 

I don't like the idea of any software doing things without my permission. Especially when it bypasses my hardware firewall.

After so many errors while attempting to instal some packages that failed I finally got firestarter to install and run but when using it I can't run a port scan on my system to see if I have any visible ports. It blocks it out.


I don't troll! I just expected more.

I may apt install Kubuntu - KDE - there is a way..or shall I do a clean install of Kubuntu. Not decided yet. I tried Xubuntu but that wasn't for me. 

Some Linux users from an oline communtity that tried to help me with this suggested finding the root of the cause. So far firestarter blocks port scans and network security utilities.

---

### Post by Linux O)o_O7 on 2006-11-10
Update:


Run some more checks and found no software at all using this port for a service and I have no servers. It is not any P2P software and I configure all other software apart from the web browser.

This time I found no closed ports - all stealth for the time being. I'll keep a close eye on this for a while until it goes away for good or I find out what it is.

I was beginning to doubt myself there for a moment since I knew Linux had never done this to me prior to this occasion.

OK actually the prob is still here. But when I use manually set rules it is stealth.

Still not happy with it.

---

### Post by kvonb on 2006-11-10
Maybe it's from your modem/router, whatever connects you to the 'net.

---

### Post by PvSinNL on 2006-11-11
> **Linux O)o_O7 said:**
> I have found a breach of security [...]
This port is displayed as closed to the whole world wide web for all to try and hack, it even bypasses my router firewall and opens this port for use and this port scan shows it as closed.

You're using a NAT router? And GRC.com reports seeing something? Then it's the router that's responding to the probes. Perhaps it's configured to allow remote management. Either that, or someone has configured port forwarding on the router, allowing inbound traffic to pass. Anyway, I'd start with giving the router a close look first, if I were you.

(Also possibly relevant before claiming you have found "a security breach": Are there other machines on your local network? If so, what OSes do these machines run? Has your router been configured properly? Do other people have administrative control of your router?)

---

### Post by K.Mandla on 2006-11-11
> **Pri0n said:**
> Going on a Linux forum and stating that Linux may be more insecure than Windows and then quoting a 5.5 year old vulnerability borders a bit on trolling. [-X
My thoughts exactly. 

You can test your network security at [http://www.hackerwatch.org/probe/](http://www.hackerwatch.org/probe/) and if you still have issues, the problem is most likely on your end.

---

