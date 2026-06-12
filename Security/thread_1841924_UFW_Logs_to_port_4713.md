---
title: "UFW Logs to port 4713"
date: 2011-09-10
forum: Security
---

### Post by SparTacux on 2011-09-10
I am currently running a small home network with several PC/Laptops using UBUNTU 10.4 LTS. I had a bit of a network dip yesterday about 8.48pm and lost the network connection on a laptop that is used to record my SYSLOG log from my modem/router. My UFW firewall logs on the laptop showed some loopback connections destined for port 4713 at the time the network went down. 

All computers are set to deny all incoming traffic and allow all outgoing traffic with the exception that ports 514 ( SYSLOG ) , 631 ( IPP ) , 161 ( SNMP ) and 5353 (MDNS ) are allowed in. I am sharing a printer on this laptop that uses IPP so the other computers on my network can connect to it. Anybody have any ideas what port 4713 is used for and why did it generate that traffic when the network went down?

I did a search through my UFW logs on another PC and also found references to Destination port 4713 on quite a few different occasions as well as yesterday. All show SRC=127.0.0.1  DST 127.0.0.1 with references to MAC 00:00:00:00:00:00.

Second question - Do I need MDNS ( 5353 ) and SNMP ( 161 ) to run a shared printer. Does anyone know any security issues with these services - particularly MDNS.

Ta for your help

---

### Post by haqking on 2011-09-10
> **SparTacux said:**
> I am currently running a small home network with several PC/Laptops using UBUNTU 10.4 LTS. I had a bit of a network dip yesterday about 8.48pm and lost the network connection on a laptop that is used to record my SYSLOG log from my modem/router. My UFW firewall logs on the laptop showed some loopback connections destined for port 4713 at the time the network went down. 

All computers are set to deny all incoming traffic and allow all outgoing traffic with the exception that ports 514 ( SYSLOG ) , 631 ( IPP ) , 161 ( SNMP ) and 5353 (MDNS ) are allowed in. I am sharing a printer on this laptop that uses IPP so the other computers on my network can connect to it. Anybody have any ideas what port 4713 is used for and why did it generate that traffic when the network went down?

I did a search through my UFW logs on another PC and also found references to Destination port 4713 on quite a few different occasions as well as yesterday. All show SRC=127.0.0.1  DST 127.0.0.1 with references to MAC 00:00:00:00:00:00.

Second question - Do I need MDNS ( 5353 ) and SNMP ( 161 ) to run a shared printer. Does anyone know any security issues with these services - particularly MDNS.

Ta for your help

4713 is your Pulseaudio daemon.

And using your router should be enough to protect your network instead of UFW on all your machines.

You only really need additional firewall protection on a internet facing server with linux

---

### Post by hydruid on 2011-09-10
it wouldn't hurt to make sure that your router isn't pingable from the internet

---

### Post by SparTacux on 2011-09-10
> **haqking said:**
> 4713 is your Pulseaudio daemon.

And using your router should be enough to protect your network instead of UFW on all your machines.

You only really need additional firewall protection on a internet facing server with linux


Thanks for the info. Should I be blocking Pusleaudio attempting to access the network? 

As far as using UFW on all machines - call it an exercise in understanding network traffic. I have the logs set to high so as I can see what is happening on my network.  My modem router has an internet facing firewall. I was working on the assumption that an internal PC on my network could get compromised via dodgy updates or whatever - then attack ( or observe ) the rest of my network from the inside. I do connect some windows machines to the network every now and then.

---

### Post by haqking on 2011-09-10
> **SparTacux said:**
> Thanks for the info. Should I be blocking Pusleaudio attempting to access the network? 

As far as using UFW on all machines - call it an exercise in understanding network traffic. I have the logs set to high so as I can see what is happening on my network.  My modem router has an internet facing firewall. I was working on the assumption that an internal PC on my network could get compromised via dodgy updates or whatever - then attack ( or observe ) the rest of my network from the inside. I do connect some windows machines to the network every now and then.


a better exercise would be to use a packet analyser such as wireshark this will give you a far better view of network traffic and what is happening.

On Linux all ports are closed by default with no services listening on them unless you open such services.

---

### Post by SparTacux on 2011-09-10
> **haqking said:**
> a better exercise would be to use a packet analyser such as wireshark this will give you a far better view of network traffic and what is happening.

On Linux all ports are closed by default with no services listening on them unless you open such services.


Yeah I know - I'm getting there - give me another couple of years or so :-)

I'm not that tech savvy these days - I don't really have the time to learn the stuff but as you say it looks like I should be using Wireshark. I've been the target of quite a lot of hacking ( DON"T GO THERE &  DON"T ASK ! ) and it's a case of having to learn as opposed of wanting to learn.

---

### Post by SparTacux on 2011-09-11
I did a bit of homework on Pulseaudio & found several references to vulnerabilities using it. My understanding is that if you remove Pulse Audio then your sound system will not work anymore?

Title: PulseAudio setuid Local Privilege Escalation Vulnerability
Severity: HIGH
Description:

PulseAudio is a sound server available for various platforms.

PulseAudio is prone to a local privilege-escalation vulnerability because it fails to drop privileges after being installed setuid root and preserves the setuid bit if a hard link is created.

The application checks the 'LD_BIND_NOW' environment variable and if it isn't set, it sets variable and then reloads. The application then determines its path name by examining the '/proc/self/exe' symbolic link that points to the complete path name of the current process (such as '/usr/bin/pulseaudio'), but this can be modified by creating a hard link.

The application's reload functionality is affected by a race-condition vulnerability. An attacker can create a hard link pointing to the PulseAudio binary, wait for the PulseAudio binary to be executed, and then replace the hard link with a different file or symbolic link before the application reloads. This will cause the attacker's file to run with superuser privileges, resulting in a complete compromise of affected computers.

********************************************

I guessing you don't need the AVAHI Daemon & MDNS on your network - it's just to make locating network services easier. It seems earlier versions of Ubuntu didn't have this installed by default due to potential vulnerabilities. Apparently an unpatched 10.04 LTS system is affected by a vulnerabilty

******************************************

Ubuntu Security Notice USN-992-1

29th September, 2010
avahi vulnerabilities

A security issue affects these releases of Ubuntu and its derivatives:

    * Ubuntu 10.04 LTS
    * Ubuntu 9.10
    * Ubuntu 9.04
    * Ubuntu 8.04 LTS

Software description

    * avahi

Details

It was discovered that Avahi incorrectly handled certain mDNS query packets
when the reflector feature is enabled, which is not the default
configuration on Ubuntu. A remote attacker could send crafted mDNS queries
and perform a denial of service on the server and on the network. This
issue only affected Ubuntu 8.04 LTS and 9.04. (CVE-2009-0758)

It was discovered that Avahi incorrectly handled mDNS packets with
corrupted checksums. A remote attacker could send crafted mDNS packets and
cause Avahi to crash, resulting in a denial of service. (CVE-2010-2244)

---

### Post by haqking on 2011-09-11
> **SparTacux said:**
> I did a bit of homework on Pulseaudio & found several references to vulnerabilities using it. My understanding is that if you remove Pulse Audio then your sound system will not work anymore?

Title: PulseAudio setuid Local Privilege Escalation Vulnerability
Severity: HIGH
Description:

PulseAudio is a sound server available for various platforms.

PulseAudio is prone to a local privilege-escalation vulnerability because it fails to drop privileges after being installed setuid root and preserves the setuid bit if a hard link is created.

The application checks the 'LD_BIND_NOW' environment variable and if it isn't set, it sets variable and then reloads. The application then determines its path name by examining the '/proc/self/exe' symbolic link that points to the complete path name of the current process (such as '/usr/bin/pulseaudio'), but this can be modified by creating a hard link.

The application's reload functionality is affected by a race-condition vulnerability. An attacker can create a hard link pointing to the PulseAudio binary, wait for the PulseAudio binary to be executed, and then replace the hard link with a different file or symbolic link before the application reloads. This will cause the attacker's file to run with superuser privileges, resulting in a complete compromise of affected computers.

********************************************

I guessing you don't need the AVAHI Daemon & MDNS on your network - it's just to make locating network services easier. It seems earlier versions of Ubuntu didn't have this installed by default due to potential vulnerabilities. Apparently an unpatched 10.04 LTS system is affected by a vulnerabilty

******************************************

Ubuntu Security Notice USN-992-1

29th September, 2010
avahi vulnerabilities

A security issue affects these releases of Ubuntu and its derivatives:

    * Ubuntu 10.04 LTS
    * Ubuntu 9.10
    * Ubuntu 9.04
    * Ubuntu 8.04 LTS

Software description

    * avahi

Details

It was discovered that Avahi incorrectly handled certain mDNS query packets
when the reflector feature is enabled, which is not the default
configuration on Ubuntu. A remote attacker could send crafted mDNS queries
and perform a denial of service on the server and on the network. This
issue only affected Ubuntu 8.04 LTS and 9.04. (CVE-2009-0758)

It was discovered that Avahi incorrectly handled mDNS packets with
corrupted checksums. A remote attacker could send crafted mDNS packets and
cause Avahi to crash, resulting in a denial of service. (CVE-2010-2244)


Avahi is linux version of APIPA in windows for zeroconfig and obtaining an IP address without DHCP server etc.

depending on your version you can disable it it GUI or from CLI.

sudo gedit /etc/default/avahi-daemon

Change the line:AVAHI_DAEMON_START = 1

to: AVAHI_DAEMON_START = 0 
   
But this may not exist.

---

### Post by SparTacux on 2011-09-13
> **haqking said:**
> Avahi is linux version of APIPA in windows for zeroconfig and obtaining an IP address without DHCP server etc.

depending on your version you can disable it it GUI or from CLI.

sudo gedit /etc/default/avahi-daemon

Change the line:AVAHI_DAEMON_START = 1

to: AVAHI_DAEMON_START = 0 
   
But this may not exist.

 Or remove it using packet manager ;-)  I spotted those references to Destination 224.0.0.251 on port 5353 in my UFW logs. I take it these are a broadcast message.

---

### Post by haqking on 2011-09-13
> **SparTacux said:**
> Or remove it using packet manager ;-)  I spotted those references to Destination 224.0.0.251 on port 5353 in my UFW logs. I take it these are a broadcast message.

preferrable to disable a service before removing.

You never know the real effect with a network service.

---

### Post by Ibidem on 2011-09-16
On Ubuntu, quite a few ports are open by default.

Avahi-daemon is needed for network printers (well maybe you could get around it, but...).  That's about all, though.  
It's worse than you'd guess: mDNS, the standard it implements, requires behavior that is inherently insecure.

Pulseaudio is not required for sound.  It runs on top of Alsa or OSS; the Pulseaudio servers can be removed easily (and are the main security problem), but removing libpulse requires losing most of the multimedia stuff.
That said, Pulseaudio does let you use more than 1-2 sound programs at once, with per-application volumes (so does OSS4 :-P), and also adds some sound devices.

---

### Post by SparTacux on 2011-09-16
I reckon I can get rid of mdns. 

I'm using static IP's - I guess I can set up each computer to point to the shared printer using IPP on it's own. mdns looks a little risky to me plus it's causing more network traffic than I need. I had quite a bit of traffic on port 631 too which was broadcasting as well as broadcasts on 5353. The result was that I 'seemed' to be losing packets from my SYSLOG which was coming from my router and the output on the SYSLOG was corrupted every now and then.

I might try removing pulse audio and see what happens as an experiment. I had one of my log files complain about rate limits being exceeded and several events supressed from pulsaudio.

---

### Post by SparTacux on 2011-09-16
Thanks for your input guys - You've given me a few things to think about :-) I'll leave the thread open just in case someone else wants to  add to it.

---

