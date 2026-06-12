---
title: "use gmail to send emails from system"
date: 2016-07-27
forum: Server Platforms
---

### Post by atux on 2016-07-27
hello everyone. i am running a server and i am using my gmail account so the system can send emails from command line, in different cases.
i have followed the [https://wiki.amahi.org/index.php/Gmail_As_Relay_On_Ubuntu](https://wiki.amahi.org/index.php/Gmail_As_Relay_On_Ubuntu) with postfix.
the only problem i have is that the message appears to be send from root.
when i receive the message it says 
root <emal_address@gmail.com>
is there a solution to that?

---

### Post by howefield on 2016-07-27
Thread moved to the "*Server Platforms*" forum.

---

### Post by mastablasta on 2016-07-28
check the postfix settings/config file if you can change sender's name.

otherwise the sender for emails is actually "root" so that part is correct.

under number 1 below the question:
[http://serverfault.com/questions/412312/configuration-of-server-root-email-change-address-and-name-on-outgoing-email](http://serverfault.com/questions/412312/configuration-of-server-root-email-change-address-and-name-on-outgoing-email)

or this one

[https://anandarajpandey.com/2014/09/10/how-to-change-default-root-email-address-linux-postfix-centos/](https://anandarajpandey.com/2014/09/10/how-to-change-default-root-email-address-linux-postfix-centos/)

---

