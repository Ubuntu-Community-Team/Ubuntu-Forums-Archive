---
title: "Postfix+mysql+mailutils"
date: 2005-03-07
forum: Server Platforms
---

### Post by jim5272 on 2005-03-07
Hey all,
  Forgive the nubeness about to be displayed....

I have recently instaled Ubuntu onto my machine, and am setting up a server environment.

So far I have succesfully setup:
[list=1]
[*]Apache2
[*]PHP4.1
[*]MySQL
[*]Bind9
[*]ProFTPd
[*]Postfix+mysql
[/list] 
My problems began with the IMAP+POP service. I started by installing the mailutils-imap4d and mailutils-pop3, that all seemed well, but the trouble is, I have no Idea how to set it up with my accounts.

I am using virtual_mailbox accounts exclusively (no local delivery), and the mysql handling of those accounts is really slick. But after installing the maiutils, and reading all the docs, and mans, and infos I could locate. I find I don't know how to actually make this service work.

I am hoping to get it to work using the same DB tables as my postfix uses for authentication. But I can't locate any cf, or conf, or any other type of configure files for this service, it seems it is strictly a command line utility.

Could someone please share their experience with me, as this is my last hurdle to overcome. IMAP+POP.

thanks in advance
- Jim

---

### Post by Harlyman on 2006-03-08
same problem, after install of mailutils-imap4d imap is not working on my server anymore, its all dead, same with webmail, but i can't find outwhat has been changed, only error i can find in mail.log is this:

20:17:20 mail imaplogin: /usr/lib/courier/courier/imaplogin: No such file or directory

any idea anyone??

---

