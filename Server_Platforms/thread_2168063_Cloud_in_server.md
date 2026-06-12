---
title: "Cloud in server"
date: 2013-08-16
forum: Server Platforms
---

### Post by salmendar on 2013-08-16
Hi,
    as my usual actions, i need to know wether i can install ubuntu cloud in my server mechine and host it for personal use. i have a lot of devices and 5 gb of unpaid data doesnt meet my requirements. can someone direct me to the steps that i need to follow to implement and access ubuntu cloud in and out of my server . installation.


pleeeease :confused:

---

### Post by TheFu on 2013-08-16
Google found these instructions as the first link: [http://www.ubuntu.com/cloud](http://www.ubuntu.com/cloud) .  I searched with "ubuntu cloud".
OTOH, what do you really want to accomplish?  "Cloud" usually means "someone elses' computer" - so which services do you specifically want?

---

### Post by TheFu on 2013-08-16
... forums posting error.

---

### Post by salmendar on 2013-08-16
i want a network attached storage that can be accessed from anywhere. (NAS)

---

### Post by TheFu on 2013-08-16
> **salmendar said:**
> i want a network attached storage that can be accessed from anywhere. (NAS)

sftp is the easiest that has world-class security. It is available from anywhere after you do a few things.  Google "ubuntu sftp server" to get started. Please use key-based authentication, not logins. Also load **fail2ban** to keep all the internet crackers out.

If you want something more like dropbox, check out **OwnCloud**. Since it uses PHP, I'd never allow it on the internet without using a real, strong VPN, like OpenVPN or IPSec.  Never PPTP.  Google "ubuntu owncloud" to get started.  Your security might not need the same level as mine, but at a minimum, you'll want a commercial SSL cert for the web server.

If this is for a business, you might want something like **Alfresco** or even a remote desktop capability. I don't know. These are more advanced and if you provide full access to all files, please use a VPN.

If these seem like too much trouble and you are willing to trust 3rd parties, look at PogoPlug or [http://www.tonido.com/](http://www.tonido.com/) or devices from WD and Seagate.  With all of these, you give up privacy, since a 3rd party **must** be able to connect to your storage to provide YOU with that same access.

If you aren't willing to trust 3rd parties, then the solutions are a little harder and require networking, router, server and knowledge for each client you'd like to connect from.  

So, after you google a bit and read up a little more, feel free to ask more questions.

---

### Post by salmendar on 2013-08-16
[[COLOR=#000000]TheFu[/COLOR]]("http://ubuntuforums.org/member.php?u=1037685")[COLOR=#000000]             [/COLOR]=D>
    
thank you very much..
 that is what i was looking for and it helped a lot. its for a small buisness but stongly it based on IT so i will also look into Alfresco but first i need to establish the cloud.
thank you again for your help
regards

---

### Post by TheFu on 2013-08-16
> **salmendar said:**
> [[COLOR=#000000]TheFu[/COLOR]]("http://ubuntuforums.org/member.php?u=1037685")[COLOR=#000000]             [/COLOR]=D>
    
thank you very much..
 that is what i was looking for and it helped a lot. its for a small buisness but stongly it based on IT so i will also look into Alfresco but first i need to establish the cloud.
thank you again for your help
regards

Using "the cloud" doesn't really mean anything to IT people. It is for marketing folks.  "The cloud" just means running services on "someone else's computer" that can be accessed over the internet.  HTTP servers are "the cloud", right?  The people setting up the remote services must be told what you want, how much security you need, how backups will be performed and the RTO and RTP for disaster recovery solutions.  Oh, and you probably need to have a list of supported clients - HW and software - so all the parts fit.

BTW, I've run Alfresco for 3 yrs and attempted to get owncloud working last month ... it sorta worked, but had issues. That VM was powered off to be thought about later.  I've been running sftp servers since '93.  It always works, never fails and supports most clients. There are very easiy to use desktop client programs.  For iDevices and Android, sftp is a little harder.  I use rsync over ssh instead.

---

### Post by hawkmage on 2013-08-16
The Ubuntu Cloud distro is not really a solution for an end user, it provides the pieces to build cloud services.  There is a solution called "Own Cloud" that I have not played with but know someone who started using it because of the 5/10/20 GB free storage limitation on the various free offerings.  I have thingt about installing it as well but just have not had the time to do so but it looks promising.

---

