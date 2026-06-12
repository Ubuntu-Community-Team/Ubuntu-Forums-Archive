---
title: "PRoxy server with web interface"
date: 2007-05-24
forum: Server Platforms
---

### Post by KAding on 2007-05-24
Hi everyone,

I'm looking to install something like [https://proxify.com](https://proxify.com) for personal use on my ubuntu server. That is, I want to install a proxy with a web interface on my server to be able to access some sites that are blocked at my school. I'd rather not use putty or any other software on the client to tunnel HTTP or things like that. What I am looking for is something that would be something like:

1. Open browser at school
2. Goto [http://myserver/proxy](http://myserver/proxy)
3. Login with username/pw
4. When login succesful it will show a dialog like proxify.com where I can enter a URL that is otherwise blocked (like gmail, ebay or hotmail!)
5. Normally blocked website opens in a frame

Is this possible? I installed the polipo proxy, but I don't think it has a webinterface. I don't have Administrator on the client rights so I can't set the proxy server in the browser settings either. Preferably this proxy web-interface thingy should allow login into gmail or hotmail.

Anyone have any ideas? I would really appreciate it!

KAding

---

### Post by KAding on 2007-05-24
I found the answer myself:
[http://www.jmarshall.com/tools/cgiproxy/](http://www.jmarshall.com/tools/cgiproxy/)

---

