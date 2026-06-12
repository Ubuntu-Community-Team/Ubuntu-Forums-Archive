---
title: "Connecting to a proxy server"
date: 2009-05-28
forum: Server Platforms
---

### Post by FarehamWeather on 2009-05-28
Hey All,

I need to connect my ubuntu server to a proxy server so it can access the internet. What do I need to do to configure it? :D

Thanks,
Chris

---

### Post by heebus on 2009-05-28
System > Preferences > Network Proxy

---

### Post by FarehamWeather on 2009-05-28
Do you know what file it is because its command line interface so I take it that it is in the networking/interfaces file ?

---

### Post by Alekz_ on 2009-05-28
You can export the variables $http_proxy and $ftp_proxy

```
export http_proxy=http://YOUR_PROXY_SERVER:PORT
export ftp_proxy=http://YOUR_PROXY_SERVER:PORT
```

[]'s

---

### Post by FarehamWeather on 2009-05-28
Sorry that has confused me lol,

So I put the following into the /interfaces file?

```

export http_proxy=http://YOUR_PROXY_SERVER:PORT
export ftp_proxy=http://YOUR_PROXY_SERVER:PORT

```

I want to make the server connect to the proxy server to access the internet. ?

Sorry I am still new to linux. :)

---

### Post by Alekz_ on 2009-05-28
No.. You "set" these variables!

Just type the "export" command in the command line interface and it should work fine!

If you want, you can insert these lines in your profile (it export both variables every time you login!).

Open you "profile" file (assuming that you use bash!)
```
vi ~/.bash_profile
```

Put these lines:
```
export http_proxy=http://YOUR_PROXY_SERVER:PORT
export ftp_proxy=http://YOUR_PROXY_SERVER:PORT
```

[]'s

---

### Post by FarehamWeather on 2009-05-28
Ahh ok.

Does it clear the variables each time you logoff or reboot the server then?

---

### Post by Alekz_ on 2009-05-28
Yeah! That's why I suggested you to put it into your "profile file"!

---

### Post by FarehamWeather on 2009-05-28
:D I was only making sure I understand it right ;) lol

Thanks for you help!

---

