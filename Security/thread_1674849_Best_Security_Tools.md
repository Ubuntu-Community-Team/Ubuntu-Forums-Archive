---
title: "Best Security Tools"
date: 2011-01-24
forum: Security
---

### Post by CNM on 2011-01-24
What are you best security tools to use in ubuntu/Linux in general ?

---

### Post by uRock on 2011-01-24
Common sense.:D

Depends on what you feel the need for. I only use a firewall on my netbook when I use a public network. I use NoScript and AdBlock add-ons in Firefox and I use the default profiles for AppArmor.

Other than that, I play with snort and some other softwares, but have never had an alert or anything that would prove the need for the software.

Have you read [Bodhi.Zazen's Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") thread? It has loads of great info.

---

### Post by cariboo on 2011-01-24
+1 common sense is the first thing that should be installed. :)

---

### Post by bodhi.zazen on 2011-01-24
> **CNM said:**
> What are you best security tools to use in ubuntu/Linux in general ?

Security tools for what task exactly ?

I would start with education, see the stickies at the top of this section.

---

### Post by CNM on 2011-01-24
Actually i am aiming at getting a "fresh" ubuntu with security tools installed on it ready to be deployed
when i say security it's not just security tools i also mean vulnerability assessment tools , encryption tools , ...

e.g
Nmap
Aircrack
Nessus
OpenVas
Truecrypt 
Metasploit
...

---

### Post by bodhi.zazen on 2011-01-24
> **CNM said:**
> Actually i am aiming at getting a "fresh" ubuntu with security tools installed on it ready to be deployed
when i say security it's not just security tools i also mean vulnerability assessment tools , encrypting tools , ...

e.g
Nmap
Aircrack
Nessus
OpenVas
Truecrypt 
Metasploit
...

That would be a matter of opinion and what you want to use it for.

For example, a firewall. I might think iptables is the best, others may feel ufw, gufw, or firestarter. Then someone will point out guarddog, finally someone will point out they are all front ends for iptables which is a front end for netfilter.

Of course iptables will not do a virus scan on a windows partition (wrong tool).

:P :twisted:

Try 

[http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)

[http://spins.fedoraproject.org/security/](http://spins.fedoraproject.org/security/)

Or any other security distro =)

---

### Post by CNM on 2011-01-25
Concerning backtrack i've been using it since the first release however i do not appreciate KDE :P lol

as for firewalls well historically it's : Netfilter which is now iptables
all other firewalls are based on iptables ...

---

### Post by artie_effim on 2011-01-25
you could always try [http://www.gnacktrack.co.uk/](http://www.gnacktrack.co.uk/)

---

### Post by artie_effim on 2011-01-25
> **CNM said:**
> Concerning backtrack i've been using it since the first release however i do not appreciate KDE :P lol

as for firewalls well historically it's : Netfilter which is now iptables
all other firewalls are based on iptables ...


you could always try [http://www.gnacktrack.co.uk/](http://www.gnacktrack.co.uk/)

---

### Post by bodhi.zazen on 2011-01-25
> **artie_effim said:**
> you could always try [http://www.gnacktrack.co.uk/](http://www.gnacktrack.co.uk/)

Thanks for that link, I had no idea there was a gnacktrack.

It is still a very large download, 2.4 Gb, those guys need to put this thing on a diet =)

/me looks for lacktrack (Lubuntu version).

---

### Post by CNM on 2011-01-25
> **artie_effim said:**
> you could always try [http://www.gnacktrack.co.uk/](http://www.gnacktrack.co.uk/)

already tried that as well but it's stil TOO buggy and HUUUUUGE !
release 4 of gnacktrack is waaaaaay better then the 3 previous releases but still ... 2.4 GB is not acceptable ... :/

---

### Post by CNM on 2011-01-25
> **bodhi.zazen said:**
> Thanks for that link, I had no idea there was a gnacktrack.

It is still a very large download, 2.4 Gb, those guys need to put this thing on a diet =)

/me looks for lacktrack (Lubuntu version).


the guys have been doing some good work on gnacktrack
i gave it a try ... gnome and based on ubuntu
beautiful graphics , very practical 
however it lacks some key tools (compared to backtrack)
and of course the size is a huge downer :/
it's a good start though :)
still need lots of time of dedicated work to get a good release ...
note that a huge improvement has been made in R4 of gnacktrack specially concerning the installation on HDD (lots of people including me were not able to install it on their PCs ... there was some kind of bugs ...) and specially concerning the wireless cards support , lots of wifi cards were added and supported now ...
still backtrack is the leader for now but i have been keeping a close eye on gnacktrack within these last 7 months and will keep a close eye cause i think it's promising ...
the first thing to work on as i said is definitely the size ... !!

---

### Post by CNM on 2011-01-25
> **bodhi.zazen said:**
> That would be a matter of opinion and what you want to use it for.

For example, a firewall. I might think iptables is the best, others may feel ufw, gufw, or firestarter. Then someone will point out guarddog, finally someone will point out they are all front ends for iptables which is a front end for netfilter.

Of course iptables will not do a virus scan on a windows partition (wrong tool).

:P :twisted:

Try 

[http://www.backtrack-linux.org/](http://www.backtrack-linux.org/)

[http://spins.fedoraproject.org/security/](http://spins.fedoraproject.org/security/)

Or any other security distro =)

thanks for the links :)
i used BT for a long time now 
but never heard of the fedora version !!!
that's cool :D
definitely giving it a try ! :D

---

### Post by CNM on 2011-01-25
Does anyone know a (FREE) linux package like "Whatsup gold" in windows ?

---

### Post by rbroom on 2011-02-05
> **cariboo907 said:**
> +1 common sense is the first thing that should be installed. :)

I checked, it's not in the repos.

On a more helpful note, I suggest folks install telnet, virtualbox for running strange stuff in a VM, and for something similar to "what's up" take a look at Nagios.

---

### Post by wacky_sung on 2011-02-05
How about consider using the security tools [here]("http://sectools.org/"). Beside that you may also wanna use [free secure dns server]("http://www.nortondns.com/"), [proxy]("http://www.squid-cache.org/"), [privoxy]("http://www.privoxy.org/"), [dansguardian]("http://dansguardian.org/"), using [arptable]("http://linux.die.net/man/8/arptables") (or you may wanna configure it in your router), [iptables]("http://www.netfilter.org/") and lot more depending on what type of application of works you are doing.

---

### Post by CNM on 2011-02-06
> **rbroom said:**
> I checked, it's not in the repos.

On a more helpful note, I suggest folks install telnet, virtualbox for running strange stuff in a VM, and for something similar to "what's up" take a look at Nagios.


Actually i always run these kinds of stuff in a VM with VBox actually ...
concerning Nagios ... i have nagios already fully working and it's amazing i also implemented cacti with it but i was checking if there was a replacement for it ... just curiosity ...

---

### Post by cariboo on 2011-02-06
> **rbroom said:**
> I checked, it's not in the repos.

On a more helpful note, I suggest folks install telnet, virtualbox for running strange stuff in a VM, and for something similar to "what's up" take a look at Nagios.

A telnet client is installed by default, no need to try and install it or the server. BTW the common sense installation was a joke.:)

---

### Post by rudelgurke on 2011-02-06
Server related:


[LIST=1]
[*]Snort, Bro etc.
[*]Aide, Yafic or Tripwire
[*]Rkhunter, Chkrootkit, Ossec
[*]mod_security, Suhosin (Patch + Extension)
[*]Secure PHP, Apache configuration
[/LIST]
Generally configuring services with the idea in mind they're being attacked all the time.
Additionally patching the Kernel with Grsecurity then chrooting everything and not using problematic software like Joomla (with several plugins), phpMyAdmin etc. etc. and encrypted logins wherever possible (SSH, SSL, SFTP etc.).

On the desktop - Yafic and Rkhunter / Chkrootkit /Ossec and a general configuration of trusting nobody - specially not myself ;)

Then reading security mailing lists where new bugs are reported.

Most important of course - "brain 2011"

---

### Post by CNM on 2011-02-07
> **rudelgurke said:**
> Server related:


[LIST=1]
[*]Snort, Bro etc.
[*]Aide, Yafic or Tripwire
[*]Rkhunter, Chkrootkit, Ossec
[*]mod_security, Suhosin (Patch + Extension)
[*]Secure PHP, Apache configuration
[/LIST]
Generally configuring services with the idea in mind they're being attacked all the time.
Additionally patching the Kernel with Grsecurity then chrooting everything and not using problematic software like Joomla (with several plugins), phpMyAdmin etc. etc. and encrypted logins wherever possible (SSH, SSL, SFTP etc.).

On the desktop - Yafic and Rkhunter / Chkrootkit /Ossec and a general configuration of trusting nobody - specially not myself ;)

Then reading security mailing lists where new bugs are reported.

Most important of course - "brain 2011"


nice post mate
keep in mind that products like tripwire are not free ...
apache should always be to the last stable version ... not the newest one though
chroot is a great way to isolate some services

what is Yaffic ?

---

### Post by hackertarget on 2011-02-07
Common sense and brain are excellent responses to such a broad question.

I would add awareness. 

- Awareness of potential threats
- Awareness of what is happening on your system

For defence [ossec]("http://www.ossec.net") is an excellent tool that assists with system awareness.

For offence nmap and metasploit.

---

### Post by markthekdeguy on 2011-02-08
linux, nat, disabled upnp, education and for standard WWW duties Adblock, better privacy, a fw and the EXCELLENT  Noscript.

noscript should be compulsory !  :lolflag:

---

### Post by wacky_sung on 2011-02-08
> **markthekdeguy said:**
> linux, nat, disabled upnp, education and for standard WWW duties Adblock, better privacy, a fw and the EXCELLENT  Noscript.

noscript should be compulsory !  :lolflag:

Actually you do not need noscript nor adblock to keep you safe. It is just more an annoyance to me inspite it work great to people who love it.

Privoxy, dansguardian, squid and bleachbit solve all your privacy issues.

FYI I do not used any addon or plugin for my browsers.

---

