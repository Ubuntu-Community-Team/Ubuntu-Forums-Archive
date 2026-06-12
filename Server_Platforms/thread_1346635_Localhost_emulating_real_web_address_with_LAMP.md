---
title: "Localhost emulating real web address with LAMP?"
date: 2009-12-05
forum: Server Platforms
---

### Post by Rallg on 2009-12-05
I have Karmic desktop version, with Apache LAMP configured. The software runs, no problem.

I do not intend to serve files to anyone else. Instead, I wish to emulate my "real" web site (hosted commercially on the Internet) on my own computer, so that I can see how some things look before I upload them to the "real" server. PHP is involved. My "real" host server is using Linux with a configuration very similar (as far as I can tell) to what I can download and install in Ubuntu on my own computer.

On the "real" server, I am a share user (my directory over there is /home/myusername/). I can duplicate that locally.

Now, for the trick question: My "real" web site is at something such as abcdefghijklmnop.com. Is there any way I can configure the virtual host on my own computer, so that it thinks it is at abcdefghijklmnop.com while it is actually reading my hard drive? Of course, I do not wish to interfere with the "real" web site, or interfere with my ability to connect to it.

Yes, I realize there's a pile of Apache documentation. But I am not knowledgeable enough to wade through all of it. Perhaps one of the users here know the answer, right off the top?

---

### Post by BkkBonanza on 2009-12-05
You would configure Apache on your local machine the same way as on the server.
Then you would put the domain name you want to route to your local Apache in your /etc/hosts file with the localhost address 127.0.0.1.

Now, you cannot have the same domain be handled by both servers at the same time. You would have to comment out the line in /etc/hosts if you want the domain to revert back to the real site on the web.

When you put an address in your browser  it starts by looking up the domain name. The first stop is the /etc/hosts file, then it gets passed out to whatever DNS server is appropriate. By changing the /etc/hosts file you divert that domain to use your local machine isntead of the one on the internet.

eg. in /etc/hosts

127.0.0.1  [www.mydomain.com](www.mydomain.com)

---

### Post by Rallg on 2009-12-05
Thanks. Sounds do-able.

I was hoping it would be as easy as turning Apache on or off. Guess not.

I could also log in with different user names (or switch users), but I'm not sure if /etc/hosts could be customized for different users.

Might be that I'll come up with a root script that will change /etc/hosts as needed, put it on my Applications menu, and switch from "real" to "virtual" that way.

The only reason I wish to imitate the "real" address is that within my site, some of the internal links use absolute URLs. If they were all relative to the file system, it wouldn't matter.

---

### Post by BkkBonanza on 2009-12-05
The /etc/hosts file is system wide, not per user.
Probably the quickest switcheroo method would be using a symbolic link.
Then you alter the link by script as needed.
eg. script,
sudo ln -s /etc/hosts.$1 /etc/hosts

and call the script with a parm indicating version to make current

---

### Post by Rallg on 2009-12-05
Thanks. I'll play around with it.

Incidentally, there's no danger that I will forget whether I am looking at my "real" site online, or the one on localhost. There is a stylesheet difference in one of the backgrounds. If it's white, I'm online; if it's another color, I'm on hard drive.

---

### Post by bab1 on 2009-12-06
> **BkkBonaza said:**
> ...

When you put an address in your browser  it starts by looking up the domain name. The first stop is the /etc/hosts file, then it gets passed out to whatever DNS server is appropriate. By changing the /etc/hosts file you divert that domain to use your local machine instead of the one on the internet.

eg. in /etc/hosts

127.0.0.1  [www.mydomain.com](www.mydomain.com)

This is not quite accurate.  If you put an IP address in the browser, the browser retrieves the requested file directly.  IP addresses are *_mapped _*to human readable names as a convenience for humans (i.e. if you put a legit name in the browser, it is converted (mapped) to the IP address).

The OP will gain little by doing all of this.  I would recommend using something like the following in the /etc/hosts file```
<private_IP> test.com
```

This will show that all parts of the Apache web server is working.  The is no need to script the *turning off/on * of anything.

Not sure why eveeryone uses "localhost"  It does not involve the installed NIC.  It is a virtual interface.  The same host also has an IP address for the NIC defined as eth0 or some such and is private to the LAN if using NAT.

---

### Post by BkkBonanza on 2009-12-06
I'm afraid you misunderstood. When I said "put an address in the browser" I meant what people typically do, which is type an URL, a website address in common folk talk. I realize absolutely that if you type in an IP then it can connect directly. 

That is not what he wants though. He wants to type in his web address (URL) and get his local web site, and be able to get the real site too. Nothing at all wrong with using 127.0.0.1 for that in the /etc/hosts and I don't know why you think he won't be able to do that. I've been doing it for more than 13 years and have never had a problem. Sure, you can use your local LAN IP address if you like as well. But it's easier to describe to him this way.

He only needs a script if he wants to change the hosts file between the real site and his local one. That will work fine and is an easy way to do it.

---

### Post by Rallg on 2009-12-21
Bkk was describing what I had in mind.

In the end, the best solution will be to edit some PHP code so that relative addresses are used. Not having much knowledge of PHP, I hesitated to do it that way.

---

