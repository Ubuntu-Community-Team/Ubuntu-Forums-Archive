---
title: "What should be a Basic Security Set-Up?"
date: 2010-05-07
forum: Security
---

### Post by listerdl on 2010-05-07
Hi - what is a basic security set-up?

Probably quite a vague question but what do you guys install and set-up to ensure that all bases are covered?

Likely no need for things like anti-virus scanners etc - more likely software reporting open ports.

Any ideas?

Thanks!!!!!!!!!

---

### Post by mikewhatever on 2010-05-07
Are you running a server? If not, the default out of the box setup should do. Keep it updated and use strong passwords.

---

### Post by HermanAB on 2010-05-07
Relax and enjoy your nice new secure system.

---

### Post by CharlesA on 2010-05-07
Unless you are running a server, there is nothing you need to do.

---

### Post by Soul-Sing on 2010-05-07
> **mikewhatever said:**
> Are you running a server? If not, the default out of the box setup should do. Keep it updated and use strong passwords.

Indeed, a server set-up is less easy.

---

### Post by Jive Turkey on 2010-05-07
1. Strong password
2. VNC/remote desktop and similar services turned off.

---

### Post by CharlesA on 2010-05-07
> **Jive Turkey said:**
> 1. Strong password
2. VNC/remote desktop and similar services turned off.

Whoops. Forgot about how easy it was to turn on the "remote desktop" doohickey.

Good point! ;)

---

### Post by yeehi on 2010-05-08
What commands turn off VNC remote desktop and similar services?

Thank you.

---

### Post by CharlesA on 2010-05-08
> **yeehi said:**
> What commands turn off VNC remote desktop and similar services?

Thank you.

Don't turn it on in the first place. I think it is located here:

System > Administration > Remote Desktop

I don't use Gnome, so I am not 100% sure.

A normal desktop install has no listening services. If you install one, just be sure that it has been secured properly.

---

### Post by Bear number one on 2010-05-08
Turn on the firewall and keep the system updated.

---

### Post by Rubi1200 on 2010-05-08
You can use the following command to check for listening services 
   
sudo netstat -tap 
   
cups should be the only service listening unless you have enabled things like remote desktop, vnc, or ssh.

I find it useful to also check the logs on a regular basis; use the tail command for this.

Other useful commands include:

w
last
ps
lsof
faillog -a

---

### Post by Bear number one on 2010-05-08
Hi, I've just tried this and, as mentioned, the cups service is listening.
There is also another service listed as listening:

exim4 on localhost smtp.

I take it this is something to do with email?
This is on Ubuntu 10.04 with a standard installation so should this be added to the 'normal services' that a user should expect to be listening?

---

### Post by Rubi1200 on 2010-05-08
Exim4 is indeed an MTA (mail transfer agent). It is associated with a number of programs, especially those that send notifications by email such as rkhunter etc.

I read somewhere that it is not considered to be as secure as other email servers (please correct me if this is wrong), so unless you really need it, I would suggest turning it off. Have you added anything recently that would be using this?

You can check by going to Synaptic and looking at History; check through recently installed programs and see what it is associated with. 

Personally, I think you should remove it, but that is just my opinion.

---

### Post by CharlesA on 2010-05-08
> **Rubi1200 said:**
> 
I read somewhere that it is not considered to be as secure as other email servers (please correct me if this is wrong), so unless you really need it, I would suggest turning it off.

Hrm. Do you remember where you read that?

I've been running EXIM4 as a local SMPT relay agent for gmail since 9.04 and haven't had any problems at all. Maybe it's how I've got it set, so that it only listens on localhost.

Thanks for any info.

---

### Post by Soul-Sing on 2010-05-08
> **Bear number one said:**
> Hi, I've just tried this and, as mentioned, the cups service is listening.
There is also another service listed as listening:

exim4 on localhost smtp.

I take it this is something to do with email?
This is on Ubuntu 10.04 with a standard installation so should this be added to the 'normal services' that a user should expect to be listening?

Same here exim4 on smtp after installing rkhunter/chkrootkit
: [http://ubuntuforums.org/showthread.php?t=1475874](http://ubuntuforums.org/showthread.php?t=1475874)

---

### Post by tubbygweilo on 2010-05-08
Use the Mozilla Firefox browser with betterprivacy, nosccript, flashblock & addblock extensions or use Chromium or Google Chrome browsers. It is OK to zip up tight your computer but just make sure you do not fall fail of social engineering attacks via your surfing expeditions.

---

### Post by Rubi1200 on 2010-05-08
> **CharlesA said:**
> Hrm. Do you remember where you read that?

I've been running EXIM4 as a local SMPT relay agent for gmail since 9.04 and haven't had any problems at all. Maybe it's how I've got it set, so that it only listens on localhost.

Thanks for any info.

Found it!

> **3.2. The Danger Zone (or r00t m3 pl34s3)**

 The following is a list of services that should ***not*** be  run over the Internet. Either disable these (see below), uninstall, or if you  really do need these services running locally, make sure they are the  current, patched versions *and* that they are effectively  firewalled. And if you don't have a firewall in place now, turn them off  until it is up and verified to be working properly. These are potentially  insecure by their very nature, and as such are prime cracker targets.  
 

[LIST]
[*]   NFS (Network File System) and related services,    including nfsd,    lockd, mountd,    statd, portmapper,    etc. NFS is the standard Unix service for sharing file systems across a    network. Great system for LAN usage, but dangerous over the Internet.    And its completely unnecessary on a stand alone system.
[*]   rpc.* services, Remote Procedure Call.*, typically NFS and NIS related (see    above).
[*]   Printer services (lpd).
[*]   The so-called r* (for "remote", i.e. Remote SHell) services:    rsh, rlogin,    rexec, rcp etc.    Unnecessary, insecure and potentially dangerous, and better utilities are    available if these capabilities are needed. ssh    will do everything these command do, and in a much more sane way. See the    man pages for each if curious.  These will probably show in    **netstat** output without the "r":    **rlogin** will be just "login", etc.
[*]   telnet server. There is no reason for this    anymore. Use sshd instead.
[*]   ftp server. There are better, safer ways for    most systems to exchange files like **scp** or     via **http** (see below). ftp is a    proper protocol only for someone who is running a dedicated ftp server, and    who has the time and skill to keep it buttoned down. For everyone else, it is    potentially big trouble.
[*]   BIND (**named**), DNS server    package. With some work, this can be done without great risk, but is not    necessary in many situations, and requires special handling no matter    how you do it. See the sections on [Exceptions]("http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Security-Quickstart-HOWTO.html#EXCEPTIONS") and special handling for [individual applications]("http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Security-Quickstart-HOWTO.html#INDAPPS").
[*]   **Mail Transport Agent, aka "MTA"    (sendmail, exim,    postfix, qmail)**.    Most installations on single computers will not really need this. If you are not    going to be directly receiving mail from Internet hosts (as a designated MX    box), but will rather use the POP server of your ISP, then it is not    needed. You may however need this if you are receiving mail    *directly* from other hosts on your LAN, but initially    it's safer to disable this. Later, you can enable it over the local    interface once your firewall and access policies have been implemented.
[/LIST]
this is the link:

[http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Security-Quickstart-HOWTO.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Security-Quickstart-HOWTO.html)

I hope this is useful.

---

### Post by CharlesA on 2010-05-08
Thank you! I just use it to send mail to gmail and let gmail do all the work. I don't believe it is allowed access to the outside internet outside of the port that gmail uses. All incoming connections are blocked.

---

### Post by Bear number one on 2010-05-09
> **Rubi1200 said:**
> Exim4 is indeed an MTA (mail transfer agent). It is associated with a number of programs, especially those that send notifications by email such as rkhunter etc.

Have you added anything recently that would be using this?



Apologies for the 'standard installation' comment, I had experimented with rkhunter and forgot it was on there.
After removing rkhunter I then removed exim4 via synaptic and the netstat -tap output now shows cups as the only listening process.
Not sure if this should be a new thread, but, out of interest, if an unexpected listening process was revealed how would the average desktop user go about tracking it down and identifying it as good or bad?

---

### Post by Soul-Sing on 2010-05-09
Thx a bunch, removed also rkhunter/exim4 completelty
and no open ports/listening services on my desktop.

---

### Post by CharlesA on 2010-05-09
> **Bear number one said:**
> Apologies for the 'standard installation' comment, I had experimented with rkhunter and forgot it was on there.
After removing rkhunter I then removed exim4 via synaptic and the netstat -tap output now shows cups as the only listening process.
Not sure if this should be a new thread, but, out of interest, if an unexpected listening process was revealed how would the average desktop user go about tracking it down and identifying it as good or bad?

netstat -l would tell you what services are listening, and a quick google would tell you if they are good or not.

---

### Post by Bear number one on 2010-05-09
Just tried this and googled a few random results, plenty of info and tips out there including services that it might be best to disable and how to do it.
Nice one.
It's a good thing to know and a good way to learn more about the Ubuntu/Linux system.
Many Thanks.

---

### Post by CharlesA on 2010-05-09
For the most part, most stuff is fairly well documented, but you do have to do some digging sometimes.

---

### Post by abickerton on 2010-05-10
> **CharlesA said:**
> For the most part, most stuff is fairly well documented, but you do have to do some digging sometimes.

Short answer... Let the end user do what they need to do but block all incoming unrelated by default. 



# Generated by iptables-save v1.4.4 on Fri Apr 23 21:04:05 2010
*filter
:INPUT DROP [112:18023]
:FORWARD DROP [0:0]
:OUTPUT ACCEPT [165:16598]
[112:54064] -A INPUT -i eth0 -m state --state RELATED,ESTABLISHED -j ACCEPT 
[4:200] -A INPUT -s 127.0.0.1/32 -j ACCEPT 
COMMIT

---

