---
title: "Basic Server Help"
date: 2007-09-18
forum: Server Platforms
---

### Post by matt79 on 2007-09-18
Hi I am new to the forum and new to anything other than windows XP pro.



what I am trying to do is start a public server, just for me. so I can get my stuff from anywhere in the world. Although I never been anywhere I just want to be able to do it from other houses :-)

I have a PC that runs a CPU 800Mhz and 512 ram. 
I put ubuntu-6.06 on it but that is as far as I got.
I am having trouble with entering the commands I get stuff like -h or somthing when I type help.

when I type "sudo shutdown" it comes up with a menu of stuff and I can not get the stuff in the menu to work (or I do not know how)

if anyone could help I could really use it.

---

### Post by mattskr on 2007-09-18
give us some more information...are you trying to just access your files from anywhere? If so....SSH is the best way to go.

You can use Windows clients like putty.exe or winscp.exe to access your files

See below:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#SSH_Server")

---

### Post by mattskr on 2007-09-18
Oops...You're running Dapper...

[http://ubuntuguide.org/wiki/Ubuntu_dapper#SSH_Server]("http://ubuntuguide.org/wiki/Ubuntu_dapper#SSH_Server")

---

### Post by HermanAB on 2007-09-19
Hmm, if it is a personal server and your first stab at it, then it would be best to do a regular desktop install so you can use the GUI and wizards.

If you come from the Windows world and are addicted to wizards, then you should drop Ubuntu and switch to Mandriva.  It has wizards for everything, many more than you will ever use.  It is the only Linux distro where you really can run a server without ever using the command line if you are so inclined.

There is a kind of Linux for everyone and Ubuntu makes a nice desktop, but the server wizards are still very rudimentary, so you need to know your way around the command line.

Cheers,

H.

---

### Post by matt79 on 2007-09-19
I would like to start using linux. Thanks for the tip

---

### Post by matt79 on 2007-09-23
another Q :-)

is it possible to put openoffice on a ubuntu 6.06 server?
I have openoffice on one of my computers that has xp pro but I would like to be able to put it on my server so if someone does not have openoffice they can still read the stuff on my server. Or could I put a data base on my server?

---

### Post by matt79 on 2007-09-23
sorry guys the internet froze then posted me three times

---

### Post by matt79 on 2007-09-23
.

---

### Post by netlogic on 2007-09-24
> **HermanAB said:**
> Hmm, if it is a personal server and your first stab at it, then it would be best to do a regular desktop install so you can use the GUI and wizards.

If you come from the Windows world and are addicted to wizards, then you should drop Ubuntu and switch to Mandriva. 

.

I agree. PcLinuxOS (based on Madriva) is a lot better for Windows users entering into Linux. I think PcLinuxOS is a lot easier than the easiest Debian distros such as Xandros and Freespire. I played with it for few days in VM. I'm not  a fan of rich GUI, but the wizards are like MS. The setup is a snap. I think Ubuntu is an easy to use Linux distro with many options. You can rip many things out and run it like the real Debian.

---

### Post by matt79 on 2007-09-24
Mandriva takes $$$ to get. right?

---

### Post by netlogic on 2007-09-24
Get PcLinuxOS 2007. It is based around Madriva.

---

### Post by KCPokes on 2007-09-24
This doesn't sound like you really want a server as much as you want a desktop that can be accessed externally.  If that were the case then I'd recommend using VNC over SSH, [https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH),  and restricting access to this machine to only port 22 (SSH).  

Normally one builds a "server" with a specific purpose in mind, thus limiting the number of applications and services to limit the number of exploits.  I'd recommend starting basic and as you gain more experience you may eventually move toward a server solution.

---

### Post by speedy67 on 2007-09-24
> **matt79 said:**
> another Q :-)

is it possible to put openoffice on a ubuntu 6.06 server?
I have openoffice on one of my computers that has xp pro but I would like to be able to put it on my server so if someone does not have openoffice they can still read the stuff on my server. Or could I put a data base on my server?

You can put anything you want on 6.06 server. If you have trouble working with just the command line try installing the graphical desktop Gnome. ( sudo apt-get install ubuntu-desktop ). It comes with open-office installed and ready-to-use.

Greetings,
Sander

---

### Post by Brazen on 2007-09-24
> **matt79 said:**
> Hi I am new to the forum and new to anything other than windows XP pro.



what I am trying to do is start a public server, just for me. so I can get my stuff from anywhere in the world. Although I never been anywhere I just want to be able to do it from other houses :-)

I have a PC that runs a CPU 800Mhz and 512 ram. 
I put ubuntu-6.06 on it but that is as far as I got.
I am having trouble with entering the commands I get stuff like -h or somthing when I type help.

when I type "sudo shutdown" it comes up with a menu of stuff and I can not get the stuff in the menu to work (or I do not know how)

if anyone could help I could really use it.

Are you using Ubuntu *desktop* or Ubuntu *server*?  In other words, are you using a gui, or command line only?  Could you show me the exact commands you are typing in and what the output is?

---

### Post by matt79 on 2007-09-24
I have learned how to shutdown my server :-)

shutdown now -h 

I think I want a server.
what I would like to do is have a server and connect to it through  the IP address until I learn how to fully use the server. Then I want to get a web address so I can host my own web pages and people can acess them like a normal web page.

If someone could tell me how to install open office on my server I could really use it. I have tried apt-get install openoffice but nothing happens. I am not really sure where it would get it to install either.

P.S. I am using Ubuntu server 6.06 (the one you type everything into like a command)

---

### Post by netlogic on 2007-09-24
I don't think you are ready for it. Just install it locally.
If you really desire, install Cygwin with Xserver on Windows box. Turn ssh forwarding on the server. Throw back the application to the local Xserver on your Window box using SSH.

---

### Post by lisati on 2007-09-24
> **matt79 said:**
> another Q :-)

is it possible to put openoffice on a ubuntu 6.06 server?
I have openoffice on one of my computers that has xp pro but I would like to be able to put it on my server so if someone does not have openoffice they can still read the stuff on my server. Or could I put a data base on my server?
You might have to check with Open Office's website for its terms and conditions @ [www.openoffice.org](www.openoffice.org)

---

### Post by oly on 2007-09-25
well if you go down the ssh root, and have x installed on the server when connecting to the server use ssh -Y user@ipaddress and you can launch applications and they will send the display to the machine you are using.

if using windows you need xming and putty or use cygwin.

also check out freenx for a complete fast remote desktop session.

---

### Post by Brazen on 2007-09-25
> **matt79 said:**
> I have learned how to shutdown my server :-)

shutdown now -h 

I think I want a server.
what I would like to do is have a server and connect to it through  the IP address until I learn how to fully use the server. Then I want to get a web address so I can host my own web pages and people can acess them like a normal web page.

If someone could tell me how to install open office on my server I could really use it. I have tried apt-get install openoffice but nothing happens. I am not really sure where it would get it to install either.

P.S. I am using Ubuntu server 6.06 (the one you type everything into like a command)

The correct command for installing OpenOffice would be "sudo apt-get install openoffice.org".  If you don't know the exact name of a package, you can do a search with "apt-cache search *searchstring*".  For instance, I didn't know the name of the OpenOffice package, so I did "apt-cache search openoffice".

I don't think installing OpenOffice on your server is going to have the desired effect though.  This will NOT let people access a webpage and view openoffice files.  This will let you log on locally to your server and use OpenOffice which will not be very usefull.  It will also pull in a lot of dependancies taking up space on your server.

If you want to get a webserver installed, you just do "sudo apt-get install apache2" and that's it.  Put some files under /var/www/ and voila, they are accessible from your web browser!  If you want php support and a mysql database server, then do "sudo apt-get install php5-mysqli php5-gd mysql-server" and it's ready to go.  I'm pretty sure the services are even already started during the installation routine.

For more information you should start here: [https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html](https://help.ubuntu.com/6.06/ubuntu/serverguide/C/httpd.html)

---

### Post by KCPokes on 2007-09-25
If you want people to view documents you created under OpenOffice then start printing as a PDF rather then putting the actual document out there.  PDF is a very basic format and pretty much anyone is going to be able to view it.  

As was stated, you can't install OpenOffice on your server and make it available via the web.

---

### Post by matt79 on 2007-09-25
Could someone please explain more of what Brazen is saying. I think he is onto the type of server I am looking for. What I need is to have a interactive form online so people can fill the form out and sent it to me. I can create a form in openoffice but most people have microsoft office. I thought if I could somehow put openoffice on my server it would take care of the problem. I guess not.

thanks

---

### Post by KCPokes on 2007-09-25
He is explaining a basic web server, thus the use of Apache.  The extent of its use is determined by the handlers you have on the server (php, ruby, etc...).  If you were to build a server to house a content management system, for example, you'd need apache, for serving content, php, for real-time compiling of php code, and mysql, to house the CMS content (articles, links, etc...).  That setup is often referred to as a LAMP system (linux, apache, mysql, and php).

---

### Post by Brazen on 2007-09-25
> **matt79 said:**
> Could someone please explain more of what Brazen is saying. I think he is onto the type of server I am looking for. What I need is to have a interactive form online so people can fill the form out and sent it to me. I can create a form in openoffice but most people have microsoft office. I thought if I could somehow put openoffice on my server it would take care of the problem. I guess not.

thanks

How do you want to people to send the form back to you?  You could create the form in OpenOffice and then export it as a PDF (as KCPokes said about 3 posts back) but people won't be able to edit it on their computer and email it back.  They would have to print it off, fill it out, and then mail it in.

Alternatively, you could create the form in OpenOffice and then save it as a Microsoft Word document.  Then people can download it and fill it out in word and email it back to you.

What I was talking about, as KCPokes (God bless the lad) said was just basic webserver setup, but it sounds like you don't even need php or mysql.  All you need is Apache.  Here I'll make is real simple:

1.  On your server do this: "sudo apt-get install -y apache2"
2.  Copy your form to the server and put it in the /var/www/ folder
3.  From a workstation, open web browser and go to: "http://ipaddress/formname.doc"
Except replace "ipaddress" with your server's ip address and replace "formname.doc" with the name of your form.
4.  Be amazed as your web browser downloads the form to your computer.

---

### Post by Brazen on 2007-09-25
5.  Send beer and pizza to brazenrocks at gmail dot com.

---

### Post by koenn on 2007-09-25
> **Brazen said:**
> 5.  Send beer and pizza to brazenrocks at gmail dot com.
He'll put it in /var/www and you can download it. Unless you want the beer as a stream.

---

### Post by Brazen on 2007-09-25
> **koenn said:**
> He'll put it in /var/www and you can download it. Unless you want the beer as a stream.

Ha, this made me LOL :D

---

### Post by matt79 on 2007-09-25
Beer and pizza to come:-)
 I will put it up for a day or two after I figure out how. when I installed my server I installed it as a lamp server.
and from what you all said lamp is the short name for linux, apache, mysql, and php. I need apache. but I think I already have it. I have a folder "var" and in that folder I do have another one name "www"
and inside the www I have one called "apache2-default" So tried to put a form I made in a html editor in the www folder, but this error keeps coming up.

Cannot create remote file '/var/www/Form #1.html'

Permission denied.
Error code: 3
Error code:message from server: Permission denied
Request code: 3

btw Brazen, an extra beer for you cause you made it really simple for me to understand the way you explained it(b) and for KCPokes who gave me the much wondering answer on what LAMP means.(b)

I have tried putting  the form I made in microsoft word but it does not work. even though it has the option in the openoffice database.

As for the PDF I could do a interactive form with the option to submit by email button but I could not get it to work. Plus I had a trial of acrobat becouse I can not afford the real thing. lol I can even afford an OS thats not free. Plus I really do want to have a server :-)

---

### Post by Brazen on 2007-09-25
how are you trying to put the file there?  Are you using "cp" from the command line?  If so, you need to prefix it with "sudo".  Another option would be to chown the directory to your username "sudo chown username /var/www".

---

### Post by matt79 on 2007-09-25
> **Brazen said:**
> how are you trying to put the file there?  Are you using "cp" from the command line?  If so, you need to prefix it with "sudo".  Another option would be to chown the directory to your username "sudo chown username /var/www".

I tried it using winscp404 it opens a window with the files on my computer on one side and the files from the server on the other. Not sure how to do it through cp. The file I have is on my computer desktop so how would I put it on my server? I also have putty for commands.

---

### Post by Brazen on 2007-09-26
> **matt79 said:**
> I tried it using winscp404 it opens a window with the files on my computer on one side and the files from the server on the other. Not sure how to do it through cp. The file I have is on my computer desktop so how would I put it on my server? I also have putty for commands.

ok, you can't copy files directly into that folder, because that folder is owned by root and you don't have write access to it.  You can take ownership of the folder with this command (run with putty): "sudo chown username /var/www" but change username to whatever your username is that you are logging on to the server with.

Then you should be able to copy the file in there with WinSCP.

---

### Post by matt79 on 2007-09-26
> **Brazen said:**
> ok, you can't copy files directly into that folder, because that folder is owned by root and you don't have write access to it.  You can take ownership of the folder with this command (run with putty): "sudo chown username /var/www" but change username to whatever your username is that you are logging on to the server with.

Then you should be able to copy the file in there with WinSCP.

ok I did it and it works. However it only works for my computers. I tried typing [http://68.236.255.220](http://68.236.255.220) like I do on my computers on a friends but it does not come up. But I can use putty and winscp on their computers to access my server. I never paid for a static IP address. My modem had an option inside it. I figured that if I could use putty or winscp on a public computer to access my server (and I can)  I could use the same ip addres for hosting a web page. Is this correct?

---

### Post by xaco1234 on 2007-09-27
you have to open port 80 in your router, or modem

---

### Post by matt79 on 2007-09-28
ok, what does that mean?

---

### Post by koenn on 2007-09-28
It's a setting on your modem/router - you may have to explicitly tell it to allow incomming connections on port 80. 
allthough, if you didn't have to do that to make putty work, and 68.236.255.220 is really the address of your server (and not of the router that connects it to the internet, that may not be necessary. In that case, your directly connected to the internet and you should realise that any service you run, is accessible to the world.

---

### Post by Brazen on 2007-10-01
> **koenn said:**
> It's a setting on your modem/router - you may have to explicitly tell it to allow incomming connections on port 80. 
allthough, if you didn't have to do that to make putty work, and 68.236.255.220 is really the address of your server (and not of the router that connects it to the internet, that may not be necessary. In that case, your directly connected to the internet and you should realise that any service you run, is accessible to the world.

I'm kinda guessing the latter is the case, too.  But if he can not get to port 80, I bet his isp is blocking incoming port 80.

---

### Post by matt79 on 2007-12-05
hi I got another Q

I installed ubuntu server 7.10 on my harddisk
I can do stuff by text commands although I am not that good at it. 
The question is, is there a way to have a graphic server so it is sort of like a desktop? One that could host web pages and database.

---

### Post by matt79 on 2008-04-10
I found the answer incase anyone wants to know. You can type "sudo apt-get install edubuntu-desktop"  And it will install a nice desktop on your server.

---

