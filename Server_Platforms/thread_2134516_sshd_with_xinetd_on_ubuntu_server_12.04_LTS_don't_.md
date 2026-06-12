---
title: "sshd with xinetd on ubuntu server 12.04 LTS don't work"
date: 2013-04-11
forum: Server Platforms
---

### Post by ensuspension on 2013-04-11
hello,
I'm trying to manage sshd with xinetd instead of managing it with upstart. So I have modified /etc/init/ssh.conf for it. I have reboot the machine and it's ok, I can't anymore connect to the machine with ssh.

Now, I configure xinetd to manage sshd by create a file /etc/xinetd.d/ssh
```

service ssh 
{
   disable            = no             
   socket_type     = stream
   port                = 22
   wait                = no
   user                = root
  server               = /usr/sbin/sshd
  server_args        = -i
 }

```

and I restart xinetd
```
service xinetd restart
```

And, it doesn't work! In can't connect to my machine by ssh! :(

For information
```

cat /etc/services | grep ssh
ssh        22/tcp 
ssh        22/udp

```

And 
```

netstat -an | grep 22
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN 

```

I there somebody who can explain to me what's wrong in my configuration?

Thanks a lot

PS : xinetd run well because for a test, I have configured telnetd with xinetd.

---

### Post by ensuspension on 2013-04-13
I have found that the problem comes from the missing /var/run/sshd file when sshd is started by xinetd.
the bug is known in former versions : [https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/45234](https://bugs.launchpad.net/ubuntu/+source/openssh/+bug/45234)

It's possible to solve the problem by writing lines in /etc/rc.local
```

[LEFT][COLOR=#333333][FONT=Ubuntu Mono]if [ ! -d /var/run/sshd ]; then[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]        mkdir /var/run/sshd[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]        chmod 0755 /var/run/sshd[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]    fi[/FONT][/COLOR][/LEFT]

```

I hope this comment helps.

---

