---
title: "mailserver SOHO with email syncronization on ubuntu server x64 and arm"
date: 2018-09-13
forum: Server Platforms
---

### Post by drc0rt3x on 2018-09-13
Dear to all, I want do a local mailserver with all the following requirements (please read carrefully):

1) when I create a local account (for example [EMAIL="me.gmail@localdomain.com"]me.gmail@localdomain.com[/EMAIL]), this account can download the mail from external mail account (for example [EMAIL="me@gmail.com"]me@gmail.com[/EMAIL]) using pop3 to download mails and delete them from gmail servers.

2) when send a mail, the mail will be sended (from thunderdird, outlook or aquamail)and stored to smtp server of localdomain.com and will be forwarded to smtp server of gmail with "from" header value "me@gmail.com" (instead of account "me.gmail@localdomain.com" configured on thunderbird or aquamail) and making authentication with username and password of gmail account; so the smtp server of local domain will act also as a smtp client versus external smtp server such hotmail, gmail and so on...

3) after that, considering that I have many devices (smartphone, tablet, notebook), I want that all the mails (sended and received) can be accessible from all the devices (for this reason in the point 2 also the mail sended will be stored on localdomain). This I can done configuring thunderbird, outlook or aquamail to connect using imap protocol for received mails, but I can't make it for syncronize mail sended, excepting using the protocol ExchangeActiveSync; for example if I send a mail from smartphone where i configure account [EMAIL="me.gmail@localdomain.com"]me.gmail@localdomain.com[/EMAIL], the mail sended isn't accessible on my notebook excepting using ExchangeActiveSync).

4) p.s. 1 : in the mail clients of the devices (thunderbird or outlook for win pc, aquamail for smartphone and tablet) don't must be added plugin or extension, the only action on mail client will consist to add the accounts of localdomain.com; on mailserver each account will be associated to an external account so [EMAIL="me.gmail@localdomain.com"]me.gmail@localdomain.com[/EMAIL] will be associated with [EMAIL="me@gmail.com"]me@gmail.com[/EMAIL], [EMAIL="me.hotmail@localdomain.com"]me.hotmail@localdomain.com[/EMAIL] will be associated with [EMAIL="me@hotmail.com"]me@hotmail.com[/EMAIL] and so on...

5) p.s. 2 : for to save space on tablet, smartphone and PCs at the first access, for both received and sended mails, will be only downloaded sender, object and date; when I open a mail from client then will be downloaded also body (and eventually attached files) of that mail.

6) p.s. 3 : I must implement the mail server with the previous requirements for linux ubuntu 64 bit and (if possible) for a qnap ts-231 arm based.


Now, point 2 can be solved with postfix as described here ?
[http://www.postfix.org/SOHO_README.html](http://www.postfix.org/SOHO_README.html)

Moreover here (no matter if You don't know italian language)
[https://www.hwupgrade.it/forum/showthread.php?t=944062](https://www.hwupgrade.it/forum/showthread.php?t=944062)

it's written that are necessary fetchmail and procmail... do you confirm? are they still supported?

the sincronization for all the devices can be made only with z-push?and how to link z-push and fetchmail? with z-push I can implement requirement of point 5?

there is a component (such z-push, procmail,...) where I must download the source code and make changes to satisfy at least the first 5 point?

---

### Post by drc0rt3x on 2019-01-04
nobody?

---

### Post by TheFu on 2019-01-08
Nope.  not with those restrictions.

I read everything twice and didn't know of a way to have separate transports for different gmail accounts and if you are going to these lengths, why have gmail involved at all?  If only 1 gmail account is involved, people do use it to forward all admin msgs, for example.

We use Zimbra as a communications server.  The web interface will allow connecting to gmail accounts and other external accounts.  I don't know if it will provide that access to other clients or if it runs on ARM.  Zimbra is fairly heavy, 3G of RAM is the min suggestion.  It demands a dedicated system.

Of course, the source code for most F/LOSS programs is available and you can make it do whatever you have the skills or can pay someone with the skills to accomplish, assuming the license allows that.

---

