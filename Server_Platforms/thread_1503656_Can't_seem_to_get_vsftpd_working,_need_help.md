---
title: "Can't seem to get vsftpd working, need help"
date: 2010-06-07
forum: Server Platforms
---

### Post by bhrunoh on 2010-06-07
Hi,

I can't figure out how to connect to vsftpd via internet, I'm new to linux OS.

I set up vsftpd to allow local accounts by uncommenting :
  local_enable=YES
  write_enable=YES
and I commented 
  #anonymous_enable=YES
And I restarted vsftpd

When I connect from localhost using my system account "username" and password "xxxxxx" from localhost and from the local network it works just fine (127.0.0.1 and 192.168.1.15)

I configured port forwarding on the router. But when I connect over the internet  (using my public ip adress 41.100.214.xxx), I can reach my computer and I'm promted to enter my username and password. But a that time I always get this message "403 Incorrect login"...... after entering the password. While the same credentials works fine in local network and localhost, they do not work over internet.

What can be the problem, need help
Thanks in advance

---

### Post by Bachstelze on 2010-06-07
Using FTP behind a router is a royal pain. If you can use SFTP (i.e. SSH file transfers), you'd really be better off doing so.

---

