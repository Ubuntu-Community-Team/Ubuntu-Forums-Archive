---
title: "postfix email server issue"
date: 2009-09-29
forum: Server Platforms
---

### Post by pantlegz on 2009-09-29
So I setup postfix according to the guildlines posted [http://www.howtoforge.com/perfect-server-ubuntu-8.10](http://www.howtoforge.com/perfect-server-ubuntu-8.10) and I'm able to send mail internally just fine, and I know I'm not going to be able to send mail to the Internet due to the fact that I have some strange dns constraints. But I do have a small network and I need to verify that I'm able to send and receive e-mail within the network. However I'm not able to log into any of the accounts with the passwords that I think I know of them. Is there a quick and easy way to either create another user and password, or check the passwords for existing users? I've searched around and checked out the postfix site but wasn't able to come up with much :(

Oh I'm using ubuntu 8.10 (desktop) if it matters

---

### Post by scrooge_74 on 2009-09-29
Well if you crate a user then you can config your mail program (evolution/thunderbird/mutt) to read mail.

About sending to the outside world you should check if you can use your ISP mail server for relaying, I just did that for mine.

If you did the dpkg-reconfigure postfix  you can tell it to include your internal network as your trusted network so internal mails are received and sent.

Remember you need something like dovecot to handle the pop part for the clients

---

### Post by pantlegz on 2009-09-29
Right, but how do I create a user? Or modify a user? The list of users I see in webmin includes both my user login as well as root and neither of the passwords for those accounts work.

I know how I should be able to make this work, with my ISP's DNS but the issue is it's a school project and the IT dept doesn't want everyone coming to them asking for mx records put in their dns, and doing zone transfers is too risky for them. However on a local domain my DNS mx records work just fine.

I should point out I found this website [http://blog.scottlowe.org/2006/03/01/creating-users-for-a-postfix-based-mail-relay/](http://blog.scottlowe.org/2006/03/01/creating-users-for-a-postfix-based-mail-relay/) and followed the steps to make a password for a user, and I'm still not able to log in with thunderbird. Grr I hate e-mail.

---

### Post by scrooge_74 on 2009-09-29
You tried doing a whois query to get the DNS or the IP of the provider? Just an idea.


On on the subject of users and passwords, I'm not that experience with postfix, i just got it running the other day with just a couple of accounts.

What I did as root made the users that will be mailing in and out. At some point for sending mails I had to do a Maildir in their respectives /home/users and give them ownership.

After I got the TLS part working for the server in the client PCs made users have the same name as in the server so when I tried to receive mail and the system asked me for a pass I gave the pass for the users I made in the server. So far is working, haven't check for any security risk by doing this, those users don't have any privs in the box since they only do mail.

Proly someone will read this and slap me silly for my setup

---

### Post by pantlegz on 2009-09-30
Actually I'm an idiot, I forgot to edit /etc/default/saslauthd to tell it what/where to authorize. after adding that last line I was able to log in wihtout issue. Thanks for all the help :)

---

