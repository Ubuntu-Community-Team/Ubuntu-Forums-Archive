---
title: "sensible emain config for home LAN (I use gmail)"
date: 2011-01-16
forum: Server Platforms
---

### Post by HankB on 2011-01-16
I'd like to get a sensible email configuration setup on my home LAN. At present, every time I am presented with the prompt to configure postfix, I select no configuration because I don't know how to proceed.

Ordinarily I use gmail for my personal email needs. What I would like is some email configuration on the machines I manage on our home LAN that would forward locally generated email to my gmail account. This would be stuff like notifications from system tools like cron and smartmon. I would also include email notification in some of the things I custom script such as backups.

What I have:
 - file server (running 10.04 LTS server)
 - several laptops used by various family members
 - desktop

Laptops and desktops run more or less current versions of Ubuntu. Laptops may not always be on the home LAN but email could wait until they return home.

I found this description [http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/](http://www.marksanborn.net/linux/send-mail-postfix-through-gmails-smtp-on-a-ubuntu-lts-server/) that seems to be part of the solution. I believe I could set that up on my server and use it to forward email to gmail for further transport (usually to me.)

Other parts I think I would need are:

[LIST]
[*]~/.forward files on each PC to forward all incoming email to <myaccount>@gmail.com
[*]check config to make sure all admin related email goes to my user.
[*]postconfig which specifies that email is sent to my mail server.
[/LIST]

Does this make sense or over-complicating this?

thanks,
hank

Edit: Maybe this tutorial is more appropriate: [http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/](http://ubuntu-tutorials.com/2008/11/11/relaying-postfix-smtp-via-smtpgmailcom/)

---

