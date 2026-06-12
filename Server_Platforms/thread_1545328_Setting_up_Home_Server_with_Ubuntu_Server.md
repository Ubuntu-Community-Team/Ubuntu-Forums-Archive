---
title: "Setting up Home Server with Ubuntu Server"
date: 2010-08-03
forum: Server Platforms
---

### Post by corrytonapple on 2010-08-03
I would like to create a low traffic server for a few websites, email server, and file server for our house (backups too!). One will be the one in my signature. I will use an homemade computer. Now, how would I go about setting it up with Comcast residential? I am not hosting an online store. I have read one of the many agreements, and it doesn't mention it. For setting up the server I have this page.
[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html) 
Thanks for the Help

---

### Post by Raymond2201 on 2010-08-03
I dont think it makes much of a difference what ISP you have (aside from maybe port blocking and the like) to set up your own webserver.

Basically what you need is:

Apache
PhP (Optional but likley you will need this or some other scripting language)
MySQL (Optional)

[https://help.ubuntu.com/10.04/serverguide/C/httpd.html](https://help.ubuntu.com/10.04/serverguide/C/httpd.html)

The only other thing you would need to do is route some ports after you have set everything up locally to forward port 80 (or another one if this is blocked) to your webserver machine on your local network. 
this is typically done through your router and instructions on how to do this differ based on the make and model of your routing equipment.

---

### Post by corrytonapple on 2010-08-03
> **Raymond2201 said:**
> I dont think it makes much of a difference what ISP you have (aside from maybe port blocking and the like) to set up your own webserver.

I have read other things on different forums and it's a mixed discussion. Most say its fine if there's not a lot of traffic. More thoughts?

---

### Post by Raymond2201 on 2010-08-03
found this in their ToC

> 
Technical restrictions:
use or run dedicated, stand-alone equipment or servers from the Premises that provide network content or any other services to anyone outside of your Premises local area network (“Premises LAN”), also commonly referred to as public services or servers. Examples of prohibited equipment and servers include, but are not limited to, e-mail, Web hosting, file sharing, and proxy services and servers;

use or run programs from the Premises that provide network content or any other services to anyone outside of your Premises LAN, except for personal and non-commercial residential use;


[http://www.xfinity.com/terms/acceptable-use/](http://www.xfinity.com/terms/acceptable-use/)


Basically you can use it for non-commercial use. everything else is a no no it seems.

---

### Post by corrytonapple on 2010-08-03
Well, what could go wrong? I lose my Internet service and owe money.:D Are all of the details to setting up a home server in that guide I linked to? What about giving it a domain name? I assume its in there. Just haven't looked through it yet.............

---

### Post by Raymond2201 on 2010-08-03
Pretty sure you could/will get your Internet stopped should they want to find out about your site for any reason.


All you need to get a web server up and running is (Apache) which is covered in that guide.

The domain name thing, well i would suggest sorting out your Apache install and basic website design/testing.

A good idea before you think about "unleashing" your website on the interweb!

But setting up a domain etc.. is trivial at best.


have fun

---

### Post by StolerTech on 2010-08-03
forget it...

---

### Post by corrytonapple on 2010-08-03
Let me get a machine. It may be a while, got some other ones I need to get rid of.

---

### Post by corrytonapple on 2010-11-01
Well, I need to get things straight. I am picking out hardware for my machine. But here is my issue. This server will be a website server, email server (EX: @custom.com), and a home file backup server (store music, pictures, videos, ect). Now, what processor should I use? Server or Desktop for this kind of use. None of the sites are going to get too busy. Well, not now at least.....

---

