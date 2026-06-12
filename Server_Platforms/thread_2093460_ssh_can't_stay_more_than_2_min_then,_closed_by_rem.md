---
title: "ssh can't stay more than 2 min then, closed by remote host,why?"
date: 2012-12-10
forum: Server Platforms
---

### Post by wingeong on 2012-12-10
Dear,

I always can't login my linode VPS ssh account.
Even I can login to my server, it can't stay more than 2 mintures, then the server told me: 
ssh_exchange_identification: Connection closed by remote host.

It seems my sshd service can't normally start up when my server boot. Then all my website can't be visited by my clients. It's a big PROBLEM!!

Would anyone help me to URGENTLY SOLVE THE PROBLEMS? WHAT CAN I DO ?

BELOW IS THE ERROR INFORMATION:

1. WHEN I FIRSTLY LOGIN AND THEN USE SCP TO TRANSFER A SMALL FILE, ERROR HAPPEN:
mypc~# sudo scp /var/run/nginx.pid myaccount@myip:/var/run/
ssh_exchange_identification: Connection closed by remote host

2. NEXT TIME WHEN I LOGIN, I ALWAYS FAIL TO LOGIN TO MY SERVER NOW.
mypc~# sudo ssh myaccount@myip
ssh_exchange_identification: Connection closed by remote host

---

### Post by tgalati4 on 2012-12-10
Try ssh with verbose switches:

```
ssh -v
or
ssh -vv
or
ssh -vvv

```

Perhaps you can cut and paste any messages of interest.

Also check your logs in /var/log, especially auth.log for ssh problems.

Also, it's not clear why you need sudo to perform scp and ssh commands to a remote server.  sudo would imply root privileges and permissions on the remote server and that would definitely cause connection problems on a hosted site.

Once you are logged into your hosted service, then you can sudo within that account to perform administrative/root actions.

---

### Post by chadk5utc on 2012-12-10
Are you using the default port 22? or another?
do you have a copy of the config?
is there a hosts.deny setup that could be blocking?

---

