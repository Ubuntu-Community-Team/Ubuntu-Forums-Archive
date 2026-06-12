---
title: "How can I be attacked?"
date: 2010-03-03
forum: Server Platforms
---

### Post by any.linux12 on 2010-03-03
Hi!

I will soon acquire a fixed IP and I have some concerns about being attacked. I don't want to attack nobody but how can you attack someone with a linux system? what are the vulnerabilities?

Thanks!

---

### Post by KiLaHuRtZ on 2010-03-03
You'll just see people pecking at port 22...we call those script kiddies...

Look at fail2ban.

---

### Post by nerdy_kid on 2010-03-03
<edit> didnt notice this was in the server section, and as i dont know what im talking about ill shutup ;)

---

### Post by any.linux12 on 2010-03-03
> **KiLaHuRtZ said:**
> You'll just see people pecking at port 22...we call those script kiddies...

Look at fail2ban.

fail2ban looks cool! is there any port else like the smtp and the http port? because I will have an email and a website server

---

### Post by KiLaHuRtZ on 2010-03-03
See what you have running/open...

```
netstat -l
```

---

### Post by NullHead on 2010-03-03
Yeah, fail2ban or denyhosts will work fine. 

Also, SSH keys and disable root login will help.

---

### Post by stlsaint on 2010-03-03
apache has some nice mod security tools as well.

---

### Post by Sherman.Boyd on 2010-03-03
Having a static IP doesn't make you any more vulnerable to attack than when you had one that changed from time to time.  In any case you want to have a firewall device at the perimeter of your network.  This can be a router, or a linux box with at least two nic cards.  The important thing is to have this device sit between your network and your internet connection. 

Be very stingy about what ports you open up on the router.  You can think of each port as a gate to your network, and the application behind it as the gatekeeper.  Let's say you have port 80 open with Apache behind it and some PHP application.  You also have port 22 open.  An attacker is going to have to either hack port 22 (SSH: very unlikely) or port 80, which is a more tempting target.

Now that firewalls are pretty common, and most home users don't forward ports you are most likely to get hacked via your web browser, or some crappy web plug in.  I'm not going to mention any names ADOBE FLASH.  You may want to lose certain plugins like Acrobat, and anything else you can live without.  You also might want to stay off questionable sites such as: porn, warez and digg.com.

SUMMARY:

Make sure all your programs that are behind an open port are up to date, and configured securely.  Make sure any program that reaches out into the internet and brings back content is up to date and cross your fingers.  Don't download warez or install anything from an untrusted source.  Don't pickup thumb drives off the street and connect the to your computer.  Make sure your wireless is encrypted.

Good luck.

---

### Post by Vunutus on 2010-03-03
> **KiLaHuRtZ said:**
> You'll just see people pecking at port 22...we call those script kiddies...

Look at fail2ban.

Or just set it to some random high port. I got dozens of not hundreds of failed SSH login attempts per day when I had my SSH server on port 22. I got tired of the log spam and set it to some random port and I don't think I've got a single hit on it yet.

---

### Post by Sherman.Boyd on 2010-03-03
If you don't need to login remotely keep port 22 closed off from the internet.  No log spam then.

---

### Post by Hathadar on 2010-03-03
I have just installed ubuntu server 9.10.
I enabled openSSH and connect to via putty.
The only protection I have noticed is it requires my username and password.
Assuming there is nobody listening to clear text packets, is there anything I need to worry about?

---

### Post by ushills on 2010-03-04
i would suggest using keys to login via ssh and disable plain logins, there is good community documentation on how to do this.  +1 for fail2ban as well.

---

### Post by R.Bucky on 2010-03-04
*2 Venutus - I too had SSH operating on port 22 for a couple of days. My server was getting beat up. Since changing to a non-standard port for SSH, I have yet to receive a single attempt in the last year. Fail2ban is excellent, but simply changing your port will solve 99% of your problems. Also, if you are uber parnoid, check out knock'd.

---

### Post by Sporkman on 2010-03-04
As far as ssh, changing the ports is a good idea as then you'll know when somebody is really trying to break in as opposed to being bombarded with automated attempts.

Another way to limit ssh vulnerability is there's a way to limit the rate of login attempts via iptables, for example:

[http://hostingfu.com/article/ssh-dictionary-attack-prevention-with-iptables](http://hostingfu.com/article/ssh-dictionary-attack-prevention-with-iptables)

---

### Post by miguel.antonio.168 on 2010-03-05
[SIZE=3]i agree with bucky and sporkman, you change the default port of your ssh server and then generate a key. 

if you are running other server applications that are only for internal or personal use, you are better off with only the ssh server running and open with non-default port open, you can still have access with your other server application ports by ssh client redirection or port forwarding when you are connecting to your server from a remote location.

if you have remote sites connecting to your server and manageable in numbers - you can have all your port close and instead setup a local ssh server on their site, initiate the connection from your end and use reverse port forwarding with matching key in order for the remote sites to have access to your server applications, this way nobody can just take a peek of your services and make sure that only those remote offices that you are connected have access to your system.

theres no such thing as a foolproof system, the least that we can do is to mitigate the risk - by employing non-default settings for any application service for a start and if possible limit to a single open service port that will provide access to the rest of your applications.

good luck
[/SIZE]

---

### Post by tlsarles on 2010-03-05
I might also mention that if you are behind a firewall/router, then you odds of having an issue are pretty low to begin with unless you have port forwards set up.

---

### Post by Sherman.Boyd on 2010-03-05
I disagree with anyone who states that changing your port number makes you more secure.  It will help with reducing log spam, but it is simple to identify your ssh port regardless of what you change it to.  You may confuse someone that has no idea of what they are doing, but those people are never going to hack past your SSH daemon unless you chose a really stupid password.

Concentrate your efforts on things that actually make you more secure, an SSH key is a good idea as long as you set a password as well, and using iptables to limit remote access to known good ip addresses.  

Still if you don't want to change your port number and just use password authentication you are perfectly secure as long as you choose a good password.  In my mind that means 14 characters with non-alpha chars.

---

### Post by Sporkman on 2010-03-05
> **Sherman.Boyd said:**
> I disagree with anyone who states that changing your port number makes you more secure.  It will help with reducing log spam, but it is simple to identify your ssh port regardless of what you change it to.

It makes you slightly more secure IMO, in that it's less likely for an automated attack to succeed, and more likely that you'll spot actual hacking attempts (without all the noise from the automated ones in your logs).

---

