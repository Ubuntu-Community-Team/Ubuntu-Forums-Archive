---
title: "[SOLVED] Server or desktop for web server use?"
date: 2008-02-27
forum: Server Platforms
---

### Post by rumblestrut on 2008-02-27
The place I work  for is currently using Red Hat, but the only thing we're using it for is on our web sever.

I'd personally like to make the switch to Ubuntu for a variety of reasons, but the thing that annoys me about the server version is the lack of a GUI.

If I install the desktop version on our server and then get a LAMP server running on it as well, is there anything wrong with that? It should hold up just as well as the server version, right?

Thanx in advance.

Eric

---

### Post by astrotech226 on 2008-02-27
The desktop and server versions are technically the same.  They use identical packages and everything.  The difference is what they install.  The desktop version installs a myriad of extra stuff that would be considered pointless on most servers.  The server install strips out just about everything except what it needs.

And if you install server and decide later you need a gui, it can be added later pretty easily.

---

### Post by rumblestrut on 2008-02-27
"The desktop version installs a myriad of extra stuff that would be considered pointless on most servers."

Sounds like Red Hat. :)

Thanks for the fast input! 

I presume adding the GUI to the server is about as difficult as adding KDE or GNOME after installing with only one or the other? (Which, do be honest, I didn't find that hard on my desktop machine.)

---

### Post by Fire_Chief on 2008-02-27
Yup, you got it. :)
```
sudo apt-get install gnome
or
sudo apt-get install kde
```

On a side note, you may also want to try a lighter desktop like XFCE or fluxbox to use fewer resources on the system.

---

### Post by HermanAB on 2008-02-27
You can always shut X11 down when you are done configuring stuff with 'sudo init 3' and start it up again when you need it with 'sudo init 5'.

---

