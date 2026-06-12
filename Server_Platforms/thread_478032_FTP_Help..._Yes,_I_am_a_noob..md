---
title: "FTP Help... Yes, I am a noob."
date: 2007-06-18
forum: Server Platforms
---

### Post by Rival904 on 2007-06-18
Well, I want to setup a small FTP for a few buddies to dump random files for each of us to access, we are constantly burning DVD's back and forth... this should make things alot easier for us.

Anyways, the planned rig is...

AMD 64 3400+
ASUS Mobo 
512MB of RAM
200GB HD

Now, heres what I have so far.

[LIST]
[*]Ubuntu Server Edition(On a DVD)
[*]Ubuntu installed and running on the machine
[*]Everything networked as I want
[/LIST]

Now, heres my problems...

At first, I wanted to get rid of the GUI, and use just a console. Well, I followed the FTP tutriol thats floating around here somewhere, and I ran into problems within the first few seconds. I couldnt get the software using the way they mentioned. No biggie, I downloaded it through the Add/Remove software. Now I go to lauch it, And it gives me an error, saying I'm not logged in as root. So I gave up going through that route. I rebooted and put in the Ubuntu Server edition, just to play around with it, and it doesnt boot to the DVD for some reason, so I get into Ubuntu and put the disk back in, still nothing. How am I supposed to install this? 

I would like to get the GUI version up and running first then play around with the console version on a spare machine(I have about 4 identical rigs set up for testing stuff like this). 

Anyways, if anyone could help me, thatd be nice, if not, point me in the right direction. I typed this up all nice and neat with hope that some people will do the same with their responses. 

Have a good day!
-Matt

:D

---

### Post by freebeer on 2007-06-18
You might want to consider installing the Desktop version of Ubuntu.  It'll automatically install the GUI (Gnome) by default.  This isn't strictly necessary, as you can install the GUI onto the Server Edition, but I have no experience with that.  Either one will allow you to run an FTP server.  

Once you've got a GUI, look for and install gproFTP (it's in the repositories).  This will give you a graphical manager for your FTP server.  There's also a very good HOWTO on this forum to set it all up.  It's what I followed.

If you have any more questions, fire away... I've got to go to bed otherwise I'd have time to answer more fully.

---

### Post by Rival904 on 2007-06-19
I do have the desktop version installed, along with gproFTP. Whenever I launch it, I get an error saying I'm not logged in as root.

---

### Post by dreadlord_chris on 2007-06-19
> **Rival904 said:**
> I do have the desktop version installed, along with gproFTP. Whenever I launch it, I get an error saying I'm not logged in as root.

launch it with gksudo

---

### Post by Rival904 on 2007-06-19
> **dreadlord_chris said:**
> launch it with gksudo

Sorry, but a little explanation?

Thanks for the help so far guys!

---

### Post by dreadlord_chris on 2007-06-19
> **Rival904 said:**
> Sorry, but a little explanation?

Thanks for the help so far guys!

press Alt-F2 - when the Run dialog comes up enter:
```

gksudo gproftpd

```
it'll then as for you password - type it in.

Walla! You are now running it with *root* privileges

---

### Post by Rival904 on 2007-06-19
> **dreadlord_chris said:**
> press Alt-F2 - when the Run dialog comes up enter:
```

gksudo gproftpd

```
it'll then as for you password - type it in.

Walla! You are now running it with *root* privileges

Run dialog...?

A step by step would be nice if you wouldnt mind.

---

### Post by Rival904 on 2007-06-19
Ok, I got the app open... Now after 2 hours, I cant get it to work right :/

---

### Post by avik on 2007-06-19
> Now after 2 hours, I cant get it to work right :/

Can you give us more information?  Any errors in particular?

---

### Post by Rival904 on 2007-06-19
> **avik said:**
> Can you give us more information?  Any errors in particular?

Just basically confusion on what to put in the GUI. Networking and the like is were I lack.

---

### Post by freebeer on 2007-06-21
> **Rival904 said:**
> Just basically confusion on what to put in the GUI. Networking and the like is were I lack.

I've been away for a few days... busy in RL.  Maybe if you post what you've done so far, we can track your steps and see what needs to be done next.

---

