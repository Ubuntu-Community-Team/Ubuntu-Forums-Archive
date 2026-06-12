---
title: "Learning ubuntu by installing servers help"
date: 2011-10-12
forum: Server Platforms
---

### Post by mushy365 on 2011-10-12
have already installed apache, samba and vsftpd and got them all configured and working how i wanted to i share my downloads with my family when the connect to my lan. 

Im doing this to learn more about ubuntu, network security and working with terminal. was just wondering what i can do next to increase knowledge

---

### Post by WasMeHere on 2011-10-12
Hi mushy365,	

What would you like best to learn about? Think in categories like
- tools: terminal commands, shell scripts, programming languages ...
- applications: photo + multimedia, desktop publishing, math, science, networking ...

Why not have a look at [[COLOR="RoyalBlue"]_Cool applications you use that others might not know of_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=382137")

Have fun learning about Ubuntu :-)
Olle

---

### Post by mushy365 on 2011-10-12
Thanks i'll have a look, i like the whole idea of network security, progamming ive done some programming in c, python, c# before, i have made alot of webpages with php mysql jquery and css

when installing and configuring i tried to use the command line as much as possible and i learnt lots of new commands and got a better understanding of how the terminal works reading the man pages, getting an understand of where the .conf files are kept,  piping output , resrarting daemons changing permissions and owners of files and folders. Doing all that through terminal for the first time and understanding it was fulfilling 

so i think ideally something about using the terminal, intergrated with some aspect of networking or managing a network service that someone could use. ill have a look at your site tho thanks

---

### Post by drdos2006 on 2011-10-12
Here is a HOWTO which I found comprehensive and invaluable. Uses Webmin to allow your browser to connect and modify your server settings.
You could also install the Desktop plus install and run the server as a virtual machine using Virtualbox and that is how I run my testing websever.

> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
"Setting up a Linux Server, Start to Finish, using Webmin". By Kevin Elwood



And on your server..........

```

Logon to your server and download from your server with :
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.550_all.deb

Install with :
sudo dpkg -i webmin_1.550_all.deb

Add extra libraries with :
sudo apt-get -f install

```

regards

---

### Post by SeijiSensei on 2011-10-12
Install a [DNS]("https://help.ubuntu.com/community/BIND9ServerHowto") server and a [mail]("https://help.ubuntu.com/community/Postfix") server. You'll learn a lot!

I also recommend the book [TCP/IP Network Administration]("http://shop.oreilly.com/product/9780596002978.do") by Craig Hunt.

---

### Post by WasMeHere on 2011-10-12
> **mushy365 said:**
> ...

so i think ideally something about using the terminal, intergrated with some aspect of networking or managing a network service that someone could use...

Maybe you can be active helping people: testing and discussing issues on the Ubuntu Forums :-) Many people need help which includes terminal commands or shell programming.

Have fun
Olle

---

### Post by mushy365 on 2011-10-12
I thought about a DHCP server, but i dont get the point of it, what would it enable me to do that i cant do already on my lan? 

All computers recognise my server name so i dont need to use an ip address to link to it, i just use the hostname of my computer. I dont get what extra benefit creating a DHCP server will have, doesnt my router do all that anyway? 

I'm also worried messing around with dhcp will mess up my network in someway or something or have i got it completely wrong?

---

### Post by WasMeHere on 2011-10-13
I suggest that you think

- what do I want to learn about?
- what do I want my computers / network to do?

So if you want to make a firewall, make one,
if you want to make a dhcp server, make one,
if you want to make a backup system using your server to store the backup data, make it ...

It need not necessarily be useful (because there is dedicated hardware, or you do not need it (now)). And don't forget about other applications than those related to servers! There are many interesting things to do with a computer.

---

