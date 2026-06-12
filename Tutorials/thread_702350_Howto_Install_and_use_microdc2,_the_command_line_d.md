---
title: "Howto: Install and use microdc2, the command line dc++ client"
date: 2008-02-20
forum: Tutorials
---

### Post by sammydee on 2008-02-20
Hi everyone.

I noticed there were no tutorials on the forums explaining how to do this, so I'll go through the steps I used to make this work here.

**_[SIZE="4"]Introduction[/SIZE]_**

Microdc2 is an excellent command line based directconnect client, just like dc++ for windows, linuxdc++ for linux or shakespeer for mac. Now linuxdc++ is a very nice, fairly stable (later versions anyway) full featured client, so you might think why would you need something else.

Answer: Command line apps are great because

a) They take very little resources so you can run them as server daemons on older hardware
b) You can control them from anywhere in the world over an ssh connection
c) They are generally much much more stable and reliable than their graphical counterpart.
d) They're often (but not always) more configurable than their graphical alternatives.

This makes them excellent for things like running as daemons on unattended servers.

There are only two command line direct connect clients for linux. Microdc2 is one, and another one is nanodc. Nanodc appears to be under heavy development, whereas I think microdc2 may be stagnant now (correct me if I'm wrong here!). However, nanodc seems to be in pretty early beta from what I could see and although it uses a prettier ncurses interface that microdc2, its not actually as easy to use. Maybe in a little while nanodc will be a better choice, but for now, microdc2 is much better in my opinion.

**_[SIZE="4"]Installing[/SIZE]_**

First you need to download the source tarball. Go to the [microdc2 website]("http://corsair626.no-ip.org/microdc/") and download the latest version of the tarball. When I downloaded it, it was version 15.6, available [here]("http://corsair626.no-ip.org/microdc/microdc2-0.15.6.tar.gz"). So go into a command line, change to a suitable directory and download/unzip the tarball:

```

cd ~
mkdir microdc2
cd microdc2
wget http://corsair626.no-ip.org/microdc/microdc2-0.15.6.tar.gz
tar xvfz microdc2-0.15.6.tar.gz
cd microdc2-0.15.6

```

Ok, there's the source, but before we can compile it we need to download some libraries that the program needs:

```
sudo aptitude install build-essential libreadline5-dev checkinstall libxml2-dev libbz2-dev
```

Now you can start making the program. I like to use checkinstall instead of make install because it installs the program as a normal debian package so you can easily remove it later.

```

./configure
make
sudo checkinstall

```

Checkinstall will ask you some questions. You don't actually have to answer any of them, just say 'y' and press enter and it will automatically create a set of package docs for you.

Ok, now microdc2 is installed! If you used the default set of package docs in checkinstall, it will be called microdc2 in synaptic, and you can treat it like a normal package.

**_[SIZE="4"]Usage[/SIZE]_**

You can start microdc2 by just typing

```
microdc2
```

at the command line. As with most command line applications, it looks a bit empty and threatening at first, but don't worry! It really is extremely easy to use:

```
user@users-pc:~$ microdc2
Loading local FileList...done
Sharing 0 bytes (0B) totally
microdc2>
```

You can type help and press enter to get a list of commands, or type help and then a command to get detailed information about what the command does.

```
microdc2> help
alias [NAME[=VALUE] ...]                                    browse [USER]
cancel CONNECTION ...                                       cd [DIRECTORY]
connect HOST[:PORT]                                         disconnect
exit                                                        find [FILE ...]
get FILE ...                                                grantslot [USER ...]
help [COMMAND ...]                                          lookup HOST ...
ls [OPTION...] [FILE...]                                    msg USER MESSAGE...
pwd                                                         queue [USER ...]
raw DATA...                                                 results [INDEX ...]
retry USER ...                                              say MESSAGE...
search WORD...                                              set [NAME [VALUE...]]
share DIR                                                   shell [COMMAND [ARGUMENTS...]]
status                                                      transfers
unalias NAME ...                                            unqueue USER [RANGE]
unsearch INDEX ...                                          unshare DIR
who [USER ...]                                              
microdc2> help set
set: set [NAME [VALUE...]]
    Without arguments, display a list of variables and their current values. With only NAME argument, display the
    value of that variable. With NAME and VALUE arguments, change the value of a variable.
microdc2> 

```

Microdc2 also supports tab completion so you press tab to finish commands or just press tab at an empty prompt to get help.

Ok, microdc2 is pretty useless at the moment, so let's tell it to connect to a hub:

```
microdc2> connect xxx.xxx.xxx.xxx:pppp
```

You should put in the ip address and port of the hub you would like to connect to. You can chat to people by doing:

```
microdc2> say This is a message broadcast to everyone
```

You can share files by doing this:

```
microdc2> share /home/user/sharedfiles/
```

Remember, microdc2 supports tab completion so it's very quick to use. These files will be instantly shared, but microdc2 will start hashing them in the background as a low priority task.

Now here's something important:

[SIZE="6"]Microdc2 ONLY remembers shared directories. All other settings are forgotten on shutdown.[/SIZE]

This is why you have to create a ~/.microdc2/config file with all the commands you would like microdc2 to execute on startup. So create and open this file in your favourite editor. I will use gedit it here:

```
cd ~/.microdc2
gedit config

```

I have made an example config file here, you can change the settings to whatever you would like microdc2 to do:

```
# You should make sure that this listen port is forwarded properly if you are behind a router. If you can't forward ports, set active off and use passive mode. This can work behind firewalls but is crippled and slower than a properly forwarded one. NOTE: the port MUST be set before active mode is set on.
set listenport xxxx
set active on

# The following address should be set to your EXTERNAL ip address. This can be found by visiting www.whatismyip.com.
set listenaddr xxx.xxx.xxx.xxx

# I like to turn autoreconnect on in case I get disconnected from the server for whatever reason.
set auto_reconnect on

# The following enables logging. Replace the logfile with wherever you want it to log to. You can of course turn it off by leaving the following two lines blank
set log_charset UTF-8
set logfile /home/user/.microdc2/log

# These should all be pretty self-explanatory. Nick is your nickname. If the hub requires a password, specify one here.
set description I'm using microdc2!
set email microdc2user@example.com
set nick microdc2user
set password xxxx
set downloaddir /home/user/Microdc2_downloads/

# The set speed option doesn't actually change anything, it only changes your REPORTED speed that other users see. The slot is how many simultaneous downloads people can get from you.
set speed somerandomstring
set slots 2

#This is the hub connect command, it should be left until last
connect xxx.xxx.xxx.xxx:pppp
```

Of course there a lot more options than these, but this should get you started. That's it if you want to leave it there and just run microdc2 normally!

**_[SIZE="4"]Running as a daemon[/SIZE]_**

I don't know how to write init scripts so I can't help you there, sorry.  I just use screen to run microdc2 as a daemon, and I reconnect to the screen every time I want to admin it. If you don't know what screen is, try typing man screen at the command prompt or do a google search.

That's it! Have fun with microdc2!

Sam

---

### Post by MightyMag on 2008-03-16
Seems to work just fine. I use it on mine and my friends server. Seems to be stable. We are running the client in a Screen.

---

### Post by Catalyst2Death on 2008-03-24
how do I access search indexes?  I'm doing this after connecting to a hub:

search <string>... and it outputs:Issuing new search with index 1.
```
Added result to search 1 (now 1 result).
Added result to search 1 (now 2 results).
Added result to search 1 (now 3 results).
Added result to search 1 (now 4 results).
Added result to search 1 (now 5 results).
Added result to search 1 (now 6 results).
Added result to search 1 (now 7 results).
Added result to search 1 (now 8 results).
Added result to search 1 (now 9 results).
Added result to search 1 (now 10 results).
Added result to search 1 (now 11 results).
Added result to search 1 (now 12 results).
Added result to search 1 (now 13 results).
Added result to search 1 (now 14 results).
Added result to search 1 (now 15 results).
Added result to search 1 (now 16 results).
Added result to search 1 (now 17 results).
Added result to search 1 (now 18 results).
Added result to search 1 (now 19 results).
Added result to search 1 (now 20 results).
Added result to search 1 (now 21 results).
Added result to search 1 (now 22 results).
Added result to search 1 (now 23 results).
Added result to search 1 (now 24 results).
Added result to search 1 (now 25 results).
Added result to search 1 (now 26 results).
Added result to search 1 (now 27 results).
Added result to search 1 (now 28 results).
Added result to search 1 (now 29 results).
Added result to search 1 (now 30 results).
Added result to search 1 (now 31 results).
Added result to search 1 (now 32 results).
Added result to search 1 (now 33 results).
Added result to search 1 (now 34 results).
Added result to search 1 (now 35 results).
```

how do I view the results?!

---

### Post by forwardo on 2008-03-25
microdc2> results # 

where # is the search index number

---

### Post by nickblame on 2008-04-01
can I join more than one hubs? I though using different config files for each hub but no option is available in microdc2 --help :(

---

### Post by sammydee on 2008-04-04
nckblame:

This is something I haven't figured out either. In one instance of microdc2 you can only connect to one hub, and there is no command line option that I can find to specify and elternate config file, so it's a complete pain. I'm sure it wouldn't be too hard to add this functionality to the code if you could program.

Sam

---

### Post by michan_ on 2008-05-30
libbz2-dev isn't really needed, is it? And, to be finicky, it's actually called a 'DC client', not 'DC++ client'. It's not even based on the source of DC++ (which is only the name of a client, not the Direct Connect network). :)

---

### Post by sammydee on 2008-06-05
michan_ actually, libbz2-dev IS needed, microdc2 will not compile without it. This is because direct connect file lists are zipped up with bzip2 before being transferred.

And I changed the thread title :-)

Sam

---

### Post by Gourgi on 2008-06-05
thanks for the tutorial :-D

---

### Post by bonfire89 on 2008-08-29
thanks man

---

### Post by defrg on 2008-10-20
> **nickblame said:**
> can I join more than one hubs? I though using different config files for each hub but no option is available in microdc2 --help :(

The syntax to load another config file is: ```
microdc2 --config=configfileyouwanttoload
```
Have a look at *man microdc* :)

Best regards

---

### Post by minuxx on 2008-11-09
Thank you very much for that easy-to-use installation guide.
Worked for me !

---

### Post by Tony25 on 2008-12-08
Hello guys!

This is the most helpful and very very simpel tutorial to understand, and I relly thankey for that :) :) :) I did everything in 10 minutes.... it is awesome and I am happy for that. Anyway I have to test how to load a second config so the client can connect in more hubs and another thing I couldnt do is to run the client out of my ssh screen, that daemon thing I dont know. I really need this because If I have to download all night, my PC will stay on too... Can you please just do another simple tut like that just to explain how to run microdc2 in another screen or like daemon I dont know because I have never done that. I have a dedicated server and I can access only with ssh and webim.

Thankey!

---

### Post by mpinovice on 2009-02-06
Hi, I am new to microdc2 ... I could install the microdc2 client on my linux machine. But when I try to connect to a hub for example, it says

microdc2> connect 204.16.252.108
Connecting to hub on 204.16.252.108:411

and when I check on the status, it says 

microdc2> status
Hub state: Waiting for complete connection
Hub users: (not logged in)
...............
...............
Cannot connect - Connection timed out
Shutting down hub connection.

The thing is I am able to connect to that hub and several others using my DC++ client, but I can't seem to connect to ANY hub using microdc2. Can you please suggest what I might need to configure to get this to work ?

Thanks a lot!

---

### Post by Hund on 2009-05-27
How do you share 2 folders with the same name from two different harddrives? No support for virtual names? :(

---

### Post by tnttrx on 2009-09-12
is there some worthy alternative for microdc2 ?:confused:

---

### Post by m47h3us on 2009-09-14
Hi, i had problems with installing this but got some help here. 

```
[http://forums.fedoraforum.org/showthread.php?t=230087]("http://forums.fedoraforum.org/showthread.php?t=230087")
```

---

### Post by mr.tapac on 2009-10-19
> **Hund said:**
> How do you share 2 folders with the same name from two different harddrives? No support for virtual names? :(

maybe, "ln" is designed for "virtual names"? :D

---

### Post by Malstrond on 2010-02-21
The developer's site seems to have vanished. Any idea where I can get it now?

---

### Post by SectorNine50 on 2010-04-12
Whenever I try to make this, I get the following errors before it quits:

```
collect2: ld returned 1 exit status
make[2]: *** [microdc2] Error 1
make[2]: Leaving directory `/usr/microdc2/microdc2-0.15.6/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/microdc2/microdc2-0.15.6/src'
make: *** [install-recursive] Error 1

****  Installation failed.  Aborting package creation.
```Any ideas?  This is on the most recent stable release of Ubuntu Server.

---

### Post by SectorNine50 on 2010-05-19
Bump

No one knows what's goin' on here?  I for the life of me can't figure it out.

---

### Post by tnttrx on 2010-05-19
> **Malstrond said:**
> The developer's site seems to have vanished. Any idea where I can get it now?

[http://corsair626.no-ip.org/microdc/](http://corsair626.no-ip.org/microdc/)
seem ok, but you can get source and some tips from some getnoo mirror:

[http://lug.mtu.edu/gentoo/distfiles/microdc2-0.15.6.tar.gz](http://lug.mtu.edu/gentoo/distfiles/microdc2-0.15.6.tar.gz)
[http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/net-p2p/microdc2/microdc2-0.15.6-r2.ebuild?revision=1.1](http://sources.gentoo.org/cgi-bin/viewvc.cgi/gentoo-x86/net-p2p/microdc2/microdc2-0.15.6-r2.ebuild?revision=1.1)
but I suggest applying slavemode patch to avoid 100% CPU usage:
[http://bugs.gentoo.org/show_bug.cgi?id=162828](http://bugs.gentoo.org/show_bug.cgi?id=162828)
[http://bugs.gentoo.org/attachment.cgi?id=230553](http://bugs.gentoo.org/attachment.cgi?id=230553)

---

### Post by mad hamish on 2011-05-11
Hi,

Managed to install microdc2 on Ubuntu 10.04 LTS, but only after applying the patch described in [http://bugs.gentoo.org/attachment.cgi?id=202926&action=diff](http://bugs.gentoo.org/attachment.cgi?id=202926&action=diff) . Thanks Gentoo guys! 

The patch is small, requiring only one line of the ./configure script to be altered, which i just did manually through a text editor. I then followed the original instructions by sammydee.

---

### Post by uuhujju on 2012-08-06
Hello,

I am trying to set up microdc2, version 0.15.6. Everything works fine except for one thing - I am unable to make the client active. The computer running microdc2 is behind a NAT, I forwarded its port, set microdc2 to active mode but I can't figure out which IP address to use for listenaddr. External IP (that is IP of the router) doesn't work ("Cannot bind to address - Cannot assign requested address") and binding to anything else doesn't work either - i.e. clients are unable to connect and download anything.

Any idea what might have gone wrong? The Internets seems to be quiet about this issue, unfortunately :(

---

### Post by uuhujju on 2012-08-07
Well, for anyone having the same problem with **port forwarding**:

The solution is to set active mode PRIOR to setting listening address, otherwise microdc2 won't know it should "bind" to your external IP address (that is the one which your router is assigned).

So the proper configuration for your port-forwarded microdc2 behind NAT is following:
```

set listenport 44444
set active on
set listenaddr 1.2.3.4

```

AND forwarding BOTH **TCP** and **UDP** ports 44444 to your microdc2 machine.

---

