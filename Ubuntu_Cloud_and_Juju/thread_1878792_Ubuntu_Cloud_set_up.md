---
title: "Ubuntu Cloud set up"
date: 2011-11-10
forum: Ubuntu Cloud and Juju
---

### Post by scubablue on 2011-11-10
Hello,
we are starting our first Ubuntu Cloud Set up. After the installation of the CC and NC (2 servers) and configuring the access of the eucalyptus user everything looks good. 
But I keep getting this screen and it does not go anywhere any ideas?
Ubuntu Enterprise Cloud
The Ubuntu Enterprise Cloud runs on port 8443.
Redirecting...
 
I run netstat -ntulp
- 
tcp 0 0 0.0.0.0:8443 0.0.0.0:* LISTEN -

---

### Post by scubablue on 2011-11-13
I was able to connect to it from the local lan to the [https://10.150.252.40:8443](https://10.150.252.40:8443). I can SSH to the public IP of the CC but I cannot get to the [https://public](https://public) ip:8443 manager
 
Anything that I need to check to allow me access to the [https://public](https://public) ip:8443 ?
 
thanks

---

