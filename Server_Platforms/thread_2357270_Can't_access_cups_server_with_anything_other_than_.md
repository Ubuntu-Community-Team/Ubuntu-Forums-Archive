---
title: "Can't access cups server with anything other than ip address"
date: 2017-03-31
forum: Server Platforms
---

### Post by Tadaen_Sylvermane on 2017-03-31
Ubuntu 16.04.2 Current updates as of 2017/3/31 @ 0832.

I have a dns server so I can resolve names instead of ip addresses on my lan. This was mainly done to simplify my minecraft servers. However on my laptop I cannot connect to the print server with the server name as  specified in the dns server, it gives "Bad Request" error. I can only connect via the actual ip address. This is true for both connecting my laptop to the print server and accessing the admin page on the server from my browser... How can I get it to work with the fqdn instead of an ip address?

*EDIT* As usual I should have googled first :/ sorry for the somewhat useless post. However the answer is to add a server alias line to the bottom of the /etc/cups/cupsd.conf file. This is what I added to my file to make the fqdn work. 

```

ServerAlias failbox.mylan.home
```

[Source]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/516018/comments/7")

---

