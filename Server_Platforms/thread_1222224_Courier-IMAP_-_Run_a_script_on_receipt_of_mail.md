---
title: "Courier-IMAP - Run a script on receipt of mail?"
date: 2009-07-24
forum: Server Platforms
---

### Post by shavenlunatic on 2009-07-24
Hi,

I've got an ubuntu (Dapper) server running Courier-IMAP managed by plesk (although I rarely touch plesk and stick to SSH).  What I want to do it start recording all undeliverable outgoing mails.

Basically, I'd like to check each mail which comes in, if the subject is "failure notice" I would like to pull out of the mail the address it was supposed to go to and process that on the server (bash script to run would be fine)

I'm sure there will likely be a better and more common way of doing this.. so any advice would be appreciated.

Cheers

---

### Post by shavenlunatic on 2009-07-27
*monday morning bump*

Any advice? :D

---

### Post by grantemsley on 2009-07-27
If you are using procmail to deliver mail from postfix or exim, you can set rules in procmail to run a script on certain emails.  You'd have to look into the exact details, but looking up procmail should get you pointed in the right direction.

---

