---
title: "hardy &amp; Tor"
date: 2008-06-13
forum: Security
---

### Post by danuk88 on 2008-06-13
Hi I am using ubuntu hardy I have installed tor and Vidalia using the following command

sudo aptitude install tor privoxy

sudo aptitude install vidalia

I have also added these repositories into 3rd Party Repositories 

deb [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) hardy main

Tor loads up all and good but do I have to change any settings on fire fox to get it to work? As I don’t think fire fox is running through tor and do I have to install fire starter to open any ports?

This is my first post sorry for any stupid questions.

Thanks
Dan

---

### Post by dazfuller_uk on 2008-06-13
Have a look at running the FoxyProxy, it's got a wizard which will help you set up tor

---

### Post by garymc1 on 2008-06-14
i am using hardy and tor i have got FoxyProxy installed on firefox i want to set up a relay what ports do i have to open ? 9001 & 9030 ?

thanks 
gary

---

### Post by satellite360 on 2008-06-17
This works for me:

  1. Run the command: sudo apt-get install tor privoxy
  2. Run the command: sudo gedit /etc/privoxy/config
  3. Add the line (including the period at the end): forward-socks4a / localhost:9050 .
  4. Comment out the line: logfile logfile
  5. Comment out the line: jarfile jarfile
  6. Restart the Privoxy service: sudo /etc/init.d/privoxy restart
  7. Install the Firefox torbutton extension

---

### Post by yizuman on 2008-06-23
> 4. Comment out the line: logfile logfile
5. Comment out the line: jarfile jarfile

What do you mean "comment out"? is that the same as remove or delete?

---

### Post by Enlitend on 2008-06-23
> **yizuman said:**
> What do you mean "comment out"? is that the same as remove or delete?

you "comment out" by putting a pound sign " # " in front of that line.
hope this help.

---

### Post by jojojo on 2008-07-12
Please help!

I cannot install *Tor* although I did sudo aptitude install tor privoxy.

This appears when I try that:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



Can anybody help me and tell me what to do??

---

### Post by mriedel on 2008-07-12
> **jojojo said:**
> Please help!

I cannot install *Tor* although I did sudo aptitude install tor privoxy.

This appears when I try that:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?



Can anybody help me and tell me what to do??

Close all running package management software processes (dpkg, apt-get, aptitude, synaptic...), then

```
sudo apt-get install tor
```

---

### Post by jojojo on 2008-07-12
MRiedel,

I tried what you suggested!

It worked!!!

You know, I was Googling how to do it, and they told me to add deb [http://mirror.noreply.org](http://mirror.noreply.org) etc. etc. in my /etc/apt/sources.list and all that. And then sudo apt-get update. And it didnt work. 

Your suggestion above worked perfectly... I didn't know it was that easy!

Thank you so much :):)

---

### Post by jojojo on 2008-07-12
Just one last question:

What do I do next?

This is what happened after I did what u said:

------------------------------------
me@me:~$ sudo apt-get install tor
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsnack2 tcltls tcl tcl8.4 tcl8.5 tk8.5
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libevent1 tsocks
Suggested packages:
  mixmaster mixminion anon-proxy
Recommended packages:
  privoxy polipo socat
The following NEW packages will be installed:
  libevent1 tor tsocks
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 1266kB of archives.
After this operation, 2765kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  tor
Install these packages without verification [y/N]? y
Get:1 [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main tor 0.1.2.19-3~hardy+1 [966kB]
Get:2 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/main libevent1 1.3e-1 [44.8kB]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) hardy/universe tsocks 1.8beta5-6 [255kB]   
Fetched 1266kB in 6s (183kB/s)                                                       
Selecting previously deselected package libevent1.
(Reading database ... 120792 files and directories currently installed.)
Unpacking libevent1 (from .../libevent1_1.3e-1_i386.deb) ...
Selecting previously deselected package tsocks.
Unpacking tsocks (from .../tsocks_1.8beta5-6_i386.deb) ...
Selecting previously deselected package tor.
Unpacking tor (from .../tor_0.1.2.19-3~hardy+1_i386.deb) ...
Setting up libevent1 (1.3e-1) ...

Setting up tsocks (1.8beta5-6) ...
Setting up tor (0.1.2.19-3~hardy+1) ...
Raising maximum number of filedescriptors (ulimit -n) to 8192.
Starting tor daemon: tor...
Jul 13 01:08:58.386 [notice] Tor v0.1.2.19. This is experimental software. Do not rely on it for strong anonymity.
Jul 13 01:08:58.389 [notice] Initialized libevent version 1.3e using method epoll. Good.
Jul 13 01:08:58.389 [notice] Opening Socks listener on 127.0.0.1:9050
done.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
me@me:~$ 
------------------------------------------------


Do I have to reboot my computer?

---

### Post by mriedel on 2008-07-12
There is no need to reboot your computer. The tor daemon is running and you can now use it. If you want to browse anonymously, try torbutton or foxyproxy, both firefox add-ons. Before assuming you're anonymous, I strongly advise you to read up about anonymity and how to achieve it on [torproject.org](torproject.org).

Tor is on the official ubuntu repositories though, there's no need to use mirror.noreply.org. To remove it from the list of repositories apt-get/aptitude/synpatic uses, type

```
gksudo gedit /etc/apt/sources.list
```

and delete the line you added before. It should read:

```
deb http://mirror.noreply.org
```

---

### Post by jojojo on 2008-07-12
Done!

Thank you once again for your time and help, my faraway friend! :)

---

### Post by bla on 2008-07-12
satellite360 gave good instructions but there is a problem with this method.
In windows land, there is a GUI that comes with Tor. It shows you live the connections you make, a map, etc.  More importantly, you are able to make new connections when the ones you are stuck on are too slow.  None of this is available following those (official) instructions.

So I have to ask.  Is there a way to get the same functionality on Ubuntu as on Windows?

---

### Post by Dr Small on 2008-07-12
No, this GUI does not come with Tor on Windows. This is another program called Vidalia, which operates Tor. Tor itself is a command line daemon.

You may be able to find Vidalia for Ubuntu though, as I think I have heard it mentioned.

[http://vidalia-project.net/download.php](http://vidalia-project.net/download.php)

Check the Repositories first though.

---

### Post by bla on 2008-07-12
^Yes, that sounds right.  I'm a linux newb, if anyone gets the vidaliaTor bundle to work, let us know.

---

### Post by mriedel on 2008-07-13
Vidalia runs fine on ubuntu (i hear) but you'll probably have to compile from source or try the tool *alien* to covern the rpm to a deb.

---

### Post by hehe22 on 2008-07-13
yeah, very good!

---

### Post by adamogardner on 2008-08-13
> **satellite360 said:**
> This works for me:

  1. Run the command: sudo apt-get install tor privoxy
  2. Run the command: sudo gedit /etc/privoxy/config
  3. Add the line (including the period at the end): forward-socks4a / localhost:9050 .
  4. Comment out the line: logfile logfile
  5. Comment out the line: jarfile jarfile
  6. Restart the Privoxy service: sudo /etc/init.d/privoxy restart
  7. Install the Firefox torbutton extension

hi what does it mean to "comment out the line?"  Please explain. Drawings help too.  Also, a window told me I don't need Privoxy after firefox something or another.  Do I want it?  I'm just starting to try and configure this stuff. Ok thanks for advising - over to you.

---

### Post by adamogardner on 2008-08-13
> **mriedel said:**
> Vidalia runs fine on ubuntu (i hear) but you'll probably have to compile from source or try the tool *alien* to covern the rpm to a deb.

how do I do that?

---

### Post by wiseguy on 2008-08-13
> **adamogardner said:**
> how do I do that?

sudo apt-get install alien
sudo alien -i /path/to/file.rpm

---

### Post by adept_king on 2008-08-29
i thought i was up to the challenge to untangle the intricacies of tor/ip, but i was wrong.  there is just TOO MUCH stuff to know.  i would have to dedicate my life to linux to make it work, thats how it feels.  its a full time all day long study to make linux work, coming from easy street (xp.)

now, i find that i cannot actually uninstall tor.  

i cant even find it in synaptic or add/remove.  i am experiencing 2 minutes of desktop freeze during shut down and after the desktop goes away, i see some text about "stopping tor daemon" as shutdown actually starts to occur.  im thinking this is the cause of alot of my system sluggishness.

am i missing a major, major concept here?

googling "remove tor daemon ubuntu" yields nothing.

i just searched my file system, and sure enough, tor is there.
when i run tor, it starts.  what gives?  where am i going wrong?  where's the beginning of the beginning?  how can one actually see what's installed if its not reflected in gnome?  better yet, how do you remove a program if you dont know where to look for it, or even if its installed at all, or just partially?

long story short, how to undo all the privoxy and tor changes to the point before i started?  can i just go and manually delete all files and folders named 'tor?'  

there's alot of tor stuff in the 'etc' folder

---

EDIT:

Using KDE's Adept Manager, I was able to find both Tor and Privoxy.  I deleted these and my computer runs alot smoother.  Especially during shut-down.  Neither of these two programs were showing up in synaptic which is strange because now that i uninstalled them they show up after a search. (uninstalled, thankfully)

---

### Post by hloupy on 2008-09-29
> **mriedel said:**
> 
```
sudo apt-get install tor
```

aha this actually works. much better than:
deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) hardy main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) hardy main
i was looking at the help tor gives ([https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)) and not really understanding very much at all!

thanks for that!

---

### Post by MoneyIntrigueMe on 2008-10-07
nvm

---

### Post by MoneyIntrigueMe on 2008-10-10
> **mriedel said:**
> There is no need to reboot your computer. The tor daemon is running and you can now use it. If you want to browse anonymously, try torbutton or foxyproxy, both firefox add-ons. Before assuming you're anonymous, I strongly advise you to read up about anonymity and how to achieve it on [torproject.org](torproject.org).

Tor is on the official ubuntu repositories though, there's no need to use mirror.noreply.org. To remove it from the list of repositories apt-get/aptitude/synpatic uses, type

```
gksudo gedit /etc/apt/sources.list
```

and delete the line you added before. It should read:

```
deb http://mirror.noreply.org
```
hey, can you anyone help me out?

i went to this site
[http://http://www.ubuntugeek.com/howto-install-torprivoxy-and-tor-gui-programs-vidaliatork-and-torbuttonin-ubuntu.html]("http://http://www.ubuntugeek.com/howto-install-torprivoxy-and-tor-gui-programs-vidaliatork-and-torbuttonin-ubuntu.html")

and they told me to.

1.type "sudo aptitude install tor privoxy" in terminal

2.type "sudo gedit /etc/apt/sources.list" in terminal

3. put these "deb" in the /etc/apt/sources.list
deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) hardy main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) hardy main
then save and exit.

4.type "sudo aptitude update" into terminal

then this error came up.


me@me:~$ sudo aptitude update
[sudo] password for me: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US        
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US         
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages          
Get:1 [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release.gpg [189B]                        
Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Translation-en_US           
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources           
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources     
Get:2 [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release [1929B]                
Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release                          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Ign [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Sources
Hit [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Packages
Hit [http://mirror.noreply.org](http://mirror.noreply.org) hardy/main Sources
Fetched 190B in 1s (126B/s)
Reading package lists... Done
W: GPG error: [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDD
W: You may want to run apt-get update to correct these problems
me@me





they told me to put these deb codes
deb [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/adnarim/ubuntu](http://ppa.launchpad.net/adnarim/ubuntu) hardy main

but i heard its better to get the deb codes from
[https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian]("https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian")
because its tor's official site.


can someone help me out here:confused:

---

### Post by MoneyIntrigueMe on 2008-10-10
anyone?

---

### Post by mikeusdev on 2008-10-18
I just wanted to share my tests: the procedure shown above on June the 17th 2008, posted by Satellite360, also worked with the latest Ubuntu 8.10 Beta version that is available today.

Thanks.
Mike

---

### Post by a0u on 2008-10-19
> **MoneyIntrigueMe said:**
> 
W: GPG error: [http://mirror.noreply.org](http://mirror.noreply.org) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CFF71CB3AFA44BDD
W: You may want to run apt-get update to correct these problems
me@mee
You don't have the GPG public key, which is needed to authenticate downloads from repositories - see [SecureApt]("https://help.ubuntu.com/community/SecureApt") for detailed information.
Of course, you can run apt-get with --allow-unauthenticated to ignore the warning.

However, you don't need [http://mirror.noreply.org]("http://mirror.noreply.org/"), since Tor is already in the official Ubuntu repositories, and judging from the commands you issued, you've already installed Tor.

Please read through earlier posts in this thread; I believe most of your questions have already been answered by others.

---

### Post by MarkieB on 2009-02-02
no longer participating in ubuntuforums.org

---

