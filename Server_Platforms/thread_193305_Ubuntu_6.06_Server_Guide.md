---
title: "Ubuntu 6.06 Server Guide"
date: 2006-06-09
forum: Server Platforms
---

### Post by mattheweast on 2006-06-09
The Server Guide is developed by the Ubuntu Documentation Team for each release. It aims to provide help for setting up and configuring server applications on Ubuntu. The guide is translated into many languages.

You can find the guide:
* Inside your system (go to the System help)
* On the Ubuntu documentation website at [http://help.ubuntu.com](http://help.ubuntu.com) in HTML or PDF format
* On the Ubuntu documentation project store at [http://lulu.com/ubuntu-doc](http://lulu.com/ubuntu-doc) in paper form

Thanks, hope it helps!

Matt

---

### Post by xpmaniac4ever on 2006-06-17
Thanks ! ;)

---

### Post by mumushi on 2006-06-22
[QUOTE=mattheweast]The Server Guide is developed by the Ubuntu Documentation Team for each release. It aims to provide help for setting up and configuring server applications on Ubuntu. The guide is translated into many languages.

You can find the guide:
* Inside your system (go to the System help)
* On the Ubuntu documentation website at [http://help.ubuntu.com](http://help.ubuntu.com) in HTML or PDF format
* On the Ubuntu documentation project store at [http://lulu.com/ubuntu-doc](http://lulu.com/ubuntu-doc) in paper form

Thanks, hope it helps!

Matt[/QUOTE]

ok i have read the guide but im still a bit confused. I installed the LAMP server which is in the ubuntu server cd. It was installed flawlessly but fter the installation it rebooted and it ended in a command prompt. Now what's next i am stranded i can't go anywhere. Please help me. My objective is to have my own web server. Thank you so much in advance for your help.

---

### Post by breezyfox on 2006-06-23
[QUOTE=mumushi]ok i have read the guide but im still a bit confused. I installed the LAMP server which is in the ubuntu server cd. It was installed flawlessly but fter the installation it rebooted and it ended in a command prompt. Now what's next i am stranded i can't go anywhere. Please help me. My objective is to have my own web server. Thank you so much in advance for your help.[/QUOTE]
 hi no worries. This is how it works. in case of server it is always better to have non graphical interface.
when you install LAMP server your Apache2, mysqlserver and php5 is already installed. Your default directory for your web site is already there. it is /var/www. if you go to 127.0.0.1 you will get it. you just need to replace it with your own content.
 other option you have to install desktop. sudo apt-get install desktop-ubantu or sudo apt-get install desktop-xbuntu what ever you like to choose.
Play around some basic linux command. there are many tutorial s available on the net.
Hope it will help. just log on with your username and password and try.
 bz

---

### Post by mumushi on 2006-06-29
[QUOTE=breezyfox]hi no worries. This is how it works. in case of server it is always better to have non graphical interface.
when you install LAMP server your Apache2, mysqlserver and php5 is already installed. Your default directory for your web site is already there. it is /var/www. if you go to 127.0.0.1 you will get it. you just need to replace it with your own content.
 other option you have to install desktop. sudo apt-get install desktop-ubantu or sudo apt-get install desktop-xbuntu what ever you like to choose.
Play around some basic linux command. there are many tutorial s available on the net.
Hope it will help. just log on with your username and password and try.
 bz[/QUOTE]


Thanks for the help i will be doing it now. :lol:

---

### Post by mumushi on 2006-07-01
i tried to install the desktop using: > sudo apt-get install desktop-ubantu but i am getting an error something like cannot find E: something i forgot the exact error message.

---

### Post by twstokes on 2006-07-01
Just a little typing error. Type ```
sudo apt-get install ubuntu-desktop
``` instead.

You might want to check out [this HOWTO]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") if this is your first time installing a LAMP. It helped me tons.

---

### Post by NeoGreen on 2006-07-02
Dude you are a Life Saver.:D

---

### Post by mumushi on 2006-07-04
[QUOTE=twstokes]Just a little typing error. Type ```
sudo apt-get install ubuntu-desktop
``` instead.

You might want to check out [this HOWTO]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") if this is your first time installing a LAMP. It helped me tons.[/QUOTE]

Ok i followed the guide 3x and had no luck. I always have an error message on step 7 page 4 of the guide. The error message is >  E: Not a valid candidate.. something.. i forgot the exact error message.

---

### Post by TonyD on 2006-07-05
:o [QUOTE=mattheweast]The Server Guide is developed by the Ubuntu Documentation Team for each release. It aims to provide help for setting up and configuring server applications on Ubuntu. The guide is translated into many languages.

You can find the guide:
* Inside your system (go to the System help)
* On the Ubuntu documentation website at [http://help.ubuntu.com](http://help.ubuntu.com) in HTML or PDF format
* On the Ubuntu documentation project store at [http://lulu.com/ubuntu-doc](http://lulu.com/ubuntu-doc) in paper form

Thanks, hope it helps!

Matt[/QUOTE]

Thanks for this info
I am an absolute newbie and heard of Ubuntu from a IT guy that installed it in our company for mail and webserver. this is my first post,but i have looked around and it seems like a nice crowd. looking forward to setting up my own web server and then moving on to mail server.

Thanks again=D>

---

### Post by twstokes on 2006-07-05
Did you update your sources.list file with the one in the tutorial? Did you run: ```
sudo apt-get update
``` followed by ```
sudo apt-get upgrade
```

Also, remember at that point in the tutorial (Page 4 Step 7) you can SSH into the server from another Linux box or running Putty (which can be downloaded for free) in Windows. I would log in through SSH and paste that huge command rather than manually typing it in and risking an error.

When I followed the tutorial I just picked out the parts I thought were important like getting Apache going and MySQL. You don't have to run a mail server, etc. if you don't need to, and can just skip over those parts if they cause trouble.

---

### Post by mumushi on 2006-07-13
> **twstokes said:**
> Did you update your sources.list file with the one in the tutorial? Did you run: ```
sudo apt-get update
``` followed by ```
sudo apt-get upgrade
```

Also, remember at that point in the tutorial (Page 4 Step 7) you can SSH into the server from another Linux box or running Putty (which can be downloaded for free) in Windows. I would log in through SSH and paste that huge command rather than manually typing it in and risking an error.

When I followed the tutorial I just picked out the parts I thought were important like getting Apache going and MySQL. You don't have to run a mail server, etc. if you don't need to, and can just skip over those parts if they cause trouble.

i did the update and upgrade but i got the error message: > E: Not a vvalid candidate something...

---

### Post by jkblitz on 2006-07-20
sudo apt-get install ubuntu-desktop

ok i used that and it put the files on and it said it wasent able to get a few arcvie files and what is the command to get to the desktop up and running?

---

### Post by n8bounds on 2006-07-24
> **jkblitz said:**
> sudo apt-get install ubuntu-desktop

ok i used that and it put the files on and it said it wasent able to get a few arcvie files and what is the command to get to the desktop up and running?

log in and do a   

  startx

that should do it for ya

---

### Post by chris.raighn on 2006-07-30
Hi, I am installing Ubuntu Server 6.06, and my Linksys WUSB11 v. 2.6 adapter isn't being detected. In Ubuntu 6.06 however, it was detected in installation. Will it still be detected when installation is complete? And if so, how do I update the mirrors that weren't configured during istallation?


Thank you

Chris Raighn

---

### Post by garylai on 2006-08-09
> **twstokes said:**
> Just a little typing error. Type ```
sudo apt-get install ubuntu-desktop
``` instead.

You might want to check out [this HOWTO]("http://www.howtoforge.com/perfect_setup_ubuntu_6.06") if this is your first time installing a LAMP. It helped me tons.


I have follow the in howto; however, after installing the ssh said in page 3 and trying to config. it, I got this message: 

root@neogen:/home/admin# vi/etc/network/interfaces
bash: vi/etc/network/interfaces: No such file or directory

what went wrong?

---

### Post by cdeszaq on 2006-08-10
Does anyone know what modifications would be needed to make this server opperational using a dynamic IP, assuming there was an outside DNS server that could be sent the "updated" IP when/if it changed?

Thanks

---

### Post by makenaa on 2006-08-15
Wow, thank you very much for this! I was having issues installing 6.06 server, but it works now! :wink:

---

### Post by SSTwinrova on 2006-08-17
> **garylai said:**
> I have follow the in howto; however, after installing the ssh said in page 3 and trying to config. it, I got this message: 

root@neogen:/home/admin# vi/etc/network/interfaces
bash: vi/etc/network/interfaces: No such file or directory

what went wrong?
You may have already figured this out, but there needs to be a space. The command should be:

```
vi /etc/network/interfaces
```
So in English, run the command "vi" on the file "/etc/network/interfaces"

---

### Post by stiiixy on 2006-08-21
Hi there. 1st post, w00t! Loving Ubuntu. So anyway, I'm having trouble. I read and followed the ultimate guide posted on this thread (thanks a bajillion. Got me up and running in no time at all) but, then I go to install eGroupware for something to do, point the browser to the install directory, and all I get is the text of the index.php pages. I did something wrong, didn't I?

---

### Post by talrasha on 2006-08-21
Ei! Thanks for the Documentation Team.
The document was great and thank God it helps me a lot.

It gives me light by answering some questions that bothers me being a linux novice. 

Squid is very helpful but I haven't tried it yet. Maybe soon as I finished configuring my box as LAMP server.

Keep up the good job! :p

---

### Post by aethernaut on 2006-09-16
I'm a bit confused...

  I ran the install LAMP option from the Server CD (this took some doing as I ended up needing to add "ide=nodma" after hitting F6 before running the install; I have no freakin' idea WHAT that means or does, other than that it let me install the LAMP server!).

  After fighting with the command line for a day and a half (all the tutorials I've found tend to tell you to do something like type "vi <whatever>" w/o telling you WHAT vi is nor HOW IT WORKS: I've rooted around enough to find the Man page and at least understand that it's a built in text editor...but since the book I'm reading on "Beginning PHP5,Apache,and MySQL by Wrox" assumes that you're running everything from a desktop I decided to take the path of (HA!) least resistance and just install a desktop; assuming I could either uninstall it or just disable it at startup after everything was up and running.

  No dice: when I try to update apt-get I see an error that reads (in part): "Temporary failure resolving 'us.archive.ububtu.com' "

](*,) 

  I tried to sudo apt-get kubuntu-desktop anyway (hope springing and all that)and it says it's: 

"reading package lists...done"
"building dependancy tree....done"
"E: couldn't find package Kubuntu-desktop"

  Since this is an old 750mhz AMD box I thought it might just have a bad connection/network card; but I ran the Kubuntu Live CD to test that w/o any problems whatsoever (it didn't even take long to load up on the piddly 250mb of RAM) and even used the Konkeror(sp?) browser to surf here...in fact I'm making this post FROM the same machine using Kubuntu Live!!

  Does anyone have any idea why the Kubuntu Live CD would allow me to access the net but the LAMP set-up refuses to update apt-get?

  I'd really like to set this up correctly (w/o a GUI) and access it via another machine on the same router (in my googling I saw several things mentioned, such as phpmyadmin, that looked like they might do the trick...but first I'd have to be able to actually ADD the appd to the server install!).

  I'm neither lazy nor stupid...but my ignorance in this area is pretty profound; so very specifically what I'm trying to do is to set up a web server on my old system to run behind a router.

  I can't imagine that this is an unusual project but I've not seen anything in my wandering to babystep me through it so any advice would be welcome.

<edit> I found the problem: I had to reconnect the ethernet cable and reboot the system; now apt-get works just dandy =D> 

  One other issue I had (and fixed) that's worth mention here is that I had to go in and manually shut off DMA again before I could install phpmyadmin; I'm not sure why this is set to "on" by defualt but it doesn't do you any favors if you're running an older system o_O </edit>

---

### Post by bewire on 2006-10-19
Hi, I have Ubuntu Server up and running at one of my "old" computers and access it from both the local network and over the internet via my D-Link router. That way I can play around with different client apps for connecting to the server externally from my Ubuntu Desktop machine or my Windows desktop at the office :-) All I did at the server side was setting up the basic LAMP server and providing SSH connection. For the router I configured a virtual web server. But you will have to deside what security measures to take before allowing external traffic. Thanks to this forum I found all the info I needed ...

bewire

---

### Post by linuxzach on 2006-11-05
I'm a big ubuntu n00b, but does LAMP let me host anything i want, or do I have to ask permission from my ISP or something?

---

### Post by r0ydster on 2006-11-08
> **linuxzach said:**
> I'm a big ubuntu n00b, but does LAMP let me host anything i want, or do I have to ask permission from my ISP or something?

This is your personal box, so you can put whatever you want on it.  All your ISP gives you is internet access.  

Just open your router to your server and anybody should be able to access your content.

The only possible issue would be traffic.  If you were to get dugg/slashdotted, I'm sure your ISP would cut you off.

Mike

---

### Post by peter@kkvs on 2006-11-20
In the section on windows networking

sudo apt-get install samba

Does not install all components such as smbclient, smbfs or quite a bit of the documentation, but later in the instructions it tells you to use smbclient commands.

Also omits to install swat or netkit-inetd, without which swat will not work over the network.

These should either be specified in the server guide or a change made in the install command so that all packages are installed.

---

### Post by mattheweast on 2006-11-21
Peter@kkvs: Thank you for your feedback, I've filed it as a bug and the maintainer will be able to consider it.

See [https://launchpad.net/products/ubuntu-doc/+bug/72680](https://launchpad.net/products/ubuntu-doc/+bug/72680)

---

### Post by lucky_chouhan on 2006-12-04
thank you very much.

Powerful Documentation.

---

### Post by aash on 2006-12-05
Hi

You might want to install webmin. it will provide you with a web administration interface to manage your ubuntu box, and you can forget to install the desktop.

---

### Post by Uta on 2007-02-06
"You might want to install webmin. it will provide you with a web administration interface to manage your ubuntu box, and you can forget to install the desktop."

I need some clarification on this suggestion--
Are you suggesting an install of webmin on a remote host(computer) and admining the server with this interface remotely? Surely you can't install "webmin" on a server that doesn't have GUI set up?
----------------------------------------------------------------------
OK, I figured it out.
You install Webmin on your server and access it from a remote computer via a webpage.
Got-it

---

### Post by Josh_b on 2007-03-05
So with the HOWTO,  am I correct in assuming that I can just skip the installation steps if I don't want that software? I only plan on running a web server (with an external DNS service), so I shouldn't need the mail server software (Courier and PostFix, right?) or the DNS server software (Bind). 

Also, when it says that a server needs to have a static IP address, is that just talking about locally, or the router's IP to the outside world? A does it have to be static (In windows, my router won't let me connect with a static local IP, even if I set it EXACTLY the same as the dynamic IP, ie running ipconfig /all before and after the change is the same)

Thanks,

Josh

---

### Post by kg1 on 2007-03-11
Josh, hopefully you've already gotten an answer...

Correct.  Don't want a mail server, don't install it.

Static IPs ensure that people can get to your server repeatedly.  If the address keeps changing they have to keep finding it again.  

For your external address, you can work around this by using a dynamic DNS service (use Google for providers).  As long as people try to reach your dynamic DNS name you'll be fine.  If your external IP address is pretty stable that can work too (I think my "dynamic" IP address has been the same for over a year now).

You'll also want to have the IP on your local LAN static (or as stable as possible) as you'll need to forward the ports for your webserver from your router to the internal address where your server is listening.  If the server's address keeps changing, you'll need to keep adjusting the destination of the ports being forwarded.  Most routers these days should allow you to specify static IP addresses, or even static DHCP addresses (it's dhcp, but the router gives the same IP address based on the mac address), but that depends on the router....

---

### Post by nbpc on 2007-03-17
I've been working with Ubuntu 6.10 Server specifically for the past week and love it!  I've tried to get into Linux before with Redhad and Suse and Mandrake, but this has been by far my best experience so I'm trying to stick with it.

Of course, it's because of the great Ubuntu community!  But, I'm wondering if there's a good book to get.  I really like Apress books and see that they have [http://www.amazon.com/o/ASIN/1590596277/ref=s9_asin_title_1/104-4557766-3037507]("http://www.amazon.com/o/ASIN/1590596277/ref=s9_asin_title_1/104-4557766-3037507")

There are a tons of online stuff but its not that easy keeping track of where it's at!

Thanks for great work,

NB

---

### Post by KunoNoOni on 2007-03-26
Well I've decided to switch from Slackware 10.2 to Ubuntu Server 6.10. It took me installing it twice to get everything the way I wanted it except for the windows manager. I also use the server to download my bittorrent so I'm looking to put fluxbox on the server, I tried ti once and it was successful but I didn't know that X wasn't on the box. so my question is what would I type in apt-get to install X? I've never had to install it as Slack comes with it already installed. 

hmm... I just realized this is a thread for server 6.06, sorry if I posted this in the wrong thread.

EDIT:

I should have searched more because I think I found the answer I was looking for. [http://ubuntuforums.org/showthread.php?t=391805]("http://ubuntuforums.org/showthread.php?t=391805")

---

### Post by dimis on 2007-03-27
Hi guys,
I installed a xubuntu distro (6.06) on a machine of a friend of mine and two days ago I asked him to install openssh-server so that I can perform some administrative tasks over the phone. Anyway, his machine was hacked two days ago. Here is the log of last:
(user1 is my friend and user2 is me.)
```
user1 pts/0        :0.0             Tue Mar 27 22:28 - 22:39  (00:11)
user1 :0                            Tue Mar 27 22:28 - 22:40  (00:11)
user2    :0                            Tue Mar 27 22:28 - 22:28  (00:00)
user2    tty4                          Tue Mar 27 22:27 - 22:41  (00:14)
user1 tty2                          Tue Mar 27 22:20 - 22:42  (00:21)
root     tty1                          Tue Mar 27 22:19 - down   (00:22)
reboot   system boot  2.6.15-28-386    Tue Mar 27 22:18          (00:23)
reboot   system boot  2.6.15-28-386    Tue Mar 27 14:57          (06:56)
root     pts/0        195.189.220.237  Tue Mar 27 14:20 - 14:26  (00:05)
oracle1  pts/1        195.189.220.237  Tue Mar 27 14:20 - 14:20  (00:00)
root     pts/1        195.189.220.237  Tue Mar 27 14:16 - 14:19  (00:03)
root     pts/0        aplic.eng-eletri Tue Mar 27 14:14 - 14:20  (00:06)
user1 pts/0        :0.0             Mon Mar 26 14:16 - 14:16  (00:00)
user1 pts/0        :0.0             Mon Mar 26 10:56 - 10:57  (00:01)
user1 pts/0        :0.0             Mon Mar 26 02:09 - 02:10  (00:00)
user1 pts/1        :0.0             Sun Mar 25 21:35 - 21:36  (00:00)
user1 :0                            Sun Mar 25 21:35 - 14:21 (1+16:46)
user1 pts/1        :0.0             Sun Mar 25 21:33 - 21:34  (00:01)
user2 pts/0        my_ip_that_day Sun Mar 25 21:29 - 21:35  (00:06)

```
As you can see this man logged in from 195.189.220.237.
Now, I ping that address and there is no packet loss. However, nslookup does not yield something .... But, traceroute does indeed bring me a route to his machine! :S

So, any ideas why this thing happens? (meaning traceroute and nslookup)

Needless to say, this man created an account named 'oracle1' (also logged in remotely 1 time) as:
```
last |grep oracle1
```
shows. Moreover, he deleted my remote accoun (user2), and ... generally vandalised many things on the pc. My friend couldn't even log-in.; I ended up in his place mounting his drives with the live cd and changing password in passwd and shadow files (which were modified remotely). Then I had to make groups, add users on groups ... mess!!!!

Tell me which log you want me to upload!

Regards,

---

### Post by CLI-Linux on 2007-06-08
Okay, I know this thread has been dead for over two months now, but I need some help.

Feisty Fawn doesn't like my hardware for whatever reason (also could be the CD I guess).  So, I've decided to install Dapper because of the Feisty Fawn issue.

When partitioning I want to create Logical Volumes for root dir and swap.  However, I'm having problems.  Fedora Core 6 is currently installed and when I create LV's they aren't overwriting all the data from what I can tell.  Here's the setup:

```
30GB IDE master
---FREE SPACE
20GB IDE slave
---FREE SPACE
```


I'm pretty sure what I want from this is:

```
LV 1 
45GB Ext3 /
LV 2 
5GB Swap 
```

Do I need a bootable flag on either hard drive?  Anyway, when I do this and install, etc. I get a message asking where I would like to install the LILO boot manager, hda(MBR) or hda1(new Ubuntu partition).  It seems like it didn't even erase all the data! ](*,) Then, when I choose where to put it (either place doesn't matter) it says it fails to install LILO.  What is going on here?  Is there anyway to completely clear the MBR?

So, I was wondering if anyone has a lot of knowledge with the LVM on the Dapper Server Install.  Thanks.
-------------------------------------------------------------------------------------------------------------------------------
***EDIT***
Figured out what happened.  LVs don't like to be used for boot partitions.  I had to put physical space on the 30GB hard drive aside so that /boot could mount there.  Then, I used the rest of the space to make the VolGroup and set up the LVs from there.

---

### Post by ubookid on 2007-06-14
i installed the 7.04 server cd, and yes, no GUI. my confusion lies in the fact that when i type "su" enter, it asks for a root passwd. i dont think i set one on installation. i tried all the passwords but no avail. is there a default su passwd? if not, how to reset? or should i re-install? thanks, Uboo

---

### Post by CLI-Linux on 2007-06-15
If you want the gui do:

```
sudo apt-get install ubuntu-desktop
```

Also, if I'm not mistaken, I believe what you're looking for to change root password:

```
sudo passwd

```

Enter the root password.  Or you could do:

```
sudo su
```

which only needs your local user's password to change to root.

---

### Post by Laryllan on 2007-06-15
Hi there!

This is a bit of an off-topic question, but I didn't find any answers in the forums.

I'm using an Ubuntu 6.06 LTS *as a* server, but I installed it with a Xubuntu Desktop CD. After some time I did a new install with a correct CD (Ubuntu 6.06 LTS Server Edition) and realized my old installation uses another kernel.

So, my question is:
How can I change my desktop installation to a server installation?

I found a metapackage called "linux-server", may it do the trick?
What about update support? The Ubuntu website states, that 6.06s desktop edition is supportet for 3 years, whereas the server edition will be supportet up to five years. As I am kind of lazy, I'd like to see my server updated as long as possible. 

Please help. :)

---

### Post by clementtinashe on 2007-07-10
hie guys 
my name is clement l have a problem, l'm trying to set up a fax server and network the server using a wireless networkcard  on  ubuntu 6.06 LTS server edition and l don't have a clue how to do that!, l have installed the server software and after l restarted it only gave me the command prompt, is there a way of activating or installing the network card in command prompt and if so how ?
Thanks in advance

---

### Post by sadeeb on 2007-09-25
How can I launch to graphical interface from shell or start a web browser from shell?  I am new to linux and I had just install ubuntu server 6.06.

---

### Post by ErikV on 2007-09-26
You should only start a graphical interface on a desktop. Your server is a server and not a workstation. So my advise would be: configure your server and test it with a dekstop.

---

### Post by Marinmo on 2007-10-23
Hello

I realize this might be a little bit farfetched, but I'm trying to follow the Postfix-guide from [https://help.ubuntu.com/7.04/server/C/postfix.html](https://help.ubuntu.com/7.04/server/C/postfix.html) but I'm encountering some problems.
First off, I want to mention that my server is debian-based, not ubuntu, but I figured they should be pretty much, if not exactly, the same.

All is going well up until the very last part of configuration; when I telnet into my server and typ ehlo domain.com, the reply given is this, as opposed to what's being said in the guide:
```
ehlo domain.com
250-domain.com
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250 8BITMIME
quit
221 Bye
```
Somehow TLS doesn't seem to work, as the expected reply should include
```
250-STARTTLS
250-AUTH LOGIN PLAIN
250-AUTH=LOGIN PLAIN
250 8BITMIME
```
Below I'll paste my main.cf and saslauthd;
main.cf
```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

myhostname = domain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = domain.com, localhost.localdomain, localhost.localdomain, localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
smtpd_sasl_local_domain =
smtpd_sasl_auth_enable = yes
smtpd_sasl_security_options = noanonymous
broken_sasl_auth_clients = yes
smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination
smtpd_tls_auth_only = no
smtp_use_tls = yes
smtpd_use_tls = yes
smtp_tls_note_starttls_offer = yes
smtpd_tls_key_file = /etc/ssl/private/smtpd.key
smtpd_tls_cert_file = /etc/ssl/certs/smtpd.crt
smtpd_tls_CAfile = /etc/ssl/certs/cacert.pem
smtpd_tls_loglevel = 1
smtpd_tls_received_header = yes
smtpd_tls_session_cache_timeout = 3600s
tls_random_source = dev:/dev/urandom
smtpd_sasl_path = smtpd
```
saslauthd
```
# This needs to be uncommented before saslauthd will be run automatically
START=yes

# You must specify the authentication mechanisms you wish to use.
# This defaults to "pam" for PAM support, but may also include
# "shadow" or "sasldb", like this:
# MECHANISMS="pam shadow"

PWDIR="/var/spool/postfix/var/run/saslauthd"
PARAMS="-m ${PWDIR}"
PIDFILE="${PWDIR}/saslauthd.pid"

MECHANISMS="shadow"

#PARAMS="-n 25 -c -s 128 -t 300"
```

I've checked and all the certificate-files is where they're supposed to (I pretty much c/p that part to make sure nothing went wrong), so I'm really out of ideas here. Anyone?

---

### Post by kragh on 2007-11-06
What is dugg/slashdotted?

---

### Post by WonderCody on 2007-11-22
about the hostname and domain we choose in the ultimate Setup guide.  Do we pick just anything or do we need to purchase a domain and use that?  Or could I use my dyndns.com address?

---

