---
title: "Samba Firestarter issues. Frustrating!!"
date: 2006-03-30
forum: Server Platforms
---

### Post by Neur0s1s on 2006-03-30
Ok,  Im running samba on my Pc in ubuntu.  Im also running firestarter for the firewall.  Im sitting behind a router and all my "3" computers are on dhcp with reserved ip's so i can use port forwarding to the ubuntu pc for ssh.  "too lazy to set it up static" shouldnt matter i dont think???  

My problem is,  I can ssh from my laptop running windows xp pro to the server/ubuntu no problem after setting a rule in firestarter.  I can also ping the server and my router no problem.  I start the xp laptop and try to connect to the server so i can copy files back and forth and no go.  I disable firestarter and it connects to the ubuntu pc no problem.  

Ok, ive tried everything with firestarter all the way to just opening up the ubuntu server to all incoming connections from the laptop and its a no go connecting to samba untill i shut down firestarter.  Once connected, I can turn firestarter back on and i dont have to worry again untill i reboot the laptop and then it starts over.  

Does anyone have any suggestions as to what the problem is?  I know this has to be something simple that i am overlooking.  

Thanks.

---

### Post by frodon on 2006-03-31
This thread will interest you : [http://ubuntuforums.org/showthread.php?t=152666](http://ubuntuforums.org/showthread.php?t=152666)

---

### Post by Neur0s1s on 2006-03-31
I guess out of curiosity, can you add iptable rules to firestarter? Would you just add them to the config file?

---

### Post by frodon on 2006-03-31
Yes you can add iptable rules, that exactly what firestarter do, however if you just add the iptables line running an iptables command i think you will have to add it after each reboot.
I don't use firestarter anymore, so i don't really know which file use firestarter to store its rules, sorry :(

---

### Post by LordHunter317 on 2006-04-01
If the box is inside the network, why is it running a firewall?  Remove it would be my first suggestion.

Samba is nortoriusly difficult and painful to firewall.   You need to allow:[list][*]TCP netbios-ssn, microsoft-ds[*]UDP netbios-ns, netbios-dgm[*]And unless you're running WINS or have everyone in DNS:[*]Broadcast UDP netbios-ns, netbios-dgm[/list]

---

