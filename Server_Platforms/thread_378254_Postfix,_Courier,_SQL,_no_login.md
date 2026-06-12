---
title: "Postfix, Courier, SQL, no login?"
date: 2007-03-07
forum: Server Platforms
---

### Post by quanin on 2007-03-07
I've done all the usual tutorials for setting up postfix, courier, and SQL. My configuration for all 3 looks exactly like[this particular one,]("http://www.howtoforge.com/virtual_postfix_mysql_quota_courier_p2") as that's the last one I tried. The problem comes up... actually there are two. I have [email]myaddie@my.host.name[/email] listed in the SQL database, and my.host.name listed in mydestinations. I can send mail just peachy fine, but receiving is an issue. Postfix wants to deliver the mail to /var/mail/user, rather than to [email]user@my.host.name[/email]'s actual mailbox. Additionally, and quite possibly related to this problem, I can't log in to my pop3 server, which runs Courier. Spits back a login failed error message when I try. I've done everything I can think of on my end, including going into the MySQL database and manually changing the password just on the off chance I typed it wrong on either end of the setup. Anyone have an answer I can borrow? Because I'm running out and google isn't being as helpful as it was an hour ago.

---

