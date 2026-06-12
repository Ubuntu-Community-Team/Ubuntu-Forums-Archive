---
title: "Host-based Intrusion Detection Systems (HIDS)"
date: 2010-05-09
forum: Security
---

### Post by bodhi.zazen on 2010-05-09
[SIZE=6][CENTER]Host-based Intrusion Detection Systems (HIDS)[/CENTER]
[/SIZE]
Intrusion detection can be divided into three broad categories: NIDS, HIDS, and vulnerability scans. In this post I will review several options for HIDS and OpenVAS (vulnerability scanner). If you are wanting information on NIDS, see the [NIDS sticky]("http://ubuntuforums.org/showthread.php?t=1477696")

Most Windows users are familiar with [HIDS]("http://en.wikipedia.org/wiki/Host-based_intrusion_detection_system"). Examples include virus and spyware scanners. HIDS monitor system files and detect unauthorized changes and _known_ threats / [malware]("http://en.wikipedia.org/wiki/Malware").

_Many Linux users may feel these tools are of limited utility because_:

1. These tools are notorious for quirks, hiccups, and the sky is falling. As with the boy who cried wolf, excessive warnings and false positives tend to get ignored.

2. These tools detect only known vulnerabilities and thus do not protect against "[zero day exploits]("http://en.wikipedia.org/wiki/Zero_day_attack")". Known vulnerabilities are generally patched rapidly in Linux. Thus many people are of the opinion keeping their systems up to date is sufficient and these tools are superfluous.

3. The majority of these tools are command line tools with limited, if any, graphical interface (web interfaces are more common). Some people tend to shy away from tools lacking a graphical interface.

4. Although every OS has potential security holes, many users find Ubuntu is "secure enough" such that additional measures are not warranted . For an overview of this mentality, see [this discussion]("http://www.theregister.co.uk/2004/10/22/security_report_windows_vs_linux/") .


This post is for those who are interested in "learning the ropes" and will review HIDS tools. IMO it is best to try these tools out **before you suspect your system is compromised**.

[COLOR=navy]Security is an advanced topic on any OS, requires knowledge of how the OS works, and comes with a steep learning curve (yes, you are expected to read). If you find these tools overwhelming, I suggest you start with the [Security Sticky]("http://ubuntuforums.org/showthread.php?t=510812") and come back to these tools when you are more comfortable with Linux, the command line, and/or have the time to work through the use of these tools.[/COLOR]


_Contents_ :

[First steps]("http://ubuntuforums.org/showpost.php?p=9265535&postcount=2")
[OSSEC]("http://ubuntuforums.org/showpost.php?p=9265566&postcount=3")
[OpenVAS]("http://ubuntuforums.org/showpost.php?p=9265600&postcount=4")
[Alternatives to OSSEC / OpenVAS]("http://ubuntuforums.org/showpost.php?p=9265617&postcount=5")
[Tiger]("http://ubuntuforums.org/showpost.php?p=9265631&postcount=6")
[chkrootkit]("http://ubuntuforums.org/showpost.php?p=9265639&postcount=7")
[rkhunter]("http://ubuntuforums.org/showpost.php?p=9265649&postcount=8")
[clamav]("http://ubuntuforums.org/showpost.php?p=9265657&postcount=9")


[SIZE=2][COLOR=navy]**Etiquette: If you are going to run these HIDS/Vulnerability tools, please read the documentation  (FAQ / README ) and perform a Google search on the results of alerts or warnings before posting on the Ubuntu forums. These tools have esoteric tendencies and support may be limited on the Ubuntu forums. Please see the various home pages / wiki and/or use the application specific forums / mailing lists for support.**[/COLOR][/SIZE]

[Discussion Thread](http://ubuntuforums.org/showthread.php?p=9265855#post9265855) - The discussion thread is for comments / feedback. Please do not use the discussion tread for support questions, start a support thread in the security forums.

---

### Post by bodhi.zazen on 2010-05-09
[center][size=6]First steps[/size][/center]


There is a nice review of the issues with HIDS [**here**](http://www.symantec.com/connect/articles/host-integrity-monitoring-best-practices-deployment). It was written in 2004, but the basic principles still apply.

IMO the foundation of HIDS is with understanding how your OS works and what types of activity are "normal". If you are new to Ubuntu or Linux security I suggest you start with the [Security Sticky](http://ubuntuforums.org/showthread.php?t=510812). In addition I suggest :


1. Keep your systems up to date, at least with security updates. Consider security only automatic updates (I set synaptic to do this).

2. Learn the following commands:

```
w
last
netstat -tulnp
ps aux # or variants
top
```


3. Familiarize yourself with the [Log files](https://help.ubuntu.com/community/LinuxLogFiles). IMO the two most relevant to HIDS are /var/log/messages and /var/log/auth.log. You may view the logs with any number of tools including System -> Administration ->  Log File Viewer or install [Logwatch](https://help.ubuntu.com/community/Logwatch).

/var/log/messages -> apparmor logs here
/var/log/auth.log -> logins and sudo access.

```
grep sudo --color=always /var/log/auth.log
```

To track user commands use [acct](http://www.cyberciti.biz/tips/howto-log-user-activity-using-process-accounting.html)

Consider installing [faillog](http://manpages.ubuntu.com/manpages/hardy/man8/faillog.8.html) (locks user accounts after failed log in attempts).

[My blog post on faillog](http://blog.bodhizazen.net/linux/ubuntu-how-to-faillog/)

Also watch the logs for your servers, particularly any error logs.

/var/log/apache2/error.log

Last, consider using logwatch. Logwatch will analyse your log files and generate a summary report. The report is a summary and you may need to manually review the logs for more specific information.

[Logwatch](http://www.debianhelp.co.uk/logwatch1.htm) - Written for Debian, but works with Ubuntu.


4. Know what services (servers) are running (hint see the netstat command above) and how to secure them (firewall, ssh keys, fail2ban, denyhosts, etc).

Keep in mind, the most common Ubuntu security breaches are due to ;

  1. Installing servers - SSH and VNC (desktop sharing )in particular - with weak passwords and port forwarding (allowing connections from the internet).

  2. Installing packages (software) or running commands / scripts from untrusted sources. This may include ppa, web sites such as gnome-look.org, and even Linux user forums. 

  3. [Social engineering](http://en.wikipedia.org/wiki/Social_engineering_(security)) which then results in #2 ...

  4. [Phishing](http://en.wikipedia.org/wiki/Phishing) - evil twin of Social engineering.


5. Learn to use [Apparmor](http://ubuntuforums.org/showthread.php?t=1008906). [bodhi.zazen's Ubuntu 10.04 apparmor profiles](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/). Although Apparmor is not a HIDS tool, I highly suggest you use apparmor to confine as many, if not all, network aware applications.


6. Highly recommended - Integrit / Tripwire / Aide (Advanced Intrusion Detection Environment) - These tools monitor system files for changes. These tools are fairly straight forward to configure, however they may need some customization (read the configuration file and documentation). Unless you want to review a long list of changes, consider not monitoring files expected to change ( /var/log/* , /tmp , /mnt , /media , /proc ). See [This blog](http://www.ccrow.org/?p=246) for tips.

[Integrit](http://www.debian-administration.org/articles/49) - Integrit is very easy to both configure and run, IMO it works well.

Advantage - Very easy to install, customize, and configure (it gets the job done).
Disadvantage - The report may be too brief for some.

Tripwire -
[How to tripwire](http://remoteadmin.org.uk/tutorials/42-linux/56-tripwire-ubuntu)
[How to Centralwire (centralized server for tripwire)](http://www.ubuntugeek.com/web-based-centralized-console-for-tripwire.html#more-3067)
[Detailed how-to tripwire](http://www.alwanza.com/howTo/linux/tripwire.html)

Advantage - One can customize what directories are monitored.
Disadvantage - Many of the files will change over time, particularly logs, so you may need to fine tune what is monitored.

Tripwire needs some Ubuntu specific adjustments in the configuration file. For example, adding /etc/init and remove monitoring of some files in /root .


Aide - Debian / Ubuntu highly customize aide and I highly suggest you read the (Debian / Ubuntu) documentation. It is located at /usr/share/doc/aide-common/README.Debian.gz [Online README.Debian](http://svn.debian.org/wsvn/pkg-aide/trunk/debian/aide-common.README.Debian?op=file&rev=0&sc=0).

Despite the guides below, aide is configured to:

1. Automatically generate a daily report. The report is mailed to root and is in /var/mail/root
2. It generates a lot of noise, you may wish to exclude a few directories - Delete the delete 99_aide_root, 70_aide_var, and 70_aide_tmp files.
3. Run with a wrapper script. Simply substitute "aide.wrapper" for "aide" in the commands in the guides below 

ie - 

aide.wrapper --init rather then aide --init
aide.wrapper --check rather then aide --check


[AIDE: Advanced Intrusion Detection Environment](http://www.debuntu.org/intrusion-detection-with-aide)
[Ubuntu wiki AIDE](https://help.ubuntu.com/community/FileIntegrityAIDE)
[Ubutu 8.04](http://www.ccrow.org/?p=246)



7. Optional - [Ninja](http://blog.bodhizazen.net/linux/how-to-ninja-ubuntu-10-04/) monitors your system for unauthorized root access.

8. "Don't panic" - Douglas Adams ([The Hitchhiker's Guide to the Galaxy](http://movies.about.com/library/graphics/hitchhikersguidepubb.jpg)).

[Back to top](http://ubuntuforums.org/showthread.php?t=1477662)

---

### Post by bodhi.zazen on 2010-05-09
[CENTER][SIZE=6]OSSEC[/SIZE][/CENTER]

[OSSEC]("http://www.ossec.net/main/about/")

Advantages of OSSEC :

1. Open source (yea).

2. OSSEC monitors integrity of system and log files.

3. Root kit detection.

4. An active response system. This means OSSEC will not only monitor, but also respond to threats (black list naughty IP addresses).

5. Optional web based graphical (monitoring) interface.

6. Optional central server (consolidates monitoring multiple systems).

7. OSSEC is *relatively* easy to set up.


The potential disadvantage of ossec, you would need to install apache to use the web interface. If you are already running a headless or remote server with apache then adding the ossec-wui is not as drastic. If you are on a Desktop you can bind apache to localhost (127.0.0.1) and restrict external connections with iptables (see below).

Home page: [http://www.ossec.net/](http://www.ossec.net/)

[OSSEC manual]("http://www.ossec.net/main/manual")
[OSSEC FAQ]("http://www.ossec.net/main/manual/manual-faq/")

[SIZE=4]Download and install OSSEC[/SIZE]

Install Dependencies (gcc)

```
apt-get install -y gcc
```Download the latest version of OSSEC

```
wget http://www.ossec.net/files/ossec-hids-2.4.tar.gz
```Extract the archive and install

```
tar xvf ossec-hids-2.4.tar.gz
cd ossec-hids-2.4
sudo ./install.sh
```The installation is very easy, you simply answer a few questions or hit the enter key for the defaults. The only question you have to answer is "What kind of installation do you want (server, agent, local or help)?" , at that question type "local" and hit enter (see below).

Select your language 

Select "local" as the type of installation

> What kind of installation do you want (server, agent, local or help)? localThe only default I personally change is the email report. Because I prefer the web interface I answer no to this question.

> Do you want e-mail notification? (y/n) [y]:nOtherwise go with the defaults (hit enter).

[SIZE=4]Start ossec[/SIZE]

```
sudo /etc/init.d/ossec start
```
[SIZE=4]Install and configure the web interface[/SIZE]

Step 1: Install apache and php5

```
sudo apt-get -y install apache2 php5
```Setp 2: Download and configure the wui (Web User Interface)

```
cd /var/www
sudo wget http://www.ossec.net/files/ui/ossec-wui-0.3.tar.gz
sudo tar xvf ossec-wui-0.3.tar.gz
sudo rm ossec-wui-0.3.tar.gz
sudo mv ossec-wui-0.3 ossec
```cd into the ossec directory and install ossec

```
cd /var/www/ossec
sudo ./setup.sh
```As the wui is installed you will be asked a user name and password. Enter the user name and password of your choice.

Set the proper permissions of the ossec directory:

```
sudo chown -R www-data.www-data /var/www/ossec
```Add www-data to the ossec group

```
sudo nano /etc/group
```Find the ossec line (most likely at the bottom of the file) and add www-data to the ossec group

> [noparse]ossec:x:1001:www-data[/noparse]Save and exit nano

Set the permissions of /var/www/ossec/tmp

```
sudo chmod 770 /var/www/ossec/tmp
sudo chgrp www-data /var/www/ossec/tmp
```Restart apache

```
sudo service apache2 restart
```Open the page with firefox and go to the ossec directory

[http://localhost/ossec](http://localhost/ossec)
[http://ip_address/ossec](http://ip_address/ossec)

As is typical of HIDS, be prepared to read up on any alerts you receive from OSSEC.

[SIZE=4]Restricting access to the ossec-wui[/SIZE]

1. Using Apache.

Edit your Virtual Host. Unless you defined a virtual host for ossec, the default is /etc/apache2/sites-available/default

Under the section <Directory /var/www> edit the following lines :

From
> Order allow,deny
allow from allTo

```
Order deny,allow
Deny from all
Allow from 127.0.0.0/255.0.0.0 ::1/128
```Restart Apache

```
sudo service apache2 restart
```2. With iptables

One line (assuming your default policy is ACCEPT):

```
sudo iptables -A INPUT -p tcp -m tcp --dport 80 ! -s 127.0.0.1 -j DROP
```3. As an alternate to iptables, simply enable ufw

```
sudo ufw enable
```That will block incoming requests to apache (connections from localhost are allowed).

4. If you connect to the ossec wui, from an external client, especially over the internet, I highly advise you use ssl (https) and password protect the ossec directory.

There are several tutorials on the internet [**including the Ubuntu wiki**]("https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html") is, IMO, a nice start.

[Apache documentation Authentication, Authorization and Access Control]("http://httpd.apache.org/docs/2.1/howto/auth.html")

5. If you do NOT have access to the apache configuration file , use .htaccess :

[Password protecting a directory with Apache and .htaccess]("http://www.debiantutorials.net/password-protecting-a-directory-with-apache-and-htaccess/")

[Apache Web Login Authentication]("http://www.yolinux.com/TUTORIALS/LinuxTutorialApacheAddingLoginSiteProtection.html#ALTAUTH")

[Apache Tutorial: .htaccess files]("http://httpd.apache.org/docs/2.1/howto/htaccess.html")

> In general, you should never use .htaccess files unless you don't have access to the main server configuration file. There is, for example, a prevailing misconception that user authentication should always be done in .htaccess files. This is simply not the case. You can put user authentication configurations in the main server configuration, and this is, in fact, the preferred way to do things.[Back to top]("http://ubuntuforums.org/showthread.php?t=1477662")

---

### Post by bodhi.zazen on 2010-05-09
[center][size=6]OpenVAS[/size][/center]

[OpenVAS](http://www.openvas.org/) (Open Vulnerability Assessment System) is, as the name implies, is used for vulnerability testing rather then a method of monitoring your host for changes.

OpenVAS is feature rich and this post will get you started, see the [online documentation](http://www.openvas.org/compendium/openvas-compendium.html) for additional details.

[size=4]Install the OpenVAS server and client[/size]

Openvas is in the Ubuntu 10.04 repositories.

```
sudo apt-get -y install openvas-server openvas-client nikto
```

The installation process will configure (server) certificates, but will not make an openvas user certificate.

wapiti and w3af were problems, you may have to run them manually.

The default icon is ugly, I downloaded and used [**this one**](http://i.zdnet.com/blogs/open_vas.jpg).

[size=4]Create a user[/size]

```
sudo openvas-adduser
```

Add a user and assign a password. You can either leave the roles blank or assign roles (see man openvas-adduser). Roles define which hosts a user is allowed to audit.

Syntax:
accept host_ip
accept host_name
accept netmask
default deny

For example, these rules restrict the audits to your LAN.
```
accept 192.168.0.0/24
default deny
```

In a nutshell, a Role == what host you are allowed to scan.

If you wish to use user certificates you will need to generate them yourself.

[size=4]Update rules[/size]

```
sudo openvas-nvt-sync
```

The command failed for me, I downloaded the update from

[http://www.openvas.org/openvas-nvt-feed-current.tar.bz2](http://www.openvas.org/openvas-nvt-feed-current.tar.bz2)

I extracted the contents (be warned, they are not packaged neatly, I suggest you extract them into a directory).

Copied the *.nasl to /var/lib/openvas/plugins/

(Re)Start openvas

```
service openvas-server start & #Yes, I needed the &
```

Scan the host (you can only scan a host that has openvas-server installed).

[size=4]Openvas client[/size]

_Command line_: 

The file hostname.txt must exist

```
echo openvas_server_ip_address > openvas_hostname.txt
```

Syntax :
> openvas-client -q hostname port user password hostname.txt results.html -T html

For example :

```
echo 127.0.0.1 > localhost.txt
openvas-client -q localhost 127.0.0.1 bodhi bodhi's_password localhost.txt results_localhost.html -T html
```

View the results with

```
firefox results_localhost.html
```

_GUI tool_

Open the client

Applications -> Internet -> OpenVAS client

Connect (use the connect icon) -> enter user name and password

Start a scan

File -> scan assistant

[Back to top](http://ubuntuforums.org/showthread.php?t=1477662)

---

### Post by bodhi.zazen on 2010-05-09
[center][size=6]Alternates to OSSEC / OpenVAS[/size][/center]

OSSEC / Openvas not your cup of tea ? You could consider one of these alternates:

Bastille - [Ubuntu Wiki Bastille](https://help.ubuntu.com/community/BastilleLinux) . Take care, bastille can lock you out of your own system and can be difficult to reverse changes. In addition it is somewhat dated and needs to be customized for Ubuntu.

Nagios - [Nagios](https://help.ubuntu.com/community/Nagios3)

Nessus - [Nessus](http://www.nessus.org/nessus/)

Osiris - [Osiris](http://osiris.shmoo.com/) (last update 2007) .

Samhain - [Samhain](http://la-samhna.de/) (Beltane is the web interface). The samhain client is in the Ubuntu repositories (and works fine), but if you wish to use the server (yule) and Beltane you have some serious reading to do.

Zenoss - [Zenoss](http://www.zenoss.com/)

Install / Download / Run the vulnerability tools manually.

[Back to top](http://ubuntuforums.org/showthread.php?t=1477662)

---

### Post by bodhi.zazen on 2010-05-09
[center][size=6]Tiger[/size][/center]

Tiger is my next favorite HIDS tool as it performs a security audit as well as several security checks including john the ripper (checks for weak passwords), scanning your system for listening "back door" ports, and chkrootkit. Output can be formatted in a HTML document, which you may then open with any browser.

Features:

1. Runs chkrootkit.
2. Gives options for hardening your installation.
3. The built in help / information for tiger alerts (tigexp) is, IMO, superior to some of the other options.

Home page: [http://www.nongnu.org/tiger/](http://www.nongnu.org/tiger/)

Please READ the "README" files !!!!

[tiger README](http://cvs.savannah.gnu.org/viewvc/*checkout*/tiger/tiger/README?content-type=text%2Fplain&revision=HEAD)
[tiger USING file](http://cvs.savannah.gnu.org/viewvc/*checkout*/tiger/tiger/USING?content-type=text%2Fplain&revision=HEAD)
[tiger README.hids](http://cvs.savannah.gnu.org/viewvc/*checkout*/tiger/tiger/README.hostids?content-type=text%2Fplain&revision=HEAD)

[man tiger](http://manpages.ubuntu.com/manpages/lucid/en/man8/tiger.8.html)

[size=4]Install tiger[/size]
 
```
sudo apt-get install tiger
```

_**Note**_: This will install john and ckrootkit as well.
_**Note**_: John does not work with the default Ubuntu password hashes (sha-512).

[size=2]Run tiger[/size]

```
sudo tiger -H
```

tiger takes some time and appears to hang at the (output) line:

> Performing system specific checks ...

Let it run ...

Tiger will generate a long list of suggestions for your investigation. 

To view the output (it is a bit of an effort):

```
sudo bash -c "cp /var/log/tiger/security.report.* /home/bodhi
sudo chown bodhi.bodhi /home/bodhi/security.report.*
```

Change "bodhi" to your user name.

Then view with Firefox:

```
firefox security.report.<tab>
```

<tab> == Use the tab key for tab completion ^^

To see an explanation of a warning or alert, use tigexp. The syntax is tigexp alert_code

For example :

> bodhi@lucid:~$ tigexp pass014w

The listed login ID is disabled in some manner ('*' in passwd field, etc),
but the login shell for the login ID is a valid shell (from /etc/shells
or the system equivalent).  A valid shell can potentially enable the
login ID to continue to be used.  The login shell should be changed to
something that doesn't exist, or to something like /bin/false.


[color=navy]**Etiquette: If you are going to run these tools, please read the documentation  (FAQ / README ) and perform a google search on the results of alerts or warnings before posting on the forums.**[/color]

You may review the security audit and decide for yourself if you wish to implement any of the suggestions (knock yourself out ... ).

[Back to top](http://ubuntuforums.org/showthread.php?t=1477662)

---

### Post by bodhi.zazen on 2010-05-09
[center][size=6]Chkrootkit[/size][/center]

chkrootkit is a HIDS tool that scans your computer for possible root kits. It is one of the most popular rootkit scanners on these forums.

Home page: [http://www.chkrootkit.org/](http://www.chkrootkit.org/)

[chkrootkit FAQ](http://www.chkrootkit.org/faq/)

[man chkrootkit](http://manpages.ubuntu.com/manpages/lucid/en/man1/chkrootkit.1.html)

[size=4]Install chkrootkit[/size]

```
sudo apt-get install chkrootkit
```

[size=4]Run chkrootkit[/size]

```
sudo chkrootkit
```

The output should all read "not found" and / or "not infected"

As with all these tools false positives are common, use Google to search for suspicious results.

[color=navy]**Etiquette: If you are going to run these tools, please read the documentation  (FAQ / README ) and perform a google search on the results of alerts or warnings before posting on the forums.**[/color]

---

### Post by bodhi.zazen on 2010-05-09
[center][size=6]Rkhunter[/size][/center]

rkhunter is the next most common HIDS tool. This tool is command line only and the output is to the terminal and a log file.

Home page : [http://rkhunter.sourceforge.net/](http://rkhunter.sourceforge.net/)

[rkhunter FAQ](http://rkhunter.cvs.sourceforge.net/viewvc/*checkout*/rkhunter/rkhunter/files/FAQ)

[man rkhunter](http://manpages.ubuntu.com/manpages/lucid/en/man8/rkhunter.8.html)

[size=4]Run rkhunter[/size]

```
sudo rkhunter -c
```

[size=4]Interpreting the Output of rkhunter[/size]

You will see a number of tests, output of "[color=green][ OK ][/color] " is good.

Warnings are exactly that, warnings and not necessarily problems. You should not either panic or ignore them, you should investigate to see if they are "normal" for your system.

Results of the scan are in /var/log/rkhunter.log

```
gksu gedit /var/log/rkhunter.log
```

Google search any warnings or alerts.

[color=navy]**Etiquette: If you are going to run these tools, please read the documentation  (FAQ / README ) and perform a google search on the results of alerts or warnings before posting on the forums.**[/color]

[Back to top](http://ubuntuforums.org/showthread.php?t=1477662)

---

### Post by bodhi.zazen on 2010-05-09
[center][size=6]Clamav[/size][/center]

- A brief word about virus / spyware scanners -

In Linux there are no known active viruses and user cases for antivirus scanners include :

1. If you are running a file server (mail server, FTP, Samba, NFS, etc) and serve windows clients you might scan all uploaded files for viruses.

2. As a netizen you may wish to scan files you receive or give (mail, usb device, etc) windows users.

3. You wish to scan / clean a Windows partition of viruses.

[Overview of Antivirus software on Ubuntu](https://help.ubuntu.com/community/Antivirus) Keep in mind, IMO, the strongest proponents of many of these tools are either new to Linux or trying to sell you something.

**I have never seen spyware on Linux nor have I seen a Linux spyware scanner/removal tool.**

Clamav is one of the more popular and IMO easiest to use Linux virus scanner. In addition clamav has the ability to run in daemon mode. This is, IMO, particularly useful on servers. Clamav can also interface with dansguardian and scan web content for viruses.

While this last feature is beyond this long series of posts, see [Squid Proxy Server On Ubuntu 9.04 Server With DansGuardian, ClamAV, And WPAD (Proxy Auto-Detection)](http://www.howtoforge.com/squid-proxy-server-on-ubuntu-9.04-server-with-dansguardian-clamav-and-wpad-proxy-auto-detection)

[Clamav Home page](http://www.clamav.net/lang/en/)

[Clamav wiki](http://wiki.clamav.net/Main/WebHome)

[clamav FAQ](http://wiki.clamav.net/bin/view/Main/FAQ)

[Ubuntu wiki ClamAV](https://help.ubuntu.com/community/ClamAV)


[size=4]Install clamav[/size]

```
sudo apt-get install clamav
```

[size=4]Update virus definitions[/size]

```
sudo freshclam
```

[size=4]Scan with clamav[/size]

Syntax : sudo clamscan -r directory_to_scan

You do NOT need sudo if you own the files to be scanned.

[size=4]Scan home directories[/size]

```
sudo clamscan -r /home
```

[size=4]Scan flash drive (change "/media/disk" to the mount point of the usb device[/size]

```
sudo clamscan -r /media/disk
```

[size=4]Scan the entire system[/size]

```
sudo clamscan -r /
```

[size=4]Remove "infected files"[/size]

```
sudo clamscan -r /home --remove
```

**[color=darkred]_Note_: clamav deletes infected files IT DOES NOT REMOVE or CLEAN THE "virus" FROM THE FILE. Take care not to delete / remove files without researching if they are infected (same with any OS).**[/color]

[size=4]Running clamav as a daemon[/size]

clamav can be installed on mail / samba servers and run as a daemon.

Install clamav-daemon

```
sudo apt-get install clamav-daemon
```

Then run as a daemon

```
sudo clamav-daemon -r /home
```

You may also use the --remove option with clamav-daemon


[size=4]Graphical front ends[/size]

You may scan your user directory or removable devices as a regular user. To scan system files or update virus definitions you will need to run these tools as root.

klamav - klamav is a KDE application but runs on gnome and xfce.

Installation:

```
sudo apt-get install -y klamav
```

klamav is in your menu under Applications -> System tools

If you wish to scan system files you will need to run klaav as root.

```
gksu klamav
```

[[img]http://bodhizazen.net/img/clam/kav1_thumb.png[/img]](http://bodhizazen.net/img/clam/kav1.png)

[[img]http://bodhizazen.net/img/clam/kav2_thumb.png[/img]](http://bodhizazen.net/img/clam/kav2.png)

clamtk - a gtk application

Home page: [http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)

[http://downloads.sourceforge.net/project/clamtk/ClamTk/4.25/clamtk_4.25-1_all.deb?use_mirror=hivelocity](http://downloads.sourceforge.net/project/clamtk/ClamTk/4.25/clamtk_4.25-1_all.deb?use_mirror=hivelocity)

Check the home page for more recent versions.

Install

```
wget http://downloads.sourceforge.net/project/clamtk/ClamTk/4.25/clamtk_4.25-1_all.deb?use_mirror=hivelocity
sudo dpkg -i clamtk_4.25-1_all.deb
sudo apt-get install -f
```

clamtk is in the menu under 

Applications -Accessories -> Virus Scan

To run as root:

```
gksu clamtk
```

[[img]http://bodhizazen.net/img/clam/ctk1_thumb.png[/img]](http://bodhizazen.net/img/clam/ctk1.png)

[[img]http://bodhizazen.net/img/clam/ctk2_thumb.png[/img]](http://bodhizazen.net/img/clam/ctk2.png)

[size=4]Clamav Test Files[/size]

If you wish to test clamav, install the test files and re-scan.

```
sudo apt-get install -y clamav-testfiles
```

Then run clamscan, or one of the graphical tools, and scan /

_Note_: If you run from the command line you will see you have 4 infected files, but the listing of the files is lost in the output.

```
sudo bash -c "clamscan -r / 2>/dev/null | grep -v OK | grep -v Empty | grep -v Excluded
``` 

[size=4]Additional information[/size]

1. clamav is maintained in backports, so you may wish to enable the backports repository.

2. There is also a [ppa for clamav](https://launchpad.net/~ubuntu-clamav/+archive/ppa) . New versions of clamav are available in the ppa first -> then if stable backports. see [MOTU - clamav](https://wiki.ubuntu.com/MOTU/Clamav)

3. clamav has an apparmor profile. To enable it :

[Back to top](http://ubuntuforums.org/showthread.php?t=1477662)

---

