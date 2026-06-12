---
title: "FTP Server Config"
date: 2007-03-24
forum: Server Platforms
---

### Post by tbuss on 2007-03-24
Hello, I'm new to Linux and I'm interested in setting up an FTP server for my family. I've recently installed Edgy and I was wondering if it was possible for me to set up an FTP server so that only my family members could connect. We are separated geographically and I would like to make available pictures and videos for the rest of my family. Everyone in my family uses windows, I'm not sure if that will work. So basically I need a FTP server that is password protected but will grant access to authorized users that don't have local access to the files. 

I've searched and found the following thread on how to setup such a configuration

[http://www.ubuntuforums.org/showthread.php?p=429783#post429783](http://www.ubuntuforums.org/showthread.php?p=429783#post429783)
[B]
During install I received this: 
[/B]
```

tbuss@tbuss-desktop:~$ sudo apt-get install proftpd
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  proftpd-doc
The following NEW packages will be installed:
  proftpd
0 upgraded, 1 newly installed, 0 to remove and 8 not upgraded.
Need to get 609kB of archives.
After unpacking 1569kB of additional disk space will be used.
Get:1 http://security.ubuntu.com edgy-security/universe proftpd 1.3.0-9ubuntu0.1 [609kB]
Fetched 609kB in 2s (227kB/s)   
Preconfiguring packages ...
Selecting previously deselected package proftpd.
(Reading database ... 142541 files and directories currently installed.)
Unpacking proftpd (from .../proftpd_1.3.0-9ubuntu0.1_i386.deb) ...
Setting up proftpd (1.3.0-9ubuntu0.1) ...
Adding system user `proftpd' with uid 109...
Adding new user `proftpd' (109) with group `nogroup'.
Not creating home directory `/var/run/proftpd'.
Adding system user `ftp' with uid 110...
Adding new user `ftp' (110) with group `nogroup'.
Creating home directory `/home/ftp'.
`/usr/share/proftpd/templates/welcome.msg' -> `/home/ftp/welcome.msg.proftpd-new'
 *** Starting ftp server proftpd                              - IPv6 getaddrinfo 'tbuss-desktop' error: Name or service not known**
                                                    [ ok ]
```

If anyone has any suggestions please reply, if you have a link or something similar I can refer to that would be great. Thank You

---

### Post by Mr. C. on 2007-03-24
A problem with FTP that you should be aware of is that the user's password is transmitted over the insecure network in clear text.  Nonetheless, FTP still is very useful, especially for non-sensitive data or accounts.

If your family members are not terribly familiar with FTP, you can also setup a web server that presents a simple listing of the files for videos and pictures.  You can use FTP to upload files into the directories.

Browsers have built-in FTP clients, so your family can simply use their browser to access the FTP site - they don't need any special programs, and uploading or downloading is drag-and-drop.

If you really want a nice web interface that you can setup on your server, consider Gallery 1 or 2 at: [http://gallery.menalto.com/](http://gallery.menalto.com/).

MrC

---

### Post by jakev383 on 2007-03-24
> **tbuss said:**
> Hello, I'm new to Linux and I'm interested in setting up an FTP server for my family. I've recently installed Edgy and I was wondering if it was possible for me to set up an FTP server so that only my family members could connect. We are separated geographically and I would like to make available pictures and videos for the rest of my family. Everyone in my family uses windows, I'm not sure if that will work. So basically I need a FTP server that is password protected but will grant access to authorized users that don't have local access to the files. 

If anyone has any suggestions please reply, if you have a link or something similar I can refer to that would be great. Thank You

Here is what I use. I create a local user on the machine (useradd family) and give it a password that I share with everyone. This config for proftpd will jail them in their home dir so they can't browse the whole system. Also keeps them from getting lost in the filesystem. They will be able to download and upload files. If you turn on ftp_conntrack they'll be able to use PASV ports, so they'll be able to open the FTP link in Internet Explorer and just drag files onto the FTP window in IE and it will upload the files. Same for downloading the files - they can just drag them and drop them in a folder. Anyway, here's the config:
```

# This is a basic ProFTPD configuration file (rename it to
# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName                      "FTP Server"
ServerType                      standalone
DefaultServer                   on

# Port 21 is the standard FTP port.
Port                            21

# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask                           022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd).
MaxInstances                    30

# Set the user and group under which the server will run.
User                            nobody
Group                           nobody

# To cause every FTP user to be "jailed" (chrooted) into their home
# directory, uncomment this line.
DefaultRoot ~

# Normally, we want files to be overwriteable.
AllowOverwrite          on

# Bar use of SITE CHMOD by default
<Limit SITE_CHMOD>
  DenyAll
</Limit>

<Global>
        AllowRetrieveRestart on
        AllowStoreRestart on
        ExtendedLog /var/log/proftpd.log
</Global>


```
Hope that helps. Don't forget to open the ports in your firewall! This config is from a Redhat system, so you may need to change the user/group to what was used during install (proftpd user and nogroup group).

---

### Post by tbuss on 2007-03-24
Thank you to both of you. I have been on the XChat #Ubuntu channel for about three hours. I have tons of information available now. I want to keep the interface as clean and simple as possible. My only experience with FTP is when I downloaded an image of Ubuntu. I though this technique and the interface would be ideal for my family members. I just installed vsftpd, I haven't tried to configure yet, keeping my fingers crossed. My only concern with setting up an FTP server is that I will somehow not configure it properly and as a result compromise the integrity of my data stored on my computer.  Thanks again

---

### Post by scxtt on 2007-03-24
add your box's name to the IPv6 info in /etc/hosts:
```
[font=courier]# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback **<add it here>**
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts[/font]
```

---

### Post by tbuss on 2007-03-25
jakev383 

> If you turn on ftp_conntrack they'll be able to use PASV ports, so they'll be able to open the FTP link in Internet Explorer and just drag files onto the FTP window in IE and it will upload the files. Same for downloading the files - they can just drag them and drop them in a folder. 

I couldn't find ftp_conntrack in /etc/proftpd/proftpd.conf I'm very new to Linux and FTP.

---

### Post by tbuss on 2007-03-25
**scxtt**

> # The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback <add it here>
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

I know this might be a silly question but I was under the impression that I was using IPv4

---

### Post by tbuss on 2007-03-25
I've successfully installed proftpd. I still have a few questions. How do I connect to the FTP server to test my configuration. Also, do I need to setup accounts for each family member that I want to share with. I want the contents to be password protected so that only authorized persons can access.  Here is my config file, I tried to attach but kept getting an invalid file type 

```
#
# Includes required DSO modules. This is mandatory in proftpd 1.3
#
Include	/etc/proftpd/modules.conf

# This is a basic ProFTPD configuration file (rename it to
# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName                      "FTP Server"
ServerType                      standalone
DefaultServer                   on

# Port 21 is the standard FTP port.
Port                            21

# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask                           022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd).
MaxInstances                    30

# Set the user and group under which the server will run.
User                            nobody
Group                           nobody

# To cause every FTP user to be "jailed" (chrooted) into their home
# directory, uncomment this line.
DefaultRoot ~

# Normally, we want files to be overwriteable.
AllowOverwrite          on

# Bar use of SITE CHMOD by default
<Limit SITE_CHMOD>
  DenyAll
</Limit>

<Global>
        AllowRetrieveRestart on
        AllowStoreRestart on
        ExtendedLog /var/log/proftpd.log
</Global>
```

---

### Post by Mr. C. on 2007-03-25
> **tbuss said:**
> I've successfully installed proftpd. I still have a few questions. How do I connect to the FTP server to test my configuration. Also, do I need to setup accounts for each family member that I want to share with. I want the contents to be password protected so that only authorized persons can access.  Here is my config file, I tried to attach but kept getting an invalid file type 


$ ftp localhost

I am not a fan of using the same username/uids for multiple people, as it makes accounting and auditing impossible.  Give each user a unique account.  This will allow you to become familiar which IPs your users connect, and which ones look suspicious.

MrC

---

### Post by tbuss on 2007-03-25
Mr. C.

Okay, I'm getting there. My ftp server is up and running. Now, I've tested it on other computers in my house which are all running Ubuntu; they all worked fine. But when I called my dad he was not able to connect. He is running windows, does he need some sort of client software. **Jakev383** mentioned that I should enable ftp-conntrack; this would enable my family memebers to be able to open my ftp link in IE. I was unable to find ftp_conntrack anywhere in the config file. What else can I do to enable my family to connect to my ftp link using internet explorer?

---

### Post by jakev383 on 2007-03-25
> **tbuss said:**
> Mr. C.

Okay, I'm getting there. My ftp server is up and running. Now, I've tested it on other computers in my house which are all running Ubuntu; they all worked fine. But when I called my dad he was not able to connect. He is running windows, does he need some sort of client software. **Jakev383** mentioned that I should enable ftp-conntrack; this would enable my family memebers to be able to open my ftp link in IE. I was unable to find ftp_conntrack anywhere in the config file. What else can I do to enable my family to connect to my ftp link using internet explorer?
You are running IPv4. I wouldn't worry too much about the IPv6 at this point.
I'm also not a fan of using the same user/pass for multiple users, but for what you're doing it will work out well. You're not interesting in auditing your family's pictures. If you are then I wouldn't use FTP for this anyway.
The ip_conntrack and ip_conntrack_ftp modules should be loaded at boot time. I'd just make sure they are or PASV ports won't work. You'd load them by:
/sbin/modprobe ip_conntrack
/sbin/modprobe ip_conntarck_ftp
And yes, your Dad will need a FTP client for Windows. For Windows I personally prefer CuteFTP, but you may like something else.
Your Dad will be able to use your FTP with IE if he wants. You'll need to give hm the proper URL to access though. Change the following to match your info and have your Dad give it a try:
[ftp://user:password@192.168.1.1](ftp://user:password@192.168.1.1)
Obviously change the user and password to what you have set up. And change the 192.168.1.1 to whatever your IP address is. If you're on a dynamic IP (cable modem, DSL, etc.) then you may want to look at something like DynDNS to give your computer a name that will move with you.
Have fun!

---

### Post by Mr. C. on 2007-03-25
Simple.  In any browser:

```
ftp://user:password@ftpserver/path
```

MrC

---

### Post by scxtt on 2007-03-26
> **tbuss said:**
> **scxtt**
I know this might be a silly question but I was under the impression that I was using IPv4what i suggested should get rid of the IPv6 error you see on proftpd startup ...

---

### Post by tbuss on 2007-03-26
**scxtt**

It worked, thanks

---

### Post by tbuss on 2007-03-26
**jakev383**

Okay, I'm getting something now but still have problems.

setup **proftpd** and used default **proftpd.conf**
setup user "userftp" and group "family" password protected
opened port 21 and configured port fowarding on router to port 21
--used ip address for this computer to act as server behind router

I have a small home network of 4 computers, all running ubuntu.
When I type [ftp://X.X.X.X](ftp://X.X.X.X) or :21 from any of these computers on the network I can connect after entering the username name and password. There is a upload and a download dir.

I also tried [ftp://userft: passwrd@X.X.X.X](ftp://userft: passwrd@X.X.X.X) and was able to connect using a computer on the network

When my dad tries to connect using the same address, he cannot connect. (perhaps a port forwarding problem?) Computers inside the router can connect but computers from the outside cannot.

I registered at **No-IP.com** bozfam.no-ip.biz and it posted the IP address for the computer. The IP was different? Does the router assign an ip for the network and an ip for outside the network. 
When I try to connect using **[ftp://bozfam.no-ip.biz](ftp://bozfam.no-ip.biz)** I get the "enter username and password" but it times out or loads forever. Do I need to change the IP for the port forwarding to the one No-IP listed? will this allow computers to connect from outside the network?

DHCP is enabled on my router

I'm going to replace my config file with the one you provided. Open the ports **20,21** and **10000-10500.** And replace the IP in the port fowarding config from the original to the one listed at No-IP

Also I tried to load the modules last night and I received an error:
```
tbuss@tbuss-desktop:~$ sudo /sbin/modprobe ip_conntarck_ftp
FATAL: Module ip_conntarck_ftp not found.
tbuss@tbuss-desktop:~$ 
```

I'm so frustrated right now. All I wanted to do was simply provide a way for family members to download pictures and home movies. I've only been using Linux for about month so everything is very cumbersome right now. I appreciate all your help. I'll post back with my results.

---

### Post by scxtt on 2007-03-26
here's a few basics when it comes to networks and registering a domain name:

if your router uses 192.168.1.1 and it's set to start assigning IP addresses like 192.168.1.100, .101, .102 etc., you'll want to make sure your FTP box has an IP on this network (looks like you've got this sorted out as you can use your FTP service from w/in the network) ...

for someone connecting, it'll be like this:

their computer (192.168.1.100) --> their router (192.168.1.1) --> their modem (external IP, anything that's not reserved like 192.168.1.1 and 10.0.0.1, etc.) <-- the internet --> [color=green]your modem's external IP[/color] --> your router's IP (192.168.1.1) --> your [color=blue]FTP server's IP (192.168.1.100)[/color] ...

so you need to make sure that route is actually accessible ... when you add something like no-ip.com to the mix, you have to be sure bozfam.no-ip.biz points to "[color=green]your modem's external IP[/color]" and that your router forwards requests "from the outside" for port 21 to [color=blue]your FTP server's IP[/color] ...

i'd also set static IPs for your router, so nothing IP-wise gets changed on reboot ...

---

### Post by jakev383 on 2007-03-26
> **tbuss said:**
> **jakev383**

Also I tried to load the modules last night and I received an error:
```
tbuss@tbuss-desktop:~$ sudo /sbin/modprobe ip_conntarck_ftp
FATAL: Module ip_conntarck_ftp not found.
tbuss@tbuss-desktop:~$ 
```

I'm so frustrated right now. All I wanted to do was simply provide a way for family members to download pictures and home movies. I've only been using Linux for about month so everything is very cumbersome right now. I appreciate all your help. I'll post back with my results.
You mispelled conntrack when you tried to load the module.
Don't get too frustrated. You're getting into some advanced stuff at a very early level. Some speedbumps are to be expected. And you're trying to learn at the same time.

---

### Post by tbuss on 2007-03-26
The good news is that with the help of everyone in this thread I was able to configure my first Linux ftp server. So thank you to everyone for all you great advice. 

I tested the connection this morning and my father was able to connect, download and upload using the DNS name I registered with No-IP.
We had to figure some things out in the beginning. In order for him to be able to drag and drop files from both the "download" and "upload" directories using IE(7), he was prompted to click on page->and then click open ftp site in IE. Once that was done, drag and drop was successful. 

Also, I'm unable to connect using my own computer (the one hosting the files) using the DNS that was successful for my father? But, if I use the ip of my computer I can then connect? These are two different ip's.

Anyway, I want to say thanks again to everyone for all your help, this is the first time I have ever tried anything like this; to actually use my computer for something other than music, web, and email :)

---

### Post by Mr. C. on 2007-03-26
> **tbuss said:**
> 
Also, I'm unable to connect using my own computer (the one hosting the files) using the DNS that was successful for my father? But, if I use the ip of my computer I can then connect? These are two different ip's.

Your router does not support NAT loopback.  On the LAN, you must use LAN addresses; on the WAN, the WAN address must be used.

Create an entry in /etc/hosts that maps your chosen domain name to your LAN server's IP address.

MrC

---

### Post by tbuss on 2007-03-26
Well, it looks like I spoke too soon.

First connection test: **[COLOR="DarkGreen"]Pass[/COLOR]**
My father was able to connect to the server with no problems using domain name.
The page loaded asking for user name and password
Logged in with credentials 
Once he was logged-in he received a message similar to this:

    [B]ftp root @ bozfam.no-ip.biz
    "To view this site in Internet Explorer click page 
    and then click open FTP site in Internet Explorer"[/B]

He followed instructions and was then prompted for Username and ID again
The user name was  already entered,  had to re-enter password
Log-in success, the Username and Password worked as advertised
For drag and drop capability in **IE7 **all he needed to do was follow the on-screen prompts.
He was able to upload and download files just fine.


Second connection test: **[COLOR="DarkOrange"]Questionable[/COLOR]**
My sister was able to connect using domain name.
This time however she was prompted to log in as** anonymous**.
I told her to try it and she was denied.
She then logged in using Username and Password.
Connection success, drag and drop, upload, download worked as advertised
I have Anonymous log-in disabled in my **proftpd.conf **
Why was she prompted when other were not?

Third and last connection test: **[COLOR="Red"]Fail[/COLOR]**
I had my brother try to connect using domain name
Connection timed out.
I told him to try the IP assigned to the domain name instead
Connection timed out.

I've gone from not knowing were to start for setting up a FTP server to a few minor problems.
It's not much but 2 out of 3 had success connecting
One of the 2 users that had success was prompted to log-in anonymously 
[B]The question of why I can't connect from inside the network has been answered by Mr. C. (I'll give it a try in a minute)
[/B]None of the 2 successful connections were greeted with the welcome message.

---

### Post by tbuss on 2007-03-26
Here is a message specific from the failed attempt by my brother(on his end)

Specific message note:

An error occurred opening that folder on the FTP Server.  Make sure you have
permission to access that folder.

Details:
200 Type set to A
227 Entering passive mode(68, 47, 183, 124, 253, 35)
421 No transfer Timeout (300 seconds) closing control connection

---

### Post by Mr. C. on 2007-03-26
You will find that a majority of input or trials by others are not as you specified, no matter how often you repeat exact instructions.  There is just too much room for interpretation and ambiguity.

The FTP mechanism you have setup will work, but it is a bit clumsy (and insecure).

Instead of speaking the URL to each of them, prepare it in an email, and send them the URL, so that they can just click to open.  You can test it, to see that it works.  This is no more or less secure than using your current method, so the password is transmitted in clear text either way.

Become comfortable with your log files in /var/log, and how to enable additional debugging when necessary.

MrC

---

### Post by tbuss on 2007-03-26
I began by sending out e-mails with the ip and No-Ip.biz to all family members. My father is a network administrator for the University of the South. For some reason he isn't willing to help; I guess he likes to see me suffer :) The only reason I can think of why my brother could not connect when others can is because of some type of proxy or some other security measure implemented where he works.  **Mr. C**. I also made the changes in etc/hosts I can now get to the ftp on my own computer using the no-ip.biz, but I still need to use the LAN ip to connect from other computers on the network.(no big deal, just wish it would work) This is beginning to be too much. I think I will just burn the pictures and movies to disc and send them in the mail. Plus I'm worried about security, there is no telling what kind of threats I've exposed my computer to with all the fumbling around with configurations, not knowing what I was doing. I was on #Ubuntu last night and someone invited me to a private session, after about thirty minutes of "acting" like they were helping, they said they had a "killer windows ftp server "lol" I probably gave them some info I probably shouldn't have, just a little too naive I guess. I know everyone here has tried to help, and I've learned alot; I think I'm going to take a break for a while

---

### Post by Mr. C. on 2007-03-26
Don't fret - this stuff takes time and patience to learn.

Your addition to the hosts file must be done on *each* machine from which you will connect to your server.  Remember, hostname translation always begins with the local system.  In a TCP/IP world, hosts and DNS are the usual choices.

Hang in there.
MrC

---

### Post by tbuss on 2007-03-26
I thought I would post this link in case anyone might be interested, or if anyone needs help setting up an ftp server. If you follow the guidance of those who have responded to my many questions you'll be off to a good start. This link might help as well. Reading the explanations provided helped with some of the terminology.  I know I said I was going to take a break, I just couldn't let it go........

[http://cpplus.info/docs/proftpd_default_server_configuration.html](http://cpplus.info/docs/proftpd_default_server_configuration.html)

---

### Post by tbuss on 2007-03-27
I'm trying to reinstall proftpd. Things were so mucked up last night I figured a clean slate would work best. 

Now when I try to install proftpd I get the following:

```
tbuss@tbuss-desktop:~$ sudo apt-get install proftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  proftpd-doc
The following NEW packages will be installed:
  proftpd
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B/609kB of archives.
After unpacking 1569kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package proftpd.
(Reading database ... 145052 files and directories currently installed.)
Unpacking proftpd (from .../proftpd_1.3.0-9ubuntu0.1_i386.deb) ...
Setting up proftpd (1.3.0-9ubuntu0.1) ...
 * Starting ftp server proftpd                                                                                     - Fatal: TLSRSACertificateFile: '/etc/gproftpd/gproftpd.pem' does not exist on line 51 of '/etc/proftpd/proftpd.conf'
                                                                                                           [fail]
invoke-rc.d: initscript proftpd, action "start" failed.
dpkg: error processing proftpd (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 proftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)
tbuss@tbuss-desktop:~$ 
```

 '/etc/gproftpd/gproftpd.pem' does not exist on line 51 of '/etc/proftpd/proftpd.conf'
    I'm confused, If I removed the previous installation would this directory still exsist?

---

### Post by scxtt on 2007-03-27
yeah, i don't think the uninstall feature for that package works well ... i also uninstalled proftpd once, then decided to reinstall it and ran into that problem ...

what i did:

sudo slocate -u (update the slocate database)
slocate proftpd (search for proftpd files/dirs)
[remove everything "slocate proftpd" returns]
sudo aptitude install proftpd

also, if you installed gftpprod, you might want to uninstall it as well or post what's on "line 51 of '/etc/proftpd/proftpd.conf'" ...

---

### Post by tbuss on 2007-03-28
Followed removal instructions:

> sudo slocate -u (update the slocate database)
slocate proftpd (search for proftpd files/dirs)
[remove everything "slocate proftpd" returns]
sudo aptitude install proftpd

this what I got after sudo aptitude install proftpd

```
tbuss@tbuss-desktop:/home/FTP-shared$ sudo aptitude install proftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages have been automatically kept back:
  transcode 
The following packages have been kept back:
  ffmpeg mjpegtools 
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
tbuss@tbuss-desktop:/home/FTP-shared$ 

```
Then I do this:

```
sudo gedit /etc/shells  #added  /bin/false to the file
cd /home
sudo mkdir FTP-shared
sudo useradd userftp -p ****** -d /home/FTP-shared -s /bin/false
sudo passwd userftp
cd /home/FTP-shared/
sudo mkdir download
sudo mkdir upload
cd /home
sudo chmod 755 FTP-shared
cd FTP-shared
sudo chmod 755 download
sudo chmod 777 upload
sudo gedit /etc/proftpd/proftpd.conf

```
I tried to configure proftpd.conf after install but it does not exsist. proftpd is nowhere in /etc/

I quit

---

### Post by scxtt on 2007-03-28
well, it definitely didn't reinstall it ... maybe try:

sudo aptitude search proftpd (see if there's an "i" in the left column)

sudo aptitude update (to make sure the package cache is up to date)
sudo aptitude install proftpd (since it didn't reinstall it before)

and make sure it's actually installed and proftpd.conf exists ...

---

### Post by tbuss on 2007-03-28
I know I said I quit,  just can't let it go.

tbuss@tbuss-desktop:/home/FTP-shared$ sudo aptitude search proftpd
Password:
p   gforge-ftp-proftpd         - Collaborative development tool - FTP
c   gproftpd                   - GTK+ configuration tool for proftpd 
**i   proftpd                    - Versatile, virtual-hosting FTP daemo**
v   proftpd-common             -                                     
p   proftpd-doc                - Versatile, virtual-hosting FTP daemo
p   proftpd-ldap               - Versatile, virtual-hosting FTP daemo
p   proftpd-mysql              - Versatile, virtual-hosting FTP daemo
p   proftpd-pgsql              - Versatile, virtual-hosting FTP daemo
tbuss@tbuss-desktop:/home/FTP-shared$

> sudo aptitude update (to make sure the package cache is up to date)
sudo aptitude install proftpd (since it didn't reinstall it before)
and make sure it's actually installed and proftpd.conf exists ...


Same result, proftpd.conf does not exists  /etc/proftpd not found

---

### Post by scxtt on 2007-03-28
do you have a **/usr/share/proftpd/templates/proftpd.conf**? ... maybe you can copy it to **/etc/proftpd/proftpd.conf** ...

do you have a **/usr/sbin/proftpd**?
and/or a **/etc/init.d/proftpd**?

---

### Post by tbuss on 2007-03-29
> do you have a /usr/share/proftpd/templates/proftpd.conf? ... maybe you can copy it to /etc/proftpd/proftpd.conf ...

do you have a /usr/sbin/proftpd?
and/or a /etc/init.d/proftpd?

No to all three, 
Also tried slocate proftpd......Nothing found

---

### Post by tbuss on 2007-03-31
Since I was dual booting with windows, I just setup a ftp server on windows, I was up and running in less than 20 minutes. I dont know why it was easier to to set up an ftp server in widows, it just was. I'll try to setup a linux sever in the future, just don't think I have the experience or*** time*** to get it done right now.

---

### Post by c_jadhav2002@yahoo.com on 2007-04-03
how to configure ftp and telnet

---

### Post by frodon on 2007-04-03
> **Mr. C. said:**
> A problem with FTP that you should be aware of is that the user's password is transmitted over the insecure network in clear text.  Nonetheless, FTP still is very useful, especially for non-sensitive data or accounts.This is true however it's easy to add TLS encryption which allow to transmit the username, the password and the datas in a encrypted way and i recomend to anyone who use his FTP server often to enable TLS encryption (the way to set TLS encryption is documented in my guide).

---

### Post by tbuss on 2007-04-03
frodon,

I have used your guide [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) but I have a problem with the password at login. I used the GUI to setup the user and group accounts, like you recomended. But if I enter Users and Groups and change the password, the next time I enter User and Groups the password has not changed. If I create a new user and give it a 4 letter password and exit out, the next time I enter User and Groups and edit that particular account, the password box shows a entry of more than 4 characters, it's like it defaults to a hidden password. I tried to logout and log back in, I also tried sudo passwd userftp nothing works. I cant login int the server because I don't know what this password is, and I cant change it.

---

### Post by frodon on 2007-04-03
wow, i looks strange, it never issued such problems here it seems like if you were having a problem with the user and group GUI.
Anyway there's a ccommand line to set the password, you should try it :
```
sudo passwd *username*
```Then you will see if it works or if there's any error output.

---

### Post by tbuss on 2007-04-03
**frodon:**

I tried sudo passwd *username,* no luck
I'm going to do a clean install of edgy today. 

I've followed your guide [http://ubuntuforums.org/showthread.php?t=79588](http://ubuntuforums.org/showthread.php?t=79588) and had much success, especially useful for  a noob like myself. Been trying to configure this ftp server properly for two weeks now, I think I finally have it down now, I've never felt so uneducated in my life :)
I'm going to use it to setup my ftp server after I reinstall edgy today

I noticed in your thread someone (post 421) had a problem with this: 
> - IPv6 getaddrinfo 'Server' error: Name or service not known

I had a similar problem and it was answered here: **(scxtt)**
> add your box's name to the IPv6 info in /etc/hosts:
```
The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback <add it here>
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

Thanks again for all your help.

---

### Post by Spiny Norman on 2007-04-03
I put shares for my family on my home server and allow them to pick up with WinSCP. 
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php). (If they can be trusted to leave everything else alone)
You might have to talk them through the setup but I personally like the SSH tunneling and no browser involvement. I am a basic user but think that that would be fairly secure? Please feel free to shoot me down if I'm talking c*%p.

---

