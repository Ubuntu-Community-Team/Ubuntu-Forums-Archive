---
title: "Multiple Virtual Domains with Roundcube"
date: 2009-02-23
forum: Server Platforms
---

### Post by btaylor101 on 2009-02-23
I have a working Postfix/Courier/Roundcube installation and I am trying to add another domain. I was able to do this successfully and send/receive email from both domains. The question I have is setting up Roundcube to only accept the domain that matches the website. I want webmail.mydomain.com to only allow logins with email addresses from [email]user@mydomain.com[/email] and webmail.mydomain2.net to only allow logins with email address from [email]user@mydomain2.net[/email]. The necessary configs are posted below. If anyone can help that would be great.


main.inc.php
> $rcmail_config['include_host_config'] = array(
        'webmail.mydomain.com' => config1_config.inc.php',
        'webmail.mydomain2.net' => config2_config.inc.php'

config1_config.inc.php
> $rcmail_config['username_domain'] = 'mydomain.com';

config2_config.inc.php
> $rcmail_config['username_domain'] = 'mydomain2.net';

---

### Post by btaylor101 on 2009-02-26
Anyone have an idea about this one?

---

### Post by iceman on 2009-10-18
i have the same problem... have you resolved?

---

