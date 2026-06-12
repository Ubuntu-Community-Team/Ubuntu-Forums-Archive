---
title: "how to test if ssh is up  and running - which tests are appropiate ?"
date: 2014-11-27
forum: Security
---

### Post by dilbert_one on 2014-11-27
hello  my dear ubuntu experts

i need to have ssh up and running. 

well i am just testing if the ssh works..

```



linux-70ce:/home/martin # lsof -i | grep ssh                                                                                                                                        
sshd       785   root    3u  IPv4  11213      0t0  TCP *:ssh (LISTEN)
sshd       785   root    4u  IPv6  11224      0t0  TCP *:ssh (LISTEN)
linux-70ce:/home/martin # ps aux | grep ssh
root       785  0.0  0.0   7440  2320 ?        Ss   19:16   0:00 /usr/sbin/sshd -D
martin    1545  0.0  0.0   5360  1080 ?        Ss   19:16   0:00 /usr/bin/gpg-agent --sh --daemon --write-env-file /home/martin/.gnupg/agent.info /usr/bin/ssh-agent /etc/X11/xinit/xinitrc
martin    1548  0.0  0.0   4180   420 ?        Ss   19:16   0:00 /usr/bin/ssh-agent /etc/X11/xinit/xinitrc
root      3345  0.0  0.0   4408   924 pts/1    S+   20:51   0:00 grep --color=auto ssh
linux-70ce:/home/martin # netstat -natp | grep ssh
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      785/sshd            
tcp        0      0 :::22                   :::*                    LISTEN      785/sshd            
linux-70ce:/home/martin # 


```

what  do you think?`

furthermore: well i could use use telnet to test low level stuff:
  
 what do you think? 
 
 if telnet (the low level stuff) runs i would know the DNS resolves, 
 the server is listening and the firewall allows the port through.

 
 love to her from you 
 greetings

---

### Post by bashiergui on 2014-11-27
I usually test it by trying to ssh from an external IP. 

You have telnet listening to the internet? Why?

---

### Post by HermanAB on 2014-11-28
$ telnet servername 22

$ ssh user@servername

---

