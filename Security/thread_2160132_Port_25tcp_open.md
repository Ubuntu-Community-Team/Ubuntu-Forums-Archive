---
title: "Port 25/tcp open ?"
date: 2013-07-05
forum: Security
---

### Post by cogset on 2013-07-05
I've always seen port 25/tcp open and used by smtp when running nmap on my computer,and I've always assumed it was needed for Thunderbird (please note this is not a server,just a normal desktop pc):later I've realized it is actually used by the service exim4 and that I can stop said service and close that port in the firewall too,and Thunderbird still works.
So the obvious question is,why was that port open and exim4 running? Is that the default for a normal Ubuntu installation? 
Anything unusual that I should check? 
Lastly,instead of stopping exim4 (although,with port 25 blocked,maybe I shouldn't bother) from a terminal,how can I disable it on boot?

---

### Post by CharlesA on 2013-07-05
If you don't need it purge it.

```
sudo apt-get purge exim4*
```

If this is a desktop install, it shouldn't be installed unless you installed something like smartmontools, which list a MTA (Mail transfer agent, exim/postfix/sendmail) as a dependency.

---

### Post by cogset on 2013-07-06
Thanks,it has indeed  been installed as a dependency/recommended package but probably not only for smartmontools:upon simulating the removal of exim4* packages,rkhunter gets removed as well,apparently it also needs exim4.
So I'll have to leave it installed and disable it on boot,I suppose:can I do this ?

---

### Post by CharlesA on 2013-07-06
The easiest way is to just remove the execute permission from the file in /etc/init.d, but that is not necessarily the "right" way.

As far as the right way go, look at update-rc.d:
[http://www.tin.org/bin/man.cgi?section=8&topic=update-rc.d](http://www.tin.org/bin/man.cgi?section=8&topic=update-rc.d)

---

### Post by cogset on 2013-09-03
Since I don't need this exim4 service at all,I've done it properly (at least,that was the plan) and removed it at boot without uninstalling it with ```
sudo update-rc.d exim4 remove 
```so thanks for pointing me in the right direction.

---

### Post by cariboo on 2013-09-03
Please be aware that running nmap locally on a system will give you different results than when run from a remote system. Running nmap on my server locally gives me the following results:

```
nmap localhost

Starting Nmap 5.21 ( http://nmap.org ) at 2013-09-03 11:36 PDT
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00024s latency).
Not shown: 991 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
25/tcp   open  smtp
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs
3306/tcp open  mysql
8200/tcp open  unknown
```

While running nmap from my main system, gives me the following result:

```
 nmap willy

Starting Nmap 6.25 ( http://nmap.org ) at 2013-09-03 11:16 PDT
Nmap scan report for willy (192.168.0.205)
Host is up (0.00031s latency).
Not shown: 993 closed ports
PORT     STATE SERVICE
22/tcp   open  ssh
80/tcp   open  http
111/tcp  open  rpcbind
139/tcp  open  netbios-ssn
445/tcp  open  microsoft-ds
2049/tcp open  nfs
8200/tcp open  trivnet1
```

As you can see from the above results, I have an MTA running, that is only accessible locally, in my case I use logwatch, and check the messages locally on my server. Removing exim4 may render some utilities useless.

---

### Post by cogset on 2013-09-06
I think you're right,every now and then I do see some mail errors in the logs:on the other end,I run rkhunter manually and I don't think I need mail messages from it-so I can probably live with this.

But you've brought up an interesting point,very likely port 25 with exim4 running was actually open only locally:I'll have to restart this service and scan this pc from another one to verify.

---

