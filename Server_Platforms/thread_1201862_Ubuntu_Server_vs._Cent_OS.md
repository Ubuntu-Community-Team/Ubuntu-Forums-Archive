---
title: "Ubuntu Server vs. Cent OS"
date: 2009-07-01
forum: Server Platforms
---

### Post by JKick on 2009-07-01
I know this is an Ubuntu forum, but I am looking for feed back. I am involved in a little adventure that will probably require our own server platform. We already know we are going with linux. My background is more Ubuntu based but I know a lot of servers are CentOS (in the enterprise). I would like to know why you would suggest Ubuntu for a server and what things bother you about Ubuntu as a server. 

this server will primarily be a Web Server running the usual Apache, MySQL and PHP. There is always a remote chance something else could come down the line.

thank you,

---

### Post by v3xtra on 2009-07-01
I've heard mostly that CentOS is just straight rock-solid.  They use older software, because it is proven to work the best and be more stable than the newest and greatest.  Personally it is just a preference call, as I don't think there are going to be HUGE performance differences between the two platforms if you set them up correctly.

What I will say though, is if your background is in Ubuntu / Debian, I would highly suggest at least trying CentOS, so that you can have a good background in both Ubuntu / Debian and CentOS / Red Hat, and become more familiar with both operating systems.  :)  In the long run, it may take longer to get things set up and fix things, but you will be able to have a more diverse understanding of both.  Just my two cents though.  :)

---

### Post by HermanAB on 2009-07-01
Howdy,

In general, the older distributions like Redhat (Centos), Suse and Mandriva have better wizards.  Consequently, installing a server using one of those three is extremely easy, to the point of being absolutely trivial - clickety-click-done.

So, from a business point of view I will not recommend using Ubuntu for a server, it wastes too much time.  All my servers are Mandriva or Redhat.  I don't like the Suse wizards - they are very good, but impossible to customise - you either do things the way the Suse wizards want or you are on your own. 

I use Ubuntu strictly for fun, since it doesn't have any server wizards to speak of, so it is good for experimenting, but in business, time is money.

---

### Post by rbishop on 2009-07-01
Hello all,

I have used both (Debian and Red Hat derivatives) in the Enterprise environment and would like to offer up my own two cents worth.....

I enjoyed the graphical wizard setup, just to make it easy, but the more I used the server, the more I was using the CLI.  When I setup and used Ubuntu it was all done with the CLI, and it seemed to be a little bit quicker in the long run on bootup's etc.  I got used to the CLI and was readily able to find help on the web to fix any issue or to help me walk through setting something up, so no time was wasted, as I was learning as it got done.

If you’re doing a basic LAMP setup either one will work,  go with what your comfortable with.  I have started using Ubuntu more and more, and the more I use it the more I enjoy working with it.

---

### Post by ibutho on 2009-07-01
Ubuntu will work just as well as CentOS. The advantages that CentOS has, include stability (its based on Red Hat Enterprise Linux which undergoes longer testing than typical Ubuntu releases) and being very secure out of the box (selinux is usually enabled by default). CentOS also has a lot more sysadmin tools (both GUI and CLI) when compared to Ubuntu where some things require manual configuration by editing text files.

---

### Post by juancarlospaco on 2009-07-01
Yes, Google uses Ubuntu Server, these guys are noobs...
:)

---

### Post by wojox on 2009-07-01
Ubuntu - 
Good community support.
Wide adoption.
Ease of use. 
apt-get.
Like the concept that Canonical represents.

---

### Post by scorp123 on 2009-07-02
> **HermanAB said:**
>  I use Ubuntu strictly for fun, since it doesn't have any server wizards to speak of, so it is good for experimenting, but in business, time is money. I agree to that last part. Look at this thread:

[http://ubuntuforums.org/showthread.php?t=640760](http://ubuntuforums.org/showthread.php?t=640760)

Credits where credits are due ... I think that one is a brilliant thread. BUT: With a distro such as SUSE Enterprise Linux 11 (or the free ones: OpenSUSE 11.1) I can do all the stuff described in that thread in just a few mouse clicks ... whereas with Ubuntu I have to edit a ton of files manually and watch out for typing mistakes and what not. That's where I find Ubuntu a bit lacking. It should be easier to do such things. "Linux for Human beings", right?

Ubuntu Server is OK for simple stuff (SSH, Apache, ...) but for more complex things I'd really love to have the help of some wizard which are standard in other distros (SUSE, Mandriva, lots of others ...)

---

