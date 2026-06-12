---
title: "Cant get FTP to work"
date: 2019-01-21
forum: Ubuntu/Debian BASED
---

### Post by jeddell on 2019-01-21
Hi All,

Im new to these forums so I apologise if this post is in the wrong place.

Ive been setting up a minecraft server using MineOS over Linux Lite. I have the minecraft server working fine and now im trying to get FTP working so I can manage the files. Normally I use Filezilla to do this. Ive installed vsftpd and I managed to get that working using some instructions (From Digital Ocean I think). And it worked....once. but the problem was I need access to /var/games/minecraft folder where the server files are located.

I set up a new user with 

```
adduser -d /var/games/minecraft newuser
```

adding a password

```
psswd newuser
```

I also have port 21 open on the linux firewall.

when I try to connect through filezilla, i get the error: [COLOR=#b22222]500 OOPS: cannot change directory:/home/rooftp/ftp

[/COLOR]I created the directory and the ftp opened up, but its not where I wanted the directory to be. I admit that the directory is pretty high up the tree but this ftp is purely a local setup. 

so Im now lost. any help would be appreciated.

I would also ask that you assume I know very little to nothing about Linux commands and basically follow the bouncing ball from websites. Please step through any explanations.

---

### Post by jeremy31 on 2019-01-21
Moved to Ubuntu/Debian based

---

### Post by HermanAB on 2019-01-21
You probably have multiple problems.  FTP uses port 21 to negotiate the connection which is then executed over a different (random) port.  Therefore you either have to disable your firewall completely, or ensure that a FTP tracker is enabled, or use 'passive' FTP.

Your FTP server may also have other configuration problems.  Here is a write-up of my own recent experiences with vsftpd:
[https://www.aeronetworks.ca/2017/02/simple-file-server.html](https://www.aeronetworks.ca/2017/02/simple-file-server.html)

There is some bolded text in that page that you should read.

---

### Post by jeddell on 2019-01-21
Did I mention that I know very little about linux commands (see the last sentence).  I'm sure your post means something to others, but I'm afraid I just shows me that you recorded your process. How you went about it is beyond me. I need help in what I should do to get my ftp to work.

---

### Post by TheFu on 2019-01-21
If this is on the internet, please don't use plain FTP.  Use **sftp** instead.  Why send your login credentials over the interent without any encryption at all?

Setting up sftp is trivial. **sudo apt install openssh-server fail2ban**  That's it.
From the client, use choose sftp for the connection.  I think filezilla supports this.  Any Linux file manager will using either sftp:// or ssh:// URLs.
If you want to make it more secure, don't use passwords, use ssh-keys.  Generate the keys on the client using ssh-keygen, then push the public key to the correct place on the remote server using ssh-copy-id.

After you have this working, you can purge vsftpd and tweak some of the ssh/scp/sftp server config for even better security. [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) - just moving to a non-default port will help greatly.  I use the router to handle this.
64001/tcp --> router --> 22/tcp --> sftp server
If you can't control the port forward+translation at the router, then you'll need to do it inside sshd_config and in the fail2ban settings.

Running a server like mindcraft means looking things up.

---

### Post by jeddell on 2019-01-21
OK.....Quick question....How does this resolve the issue I have currently? When I can get FTP to work, THEN I will deal with security. I did say this is purely a local setup.

Please to everyone who reads this....I come to these forums to learn how to resolve the issues I am having and hopefully learn a thing or two along the process. I fully acknowledge that the people responding to this know a lot more than I do. Its been very much my experience tho that many of you don't really know how to bring your language down to a level where noobs like myself can relate. This pretty much makes your posts useless to me.  Lets work to resolve the issue and question I asked earlier, and well take it from there.

If you want to resolve my issue with me through a live chat like discord. here is my server: [https://discord.gg/CHm9xE](https://discord.gg/CHm9xE) . I live on Australian Eastern Standard time (Brisbane). and I'm more than happy to go down that path.

---

