---
title: "ubuntu server goes to sleep"
date: 2010-03-10
forum: Server Platforms
---

### Post by stdcinout on 2010-03-10
hi guys i have problem here : 

i have installed ubuntu server with webmin so far 
but if i dont touch the keyboard for certain times it will be "sleeping" and i could n't access to webmin and so on 

i need to wake it up by touching the keyboard and all other processes will resume 

this can be seen from my monitor switching off. 

where do we configure this kind of power management thing on ubuntu ? does it always like this ? I don't think this is a very good idea for server platform.. 

looking through the log messages does not really tell what caused this. it was not because network inactivity or nothing but it just goes to sleep ( kinda like using a laptop )

thanks

---

### Post by jonabyte on 2010-03-10
Are you sure it's not just the monitor...and no I am not being a smarta$$...:D

---

### Post by FiveSidedPoly on 2010-03-10
I don't think your server is going to "sleep" but I could be wrong.  When I switch connections on my monitor the screen shows all black like you said, unless I connect a keyboard to the server and press a key.  But I believe there are settings in Webmin that may affect the state of the connection after a prolonged time.
 
I can't give you better help on it, I stopped using Webmin after it kept screwing up the config files of anything I tweaked it with.  I can't recommend eBox on Karmic, tried an install last night following the Official Server Guide, when I opened the browser up none of the modules would show up.  They say to use Hardy with eBox and you should have no problems.
 
I'm sticking to CLI for now, hope Lucid offers something quick and easy for some tasks.
 
Have you tried to SSH into the server?  That will tell you if something is happening and let you troubleshoot the problem.

---

