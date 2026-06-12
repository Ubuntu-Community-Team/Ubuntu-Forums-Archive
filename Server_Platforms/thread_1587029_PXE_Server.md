---
title: "PXE Server"
date: 2010-10-02
forum: Server Platforms
---

### Post by Z.K. on 2010-10-02
I am trying to setup a PXE Server using the tutorial at [http://ubuntuforums.org/showthread.php?p=9918189#post9918189]("http://ubuntuforums.org/showthread.php?p=9918189#post9918189") but I get a dhcp error failed message.

Since I already have a dhcp server in my router, could this be the problem or is it something entirely different?  The error message I get is:

```


Setting up dhcp3-server (3.1.3-2ubuntu3) ...
Generating /etc/default/dhcp3-server...
 * Starting DHCP server 
dhcpd3
                                                   
* check syslog for diagnostics. 
                                                              [fail]
invoke-rc.d: initscript dhcp3-server, action "start" failed.


```


:confused:

---

### Post by gobbledigook on 2010-10-02
if you have a router giving out dhcp then it won't work unless you make the server give out dhcp.... or if you have the ability on your router to set dnsmasq options you can add a rule to forward the pxe to the server... see [here ]("http://www.dd-wrt.com/wiki/index.php/PXE")on the DD-WRT wiki

---

### Post by koenn on 2010-10-03
check syslog for diagnostics. 

translation : the reason your dhcp server fails to start is probably mentioned in the log file. 

try ```
grep dhcp /var/log/syslog
``` or so


your serbver most likely doesn't care whether your router is doing dhcp, but you will run into all sorts of trouble with two dhcp servers on the same network segment, especially when one of the is expected to give out pxe info.
you'll need to fix that too.

---

### Post by Z.K. on 2010-10-04
Thanks for the suggestions.  I managed to get the dhcp server working and when I boot my client it is assigned an ip address in the range I specified in the dhcpd.conf file.  But now it fails with the tftp.  It just sits there forever and does not do much until it finally boots to the hard drive.

Anyone have any suggestions.  I checked and it looks as if the tftp is up and running.  I set up the /tftpboot/ directory according to a couple of tutorials I found, but still nothing.

:confused:

---

### Post by koenn on 2010-10-04
again, check the logs, see what your tftp server is doing exactly, and whether it complains about something.

here's a short write up of some PXE stuff i once did, 
you might find it helpfull

---

### Post by Z.K. on 2010-10-05
> **koenn said:**
> again, check the logs, see what your tftp server is doing exactly, and whether it complains about something.

here's a short write up of some PXE stuff i once did, 
you might find it helpfull

What write up? 

Here is the pertinent output of the syslog:

Oct  4 22:00:25 print-server dhcpd: DHCPINFORM from 192.168.0.16 via eth0
Oct  4 22:00:25 print-server dhcpd: DHCPACK to 192.168.0.16 (00:26:18:e1:76:35) via eth0
Oct  4 22:02:57 print-server dhcpd: DHCPDISCOVER from 00:1a:4d:4e:a4:b7 via eth0
Oct  4 22:02:58 print-server dhcpd: DHCPOFFER on 192.168.0.101 to 00:1a:4d:4e:a4:b7 via eth0
Oct  4 22:02:59 print-server dhcpd: DHCPREQUEST for 192.168.0.101 (192.168.0.2) from 00:1a:4d:4e:a4:b7 via eth0
Oct  4 22:02:59 print-server dhcpd: DHCPACK on 192.168.0.101 to 00:1a:4d:4e:a4:b7 via eth0

It is all dhcp related.  Should there not be something about the tftp?

---

### Post by BobVila on 2010-10-05
> **Z.K. said:**
> What write up? 

Here is the pertinent output of the syslog:

Oct  4 22:00:25 print-server dhcpd: DHCPINFORM from 192.168.0.16 via eth0
Oct  4 22:00:25 print-server dhcpd: DHCPACK to 192.168.0.16 (00:26:18:e1:76:35) via eth0
Oct  4 22:02:57 print-server dhcpd: DHCPDISCOVER from 00:1a:4d:4e:a4:b7 via eth0
Oct  4 22:02:58 print-server dhcpd: DHCPOFFER on 192.168.0.101 to 00:1a:4d:4e:a4:b7 via eth0
Oct  4 22:02:59 print-server dhcpd: DHCPREQUEST for 192.168.0.101 (192.168.0.2) from 00:1a:4d:4e:a4:b7 via eth0
Oct  4 22:02:59 print-server dhcpd: DHCPACK on 192.168.0.101 to 00:1a:4d:4e:a4:b7 via eth0

It is all dhcp related.  Should there not be something about the tftp?

Yes, you should see a series of file requests starting with a really specific file name and then broadening out until it gets a match. Are you sure the tftp service is up?

---

### Post by koenn on 2010-10-05
> **Z.K. said:**
> What write up? 
hm, forgot to paste the link. I must be getting old.
[http://users.telenet.be/mydotcom/howto/linux/diskless01.htm](http://users.telenet.be/mydotcom/howto/linux/diskless01.htm)


> **Z.K. said:**
> 
It is all dhcp related.  Should there not be something about the tftp?
yeah, unless it's not running, or does not log to syslog. 

You mentioned before that "it *looks as if * the tftp is up and running" - now is  the time you want to be sure about that. how did you check and what was the result (post real output) ? 

Also, does your dhcp tells the client what their 'next server' is and what file to look for ? Is that file world readable ? etc. 

look through the write up, it contains what I gathered is the absolute minimum config to get PXE boots working.

---

### Post by Z.K. on 2010-10-10
> **koenn said:**
> hm, forgot to paste the link. I must be getting old.
[http://users.telenet.be/mydotcom/howto/linux/diskless01.htm](http://users.telenet.be/mydotcom/howto/linux/diskless01.htm)



yeah, unless it's not running, or does not log to syslog. 

You mentioned before that "it *looks as if * the tftp is up and running" - now is  the time you want to be sure about that. how did you check and what was the result (post real output) ? 

Also, does your dhcp tells the client what their 'next server' is and what file to look for ? Is that file world readable ? etc. 

look through the write up, it contains what I gathered is the absolute minimum config to get PXE boots working.


I did a netstat -lu and received a line like
udp        0      0 *:tftp                  *:*

which tells me the tftp server is running.

I did not set the next server in the dhcp config file as this is a private network with only the single server.  Do I really need to?

What I have is my DSL connection goes to a wireless router which I disabled the dhcp funtion.  From the router all my PC are connected including the server with a static ip address.  The DHCP is running and my client boots and received its IP address so that part seems to be working, but I never get the menu from the tftp server.

---

### Post by koenn on 2010-10-13
you don't need 'next server' if the tftp is on the same server as the dhcp server, but it never hurts. 

what else did you check after reading that write-up ?

location of the pxelinux.0 and pxelinux.cfg files vs paths in the corresponfing dhcp option ? ownership and permissions of the files ? 

what does that say ?

---

