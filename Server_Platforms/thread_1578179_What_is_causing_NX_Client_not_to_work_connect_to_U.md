---
title: "What is causing NX Client not to work connect to Ubuntu 10.4 running neatx"
date: 2010-09-20
forum: Server Platforms
---

### Post by cowmix on 2010-09-20
**Here's the client side log:**

NX> 203 NXSSH running with pid: 6862
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: server.acme.com on port: 2225
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.3.0 - GPL
NX> 105 Hello nxclient - version 3.3.0
NX> 134 Accepted protocol: 3.3.0
NX> 105 Set SHELL_MODE: SHELL
NX> 105 Set AUTH_MODE: PASSWORD
NX> 105 Login
NX> 101 User: bob
NX> 102 Password: **********
[B][COLOR="DarkRed"]connect /tmp/launch-URGDRj/org.x port 6000: Connection refused
[/COLOR][/B]NX> 280 Exiting on signal: 15
[B]
Here's the server:[/B]

==> auth.log <==
Sep 19 16:10:00 5am-oob-srvr su[6737]: Successful su for bob by nx
Sep 19 16:10:00 5am-oob-srvr su[6737]: + /dev/pts/4 nx:bob
Sep 19 16:10:00 5am-oob-srvr su[6737]: pam_unix(su:session): session opened for user bob by (uid=115)
Sep 19 16:10:00 5am-oob-srvr sshd[6722]: channel 3: open failed: administratively prohibited: open failed
==> debug <==
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'hello NXCLIENT - Version 3.3.0\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Hello nxclient - version 3.3.0\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG nxserver_login:111 Got client protocol version 3030000 ('3.3.0'), want 3030000
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 134 Accepted protocol: 3.3.0\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 105 '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'SET SHELL_MODE SHELL\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Set SHELL_MODE: SHELL\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 105 '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'SET AUTH_MODE PASSWORD\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Set AUTH_MODE: PASSWORD\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 105 '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'login\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Login\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 101 User: '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'bob\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'bob\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 102 Password: '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:225 <<< [hidden]
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> '**********\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG auth:50 Authenticating as 'bob', running ['/usr/lib/neatx/nxserver', '--proto=3030000', '--', 'bob']
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG auth:53 Auth command ['/usr/lib/neatx/ttysetup', '/bin/su', 'bob', '-c', 'cd && /usr/lib/neatx/nxserver --proto=3030000 -- bob']
==> messages <==
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: INFO nxserver_login:253 Trying login for user 'bob' using auth method 'su'
==> syslog <==
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'hello NXCLIENT - Version 3.3.0\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Hello nxclient - version 3.3.0\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG nxserver_login:111 Got client protocol version 3030000 ('3.3.0'), want 3030000
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 134 Accepted protocol: 3.3.0\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 105 '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'SET SHELL_MODE SHELL\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Set SHELL_MODE: SHELL\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 105 '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'SET AUTH_MODE PASSWORD\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Set AUTH_MODE: PASSWORD\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 105 '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'login\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Login\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 101 User: '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'bob\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'bob\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 102 Password: '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:225 <<< [hidden]
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> '**********\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: INFO nxserver_login:253 Trying login for user 'bob' using auth method 'su'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG auth:50 Authenticating as 'bob', running ['/usr/lib/neatx/nxserver', '--proto=3030000', '--', 'bob']
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG auth:53 Auth command ['/usr/lib/neatx/ttysetup', '/bin/su', 'bob', '-c', 'cd && /usr/lib/neatx/nxserver --proto=3030000 -- bob']
==> user.log <==
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'hello NXCLIENT - Version 3.3.0\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Hello nxclient - version 3.3.0\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG nxserver_login:111 Got client protocol version 3030000 ('3.3.0'), want 3030000
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 134 Accepted protocol: 3.3.0\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 105 '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'SET SHELL_MODE SHELL\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Set SHELL_MODE: SHELL\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 105 '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'SET AUTH_MODE PASSWORD\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Set AUTH_MODE: PASSWORD\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 105 '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'login\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'Login\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 101 User: '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:227 <<< 'bob\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'bob\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> 'NX> 102 Password: '
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:225 <<< [hidden]
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG protocol:172 >>> '**********\n'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: INFO nxserver_login:253 Trying login for user 'bob' using auth method 'su'
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG auth:50 Authenticating as 'bob', running ['/usr/lib/neatx/nxserver', '--proto=3030000', '--', 'bob']
Sep 19 16:09:59 5am-oob-srvr nxserver-login[6734]: DEBUG auth:53 Auth command ['/usr/lib/neatx/ttysetup', '/bin/su', 'bob', '-c', 'cd && /usr/lib/neatx/nxserver --proto=3030000 -- bob']
==> auth.log <==
Sep 19 16:10:00 5am-oob-srvr sshd[6634]: pam_unix(sshd:session): session closed for user nx
==> debug <==
Sep 19 16:10:00 5am-oob-srvr nxserver[6747]: DEBUG protocol:172 >>> 'NX> 103 Welcome to: server.acme.com user: bob\n'
Sep 19 16:10:00 5am-oob-srvr nxserver[6747]: DEBUG protocol:172 >>> 'NX> 105 '
==> messages <==
Sep 19 16:10:00 5am-oob-srvr nxserver[6747]: INFO nxserver:689 Starting nxserver for user bob
==> syslog <==
Sep 19 16:10:00 5am-oob-srvr nxserver[6747]: INFO nxserver:689 Starting nxserver for user bob
Sep 19 16:10:00 5am-oob-srvr nxserver[6747]: DEBUG protocol:172 >>> 'NX> 103 Welcome to: server.acme.com user: bob\n'
Sep 19 16:10:00 5am-oob-srvr nxserver[6747]: DEBUG protocol:172 >>> 'NX> 105 '
==> user.log <==
Sep 19 16:10:00 5am-oob-srvr nxserver[6747]: INFO nxserver:689 Starting nxserver for user bob
Sep 19 16:10:00 5am-oob-srvr nxserver[6747]: DEBUG protocol:172 >>> 'NX> 103 Welcome to: server.acme.com user: bob\n'
Sep 19 16:10:00 5am-oob-srvr nxserver[6747]: DEBUG protocol:172 >>> 'NX> 105 '

---

