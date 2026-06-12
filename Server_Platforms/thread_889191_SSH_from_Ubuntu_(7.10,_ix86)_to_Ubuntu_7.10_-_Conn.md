---
title: "SSH from Ubuntu (7.10, ix86) to Ubuntu 7.10 - Connection Closed"
date: 2008-08-13
forum: Server Platforms
---

### Post by bprof on 2008-08-13
I am trying to establish an SSH connection from an Ubuntu 7.10(ix86) server to another Ubuntu 7.10 server.


The first attempt resulted in the following message,

The authenticity of host '10.10.10.110 (10.10.10.110)' can't be established. RSA key fingerprint is 44:da:4b:d7:43:de:ed:73:4b:3a:cc:52:69:25:6f:11.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.10.10.110' (RSA) to the list of known hosts.
Connection closed by 10.10.10.110

The second attempt (with the '~/.ssh/known_hosts' file now in place) results in the message,

Connection closed by 10.10.10.110

The SSHD daemon is active on the both servers using the default port of 22. 

Any help?

Thanks!

---

### Post by windependence on 2008-08-14
What user are you trying to log on as?

Is there anything in the logs? /var/log/auth.log

Try this from the server: 'ssh myusername@localhost'

If it lets you in then there's something wrong with your network or firewall.

If it does NOT let you in then there's something wrong with your configuration or your permissions.

I believe you can also run the server in verbose mode to get more detailed debugging information.

-Tim

---

