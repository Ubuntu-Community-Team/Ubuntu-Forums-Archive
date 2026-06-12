---
title: "port forwarding"
date: 2010-03-23
forum: Server Platforms
---

### Post by flintman on 2010-03-23
Hello,

Background:  
Was running windows 2003 server but sick of all the memory being used by the GUI.  I just finished installing ubuntu 9.10 server.

Question:
I have remote desktop running on ubuntu 9.10 64bit desktop edition.  In windows I had a port forwarding program that took port 5901 and send it to that computer at port 5900. The reason was I had port 5900 going to the windows server so I could remote into it. Now I have searched on it and find out a lot about using iptables.  There really isn't, well I can't find a clear tutorial on how to use it.  Is this my best option?  if so does anyone have a good tutorial?  or could someone explain it to me a little bit?

Thanks

---

### Post by KB1JWQ on 2010-03-23
It could work.  So could ssh, netcat, and a few other programs.

Remember, nobody here knows what your network looks like besides you.  Can you describe the relevant components, what they do, how they're hooked together, and what you'd like to ultimately have done?

It'll enable us to give advice that's a lot more relevant past "Yeah, program X does that!"

---

### Post by flintman on 2010-03-23
Sorry about that

My set-up:

Cable modem/Router goes into a 100 port switch.  Off my 100 port switch I have 10 computers all running ubuntu 9.10 32 bit and 64 bit.  And 1 NAS running a windows based NAS software.  

Also out of my Router 
I run into my Server Dell 1750 with static IP.

My Router forwards all ports to my server. 

What I'm not sure on doing:
I'm debating is it worth setting my router up as my firewall or using my server as my firewall.  


I would like to be as secure as possible

Pre thanks

---

### Post by spynappels on 2010-03-23
Routers are generally easier to use if you are happy enough to do so. If you were using the server, you'd have to have 2 NICs in it and connect the switch to the "LAN" NIC while the router would be connected to the "WAN" NIC. If the router can do it, I'd say go with that. Just make sure you only forward ports that you absolutely require to be open to the LAN side of the router, and forward them all to the server, which can have it's own firewall running too.

---

### Post by EmanresuusernamE on 2010-03-23
Honestly, I'd say use your router as a firewall too.

If you're going to consider using your server as a firewall, might I recommend using Shorewall and Webmin to configure iptables for you?  It's a little touchy, but once you get it installed, it's fairly easy to play with.  And Webmin makes server administration a lot easier to use.

---

### Post by flintman on 2010-03-24
thanks for the help I will  use the router.  much easier

---

### Post by KB1JWQ on 2010-03-24
Glad you got it sorted!

You might want to mark this thread as "Solved."

---

