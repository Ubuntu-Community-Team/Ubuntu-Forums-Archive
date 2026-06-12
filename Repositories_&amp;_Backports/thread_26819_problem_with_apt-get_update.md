---
title: "problem with apt-get update"
date: 2005-04-14
forum: Repositories &amp; Backports
---

### Post by bkj on 2005-04-14
I hope this is the right forum for this - I cannot get apt to connect to the marillat repositories -  I have no trouble connecting to them in debian sarge, but ubuntu will not seem to connect.  setting http_proxy and ftp_proxy (i am behind a firewall) in .bashrc and /etc/apt/apt.conf in different ways does not seem to work, nor does using the sarge apt.conf work when in ubuntu.

this is the readout from sudo apt-get update:

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
[ etc. etc. ]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg
Could not connect to ftp.nerim.net:21 (62.4.16.82), connection timed out
Err [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg

and if I let it go it will eventually fall over.  synaptic gives a similar problem, even though i have set up the proxies there and it works in sarge.  i would really like to use ubuntu, but have no idea why I cannot get this to work.  can anyone offer me a clue on this?  this is the first time i have posted to a forum, as i can usually figure things out given long enough.  cheers.

---

### Post by Leif on 2005-04-14
Have you added nerim.net to your keychain ? If you haven't, please search the forums for marillat and gpg.

---

### Post by lao_V on 2005-04-14
Type the following in terminal

 ```
gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 1F41B907
gpg --armor --export 1F41B907 | sudo apt-key add -
sudo apt-get update
``` 

to get the key

---

### Post by bkj on 2005-04-14
thanks - i will give this a shot and get back to you.

---

### Post by Melvin on 2005-04-14
[QUOTE=bkj]thanks - i will give this a shot and get back to you.[/QUOTE]
 I seem to have a slightly different problem (maybe related?).

When performing apt-get update, the process goes through but with an error message:

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Anyone has any clues?  I have added the repositories according to the UbuntuGuide.org,

---

### Post by bkj on 2005-04-15
Thanks for the GPG tip, but I am pretty sure my problems are not to do with gpg - the problem, as far as I can tell, is to do with using my http_proxy settings for the ftp_proxy, which I have to do, since behind this firewall there is not an ftp proxy that I am aware of.  Setting the ftp proxy as "http://x.x.x.x:80" solves this in Debian (and all other deb based systems I have tried)- for the life of me I cannot tell why I cannot connect to ftp repositories in Ubuntu doing the same thing.  ubuntu is really slick, but I wish to connect to marillat etc. and cannot figure this out.  Any ideas? - in desperation I even searched for a http mirror of the marillat repository, but could not find one.  Thanks again.

---

### Post by bkj on 2005-04-15
Finally got it going - should anyone else have this problem I got around it by getting rid of /etc/apt.conf altogether and setting (just to be on the safe side) all of the following in ~/.bashrc:

HTTP_PROXY='http://x.x.x.x:80'
http_proxy='http://x.x.x.x:80'
FTP_PROXY='http://x.x.x.x:80'
ftp_proxy='http://x.x.x.x:80'
export HTTP_PROXY http_proxy ftp_proxy FTP_PROXY

now aptitude works, and I am getting (finally) the GPG error - but I know how to fix that so it is not a problem.  Cheers.

---

### Post by Melvin on 2005-04-17
[QUOTE=bkj]Finally got it going - should anyone else have this problem I got around it by getting rid of /etc/apt.conf altogether and setting (just to be on the safe side) all of the following in ~/.bashrc:

HTTP_PROXY='http://x.x.x.x:80'
http_proxy='http://x.x.x.x:80'
FTP_PROXY='http://x.x.x.x:80'
ftp_proxy='http://x.x.x.x:80'
export HTTP_PROXY http_proxy ftp_proxy FTP_PROXY

now aptitude works, and I am getting (finally) the GPG error - but I know how to fix that so it is not a problem.  Cheers.[/QUOTE]
 Care to share how you fix the invalid signature problem?

---

### Post by bkj on 2005-04-17
melvin - i have not fixed the bad-signature problem yet - i use linux at work, debian sarge, and have suse on another partition - wanted to make sure i could get ubuntu configured properly and doing all that i wanted it to before i took the plunge and replaced debian and suse with it - as i am not paid to do nerd stuff on my computer (i use linux because i refuse to use windows) this will probably take me a couple of weeks to do in bits and pieces during lunch breaks etc.- when i said i know how to fix it what i meant was that there are previous posts in this thread on fixing it, as well as how-tos etc - my problem was that i could not connect at all to ftp repositories.  will post again when i do fix this, but that could be any time in the next month - try the other how-to's on this if you need to solve it quickly.  cheers, brad. (ps - the bad-signature does not stop you installing stuff, just bugs you with error messages)

---

### Post by Morphius on 2005-05-03
I am also having this exact same problem. I need to install Kdevelop for a programming class and it doesn't show up in the apt-cache. I am trying to update the list and using the apt-get update command and I recieve the following error.

GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release: The following signatur es were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <f [email]tpmaster@ubuntu.com[/email]>
W: You may want to run apt-get update to correct these problems <-- please note the irony in this statement.

Does anyone know how to resolve this issue?

---

### Post by chrisf on 2005-05-04
Try this - it worked for me:

gpg --keyserver wwwkeys.eu.pgp.net --recv-keys 40976EAF437D05B5
gpg --armor --export 437D05B5 | sudo apt-key add -
sudo apt-get update

---

### Post by Morphius on 2006-04-26
Turns out that apt has issues when it tries to update but is not connected to the internet. To fix this I had to comment out all the lines in my sources.list file, apt-get update, then uncomment them and apt-get update. This has resolved this issue several times for me (My laptop's wireless drops sometimes so...)

---

