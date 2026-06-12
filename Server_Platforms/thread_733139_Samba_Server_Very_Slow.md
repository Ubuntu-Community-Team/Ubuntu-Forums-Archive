---
title: "Samba Server Very Slow"
date: 2008-03-23
forum: Server Platforms
---

### Post by Charliecyr on 2008-03-23
I keep seeing references to this problem but no real solution yet.  I am running Ubutu/Kubuntu 7.10.  When connecting to a Samba share from a windows box it is very slow.  If you type //linux in a windows run box it takes 5-10 minutes to open up and show Samba shares.  I don not have this problem with my Mac OSX box as it connects to the samba shares very quickly.  This is new problem that I believe started when I upgraded to 7.10.

---

### Post by HermanAB on 2008-03-23
You need to run tcpdump and look at the packets to see what is amiss.

---

### Post by Charliecyr on 2008-03-23
I found that buy disabling DHCP and setting a fixed IP and setting a DNS alias fixed it.  Very odd as this worked with DHCP before.  Seems DHCP isn't updating the host name and seeing as it's a home network without a local DNS server it cant resolve the host name.  The odd thing is that if I connected to it using the IP address alone it was still slow.  I usually do that to rule out DNS issues.

---

### Post by netlogic on 2008-03-23
1. Make sure Samba server is the browser master
2. Make sure your names don't conflict between DNS and Wins
3. Run Wins server and make sure Windows client are running in  H-node, not B-NODE. H-node is hybrid mode. Ask the Wins server first then annoy everyone in the network with the broadcast. If you don't understand the node type, it is better to run Wins and point it to there, but make sure the machines use cifs connections only with Wins, not DNS.

DHCP is probably working, because it is asking the server for the extra information.

---

### Post by HermanAB on 2008-03-24
It is basically an authentication problem - for each and every file access, the system has to figure out whether a particular user has the required permissions to access the file and various services are used to determine that.  Windows networking is a horrible mess of things and the hostnames and DNS has to be just right  for everything to work properly, other wise you can get a 1.5 to 2 minute timeout per file for each failed lookup.

---

### Post by netlogic on 2008-03-24
I am not sure that is it, dude. I'm pretty sure that isn't it. Windows XP always cache it's credential in the registry in the local_user. Once, it negotiated it once, it will use the same cred. I think it is the browsing and name issue, because it isn't happening with OSX. Osx'S smb implementation doesn't have elections. It just ignores it.

---

### Post by FakeOutdoorsman on 2008-03-24
First measure raw TCP throughput with iperf (it is in the universe repository) just to make sure it is not a network problem before messing with Samba. There is a good description of iperf by netztier (post 13): [slow gigabit transfers via samba]("http://ubuntuforums.org/showthread.php?t=531505&page=2").

---

### Post by Charliecyr on 2008-03-24
After checking somemore it seems that the workgroup value in smb.comf was missing so samba was defaulting to  "workgroup" but the actual home workgroup is "domain2".  After changing this in smb.conf I was able to enable DHCP and connect just fine.  An update along the way must have deleted the workgroup setting from the file.  BTW the DNS domain name set by DHCP was "domain2" so the samba server had completely different DNS and NETBIOS names.

---

### Post by netlogic on 2008-03-24
If it was on its own workgroup, it was probably maintaining its own browser list and asking other browse master or asking everyone in the workgroup about what are being shared.  Another issue could have been, every time it was requesting something from others it could not figure out who was the browse master. Another issue is if you set the OS level to default, it could have been going through the voting process of who will be the master. If you want very fast lookup, setup WINS, setup your samba workgroup server as "preferred master = yes" and set up your OS LEVEL very high such as "os level = 250." Samba 3.0 is an improved NT4 style system. Many of the issue from NT4 is still there, but with Samba things can be set to manual mode unlike NT4's automatic and hope for the best, or reinstall, because server roles have been changed.

---

### Post by HermanAB on 2008-03-25
See para 4 Notes, of this guide: [http://aeronetworks.ca/LinuxActiveDirectory.html](http://aeronetworks.ca/LinuxActiveDirectory.html)

Maybe it rings a bell.

Cheers,

Herman

---

