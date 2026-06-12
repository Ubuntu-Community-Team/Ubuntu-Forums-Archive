---
title: "Ubuntu Server 10.04 LTS First-time Setup"
date: 2010-11-29
forum: Server Platforms
---

### Post by ShadeS_07 on 2010-11-29
Hi peepz, it's my very first time to make a server type system... I've been looking for tutorials and guides for making one... about a month, I guess... So far, I've found one that I think would work best for this Ubuntu Server Edition I have here -- v10.04 LTS.

I haven't installed it yet though, but, I think that wouldn't be much harder than I'd expect. Anyway, the link for the "tutorial" for making/setting up and configuring a server based on Ubuntu Server Edition 10.04 is right here:

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2)

Now, before I try that tut, I wanna know if it's safe, and if it will give me a secured server, I mean not "secured" as in perfectly secured, but at least "decently secured" especially for a first timer like me. I don't wanna be exploited by "Black Hats" out there for being a newbie, if you know what I mean.... -_+

The purpose is, to learn / educate my self... might be for future use, perhaps I might make a "real" commercial server to earn more money, but for now, I'm in the "learning stage"...

For now, I'm staring with an ordinary PC with the following specs:

CPU: P4 + HT Technology; 2.80 Ghz
RAM: SD DDRAM; 1GB
GFX: NVIDIA GeForce FX 5200

HDD: [All IDE]
     PM: 80GB; WinXP
     PS: 40GB; Kubuntu 10.04 LTS
     SM: 40GB; Ubuntu Server Edition 10.04 LTS (See note)

CD/DVD ROM: SATA DVD RW

NOTE: Don't get confused with the specs and what I said earlier above that Ubuntu Server Edition is NOT yet installed... I am planning to install Ubuntu Server Edition 10.04 on my HDD Secondary Master.... Just to avoid confusion.... hehe -_+

So yeah, for now these are my questions:

1. ***Is the tutorial I found for making a server system (link provided above) is a good tut?***

2. ***What kind of server will I make from that tutorial?***

3. [B][I]Is it "decently secure"? (Not perfect, but sufficient to prevent my system from being hacked/cracked "easily") 
[/I][/B]
4. Assuming that I have already installed it (Ubuntu Server) on HDD secondary master (SM), which would then mean that I have two (2) "Desktop Systems": Win XP and Kubuntu 10.04 on HDD PM and HDD PS, respectively; and a "Server System" which is the Ubuntu Server Edition 10.04 on HDD SM, on a single system unit (SU)... If ever (EVER! ;)) I use Ubuntu Server (I booted it, and did some stuffs, configure, etc...) and suddenly, a hacker (black hat) / cracker got into my system while booted on Ubuntu Server, and exploited any possible vulnerabilities found, will it also affect my "Desktop Systems"? If I shut down my Ubuntu Server and go back to one of my "Desktop Systems" say, win XP, would the hacker be able to still do some "nasty" stuffs with my system for having had been able to hack / crack my system while booted on my Ubuntu Server? OR.. Let's say I am booted to my Ubuntu Server and then I encountered a hacker which then exploited my computer system including my other HDD's which contain my "Desktop Systems", (okay, here's the real question for number 4, I'm sorry for the long "scenario" I made... peace peepz... ^^) ***will it be a better idea to "disable" my "Desktop Systems" HDD's: PM (WinXP) and PS (Kubuntu 10.04LTS)?*** By "disabling", I mean by _unplugging the Molex power_ of my Desktop Systems HDD's so that it won't turn on at all whenever I turn on my computer... NOT just by disabling it in BIOS/CMOS Setup. So that leaves the Server System HDD turned on, and when I switch back to one of my Desktop Systems, say, Kubuntu 10.04, I would just shutdown my PC, plug the power back in and perhaps, might unplug the Server System HDD's power.

Heh, anyway I hope I made a good thread that is easy to understand. I'm trying to go for the detail so that you won't have problem(s) dealing with my situation, but, if you still have question, or anything that you could hardly understand, please ask question(s), and I'll answer back for clarification...

Thanks in advance and God bless all! :popcorn:

---

### Post by CharlesA on 2010-11-29
One word of warning is this:

Do not enable the root account, you can use ***sudo -i*** to get to a reoot prompt.

See here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also don't disable AppArmor. It's there for a reason.

There is more to security then that tutorial goes into. Using strong passwords and only running the services you require go a long way to keeping yer box secure.

With that said, I would strongly recommend against installing the FTP server, if you need to transfer files to/from the server, use sftp instead as it is much more secure.

---

### Post by ShadeS_07 on 2010-11-29
Oh, nice response... thanks... ^^

Uh, yeah, I thought about that AppArmor thing... And actually, I won't really disable it when I'm going to install this server system... I won't follow that step... Thanks for your valuable tips/advise btw...

Let me also add, I'd be using LXDE (Desktop Environment) for this server system, so it's not totally CLI... For some reasons, I'd like to install LXDE for my server system... Hehe... :popcorn:

---

### Post by CharlesA on 2010-11-29
Well, you'd be configuring it with ISPconfig wouldn't you?

---

### Post by ShadeS_07 on 2010-11-29
Yes. Would that be good? If not, how about Webmin? I think they're similar... or am I just confused? As far as I know ISPCFG and Webmin are used to configure a system (server?)... However, I read that they musn't be "used" at the same time... Hmmmm?

---

### Post by CharlesA on 2010-11-29
It's either one or the other, since they are both web frontends.

---

### Post by ShadeS_07 on 2010-11-29
Oh, so which one would you recommend?

---

### Post by CharlesA on 2010-11-29
I've not used Webmin in a long time, and I've never used ISPconfig. I have however, heard good things about it.

Use whatever you want, if you don't like it, you can always install something else.

---

### Post by abix_adam_pl on 2010-11-29
Webmin is good for configuring the server as server for one company file server, maybe mail server.

ISPConfig is for Hosting server.

So, you must decide, for what do you plan use the sserver.

Best regards, 
Adam

---

### Post by ShadeS_07 on 2010-11-30
Oh, I see... I am still currently learning about servers and kinds of servers... Anyway, from the tutorial (link provided above) I've posted earlier, what kind of server will I make? I think, it's more like a hosting server, hmmmm?

Btw, I forgot to say what "kind" of server I like to make (sorry... ^^), so here it is:

[B][I]- I'd like to share files/folders/printer in my LAN consisting of Windows and Linux PC's (NFS & SAMBA?)
- A web server + database server, which I think is needed if I want to share my files across the Internet/WAN (Apache, SQL, PHP / LAMP?)
- FTP Server *?[1]*
- DNS Server *?[2]*
- Mail Server[/I][/B]

Further Questions:
***?[1]***: What is the difference between a web server and an FTP Server?
***?[2]***: What does a DNS server do in layman's terms?

And of course, I'd like to make my "server" "decently secured"...

So uhmmm.... Will I make those kinds of servers from the tutorial I've posted earlier above? (link provided above)

What would you say about the tutorial I've posted? Would you recommend me to use it or not? If not, are there any other tutz out there that would better fit my distro? (Ubuntu Server 10.04)

And, again, the questions above (see my first post in this thread)... I'd like to know what your answers about it....

Some people might say that I mustn't be asking others about this and it depends on my preferences, which I believe is true... But I'd rather base my preferences to those experienced ones... I really want to start good with less trials and errors... I know it's part of learning, but I want to at least minimize the number of trials and errors...

Thanks again yo, and thanks in advance for further response and help(s)...
God bless all! :popcorn:

---

### Post by rubylaser on 2010-11-30
1. A Web server serves webpages over HTTP or HTTPS, FTP is File Transfer Protocol and is used by many sites to transfer files to another server.  As suggested before, just use SFTP (Secure File Transfer Protocol).

2. DNS in a nutshell via Wikipedia:  It serves as the "phone book" for the Internet by translating human-friendly computer hostnames into IP addresses. For example, the domain name [www.example.com](www.example.com) translates to the addresses 192.0.32.10

Also, you seem confused about some of the packages you mention.  You don't use a LAMP stack to share files over the internet, instead you'd use that for a dynamic website.  If you want to share your files, you could use sftp, vpn, or any number of applications tailored for that purpose.

Hope that helps.

---

### Post by ShadeS_07 on 2010-11-30
Hehe, thanks... 

Uhmmm, about the DNS thing, to tell you frankly, in all these "kinds" of servers I would like to make / configure (and learn), I'm still feeling a bit confused about it... (the DNS server thing...)

It's kinda funny, 'coz, I'd like to make one when I don't know much about it... but that's because I want to learn about it... ya dig? Hehehe... -_+

So, who need(s)/use(s) a DNS server... Who's "served" by a DNS server? What would be one's purpose to make one?

---

### Post by ShadeS_07 on 2010-11-30
Btw, here's the recap of my "concerns" / questions:

I want to make, configure a server.
Because I want to learn / educate myself... and perhaps, others as well who's in the same situation as mine.

**My PC's Specs:**

[I]CPU: P4 + HT Technology; 2.80 Ghz
RAM: SD DDRAM; 1GB
GFX: NVIDIA GeForce FX 5200

HDD: [All IDE]
PM: 80GB; WinXP
PS: 40GB; Kubuntu 10.04 LTS
SM: 40GB; Ubuntu Server Edition 10.04 LTS (To be installed in this drive)

CD/DVD ROM: SATA DVD RW[/I]

**Link to the tut I found:**

[http://www.howtoforge.com/perfect-se...nx-ispconfig-2](http://www.howtoforge.com/perfect-se...nx-ispconfig-2)
[B]
Questions:[/B]

[I]1. Is the tutorial I found for making a server system (link provided above) is a good tut?

2. What kind of server will I make from that tutorial?

3. Is it "decently secure"? (Not perfect, but sufficient to prevent my system from being hacked/cracked "easily")

4. Assuming that I have already installed it (Ubuntu Server) on HDD secondary master (SM), which would then mean that I have two (2) "Desktop Systems": Win XP and Kubuntu 10.04 on HDD PM and HDD PS, respectively; and a "Server System" which is the Ubuntu Server Edition 10.04 on HDD SM, on a single system unit (SU)... If ever (EVER! ) I use Ubuntu Server (I booted it, and did some stuffs, configure, etc...) and suddenly, a hacker (black hat) / cracker got into my system while booted on Ubuntu Server, and exploited any possible vulnerabilities found, will it also affect my "Desktop Systems"? If I shut down my Ubuntu Server and go back to one of my "Desktop Systems" say, win XP, would the hacker be able to still do some "nasty" stuffs with my system for having had been able to hack / crack my system while booted on my Ubuntu Server? OR.. Let's say I am booted to my Ubuntu Server and then I encountered a hacker which then exploited my computer system including my other HDD's which contain my "Desktop Systems", (okay, here's the real question for number 4, I'm sorry for the long "scenario" I made... peace peepz... ^^) will it be a better idea to "disable" my "Desktop Systems" HDD's: PM (WinXP) and PS (Kubuntu 10.04LTS)? By "disabling", I mean by unplugging the Molex power of my Desktop Systems HDD's so that it won't turn on at all whenever I turn on my computer... NOT just by disabling it in BIOS/CMOS Setup. So that leaves the Server System HDD turned on, and when I switch back to one of my Desktop Systems, say, Kubuntu 10.04, I would just shutdown my PC, plug the power back in and perhaps, might unplug the Server System HDD's power.[/I]

[B]"Kind" of server I like to make:
[/B]
[I]- I'd like to share files/folders/printer in my LAN consisting of Windows and Linux PC's (NFS & SAMBA?)
- A web server (dynamic) + database server (Apache, SQL, PHP / LAMP?)
- FTP Server ?[1]
- DNS Server ?[2]
- Mail Server[/I]

And of course I'd like my server to be "decently secured"...


Hehe, gotta sleep now, later peepz... ^^

Thank you very much and thanks in advance...

God bless all! :popcorn:

---

### Post by CharlesA on 2010-11-30
That tut will get you yer basic "hosting" server, that would be used to server web pages and whatnot.

If you are just trying to learn about it, just go nuts with installing and configuring stuff. You can always reinstall if you screw the system up (and you'll learn from your mistakes too)

---

### Post by ShadeS_07 on 2010-12-01
What exactly can that server do, when you say it's a "hosting" server? Uhmm, yeah, I know it "hosts", but what "services" does that server/tut provide exactly?


[QUOTE=ShadeS_07]"Kind" of server I like to make:

- I'd like to share files/folders/printer in my LAN consisting of Windows and Linux PC's (NFS & SAMBA?)
- A web server (dynamic) + database server (Apache, SQL, PHP / LAMP?)
- FTP Server
- DNS Server
- Mail Server[/QUOTE]

With that tut, will I make all those "kinds" of servers above? If so, I'll stick with it, and try to get some more tips for making it even "better" and quite "close" to flawless... 

About the security stuff, I think I'll post another thread in the appropriate category in this forum... So that it's neater, and to avoid mix up...

And also, about the DNS Server thing, I think, that needs another thread as well... I think that's better...

Anyway, this server I'm planning to make isn't just about learning... In the future or shall I say, "if it works", I'll be doing business with it...

---

### Post by CharlesA on 2010-12-01
It's a web server, it serves web pages.

Apache = HTTP
MySQL = Database server
Mail = SMTP or POP3
DNS = name resolution
FTP = file transfer

---

### Post by tarahmarie on 2010-12-01
Hmm. I too am setting up an Apache server for the first time. It's not really for the faint of heart, and I have a question I bet the OP will have soon:

How do I set up the apache2.conf or httpd.conf (whichever one it is, cuz I don't actually know yet) so that when I hit my IP address (123.456.789.101 or whatever) such that the domain name is displayed instead of the IP address in the browser bar?

Here's my httpd.conf:

```

NameVirtualHost *:80

<VirtualHost *:80>
ServerName www.blah.com
ServerAlias blah.com *.blah.com
DocumentRoot /var/www/
</VirtualHost>

<VirtualHost *:80>
ServerName www.blah2.com
DocumentRoot /var/www/
</VirtualHost>


```

That root is where index.html is located. What am I doing wrong?

---

### Post by CharlesA on 2010-12-01
You'd need to set it so that [www.blah2.com](www.blah2.com) redirects to whatever IP you are using for your web server.

You can use your hosts file to do that.

Also: You configure virtualhosts in /etc/apache2/httpd.conf like so:

```
charles@lucid:~$ cat /etc/apache2/httpd.conf 
<VirtualHost *:80>
DocumentRoot /home/charles/site/
</VirtualHost>
```

---

### Post by Sazhen86 on 2010-12-02
Hi

It looks like you're going to install Ubuntu Server on the same PC as you have Windows & Kubuntu on already.  I'd suggest that you grab a copy of VirtualBox and install Ubuntu Server in that.  That way you can still use the PC for web browsing whilst you play around with Ubuntu Server and you can take snapshots which you can go back to in case you mess anything up.  Just my thoughts...

Cheers

---

### Post by CharlesA on 2010-12-02
> **Sazhen86 said:**
> Hi

It looks like you're going to install Ubuntu Server on the same PC as you have Windows & Kubuntu on already.  I'd suggest that you grab a copy of VirtualBox and install Ubuntu Server in that.  That way you can still use the PC for web browsing whilst you play around with Ubuntu Server and you can take snapshots which you can go back to in case you mess anything up.  Just my thoughts...

Cheers
+1 to that. Unfortunately, I don't think that you'll be able to run a virtual machine on top of a GUI with only 1GB of RAM total.

Since Ubuntu server defaults to 512MB of RAM, you may cause more problems by running a virtual machine, then by just dual booting.

---

### Post by Sazhen86 on 2010-12-02
Hi

I agree that it might be a bit tight on a 1GB host, but for experimental purposes Ubuntu Server can get away with 128MB which might be a better fit.  I just tried booting my VMware 10.04 server with 128MB and it seems quite happy, although it isn't doing much.

Cheers

---

### Post by CharlesA on 2010-12-02
> **Sazhen86 said:**
> Hi

I agree that it might be a bit tight on a 1GB host, but for experimental purposes Ubuntu Server can get away with 128MB which might be a better fit.  I just tried booting my VMware 10.04 server with 128MB and it seems quite happy, although it isn't doing much.

Cheers
Hrm, that may work, but it might get a bit touchy once you start adding a load of services.

---

### Post by ShadeS_07 on 2010-12-02
Sorry for the late response, I've been researching / Googling recently so I could help myself as well... Anyway, thanks again for the tips / advises.... :popcorn:

===================================================================

> **CharlesA]It's a web server, it serves web pages.

Apache = HTTP
MySQL = Database server
Mail = SMTP or POP3
DNS = name resolution
FTP = file transfer [/QUOTE]

Thanks man, now I think that tut is the right tut for what I want to do. I have another question about it though, aside from using SFTP instead of plain FTP and not disabling AppArmor, what else would you recommend / suggest about the tut to make it even better?

Btw, can I make an SFTP server with ProFTPd?

[QUOTE=tarahmarie]Hmm. I too am setting up an Apache server for the first time. It's not really for the faint of heart[/QUOTE]

I just had my medical check-up because of what you've posted, and I'm happy to give you the good news: My heart's working good and healthy! xD  said:**
> Hi

It looks like you're going to install Ubuntu Server on the same PC as you have Windows & Kubuntu on already. I'd suggest that you grab a copy of VirtualBox and install Ubuntu Server in that. That way you can still use the PC for web browsing whilst you play around with Ubuntu Server and you can take snapshots which you can go back to in case you mess anything up. Just my thoughts...

Cheers 

[QUOTE=CharlesA]+1 to that. Unfortunately, I don't think that you'll be able to run a virtual machine on top of a GUI with only 1GB of RAM total.

Since Ubuntu server defaults to 512MB of RAM, you may cause more problems by running a virtual machine, then by just dual booting.[/QUOTE]

[QUOTE=Sazhen86]Hi

I agree that it might be a bit tight on a 1GB host, but for experimental purposes Ubuntu Server can get away with 128MB which might be a better fit. I just tried booting my VMware 10.04 server with 128MB and it seems quite happy, although it isn't doing much.

Cheers [/QUOTE]

[QUOTE=CharlesA]
Hrm, that may work, but it might get a bit touchy once you start adding a load of services. [/QUOTE]

Actually, I have tried running Ubuntu Server on a virtual machine, but I still feel it more stable and fast by multi-bootin' it...

This thing I'm tryin' to do might seem experimental, but later on, it'd be more serious than that... -_+



Heh, anyway, thank you very much to all of you... :KS 

God bless all! :popcorn:

---

### Post by Sazhen86 on 2010-12-02
Hi

You don't need an FTP server to use SFTP, you just need to install the openSSH package which will give you secure shell (SSH) and secure FTP (SFTP).  To make it even more secure, I'd recommend generating a public key pair on your client machine, adding the public key to the authorized_keys file and disabling the use of passwords.

As for proFTPd, if you do want to use it, make sure that you don't download the hacked version with the backdoor in it.  Google for it and you'll find that their website was compromised recently.

Cheers

---

### Post by ShadeS_07 on 2010-12-03
Oh, I see...

Hmmm, have you read the tut I've posted? Check out **page 6, number 18: "Proftpd"**... From what you've just said / posted, does it mean that I should skip the installation of Proftpd and go ahead and install openSSH package instead?

---

### Post by CharlesA on 2010-12-03
> **ShadeS_07 said:**
> 
Thanks man, now I think that tut is the right tut for what I want to do. I have another question about it though, aside from using SFTP instead of plain FTP and not disabling AppArmor, what else would you recommend / suggest about the tut to make it even better?

I think that's about it. 

> Btw, can I make an SFTP server with ProFTPd?

You'd use SFTP instead of proftpd.

> Actually, I have tried running Ubuntu Server on a virtual machine, but I still feel it more stable and fast by multi-bootin' it...

Yep. On a machine with limited memory, virtulization probably isn't a good idea.

> **Sazhen86 said:**
> 
As for proFTPd, if you do want to use it, make sure that you don't download the hacked version with the backdoor in it.  Google for it and you'll find that their website was compromised recently.

Their site says their ftp server and mirrors carried a compromised version for 5 days. If you install the version from the repos, it shouldn't be a problem. 

> **ShadeS_07 said:**
> Oh, I see...

Hmmm, have you read the tut I've posted? Check out **page 6, number 18: "Proftpd"**... From what you've just said / posted, does it mean that I should skip the installation of Proftpd and go ahead and install openSSH package instead?

I don't know if ISPconfig depends on proftpd or not, so if your machine isn't going to be accessed from the internet, you should just install it and see how to use it and configure it.

---

### Post by ShadeS_07 on 2010-12-03
[QUOTE=CharlesA]I think that's about it.[/QUOTE]

Thanks again man, now I'm gonna start making that server with that tut... I've been exited on making my first server system since this is really my first time, that should also explain *all* the questions that I've asked / been asking...

> Yep. On a machine with limited memory, virtulization probably isn't a good idea.

Yeah, I'm with you man... I feel ya bro... >.>

Hehe, anyway.... About the FTP thing, I've researched recently about it and now I have some questions to ask regarding this FTP thing...

1. Is it true that with SFTP (openSSH), only users who have the "key" could access the files in my server? I'll use key authentication instead of password authentication because I think it's better and more secure according to this link: **[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)** . So, does it really mean that it will be impossible if I want to access / download files from my server using a friend's computer or maybe a computer in an internet cafe, unless that particular computer has the key?

2. According to the server system setup tutorial (howtoforge.com link), during the installation of Ubuntu Server, there's some sort of a check-boxes (or asterisk boxes?) where he (she?) "checked" **openSSH server** (it's on page 2 of the tut)... does it mean that SFTP has been installed as well when he "selected" and installed openSSH from that point?

3. > I don't know if ISPconfig depends on proftpd or not, so if your machine isn't going to be accessed from the internet, you should just install it and see how to use it and configure it.

What do you mean by, "ISPConfig *depends* on proftpd"? Anyway, I think I'll use openSSH instead of ProFTPd... And I also want my computer to be accessed from the Internet, are you saying openSSH is not a good idea for that?

=================================================================

Basically, I would like to:

Make an SFTP server because according to what I've researched and you've (plural) said / posted, it's better and more secured than plain FTP... [security]

and, have my SFTP server setup be accessible from the Internet so that I could download files / upload files to any computer from the Internet... [accessibility]

What would you suggest / recommend for that criteria of mine? I'm getting confused about this actually, so please clear things up a bit for me... 

I also kinda feel that my criteria "conflicts", you know, usually security and accessibility don't get along with each other all the time, right?

But I still hope to get this working... I'm really out of ideas even though I've researched about it, it just makes me more confused...

Thanks again everyone for sharing knowledge and tips / advises... I really appreciate all that love... I feel it, it's warm... of wait, now it's burnin'! OMG!!! hehe.. 

God bless all! :popcorn:

---

### Post by CharlesA on 2010-12-03
You can carry the private key with you and connect from any machine. That's what I do. That's the best thing to do. You can also use a very strong password, but I prefer using keys, myself.

---

### Post by Sazhen86 on 2010-12-03
[QUOTE=
1. Is it true that with SFTP (openSSH), only users who have the "key" could access the files in my server? I'll use key authentication instead of password authentication because I think it's better and more secure according to this link: **[https://help.ubuntu.com/community/SSH/OpenSSH/Configuring](https://help.ubuntu.com/community/SSH/OpenSSH/Configuring)** . So, does it really mean that it will be impossible if I want to access / download files from my server using a friend's computer or maybe a computer in an internet cafe, unless that particular computer has the key?
[/QUOTE]

OpenSSH can be configured to use a username/password or to use public/private keys, or both.  Using username and passwords allows anyone with network access to your server to attempt to login.  It is also possible for each user that you want to connect to the server to have their own public/private key pair.  The private keys are passphrase protected and remain secret on the users' client machines.  The public keys are added to the server.  Each user can have more than one pair of keys, typically one per computer that they use to connect.  If you want anyone to be able to connect from anywhere, then I'd go for the username/password approach.

> 
2. According to the server system setup tutorial (howtoforge.com link), during the installation of Ubuntu Server, there's some sort of a check-boxes (or asterisk boxes?) where he (she?) "checked" **openSSH server** (it's on page 2 of the tut)... does it mean that SFTP has been installed as well when he "selected" and installed openSSH from that point?
During installation of the Ubuntu Server, there's a page where it allows you to select the services that you want to run, including such things as DNS, mySQL etc.  One of the options is OpenSSH server, which you need to install if you want both SSH and SFTP.

> 
3. What do you mean by, "ISPConfig *depends* on proftpd"? Anyway, I think I'll use openSSH instead of ProFTPd... And I also want my computer to be accessed from the Internet, are you saying openSSH is not a good idea for that?
OpenSSH is perfect for computers wanting to be accessed from the internet.

> 
 Make an SFTP server because according to what I've researched and you've (plural) said / posted, it's better and more secured than plain FTP... [security]
 OK, that's good.

> 
  and, have my SFTP server setup be accessible from the Internet so that I could download files / upload files to any computer from the Internet... [accessibility]
To be accessible from the internet will require that you forward port 22 in your router if you're using one.

> 
   What would you suggest / recommend for that criteria of mine? I'm getting confused about this actually, so please clear things up a bit for me... 
I'd start by making SSH/SFTP work and go from there.  Install OpenSSH, take a look at /etc/ssh/sshd_config and read the comments/man page and make any changes you need, or ask if you need any help.

 > 
    I also kinda feel that my criteria "conflicts", you know, usually security and accessibility don't get along with each other all the time, right?
 This is always a problem.  If security won out, we'd all have 16 digits PINs for our credit cards :-)

> 
     But I still hope to get this working... I'm really out of ideas even though I've researched about it, it just makes me more confused...
  Stick with it, you'll get there.

> 
      Thanks again everyone for sharing knowledge and tips / advises... I really appreciate all that love... I feel it, it's warm... of wait, now it's burnin'! OMG!!! hehe.. 
   That's the great thing about Linux - there's always someone willing to help out.

---

### Post by Sazhen86 on 2010-12-03
I just read Charles' reply, and I would agree about using keys.  That's what I do.  You could start with username/password and when that works, move over to using keys.

---

### Post by CharlesA on 2010-12-03
> **Sazhen86 said:**
> I just read Charles' reply, and I would agree about using keys.  That's what I do.  You could start with username/password and when that works, move over to using keys.
Indeed. Just be sure to use a super strong non-dictionary password (15-30 characters with letters, numbers and special characters) if you are going to be using password authentication.

---

### Post by ShadeS_07 on 2010-12-03
[QUOTE=CharlesA]You can carry the private key with you and connect from any machine. That's what I do. That's the best thing to do. You can also use a very strong password, but I prefer using keys, myself.[/QUOTE]

I'm with you man, I'd prefer key auth over passcode auth... But I have some questions about this crypto-key thing...

[B][I]1. This key authentication is applicable not only to SFTP but to all the tools / programs that uses SSH protocol, right?

2. I know that the public-key is used to "encrypt" / "lock", and the private-key is used to "decrypt" / "unlock"... Now, please consider the following criteria:

- Let's say I already have my server running with OpenSSH (SSH, SFTP, etc...), let's name it "TheServer".

- And there's this computer called "TheClient", that should download files from TheServer via SFTP.

My question is, which of these computers should have which key? Or, should it be that both computers have both keys?

3. Are these keys "portable"? I think, based on what I've researched (you can correct me if I'm wrong, though), downloading from TheServer with TheClient's web browser via SFTP is not possible, so there's a program I found called "FileZilla" (check it out if you don't know about it yet) to download and upload files to/from TheServer, given that the TheClient has this FileZilla installed... Now, this key, can it be used on any platform? Linux only? Windows and Linux? Mac?

4. And where can these keys be generated? I've read in the documentations that it's on the client? It's really confusing! xD Why not on the server?
[/I][/B]
=================================================================

As you've noticed, it's really apparent that I'm really confused with all these stuffs, because for someone new like me, everything seems to be *very* complicated... And now I think it's narrowing down to this point... I'm really getting acquainted with this... Heh.

=================================================================

[QUOTE=Sazhen86]I'd start by making SSH/SFTP work and go from there. Install OpenSSH, take a look at /etc/ssh/sshd_config and read the comments/man page and make any changes you need, or ask if you need any help.[/QUOTE]

> During installation of the Ubuntu Server, there's a page where it allows you to select the services that you want to run, including such things as DNS, mySQL etc. One of the options is OpenSSH server, which you need to install if you want both SSH and SFTP.


Nicely explained, so that's what I need to do to have SSH, SFTP, and all those OpenSSH stuff running, right? <happy! ^^>

> This is always a problem. If security won out, we'd all have 16 digits PINs for our credit cards :)

Lol, yeah...

> Stick with it, you'll get there.

> That's the great thing about Linux - there's always someone willing to help out.

And that's why I never regretted using such OS... -_+


=================================================================

Well, I think, I'll research for the rest of other things I'd like to know regarding this server system thing... For now, I'm gonna log out, coz, I'm gonna eat, and work, and... uh.... eat. yeah..

THANKS ALL!!

God bless all! :popcorn:

---

### Post by CharlesA on 2010-12-03
The server has the public key and the client has the private key.

I use WinSCP and Filezilla to transfer files to/from the server.

---

### Post by Sazhen86 on 2010-12-04
> 
[B][I]1. This key authentication is applicable not only to SFTP but to all the tools / programs that uses SSH protocol, right?
[/I][/B]

That's correct.

> 
[B][I]2. I know that the public-key is used to "encrypt" / "lock", and the private-key is used to "decrypt" / "unlock"... Now, please consider the following criteria:
[/I][/B]
 
That depends, either key can be used to encrypt or decrypt, but whichever is used to encrypt, you need the other one to decrypt.

> 
 [B][I]- Let's say I already have my server running with OpenSSH (SSH, SFTP, etc...), let's name it "TheServer".
[/I][/B]
  OK

> 
  [B][I]- And there's this computer called "TheClient", that should download files from TheServer via SFTP.
[/I][/B]
   OK

> 
   [B][I]My question is, which of these computers should have which key? Or, should it be that both computers have both keys?
[/I][/B]
    
Each client should have both a private key and a public key and the server should have a copy of each client's public key.  Each client can have the same pair of keys, but typically they each have their own and the server has a copy of all the public keys.

> 
    [B][I]3. Are these keys "portable"? I think, based on what I've researched (you can correct me if I'm wrong, though), downloading from TheServer with TheClient's web browser via SFTP is not possible, so there's a program I found called "FileZilla" (check it out if you don't know about it yet) to download and upload files to/from TheServer, given that the TheClient has this FileZilla installed... Now, this key, can it be used on any platform? Linux only? Windows and Linux? Mac?
[/I][/B]
     Filezilla is cool. You can also use sftp from the command line.  Keys are not platform specific but the format that they are in may be.  Make it easy for yourself and give each client its own key pair.

> 
     [B][I]4. And where can these keys be generated? I've read in the documentations that it's on the client? It's really confusing! xD Why not on the server?
[/I][/B]
      They are generated on the client because you need both a public key and a private key pair on the client.  The private key needs to stay private to the client and it's the public key that gets send to one or more servers.
On Ubuntu desktop editions, you can use the "Passwords and encryption Keys" application from the main menu to generate SSH keys.  This will generate both keys for the client and ask you for a passphrase to protect the private key.  It will also add the private key to the key agent which allows the client to use the key without you having to tell it - filezilla will probably just ask the agent for the private key.  The agent will also ask you for the passphrase when something wants to us the private key.  The key generation application also allows you to add the public key to an SSH server by telling it the server's hostname and the user and user's password on the server that the key should belong to.  Each user on the client should have their own key pair.
On windows, most people use PuTTY as an SSH client which also comes with a key agent.  There's PuTTYGen for generating key pairs and it will show you the key in the right format to add to the .ssh/authorized_keys file on the server so that you can cut and paste it.  Other applications on Windows such as WinSCP can also use the PuTTY agent to get the private keys.

> 
      As you've noticed, it's really apparent that I'm really confused with all these stuffs, because for someone new like me, everything seems to be *very* complicated... And now I think it's narrowing down to this point... I'm really getting acquainted with this... Heh.

       
We were all confused when we started - well at least I was.

> 
       Well, I think, I'll research for the rest of other things I'd like to know regarding this server system thing... For now, I'm gonna log out, coz, I'm gonna eat, and work, and... uh.... eat. yeah..

        Don't forget to sleep as well.

Cheers

---

### Post by ShadeS_07 on 2010-12-05
Now I get it! Haha! Thanks all, CharlesA, Sazhen86, all of you who're helping... I highly appreciate your responses/helps/advises/tips/guides regarding this matter.

No more confusion with the SSH Key thing... It's really awesome thing, it's really cool now that I know how it works...

Hmmmm, after I make the server, I'm gonna post here a tutorial for making a server, based from the howtoforge.com tut I've found and revise it according to the tips you've given... So it's not the exact tut I've found, but a revised one which is still based on that tut I've found so that I could help other people too... Is that cool? Would that be ok?

=================================================================

Btw, CharlesA, you've posted this earlier:

[QUOTE=CharlesA]I don't know if ISPconfig depends on proftpd or not, ...[/QUOTE]

At first, it didn't make sense to me and so I asked you this:

[QUOTE=ShadeS_07 (Me!)]What do you mean by, "ISPConfig depends on proftpd"?[/QUOTE]

But, after researching recently, it now makes sense to me... And I think it could be a problem later on, so I'm gonna ask some questions about this... I wanna make this neat, and as much as possible, avoid troubles as much as possible (at least, not totally... 'coz trouble's part of new stuffs, ya know...)

I went to ISPConfig's website and read details about ISPConfig 2... (The following quoted details were copied from the ISPConfig website...)

[QUOTE=http://www.ispconfig.org/ispconfig-2/]
[SIZE="6"]**[FONT="Arial"]ISPConfig 2[/FONT]**[/SIZE]
-----------------------------------------------------------------
[FONT="Arial"]ISPConfig 2 is an open source hosting control panel for Linux. ISPConfig is licensed under BSD license.


[SIZE="4"]**Managed Services**[/SIZE]
 - Httpd (virtual hosts, domain and IP based)
 - FTP
 - Bind (A, CNAME, MX and SPF Records)
 - POP3 Auto-Responder
 - MySQL client-databases
 - Webalizer statistics
 - Harddisk quota
 - Mail-Quota
 - Traffic limits
 - IP-addresses
 - SSL
 - SSI
 - Shell-access
 - Mailscanner (Antivirus)
 - Firewall

[SIZE="4"]**System Requirements**[/SIZE]

[SIZE="2"]**Supported Distributions**[/SIZE]

 - Mandrake Linux starting from version 8.1 to 10.2
 - Mandriva 2006 – 2010.0
 - Red Hat Linux starting from version 7.3 to 9.0
 - Fedora Core 1 – 6, Fedora 7 – 14
 - SuSE Linux starting from version 7.2 to 11.3
 - Debian 3.0 – 5.0
 - Ubuntu 5.04 (Hoary Hedgehog) – 10.10 (Maverick Meerkat)
 - CentOS 4.1 – 5.5

[SIZE="2"]**Details**[/SIZE]

 - Operating System: Linux (Kernel 2.4 or later with glibc6) (the
following distributions are supported: Mandrake Linux, Mandriva, Red Hat Linux, Fedora Core, Fedora, SuSE Linux, ***OpenSuSE, Debian, Ubuntu and CentOS)
 - Apache Webserver version 1.3.12 or later / 2.0.40 or later
 - Sendmail or Postfix
 - Procmail
 - Quota Package
 - ***_[COLOR="Red"]ProFTP as standalone version or vsftpd as[/COLOR]_*** [B][I][U][COLOR="Red"]inetd/xinetd/standalone
version[/COLOR][/U][/I][/B]
 - Php 4.0.5 or newer as Apache module
 - MySQL data base
 - a POP3/IMAP daemon that supports either the traditional Unix- Mailbox
format (e.g. gnu-pop3d, qpopper, ipop3d, popa3d or vm-pop3d) or the Maildir format (e.g. Courier-Imap, Dovecot)
 - OpenSSL and mod_ssl for the creation of SSL virtual hosts
 - BIND8 / BIND9
 - iptables or ipchains[/FONT]
[/QUOTE]

Criteria:

- I'm going to use SFTP (OpenSSH), and not plain FTP (ProFTPd's just plain FTP server, right? You can correct that if I'm wrong though...);

- I'm gonna install and use ISPConfig 2;

- However, ISPConfig seems to "require" that ProFTPd be installed...;

Now, my questions are:

1. Should I skip installation of ProFTPd or not?
2. Will ISPConfig still work fine if I don't install ProFTPd?
3. If I really have to install ProFTPd to have ISPConfig working fine, will it pose a threat to my server system? Will plain FTP be enabled in my system if I install ProFTPd?

Now that you've said that I have to stay away from plain FTP, and choose SFTP as a better choice/option, I really am staying away from plain FTP 'coz I don't wanna expose my system to the security vulnerability(ies) that the plain FTP has... ya dig? You feel me bro?

Hehehe...

God bless all!! :popcorn:

---

### Post by CharlesA on 2010-12-05
That's kinda what I meant - ISPconfig wouldn't install without that ftp server installed.

You could install the ftp server, but tell it not to run/block the ftp port with iptables.

I don't know how well that'll work, but it's worth a shot.

---

### Post by ShadeS_07 on 2010-12-05
So, I mustn't skip the installation of ProFTPd... I must install ProFTPd, but I should disable plain FTP in my server (install but don't use), leaving only the SFTP enabled for file transfer with my server... Which means that I'll have ISPConfig 2 working fine at the same time having a secure file transfer with SFTP, is that correct?

You also said that I could block the FTP port with iptables... Can I use UFW with that?

And you've also told me to "tell it not to run", which I interpreted as "disabling" it... How can I do that?

Thanks man... again... ;)

---

### Post by CharlesA on 2010-12-05
Yeah. I've never done ISPconfig, so I don't know how well it's going to behave, but it's worth a shot. :)

Disabling the ftp server tells it not to run. ;)

---

### Post by ShadeS_07 on 2010-12-05
Hehehe, worth a shot, eh? -_+ Aryt man... :D

To disable FTP, should I do this..?

```

sudo /etc/init.d/ftp stop

```

like that? How can I prevent it from starting every time my server system boots?

Or doing this FTP-disable-thing with UFW/GUFW is just what I have to do, and I'm all good.... Hmmmm? :guitar:

---

### Post by CharlesA on 2010-12-05
See here: [http://www.unixtutorial.org/2009/01/disable-service-startup-in-ubuntu/](http://www.unixtutorial.org/2009/01/disable-service-startup-in-ubuntu/)

---

### Post by ShadeS_07 on 2010-12-05
Hehehe, thanks again man... :D :KS

Uhmmm, btw, what protocol is used when you download from a website? You know, using your browser, you download something from a website with links... like the following:

TerminatorX:
[http://terminatorx.org/dist/terminatorX-3.82.tar.gz](http://terminatorx.org/dist/terminatorX-3.82.tar.gz)

Some random download link (Kruptos 2 Pro) from CNet Downloads: 
[http://dw.com.com/redir?edId=3&siteId=4&oId=3150-2092_4-0&ontId=2092_4&spi=50cfa5d99569e841bcee052d89605d4f&lop=link&tag=tdw_dltext&ltype=dl_elite_dlnow&pid=11654207&mfgId=6276077&merId=6276077&pguid=sazF9AoOYJEAAHmmoUIAAADR&destUrl=http%3A%2F%2Fdownload.cnet.com%2F3001-2092_4-10446164.html%3Fspi%3D50cfa5d99569e841bcee052d89605d4f](http://dw.com.com/redir?edId=3&siteId=4&oId=3150-2092_4-0&ontId=2092_4&spi=50cfa5d99569e841bcee052d89605d4f&lop=link&tag=tdw_dltext&ltype=dl_elite_dlnow&pid=11654207&mfgId=6276077&merId=6276077&pguid=sazF9AoOYJEAAHmmoUIAAADR&destUrl=http%3A%2F%2Fdownload.cnet.com%2F3001-2092_4-10446164.html%3Fspi%3D50cfa5d99569e841bcee052d89605d4f)

Is it HTTP? If yes, then Apache and Apache configuration is concerned here and not SFTP, right?

Uhmmm, is that correct? After finishing making my server, I'd have a directory for HTTP Downloads and another directory for SFTP downloads, correct? :popcorn:

---

### Post by CharlesA on 2010-12-05
All websites use http.

You'd use sftp to upload stuff like new pages or updated files to your server, not for doing downloads off a web site.

---

### Post by ShadeS_07 on 2010-12-05
Oh... I get it now... So the sample links I provided use HTTP for me to download those files from their web servers, not SFTP.

Basically, SFTP is what I would use to download/upload server-related stuffs from/to my server using a client computer that I might use...

And HTTP is what other people who visit my website would use to download and upload files from and to my Apache web server...

Is my interpretation correct, dude?

---

### Post by CharlesA on 2010-12-05
Yes, that's right.

If you are serving files, using Apache is server them is fine.

---

### Post by ShadeS_07 on 2010-12-05
Wow, thanks a lot man... ^^

I think I'm ready to make my tutorial based on every helps/tips/guides/advises I got, and use it to make my server... Then, I'll post it here in the forum, to help other people too...

Would the forum admin/mod mind if I ask them to make it a sticky? ;)

---

### Post by CharlesA on 2010-12-05
There is a [Tips & Tutorials]("http://ubuntuforums.org/forumdisplay.php?f=100") area for that sort of thing.

---

### Post by ShadeS_07 on 2010-12-09
Uhmmmm, hey, another question....

Is there any way for me to have a free domain name? I think I found one from [http://www.co.cc/](http://www.co.cc/), but I don't know how to use it... I watched some tuts on YouTube, and there's this thing they're doing... There's some sort of text boxes for them to put **name servers** as part of making a co.cc domain, and I have no idea where did those peepz get the name servers they put from.... 

I wanna give my web server a free domain name, for short... Is there any way? Thanks! ^^

---

### Post by CharlesA on 2010-12-09
You'd have to set the domain name to point to your server by giving it a host record (A record) in DNS.

I don't know the specifics of that site, but there should be documentation somewhere.

[http://www.co.cc/faq/faq.php](http://www.co.cc/faq/faq.php)

---

### Post by ShadeS_07 on 2010-12-09
Hehehe, oh yeah, thanks man!

---

