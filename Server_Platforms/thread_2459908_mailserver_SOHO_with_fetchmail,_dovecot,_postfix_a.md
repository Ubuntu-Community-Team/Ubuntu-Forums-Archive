---
title: "mailserver SOHO with fetchmail, dovecot, postfix and z-push"
date: 2021-03-29
forum: Server Platforms
---

### Post by drc0rt3x on 2021-03-29
Dear to all, some years ago I have written the following thread
[https://ubuntuforums.org/showthread.php?t=2401106&p=13828325#post13828325](https://ubuntuforums.org/showthread.php?t=2401106&p=13828325#post13828325)

but both for only one user post a response many months after, both for various reasons, I don't go forward with that project. Now I remake the same questions but with some differences.

1) when I create a local account (for example [EMAIL="me.gmail@localdomain.com"]me.gmail@localdomain.com[/EMAIL]), this account must download the mail from external mail account (for example [EMAIL="me@gmail.com"]me@gmail.com[/EMAIL]) using pop3 to download all mails and delete them from gmail servers. So each account must be associated to an external account so [EMAIL="me.gmail@localdomain.com"]me.gmail@localdomain.com[/EMAIL] must be associated with [EMAIL="me@gmail.com"]me@gmail.com[/EMAIL], [EMAIL="me.hotmail@localdomain.com"]me.hotmail@localdomain.com[/EMAIL] must be associated with [EMAIL="me@hotmail.com"]me@hotmail.com[/EMAIL] and so on...
(this must be done with **fetchmail**)

2) when send a mail, the mail will be sended (from mail client thunderdird, outlook or aquamail) to smtp server of localdomain.com, stored there and will be forwarded to relative smtp server ( for example if I send a mail with [EMAIL="me.gmail@localdomain.com"]me.gmail@localdomain.com[/EMAIL] that is my private mail address, the "from" header value visible to destination must be "me@gmail.com" instead of account "me.gmail@localdomain.com" configured on thunderbird or aquamail), necessary that my private smtp server must make an authentication with username and password of gmail account; so the smtp server of local domain will act also as a smtp client versus the external smtp server (for example hotmail, gmail and so on...). (this must be done with **postfix**)

3) after that, considering that I have many devices (smartphone, tablet, notebook), I want that all the mails (sended and received) can be accessible from all the devices (for this reason in the point 2 also the mail sended will be stored on localdomain). This I can done configuring thunderbird, outlook or aquamail to connect using imap protocol for received mails, but I can't make it for syncronize mail sended, excepting using the protocol ExchangeActiveSync; for example if I send a mail from smartphone where i configure account [EMAIL="me.gmail@localdomain.com"]me.gmail@localdomain.com[/EMAIL], the mail sended isn't accessible on my notebook excepting using ExchangeActiveSync). For this limitation I've found the **z-push** system that allow the creation of the server that support exchange active protocol, while for the side of client outlook support it natively, thunderbird have the TbSync extension and aquamail also support it natively). 

4) this system should be implemented before on a x86 platform to make test, after on an arm platform (hope to find a motherboard that support arm processor with an architecture low power, else I'll switch to armbian and sbc): for these reason the components must be opensource, ready to be compiled on the arm architecture.

I have found all these components (fetchmail, postfix,z-push and I don't know if also dovecot will be necessary) but I don't know how install and set them. I think that it's possible make that because I have read the following references:

a) [https://ubuntuforums.org/showthread.php?t=1015150](https://ubuntuforums.org/showthread.php?t=1015150)
b) [https://www.howtoforge.com/the-perfect-push-mail-server-debian-squeeze-debian-6.0-with-ispconfig-3-and-z-push](https://www.howtoforge.com/the-perfect-push-mail-server-debian-squeeze-debian-6.0-with-ispconfig-3-and-z-push)

but the question are:
1) at point a it's obligatory that for each mail account should be created a new user... why? It's possible create in a user only a directory for each account created?
2) at point b it's necessary ispconfig? what is the scope of that component?
3) what is the backend here [https://z-push.org/](https://z-push.org/) ? 
3) how to compile, how to install and how I should configure the settings of the 3 (fetchmail, postfix, z-push) or 4 (dovecot, fetchmail, postfix, z-push) component? Can somebody help me?

drc0rt3x

---

### Post by rsteinmetz70112 on 2021-03-29
I'm not entirely following what the goal is here. 
But is is possible to set up Thunderbird and probably other email clients to do pretty much everything you say. You could probably send email using the gmail smtp server or your ISPs server and not need a local mail server. Usually once you login to the outgoing smtp server it doesn't care about the address in the "From" header. That would not require any the the email accounts have a separate account on your Linux machine.

---

### Post by drc0rt3x on 2021-03-30
> **rsteinmetz70112 said:**
> I'm not entirely following what the goal is here. 
But is is possible to set up Thunderbird and probably other email clients to do pretty much everything you say. You could probably send email using the gmail smtp server or your ISPs server and not need a local mail server. Usually once you login to the outgoing smtp server it doesn't care about the address in the "From" header. That would not require any the the email accounts have a separate account on your Linux machine.

the goals are multiple:
1. download mails from external account (aruba, libero, alice, hotmail, gmail) with pop3 because in some ISPs the amount of storage reserved to an account is low and there is the risk that is reached the limit
2. make a system where both mail sended that received can be readable from all device (also if gmail smtp server doesn't care about the address in the "From" header however the outgoing mail can be viewed only on device that have send it)
3. make a system that can be run on lowpower device arm such as helios64

---

### Post by rsteinmetz70112 on 2021-03-30
> **drc0rt3x said:**
> the goals are multiple:
1. download mails from external account (aruba, libero, alice, hotmail, gmail) with pop3 because in some ISPs the amount of storage reserved to an account is low and there is the risk that is reached the limit
Thunderbird can be set up with many email accounts - each of which can automatically download any new messages and delete email on the server when it is downloaded although I generally set my clients to leave it on the server for a set period of time depending on the amount of storage and the volume of email.
> 2. make a system where both mail sended that received can be readable from all device (also if gmail smtp server doesn't care about the address in the "From" header however the outgoing mail can be viewed only on device that have send it)
Thunderbird can be set to bcc all outgoing email to a specific account and although I've never done it, probably multiple accounts. As long as each device can read the email from the bcc: account all sent email will be available to every device. I do this with several computers I use in different locations so I have a record of all sent email wherever I am.
> 3. make a system that can be run on lowpower device arm such as helios64
I'm not familiar with Helios64 but it apparently can run Ubuntu or Debian and should have Thunderbird available. Thunderbird generally runs in a GUI which does take more resources. Apparently you can connect a TV/monitor and USB keyboard and have a fully functional workstation.  

There are also other GUI and command line email clients but I am not really familiar with them.

I'm pretty sure a Raspberry Pi could do all of this but I've never done it.

I'm sorry I can't be more definitive but the approach you initially outlined seemed to me to be overly complex.

---

