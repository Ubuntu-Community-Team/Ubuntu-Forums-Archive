---
title: "hacker redirecting my browser ?"
date: 2007-11-23
forum: Server Platforms
---

### Post by firedancer on 2007-11-23
hi, i'm having some , trouble after cleaning xp pc, i wasn't able to reach my debian server neither my kubuntu desktop
the xp pc is still being bugged ,as you can read , and i'll have to reinstall xp there, 
but i wasn't able to download anything usingon my pc neither  firefox which i installed on kubuntu, meaning browser was also hijacked ?
and when i sudo apt-get nmap, i had firestarter setup to monitor everything , no first did a netstat noticed a ip which wasn't suppose to be connected, 
while installing i noticed one "entry" with strange characters where basic canonical info has to be , 
well i just finished reinstalling kubuntu , cause can't trust that.
what can i do in this situation , for now i'm not going to use that pc to see if my website/server is doing ok, 
but now for myself, my pc and security. well i have the suspcious static ip , when i try it , i reach the same bogus error page like when i use the xp pc, so there is a connection,  
later on i'll use the program to dissect the network , forgot the name , and i''l try monitoring him then , i used it once , 
i don't know what to do , another linux forum which i'm a registered too also,giving no replies at all,   
and i'm just getting to learn the trade , about networking , was gonna set up an kubuntu webserver , and some development stuff, but now this is taking all my time , i still have to send in a teacherspractice schedule, and can't finish, cause this got me busy,  
if anyone has a suggestion , it 'll be appreciated, 
firedancer

---

### Post by MJN on 2007-11-23
> **firedancer said:**
> i don't know what to do , another linux forum which i'm a registered too also,giving no replies at all, 

I'm not surprised! I couldn't make head nor tail of your post - just a whole bunch of words and commas! :o

Can you elaborate in no more than one or two sentences what your problem is?

I strongly recommend reading [http://www.catb.org/~esr/faqs/smart-questions.html]("http://www.catb.org/%7Eesr/faqs/smart-questions.html") as if you heed the advice it'll help us to help you.

Mathew

---

### Post by firedancer on 2007-11-23
how can i avoid that my own browser is being hijacked, 
 
thank you, 

firedancer

---

### Post by firedancer on 2007-11-23
reading rite now 

thank you very much

---

### Post by mellowd on 2007-11-23
Still a bit difficult to understand exactly your problem. Could you start from the beginning and explain exactly what happened and when? From there we'll be able to come to some conclusion

---

### Post by firedancer on 2007-11-23
i use some one xp box to see if my site/server is doing ok and how looks
the owner checked her bankaccount a week ago and the next morning , it was flooding malware, adware, with trojan busky, used to compromise ppl their pc for data,info,credit card ,etc

cause i use it , i helped cleaning it , i ran ubuntu a couple of nites until her son was "demanding" xp to play his online game 

after two days it was done , pc looked alrite , 
i did something stupid though , i went on dubious sites to test spybot , i know not a good idea, after running scan ,it was still clean

the next day however the only website IE 8 would not go on was mine (debian server)

i tried other methods and suddenly i was able to ,until reboot, now it's even worse, wont go on sites to get security stuff nor drivers 

but what seems odd is that , when i tried to get on those sites myself from my kubuntu desktop which uses the same router (only one connection) , i was getting the same problems as above 

netstat -a showed me these ip 192.198.164.16 and 192.198.164.161 , and this was after i  closed firefox  , so it's not an ip from site i was on i thought 

then i apt-get install nmap , netstat showed that ip was still  
connected, i tried these ip's and got the "error page"  as when i tried going on specific sites as mentioned above

and as last , this is some what difficult to explain, 
but while installing nmap , i monitored it with firestarter also

and you can see what is being installled and from where it comes, well there was one line with strange characters,

after i finished installing nmap, i wasn't able to browse the web anymore 

hence the question , is browser hijacking also a linux vulnerabilty
and should i take some security measures

i'm sorry , if it's still not clear , 

english is not my first language , so i try my best , 


thanx for the attention, appreciate it alot

---

### Post by MJN on 2007-11-23
I think it's becoming a little clearer - thank you for making the effort to clarify the situation.

The way I am understanding it is that you've got two PCs - one running Kubuntu and the other running XP ...? And they are both connected to the Internet via the same router?

Are you saying that neither machine will connect to the Internet, or at least the browser on each machine won't connect to any websites?

Those two IP addresses belong to Intel - were you browsing an Intel site at any time?

At your console prompt on your Linux machine, try running **dig google.com **and post the output. This will perform some DNS queries which will confirm whether or not you're able to connect to the Internet and at least send and receive packets satisfactorily. It will also demonstrate whether or not your connection is configured to support DNS which is a fundamental requirement for general web browsing.

Mathew

---

### Post by firedancer on 2007-11-23
no , sorry , 

the xp pc is the neighbour's , 

and i can acces the web from my pc now, after reinstalling kubuntu, 

the questions can my webbrowser be hijacked/used by someone else, 

yes i was on intel sites to download the drivers (for the lady who own the other pc)   

i have no problems now, i think it has everything to do with the xp pc and vulnerability and not so much to do with my debian server

i will ask others to check my site to see wether they can acces it 

would like post mysite here  , but i' using the same  router with one connection , busy with dnsmasq and ipmasq , almost there (off topic) so it's either kubuntu or headless debian server to surf the web 

thanx for the reply , but it still isn't clear if browserhijacking is something that happens if using a linux os (i believe it's possible)


i think , my worries are some what over

---

### Post by savage on 2007-11-23
This sounds similar to a problem I had a few months back, although they may not be related at all. However I would suggest starting with your cable/dsl modem since the problem is appearing on all your machines. Try power cycling the modem (unplugging then plugging back in the device), if that has no effect then try resetting (which will clear all your modems settings), so you may want to back it up first. The owners manual will come in handy here. Make sure you have your username/password type information written down.

What I was experiencing was some sort of DNS pollution. I still haven't researched it in full, but the Actiontec modem I have passes bad DNS information to my machines on the network. To work around it I had to convince my computers to get their DNS information straight from my ISP's (Qwest) servers instead of using the DSL modem as an intermediary. When this first happened I thought I had been hacked by some sort of "man in the middle" attack. If you open up a command line *under gnome* (Main Menu > Accessories > Terminal) and then type (without the dollar sign):
$ dig google.com

You should get something similar to what is below.

```

$ dig google.com

; <<>> DiG 9.3.2 <<>> google.com
;; global options:  printcmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 41454
;; flags: qr rd ra; QUERY: 1, ANSWER: 3, AUTHORITY: 4, ADDITIONAL: 4

;; QUESTION SECTION:
;google.com.                    IN      A

;; ANSWER SECTION:
google.com.             208     IN      A       64.233.167.99
google.com.             208     IN      A       72.14.207.99
google.com.             208     IN      A       64.233.187.99

;; AUTHORITY SECTION:
google.com.             82012   IN      NS      ns3.google.com.
google.com.             82012   IN      NS      ns2.google.com.
google.com.             82012   IN      NS      ns4.google.com.
google.com.             82012   IN      NS      ns1.google.com.

;; ADDITIONAL SECTION:
ns1.google.com.         10180   IN      A       216.239.32.10
ns2.google.com.         185253  IN      A       216.239.34.10
ns3.google.com.         12462   IN      A       216.239.36.10
ns4.google.com.         12462   IN      A       216.239.38.10

;; Query time: 53 msec
;; SERVER: 205.171.3.65#53(205.171.3.65)
;; WHEN: Fri Nov 23 13:49:23 2007
;; MSG SIZE  rcvd: 212

```Now you will notice that in the line that starts with ;;SERVER, that it has 205.171.3.65. This is my ISP's DNS server. If your results from dig show something like 192.168.0.xxx, 10.10.90.xxx, 192.168.1.xxx, where the x could be 1 or something else then that means that your DNS information is coming from your modem. Furthermore if you are experiencing "DNS pollution" then you will see very strange entries in the ns.google.com areas such as hackfun.google.com, entries that google would not have there.

A simpler way to see what your computer is using for DNS information is to run the following command from the terminal (again without the dollar sign):
$ cat /etc/resolv.conf

Mine produces this:

search domain.actdsltmp
nameserver 205.171.3.65

If that nameserver line is 192.168.0.xxx, 192.168.1.xxx, or 10.10.90.xxx then your modem is serving DNS instead of your ISP's DNS servers.

Applications that you will find helpful for network troubleshooting are:
Main Menu > Administration > Networking
Main Menu > Administration > Network Tools

From the terminal/command line:
ping
ifconfig
iwconfig
ifup
ifdown
tracepath
traceroute
netstat
dig
nmap

You may also want to use the apropos command from the terminal:
$ apropos network
$ apropos dns

Files and directories related to networking, and which you can read by using:
$ cat <filename>
or
$ less <filename>

/etc/dhclient-exit-hooks
/etc/dhcp3
/etc/host.conf
/etc/hosts
/etc/network
/etc/resolv.conf

The most important of the above files will probably be /etc/resolv.conf and /etc/network/interfaces. If you start fiddling with these files make sure to make a backup of them, for example, using:
$ sudo cp /etc/resolv.conf /etc/resolv.bak

Last of all if you are going to be editing files from the command line then you will need an editor, pico is probably the best if you haven't done this before. Another helpful command is man so:
$ man pico
use "q" to exit the man page
$ sudo cp /etc/resolv.conf /etc/resolv.bak
$ sudo pico /etc/resolv.conf

You will probably want to look into these following posts, if this is indeed the issue. Good luck.

[https://help.ubuntu.com/community/StaticDnsWithDhcp](https://help.ubuntu.com/community/StaticDnsWithDhcp)
[http://ubuntuforums.org/showthread.php?p=116857#post116857](http://ubuntuforums.org/showthread.php?p=116857#post116857)

---

### Post by firedancer on 2007-11-23
thank you very much savage, 

my modem indeed was acting strange at times, i just didn't wanted to ask too much , since i wasn't being clear, about one problem  

i'm a bit familiar with the terminal , so this helps alot 

appreciated alot , once again thank you all


firedancer

---

### Post by firedancer on 2007-11-26
well in the log of my dslmodem it says "detected ip spoofing" and my ip numbers was in between the range , 

i noticed slow updating , and a few failures, 

i know it;s not all related ,but can spoofing slow down your network traffic , 

maybe all the problems i'm having have to do with someone who doesn't seem to like me or theirselves

:mad:

---

