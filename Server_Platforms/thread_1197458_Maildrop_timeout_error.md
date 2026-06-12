---
title: "Maildrop timeout error"
date: 2009-06-26
forum: Server Platforms
---

### Post by barti on 2009-06-26
I'm having some odd issues with maildrop delivery emails above a certain size. Small messages (up to around a megabyte or so) get delivered correctly, but larger ones generate logs such as this:

```
Jun 26 10:34:55 mail2 postgrey: action=pass, reason=triplet found, client_name=unknown, client_address=nnn.nnn.nnn.nnn, sender=xxxxxx@xxxxx.xx.xx, recipient=myaccount@xxxx.xxx
Jun 26 10:35:58 mail2 postfix/qmgr[542]: 8216615401A: from=<xxxxxx@xxxxx.xx.xx>, size=4153279, nrcpt=1 (queue active)
Jun 26 10:35:58 mail2 amavis[6740]: (06740-10) ESMTP::10024 /var/lib/amavis/tmp/amavis-20090626T102004-06740: <xxxxxx@xxxxx.xx.xxk> -> <myaccount@xxxx.xxx> SIZE=4153279 Received: from mail.xxxx.xxx ([127.0.0.1]) by localhost (mail.xxxx.xxx [127.0.0.1]) (amavisd-new, port 10024) with ESMTP for <myaccount@xxxx.xxx>; Fri, 26 Jun 2009 10:35:58 +0100 (BST)
Jun 26 10:35:58 mail2 amavis[6740]: (06740-10) Checking: xS+LPyptKPjk [nnn.nnn.nnn.nnn] <xxxxxx@xxxxx.xx.xx> -> <myaccount@xxxx.xxx>
Jun 26 10:35:59 mail2 amavis[6740]: (06740-10) FWD via SMTP: <xxxxxx@xxxxx.xx.xx> -> <myaccount@xxxx.xxx>,BODY=7BIT 250 2.6.0 Ok, id=06740-10, from MTA([127.0.0.1]:10025): 250 2.0.0 Ok: queued as DC590154144
Jun 26 10:35:59 mail2 amavis[6740]: (06740-10) Passed CLEAN, [nnn.nnn.nnn.nnn] [nnn.nnn.nnn.nnn] <xxxxxx@xxxxx.xx.xx> -> <myaccount@xxxx.xxx>, Message-ID: <C3B943F1B184EC4EB0BD19866A65848D10F4D915A3@orion>, mail_id: xS+LPyptKPjk, Hits: -, size: 4153279, queued_as: DC590154144, 1227 ms
Jun 26 10:35:59 mail2 postfix/smtp[7980]: 8216615401A: to=<myaccount@xxxx.xxx>, relay=127.0.0.1[127.0.0.1]:10024, delay=64, delays=63/0/0/1.2, dsn=2.0.0, status=sent (250 2.0.0 Ok: queued as DC590154144)
Jun 26 10:35:59 mail2 postfix/qmgr[542]: DC590154144: from=<xxxxxx@xxxxx.xx.xx>, size=4153734, nrcpt=1 (queue active)
Jun 26 10:40:59 mail2 postfix/pipe[8215]: DC590154144: to=<myaccount@xxxx.xxx>, relay=maildrop, delay=301, delays=0.54/0.04/0/300, dsn=4.3.0, status=deferred (temporary failure. Command output: maildrop: Timeout quota exceeded. )
```

Messages of any significant size are building up in the deferred queue in postfix, and eventually being discarded without delivery. The account is not over quota, and I've been unable to find out what the timeout is - surely 4MB isn't too large to scan (on a new Quad-core Xeon server)?

The server is Ubuntu 8.04 LTS 64-bit, running postfix, with amavis-new (scanning with clam-av and spamassassin), and passing messages into a Courier-IMAP Maildir structure using maildrop.

Any suggestions on where to look for a cause?

Stephen

---

### Post by barti on 2009-06-26
After further investigation, it looks like this is actually an issue with NFS - the Maildirs are stored on another server, and mounted as an NFS volume. Carrying out any operations on the mounted volume takes a long time (which it shouldn't, as both servers are directly connected via a patch lead between their gigabit Ethernet interfaces).

The volume is mounted in /etc/fstab with the following:

```
192.168.255.1:/mnt/maildrive    /mnt/maildrive  nfs     rw,hard,sync,intr       0       0
```

and that is exported on the other server with this:

```
/mnt/maildrive 192.168.255.2(rw,sync,no_subtree_check)
```

I've had a look around, and I think they should be correct - unless anyone has other suggestions?

Stephen

---

