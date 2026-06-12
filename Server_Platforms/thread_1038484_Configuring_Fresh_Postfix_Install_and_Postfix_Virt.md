---
title: "Configuring Fresh Postfix Install and Postfix Virtual Hosts"
date: 2009-01-12
forum: Server Platforms
---

### Post by ehull82 on 2009-01-12
**Cliff Notes:** New to Postfix, and not sure where to start with my configuration. I'm running multiple domains off of a single box. Used the default Postfix install from the 8.10 Server install. Read the community guide [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) and now I’m more confused.

**Details:**
I've set up an old machine to act as a LAMP + FTP + E-Mail server for multiple domains on my home ISP connection. I've configured the Virtual Hosts for my Apache2 server using [http://www.corey-m.com/blog/?p=315](http://www.corey-m.com/blog/?p=315) as a guide and they are running great.

I've run into some difficulty with Postfix though. I have no prior experience with running an e-mail server so this is completely new territory for me. When I initially installed Ubuntu on my system, I chose E-mail server as one of the configuration options so I know that Postfix and Dovecot are installed.

I'm using Namecheap as my Registrar and currently have the mail settings set to forward to my Gmail account. I'd like to be able to set up postfix to work for my domains (*personaldomain*.com and *projectdomain*.net) as full fledged e-mail servers. I plan to access them through a POP3 connection using my g-mail account and its "Get mail" feature.

I read through the [https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix) guide but I’m even more confused as to what I should do. The server’s name is eh-server and I have it set as the DMZ computer on my ISP’s DSL Modem/Router because that is the only way that it will allow external connections.

Using the community guide I have set the following settings:
```
General type of mail configuration: Internet Site
System mail name: eh-server.local
Root and postmaster mail recipient: <admin_user_name>
Other destinations for mail: eh-server.local, localhost, mail.*personaldomain*.com, mail.*projectdomain*.net
Force synchronous updates on mail queue?: No
Local networks: 127.0.0.0/8
Procmail: Yes
Mialbox size limit (bytes): 0
Local address extension character: +
Internet protocols to use: all
```

Any further assistance is most appreciated!

---

