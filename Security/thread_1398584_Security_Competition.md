---
title: "Security Competition"
date: 2010-02-04
forum: Security
---

### Post by enduser000 on 2010-02-04
Hello,
     My school recently started a security group and we're about to embark on our first competition.  I'm told we can't get many details about the competition, but I know that we will have to secure a Cisco network and at least 5 different servers.  We decided to 'divide and conquer' this setup, so I'm the main guy securing both the Ubuntu and CentOS servers.  On the ubuntu server (headless, remoting in from SSH) there will be a file server that will need to be up for the duration of the game.  The CentOS box will be running some kind of IDS (hopefully snort, I'm told), and a MySQL server.  All I know is that these services need to be up throughout the duration of the game while the other team tries to shut us down.  If they do break in or mess something, we need to find out, report the incident, and get up and patched as soon as possible.  I'm writing this to ask you all about a few tools I need to learn about before we delve into this competition.  The first of these tools is nmap, the second is snort, other than that any IDS and port scanning utilities would be nice, and I'm open to recommendations of anything I should try before the game.  Thanks for your comments, speculations, and any help in advance,

end

PS: I'm told this is not cheating as long as you don't tell me things about the competition I don't/am not allowed to know.  I'm not going to mention the name of it (don't know it offhand), so that shouldn't be a problem :)

end again

---

### Post by bodhi.zazen on 2010-02-04
Good luck to you, google will give you much of what you want.

If you have a specific question, please ask.

---

### Post by rookcifer on 2010-02-04
Lock the CentOS box down with SELinux.  There is a box someone put online with open shell access, but it has been locked down by a SELinux policy.  It hasn't been cracked yet.

---

### Post by bodhi.zazen on 2010-02-04
By default Centos uses a targeted selinux policy.

The box you are referring to uses full SELinux, and while effective, takes some time to get working ;)

---

### Post by witeshark17 on 2010-02-04
Looks like a fun game; please keep us posted! :popcorn:

---

### Post by enduser000 on 2010-02-05
Hello,
     Thanks for your interest in this.  As I read more I get more interested too.  I guess my questions to start would be these:

1. SELinux sounds like a good idea, do Ubuntu Server and CentOS Server come with command line tools to configure this?

2. Where are the good Ubuntu Server (headless) + file server tutorials? :P

3. Should I update an out of date system to a new version? ... or possibly just try to secure it from there.

4. Where are the really good tutorials on logs? (securing and reading)

5. What's a good way to remove everything on the system I don't need? I'm assuming when I get the machine all kinds of unnessecary things'll be running and installed and I need to remove, reconfigure, or reinstall them.

6. Should I chmod the whole thing?  Should I try to encrypt it too?  We're supposto keep 'normal business operations' so I'll need the outside world to be able to do what they're supposed to be able to do (file server on Ubuntu, MySQL/IDS on CentOS), and things like encryptions/permissions shouldn't hinder this.

I hope to learn all of this and more in less than a month!  They'll be after our network and I don't intend to make it easy on them and their automation tools ;D

end

EDIT: Added 5 and 6

---

### Post by adam814 on 2010-02-05
[http://beginlinux.com/blog/2009/10/ubuntu-9-10-chroot-jail-for-ftp/](http://beginlinux.com/blog/2009/10/ubuntu-9-10-chroot-jail-for-ftp/)

That might help out since you'll be running a file server.  I'd also suggest using fail2ban or denyhosts (or iptables for that matter) to slow down any brute-forcing they might do.

As a general practice I'd lock down any ports you're not required to use.  Ideally you'd only have SSH open and users would need to forward ports for any other services.  I'd also recommend key-based authentication for SSH instead of passwords.

---

### Post by enduser000 on 2010-02-12
Hey,
   Thanks so far for the links.  So far we've set a few test computers up and are planning to get together to test them soon.  In the mean time I had a question for you all.  What exactly can you use for a 'file server'?  Do you just set your computer up on the net and say "Here are my files!"? or is there something else involved.

I ask because one of the machines originally was supposed to be an FTP server, and when it was changed it changed to running Ubuntu and being a file server. And definition of the differences or how to go about playing with file server software would be greatly appreciated, thanks,

end

---

### Post by Cabs21 on 2010-02-12
what OS are you using for this game/competition?  If you are not required to use single OS I would recommend looking into BackTrack.  It is great for security testing but can be used for other purposes.  It was written from Ubuntu.  (Backtrack is to Ubuntu as Ubuntu is to Debian)  Just a thought I use it to test my wireless security and passwords.  comes standard with about 20 different wireless security tools for cracking and testing and comes with several password cracking tools.  Very useful.

After posting I realized you probably already know or use Backtrack so ignore this post. :-P

---

### Post by enduser000 on 2010-02-12
The machines I'll be partially responsible will be Ubuntu (file server; possibly other things) and CentOS (IDS, probably snort; MySQL server; possibly other things).  I've run some backtrack, maybe I can use it to test my configuration when I have things up and running.

For now though I'm just trying to learn how to serve up these services to the outside world.

end

---

### Post by cariboo on 2010-02-12
File servers are usually setup to work on a local network only, I use mine for storing media files, documents, just about anything that I think I may need. It can access the internet for updates, but thats about it, there are no ports forwarded on the router, because at this time, I don't need to access it remotely.

When I do need to access the server from outside my internal network, I open up ssh on a non-standard port, and I already have key based authorization setup.

---

