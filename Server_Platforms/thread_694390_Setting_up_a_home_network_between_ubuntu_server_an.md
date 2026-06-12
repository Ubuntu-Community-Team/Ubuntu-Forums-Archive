---
title: "Setting up a home network between ubuntu server and a windows laptop using putty"
date: 2008-02-12
forum: Server Platforms
---

### Post by James27 on 2008-02-12
maybe you guys can lead me in the right direction, or even help me understand if what i want to do is possible
i have a linux box running the latest version of ubuntu server, as well as a couple windows machines (specifically my laptop) that are using putty to ssh into my box. i have my IP and everything set up now, and i have all my files set up as i want them. this leads me to my question. When i get this all smoothed out, how can i transfer pics, .odt files, music etc between my laptop running putty and my linux box when sshing. in other words, if i forget my report at home (and im at school) and i hop on my laptop, how can i (using putty) get the file off onto my windows machine?
thanks in advanced for your help and i look forward to being a better member of the community (as opposed the occasional lurker that i already am). home this is in the right place, if not i apologize. thanks
james

---

### Post by faulkes on 2008-02-12
You can't using putty.  See below for options.

For windows, you want a program called winscp, which is a graphical fron-end, works much like any ftp client you've ever seen.  Alternatively, you can download putty.exe well known red-headed cousins, sftp.exe and scp.exe, these work like any other typical command line program (i.e. like sftp from the command line).

Connecting into your box may be a different matter altogether, depending on your setup you may need to tell your router (if you have one) to forward the appropriate ports to the internal linux box (i.e. port 22).  

And this is as good a place as any, especially considering you are running a server.  Welcome to the community.

Faulkes

---

### Post by James27 on 2008-02-12
I already forwarded the ports so im already in, in fact i've been configuring some of my settings from my laptop today (getting late but im on a roll). im going to check those out and see which is going to fan out better for  me in the end. thanks for your help
james

---

