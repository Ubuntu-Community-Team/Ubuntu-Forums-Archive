---
title: "PHP based gui for iptables?"
date: 2006-10-04
forum: Server Platforms
---

### Post by rocktorrentz on 2006-10-04
I've set up a basic LAMP server and am very pleased with the results so far. However I find the iptables command interface very complicated and I just wondered if there is a decent GUI which would allow me to administer the firewall from a web browser. 

Thanks
rocktorrentz

---

### Post by paul.maddox on 2006-10-04
Try webmin, it covers lots of aspects of server management including iptables.

[www.webmin.com](www.webmin.com)

---

### Post by lkagan on 2006-10-04
Indisputably the most popular open-source gui for server administration is webmin ([http://www.webmin.com/index.html)](http://www.webmin.com/index.html)).  I'm not sure if it's written in PHP but it is open source and it does handle iptables/ipchains as well as a number of other firewalls along with just about any other server administration tool you could want.

I have to say though, I don't agree with having a web interface to server administration.  I think it's too much of a security risk.  However, many people disagree with me on this.  Just make sure you lock it down and don't send passwords over an unencrypted network.

Larry

---

### Post by paul.maddox on 2006-10-04
> **lkagan said:**
> I don't agree with having a web interface to server administration.  I think it's too much of a security risk.

I couldn't agree more!
Whatever you do, make sure webmin (or any other tool) is firewalled off so that only your IP address (and preferably one backup IP) can access it.

And buy a book on administration from the commandline!

:)

---

### Post by rocktorrentz on 2006-10-05
Thanks for all the replys. I'll install webmin and will definitely set it up so only my pc can access it. I do intend to learn command line administration but I just want a simple way to set up some good firewall rules while I learn.

Thanks again
rocktorrentz

---

### Post by lkagan on 2006-10-05
Even once you get good at command line administration, iptables is one of those things that are just really difficult to remember.  But if you want to get started with command line admin, check out the free Ubuntu Server guide located here: [https://help.ubuntu.com/](https://help.ubuntu.com/)

Larry Kagan

---

### Post by peanut butter on 2006-10-06
BTW webmin is written in CGI. it contains its own webserver on port 10000

so to get to webmin on local machine go to [https://127.0.0.1:10000](https://127.0.0.1:10000)

before installing you should set a root password.

---

### Post by lkagan on 2006-10-06
I just downloaded and looked at the code for webmin.  It's written in Perl.  Perl is sometime referred to as CGI.  However CGI stands for Common Gateway Interface.  CGI is a method of serving dynamic pages that can be written in a number of different languages including Perl or C.  If you know PHP, then perl shouldn't be that hard to modify should you feel so inclined.

Larry Kagan

---

