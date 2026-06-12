---
title: "How to make web server available over the internet"
date: 2013-03-26
forum: Server Platforms
---

### Post by Zero000 on 2013-03-26
Ok I am running ubuntu 12.10 server edition 64bit, I have installed the LAMP stack and configured it accordingly. The website works fine over the internal network. But if I try to access it from anywhere outside of the network the browser cannot find it. The server is behind one router (though there are 3 routers including our modem) and I forwarded port 80 to my server, and I know that my ISP is not blocking port 80. The server's ip is static but our public ip is not (though it will be soon). I have experience using ubuntu but I dont know much about servers. Any help would be appreciated and if anymore info is needed I will post it.

---

### Post by papibe on 2013-03-26
Hi Zero000. Welcome to the forums ):P

It is usually not possible to access a LAN machine, from the LAN itself, using its public Internet IP. Your router would have to support an advance feature called NAT loopback (read about it [here]("http://opensimulator.org/wiki/NAT_Loopback_Routers")), and most consumer routers don't support it.

The easiest way to test remote access is using your cell or tablet wireless service (be sure not to be connected to your own WiFi), or from an Internet café, public library or a friend house.

For more tips on how to access your server from the outside, take a look at post #3 of this [thread]("ubuntuforums.org/showthread.php?t=2126021&highlight").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Zero000 on 2013-05-22
Sorry to resurrect this but I just wanted to say that papibe offered the solution, I didn't know you couldn't access it over LAN. Don't know how to mark as solved :/

---

### Post by Drenriza on 2013-05-22
> **Zero000 said:**
> Sorry to resurrect this but I just wanted to say that papibe offered the solution, I didn't know you couldn't access it over LAN. Don't know how to mark as solved :/

Zero000 what modem do you currently have? I suspect it's a modem delivered by your ISP.

I'll gladly help you if i can. To access your local server from the WAN is not a big deal.

> **papibe said:**
> 
#1 It is usually not possible to access a LAN machine, from the LAN itself,  using its public Internet IP. 


[LIST=1]
[*]Tor is the easiest way to test your server from a "remote" location. In the correct format and such unless its a phone website.  
[/LIST]

---

### Post by papibe on 2013-05-22
[Here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to mark the thread as solved.

Regards.

---

