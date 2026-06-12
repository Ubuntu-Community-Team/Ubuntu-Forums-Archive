---
title: "Apache2, need it set up for private use"
date: 2007-06-25
forum: Server Platforms
---

### Post by American_Outcast on 2007-06-25
What I want is to just use apache2 for my computer and eventually a local network. I don't want the whole world, or even part of it, lol, to have access to this.

I can't find any information that is helpful and I have searched. From what I understand I need to close port 80 in Apache2 somewhere, I am not sure where. I tried to edit the httpd.conf file but nothing is there and the only thing in ports.conf is listen 80.

if I change that to listen 127.0.0.1 I can't restart it with 

sudo /etc/init.d/apache2 restart

 so I am not sure it is the correct thing to use.


Can anyone help me or point me to a thread that I missed in my search?

Thanks

---

### Post by American_Outcast on 2007-06-25
I figured out what to change in the ports.conf. It works the way I want it to now. I just added localhost.

---

