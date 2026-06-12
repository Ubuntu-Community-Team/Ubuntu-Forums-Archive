---
title: "Securing Ubuntu questions"
date: 2009-06-01
forum: Security
---

### Post by Alden born on 2009-06-01
OK i have a system that i want to put some extra protection on it.  I know in general Ubuntu is secure. This particular machine has windows and Ubuntu computers that connect to it. (FYI)

From what i have read online i was thinking about the following setup. And please tell me your thoughts on each section. Or if you have something to suggest let me know. 

_Firewall_ -> Fire starter
_Anti virus_ -> AVG
_Root kit detection_ -> chkrootkit


Thanks

---

### Post by HermanAB on 2009-06-02
Hmm...
chrootkit - useless, waste of time.
AVG - good for scanning Windows files, so run it on the Windows VM. Alternatively use ClamWin.
Firestarter - Deprecated, use UFW instead.

Do activate Window Firewall on the Windows VM.

---

### Post by lovinglinux on 2009-06-02
chrootkit - I use rkhunter, which also check if important files have been changed

AVG -  doesn't remove or clean infected files and as far as I know, it doesn't have a GUI. Use [BitDefender](https://help.ubuntu.com/community/BitDefender) instead, which scans fast, has a nice gui, has integration with Nautilus and a nice drop-box.

Firestarter - Deprecated, use UFW instead and Gufw for graphical interface. UFW is installed by default. You can install the gui by searching for "Firewall Configuration" in the "Add/Remove manager".

Some things you should know:

[list][*] Anti-virus is useful if you have Windows on your network, because they don't scan Linux virus, since there aren't any in the wild.
[*] 
[*] Firestarter and UFW/GUFW are just firewall managers, which means they allow you to create rules for iptables (the real firewall) without knowing the commands. You don't need them if you know the iptables commands. 
[*] 
[*] Iptables are installed by default and activated at boot, but they allow all traffic by default. Since Ubuntu doesn't come with any services running by default, then you don't need the firewall. If you install services, then you might want to use a firewall to restrict access to the open ports.
[*] 
[*] Most people coming from Windows like Firestarter because of the connection monitoring feature, but you shouldn't be running it all the time, due to security risks of it's root requirements. Besides, you don't have to run it all the time to be protected, since iptables runs in the background.
[*] 
[*] UFW doesn't have a monitoring tool. You can use use another tool like [IPTstate](http://ubuntuforums.org/showpost.php?p=7331295&postcount=8) for that
[*] 
[*] If you have a router with firewall capabilities, then you probably don't need to activate the firewall on Ubuntu.
[*] 
[*] If you use p2p programs, you might want to use [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/).[/list]


*UKeywords: 649167 2009 june firestarter ufw gufw avg bitdefender rkhunter iptables firewall*

---

### Post by Alden born on 2009-06-02
OK thanks i will take that into consideration? 

Another question the computer I'm using is mainly just to store data, music and download torrents. Do you think i need to change anything with the firewall? What do you recommend?

---

### Post by lovinglinux on 2009-06-02
> **Alden born said:**
> OK thanks i will take that into consideration? 

Another question the computer I'm using is mainly just to store data, music and download torrents. Do you think i need to change anything with the firewall? What do you recommend?

Deny all incoming traffic and allow only the ports you need for torrent and for connecting to the file server. If you access it remotely only from your LAN, then you might also want to restrict access to the internal IPs.

You might like Deluge for torrents, since you can connect remotely with terminal, webui and gtk interfaces.

---

### Post by Alden born on 2009-06-02
Thanks again ill check Deluge out.  

Right now i use transmission it has always felt like it was lacking in features.

---

### Post by lovinglinux on 2009-06-02
> **Alden born said:**
> Thanks again ill check Deluge out.  

Right now i use transmission it has always felt like it was lacking in features.

I also think Transmission lacks features. Deluge is much more complete, but it is easy to configure.

---

### Post by Alden born on 2009-06-02
> **HermanAB said:**
> Hmm...
chrootkit - useless, waste of time.
AVG - good for scanning Windows files, so run it on the Windows VM. Alternatively use ClamWin.
Firestarter - Deprecated, use UFW instead.

Do activate Window Firewall on the Windows VM.

I'm not talking about a windows VM.  I talking about other windows machines on my network.

---

### Post by Alden born on 2009-06-02
> **lovinglinux said:**
> chrootkit - I use rkhunter, which also check if important files have been changed

AVG -  doesn't remove or clean infected files and as far as I know, it doesn't have a GUI. Use [BitDefender](https://help.ubuntu.com/community/BitDefender) instead, which scans fast, has a nice gui, has integration with Nautilus and a nice drop-box.

Firestarter - Deprecated, use UFW instead and Gufw for graphical interface. UFW is installed by default. You can install the gui by searching for "Firewall Configuration" in the "Add/Remove manager".

Some things you should know:

[list][*] Anti-virus is useful if you have Windows on your network, because they don't scan Linux virus, since there aren't any in the wild.
[*] 
[*] Firestarter and UFW/GUFW are just firewall managers, which means they allow you to create rules for iptables (the real firewall) without knowing the commands. You don't need them if you know the iptables commands. 
[*] 
[*] Iptables are installed by default and activated at boot, but they allow all traffic by default. Since Ubuntu doesn't come with any services running by default, then you don't need the firewall. If you install services, then you might want to use a firewall to restrict access to the open ports.
[*] 
[*] Most people coming from Windows like Firestarter because of the connection monitoring feature, but you shouldn't be running it all the time, due to security risks of it's root requirements. Besides, you don't have to run it all the time to be protected, since iptables runs in the background.
[*] 
[*] UFW doesn't have a monitoring tool. You can use use another tool like [IPTstate](http://ubuntuforums.org/showpost.php?p=7331295&postcount=8) for that
[*] 
[*] If you have a router with firewall capabilities, then you probably don't need to activate the firewall on Ubuntu.
[*] 
[*] If you use p2p programs, you might want to use [moblock](http://moblock-deb.sourceforge.net/) or [iplist](http://iplist.sourceforge.net/).[/list]


*UKeywords: 649167 firestarter ufw gufw avg bitdefender rkhunter iptables firewall june 2009*


What exactly do you mean by services? And i also thought that Ubuntu ships with no open ports. Does transmission count as a service?

You where right about avg and clamAV does the same as well.  Also is bit defender free it looks like you have to pay for it? 

thanks again.

---

### Post by lovinglinux on 2009-06-02
> **Alden born said:**
> What exactly do you mean by services?

Services are programs that listen to ports for remote connections requests, like a web server or a torrent client. If you don't have services running, then all ports are essentially closed and you don't need a firewall. Other computers might reach you through your IP, but then won't be able to do anything, because there aren't any programs accepting connections on any port.

> **Alden born said:**
> and do you know if ClamAV removes viruses?

I think so, but my experience with Clam was really short. I didn't like it.

> **Alden born said:**
> Also i bitdefender free i look like you have to pay for it?

It's free for personal use. You have to request a free registration key from their web site.

> **Alden born said:**
> And i also thought that Ubuntu ships with no open ports

Yes, you are correct. Ubuntu comes with no listening services, so all ports are closed by default.

---

### Post by Alden born on 2009-06-05
Hey one more question.  

Does Bitdefender (Linux Version) remove the virus once it finds them?

---

### Post by lovinglinux on 2009-06-05
> **Alden born said:**
> Hey one more question.  

Does Bitdefender (Linux Version) remove the virus once it finds them?

Yes, it provides options to disinfect, quarantine or delete the file.

---

