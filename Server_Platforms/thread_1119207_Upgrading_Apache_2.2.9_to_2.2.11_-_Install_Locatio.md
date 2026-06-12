---
title: "Upgrading Apache 2.2.9 to 2.2.11 - Install Location"
date: 2009-04-07
forum: Server Platforms
---

### Post by hamz01 on 2009-04-07
I installed Ubuntu Server 8.10. Apache was installed by default. I have Apache up and running exactly as I want it, no issues. I am on 2.2.9 and trying to upgrade to 2.2.11. apt-get does not show me 2.2.11, so I downloaded the source from Apache's website to manually install.

I manually installed 2.2.11 successfully, but it installed to /usr/local/apache2 and left my 2.2.9 installation alone. The 2.2.11 version wants files to be in different places than my 2.2.9 version does. 2.2.11 doesn't look for anything in /etc/apache2 or /var/www which I thought were default locations.

I'm assuming I can go in and manually change lots of stuff in the configuration, but can I install it to have the same layout/file location as is the default with Ubuntu Server 8.10?

Thanks for any help,
Brandon

---

### Post by dguitar on 2009-04-07
> **hamz01 said:**
> I have Apache up and running exactly as I want it, no issues. I am on 2.2.9 and trying to upgrade to 2.2.11.

Why are you moving to 2.2.11 then? 

How did you install Apache? Did you compile it from source or some sort of package?

You could compile from source and pass the paths you want or if you want to be lazy you could setup symbolic links ('man ln').

If there isn't a feature that you **can't live without** in 2.2.11, I highly suggest sticking with the default version that Ubuntu ships with.

---

### Post by hamz01 on 2009-04-07
I am not upgrading to 2.2.11 for any specific reason, it's more that I want to know how to do so in case I need to in the future.

I installed 2.2.11 by compiling from source. I know I can change paths, but it seems like I'd have to go in and change a whole lot, and I still wouldn't know how to get the layout right. It doesn't seem like this is a practical way to update Apache.

I'm new to Ubuntu Server. Is it customary to wait until new versions of something like Apache are added to the repositories?

Thanks for the response.

---

### Post by dguitar on 2009-04-07
> **hamz01 said:**
> Is it customary to wait until new versions of something like Apache are added to the repositories?

Yes, this is true of all non-source based distros (IE: Ubuntu, Debian, Fedora, etcetc). The reason you wait, is because the packages in the repos have been built and tested to work with your distro/kernel and the other software in the repos. You never want to use the 'latest and greatest' or 'bleeding edge', at least in the server world, unless you absolutely have to. Stability is #1.

---

### Post by hamz01 on 2009-04-07
> **dguitar said:**
> Yes, this is true of all non-source based distros (IE: Ubuntu, Debian, Fedora, etcetc). The reason you wait, is because the packages in the repos have been built and tested to work with your distro/kernel and the other software in the repos. You never want to use the 'latest and greatest' or 'bleeding edge', at least in the server world, unless you absolutely have to. Stability is #1.

Good to know, and I agree completely.

So basically, if 2.2.11 was deemed necessary and appropriate for the vast Ubuntu Server base, the big-dogs would build a semi-custom configuration of Apache and then put it in the repository? My next question would be, isn't it difficult for whoever manages the repositories to build custom configs of all the packages? I used Webmin to upgrade to the latest version of Webmin because it wasn't showing up in apt-get upgrade. Should I have also waited for that to show up in the repositories?

---

### Post by dguitar on 2009-04-07
> **hamz01 said:**
> So basically, if 2.2.11 was deemed necessary and appropriate for the vast Ubuntu Server base, the big-dogs would build a semi-custom configuration of Apache and then put it in the repository?

Not exactly. I could be wrong, but I believe Ubuntu ships with a version, and will only update that package for security reasons. So to get a newer version of Software, you need to use a newer version of the OS.

> **hamz01 said:**
> My next question would be, isn't it difficult for whoever manages the repositories to build custom configs of all the packages?

Yes it is. Thats why it takes a lot of dedicated people who rarely get a lot of credit.

> **hamz01 said:**
> I used Webmin to upgrade to the latest version of Webmin because it wasn't showing up in apt-get upgrade. Should I have also waited for that to show up in the repositories?

I don't use Webmin, however I *think* this is what you want to do. The repo can't keep up with Webmin and Webmin can be so dangerous, it's best to have the latest (stable) version for security updates. Someone that knows more about Webmin, may be able to provide more/better info.

---

### Post by Thirtysixway on 2009-07-24
I upgrade webmin by using the built-in upgrade tool.  I didn't even think about it being updated in the repos...

---

