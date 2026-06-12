---
title: "Nagios and VPN"
date: 2011-05-19
forum: Server Platforms
---

### Post by tapi0n on 2011-05-19
My apologies if I posted a wrong section. But I think it's most suited here since I'm running a Ubuntu 9.10 server. If someone says it's more suited in another section please say so and I'll be happy to redo it over there. :)

The question itself doesn't have that much to do with the server but more with the host it's monitoring.

So, running Nagios is all good and well when it's monitoring hosts on the local network. 
Thing is, when I want to log hosts from another private network (customers). I need to set up a vpn (done), add the nagios host to the allowed hosts section in NSC.ini (I'm using NSClient++). At this point I can do basic checks like ping.

Now, when I try to use an nrpe plugin. I get an error message in my nsc.log about unauthorized acces from xxx.xxx.xxx.xxx

xxx.xxx.xxx.xxx being an ip from the local network (the customer). So I added the ip from the logs to the allowed hosts in NSC.ini and now I'm getting the desired responses on my nagios interface.

Now my question is this.
Is there a way to make this go a little more automated? Because I can imagine that when the vpn goes down, the ip changes too? Setting me back to the point where I couldn't monitor nrpe services.


Cheers,

---

### Post by tapi0n on 2011-05-19
Found the solution, this is just to share with someone who might experience the same thing :)
In the NSC.ini file I had to add xxx.xxx.xxx.xxx address, which was the routers' ip, to the allowed hosts section and that did the trick. Hope this helps someone some day!

---

