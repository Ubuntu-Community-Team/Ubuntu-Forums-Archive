---
title: "Reccomend FTP Server"
date: 2007-01-05
forum: Server Platforms
---

### Post by weaver4 on 2007-01-05
I have been using Cerurbus FTP server under windows for our lightweight FTP server. 

I would like to get one up and running on ubuntu.

What FTP server would people recommend?  I would like a gui to set up the users and such, but it is not an absolute requirement.

I would like something that is easy to set-up.

Thanks,

---

### Post by play0r on 2007-01-05
if you're comfortable with the terminal (or are willing to become comfortable), i would suggest glftpd; [http://www.glftpd.com/](http://www.glftpd.com/)
it's very flexible & configurable. it runs in a chroot environment, so it's relatively secure in the overall scope of things. 
there's lots of useful external add-ons & scripts, if you're into that kinda thing. 
also, installation is a breeze if you rtfm.

ez,
play0r

---

### Post by Epica on 2007-01-05
give proftpd a try [http://www.proftpd.org]("http://www.proftpd.org")
(note you may have to enable extra repositories for this one to work).

I found it reasonably easy to configure and theres plenty of documentation for it.

It doesn't have a gui by default but gproftpd is a graphical frontend for it.

---

### Post by sailingboarder on 2007-01-05
another really good ftp server is vsftpd
to install it, all you have to do is run the command ```
sudo apt-get install vsftpd
```

---

### Post by dannyboy79 on 2007-01-05
if you're trying to make it so that you alone can access files on your box than an ftp server is not needed. just run a ssh server and retrieve files using scp I believe it's called. this way your traffic is encrypted also. there's even a free version for windows, winscp382. I use it all the time. otherwise if you need to allow friends to download and upload files from your server than go with proftpd, there is an awesome guide by frodon in these forums. it's not hard to cofigure because frodon has made a how-to even my grandma could follow. good luck

---

### Post by weaver4 on 2007-01-17
I'm from the windows world and these ftpservers really confuse me.

I just want to set up a list of users, with their password and what directory/permissions they have access to (in a ftp-root directory).  

I don't want to set these people up for user accounts on my system.  I just want for them to have restricted access to some directories on the server.

Some of these FTP servers get so twisted with Unix security that it is very hard for a newbie to set them up.

Any help would be appreciated.

---

### Post by Parama on 2007-01-17
I know only too well how you feel about the complexity of *nix security if you are used to Windows. 
However, if you run a 'sudo aptitude install proftpd' and a 'sudo /etc/init.d/proftpd start' you should be up and running in a minute. 

The ProFTPD is pretty fast and somewhat light. And then it has nice features such as virtual users and the ability to individualize everything from just client IP.

Further reading: [https://help.ubuntu.com/community/ProFTPD](https://help.ubuntu.com/community/ProFTPD)

---

### Post by Aberrix on 2007-01-17
Another vote for Proftpd

---

### Post by Brazen on 2007-01-17
vsftpd is pretty much the standard.  It's faster and simpler than Proftpd.  The only reason a person would go with Proftpd is for the extra features BUT you can do pretty much anything in vsftpd that you can do in Proftpd using external tools.

---

### Post by weaver4 on 2007-01-18
Well I ended up using proftpd.  I used gproftpd to set it up and then made some minor modifications to the configuration file manually and I was done.

It was pretty easy, I would recommend it to any newbies (like myself) to Linux who want to set up a ftp server.

---

### Post by Mirrorball on 2007-01-19
Another vote for vsftpd. If you want them to have restricted access to a directory, create the user with that directory as their home and turn on the chroot_local_user setting. At least that's what I did in my newbieness.

---

### Post by Parama on 2007-01-20
> **Brazen said:**
> vsftpd is pretty much the standard. 
As is ProFTPD ;) 
> **Brazen said:**
> It's faster and simpler than Proftpd.
The difference in speed is (to my experience) completely depending on the setup. I've seen a lot of vsftpd's running slower than many ProFTPD setups (with the disk and CPU speed taken into count).
> **Brazen said:**
>  The only reason a person would go with Proftpd is for the extra features BUT you can do pretty much anything in vsftpd that you can do in Proftpd using external tools.
I'll have to somewhat disagree with you on that. 
Firstly vsftpd is not necessarily more secure than ProFTPD. Secondly ProFTPD has both a simple default setup (as hinted earlier in this thread) and it doesn't lack any features should you ever need them :)
I started out using vsftpd on both Trustix Linux 3 and Fedora and moved on to ProFTPD because the vsftpd installation coudn't do any of the things it promised it could and it made some weird things in the logs. Later I moved on to Ubuntu because Trustix also promised it could something that it can't and Fedora is slow. IMHO both vsftpd and Trustix are good examples of *incompatibility*.

---

