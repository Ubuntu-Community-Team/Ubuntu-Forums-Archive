---
title: "Exim configuration help"
date: 2006-12-01
forum: Server Platforms
---

### Post by jeffdutra on 2006-12-01
Hi, I'm have a problem where I need to configure exim to either send mail from the *@xyz.com domain to both *@xyz.com and *@mailbackup.xyz.com or even if i need to do some kind of rewrite rule like jeff@xyz.com it will send to both jeff@mailbackup.xyz.com and jeff@xyz.com.

Any help would be greatly appreciated as i have been stuck on this issue for 3 days now.

Thanks in advance.

~Jeff

---

### Post by jeffdutra on 2006-12-03
so does anyone have an idea on how to do this??

---

### Post by hernan43 on 2006-12-03
A quick and dirty way to do this would be to use a global maildrop rule that does what you are asking. It would be simple to accomplish and maildrop plugs in nice and easy to exim.

---

### Post by jeffdutra on 2006-12-05
so how would i configure maildrop to do this??

---

### Post by coach-x on 2006-12-05
One way to do it would be using a .forward file, this assumes you are using standard accounts, as well as maildir for delivery.

[PHP]# Exim filter

if $header_to: contains "jeff@xyz.com" 

then
        save /home/jeff/Maildir/
        deliver jeff@mailbackup.xyz.com
finish
endif
[/PHP]

Good info on exim filtering can be found here:

[http://www.exim.org/exim-html-4.50/doc/html/filter_toc.html](http://www.exim.org/exim-html-4.50/doc/html/filter_toc.html)

---

### Post by jeffdutra on 2006-12-06
I am using exim as a mail gateway to filter spam and such and from there it forwards to an exchange server would it still work to use the .forward file?

---

### Post by coach-x on 2006-12-06
> **jeffdutra said:**
> I am using exim as a mail gateway to filter spam and such and from there it forwards to an exchange server would it still work to use the .forward file?

You need a system filter for that.  However, if your gateway is accepting mail for xyz.com, then forwarding to both xyz.com and mailbackup.xyz.com would form a mail loop with xyz.com.  

This setup will enable forwarding for all accounts.

Enable the system filter in your exim.conf file:

system_filter = /etc/exim/exim.filter

Put this in the exim.filter file:

[PHP]# Exim filter

if $header_to: contains "xyz.com" 

then
        deliver $local_part@anothermailserver.xyz.com
        deliver $local_part@mailbackup.xyz.com
finish
endif  [/PHP]

---

