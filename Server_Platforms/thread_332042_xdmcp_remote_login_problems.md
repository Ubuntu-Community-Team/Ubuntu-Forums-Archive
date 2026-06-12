---
title: "xdmcp remote login problems"
date: 2007-01-05
forum: Server Platforms
---

### Post by Epica on 2007-01-05
I have a desktop running Dapper and a server running Edgy. I have enabled graphical remote login using xdmcp using the login window options.

every time i try and use xnest, terminal server client or the login windows own xdmcp client
it displays a black screen with an X for a cursor.

xnest gives the following error message?

> error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/share/X11/fonts/TTF/, removing from list!
Could not init font path element /usr/share/X11/fonts/OTF, removing from list!
Could not init font path element /usr/share/X11/fonts/CID/, removing from list!
X connection to :0.0 broken (explicit kill or server shutdown).

 I really have no idea what is wrong as this has always worked before.
plz help me ](*,)

---

### Post by chrismyers on 2007-01-27
I'd like to bump this message because I'm having this too.

I've searched the forums with no results yet. :-({|= 

Cheers.

---

### Post by motumboe on 2007-02-06
ehr, have you solved the problem? I have the same problem...

---

### Post by chrismyers on 2007-02-06
Nope. Sorry :( 

I have had it working in the past, but I think it was Dapper. I'm now using edgy.

I'd love to know if its just broke in Edgy, or whether we just need to do bit of tweaking.

I'm still hoping for a fix.

---

### Post by Deus42 on 2007-02-15
I have the same problem.

I'm using an Edgy client with a Dapper server.

Anyone have any ideas?

---

### Post by Jabran Asghar on 2007-02-17
Was anyone able to solve the problem ?... I am also getting the same error on Edgy.

---

### Post by chrismyers on 2007-02-18
Found a fix:
 
**Host machine:**
 
1. Go to System » Administration » Login Window.
[INDENT]Select tab Remote » Style: Same as Local
[/INDENT][INDENT]Close the window
[/INDENT]2. Open a terminal & type: sudo gedit /etc/X11/gdm/gdm.conf (for Hardy /etc/gdm/gdm.conf)
[INDENT]Now search for RemoteGreeter=/usr/lib/gdm/gdmlogin
[/INDENT][INDENT]& uncomment this line.
[/INDENT]3. Search for the [xdmcp] section & scroll a few lines down until you find Enable=False
[INDENT]Change it to Enable=True
[/INDENT]4. Save & reboot. Your host is sorted.
 
**Client Machine**
 
Enable the XDMCP option in the Terminal Server Client:
 
sudo apt-get install xnest
 
I hope this helps.

---

### Post by Deus42 on 2007-02-22
hmmm, I'm still having the same problem even after following the above steps.

Does anyone know where I can try to track this problem down in the logs on the server?

Also, me problem doesn't seem to be limited to xnest. I have the same problem connecting using my clients login manager to connect.

---

### Post by penno on 2007-02-23
thanks chrismyers! Sorted my problem out nicely. :KS

---

