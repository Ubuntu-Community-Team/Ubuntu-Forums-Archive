---
title: "Strange network traffic.."
date: 2013-05-31
forum: Security
---

### Post by jonnyboysmithy on 2013-05-31
EDITED: solved.
didn't notice the traffic was coming from 6881...  which is my torrent client. stupid mistake.#-o

solved

---

### Post by sanderj on 2013-05-31
6881 is indeed the default bittorrent port... So check which processes are listening:

```
netstat -apon | grep -i listen | grep -vi listening
```

---

### Post by HermanAB on 2013-05-31
There are a few simple solutions to the problem:
htop
ps -e
kill -9
rm /usr/wherever/filename

With Linux, you have full control over your system, so stop the offending process and get rid of it.

---

### Post by jonnyboysmithy on 2013-05-31
Edited

---

### Post by sanderj on 2013-06-01
If you keep on editing your posts, I can't help you

---

### Post by jonnyboysmithy on 2013-06-01
On second thoughts I should have just left it as it was and posted another post.
I didn't notice that the traffic was coming from port 6881 on my computer. Stupid as it may seem. Yup :/
I wont edit them like I did before anymore. Sorry.

And on second thoughts that traffic shouldn't shown up after a reboot without having started anything other than terminal.

---

### Post by cariboo on 2013-06-02
I jailed a zero content post.

---

