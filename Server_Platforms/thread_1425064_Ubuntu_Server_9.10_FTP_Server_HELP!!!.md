---
title: "Ubuntu Server 9.10 FTP Server HELP!!!"
date: 2010-03-08
forum: Server Platforms
---

### Post by AdamShumpisxXx on 2010-03-08
Hey, everyone! Great to be back. I'm having a bit of a dilemma here. I'm running Ubuntu Server 9.10 and I'm looking to setup an FTP server. I have SSH running beautifully and it's accessible from any computer whether it be inside the network or coming in from the internet (provided you have the administrator username and password :p). I've tried Proftpd and vsftpd and have failed miserably so far. I've read countless tutorials and have spent days researching and I've come up with next to nothing. I will say that I've gained a great deal of knowledge so far but not enough to solve my own problem. Here's where you geniuses come in :D...

Which FTP server application do you think I should go with and how could I go about setting it up through my SSH connection?

My current setup is this:

- Ubuntu Server 9.10 with Fixed IP of 192.168.1.100
- 500GB Hard Drive
- SDA1 = 512MB ext2 /boot
- SDA2 = 2GB swap
- SDA3 = 20GB ext4 /
- SDA5 = 438GB ext4 /home
- One User (Username = administrator)
- Full SSH Capabilities
- IP Address to DNS provided by [www.dyndns.org](www.dyndns.org)
- WRT120N Router with Remote Access and Port 22 Open

I basically want to set up a secure FTP server that anyone on the internal network can access as well as anyone from the internet (as long as they have a username and password). I want to setup a username and password for each user so that they all have read/write access to the same folder in my /home partition (I'll call it FTPSHARE). Any help on this would be GREATLY appreciated. Thank you all very much in advance for any help!!!

---

### Post by fang0654 on 2010-03-08
If you are looking for a fast, secure ftp over ssh setup, then why not use sftp?  It is built into OpenSSH, and will provide users with access to their home drives.  You can then put a symbolic link in there to the shared folder that everyone will use.

More info can be found here:

[http://www.openbsd.org/cgi-bin/man.cgi?query=sftp-server&sektion=8&arch=&apropos=0&manpath=OpenBSD+Current]("http://www.openbsd.org/cgi-bin/man.cgi?query=sftp-server&sektion=8&arch=&apropos=0&manpath=OpenBSD+Current")

---

### Post by AdamShumpisxXx on 2010-03-08
> **fang0654 said:**
> If you are looking for a fast, secure ftp over ssh setup, then why not use sftp?  It is built into OpenSSH, and will provide users with access to their home drives.  You can then put a symbolic link in there to the shared folder that everyone will use.

More info can be found here:

[http://www.openbsd.org/cgi-bin/man.cgi?query=sftp-server&sektion=8&arch=&apropos=0&manpath=OpenBSD+Current]("http://www.openbsd.org/cgi-bin/man.cgi?query=sftp-server&sektion=8&arch=&apropos=0&manpath=OpenBSD+Current")

I thought of that first before FTPcame into my head. Thing is...the users like the idea of being able to use Filezilla to download/upload files or even just use Firefox to download some documents real quick. My mind is made up in wanting to use FTP. Would you be able to help me in that respect? Thank you very much for your help, anyways!

---

### Post by jeffshowalter7 on 2010-03-08
Having just gone down this road myself:)  I found that I like the proftpd setup the best. It is easy to configure/work with. I though ran into a networking issue though with mine with the passive ports and came around with an alternate resolution after many days of searching. I ended up using a mix of proftpd for a generic ftp site, but when I came to securing ftp for upload and download, I just used sftp(which users can use filezilla with) After Chrooting the users I found it was a much easier solution. you also only have to configure what your ssh port is then on the firewall.
I have never had much luck with secure ftp through a browser.
Hope that helps.
Jeff

---

### Post by AdamShumpisxXx on 2010-03-08
> **jeffshowalter7 said:**
> Having just gone down this road myself:)  I found that I like the proftpd setup the best. It is easy to configure/work with. I though ran into a networking issue though with mine with the passive ports and came around with an alternate resolution after many days of searching. I ended up using a mix of proftpd for a generic ftp site, but when I came to securing ftp for upload and download, I just used sftp(which users can use filezilla with) After Chrooting the users I found it was a much easier solution. you also only have to configure what your ssh port is then on the firewall.
I have never had much luck with secure ftp through a browser.
Hope that helps.
Jeff

SFTP would be a viable solution if everyone who was going to use this server had any sort of knowledge with such things. Thing is though is that they're all basically monkeys with screwdrivers :p. They know how to use FTP because they've been using it and any change would just cause a huge uproar followed by flying feces, if you catch my drift. I've been hearing Proftpd is a better way to go like you said though. I just need something that would work with the parameters I have shown above in my first post.

I'm begging you guys :confused:...

Also, I don't know if I was clear or not but I'm the only one using SSH. Everyone else will ONLY be using Filezilla or Firefox for FTP. I need each user to be able to download/upload to the same same directory (/home/UserFTP/FTPSHARE/) with full read/write access.

Thanks for all the help so far. I'm just so lost. Can anyone help?

---

### Post by jeffshowalter7 on 2010-03-08
> **AdamShumpisxXx said:**
> SFTP would be a viable solution if everyone who was going to use this server had any sort of knowledge with such things. Thing is though is that they're all basically monkeys with screwdrivers :p. They know how to use FTP because they've been using it and any change would just cause a huge uproar followed by flying feces, if you catch my drift. I've been hearing Proftpd is a better way to go like you said though. I just need something that would work with the parameters I have shown above in my first post.

I'm begging you guys :confused:...

Also, I don't know if I was clear or not but I'm the only one using SSH. Everyone else will ONLY be using Filezilla or Firefox for FTP. I need each user to be able to download/upload to the same same directory (/home/UserFTP/FTPSHARE/) with full read/write access.

Thanks for all the help so far. I'm just so lost. Can anyone help?


Here's my final input in case you don't get any other speedy responses. I hope you do as I was looking originally for the same solution

Here are all your requirements from previous posts
1. Secure over internet or internally 
2. users can upload files filezilla
3. upload to a common folder /home/UserFTP/FTPSHARE/ 
4. lock users down to only that folder so they can't access other folders...etc.

straight Sftp can do all these things. I hate to be that person,(you know the one that says "hey do this instead its so much better then what your doing") :) but it was the best solution for me and it looks like it might be for you.

Sorry that is all I got. Hope you find what you need if you don't go with SFTP. I just know that it works for me after trying for a long time to get vsftpd and proftpd to work correctly without errors and firewall issues. 
thanks,
Jeff

---

### Post by cdenley on 2010-03-08
As already said, FileZilla does work with SFTP as well as FTP and FTPS. With ubuntu 8.04, recent versions of filezilla will not work with proftpd using SSL, but seem to work fine with vsftpd, which is why I recently switched. I think 9.10 should work fine, though. As far as I can tell, vsftpd is lighter and simpler (probably more stable and secure), but proftpd has more features. I would not use FTP, especially over the internet, unless you use SSL encryption (FTPS/FTPES) since logins can be easily intercepted.

---

### Post by AdamShumpisxXx on 2010-03-08
So, I'm seeing that the consensus is to use SFTP...Would anyone know of a link to a tutorial on how to get that running with the requirements I have listed in my previous posts? I'd be happy to try it. It just has to do what I need it to do is all and it has to be secure. Thank you all for your help in this matter so far!

:KS

---

### Post by jeffshowalter7 on 2010-03-09
I just took this from another site. Really the easiest is follow the weblink below steps 1-3. Below I have how to set up a user with a different home directory. Really, If you just google chroot sftp users or jail sftp users you will get a lot of info.(almost more then you ever wanted to know.)

[HTML]Now we create a user that we want to have sftp access only. This user won't be able to login on a standard ssh login but will be able to login using sftp to transfer files. Replace user with whatever you wish. Set the home directory (in this case /var/www/vhosts/theirsite.com) to the folder you want the user to have access to.

sudo useradd -d /var/www/vhosts/theirsite.com user

Now set a password for the user:

sudo passwd user

Change the user's primary group to the sftp group we just created

sudo usermod -g sftp user

Then we need to set the user's shell to /bin/false

sudo usermod -s /bin/false user
[/HTML]


[http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny](http://www.howtoforge.com/chrooted-ssh-sftp-tutorial-debian-lenny)

---

### Post by doogy2004 on 2010-03-09
> **AdamShumpisxXx said:**
> So, I'm seeing that the consensus is to use SFTP...Would anyone know of a link to a tutorial on how to get that running with the requirements I have listed in my previous posts? I'd be happy to try it. It just has to do what I need it to do is all and it has to be secure. Thank you all for your help in this matter so far!

:KS

When using OpenSSH for SFTP you should only need to do the following (unless you want to limit access or do some other fancy stuff).  In filezilla use the following settings for your connection:

Host: the address of your host (e.g. 192.168.1.10, server.com)
Port: the port you are running SSH on (e.g. 22)
Username: obvious
Password: obvious

Done, Filezilla will figure the rest out, as long as you are using Filezilla (others may work too) it will be transparent to users as to what you are using to support File Transfers.

---

### Post by AdamShumpisxXx on 2010-03-12
Thanks to everyone who helped! I have my SFTP server running now and all is well! I just need to figure out how to jail the user I set up to it's home directory. It's a bit tough...suggestions?

Thanks again! :KS

---

### Post by doogy2004 on 2010-03-12
> **AdamShumpisxXx said:**
> Thanks to everyone who helped! I have my SFTP server running now and all is well! I just need to figure out how to jail the user I set up to it's home directory. It's a bit tough...suggestions?

Thanks again! :KS

What version of Ubuntu are you running?  I ask this because the version that I am currently running (8.04) does not support jailed SFTP.  Any of the new versions should support this feature.

Here is a very good tutorial [http://adamsworld.name/chrootjailv5.php](http://adamsworld.name/chrootjailv5.php)

---

### Post by cdenley on 2010-03-12
> **doogy2004 said:**
> What version of Ubuntu are you running?  I ask this because the version that I am currently running (6.06) does not support jailed SFTP.  Any of the new versions should support this feature.

Here is a very good tutorial [http://adamsworld.name/chrootjailv5.php](http://adamsworld.name/chrootjailv5.php)

8.04, the current LTS release, doesn't either.

---

### Post by doogy2004 on 2010-03-12
> **cdenley said:**
> 8.04, the current LTS release, doesn't either.

I put the wrong version in for my server, I changed it.  I didn't bother looking at the title of the thread either when I asked what version.

Given that there should be no problem chrooting in Ubuntu 9.10.

---

### Post by AdamShumpisxXx on 2010-03-12
I'm running Ubuntu Server 9.10 Karmic Koala. I'll give your link a shot. Wish me luck!

Thanks a lot! :popcorn:

---

### Post by AdamShumpisxXx on 2010-03-12
No luck with that link. I don't think it applied to my OS or even my OpenSSH version. Thanks anyways...

---

### Post by bombird on 2010-03-13
> **AdamShumpisxXx said:**
> No luck with that link. I don't think it applied to my OS or even my OpenSSH version. Thanks anyways...

I think [Wing FTP Server]("http://www.wftpserver.com") can solve your problem,  it is very powerful and easy to use,  and provides 30-day trial version.

You can have a look at here: [http://www.wftpserver.com]("http://www.wftpserver.com")

---

### Post by ipng on 2010-03-13
I would strongly recommend ProFTPd, with LAMP and Webmin. That's what i'm using, and it works just fine!

You might find this guide usefull - [http://www.howtoforge.com/proftpd_mysql_virtual_hosting](http://www.howtoforge.com/proftpd_mysql_virtual_hosting)

With a ProFTPd-server you kan lock the users of ProFTPd into their own home directories, so they cannot browse all your "private" stuff (and each others, of course) :popcorn:

---

### Post by yug23 on 2010-04-02
Just to add to this thread, I am basically trying to do the same thing, I have set up SFTP and it's all running smoothly with the users Chrooted etc. But I can't work out how to add a folder to the users' home directories by means of a symlink.

I can add the symlink but they are denied access to the folder to which the symbolic link points, unless I make that folder chmodded to 777 which I believe is an unnecessary security risk.

Is there any way to allow the members of the sftpusers group download access to this particular folder without chmodding it to 777?

Thanks for any advice.

---

### Post by cdenley on 2010-04-02
> **yug23 said:**
> Just to add to this thread, I am basically trying to do the same thing, I have set up SFTP and it's all running smoothly with the users Chrooted etc. But I can't work out how to add a folder to the users' home directories by means of a symlink.

I can add the symlink but they are denied access to the folder to which the symbolic link points, unless I make that folder chmodded to 777 which I believe is an unnecessary security risk.

Is there any way to allow the members of the sftpusers group download access to this particular folder without chmodding it to 777?

Thanks for any advice.

What happens when you chmod it to 755?

---

