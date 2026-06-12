---
title: "nervous webserver owner"
date: 2007-09-03
forum: Server Platforms
---

### Post by gishaust on 2007-09-03
hi everyone

I have had my new webserver online(very very exciting). I have spent two days making sure that  it is secure(i think). Other than checking the logs and the webpage are there any other checks I should do now it is online.

very excited gishaust.

---

### Post by kwambus on 2007-09-03
Just keep an eye on things generally.

Personally I use OSSEC-HIDS [http://www.ossec.net/en/attacking-loganalysis.html](http://www.ossec.net/en/attacking-loganalysis.html) on all  web servers I create. 

The OSSEC software enables logging of the system files amongst other features, and can send you emails when different events happen within the system. I find it tremendously useful, and gives good peace of mind.

There is a Ubuntu install "how-to" at: [http://ubuntuforums.org/showthread.php?t=213445](http://ubuntuforums.org/showthread.php?t=213445)

---

### Post by dantrevino on 2007-09-03
> **gishaust said:**
> hi everyone

I have had my new webserver online(very very exciting). I have spent two days making sure that  it is secure(i think). Other than checking the logs and the webpage are there any other checks I should do now it is online.

very excited gishaust.


I suggest subscribing to one of the security alert bulletins.  You should be watching for application vulnerabilities that may be reported.

[http://www.us-cert.gov/](http://www.us-cert.gov/)

dan

---

### Post by gishaust on 2007-09-03
Thankyou  for responses

when you use OSSEC do you use the web gui.
The  [www.us-cert.gove](www.us-cert.gove) was great thanks

Gishaust

---

### Post by HermanAB on 2007-09-04
Hmm, change SSH to run on a non-standard port, use looooong random passwords of 9 characters or more, set iptables to throttle SYNs, then relax and enjoy it!

Cheers,

H.

---

### Post by KCPokes on 2007-09-04
> **HermanAB said:**
> Hmm, change SSH to run on a non-standard port, use looooong random passwords of 9 characters or more, set iptables to throttle SYNs, then relax and enjoy it!

Cheers,

H.

Always good advice, if its possible.  The need for SSH, most times, is for remote administration, but depending on where you are coming from the ability to use non-standard ports isn't an option.  For example, from work I have a very limited number of ports that they allow out of the corporate firewall, thus I'd suggest that you verify whether ports are available to you prior to making your changes.  Nothing like making the change at home and finding out that you cannot perform remote administration!  

Just something to think about.

---

### Post by Brazen on 2007-09-04
> **KCPokes said:**
> Always good advice, if its possible.  The need for SSH, most times, is for remote administration, but depending on where you are coming from the ability to use non-standard ports isn't an option.  For example, from work I have a very limited number of ports that they allow out of the corporate firewall, thus I'd suggest that you verify whether ports are available to you prior to making your changes.  Nothing like making the change at home and finding out that you cannot perform remote administration!  

Just something to think about.

If port 22 is blocked, you could always try changing it to port 21.  FTP is almost ALWAYS allowed out of corporate networks.

---

### Post by KCPokes on 2007-09-04
> **Brazen said:**
> If port 22 is blocked, you could always try changing it to port 21.  FTP is almost ALWAYS allowed out of corporate networks.

Good advice.  I tend to use standard ports and remap them, at my firewall, to a different port on the backend.  That allows me more access with limited ports, plus being able to remap allows me to use a telnet port for SSH access to a second server on my internal network.

---

### Post by gishaust on 2007-09-05
thank you guys 

I have not set up ssh yet as I am a very new. I know it exist but not confident. Someone in an other forum was say that you set this up though apache. But linux does not need apache to set up ssh. I don't know!!!!!

 I like the idea of using a different port using iptables. I have to read some more on ssh I know it is like a tunnel that I have to log into. but I have no idea how the second computer logs in. Is it through a webpage????

So I have is right syns, is where someone fills the memory of the webserver.  Is this correct? and how do I set the firewall up to stop it

Gishaust

---

### Post by Brazen on 2007-09-05
you connect to ssh from a second computer using an ssh client, such as Putty on Windows.  When you connect, you basically have a command line just like if you were sitting at the server.  It has nothing to do with Apache or webpages.

---

### Post by gishaust on 2007-09-05
Brazen

Thanks for clearing that up.
What is the program you use in the ubuntu client?

Gishaust

---

### Post by lamnk on 2007-09-05
> ssh yourusername@yourhostname -p port
Cant be simpler than that :D

---

### Post by stuartt on 2007-09-06
to install ssh:
```
sudo apt-get install ssh
```

to use a port besides the default port 22 ( this is for security and to reduce the amount of log data recorded by failed ssh hacking attempts):
```
sudo nano /etc/ssh/sshd_config
```
that opens the ssh config in the easy to use nano text editor, next you change the setting for the port to some unused port... I like 2247. It is located at the following spot in your sshd_config:
```
# What ports, IPs and protocols we listen for
Port 22
```

As a bonus security treat, disallow root login via ssh (forcing any ssh user to authenticate during their session) by setting the following in sshd_config:
```
PermitRootLogin no
```

Editing in nano is a snap and the perfect new user text editor. Navigate with the arrow keys. The possible commands are at the bottom of the screen ( the ^ symbol means ctrl) but you just need to know how to save (ctrl-o) and how to quit (ctrl-x).

---

### Post by gishaust on 2007-09-06
thankyou everyone 

I am a much more relax. ssh looks like some thing I am going to try that way I can access it from any where in the world. 

As for the tutorial on ssh I am going  to add it to server in the next couple of days. I like how you access ssh but stil have to sudo to get any where in the box.

Gishaust

---

