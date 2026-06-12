---
title: "Cheese Webcam Booth - backdoor Trojan?"
date: 2009-06-26
forum: Security
---

### Post by dunbrokin on 2009-06-26
The weirdest thing just happened to me.....(or else I am going crazy - possible but not very probabale). I have two ID's on my PC. One for work and one for home. The home one is the master ID. I was using the work ID taking some mug shots using Cheese Webcam Booth...when, all of a sudden, a voice (in a foreign accent...like a French accent) said laughingly " I am watching"....I must say it frightened the Bejasus out of me. I am on a wireless LAN and there is only one other PC on the LAN and that runs my weather station....

What is going on?

How do I check my logs to see if an intrusion has occured?

---

### Post by snek on 2009-06-26
First of all the question is if your WIFI is secured.
Second you might want to check open connections using:
```
netstat -a
```
Third you will want to configure iptables to only allow ports you need.

If someone got access to your machine through SSH you can check the auth.log like so:
```

sudo cat /var/log/auth.log |grep ssh

```
This will show all SSH connection (attempts).

It is a bit scary though, I agree!

---

### Post by loell on 2009-06-26
oh come on, could it be that you're watching some flash based movies, that may have coincidentally utter the words "I am watching"? :D

---

### Post by dunbrokin on 2009-06-26
> **loell said:**
> oh come on, could it be that you're watching some flash based movies, that may have coincidentally utter the words "I am watching"? :D

Entirely possible...except that my browser was not running at the time....so, curiouser and curiouser..

---

### Post by dunbrokin on 2009-06-26
> **snek said:**
> First of all the question is if your WIFI is secured.
Second you might want to check open connections using:
```
netstat -a
```


I live in a remote area, so while theoretically my wireless could have been hacked, it is not likely. The output of netstat -a is very long and, I am unhappy to say, makes little sense to me.

---

### Post by dunbrokin on 2009-06-26
> **snek said:**
> 

```

sudo cat /var/log/auth.log |grep ssh

```
This will show all SSH connection (attempts).!

:~$ sudo cat /var/log/auth.log |grep ssh
{sudo] password forxxxj: 
:~$ sudo cat /var/log/auth.log |grep ssh
:~$

---

### Post by dunbrokin on 2009-06-26
How do I configure iptables to only configure ports that I need...how do I know what ports I need?

---

### Post by canadiandude007 on 2009-06-26
I would recommend reading this first (about intrusion detection):

[http://ubuntuforums.org/showthread.php?p=5787017&mode=threaded&highlight=iptables#post5787017](http://ubuntuforums.org/showthread.php?p=5787017&mode=threaded&highlight=iptables#post5787017)

and this ...

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Both very useful.  Good luck!

---

### Post by dunbrokin on 2009-06-26
> **canadiandude007 said:**
> I would recommend reading this first (about intrusion detection):

[http://ubuntuforums.org/showthread.php?p=5787017&mode=threaded&highlight=iptables#post5787017](http://ubuntuforums.org/showthread.php?p=5787017&mode=threaded&highlight=iptables#post5787017)

and this ...

[https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)

Both very useful.  Good luck!

Thanks for that...the first link seems really complicated...not sure I am up to that....I should be able to crack the Iptables....but is there any traces in the logs where the intruder entered and how they entered?

---

### Post by mikewhatever on 2009-06-26
> **dunbrokin said:**
> I live in a remote area, so while theoretically my wireless could have been hacked, it is not likely. The output of netstat -a is very long and, I am unhappy to say, makes little sense to me.

You can put it all into a text file and attach the file for review. Run the following command, then check for netstat.txt on the Desktop.

netstat -a > ~/Desktop/netstat.txt

---

### Post by rookcifer on 2009-06-26
First off, how are you securing your wireless network?  Are you using WPA/WPA2?  Do you have it secured with a password?

Secondly, is the other PC on your LAN also running Ubuntu?  Are you using Samba?  Is the other PC connected directly to the Internet?

Third, are you running ssh?

---

### Post by dunbrokin on 2009-06-26
> **mikewhatever said:**
> You can put it all into a text file and attach the file for review. Run the following command, then check for netstat.txt on the Desktop.

netstat -a > ~/Desktop/netstat.txt

But if I attach this information as you suggest, would that not give more information to a hacker when he sees it here and so make me more vulnerable.

---

### Post by dunbrokin on 2009-06-26
> **rookcifer said:**
> First off, how are you securing your wireless network?  Are you using WPA/WPA2?  Do you have it secured with a password?

Secondly, is the other PC on your LAN also running Ubuntu?  Are you using Samba?  Is the other PC connected directly to the Internet?

Third, are you running ssh?
I am using WEP with a secure password.....for somebody to hack into my wireless, they would have had to sit outside my house in 1 degree C last night....and as I say, I live in a remote area. It is possible, but unlikely that somebody could have been in a car and did it via a laptop.....but I am discounting that theory for now. 

The other PC on my LAN is also running 9.04. I have set it up so that my PC can access it remotely within the confines of the LAN. It is connected directly to the net as it sends weather information to WeatherUnderground every minute.The printer for the LAN is connected to the weather PC - so that is Samba.

---

### Post by loell on 2009-06-26
> **dunbrokin said:**
> But if I attach this information as you suggest, would that not give more information to a hacker when he sees it here and so make me more vulnerable.

he could have obtain that least information ages ago if indeed your system has been compromised.

where have you downloaded cheese? if you got it from  the main repository then it sure isn't a trojan.

you can install and use **gufw** to utilise the already installed **ufw**(uncomplicated firewall).

---

### Post by dunbrokin on 2009-06-26
I installed it from the repositories.

---

### Post by dunbrokin on 2009-06-26
These are the netstat results from both of my machines.

---

### Post by rookcifer on 2009-06-26
> **dunbrokin said:**
> These are the netstat results from both of my machines.

Since you are concerned that someone *might* have infiltrated your box, then netstat might not be reliable (because an attacker could have installed a rootkit).  A better way than using netstat is to port scan yourself with nmap.

```
sudo apt-get install nmap
```

First, close your browser and other things that you know are connecting to the Internet.

Then to do a scan, do:

```
sudo nmap -sT -v -p- localhost
```

The output will show all listening ports and what services are listening on each open port.  If for some reason, it doesn't list the service, then you can use lsof.

```
sudo lsof -i | grep <port number>
```

Where "port number" is the number of the port.

NOTE: if you are behind a router, don't scan the router.  Only scan locally, or else it will take several hours.  You can also try scanning both machines.

---

### Post by dunbrokin on 2009-06-27
Thanks for that....here is the output...first of the main machine...then of the weather machine.

~$ sudo nmap -sT -v -p- localhost 

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-06-27 16:10 NZST 
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1. 
Initiating Connect Scan at 16:10 
Scanning localhost (127.0.0.1) [65535 ports] 
Discovered open port 445/tcp on 127.0.0.1 
Discovered open port 139/tcp on 127.0.0.1 
Discovered open port 631/tcp on 127.0.0.1 
Completed Connect Scan at 16:10, 1.23s elapsed (65535 total ports) 
Host localhost (127.0.0.1) appears to be up ... good. 
Interesting ports on localhost (127.0.0.1): 
Not shown: 65532 closed ports 
PORT    STATE SERVICE 
139/tcp open  netbios-ssn 
445/tcp open  microsoft-ds 
631/tcp open  ipp 

Read data files from: /usr/share/nmap 
Nmap done: 1 IP address (1 host up) scanned in 1.38 seconds 
           Raw packets sent: 0 (0B) | Rcvd: 0 (0B) 

weather:~$ sudo nmap -sT -v -p- localhost 

Starting Nmap 4.76 ( [http://nmap.org](http://nmap.org) ) at 2009-06-27 16:20 NZST
Warning: Hostname localhost resolves to 2 IPs. Using 127.0.0.1.
Initiating Connect Scan at 16:20
Scanning localhost (127.0.0.1) [65535 ports]
Discovered open port 631/tcp on 127.0.0.1
Discovered open port 5900/tcp on 127.0.0.1
Completed Connect Scan at 16:20, 7.48s elapsed (65535 total ports)
Host localhost (127.0.0.1) appears to be up ... good.
Interesting ports on localhost (127.0.0.1):
Not shown: 65533 closed ports
PORT     STATE SERVICE
631/tcp  open  ipp
5900/tcp open  vnc

Read data files from: /usr/share/nmap
Nmap done: 1 IP address (1 host up) scanned in 8.21 seconds
           Raw packets sent: 0 (0B) | Rcvd: 0 (0B)

---

### Post by rookcifer on 2009-06-27
Everything looks fine on first machine (Samba and printer which should be bound locally).  On the second machine, do you have that VNC server locked down with a strong password?  

Other than the VNC server, I don't see any way in.

---

### Post by dunbrokin on 2009-06-27
I appear to have caught a fish on my weather machine.....what do I do now? This is part of the output of chkrootkit.

Checking `asp'...                                           not infected 
Checking `bindshell'...                                     not infected 
Checking `lkm'...                                           You have     1 process hidden for readdir command 
You have     1 process hidden for ps command 
chkproc: Warning: Possible LKM Trojan installed 
chkdirs: nothing detected 
Checking `rexedcs'...                                       not found 
Checking `sniffer'...                                       lo: not promisc and no packet sniffer sockets 
eth1: PACKET SNIFFER(/sbin/wpa_supplicant[2662], /sbin/dhclient3[3257]) 
Checking `w55808'...                                        not infected 
Checking `wted'...                                          chkwtmp: nothing deleted 
Checking `scalper'...                                       not infected 
Checking `slapper'...                                       not infected

---

### Post by dunbrokin on 2009-06-27
> **rookcifer said:**
> Everything looks fine on first machine (Samba and printer which should be bound locally).  On the second machine, do you have that VNC server locked down with a strong password?  

Other than the VNC server, I don't see any way in.

No password between the VNC weather machine and the main PC...which, presumably, is how ge got in....

---

### Post by dunbrokin on 2009-06-27
From rkhunter - the same warning occurs on both machines....
[18:08:13] Warning: The file '/usr/sbin/unhide' exists on the system, but it is not present in the rkhunter.dat file.
[18:08:13] /usr/sbin/useradd                                 [ OK ]
[18:08:13] /usr/sbin/userdel                                 [ OK ]
[18:08:14] /usr/sbin/usermod                                 [ OK ]
[18:08:14] /usr/sbin/vipw                                    [ OK ]
[18:08:14] /usr/sbin/unhide-linux26                          [ Warning ]
[18:08:14] Warning: The file '/usr/sbin/unhide-linux26' exists on the system, but it is not present in the rkhunter.dat file.
[18:08:21]
.
.
.
[18:08:57]   Checking /dev for suspicious file types         [ Warning ]
[18:08:57] Warning: Suspicious file types found in /dev:
[18:08:57]          /dev/shm/pulse-shm-2901440300: data
[18:08:57]          /dev/shm/pulse-shm-2260800593: data
[18:08:57]   Checking for hidden files and directories       [ None found ]

---

### Post by dunbrokin on 2009-06-27
To further complicate matters, my weather PC is showing at 100% CPU all the time despite the attached from "top"

---

### Post by dunbrokin on 2009-06-27
bump

---

### Post by rookcifer on 2009-06-28
As for the first warning from chrootkit, see [this thread]("http://ubuntuforums.org/showthread.php?p=7083343").  It appears others have had this very warning and it was nothing.

As for the second warning from rkhunter, see [this thread.]("http://ubuntuforums.org/showthread.php?t=1114121")  Same thing here, it appears to be nothing out of the ordinary.

---

### Post by dunbrokin on 2009-06-28
Thanks, once again, for your help....

So, after all that we are none the wiser how the intruder got in ....or how he can be stopped in the future?!

---

### Post by seaq on 2009-06-28
hmmm. it doesn't look normal.  i would try to figure out how they did it.

Is your Wireless AP the router for your net?

Are you using a dynamic ip or fixed one?

Your Wireless AP is accesible via web?  from inside or it's enabled the remote admin (web access via WAN side of the AP)?

Your AP uses the standard password?

Unless your "weather" linux pc is the "frontend" for the internet, i don't see a feasible way to break a system as described.

Sadly the data that you've send is useless on the sense that the event already happened and there wasn't logs from the event itself. ( a netstat would have been perfect.)

---

### Post by seaq on 2009-06-28
aahh, please check in your AP the firewall and port redirection sections, if your AP uses the standard password and the admin web page is accessible from outside, someone could have accessed, configure a redirection to the vnc pc, and from there .. well who nows!?

---

### Post by loell on 2009-06-28
> **dunbrokin said:**
> 
So, after all that we are none the wiser how the intruder got in ....or how he can be stopped in the future?!


and if you're really concerned about your personal data and privacy, you should have wipe your old installation by now for a newer one with basic firewall protection. don't go chasing a ghost who could have covered his tracks after that unlikely incident.

---

### Post by dunbrokin on 2009-06-28
Is your Wireless AP the router for your net?
Yes.

Are you using a dynamic ip or fixed one?
Dynamic

Your Wireless AP is accesible via web?  from inside or it's enabled the remote admin (web access via WAN side of the AP)?
Not sure what this means.

Your AP uses the standard password?
No, a randomly generated password. A friend came bye last week with his PC (using Vista) and I gave him access to the net via my wireless....not sure if somebody (not him) could have got access to the password that way.

Unless your "weather" linux pc is the "frontend" for the internet, i don't see a feasible way to break a system as described.
The weather PC is not the front end. It is just another connection.

Sadly the data that you've send is useless on the sense that the event already happened and there wasn't logs from the event itself. ( a netstat would have been perfect.)
But there are netstat logs attached above?

---

### Post by dunbrokin on 2009-06-28
> **seaq said:**
> aahh, please check in your AP the firewall and port redirection sections, if your AP uses the standard password and the admin web page is accessible from outside, someone could have accessed, configure a redirection to the vnc pc, and from there .. well who nows!?

How would the admin page be accessible from outside?

Not sure I understand your suggestion " please check in your AP the firewall and port redirection sections"

---

### Post by dunbrokin on 2009-06-28
The Firewall and NAT service is enabled on my router.

No port redirection set up on the router.

---

### Post by dunbrokin on 2009-06-28
> **loell said:**
> and if you're really concerned about your personal data and privacy, you should have wipe your old installation by now for a newer one with basic firewall protection. don't go chasing a ghost who could have covered his tracks after that unlikely incident.

I am not really concerned about the personal data situation...it is more the snooping/spying on people through their webcam etc that bothers me.

I am not sure what you mean by "unlikely incident" - do you mean a low probability incident or an incident which is unlikely to have happened i.e. a figment of my imagination?

From what I have read elsewhere, adding a basic firewall does not really give any extra protection to that which you have anyway. It is more a provider of psychological comfort.

---

### Post by rookcifer on 2009-06-28
I am doubting you were cracked at all, but *if* you were, it was almost definitely from that VNC server.

The problem with the rootkit scanners is they produce too many false positives and one needs to be somewhat of a security guru to even use them effectively in the first place.  And even then they wont do much good if an attacker is aware of the scanner and has altered it in some way.

The only thing I can say at this point is to: 

A) Keep monitoring your TCP connections to see if any fishy connections to unknown places pops up.

or 

B) Format/reinstall and be done with the worries.  This time be sure to secure that VNC server or, even better, don't use VNC at all.  Set up an SSH X tunnel as outlined [here]("http://ubuntuforums.org/showthread.php?t=446276").

---

### Post by dunbrokin on 2009-06-28
Thanks again for that....I appreciate your help.

I am sure you are right in that I have not been cracked...as in that some malware was not placed on my PC. An intruder certainly was present...but  I am pretty sure it was of the tagging variety rather than that of the malicious variety. None the less, I would like to ensure that it does not happen again. The intruder most certainly got to my main PC via the VNC link from my weather PC...but that kind of begs the question of how he got to the weather PC in the first place - given that the set up is similar for both machines?

What do you recommend for TCP monitoring?

---

### Post by loell on 2009-06-28
> **dunbrokin said:**
> 
I am not sure what you mean by "unlikely incident" - do you mean a low probability incident or an incident which is unlikely to have happened i.e. a figment of my imagination?

no i'm not implying that you have psychological problems or that you're not sober at that time, hearing voices should still be our last resort of recommendation. :)

what i meant by unlikely is, the intruder really waited for you to use cheese and he blew his cover by a voice data stream? 

it's just hard for me to believe he did that after compromising your system, he could have use your system a million different ways yet he choosed to alarm you.

---

### Post by dunbrokin on 2009-06-28
Indeed...that is what I mean by it was a tagging prank rather than a malicious intrusion.....but it still leaves me with the problem of trying to prevent it from happening again. Even if I do a fresh install, what will change that will stop the tagging intrusion again...? I think I need to try and find the weakness and fix that....but it looks from all the feedback that nobody can really see a weakness in my system set up - apart from the vnc - but that is not really the problem, it is a route from one PC to the other...but does not tackle the initial problem.

---

### Post by dunbrokin on 2009-06-29
Does this help any? Why would iptstate be showing nothing?

---

### Post by loell on 2009-06-29
> **dunbrokin said:**
>  Even if I do a fresh install, what will change that will stop the tagging intrusion again...? 


it will rule out that there's a trojan in your system.

ubuntu's default install is fairly secure even w/o explicitly setting a firewall. by starting from ground zero you will have the opportunity to decide again on what outside programs you'll be installing.

if it's from ubuntu repository then you can flag the program  as safe , if it is from other sources then you begin suspecting if that was the trojan or not.

---

### Post by lisati on 2009-06-29
> **dunbrokin said:**
> I am using WEP with a secure password.....for somebody to hack into my wireless, they would have had to sit outside my house in 1 degree C last night....and as I say, I live in a remote area. It is possible, but unlikely that somebody could have been in a car and did it via a laptop.....but I am discounting that theory for now. 

You might want to pencil in changing to WPA or WPA2 on your "To do" list, as it's a lot harder to crack than WEP.

As unlikely as it is, it could be possible that someone sat nearby in a car with a laptop. I saw a news item on (possibly TV3) a year or two back about people's vulnerability to intrusion, where a reporter did the rounds of some suburban streets, looking for wireless networks which were not properly secured. The reporter noted that many networks he discovered didn't even have WEP enabled.

---

### Post by dunbrokin on 2009-06-29
> **lisati said:**
> You might want to pencil in changing to WPA or WPA2 on your "To do" list, as it's a lot harder to crack than WEP.

As unlikely as it is, it could be possible that someone sat nearby in a car with a laptop. I saw a news item on (possibly TV3) a year or two back about people's vulnerability to intrusion, where a reporter did the rounds of some suburban streets, looking for wireless networks which were not properly secured. The reporter noted that many networks he discovered didn't even have WEP enabled.

I live in remote Otago....I take your point...but chances realistically about zero, when you can cruise around Queenstown and pick up as much as you want!

---

### Post by dunbrokin on 2009-06-29
tcp        1      0 pj-xxx.loc:37981 p3plpkivs-v03.any.p:www CLOSE_WAIT 
tcp        0      0 pj-xxx.loc:49672 wf-in-f125.:xmpp-client ESTABLISHED
tcp      215      0 pj-xxx.loc:51374 p4171-ipbf604maru:63894 CLOSE_WAIT 

How do I find out what these are?

---

### Post by rookcifer on 2009-06-29
> **dunbrokin said:**
> tcp        1      0 pj-xxx.loc:37981 p3plpkivs-v03.any.p:www CLOSE_WAIT 
tcp        0      0 pj-xxx.loc:49672 wf-in-f125.:xmpp-client ESTABLISHED
tcp      215      0 pj-xxx.loc:51374 p4171-ipbf604maru:63894 CLOSE_WAIT 

How do I find out what these are?

The first one looks like your web browser (but I'm not positive).  The second one looks like Jabber is connected. Not sure about the 3rd one. 

But you can use lsof.  For instance in this case, type:

```
lsof -i 
```

And it will list all TCP connections and what process is using them.  Or you can find out what is running based on the port:

```
lsof -i :37981
```

Do that for all ports you are wondering about.

---

### Post by dunbrokin on 2009-06-30
> **seaq said:**
> aahh, please check in your AP the firewall and port redirection sections, if your AP uses the standard password and the admin web page is accessible from outside, someone could have accessed, configure a redirection to the vnc pc, and from there .. well who nows!?

I am not sure that my AP is accessible from outside...how do I check that. The password is not standard....but probably not that difficult to break under repeated attachk.

---

### Post by dunbrokin on 2009-06-30
> **rookcifer said:**
> I am doubting you were cracked at all, but *if* you were, it was almost definitely from that VNC server.
[/URL].

But the VNC server is behind my AP with the router firewall enabled...

---

### Post by dunbrokin on 2009-07-01
I am beginning to wonder whether the intruder came through Skype to my webcam...Skype has been acting weird lately - using up a lot of CPU so I have deleted it from my system.

---

### Post by dunbrokin on 2009-07-11
When I do an AutoScan Network, I find that my Router (10.1.1.1) has two open ports - Telnet and Http.....I presume the http is the internet connection....but why do I need the Telnet? ...and is that a possible route in for the intruder?

---

### Post by dunbrokin on 2009-08-01
Panic over....there is an evil Easter egg in Cheese...where after a certain number of photos, a voice is activated and says a number of different phrases.......So all that for nothing....now I have completely screwed up my VNC etc and it will take me ages to get back to where I was......aaaarrrrgggghhhhhhh!!!!

---

### Post by southbound395 on 2009-08-12
> **dunbrokin said:**
> Panic over....there is an evil Easter egg in Cheese...where after a certain number of photos, a voice is activated and says a number of different phrases.......So all that for nothing....now I have completely screwed up my VNC etc and it will take me ages to get back to where I was......aaaarrrrgggghhhhhhh!!!!

wow, and this is yet another reason I won't ever use webcams... 
not really much ado about nothing, because it could have been a much more malignant easter egg than it turned out to be.
thank you all for the interesting reading as I am straight linux NEWB and need to learn what i can :)

---

### Post by loell on 2009-08-12
> **southbound395 said:**
> wow, and this is yet another reason I won't ever use webcams... 
not really much ado about nothing, because it could have been a much more malignant easter egg than it turned out to be.
thank you all for the interesting reading as I am straight linux NEWB and need to learn what i can :)

first rule of thumb, never download from untrusted sources.

second, unless there is concrete evidence that an open source  program is a trojan, be skeptical on what other people are saying.

---

### Post by pianoscarf88 on 2010-03-03
yeee you can go ahead and mark this one as [solved] the random guy yelling in cheese is part of the program. I get the same thing. It actually is quite creepy and freaked me out. The recording starts playing more and more often the more you take photos and it says like three different things. One of them being CHEESE! lolz

---

### Post by pianoscarf88 on 2010-03-03
yeee you can go ahead and mark this one as [solved] the random guy yelling in cheese is part of the program. I get the same thing. It actually is quite creepy and freaked me out. The recording starts playing more and more often the more you take photos and it says like three different things. One of them being CHEESE! lolz...

---

### Post by Jive Turkey on 2010-03-04
was the sound you heard one of these files?

/usr/share/cheese/sounds/shutter0.ogg
/usr/share/cheese/sounds/shutter1.ogg
/usr/share/cheese/sounds/shutter2.ogg
/usr/share/cheese/sounds/shutter3.ogg
/usr/share/cheese/sounds/shutter4.ogg

Even so, you would do well to lock down the VNC somehow.  The freeNX from nomachine is quite a bit better that the default ubuntu VNC in several ways.

---

### Post by fargle on 2010-04-14
LOL glad it turned out - that is rather uncool behavior in Cheese though, I'm glad I didn't hit that when I played with it, because I would have been quite unhappy.

Anyway reminds me of the first time my wife discovered the new functionality in gnome-screensaver to leave a message a couple of years back.  She typed "I can see you" and "I know where you are" and some other things, when I came back and unlocked the messages were there like Post-It notes on my desktop.  Completely freaked me out!  She laughed.  I didn't.

---

