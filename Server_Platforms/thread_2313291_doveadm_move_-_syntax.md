---
title: "doveadm move - syntax?"
date: 2016-02-11
forum: Server Platforms
---

### Post by babaton on 2016-02-11
Hi,

I'm trying to use doveadm move to move all mail older than x days for a specific user to their trash folder.

Here's my command....

[COLOR=#0000ff]doveadm move -u user TRASH mailbox INBOX BEFORE 10-Feb-2016 SINCE 1-Feb-2016[/COLOR]

When I run the command I get : Can't open mailbox TRASH : Mailbox doesn't exist: TRASH

I've tried this with other folders and I  always get the same error, all folders do exist and I can succesfully examine them if I login via telnet using IMAP. What am I doing wrong? I've searched all over the web but can't find many examples other thant he one on the doveadm wiki page.

---

### Post by babaton on 2016-02-11
Got it....

I ran doveadm mailbox list -u user

It lists the folders for the account and the trash folder is listed at INBOX.trash

So it should be : doveadm move -u user INBOX.Trash mailbox INBOX BEFORE 10-Feb-2016 SINCE 1-Feb-2016

---

