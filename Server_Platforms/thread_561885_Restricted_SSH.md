---
title: "Restricted SSH"
date: 2007-09-28
forum: Server Platforms
---

### Post by galeron on 2007-09-28
Hi guys,

I need some help here.

Over the next few months, I'll be allowing a couple of people to SSH into my server. The only 2 functions that they need to carry out are telnet and ssh. No local storage is needed.

Is there any way for me to restrict them to these 2 commands only? It would be even better if I could also restrict their telnet/ssh destinations.

Thanks!

---

### Post by steve.horsley on 2007-09-28
This might help. I guess you set it up as their login shell (users and groups configuration) and set their .bashrc to set the path to a very limited set of commands. Try googling for more info on how to use it. The first link in a google search for "configure rbash" looks good: [http://www.securityfocus.com/infocus/1575](http://www.securityfocus.com/infocus/1575)

---

### Post by HermanAB on 2007-09-28
Hmm, you should follow the Ubuntu sudo model:
Set up OpenSSH for access.  Disable login for root in /etc/ssh/sshd_config, then configure a group and allow this group to run only the one or two programs that you want them to run in the file /etc/sudoers and make the restricted users members of that group.

This is really the only way to do what you want.  Usually there are multiple solutions to a problem, but in this case I think there is only one.

Cheers,

Herman

---

