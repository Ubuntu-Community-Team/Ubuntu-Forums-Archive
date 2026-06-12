---
title: "Copy files SSH"
date: 2012-02-10
forum: Server Platforms
---

### Post by benpack101 on 2012-02-10
As you may or may not have heard, HP is testing its new Cloud Service. I am using the beta. Either way that means I have access to a few of their servers to use myself. The recommended way to connect is through ssh. They use a private key to connect to the server instances.

My question is how do I move a file from my local computer to a server?

I have seen this > scp /path/to/local/file [email]username@remote.host[/email]:/path/to/save/file/ but I am not sure how to include the private key (.pem).

I am running Ubuntu 11.10 and connecting to a server instance that is running 10.10.

Any and all help would be much appreciated.

Thank you.

---

### Post by collisionystm on 2012-02-10
> **benpack101 said:**
> As you may or may not have heard, HP is testing its new Cloud Service. I am using the beta. Either way that means I have access to a few of their servers to use myself. The recommended way to connect is through ssh. They use a private key to connect to the server instances.

My question is how do I move a file from my local computer to a server?

I have seen this  but I am not sure how to include the private key (.pem).

I am running Ubuntu 11.10 and connecting to a server instance that is running 10.10.

Any and all help would be much appreciated.

Thank you.


when you initiate an ssh session you will be asked to accept the key

I dont scp, i just rsync because I get better results

rsync -ra --progress <source> <destination>

rsync -ra --progress /home/myfiles user@hpcloudserver:/destination

---

### Post by benpack101 on 2012-02-10
> rsync -ra --progress <source> <destination>

My apologies but what exactly do I want to put as <source> and <destination>?

I understand the second step though.
> rsync -ra --progress /home/myfiles user@hpcloudserver:/destination


Thanks in advance!

---

### Post by collisionystm on 2012-02-10
> **benpack101 said:**
> My apologies but what exactly do I want to put as <source> and <destination>?

I understand the second step though.


Thanks in advance!

The 2nd step was just an example of what I mean by source and destination lol.

source = where the files are coming from

---

### Post by benpack101 on 2012-02-10
I am getting this error:

> 
Unexpected remote arg: user@hpcloudservice:
rsync error: syntax or usage error (code 1) at main.c(1232) [sender=3.0.8]

Hmmm...I tried using ip address and name of server, neither worked.

Thanks so much in advance!

---

### Post by collisionystm on 2012-02-10
replace
user@hpcloudservice:

with 

the username you have on your HP server and the IP you reach your server with

username@ipaddress

user@hpcloudservice was an example I made

---

### Post by benpack101 on 2012-02-10
Yes I know that, I just didn't want to write out the ip and such as you can understand.

---

### Post by collisionystm on 2012-02-10
Although... now that I think about it. Lets scratch this whole thing

Install Filezilla from the software center

Use that to connect to your server. The port you want to use is 22

---

### Post by benpack101 on 2012-02-10
Thanks! I have to go now but when I get back to it either tomorrow or Sunday I'm sure it'll work.

Thanks for all of your help!:)

---

### Post by collisionystm on 2012-02-10
> **benpack101 said:**
> Thanks! I have to go now but when I get back to it either tomorrow or Sunday I'm sure it'll work.

Thanks for all of your help!:)


No problem! Good luck :KS

---

### Post by benpack101 on 2012-02-12
Got it to work, I tend to try and stay away from gui (to become more and more comfortable with the terminal) but this worked and I was getting quite fed-up.

Thanks collisionystm! :KS

---

### Post by collisionystm on 2012-02-12
> **benpack101 said:**
> Got it to work, I tend to try and stay away from gui (to become more and more comfortable with the terminal) but this worked and I was getting quite fed-up.

Thanks collisionystm! :KS

Your welcome :D

---

