---
title: "Unsecured VNC"
date: 2011-03-15
forum: Security
---

### Post by Chrissd on 2011-03-15
Hi,

Can anyone advise me if it's safe enough to run VNC unsecured over a local network, secured with WPA? Or is it just not really worth the risk and best to use SSH?

Thanks

---

### Post by Grenage on 2011-03-15
I would personally never use unsecured VNC, and rarely VNC; for linux, I prefer nomachine nx.  While the Wifi is secure, it could establish a connection through the router using uPnP.

---

### Post by Chrissd on 2011-03-15
My situation is I need to move the mouse on the screen remotely. I'm using the PC as a TV, playing on demand content.

Would the program you suggested be suitable for this?

Thanks in advance!

---

### Post by Grenage on 2011-03-15
I don't know if nomachine nx has a windows client, but if they are both Linux machines, yes!  It's a great remote desktop tool.  Far more responsive than VNC, and far more secure.

---

### Post by Chrissd on 2011-03-15
Is it secured by default or have to be tunneled through SSH?

---

### Post by Grenage on 2011-03-15
It wraps its own connections in SSH, so you'll not have much to worry about, as long as SSH is installed.

---

### Post by Chrissd on 2011-03-15
Sounds perfect, I'll look into it tonight.

---

### Post by Chrissd on 2011-03-15
Hi, I found a FreeNX guide and from what I understand, it's an open source version of NoMachine's NX.

I kind of have it setup at the moment, but it just seems to be opening up a session in a Window, rather than letting me start stuff on the remote screen, like VNC.

Any advice as to what I'm doing wrong or is FreeNX totally different to NX?

Thanks

---

### Post by Grenage on 2011-03-15
Oh no, it should be fine.  Is there a 'shadow desktop' option on the client?  I've not done what you are doing (I always use a new session), but I'm sure it's an option.

Ah, here: (I linked the cache, because for some reason I can't access the nx site at the moment.)

[http://webcache.googleusercontent.com/search?q=cache:spEgZIJIX6MJ:www.nomachine.com/ar/view.php%3Far_id%3DAR11B00098+http://www.nomachine.com/ar/view.php%3Far_id%3DAR11B00098&cd=1&hl=en&ct=clnk&gl=uk&source=www.google.co.uk](http://webcache.googleusercontent.com/search?q=cache:spEgZIJIX6MJ:www.nomachine.com/ar/view.php%3Far_id%3DAR11B00098+http://www.nomachine.com/ar/view.php%3Far_id%3DAR11B00098&cd=1&hl=en&ct=clnk&gl=uk&source=www.google.co.uk)

---

### Post by Chrissd on 2011-03-15
I have NoMachine's NX working brilliantly now! Thanks!

---

### Post by Grenage on 2011-03-15
Glad to hear it!

---

