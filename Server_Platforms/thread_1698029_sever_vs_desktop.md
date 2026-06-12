---
title: "sever vs desktop"
date: 2011-03-01
forum: Server Platforms
---

### Post by macstl on 2011-03-01
What are the advantages of running server version as opposed to running server app eg. dhcp or samba on a desktop version?

---

### Post by dipeshmehta on 2011-03-01
You could search forums to get your question answered yourself, there had been discussion in the matter so many times.

Anyways, unlike windows, there should be nothing preventing you from either adding the server tools to a desktop installation or desktop applications to the server installation.

The thing is, if you install Desktop and afterward the server applications you might have a bit more work to get the server apps configured properly.  GUI make things easy. They are good for that reason. They do add some weight. Nothing comes free. On other hand, a server install is a bare command line, and no service running. Then add what you need.  Once you are familiar with CLI you won't go anymore with GUI.

Technically, there is difference within the kernel itself.  Kernel shipped with server version is especially meant for server specific task with heavy load environments.

It depends on you what are your primary goals.  I won't mix server and desktop environment.

Dipesh

---

### Post by perspectoff on 2011-03-01
Doesn't make any difference anymore. 

You can run most servers on a desktop version, and can add a desktop to a server version. There are some differences in timing of the OS, with the server version being more efficient. For virtual machines, headless servers, clusters, well-tuned servers, and straight CLI servers, of course the server version is better.

But if you are asking this question you aren't a straight CLI server user anyway, so for you I would say do either. You probably will need to mix GUI and CLI.

---

### Post by gamebusterzade on 2011-03-01
the boot file inittab is where you will find the difference between a desktop and a server 

if you are starting a Linux server then start with CentOS for the OS because Red Hat is the standard for servers 

but if you are starting a with a desktop then start with Ubuntu because that is what is normally used as the desktop

FYI inittab is in the /etc/ dirctory

---

### Post by churlishbeaver on 2011-03-12
(sorry about mis-spelling 'inittab' as 'inittib' in the subject heading.  I am unable to correct it.)

I am unable to find /etc/inittab on my Ubuntu 10.10 desktop system.

Can someone tell me if there is any reason why it should not be there or if it should be there why my Ubuntu desktop system works?

---

### Post by perspectoff on 2011-03-12
> **gamebusterzade said:**
> the boot file inittab is where you will find the difference between a desktop and a server 

if you are starting a Linux server then start with CentOS for the OS because Red Hat is the standard for servers 

but if you are starting a with a desktop then start with Ubuntu because that is what is normally used as the desktop

FYI inittab is in the /etc/ dirctory

This is nonsense advice. Switching back and forth between the Debian/Ubuntu/Kubuntu world and the RedHat/CentOS/Fedora world is not that easy except for advanced users (and semi-professionals). While many server farms run on CentOS, it is not very good advice on an Ubuntu forum to advise another OS.

I would not at all recommend CentOS as a server and Ubuntu as a desktop. Choose one ecosystem (RedHat/Fedora/CentOS) or the other (Debian/Ubuntu/Kubuntu) and stick with it. It's better to learn one Linux ecosystem than risk being confused learning 2 or 3.

Debian/Ubuntu servers are very fast and quite capable, and, further, have a good vertical integration with the desktop. They have cloud expandability, and worldwide Ubuntu is the most installed OS.  

Many of the parts of Ubuntu that don't work so well, IMO, are those they tried to adapt from the RedHat systems. Sometimes you can't fit a square peg in a round hole.

On another thread a Fedora user came to the Ubuntu forums for advice. Ask yourself why.

---

### Post by gamebusterzade on 2011-03-13
> **gamebusterzade said:**
> if you are starting a Linux server then start with CentOS for the OS because Red Hat is the standard for servers 


this is a valid statement i got this from **Joe Cicero**, my NWTC instructor

if you are not sure who he is see attached sight: [http://www.defcon.org/html/defcon-16/dc-16-speakers.html](http://www.defcon.org/html/defcon-16/dc-16-speakers.html)

---

### Post by HermanAB on 2011-03-13
Yup, Ubuntu is really a very small player in the server world.  Redhat is the 800 lb server gorilla and there are various reasons for that.

In general, Linux is Linux is Linux, so the better you know Linux, the less it matters which distribution you use.  However, for a new server user, starting with Ubuntu is probably not very wise.

---

