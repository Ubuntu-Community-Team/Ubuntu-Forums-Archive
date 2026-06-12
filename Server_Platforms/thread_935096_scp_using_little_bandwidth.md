---
title: "scp using little bandwidth"
date: 2008-10-01
forum: Server Platforms
---

### Post by bbarrons on 2008-10-01
I just started to use a script to copy a backup from one email server to another. I use ssh and scp to copy the file but it only seems to ttasnfer at about 39kb. Both systems are on dsl and should be able to transfer at at rate of at least 256kb. IS there someplace that throttles the bandwidth that I can change? here is the code that I have used before
scp -l 256 "zcs-5.0.10_GA_2609.UBUNTU8.20080922131729.tgz" [email]me@ms1.mail[/email]server:Desktop/ 
The mailserver is the only computer on the dsl router.
I can use the server to download from the net at rates as high as 312kb
same condition at my home server. download speeds are at 312kb. but I get only 39kb when transferring either way from either server.
can anyone help ?
thanks
 Bill B

---

### Post by bbarrons on 2008-10-01
Did I post to the wrong category of the forum?

---

### Post by Sef on 2008-10-02
1) Moved to server platforms.

2) What version of Kubuntu do you have?

3) Are you using 4.1, or 3.5.9,or other desktop?

---

### Post by bbarrons on 2008-10-02
kubuntu 3.5.9

---

### Post by lykwydchykyn on 2008-10-02
It's possible that scp may be slowed down by having to encrypt the data before sending it.  How powerful is your computer and server?

Just a thought.

---

### Post by bbarrons on 2008-10-02
both servers are the same. dual 2.8 xeon with 4 gigs of ram. scsi drives. both servers are connected to a dsl line that is 3mb's down and 500kb up. Both servers can download a torrent or other file from the net at up to 312kb. I did try just a simple transfer of a zip file that was only 10 mbs and could still only get 39kb on the transfer going either way. I was hoping that there is a setting somewhere that throttles this and I could up it. I did try to use -l 256 before the transfer in the hopes that it would push it. I am out of ideas and places to look.

---

### Post by lykwydchykyn on 2008-10-02
I know I can get more bw than that out of scp on a vanilla ubuntu install, so either something got changed on your servers, or it's an external problem.  The only configs I know of that would affect scp directly would be /etc/ssh/ssh_config (for the client) and /etc/ssh/sshd_config (for the server).

Have you tried rsync instead to see if there is any difference?

---

### Post by bbarrons on 2008-10-02
I havent tried that yet. I will give it a try to see if I can get more out of it than scp. I will also look at ssh config to see if I can bump it there thanks for the suggestions.
 Bill B

---

