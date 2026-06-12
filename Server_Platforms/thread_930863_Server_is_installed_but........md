---
title: "Server is installed but......."
date: 2008-09-26
forum: Server Platforms
---

### Post by webbdawg on 2008-09-26
Let me ask a few questions, as I have read many of the server GUI threads. at my house I have an older AMD Sempron that I have my son using with Ubuntu and he likes it. I just installed Kbuntu on an older intel p3600mhz. All that works great. I took some parts along with some new stuff and installed Ubuntu Server. I added the Lamp server, openssh and DNS. I am planing on making a test platform for my web work. I have written in VB6 and PHP worked with both MS and MY sql.

It seems many of you guys do not like the GUI route. I have worked in the old DOS commmand line interface so I am not afraid of it but with the server I am not sure where to begin. 

[LIST]
[*]Is there a recommended book I should get and thumb through?? 

[*]I have used PHPMyAdmin for MySql on one of the sites I take care of. But I do not not know if any of that was installed.

[*]I have seen the Cpanel Program for server administration?

[*]I don't even know how to bring up a dir listing to see what was installed.
[/LIST]


I work off of my XPpro Laptop at a docking station with a big monitor. Can I use the terminal to remotely access the server to do admin like you guys suggest?? I will need to figure that part out.

I do hope to start using the Kubuntu system for my work with the Quanta Plus web tool. Currently I use Macromedia studio 8.

---

### Post by kino6113 on 2008-09-26
in my opinion the command line use of ubuntu is much easyer to use than dos. i have recently dipped into the Linux server "thing" and honestly i can tell you i will never go back. i used this link to set up my first server [http://howtoforge.org/perfect-server-ubuntu8.04-lts](http://howtoforge.org/perfect-server-ubuntu8.04-lts) and while its a how to it gives some of the basics of how it works. also there is some good how to's on the links.

i may want to point out that i very rarely go to the actual server as i have open ssh set up on it to remotely connect anywhere. like i say to people that ask. its really easy to use. if you ever get stuck on any thing just do a google search on the particular program that your stuck on. that will give a broad search on it. and for a narrower just add ubuntu or so forth to the end of it and it will give you a more specific answer.

i also forgot to add i use webmin for management of my server. i like it and works nice.

---

### Post by megabytemonster on 2008-09-26
If you literally just want to test PHP/SQL on a local machine, it may be much easier to use something like XAMPP. Essentially just installs the whole LAMP stack for you, setup to test local PHP.

[http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html")

I used this recently when doing an interview test. Once it's downloaded, can have the whole thing setup in 2 minutes, works great.

---

### Post by webbdawg on 2008-09-26
> **kino6113 said:**
> in my opinion the command line use of ubuntu is much easyer to use than dos. i have recently dipped into the Linux server "thing" and honestly i can tell you i will never go back. i used this link to set up my first server [http://howtoforge.org/perfect-server-ubuntu8.04-lts](http://howtoforge.org/perfect-server-ubuntu8.04-lts) and while its a how to it gives some of the basics of how it works. also there is some good how to's on the links.

i may want to point out that i very rarely go to the actual server as i have open ssh set up on it to remotely connect anywhere. like i say to people that ask. its really easy to use. if you ever get stuck on any thing just do a google search on the particular program that your stuck on. that will give a broad search on it. and for a narrower just add ubuntu or so forth to the end of it and it will give you a more specific answer.

i also forgot to add i use webmin for management of my server. i like it and works nice.
Thanks, I went to the site and scrolled through the document. I wanted to print some of it but now I have to join yet another site. I am getting really tired of having to join. I am frustrated now because I cannot even use the shutdown command on my server. I follow the instructions in the help documentation but it just says command unknown. I tried to get a directory listing so I could see something but the old Linux Commands book I have must be out dated because it does not work either.

I just want to get the programs configured. I guess this is why unix admins make big bucks.

> **megabytemonster said:**
> If you literally just want to test PHP/SQL on a local machine, it may be much easier to use something like XAMPP. Essentially just installs the whole LAMP stack for you, setup to test local PHP.

[http://www.apachefriends.org/en/xampp-linux.html]("http://www.apachefriends.org/en/xampp-linux.html")

I used this recently when doing an interview test. Once it's downloaded, can have the whole thing setup in 2 minutes, works great.

I already have the programs installed from the first install so I don't know if this will help??

Thanks Guys

---

### Post by lykwydchykyn on 2008-09-26
shutdown should work fine; keep in mind things are case-sensitive (you may already know that, but without more info I'm just stabbing in the dark about what the problem might be).  You will of course have to run it as root, so for example, 

sudo shutdown -h now

> 
I guess this is why unix admins make big bucks.


Man, I wish this were true for me.  Where are all these high-paying *nix jobs I keep hearing about?

BTW, I will second the suggestion of installing webmin.  It's easy to install and it will make your life much easier if you are a GUI kind of person.

Also, bear in mind that Ubuntu is a little different in that it uses "sudo" to gain root permissions rather than the "su" command which is traditional, so if you are looking at old Unix/Linux books (most of them are redhat centric) you'll probably see more "su" use.

Finally let me put in a plug for O'Reilly's "linux server hacks" books.  I have them both and they took me well down the road of Linux guru.  You can usually find used copies online for under $10 apiece.

---

### Post by webbdawg on 2008-09-26
> **lykwydchykyn said:**
> shutdown should work fine; keep in mind things are case-sensitive (you may already know that, but without more info I'm just stabbing in the dark about what the problem might be).  You will of course have to run it as root, so for example, 

sudo shutdown -h now



Man, I wish this were true for me.  Where are all these high-paying *nix jobs I keep hearing about?

BTW, I will second the suggestion of installing webmin.  It's easy to install and it will make your life much easier if you are a GUI kind of person.

Also, bear in mind that Ubuntu is a little different in that it uses "sudo" to gain root permissions rather than the "su" command which is traditional, so if you are looking at old Unix/Linux books (most of them are redhat centric) you'll probably see more "su" use.

Finally let me put in a plug for O'Reilly's "linux server hacks" books.  I have them both and they took me well down the road of Linux guru.  You can usually find used copies online for under $10 apiece.

Thanks, I was using the sudo command but the book was telling me to use the shutdown -h-H for a complete halt. I finally found some online stuff in the link at the top of the Server forum. I should have looked there first.

I like to do both gui and command line as the each have their purpose. I need to get Apache, MySql, PHP and FTP configured so I can pretend like I am working on a real web server. I'll have to look for the webmin tool. 

I think a gui really helps break the ice to get things rolling. I don't see why a basic one is not installed and boots directly to it. Like with the desktop versions, you have the option of going to a terminal or command line session.

Thanks again

---

### Post by lykwydchykyn on 2008-09-27
> **webbdawg said:**
> 
I like to do both gui and command line as the each have their purpose. I need to get Apache, MySql, PHP and FTP configured so I can pretend like I am working on a real web server. I'll have to look for the webmin tool. 

I can't fault you there, I work with GUI, web interface, or CLI -- just depends on my mood or which tool works best for the task.  You can download a .deb of webmin from [www.webmin.com](www.webmin.com).  It might be in the repos too.  Once installed, you just direct a web browser to [https://hostname:10000](https://hostname:10000) and log in as your admin user (the first user you create).  It can do just about everything, including installing packages for you.

If you plan on using webmin, I recommend using proftpd for your FTP server.  It's got a nice webmin module.  Pure-ftpd does also, but it's a bit more complicated (though more useful in some situations).

For the rest, just google "Ubuntu LAMP howto" and you'll get about a million tutorials on setting one up from scratch.

> 
I think a gui really helps break the ice to get things rolling. I don't see why a basic one is not installed and boots directly to it. Like with the desktop versions, you have the option of going to a terminal or command line session.

I have to admit, of all the distros out there, I would never have thought Ubuntu would ship a server with no GUI.  Still, it can be installed without much fuss if you need it; if you want xfce for instance:

aptitude install xorg gdm xfce4

That should have you in GUI land in a few minutes.

---

### Post by webbdawg on 2008-09-27
> **lykwydchykyn said:**
> I can't fault you there, I work with GUI, web interface, or CLI -- just depends on my mood or which tool works best for the task.  You can download a .deb of webmin from [www.webmin.com](www.webmin.com).  It might be in the repos too.  Once installed, you just direct a web browser to [https://hostname:10000](https://hostname:10000) and log in as your admin user (the first user you create).  It can do just about everything, including installing packages for you.

I looked at the webmin site and the screen shots look pretty straight forward. I downloaded the file from my Kbuntu system but I am kind of stumped on how to get in installed on the server. 

I am heading to the book store today :)

Thanks

---

### Post by kino6113 on 2008-09-27
[QUOTE=webbdawg;5861117]Thanks, I went to the site and scrolled through the document. I wanted to print some of it but now I have to join yet another site. I am getting really tired of having to join. I am frustrated now because I cannot even use the shutdown command on my server. I follow the instructions in the help documentation but it just says command unknown. I tried to get a directory listing so I could see something but the old Linux Commands book I have must be out dated because it does not work either.


i did not join on that site i just bookmarked it and use it like that. i guess you could select what you want to print go to print and check the print selected option. 

also let me know what book you get on this i would love to know.

---

### Post by freebeer on 2008-09-27
If you think a GUI is going to help you, by all means feel free to install one!  I run a GUI on my servers.  Sure it takes a few more resources (but still less than Windows), but sometimes a GUI is a better tool for a particular job.

---

### Post by lykwydchykyn on 2008-09-27
> **webbdawg said:**
> I looked at the webmin site and the screen shots look pretty straight forward. I downloaded the file from my Kbuntu system but I am kind of stumped on how to get in installed on the server. 

I am heading to the book store today :)

Thanks

If you downloaded the .deb file, the command is 
```

dpkg -i webmin.deb

```
Obviously, replace the "webmin.deb" with whatever the file name is.  If that gives you a bunch of dependency errors (and it probably will), just run:
```

apt-get -f install

```
And that should install the dependencies as well (does anyone know a cleaner method for installing .deb files with dependencies from the CLI??)

Alternately, if you download the .tar.gz file, I recommend placing it in /opt, then run:
```

tar -xvzf webmin-1.430.tar.gz
webmin-1.430/setup.sh

```

---

### Post by webbdawg on 2008-09-28
I have the downloaded webmin file on my Kbuntu system not the server.

[LIST]
[*]I figured I better share my Kbuntu documents dir so I can access it from the server.
[*]When trying to share it, Kbuntu said I needed smb and nfs servers installed.
[*]I went to the Add/Remove Programs and was given a choice of programs beyone comprehension
[*]I went to the Adept Manager and found nothing.
[/LIST]

So moving on, I figured I better give my server a static IP so it is not getting a new one (dhcp) from my router all the time.

I entered the command ipconfig to see what is listed from the server command line and it is an unrecognizable command. So I tried the sudo ipconfig command and the same answer came up. WTF

I am using an "Ubuntu Unleashed" book by Andrew and Paul Hudson with a 2008 printing and copyright date. It is a very current book. Everything I am trying is based on Ubuntu but nothing seems to work. I am going to see if I can return the book and grab something else.

I forgot to mention after issuing the ipconfig command the command line went to a > and nothing works now. I can't even issue the shutdown command

I hope this exploration into the server realm is not going to make me want to throw all my Linux stuff in the trash.

---

### Post by lykwydchykyn on 2008-09-28
ipconfig is a windows command.  You want "ifconfig" (short for "interface configuration"), this is the Linux/unix command. Did you get ipconfig from the book?

If your server is running ssh, don't bother with smb or nfs.  Just open Konqueror on your Kubuntu machine and enter this address:

fish://serverIP

That will get you to your home directory on the server via ssh.  Then just drag the webmin file over.

Also, when your prompt turns into a >, it's because you have entered a command that isn't complete in some way -- for instance you have a quote, double quote, or open parenthesis that isn't closed.   Ctrl-C will get you out of that.

---

### Post by webbdawg on 2008-09-28
> **lykwydchykyn said:**
> ipconfig is a windows command.  You want "ifconfig" (short for "interface configuration"), this is the Linux/unix command. Did you get ipconfig from the book?

If your server is running ssh, don't bother with smb or nfs.  Just open Konqueror on your Kubuntu machine and enter this address:

fish://serverIP

That will get you to your home directory on the server via ssh.  Then just drag the webmin file over.

Also, when your prompt turns into a >, it's because you have entered a command that isn't complete in some way -- for instance you have a quote, double quote, or open parenthesis that isn't closed.   Ctrl-C will get you out of that.

OMG, I should have put my glasses on. An f and P look too similar with out my glasses. It is amazing that the commands can be so similar but different. But I guess anything that can be done to make life more difficult will be done.

Thanks for the help

---

### Post by lykwydchykyn on 2008-09-28
I don't guess it's worth pointing out that "ifconfig" predates the "ipconfig" command by about 12 years.

---

### Post by webbdawg on 2008-09-28
> **lykwydchykyn said:**
> I don't guess it's worth pointing out that "ifconfig" predates the "ipconfig" command by about 12 years.

I figured it did and it was MS who decided to F things up.

---

### Post by lykwydchykyn on 2008-09-28
Technically they decided to "P" things up, eh?

Ok, bad joke.

---

### Post by webbdawg on 2008-09-28
> **lykwydchykyn said:**
> 

If your server is running ssh, don't bother with smb or nfs.  Just open Konqueror on your Kubuntu machine and enter this address:

fish://serverIP

That will get you to your home directory on the server via ssh.  Then just drag the webmin file over.
OK. I got it transfered over and I even right clicked on it and to install it. It appeared to install but the command to run it does not seem to do anything. I tried several vairations but nothing yet.

---

### Post by webbdawg on 2008-09-28
I give up, 2 days a new book and all the help here and I have got nothing to show for it except for sore eyes, a sore ***, stiff shoulders and a head that aches and a pissed off demeanor.

I can't even get a gui installed to help out.

Thanks for the input.

---

### Post by jerome1232 on 2008-09-28
Ok maybe this will help, all these commands would be done while logged into the server.

To install webmin

wget is a tool to download files, I just found the download file using firefox then ssh'd in to my server and copy/pasted the url.

sudo dpkg -i packagename will install debain package we just downloaded, this had errors due to unmet dependencies so the next command (apt-get -f install) resolves those dependencies.

```
wget http://internap.dl.sourceforge.net/sourceforge/webadmin/webmin_1.430_all.deb
sudo dpkg -i webmin_1.430_all.deb 
sudo apt-get -f install
```

edit: Okay it ran immediately after install, I just point my browser to [https://host:10000](https://host:10000) and login as my admin user.

If later you want to completely remove the program you would do this:

```
sudo apt-get remove --purge webmin
sudo apt-get autoremove --purge
```

---

### Post by webbdawg on 2008-09-28
> **jerome1232 said:**
> 

```

sudo dpkg -i webmin_1.430_all.deb 
sudo apt-get -f install
```

I actually got it installed using the above code before you posted this but thanks. It shows how willing you guys are to help.

I got webmin up and running and found where to change the ip. What is odd is I was able to do this at the command line. But when I rebooted the server the IP changed back (probably because of my router's dhcp server). So I hope that the webmin may change the ip permanently. I didn't see any place to specify a static or dhcp address.

Now on to setting up some websites with apache, mysql and php.

Thanks again

---

### Post by webbdawg on 2008-09-29
I am so lost. Even with webmin I am having a really hard time trying to get things going.

I could not find any documentation on the webmin site to explain any of the interfaces for the various services and servers i have installed.

I have not found a good book that really explains clearly from a beginners POV. Everything seems to be based on the fact you already know Linux/Unix.

So I have Apache, MySql, php and Proftp installed but am not getting very far very fast.

It getting very frustrating.

---

### Post by jerome1232 on 2008-09-29
What is it your are trying to do, getting these programs configured usually just takes the editing of a few text files. 

(hence the reason I see no need for a gui for a server, although some web based tools can be nice)

As for some basics I thought this was a decent tut about the basics of a linux command line [http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/](http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/)

There are great tuts out there for configuring each of those individual apps you have installed.

---

### Post by webbdawg on 2008-09-29
> **jerome1232 said:**
> What is it your are trying to do, getting these programs configured usually just takes the editing of a few text files. 

(hence the reason I see no need for a gui for a server, although some web based tools can be nice)

As for some basics I thought this was a decent tut about the basics of a linux command line [http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/](http://www.physics.ubc.ca/mbelab/computer/linux-intro/html/)

There are great tuts out there for configuring each of those individual apps you have installed.

I have been trying to get the server to keep a static IP. I can change it but it changes back to an address received from the home router when I reboot or at startup. I cannot find any setting to specify that the server should be a static ip.

Creating a new site in apache sounds easy but there are many settings when I look in webmin and I have no idea what all the different fields are or mean.

If I ever get phpmyadmin or a different MySql manager installed that should no be a be problem as I use phpmyadmin now. I also have experience with Enterprise manager.

But Apache and FTP administration I am lost because I do not know what all the different settings do and mean.


I don't want my hand held, but an explanation (from somewhere, I do like books) of the different settings and fields would be nice.


Thanks

---

### Post by jerome1232 on 2008-09-29
Well for a quick reply about the static networking I googled 'static ip ubuntu' and this was the first result

[http://codesnippets.joyent.com/posts/show/319](http://codesnippets.joyent.com/posts/show/319)

It explains how to setup a static ip.

Official Apache doc's [http://httpd.apache.org/docs/2.0/](http://httpd.apache.org/docs/2.0/)

This is a good guide to get you up and running with apache
[http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/](http://www.zaphu.com/2007/08/21/ubuntu-lamp-server-guide-configure-apache-mysql-and-cgi-bin/)

I've heard this is a good book about ubuntu in general [http://www.amazon.com/Ubuntu-Unleashed-Andrew-Hudson/dp/0672329093](http://www.amazon.com/Ubuntu-Unleashed-Andrew-Hudson/dp/0672329093)

Here is an online version of it [http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/](http://book.opensourceproject.org.cn/distrib/ubuntu/unleashed/)

hope that helps

---

### Post by lykwydchykyn on 2008-09-30
You can set the IP using webmin, under the networking section, but quite honestly it's easiest to "go to the source" and edit the config file.  The file in question is /etc/network/interfaces.  It's probably got a line like:
```

iface eth0 inet dhcp

```

Just change that to:
```

iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1
broadcast 192.168.1.255

```
Obviously, those are example values, change them to the values you need (broadcast is optional, btw.  I don't know why you need to specify it, but you can).

People make lots of guis for this stuff but frankly it's sometimes just as easy to edit a text file.

Once you've edited it, just reboot or run:
```

/etc/init.d/networking restart

```

---

### Post by webbdawg on 2008-09-30
OK, I'm slowly getting along. I just read so many posts about how it was a breeze.

Anyway I am trying to log into the server remotely via the Kbuntu system. I open up Konsole and type what the book says, changing the IP and user. But I don't connect. I only get command unknown.

Isn't Konsole for SSH and remote access along with local system administration??

---

### Post by lykwydchykyn on 2008-09-30
Absolutely it is.  Any time you get "command unknown", it means you're typing in the command wrong.  Copy what you are typing into Konsole and paste it here.

The command to ssh should be:
```

ssh user@ip_address

```

Remember commands are case-sensitive too, and almost universally in lower case (a few mostly newer programs use upper case letters, but the old unix commands are all lower case).

---

### Post by webbdawg on 2008-09-30
I'm not at my Kbuntu machine right now but I used the syntax the book used.

I like lower case anyway.

Thanks and I'll try it tomorrow.

PS, is there a good ssh for WinXPpro??

Thanks

---

### Post by jerome1232 on 2008-10-01
Yeah there's putty which is good, but I like to use openssh, because it's syntax is the same as if you were on a linux system, if you google openssh for windows it should be the first site you that gets listed same with putty.

---

### Post by karryn on 2008-10-02
I've never worked on the Ubuntu desktop, only on the command line, and it was frustrating trying to find a book that wasn't centered around the desktop.  I finally found this:

[http://www.amazon.com/Ubuntu-Linux-Toolbox-Commands-Debian/dp/0470082933/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1222965789&sr=8-1](http://www.amazon.com/Ubuntu-Linux-Toolbox-Commands-Debian/dp/0470082933/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1222965789&sr=8-1)

It has absolutley no information on any of the gui apps.  Since I only deal with the server versions of Ubuntu, it's been a huge help to me.

---

### Post by karryn on 2008-10-02
This is an article in Linux magazine that explains why the command line is so useful:

[The Importance of Command Line Literacy]("http://www.linux-mag.com/id/7096")

It does require registration to read, though...

---

### Post by webbdawg on 2009-10-09
Ok, I am resurrecting this thread because it has so much good informatioin it for others to scan through and I have more questions.

Having gotten the server back up and running (I figured it out by myself) I cannot seem to get the apache server to dish up my test site.

here is the virtual config section from the config file
> # Include the virtual host configurations:
Include /etc/apache2/sites-enabled/
ServerName Local
UseCanonicalName off
<VirtualHost 192.168.1.10>
DocumentRoot /var/www/testanarchy
ServerName [www.testanarchy.com](www.testanarchy.com)
<Directory "/var/www/testanarchy">
allow from all
Options Indexes
</Directory>
<Directory "/var/www/testanarchy">
</Directory>
<Directory "/var/www/testanarchy">
</Directory>
</VirtualHost>

When I type the server IP in the browser address I can get the root index I put there. But I cannot get the virtual server site I have tried to create.

I plan on getting several test sites as this will be my test server (LAMP). If I can't even get one site going I am in trouble.

Thanks for keeping it going.

---

