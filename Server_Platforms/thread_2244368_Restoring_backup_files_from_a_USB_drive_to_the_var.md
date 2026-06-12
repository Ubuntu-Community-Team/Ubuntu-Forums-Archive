---
title: "Restoring backup files from a USB drive to the /var/www/ location"
date: 2014-09-15
forum: Server Platforms
---

### Post by irv on 2014-09-15
I have all my backup files on a external drive which is connected to my server via USB. I mounted it and it is mounted in /media/usb/
Now I want to copy all the files and directories with all there files and directories to my internal hard drive.

My source and destination are as such: from /media/usb/Server backup 9-13-14/var/www/ to my destination /var/www/
I am not sure about the command I should use. If I am in my source like:
irv@wabasha-server:/media/usb/Server backup 9-13-14/var/www$ 
What command would I need to type to get everything in one copy.

---

### Post by TheFu on 2014-09-16
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) will help you immensely. Skim the 1st 100 pgs quickly.

Before answering the question, which file system is on the USB drive? Did it retain all the proper file owners, groups, and permissions? Did it retain any ACLs attached to any files as well?  Were their any hard or soft links used in that part of the file system?

If all you did was copy everything off ... great - you have the data, but that isn't enough to be a "backup" on Linux.  This is why using a real backup tool for backups is important and having a basic understanding of ownership, groups and file permissions.  That link will help gain the understanding.

So - I'll assume that your USB drive has a Linux file system and has retained all the permissions, owner, groups and might contain symbolic links. 

**sudo rsync -avz "/media/usb/Server backup 9-13-14/var/www/" /var/www/ **
That should do it.  Quotes matter for file paths that have spaces - better to avoid that next time.
If the USB storage is NTFS or FAT-whatever - that command probably won't do what you need.

Oh - and if you have a database driven website - none of this will help restore the DB.

Unrelated, but I lived on the Mississippi and Missouri rivers a few times over the years. ;)

If you want a backup tool that DOES handle all the things I''ve mentioned ... do a little forum searching, homework and ask some questions.

---

### Post by irv on 2014-09-16
I guess I am still in the learning stages when it come to servers. This is my first time trying to run a text based server from a remote box. (headless server).
My backup is on a fat32 USB drive and yes the files were just copied over from the servers www directory so no symbolic links or no retained ACLs.
All I want to do for now is get all the files and directories back over to the /var/www/ on the server for now.
Will the command you gave do that?
Thank you for the information on the backup restore.

---

### Post by TheFu on 2014-09-16
We are all in the learning stages - always, forever.

The link to that book above has most answers you need for now in a single place. The PDF version is free, no hassle, download. It has a section on **rsync**, but you can always RTFM which is already put on your system when rsync is installed too - **man rsync**  If you plan to be a server admin - reading manpages is mandatory.

Why not just use **cp**? cp doesn't handle some special files in the desired manner. If your directory doesn't have those files - fine.  Going to non-linux file systems will loss those anyway.

---

### Post by nerdtron on 2014-09-16
```
**sudo rsync -avz "/media/usb/Server backup 9-13-14/var/www/" /var/www/ **
```

This will do the work for you. However, as you have mentioned, since this is and external usb drive with fat32 partition, the permissions on the external will also be copied. I'm guessing they are all 777 permission which is not quite good.
BTW, why use -z for compression when this copy is only on local folder?

The normal copy command will also do the work for you. (although it won't show the progress)
```
cp -R /media/usb/Server backup 9-13-14/var/www/* /var/www/*
```

When it finishes, to check the permission/ownership, post the output of the following command so that we can check:
```
ls -lah /var/www/
```

---

### Post by irv on 2014-09-16
It's still working but here is a readout of what I get with ls -lah /var/www/

> irv@wabasha-server:/var/www$ ls -lah /var/www/
total 299M
drwxr-xr-x 38 root root 4.0K Sep  8 20:55 .
drwxr-xr-x 13 root root 4.0K Sep 15 09:22 ..
-rwxr-xr-x  1 root root 9.4M Dec  4  2009 12 How Great Thou Art.m4a
-rwxr-xr-x  1 root root 804K Jul  4  2010 14140.jpg
-rwxr-xr-x  1 root root 3.8K Jun 13  2012 Angrybirds.png
-rwxr-xr-x  1 root root  44M Aug  8  2008 ann.mpg
drwx------  2 root root 4.0K Sep 16 18:39 apache2-default
drwx------  2 root root 4.0K Sep 16 18:39 audio
drwxr-xr-x  2 root root 4.0K Aug  2  2013 Audio_Files
drwxr-xr-x  2 root root 4.0K Feb 12  2013 Audio writings by Irv Risch
-rwxr-xr-x  1 root root 445K Jun 13  2012 Bejeweled.png
drwxr-xr-x 53 root root 4.0K Oct  2  2013 BibleTeaching
-rwxr-xr-x  1 root root 1.5M Apr  5 17:33 Capture2.PNG
drwxr-xr-x  6 root root 4.0K Mar 19  2013 Christian Audio Writings
-rwxr-xr-x  1 root root  58K Jan  4  2008 Corn_Flakes.jpg
-rwxr-xr-x  1 root root 1.4M Aug 21  2008 crossbib2.tif
-rwxr-xr-x  1 root root 204K Aug 21  2008 CrossBible3.jpg
-rwxr-xr-x  1 root root  47K Sep 16  2009 Dazed & Confused.jpg
drwxr-xr-x  2 root root 4.0K May 22  2013 Downloads
drwx------  2 root root 4.0K Sep 16 18:39 ebay
drwx------  2 root root 4.0K Sep 16 18:39 ebay_files
drwx------  2 root root 4.0K Sep 16 18:39 ebooks
drwx------  2 root root 4.0K Sep 16 18:39 epub files
-rwxr-xr-x  1 root root 2.6K Jun 13  2012 EvernoteWeb.png
drwxr-xr-x  2 root root 4.0K Feb 27  2012 FC_epub_files
-rwxr-xr-x  1 root root 209M Jun 27  2008 For Graham.avi
-rwxr-xr-x  1 root root 126K Jun 13  2012 fsbank.png
-rwxr-xr-x  1 root root 2.5K Jun 13  2012 GoogleCalendar.png
-rwxr-xr-x  1 root root 1.8K Jun 13  2012 GoogleDocs.png
-rwxr-xr-x  1 root root 3.0K Jun 13  2012 GooglePlayBooks.png
drwxr-xr-x  2 root root 4.0K Jan 30  2013 Grahams
-rwxr-xr-x  1 root root  93K Sep 24  2009 Health Care Quiz.pdf
drwxr-xr-x  2 root root 4.0K Sep 15 09:22 html
drwx------  2 root root 4.0K Sep 16 18:39 html_files
-rwxr-xr-x  1 root root 1.9K Jun 13  2012 Humana.png
drwxr-xr-x  2 root root 4.0K Jun 27  2011 Hymns
-rwxr-xr-x  1 root root   45 May 10  2008 index.bak
-rwxr-xr-x  1 root root   45 Jul  9  2009 index.html-bak
-rwxr-xr-x  1 root root  177 Feb 18  2014 index.html.bk
-rwxr-xr-x  1 root root 337K Jul 28  2008 irv072808-2.JPG
-rwxr-xr-x  1 root root  44K Apr 22  2009 irv072808-4.JPG
-rwxr-xr-x  1 root root 597K Jan 10  2008 Irv-Nancy.JPG
-rwxr-xr-x  1 root root  45K Jan 10  2008 Irv-Nancy_small.JPG
-rwxr-xr-x  1 root root 3.4M Jul 31  2008 Irvs-server.jpeg
-rwxr-xr-x  1 root root 866K Jul 31  2008 Irvs-server-small.jpeg
drwxr-xr-x  2 root root 4.0K Oct 11  2012 Josiah
drwxr-xr-x  2 root root 4.0K Jun 25  2011 Kevin-Corrie-wedding
drwx------  2 root root 4.0K Sep 16 18:39 liveoffice
-rwxr-xr-x  1 root root  30K Mar  6  2010 MACKI_CH.png
-rwxr-xr-x  1 root root 3.8K Jun 13  2012 Mahjong.png
-rwxr-xr-x  1 root root  12K Aug 21  2008 masthead-products.jpg
drwxr-xr-x  5 root root 4.0K Apr 16 20:16 Music
-rwxr-xr-x  1 root root 306K Jan 10  2008 My Family.JPG
drwxr-xr-x  2 root root 4.0K Aug 27  2007 My Stuff
-rwxr-xr-x  1 root root 1.1M Oct 25  2008 Nancy_Irv_36.jpeg
-rwxr-xr-x  1 root root 3.2M Sep 16  2009 Nancy w_the moonbat eyes.mp3
drwxr-xr-x  2 root root 4.0K Jul 11  2009 Nautilus Scripts
-rwxr-xr-x  1 root root 2.2M Oct  8  2009 OBAMA MONEY!.mp3
drwxr-xr-x 44 root root 4.0K Sep 16 20:07 Old_Writings
drwxr-xr-x 18 root root 4.0K Feb 25  2013 Old Writings with Audio Files
-rwxr-xr-x  1 root root 6.2M Oct  7  2009 One_Pair_Of_Hands.wmv
-rwxr-xr-x  1 root root 9.4M Jul 31  2008 Outlook.pdf
drwx------  2 root root 4.0K Sep 16 18:39 owncloud
-rwxr-xr-x  1 root root 2.8K Jun 13  2012 Pandora.png
-rwxr-xr-x  1 root root 486K Jul  5  2013 phone.PNG
drwx------  2 root root 4.0K Sep 16 18:39 php
-rwxr-xr-x  1 root root 3.4K Jun 13  2012 Picasa.png
drwx------  2 root root 4.0K Sep 16 18:39 podcast
drwx------  2 root root 4.0K Sep 16 18:39 Romans-Videos
-rwxr-xr-x  1 root root 2.3M Oct  8  2009 Saftey_101.wmv
-rwxr-xr-x  1 root root  73K Dec 13  2007 scanModem.gz
-rwxr-xr-x  1 root root 6.8K Apr 25  2009 Screenshot-HPLIP Status Service.png
-rwxr-xr-x  1 root root 289K Jul 28  2009 Screenshot.png
drwx------  2 root root 4.0K Sep 16 18:39 Screen_Shots
drwx------  2 root root 4.0K Sep 16 18:39 Scripts
drwx------  2 root root 4.0K Sep 16 18:39 Scripture
-rwxr-xr-x  1 root root 6.1K Jan 14  2008 Sullie-small.jpg
-rwxr-xr-x  1 root root 146K Aug 25  2012 system-ready.ogg
-rwxr-xr-x  1 root root 276K May 21  2008 test.ogg
-rwxr-xr-x  1 root root   34 Jul  9  2009 test.php
-rwxr-xr-x  1 root root   20 Feb 18  2014 testphp.php.bk
drwx------  2 root root 4.0K Sep 16 18:39 The-Bible
-rwxr-xr-x  1 root root  51K Jan  6  2010 The wisdom of God.pdf
-rwxr-xr-x  1 root root  16K May 23  2007 turkey_small.jpg
-rwxr-xr-x  1 root root 3.2K Jun 13  2012 TV.png
drwx------  2 root root 4.0K Sep 16 18:39 Ubuntu
-rwxr-xr-x  1 root root 621K Jun  6  2012 Ubuntu Display.png
drwx------  2 root root 4.0K Sep 16 18:39 videos
-rwxr-xr-x  1 root root 665K Jun 14  2012 wallpaper01.png
-rwxr-xr-x  1 root root 3.1K Jun 13  2012 WeatherBug.png
-rwxr-xr-x  1 root root 3.2K Jun 13  2012 WebcamToy.png
drwx------  2 root root 4.0K Sep 16 18:39 Websites
drwx------  2 root root 4.0K Sep 16 18:39 zip


---

### Post by nerdtron on 2014-09-17
Hmmm.. seems about right. Only thing is the directories are only readable by the root user. And the /var/www/ should be owned by the www-data user.

Anyway since it is working as expected, then you don't have to do anything, of if this is a public website, you definitely need to correct the permissions and ownerships.

---

### Post by irv on 2014-09-17
It does look good and I have been changing the rights because I can get into my files in the www directory form a browser like I did before. Also I can't FTP into my server from FileZilla. Here is what I am seeing if I use the domain name or my static ip address.

[ATTACH=CONFIG]256495[/ATTACH][ATTACH=CONFIG]256496[/ATTACH][ATTACH=CONFIG]256497[/ATTACH]

---

### Post by nerdtron on 2014-09-17
You transferred to a new server right? Is the IP of the server you are connecting the correct one?
What version of Ubuntu is this? 12.04 or 14.04.

Also try "chmod -R a+r /var/www" to eliminate possible read permission issue on the folders.

EDIT: Could not connect to server. Is SSH server process installed and running on the server?

---

### Post by irv on 2014-09-17
> **nerdtron said:**
> You transferred to a new server right? Is the IP of the server you are connecting the correct one?
What version of Ubuntu is this? 12.04 or 14.04.

Also try "chmod -R a+r /var/www" to eliminate possible read permission issue on the folders.

EDIT: Could not connect to server. Is SSH server process installed and running on the server?

To answers your questions.
Yes, I transferred to a new server. with the same name. The old server is no more. I believe the the ip address I am connecting to is correct.
all pings from server.
> If I ping 192.168.1.105 I get
64 bytes from 192.168.1.105: icmp_seq=3 ttl=64 time=0.027 ms

> if I ping wabasha-server I get
64 bytes from wabasha-server (127.0.1.1): icmp_seq=1 ttl=64 time=0.038 ms

> If I ping my domain "wabasha-server.net" I get
64 bytes from ftth-1-13.hbci.com (205.243.122.13): icmp_seq=1 ttl=64 time=2.48 ms


My old server was 12.04 and when I went to up grade it to 14.04 it messed it up.

Now my new server setup is 14.04 with no desktop so everything is running Okay.

I can ssh into my server so I believe it is setup, but I can't get FTP to work right. I need this to upload files to my server.

Is there a way to ssh into my server over the internet? I tried doing it using my domain name it and it did not work.

And if I try this 

> irv@irv-Q500A:~$ ssh irv@205.243.122.13
ssh: connect to host 205.243.122.13 port 22: Connection refused
irv@irv-Q500A:~$ 
It will not work.

---

### Post by nerdtron on 2014-09-17
> My old server was 12.04 and when I went to up grade it to 14.04 it messed it up.

Note that /var/www/ on apache2 of 12.04 is not /var/www/html/ on apache2 of 14.04. So I guess you need to work out first this problem to let your website show up (even on your local network).

Now on the ssh and ftp issue. Since you can ssh to the server (using your local network) then ssh-server is running. If you want to ssh from the outside internet, we have to troubleshoot your firewall settings first, on your server and on your network devices.

What is the output of "sudo netstat -tulpn" on the ubuntu 14.04 server? Did you modify any iptables settings? What is output of "sudo ufw status"?
On your network, did you make any changes that restricted access to ssh port 22?

On a computer using the outside internet, try this on the command line and let's see the output. This will give us some more ideas on what is happening between your computer and the server.
```
ssh -vvv irv@205.243.122.13
```

---

### Post by irv on 2014-09-18
> **nerdtron said:**
> Note that /var/www/ on apache2 of 12.04 is not /var/www/html/ on apache2 of 14.04. So I guess you need to work out first this problem to let your website show up (even on your local network).

Now on the ssh and ftp issue. Since you can ssh to the server (using your local network) then ssh-server is running. If you want to ssh from the outside internet, we have to troubleshoot your firewall settings first, on your server and on your network devices.

What is the output of "sudo netstat -tulpn" on the ubuntu 14.04 server? Did you modify any iptables settings? What is output of "sudo ufw status"?
On your network, did you make any changes that restricted access to ssh port 22?

On a computer using the outside internet, try this on the command line and let's see the output. This will give us some more ideas on what is happening between your computer and the server.
```
ssh -vvv ssh irv@205.243.122.13
```

> irv@wabasha-server:~$ sudo netstat -tulpn
[sudo] password for irv: 
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      1017/mysqld     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      631/smbd        
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      1249/perl       
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      707/vsftpd      
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      872/sshd        
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      631/smbd        
tcp6       0      0 :::139                  :::*                    LISTEN      631/smbd        
tcp6       0      0 :::80                   :::*                    LISTEN      1094/apache2    
tcp6       0      0 :::22                   :::*                    LISTEN      872/sshd        
tcp6       0      0 :::445                  :::*                    LISTEN      631/smbd        
udp        0      0 0.0.0.0:45048           0.0.0.0:*                           654/dhclient    
udp        0      0 0.0.0.0:68              0.0.0.0:*                           654/dhclient    
udp        0      0 192.168.1.255:137       0.0.0.0:*                           959/nmbd        
udp        0      0 192.168.1.105:137       0.0.0.0:*                           959/nmbd        
udp        0      0 0.0.0.0:137             0.0.0.0:*                           959/nmbd        
udp        0      0 192.168.1.255:138       0.0.0.0:*                           959/nmbd        
udp        0      0 192.168.1.105:138       0.0.0.0:*                           959/nmbd        
udp        0      0 0.0.0.0:138             0.0.0.0:*                           959/nmbd        
udp        0      0 0.0.0.0:10000           0.0.0.0:*                           1249/perl       
udp6       0      0 :::42281                :::*                                654/dhclient   

I didn't modify any iptables settings.

i> rv@wabasha-server:~$ sudo ufw status
Status: inactive

I am not sure about restricted access to ssh on port 22. I don't have it set in my port setting on my router. 
[ATTACH=CONFIG]256518[/ATTACH]

Output from "ssh -vvv ssh irv@205.243.122.13"

> irv@wabasha-server:~$ ssh -vvv ssh irv@205.243.122.13
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
ssh: Could not resolve hostname ssh: Name or service not known


---

### Post by irv on 2014-09-18
> Output from "ssh -vvv ssh irv@205.243.122.13"

irv@wabasha-server:~$ ssh -vvv ssh irv@205.243.122.13
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
ssh: Could not resolve hostname ssh: Name or service not known

Sorry the above was tried from my lan not over the Internet.
I will be on the road later today and I will give it a try then and repost it.

[COLOR="#FF0000"]EDIT:[/COLOR] Okay, I ran the command again to ssh to my server over the Internet and got the same message.
I am having other issues not http-ing to website and not able to FTP to domain name. I believe the problem is with the host name i check with the hosting server to make sure the hostname was pointing to the ip address 205.243.122.13 and it was. I am thinking it has something to do with one of my config files on my server but I am not sure which one and where. Before my old server when down everything was working so I know the problem is not on my router either. When I get back home I will check line 19 in the /etc/ssh/ssh_config file to see if that is where the problem is.

---

### Post by irv on 2014-09-18
> Note that /var/www/ on apache2 of 12.04 is not /var/www/html/ on apache2 of 14.04. So I guess you need to work out first this problem to let your website show up (even on your local network).

I forgot to say, that the apache test page did show up when I went to the URL "wabasha-server.net" but I deleted the directory "html" because I didn't want a webpage. On my old server I just wanted the list of files and directories. most were audio file and I could just select them and play them in a browser. But for some reason they do not show up even if I type them in.

---

### Post by irv on 2014-09-18
I have been moving around today so I tried this command again:
```
Output from "ssh -vvv ssh irv@205.243.122.13"
```

This time I got this:
> irv@irv-Q500A:~$ ssh -vvv ssh irv@205.243.122.13
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ssh [208.69.32.145] port 22.
debug1: connect to address 208.69.32.145 port 22: Connection timed out
ssh: connect to host ssh port 22: Connection timed out


---

### Post by nerdtron on 2014-09-19
Sorry it was a typo on my part. It should be:
```
ssh -vvv irv@205.243.122.13
```

Alright, from your router port forwarding, there is no entry there for port 22. You should setup port 22 on the router to forward to the server. Then try again.
Testing to see if port 22 is open. Try this from the outside network
```
 telnet 205.243.122.13 22 
```

Then try ssh again:
```
ssh -vvv irv@205.243.122.13
```

---

### Post by irv on 2014-09-19
I am still home but I did the ssh -vvv irv@205.243.122.13 to see what would happen but couldn't get on the server. Then I open port 22 and everything works. I can even use
```
ssh -vv irv@wabasha-server.net
```
and can get on my server. I will try it later on from outside my network and will post what happens.

---

### Post by irv on 2014-09-19
Okay, I am going to mark this thread solved because I have things working now.
I am on the road and the ssh to server is working.  the command ssh -vv irv@server name is working from outside my network. and I have all my files back on my server.
Thanks to all who helped.

---

