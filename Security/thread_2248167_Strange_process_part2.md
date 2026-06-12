---
title: "Strange process part2"
date: 2014-10-13
forum: Security
---

### Post by kurogane2 on 2014-10-13
Hello,

I [previously]("http://ubuntuforums.org/showthread.php?t=2226673") talk about a problem with a process seems for the proporse of DDoSing now there is a new kiddo script same as IptabLes strategy

Here the new details of this script

```

# lsof -p 22005
COMMAND     PID USER   FD   TYPE    DEVICE SIZE/OFF    NODE NAME
ylhblcttd 22005 root  cwd    DIR     253,6    12288 3008769 /root
ylhblcttd 22005 root  rtd    DIR     253,6     4096       2 /
ylhblcttd 22005 root  txt    REG     253,6   676049  786098 /boot/ylhblcttdo
ylhblcttd 22005 root    0u   CHR       1,3      0t0    4176 /dev/null
ylhblcttd 22005 root    1u   CHR       1,3      0t0    4176 /dev/null
ylhblcttd 22005 root    2u   CHR       1,3      0t0    4176 /dev/null
ylhblcttd 22005 root    5u  IPv4 937371962      0t0     UDP *:50994

```

```

strings /boot/ylhblcttdo

```

[https://www.dropbox.com/s/go2o3rlqyf5h7d3/XOR.DDoS.txt](https://www.dropbox.com/s/go2o3rlqyf5h7d3/XOR.DDoS.txt)

This new script called [XOR.DDoS]("http://blog.malwaremustdie.org/2014/09/mmd-0028-2014-fuzzy-reversing-new-china.html"), i try to clean but for some reason when i kill the process and appears again under another name immediately.

So, i think there is another process/script is exec when the process killed appears something i'm not found anything yet.

I call the expert how to find that process.

---

### Post by unspawn on 2014-10-13
> **kurogane2 said:**
> I [previously]("http://ubuntuforums.org/showthread.php?t=2226673") talk about a problem with a process seems for the proporse of DDoSing now there is a new kiddo script same as IptabLes strategy Then with all due respect you haven't been paying attention: that was a root exploit. So that required immediate and decisive action. You should have isolated the machine, backed up whatever personal data you could verify later on, then reinstalled the OS from scratch, renewed all credentials and properly hardened your install before exposing it to (hostile) networks. Once integrity is compromised there should not be any thought of blithely "fixing" things.    *Note Linux may be free to use but using it should not be free of responsibilities.*

---

### Post by bashiergui on 2014-10-13
i will very generously provide you with the expert advice you're seeking, at no cost to you: 
> **unspawn said:**
> You should have isolated the machine, backed up whatever personal data you could verify later on, then reinstalled the OS from scratch, renewed all credentials and properly hardened your install before exposing it to (hostile) networks.  Or to simplify....
[SIZE=7][B]Reimage.
[/B][/SIZE]

---

