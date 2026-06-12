---
title: "Easy way to get servers to be able to send emails?"
date: 2010-10-28
forum: Server Platforms
---

### Post by fizgig on 2010-10-28
I'm going to be setting up a couple of servers for some friends.  I'd like them to be able to email me some information after they do some maintenance scripts via cron.

I got my own server to send email using a tutorial I found but that involved using my personal gmail account.

Anyone have any suggestions for getting email sending working on ubuntu server with minimal fuss and account credential exposure?

---

### Post by SeijiSensei on 2010-10-28
1) Install postfix and the bsd-mailx packages.

2) Use the "mail" command like this:

```
script.sh | mail -s 'todays results' me@example.com
```

pipes the output of script.sh to the mail program which sends it to me@example.com.

Whether you can receive these messages depends on whether your friends' ISPs have blocked outbound port 25 or not.  If they have, you'll need to do some configuring to make the mail appear valid and to relay it through the ISPs SMTP server.  You might need to futz with how the server identifies itself as well.

Frankly a better long-term solution is to use OpenVPN and set up a full-time tunnel between the remote box and you.  You can configure OpenVPN on the remote as a client so it will build a tunnel back to you when it's booted.

---

### Post by fizgig on 2010-10-28
Thanks a lot for your help.  The vpn tunnel seems like a good solution so I'll give that a shot.

---

