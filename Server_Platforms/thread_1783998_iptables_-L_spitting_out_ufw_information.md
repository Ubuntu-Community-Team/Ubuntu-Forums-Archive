---
title: "iptables -L spitting out ufw information"
date: 2011-06-16
forum: Server Platforms
---

### Post by deanklear on 2011-06-16
Hello,

Though I have uninstalled and rm -rf'ed everything I can find having to do with ufw, I am still getting weird output from iptables -L

If I type in

```
iptables -F
iptables -Z
iptables -L
```

I should get 

```
# iptables --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Which I do get, without any current routing information, followed by

```
Chain ufw-after-forward (0 references)
target prot opt source destination
```

and about 15 more entries. Does anyone have any ideas? Using 11.04 Server 64-bit.

---

### Post by Toz on 2011-06-16
Have a look at: [http://www.fistagon.us/2011/01/22/the-complicated-process-for-removing-the-uncomplicated-firewall/]("http://www.fistagon.us/2011/01/22/the-complicated-process-for-removing-the-uncomplicated-firewall/")

---

### Post by deanklear on 2011-06-19
Thank you. I was not aware that iptables works only on the *filter table by default, so you must specify the other tables using -t like so:

```
iptables --flush
iptables -t net --flush
iptables -t mangle --flush

```

Then I saved the flushed table by

```
iptables-save > /etc/flush
```

which I use to reset all the tables by issuing

```
iptables-restore /etc/flush
```

---

