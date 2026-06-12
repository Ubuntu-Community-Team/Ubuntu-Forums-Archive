---
title: "need advice with MySQL performance"
date: 2008-10-15
forum: Server Platforms
---

### Post by Panos on 2008-10-15
Hello

I use an application that access various MySQL databases in my local LAN and performance is fine. However, I tried to use the application outside my LAN and access the databases from the Internet, and performance is really awful. So, my question is whether I can tune MySQL for better remote access performance in my server (Ubuntu Hardy), or there will always be limitations due to my upload bandwidth (700-800k) or due to the application itself (it is commercial, closed-code, so there's nothing I can do with it).

Thank you.

---

### Post by condonm on 2008-10-15
I've not had any real experience with your problem myself, though I'd imagine there's not really much you can do about your problem... You're always going to be hitting the roadblocks that you have with your bandwidth limit. Why are you running this on your lan, why not just pony up the cash and buy a real server?

---

### Post by Panos on 2008-10-16
Hi

I suspect too that my problem is the bandwidth.
The application itself is not multi-user neither does it require huge bandwidth. It is a productivity program (something like ms access or openoffice's base) and it is designed for home or office use. However, sometimes I would like to have the ability to work from distance, for example from an internet cafe or from another office, and that's why I am trying this out. What do you mean by "buy a real server"? Do you mean hosting my databases on a web-hosting server or leasing a dedicated server? The second option is out of the question due to the reasons I mention above.

Thanks for your reply. 

> **condonm said:**
> I've not had any real experience with your problem myself, though I'd imagine there's not really much you can do about your problem... You're always going to be hitting the roadblocks that you have with your bandwidth limit. Why are you running this on your lan, why not just pony up the cash and buy a real server?

---

### Post by lykwydchykyn on 2008-10-16
You can try to tweak mysql to be as efficient as it can be, but I don't think you can do anything to address the real bottleneck which is bandwidth.  About the only things that would help that would have to involve client-side tweaking.  

I had a similar situation (though the software wasn't proprietary, it was in-house), and what I found worked best was to install the program on a machine local to the server and then use FreeNX to serve out just the interface to remote users.  This provided much better performance.

Does your app run on Linux?  If it runs on Windows, you might be able to rig up something with remote desktop, but I'm not sure how fast that'll run over your connection.  FreeNX is quite fast, even over dialup.

---

