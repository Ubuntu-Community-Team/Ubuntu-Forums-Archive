---
title: "Aliases in Postfix"
date: 2006-07-05
forum: Server Platforms
---

### Post by GlennB on 2006-07-05
Hi All,

I just set up Postfix under Dapper using virtual mailboxes, as per the howto here:

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

Things are working fine, but I'm having trouble working out how to setup aliases for postmaster, abuse etc.

I thought I could do this by editing /etc/aliases like so:

```
postmaster: glenn
abuse: glenn
```
etc. and then running 'newaliases'. However, this doesn't seem to work.

Any email addressed to 'postmaster' or 'abuse' gets bounced, which is going to make me unpopular with the (wo)man who runs the internet 8-[ 

Anyone know how to add new aliases in postfix?

Thanks,

Glenn.

---

