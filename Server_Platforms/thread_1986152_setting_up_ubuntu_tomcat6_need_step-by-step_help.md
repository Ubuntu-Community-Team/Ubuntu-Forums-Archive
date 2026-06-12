---
title: "setting up ubuntu tomcat6 need step-by-step help"
date: 2012-05-24
forum: Server Platforms
---

### Post by mjfroggy on 2012-05-24
OK I am hoping some kind soul will give me sime direction.
I have a cpu which I am trying to make be a local java/tomcat server.

So I put in the newest Ubuntu server install 12.04 LTS
I walked through all the steps without any issues or errors
I then selected openssh and tomcat to be installed
and everything seemed to work just fine no errors on any of the screens
After getting the reboot screen and taking the cd out of the cpu and rebooted the pc. I then did a ifconfig on the command line go the ip address and could not reach/find the server on my network I tried using the inet addr as well as the Bcast ip address . I also tried using the hostname still not able to reach the server

So I then did a sudo etc/init.d/tomcat6 restart command and tomcat6 restarted with no errors (its says OK)

So now I still am not able to reach or find the server I tried putting a :8080 at the end of the ip. So any suggestions on what I am missing? I should not I had setup a LAMP server using the similar process but selecting LAMP server on a seperate pc and had no issues getting that all to work so it just seems like I am missing something to get this tomcat server to run??

any suggestions
Thanks

---

### Post by 2F4U on 2012-05-24
Can you ping from the server to another machine on the same network?

---

### Post by mjfroggy on 2012-05-24
yes I can ping yahoo.com and it works

---

