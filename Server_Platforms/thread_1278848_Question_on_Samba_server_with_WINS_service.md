---
title: "Question on Samba server with WINS service"
date: 2009-09-30
forum: Server Platforms
---

### Post by cpthk on 2009-09-30
I am setting up a samba server with WINS service. I set:
```
wins support = yes
name resolve order = lmhosts host wins bcast
```

And then I created the lmhosts file under /etc/samba/lmhosts with info in short:
```
192.168.1.5 TESTPC
...
```

I found that when I start samba server, I check the file /var/lib/samba/wins.dat, I did not see those data in lmhosts file. It only has the samba's hostname and its workgroup name.

I then found that I have to go to every computer and setup WINS server address in the network connections, then restart(or give nbtstat -RR) to make wins.dat file show up each computer name and ip address. Isn't samba suppose to read lmhosts file upon startup? It seems like samba doesn't read the lmhosts file at all.

Anyone know the reason?

Thanks.

---

