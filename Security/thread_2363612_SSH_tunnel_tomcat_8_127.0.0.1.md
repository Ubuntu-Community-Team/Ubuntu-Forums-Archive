---
title: "SSH tunnel tomcat 8 127.0.0.1"
date: 2017-06-12
forum: Security
---

### Post by Drenriza on 2017-06-12
I have installed a home Tomcat 8 server, this server has an admin interface on **IP:8080/manager/html** that i would like to connect to.
But by default Tomcat 8 only allow local connections to use this interface
[LIST]
[*]127.0.0.1
[*]::1
[*]0:0:0:0:0:0:0:1
[/LIST]

I dont want to soften Tomcat's security policy and would instead like to create an SSH tunnel,
that allow me to make requests as if i am 127.0.0.1 on the remote server on port 8080.

I believe i need to make a local-port-forwarding but i am not sure how.

Anyone who can advice me on how to achieve this?

Thanks on advance
Kind regards

---

### Post by Drenriza on 2017-06-12
So a solution came to me after a few hours of doing other stuff.
```
ssh -L 8080:127.0.0.1:8080 [serverSSHUser]@[serverIP/Hostname]
```

url: [http://localhost:8080](http://localhost:8080)

---

### Post by LastDino on 2017-06-12
Thanks for posting solution, also please mark the thread as solved so others will get answer too from this solution

---

