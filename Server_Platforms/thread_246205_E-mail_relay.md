---
title: "E-mail relay"
date: 2006-08-28
forum: Server Platforms
---

### Post by clapper65 on 2006-08-28
I would like to pull e-mail from my roadrunner ISP to a server on my network, then allow other clients on my network to get their mail. I don't have my own domain and would like to keep using my [email]xxxx@rr.com[/email] addresses. I can pull mail to my server using fetchmail, but how do I serve it to the clients on my network? Any help would be greatly appreciated.

---

### Post by funchords on 2006-08-29
You will want to run a POP3 or IMAP server.  (or am I misunderstanding your question?)

---

### Post by clapper65 on 2006-08-29
I plan on using dovecot as a pop3 server.  My big question is the configuration, since I don't have my own domain name, how do I configure it to make make mail available after I retrieve using fetchmail?

---

### Post by jimcooncat on 2006-08-29
Don't see that you need your own domain to do this. Once you set up dovecot, just configure your email client to the machine dovecot's running on. You can just use the IP address if you don't want to mess with machine names.

---

### Post by Woei on 2006-08-29
> **clapper65 said:**
> I plan on using dovecot as a pop3 server.  My big question is the configuration, since I don't have my own domain name, how do I configure it to make make mail available after I retrieve using fetchmail?

Why do you think you need a domain name to pop your mail or browse it with IMAP on your local network ? If you're running an smtp and pop3 server on your ubuntu machine, say 192.168.1.50, then the other clients on your LAN should just point their MUA (Outlook, Thunderbird) to that IP. Sending will happen through your ISP's smtp server either directly, or through 192.168.1.50 if postfix is configured to use your ISP's SMTP server as its smarthost and allows connections from your LAN's netblock (it does not by default, only from localhost). The From: address is a matter of the MUA, not the smtp/pop3 server. I can send you a mail with  "From: Mark Shuttleworth <mark@ubuntu.com>" in its headers just by changing mutt's configuration for instance.

Once you've popped your mail with fetchmail and it's on the ubuntu box, you just have to setup a POP3 or IMAP server on the ubuntu box to distribute the mail to clients on your LAN.

---

### Post by jimm on 2006-08-29
Hi,

With Fetchmail you can tell it that remote user XXX is the same as local user YYY. Fetchmail will then deliver mail for remote user XXX to local user YYY and you can then use pop or whatever local client you want for your clients to get thier mail. 

You do need unique remote mail accounts to differentiate for local delivery of course. You can get fancy with you local mail setup to filter the mail on other things, but thats a bit more tricky! If you have a bunch of unique mail accounts at your ISP you want to pick up mail for and deliver locally, then Fetchmail will do the trick. 

Sorry I dont know the fetchmail syntax off the top of my head, but there a plenty of examples on the net (google). 

Thanks,
James

---

### Post by stormblue on 2006-08-29
If road runner offers IMAP, why do you need your own server.  What I would do is configure all the clients to use IMAP off of the RR servers.

---

### Post by clapper65 on 2006-08-29
Thanks for everybody's help on this.  I was trying to make it more complicated than it needed to be.  I've got it working like I want, spam filters and all.  Thanks again.

---

