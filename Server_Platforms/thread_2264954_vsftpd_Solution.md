---
title: "vsftpd Solution"
date: 2015-02-11
forum: Server Platforms
---

### Post by waterwalker2 on 2015-02-11
I am pretty new to linux and could use some help.  I'm using Ubuntu server 14.04 LTS.  I work for an adult mental health facility and we need to find a way to allow clients to access their records (It has to do with Insurance and lawyers :mad:).  Anyway, One option I have looked at is vsftpd.  From what I know it seems like the best option because of it's security.  This has to available to the outside world, so the server will be in our DMZ.  Currently I am testing from my test environment and am having challenges.  From a management standpoint, the request for access will come to our medical records department, they will gather all the data and format it into pdf.

Here's what is required for clients...

[LIST=1]
[*]username/password authentication 
[*]Confined to one directory 
[*]Only download, no upload 
[*]SSL 
[/LIST]

Here's what I would like for Medical Records Staff...
[LIST=1]
[*]Ability to Create accounts 
[*]Ability to set client credentials 
[*]Ability to upload files to the clients directory 
[*]simple and easy to use Web based / client based administration would be best 
[/LIST]


Is this possible?  Any and all suggestions are appreciated!!

Scott

---

### Post by TheFu on 2015-02-12
Please don't use FTP. Nobody should use plain FTP anymore - ok - almost nobody. Just for fun, google "vsftpd hacked", please.

Rather use sftp which is built-into openssh-server.  This is how you'll let the staff place fies there ... assuming you don't automate the process using an hourly rsync script (which is what I'd do).  It is best to keep end-users off internet servers and definitely don't let them push files there directly - except to a different domain where AV checks and automatic file conversions can be run first.

Realistically, I think you'd be better off using a web-app with https for patient access.  Before you ask, I cannot recommend any - alternativeto.net or freecode may be able to suggest something.  May want to check out Alfresco, if there is budget for a patient access portal.

We were all new to Unix/Linux at some point, but please be aware that security of internet-facing servers is a non-trivial task best left to someone with years of Unix security experience.  MSFT skills don't really transfer very much, since the philosophies for the OS are vastly different and so is the security model.

---

### Post by nerdtron on 2015-02-12
> This has to available to the outside world, so the server will be in our DMZ.

Don't. Please port forward only the needed ports to the server like port 22 for sftp download/upload and port 80/443 for the web access portal. Less ports exposed to public the better.
I think the first 4 requirements are easy to create, but the later 4, I have no recommendations.

---

### Post by steeldriver on 2015-02-12
Amen to all that. Please also be aware that depending on your jurisdiction there are likely some very specific regulatory compliance and audit requirements (such as HIPAA in the US) for anything involving health information. This is not something the average joe should even contemplate putting together from scratch imho.

---

### Post by TheFu on 2015-02-12
Met a former CEO last fall with a small medical testing company nearby. They had 1 file with patient billing data leaked in 2008.

The FTC heard about it from a "cyber security" company and started an investigation.  5 yrs later ... the company doesn't exist anymore. All the employees had to find other jobs.  The FTC ended up suing the company out of business - it is an interesting story worthy of reading an article about: [http://www.bizjournals.com/bizjournals/washingtonbureau/2013/09/13/medical-testing-lab-fights-the-devil.html?page=all](http://www.bizjournals.com/bizjournals/washingtonbureau/2013/09/13/medical-testing-lab-fights-the-devil.html?page=all)  The CEO wrote a book about the experience withe the cybersecurity company, the insider connections it had to DoD and the FTC, and how the FTC just expected his company to admit wrong-doing and accept 20yrs of high-cost security audits to stop the lawsuit - but I can't see most people being interested. The linked article IS worth a read, IMHO.

---

