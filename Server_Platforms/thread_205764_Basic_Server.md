---
title: "Basic Server"
date: 2006-06-28
forum: Server Platforms
---

### Post by tgunner on 2006-06-28
Hi all, I am new to this whole server thing. I want to have a server with a GUI which will allow me to just take a plain html file, and host it under a domain name with godaddy.com. FTP would be nice, as would being able to do like... a remote desktop thing. I have already installed apache2 on 6.06, but don't know what to do now. This is just a basic server for my own website, no biggie, just straight html. I would like to be able to do everything right on this computer with a GUI (gnome), I don't want to get into deep command-line stuff, let alone remote command line with the standard server edition. All help appreciated.

---

### Post by amohanty on 2006-06-29
Wow. Thats a lot to do, especially if you are still beginning. First off, please keep in mind that there are quite a few security issues with hosting your own server. Explaining or even mentioning them in brief would take way more time and space than I can do here. So my suggestion would be to 
- host it with a hosting provider
- use the linux boxen to learn a bit more about the OS and the whole server thing
- once you are comfortable with your level and knowledge and security issues _then_ host it on your own machine

Having said that, if you still want to do it heres what you would need:

1. A hardware firewall (if within budget), at the very least one of those router firewall thingies
2. Somewhat high bandwidth broadband connection. Pay attention to the second number in the dsl/cable plan (eg 384/128 - 128). The second number is the upload speed and is what is relevant for the server (outgoing data)
3. A static ip (with stuff like dyndns.org you dont really need it - but I would suggest starting out with static ip if you can to simplify things) - this is expensive
4. Web server - apache2 is fine - just read up on the docs. Unfortunately I dont know of any good gui tools to configure apache (doesnt mean that there arent any - just that I dont know of any), so you might have to wade through tthe conf file, however the defaults work just fine. At the very least open the conf file to figure out where to put your html files.
5. To set it up to start at boot, fire up System->Administration->Boot up manager and select apache2 and mark the checkbox before it if it isnt already checked.

You are all set to go as far as the web server is concerned.

I would _strongly_ suggest _not_ setting up an ftp server unless you know how to setup a secure ftp server (google for sftp).

Also I would _strongly_ suggest _not_ setting up remote login capability. Just in case you want to play around with it (I would advise against this on a system connected directly to the internet - internal lan behind a router-firewall thingy should be ok), in System->Administration->Login Screen Setup in the Security tab check 'Enable XDMCP' and then setup advanced settings on the 'XDMCP' tab. To login then you would either need another linux boxen or cygwin with X on windows.

HTH
AM

---

### Post by tgunner on 2006-06-29
Alright, thanks, this really helps. I won't go for remote log-in, or ftp yet, as you reccomended. I have a dedicated monowall firewall, connected to cable internet (4 Mbps down, 768 Kbps up). The server will be the only machine in the DMZ. I am using the plain 6.06 desktop version to do this. I grew up in the world of GUI's, and don't think that I have the skills to manage this whole thing from the command line. So it sounds fairly easy now, I was ready to pull my hair out last night after reading some tutorials. But you have made it seem so easy. So I will read up on apache2 and give this a go. Now, my domain hoster is godaddy.com, how do I go about pointing my domain to apache2? Can I host more than 1 site in apache2?

---

### Post by DirtDart on 2006-06-29
I think amohanty hit the nail on the head, as far as software/hardware recommendations.

Only thing I would add would be, for a server, it is better to have a dedicated machine just for a server.  Wonderful thing about linux is that it will run on many machines that people get rid of because it won't run Windoze the way they want it to.  

You can use your desktop for your personal needs (surfing, email, etc), and let the server do what it should: serve (in your case, web files).

---

### Post by tgunner on 2006-06-29
True, but this machine is my dedicated server, I just want the GUI to make it easier to work with. For what I'm doing, just using apache, would it be better to get the standard desktop, and install apache, or get the server version, and install the desktop?

---

### Post by DirtDart on 2006-06-29
[QUOTE=tgunner]Can I host more than 1 site in apache2?[/QUOTE]

Yes, you would need to add the site(s) in the virtual host section of your apache config file.

[QUOTE=tgunner]how do I go about pointing my domain to apache2[/QUOTE]

What you need is a DNS (domain name server) entry that points your domain to your current IP address.  I'm assuming that you're on a residential cable connection, so your IP address can change from time to time (the time depends on your ISP).  When your IP address changes, you need the DNS entry to change also.  

What you need is a dynamic name service, such as no-ip.com.  When your IP address changes, they get notified, and change the DNS entry for your site automatically.  I've been using no-ip for a few years now with no compalints.


Also, to remotely configure your server, without having to go cold turkey (command line only), check out webmin.  Nice little web interface to configure your server.

---

### Post by houstonbofh on 2006-06-30
I am active on the m0n0wall lists, so I know what you have in place.  If your IP address is dynamic, use the DnyDNS support built into m0n0wall, as it will be much easier for you.  If you are going from scratch, I would install a LAMP server, and lay the desktop over the top with *apt-get install ubuntu-desktop*  the LAMP server will install and configure Apache, MySQL and PHP/Perl to work out of the box.  You don't need it now, but may want it soon!  Enable FTP and remote access (SSH comes to mind) but block in in m0n0wall.  You can always VPN in, and the hackers can't.  It will also make it easier to manage from your desktop at home.

---

