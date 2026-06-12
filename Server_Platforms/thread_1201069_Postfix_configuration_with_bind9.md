---
title: "Postfix configuration with bind9"
date: 2009-06-30
forum: Server Platforms
---

### Post by xiaomahe on 2009-06-30
Hai, anyone familiar with Postfix configuration using bind9??

i had configure my bind9 and currently had my virtual domain name (which is not really available in Internet), which called as secure.sec

in bind9 configuration i had configured the mail (IN MX 10 mail.secure.sec).

So, i was on the way installing Postfix using synaptic packet manager, and it ask me for some configurations..

At first, it ask me to 
1. Choose General type of mail configuration, which has several choices :Internet Site, internet with smarthost, sattelite system, local only.
2.System mail name. Default is my laptop name which is ming-laptop. 

For question number 2, do i had to put mail.secure.sec ?

i am trying to create a webmail by using bind9(for the domain configuration), Postfix(MTA), dovecot(IMAP/POP3). It just work as protoype, so it does not really an online application..

ANyone can help me answer that 2 questions above??


Thanks,




MING

---

