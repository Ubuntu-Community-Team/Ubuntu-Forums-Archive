---
title: "hostname problem after installing webserver"
date: 2008-06-29
forum: Server Platforms
---

### Post by mogie on 2008-06-29
I've installed Lighhtpd + libtorrent + rtorrent + xmlrpc and got my wTorrent-webinterface up'n running with rtorrent..

Now my hostname suddenly cant be found by other computers on the LAN. Everything is as it should be in /etc/hosts and /etc/hostname. (It worked just before I got the webserver up, right?) Now I need some log, or..anything to find out what happends.

All the other computers do experience this problem..

(been working with ubuntu/debian bout a year now.)

Thanks for all your help guys!

---

### Post by windependence on 2008-06-30
Can you reach it by IP address?

-Tim

---

### Post by mogie on 2008-06-30
> **windependence said:**
> Can you reach it by IP address?

-Tim

Absolutely. Trough UNC (\\10.0.0.2) and [http://10.0.0.2](http://10.0.0.2), but no hostname: (\\hostname, [http://hostname](http://hostname))

As I said, it worked just before compleeting the webserver. Is there any loging for this in /var/log etc?

---

### Post by windependence on 2008-06-30
I know you said so but can you post the contents of your hosts file on the box you are tryin to access the server from? Each box must have an alias defined if you are not running your own DNS server.

Also, can you ping it by hostname?

-Tim

---

### Post by mogie on 2008-06-30
I mainly use Windows XP on all desktops, so there's no /etc/hosts on the boxes I'm trying to ping/connect from. Every computer and server on the network has been configured 10.0.0.138 for its DNS-nameserver and Gateway (and DHCP-server). I'm a bit unsure of how the hostnames are being handled by the pfSense-server (free-BSD) from the linux-boxes, but for now all servers and desktops have been working flawless, exept for this last server..

I cannot ping the "tor"/"tor.lan" hostname from my previous Ubuntu server, nor any other computer. Only connection trough IP on any protocol.

/etc/hosts on my new rtorrent server (tor)
```

127.0.0.1       localhost
10.0.0.2        tor.lan         tor

```

/etc/hosts to tore (as u see there's no difference)
```

127.0.0.1       localhost
10.0.0.5        tore.lan        tore

```

~#hostname and ~#hostname -f gives correct outputs.

I'm more curious to what you mean about alias on every computer :)


Added:
domain prefix (.lan or any other for that sake) has nothing to say on the M$ network. I can easily connect trough the "Run"-meny with \\hostname on a sambashare without any ".lan" at the end.

---

### Post by mrpeenut24 on 2008-06-30
Windows has a hosts files also.  Look in C:\Windows\system32\drivers\etc\hosts


At my house, when I want to talk to my server (since my modem refuses to let connections leave, then reenter) I have to have an alias on my laptop.  Here's what I've got:
```

127.0.0.1   localhost
...
192.168.1.115    www.myserver.com

```

---

### Post by mogie on 2008-06-30
> **mrpeenut24 said:**
> Windows has a hosts files also.  Look in C:\Windows\system32\drivers\etc\hosts


At my house, when I want to talk to my server (since my modem refuses to let connections leave, then reenter) I have to have an alias on my laptop.  Here's what I've got:
```

127.0.0.1   localhost
...
192.168.1.115    www.myserver.com

```

Brilliant! Thanks. I didn't know about those files on the MS plattform :)

Though, why i cannot get connection to tor like I usually do is still unanswered...

---

### Post by windependence on 2008-07-01
Have you added the DNS entry to the Windows machine like mrpeenut suggested? The box cannot resolve the name if you don't do this.

-Tim

---

### Post by windependence on 2008-07-01
> **mogie said:**
> 

I'm more curious to what you mean about alias on every computer :)



Exactly what your problem is. You need an alias in every Windoze system in C:\Windows\system32\drivers\etc\hosts for your servers. Then you will be able to connect via server name.

-Tim

---

