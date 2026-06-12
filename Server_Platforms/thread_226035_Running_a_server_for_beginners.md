---
title: "Running a server for beginners"
date: 2006-07-30
forum: Server Platforms
---

### Post by DigitDuke on 2006-07-30
Hi there,

I'm really interested in starting to play around with setting up a web server.  I want to set up a stable and secure server and I want to know how to maintain it.

Because the risk of asking for recommendations of reading material are big, because "newbie" means different things for different people.
[LIST]
[*]I grasp the basic thought behind hosting.  I even have my own up and running server which I installed with help from Howtoforge.  I have a Mac, and they have Apache and PHP out of the box (and I have installed MySQL), which I use as a development environment.
[*]I know Perl, and I can use it for linear development.  With a lot of help I've established a client for the "Spinchat" protocol.  I've also made some scripts to make my life easier, for example for making things get done faster around my cPanel.
[*]I've been using cPanel hosting for many years.  I know all the services that normal hosts offer, what they're about and how they work on the user end.
[*]I write pretty much linear PHP as well, my PHP skills are nearly as good as my Perl ones.
[*]I know the basic SQL commands and I use MySQL for most of my development.
[/LIST]

Now, you may not see how that is relevant, but my point with this is to show you [i]what sort[i] of a beginner I am, instead of simply stating "I'm a beginner" which could mean everything from only having ever played computer games to only having ever run a Windows server.

Now, can anyone recommend reading material for my user level with information about hosting a web server?  I'd like to learn how to securely use SSH, DNS and BIND, Apache, PHP configuration, MySQL... I want to learn everything to do with hosting a server, maybe spiced up with a little PHP programming. :-)

It can be a book (many books won't hurt) or it can be a website (even many websites) - I really don't care as long as it has thorough and well-explained material, preferrably with information as to "why" and "how" things are done.  

Thanks a lot, and I hope this thread will be a resource to more users in this very same position later on.

---

### Post by Cephus on 2006-07-30
I'm also a newbie, though I am still in the learning stages of dynamic web programming, using DHTML, PHP, MySQL, etc.  I had my introduction through several Continuing Education classes at the local university.  I also began on a Windows platform using PHPDEV, which for all practical purposes configured the machine without much user intervention.

I've been running Dapper exclusively for the past several weeks, and am happy to report that I find I can do anything with Linux that I did with Windows.

I installed Apache, PHP, and MySQL the other night, and everything seems to be talking nicely with each other.  The only change I made in Apache was in the 'ports.conf' file, where I stated 'listen 127.0.0.1:80'.  As I'm still learning about Linux security, I believe this will prevent any outside snooping.

I'll admit that I'm not used to running on a platform without virus scanners, software firewalls, etc.  What else do I need to consider for security while running a local server not intended for outside use, as well as general security for a machine that is generally on 24/7? 

Cephus

---

### Post by az on 2006-07-30
[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

[https://help.ubuntu.com/community/WebServerHosting](https://help.ubuntu.com/community/WebServerHosting)

---

### Post by adamkane on 2006-07-30
Unfortunatley Ubuntu web server maintenance is difficult. At some point your installation will become hosed, and you need to know how to deal with it.

Unfortunately there is no foolproof backup/restore options, and you will need to know how to re-install and migrate data when the time comes.

If you have a MySQL database, run a cron to automatically back up your databases.

Use sbackup to automatically backup your files to a safe place. You can use sbackup to restore, but you will probably just move the files over manually.

If you are going to run a LAMP server, there are good ways and bad ways to install, and unfortunately no proven ways to re-install, when necessary.

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

``` 
Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

``` 
Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

Some people say to use MySQL-Administrator, but unfortunately there are sudo (permission) issues, which make mysql-admin too unusable in my opinion. You will have better results with phpMyAdmin and MySQL-Query-Browser.

The issue of Perl (CGI) scripts is even more troublesome. You will need to edit your apache2.conf file to allow cgi scripts to run. I had success with this a while back after reading the official documentation at apache.org.

---

### Post by Nap_BlownApart on 2006-09-15
Hi,
  I to am a beginner (in a similar sense to DigitDukes first post here).  In my case, I would like to setup a LAMP server with the following options:

Perl 5.8.7
Apache 1.3.37,
MySQL-Server 4.1.21-Standard,
PHP 4.4.4,
phpMyAdmin 2.8.0.2, and 
cPanel 10.8.2-Release 119

I need these versions so as to mirror my Web Hoster's setup.
In the above commandline that "AdamKane" posted, there are some additional things included (like mod_PHP4).

I've noticed that the _naming convention for packages_ does not seem to specify a certain standard for version numbers.  That is, some have '-' between the name and version, some don't.  This is a problem for me as a beginner.

Here are my questions:

Q1) On my Ubuntu (which I set up a few days ago), most of Perl 5.8.7 is already installed.  According to Synaptic, there are a few things which haven't been, such as the DOCs (which I will install).  **Should I install all the other Perl related items for a LAMP server?**

Q2) Can someone provide me with some guidance on what I need to install in addition to Q1 above.  A commandline similar to "AdamKane's" would be great.  If someone's already covered this elsewhere, a link will be fine too.

Q3) In "AdamKane's" commandline above, MySQL-Client is installed.  Is this required?  (My intention is to connect to this Linux box through my browser and Putty [or equivalent].)

Cheers,
Nap

---

### Post by mssever on 2006-09-21
> **DigitDuke said:**
> Now, can anyone recommend reading material for my user level with information about hosting a web server?  I'd like to learn how to securely use SSH, DNS and BIND, Apache, PHP configuration, MySQL... I want to learn everything to do with hosting a server, maybe spiced up with a little PHP programming. :-)

I've found the DNS HOWTO to be really helpful: [http://tldp.org/HOWTO/DNS-HOWTO.html](http://tldp.org/HOWTO/DNS-HOWTO.html)

---

### Post by Icereval on 2006-09-22
If you decide to do development on your server (Trac, SVN, Apache, MySQL) here is a very nice bash script for backing all that data and offloading it to another computer.

Just setup a few variables in the backup.sh file and cron it to run every night.

[http://blog.i-loveyou.info/2006/07/28/backup-script-for-mysql-svn-trac-and-www/](http://blog.i-loveyou.info/2006/07/28/backup-script-for-mysql-svn-trac-and-www/)

---

### Post by Jingo on 2006-09-23
About maintenance..
Is it posible to get an email when packages needs upgrading ?

---

### Post by 5parx on 2008-05-17
>With a lot of help I've established a client for the "Spinchat" protocol.

Hello. I am a normal user on spinchat. A beginner programmer in java and I am rapidly learning Java.
I would like to ask what details you could give me on the protocol, I have most of it but hopefully you can fill in my gaps. Email me back at [email]thebandit232@gmail.com[/email] please if you plan on dispatching a reponse. Thanks.

---

### Post by mssever on 2008-05-18
> **5parx said:**
> >With a lot of help I've established a client for the "Spinchat" protocol.

Hello. I am a normal user on spinchat. A beginner programmer in java and I am rapidly learning Java.
I would like to ask what details you could give me on the protocol, I have most of it but hopefully you can fill in my gaps. Email me back at [EMAIL="thebandit232@gmail.com"]thebandit232@gmail.com[/EMAIL] please if you plan on dispatching a reponse. Thanks.

This thread is really old (July-September 2006). You'd be better off posting a new thread. Also, please don't ask for responses by private e-mail. Public replies mean that the info is available for future readers. You can configure your Ubuntu Forums account to send you e-mail whenever someone replies to one of your subscribed threads.

(About spinchat: I've never heard about it. Sorry I can't help you there.)

---

