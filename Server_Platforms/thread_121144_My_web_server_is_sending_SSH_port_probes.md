---
title: "My web server is sending SSH port probes"
date: 2006-01-24
forum: Server Platforms
---

### Post by jeff.bjarke on 2006-01-24
Hi, maybe someone here can help, or at least send me in the right direction.
I received an email this morning informing me that the server I run at school has been compromised. This link 
[http://www.mynetwatchman.com/LID.asp?IID=185827814]("http://www.mynetwatchman.com/LID.asp?IID=185827814")
goes to the  mynetwatchman incident report if it helps.

I need to point out that I am an economics grad student, have some little linux experience, and maintain this server for my department to run web surveys on, so I don't know much about linux security.  The services I need to run are apache, php 5, and mysql.  So those have to stay.  I am also running ssh so that I can remotely connect.  This is running on breezy badger, and I just ran apt-get upgrade yesterday.

Thanks,
Jeff :confused: :confused:

---

### Post by LordHunter317 on 2006-01-24
I don't see how you can conclude that from that incident report.

---

### Post by jeff.bjarke on 2006-01-24
Here is the text of the original email I got from campus computing this morning.  Maybe it will shed some more light on things. Again, I'm fairly green at this, so I'm going by what the campus computing folks are telling me.

Thanks,
Jeff

"Hello,

It appears that your host, quaero.unm.edu, has been compromised, and is attacking other computers outside of UNM's network.  Please investigate and take appropriate action.  The logs below indicate the nature of the attack.

Thanks,
<admin guy>
---------- Forwarded message ----------
Date: Tue, 24 Jan 2006 00:40:00 -0400
From: myNetWatchman <updatestatusonly@mynetwatchman.com>
To: [email]INTSEC-L@LIST.UNM.EDU[/email]
Subject: [INTSEC-L] myNetWatchman Incident [185827814] Src:(129.24.90.54)
    Targets:3

myNetWatchman Incident [185827814] Src:(129.24.90.54) Targets:3


FYI,

Based on multiple reports from myNetWatchman users, we believe that the
following host is compromised or infected:

Source IP: 129.24.90.54 LastEvent: 24 Jan 2006 05:04:43 UTC
Time Zone: UTC

Event Date Time, Destination IP, IP Protocol, Target Port, Issue Description, Source Port, Event Count
EventRecord: 24 Jan 2006 05:04:43, 24.16.x.x, 6, 22, SSH Probe, 37888, 2
EventRecord: 24 Jan 2006 04:31:30, 24.11.x.x, 6, 22, SSH Probe, 45371, 1
EventRecord: 24 Jan 2006 04:01:31, 24.11.x.x, 6, 22, SSH Probe, 45371, 1
EventRecord: 24 Jan 2006 02:30:58, 24.6.x.x, 6, 22, SSH Probe, 44878, 1


Click here to get further details regarding this incident:
[http://www.mynetwatchman.com/LID.asp?IID=185827814](http://www.mynetwatchman.com/LID.asp?IID=185827814)

If you are running Windows, see our lockdown
and disinfection guide:
See: [http://www.mynetwatchman.com/kb/security/disinfect.htm](http://www.mynetwatchman.com/kb/security/disinfect.htm)



If you have any questions, feel free to contact me.

IMPORTANT: All replies to this e-mail are automatically posted
to a PUBLICLY viewable incident status.

If possible, please use the following URL to update incident status:

[http://www.mynetwatchman.com/UI.asp?IID=185827814&CD=23Jan200621:36:03](http://www.mynetwatchman.com/UI.asp?IID=185827814&CD=23Jan200621:36:03)

This allows us to efficiently communicate incident status to all interested
parties and minimizes the number of complaints you receive directly.

Please send PRIVATE communications to: [email]support@mynetwatchman.com[/email]
Regards,

Lawrence Baldwin
Chief Forensics Officer
[http://www.myNetWatchman.com](http://www.myNetWatchman.com)
The Internet Neighborhood Watch
Atlanta, Georgia USA
"

---

### Post by MJN on 2006-01-25
Given that these 'probes' have all been using UDP it opens up the possibility that your address has been spoofed and thus your machine has not been compromised and indeed had nothing to do with it.
 
This of course raises the question why would anyone spoof a source address using UDP whilst probing the SSH port? This after all would result in any ICMP response from a closed port not being not reaching the 'attacker'. Well, a common reason for this is that the attacker is attempting to cloak his relatively-few-in-number TCP probes in a sea of spoofed UDP packets and hence decreasing the ability for a intrusion detection system to spot an attack 'signature'. Not a particularly effective technique these days but then the actions of script kiddies often aren't.
 
This is just a potential theory and can in no way mean you can assume your machine is necessarilly safe - you need to investigate your own logs, those of your Internet connection and your security policy in general to see if these UDP packets really did could come from your machine.
 
At the very least if you can block outgoing connections on port 22 (assuming you don't need it open) then you can see if these probes still get reported.
 
Mathew

---

### Post by tcwitte on 2006-01-25
I would indeed look at the logs of especially SSH to check whether someone broke in. Maybe /etc/ssh/sshd_config allows empty passwords or some password on the box was bad. (It's best to always disable password logins and only use keys because that way people can't just guess a password and gain access to the server.) You mention PHP; if it's not in safe mode an unsafe script can allow someone else to probe from your machine without breaking in any further.

---

### Post by imagine on 2006-01-28
[QUOTE=MJN]Given that these 'probes' have all been using UDP[/QUOTE]Umm, what leads you to the conclusion UDP was used?
[http://www.iana.org/assignments/protocol-numbers](http://www.iana.org/assignments/protocol-numbers)



It could be very well that the system has been compromised and is now used as a bot to attack other systems.
First action should be to disconnect the system from the network and then audit it, best from a Live-CD. Check the logs, user accounts, last logins, scan for rootkits, etc. If there's evidence that the system has been indeed compromised you should find out how that happened (eg account with an insecure password / unpatched vulnerability in LAMP) and then reinstall the complete system.

Since I never heard of mynetwatchman I can't tell if their reports are reliable.

---

### Post by MJN on 2006-01-29
I'm not sure where I got that they were UDP from... it certainly wasn't anything related to the port number however I can't find any reference on the URLs so I think I must've got confused somewhere (wouldn't be the first time...).

Mathew

---

