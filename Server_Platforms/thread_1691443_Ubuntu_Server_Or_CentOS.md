---
title: "Ubuntu Server Or CentOS"
date: 2011-02-19
forum: Server Platforms
---

### Post by SecretLegend on 2011-02-19
Hey guys I am soon to deploy a new server for quite a bit of things such as web serving, Game Servers, and File Hosting. I have one main question is whether to go with Ubuntu Server 10.10 or CentOS 5.5 in terms of reliability, uptime, expandability, and the most professional one to use. It would be great to read some of your opinions. Also if you would like you can also post what you think is the best overall server operating system....   Thank you in advance :D

---

### Post by hawkmage on 2011-02-19
If this server is going to be running existing software that is readily available on either platform then it really comes down to which one you are more familiar with.

The only reason I would lean towards CentOS is if you are going to try running vendor software, many software companies officially support RedHat Enterprise Linux which CentOS is built from the RHE public source packages.

As for the overall beast server OS it really depends on what you are trying to do.

---

### Post by HermanAB on 2011-02-19
Howdy,

Linux is Linux is Linux...

Or in other words, it is the same difference...

Pick your poison.  

However, the older distros have better wizards and since in a business environment time=money, most business users use RedHat or Suse distros.

---

### Post by Sir Jake on 2011-02-20
As most people have said pick what you're used to.
I'm switching my Centos box back to Ubuntu just because it's what I started with and found support here is the best yet.

I used mine for game servers and webserver, switching my web server onto another box as I found everything for the game servers run much better without all the other crap on the box.

Best of luck.

---

### Post by SeijiSensei on 2011-02-20
Linux may be Linux when you're talking about the kernel, but there are some important differences between Debian derivatives like Ubuntu and RHEL derivatives like CentOS.

The first has to do with repositories and how software is installed.  Ubuntu uses apt with the .deb container; CentOS uses yum with the .rpm container.  You may have to relearn a few commands if you use apt-get or yum from the command line.  CentOS also has fewer packages in the official repositories than Ubuntu, but the well-maintained, third-party [rpmforge]("http://rpmrepo.org/RPMforge") repository has pretty much everything else you'd need.

Next, there are differences in how programs are named (Apache is httpd in CentOS; apache2 in Ubuntu) and where configuration files are located.  The Apache configuration in CentOS is very different from the one in Ubuntu, for instance.  By default, CentOS uses sendmail; Ubuntu runs Postfix.

That said, I use CentOS 5.5 on all the servers I run unless a client specifies something else like Debian.  I have over a decade's worth of experience with the RHEL platform and didn't see any advantages to switching to Debian or Ubuntu.  Switching from sendmail to Postfix, for instance, would take a bit of doing.  I also use some software like [MailScanner]("http://www.mailscanner.info/") which is packaged by the author to work with RHEL platforms.  (It's also in the Ubuntu repositories, of course, but I'm more comfortable with its packaging for CentOS.) If you have specific software packages in mind, see how portable they are across platforms.

Finally, if you have exotic hardware, it's more likely that proprietary drivers exist for RedHat than for Ubuntu.  Take a look at pre-configured Dell servers for instance.  You'll see that Dell maintains it's own repository of proprietary drivers that work with some of the server hardware they sell.

---

