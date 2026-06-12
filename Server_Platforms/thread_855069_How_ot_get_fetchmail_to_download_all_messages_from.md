---
title: "How ot get fetchmail to download all messages from server including any already seen"
date: 2008-07-10
forum: Server Platforms
---

### Post by beaker15 on 2008-07-10
Hi
The current setup i have is fetchmail fetching mail from my ISP, putting it in a postfix mailbox, then thunderbird on the client downloading it from there. All was fine but I had a problem with a thunderbird profile which decided to lose about a years worth of email for no apparent reason (although it still sends/receives new mail fine). I still have all these old emails at the ISP because i set fetchmail to leave messages on the server so no probs there. I've created a new thunderbird profile and need to get all of the mail from my ISP into this inbox BUT fetchmail won't fetch them because it they're marked as seen because it's downloaded them before. So how can i get fetchmail to recognise these as not seen, download all messages and leave them on the server at the ISP?

thanks for reading

---

### Post by carcdrcdr on 2008-07-10
Its:
```
fetchmail -a
```

To get ALL messages from the server ;)

On a some what related topic you may also be interested in procmail: [http://www.panix.com/help/mail.procmail.html](http://www.panix.com/help/mail.procmail.html)

---

### Post by beaker15 on 2008-07-10
its important that it leaves all of them them on the server though. Will this command do that?

---

### Post by carcdrcdr on 2008-07-10
Hehe, to put it nicely you need to RTFM ;)
```
man fetchmail
```

The command you need is:
```
fetchmail -a -k
```

A little bit of man page can go along way ;)

---

### Post by beaker15 on 2008-07-10
fair enough point taken :). I asked because i usually manage fetchmail through webmin and it wouldn't allow me to fetch all mail and leave mail on the remote server, it said the two contradicted each other (although i can't see how). I'll stop being lazy and use the command line. Thanks

---

### Post by beaker15 on 2008-07-15
for those interested in how i ended up doing this, i edited the user's .fetchmailrc file (should be in their home folder)and added  to that the lines to 'keep' and  'fetchall'

---

