---
title: "new connections ?"
date: 2006-12-15
forum: Server Platforms
---

### Post by neewby on 2006-12-15
someone tell me what these connections are

After running netstat -a 
I have these two connections , which have never been there before suspicious me ?




tcp6       0      0 deefault.BigPond:43166  ppp-70-243-110-181:2097 TIME_WAIT
tcp6       0      0 ip6-localhost:43024     ip6-localhost:41753     TIME_WAIT

---

### Post by neewby on 2006-12-15
bump

---

### Post by gaten on 2006-12-17
Try this netstat command instead:
```
netstat -pan --inet
```

The options (after -):
[LIST]
[*]p  
Display the PID of the process 
[*]a  
All connections, listening and not listening
[*]n  
Output the number of the port rather than the service. such as 80 rather than HTTP. 
[*]--inet  
Tells it only to display network traffic (AFAIK --ip does the same thing). 
[/LIST]

If you can post the output to that code, I can help you more. That will show you something like
```

tcp        0      0 192.168.1.100:42642     207.46.108.81:1863      ESTABLISHED8688/gaim
```

The last part, gaim, tells me that gAIM is the process responsible for the connection. And the 8688 is the PID of the process. If i wanted to kill it, i would do this:
```
kill -9 8688
```

But make sure you know what it is before you kill it.

Hope this helps.

---

