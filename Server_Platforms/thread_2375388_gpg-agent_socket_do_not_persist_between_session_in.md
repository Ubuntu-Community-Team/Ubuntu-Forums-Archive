---
title: "gpg-agent socket do not persist between session in Ubuntu 17.10"
date: 2017-10-24
forum: Server Platforms
---

### Post by skualito2 on 2017-10-24
Hello,

I upgrade to 17.10 yesterday and now i had trouble with gpg-agent, it seems now **/run/user/PID/** is clean when user logout and so the gpg-agent socket disapear and when i re-log i can't connect to the running gpg-agent daemon.

I compare with a server in 17.04 and **/run/user/PID/** persist between session so is it a bug with 17.10 or a new behavior ? if so what is the new correct way to get a gpg-agent daemon who persist between session ?

Thanks in advance for your help !

---

