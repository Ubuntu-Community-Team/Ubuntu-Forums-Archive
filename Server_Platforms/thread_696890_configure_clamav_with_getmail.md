---
title: "configure clamav with getmail"
date: 2008-02-14
forum: Server Platforms
---

### Post by bmorency on 2008-02-14
HI,

I am trying to configure an email server that will download email from the ISP and scan the incoming mail with clamav then the user can use outlook to get the email. I am using getmail and postfix.

I can send and receive email thru outlook with this setup so far but clamscan will not scan attachements (or possibly not scan inside attachements). When I run getmail I have set it to be verbose but nothing displays on the screen. I have tested clamscan with zip files in my user's home directory. it will extract it, find the virus and delete the archive. Here is my getmailrc file in my home directory.

```

[retriever]

type = SimplePOP3Retriever
server = mail.server.com
username = user@domain.com
password = password

[destination]

type = Maildir
path = ~/Maildir/

[options]

delete = true
message_log = ~/.getmail/log

[filter-av]
type = Filter_classifier
path = /usr/bin/clamscan
arguments = ("-", "--remove","--verbose","--stdout",
        "--unzip=/usr/bin/unzip",
    "--unrar=/usr/bin/unrar",
    "--lha=/usr/bin/lha",
    "--jar=/usr/bin/unzip",
    "--tar=/usr/bin/tar",
    "--tgz=/usr/bin/tar")
exitcodes_keep = (0,1)

```


Does anyone know what I could be missing for clamscan to scan attachments?

Thanks for any help.

---

