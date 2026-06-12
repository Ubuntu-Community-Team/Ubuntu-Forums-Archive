---
title: "Security for the vino-server"
date: 2007-06-16
forum: Server Platforms
---

### Post by NickD-NLUG on 2007-06-16
Hi,

The vino-server is a great tool, especially being able to remotely reconnect to established sessions.  However its relatively insecure as its listening on the network interface, and there's no way to restrict which IP addresses can connect ( without resorting to firewalling ), or forcing it just to listen on localhost.  I'd like to do any of the following in Feisty...

Is there any way to remotely start and stop the service, so its only running when needed?

( Step 5 on here:

[http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981)

disables remote access, but I'd like to be paranoid and turn the service off completely ).

Alternatively is there a way to restrict what IP addresses can connect to the service ( above and beyond firewall rules ).

Alternatively is there a way to make the vino-server only listen on localhost, rather than on the external IP address?

Thank you.

---

### Post by gaten on 2007-06-17
I wrote a howto that could solve your problem. It details accessing your VNC connection over SSH. In this way, the vino-server doesn't even need to listen on an outside port, only a local port and you can forward all the traffic over the shh port. 

Here it is, hope it helps.

[http://ubuntuforums.org/showthread.php?t=383053](http://ubuntuforums.org/showthread.php?t=383053)

---

### Post by NickD-NLUG on 2007-06-17
Thanks for this, really nice HOWTO by the way :)

The problem is that if I access the vino-server over SSH, it's still listening on the network interface, rather than just on 127.0.0.1 ( or ::1  if you so wish ).  So even if I'm not connecting to it on my host's external IP address, it's still listening on that IP address so other people can try and connect to it.

That's the bit I'm trying to turn off.... any ideas?

Thanks again, appreciated.

---

### Post by gaten on 2007-06-17
Well if you have a router, you can just disable access to the port from the outside. As for changing the interface Vino is listening on, I can't remember off hand. Try looking in gconf for something (sorry, not on my Ubuntu box right now). 

Oh, and **::1** means port 5901, fyi.

You could also try blocking all attempts to that port not from that machine with iptables. This should work because all the data and requests to the VNC port will be given by the ssh server on that machine.

---

### Post by NickD-NLUG on 2007-06-17
Thanks for the reply :)

Yeah, disabled access to the port from the outside... but still, you know, it's *listening*... that's just not right.

And, well, no, "::1" is the IPv6 equivalent of 127.0.0.1, i.e. "localhost".

I think there's a way using gconf to get it to listen on localhost only... and that's only possible on Feisty.  I saw this mentioned somewhere online, but I can't find it now, and there's no clues in the relevant %gconf.xml file.

I'll be blocking the port with IPtables anyway.

But still...

You know...

It's a service listening on an external interface when it shouldn't be... its secure enough, but if I figure out a way to calm my instinctive uneasiness about this I'll post it here....

---

### Post by gaten on 2007-06-17
>  And, well, no, "::1" is the IPv6 equivalent of 127.0.0.1, i.e. "localhost".

Woops, sorry. Though you meant "::1" in the context of a connection address to a VNC server.

> I think there's a way using gconf to get it to listen on localhost only... and that's only possible on Feisty. I saw this mentioned somewhere online, but I can't find it now, and there's no clues in the relevant %gconf.xml file.

Yes, in Feisty run gconf-editor and browse to /desktop/gnome/remote_access and check **local_only**. However, it sounds like you'd don't have Feisty, so if that's a new addition I don't know ;)

My %gconf.xml file for vino-server has this entry when I have 'local_only' checked:

```
<entry name="local_only" mtime="1182136569" type="bool" value="true">
>         </entry>
```

Try putting that in your config file. Good luck :P

> It's a service listening on an external interface when it shouldn't be... its secure enough, but if I figure out a way to calm my instinctive uneasiness about this I'll post it here....

I completely agree with you. And I personally find vino-server a poorly thought out addition to Ubuntu. The options we are talking about should be configurable when you enable the service, this whole 'simple is better' approach is foolish.

---

### Post by NickD-NLUG on 2007-06-19
Brilliant :)

It's a little obscure, but yes, checking "local_only" works, so now the vino-server listening on localhost only.

And something I didn't realise before, the lines

gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true

and

gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled false

do turn the server on and off completely.  They appear to take a little while to have an effect, but it is possible to ssh in, turn the vino server on, and then connect.

Thanks for your help on this, very much appreciated.

---

