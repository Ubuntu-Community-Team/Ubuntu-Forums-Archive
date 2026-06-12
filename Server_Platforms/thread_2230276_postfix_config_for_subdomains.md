---
title: "postfix config for subdomains"
date: 2014-06-18
forum: Server Platforms
---

### Post by mlecho on 2014-06-18
I hope this is the right place for a question like this...we have an reply to email feature implemented, but having issues keeping things from production and staging separate.
Ultimately, i'd like to route all mail for two sub-domains to their respective script depending, on which subdomain receives the mail. 


messages.mydomain.com
stagingmessages.mydomain.com




Everything works for messages.mydomain.com, but not for stagingmeassages. i am getting a little confused on how to set up my main.cf and the maps for subdomain parsing. it's very likely that in all my research i've added perhaps too much to my main.cf


/etc/postfix/main.cf

```

myhostname = mydomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = $myhostname, /etc/postfix/domains 
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all


virtual_maps = hash:/etc/postfix/addresses
alias_maps = hash:/etc/aliases
inet_protocols = all

```


/etc/aliases

```

rails_mailer_staging:    "|/var/www/vhosts/admin.mydomain.com/htdocs/bin/mail_handler_staging.rb"
rails_mailer:        "|/var/www/vhosts/mydomain.com/htdocs/bin/mail_handler_production.rb"

```


/etc/postfix/domains 
```

messages.mydomain.com
stagingmessages.mydomain.com

```

/etc/postfix/addresses

```

messages.mydomian.com        DOMAIN
@messages.mydomian.com        rails_mailer


stagingmessages.mydomian.com    DOMAIN
@stagingmessages.mydomian.com     rails_mailer_staging

```

---

