---
title: "can view the website but cannot ping my own server."
date: 2011-03-14
forum: Server Platforms
---

### Post by howtechstuffworks on 2011-03-14
Hi,
  I am setting up an wiki software, along with that I need to set up postfix server for sending confirmation mails. But I cannot send anymails. Even though the wiki application says mail has been sent succesfully, I didnt receive any mails(mostly gmail ID). I saw the log in /var/log/mail.err1 and it says connection timed out. Also when I try to ping my server it says connection timed out. But I can able to view the website. Also I can see the port 25 is assigned to smtp(query:nmap). 

Thanks

---

### Post by SeijiSensei on 2011-03-14
Your ISP is probably blocking *outbound* port 25.  You might be able to use the ISPs SMTP server to relay mail.

---

### Post by rubylaser on 2011-03-14
Ping responses are likely disabled on the firewall to prevent ping floods.  In regards to email, besides using your ISP's SMTP server (which is a great idea), you can potentially use Gmail's as well if you have a Gmail account.  This works great for me at home.
[http://www.hierax.org/2009/10/using-gmail-with-postfix-on-ubuntu.html]("http://www.hierax.org/2009/10/using-gmail-with-postfix-on-ubuntu.html")

---

