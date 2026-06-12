---
title: "Howto setup OSSEC-HIDS on your ubuntu box"
date: 2006-07-11
forum: Tutorials
---

### Post by RShadow on 2006-07-11
This HOWTO will walk you through the very simple installation of the [OSSEC-HIDS](http://www.ossec.net) application.  Before we continue lets make sure everybody is on the same sheet of music.

1. OSSEC-HIDS is a host based intrusion detection system.  It is a very flexible system that will allow you to achieve the following.

[INDENT][LIST]
[*]rootkit detection
[*]file system integrity
[*]log file analysis
[*]time based alerting
[*]active responses
[/LIST][/INDENT]

Taken from the ossec-hids FAQ
"OSSEC HIDS is an Open Source Host-based Intrusion Detection System. It performs log analysis, integrity checking, rootkit detection, time-based alerting and active response"

2. This howto is based on the following assumptions
[INDENT][LIST]
[*]You are running an up to date installation of Dapper
[*]You are preforming a "local" installation (i.e. a single host)
[/LIST][/INDENT]

3. The majority of this HOWTO is taken directly from the [Installation Manual](http://www.ossec.net/en/manual.html) for OSSEC-HID which is a very easy to follow Manual.  If you run into trouble please look at the Manual first as it will always have the most up to date information.

Ok, Now that we are all together lets proceed.  As mentioned above this HOWTO will only cover a local installation.  ossec-hids has the ability to monitor multiple hosts all using the same ruleset.  This is accomplished by installed the ossec-hids server on one machine and then doing an agents installation on every other machine you wish to protect.  The agents communicate to the server via a secure connection.  If you need this type of setup please take a look at the [manual](http://www.ossec.net/en/manual.html), however the installation is not very different (just different options available in your conf file is about it.  The other nice thing is that the agents portion of the application will also run under a windows host.  This allows those of you that have to and/or want to run a windows box to secure that as well (install the server on your /flamebait/ superior /flamebait/ Linux box and the agent on your windows box)

Now the first thing we need to do is grab the latest sources.  For this HOWTO we will be installing 0.8, however feel free to get the latest copy available from their site.  We also need to install some stuff so we can compile it later.
```

sudo apt-get install build-essentials
cd ~
mkdir src
cd src
wget http://www.ossec.net/files/ossec-hids-0.8.tar.gz
http://www.ossec.net/files/ossec-hids-0.8_checksum.txt

```

Before we go ahead and extract this, lets make sure we got what we think we got. Verify the checksums in the .txt file and the same that the commands below output.  THIS IS IMPORTANT -- DON'T SKIP IT --
```

cat ossec-hids-0.8_checksum.txt
md5sum ossec-hids-0.8.tar.gz
sha1sum ossec-hids-0.8.tar.gz

```

Well now, after verifying you have legit files (you did do that didn't you?) lets extract this bugger
```

tar -zxvf ossec-hids-0.8.tar.gz
cd ossec-hids-0.8

```

Now the fun and easy part.  We are going to run the installation script and let it do all the hard work.  Note: Here I enter a su shell for the sake of simplicity.  If you don't want to do this simply append "sudo" to the following commands
```

sudo -s
./install.sh

```

Go ahead and pick what language you want to read everything in and hit enter
```

 ** Para instalação em português, escolha [br].
  ** Fur eine deutsche Installation wohlen Sie [de].
  ** For installation in English, choose [en].
  ** Per l'installazione in Italiano, scegli [it].
  ** Aby instalowa&#263; w j&#281;zyku Polskim, wybierz [pl].
  ** Türkçe kurulum için seçin [tr].
  (en/br/de/it/pl/tr) [en]: ** en <enter> **

```

Next it is going to warn us that we need a C compiler on the machine. (you did install build-essentials didn't you?) and give you some general information about your computer (kernel version, user and host). Go ahead and hit enter likes it says.
```

OSSEC HIDS v0.8 Installation Script - http://www.ossec.net

 You are about to start the installation process of the OSSEC HIDS.
 You must have a C compiler pre-installed in your system.
 If you have any questions or comments, please send an e-mail
 to dcid@ossec.net (or daniel.cid@gmail.com).

  - System: Linux diana 2.6.15-25-k7
  - User: root
  - Host: diana


  -- Press ENTER to continue or Ctrl-C to abort. --
**<enter>**

```

Next select a local install
```

1- What kind of installation do you want (server, agent, local or help)? **local <enter> **

```

Now choose were you want to install it.  This HOWTO will choose the default
```

- Choose where to install the OSSEC HIDS [/var/ossec]: ** <enter> **

```

Now select you notification options.  You can choose my answers or different ones.  I would recommend setting "Y" to everything.  Active responses are really nice.  It will set some default configuration variables based on your answers and certian things it finds on your system.
```

3- Configuring the OSSEC HIDS.

  3.1- Do you want e-mail notification? (y/n) [y]: **y**
   - What's your e-mail address? **youremail@yourdomain.com**
   - What's your SMTP server ip/host? **your smtp server address (localhost)**

  3.2- Do you want to run the integrity check daemon? (y/n) [y]: **y**

   - Running syscheck (integrity check daemon).

  3.3- Do you want to run the rootkit detection engine? (y/n) [y]: **y**

   - Running rootcheck (rootkit detection).

  3.4- Active response allows you to execute a specific
       command based on the events received. For example,
       you can block an IP address or disable access for
       a specific user.
       More information at:
       http://www.ossec.net/en/manual.html#active-response

   - Do you want to enable active response? (y/n) [y]: **y**

     - Active response enabled.

   - By default, we can enable the host-deny and the
     firewall-drop responses. The first one will add
     a host to the /etc/hosts.deny and the second one
     will block the host on iptables (if linux) or on
     ipfilter (if Solaris, FreeBSD or NetBSD).
   - They can be used to stop SSHD brute force scans,
     portscans and some other forms of attacks. You can
     also add them to block on snort events, for example.

   - Do you want to enable the firewall-drop response? (y/n) [y]: **y**

     - firewall-drop enabled (local) for levels >= 6

   - Default white list for the active response:
      - 192.168.2.1

   - Do you want to add more IPs to the white list? (y/n)? [n]: **n**

  3.6- Setting the configuration to analyze the following logs:
    -- /var/log/messages
    -- /var/log/auth.log
    -- /var/log/syslog
    -- /var/log/mail.info
    -- /var/log/apache2/error.log (apache log)
    -- /var/log/apache2/access.log (apache log)

 - If you want to monitor any other file, just change
   the ossec.conf and add a new localfile entry.
   Any questions about the configuration can be answered
   by visiting us online at http://www.ossec.net .


   --- Press ENTER to continue ---

```

Now it will compile everything.  This shouldn't take too long to complete.  It only took around 1-2 minutes for my boxes.  After it is completed press enter to finish.
```

 - Unknown system. No init script added.

 - Configuration finished properly.

 - To start OSSEC HIDS:
                /var/ossec/bin/ossec-control start

 - To stop OSSEC HIDS:
                /var/ossec/bin/ossec-control stop

 - The configuration can be viewed or modified at /var/ossec/etc/ossec.conf


    Thanks for using the OSSEC HIDS.
    If you have any question, suggestion or if you find any bug,
    contact us at contact@ossec.net or using our public maillist at
    ossec-list@ossec.net
    (http://mailman.underlinux.com.br/mailman/listinfo/ossec-list).

    More information can be found at http://www.ossec.net

    ---  Press ENTER to finish (maybe more information bellow). ---

```

Now unfourtuntly it doesn't detect Ubuntu so it will not create an init script.  This is simple enough to take care of. (Yes, its basic. If you want to improve it please feel free to do so)  Copy and paste the following into /etc/init.d/ossec

```

#!/bin/sh

case "$1" in
start)
  /var/ossec/bin/ossec-control start
;;
stop)
  /var/ossec/bin/ossec-control stop
;;
restart)
  $0 stop && sleep 3
  $0 start
;;
reload)
  $0 stop
  $0 start
;;
*)
echo "Usage: $0 {start|stop|restart|reload}"
exit 1
esac

```

Now make it executable
```

cd /etc/init.d
chmod +x ossec

```

Add it to our runlevels so it starts on boot
```

update-rc.d ossec defaults

```

Now lets crank her up and make sure everything works
```

/etc/init.d/ossec start

```

If you get something like this, you should be in good shape.
```

Starting OSSEC HIDS v0.8 (by Daniel B. Cid)...
Started ossec-maild...
Started ossec-execd...
Started ossec-analysisd...
Started ossec-logcollector...
Started ossec-syscheckd...
Completed.

```

Now you can go on to customize the setup.  Chances are you going to want it to ignore certian directories and create your own rules.  Please check out the manual for excellent instructions on doing so.

Caveat: the check_xxx values listed in the documentation should appear as directory attributes (i.e. <directory blah blah check_perms yes>

Resources:
[OSSEC Homepage](http://www.ossec.net)
[OSSEC-HIDS Manual](http://www.ossec.net/en/manual.html)

---

### Post by RShadow on 2006-07-11
Nobody's interested?

---

### Post by airjunman on 2006-07-12
very interested ...am gonna try it ,.... how does it compare to something like snort though in ur view?

---

### Post by RShadow on 2006-07-12
Well I think the two essentialy deal with different issues (ossec can actualy monitor your snort logs and send warnings ).

Snort is a network IDS whereas ossec is Host IDS.  Snort monitors your network traffic to look for attacks.

Ossec can kind of help with this (by monitoring your logs) but mainly deals with looking at the actual computer to determine if it has been comprimised. (i.e. rootchecks, log anomolies, etc).  However OSSEC dives into the NIDS areana with realtime log monitoring and can for example issue an IPTable rule to block an IP address if it detects multiple failed attempts from a single IP (as an example this morning I received a message from OSSEC about somebody scanning my web server for exploits, it detected this from my apahce logs and automaticly restricted that IP from my machine).  The "Active Response" is also very cool because you can basily pipe to your own program, so can really do whatever you want when an "alert" is fired.

I would like to install snort and see how the two operate together, but alas I can get snort to install on Ubuntu.  The package simple doesn't install all the files its supposed to (no /etc/snort/rules is created, and its missing other key configuration files).. and nobody seems to have a clue as to why.. so no snort for me on this box.

Anyways OSSEC is very lightweight, doesn't consume alot of memory, and so far has been very "on the ball" for me.  There will of couse be tweaks you will have to make (for example I run tinydns and it kept firing alerts because my tinydns log files were changing, so I simply had to tell it to ignore those files for monitoring changes).


Hope that helps alittle,

btw: the latest version is 0.8-6 and I installed that this morning, the script automaticly detected a previous installed and upgrading was the most painless process I have ** ever ** experinced in Linux.

Edit: as mentioned on their homepage (snort being #1)
"Insecure.org released the results of their Top security tools survey and OSSEC was rated second (#2) in the IDS category and  #56 in the overall. We were better classified than Base, Sguil, Honeyd, Nagios, chkrootkit and some other very good tools. Congratulations to everyone who contributed to the project!"

allthough again, I think Snort (NIDS) and OSSEC (HIDS) deal with different issues.

---

### Post by airjunman on 2006-07-12
Thanks RShadow ... I need to tinker around with boh of them first before I ask anything more.. I think I'll start with OSSEC cos I need it only my workstation ..Will post the results of that, and after reading up a lill abt it maybe then we can have a better discussion abt it... Thanks for the help again...

---

### Post by marcus123 on 2006-07-12
Wow, very nice howto. I just registered to be able to ask something. What about a .deb package for it? I couldn't find
anything like that in their web site related to that, but this tool seems excelent.

*I tried the default package and worked fine.

-M

---

### Post by RShadow on 2006-07-13
I'm sure a .deb package could be made, but I don't have the knowledge to do so.  I'm glad everything has worked for you however.

---

### Post by marcus123 on 2006-07-13
You should also send this document to the official site, since it is better written than what is there. ;)

---

### Post by marcus123 on 2006-07-13
Sounds like someone had the idea of the .deb already:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=361954](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=361954)

---

### Post by airjunman on 2006-07-17
Thanks again.. I tried installing it from your directions and it worked perfectly... Next I need to try to configure active-response and learn to get the firewall to work with it... I use firestarter on my system..... i also need to be able to create and add rules ...do u know of any resource that helps to that effect? n  not the manual, i cant figure out much from there , maybe i'm too much of a newbie for that... it just has variable names and their possible values...nutin really that explains the variables.,.  I'm in the process of preparing a small beginners tutorial so newbies like me can understand how certain parts of ossec work... just a short way of relating theoretical to practical .. will post in a day or two .. thanks for the help so far though...

---

### Post by RShadow on 2006-07-17
I've actualy been playing with this recently.  Using firestarer should not be a problem because it is just a front-end for IPTables.  If you look in
/var/ossec/active-response you should see a log file there that details when it add/removes it's entries.. you can also test it out by issuing bin/firewall-drop.sh add null a second machines ip address and if all goes well that IP address should have zero connection to your server.  So anyways as long as you have Iptables installed and running on your machine and you said "yes" to active-response when you installed ossec it should be doing its job (which you can verify from the log file).


I'm actualy constructing an in-depth howto on a computer secure server setup because I have found that Ubuntu is a very insecure server by default (for example the version of apache in the repos is outdated and the particular version is suseptibal to several exploits, as with the version of openssl.. (which you can verity by running nikto on your apache server)

---

### Post by Aramil on 2006-07-20
I tried to install OSSEC HIDS but although i followed the instructions when the installation is about to compile everything I receive the following error

5- Installing the system
 - Running the Makefile
./install.sh: line 55: make: command not found
0x0000 - Internal error for 0x5-build




Does anybody know how to fix this?

---

### Post by RShadow on 2006-07-20
Did you install build-essentials ? You don't have make on your machine.

---

### Post by telmo on 2006-07-26
This sounds nice and all, but.... one thing looks important to me... **How do i remove it?** I found that everywhere in this forum this is something people forget, instructions is how to remove stuff they tell you how to install, and it seems quite relevant for newbies such as myself.

Thanx, sorry to bother.

---

### Post by RShadow on 2006-07-26
If you would like to remove it, just reverse the process.  Delete the /var/ossec directory, remove the init script and its gone..

---

### Post by telmo on 2006-07-26
Thx! ;)

---

### Post by duality on 2006-07-31
perfect,, this is just what i was looking for,, thank you

---

### Post by gregh on 2006-08-03
I have a question, I am setting up ossec with a view to monitor remote windows boxes at work.

What I need to do is get a summary each day emailed to me.

Q. How do I do it? I don't just want to be alerted when something is wrong (my bosses like me to appear proactive) so a daily summary, even if it says everything is fine, is required.

BTW, great product I have it on my home server :-)

---

### Post by antilog on 2006-08-03
This looks really handy, thanks for the HOW-To.  The only part that is not clear to me is how to monitor activity.  I am running snort > mysql > base - is there a way to tie it in?

Thanks

---

### Post by gederoth on 2006-08-11
very interested,  thanks for the help!  Gonna setup a server for this and my whole network soon,  if i can get some time that is.. :)

---

### Post by action09 on 2006-09-24
Hi, 

thanks for your doc. I agree with the person who ask for a .deb.
Can you add it in the doc ?

---

### Post by action09 on 2006-09-24
I mean, it may be useful to add the line to build a .deb and dpkg -i ..

---

### Post by neill on 2007-01-29
quality guide :guitar: 

now .... any idea how you update the rootkit detection signatures ?

neill

---

### Post by bodhi.zazen on 2007-02-05
Nice How-to

This thread has been added to the UDSF wiki.

[OSSEC-HIDS](http://doc.gwos.org/index.php/OSSEC-HIDS)

---

### Post by mistypotato on 2007-02-15
Hi,

Super HOW-TO !   Thanks for taking the time to do it.

I'm having a leetle problem with ossec....

Everything starts looking good then BLOTTO...end of fun!
Here's the output starting where things fall apart
**any help would be wunnerful !** :KS 



5- Installing the system
 - Running the Makefile

 *** Making zlib (by Jean-loup Gailly and Mark Adler)  ***
make[1]: Entering directory `/home/meuser/Downloads/ossec-hids-1.0/src/external/zlib-1.2.3'
cc -c -Wall -I../../ -I../../headers  -DDEFAULTDIR=\"/var/ossec\"   -DARGV0=\"zlib\" -DXML_VAR=\"var\" -DOSSECHIDS *.c
/bin/sh: cc: command not found
make[1]: *** [shared] Error 127
make[1]: Leaving directory `/home/meuser/Downloads/ossec-hids-1.0/src/external/zlib-1.2.3'
make[1]: Entering directory `/home/meuser/Downloads/ossec-hids-1.0/src/external/zlib-1.2.3'
cp -pr zlib.h zconf.h ../../headers/
cp -pr libz.a ../
cp: cannot stat `libz.a': No such file or directory
make[1]: *** [ossec] Error 1
make[1]: Leaving directory `/home/meuser/Downloads/ossec-hids-1.0/src/external/zlib-1.2.3'



 *** Making os_xml ***

make[1]: Entering directory `/home/meuser/Downloads/ossec-hids-1.0/src/os_xml'
cc -DXML_VAR=\"var\" -Wall -I../ -I../headers  -DDEFAULTDIR=\"/var/ossec\"   -DARGV0=\"os_xml\" -DXML_VAR=\"var\" -DOSSECHIDS -c os_xml.c os_xml_access.c os_xml_node_access.c os_xml_variables.c
make[1]: cc: Command not found
make[1]: *** [xml] Error 127
make[1]: Leaving directory `/home/meuser/Downloads/ossec-hids-1.0/src/os_xml'

Error Making os_xml
make: *** [all] Error 1

 Error 0x5.
 Building error. Unable to finish the installation.

---

### Post by ncbb on 2007-04-27
Thanks for this great Howto! The current version (v1.1) even detected that I was running Ubuntu (Feisty) and setup the init scripts automatically.

---

### Post by jns-nun on 2007-08-15
I don't have problems with the explanation, with the installation, in the last of cases, the question is: 

¿Why don't create the Ossec files?
it's so weird, i run the script and it's OK, very WELL, but in the final of installation a line broken the script saying somethig like this:

5- Installing the system
 - Executing Makefile
./install.sh: line 85: make: order not found

 Error 0x5.
 Building error. Unable to finish the installation.

Sorry for my english, Im from Mexico and I use OSSEC v1.3 whit Ubuntu 6.06 LTS.

---

### Post by arijarot on 2007-09-17
Thanks for the guide and info, RShadow :) Was indeed helpful.

---

### Post by battletux on 2007-09-20
Thanks for this, but I now have 1 question,

How do I unban an IP address?

My friend kindly tested this for me by trying to ssh into my box 6 times with a fake account and he got kicked and can no longer access any service running on my machine.

How to I go about removing this ban?

---

### Post by tjalling on 2007-09-20
Great HowTo!

Just one small thing: it took me an hour to discover that this code:


> **RShadow said:**
> 
[code]
sudo apt-get install build-essentials
cd ~


has one "s" to many:(

When I finally typed "sudo apt-get install build-essential" it took me another hour to retreive the cd-rom from behind my desk:)

Tjalling

---

### Post by mcc666 on 2007-11-05
Hello,

    let me renew this thread. As I used to use portsentry, then i found psad, and now I'm reading about ossec and wondering if there is a need to use e.g. iptables + psad + ossec + snort installed on the same server? After reading several articles I found that psad and portsentry are some subsets of ossec - or there is something what I missed? :confused:

What would you recommend if I have two servers providing several services in the internet (www+DNS+mail) in the same subnetwork - should I install ossec in client - master scenario, what about other software (snort) - should be somehow synchronized? Is there any chance to correlate every security issue (mentioned above + apache logs + mysql logs) in one user friendly software? 

Many thanks,
MCC

---

### Post by jetole on 2008-01-05
> **RShadow said:**
> I would like to install snort and see how the two operate together, but alas I can get snort to install on Ubuntu.  The package simple doesn't install all the files its supposed to (no /etc/snort/rules is created, and its missing other key configuration files).. and nobody seems to have a clue as to why.. so no snort for me on this box.

RShadow, I appreciate the docs since OSSEC is something new I am going to try however, with your issue with snort, don't use a .deb.

Snort is not near beign actively maintained in debian (where the ubuntu .deb comes from). The current .deb install Snort 2.3 where I just installed snort 2.8.

Also, there is a specific reason why there is no rules included. Although Debian could choose to use the default rules with snort there are different rule sets available to different groups from the snort.org website as well as the option to use other rules such as the ones from Bleeding Edge Threats ([http://www.bleedingthreats.net/](http://www.bleedingthreats.net/)) and in my case I use both the snort.org commercial / pay rules as well as the ones from Bleeding Edge Threats.

Long story short, take the time time to install snort properly and you will have an exceptional NIDS that functions properly. If you expect a pre built binary from Debian/Ubuntu then you are trusting someone else to give you a one size fits all solution to one of the most important aspects of network security.

Also when you have the time look into barnyard, base and oinkmaster. (Oinkmaster constantly updates rules when new ones are released).

Cheers

---

### Post by BattleRaT on 2008-01-16
Excellent HowTo RShadow.

Now, I will add this for Prelude-IDS support:

Before you run the "./install.sh" script, execute the following:

```

$ cd ossec-hids-xx
$ cd src
$ make setprelude

```

Then edit Config.OS and add **-lgcc_s** in all lines ahead **-lpthread** like this:

```

CPRELUDE=-DPRELUDE -lprelude -pthread **-lgcc_s** -L/usr/lib -lprelude -lgnutls -lgcrypt -lrt -ldl
CPRELUDE=-DPRELUDE -lprelude -pthread **-lgcc_s** -L/usr/lib -lprelude -lgnutls -lgcrypt -lrt -ldl
CPRELUDE=-DPRELUDE -lprelude -pthread **-lgcc_s** -L/usr/lib -lprelude -lgnutls -lgcrypt -lrt -ldl
...
CPRELUDE=-DPRELUDE -lprelude -pthread **-lgcc_s** -L/usr/lib -lprelude -lgnutls -lgcrypt -lrt -ldl
...
```

*(this addon fix a error with GCC3 ... "**libgcc_s.so.1 must be installed for pthread_cancel to work**"*

Then install ossec:
```

$ ./install.sh
```

Add the following entry to $PATH_OSSEC/etc/ossec.conf:

```

 <prelude_output>yes</prelude_output>
```


Finally, in prelude-ids, add the ossec sensor:

First, in Terminal1:
```

$ prelude-adduser registration-server prelude-manager

```

... and then in Terminal2:
```

$ prelude-adduser register **OSSEC** "idmef:w" localhost --uid 0 --gid 0

```
*Note: The sensor name MUST be in OSSEC with upcase.*



Start the ossec with init.d script powered by OSSEC (1.4 version now detect ubuntu/debian OS and the init script work!) or RShadow script.

You will see this:
```

Starting OSSEC HIDS v1.4 (by Daniel B. Cid)...
Connecting to 127.0.0.1:4690 prelude Manager server.
TLS authentication succeed with Prelude Manager.

```

Enjoy! :guitar:

---

### Post by chiefbutz on 2008-03-05
Very nice, thank you. Though your links are outdated and OSSEC now detects Ubuntu and does the init.d stuff for you.

---

### Post by vitorio on 2008-03-10
I've installed and run OSSEC without problems.  At least I regularly get e-mails as expected.

But when I tried to make some changes to "ossec.conf" file in /var/ossec/etc I was not allowed to save them.

Before editing the file I had stopped OSSEC executing "sudo /etc/init.d/ossec stop".  Then tried:
 
"gksudo gedit /var/ossec/etc/ossec.conf"

or "sudo vim/var/ossec/etc/ossec.conf" 

or "sudo -s" and then as root tried to edit the file.

In all cases I was not allowed save my changes.  In Gedit the Save options was simply disabled.  Vim failed with Bach reporting attempt to change read-only file.

Is the problem in OSSEC protecting its files?.   I could attempt to change the permissions to the file allowing writing to it.  But first, I am not sure OSSEC will allow me to do it, and second, it looks to me like a hack.  Hence I've even not tried doing it.  At the end I'm not interesting to hack it but rather to find the right way to customize my configuration.  

So far I've not found anything related to the case in OSSEC's documentation and wiki, and could not get any help on newsgroups.  Anybody experienced something like this?  Any suggestions, please?

---

### Post by pytheas22 on 2008-03-31
> But when I tried to make some changes to "ossec.conf" file in /var/ossec/etc I was not allowed to save them.

I had the same issue; it turned out to be just because ossec.conf by default is not writable, even by its owner, root.  Maybe this is supposed to provide a little extra security, or maybe it's just an oversight.

Running

```
chmod +rw /var/ossec/etc/ossec.conf
```

fixes the problem and allows you to edit the file.

---

### Post by vaineh on 2008-04-08
anyone else had an issue with email alerting just stopping for no apparent reason? i found a post in a mailing list that said it was a problem with an older version but im running the latest. 

basically alerts were working fine and then just stopped. i was using an external relay at the time so i changed it to just use localhost to test and i restarted ossec and got an email alert saying the server had been started. great i thought, alerts working again. but i now havent received anything further.

any clues?

---

### Post by pytheas22 on 2008-04-08
> anyone else had an issue with email alerting just stopping for no apparent reason? i found a post in a mailing list that said it was a problem with an older version but im running the latest.

Did you check to make sure the OSSEC mail daemon is still alive?  On my server it seems to die after some time for no reason.  I set up a cronjob to restart the whole server every once in a while to work around this.

---

### Post by fischer98 on 2008-05-16
I'm new to OSSEC, trying to get it setup for the first time. I've gotten pretty far, but still have a few kinks I need help working out. My setup:

Ubuntu 8.04 server
OSSEC 1.5 installed in server mode
Snort 2.7
Syslog-NG
One windows agent
One windows box sending syslog via Eventlog to Syslog ([https://engineering.purdue.edu/ECN/Resources/Documents/UNIX/evtsys](https://engineering.purdue.edu/ECN/Resources/Documents/UNIX/evtsys))


Problems:
1. OSSEC wouldn't listen on 514 udp for syslog connections. I checked netstat, and nothing was running on 514, but even with this:
  <remote>
    <connection>syslog</connection>
  </remote>
 in my ossec.conf file, ossec wouldn't do syslog. Will it only do one or the other (syslog vs. secure)? I've installed syslog-ng to accept syslog messages, which is working ok for the most part. Will this cause problems?

2. My IT guys are much more likely to accept this as a solution if I don't have to install the windows agents. They are already using the syslog program above on windows boxes to send syslog to their syslog server. What limitations do I face by not using the agent? Lack of active response on the client would be one, I'm guessing.

3. The <match> tag seems very spotty. I'm trying to work with the syslog format that this windows syslog program generates. On an event starting with Security: 528: ..., ossec will match the 528, but not the Security. I'm using Kiwi SyslogGen to send messages and confirmed they are getting there. Here is what I tried to use to match in a separate rules file:

<group name="syslog,">
  <rule id="47001" level="1">
    <match>528</match>
    <description>Test alert from laptop</description>
  </rule>
</group>

In between each rule change, I'm restarting ossec (is there a better way?) The above will match the string "Security: 528:". However, if I change the 528 above to Security, no match. I tried "Application" with a syslog message of "Application: 1009:", no match. I tried other random words, and still no match.

Any help would be greatly appreciated.

---

### Post by pytheas22 on 2008-05-16
> 1. OSSEC wouldn't listen on 514 udp for syslog connections.

I think you want to open port 1514, not 514.  There was a related issue on the mailing list yesterday, and here's the reply from Daniel Cid:
> 
As others stated, you only need to open port 1514 UDP, keeping the
state (same as you would open for
dns on the client side, keeping the state so the reply from the dns
server can reach back).

EDIT: actually I'm not sure about this anymore; it looks like 514 might be the right port for what you want.  But maybe you could try opening 1514 too and see if it solves the problem.  Apparently OSSEC uses both.

> 2. My IT guys are much more likely to accept this as a solution if I don't have to install the windows agents. They are already using the syslog program above on windows boxes to send syslog to their syslog server. What limitations do I face by not using the agent? Lack of active response on the client would be one, I'm guessing.


As far as I know, there is no active response for Windows machines; that feature remains limited at this time to Unix platforms, so you wouldn't be missing out.  You would, however, not be able to take advantage of [Windows policy monitoring]("http://www.ossec.net/wiki/index.php/Know_How:WindowsPolicy"), which will check for malware, rootkits, bad policies (like null sessions) and the presence of certain applications that you may not want users to have (Skype, Limewire...).  These programs need to run on the Windows boxes themselves because they look at more than logs (they watch for certain processes, executables...).  Otherwise though I can't think of any downfalls of not running the OSSEC agent (is there a particular reason why you're averse to it?) as long as the syslog server is running well.

As for the third question, hopefully someone on the mailing list will answer your post from this morning.

---

### Post by tsoul on 2008-05-18
Hye I have installed OSSEC without any issues, but i need help with ALERTS!

I can not send out mail because my ISP blocks port 25 and the relay through there server gets "RCPT TO not accepted".

I have mailx installed and would like to get the alerts deliverd my local inbox but I have no idea how to point ossec to send alerts to my mialx local inbox.

Thank you!

---

### Post by pytheas22 on 2008-05-18
> I have no idea how to point ossec to send alerts to my mialx local inbox.

You should be able to simply specify your local address inside the <email_to> tags in /var/ossec/etc/ossec.conf.

Also if you want only to view alerts locally, you could install the [WUI]("http://www.ossec.net/wiki/index.php/OSSECWUI").

---

### Post by blc2001ro on 2008-06-10
> **RShadow said:**
> This HOWTO will walk you through the very simple installation of the [OSSEC-HIDS](http://www.ossec.net) application.  Before we continue lets make sure everybody is on the same sheet of music.

1. OSSEC-HIDS is a host based intrusion detection system.  It is a very flexible system that will allow you to achieve the following.

[INDENT][LIST]
[*]rootkit detection
[*]file system integrity
[*]log file analysis
[*]time based alerting
[*]active responses
[/LIST][/INDENT]

Taken from the ossec-hids FAQ
"OSSEC HIDS is an Open Source Host-based Intrusion Detection System. It performs log analysis, integrity checking, rootkit detection, time-based alerting and active response"

2. This howto is based on the following assumptions
[INDENT][LIST]
[*]You are running an up to date installation of Dapper
[*]You are preforming a "local" installation (i.e. a single host)
[/LIST][/INDENT]

3. The majority of this HOWTO is taken directly from the [Installation Manual](http://www.ossec.net/en/manual.html) for OSSEC-HID which is a very easy to follow Manual.  If you run into trouble please look at the Manual first as it will always have the most up to date information.

Ok, Now that we are all together lets proceed.  As mentioned above this HOWTO will only cover a local installation.  ossec-hids has the ability to monitor multiple hosts all using the same ruleset.  This is accomplished by installed the ossec-hids server on one machine and then doing an agents installation on every other machine you wish to protect.  The agents communicate to the server via a secure connection.  If you need this type of setup please take a look at the [manual](http://www.ossec.net/en/manual.html), however the installation is not very different (just different options available in your conf file is about it.  The other nice thing is that the agents portion of the application will also run under a windows host.  This allows those of you that have to and/or want to run a windows box to secure that as well (install the server on your /flamebait/ superior /flamebait/ Linux box and the agent on your windows box)

Now the first thing we need to do is grab the latest sources.  For this HOWTO we will be installing 0.8, however feel free to get the latest copy available from their site.  We also need to install some stuff so we can compile it later.
```

sudo apt-get install build-essentials
cd ~
mkdir src
cd src
wget http://www.ossec.net/files/ossec-hids-0.8.tar.gz
http://www.ossec.net/files/ossec-hids-0.8_checksum.txt

```

Before we go ahead and extract this, lets make sure we got what we think we got. Verify the checksums in the .txt file and the same that the commands below output.  THIS IS IMPORTANT -- DON'T SKIP IT --
```

cat ossec-hids-0.8_checksum.txt
md5sum ossec-hids-0.8.tar.gz
sha1sum ossec-hids-0.8.tar.gz

```

Well now, after verifying you have legit files (you did do that didn't you?) lets extract this bugger
```

tar -zxvf ossec-hids-0.8.tar.gz
cd ossec-hids-0.8

```

Now the fun and easy part.  We are going to run the installation script and let it do all the hard work.  Note: Here I enter a su shell for the sake of simplicity.  If you don't want to do this simply append "sudo" to the following commands
```

sudo -s
./install.sh

```

Go ahead and pick what language you want to read everything in and hit enter
```

 ** Para instalação em português, escolha [br].
  ** Fur eine deutsche Installation wohlen Sie [de].
  ** For installation in English, choose [en].
  ** Per l'installazione in Italiano, scegli [it].
  ** Aby instalowa&#263; w j&#281;zyku Polskim, wybierz [pl].
  ** Türkçe kurulum için seçin [tr].
  (en/br/de/it/pl/tr) [en]: ** en <enter> **

```

Next it is going to warn us that we need a C compiler on the machine. (you did install build-essentials didn't you?) and give you some general information about your computer (kernel version, user and host). Go ahead and hit enter likes it says.
```

OSSEC HIDS v0.8 Installation Script - http://www.ossec.net

 You are about to start the installation process of the OSSEC HIDS.
 You must have a C compiler pre-installed in your system.
 If you have any questions or comments, please send an e-mail
 to dcid@ossec.net (or daniel.cid@gmail.com).

  - System: Linux diana 2.6.15-25-k7
  - User: root
  - Host: diana


  -- Press ENTER to continue or Ctrl-C to abort. --
**<enter>**

```

Next select a local install
```

1- What kind of installation do you want (server, agent, local or help)? **local <enter> **

```

Now choose were you want to install it.  This HOWTO will choose the default
```

- Choose where to install the OSSEC HIDS [/var/ossec]: ** <enter> **

```

Now select you notification options.  You can choose my answers or different ones.  I would recommend setting "Y" to everything.  Active responses are really nice.  It will set some default configuration variables based on your answers and certian things it finds on your system.
```

3- Configuring the OSSEC HIDS.

  3.1- Do you want e-mail notification? (y/n) [y]: **y**
   - What's your e-mail address? **youremail@yourdomain.com**
   - What's your SMTP server ip/host? **your smtp server address (localhost)**

  3.2- Do you want to run the integrity check daemon? (y/n) [y]: **y**

   - Running syscheck (integrity check daemon).

  3.3- Do you want to run the rootkit detection engine? (y/n) [y]: **y**

   - Running rootcheck (rootkit detection).

  3.4- Active response allows you to execute a specific
       command based on the events received. For example,
       you can block an IP address or disable access for
       a specific user.
       More information at:
       http://www.ossec.net/en/manual.html#active-response

   - Do you want to enable active response? (y/n) [y]: **y**

     - Active response enabled.

   - By default, we can enable the host-deny and the
     firewall-drop responses. The first one will add
     a host to the /etc/hosts.deny and the second one
     will block the host on iptables (if linux) or on
     ipfilter (if Solaris, FreeBSD or NetBSD).
   - They can be used to stop SSHD brute force scans,
     portscans and some other forms of attacks. You can
     also add them to block on snort events, for example.

   - Do you want to enable the firewall-drop response? (y/n) [y]: **y**

     - firewall-drop enabled (local) for levels >= 6

   - Default white list for the active response:
      - 192.168.2.1

   - Do you want to add more IPs to the white list? (y/n)? [n]: **n**

  3.6- Setting the configuration to analyze the following logs:
    -- /var/log/messages
    -- /var/log/auth.log
    -- /var/log/syslog
    -- /var/log/mail.info
    -- /var/log/apache2/error.log (apache log)
    -- /var/log/apache2/access.log (apache log)

 - If you want to monitor any other file, just change
   the ossec.conf and add a new localfile entry.
   Any questions about the configuration can be answered
   by visiting us online at http://www.ossec.net .


   --- Press ENTER to continue ---

```

Now it will compile everything.  This shouldn't take too long to complete.  It only took around 1-2 minutes for my boxes.  After it is completed press enter to finish.
```

 - Unknown system. No init script added.

 - Configuration finished properly.

 - To start OSSEC HIDS:
                /var/ossec/bin/ossec-control start

 - To stop OSSEC HIDS:
                /var/ossec/bin/ossec-control stop

 - The configuration can be viewed or modified at /var/ossec/etc/ossec.conf


    Thanks for using the OSSEC HIDS.
    If you have any question, suggestion or if you find any bug,
    contact us at contact@ossec.net or using our public maillist at
    ossec-list@ossec.net
    (http://mailman.underlinux.com.br/mailman/listinfo/ossec-list).

    More information can be found at http://www.ossec.net

    ---  Press ENTER to finish (maybe more information bellow). ---

```

Now unfourtuntly it doesn't detect Ubuntu so it will not create an init script.  This is simple enough to take care of. (Yes, its basic. If you want to improve it please feel free to do so)  Copy and paste the following into /etc/init.d/ossec

```

#!/bin/sh

case "$1" in
start)
  /var/ossec/bin/ossec-control start
;;
stop)
  /var/ossec/bin/ossec-control stop
;;
restart)
  $0 stop && sleep 3
  $0 start
;;
reload)
  $0 stop
  $0 start
;;
*)
echo "Usage: $0 {start|stop|restart|reload}"
exit 1
esac

```

Now make it executable
```

cd /etc/init.d
chmod +x ossec

```

Add it to our runlevels so it starts on boot
```

update-rc.d ossec defaults

```

Now lets crank her up and make sure everything works
```

/etc/init.d/ossec start

```

If you get something like this, you should be in good shape.
```

Starting OSSEC HIDS v0.8 (by Daniel B. Cid)...
Started ossec-maild...
Started ossec-execd...
Started ossec-analysisd...
Started ossec-logcollector...
Started ossec-syscheckd...
Completed.

```

Now you can go on to customize the setup.  Chances are you going to want it to ignore certian directories and create your own rules.  Please check out the manual for excellent instructions on doing so.

Caveat: the check_xxx values listed in the documentation should appear as directory attributes (i.e. <directory blah blah check_perms yes>

Resources:
[OSSEC Homepage](http://www.ossec.net)
[OSSEC-HIDS Manual](http://www.ossec.net/en/manual.html)
Hi.
Just installed ossec last version (last updates).
Step by step, as shown in your tutorial, with implicite values, on a Ubuntu 6.0 LTS Server.
But, when I tried to start the service, the following messages appear:

ossec-maild(1501): ERROR: Invalid SMTP Server
ossec-maild(1202): Error: Configuration error at 'var/ossec/etc/ossec.conf'.Exiting

I am not using any SMTP Server, but I guess is installed automatically by Ubuntu SLT. OK. 
What I have to modify in the ossec.conf file?
Thank you.

---

### Post by blc2001ro on 2008-06-10
> **RShadow said:**
> This HOWTO will walk you through the very simple installation of the [OSSEC-HIDS](http://www.ossec.net) application.  Before we continue lets make sure everybody is on the same sheet of music.

1. OSSEC-HIDS is a host based intrusion detection system.  It is a very flexible system that will allow you to achieve the following.

[INDENT][LIST]
[*]rootkit detection
[*]file system integrity
[*]log file analysis
[*]time based alerting
[*]active responses
[/LIST][/INDENT]

Taken from the ossec-hids FAQ
"OSSEC HIDS is an Open Source Host-based Intrusion Detection System. It performs log analysis, integrity checking, rootkit detection, time-based alerting and active response"

2. This howto is based on the following assumptions
[INDENT][LIST]
[*]You are running an up to date installation of Dapper
[*]You are preforming a "local" installation (i.e. a single host)
[/LIST][/INDENT]

3. The majority of this HOWTO is taken directly from the [Installation Manual](http://www.ossec.net/en/manual.html) for OSSEC-HID which is a very easy to follow Manual.  If you run into trouble please look at the Manual first as it will always have the most up to date information.

Ok, Now that we are all together lets proceed.  As mentioned above this HOWTO will only cover a local installation.  ossec-hids has the ability to monitor multiple hosts all using the same ruleset.  This is accomplished by installed the ossec-hids server on one machine and then doing an agents installation on every other machine you wish to protect.  The agents communicate to the server via a secure connection.  If you need this type of setup please take a look at the [manual](http://www.ossec.net/en/manual.html), however the installation is not very different (just different options available in your conf file is about it.  The other nice thing is that the agents portion of the application will also run under a windows host.  This allows those of you that have to and/or want to run a windows box to secure that as well (install the server on your /flamebait/ superior /flamebait/ Linux box and the agent on your windows box)

Now the first thing we need to do is grab the latest sources.  For this HOWTO we will be installing 0.8, however feel free to get the latest copy available from their site.  We also need to install some stuff so we can compile it later.
```

sudo apt-get install build-essentials
cd ~
mkdir src
cd src
wget http://www.ossec.net/files/ossec-hids-0.8.tar.gz
http://www.ossec.net/files/ossec-hids-0.8_checksum.txt

```

Before we go ahead and extract this, lets make sure we got what we think we got. Verify the checksums in the .txt file and the same that the commands below output.  THIS IS IMPORTANT -- DON'T SKIP IT --
```

cat ossec-hids-0.8_checksum.txt
md5sum ossec-hids-0.8.tar.gz
sha1sum ossec-hids-0.8.tar.gz

```

Well now, after verifying you have legit files (you did do that didn't you?) lets extract this bugger
```

tar -zxvf ossec-hids-0.8.tar.gz
cd ossec-hids-0.8

```

Now the fun and easy part.  We are going to run the installation script and let it do all the hard work.  Note: Here I enter a su shell for the sake of simplicity.  If you don't want to do this simply append "sudo" to the following commands
```

sudo -s
./install.sh

```

Go ahead and pick what language you want to read everything in and hit enter
```

 ** Para instalação em português, escolha [br].
  ** Fur eine deutsche Installation wohlen Sie [de].
  ** For installation in English, choose [en].
  ** Per l'installazione in Italiano, scegli [it].
  ** Aby instalowa&#263; w j&#281;zyku Polskim, wybierz [pl].
  ** Türkçe kurulum için seçin [tr].
  (en/br/de/it/pl/tr) [en]: ** en <enter> **

```

Next it is going to warn us that we need a C compiler on the machine. (you did install build-essentials didn't you?) and give you some general information about your computer (kernel version, user and host). Go ahead and hit enter likes it says.
```

OSSEC HIDS v0.8 Installation Script - http://www.ossec.net

 You are about to start the installation process of the OSSEC HIDS.
 You must have a C compiler pre-installed in your system.
 If you have any questions or comments, please send an e-mail
 to dcid@ossec.net (or daniel.cid@gmail.com).

  - System: Linux diana 2.6.15-25-k7
  - User: root
  - Host: diana


  -- Press ENTER to continue or Ctrl-C to abort. --
**<enter>**

```

Next select a local install
```

1- What kind of installation do you want (server, agent, local or help)? **local <enter> **

```

Now choose were you want to install it.  This HOWTO will choose the default
```

- Choose where to install the OSSEC HIDS [/var/ossec]: ** <enter> **

```

Now select you notification options.  You can choose my answers or different ones.  I would recommend setting "Y" to everything.  Active responses are really nice.  It will set some default configuration variables based on your answers and certian things it finds on your system.
```

3- Configuring the OSSEC HIDS.

  3.1- Do you want e-mail notification? (y/n) [y]: **y**
   - What's your e-mail address? **youremail@yourdomain.com**
   - What's your SMTP server ip/host? **your smtp server address (localhost)**

  3.2- Do you want to run the integrity check daemon? (y/n) [y]: **y**

   - Running syscheck (integrity check daemon).

  3.3- Do you want to run the rootkit detection engine? (y/n) [y]: **y**

   - Running rootcheck (rootkit detection).

  3.4- Active response allows you to execute a specific
       command based on the events received. For example,
       you can block an IP address or disable access for
       a specific user.
       More information at:
       http://www.ossec.net/en/manual.html#active-response

   - Do you want to enable active response? (y/n) [y]: **y**

     - Active response enabled.

   - By default, we can enable the host-deny and the
     firewall-drop responses. The first one will add
     a host to the /etc/hosts.deny and the second one
     will block the host on iptables (if linux) or on
     ipfilter (if Solaris, FreeBSD or NetBSD).
   - They can be used to stop SSHD brute force scans,
     portscans and some other forms of attacks. You can
     also add them to block on snort events, for example.

   - Do you want to enable the firewall-drop response? (y/n) [y]: **y**

     - firewall-drop enabled (local) for levels >= 6

   - Default white list for the active response:
      - 192.168.2.1

   - Do you want to add more IPs to the white list? (y/n)? [n]: **n**

  3.6- Setting the configuration to analyze the following logs:
    -- /var/log/messages
    -- /var/log/auth.log
    -- /var/log/syslog
    -- /var/log/mail.info
    -- /var/log/apache2/error.log (apache log)
    -- /var/log/apache2/access.log (apache log)

 - If you want to monitor any other file, just change
   the ossec.conf and add a new localfile entry.
   Any questions about the configuration can be answered
   by visiting us online at http://www.ossec.net .


   --- Press ENTER to continue ---

```

Now it will compile everything.  This shouldn't take too long to complete.  It only took around 1-2 minutes for my boxes.  After it is completed press enter to finish.
```

 - Unknown system. No init script added.

 - Configuration finished properly.

 - To start OSSEC HIDS:
                /var/ossec/bin/ossec-control start

 - To stop OSSEC HIDS:
                /var/ossec/bin/ossec-control stop

 - The configuration can be viewed or modified at /var/ossec/etc/ossec.conf


    Thanks for using the OSSEC HIDS.
    If you have any question, suggestion or if you find any bug,
    contact us at contact@ossec.net or using our public maillist at
    ossec-list@ossec.net
    (http://mailman.underlinux.com.br/mailman/listinfo/ossec-list).

    More information can be found at http://www.ossec.net

    ---  Press ENTER to finish (maybe more information bellow). ---

```

Now unfourtuntly it doesn't detect Ubuntu so it will not create an init script.  This is simple enough to take care of. (Yes, its basic. If you want to improve it please feel free to do so)  Copy and paste the following into /etc/init.d/ossec

```

#!/bin/sh

case "$1" in
start)
  /var/ossec/bin/ossec-control start
;;
stop)
  /var/ossec/bin/ossec-control stop
;;
restart)
  $0 stop && sleep 3
  $0 start
;;
reload)
  $0 stop
  $0 start
;;
*)
echo "Usage: $0 {start|stop|restart|reload}"
exit 1
esac

```

Now make it executable
```

cd /etc/init.d
chmod +x ossec

```

Add it to our runlevels so it starts on boot
```

update-rc.d ossec defaults

```

Now lets crank her up and make sure everything works
```

/etc/init.d/ossec start

```

If you get something like this, you should be in good shape.
```

Starting OSSEC HIDS v0.8 (by Daniel B. Cid)...
Started ossec-maild...
Started ossec-execd...
Started ossec-analysisd...
Started ossec-logcollector...
Started ossec-syscheckd...
Completed.

```

Now you can go on to customize the setup.  Chances are you going to want it to ignore certian directories and create your own rules.  Please check out the manual for excellent instructions on doing so.

Caveat: the check_xxx values listed in the documentation should appear as directory attributes (i.e. <directory blah blah check_perms yes>

Resources:
[OSSEC Homepage](http://www.ossec.net)
[OSSEC-HIDS Manual](http://www.ossec.net/en/manual.html)
OK. On Ubuntu 6 SLT, step by step installation and configuration as shown in the topic (with latest packages)....But, when to start...

ossec-maild(1501) ERROR:Invalid SMTP Server
ossec-maild(1202) ERROR Configuration error at '/var/ossec/etc/ossec.conf'. Exiting


I do not have am SMTP server configured, I guess is the one installeb by default by the Ubuntu 6 LTS. 
What do I have to do?

---

### Post by pytheas22 on 2008-06-10
> I do not have am SMTP server configured, I guess is the one installeb by default by the Ubuntu 6 LTS.
What do I have to do?

It's not referring to an SMTP server installed on the OSSEC server.  OSSEC doesn't use a local SMTP server to send mail (unless you tell it to); it uses any SMTP server anywhere on the Internet.  For example, mine uses a Gmail SMTP server, because I receive alerts at a gmail account.

The OSSEC installer should have asked you for the email address that you wanted to use to receive email alerts, and based on that address it should have automatically detected which SMTP server to use.  Maybe it made a mistake in detecting the server, or maybe your email address is not correct?  Look in /var/ossec/etc/ossec.conf to see which options you have specified.  Email options should be right at the top.

---

### Post by hansoffate on 2008-09-18
> **pytheas22 said:**
> It's not referring to an SMTP server installed on the OSSEC server.  OSSEC doesn't use a local SMTP server to send mail (unless you tell it to); it uses any SMTP server anywhere on the Internet.  For example, mine uses a Gmail SMTP server, because I receive alerts at a gmail account.

The OSSEC installer should have asked you for the email address that you wanted to use to receive email alerts, and based on that address it should have automatically detected which SMTP server to use.  Maybe it made a mistake in detecting the server, or maybe your email address is not correct?  Look in /var/ossec/etc/ossec.conf to see which options you have specified.  Email options should be right at the top.

Did you have to configure authentication to the gmail smtp server?  Did you just use smtp.gmail.com and it worked?

BTW, great job on the guide, it worked flawlessly.

---

### Post by pytheas22 on 2008-09-18
> Did you have to configure authentication to the gmail smtp server? Did you just use smtp.gmail.com and it worked?

My smpt server is 'alt1.gmail-smtp-in.l.google.com.'  I think OSSEC auto-detected it when I gave it my email address during the installation.  I don't know if specifying just smtp.google.com would work, but maybe.

---

### Post by bodhi.zazen on 2008-09-18
When installing, I just said no, and disabled e-mail notification altogether. I use the web interface instead ;)

---

### Post by Mrvyper2u on 2008-12-07
Thanks for the great How To.

I have a Gutsy or Hardy server and had to 
apt-get install gcc 
and 
apt-get install libc6-dev

for this how to, to work.

There was no "Build Essentials" there was "build essential" but that did not install the libc6-dev and gcc. 
I could have been doing something wrong but this post is in case someone else has similar problems.

I had errors similar to below when libc6-dev was not installed.

[I]>  *** Making zlib (by Jean-loup Gailly and Mark Adler)  ***
> make[1]: Entering directory
> `/root/installs/ossec-hids-1.3/src/external/zlib-1.2.3'
> gcc -c -g -Wall -I../../ -I../../headers  -DDEFAULTDIR=\"/var/ossec\"
> -DARGV0=\"zlib\" -DXML_VAR=\"var\" -DOSSECHIDS *.c
> In file included from crc32.c:29:
> zutil.h:23:22: error: string.h: No such file or directory
> zutil.h:24:22: error: stdlib.h: No such file or directory
> zutil.h:38:23: error: errno.h: No such file or directory
> In file included
> from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
[/I]

Hope this helps

---

### Post by SyL on 2009-04-10
Very nice topic! Thx!

What do you think about [Tiger ]("http://www.nongnu.org/tiger/")(which is in the repository)?

---

### Post by bodhi.zazen on 2009-04-10
> **SyL said:**
> Very nice topic! Thx!

What do you think about [Tiger ]("http://www.nongnu.org/tiger/")(which is in the repository)?

Tiger is discussed in the security thread :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by SyL on 2009-04-14
> **bodhi.zazen said:**
> Tiger is discussed in the security thread :

[Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812")


Thanks, for remind me your useful topic!
Nevertheless, i'm interesting to know your opinion regarding the difference between OSSEC and Tiger, as they are both HIDS.
OSSEC is obviously much bigger, but Tiger is still the only mentioned in Debian's security documentation.


Cheers

---

### Post by drinkydoo on 2009-12-18
Hello Everyone! First of all thanks so much for such a wonderful thread, these were the instructions that helped me (very noob) to get ossec on Ubuntu. 

My configuration is a Server-agent installation, i am stuck (and have been for the last week) trying to run the Manage_Agents tool on the server to add the agents and get the key, etc....

I get a permission denied error, please help!

Thanks in advance for all the help!

---

### Post by pytheas22 on 2009-12-18
drinkydoo: it sounds like you need to be root.  Prefix your commands with "sudo" and it should work, e.g.:
```

sudo /var/ossec/bin/manage_agents
```

---

### Post by drinkydoo on 2009-12-19
THANKS SO MUCH PYTHEAS22!!!!!!

You just saved a noob from shooting himself!

Thanks a ton !!!!

---

### Post by drinkydoo on 2009-12-20
Noobie here bothering again...

I got everything running fine, now i need to add another email address to send emails to, how can i access the conf file or how do i do so? I also want to modify the alerts i get via email...

i tried /var/ossec/etc/ossec.conf and also with sudo but says comand not found..


Thanks in advance!

---

### Post by pytheas22 on 2009-12-20
> **drinkydoo said:**
> Noobie here bothering again...

I got everything running fine, now i need to add another email address to send emails to, how can i access the conf file or how do i do so? I also want to modify the alerts i get via email...

i tried /var/ossec/etc/ossec.conf and also with sudo but says comand not found..


Thanks in advance!

You need to open the configuration file with a text editor, so you would type something like:
```

sudo nano /var/ossec/etc/ossec.conf
```

(Replace 'nano' with 'vi', 'emacs', 'gedit', etc. depending on which text editor you prefer.)

Not sure if OSSEC can send reports to more than one email address, however.  I think I tried this once and couldn't get it to work.  But maybe it was just me.

To modify which alerts send emails, you need to edit the rules files; you can also change the minimum alert level that results in an email by changing the value in the main ossec.conf file (but note that some rules override this value, if they have the <alert_by_email> flag set).  This mail thread might be useful for you: [http://www.mail-archive.com/ossec-list@googlegroups.com/msg02885.html](http://www.mail-archive.com/ossec-list@googlegroups.com/msg02885.html)

---

### Post by drinkydoo on 2009-12-21
Hello Pyhtheas22 Thanks for your awesome help...one last thing...i cant save after doing changes...it tells me its a read only... i used gedit
 
I am really sorry to ask this stupid questions, but im very bnew to ubunto so im in the leraning process..
 
 
Thanks in advance!

---

### Post by pytheas22 on 2009-12-21
You may need to make the file writeable first.  Try typing:
```

sudo chmod +w /var/ossec/etc/ossec.conf
```

Then try editing it again and you should be able to save changes.

---

### Post by drinkydoo on 2009-12-21
Thanks Pytheas22..
 
I trried the sudo chmod -w.... and then sudo gedit ....
 
It tells me i cant save its a read only disk...
 
Im so sorry for asking so much dumb noob questions...
 
Thanks in advance!

---

### Post by pytheas22 on 2009-12-22
That's strange.  What is the output of these commands:
```

sudo ls -l /var/ossec
sudo ls -l /var/ossec/etc
mount
```

Sorry for the slow reply; I was traveling.

---

### Post by klikevil on 2011-02-09
> **RShadow said:**
> Nobody's interested?


Sorry for the necro bump, but thanks thsi helped me with an init script question, but anyway.. now do one for samhain!

---

### Post by jbeiter on 2011-06-21
How do you tell it to use a different smtp port? My isp blocks port 25... I need to use 587 or 465.

---

### Post by drifting on 2011-08-18
Well the install went really well. Thank you so much.

But has anyone tried installing the OSSECWUI ?

mv: cannot move `ossec-wui-0.3' to `/var/www/htdocs/ossec-wui': No such file or directory

Is all I get? Do I manually create the directories?

Regards Paul

---

### Post by bodhi.zazen on 2011-08-18
the wui is nice, yes you will need to install apache and put those files into an existing directory.

---

### Post by drifting on 2011-08-18
Hi, thanks for the reply.

Apache is already installed, this server is my Mythbox as well as gateway. Any hint on where I should put those files? which existing directory? Oh and by the way I am running 11.04 

Regards Paul

---

### Post by bodhi.zazen on 2011-08-18
Apache uses /var/www , you can organize the content in that file any way you wish.

---

### Post by drifting on 2011-08-25
Well I have the WUI running as suggested, but it is complaining of having no agent? which is odd as I setup a local only install? Anyone else seen this problem? Suppose a wade through the OSSEC docs is next?

---

### Post by tehowe on 2012-01-11
So I managed to get OSSEC and OSSEC-WUI up and running. I guess I'll let the email notification go since it doesn't support SMTP auth and I don't want to set up a local server.

However, it doesn't seem to be reading the firewall. I took a stab at it and added this to 

sudo nano /var/ossec/etc/ossec.conf

```
 <localfile>
     <log_format>syslog</log_format>
     <location>/var/log/ufw.log</location>
  </localfile>
```But OSSEC-WUI reports

```
Hour     Alerts     Alerts %     Syscheck     Syscheck %     Firewall     Firewall %     Total     Total %
Hour 0     251     100.0%     7,533          100.0%           0           0.0%           9,990     100.0%
```Oh, it's picking up all those ecryptfs alerts that 11.04 seems to generate in syslog, but nothing showing for the firewall, which unless I miss my guess is the whole point of active monitoring

Meanwhile, I'm getting a couple scans a minute when I check 

```
tail -f /var/log/ufw.log
```Is there a better approach? Is ufw.log incompatible with the 'syslog' template OSSEC provides? There must be a way to get this going. Or does the fact UFW is blocking everything mean it's working as desired?

Thanks in advance for any help, and to senseis RShadow, bodhi.zazen and others for their expertise.

---

### Post by bodhi.zazen on 2012-01-11
Personally I use snort for network monitoring (and OSSEC for host monitoring).

---

### Post by sharathshanker on 2013-02-02
I am getting the following error while connecting to ossec manager .can any one answer hoe to resolve this? 

please reply very soon... awaiting for reply.




Process locked. Waiting for permission...

2013/02/02 22:13:09 ossec-agent(4101): WARN: Waiting for server reply (not started). Tried: '192.168.168.1'.

2013/02/02 22:13:11 ossec-agent: INFO: Trying to connect to server (192.168.168.1:1514).

2013/02/02 22:13:11 ossec-agent: INFO: Using IPv4 for: 192.168.168.1 .

2013/02/02 22:13:32 ossec-agent(4101): WARN: Waiting for server reply (not started). Tried: '192.168.168.1'.

2013/02/02 22:13:52 ossec-agent: INFO: Trying to connect to server (192.168.168.1:1514).

2013/02/02 22:13:52 ossec-agent: INFO: Using IPv4 for: 192.168.168.1 .

2013/02/02 22:14:13 ossec-agent(4101): WARN: Waiting for server reply (not started). Tried: '192.168.168.1'.

2013/02/02 22:14:51 ossec-agent: INFO: Trying to connect to server (192.168.168.1:1514).

2013/02/02 22:14:51 ossec-agent: INFO: Using IPv4 for: 192.168.168.1 .

2013/02/02 22:15:12 ossec-agent(4101): WARN: Waiting for server reply (not started). Tried: '192.168.168.1'.

---

### Post by cprofitt on 2013-02-02
Is that error on a client machine?  Have you checked your server to ensure it is up and running 100%?  Did you put the right 'key' in the client machine?

---

### Post by Clicksights on 2013-04-13
Hi,

i installed OSSEC on my laptop, including the webpanel, and want to do an agent install on my server(s).
I used Bodhi Zazen his tuto: [http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662) and than found this thread.
And after a succesful install on my laptop i suddenly have 3 new users, "ossec", "ossecr" and "ossecm".
Is this normal or did i go wrong somewhere along the way? It is nowhere mentioned....

The webinterface works, all seems ok.
Just asking for conformation.

-Ubuntu 12.04 LTS

---

### Post by st4rtx on 2013-07-14
hi all,
i setup ossec server on linux and have a windows(jost for  test!) for agent i want test ossec sys check but when i change perm or  owner of monitoring file ossec not detect i test it on windows and linux  os but ossec nit detect it ! how can i use of this fiuther?

---

