---
title: "different access to webserver: internet vs LAN ?"
date: 2009-03-12
forum: Server Platforms
---

### Post by browndrake on 2009-03-12
I am new to ubuntu and to all flavors of linux.  

I just built a linux box to use a server in my office.  My office software is mostly written in php and runs through the web browser on the client machines. 

I have installed about all the software that(I think)I need. The system seems to run well and function properly.

Most of my work I do from a client on my lan, however, I do like to do some work from home.  I have set up my router so that I can work from home.   So far all good....

Is there a way that I can require more security..password, or something...if logging in from the internet, than if connecting from my lan?

A second question that could resolve the first:  Can I set it up so that access from the internet (I would want this restriction to be on access from outside the lan) can only go to a specific file or folder...if so I could then make a portal that would require more security to get through.  

As you may tell from the questions, I am pretty new to this and net working in general.  So far, I am happy that my small network is funtioning so well with xp boxes and an ubuntu box. file/print sharing/etc all work well. I just need to come up with some security fixes to allow me to work more securely when out of the office. 

And help/feedback appreciated.


browndrake

---

### Post by BkkBonanza on 2009-03-12
One way that people do this is to use http authentication. You configure it in Apache (httpd.conf) so that certain directories require a password to access. This is simple and unsophisticated. You could also configure apache to listen on port 443 with ssl instead of port 80. This would cause all pages to be encrypted. Setting that up is a bit more complicated. 

Another approach (and likely the most safe) is to configure a VPN (virtual private network). This gives you an encrypted "tunnel" between your machine and the server. There are also several ways to do that. I haven't set up a VPN myself yet and so can't vouch for how easy it is or not, but there is lots of info about VPN easy to find via google. 

I have used "secure ssh tunnels" though. This isn't too hard either and is similar to a vpn and since you are (probably) already running sshd on your server may be quick to configure. Your home machine uses ssh to connect to the work server and then tunnels through that to port 80 (the web server). If your home machine is Windows then a program called Tunnelier makes it fairly easy to tunnel via ssh to the web server. I guess it's a bit fancy but works well and is secure. You would then block any non-local access to the web server because access is only via the ssh tunnel (port 22). I have done this myself but used it for external secure syncing of mysql data via replication. There is a useful description here, [http://www.bitvise.com/port-forwarding](http://www.bitvise.com/port-forwarding) - but it can typically be done with any ssh client/servers.

---

### Post by mrsteveman1 on 2009-03-12
You can setup Apache to require authentication based on the IP used to access it. I'm not at home right now but once i get back if someone else hasn't chimed in i'll walk you through it.

Or you could look around the apache site, there is some documentation for setting up authentication, i believe digest auth is the one you want.

---

### Post by browndrake on 2009-03-12
Thanks for the input.  I will play around with it and see what I can do. 

steve: your idea sounds pretty much like what I had thought of but didn't know if it could be done.  I will search around a see what I can find.  A walkthough of sorts would be nice, if you or another has such.  

I will be tied up, in the office, for the next several hours and wont be able to search/try until then

thanks

browndrake

---

### Post by BkkBonanza on 2009-03-12
I thought that I'd add that with a SSH tunnel you do not need to alter your apache or server config. Just don't allow port 80 out to the net anymore by updating your router. 

Then on your home machine use ssh or tunnelier (if windows, it's free for personal use) to connect via ssh on your server (port 22 needs to be open for any remote admin anyway). For example with Tunnelier you would config a C2S tunnel that forwards some local (home) port to 127.0.0.1:80 on your server. Then you access the page via the local address & port but data is encrypted and sent via ssh to the server where it gets unencrypted and dumped into port 80. Likewise for reply data.

This can also be setup as a proxy on a home network so that any access from that LAN gets routed via the tunnel. 

Tunnelier is a gui tool so you can config the C2S by clicking options and filling in a few values. If using Linux at home then you would have to give appropriate command line values to ssh so that it starts a tunnel. I'll dig around a bit to see if I can give you a simple command that works. 

The nice thing about this method is that you are using the well regarded security of ssh to hide your public activity completely.

---

### Post by BkkBonanza on 2009-03-12
I found this page with a quick and easy tutorial on ssh tunnels,

[http://www.revsys.com/writings/quicktips/ssh-tunnel.html](http://www.revsys.com/writings/quicktips/ssh-tunnel.html)

Looks like a command like,

ssh -f [email]user@myserver.com[/email] -L 80:localhost:80 -N

does the trick. Then you access your web page at home on port 80 on localhost at home. ssh listens on port 80 and forwards to port 80 on the server. You could use a different local port.

Edit: I just tried this out here (it worked fine) and wanted to add a few notes. If you are doing this on Ubuntu then forwarding port 80 requires using sudo since this is a privileged port. I edited my original cmd above to use 80:localhost:80 instead of the 80:myserver.com:80. Actually both may work as long as myserver.com can be resolved on your server. localhost is probably better since it skips any routing issues if the domain isn't routed publicly. You could add myserver.com to the /etc/hosts to aid resolution if you wanted to use that name. Also be careful of any non-standard ssh port and any local forwarding you may have already. I forgot about that at first and couldn't figure why it kept not working. Once you run this command ssh sits in the background. You would need to kill that process if you want to terminate the tunnel. It's a bit nasty and there are other ways to auto-close it.

---

### Post by browndrake on 2009-03-12
thanks bkkbonanza.  I will check out your links too.  As I said, this is a whole new world to me.  

I have always didled with computers..my first pc was in 85.   Most of my experience is in webpage development especially actionscipt.   ubuntu, and all this is new..but is has been fun and it has been pretty exciting..that it has all worked as I have wanted..so far. Reminds me of when I used to play with dos and programmed in basic as a kid. 

thanks

browndrake

---

### Post by BkkBonanza on 2009-03-12
I'm assuming you already use ssh to do admin work on your server and so it's already up and going anyway. New admins often use a control panel but even so, usually on a server install the ssh-server is already there and running anyway. Given it's there, then I think this is almost no extra work to give you secure outside access to what is normally a private site.

There's actually lots of other uses for tunneling too - so it's sometimes handy to know about it.

---

### Post by browndrake on 2009-03-13
things have been very busy.  I have only been able to work on it this morning. I installed the client on my win xp laptop and am able to connect into the server. It opens up the terminal and sftp. Now I need to enable it to let me access files on the web server...through my browser.  I still have more of the above reading to complete, but have to leave the office for the next while.

Thanks for all the help so far.  Any continued pushes, in the right direction, are welcome.

browndrake

---

