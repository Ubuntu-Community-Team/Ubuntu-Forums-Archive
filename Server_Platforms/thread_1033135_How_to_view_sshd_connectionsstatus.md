---
title: "How to view sshd connections/status?"
date: 2009-01-07
forum: Server Platforms
---

### Post by xrvjorn on 2009-01-07
Is there a way to list/view all users who are connected via a file transfer client such as WinSCP, and to see the status of their file transfers?

---

### Post by windependence on 2009-01-07
```
nmap
tcpdump
who
users
netstat -tunva
```

-Tim

---

### Post by xrvjorn on 2009-02-11
Thanks for the tips, but they don't work.

When I try 'users' and 'who', they only show users using the ssh terminal window (putty in my case). Users logged in via e g WinSCP aren't visible. 

netstat -tunva shows connected IP's, but I can't see any user names. tcpdump shows a lot of info, but nothing about connected users. nmap shows me open ports, but no user info there either.

---

### Post by windependence on 2009-02-11
Well you could try also:

```
sudo ps aux | grep sshd
```

or see if this works:

```
lsof | grep sshd | grep TCP | cut -c18-28,70-
```

You could also install ntop for connections in real time, and last but not least look at the authlog.

-Tim

---

### Post by xrvjorn on 2009-02-11
That worked - thanks!

---

### Post by gtdaqua on 2009-02-11
```

last | head

```
That will also tell you who is currenty logged in from where (ip address).

---

