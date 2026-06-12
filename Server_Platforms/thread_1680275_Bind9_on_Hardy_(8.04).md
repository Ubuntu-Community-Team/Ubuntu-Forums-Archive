---
title: "Bind9 on Hardy (8.04)"
date: 2011-02-02
forum: Server Platforms
---

### Post by volvolinux on 2011-02-02
Hello
 
I installed bind 9 on ubuntu 8.04. Why 8.04? , cause I am using openvz on 8.04...which is not offical supported in 10.04.
 
the bind goes well except an issue with "rndc"
 
root@dnsm01:/etc/bind# /etc/init.d/bind9 stop
* Stopping domain name service... bind rndc: connection to remote host closed
This may indicate that
* the remote server is using an older version of the command protocol,
* this host is not authorized to connect,
* the clocks are not syncronized, or
* the key is invalid.
 
I know it maybe the key mismatch, but I have checked it... it is correct:
 
 
-----------------------------------------------------------------------
root@dnsm01:/etc/bind# cat named.conf
key "rndc-key" {
algorithm hmac-md5;
secret "[COLOR=blue]AHBj6DCw9SsKe5nZR0UMsw==[/COLOR]";
};
controls {
inet 127.0.0.1 port 953
allow { 127.0.0.1; } keys { "rndc-key"; };
};
------------------------------------------------------------------------
 
root@dnsm01:/etc/bind# cat rndc.conf
key "rndc-key" {
algorithm hmac-md5;
secret "[COLOR=blue]AHBj6DCw9SsKe5nZR0UMsw==[/COLOR]";
};
options {
default-key "rndc-key";
default-server 127.0.0.1;
default-port 953;
};
------------------------------------------------------------------------
 
root@dnsm01:/etc/bind# cat rndc.key
key "rndc-key" {
algorithm hmac-md5;
secret "[COLOR=blue]AHBj6DCw9SsKe5nZR0UMsw==";[/COLOR]
};
------------------------------------------------------------------------
 
I also find a post in [http://www.linuxquestions.org/questions/linux-server-73/ubuntu-bind9-problem-657286/](http://www.linuxquestions.org/questions/linux-server-73/ubuntu-bind9-problem-657286/)
 
this guy has the same problem as me, but the probem wasn't solved at last.
 
Do some one has the same problem as me? 
 
THanks in advace.

---

### Post by terazen on 2011-02-02
I have had that problem twice where a reboot fixed it strangely enough.  Have you done that yet?

---

### Post by volvolinux on 2011-02-02
Hello
 
Oh,- -~!

The reboot do solve the problem. it is weird.... then make the linux to be a "windows" that the reboot solve the problem always....
 
Thanks.~

---

