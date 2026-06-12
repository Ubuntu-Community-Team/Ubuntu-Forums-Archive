---
title: "SSH Forwarding help?"
date: 2009-04-25
forum: Server Platforms
---

### Post by jigglywiggly on 2009-04-25
So ok here is the thing that is happening. I have been successfully using a SSH server now for a while, and it works anywhere which is awesome. However, I got this app on my iphone called jaadu RDP to remote desktop my server. I can connect normally with the default RDP stuff, but there is an option for SSH. I enabled it, put my password in and then... could not create tunnel to 127.0.0.1

I asked them and they said have you allowed forwarding on my ssh server? So I went to webmin and enabled forwarding, but still no go and they have not replied. I wish they had a dynamic socks proxy, would work easier :D

Ok so here is my config for my server on webmin anyone have any ideas? Oh and I'm using OpenSSH


BTW this is the structure: Host OS Windows 2k3 runs virtualbox that runs a virtualmachine of the linux server.

Do I not post the client host options? I don't think I have to?


[[IMG]http://img16.imageshack.us/img16/6198/59974158.th.jpg[/IMG]](http://img16.imageshack.us/my.php?image=59974158.jpg)
[[IMG]http://img10.imageshack.us/img10/8884/82048532.th.jpg[/IMG]](http://img10.imageshack.us/my.php?image=82048532.jpg)
[[IMG]http://img11.imageshack.us/img11/6013/85141485.th.jpg[/IMG]](http://img11.imageshack.us/my.php?image=85141485.jpg)

---

### Post by HermanAB on 2009-04-25
Hmm, here is a test from another Linux machine:

```
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"
```

If that works, then SSH server is configured correctly and your problem is on the client side on your phone.

---

### Post by jigglywiggly on 2009-04-25
> **HermanAB said:**
> Hmm, here is a test from another Linux machine:

```
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"
```

If that works, then SSH server is configured correctly and your problem is on the client side on your phone.

Wait so I should just put that in the terminal of my ubuntu server? Exactly like that? I am confused D:

---

### Post by HermanAB on 2009-04-25
Just type that line and see if it works.

---

### Post by jigglywiggly on 2009-04-25
It just sits there doing nothing :?

---

### Post by HermanAB on 2009-04-25
Then you still have something wrong with the server configuration in /etc/ssh/sshd_config.

---

### Post by jigglywiggly on 2009-04-25
Just to mkae sure, is it safe to post my sshd_config?

---

### Post by jigglywiggly on 2009-04-25
Err same thing, I uninstalled SSH I then removed the directory.

Same thing for jaadu rdp and this
```

ssh -X -C -c blowfish user@server "gedit /etc/fstab"
```

Port 22 is closed on my server, I use a different port could that be a problem? Let me open it and see... Nope same problem
I'm on jaunty if that matters.

---

### Post by HermanAB on 2009-04-25
```
ssh -X -C -c blowfish user@server -p 2222 "gedit /etc/fstab"
```

---

### Post by jigglywiggly on 2009-04-26
Still nothing :confused:

---

### Post by eentonig on 2009-04-26
can you post the output from the following command on the server?

> sudo more /etc/ssh/sshd_config

That's your sshd config file.


Also, is your server CLI based (server install) or GUI based (Desktop install)? 

On the server, open a terminal and issue 
> ssh -v -v -v -X -C -c blowfish user@server "gedit /etc/fstab"

Same command as above, but with a lot of debugging info ;)

PS. user is your server's username and server is the localhost. you'r basically ssh-ing to the same box.

---

