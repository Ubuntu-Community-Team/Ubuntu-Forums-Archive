---
title: "LDAP Authentication Apache2"
date: 2015-08-02
forum: Server Platforms
---

### Post by dmytro2 on 2015-08-02
Hello everyone) I'm having a problem with setting ldap authentication up on apache2 web server which runs on ubuntu server 15.04. Right now I managed to make apache2 to show authentication form each time anyone accesses site, but I can't go any further (the form just appears again). Could anyone please help me? Thanks)

P.S.
Here is some additional info:

I access site on host via http protocol. 

apache2 error.log messages:
```
[auth_basic:error] [pid 18013] [client x.x.x.x:62042] AH01618: user username@mailshost not found: /

[auth_basic:error] [pid 17671] [client x.x.x.x:61789] AH01618: user username not found: /
```

.htaccess content:
```
AuthType Basic
AuthBasicProvider ldap
AuthName "Some text for pop up window"
AuthLDAPURL ldap://my.host.address:389/o=XDS,ou=users?mail
AuthUserFile /dev/null
require valid-user
```


Message displayed in browser:
[COLOR=#000000][FONT=Times New Roman]This server could not verify that you are authorized to access the document requested. Either you supplied the wrong credentials (e.g., bad password), or your browser doesn't understand how to supply the credentials required.[/FONT][/COLOR]

---

### Post by volkswagner on 2015-08-02
Shouldn't you be using localhost or local ip if LDAP is another machine on same LAN?
```
AuthLDAPURL ldap://localhost:389/o=XDS,ou=users?mail
```

I don't think you should be exposing port 389 to public, so I wouldn't open that on your router (which would need to occur with your current configuration).
EDIT: or your local DNS would need to have an A record mapping my.host.address to a local LAN address.

---

### Post by dmytro2 on 2015-08-02
Thanks for your reply) I had my config updated according to your advice) But event though I still have the original problem.

---

