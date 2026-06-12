---
title: "Problem with remote desktop"
date: 2010-06-06
forum: Server Platforms
---

### Post by Karl Norway on 2010-06-06
Hi im having trouble with remote desktop. I restared the server and then after that Im not able to control my desktop. I can logon but its like the server wont send the desktop info back to the controlling computer (using ultra VNCviewer on win 7).

Is there something like a service that havent bee started properly?

Befor the restrt it worked like a charm ;)

---

### Post by HermanAB on 2010-06-06
Just as well probably...

VNC is a surefire way to get your machine hacked.  There are many tales of woe on these forums.  Rather use SSH.

The problems with VNC are:
[LIST]
[*]VNC is inherently insecure.
[*]VNC uses plug and play to open up your home router to the world.
[*]The Ubuntu default minimum password requirements are stupidly insecure, so many users set up accounts with insecure passwords.
[*]There are automated VNC hacking scripts in the wild that actively seek out machines to compromise, so it is just a matter of time before you will get hit.
[/LIST]

---

### Post by Karl Norway on 2010-06-06
Ok 

Both my server and controlling machine is behind tha same firewall..

Can I get GUI with SSH ??

If so can someone give me a quick guid on how to set it up?

---

### Post by bodhi.zazen on 2010-06-06
VNC is not really the best option for you. 95+ % of managing a server is either performed at the command line or involves editing configuration files and VNC / Gnome desktop does not add much.

Learn to use ssh , you can forward X applications with ssh -X.

If you want a graphical interface, I suggest webmin (or similar tools).

---

### Post by HermanAB on 2010-06-06
ssh -C -c blowfish -X user@server "gedit /etc/fstab"

---

### Post by scorp123 on 2010-06-06
If VNC really is a "must have" (e.g. because of its "reconnect" feature) then I'd recommend to tunnel it through SSH. Example:

```
ssh -C -c blowfish -X -L 5910:server.internal.ip.here:5900 user@remote-host
```

What these switches do:

-C => enable comnpression; may help gain speed
-c blowfish => use the "blowfish" algorithm which supposedly is very fast
-X => forward X11 programs to the remote host
-L 5910:server.internal.ip.here:5900  => port-forward connections from "localhost:10" to the host 'server.internal.ip.here:0"

So after above command, when you execute this:
```
vncviewer localhost:10
```

... you get forwarded to the remote server's VNC screen. All traffic then travels safely inside the SSH tunnel.

But this is not ideal, to be quite frank. A safer and better performing alternative would be to use NX ... See here:
[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

---

