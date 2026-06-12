---
title: "Learning to install postfix in a mail server."
date: 2011-03-16
forum: Server Platforms
---

### Post by kohdesmond on 2011-03-16
Hi Guys,

Just start learning unix network admin, was trying out the [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto) to install postfix.

did all till here: 
[FONT=monospace]https://help.ubuntu.com/community/PostfixBasicSetupHowto#Test%20your%20default%20setup

i tried to check mail in fmaster, but i was told access denied and there is no mail. may i know what happen ?

i'm using ubuntu 10 lucid server edition

thanks for replying me

Desmond
[/FONT]

---

### Post by falko on 2011-03-16
Are there any errors in /var/log/mail.log?

---

### Post by kohdesmond on 2011-03-16
if i 'm not wrong, there isn't any error in it.

all i need to do is to have a mail server in the internal network with a smtp mail relay @ DMZ

and to have email working internally within your network over IPv4 and IPv6 thats all....looks like Linux is tough

---

