---
title: "Security issue ??"
date: 2008-09-11
forum: Security
---

### Post by dplecto on 2008-09-11
Maybe it is just me being paranoid but, I was going through the authentication logs on my system and came across this;

**Sep 10 07:35:03 system1 sudo:     root : TTY=unknown ; PWD=/ ; USER=userx ; COMMAND=/usr/bin/gconftool --get /system/http_proxy/use_http_proxy**

The username, userx is a valid admin user that I use only when I have to fix the system. I know I haven't used that user for quiet sometime. 

I have a ssh server running that listens to a different port then the regular ssh port. My firewall logs shows no attempts made to connect via. ssh.  

The command "gconftool --get" seems to be pretty harmless - it simply returned a false value when I ran it. The reason I am getting suspicious is that, my pidgin connection got terminated sometimes during the night- it has never happened before. 

Anyway, how serious is this?? 

Thanks

---

### Post by Dr Small on 2008-09-11
Not serious at present, from what I can tell, but just keep watching the logs for futher evidence of something.

---

### Post by dplecto on 2008-09-11
Yeah. It just seems too harmless - I just hate when something goes on and i don't know about it.

---

