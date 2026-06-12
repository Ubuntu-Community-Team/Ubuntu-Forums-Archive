---
title: "TELNETD not listening?"
date: 2009-12-18
forum: Server Platforms
---

### Post by Vegan on 2009-12-18
I cannot seem to find out if telnetd is actually running as I keep getting connection refused when attempting to connect.

---

### Post by cariboo on 2009-12-18
Unless you specifically install and start the service, it isn't there in a default installation. You can check a couple of ways. on the server type:

```
ps ax | grep telnet
```

You can also port-scan the server to see if port 23 is open

---

### Post by BkkBonanza on 2009-12-18
Check your firewall is open for that port. And "netstat -lntp" to see it is listening.

---

### Post by Vegan on 2009-12-18
I ran netstat and that is why I am inquiring, its not seemingly there so no wonder connections are refused.

```

sudo apt-get install telnetd

```

is what I used to install it, no error but no joy.:(

---

### Post by BkkBonanza on 2009-12-18
Does it show up in "ps afx"?
Possibly telnetd doesn't get started by default. I never use it but I guess it would be manually started like this,

/etc/init.d/telnetd start

---

### Post by Vegan on 2009-12-18
too many items with ps afx so I used grep to filter for "telnet"

```
sudo netstat -lntp
```

I grepped it to death and even manually after piping it to a file. Nothing there. Nobody seems to be listening.

```
sudo ps afx | grep telnet
```

showed no telnetd but it does show my terminal session.

```
sudo /etc/init.d/telnetd start
```

command not found.

```
sudo ufw allow 23/tcp
```

rules updated

---

### Post by BkkBonanza on 2009-12-18
A bit of googling shows that telnet makes use of xinetd to manage it. To me this counts as strike two for the program. Here's a page that has a section on using it in Ubuntu,

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch16_:_Telnet,_TFTP,_and_xinetd#Debian_.2F_Ubuntu](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch16_:_Telnet,_TFTP,_and_xinetd#Debian_.2F_Ubuntu)

Hopefully that helps. It looks like more effort to enable it.

What I don't understand is why you need to use telnet instead of just using ssh installed by default. It is far more powerful, more secure, already there and generally considered to be a far better successor to telnet.

---

### Post by Vegan on 2009-12-18
I recall that with 8.04

sudo apt-get install telnetd

worked, 9.10 no joy :(

mind you I was manually installing everything so that I could better see all the dependencies and programs in use.

---

### Post by coffeeandlinux on 2009-12-18
I agree. Try to go with ssh. Telnet transfers everything via plain text so it has a high volubility to eavesdroppers while ssh uses cryptography to guard the connection.

---

### Post by Vegan on 2009-12-19
I am on an intranet so my router protects me. Telnet is all I need to manage the machine.

---

