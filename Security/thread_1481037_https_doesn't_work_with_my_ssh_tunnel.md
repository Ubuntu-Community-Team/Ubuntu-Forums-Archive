---
title: "https doesn't work with my ssh tunnel"
date: 2010-05-12
forum: Security
---

### Post by mondale on 2010-05-12
Hello,

I have an ssh tunnel with my ubuntu (vps) server.
On my local computer I have proxifier, to redirect everything with socks5.

Everything works fine, I can browse websites and that.
Email also works.

But when I want to visit a website that uses https it doesn't work.
I do not get to see the website, or receive an internal server error.

Does anyone know how this is possible, and what I have to do to resolve this error?

---

### Post by iponeverything on 2010-05-12
The some of the results look promising in resolving your issue:

[http://www.google.com/search?hl=en&q=tunnel+https+over+ssh](http://www.google.com/search?hl=en&q=tunnel+https+over+ssh)

---

### Post by mondale on 2010-05-12
None of them helps me with https. Http is working correctly :(.

---

### Post by cdenley on 2010-05-12
Disable or remove proxifier, then run these commands and post the output.
```

sudo apt-get install tsocks
sed -e 's/^server *= *[^ ]*/server = 127.0.0.1/g' /etc/tsocks.conf|sudo tee /etc/tsocks.conf
ssh -D 1080 myuser@myserver
echo -e "GET / HTTP/1.0\n"|tsocks openssl s_client -quiet -connect google.com:443

```

Why proxifier? Do the global proxy settings not accomplish what you need?
System>Preferences>Network Proxy

---

### Post by mondale on 2010-05-12
The proxifier I use on my windows laptop.
It's the server that is Ubuntu.

But i'm going to check out when I go home in the evening if my Ubuntu Machine can use the socks5 proxy without troubles, as you said.

Any more ideas?

---

### Post by cdenley on 2010-05-12
> **mondale said:**
> The proxifier I use on my windows laptop.
It's the server that is Ubuntu.

But i'm going to check out when I go home in the evening if my Ubuntu Machine can use the socks5 proxy without troubles, as you said.

Any more ideas?

I doubt the problem is on the server side. You can run this command to verify your server can connect to https servers.
```

echo -e "GET / HTTP/1.0\n"|openssl s_client -quiet -connect google.com:443

```

---

### Post by CharlesA on 2010-05-12
Why are you using Proxifier on Windows? If you use Chrome, Opera, or Firefox, you can just set the proxy manually once the SSH tunnel is established.

---

### Post by mondale on 2010-05-13
That is because I want to have everything secured, from my Outlook, to Picasa, and other software that I use and is connected to the web.

---

