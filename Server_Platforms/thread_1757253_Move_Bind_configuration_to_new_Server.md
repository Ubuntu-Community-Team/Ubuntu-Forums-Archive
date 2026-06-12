---
title: "Move Bind configuration to new Server"
date: 2011-05-13
forum: Server Platforms
---

### Post by sdsnyr94 on 2011-05-13
I hope someone can help me out with this, as I am a little pressed for time.

We have a Suse 9.3 server running Bind for DNS. This server is also our e-mail server, and we are replacing it as part of an upgrade. The new server is Ubuntu 10.04, and I am looking to move the DNS server information to this new server.

I have no experience at all with Bind9, and an average knowledge of Linux commands. I have tried copying the zone files to the new server, along with the named.conf file, but could not get Bind to restart. Running "tail -f /var/log/syslog" I see some permission errors with the named.conf file. I have tried changing permissions and ownership of the file, but nothing seemed to help.

I have now reverted all changes I made, and have Bind running with the default configuration. Can someone please walk me through the correct steps of moving this data to the new server?

As I have said, I am a little pressed for time. I have a lot of projects running at one time, and not a lot of time to sit down and read up on how to properly do this. After this is complete, if someone could link a good resource so that I can read up on this to better understand it (when things settle and I have more time), it would also be appreciated. 

Thank you in advance for the help.

---

### Post by sdsnyr94 on 2011-05-16
Can anyone please help?

---

### Post by hawkmage on 2011-05-16
I am not sure how SUSE has their BIND set up but the config should be fairly easy to move over.  One thing to consider is what user the BIND service runs under, on Ubuntu it runs under its own user "bind".  Also you will have to verify that the path to the zone and other files in the named.conf are correct if the directories are different between SUSE and Ubuntu.  Also is the SUSE implementation of bind a chrooted instance of bind?

What files are you getting the permissions errors on?

---

### Post by sdsnyr94 on 2011-05-16
Thank you for the reply!

> Also is the SUSE implementation of bind a chrooted instance of bind?
I am making an assumption here, but I think it may be because everything is located in /var/lib/named.

> One thing to consider is what user the BIND service runs under, on Ubuntu it runs under its own user "bind"

This was something that confused me. Does this mean that the Ubuntu install of Bind already runs chrooted? 

I had tried to follow a tutorial on running Bind in a chroot, and then I moved the configuration files to they're <I think> proper location. I copied and edited the named.conf file so that the path to the zone files were correct. When I tried to start Bind, I was getting permission errors on the named.conf file. I made sure the user and group were "bind" but that did not help. At that point I figured I was over my head and reverted everything that I had done.

---

### Post by sdsnyr94 on 2011-05-16
I think this should confirm that the SUSE 9.3 is running in a chroot.


mail:~ # ps aux | grep named
named     7564  0.0  1.2  40656 12624 ?        Ssl   2010 134:22 /usr/sbin/named -t /var/lib/named -u named

---

### Post by hawkmage on 2011-05-16
OK, that tells me that your SUSE BIND is running chrooted.  If you tried to run BIND chrooted on Ubuntu do you have AppArmor installed and running?  If so it could be causing the permissions errors.  

Have you seen this: [http://ubuntuforums.org/showpost.php?p=5828381&postcount=17](http://ubuntuforums.org/showpost.php?p=5828381&postcount=17) About AppArmor and chrooted BIND on Ubuntu?  Also keep in mind all of the paths in the BIND config files are relative to the chrooted directory.  

If you coulf post some of the permissions errors it may help.

---

### Post by sdsnyr94 on 2011-05-16
I will have to double check in the morning... but I think I checked and AppArmor was not installed. 

Thanks for your help so far.

---

### Post by brettg on 2011-05-17
It will probably be easier and more successful for you to just reconfigure Bind from scratch [using this guide]("http://tuxnetworks.blogspot.com/2011/01/howto-caching-authorative-nameserver.html");

It should only take half an hour and you can just use your old zone file during that process.

---

### Post by sdsnyr94 on 2011-05-18
Thanks for the link brettg... that got me going. Now bind appears to be running properly, and using the original config.

Now, that tutorial does not have Bind running in a chroot. Since AppArmor is on the server (I was wrong in a previous post), is this a security issue? 

Thank you both for all the help!

---

### Post by hawkmage on 2011-05-18
AppArmor is supposedly as secure if not more secure than using chroot.

---

