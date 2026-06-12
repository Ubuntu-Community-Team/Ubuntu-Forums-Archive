---
title: "Set Up ubuntu 12.04 as file server"
date: 2012-05-15
forum: Server Platforms
---

### Post by eraven6 on 2012-05-15
Hello all. I have Ubuntu 12.04 and I want to set up a file server in my office. I have several ubuntu box and win box here. I've read some tutorial out there and I confused with the setup. All i know is I need a samba. Some of the tutorial said that I need a winbind but some of them do not include winbind in their tutorial.

so, can someone give me a checklist item for fileserver installation? or some tutorial please? Thanks. Sorry for my bad English

---

### Post by RAND0M1ZER on 2012-05-15
Here's a good one:

[http://rbgeek.wordpress.com/2012/04/25/how-to-install-samba-server-on-ubuntu-12-04/](http://rbgeek.wordpress.com/2012/04/25/how-to-install-samba-server-on-ubuntu-12-04/)

---

### Post by eraven6 on 2012-05-15
ok, thanks for the tutorial and it works. Now I want to make the Ubuntu as the domain controller, sothe other win box and ubuntu can join domain. Is it related with samba too? I've tried to search it too, and still confused about the configuration. Do you have some other tutorial for setting up ubuntu as domain controller? 

The last time I tried, when I tried to join domain from my win box, I got the following error:
the specified domain either does not exist or could not be contacted. 

what is the problem?

---

### Post by HermanAB on 2012-05-16
Howdy,

I would keep it simple for starters.

You don't really NEED a domain controller.  A network with up to about 30 users can be easily managed without.  All that a domain controller does, is it centralizes the configuration so that you don't need to walk around from machine to machine to set the user names and passwords.  So you need to have so many users that the pain of the head-ache from administering the domain controller itself is outweighed by the reduced pain in your feet.

---

### Post by bubylou on 2012-05-16
Try using the official Ubuntu documentation for windows networking.
[https://help.ubuntu.com/12.04/serverguide/windows-networking.html](https://help.ubuntu.com/12.04/serverguide/windows-networking.html)

---

### Post by LHammonds on 2012-05-16
You might want to look at [Zentyal]("http://www.zentyal.org/") for your solution.  It is built off Ubuntu but tailored to replace the Small Business Server edition of Windows.  You can setup DCs, file / print servers, etc.

You can run much of it on a single server or spread it out over multiple servers if necessary.

LHammonds

---

### Post by eraven6 on 2012-05-17
Thanks for your replies :)

1. Herman AB: Ok, I know that I don't need a domain controller, I've tried to set up file server and it was success. But now my superior wants to set up the Ubuntu (currently 12.04 desktop) as a domain controller in this office. Yes, I need something like if I join domain from winbox, and change my password there, it'll change the password in the server too. I've read some tutorial about it, umm, some of them related to openLDAP. Is it true? I'll give the link below, I hope you can check it and help me about it :)

2. Bubylou: okay, thanks fot the link. I'll try it right now. :)

3. LHammonds: umm, okay thanks about Zentyal, but I a domain controller inside Ubuntu. But thanks for you reply :) I appreciate it

Okay, here they are.. Some of these links about openLDAP? I've tried it but still can't understand. Yes, it is a step by step tutorial, but I'm confused because I don't really understand all the configuration there.. Maybe someone can check it out? ;)

[http://ubuntuforums.org/showthread.php?t=1330637](http://ubuntuforums.org/showthread.php?t=1330637)
[http://ubuntuforums.org/showthread.php?t=1184288](http://ubuntuforums.org/showthread.php?t=1184288)

Ok, waiting for your reply :) Sorry for my bad English.
__

---

### Post by eraven6 on 2012-05-17
Ok, here is some info again. I've tried the configuration in [https://help.ubuntu.com/12.04/serverguide/samba-dc.html](https://help.ubuntu.com/12.04/serverguide/samba-dc.html) to set up ubuntu as PDC. I did all the step except step 8, because I dont have a group in my system right now, so I think I can skip the step. 

I restart the smbd and nmbd and tried to join domain from my winbox. I entered my domain name like the one I wrote on the smb.conf. Then, winbox response with a authentication box. Hmm, so I think the winbox can found my domain. But when I trien to enter the credentials, the respond is: "the following error occured attempting to join the domain "mydomainname":

the specified domain either does not exist or could not be contacted. "

Humm, I don't know what is the problem then? Can someone tell me? Thank you

---

### Post by OO-Dragon on 2012-06-09
Chances are your computer is not pointing to a DNS server that actually has "yourserver" in its records.  You should make the ubuntu machine a DNS server, and make sure it has the records of itself there, and make sure your computers use it as a DNS server... that or add your server in your hosts file on each windows box.

Just to see if its working, instead of entering your server name when joining the domain, just enter its IP address.  If it works that way, then you need to resolve the DNS issue.

** edit **
I thought I would try it out and see, but I'm having the same issue.  Odd...

---

