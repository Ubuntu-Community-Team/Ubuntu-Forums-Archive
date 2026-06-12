---
title: "Seahorse fails to synchronize with key servers"
date: 2012-05-10
forum: Security
---

### Post by Welly Wu on 2012-05-10
Hi. I have an ASUS N61JV-X2 notebook PC with 8 GB of dual-channel DDR3 PC-8500 SDRAM and an Intel 2nd Generation X25-M 160 GB SSD. I installed Ubuntu 12.04 64 bit LTS yesterday. I added hkp://pgp.mit.edu:11371 to my list of key servers in seahorse, but it can not connect with any of the key servers. It says that it couldn't connect with any of the servers and there is an internal server error. I enabled UFW firewall and I use GUFW to configure it so that it permits all outgoing traffic and it permits incoming FTP and SFTP traffic on ports 20, 21, and 22 for my VSFTPD server.

How do I synchronize and publish my keys to the key servers?

---

### Post by donsy on 2012-05-10
In UFW/GUFW did you allow out 11371/tcp?

Edit: oops, I just reread your post and see you're allowing all outgoing traffic.

---

### Post by ottosykora on 2012-05-10
well it should connect, but sometimes I also have to try 4-5 key servers until I get connection with one. That is why I have about 20 on some installs.

But believe or not, some keyservers can be called on port 80 too.
Try port 80 and see.

Otherwise many key servers have also web interface.

You can also send an e-mail to the key server:

send e-mail to:

[email]pgp-public-keys@pgp.mit.edu[/email] for example, in subject enter

get 0xF204AC51


and you are supposed to get one of my public keys



you can also send an e-mail to that server and in the subject HELP

This will send you back the whole instruction set for other functions.


see also : [http://www.pgp.net/pgpnet/email-help-en](http://www.pgp.net/pgpnet/email-help-en)

---

### Post by Welly Wu on 2012-05-10
I tried HTTP port 80 with all of the key servers and it still failed to synchronize and publish my keys. I have a Verizon FiOS fiber optic Internet network at home with the Actiontec MI424WR 802.11 B/G router and switch. I set the firewall to the default medium which blocks incoming traffic and it permits all outgoing traffic. I set my GUFW to permit some incoming traffic for FTP, SFTP, and Samba Server along with Samba Client and I permitted all outgoing traffic. It seems that I am not the only one with this problem. I want to synchronize and publish my keys to the MIT PGP key server specifically because I have already done this when I used to use Red Hat Fedora 16 64 bit GNU/Linux on my ASUS N61JV-X2 notebook PC a few days ago. I had the same problem, but I eventually got it to work in Red Hat Fedora. It looks like I should be able to make a connection with any key server in the world that I trust, but it keeps giving me an internal server error message.

What are my options?

---

### Post by rookcifer on 2012-05-10
> **Welly Wu said:**
> How do I synchronize and publish my keys to the key servers?

Just go to pgp.mit.edu with your browser and cut and paste your keys in the box.  It is easier than worrying with this, imo.  pgp.mit.edu will synchronize your keys with all the other keyservers (it might take a couple days tho).

---

### Post by Welly Wu on 2012-05-10
As I stated earlier, I have already uploaded my GnuPG public key to MIT's PGP key server. I did this several weeks ago. My current problem is that seahorse will not synchronize my other keys. It says that I have 10 keys that need to be published and synchronized, but it fails to connect to any key server.

What do I do to solve this problem?

Should I just go to the different key servers and upload my keys through the websites? I hope this will solve the problem with seahorse that I just described in due time.

---

### Post by ottosykora on 2012-05-10
> **Welly Wu said:**
> As I stated earlier, I have already uploaded my GnuPG public key to MIT's PGP key server. I did this several weeks ago. My current problem is that seahorse will not synchronize my other keys. It says that I have 10 keys that need to be published and synchronized, but it fails to connect to any key server.

What do I do to solve this problem?

Should I just go to the different key servers and upload my keys through the websites? I hope this will solve the problem with seahorse that I just described in due time.

you can use any key server, it is not much relevant as they are synched, ths may take some time, something like few minutes to 2 days is typical.
You can use any way of upload, the http, the e-mail or the webinterface. All is the same and all is going to the one big data base eventually.
Sometimes some servers might be difficult to reach, well in the case of mit.edu I seldom experienced it, but possible.

Here is the link for the mit.edu server web interface:

[http://pgp.mit.edu/](http://pgp.mit.edu/)




Q: what do you need 10 keys to be published? 

Bear in mind, that once you have published the keys, they are out and the only thing you are supposed to do if you do not want them is to revoke them.
So if you have just some 'test keys' or similar, better delete them locally so the servers are less cluttered.
And BTW, you do not need the upload any keys at all if you do not need them to be distributed. You can have your public keys stored locally and distribute them by mail or otherwise too.

---

