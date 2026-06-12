---
title: "can somone tell me what this postfix error means?"
date: 2009-02-04
forum: Server Platforms
---

### Post by sfuller on 2009-02-04
postfix/smtpd[26515]: NOQUEUE: reject: RCPT from unknown
[10.1.10.11] 554 5.1.1 <root@example.com> relay access denied

my domain is example.net an my static gateway address is in the mynetworks but can not send out the domain i thought that any address in the nynetworks = could relay though my smtp? could someone help i dont need remote users only mynetwork so i thought i dont have to auth via sasl could some one tell me if i am under standing this right

---

### Post by gombadi on 2009-02-04
> 
[10.1.10.11] 554 5.1.1 <root@example.com> relay access denied


and

> 
my domain is example.net


Is that a typo? If not then it is rejecting the example.com email address because it is not an example.net address.

Also could you show us your main.cf - it may help if we see more of your config.

---

### Post by martien on 2009-02-04
Probably you aren't add your ip to mynetworks and your mynetworks is not added to your smtp recipient restrictions (permit_mynetworks) OR you have smtp auth configured and your postfix reject all unauthenticated requests. We can give you more advices and be more sure if you post your main.cf here.

---

### Post by sfuller on 2009-02-04
> **gombadi said:**
> and



Is that a typo? If not then it is rejecting the example.com email address because it is not an example.net address.

Also could you show us your main.cf - it may help if we see more of your config.

yes i can post my main.cf put i cant do it until tomarrow morning when i go to the office where the server is. no that was not a type i was try to send i massage we have the .com name and the .net name the .com is hosted by somone else i was trying to send a test message from the .net server i set up to the .com server over the internet. can postfix's smtp not do mail from mynetwork over the internet to another server ? if so how is this done ?

---

### Post by sfuller on 2009-02-04
> **gombadi said:**
> and



Is that a typo? If not then it is rejecting the example.com email address because it is not an example.net address.

Also could you show us your main.cf - it may help if we see more of your config.

> **martien said:**
> Probably you aren't add your ip to mynetworks and your mynetworks is not added to your smtp recipient restrictions (permit_mynetworks) OR you have smtp auth configured and your postfix reject all unauthenticated requests. We can give you more advices and be more sure if you post your main.cf here.

the only auth i have is smtp_uses_tls = yes no sasl net up i have add my ip address to the mynetworks and 
recipient restrictions = permit_mynetworks is thier any thing else that needs to be done to allow only mynetwork to send mail any where over the net over do i need somthing else to send maail over the net?

---

