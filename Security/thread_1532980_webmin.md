---
title: "webmin"
date: 2010-07-17
forum: Security
---

### Post by =ChAoS= on 2010-07-17
Hi i just installed webmin to help with hosting my own websites. Its all a bit new to me but i understand some of it. After i nstalled it i was told i could log in with my username and password that was the same as i use to log into my remote ubuntu machine. When i enter https://<my ip>.com i get this warning ...
 
**There is a problem with this website's security certificate.**
 
I continued anyway and entered my user name and password and it seemed that everything was ok and worked like it was supposed to. Should i just ignore this and carry on?
 
Sorry for the dumb question as i don't know anything about certificates and also sorry if i posted this in the wrong place.
 
Thanks =ChAoS=

---

### Post by timothy_tim on 2010-07-17
It's because of the SSL-certificate isn't issued by a well known Certificate Authority.
You could check the certificate to confirm this.

---

### Post by bodhi.zazen on 2010-07-17
[QUOTE==ChAoS]I continued anyway and entered my user name and password and it seemed that everything was ok and worked like it was supposed to. Should i just ignore this and carry on?[/QUOTE]

yes.

If you have the interest, take a look at https (ssl) certificates.

[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html]("http://www.tc.umn.edu/%7Ebrams006/selfsign_ubuntu.html")

---

### Post by =ChAoS= on 2010-07-17
Thanks for the reply. I'm looking into the link above now.

---

### Post by anomie on 2010-07-19
If you do opt to get a CA-signed cert (or even a self-signed one, for that matter), you can configure Webmin to use them. 

Webmin -> Webmin Configuration -> SSL Encryption

---

### Post by i.r.id10t on 2010-07-20
StartSSL gives free "real" certs...

---

