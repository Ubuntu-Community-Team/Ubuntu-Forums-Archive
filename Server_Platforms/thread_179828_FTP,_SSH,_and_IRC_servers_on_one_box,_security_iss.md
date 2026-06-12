---
title: "FTP, SSH, and IRC servers on one box, security issues abound"
date: 2006-05-20
forum: Server Platforms
---

### Post by cleverselfreferentialname on 2006-05-20
I have a box which I use at my desktop, which has grown to serve other purposes, such as an FTP, SSH, and IRC server for my circle of friends., due to lack of funding in regard to the purchase of a second, dedicated box.

One fellow within said circle is a little more security literate than the others, and as such, has found a number of problems with my implementation. He has managed to drop a shell in the FTP server and run it, as well as spawn one with vim. Not that I don't trust him, I'd just like to patch some holes in my implementation. How I've got it set up now, people connect to the SSH daemon, and from there run irssi, and connect to a local IRC server. 

I'd prefer to keep this implementation, because it allows me to use IRC daemons without SSL support and still have a secure setup. If possible,  I'd like it if, upon login, irssi could be started automatically, without fear of any attacks. Some other concerns are the use of forkbombs as a DoS attack, as well as gcc to compile something destructive. A way to encrypt FTP connections would be much appreciated also.

My FTP daemon is proftpd, my SSH daemon is opensshd, and my IRC server was a little perl hack my friend wrote.

---

### Post by Azrael on 2006-05-21
It doesn't seem to make much sense to run a seperate ftp daemon on your box; sshd has sftp ([http://en.wikipedia.org/wiki/SSH_file_transfer_protocol]("http://en.wikipedia.org/wiki/SSH_file_transfer_protocol")) functionality enabled by default! Windows clients can then use WinSCP ([http://winscp.net/eng/index.php]("http://winscp.net/eng/index.php")) to connect to you and Ubuntu users can connect straight out of gnome (Places > Connect to server.. > SSH).

Check [http://www.seifried.org/lasg/users/]("http://www.seifried.org/lasg/users/") for some info on how to limit user resources.

As for irssi, I dunno, but a simple shell script should do.

---

### Post by cleverselfreferentialname on 2006-05-21
Thanks a lot man.

---

