---
title: "Namecheap squirrelmail help"
date: 2016-09-29
forum: Server Platforms
---

### Post by a09hopper on 2016-09-29
I  have set up squirrelmail before to host my own email but when I bought an actual domain from Namecheap.com it said when I entered the domain into the search bar that it could not be found. However it may just be I do not know how to set it up but any help would be appreciated.

---

### Post by SeijiSensei on 2016-09-29
Do you have the following records set up for your domain?

1)  An [MX record]("https://en.wikipedia.org/wiki/MX_record") that points to your server and designates it as the destination for your mail?

2)  An [A record]("https://en.wikipedia.org/wiki/List_of_DNS_record_types") that points your domain name to your host so that you can reach it over the web?  I suggest using a name like "mail.example.com" rather than just "example.com" for the host.

That's just the first step though.  You'll also need to install and configure a mail exchanger like Postfix or sendmail to handle inbound and outbound messages, and a POP/IMAP server like dovecot that enables mail clients, including Squirrelmail, to access the inboxes and any other user folders.  Then once that is set up, you'll also need to set up a web server like Apache to host Squirrelmail..  

Expect this to take at least a day or more of your time if you've never done anything like this before.

---

### Post by a09hopper on 2016-10-05
I was able to set it up in a couple of days and for a MX record what do I put in mail server and priority

---

### Post by a09hopper on 2016-10-05
Doesn't matter this thread can now be closed or solved as it now works

---

### Post by wildmanne39 on 2016-10-05
Please post the solution so any one else with the same issue may benefit from your answer.
Thanks

---

