---
title: "Docker edition Al fresco install problem on Ubuntu server 18.04 reg giSSL certificate"
date: 2019-08-14
forum: Server Platforms
---

### Post by deepakdeshp on 2019-08-14
I am trying to install Docker Alfresco but am getting error. The link I am following is [ALF docker install process]("https://community.alfresco.com/external-link.jspa?url=https%3A%2F%2Fdocs.alfresco.com%2Fcommunity%2Ftasks%2Fdeploy-docker-compose.html")  . I am using 64 bit Ubuntu server 18.04 which is fully updated.


```
 $ git clone [https://github.com/Alfresco/acs-community-deployment.git]("https://community.alfresco.com/external-link.jspa?url=https%3A%2F%2Fgithub.com%2FAlfresco%2Facs-community-deployment.git")
```
```

Cloning into 'acs-community-deployment'...
fatal: unable to access '[https://github.com/Alfresco/acs-community-deployment.git/':]("https://community.alfresco.com/external-link.jspa?url=https%3A%2F%2Fgithub.com%2FAlfresco%2Facs-community-deployment.git%2F%27%3A") server certificate verification failed. CAfile: /etc/ssl/certs/ca-certificates.crt CRLfile: 
none
```

Please advise

---

### Post by deepakdeshp on 2019-08-15
Hello,
Any body ?

---

### Post by LHammonds on 2019-08-16
Sorry but I do not have Docker experience.  I'm not sure I would ever use a Docker system in production and as such, do not run it for a test either.

I am not familiar with the install process but what you described sounds like an SSL certificate problem....probably with the github location.

I opened [https://github.com/Alfresco/acs-community-deployment.git](https://github.com/Alfresco/acs-community-deployment.git) in a browser and it does show the site has a valid SSL certificate though.  Not sure what the problem would be beyond that.

Is it working now?

---

### Post by TheFu on 2019-08-16
I've deployed Alfresco a few times, but never using docker.  I'm not a fan of docker, but I am a fan of containers that I build and manage. I do not trust pre-build containers.
I use a reverse proxy on a different system to handle all SSL cert termination, so Alfresco doesn't know anything about the certs.

---

### Post by deepakdeshp on 2019-08-21
> **LHammonds said:**
> Sorry but I do not have Docker experience.  I'm not sure I would ever use a Docker system in production and as such, do not run it for a test either.

I am not familiar with the install process but what you described sounds like an SSL certificate problem....probably with the github location.

I opened [https://github.com/Alfresco/acs-community-deployment.git](https://github.com/Alfresco/acs-community-deployment.git) in a browser and it does show the site has a valid SSL certificate though.  Not sure what the problem would be beyond that.

Is it working now?
No its not working. Let me try with Googling and see if i get it to work.

---

