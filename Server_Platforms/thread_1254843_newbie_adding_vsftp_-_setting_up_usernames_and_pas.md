---
title: "newbie adding vsftp - setting up usernames and passwords"
date: 2009-08-31
forum: Server Platforms
---

### Post by krraleigh on 2009-08-31
I just added vsftp and I am trying to figure out how to setup usernames and passwords for each directory that I create on my virtual server so that I connect using filezilla ftp. I was looking at some of the articles out there and being rather new I am not making much progress.
 
NOTE: I tried to connect using fillazilla but the connection failed.
I used my username and password for connecting to my server via ssh. I think I read somewhere that I don't want that option engaged, but I wasn't to sure on the info.
 
Can anyone give me an idea of where to start?
thanx
Kevin

---

### Post by hessiess on 2009-09-01
Use sftp instead, if you can ssh, you can also sftp with no extra set-up and its also substantially more secure. And to block ssh shell log in see: [http://www.debian-administration.org/articles/94](http://www.debian-administration.org/articles/94).

---

### Post by krraleigh on 2009-09-04
I'm looking for sftp, but I don't see among my packages
the only thing I can find is:
libnet-sftp-ruby1.8 and according to the info it is an alpha
release which sounds pretty unstable.
 
One other thing; I am really new to all this so will there be
any docs that I can use to help me find my way around.
 
right now I am running ssh with the encryption and connecting
via putty on a win machine. I develop on win so I would like
to connect via winscm which I am told is pretty cool
 
can you advise

Kevin

---

### Post by krraleigh on 2009-09-07
Just found this article on proftpd
[http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server](http://ubuntuforums.org/showthread.php?t=79588&highlight=ftp+server)
 
I want to setup a web server for viewing https webpages and not a file server for the gen public to upload and download files. With this in mind can I modify these instructions for my ubuntu intrepid server in a secure manor?
 
Anyway I haven't been able to connect to my server and I am wondering if it is because I encrypted it for ssh access with public and private keys. It is the only thing that I have done that the tutorials don't show how to do, and the only reason I can think of that would prevent me from connecting.
 
With the above in mind how much risk will I generate if I install ssh without the encryption so that I can get my server up and running.
 
could really use some help here
been at it for over a week and I just can't find anything out there
 
thanx
kevin:confused:

---

### Post by hessiess on 2009-09-07
> 
I'm looking for sftp, but I don't see among my packages.


Its just part of openssh.

---

### Post by krraleigh on 2009-09-07
> **hessiess said:**
> Its just part of openssh.
 
O.K. that is good to hear. One down and a couple to go.
 
Would you be able to advise me on whether my ssh encryption is the cause of my failure to connect to my server? Or is that an entirely separate issue?
 
Kevin

---

### Post by cariboo on 2009-09-07
Ftp and sftp are two different protocols, the one has nothing to do with the other. I would suggest that you have a misconfiguration in your vsftp configuration file. I would aslo suggest changing to key based [ssh authorization]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys").

You can use Filezilla for sftp, it is free, and there are Windows and Linux clients

---

### Post by krraleigh on 2009-09-07
I failed to understand what you were saying when you said that all I needed was sftp. I didn't realize that I would be using the same settings for sftp as I did for ssh.
 
Once I changed my settings on winscm my sftp windows tool to match the ssh settings then I was able to connect the very first time.
 
The trick thing was that the setup article in the wiki had me change my ssh port to xxx so that the kiddies couldn't spend all day knocking on my door. Once I dialed it in then everything worked.
 
You gave me the answer I just had a few other pieces of information to put together so that the picture would clear itself up.
The article that finally plugged all the pieces together was:
[http://cloudservers.mosso.com/index.php/Secure_File_Transfer_Protocol_%28SFTP%29]("http://cloudservers.mosso.com/index.php/Secure_File_Transfer_Protocol_%28SFTP%29")
 
hats off to tech support over at rackspace and their wiki as well...
 
thanx
Kevin:popcorn:

---

