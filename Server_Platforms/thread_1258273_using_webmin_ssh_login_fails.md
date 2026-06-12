---
title: "using webmin ssh login fails"
date: 2009-09-04
forum: Server Platforms
---

### Post by tkman26 on 2009-09-04
Hello all.
I have Ubuntu 9.04 installed, and am trying to use webmin 1.480 from an xp box.  In webmin is a SSH login.  When I click this it prompts me for a login name and password.  
I enter the same name and password I use for logging into webmin and for when I log directly into the server.  It does not work though.  Text at the bottom of the display window change to "not connected" and offline.
I have tried ssh <userid>@localhost and this works fine on the ubuntu server.  
Any suggestions about how to track this problem down would be appreciated.
Thanks
Todd.

---

### Post by tkman26 on 2009-09-05
Well just tried Putty from xp and this works no problem.  Thus it must be a bug with the implementation of SSH in webmin. 
Will contact the developers and see if this is a known issue.

---

### Post by tkman26 on 2009-09-05
I did a little further and find that the SSH plugin relies on Java and I look in the Java console and can see errors.
I am beginning to believe this is an integration bug with webmin and the SSH plugin.  Have contacted both the ssh developer and the webmin team.

---

### Post by DPeng on 2009-11-02
I have the same problem, my office environment only allow 80 or 443, so i can only control my Ubuntu box via web interface. shame i cannot use the SSH of Webmin..

any update yet?

---

### Post by DraZtiK on 2009-11-12
Just wanted to see if I can help...I run a Debian server but was searching the net for an answer as to why I could not get the SSH Login module working either and popped up here. more digging and I found an alternative to the what I believe achieves the same goals.

Shellinabox webmin module. 

Can be downloaded here... [http://www.webmin.com/download/modules/shellinabox.wbm.gz](http://www.webmin.com/download/modules/shellinabox.wbm.gz)

Install as you would any other webmin module and can be found under the "others" category of webmin labeled Shell in a box. worked for me...good luck!

---

### Post by DPeng on 2009-11-13
Tried that Shellinabox thing, but it has error saying that it only works at x86 Linux system...I am running AMD64......

---

### Post by nsimos on 2009-11-26
> **DPeng said:**
> Tried that Shellinabox thing, but it has error saying that it only works at x86 Linux system...I am running AMD64......

There's a new version of shellinabox which supports 64bit systems.

You can find it [here]("http://download.webmin.com/download/modules/shellinabox.wbm.gz") ;)

---

### Post by Thirtysixway on 2009-11-26
Change Localhost to the IP of the system.  For my webmin, I changed it from localhost to the external address of my server and it worked.  So if you're just going to be doing it inside lan, changing localhost to the lan IP of the server should work.

---

### Post by DPeng on 2009-11-26
> **nsimos said:**
> There's a new version of shellinabox which supports 64bit systems.

You can find it [here]("http://download.webmin.com/download/modules/shellinabox.wbm.gz") ;)


Successfully installed and loaded, but what should i type to connect?
i tried *localhost, Server IP, EXt IP.....*

what sort of format i should be using? i just keep getting error message saying 
"cannot open connection"

---

### Post by DPeng on 2009-11-27
> **Thirtysixway said:**
> Change Localhost to the IP of the system.  For my webmin, I changed it from localhost to the external address of my server and it worked.  So if you're just going to be doing it inside lan, changing localhost to the lan IP of the server should work.

Did change hostname to my external ip address, and seems connected and login correctly, but i cannot type anything.....damn it...

---

### Post by IrishWristwatch on 2010-03-10
The SSH module on Webmin is old and updated.  I haven't been able to get it to work with my Ubuntu box.  However, the third-party module **SSH2** has worked wonderfully.

To install it go to **Webmin** > **Webmin Configuration** > **Webmin Modules** and select _SSH2_ from the list **"Third party module from"**.

---

### Post by yaztromo on 2010-03-17
> **IrishWristwatch said:**
> The SSH module on Webmin is old and updated.  I haven't been able to get it to work with my Ubuntu box.  However, the third-party module **SSH2** has worked wonderfully.

To install it go to **Webmin** > **Webmin Configuration** > **Webmin Modules** and select _SSH2_ from the list **"Third party module from"**.

Accepted solution :D

Thank you.

---

### Post by grendelkhan on 2010-10-18
> **DPeng said:**
> Successfully installed and loaded, but what should i type to connect?
i tried *localhost, Server IP, EXt IP.....*

what sort of format i should be using? i just keep getting error message saying 
"cannot open connection"

Did you ever get this resolved? I'm having the same problem.

---

