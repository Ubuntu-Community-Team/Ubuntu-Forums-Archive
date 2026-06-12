---
title: "I wish for a help from a PRO/experienced Ubuntu/Linux server personnel, for pay!"
date: 2014-03-21
forum: The Cafe
---

### Post by August_Gislason on 2014-03-21
Sorry about the topic maybe being not too descriptive, I would have needed a few extra characters there to make it look good ;)

I shall get right to the point. I'm looking for a PRO/experienced person in setting up and securing a Ubuntu/Linux server(s) to help me, which I would of course would pay for (a beforehand decided amount that you/he/she/it is satisfied with). I am by no means some total newbie when it comes to using Ubuntu or other similarly based OS's, however I am nowhere nearly qualified enough to set up a good solid server that can securely run for long periods of time. The reason I don't just figure this out totally by myself is that I'm on my final year finishing my PH.D and I unfortunately don't have the time right now to read very much, that is not much other than my academic texts and I too really need a several servers set up securely. I had a fairly well functioning server that I had set up by myself, but the server computer got ruined when the house got caught on fire two weeks ago. It is really making my final weeks/months in finishing my PH.D a hell of a lot harder, but as I travel a lot, simply being able to access all my files/folders (etc) from anywhere via SSH was really a life saver.
     So what I wanted to ask here is if there is any PRO/experienced personnel here that would be willing to set up my server (I would describe later exactly what I need) simply over the internet. I would install the server OS and simply give a root access to the (very very lovely person) that would be willing to do this. I would be glad to pay in advance so no one would have to worry about being "ripped off".

Thank you very much for reading.
Kindest regards,
August.

---

### Post by Lars Noodén on 2014-03-21
> **August_Gislason said:**
> ... willing to set up my server (I would describe later exactly what I need) simply over the internet...

Can you go into exactly what you need so that you can reach the people with the right skills and interests?

---

### Post by coffeecat on 2014-03-21
Not a Forum Feedback thread.

*Thread moved to **The Cafe**.*

---

### Post by August_Gislason on 2014-03-21
I'm sorry for not posting this in the right section of the forum, thanks for moving it.

Lars Noodén:  well, perhaps I could have been a little bit more clear in my writing. What I'm looking for is simply someone with enough knowledge to safely set up a SSH server, file server/storage server (remotely accessible for my data), and for now, that should be it - I can live without the other servers/softwares I had installed by myself as they're not important for me right now - as my priority is of course to finish what I have to do for my graduation. Not a very complicated task probably, but I'm no geek and unfortunately don't have the time to sit and read/watch video tutorials and do this myself. Thank you. ;)

---

### Post by lykwydchykyn on 2014-03-21
> **August_Gislason said:**
> I'm sorry for not posting this in the right section of the forum, thanks for moving it.

Lars Noodén:  well, perhaps I could have been a little bit more clear in my writing. What I'm looking for is simply someone with enough knowledge to safely set up a SSH server, file server/storage server (remotely accessible for my data), and for now, that should be it - I can live without the other servers/softwares I had installed by myself as they're not important for me right now - as my priority is of course to finish what I have to do for my graduation. Not a very complicated task probably, but I'm no geek and unfortunately don't have the time to sit and read/watch video tutorials and do this myself. Thank you. ;)

Since all you really need for this is installing ssh on the server and configuring your router to forward SSH, by the time you were set up for anyone to remote in and configure it for you the job would be done.

---

### Post by Lars Noodén on 2014-03-22
> **lykwydchykyn said:**
> Since all you really need for this is installing ssh on the server and configuring your router to forward SSH, by the time you were set up for anyone to remote in and configure it for you the job would be done.

+1

SSH is simple to set up, just add the package openssh-server.  Then you automatically get SFTP as part of the package and that gives you a secure way to access you files either via the program sftp, the file manager (e.g. Nautilus) or the utility sshfs.  

Set up SSH and then check it from your LAN.  If that works, configure your router to keep giving the machine the same IP number.  Then set the router to forward an external port to port 22 (SSH) on your machine.  At that point you'll be able to even have someone turn on the machine while you are away and connect to it from anywhere and get at your files securely.

---

### Post by TheFu on 2014-03-22
+1 - I would add installing **fail2ban**.

And be certain to setup key-based authentication.  Google "secure ssh" to find these. Should be 15 minutes, tops.

---

