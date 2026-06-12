---
title: "very slow response of browser exported on ssh connection"
date: 2010-07-19
forum: Server Platforms
---

### Post by tapas_mishra on 2010-07-19
I logged in to my server as 
```

ssh root@myserver.com -X

```
and then 
```

firefox&

```
firstly it took a very long time to display the browser.
After the browser was working on my localmachine it took really long time to show the response.
I am doing all this on internet and the server has bandwidth as 6Mbps and my internet connection has a speed 1Mbps what could be the reason for such a slow response.
The same exists in case of Chromium is there a way to make it fast.
Ubuntu 10.04 server edition 
and ssh2
bot

---

### Post by BobVila on 2010-07-19
> **tapas_mishra said:**
> I logged in to my server as 
```

ssh root@myserver.com -X

```and then 
```

firefox&

```firstly it took a very long time to display the browser.
After the browser was working on my localmachine it took really long time to show the response.
I am doing all this on internet and the server has bandwidth as 6Mbps and my internet connection has a speed 1Mbps what could be the reason for such a slow response.
The same exists in case of Chromium is there a way to make it fast.
Ubuntu 10.04 server edition 
and ssh2
bot

Is that 1Mb symmetrical? If you're doing it with a server on a cable connection, things can get a bit icky...

---

### Post by tapas_mishra on 2010-07-19
On the same machines in problem I used teamviewer and things worked superpfast.

---

