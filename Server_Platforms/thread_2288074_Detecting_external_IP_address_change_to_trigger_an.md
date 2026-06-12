---
title: "Detecting external IP address change to trigger an incron job"
date: 2015-07-24
forum: Server Platforms
---

### Post by ChrisRChamberlain on 2015-07-24
Hi all

If this has been solved before, apologies, and a link would be appreciated.

Currently using Ubuntu Server 14.04 LTS and have a cron job running every 5 minutes that checks for changes to the external IP address.

If changed, script runs updating DNS servers at xyz.com, email is sent, etc.

Would prefer this to be an incron job but not sure where in the file system such a change might be detected?

TIA

---

### Post by Lars Noodén on 2015-07-24
What level of external IP address?  Do you mean on one of the machine's own interfaces or out on a router somewhere between your machine and the Internet?

Would [ddclient](http://manpages.ubuntu.com/manpages/trusty/en/man8/ddclient.8.html) work for you?  You'd need an account at a dynamic DNS service but then you could point a CNAME at the A name provided by the service.

---

### Post by ChrisRChamberlain on 2015-07-24
Lars Noodén

Thanks for your reply
> out on a router somewhere between your machine and the Internet
As far as ddclient is concerned, would prefer to use the existing script, minus its IP address checking procedure, but triggered by incron as opposed to cron.

---

### Post by Lars Noodén on 2015-07-24
incron can only work with changes to local files or directories.  Something like the external IP number is out of reach if it is on another machine.

---

### Post by ChrisRChamberlain on 2015-07-24
In this thread, [https://bbs.archlinux.org/viewtopic.php?id=89854](https://bbs.archlinux.org/viewtopic.php?id=89854), which discusses the same topic, there is mentioned in post #3 >  But if it is a ADSL connection, why not use a script in /etc/ppp/ip-up.local?
This way, any time your ppp connection is executed (when ipaddress changes), you can run anything you want (a firewall, a script sending your new ip... whatever).
This is the way I do it in my home system.I read that to indicate there would be a file content change which might be used to trigger an incron job? 

The server sits behind a conventional router with port forwarding so maybe that's an incorrect interpretation?

---

