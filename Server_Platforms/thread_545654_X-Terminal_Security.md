---
title: "X-Terminal Security"
date: 2007-09-07
forum: Server Platforms
---

### Post by Darren996 on 2007-09-07
Hi,

I want to run X-terminal so a group people can log in and help out with my server cause I am no linux genius.  Ubuntu server x64 is up and running but  it doesn't come with a desktop for security reasons.  Anyway if I block 6000 tcp at the firewall and let people VPN into my router so they are inside the firewall is that going to be secure enough? :biggrin:

Thanks,
Darren

---

### Post by Dark Hornet on 2007-09-07
I am not quite sure I understand you....if you allow someone to VPN in to help set up your server---I suppose they will have complete control over your system, so the issue is more of "do you trust the people helping you".  Personally, I would never do this, but I am pretty anal and don't like anyone else "playing" around in my systems....hope this helps, and good luck.

---

### Post by Darren996 on 2007-09-09
I guess I watched too much Barney and Friends as a child... :biggrin:

Back to the original question.  I have a firewall router with VPN support.  I have to configure the router with the logins and passwords for VPN.  I have one graphic card in my server.  In my firewall 6000 tcp is not open.  If my clients login through VPN first then start X that should be secure no?

---

### Post by koenn on 2007-09-09
can you rephrase your original question ? I'm completely in the dark as to what you're trying to do. 
If you just want people to login frome remote, can't they just use ssh ? why do you mention X-terminals ? and how are your friends gonna "start X" if, re your OP, the system doesn't have a desktop ? 
I think you're leaving out way too much info here.

---

### Post by Darren996 on 2007-09-09
Hi Koenn

I want to be able to give my administrators an X desktop.  How would one do that securely?  From what I understand the password for an X session goes clear text and is therefore insecure much like ftp.  If I require my admins to login through VPN first would that mean the password never goes across the internet in the clear.

Is there some other remote desktop software I can use?

Can I use SSH to start an X terminal securely?  Could you point me to a tutorial for that if there is such an document?

Thanks,
Darren

---

### Post by bodhi.zazen on 2007-09-09
I am not sure if I understand either.

ssh is a terminal connection.

ssh -X will forward x apps, if tht is what you want.

ssh -x will forward a desktop, but it is slower then VNC.

You can tunnel VNC over ssh as well. This will give you a desktop and users will need to enter 2 passwords, one for ssh and one for the VNC session.

You can increase ssh security in a number of ways.

[uwiki]SSHHowto[/uwiki]
[uwiki]VNCOverSSH[/uwiki]
[uwiki]AdvancedOpenSSH[/uwiki]

---

### Post by Darren996 on 2007-09-09
Hi bodhi.zazen,

I've just heard X was insecure, Ubuntu server doesn't come with X for "security" reasons or at least that's what the first post I came to said.  Like I said I'm no Linux genius that's why I am asking these questions.

Thanks for the links.

Thanks,
Darren

---

### Post by koenn on 2007-09-09
There's a number of ways that you can allow other users to remotely access your computer, from remote shells to individual (GUI) applications to complete remote desktops. 
here's a small overview : [http://users.telenet.be/mydotcom/howto/linux/xremote.htm](http://users.telenet.be/mydotcom/howto/linux/xremote.htm)

It's a very good idea to do this through a VPN. As explained in the web page I referred to, you can also export X applications through ssh, so you won't have to expose too many services/ports to the internet or worry about clear text passwords. 

But, as mentioned before : you do have to worry about giving root powers to others.

---

### Post by bodhi.zazen on 2007-09-09
> **Darren996 said:**
> Hi bodhi.zazen,

I've just heard X was insecure, Ubuntu server doesn't come with X for "security" reasons or at least that's what the first post I came to said.  Like I said I'm no Linux genius that's why I am asking these questions.

Thanks for the links.

Thanks,
Darren

Yea, X can have a number of problems, and you are asking a number of good questions. On desktops we all accept those risks and I would not say they are overly high (IMO at least).

First, in terms of security, X can have a number of holes, but that is not why we do not run X on a server. We like to save resources on the server for serving and are comfortable with the CLI to do so. Of course the lack of a gui can slow some crackers, but only if they are unfamiliar with the cli.

The second question is regarding remote access. ssh is the most common route and is reasonable secure. If you are forwarding single apps, it is reasonable to ssh.

If you are forwarding an entire desktop, VNC (tunneled over ssh) is the way to go (or FreeNX).

If you want to remotely admin a server look at something like webmin.

koenn, and others, can also offer good advice soI would advise you check out his link as well.

---

### Post by Darren996 on 2007-09-09
Thanks for the info.  I like the OpenSSH for windows.  Looks like I can run my X terminal software on my XP laptop and still be secure. Awesome!

Here's what I am doing.  I am putting up a LAMP server for a website.  The server I built is a Core 2 Quad with 4Gb of ram and 6 mirrored hard drives.  One mirror drive is for the OS, one for the file share and one for the MySQL database.  The only ports that'll be open are HTTP, SSH, SSL (maybe) and DNS I think.  

My website gets about 3000 page hits a day.  I have business FIOS with a static IP and a 5Mbps uplink.

I should still have a little horsepower left over for a X desktop shouldn't I?   Maybe I should stick with Webmin.  Don't I need a SSL certificate for Webmin to be really secure? 

Thanks,
Darren

---

