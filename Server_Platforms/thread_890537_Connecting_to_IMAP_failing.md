---
title: "Connecting to IMAP failing"
date: 2008-08-15
forum: Server Platforms
---

### Post by bobbyn on 2008-08-15
Hi,

  I have just setup Ubuntu Server and since I have a spare license also installed Plesk.
  Everything seems to run fine. I've added a mail account and installed roundcubemail as a separate webmail client.

  And now the problem: connecting to the imap account using the roundcubemail client on the same server works fine. When I try to connect by Thunderbird from the outside I get no connection. If I enable SSL in Thunderbird and use some default certificate it works.

  Whats happening?

  Greetings,
     Daniel

---

### Post by MJN on 2008-08-15
It sounds like perfectly sensible behaviour - only allowing plaintext authentication from external clients if SSL encryption is being used. For access from localhost such protection is not required as there are no credentials being sent on the wire.
 
I have my IMAP server (Dovecot) set up in the same way.
 
Mathew

---

### Post by bobbyn on 2008-08-15
Sorry. My fault. For some reason my companies IT admin have blocked port 143.

---

### Post by wintersnows on 2008-08-15
> **MJN said:**
> It sounds like perfectly sensible behaviour - only allowing plaintext authentication from external clients if SSL encryption is being used. For access from localhost such protection is not required as there are no credentials being sent on the wire.
 
I have my IMAP server (Dovecot) set up in the same way.
 
Mathew

hiya, I seen you experience in IMAP configuration. I need Courier-IMAP, the most common one install immediately for me to test my Python program as well. COuld you please show me? Thank in ahead of time.

---

### Post by wintersnows on 2008-08-15
yes, forget to ask: is this the right one for Hardy 8.04 version?

[http://www.flatmtn.com/article/setting-courier-imap](http://www.flatmtn.com/article/setting-courier-imap)

---

### Post by MJN on 2008-08-16
I'm afraid I don't have experience of Courier so anything Courier-specific would be handle be someone.

I recommend starting a new thread with your specific query as it'll only get lost in this one!

Mathew

---

