---
title: "Calling all coders..."
date: 2008-08-01
forum: The Cafe
---

### Post by sefs on 2008-08-01
With the source code of Firestarter here... [http://www.fs-security.com/download.php](http://www.fs-security.com/download.php) 

How easy is it to strip down this application to just a simple application that displays one window....Active connections.

Does anyone have the means to do this?

Thanks.

---

### Post by pytheas22 on 2008-08-01
I'm not a programmer so I can't help you with your request, but I can make a suggestion that might solve your problem.  You can install iptraf if you want to monitor active connections (you can also optionally log all connections):
```

sudo apt-get install iptraf
```

It doesn't have a graphical interface--you have to run it from the command-line--but it's simple and readable.

You could also monitor traffic with Wireshark or tcpdump.

---

### Post by sefs on 2008-08-06
I found the best tool ever called Netactview.

Netactview is a graphical network (active) connections viewer for Linux, similar in functionality with Netstat (OR TCPView). It includes features like process information, host name retrieval, automatic refresh and sorting. It has a fully featured GTK 2 graphical interface. 

[http://netactview.sourceforge.net/index.html](http://netactview.sourceforge.net/index.html)

This lil program is good stuff!

---

### Post by original_jamingrit on 2008-08-06
Conky has this functionality.

---

### Post by Sand Lee on 2008-08-06
You probably want the Development & Programming forum.

---

