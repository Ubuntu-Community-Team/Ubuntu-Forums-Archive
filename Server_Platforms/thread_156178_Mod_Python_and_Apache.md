---
title: "Mod_Python and Apache"
date: 2006-04-06
forum: Server Platforms
---

### Post by Jimmey on 2006-04-06
> [Thu Apr  6 19:09:01 2006] [notice] Apache/1.3.33 (Debian GNU/Linux) mod_python/2.7.10 Python/2.4.1a0 configured -- resuming normal operations
[Thu Apr  6 19:09:01 2006] [notice] Accept mutex: sysvsem (Default: sysvsem)
make_obcallback(): could not import mod_python.apache.
make_obcallback(): could not call init.
[Thu Apr  6 19:09:04 2006] [error] [client 192.168.1.1] python_handler: make_obcallback returned no obCallBack!

I get this when I try and visit [this site.]("http://jimmey.ath.cx/modP/hello.py")

Anyone know how to get this script to work?

Thanks!

---

### Post by Velvet Elvis on 2006-04-08
Make sure that you have the right versions of both mod-python and apache installed.  You can't use the apache2 version of mod-python with apache1.3 and vice versa.

It looks like you have apache1.3 running but there is really no reason not to use 2.0.  It's much easier to get running, IMHO.

You need to make sure you have libapache2-mod-python installed with a symlink from /etc/apache2/mods-available to /etc/apache2/mods-enabled.

---

### Post by Jimmey on 2006-04-08
To be honest, I'm really not sure which version of Apache I have.

When I get a server error message, It says 1.3.X. When the system shuts down, it says Apache(2). There's also Apache and Apache2 folders in /etc ( or wherever they are ).

I've installed the mod_python for 1.3. I'm not sure why my computer's showing signs of running 2 - any ideas why, or how to correct this?

---

### Post by Velvet Elvis on 2006-04-08
Sorry, that's a post-coffee question and I'm still pre-coffee. I'll try and respond with more usefull information later if nobody else gets to it first.

Pretty much you just want to go into synaptic and remove all the apache1.3 stuff and make sure the apache2 stuff is installed.

IIRC mod-python lives in the python section but everything else should be in the web or network sections. I'm not real sure what is debian and what is ubuntu at this point. 

OK.  Coffee.

Good luck.

---

