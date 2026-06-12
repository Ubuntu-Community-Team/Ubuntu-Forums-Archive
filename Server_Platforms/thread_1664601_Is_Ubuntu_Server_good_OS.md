---
title: "Is Ubuntu Server good OS  ?"
date: 2011-01-11
forum: Server Platforms
---

### Post by West201 on 2011-01-11
I've been using Ubuntu Desktop for several months now, and I've been very happy with it. However I just purchased an HP server that came with Windows 2008. I want to use the server to host my website.

Is Ubuntu Server a good choice for someone thats never setup a server ? Is Ubuntu Server a good choice compared to other linux Distros ? What are some of the benefits and cons of using a Linux Server vs Windows ?  Any advice is really appreciated :)

---

### Post by Grenage on 2011-01-11
Normally, the software that you want to run on it.

We use Linux servers, but it's not always an option; both have distinct merits.

---

### Post by sj1410 on 2011-01-11
Yes Ubuntu Server is a good choice but depends on for what application you would like to use it.

---

### Post by James78 on 2011-01-11
You're probably also asking is it good in terms of security, speed, easyness... All of the above. :) I've been using it for 6 months now, and haven't had a single problem that had anything to do with Ubuntu Server itself being bad. :D It's a fine choice, and since you know fairly well how Ubuntu/Debian/Linux works, it's a good transition to Ubuntu Server vs Red Hat for example, even if it's command line only. You shan't regret it.

Benefits and cons against Windows, well.. I can't even think of 1 benefit for Windows honestly, we all know that Linux is much better for running servers on hands down.

---

### Post by HermanAB on 2011-01-11
There are bazillions of websites running on Linux, more than any other OS.  So yes, Linux is good for what you want to do.

However, if you want a GUI to make your life easier, use ordinary Ubuntu and if you want wizards for everything as in Windows, use OpenSuse.

---

### Post by cabaro on 2011-01-11
I am sysadmining about 20 ubuntu servers virtualized atop xen. 
Easy administration, i can tell you.

Most running tomcat6, postgres, apache2 websites.

Security updates are very on-to-date.
Easy movability, scriptability, flexibility, and so on.


So, in my opinion, yes.

---

### Post by snowpine on 2011-01-11
Yes, highly recommended. 

I recommend giving the [Ubuntu Server Guide ]("https://help.ubuntu.com/10.04/serverguide/C/index.html")a thorough read-through.

---

### Post by Thirtysixway on 2011-01-11
Ubuntu makes a great server operating system.  It's stable and supported for 5 years with the LTS version.  I'm currently a part of a team that's moving a major michigan school district over to Ubuntu server on amazon ec2 for all of their public facing websites for buildings, schools, and services.

---

### Post by lykwydchykyn on 2011-01-11
> **jessejj89 said:**
> I've been using Ubuntu Desktop for several months now, and I've been very happy with it. However I just purchased an HP server that came with Windows 2008. I want to use the server to host my website.

Hosting a website is usually pretty light work for any server, but I'd put Apache on Linux up against IIS on Windows server any day for speed, security, and flexibility.  

> 
Is Ubuntu Server a good choice for someone thats never setup a server ? Is Ubuntu Server a good choice compared to other linux Distros ? What are some of the benefits and cons of using a Linux Server vs Windows ?  Any advice is really appreciated :)

Ubuntu server is a good choice.  It's not the only good choice, and depending on what you want it may not be the best choice.  

It's biggest distinctions from other major server distros are (1) lack of GUI server management tools and (2) more cutting-edge (or, on the other hand, less tried-and-proven) software at release time.  

I personally prefer Debian stable in most server applications, but if you want a server with a nice GUI try clearOS, Zentyal, or Suse.

---

### Post by kevinthecomputerguy on 2011-01-11
I also prefer Debian stable.
*I dont have anything bad to say about Ubuntu Server. They are quick too make changes, but i think that is their mission, and hey, somebodys got to do it...  :- )

---

### Post by Thirtysixway on 2011-01-11
Debian stable is good for nice solid production servers, but it has older versions of software.  While they're tested against bugs and security holes, it's a bit annoying at times to have such old software in the repos.

---

### Post by Neo@Matrix on 2011-01-11
> **lykwydchykyn said:**
> [QUOTE] lack of GUI server management tools and
? By my humble opinion this can be fixed by:
```
$ sudo apt-get install ubuntu-desktop
```
Might be wrong , but worked for me :)

---

### Post by Vegan on 2011-01-11
I have been using the Ubuntu distribution successfully for a couple of years now.

The forum members helped me get all the issues clarified so I was able to learn how to use it to advantage.

It takes time to learn but its useful. Linux can act as a a production server readily.

---

### Post by Thirtysixway on 2011-01-11
> **Neo@Matrix said:**
> [QUOTE=lykwydchykyn;10345572]
? By my humble opinion this can be fixed by:
```
$ sudo apt-get install ubuntu-desktop
```
Might be wrong , but worked for me :)

I'd rather use webmin.  It's more focused on admin of the server without using all the resources that running a GUI desktop does.

---

### Post by lykwydchykyn on 2011-01-11
> **Neo@Matrix said:**
> [QUOTE=lykwydchykyn;10345572]
? By my humble opinion this can be fixed by:
```
$ sudo apt-get install ubuntu-desktop
```
Might be wrong , but worked for me :)

Having a desktop is not the same as having GUI management tools for a server.  Go take a look at the web interface in Zentyal or ClearOS, or YAST in Suse and you'll see what I mean.  

You can install GNOME (big waste of resources, IMO), but the only difference for server administration on Ubuntu server is that you get to use an Xterm and GEdit instead of a VT and nano.  :)

---

### Post by James78 on 2011-01-12
> **lykwydchykyn said:**
> 
Having a desktop is not the same as having GUI management tools for a server.  Go take a look at the web interface in Zentyal or ClearOS, or YAST in Suse and you'll see what I mean.  

You can install GNOME (big waste of resources, IMO), but the only difference for server administration on Ubuntu server is that you get to use an Xterm and GEdit instead of a VT and nano.  :)
In complete agreement here. Desktop GUI's would offer an easier way to do things like editing files (Gedit vs nano). But a), BIG waste of server resources, b) uneeded software bloat, and c) those tools don't offer things like BIND DNS management, creating Apache VHosts, etc. Webmin and Virtualmin are great tools to use and I highly recommend them. I also highly recommend learning to administer a Linux server completely from the command line and possibly a tool like Webmin too if you need a little bit more of a kick in features (use both and you're good to go). :)

---

### Post by West201 on 2011-01-12
Thanks You for all positive feedback :) . I found this nice webpage with great details about Linux Server Distros.

Check this link out:
[http://www.serverwatch.com/columns/article.php/3900711/The-Top-10-Linux-Server-Distributions.htm]("http://www.serverwatch.com/columns/article.php/3900711/The-Top-10-Linux-Server-Distributions.htm")

---

### Post by chrislynch8 on 2011-01-12
Ubuntu is perfect for almost anything you want to do. For hosting a website linux is used more then any other OS, I have 30 Ubuntu servers running here throughout various offices etc, they have been rock solid for almost three years now.

The server you got has windows server2008, although ubuntu is great, you've abviously already paid for the windows server so why wash your money.

---

### Post by NightwishFan on 2011-01-12
Ubuntu Server is awesome! The Server team are very hardworking and professional as well. Ubuntu server is also reliable and supported for 5 years for LTS. Also Ubuntu server is used by Wikipedia.
[http://www.canonical.com/about-canonical/resources/case-studies](http://www.canonical.com/about-canonical/resources/case-studies)

I would use Lucid. As was said there is nothing against using a GUI on a server except potential complication and slightly more resource use. Personally I would use a gui on mine as I use a server type system for more than what I am comfortable doing on a cli, but if it was just for something background like apache, using a cli is not difficult and would yield many benefits in performance and security.

Also Ubuntu Server is no different from the desktop except package selection and the default kernel. It is safe to mix and match, and packages can always be removed, though to be honest I would watch running a bunch of daemons that come with the desktop like cups for printing and bluetooth. Those can be easily disabled with Boot Up Manager though.

Also good choices are Suse Linux and CentOS, as well as Debian.

---

### Post by kaldor on 2011-01-12
> **NightwishFan said:**
> Ubuntu Server is awesome! The Server team are very hardworking and professional as well. Ubuntu server is also reliable and supported for 5 years for LTS. Also Ubuntu server is used by Wikipedia.
[http://www.canonical.com/about-canonical/resources/case-studies](http://www.canonical.com/about-canonical/resources/case-studies)

I would use Lucid. As was said there is nothing against using a GUI on a server except potential complication and slightly more resource use. Personally I would use a gui on mine as I use a server type system for more than what I am comfortable doing on a cli, but if it was just for something background like apache, using a cli is not difficult and would yield many benefits in performance and security.

Also Ubuntu Server is no different from the desktop except package selection and the default kernel. It is safe to mix and match, and packages can always be removed, though to be honest I would watch running a bunch of daemons that come with the desktop like cups for printing and bluetooth. Those can be easily disabled with Boot Up Manager though.

Also good choices are Suse Linux and CentOS, as well as Debian.

You summed up my opinion exactly, Mr. Lee.

---

