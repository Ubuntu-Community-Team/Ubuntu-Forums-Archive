---
title: "Webmin, Virtualmin, and mysql problems :("
date: 2016-12-31
forum: Server Platforms
---

### Post by teachingtech.me on 2016-12-31
[COLOR=#111111][FONT=Ubuntu]I posted this on stackexchange but haven't gotten a reply and am really curious as to what is wrong.

First I just want to say I am fairly new to linux and even newer to setting up a server, so please bear with me.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Ok so first I have a (small) issue while installing webmin which is here [Error installing webmin on ubuntu 16.04]("http://askubuntu.com/questions/866477/error-installing-webmin-on-ubuntu-16-04/866483#866483") after fixing that everything worked fine and I was able to login to webmin no problem. After logging into webmin I wanted to install wordpress. After a google search I found I can install through virtualmin (which I believe is supposed to come with webmin?)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I tried to install virtualmin using

```
[FONT=Consolas]sudo /bin/sh install.sh[/FONT]
```

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Which returned this

[/FONT][/COLOR]```
[COLOR=#111111][FONT=Consolas]Displaying the last 15 lines of /root/virtualmin-install.log to help troubleshoot this problem:[/FONT][/COLOR]
mysql-client is already the newest version (5.7.16-0ubuntu0.16.04.1).
mysql-common is already the newest version (5.7.16-0ubuntu0.16.04.1).
mysql-server is already the newest version (5.7.16-0ubuntu0.16.04.1).
ntpdate is already the newest version (1:4.2.8p4+dfsg-3ubuntu5.3).
openssl is already the newest version (1.0.2g-1ubuntu4.5).
apache2-suexec-custom is already the newest version (2.4.18-2ubuntu3.1).
clamav-testfiles is already the newest version (0.99.2+dfsg-    0ubuntu0.16.04.1).
libdbd-mysql-perl is already the newest version (4.033-1ubuntu0.1).
procmail-wrapper is already the newest version (1.0-2).
scponly is already the newest version (4.8-4).
usermin is already the newest version (1.701).
webmin is already the newest version (1.830).
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
mysql-server : Depends: mysql-server-5.7 but it is not going to be installed
FATAL - Fatal Error Occurred: Something went wrong during installation: 0
FATAL - Cannot continue installation.
FATAL - Attempting to remove virtualmin repository configuration, so the     installation can be
FATAL - re-attempted after any problems have been resolved.
FATAL - Removing temporary directory and files.
FATAL - If you are unsure of what went wrong, you may wish to review the log [COLOR=#111111][FONT=Consolas]FATAL - in /root/virtualmin-install.log[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]I have tried doing 'apt-get -f install Which does not work. It's obvious the issue is with mysql
so I tried
[/FONT][/COLOR]```
[COLOR=#111111][FONT=Consolas]sudo apt-get purge mysql-server mysql-client mysql-common mysql-server-core-5.5 mysql-client-core-5.5[/FONT][/COLOR]
```[COLOR=#111111][FONT=Ubuntu]

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]which just tells me to try 'apt-get -f install'[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Someone PLEASE help![/FONT][/COLOR]

---

### Post by TheFu on 2016-12-31
Welcome to the forums.

Let's step back a bit.

If you want to learn Linux, don't use webmin.  For people really new to Linux, webmin generally just makes taking over their systems by hackers much easier.  They just don't have a sufficient background to secure it properly.  OTOH, if someone with 5+ yrs of server admin experience sets up these tools for you, then they will likely be sufficiently secured (probably through an ssh tunnel) to be used.  Hopefully, the firewall only allows access to localhost for  webmin, virtualmin, and mysql - though I can see opening the mysql port for the exact, specific, non-public, IPs for client access.

Does that make sense?

I felt your pain, BTW. When I was new, I searched and searched for some GUI, any GUI to make management of my Linux system a little easier.  Fortunately, it was even harder to get webmin installed and working back then, so I failed.  I spoke with all the Unix gurus at work and they made the same suggestion I made to you above.  Learn to do it the Unix way, from the shell.  For server management, use the shell when you are new. There isn't any other way to learn it.  People have asked for a GUI to do this stuff for decades.  There are specialized distros for that. Perhaps using one of them and learning about the lack of flexibility first hand would be good?

I dunno.

---

### Post by teachingtech.me on 2016-12-31
> **TheFu said:**
> Welcome to the forums.

Let's step back a bit.

If you want to learn Linux, don't use webmin. For people really new to Linux, webmin generally just makes taking over their systems by hackers much easier. They just don't have a sufficient background to secure it properly. OTOH, if someone with 5+ yrs of server admin experience sets up these tools for you, then they will likely be sufficiently secured (probably through an ssh tunnel) to be used. Hopefully, the firewall only allows access to localhost for webmin, virtualmin, and mysql - though I can see opening the mysql port for the exact, specific, non-public, IPs for client access.

Does that make sense?

I felt your pain, BTW. When I was new, I searched and searched for some GUI, any GUI to make management of my Linux system a little easier. Fortunately, it was even harder to get webmin installed and working back then, so I failed. I spoke with all the Unix gurus at work and they made the same suggestion I made to you above. Learn to do it the Unix way, from the shell. For server management, use the shell when you are new. There isn't any other way to learn it. People have asked for a GUI to do this stuff for decades. There are specialized distros for that. Perhaps using one of them and learning about the lack of flexibility first hand would be good?

I dunno.
Thanks for the advice. I figured webmin would make things easier, not harder. I am sort of limited to what OS I can use since I am using AWS. Not sure if you are familiar with their services or not, but if you are, maybe you could give me a bit more advice as to what direction to go in?

---

### Post by SeijiSensei on 2017-01-01
If you can start over, I suggest doing so.  I don't know what software comes with an AWS image, but to run WordPress, I suggest installing the "lamp-server" package like this:
```
sudo apt-get install lamp-server^
```
The tilde is required.  That will give you Apache, PHP, and MySQL.  Now to get started with WordPress, download the latest version from wordpress.org, and unzip it into /var/www/html.  You'll need root privileges to do this.  Since you're new to this, I'd put WP in its own directory:
```

cd /var/www/html
sudo mkdir wp 
cd wp
sudo unzip /path/to/wordpress.latest.zip

```
Next you'll need to create an empty MySQL database.  Run the command
```
sudo echo 'create database database_name' | mysql -u root
```
replacing database_name with whatever you want.  If you created a password for MySQL during installation, add "-p password" after "-u root".  Then you should be able to navigate to [http://localhost/wp](http://localhost/wp) to start the WordPress configuration.

---

### Post by TheFu on 2017-01-01
I've never used AWS. Seems too expensive for anything longer than a few hours. There are faster, less expensive, VPS options, but I've never used those either.

Be very careful running wordpress.  It is commonly hacked.  There are some recent write-ups about attackers specifically against wordpress.  Be certain to avoid the dangerous WP plugins/addons and poorly maintained themes.  BTW, my niece's husband works for Automattic (the company behind Wordpress).
[https://www.wordfence.com/blog/2016/04/hackers-compromised-wordpress-sites/](https://www.wordfence.com/blog/2016/04/hackers-compromised-wordpress-sites/)
[https://www.wordfence.com/blog/2016/12/russia-malware-ip-hack/](https://www.wordfence.com/blog/2016/12/russia-malware-ip-hack/) - 
[https://www.wordfence.com/blog/2016/08/top-50-attacked-wordpress-plugins-week/](https://www.wordfence.com/blog/2016/08/top-50-attacked-wordpress-plugins-week/)

Every server has similar issues. Regardless, we all need to be aware and take "appropriate steps"*  to mitigate.

* whatever you think is necessary, but being very new means knowing the all issues is impossible.

I don't think AWS limits which OSes you can run or what can be installed. They just make using certain releases/versions easier.

---

### Post by Habitual on 2017-01-01
> **teachingtech.me said:**
> I am using AWS. Not sure if you are  familiar with their services or not, but if you are, maybe you could  give me a bit more advice as to what direction to go in?Yes,  sure can. You will need to have port 10000 opened in your [SecurityGroup]("https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html#creating-your-own-security-groups") for <Trusted IP(s)> for the Running Instance as it says all out, no in, unless explicit.
The following are the default rules for a security group that you create:


[LIST]
[*]Allows no inbound traffic 
[*]Allows all outbound traffic 
[/LIST]


Simply allow trusted.ip.1/32 for on tcp:10000 on your existing SecurityGroup for the Instance. No restart. Declare ip/32 on tcp:10000  and go.
This will inhibit unauthorized access to the webmin interface.
I take no responsibility for other rules. ;)

Happy New Year and what TheFu says. :)

---

### Post by SeijiSensei on 2017-01-01
> **TheFu said:**
> Be very careful running wordpress.  It is commonly hacked.  There are some recent write-ups about attackers specifically against wordpress.
Yes, you do have to pay attention when WP updates are released.  I see one every month or so.

---

