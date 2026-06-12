---
title: "how to set up simple online file storage? (my own personal &quot;cloud')"
date: 2009-03-11
forum: Server Platforms
---

### Post by jespes on 2009-03-11
I’m brand new to Linux -- yesterday I installed it for the first time ever! -- and very excited to learn. 
Here’s the first thing I want to do:
I want to set up my Ubuntu 8.10 (Desktop Edition) machine as a simple “online file storage” server. Basically I want to be able to access its hard disk, over the internet, from my Mac laptop when I'm on the road. Call it my own personal "cloud storage." 
Is this doable? If so, what software do I need to install and set up, and how should it be configured? 
Reminder: I'm a NOOB, so I might be asking this the wrong way!
 Any and all help is welcomed, especially advice tailored for a novice. Many thanks in advance.

---

### Post by Eviltechie on 2009-03-11
Ok, I recommend you use ssh, with your favourite sftp client.

To install ssh, type...
```
sudo apt-get install ssh
```

Then make sure that you forward port 22 in your router to your computer. (the server)

Then pull up a terminal in either your mac or linux computer and type...
```
ssh username@xx.xx.xx.xx
```

Make sure that you replace username with your linux username and xx.xx.xx.xx with the IP of your linux computer. (remember to use your WAN ip when not on your home network)

If it prompts you to accept a key, and then a password it worked. You now have shell access on your computer. You just need to find a sftp client for a mac. (there may be one built in, I don't know)

Also, make sure that you chose a really strong password, with lots of letters and numbers and symbols. Otherwise you will be hacked, and nobody wants that. I would also recommend you secure ssh further, but I don't know how to do that.

---

### Post by mrsteveman1 on 2009-03-11
Macs come with the commandline sftp client i use it all the time, but there is also sshfs and macfusion, both work pretty well. 

You could also setup lighttpd with webdav which should be mountable on any current OS but also available from inside a browser.

---

### Post by jespes on 2009-03-14
SSH works perfectly -- thanks! 

Before going live I want to make it very secure. If anyone has recommendations on how to secure a ssh connection like this, i'd love to hear. Thanks again.

---

### Post by HermanAB on 2009-03-14
Uhmmm,  the Secure Shell *is* secure.

More information here:
[http://www.openssh.com/](http://www.openssh.com/)

Cheers,

Herman

---

### Post by jespes on 2009-03-14
re xxx Secure Shell *is* secure xxx

apologies, i'm probably not asking the right way.  basically, are there other steps i can/should should take to minimize the chance someone can access my little file server, once it's exposed to the wilds of the internets?

naturally, i'll give it a complicated password. are there other things i can/should do?  for instance does it help at all to use a different port rather than 22? etc? 

if you haven't guessed, you're dealing with a newbie! many thanks...

---

### Post by mrsteveman1 on 2009-03-14
Yes, use a different listen port, and disable root login in the ssh daemon (its an option in the config). Root login should be disabled by default but sometimes it isn't.

You can also restrict the IPs that are even allowed to connect to the sshd by using your router firewall or the /etc/hosts.allow and /etc/hosts.deny files.

It is a good idea to at least move the port, you will inevitably get random ssh login attempts or organized dictionary attacks. Those are not a big problem if you have a good password. Lately i've also seen my logfiles on various webservers i manage showing people trying to pass shellcode to the sshd, or rather what looks like shellcode. That could be a problem if they know an exploit, your password won't matter then. IP blocking would stop that sort of attack.

---

### Post by jespes on 2009-03-14
thanks ... how do i change port 22 to something else? when i try to change it in etc/ssh/ssh_config, it says i don't have the authority.

also,i don't see an option in that file to deny root login. 

am i doing this in the right place?

---

### Post by jespes on 2009-03-14
okay,
i looked at the "permissions' for the file "ssh_config" and it says i don't have edit privileges because i'm not the "root" user. how do i get root privileges?? i'm  logged in on an administrator's login (or so it appears to me). in fact, it's actually the only login on this brand-new install of ubuntu.

---

### Post by volkswagner on 2009-03-14
When you installed Ubuntu, you may have been asked to create a root password.  If not you can create or change it.  The first user created during the install, (you) is an administrator.

To change or set the root password

```
sudo passwd root
```

To run things with root permissions you can safely use sudo, "super user do once".

IE: to use nano to edit a config file

```
sudo nano config.file
```

To help secure ssh deamon you can use host.deny and host.allow.  Both are located in /etc.

---

### Post by jespes on 2009-03-14
nano! who knew.

perfect, works like a charm, many thanks. much to learn.

---

### Post by jespes on 2009-03-14
thank you, everyone, for your invaluable advice. i'm officially going live with my brand new ssh server, complete with ridiculously long/zany password, turned-off ssh root access,  and super-doublesecret (aka, not "22") port! it's all working (so far) like a charm and i feel like einstein's smarter cousin, thanks to your assists.

---

### Post by ad_267 on 2009-03-14
Do you have a static IP address for your home network? Otherwise how do you access your computer from the internet?

This is something I really have no idea about, but I'm interested to know what other people do because I'd find it useful to be able to have a similar setup. I've heard if you have a dynamic IP address there are some domain name services that will keep track of your IP.

---

### Post by jespes on 2009-03-14
i have a dynamic address. so i use dyndns.com (free service) to provide me with an unchanging address. setting that up took some head-scratching, especially because i'm new to linux.

 it boils down to this: you set up an account at dyndns.com to create a static domain name (for example, "yourname.dyndns.org"), and you point it to your dynamic home ip address. then, you download/install software onto your pc that automatically alerts dyndns whenever your dynamic ip address changes.

sounds simple, doesn't it? 

dyndns.com, explains how to install various flavors of this alert software. i used "ddclient" and it's working splendidly for me. however, i installed using the below terminal commands rather than trying to follow the THOROUGHLY BAFFLING INSTRUCTIONS i blundered into on dyndns.com and elsewhere. 

Here are the instructions i used to successfully get ddclient running:

help.ubuntu.com/community/DynamicDNS

these will walk you through the installation process using terminal commands.


okay let's recap, shall we?

(1) open an account at dyndns.com and create your "permanent " domain name (such as "your-name.dyndns.org") pointing to your "dynamic" home ip address (12.345.67.89).

(2) install ddclient on your home machine and get it running so that it will alert dyndns.com whenever your dynamic address changes (see above in this message thread)

(3) take a few more security steps, such as changing the default ssh port from "22" to something less obvious, like "56789" or whatever you prefer. and creating a triple-zany long password to hopefully thwart hackers.

---

### Post by ad_267 on 2009-03-14
> **jespes said:**
> i have a dynamic address. so i use dyndns.com (free service) to provide me with an unchanging address. setting that up took some head-scratching, especially because i'm new to linux.


Thanks for that detailed explanation. I'd like to get a subversion server working from home eventually so that looks exactly like what I need.

---

### Post by jespes on 2009-03-15
so, i'm still doing research on setting up the most secure possible SSH server for myself. I've now stumbled across references to authenticated "public keys" (as opposed to a regular password) but after much reading i still don't understand how i would implement this. does anyone know a simple step-by-step guide? many thanks.

---

### Post by mrsteveman1 on 2009-03-15
Most ISPs will give you a static IP for another $5 a month, it tends to be worth it. And you can get a domain for another $5 and get free DNS service for the domain from zoneedit. :)

---

### Post by windependence on 2009-03-15
> **jespes said:**
> re xxx Secure Shell *is* secure xxx

apologies, i'm probably not asking the right way.  basically, are there other steps i can/should should take to minimize the chance someone can access my little file server, once it's exposed to the wilds of the internets?

naturally, i'll give it a complicated password. are there other things i can/should do?  for instance does it help at all to use a different port rather than 22? etc? 

if you haven't guessed, you're dealing with a newbie! many thanks...

Some people will disagree with me but changing the port does little if anything to protect you from script kiddies. They are scanning all the lower ports anyway and will quickly find out what port you are using. Doing this only creates a hassle for you. If you want to take some better steps, you should set up passwordless access and disallow root logons. More info here:

[http://fosswire.com/post/2008/01/bullet-proof-your-server-2-ssh/](http://fosswire.com/post/2008/01/bullet-proof-your-server-2-ssh/)

-Tim

---

### Post by hyper_ch on 2009-03-15
changing port will not enhance security (just result in less log entries)

---

### Post by jespes on 2009-03-15
tim,
 thanks for the link-- exactly what i needed. gonna go the passwordless route.

---

### Post by mrsteveman1 on 2009-03-15
> **windependence said:**
> Some people will disagree with me but changing the port does little if anything to protect you from script kiddies. They are scanning all the lower ports anyway and will quickly find out what port you are using. Doing this only creates a hassle for you. If you want to take some better steps, you should set up passwordless access and disallow root logons. More info here:

[http://fosswire.com/post/2008/01/bullet-proof-your-server-2-ssh/](http://fosswire.com/post/2008/01/bullet-proof-your-server-2-ssh/)

-Tim

That link recommends changing the port, and it is a good idea. Run it in the 30000-65535 range. While it is true that sometimes they scan port ranges to find open ports, they tend to hit the standard ports first. Most attacks by the beginner script kiddies can be stopped like this.

And if you block by IP with a whitelist it isn't possible for them to connect in any meaningful way regardless of port :)

---

### Post by hyper_ch on 2009-03-15
yet it will not imrpove security at all.. as said, the only thing that will be improved is you get less log entries.

If your password is too weak anyway to run ssh on default port then you have other issues.

---

### Post by mrsteveman1 on 2009-03-15
Passwords are not the only attack, if there is an exploit in the ssh daemon it could be directly compromised. SSHD runs as root by default, so it is a good target, and on port 22 an easy one to find.

Security is multi-faceted, you can't rely on changing ports alone but it is a good idea. For a home machine it might not matter so much, but on the machines i manage attacks are frequent, anything that can help reduce the attack surface is worth doing.

Again if you know where you will be connecting from, do IP blocking.

---

### Post by hyper_ch on 2009-03-15
and script-kiddies won't exploit 0-day weaknesses and those that do exploit those things will scan you completely.

Again, moving ports grants no additional security.

---

### Post by mrsteveman1 on 2009-03-15
> **hyper_ch said:**
> and script-kiddies won't exploit 0-day weaknesses and those that do exploit those things will scan you completely.

Thats why you block IPs that port scan you :)

---

### Post by jespes on 2009-03-15
thanks, i now have a thorough grounding in the issues regarding whether to switch away from port 22! 

and my decision is ....drum roll, please .....

i've switched ports! reasoning: (1) it's easy to do in my simple, one-server-one-laptop setup, and (2) if it cuts out some basic attacks, that's either a good thing, or a wash, but it's not a bad thing.

i've also done the other basic things that people  advise:
-verrry long/tricky password
-protocol 2
-no root login
-etc etc etc (the various others listed here and there)  

i cant seem to get the public/private key thingy working just yet. but give me time.

---

### Post by papenpj on 2009-03-16
I am also trying to do the same thing, sortof. Ideally I want to find a program that allows me to have web-based ftp access.  This is because I would like to have access to all my files without needing anything special installed on the computer im using.

The method I use for remotely logging in is having the following line
"AllowUsers *@192.168.0.* [my non-root username]@*"
in the config file
/etc/ssh/sshd_config


That way, any user on my local network can SSH into the computer, but only the special name i designated has access to the computer from anywhere. Which is important to me because the computer is running completely headless in my basement.

Also, because you said your new, I highly recommend you never make any major network changes while your in a different location, I learned that the hard way. Such as reassigning port 22 to a new port #.

Another important question, how is the IP address set on your local network? do you have the ability to use static DHCP, because nothing is more annoying than your router changing the IP address of your computer so none of your forwarding works.

---

### Post by mrsteveman1 on 2009-03-16
> **papenpj said:**
> I am also trying to do the same thing, sortof. Ideally I want to find a program that allows me to have web-based ftp access.  This is because I would like to have access to all my files without needing anything special installed on the computer im using.

You would probably be happy with webdav (for various values of "happy"). It isn't too hard to setup, there are tutorials all over the forum and the web for ubuntu specifically.

You should be able to access your files, with authentication, from any web browser. And it is even possible to upload files with the web browser too, though i believe that takes a bit more work.

---

### Post by MrWES on 2009-03-16
Installing and running denyhosts is a good idea too if your forwarding port 22

[http://ubuntuforums.org/showthread.php?t=450853]("http://ubuntuforums.org/showthread.php?t=450853")

and rate limits on brute force attacks:

[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/]("http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/")

I have both setup and as nothing is 100%, it surely helps.

Bill

---

