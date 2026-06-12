---
title: "get mail across a LAN - quick and easy solution needed"
date: 2007-03-06
forum: Server Platforms
---

### Post by neill on 2007-03-06
hi

i use an ubuntu box as a headless rdiff backup server on my LAN and i need a quick and dirty way to forward root's mail to my main server

ideally i need a simple POP3 server running on the backup box which serves up /var/mail as and then i can collect it onto my main server with getmail, which is how i get all my other external mail (whihc then runs an IMAP server for all the LAN clients)

anyone point me to a quick and simple way to do this ?

as it's all on an internal LAN security is not a big issue

thanks

neill

---

### Post by hlynur on 2007-03-06
If you jus want to forward eks /var/mail/root to another address you can do 
formail -n 3 -s /usr/sbin/sendmail [email]receiver@domin.com[/email] < /var/mail/root

to forwar all root mail to [email]receiver@domin.com[/email]

/ Thor

---

### Post by neill on 2007-03-06
perfect thanks, i'll do that :)

neill

---

