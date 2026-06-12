---
title: "Poll: How many Users when First Installed Ubuntu Knew  Firewall was Off by Default?"
date: 2008-06-04
forum: The Cafe
---

### Post by kevdog on 2008-06-04
This is a first of a two part poll stemming from a discussion in the Security Section.

Poll #1
How many Users when They First Installed Ubuntu knew that Ubuntu's Firewall (iptables) was Turned Off by Default?


Future Poll #2:
How many Users since Installing Ubuntu have installed a listening process or server? (An example would be SSH, FTP, Web (HTTP), Time (NTP) servers?)

---

### Post by 50words on 2008-06-04
I had no idea. I thought Firestarter was just an optional GUI for a service that was already running.

The information out there about security in Ubuntu is not very good for the non-techie user.

---

### Post by klange on 2008-06-04
Heh? All I had to do was add a record and iptables handled it perfectly...

---

### Post by KingTermite on 2008-06-04
I had no idea. I just started Linux and was reading "Ubuntu Linux Bible" (crappy book) and it mentioned that in the security chapter (near end of book).

---

### Post by bufsabre666 on 2008-06-04
i read that in the wiki a long time ago, and ive never turned it on, no need too

---

### Post by Sealbhach on 2008-06-04
I thought you had a to download a Firewall if you wanted one (for Desktop edition).


.

---

### Post by Ozor Mox on 2008-06-04
I thought iptables was on by default, I'm quite surprised at this! Does Ubuntu have no open ports by default or is that only the server?

Also, should I be activating the firewall, or do I not need to worry since I have a router?

---

### Post by dizee on 2008-06-04
When I first installed it, yes I did assume the firewall was on by default.

However, now I know it isn't and it isn't really needed in the same way as it is in Windows because all ports are closed by default.

---

### Post by jonfenton on 2008-06-04
I also thought iptables was set up by default. Mind you I am not sure how much would get past my router.

---

### Post by hyper_ch on 2008-06-04
iptables is setup by default and it is running

however it does not contain any rules and hence does not do any filtering

by default there are no services running upon a fresh installation

---

### Post by mister_pink on 2008-06-04
Yep, this poll is a bit pointless seeing as the questions wrong. The firewall is on by default. There is absolutely no need to do anything to it. 

The only time you'll need it is if you have set up something to listen and you only want to accept connections from certain places. If this is the case the chances are you aren't a complete beginner. 

If, on the other hand, you were a complete beginner, then chances are that having the firewall set to deny all by default would confuse you when you did try to install ssh.

---

### Post by shadylookin on 2008-06-04
I thought it was on there just weren't any rules by default. Not that it matters since all ports were closed by default.

---

### Post by koenn on 2008-06-04
I voted "Yes I knew the Ubuntu firewall - iptables - was deactivated by default"
Actually I didn't know there was I firewall installed by default, I expected that if I'd want a firewall, I'd just have to install it and configure it.
Which is good enough for me, I'm on a private LAN with a perimeter firewall; no need to set up a firewall on each individual host.

---

### Post by kevdog on 2008-06-04
Just an FYI there are no rules set up on the firewall.  All the firewall is technically activated -- a firewall without any rules is equivalent to no firewall at all -- its totally inactive.  If you install openssh server for example -- it listens by default on port 22, and this port is indeed open -- the firewall does no filtering unless a rule is activated.  Open ports are only vulnerable if there is actually a service listening on the particular port.  An open port with no listening process is not a vulnerability.  

From the responses on this forum, this is definitely an area of confusion and misunderstanding for many.

---

### Post by the yawner on 2008-06-04
I'm not sure if I read it right. But on that other operating system, I think there are a couple of opened _and_ listening ports by default. This has to do with how they run their system process. Right?

---

### Post by kevdog on 2008-06-04
Yes there are listening process open by default.  Linux has no listening process to the outside world -- unless you count the ping (icmp packets) which is not blocked by default.  I believe the cups process only listens on the loopback interface.

---

### Post by Mateo on 2008-06-04
> **kevdog said:**
> Yes there are listening process open by default.  Linux has no listening process to the outside world -- unless you count the ping (icmp packets) which is not blocked by default.  I believe the cups process only listens on the loopback interface.

excuse my ignorance, but how does one access the internet without ports for http, pop3, ftp, etc?

---

### Post by BLTicklemonster on 2008-06-04
Well let me ask a question, if my firewall is already running when I install (If I read that correctly); why is it when I go to [www.grc.com](www.grc.com) and go to sheilds up, I get this on my ports:

113 	
IDENT 	
Closed 	Your computer has responded that this port exists but is currently closed to connections.

Is there any way to close that?

---

### Post by LaRoza on 2008-06-04
> **Mateo said:**
> excuse my ignorance, but how does one access the internet without ports for http, pop3, ftp, etc?

They aren't listening. Listening is something like a server which listens on port 80 and responds. Nothing is listening, so it doesn't matter what comes.

---

### Post by LaRoza on 2008-06-04
> **BLTicklemonster said:**
> Well let me ask a question, if my firewall is already running when I install (If I read that correctly); why is it when I go to [www.grc.com](www.grc.com) and go to sheilds up, I get this on my ports:

113 	
IDENT 	
Closed 	Your computer has responded that this port exists but is currently closed to connections.

Is there any way to close that?

Perhaps this will help: [http://www.grc.com/faq-shieldsup.htm#IDENT](http://www.grc.com/faq-shieldsup.htm#IDENT)

---

### Post by Mateo on 2008-06-04
> **LaRoza said:**
> They aren't listening. Listening is something like a server which listens on port 80 and responds. Nothing is listening, so it doesn't matter what comes.

hmm, i guess i understand the distinction then.  i'm still having trouble decipher what *is* listening.  for example, i have apache running, is that listening?  if so, how do I block non-intranet traffic?

---

### Post by lisati on 2008-06-04
To be honest, when I first installed Ubuntu, I didn't know what iptables or firstart were (are?) let alone how to configure them. I haven't bothered researching them in the perhaps misguided belief that the firewalls in the routers (one for wifi & cable, the other disguised as an ADSL modem) are, for the most part, sufficient.

---

### Post by LaRoza on 2008-06-04
> **Mateo said:**
> hmm, i guess i understand the distinction then.  i'm still having trouble decipher what *is* listening.  for example, i have apache running, is that listening?  if so, how do I block non-intranet traffic?

Yes, apache would be listening.

---

### Post by macogw on 2008-06-04
> **kevdog said:**
> just An Fyi There Are No Rules Set Up On The Firewall.  All The Firewall Is Technically Activated -- A Firewall Without Any Rules Is Equivalent To No Firewall At All -- Its Totally Inactive.  If You Install Openssh Server For Example -- It Listens By Default On Port 22, And This Port Is Indeed Open -- The Firewall Does No Filtering Unless A Rule Is Activated.  Open Ports Are Only Vulnerable If There Is Actually A Service Listening On The Particular Port.  An Open Port With No Listening Process Is Not A Vulnerability.  

From The Responses On This Forum, This Is Definitely An Area Of Confusion And Misunderstanding For Many.
Qft

---

### Post by tact on 2008-06-04
I don't know what the fuss is about.

Making such a noise about "...firewall is off by default!" is like making a noise "...the sky is BLUE"

From a sticky on the security discussion page:
**[SIZE=4]_"Firewall_[/SIZE]**

Discussions about firewalls often are passionate (just search the Ubuntu forums). By default, Ubuntu includes a firewall, iptables, but by default nothing is engaged. *This is reasonable as a default Ubuntu install opens **zero** ports to the outside world, so a firewall is redundant.* However, installing "server software" will cause ports to open, so some people like to use a firewall as a catch-all layer to find mistakes in their configuration   [La Rosa]
**[SIZE=4]"[/SIZE]** 

The significant sentence is in italics above.

So where is the fire?  Why the excitement?

Cheers

---

### Post by kevdog on 2008-06-04
I think the crucial part is how many people install server software.  This is probably the most accurate question.  Since take for example a distribution that didn't offer a web browser, but everyone who used the distro downloaded and installed the browser.    Ubuntu may not be default contain any listening server programs, but how many people go ahead and install these anyway?  If the answer is a high number, then wouldn't you think at least the idea of some sort of default firewall be activated (or prompted for activation?)

---

### Post by PrimoTurbo on 2008-06-04
I didn't know, didn't care and if there was a firefox I would of disabled it. I have a router for that.

---

### Post by tact on 2008-06-05
> **kevdog said:**
> I think the crucial part is how many people install server software.  This is probably the most accurate question.  Since take for example a distribution that didn't offer a web browser, but everyone who used the distro downloaded and installed the browser.    Ubuntu may not be default contain any listening server programs, but how many people go ahead and install these anyway?  If the answer is a high number, then wouldn't you think at least the idea of some sort of default firewall be activated (or prompted for activation?)

I think if someone has the smarts to even have a need for a server of any kind, then some more smarts to go install and configure same - that person ought to be clever enough to know his exposure.

A computer without a firewall does not equal a car sold without brakes.  Its no travesty of safety or neglect of duty.

Its just not possible to save people from themselves.  You mention the idea of trying to ensure that if someone installs something that opens up a port they are prompted to configure their firewall...  where do you stop?    

Is the next step having usb ports disabled by default until the user reads a safety bulletin and passes a test to show thy understand the risks (possibility of a virus infection just plugging in a thumbdrive or picture frame) - all for their own safety of course.

NoooOOOOooooooooOOOOooOooooooo  :)

---

### Post by scorp123 on 2008-06-05
> **tact said:**
>  I think if someone has the smarts to even have a need for a server of any kind, then some more smarts to go install and configure same - that person ought to be clever enough to know his exposure.  Yes, they ought to know ... but often enough they don't. The excuse here being "But I just want to use this computer, not study computer science ... !"

> **tact said:**
>  Its just not possible to save people from themselves. True.

> **tact said:**
>    You mention the idea of trying to ensure that if someone installs something that opens up a port they are prompted to configure their firewall...  where do you stop?  Right there? Most distros (openSUSE, Mandriva, Fedora ...) ship with their firewalls turned on and with filtering activated. The SUSE installer offers the option to disable it during the installation (so people who know what they do don't have to bother with it any further than that) and I guess most other distros have similar options. I fail to see why this could not be done for Ubuntu as well? The installer would ask you if you wanted a firewall ... Click "No" and you get the current behaviour. Click "Yes" and a default ruleset will limit all services to your own RFC1918 private IP range. If a newbie still wants to play around with stuff such as Apache and MySQL and so on they can still do so without exposing themselves too much. People who know what they do and who want the current behaviour simply turn off the thing during the installation, voila done.

I can't see why this should be such a big problem here? :)

I know -- in Ubuntu's default setting (= no service that is listening for anything) such a firewall would not be of much use. But then again: Ubuntu's motto is "Linux for human beings" and some people here on these forums seem to feel 'naked' without firewall ... so why not satisfy their needs and offer the rest of us the option to easily turn the thing off during install? Shouldn't really be too much of a problem I guess and voila, both sides of the argument get what they want.

---

### Post by samjh on 2008-06-05
For me, I thought iptables was deactivated by default, only to find that it was active but without filtering rules set.

It doesn't really matter unless you're running a server anyway, and if you have need to run a server, then you should do your homework and learn to set up security appropriately.

A person who run servers without knowing about network security, is like someone who tries to drive a bus without knowing how.

---

### Post by D.Sync on 2008-06-05
Eh? Is there any firewall software installed on Ubuntu? Never thought and worry about it though. :)

---

### Post by klange on 2008-06-05
> **D.Sync said:**
> Eh? Is there any firewall software installed on Ubuntu? Never thought and worry about it though. :)

iptables comes preinstalled and is *active*. It just has no rules.

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-05
iptables is the Ubuntu Firewall and it is always active. It just doesn't do anything if there are no virus definitions or restrictions. Basically, it's IDLE. Not off, IDLE.

Armageddon

---

### Post by mister_pink on 2008-06-05
How about another question then. How many people using ubuntu have had their computer hacked whilst using the default config? 

None?

Right then.

As for installing listening servers? How many people do that? Not even 10% I'll bet. I don't suppose most people have even heard of ssh, and if they have they should be able to deal with the firewall - if they even need it! You do not need to do anything to the firewall if you want ssh to accept connections from anywhere. It's far more important to get your ssh rules correct.

---

### Post by tigrezno on 2008-06-05
first time i installed ubuntu (about 3 weeks ago), first thing i did was on console:

sudo netstat -nlp

to check what i was sharing with my internet hackers :)

then i checked that ubuntu default installation don't carry any firewall GUI, so i installed firestarter.

---

### Post by BLTicklemonster on 2008-06-05
> **LaRoza said:**
> Perhaps this will help: [http://www.grc.com/faq-shieldsup.htm#IDENT](http://www.grc.com/faq-shieldsup.htm#IDENT)

Yeah, I read that, but I WANT TO SHOW UP STEALTHY, dangit!

:)

---

### Post by hyper_ch on 2008-06-05
> **tigrezno said:**
>  so i installed firestarter.

firestarter IS NOT a firewall

---

### Post by scorp123 on 2008-06-05
> **hyper_ch said:**
> firestarter IS NOT a firewall Ahemm ... Usually you'd be right but please see his posting again :) ... he talked about "firewall GUI" ;)  And "firestarter" is just that ;)

---

### Post by Dr Small on 2008-06-05
Ubuntu at least has iptables installed, but since there are no services listening, no need to open any ports. On Arch, I would have to install iptables (if I wanted it), but see no use for it when I am already behind a firewall.

---

### Post by aysiu on 2008-06-05
> **scorp123 said:**
> Yes, they ought to know ... but often enough they don't. The excuse here being "But I just want to use this computer, not study computer science ... !" If you don't want to study computer science, don't make your computer a server.

Seriously.

Take me, for example. I don't want to study computer science, and I don't mess with IP tables. And, lo and behold, I also never make my computer a server.

I just want to use the computer. So I use the web browser, email, word processor, etc. I use sensible software targeted at end-users, not server software targeted at network administrators.

---

### Post by hyper_ch on 2008-06-05
> **scorp123 said:**
> Ahemm ... Usually you'd be right but please see his posting again :) ... he talked about "firewall GUI" ;)  And "firestarter" is just that ;)

Sorry :(:(:(:(:(

---

### Post by billgoldberg on 2008-06-05
I knew, but I don't have the firewall active.

I have a hardware firewall.

Not having a firewall on the computers is easier for my upnp network.

---

### Post by scorp123 on 2008-06-05
> **aysiu said:**
> If you don't want to study computer science, don't make your computer a server. Seriously.  I know :D  But you see ... I had such discussions before and then the next argument usually is "What good is the openness of Linux if God forbid that one tinkers with it???" :lolflag:

If all users accepted the fact that on UNIX-ish operating systems they assume full responsibility for everything they do or don't do (because the OS will assume exactly that! No matter how stupid the command was you just typed in: you are the user, you're the one with the 1+ billion brain cells, you *have to* know what you do!) then we wouldn't have such discussions I guess :D

---

### Post by koenn on 2008-06-05
> **aysiu said:**
> If you don't want to study computer science, don't make your computer a server.

Seriously.

I agree, sort of.
On the other hand, anything that accepts incoming connections is technically a server. That includes openssh-server and remote desktops (so you can connect to your own PC from a remote location), sharing files from your PC to other PC's, to setting up a web server and the likes. Reading these forums, it looks as if just about averybody is doing at least 1 of those. 

I fully agree that people shouldn't be doing stuff like that, especially not if they also want to provide those services to or over the internet, unless they know what they're doing and understand the security issues involved.  (I hate those "how do I set up samba so I can share files with my friends over the internet" threads)

Yet, it happens, and a firewall would help (a bit) to keep it secure.
It would also provide a false sense of security : you need to open up ports in your firewall for servers to actually be accessible, so it's back to square 1 :  you need to know what you're doing, or 
- you open up too much on your firewall just to make sure everythiong works.
- you neglect other security practices, so alowing people access to 1 service gives them enough room to start messing around, elevate their priviligues, access stuff you didn't intend them to have access to, etc. 

I'm undecided about whether having a firewall on by default is a good idea. 
But allowing any form of remote access without understanding the consequences is definitively a bad idea.

---

### Post by ad_267 on 2008-06-12
If I've installed apache2 and mysql for testing websites locally is there something I need to do to configure iptables?

---

### Post by kevdog on 2008-06-12
All ports are open by default -- so you shouldn't run into any problems.  If you need to restrict access, such as to your local LAN or specific computers, this would be the role of altering the iptables.

---

### Post by ad_267 on 2008-06-12
> **kevdog said:**
> All ports are open by default -- so you shouldn't run into any problems.  If you need to restrict access, such as to your local LAN or specific computers, this would be the role of altering the iptables.

OK so there aren't any security risks involved with running apache and mysql without configuring iptables?

---

### Post by kevdog on 2008-06-13
Well that depends..

If you are behind a NAT/router, and you don't have any port forwards setup to the internal http server, then your risk would be minimal unless you fear other computers on the LAN.

If you really wanted to lockdown apache, then you could either configure it to filter access, or you could use a firewall for such  purposes.  Again firewalls just block access, limit access, etc.  They just packet filter, redirect packets, etc.  They dont authenticate -- this would need to be done with Apache.  It just depends on what your needs are.

---

### Post by ad_267 on 2008-06-13
> **kevdog said:**
> Well that depends..

If you are behind a NAT/router, and you don't have any port forwards setup to the internal http server, then your risk would be minimal unless you fear other computers on the LAN.

If you really wanted to lockdown apache, then you could either configure it to filter access, or you could use a firewall for such  purposes.  Again firewalls just block access, limit access, etc.  They just packet filter, redirect packets, etc.  They dont authenticate -- this would need to be done with Apache.  It just depends on what your needs are.

Ok thanks, I guess I should be fine then.

---

### Post by keiichidono on 2008-06-14
I thought the firewall was on by default but by reading this thread i understand that i don't need one and that it is idle as it has no rules set which is only needed for a server.

---

### Post by Skorzen on 2008-06-14
I thought the Ubuntu firewall was on by default!

---

### Post by RedMartin on 2008-06-14
> **tigrezno said:**
> first time i installed ubuntu (about 3 weeks ago), first thing i did was on console:

sudo netstat -nlp

to check what i was sharing with my internet hackers :)

then i checked that ubuntu default installation don't carry any firewall GUI, so i installed firestarter.

After doing the netstat -nlp thing what results did you get and what should I be looking for?

---

### Post by kevdog on 2008-06-14
You just want to check for listening processes since this will tell you if you have an open port with a listening process behind it.  Post what you have if you don't understand.

---

### Post by RedMartin on 2008-06-15
[quote=kevdog]You just want to check for listening processes since this will tell you if you have an open port with a listening process behind it. Post what you have if you don't understand.[/quote]

This is what is see with sudo netstat -nlp.


Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5351/cupsd      
udp        0      0 0.0.0.0:68              0.0.0.0:*                           5728/dhclient   
udp        0      0 0.0.0.0:5353            0.0.0.0:*                           5318/avahi-daemon: 
udp        0      0 0.0.0.0:56685           0.0.0.0:*                           5318/avahi-daemon: 
Active UNIX domain sockets (only servers)
Proto RefCnt Flags       Type       State         I-Node   PID/Program name    Path
unix  2      [ ACC ]     STREAM     LISTENING     14079    5714/gdm            /var/run/gdm_socket
unix  2      [ ACC ]     STREAM     LISTENING     13108    5424/winbindd       /tmp/.winbindd/pipe
unix  2      [ ACC ]     STREAM     LISTENING     14117    5721/X              /tmp/.X11-unix/X0
unix  2      [ ACC ]     STREAM     LISTENING     14553    5951/gconfd-2       /tmp/orbit-martin/linc-173f-0-73afb49160b6a
unix  2      [ ACC ]     STREAM     LISTENING     14563    5958/gnome-keyring- /tmp/orbit-martin/linc-173d-0-4cae673e713f1
unix  2      [ ACC ]     STREAM     LISTENING     14801    5958/gnome-keyring- /tmp/keyring-7qSRVx/socket
unix  2      [ ACC ]     STREAM     LISTENING     14803    5958/gnome-keyring- /tmp/keyring-7qSRVx/ssh
unix  2      [ ACC ]     STREAM     LISTENING     14805    5958/gnome-keyring- /tmp/keyring-7qSRVx/socket.pkcs11
unix  2      [ ACC ]     STREAM     LISTENING     15204    6049/seahorse-agent /tmp/orbit-martin/linc-1747-0-6699ee5f79060
unix  2      [ ACC ]     STREAM     LISTENING     15235    5959/gnome-session  /tmp/seahorse-IPYAPu/S.gpg-agent
unix  2      [ ACC ]     STREAM     LISTENING     15278    5959/gnome-session  /tmp/orbit-martin/linc-1747-0-7c28ac71d36ff
unix  2      [ ACC ]     STREAM     LISTENING     15282    5959/gnome-session  /tmp/.ICE-unix/5959
unix  2      [ ACC ]     STREAM     LISTENING     15443    6054/gnome-settings /tmp/orbit-martin/linc-17a6-0-14bf25db386da
unix  2      [ ACC ]     STREAM     LISTENING     19044    6086/pulseaudio     /tmp/.esd-1000/socket
unix  2      [ ACC ]     STREAM     LISTENING     19050    6086/pulseaudio     /tmp/pulse-martin/native
unix  2      [ ACC ]     STREAM     LISTENING     12825    5255/dbus-daemon    /var/run/dbus/system_bus_socket
unix  2      [ ACC ]     STREAM     LISTENING     19115    6166/gconf-helper   /tmp/orbit-martin/linc-1816-0-10acb0f47ee01
unix  2      [ ACC ]     STREAM     LISTENING     19417    6311/gnome-screensa /tmp/orbit-martin/linc-18a6-0-38b880b8bdb32
unix  2      [ ACC ]     STREAM     LISTENING     19586    6322/gnome-panel    /tmp/orbit-martin/linc-18b2-0-4aceb79123a70
unix  2      [ ACC ]     STREAM     LISTENING     19641    6321/nautilus       /tmp/orbit-martin/linc-18b1-0-4aceb79138d7c
unix  2      [ ACC ]     STREAM     LISTENING     19720    6326/bonobo-activat /tmp/orbit-martin/linc-18b6-0-631b3fd463b05
unix  2      [ ACC ]     STREAM     LISTENING     20569    6387/update-notifie /tmp/orbit-martin/linc-18f3-0-38df781a74c9a
unix  2      [ ACC ]     STREAM     LISTENING     20575    6426/gnome-power-ma /tmp/orbit-martin/linc-18f1-0-38df781a75ad9
unix  2      [ ACC ]     STREAM     LISTENING     20618    6429/gnome-volume-m /tmp/orbit-martin/linc-18fe-0-565e29619ed3d
unix  2      [ ACC ]     STREAM     LISTENING     20638    6384/compiz.real    /tmp/orbit-martin/linc-18f0-0-4832f9d3c1028
unix  2      [ ACC ]     STREAM     LISTENING     21775    6540/firefox        /tmp/orbit-martin/linc-198c-0-29e89fee1e050
unix  2      [ ACC ]     STREAM     LISTENING     13864    5635/hcid           /var/run/sdp
unix  2      [ ACC ]     STREAM     LISTENING     20690    6400/nm-applet      /tmp/orbit-martin/linc-1900-0-5ebee57255e7a
unix  2      [ ACC ]     STREAM     LISTENING     20988    6478/trashapplet    /tmp/orbit-martin/linc-194e-0-2fb95c0fb1eb0
unix  2      [ ACC ]     STREAM     LISTENING     21109    6494/gtk-window-dec /tmp/orbit-martin/linc-195e-0-1d876c0356a11
unix  2      [ ACC ]     STREAM     LISTENING     21196    6500/mixer_applet2  /tmp/orbit-martin/linc-1964-0-794cfd2d37d2d
unix  2      [ ACC ]     STREAM     LISTENING     21217    6497/gnome-brightne /tmp/orbit-martin/linc-1961-0-794cfd2d57ba7
unix  2      [ ACC ]     STREAM     LISTENING     22792    6708/evolution-data /tmp/orbit-martin/linc-1a34-0-4e40ce7749615
unix  2      [ ACC ]     STREAM     LISTENING     22857    6712/evolution-exch /tmp/orbit-martin/linc-1a38-0-4e40ce77ab234
unix  2      [ ACC ]     STREAM     LISTENING     23442    6812/gnome-terminal /tmp/orbit-martin/linc-1a9c-0-6a7c060bb7e3a
unix  2      [ ACC ]     STREAM     LISTENING     13110    5424/winbindd       /var/run/samba/winbindd_privileged/pipe
unix  2      [ ACC ]     STREAM     LISTENING     12606    5063/acpid          /var/run/acpid.socket
unix  2      [ ACC ]     STREAM     LISTENING     13918    5656/bluetoothd-ser @/org/bluez/audio
unix  2      [ ACC ]     STREAM     LISTENING     13866    5635/hcid           @/var/run/dbus-KcLnd8DBcO
unix  2      [ ACC ]     STREAM     LISTENING     12916    5318/avahi-daemon:  /var/run/avahi-daemon/socket
unix  2      [ ACC ]     STREAM     LISTENING     12957    5351/cupsd          /var/run/cups/cups.sock
unix  2      [ ACC ]     STREAM     LISTENING     13145    5488/hald           @/var/run/hald/dbus-XHnslFeT4F
unix  2      [ ACC ]     STREAM     LISTENING     13162    5488/hald           @/var/run/hald/dbus-oe4z0BhaSU
unix  2      [ ACC ]     STREAM     LISTENING     15296    6053/dbus-daemon    @/tmp/dbus-Tj77tbr6Ha
martin@martin-laptop:~$

---

### Post by kevdog on 2008-06-15
These are your listening processes:

tcp 0 0 127.0.0.1:631 0.0.0.0:* LISTEN 5351/cupsd
udp 0 0 0.0.0.0:68 0.0.0.0:* 5728/dhclient
udp 0 0 0.0.0.0:5353 0.0.0.0:* 5318/avahi-daemon:
udp 0 0 0.0.0.0:56685 0.0.0.0:* 5318/avahi-daemon: 

cups is only listening on the lo interface. Your dhclient is for your router.  Im not an expert with avahi, however that is the only other listening process.  Perhaps someone could shed light on whether avahi represents a possible security risk.

---

### Post by scorp123 on 2008-06-15
As I wrote above ... 
```
sudo lsof -n -i -P | grep LISTEN
``` ... this gives much nicer and less confusing output ;)

---

### Post by RedMartin on 2008-06-18
> **scorp123 said:**
> As I wrote above ... 
```
sudo lsof -n -i -P | grep LISTEN
``` ... this gives much nicer and less confusing output ;)

In that case, how does this look?

cupsd     5150  root    2u  IPv4  12985       TCP 127.0.0.1:631 (LISTEN)

---

### Post by ma_nkooo on 2008-06-18
Thne how can I turn it on?

---

### Post by aysiu on 2008-06-18
> **ma_nkooo said:**
> Thne how can I turn it on?
It is on. It's just not blocking anything right now, because there's nothing to block.

Are you running an OpenSSH Server, FTP server, or Apache?

---

### Post by ma_nkooo on 2008-06-18
> **aysiu said:**
> It is on. It's just not blocking anything right now, because there's nothing to block.

**Are you running an OpenSSH Server, FTP server, or Apache?**no.

---

### Post by kevdog on 2008-06-19
If you are not running any listening processes (which would include samba), then a firewall aint going to do you much good) -- or you are not sharing your internet connection -- that would be yet another scenario where a firewall would be helpful.  It doesnt seem like this describes your situation however.

---

