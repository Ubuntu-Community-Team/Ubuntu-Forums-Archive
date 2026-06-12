---
title: "VSFTPD force SSL"
date: 2005-10-02
forum: Server Platforms
---

### Post by damonkohler on 2005-10-02
For some reason the configuration to force SSL connections on vsftpd is not working for me. I have it set up with virtual users using pam_userdb, and SSL is enabled and working, but I want to only allow SSL connections. Supposedly, force_local_data_ssl and force_local_logins_ssl (both of which default to YES) should enable this behavior. Anyone else having this problem? Or have any ideas why I'm having this problem? :)

---

### Post by damonkohler on 2005-10-02
Actually, just figured it out on a hunch. Turns out that if you use the username "ftp" (even if anonymous_enable=NO), then it "thinks" it's an anonymous connection as far as forcing SSL. Changed the username, now it forces SSL. Bug?

---

### Post by franke on 2006-01-31
Did you use the user ftp to connect you mean ?  

I cant get my ssl to work, I figured out that vsftpd doesn't start when I do enable_ssl=yes .. 

It says * Starting ftp server ....  but it never starts .
When I comment out enable_ssl=yes  it does indeed start and I can login. 

Any thoughts on why it doesn't start ??

---

### Post by damonkohler on 2006-02-02
Unfortunately it's been awhile since I set this up. So long in fact that the HD died and I had to start over and have not tried to set it up again yet! Sorry :( Nothing comes to mind.

---

### Post by franke on 2006-02-04
np, It worked out =).

---

### Post by hypatia on 2006-02-20
franke, any word on how you got things working?  i'm having the same trouble with trying to get vsftpd running in ssl/tls mode.

---

