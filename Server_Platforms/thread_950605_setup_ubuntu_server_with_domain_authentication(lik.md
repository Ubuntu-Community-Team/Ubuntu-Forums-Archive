---
title: "setup ubuntu server with domain authentication(like windows)"
date: 2008-10-17
forum: Server Platforms
---

### Post by Yaspoon on 2008-10-17
Hey i was wondering whether this is possible yet if so whether anyone can point me in the right direction cause i've been looking and failed :). Anyway i have a ubuntu server and client pretty much i want it to that when i log into the client, it connects to the server authenticates my username and password on the server mounts certain drives depending on who i am and sets the correct permissions. The main one that i cant seem to find a way of doing is authenticating off the server (like in a windows buisness situation ie i login to domain.local the windows server it tehn check the active directory for if my user name and password are correct and so on)
any help is appreciated 
Yaspoon

---

### Post by lykwydchykyn on 2008-10-17
The most common way of doing this is OpenLDAP, but it's not trivial to set up and is way overkill for one client and one server. 

You can also accomplish this using Samba by setting up an NT-style domain and joining your client to the domain.

There is not a quick and easy analog to Active Directory/Windows Domains in Ubuntu, but there are tools available to accomplish the same things.

---

### Post by bab1 on 2008-10-17
There aare 2 new projects that create the equivalent to a Windows DC using Linux.  They are: [[COLOR="Green"]**eBox**[/COLOR]]("http://ebox-platform.com/") and [**[COLOR="Blue"]Zivios[/COLOR]**]("http://www.zivios.org/").

---

### Post by Yaspoon on 2008-10-21
Thanks guys very helpful :) ill look into it more i've got some stuff to look into now i had looked at openLDAP so ill see what i can do
Thanks
Yaspoon

---

