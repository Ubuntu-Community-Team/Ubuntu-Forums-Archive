---
title: "OpenSSH refuses my key at login after root copied file to my ~ (and forgot chown)"
date: 2008-03-01
forum: Server Platforms
---

### Post by kentl on 2008-03-01
Hi!

Suddly I can't login using SSH any more. It happens after I logged in as kent and used sudo -i, where I then copied a file to /home/kent and forgot chowning it as kent.

By some strange way OpenSSH seems to pick up on this and refused my login using key pass ever since. The catch is that I have no monitor, keyboard or mouse attached. So I'll have to do some dragging I guess.

I *might* be connecting apples and oranges here but I can't seem of any other reason why my key suddenly is refused. I did nothing else than that copy. Then trying to login again, failed.

Could someone explain why OpenSSH behaves like this?

---

### Post by rapiscan on 2008-03-01
The SSH configuration on your server has an option called StrictModes which is set to 'yes' by default.  This means that file permissions on authorized keys are verified before permitting a login.

EDIT: Sorry, I read through your post too fast.  My comment is only referring to the permissions on your authorized keys file.  If this isn't what you're referring to, then my comment is unrelated.

---

### Post by danboland on 2008-03-01
What files to you move to user kent's home directory?   There shouldn't be a problem with any of this, even if the home directory was owned by kent, you could still log in but you would get a message like this:

No directory, logging in with HOME=/

the only exception is, if the ownership of the key file on the server was owned by root and permissions forbidden you from reading it.  If thats the case, then the only way to fix the problem is to ssh as a different user or login in physically on the server. 

Dan

---

### Post by kentl on 2008-03-01
I only moved a rar file into ~. And it was a totally unrelated file. At next SSH login I get refused key. I can't wrap my head around it.

I'll move the server to the monitor and check it out tomorrow. To be continued. :-)

---

