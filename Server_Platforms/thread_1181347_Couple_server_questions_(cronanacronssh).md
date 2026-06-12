---
title: "Couple server questions (cron/anacron/ssh)"
date: 2009-06-07
forum: Server Platforms
---

### Post by ooobooontooo on 2009-06-07
Hi,

I plan to run a server at home and connect to it from other places when I'm not around. Unfortunately, my home network is behind a NAT so it's not so easy to login (I also do not wish to get involved with 3rd party websites like dyndns). So, what I've set up to do is automate wakeup on my server every day use anacron to copy the exterior ip of my server to another server (with a static ip) that I trust. Unfortunately, I haven't actually tested this yet...and there are some questions that I had.

1. I'm using a rsa key with no password to automate the scp transaction (I may use the expect script later, but for now I'm just trying to get it work). Because I use anacron which is run by root, do I put the private key in the root directory or the user directory?

2. After I update my external ip address, I want my server at home to power down. For this I can use cron, and I wish to use the UTC standard to automate its shutting down. Is adding TZ=UTC in /etc/init.d/cron enough? (TZ wasn't defined in the cron environment to begin with...)

3. As I said before I copy the ip address to a server that I trust. However, I don't trust them completely. I know that anacron is run as root, so does that mean everything in the script that I wrote is run as root? If so, because I do some sshing and scping, is that unsafe? Should I try get the script to run as a user instead? ...How would I go about doing that?

Thanks for reading up til now and thanks in advance to answers.

---

### Post by LepeKaname on 2009-06-07
Instead of doing it through scp (and risk the security), why you don't create a PHP/(JSP or what ever) that will listen a GET parameter with your IP? you can save that ip in a file and then retrieved anytime.
In your home server, just call that page with wget and add your external IP.

---

### Post by ooobooontooo on 2009-06-09
> **LepeKaname said:**
> Instead of doing it through scp (and risk the security), why you don't create a PHP/(JSP or what ever) that will listen a GET parameter with your IP? you can save that ip in a file and then retrieved anytime.
In your home server, just call that page with wget and add your external IP.

That's really smart...Unfortunately, the guys who run the server probably won't let me use any of the port especially 80 (They run their own website). Also, I would like to know the answers to the questions above anyway. Nice idea though.

---

### Post by LepeKaname on 2009-06-09
> 1. I'm using a rsa key with no password to automate the scp transaction (I may use the expect script later, but for now I'm just trying to get it work). Because I use anacron which is run by root, do I put the private key in the root directory or the user directory?

At your root directory. 

> 2. After I update my external ip address, I want my server at home to power down. For this I can use cron, and I wish to use the UTC standard to automate its shutting down. Is adding TZ=UTC in /etc/init.d/cron enough? (TZ wasn't defined in the cron environment to begin with...)

If you are executing the script as root, and you want to power down your computer right after sending the IP, why don't you just add "halt" or "shutdown now" at the end of your script?

> 3. As I said before I copy the ip address to a server that I trust. However, I don't trust them completely. I know that anacron is run as root, so does that mean everything in the script that I wrote is run as root? 

In your server, yes.

> If so, because I do some sshing and scping, is that unsafe?

Theoretically is safe (because it uses SSH public/private keys) if you keep your private keys for yourself. You will have access to their server but not otherwise.
However, I usually dislike the idea to connect to an external server (not inside your local network) using a root user.

> Should I try get the script to run as a user instead? ...How would I go about doing that?

Read this: [http://ubuntuforums.org/archive/index.php/t-312328.html](http://ubuntuforums.org/archive/index.php/t-312328.html)

There is something I don't get... you don't trust them but still you want to use their server and you don't trust well known services as "no-ip". I use "no-ip" for my personal server and I have been using it since 3 years ago, and I have never had any problem (attack or anything). It is faster and easy to setup. Even Ubuntu has a no-ip installation package in their repositories.

---

### Post by ooobooontooo on 2009-06-09
Thanks once again. :D

> There is something I don't get... you don't trust them but still you want to use their server and you don't trust well known services as "no-ip". I use "no-ip" for my personal server and I have been using it since 3 years ago, and I have never had any problem (attack or anything). It is faster and easy to setup. Even Ubuntu has a no-ip installation package in their repositories.

I can see how you would think that. For me it was just a combination of wanting do it by myself so I could learn a bit more and the fact that if I did suspect an attack from the guys running the servers I could just go to them and have a shouting match (bit hard to yell at no-ip/dyndns). But once again thanks for the answers

---

