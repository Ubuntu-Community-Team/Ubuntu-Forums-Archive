---
title: "Tor, TorButton, Firefox and download managers"
date: 2011-03-14
forum: The Cafe
---

### Post by billdotson on 2011-03-14
I am experimenting with Tor and was going around to different websites earlier. On one website I downloaded a couple files and a dialog box came up warning me about an external application. I said to continue on (whatever the option) and then the firefox download chooser window came up (that allows you to open the file, save it, or if you have flashget installed, choose a download manager). 

I understand that if you are opening a file then the program opening it might not be using a proxy, but what about if you choose to download? Will TorButton extend the proxy to the built-in Firefox downloader? Does anyone know what settings I need to have to use the proxy in a download manager? I tried localhost and port 8118 in gwget and the download just kept staying at 0%. Do I need to open up port 8118 in iptables and/or my router?

---

### Post by dirty_harry on 2011-03-14
hello

To my understanding the built-in download manager should use your firefox proxy settings. eg. for downthemall is an option to use firefox settings or configure it to use a different connection. 

 > I tried localhost and port 8118 in gwget and the download just kept  staying at 0%. Do I need to open up port 8118 in iptables and/or my  router?     I don't think that you should adjust your router in that way. Iptables I'm not sure.
I configured polipo as described here [https://www.torproject.org/docs/tor-doc-unix.html.en#polipo](https://www.torproject.org/docs/tor-doc-unix.html.en#polipo) to "localhost:9050". 

To test your tor configuration you could use this: [http://what-is-my-ip-address.anonymous-proxy-servers.net/](http://what-is-my-ip-address.anonymous-proxy-servers.net/) (comes with a lot of tricks to test tor, such as ftp/flash/jave lookup...)

Maybe the reason that torbutton comes up with this message about external application is because we have installed an addtional download-manager in firefox, but I'm only guessing.


**not your usual community café post**

have fun

---

### Post by billdotson on 2011-03-14
Well I don't have any ports forwarded at all in my router. I know to get bit torrent to work I have to forward a port on my router and add an exception rule in iptables.

---

