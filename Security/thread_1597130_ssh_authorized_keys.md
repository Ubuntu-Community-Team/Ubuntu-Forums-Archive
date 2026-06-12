---
title: "ssh authorized_keys"
date: 2010-10-15
forum: Security
---

### Post by hyuk48 on 2010-10-15
hello

In authorized_keys file, what is that which has no user info?
I appreciate if let me know the reason. :)

example :
ssh-dss asdfnwienfliseflahefawef/asefaewf/......  
adfasdfasasdfasdfasdfas/asdfasdf    == user1@test1
ssh-dss asdfsdafasdfsdfsdfsdwef/asdfsadf/......  
adfasdfasasdfasdfasdfas/sdffsdfsf    == root@test1
ssh-dss asdfsdafasdfsdfsdfsdwef/asdfsadf/......  
 adfasdfasasdfasdfasdfas/sdffsdfsf    == user2@test1
[COLOR=Blue]ssh-dss asdfsdafasdfsdfsdfsdwef/asdfsadf/......  
 adfasdfasasdfasdfasdfas/sdffsdfsf    == [/COLOR][COLOR=Blue][/COLOR]

In blue line, there is no user info.
what is that line?

thank you

---

