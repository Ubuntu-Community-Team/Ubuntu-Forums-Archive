---
title: "Problem installing CUPS on Ubuntu 8.10 server"
date: 2009-01-10
forum: Server Platforms
---

### Post by svsig on 2009-01-10
I have installed Ubuntu 8.10 server, and I am now trying to install CUPS. I have tried to follow several How-To's found on the web, but I can't make it work. When I try to access the CUPS web interface at port 631 on the server from another machine in the network I get an error message.

I have basically tried to follow the description in [_this how-to_]("http://www.howtoforge.com/ubuntu-gutsy-samba-domaincontroller-p2"), under Installing CUPS. This is for 7.10, but it is the best one I have been able to find. I have found a couple of other how-to's, but they have not been of any more help.

My server has IP address 10.0.0.201, and the client has IP address 10.0.0.145. This is how my cupsd.conf file looks:

[FONT="Courier New"][INDENT]...
...
#Listen localhost:631
Listen 10.0.0.145:631
Listen /var/run/cups/cups.sock
...
...
# Restrict access to the server...
<Location />
  Order allow,deny
  Allow localhost
  Allow 10.0.0.145
</Location>

# Restrict access to the admin pages...
<Location /admin>
  Order allow,deny
  Allow localhost
  Allow 10.0.0.145
</Location>
...
...
[/INDENT][/FONT]

When I try to access [http://10.0.0.201:631](http://10.0.0.201:631) from my client I get the error message:

Failed to Connect
Firefox can't establish a connection to the server at 10.0.0.201:631

The server itself seems to be OK.  I have installed LAMP server and MediaWiki, and these are working fine. Sharing with Samba and NFS is also working fine.

Can somebody please help?

---

### Post by jonathanmotes on 2009-01-19
Sweet! I've had the same problem and just figured it out!

**This is what I did:**

1. SSH into server
2. Install links2 command-line web browser
```
sudo apt-get install links2
```
3. Open CUPS interface link this
```
links2 http://localhost:631/
```
4. Click on Administration link
5. Check "Allow remote administration" and click on "Change Settings"
6. Enter username and password
7. I think you have to click on the redirect link at the top of the page (it seems that links2 does not support automatic redirection).

Thats it! You can now use the CUPS web interface to set up the printer remotely!


**Or, I think you can just use my new cupsd.conf file: **

Get it here: [http://dl.getdropbox.com/u/386086/cupsd.conf.txt](http://dl.getdropbox.com/u/386086/cupsd.conf.txt)

Be sure to make a backup of your cupsd.conf file before modifying it!

If you go this route, restart cups after saving the /etc/cups/cupsd.conf file:
```
sudo service cups restart
```

I think these are the important parts (if you don't want to replace the whole file):

1. 
```
# Allow remote access
Port 631
```

2. Allow @LOCAL in these sections
```
<Location />
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin>
  Encryption Required
  # Allow remote administration...
  Order allow,deny
  Allow @LOCAL
</Location>
<Location /admin/conf>
  AuthType Default
  Require user @SYSTEM
  # Allow remote access to the configuration files...
  Order allow,deny
  Allow @LOCAL
</Location>
```

Just ask if you have questions!

---

### Post by joshiss on 2009-01-24
I am stuckup with the user name and password only the cups is asking for username and password and not accepting any password i tried root, my regular username and all weird possibilities.
Kindly help:(
sorry i forgot to mention that i am using ubuntu 8.10

---

### Post by jonathanmotes on 2009-01-24
> **joshiss said:**
> I am stuckup with the user name and password only the cups is asking for username and password and not accepting any password i tried root, my regular username and all weird possibilities.
Kindly help:(
sorry i forgot to mention that i am using ubuntu 8.10

I'm not certain, but I believe I was prompted to make a password when I installed CUPS. Do you remember doing that?

---

### Post by waspinator on 2009-01-27
I'm also trying to get CUPS to work in Ubuntu 8.10 Server. I can log into it using links2 in ssh, but when I try to use access the server from another computer i get 403 Forbidden. 

Also slightly related is that in webmin, in the printer configuration it doesn't show any CUPS drivers.

---

### Post by cariboo on 2009-01-27
You only need the username and password you setup when you installed the server edition  for administrative functions. 

Just for fun I accessed the cups web interface running elinks as root, and it still asked for my username and password.

Jim

---

### Post by jonathanmotes on 2009-01-28
> **waspinator said:**
> I'm also trying to get CUPS to work in Ubuntu 8.10 Server. I can log into it using links2 in ssh, but when I try to use access the server from another computer i get 403 Forbidden. 
Did you use links2 while "sshed' in" to access the CUPS web interface and change the settings to "Allow remote administration"? 

You just have to restart CUPS afterwards, and then you should then be able to access the CUPS interface from any computer on your network.

---

### Post by waspinator on 2009-01-28
@jonathanmotes

Yes I did set it to allow remote administration, and then reset cups. Before I did that it wouldn't show anything when i typed in my address at port 631. Now at least I get 403 Forbidden.

Is there maybe a good tutorial on how to confiture the cups config file?

Thanks

---

