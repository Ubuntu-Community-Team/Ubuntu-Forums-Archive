---
title: "Local host problem"
date: 2011-07-12
forum: Server Platforms
---

### Post by muzammil8t6 on 2011-07-12
hey guys , m new in Ubuntu , m trying to configure ired mail server  but i am having a problem with local host , i'm usign ubuntu 11... server edition .
please help me to sort out this problem ... 

Error :_

root @IREDMAIL :# hostname -f   (this is what i type )
hostname : name or service not known. (this is the error )

my /etc/hosts file

127.0.0.1 localhost
127.0.1.1 mail.testserver.com mail localhost lo

i have tried all the mentioned but couldn't get success ,

regards
muzammil:confused:

---

### Post by papibe on 2011-07-12
> **muzammil8t6 said:**
> 127.0.0.1 localhost
127.0.1.1 mail.testserver.com mail localhost lo
The second line should have the same address: 127.0.0.1, not 127.0.[COLOR="Red"]**1**[/COLOR].1

Regards.

---

