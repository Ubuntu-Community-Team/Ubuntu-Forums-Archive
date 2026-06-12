---
title: "Your thoughts on web interfaces?"
date: 2007-12-25
forum: Server Platforms
---

### Post by nalmeth on 2007-12-25
I am accustomed to the Non-GUI Ubuntu way of server admin, but I'm kind of curious about these web interfaces, such as Webmin, ISPConfig and the like.

The terminal is quite sufficient if you know what you're doing, and has advantages such as saving memory for server tasks. Remote access is easy with ssh.
--
These web interfaces seem to bring a nice centralized collection of tools to do all your server work, and AFAIK, can be used remotely also saving the need to install a GUI on the server.

What are your thoughts and experiences with these tools? Does it really make life much easier?

---

### Post by p_quarles on 2007-12-25
I can't remember who said this, but I agree with whoever it was: "Once you know enough to secure Webmin, you don't need it."

---

### Post by koenn on 2007-12-25
I had a short look at webmin and swat, and at work I use a web interface to a firewall /gateway server, basically a linux PC with iptables, dns, dhcp, web proxy, mail relay, etc. 

occasionally, web interfaces can help to find your bearings in an area you're not familiar with, but in areas you're not familiar with, you shouldn't be sysadminning anyway, so using a GUI or a web interface should never become an alternative to learning the ropes 

what bothers me most about web interfaces (and GUI's in general) is that they obfuscate things. A shell command is a shell command, and a value in a config file is what it is. GUI's summarise, interpret, and often include assumptions by the GUI developer. I find myself always trying to look through the GUI to know what is really going on - so leaving out the GUI makes things easier.

---

### Post by nalmeth on 2007-12-25
>  what bothers me most about web interfaces (and GUI's in general) is that they obfuscate things. A shell command is a shell command, and a value in a config file is what it is. GUI's summarise, interpret, and often include assumptions by the GUI developer. I find myself always trying to look through the GUI to know what is really going on - so leaving out the GUI makes things easier.Thats kind of what bothers me about the idea aswell. Besides something like ntop which can spit out graphical stats of your page is much better for that. 
If the form and layout is functional and intuitive, then I could see a benefit. Otherwise it may just add more confusion.
>          I can't remember who said this, but I agree with whoever it was: "Once you know enough to secure Webmin, you don't need it."Is security a problem with this? Like I said I haven't used it yet, but it seems to me it will just use a port of your choice, and hopefully an encrypted connection. Anyway, it is a concern nonetheless. 
> 
occasionally, web interfaces can help to find your bearings in an area you're not familiar with, but in areas you're not familiar with, you shouldn't be sysadminning anyway, so using a GUI or a web interface should never become an alternative to learning the ropes
Certainly agree with that

         Somehow I just get the feeling this is more trouble than it is worth, and is meant to appease admins who are used to MS Server, or YaST. Yet I can't help but feel curious.

---

### Post by p_quarles on 2007-12-25
> **nalmeth said:**
> Is security a problem with this? Like I said I haven't used it yet, but it seems to me it will just use a port of your choice, and hopefully an encrypted connection. Anyway, it is a concern nonetheless. 
If you have the port open to the WAN, then yes, it's a security risk. That's true of just about anything, of course, but Webmin is a very attractive target. 

If you just want to use it to manage a headless server from within the local network, though, you would be safe.

---

