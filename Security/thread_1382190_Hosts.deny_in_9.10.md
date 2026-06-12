---
title: "Hosts.deny in 9.10"
date: 2010-01-15
forum: Security
---

### Post by lostwf on 2010-01-15
Hi All,

I am a newbie here trying to figure out how to secure a linux server for deployment in DMZ

Installed Ubuntu Server 9.10 into a vmware image and selected the LAMP option and completed the install.

From some of the security docs I have been reading, one way of securing the server is to add ALL: ALL to the /etc/hosts.deny. I have tried this and there was no differences. The www service was still available to other machines on the network.

Trying to investigate the issue further, I found some documentation on using tcpdchk and tcpdmatch, but they do not work, they are looking for inetd.conf and the install did not install and inetd.conf file. 

I have never tried to use the server install, so I am not sure what the end result should be if you add the statement ALL: ALL to the /etc/hosts.deny file. But from what I could read I should not be able to access the web server from a network machine

I have tried finding information regarding this issue in the forum but I have not been successful

Is the observations correct ? How should hosts.deny act with the web server connections?

Is the recommended version to do this testing, 8.04 ?

Thanks

---

### Post by FuturePilot on 2010-01-15
Apache does not use the tcpwraper (hosts.deny, hosts.allow). Therefore anything you put in there will have no effect on Apache.

---

