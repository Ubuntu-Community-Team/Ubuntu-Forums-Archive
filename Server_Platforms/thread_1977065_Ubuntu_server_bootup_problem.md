---
title: "Ubuntu server bootup problem"
date: 2012-05-09
forum: Server Platforms
---

### Post by Ishikawa91 on 2012-05-09
Hello,

I am trying to learn how to use Linux servers. I have installed Ubuntu Server 12.04. I have apache2, mysql, and proftpd installed.   For proftpd I created authentication via TLS. I had to  generate a certificate with a passphrase. (I followed a tutorial on the  Ubuntu Forums but forgot the link) 
  Whenever I start the server, before fully booting to the login screen, **it prompts me for the RSA certificate passphrase**.  The only problem is, 4 out of 5 times it won't let me actually input  anything and just hangs there saying: 
"incorrect passphrase" once. 
  If I reboot the server a couple times while randomly pressing  buttons, sometimes it will let me enter the passphrase but will not  accept it. So if I just keep hitting enter at this point, after about 4  or 5 "incorrect passphrase" messages it finally just gives up and  presents the login screen finally. 
  Any ideas why this is happening? I'd rather not just remove the  passphrase and do not know enough yet about server administration and  the like to really know whats going on here.

---

### Post by howefield on 2012-05-10
Thread moved to the "*Server Platforms*" forum.

---

