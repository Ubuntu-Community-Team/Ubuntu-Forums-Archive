---
title: "Postfix Maildir Operation not permitted"
date: 2013-06-15
forum: Server Platforms
---

### Post by luisjone on 2013-06-15
Hi all,

I'm trying to set postfix with virtual mailboxes in Ubuntu server 12.04 in a virtual machine with same OS as host. I have done so in the past following:

[https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto](https://help.ubuntu.com/community/PostfixVirtualMailBoxClamSmtpHowto)

However for some reason I'm stuck testing the virtual mailbox setup, I can send email even out of the network but maildir fails delivery when receiving. I keep on getting an error in /var/log/mail.log:

```
Jun 15 20:11:57 mail postfix/virtual[1222]: 15A67A2D28: to=<hello@domain.com>, relay=virtual, delay=0.05, delays=0.04/0/0/0.01, dsn=4.2.0, status=deferred (maildir delivery failed: create maildir file /home/vmail/domain.com/hello/new/1371341517.V14IcM123045.mail.domain.com: Operation not permitted)
```

I've dealt with Protocol error or permission error and there are plenty of threads about them, but for the last 3 days I can't figure out this "operation not permitted". It goes as far as creating the directories by itself (~/domain.com/hello/new/) but it can create the email file.....Config file and situation are pretty much the same in the tutorial, I have checked permissions, configs, users, groups, chroot, apparmor everything seems fine, there is no dovecot or certificates so should be straight forward....I must be missing something.

I would much appreciate if someone can throw any idea....I am running out.

Thanks in advance.

---

### Post by lisati on 2013-06-15
It *looks* like a permissions issue to me. Sometimes useradd, groupadd etc don't take effect until you do a restart.

---

### Post by luisjone on 2013-06-15
Hi lisati,

Thanks for the suggestion, I did restart several times. Because it is a guest machine permissions are always a pain, however they are, maybe you see something I don't:

in /etc/postfix/main.cf:

virtual_uid_maps = static:5000 
virtual_gid_maps = static:1001

id vmail:
uid=5000(vmail) gid=5000(vmail) groups=5000(vmail),100(users),1001(vboxsf)

ls -l /home/
drwxrwxr-x 1 vmail vboxsf 4096 Jun 14 21:50 vmail

ls -l /home/vmail/
drwxrwxr-x 1 vmail vboxsf 4096 Jun 15 18:26 domain.com

ls -l /home/vmail/domain.com/
drwxrwxr-x 1 vmail vboxsf 4096 Jun 15 08:56 hello

ls -l /home/vmail/domain.com/hello/
drwxrwxr-x 1 vmail vboxsf 4096 Jun 15 08:56 cur
drwxrwxr-x 1 vmail vboxsf 4096 Jun 15 18:30 new
drwxrwxr-x 1 vmail vboxsf 4096 Jun 15 20:53 tmp

I have set it to 1001(vboxsf) because I find it makes always my life easier but I get the same error even if I set it to 5000(vmail). Am I missing something?

---

### Post by lisati on 2013-06-15
Apologies if I'm unable to offer additional suggestions at this stage: my server setup is a little different to those given in the guides. I don't mind if someone else takes a look.

---

### Post by luisjone on 2013-06-15
Thank you very much though Lisati.

At this point this machine only has the postfix....And about the permissions I am thinking that was postfix the one creating the folders, one would think it can indeed write on them...

Cheers,

---

### Post by lisati on 2013-06-15
<aside>
There are several different ways of configuring Postfix. Some, like you have done, use virtual mailboxes, others base their setup around standard *nix accounts and have the Maildir folder in a user's Home directory. Then there's virtual domains, aliases, virtual aliases and a whole bunch of other stuff which could confuse the beginner. 
</aside>

---

### Post by luisjone on 2013-06-15
I know, and before I setup the virtual mailboxes I tested it working with *nix users and it did. However, I did get the virtual mailboxes working in the past and base my organization around that (which I find much more convenient and easier to grow). 

For sure there is a complexity layer added setting virtual mailboxes, but it is not magic, and I don't want to give up because it's difficult, if so I wouldn't even try to have a mail server... At this point I can't find no good reason because it is not working, but then again I am obviously missing something....

Thanks for your input anyway Lisati, much appreciate your time. 

Anyone has any other idea?

---

