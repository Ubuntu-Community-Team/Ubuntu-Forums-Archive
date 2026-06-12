---
title: "[SOLVED] Unwanted application network connection"
date: 2008-08-29
forum: Security
---

### Post by lovinglinux on 2008-08-29
Today the firewall registered a network connection attempt, using Samba service. I really don't know what Samba does and if it is part of the OS. In the same log there was another blocked attempt using Microsoft-dt service.

Should I be worried? Could someone explain what is Samba and why it is trying to connect to the outside world?

Since Microsoft related service is involved I guess it was an application that was running through Wine.

---

### Post by hyper_ch on 2008-08-29
> **lovinglinux said:**
> Could someone explain what is Samba and why it is trying to connect to the outside world?

Did you try to find out yourself what samba is?

---

### Post by cdenley on 2008-08-29
> **lovinglinux said:**
> Today the firewall registered a network connection attempt, using Samba service. I really don't know what Samba does and if it is part of the OS. In the same log there was another blocked attempt using Microsoft-dt service.

Should I be worried? Could someone explain what is Samba and why it is trying to connect to the outside world?

Since Microsoft related service is involved I guess it was an application that was running through Wine.

Are you sure it was your system trying to connect to the outside world? More likely it was someone trying to connect to you, hoping you have an insecure windows operating system. Most firewall configurations in linux don't filter outgoing connections.

---

### Post by lovinglinux on 2008-08-29
> **hyper_ch said:**
> Did you try to find out yourself what samba is?

Yes. I'm not lazy.

> 
Samba is a free software re-implementation of SMB/CIFS networking protocol, originally developed by Australian Andrew Tridgell. Samba is released under the GNU General Public License. The name Samba comes from SMB (Server Message Block), the name of the standard protocol used by the Microsoft Windows network file system.

As of version 3 Samba provides file and print services for various Microsoft Windows clients and can integrate with a Windows Server domain, either as a Primary Domain Controller (PDC) or as a domain member. It can also be part of an Active Directory domain. Samba runs on most Unix and Unix-like systems, such as Linux, Solaris, AIX and the BSD variants, including Apple's Mac OS X Server (which was added to the Mac OS X client in version 10.2). Samba is standard on nearly all distributions of Linux and is commonly included as a basic system service on other Unix-based operating systems as well.

But this doesn't explain why it was loaded, if it was loaded by Wine or by Linux and why it is trying to connect to the outside.

> **cdenley said:**
> Are you sure it was your system trying to connect to the outside world? More likely it was someone trying to connect to you, hoping you have an insecure windows operating system. Most firewall configurations in linux don't filter outgoing connections.

Yes, I'm sure. I'm a former paranoid Windows user, so I have limited outbound connection configuration in the firewall (allow only HTTP, HTTPS and FTP ports) and IP filtering using blocklists. I don't remember which port Samba was using or the protocol, but I imagine the connection was blocked by the IP filter.

---

### Post by brian_p on 2008-08-29
> **lovinglinux said:**
> 

But this doesn't explain why it was loaded, if it was loaded by Wine or by Linux and why it is trying to connect to the outside.


What are the outputs from

```
dpkg -l | grep samba
```

and

```
dpkg -l | grep smb
```

---

### Post by cdenley on 2008-08-29
A standard ubuntu desktop install includes a samba client. However, I wouldn't expect any traffic on ports used by samba unless you are attempting to connect to a samba/windows server. Perhaps you were installing a printer, and it was looking for printers shared from windows hosts.

It was probably identified as a microsoft service only because of the port it was using. It isn't necessarily something running in wine.

---

### Post by lovinglinux on 2008-08-29
> **brian_p said:**
> What are the outputs from

```
dpkg -l | grep samba
```

```
ii  samba-common                               3.0.28a-1ubuntu4.4                                   Samba common files used by both the server a
```

> **brian_p said:**
> and

```
dpkg -l | grep smb
```

```
ii  libsmbclient                               3.0.28a-1ubuntu4.4                                   shared library that allows applications to t
ii  libsmbios1                                 0.13.10-1ubuntu1.1                                   Provide access to (SM)BIOS information -- dy
ii  smbclient                                  3.0.28a-1ubuntu4.4                                   a LanManager-like simple client for Unix
```

> **cdenley said:**
> A standard ubuntu desktop install includes a samba client. However, I wouldn't expect any traffic on ports used by samba unless you are attempting to connect to a samba/windows server. Perhaps you were installing a printer, and it was looking for printers shared from windows hosts.

It was probably identified as a microsoft service only because of the port it was using. It isn't necessarily something running in wine.

I don't have a printer installed. I have a Ultra@VNC installed under Wine to access a Windows notebook in the network, but I do not share any folder, driver, printer or anything else. The notebook is connected to the network via wireless router, which has WEP protection and restricted access using limited amount of IP number assignments in the DHCP configuration, plus MAC address access filter. The notebook was disconnected when this happened.

---

### Post by lovinglinux on 2008-08-30
It happened again. Now I know the ports.

SAMBA outgoing port 137 protocol UDP destination 192.168.2.255
SAMBA outgoing port 139 protocol TCP destination smartbrowsesandvine.terra.com
Microsoft-ds  outgoing port 445 protocol TCP destination smartbrowsesandvine.terra.com

My ISP provider is [www.terra.com.br](www.terra.com.br), but the domain terra.com is not in my country. The IP contacted is not the ones for DNS and the pppoe authentication is performed by the router.

---

### Post by lovinglinux on 2008-09-03
I think this is due to last.fm player. I reinstalled Ubuntu and Networks Servers weren't available until I installed the last.fm app.

Is it possible that last.fm is trying to send the so called scrobbling info?

---

### Post by thesurgeon on 2008-09-03
Heres some information about Samba, the port numbers and the domain name you provided. Hope it helps some in your investigation.

[http://en.wikipedia.org/wiki/Samba_(software](http://en.wikipedia.org/wiki/Samba_(software))

137, 139 and 445 are for windows file and printer sharing.

Port:
139

Name:  
netbios-ssn
 
Purpose:  
NETBIOS Session Service
 
Description:  
TCP NetBIOS connections are made over this port, usually with Windows machines but also with any other system running Samba (SMB). These TCP connections form "NetBIOS sessions" to support connection oriented file sharing activities. 


Port:
137

Name:  
netbios-ns
 
Purpose:  
NetBIOS Name Service
 
Description:  
UDP NetBIOS name query packets are sent to this port, usually of Windows machines but also of any other system running Samba (SMB), to ask the receiving machine to disclose and return its current set of NetBIOS names. 

Port:
445

ame:  
microsoft-ds
 
Purpose:  
Microsoft Directory Services
 
Description:  
This port replaces the notorious Windows NetBIOS trio (ports 137-139), for all versions of Windows after NT, as the preferred port for carrying Windows file sharing and numerous other services.


Is someone from the ISP terra.com not connecting to file shares on your machine?

heres the email to report abuse or even just ask why they are connected on those ports to your network or your local machine. [email]abuse@terra.com[/email]

I found an email address also for this domain [email]thiago@smartbrowsesandvine.terra.com[/email] which comes from a site 

[http://translate.google.co.uk/translate?hl=en&sl=pt&u=http://freehg.org/u/tfmoraes/dotfiles/log/&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3Dsmartbrowsesandvine%26hl%3Den%26safe%3Doff](http://translate.google.co.uk/translate?hl=en&sl=pt&u=http://freehg.org/u/tfmoraes/dotfiles/log/&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3Dsmartbrowsesandvine%26hl%3Den%26safe%3Doff)

I've done a few different checks but nothing really comes back for that full  domain name. So the only person I could find is that thiago dude, you could try him...

terra.com is a Madrid ISP

who ever thiago is he gos on freehg.org for developer code to do with Ubuntu so you do the maths.

He uses Ubuntu, you use Ubuntu...hes a developer...if its him that is...again hes the only person I can find connected to that domain name.

The 192.168.2.255 is a broadcast address which is for your internal network.

the following link explains a broadcast address 

[http://en.wikipedia.org/wiki/Broadcast_address](http://en.wikipedia.org/wiki/Broadcast_address)

---

### Post by lovinglinux on 2008-09-04
> **thesurgeon said:**
> Heres some information about Samba, the port numbers and the domain name you provided. Hope it helps some in your investigation.

[http://en.wikipedia.org/wiki/Samba_(software](http://en.wikipedia.org/wiki/Samba_(software))

137, 139 and 445 are for windows file and printer sharing.

Port:
139

Name:  
netbios-ssn
 
Purpose:  
NETBIOS Session Service
 
Description:  
TCP NetBIOS connections are made over this port, usually with Windows machines but also with any other system running Samba (SMB). These TCP connections form "NetBIOS sessions" to support connection oriented file sharing activities. 


Port:
137

Name:  
netbios-ns
 
Purpose:  
NetBIOS Name Service
 
Description:  
UDP NetBIOS name query packets are sent to this port, usually of Windows machines but also of any other system running Samba (SMB), to ask the receiving machine to disclose and return its current set of NetBIOS names. 

Port:
445

ame:  
microsoft-ds
 
Purpose:  
Microsoft Directory Services
 
Description:  
This port replaces the notorious Windows NetBIOS trio (ports 137-139), for all versions of Windows after NT, as the preferred port for carrying Windows file sharing and numerous other services.


Is someone from the ISP terra.com not connecting to file shares on your machine?

heres the email to report abuse or even just ask why they are connected on those ports to your network or your local machine. [email]abuse@terra.com[/email]

I found an email address also for this domain [email]thiago@smartbrowsesandvine.terra.com[/email] which comes from a site 

[http://translate.google.co.uk/translate?hl=en&sl=pt&u=http://freehg.org/u/tfmoraes/dotfiles/log/&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3Dsmartbrowsesandvine%26hl%3Den%26safe%3Doff](http://translate.google.co.uk/translate?hl=en&sl=pt&u=http://freehg.org/u/tfmoraes/dotfiles/log/&sa=X&oi=translate&resnum=4&ct=result&prev=/search%3Fq%3Dsmartbrowsesandvine%26hl%3Den%26safe%3Doff)

I've done a few different checks but nothing really comes back for that full  domain name. So the only person I could find is that thiago dude, you could try him...

terra.com is a Madrid ISP

who ever thiago is he gos on freehg.org for developer code to do with Ubuntu so you do the maths.

He uses Ubuntu, you use Ubuntu...hes a developer...if its him that is...again hes the only person I can find connected to that domain name.

The 192.168.2.255 is a broadcast address which is for your internal network.

the following link explains a broadcast address 

[http://en.wikipedia.org/wiki/Broadcast_address](http://en.wikipedia.org/wiki/Broadcast_address)

Thank you very much for spending time researching this. 

I don't share folders, printers or anything else, that is why I'm a little bit paranoid. I will contact that thiago if this issue persists.

---

### Post by lovinglinux on 2008-09-13
Apparently, the connection to that host only happens when I hit the Network Servers icon in the file browser.

I will set this thread as solved, because I know what is generating the outbound connection, but if someone knows why it is trying to connect the specific address mentioned before, please let me know.

---

