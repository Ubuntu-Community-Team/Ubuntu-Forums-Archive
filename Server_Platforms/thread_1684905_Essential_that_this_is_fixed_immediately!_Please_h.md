---
title: "Essential that this is fixed immediately! Please help!"
date: 2011-02-09
forum: Server Platforms
---

### Post by memaster3 on 2011-02-09
My home file server is not connecting via ssh or ftp. With FTP it gives a different error, but currently I am unable to reproduce that error when connecting, it just doesn't do anything. The following is what it does when I try to connect through ssh. The external IP address here has x's replacing the first number block. That is because it doesn't have a firewall yet. It is very new.

**_[CENTER]Local IP Address[/CENTER]_**
```
jon@Jons-Macbook:~$ ssh jon@10.0.1.201
Read from socket failed: Connection reset by peer
```

**_[CENTER]External IP Address[/CENTER]_**
```
jon@Jons-Macbook:~$ ssh jon@xxx.84.174.196
Read from socket failed: Connection reset by peer
```

---

### Post by wojox on 2011-02-09
What does that say?

```
ssh -vvv jon@10.0.1.201
```

---

### Post by tgm4883 on 2011-02-09
> Essential that this is fixed immediately! Please help!

[http://shop.canonical.com/product_info.php?products_id=715](http://shop.canonical.com/product_info.php?products_id=715)

---

### Post by cipherboy_loc on 2011-02-09
Try turning everything off (starting with the desktops, ending with the router) and then turn on the router and then the desktops. It seems like it is a network error.



Cipherboy

---

### Post by elico on 2011-02-10
did you tried yo ping the ip address?
do you have physycal access to the server?
if yes the try pinging to the server.. and from the server to the internet.

---

### Post by memaster3 on 2011-02-10
> **wojox said:**
> What does that say?

```
ssh -vvv jon@10.0.1.201
```


jon@Jons-Macbook:~$ ssh -vvv jon@xxx.84.174.196
OpenSSH_5.5p1 Debian-4ubuntu5, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to xxx.84.174.196 [xxx.84.174.196] port 22.

---

### Post by dtfinch on 2011-02-10
What kind of network card/chipset does the system have? I had a really cheap VIA C7 server (Rhine II network chipset I think) that had those sort of symptoms (ssh connection reset as soon as it connects, though for the first few days it worked ok), and adding a new nic card fixed the problem.

---

### Post by cariboo on 2011-02-10
Having permissions set wrong could lead to the problem you are having ~/.ssh should have a permission of 700 and the files inside should have a permission of 644.

---

### Post by memaster3 on 2011-02-10
> **cariboo907 said:**
> Having permissions set wrong could lead to the problem you are having ~/.ssh should have a permission of 700 and the files inside should have a permission of 644.

Thanks, I think it's a permissions problem. I was changing permissions and I had a power failure mid-process. What would I do to reset the permissions? If I can't reset them completely, how would I fix them in the ~/.ssh folder and the files inside. Can you tell me what commands to type?

---

### Post by memaster3 on 2011-02-10
Since the ssh prompt is giving an error, it doesn't have a screen or keyboard, so how am I supposed to change the settings? Anyone have any ideas? I have physical access to the server, but it will take about a half an hour to get it out from where it is. I had to use a car jack to lift the edge of the desk to slide it underneath, and I couldn't slide it out or in without jacking the table up a little bit.

---

