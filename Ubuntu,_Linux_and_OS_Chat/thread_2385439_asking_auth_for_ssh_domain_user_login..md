---
title: "asking auth for ssh domain user login."
date: 2018-02-20
forum: Ubuntu, Linux and OS Chat
---

### Post by kbhaskar006 on 2018-02-20
Hi guys,
we have domain user accounts and we trying to login by using the "ssh domainuser@host". But i need to login with out password to the user account.
is there any procedure to login without password. please help me on this.

---

### Post by mastablasta on 2018-02-20
you can use keys. 

about SSH:
[https://help.ubuntu.com/lts/serverguide/openssh-server.html](https://help.ubuntu.com/lts/serverguide/openssh-server.html)

Configuring SSH server:
[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)


Using Keys:
[https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

---

### Post by mastablasta on 2018-02-21
when using keys both windows machines need to have the user's (private) key. 

of course for local use you can also set it up to use only passwords. in that case it should work from any PC or phone or whatever as long as the login password is correct.

if you are still getting permission dedied then check the SSH settings on server. permission (authentication) and ssh server logs will also tell you what is going on server in more detail. you can use them to pinpoint the issue.

---

