---
title: "SAMBA issue with firestarter"
date: 2007-08-20
forum: Server Platforms
---

### Post by guilly on 2007-08-20
For some reason as soon as i enable my firestarter firewall i can not connect to any of my shares. I have the proper ports opened and the policy is applied, as soon as i disable firstarter my shares work fine.

any ideas what other configuration in firestarter could be blocking it? Or perhaps i don't have the proper ports opened? i'm at work but if i remmeber correctly i have ports 137-139 and 445 opened

---

### Post by southernman on 2007-08-20
I did a quick google, to see if I could find something for you. Do you have both udp and tcp allowed with 137 - 139?

[http://www.ale.org/archive/ale/ale-1999-08/msg00245.html]("http://www.ale.org/archive/ale/ale-1999-08/msg00245.html")

---

### Post by guilly on 2007-08-20
yes i do.... by having udp and tcp enabled you mean in my router or are you talking about firestarter?

---

### Post by southernman on 2007-08-20
> **guilly said:**
> yes i do.... by having udp and tcp enabled you mean in my router or are you talking about firestarter?
Yes.


Being that your using layered firewalls (eg router and firestarter) then it would have to be enabled in both. Of course I don't use firestater so would have no ideal how to tell you to do this.

---

### Post by stinger30au on 2007-08-20
> **guilly said:**
> For some reason as soon as i enable my firestarter firewall i can not connect to any of my shares. I have the proper ports opened and the policy is applied, as soon as i disable firstarter my shares work fine.

any ideas what other configuration in firestarter could be blocking it? Or perhaps i don't have the proper ports opened? i'm at work but if i remmeber correctly i have ports 137-139 and 445 opened

i had this same error. i when to synaptic manager and uninstalled firestarter and i have never had a drama with my shares since

---

### Post by ruibernardo on 2007-08-20
Uninstallig Firestarter and not replacing it with another firewall (firehol, shorerwall, etc) on a computer connected to the internet with a server running (samba in this case) is not a good policy.

About guilly's problem here, I'm not using Firestarter now. But from what I know, you have to right-click "Add rule" on the "Allow service" box when editing "Inbound traffic policy". Then select "Samba (SMB)" and select from where you want to accept connections.

I suppose you have done this, but check if you have allowed "Anyone" or the right IP or IP ranges. 

Also, when you are trying to access your share from the other computer, and if Firestarter is really blocking it, you should have a "Blocked connection" event. If you see the IP of the computer from where you are connecting, you could right-click that event and select "Allow Inbound Service for Source".

If this is all ok, then check in the "Preferences", in "Advanced Options". Maybe if you toggle "Block broadcast from.." options you get some response.

Hope this helps in some way. Like I said, I'm not using Firestarter now, but have confirmed it in vmware. Also, most of it is just basic Firestarter usage.

---

### Post by guilly on 2007-08-21
epimeteo, thanks for the reply. I can honestly say i've tried all your suggestions except for the block broadcast one. I will try that out tonight, if this fails as well. What would be a good alternative for a firewall because like you said i really don't want ot be running without one since this server is configured for file sharing and ftp as well...

thanks

---

### Post by ruibernardo on 2007-08-21
guilly,

as a reference to what I was talking about, there is a new tutorial that explains very well how to set samba and Firestarter:  [HOWTO: Easily set up Samba on Feisty]("http://ubuntuforums.org/showthread.php?t=528592").

About the "Block broadcast" tip, you can find some more info in [this thread on fedora forum]("http://forums.fedoraforum.org/archive/index.php/t-47624.html"). It's a bit old, but there are various approaches to the problem, maybe one of them applies to your case. 

About alternative firewalls, if you decide to change, there are many options, but none of them is like Firestarter.

Two of them with a GUI are [Guarddog]("http://www.simonzone.com/software/guarddog/#screenshots") and [Guidedog]("http://www.simonzone.com/software/guidedog/#screenshots") (guidedog complements guarddog when you need a advanced routing/network configuration, so maybe you don't need guidedog) and [fwbuilder]("http://www.fwbuilder.org/").

Without GUI, but still far from being complicated as [iptables]("http://iptables-tutorial.frozentux.net/iptables-tutorial.html"), there is [shorewall]("http://www.shorewall.net/") and [firehol]("http://firehol.sourceforge.net/"). 

This last one being really easy to setup (check its tutorial on the homepage). To setup firehol in Debian/Ubuntu, check [this page on debianhelp.co.uk]("http://www.debianhelp.co.uk/firehol.htm").

NOTE: the actual package of Firehol in Feisty has a bug that doesn't allow it to run with BASH 3.2. You have to apply a workaround as posted here in [Launchpad]("https://bugs.launchpad.net/ubuntu/+source/firehol/+bug/78017/comments/23").

Another note: if you plan to test all these firewalls, certify yourself that you uninstall the previous firewall (purging the configuration files too)  so that two or more firewalls aren't active at the same time. A reboot is also recommended, just to flush any iptables rules that might remain. Then install the other.

I hope all this isn't too confusing, just hope it helps you in some way. :)

---

### Post by wieman01 on 2007-08-21
How do you connect? Using the IP address or the computer's name? 

If you use Firestarter, you won't be able to reach the other computer unless you try to do so by means of (local) IP address. It does not allow you to resolve names...

---

### Post by guilly on 2007-08-21
wieman01, i think you may have a very good point. I'm connecting to my shares by going to network then i see my workgoup ?? however you say it will nto allow you to connect using the hostname then how come it still sees the server "linux-ftp" in this case but when i go to double click on it that's when i'm getting rejected. If this is the reason why i can't connect with hostnames is there a way to map a drive like in windows by ip ?? if so how ?

epimeteo, I will have a closer look at those links when ig et home from work. thanks a ton

thanks

---

### Post by wieman01 on 2007-08-21
> **guilly said:**
> wieman01, i think you may have a very good point. I'm connecting to my shares by going to network then i see my workgoup ?? however you say it will nto allow you to connect using the hostname then how come it still sees the server "linux-ftp" in this case but when i go to double click on it that's when i'm getting rejected. If this is the reason why i can't connect with hostnames is there a way to map a drive like in windows by ip ?? if so how ?

epimeteo, I will have a closer look at those links when ig et home from work. thanks a ton

thanks
I assume that you have opened the ports for inbound & outbound traffic.

Second, you don't really map driver in Ubuntu. Fire up you file browser and connect to the driver by typing:
> smb://192.168.168.40/data
That's just an example. Replace the IP and the folder name with yours. That should do... and bookmark the URL. Then you have what you want. :-)

---

### Post by guilly on 2007-08-21
ok great is there a way to tell ubunt to connect to this share everytime at boot up??  the reason i need this is because i need to use windows for school when programming .NET but i've sorta fell into this hole linux addiction over the summer and would still like to use it for my primary OS. So i set up a VM for vista for my programming puproses.. but i'd like a centralised location to save all my school crap thats why i set up the samba server. But if i could just work off the one folder that is mapped from linux and windows it would make sure that i'm always workign with the most current file..


thanks

---

### Post by wieman01 on 2007-08-21
> **guilly said:**
> ok great is there a way to tell ubunt to connect to this share everytime at boot up??  the reason i need this is because i need to use windows for school when programming .NET but i've sorta fell into this hole linux addiction over the summer and would still like to use it for my primary OS. So i set up a VM for vista for my programming puproses.. but i'd like a centralised location to save all my school crap thats why i set up the samba server. But if i could just work off the one folder that is mapped from linux and windows it would make sure that i'm always workign with the most current file..


thanks
What you are looking for is NFS in that case. You can mount NFS folders over the network. SAMBA is a bit different, but the advantage is that you can share files between Windows & Linux systems.

[http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605")

But setting a bookmark, you have more or less mapped the drive... What else would you need?

---

### Post by guilly on 2007-08-21
hey wieman, your were 100% correct it to do with firestarter not being able to resolve hostnames. And your right a bookmark will be fine, NFS won't do it since i am running windows as well in a VM 

thanks for the help

---

### Post by wieman01 on 2007-08-21
> **guilly said:**
> hey wieman, your were 100% correct it to do with firestarter not being able to resolve hostnames. And your right a bookmark will be fine, NFS won't do it since i am running windows as well in a VM 

thanks for the help
Welcome. This has been a problem since Dapper at least. So I use the same workaround. I am in good company now. :-)

---

