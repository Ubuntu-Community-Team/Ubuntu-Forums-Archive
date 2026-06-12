---
title: "webserver installation"
date: 2011-08-25
forum: Server Platforms
---

### Post by slaz on 2011-08-25
Hello,
 
I am in the process of setting a webserver. I used Ubuntu server 11.04, installed lamp. Everything is up and running, I checked the log files for apache2, and seen morpheus *** scanner entry in it. After googling that, it might be a web crawler, or someone scanning my webserver. Since this server is going to sit on the outside, is the ufw secure enough as it is by default? I also would like to set ftp up on it, which ftp server would be the best to use for user to remotely access a directory to edit the webpage? 
 
Thanks for the help in advance,
 
slaz:P

---

### Post by Monolith on 2011-08-25
If your box is visible to the outside world, get ready for LOADS of computers sniffing around at your box.

My box gets literally tens of different IP-addresses sniffing around at various ports, trying various logins, etc.

Make sure you lock down unused ports, follow the usual precautions (no root login for SSH, strong passwords, etc) and you'll be fine. There no inherent danger in people sniffing out your box, as long as they can't get in. All they do is clutter up your log files.

FTP is not a very secure protocol, I would strongly recommend using SFTP. Or you could install Webmin with Usermin ([www.webmin.com](www.webmin.com)).

---

### Post by slaz on 2011-08-25
> **Monolith said:**
> If your box is visible to the outside world, get ready for LOADS of computers sniffing around at your box.
 
My box gets literally tens of different IP-addresses sniffing around at various ports, trying various logins, etc.
 
Make sure you lock down unused ports, follow the usual precautions (no root login for SSH, strong passwords, etc) and you'll be fine. There no inherent danger in people sniffing out your box, as long as they can't get in. All they do is clutter up your log files.
 
FTP is not a very secure protocol, I would strongly recommend using SFTP. Or you could install Webmin with Usermin ([www.webmin.com]("http://www.webmin.com")).
 
Hi Monolith,
 
Thanks for the information, is vsftp the same as sftp?

---

### Post by Monolith on 2011-08-25
> **slaz said:**
> Hi Monolith,
 
Thanks for the information, is vsftp the same as sftp?

Very different things. Check out this thread for some interesting information:

[http://www.linuxquestions.org/questions/linux-software-2/sftp-versus-vsftpd-590454/](http://www.linuxquestions.org/questions/linux-software-2/sftp-versus-vsftpd-590454/)

---

### Post by Dangertux on 2011-08-25
Something I thought I'd add to this. 

When running a web server most individuals fail to realize there is an entire facet to security outside of the typical network intrusion. IE: Port scan, find vulnerable application, exploit vulnerable application. That is only one way of doing things. While this should be taken into consideration, things like sql injection and xss can be equally devestating and are far more common, they also frequently will not even require something "easy" to detect like a failed login or a port scan. 

Keep this in mind when using or developing web applications.

---

### Post by slaz on 2011-08-25
I see how to setup sftp, is there a way to lock that user to a specific directory? Once they are locked to that directory, would creating a link in that directory to the web pages be the way to do it?
 
Thanks,
slaz

---

### Post by Lars Noodén on 2011-08-26
> **slaz said:**
> I see how to setup sftp, is there a way to lock that user to a specific directory? 

You can do that by using the ChrootDirectory directive in OpenSSH's configuration.  It works seamlessly out of the box with [SFTP](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads).  If you want to do shell access then that is more work but doable.

---

### Post by inphektion on 2011-08-26
Consider moving your ssh port from 22 to something else.  that will block a lot of attempts alone.  also i'd recommend against not installing any webadmin, phpmyadmin, etc.  half the scripts that run against my sites seem to check for those.  I'd supplement with fail2ban to ban them after x attempts so they just can't pound on you.

---

### Post by Lars Noodén on 2011-08-26
> **inphektion said:**
> so they just can't pound on you.

Port 22 is fine.  But you can use IP tables to throttle bruteforce attacks.

```

   ip6tables -N SSH;    # create chain
   iptables  -N SSH;    # create chain

   # send all incoming SSH trafficc to SSH chain
   ip6tables -I INPUT -i eth0 -p tcp --destination-port 22 -m state --state NEW -j SSH;
   iptables  -I INPUT -i eth0 -p tcp --destination-port 22 -m state --state NEW -j SSH;

   # iptables -I INPUT -p TCP -m state --state NEW -m limit --limit 30/minute --limit-burst 5 -j ACCEPT

   # add host to "recent" list
   ip6tables -I SSH -m recent --set --name SSHLIMIT -j ACCEPT;
   iptables  -I SSH -m recent --set --name SSHLIMIT -j ACCEPT;

   # allow finite number of new connections per time limit
   ip6tables -I SSH -m recent --update --seconds 60 --hitcount 4 --name SSHLIMIT -j REJECT
   iptables  -I SSH -m recent --update --seconds 60 --hitcount 4 --name SSHLIMIT -j REJECT

```

---

### Post by inphektion on 2011-08-26
uhm yea its fine in that it works.  But everyday in my logs on every server publicly exposed to the internet there are attempts to login with various scripted names via port 22.  By simply changing the port to something like 2222, every single one of those attempts have disappeared.  I'd still say you should port limit it via iptables or ufw and i also have fail2ban sitting there watching it but since the move to the non standard port it has needed to ban zero IP's.  
And its not a hard change.

---

