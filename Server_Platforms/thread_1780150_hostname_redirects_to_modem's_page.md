---
title: "hostname redirects to modem's page"
date: 2011-06-11
forum: Server Platforms
---

### Post by flyingsuperhigh on 2011-06-11
Hey,

Just last week, when I asked a friend to type my hostname in an address bar, she was able to see my website's homepage. I asked her to do it again just a couple of hours ago and now she tells me that it brings her to my modem's webpage. My friend is not on the same network as me. I am not sure what is going on. I have forwarded port 22 in order to ssh and forwarded port 80 to get redirected to my website. Both these ports have been forwarded to the LAN address of the server. I know for a fact that they're open because when I go to canyouseeme.org it says that it can see my service. It was working last week but it is not working now and I am really not sure what is going on. Help.

---

### Post by papibe on 2011-06-11
My guess is that if your are being redirected to the router, it means that the routes has been configured to be accessed from the Internet (or outside the LAN) using the port 80.

For example, in a DD-WRT router you can enable that on Administration -> Management, by enabling Web GUI Management on the Remote Access section. Then you can set the port to access your router on Web GUI Port.

If by any chance that last port is 80, your router will face a conflict that maybe is being resolve by the safest option: not granting access to the local network, but opening the router interface.

Just a thought.
Regards.

---

### Post by flyingsuperhigh on 2011-06-11
I don't have remote access by administration available. I don't really understand why last week, when I typed in the hostname, I was redirected to the contents of the index.html page and now I am redirected to my modem's page. As far as I know, I did not really change any settings. I'm also not sure why I am able to access the modem page from WAN.

---

### Post by volkswagner on 2011-06-11
Have you checked logs for any relevant information in the past week?

```
less /var/log/apache2/access.log
```

```
less /var/log/apache2/error.log
```

You can also test from home (inside server LAN) by using a proxy service.  Sorry I can't recommend a good one, since I have yet to use any.  Google will help here.

---

