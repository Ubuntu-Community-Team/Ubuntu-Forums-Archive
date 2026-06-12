---
title: "apache is restarting"
date: 2009-03-22
forum: Server Platforms
---

### Post by haynest on 2009-03-22
Greetings...

I have a recent server install and am getting the following in the logs. It is every eight minutes. Does anyone know where I should look to fix this?

The server is a basic LAMP server/8.10 with EHCP installed to manage virtual hosts.

Thanks...   Tom 


[Sun Mar 22 06:46:19 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sun Mar 22 06:46:19 2009] [notice] Graceful restart requested, doing restart
[Sun Mar 22 06:46:19 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sun Mar 22 06:54:40 2009] [notice] Graceful restart requested, doing restart
[Sun Mar 22 06:54:40 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations
[Sun Mar 22 06:54:40 2009] [notice] Graceful restart requested, doing restart
[Sun Mar 22 06:54:40 2009] [notice] Apache/2.2.9 (Ubuntu) PHP/5.2.6-2ubuntu4.1 with Suhosin-Patch configured -- resuming normal operations

---

### Post by windependence on 2009-03-22
What log file is this? Check your messages and apache error log although this looks like something is requesting a graceful restart. Have you checked your cron tab?

-Tim

---

### Post by haynest on 2009-03-22
This was from apache error.

I checked cron and that is not it. I am really scratching my head here.

It may be related to the EHCP, but I emailed the developer and came up empty.

---

### Post by volkswagner on 2009-03-22
Not very scientific but, if you know the appox. time, run top in a terminal.  Perhaps you can catch the service causing the restart????

---

### Post by haynest on 2009-03-22
heh -The wait and see approach is what I try next. I may be able to snag it. It is at 8 min intervals, so I should not have to wait too long.

---

### Post by windependence on 2009-03-22
What is EHCP? Do you have any other applications on the box?

-Tim

---

### Post by haynest on 2009-03-22
EHCP is Easy Hosting Control Panel. I essentially want to move domains and email from Bluehost to a server at home. I have a business account with the cable company, and I have tried a couple of things on the server so far. Ubuntu 8.10/EHCP is closer to what I am looking for than anything so far. EHCP is rough around the edges though, and it emails info to the developer without asking. 

The apache restart seems to be related to a python script that is always running. I am not the most capable of reading things like this, but it seems that I have ports closed it wants open.

---

### Post by windependence on 2009-03-22
I'm thinking it may be related to EHCP. Have you tried ISPconfig?

Maybe you could shut down EHCP and see what happens.

I'm probably not much help on hosting control panels because all my commercial customers I host on FreeBSD systems with no control panel. I do use Vmware ESXi and Webmin in some places though.

-Tim

---

### Post by haynest on 2009-03-22
I tried ISPconfig, and I tried tried ebox. I may have to look some more. I used to use ClarkConnect, but they have a 10 mailbox limit now. 

I moved my various projects to Bluehost in 2005 and used a RHEL clone for the local network at home. Now Bluehost is complaining because I have too many files. It is time to consolidate.

---

### Post by haynest on 2009-03-23
FWIW, I am back with ebox on Hardy, and now that I have spent some more time with it, all is working as I intend. I appreciated all the replies as I was trying to sort this out.

---

