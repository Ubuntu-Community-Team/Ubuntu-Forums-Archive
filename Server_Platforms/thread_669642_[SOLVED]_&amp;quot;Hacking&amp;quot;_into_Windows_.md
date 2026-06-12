---
title: "[SOLVED] &amp;quot;Hacking&amp;quot; into Windows Server 2003"
date: 2008-01-16
forum: Server Platforms
---

### Post by nfox on 2008-01-16
Hi,

I'm using Feisty at work and our server is Windows Server 2003. Since it's headless, I'm remote-desktoping my way around.

I would like to be able to "hack" into it from preferably the terminal. How can I get to the command prompt on the server? I would like to be able to, for instance, restart the Java server, run the backup utility, etc. and console access would be swell.

I know there are people hacking boxes (I assume Windows easier than other) and I'm not looking (although I'd love it) to find out how to break into someone's computer-- I simply want to gain access to the server. 

I would have expected a widely-used app just for it where users can log into the remote computer as they would with remote desktop. 

Any ideas?

---

### Post by veloce on 2008-01-16
I just rdp to the server and run "Command Prompt".

---

### Post by AaronMiller on 2008-01-16
You can setup SSH for windows I know.

Have no clue on HOW though

---

### Post by koenn on 2008-01-16
WIndows is a GUI-oriented system, and thus the common way to de remote administration is a remote desktop or terminal services in administration mode (which is the same as rempte desktop, really).

Windows Server has also a telnet service, if you start it you can telnet to the server and you get the windows command prompt (cmd) - with all its limitations.

You can also install adminpak and/or windows support tools (I always forget which is which) which give you clients (eg on your PC) that you can use to admin certain services on the server. Some tools in Control Pannl can also be used against remote systems.

---

### Post by nfox on 2008-01-17
Yesterday reminded me of why I'd like a better solution than remote desktop. I accidentally opened a 1.9gb text file which halted the web server and shut my remote connection off for about 5 minutes. 

I couldn't plug in a keyboard because the USB driver needs to load with the device attached at startup and the mouse can't exactly CTRL+ALT+DEL my way to the desktop. 

Remote desktop failed me then and disappoints me now.


SSH is neat but not very useful. I want to be able to get 'all up in it' pref. from the command line and I know there are people able to do it. I'd assume they are using that knowledge for questionable purposes so it's kind of difficult to find the info. 

It's 2008 and there should be ways to do this.

---

### Post by morgan_greywolf on 2008-01-17
You can do a whole lot from the command line via SSH.  You might want to look into the [SysInternals ](http://technet.microsoft.com/en-us/sysinternals/default.aspx)utilities.  They can be used to do many, many things such as killing and restarting services and processes.  You can't do exactly everything, but between the Sysinternals stuff and scripting tools like [PowerShell](http://www.microsoft.com/windowsserver2003/technologies/management/powershell/default.mspx), you can do just about anything.

You can install ssh by installing [Cygwin](http://www.cygwin.com/)

---

### Post by nfox on 2008-01-17
SSH without flaky port of Cygwin (no offense):

[http://www.networkcomputing.com/1206/1206sp3.html](http://www.networkcomputing.com/1206/1206sp3.html)

---

