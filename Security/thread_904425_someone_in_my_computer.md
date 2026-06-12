---
title: "someone in my computer?"
date: 2008-08-29
forum: Security
---

### Post by kritro on 2008-08-29
I saw a strange thing today. My ubuntu server machine was running and suddenly there was unauthorized activity. A consoll was opened and commands where written and also the mousepointer was moving. 

There was also opened a seccond consoll that logged in to my asterisk server. 

I don't remembered the commands, but 'show smbpassw, and 'show kpasswd' I think was some of them. 

Are there any log files where I can track IP addresses of possible intruders and log files to see what commands have been used?

This is very strange.

Thanks kritro

---

### Post by Titan8990 on 2008-08-29
Do you have VNC or any other kind remote desktop ports open?

> Are there any log files where I can track IP addresses of possible intruders and log files to see what commands have been used?


It wouldn't matter if you could get the intruders IP. This will never actually lead back to the intruder. Most likely it will lead back to a bot computer or a proxy.

---

### Post by ByteJuggler on 2008-08-29
> **kritro said:**
> I saw a strange thing today. My ubuntu server machine was running and suddenly there was unauthorized activity. A consoll was opened and commands where written and also the mousepointer was moving. 

There was also opened a seccond consoll that logged in to my asterisk server. 

I don't remembered the commands, but 'show smbpassw, and 'show kpasswd' I think was some of them. 

Are there any log files where I can track IP addresses of possible intruders and log files to see what commands have been used?

This is very strange.

Thanks kritro

1.) Do you use VNC/have it enabled on your desktop?  If so have you set a secure password?  

2.) Do you run/have you set up to anything to run as root deliberately?

3.) What servers/custom software have you set up on your system?

Commands entered at the command prompt will be stored in the file ".bash_history" in your home folder.  (Go to Places, Home folder, then enable viewing hidden files, then try opening the file in e.g. "gedit".)

---

### Post by ukripper on 2008-08-29
> **kritro said:**
> I saw a strange thing today. My ubuntu server machine was running and suddenly there was unauthorized activity. A consoll was opened and commands where written and also the mousepointer was moving. 

There was also opened a seccond consoll that logged in to my asterisk server. 

I don't remembered the commands, but 'show smbpassw, and 'show kpasswd' I think was some of them. 

Are there any log files where I can track IP addresses of possible intruders and log files to see what commands have been used?

This is very strange.

Thanks kritro

Thats what happens when doors are open to your server. You should secure your VNC via ssh just don't connect it without over ssh and give open invitation to intruders.

And also why would you install X window based environment on  the server. Default ubuntu server only comes with command line which is more secure and can be administered using ssh or webmin.
you can check your open ports using:
**nmap localhost**

---

### Post by adept_king on 2008-08-29
PORT     STATE SERVICE
631/tcp  open  ipp
8118/tcp open  privoxy

i installed and ran nmap, and this is what i got.

i once thought i was a genius and could figure out privoxy and tor, but could not.  i cant even figure out how to get rid of privoxy or tor.

but, other than that, are these numbers normal?

---

### Post by ukripper on 2008-08-29
> **adept_king said:**
> PORT     STATE SERVICE
631/tcp  open  ipp
8118/tcp open  privoxy

i installed and ran nmap, and this is what i got.

i once thought i was a genius and could figure out privoxy and tor, but could not.  i cant even figure out how to get rid of privoxy or tor.

but, other than that, are these numbers normal?

tor is never been secure. It makes you anonymous but don't gurantee secure packets. tor and privoxy is your culprit here. And you shouldn't be having them on your production server.

631 is your normal printer port taht is fine.

---

### Post by Oldsoldier2003 on 2008-08-29
yep your server has been compromised. The best thing to do is make sure you have backups of your data and completely reinstall the OS. Take special care to secure VNC, and apply all security patches. There is really no way to guarantee the integrity of the machine since it has been breached.

As stated above running gui on your servers is an additional point of vulnerability, but right now the biggest issue is saving data and reinstalling the OS to insure future network integrity.

---

### Post by kritro on 2008-08-29
It was a VNC running without a password and I was logged in as root. Doublebad...asterisk. There was also incoming traffic on port 5900 on the log of my router.

It wasn't so important as it was only a test server for asterisk with no important data on it, but it is certainly a wakeup call. 

Thanks for solving the case

---

### Post by ukripper on 2008-08-29
> **kritro said:**
> It was a VNC running without a password and I was logged in as root. Doublebad...asterisk. There was also incoming traffic on port 5900 on the log of my router.

It wasn't so important as it was only a test server for asterisk with no important data on it, but it is certainly a wakeup call. 

Thanks for solving the case

Surely is, with tor and privoxy also running!

---

### Post by adept_king on 2008-08-29
> **ukripper said:**
> tor is never been secure. It makes you anonymous but don't gurantee secure packets. tor and privoxy is your culprit here. And you shouldn't be having them on your production server.

631 is your normal printer port taht is fine.

how stop privoxy from being on that list?

and WHAT is that list?

how am i on the net if the only two things on that list are printer port and privoxy?  im not using privoxy... am i?  i thought i uninstalled it.

EDIT:

neither synaptic was returning results for tor or privoxy.
i ran "adept manager" in sudo and was able to find both of these programs listed.
after deleting these bad files, my desktop shut-down time went from 2 minutes down to 500ms.

hopefully this move was good for security.

---

### Post by rogeriopvl on 2008-08-29
> **adept_king said:**
> how stop privoxy from being on that list?

and WHAT is that list?

how am i on the net if the only two things on that list are printer port and privoxy?  im not using privoxy... am i?  i thought i uninstalled it.

uninstalling anything in linux is my hell dujour, what's yours?

I assume you are installing software with something like:

```
sudo apt-get install name_of_the_software
```

Or by going to the add/remove software in the menu...

To remove a program is as simple as this:

```
sudo apt-get remove name_of_the_software
```

Or go to the add/remove software, search for the name of the software and then uncheck the box.

---

### Post by adept_king on 2008-08-29
whoops, i edited before reading page 2 and your post.

neither synaptic from the applications or system menu showed results when i searched for tor and privoxy.  tork showed up unchecked, but when i executed tor from a command line, it ran.  this told me tor was installed somewhere even though i couldnt find it where tor's website said it would be.  searching my file system (for hidden files and folders) yielded nothing for privoxy.  yet, privoxy was using one of my ports according to nmap.

i finally found both programs in 'adept manager.' i ran adept in sudo and unchecked both programs.  now my computer shuts down in a second instead of 2 minutes.  i wasnt even using tor or privoxy.  i thought i uninstalled them.  now they are gone, thanks to adept manager.  

pretty confusing since AM is a KDE program.  i thought i was using gnome.  its all very confusing.

---

### Post by cariboo on 2008-08-29
When uninstalling programs that run a server, shut down the server first for example the following will shut down apache2

```
sudo /etc/init.d/apache2 stop
```

then, uninstall the program. Use any of the gui interfaces for apt, or on the command line:

```
sudo apt-get purge <program_name>
```

This will insure that the program and all its configuration files are removed. If a server is running when you try to uninstall it, you will not be able to remove all it's configuration file, and it will keep running even if you assumed you uninstalled it.

Jim

---

### Post by foez on 2008-08-29
If you run tor you will be compromized. 
The all seeing eye wants to know why you need that tool.

---

