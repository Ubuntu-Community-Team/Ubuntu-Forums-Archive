---
title: "Postfix: delete recipients from mailq?"
date: 2007-08-14
forum: Server Platforms
---

### Post by qrwe on 2007-08-14
Hello,

I have a list of spammers in my my mailq on my MTA, which is trying to send to the the same recipient. I want to delete them using a for-loop and the "postsuper -d <mail-id>" command. The problem is that mailq adresses the recipients on a different row than the mail-ID, as shown:

61A6F3A829B 2838 Tue Aug  7 06:53:10 [email]spammer1@uglydomain.com[/email]
                                         [email]recipient@mydomain.com[/email]
B9B573A8435 2823 Tue Aug  7 21:49:57 [email]spammer2@awfuldomain.com[/email]
                                         [email]recipient@mydomain.com[/email]

..therefor, i can't just grep and awk my way to the mailq-id, which is the first word on the first line. Does anyone have a suggestion how to make my system to look for the second row (the recipient) and then get the mailq-id from the first row out of that information?
Kind regards!

---

### Post by Mr. C. on 2007-08-14
Here's a quick perl script that will join the recipients after the sender.  It handles multiple recipients.

```
#!/usr/bin/perl

undef $/;
$_ = <>;

s/\n^(^\S+[@]\S+)/ \1/gms ;

print "$_";
```

```
$ mailq 
61A6F3A829B 2838 Tue Aug 7 06:53:10 spammer1@uglydomain.com
recipient1@mydomain.com
B9B573A8435 2823 Tue Aug 7 21:49:57 spammer2@awfuldomain.com
recipient2@mydomain.com
recipient3@mydomain.com
$ mailq  | mailqjoin.pl
61A6F3A829B 2838 Tue Aug 7 06:53:10 spammer1@uglydomain.com recipient1@mydomain.com
B9B573A8435 2823 Tue Aug 7 21:49:57 spammer2@awfuldomain.com recipient2@mydomain.com recipient3@mydomain.com
```

You haven't said explicitly what you want to use as input. An email address ?  The script above can be easily modified to output a list of QIDs given an sender email address, or you can pipe it to other filtering programs.

MrC

---

### Post by qrwe on 2007-08-20
Thanks very much! I'll try this out (and modify it to fit my need if necessary).

---

