---
title: "Can't login via SSH, access denied."
date: 2020-04-03
forum: Server Platforms
---

### Post by simonhk2 on 2020-04-03
I just installed Ubuntu Server 18.04 LTS. During setup I enabled the SSH server without a key.
After installation I was able to login using the credentials I created during the setup.

I got disconnected from SSH due to inactivity and now when I try to login I get "Access denied" after typing the password and hitting enter.

I can still logon to the machine locally using the same username and password.

- Firewall is disabled
- PasswordAuthentication is enabled in sshd_config
- Restarting sshd or the entire system makes no difference, still getting access denied
- Username and password is correct, works fine for local logon

What's up with that? 
Never seen anything like it before so I'm a bit lost in terms of troubleshooting. It worked fine and without any changes being made it just stopped working.

Any help appreciated!

Thanks!

Kind regards
Simon

---

### Post by TheFu on 2020-04-03
The hostname must be correct.
The permissions for the directory and files inside ~/.ssh/ must all be correct.
[https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections)
has steps.

---

### Post by simonhk2 on 2020-04-04
Thanks for the input!

---

