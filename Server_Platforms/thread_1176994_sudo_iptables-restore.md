---
title: "sudo iptables-restore"
date: 2009-06-02
forum: Server Platforms
---

### Post by goneskiing on 2009-06-02
I have a Hardy server - under a user I'm trying to do sudo iptables-restore ... and get a failed line 2 error - this didn't happen when originally done under root so it appears some problem doing it as an admin user.   Has anyone gotten this to work ?

---

### Post by MrWES on 2009-06-03
> **goneskiing said:**
> I have a Hardy server - under a user I'm trying to do sudo iptables-restore ... and get a failed line 2 error - this didn't happen when originally done under root so it appears some problem doing it as an admin user.   Has anyone gotten this to work ?

What is the output of 
```
sudo iptables -L
```

---

### Post by goneskiing on 2009-06-03
I'm not so big on publishing the firewall rules.  But are you implying there might be something there that is being blocked ?   Under the user I can access via ssh and perform other sudo tasks.  I thought it was more of a bug in the iptables version. 

Actually there seems a few things wrong with the Hardy LTS server release - the included vim is apparently a tiny release and has problems (I had to get around it with a set compatible command).  Now this.

---

### Post by keithweddell on 2009-06-03
OK So what do you have in line 2?

---

### Post by goneskiing on 2009-06-03
current table
target     prot opt source               destination 

table that is to be restored
-A INPUT -i lo -j ACCEPT

---

### Post by goneskiing on 2009-06-04
somewhat fixed
I needed the first line:
*filter

I was able to save and restore 

however now I cannot save - getting a permission denied to write to /etc/iptables.up.rules even though I used:
sudo iptables-save > /etc/iptables.up.rules

frustrating

---

### Post by Rubicon_82 on 2009-06-04
[quote="goneskiing"]
however now I cannot save - getting a permission denied to write to /etc/iptables.up.rules even though I used:
sudo iptables-save > /etc/iptables.up.rules
[/quote]

Redirections such as ">" are handled by the shell, which is running as you (not root), so it won't be able to write to /etc.

Try using tee:
```

sudo iptables-save | sudo tee /etc/iptables.up.rules

```

---

### Post by Sword2 on 2009-06-18
> **Rubicon_82 said:**
> Redirections such as ">" are handled by the shell, which is running as you (not root), so it won't be able to write to /etc.

Try using tee:
```

sudo iptables-save | sudo tee /etc/iptables.up.rules

```

or ```
sudo sh -c "iptables-save > /etc/iptables.up.rules"
```

---

