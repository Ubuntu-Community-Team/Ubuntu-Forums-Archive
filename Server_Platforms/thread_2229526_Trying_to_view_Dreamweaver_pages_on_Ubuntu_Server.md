---
title: "Trying to view Dreamweaver pages on Ubuntu Server"
date: 2014-06-13
forum: Server Platforms
---

### Post by tom109 on 2014-06-13
I hope I have posted this in the correct area.  Anyway, I have a desktop computer running Windows 7 Ultimate and I have a server running Ubuntu 14.04 with LAMP.
I have on my desktop Dreamweaver CS5 where I have developed a web page with some PHP and Ajax written into the code.  My Dreamweave says that it is connected to my server, but my web page does not show up on my screen.  Instead I get the message, "Dynamically-related files could not be resolved because your credentials don't allow file activity on the server.  My site name is, "calendar"; Local Site Folder is, "C:\Calendar"; Servers are, "name=localhost, address=ip address of the server, connection=FTP, and Testing is checked"; Under Server setup, Server Name=localhost, Connect Using=FTP, FTP Address=ip address of server, Username=username for serever, Password=password for entry into FTP, Root Directory=/../, and web URL=http://ip address of server.  When I press the test button this message pops up, "Dreamweaver connected to your Web server successfully".  In advanced options the, "Maintain synchronization information" box is checked and the Server Model=PHP MySQL.  If I am truly connected to my Web Server then why can I not view my web pages which have been developed in Dreamweaver.  I am always learning and everything I have done up to now has been learned through books and the internet.  Any help will do as I am becoming increasingly frustrated with this process.  Thank you.

Here is another thought, my Dreamweaver files are on my desktop computer do they need to be on my server also?  If so, how do I get those files onto my server?  It would be nice to use a USB drive, but from what I know about Ubuntu Server it will not be that easy.

---

### Post by Bucky Ball on 2014-06-13
*Thread moved to **Server Platforms**.*

Welcome. Try here. You might have better luck.

---

### Post by tom109 on 2014-06-13
One thing I forgot to mention was my server is being used on my home network only.  It is behind a router connected to a switch with my desktop and laptop computers.  I am unable to view my server when I try and map my network from my desktop or laptop, but that is another story.  I have no intention of running this server out on the internet because I do not want that headache.  To many security issues to deal with and right now I don't want to have to deal with them.  Already have my router set up with all kinds of security measures plus the security I have on individual computers on my network is enough for now.  The only purpose for this server is to be used as a testing server for my web pages.  I am use PHP, Ajax and other similar programming languages on my web pages and want an area where I can safely test my product.

Sorry, by the way thank you for your reply and the link to, "Building a Linux Computer".

---

### Post by bab1 on 2014-06-14
> **tom109 said:**
> I hope I have posted this in the correct area.  Anyway, I have a desktop computer running Windows 7 Ultimate and I have a server running Ubuntu 14.04 with LAMP.
I have on my desktop Dreamweaver CS5 where I have developed a web page with some PHP and Ajax written into the code.  My Dreamweave says that it is connected to my server, but my web page does not show up on my screen.  Instead I get the message, "Dynamically-related files could not be resolved because your credentials don't allow file activity on the server.  My site name is, "calendar"; Local Site Folder is, "C:\Calendar"; Servers are, "name=localhost, address=ip address of the server, connection=FTP, and Testing is checked"; Under Server setup, Server Name=localhost, Connect Using=FTP, FTP Address=ip address of server, Username=username for serever, Password=password for entry into FTP, Root Directory=/../, and web URL=http://ip address of server.  When I press the test button this message pops up, "Dreamweaver connected to your Web server successfully".  In advanced options the, "Maintain synchronization information" box is checked and the Server Model=PHP MySQL.  If I am truly connected to my Web Server then why can I not view my web pages which have been developed in Dreamweaver.  I am always learning and everything I have done up to now has been learned through books and the internet.  Any help will do as I am becoming increasingly frustrated with this process.  Thank you.

Here is another thought, my Dreamweaver files are on my desktop computer do they need to be on my server also?  If so, how do I get those files onto my server?  It would be nice to use a USB drive, but from what I know about Ubuntu Server it will not be that easy.
Starting with the last question first: The most efficient method fo transfering the files from one machine to another is via the network.  NO need for USB drives at all.  In this scenario you are connected via a file transfer protocol ( e.g. SFTP).  You transfer the files directly from your desktop to the Ubuntu LAMP server.  It would look the same as moving files from one folder to another in the desktop even though you are moving files from one machine to the other.  Dreamweaver has that functionality built in.  Unfortunately it uses FTP which is insecure and not available by default with the Ubuntu server install. 

As far as the first question goes, there are many ways you can *"connect to the server" *.  You can have connectivity with one protocol (e.g. Ethernet) and not another (e.g HTTP).  Searching Google using the terms: *dreamweaver sftp ssh* reveals a few workarounds to the limitations of Dreamweaver's connectivity.   In the end you will find it easier to setup the SSH server for SFTP use on the LAMP server and use WinSCP on the Windows desktop to transfer the files to the LAMP server and not use Dreamweaver for that type of thing.   

> One thing I forgot to mention was my server is being used on my home network only. It is behind a router connected to a switch with my desktop and laptop computers. I am unable to view my server when I try and map my network from my desktop or laptop, but that is another story. 

I assume you mean *"Windows Sharing" * here.  You can do that but you need to install and configure Samba for that.  If you are just transferring files then I'd just use SSH/SFTP and leave it at that.
> 
I have no intention of running this server out on the internet because I do not want that headache. To many security issues to deal with and right now I don't want to have to deal with them. Already have my router set up with all kinds of security measures plus the security I have on individual computers on my network is enough for now. The only purpose for this server is to be used as a testing server for my web pages. I am use PHP, Ajax and other similar programming languages on my web pages and want an area where I can safely test my product.

Security is a good thing and you should learn as much as you can.  Good security habits start with the first web server you create, regardless of whether it is private or public facing the Internet.

My own solution a long time ago was to use Dreamweaver as an editor only and set up the outside services myself.  I now use Bluefish as a webpage editor.  I'm sure there are others too.  My habit is to maintain the source files on the workstation and transfer a copy to the web server.  In that way you are syncing the files.

Are you really using Ubuntu server; no GUI?  How have you worked out the file permissions for the web root directory?

---

