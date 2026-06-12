---
title: "Mail problem"
date: 2013-10-13
forum: Server Platforms
---

### Post by Bondar_Mircea on 2013-10-13
I have ubuntu server with postfix and dovecot. I have send a mail to a client, there client has a mail addresshosted by centos/cpanel&whm and there client say cannot receive any mail from me.I try to send mail to other client with same config and error persist (there client not receive any mail from me). I try to send email from my outlook.com account and message send succesfully. Something happens to my server or client server?

---

### Post by volkswagner on 2013-10-13
What error messages do you receive?

Are you hosting mail from home/residential connection?  Does your server have a static ip address assigned from your ISP?
Is your public ip address black listed?

Go to mxtoolbox.com and use there tools to check your ip, reverse DNS, etc.

---

### Post by nerdtron on 2013-10-13
Watch the /var/log/mail.log while you send emails to see the errors.
If you are successful from sending through outlook, I think the problem here is the "from field" when you send mail. How do you exactly send email?

---

### Post by Bondar_Mircea on 2013-10-13
I have bussines conection with static ip. In mail log says: delivered to maildir, but in centos (cpanel) mail clint is not appear.

---

### Post by SeijiSensei on 2013-10-14
Is dovecot configured for IMAP?  If so, try "telnet localhost 143" from the server's command prompt.  Can you connect?  If you're using POP3, try "telnet localhost 110".  

If you can connect with IMAP, try this:
```

$ [COLOR="#0000FF"]telnet localhost 143[/COLOR]
[stuff]
OK Dovecot ready
[COLOR="#0000FF"]1 login username password[/COLOR]
1 OK logged in
[COLOR="#0000FF"]2 select INBOX[/COLOR]
[lots of stuff]
[COLOR="#0000FF"]3 logout[/COLOR]

```

replacing "username" and "password" with the correct values.  (The commands you type are in [color='blue']blue[/color]. In the reply to the select command, you should see a lot of information about the mailbox.  

Are you sure the cpanel mail client is configured correctly?

---

