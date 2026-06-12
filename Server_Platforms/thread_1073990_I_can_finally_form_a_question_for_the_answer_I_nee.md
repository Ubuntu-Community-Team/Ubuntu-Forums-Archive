---
title: "I can finally form a question for the answer I need :)"
date: 2009-02-18
forum: Server Platforms
---

### Post by michaeljessie on 2009-02-18
ok I am setting up my mail server and I just looked at the headers when I send an email to myself and the originating IP address is my 127.0.0.1 address I think in order for a yahoo or another freebe service needs the external IP address in the header so anyways umm how do I change that in my mail configuration? Thats also probably why I cant recieve emails?

---

### Post by rhcm123 on 2009-02-18
> **michaeljessie said:**
> ok I am setting up my mail server and I just looked at the headers when I send an email to myself and the originating IP address is my 127.0.0.1 address I think in order for a yahoo or another freebe service needs the external IP address in the header so anyways umm how do I change that in my mail configuration? Thats also probably why I cant recieve emails?

i think you need to see this:
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)
(i used it to setup my mail server)

scroll down until you find the postfix guide and read through that, they walk you through what you need to do (essentially what you need to input into the dpkg-reconfigure prompts)

have fun on your long and painful mail server journey. i know i am :)

---

### Post by windependence on 2009-02-18
If you really want to reliably send mail, you will need a static IP and you will need to set up reverse DNS (PTR) records for it. Otherwise, some mail servers will not send mail that cannot be verified.

-Tim

---

### Post by michaeljessie on 2009-02-19
I do have a static IP address

---

### Post by rhcm123 on 2009-02-19
> **michaeljessie said:**
> I do have a static IP address

then you should be fine. I have a DHCP configured address, but with dyndns all my mail originates from (Domain).dyndns.org. As long as your mail system is setup properly then sending mail outside of your network shoulden't be a big problem.

However, i don't understand your question. What exactly are you trying to accomplish?

---

### Post by michaeljessie on 2009-02-20
I want to do exactly what your doing with email setting it up at koolkreations.dyndns.org go check it out

---

### Post by rhcm123 on 2009-02-20
> **michaeljessie said:**
> I want to do exactly what your doing with email setting it up at koolkreations.dyndns.org go check it out

follow the guide i gave in the previous post at:
[https://help.ubuntu.com/community/MailServer](https://help.ubuntu.com/community/MailServer)

---

