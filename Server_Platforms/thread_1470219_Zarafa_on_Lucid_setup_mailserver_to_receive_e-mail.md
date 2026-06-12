---
title: "Zarafa on Lucid: setup mailserver to receive e-mail"
date: 2010-05-02
forum: Server Platforms
---

### Post by ahbart on 2010-05-02
I hope someone can help me setting up receiving e-mail on my home server. Ubuntu Lucid and Zarafa from repository.
Zarafa is running well. I can send e-mail via the relay smtp host from my ISP. 
But though the e-mail address should be correct (username@xxxx.dyndns.org) I never see this e-mail appear in zarafa inbox.
The e-mail reaches the server via an open 25 port forwarded to my server, but it seems postfix does not know how to handle it. Or is there something else going wrong here?
Below are my settings. These are the settings I added or edited. the rest is Ubuntu Lucid (10.04) standard.
Can someone help me please? It too me hours till now.
Bart

/etc/postfix/main.cf
```

myhostname = xxxx.dyndns.org
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = xxxx.dyndns.org, localhost.homeip.net, , localhost
relayhost = smtp.myisp.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all

mailbox_command = /usr/bin/zarafa-dagent "$USER"
mailbox_transport = zarafa: zarafa_destination_recipient_limit = 1

```

/etc/postfix/master.cf
```

zarafa unix – n n – 10 pipe flags= user=vmail argv=/usr/bin/zarafa-dagent ${user}
```

/etc/zarafa/server.cfg
```

..
local_admin_users	= root vmail
..
#  USER PLUGIN SETTINGS
user_plugin		= unix
user_plugin_config	= /etc/zarafa/unix.cfg
```

/etc/zarafa/unix.cfg
```

default_domain = xxxx.dyndns.org
```

/etc/default/zarafa-dagent
```

DAGENT_ENABLED=yes
```

/etc/hostname
```

xxxx.dyndns.org
```

/etc/host
```

127.0.0.1	localhost.localdomain	localhost
127.0.1.1	servername
192.168.0.10	xxxx.dyndns.org servername
```

/etc/mailname
```

xxxx.dyndns.org
```

---

### Post by ahbart on 2010-05-03
nobody a clue?

---

