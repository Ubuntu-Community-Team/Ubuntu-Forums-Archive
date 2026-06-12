---
title: "Intrusion Detection"
date: 2008-09-14
forum: Security
---

### Post by bodhi.zazen on 2008-09-14
[CENTER][SIZE=6][COLOR=darkred]Ubuntu Intrusion Detection[/COLOR][/SIZE]

[IMG]http://www.idsia.ch/%7Ejuergen/galaxy180grey.jpg[/IMG][/CENTER]

**Quote :** 

*[SIZE=6][COLOR=darkred]“Paranoia will get you through times of no enemies better than enemies will get you through times of no paranoia”[/COLOR][/SIZE]*

~ Pete Granger

**[SIZE=4]Contents[/SIZE]**
[LIST=1]
[*]Introduction ~ post #1
[*]Install Snort ~ [post #2]("http://ubuntuforums.org/showpost.php?p=5786055&postcount=2")
[*]Configure snort ~ [post #3]("http://ubuntuforums.org/showpost.php?p=5786252&postcount=3")
[*]Install base ~ [post #4]("http://ubuntuforums.org/showpost.php?p=5786356&postcount=4")
[*]Using snort / base ~ [post #5]("http://ubuntuforums.org/showpost.php?p=5786477&postcount=5")
[*]Install ossec-hids ~ [post #6]("http://ubuntuforums.org/showpost.php?p=5786503&postcount=6")
[*]Install ossec-hids web interface ~ [post #7]("http://ubuntuforums.org/showpost.php?p=5786522&postcount=7")
[*]Using ossec-hids ~ [post #8]("http://ubuntuforums.org/showpost.php?p=5786575&postcount=8")
[/LIST]
**[SIZE=4]Introduction[/SIZE]** 

This how to was written as an extension to [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=510812") and is intended as an introduction to intrusion detection, Ubuntu Style.

This post is quite long, and for what I hope is greater readability, I have broken it into separate posts.

Here is a very nice link that reviews IDS :

[Security Focus ~ An Introduction to Intrusion Detection Systems]("http://www.securityfocus.com/infocus/1520")

And for the impatient, the readers digest version :

There are two "arms" of intrusion detection: HIDS and NIDS.

HIDS = Host-based Intrusion Detection System.
NIDS = Network-based Intrusion Detection System.

In a nut-shell, HIDS monitors you system files for unauthorized changes. Examples of this type of monitoring methodology might include techniques such as scanning for viruses, [tripwire]("http://sourceforge.net/projects/tripwire/"), [Tiger]("http://www.nongnu.org/tiger/"), [rkhunter]("http://rkhunter.sourceforge.net/"), and [chkrootkit]("http://www.chkrootkit.org/").

Similarly, NIDS monitors your network traffic for DOS attacks, port scans, or other suspicious network activity. Examples include watching your firewall in Windows for alerts, [snort]("http://www.snort.org/"), or [Wireshark]("http://www.wireshark.org/").

Although there are other options, both for applications and configuration, in this tutorial I will show you how to install ossec-hids and snort:

NIDS = [snort]("http://www.snort.org/")
HIDS = [ossec]("http://www.ossec.net/")

_**Snort**_ :

Snort will monitor your network traffic by checking packets against "rules". We will configure snort to log "alerts" to a mysql database. We will then use base to display this information in a web browser (Firefox). Although seemingly foreign at first, base is a very nice web based gui front end for snort. Base is basically point and click and contains numerous links to help interpret alerts.

> SNORT® is an open source network intrusion prevention and detection system utilizing a rule-driven language, which combines the benefits of signature, protocol and anomaly based inspection methods. With millions of downloads to date, Snort is the most widely deployed intrusion detection and prevention technology worldwide and has become the de facto standard for the industry.
[LIST]
[*]_Note_ : Snort will not work with wireless interfaces, you need to use [airsnort]("http://airsnort.shmoo.com/") instead.
[/LIST]

**_OSSEC-HIDS_** : 

OSSEC-HIDS will monitor your log files, monitor the integrity of system files, check for root kits, and perform active response. Active response means ossec will blacklist (block connections) from potential crackers "automagically".

> OSSEC is an Open Source Host-based Intrusion Detection System. It performs log analysis, integrity checking, Windows registry monitoring, rootkit detection, real-time alerting and active response.OSSEC will, amongst other things, monitor snort and blacklist offending ip addresses.

_**Note**_ : There are of course other options for HIDS, NIDS, as well as alternate configuration options for both snort and ossec.


You should be familiar with :

1. Installing from source (don't worry I will walk you through it).

2. Your ip address, both on your private LAN and public IP address.

3. Your [netmask]("http://www.unixwiz.net/techtips/netmask-ref.html")

[LIST]
[*]You can show your netmask with ```
sudo ifconfig | grep --color=always -e Mask -e 255
```
[/LIST]

4. If you wish to access base and the OSSEC web interface outside your LAN you will need to know how to configure your router (you do have a router don't you?). In addition be sure to understand the security implications of running LAMP. In addition you may wish to use [,htaccess]("http://www.javascriptkit.com/howto/htaccess.shtml") or [ssl]("http://www.tc.umn.edu/%7Ebrams006/selfsign_ubuntu.html").

Reference: [uhelp]community/ApacheMySQLPHP[/uhelp]

5. Installing and configuring snort will take some time, give yourself a few hours.

[COLOR=red][SIZE=4]**We will be running all commands in this tutorial as root**[/SIZE][/COLOR]

So either add "sudo" in front of these commands or open a terminal and obtain a root shell: ```
sudo -i
```

---

### Post by bodhi.zazen on 2008-09-14
[SIZE=4]**How to install snort + mysql + base**[/SIZE][INDENT][COLOR=green]As has been pointed out by[/COLOR] [Sarmacid]("http://ubuntuforums.org/member.php?u=597914")[COLOR=green] you can install snort from the Ubuntu repositories. In the repos snort is on version 2.7 where from source we are on snort 2.8. To use the repos use "sudo apt-get install snort-mysql".[/COLOR]

[LIST]
[*]See post 20 & 21 for (brief) discussion.
[/LIST]
[/INDENT]You will need to download a set of rules for snort. The downloads page is here :

[http://www.snort.org/pub-bin/downloads.cgi](http://www.snort.org/pub-bin/downloads.cgi)


1. prep ~ Install the various tools and dependencies for Snort and OSSEC.

You wee need the Universe repository enabled.

If you need assistance enabling your repositories, see : [uhelp]/community/Repositories/Ubuntu[/uhelp]

```
apt-get -y install build-essential libpcap0.8-dev libmysqlclient15-dev mysql-client-5.0 mysql-server-5.0 bison flex apache2 libapache2-mod-php5 php5-gd php5-mysql libphp-adodb php-pear libc6-dev g++ gcc pcregrep libpcre3-dev
```[COLOR=red]_Note_: This will install mysql and apache. Please be sure you understand the implications of this.[/COLOR]

For reference : [uhelp]/community/Repositories/ApacheMySQLPHP[/uhelp]

During the installation of these applications, make note of (write down) your mysql root password.

2. Obtain snort source code ~ [COLOR=blue]be sure to check the [/COLOR][snort home page]("http://www.snort.org/") [COLOR=blue]for updated versions of snort[/COLOR].

[COLOR=red]Although snort is in the repositories you will need to compile snort yourself. This is because the binary in Ubuntu does not have support for snort logging to a mysql database enabled.[/COLOR]

This procedure has been tested (and is working) on both 32 bit 64 bit arch.

```
cd /usr/src
wget http://www.snort.org/dl/current/snort-2.8.3.tar.gz
tar zxvf snort-2.8.3.tar.gz
```3. Obtain a set of rules. Snort uses rules to examine packets and report suspicious activity to your logs and mysql.

In order to get a set of rules you have a set of options listed on the [snort rules page]("http://www.snort.org/pub-bin/downloads.cgi")

The "Community Rules", at the bottom of the page, are available without any further registration. For a more "up to date" set of rules you must either register or subscribe.

(continuing in the /usr/src directory)

```
wget http://www.snort.org/the_rules_you_wish_to_use
cd snort-2.8.3
tar zxvf ../snortrules*
```In addition you may be interested in obtaining a copy of "bleeding" rules from here :
[Bleeding Edge Threats]("http://www.bleedingthreats.net/")

The snort rule sets are here : [http://doc.bleedingthreats.net/bin/view/Main/AllRulesets](http://doc.bleedingthreats.net/bin/view/Main/AllRulesets)

I downloaded the [bleeding-all.rules]("http://www.bleedingthreats.net/rules/bleeding-all.rules")

You may also be interested in : [http://www.emergingthreats.net](http://www.emergingthreats.net)

[COLOR=blue]You can keep your rules up to date with[/COLOR] [oinkmaster]("http://oinkmaster.sourceforge.net/features.shtml"). [COLOR=blue]Oinkmaster is in the reops[/COLOR].

[COLOR=red]If you use oinkmaster, be sure to READ THE DOCUMENTATION[/COLOR].

```
cd /usr/src/snort-2.8.3/rules
wget http://www.bleedingthreats.net/rules/bleeding-all.rules
```4. Compile snort :

```
cd /usr/src/snort-2.8.3
./configure -enable-dynamicplugin --with-mysql
make
make install
```Snort *should* compile and install without errors.

[color=darkred]**[size=4]If, however, you do get errors when compiling snort, see[/color] [This thread](http://ubuntuforums.org/showthread.php?t=1040886)**[/size]

5. You can remove snort with :
```
make uninstall
```[Back to top]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by bodhi.zazen on 2008-09-14
[SIZE=4]**Configure snort**[/SIZE]

[SIZE=2]**Configure mysql**[/SIZE]

Next we need to configure a mysql database for snort to use for alerts.

```
mysql -u root -p
```Enter your *mysql password for root* (you did write it down didn't you ?)

You will get a mysql prompt "mysql>". I will use this prompt to indicate commands entered in mysql (as opposed to the command line) *you do not need to enter the "mysql >"*.

>  mysql> create database snort;
mysql> grant all privileges on snort.* to 'snort'@'localhost' identified by 'snort_password';
mysql> exit
[LIST]
[*]Consider changing the name of the database to something other than "snort".
[*]Consider changing the name of mysql user to something other then "snort" (in 'snort'@'localhost').
[*]Change the password to something other then "snort_password".
[/LIST]

Now, back at the command line, import the snort database scheme

```
mysql -D snort -u snort -p < /usr/src/snort-2.8.3/schemas/create_mysql
```[SIZE=2]**Configure snort**[/SIZE]

We need to configure snort and write a start script, and add a cron job.

If things are too quiet, and snort goes a few hours without logging an alert to mysql, snort loses the connection with mysql. You then need to restart snort to re-establish a connection with the mysql database.

First lets create a user for snort. Again change the user name if you wish.

```
adduser snort
```Enter a password (it does not matter, we will be locking the account anyways)

```
chsh snort
```Enter a shell of "/bin/true" (without quotes).

Last, lock the account.

```
passwd snort -l
```Next configure snort :
```
cd /usr/src/snort-2.8.3
mkdir -p /etc/snort/rules /var/log/snort
chown -R root.snort /var/log/snort
chmod -R 770 /var/log/snort
cp etc/* /etc/snort/
cp rules/* /etc/snort/rules
```We next need to make a few edits to /etc/snort/snort.conf :

Using any editor, open /etc/snort/snort.conf and make the following changes :

[LIST]
[*]In nano you can search using ctrl-W
[*]In vim you can search using /
[*]Search for "HOME_NET" , "EXTERNAL_NET", then mysql (without quotes).
[/LIST]


[LIST=1]
[*]Change **"var HOME_NET any"** to **"var HOME_NET 192.168.0.0/16"** (use your netmask here).
[*]Change **"var EXTERNAL_NET any"** to **"var EXTERNAL_NET !$HOME_NET"**. This sets the external variable to everything other then your network.
[*]Change **"var RULE_PATH ../rules"** to **"var RULE_PATH /etc/snort/rules"**. This tells snort where to find the rule set.
[*]Search for "mysql" or scroll down the list to the section with **"# output database: log, mysql, user= ..."**, remove the "#" at the front of this line and change the syntax to : ```
**output database: log, mysql, user=snort password=snort_password dbname=snort host=localhost**
```
[/LIST]


[SIZE=2]**Write a script to start snort** :[/SIZE]

The only "problem" with installing snort from source is that we now need a script to start snort. The other issue is that if there are no alerts, snort will lose it's connection with the mysql database.

To solve this, I wrote a script to start / restart snort. 

**[COLOR=blue]The script is attached to this post and is called "ubuntu.snort.init.txt"[/COLOR]**

Copy this file to your computer and copy/move it to /etc/init.d/snort

Now lets look at the code. You need to look at two lines.

[LIST=1]
[*]The first is your interface. The default is eth0. If you wish to use snort on an alternate interface, such as eth1, you will need to edit the line **IFACE="eth0"** and change "eth0" to "eth1"
[LIST]
[*]_Note_ : Snort will not work with wireless interfaces, you need to use [airsnort]("http://airsnort.shmoo.com/") instead.
[/LIST]
 
[*]The second option is to whitelist ip addresses. I advise you do this with caution, but you *may* wish to white IP addresses such as your router and your public ip address.

To white list an IP , add it to the line **WHITELIST=''**  (note that is two single quotes, ' ' and not a double quote " ) , one ip at a time, separated by a space, like this :

```
WHITELIST='127.0.0.1 192.168.1.1'
```
[/LIST]

Now that you are done editing the file, set ownership and permissions :

```
chown root.root /etc/init.d/snort
chmod 500 /etc/init.d/snort
```[SIZE=2]**Starting snort on boot**[/SIZE]

My script has a 20 second sleep built in (sometimes when you start snort it will fail after a 10-15 second delay). To avoid adding a 20 second longer boot time, use the "boot" option.

With this factoid in mind, edit /etc/rc.local and add :

```
exec /etc/init.d/snort boot
```Add this single line above "exit 0" *if your have an exit 0 in the file*


[SIZE=2]**Restarting snort with a cron job**[/SIZE]

Did I mention, Snort may lose the connection to the mysql data base if no alerts are received for several hours (which can happen once we eliminate false positives and install OSSEC-HIDS)? In addition if you clear your data in base you may need to re-start snort.

To restart snort with my script :

```
/etc/init.d/snort restart
```The script will use zenity (a gui interface) if you have it installed (zenity is included in a default Ubuntu or Xubuntu desktop installation, but you will need to add it if you are running Kubuntu). On servers, without X, the script will run without zenity (the script runs either with or without X). In addition, if you run the script as a user you will need to be in the admin group and will be prompted for your password (unless you are in the 15 minute grace period for sudo/gksu).

To restart snort every 6 hours, use [crontab]("http://www.adminschoice.com/docs/crontab.htm") (as root)

```
crontab -e
```Add a line for snort :

```
0 0,6,12,18 * * * /etc/init.d/snort restart >/dev/null 2>&1
```Congratulations !! Snort is now configured.


[Back to top]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by bodhi.zazen on 2008-09-14
[SIZE=4]** Install base**[/SIZE]

Base is a web interface for snort and the snort alerts. See the "using base" section for a brief introduction.

```
cd
wget http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz
```**[COLOR=red]Note : Later versions of base do not work (with Ubuntu at least).[/COLOR]**

```
cd /var/www
tar zvxf ~/base-1.3.9.tar.gz
mv base-1.3.9 base
cd base
cp -R /usr/src/snort-2.8.3/doc/signatures .
cd ..
chown -R www-data.www-data base
```Install a few Pear modules:

```
pear install Image_Color Image_Canvas-alpha Image_Graph-alpha
```Configure apache to use php5, use any editor (nano)

```
nano /etc/apache2/apache2.conf
```At the very bottom of the file add :

```
DirectoryIndex index.html index.cgi index.pl index.php index.xhtml
```Save your changes and re-start apache:

```
/etc/init.d/apache2 restart
```Open a web browser and navigate to [http://your_ip_address/base](http://your_ip_address/base)

**You must accept cookies from base**

Click continue on the first page.

Step 1 of 5: Enter the path to ADODB.
      This is /usr/share/php/adodb.

[LIST]
[*]Sometimes when setting up base , after this first step I get a white page, just repeat step 1
[/LIST]

Step 2 of 5:
      Database type = MySQL, Database name = snort, Database Host = localhost, Database username = snort, Database Password = snort_password

[LIST]
[*]leave default port blank.
[/LIST]

Step 3 of 5: If you want to use authentication (used to log into the web interface) enter a username and password here and check the box.

Step 4 of 5: Click on Create BASE AG.

Step 5 of 5: once step 4 is done at the bottom click on Now continue to step 5 and log in.

Congratulations ! You should now see something that looks like this :

[[IMG]http://bodhizazen.net/img/IDS/base_1_sm.JPG[/IMG]]("http://bodhizazen.net/img/IDS/base_1.JPG")
[INDENT]Click to enlarge picture[/INDENT]You can password protect the base directory with [.htaccess]("http://www.javascriptkit.com/howto/htaccess.shtml") and/or use [ssl]("http://blog.offbytwo.com/2008/01/22/apache2-ssl-in-ubuntu-710-gutsy/").

[Back to top]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by bodhi.zazen on 2008-09-14
[SIZE=4]**Using snort / base**[/SIZE]

Although seemingly foreign, everything in base is point and click. Click on your alerts for example and they will be listed. Click on various links and you will be brought to web pages(s) where the alert is explained in more detail.

For example, here is a screen shot showing us some alerts.

[[IMG]http://bodhizazen.net/img/IDS/base_1_sm.JPG[/IMG]]("http://bodhizazen.net/img/IDS/base_1.JPG")[INDENT]Click to enlarge picture[/INDENT]Clilck on the blue "19" by "Total Number of Alerts" and base will show you ...

[[IMG]http://bodhizazen.net/img/IDS/base_2_sm.JPG[/IMG]]("http://bodhizazen.net/img/IDS/base_2.JPG")[INDENT]Click to enlarge picture[/INDENT]Alerts :

> #0-(72-1)      [nessus] [local] [snort] WEB-MISC robots.txt access      2008-09-07 08:38:48      74.6.17.188:34357      [noparse]192.168.1.3:80[/noparse]      TCPclick on the [[nessus]]("http://www.nessus.org/plugins/index.php?view=single&id=10302"), [local], or [[snort]]("http://www.snort.org/pub-bin/sigs.cgi?sid=1:1852") takes you to a  web page explaining the alert.

click on the ip address ([noparse]74.6.17.188[/noparse]) to take you to a page where you can select a link to look up the offending ip.

[[IMG]http://bodhizazen.net/img/IDS/base_3_sm.JPG[/IMG]]("http://bodhizazen.net/img/IDS/base_3.JPG")

On this second page, click on [ARIN]("http://ws.arin.net/whois/?queryinput=74.6.17.188") (or any other) which will take us to a page where we can see this ip address belongs to Yahoo.com

===============

Another example, from a local port scan :

> #18-(72-19)      [snort] (http_inspect) NON-RFC DEFINED CHAR      2008-09-11 16:49:57      192.168.1.5:52093      [noparse]192.168.1.3:80[/noparse]      TCPHere we only have the option [snort] which takes us to :

[http://www.snort.org/pub-bin/sigs.cgi?sid=119:14](http://www.snort.org/pub-bin/sigs.cgi?sid=119:14)

This alert was generated by my portscan to show the active response of ossec (see below).


[SIZE=2]**Basic alert management**[/SIZE]


First, when you first install snort, you will likely get a large number of alerts. Most of these are legitimate traffic (false positives).

YOU WILL NEED TO RESEARCH EACH ALERT AND DETERMINE IF YOU ARE VULNERABLE. IF SO, FIX YOUR VULNERABILITY.

For "false positives, once you have confirmed an alert is indeed either a false positive or legitimate traffic, either modify or comment out the rule (writing snort rules is beyond this tutorial, see [How to snort rules]("http://www.snort.org/docs/snort_htmanuals/htmanual_2.4/node14.html")).

For the example here, robots.txt :

_Note_: There are better ways of managing robots.txt, see the snort links and apache documentation, I am using this only as an example of editing snort rules.

grep is our friend here, so find the alert with :

```
grep robots.txt /etc/snort/rules/*
```returns :

> /etc/snort/rules/web-misc.rules:# NOTES: this signature looks for someone accessing the file "robots.txt" via
/etc/snort/rules/web-misc.rules:# engines) more efficient.  robots.txt is often used to inform a web spider
/etc/snort/rules/web-misc.rules:# Verify that the robots.txt does not include any sensitive information.
[COLOR=green]/etc/snort/rules/web-misc.rules:alert tcp $EXTERNAL_NET any -> $HTTP_SERVERS $HTTP_PORTS (msg:"WEB-MISC robots.txt access"; flow:to_server,established; uricontent:"/robots.txt"; nocase; metadata:service http; reference:nessus,10302; classtype:web-application-activity; sid:1852; [noparse]rev:4;)[/noparse][/COLOR]so now open /etc/snort/rules/web-misc and comment out the line:

```
sudo nano -w /etc/snort/rules/web-misc.rules
```Hit Ctrl-W to search, search for "robots.txt" (without quotes). Keep hitting Crtl-W to go to the next robots.txt.

When you find the appropriate line (the one that starts with a "alert"), add a # to the front of the line.

Re-start snort.

Once you have managed the false positives, watch for repeat offenders. If I see an IP address persistently triggering snort, I black list it in iptables.

If you do not know how to do this, see here : [uhelp]Uncomplicated_Firewall_ufw[/uhelp]

Specifically : [https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Advanced%20Blocking%20Rules]("https://help.ubuntu.com/community/Uncomplicated_Firewall_ufw#Advanced%20Blocking%20Rules")

Hint: EDIT /etc/ufw/before.rules


[Back to top]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by bodhi.zazen on 2008-09-14
[SIZE=4]**OSSEC-HIDS**[/SIZE]

OSSEC-HIDS is much easier to install. Basically it is downloading and then running a script.

Go to the ossec download page and download the most recent version :

[http://www.ossec.net/main/downloads/](http://www.ossec.net/main/downloads/)

```
wget http://www.ossec.net/files/ossec-hids-1.6.tar.gz
tar xzvf ossec-hids-1.6.tar.gz
```Now run the installation script :

```
cd ossec-hids-1.6
./install.sh
```You will be asked a series of questions. Basically select your language, use a "local" installation, and enter an e-mail address. Otherwise go with the defaults.

When you get to the question :

>  - Do you want to add more IPs to the white list? (y/n)? [n]: *Answer y and add additional IP if you wish to white list them.*

There is a very nice post on the Ubuntu forums here :

[Howto setup OSSEC-HIDS on your ubuntu box]("http://ubuntuforums.org/showthread.php?t=213445")

[COLOR=blue]~ Thanks[/COLOR] [RShadow]("http://ubuntuforums.org/member.php?u=130519")

[COLOR=red]The only "problem" is that the post is a little outdated. The information about running the install script is accurate, but you DO NOT need to write an init script. ossec 1.6 will install a script for you into /etc/init.d/ossec[/COLOR]

Start / Stop OSSEC with :

```
sudo /etc/init.d/ossec start|stop
```
[SIZE=2]**Configure OSSEC**[/SIZE]

Not much needs to be done. HOWEVER I would caution you that OSSEC has an active response to threats. If OSSEC detects a bad ip address, it will block that ip address using iptables. This means that if your snort rules are giving you false alerts legitimate traffic to your server will be blocked.

***This also means you can lose access to your server as well.***

Fortunately this is a temporary ban. It is more than sufficient to deter the script kiddies and if your access is blocked, access is restored in a few minutes.

This means , however, you need to monitor snort (base) and fine tune your rules so you are not blocking legitimate traffic.

Again, if there are repeat offending IP addresses, black list them in iptables (See the using snort/base post for how to do this).

Additional configuration of OSSEC is is done by editing /var/ossec/etc/ossec.conf

This configuration file is well commented and you will see a white list section where you may white list additional ip addresses if needed.


[Back to top]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by bodhi.zazen on 2008-09-14
**[SIZE=4]Web access to ossec[/SIZE]**

Download the web interface from [http://www.ossec.net/main/downloads/](http://www.ossec.net/main/downloads/)

```
cd
wget http://www.ossec.net/files/ui/ossec-wui-0.3.tar.gz
cd /var/www
tar xzvf ~/ossec-wui-0.3.tar.gz
mv ossec-wui* ossec

cd ossec
./setup.sh
```During the setup you will be asked for a user name and password. You will use this user name and password to access the web interface.

When the script is finished running, change ownership of the directory and add www-data to the ossec group 

```
cd /var/www
chown -R www-data.www-data ossec
usermod -G ossec -a www-data
```Restart apache

```
/etc/init.d/apache2 restart
```Log in at [http://your_ip_address/ossec](http://your_ip_address/ossec)

From the web interface you can see any changes to system files and alerts.


[Back to top]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by bodhi.zazen on 2008-09-14
[SIZE=4]**Using ossec**[/SIZE] :

Once you log into the web interface you will have a number of tabs. 

_Main_ ~ This is where you will see alerts.

_Integrity checking_ ~ Will show you recent changes to system files.

[[IMG]http://bodhizazen.net/img/IDS/OSSEC_1_sm.JPG[/IMG]]("http://bodhizazen.net/img/IDS/OSSEC_1.JPG")


[size=2]**Understanding and modifying rules[/size]**

_Listing of rules_ (it is incomplete): [http://www.ossec.net/wiki/index.php/Rule](http://www.ossec.net/wiki/index.php/Rule)

_Modifying rules_ : [http://www.ossec.net/wiki/index.php/Know_How:Ignore_Rules](http://www.ossec.net/wiki/index.php/Know_How:Ignore_Rules) 

I did find this wiki page on integrating base + ossec, but I have not tried it.

ossec + base : [http://www.ossec.net/wiki/index.php/OSSEC_&_BASE](http://www.ossec.net/wiki/index.php/OSSEC_&_BASE)


[SIZE=2]**Example of ossec active response**[/SIZE] :

> 
[COLOR=green]# Start by pinging the server:[/COLOR]

root@hardy:~#ping 192.168.0.3
PING 192.168.1.3 (192.168.0.3) 56(84) bytes of data.
64 bytes from 192.168.0.3: icmp_seq=1 ttl=64 time=0.378 ms
64 bytes from 192.168.0.3: icmp_seq=2 ttl=64 time=0.377 ms
64 bytes from 192.168.0.3: icmp_seq=3 ttl=64 time=0.359 ms

--- 192.168.0.3 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 0.359/0.371/0.378/0.018 ms

Portscan the server :
[COLOR=red]root@hardy:~#nmap -sS -sV -O -PI -PT 192.168.0.3[/COLOR]

[COLOR=red]Starting Nmap 4.53 ( [http://insecure.org](http://insecure.org) ) at 2008-09-11 17:27 MDT[/COLOR]

[COLOR=red]<-- Notice how Nmap hangs ? -->[/COLOR]

[COLOR=blue]# Now ping the server again[/COLOR]:

root@hardy:~#ping 192.168.0.3
PING 192.168.0.3 (192.168.0.3) 56(84) bytes of data.

**[SIZE=2][COLOR=blue]<-- Notice how your pings are blocked ? -->[/COLOR][/SIZE]**

--- 192.168.0.3 ping statistics ---
[COLOR=blue]4 packets transmitted, 0 received, 100% packet loss, time 2999ms[/COLOR][Back to top]("http://ubuntuforums.org/showthread.php?t=919472")

---

### Post by Rocket2DMn on 2008-09-14
The Ubuntu Guru strikes again!  Thanks bodhi, this thread is great, I think it's your best so far.

Now for a short little addendum to the main guide, for those interested in low system impact.

**_[SIZE="3"]Intrusion Detection using a Virtual Machine[/SIZE]_**

If you would like to take this guide for a run without heavily messing with their current system configuration, you can still get the full effect by setting up Ubuntu in a Virtual Machine (VM) and following the guide from there.  The concepts here apply to whatever virtualization software you prefer, I just use vbox as an example since that is what I used.

The only work that needs to be done on your host machine (not the VM) is to setup a network bridge so that your VM will have an IP assigned by your network's DHCP server (in a home network, this is usually the central router). You can also opt set a static IP that is recognized by the rest of the network.  With this network IP, you can then actually see what is happening on the network, unlike with the default private IP that VMs normally get assigned.
Example:
[INDENT]Normal Private IP: 10.0.2.15
Network IP: 192.168.1.101[/INDENT]
(Note: Yes, yes, 192.168.xxx.yyy is also in the private IP range, but this is what is generally seen on a home network, and I therefore refer to as the network IP.)

**_General Directions for using VirtualBox:_**

Setup your virtual machine with an Ubuntu installation - there are many guides out there on how to do this (ex: [uhelp]community/VirtualBox[/uhelp]).  Don't forget to install [LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP") and the *build-essential* metapackage which are needed for the above tutorial.

Now create a network bridge on your host machine by following the directions at [uhelp]community/VirtualBox#Networking[/uhelp].  Our guru, bodhi.zazen, also suggested the following link which will also work for vbox - [uhelp]community/KVM#Creating a network bridge on the host[/uhelp].  I found it helps to first set your host to DHCP temporarily if you are using a static IP so that you can easily configure the bridge.  Then you can setup your static IP after your bridge is successfully created and tested.  The VM won't know the difference, other than it will get an IP immediately compatible with your network.  Also, don't forget to create the scripts to bring the bridge up and down as described in the VirtualBox wiki link.
Here is my /etc/network/interfaces file, with static IP on the host, for your reference (yours will vary).  I have edited out my username, and I am using a Linksys WRT54G router:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

auto eth0
iface eth0 inet manual
address 0.0.0.0

auto br0
iface br0 inet static
   bridge_ports eth0
address 192.168.1.201
netmask 255.255.255.0
gateway 192.168.1.1

auto lo
iface lo inet loopback

auto tap1
iface tap1 inet manual
up ifconfig $iface 0.0.0.0 up
down ifconfig $iface down
tunctl_user *username*

```
where *username* is your username which is used in /etc/vbox/interfaces (see the Network portion of vbox guide linked above).

If you're in to using static IPs, you can now set a static IP on your VM as well.  This makes it convenient to access the web service interfaces for BASE and OSSEC from another system (like the host).

Enjoy!

---

### Post by Vivaldi Gloria on 2008-09-14
Thanks mate. This thread is indeed great.

---

### Post by Oldsoldier2003 on 2008-09-14
> **Rocket2DMn said:**
> The Ubuntu Guru strikes again!

Thanks bodhi, this thread is great, I think it's your best so far.  I look forward to putting it to good use very soon.

+1 You've outdone yourself this time:)

---

### Post by The Tronyx on 2008-09-15
I endorse this thread.

---

### Post by Uchiha_madara on 2008-09-15
thanks a lot man

you have done a huge effort you are very nice ,,,,,,

---

### Post by Drezard on 2008-09-18
You are an absolute genious of security.

Thanks so much. 

Daniel

---

### Post by etusha on 2008-09-21
can i install both 
without create any conflict ?

if install both do they need a lot off CPU recourse ?

---

### Post by bodhi.zazen on 2008-09-21
> **etusha said:**
> can i install both 
without create any conflict ?

if install both do they need a lot off CPU recourse ?

snort and ossec perform different tasks and are complementary. See :

[Security Focus ~ An Introduction to Intrusion Detection Systems]("http://www.securityfocus.com/infocus/1520")

Yes you can run them together. "lot of CPU" is subjective and means different things to different people. In general snort and ossec do not slow down your web server and if they do, IMO, your server is probably underpowered.

---

### Post by henke54 on 2008-10-01
Code-based Intrusion Detection for Linux by Ohad Ben-Cohen and Avishai Wool :
[http://www.korset.org/?page_id=2](http://www.korset.org/?page_id=2)

---

### Post by RRFarFar on 2008-10-02
Just a newbie question:
Does that info have any use for desktop version of Ubuntu? 
I do have ufw enabled and ports closed, but I want to monitor internet connections and other things. Can I use snort and the other thing for that??? 
Sorry, I know I do look like an incompetent person now, but... I really am)))
Thanks very much for this post

---

### Post by bodhi.zazen on 2008-10-02
> **RRFarFar said:**
> Just a newbie question:
Does that info have any use for desktop version of Ubuntu? 
I do have ufw enabled and ports closed, but I want to monitor internet connections and other things. Can I use snort and the other thing for that??? 
Sorry, I know I do look like an incompetent person now, but... I really am)))
Thanks very much for this post

No problem, ask away.

You are asking the right questions, but you will get a range of answers depending on who you ask.

Rather then turn this thread into a meandering debate re: firewalls and security I would prefer to keep it on topic, ie intrusion detection.

My best advice is that you start by asking yourself what it is you are trying to accomplish and determine your own level of "paranoia". Next read through some of the links I provided and determine the right tool for the job.

ossec == HIDS
snort  == NIDS

As most people come from a Windows background, the HIDS systems are most familiar. These are tools to monitor your host (desktop) for changes in system files. For example on Windows one scans for viruses or other malware (adblock software is often HIDS).

You are asking about NIDS, ie monitoring network traffic. Snort captures or monitors all network activity (packets) going to and coming from your Desktop (or server). You will likely recieve several thousand packets in short order, Snort filters through these thousands of packets by checking each packet against a set of "rules" and logs sustpcious activity to a database (mysql). You then use Base to generate a "report" you can view on any web browser. From there you will need to research any "alerts". How you manage alterts then is also a matter of style.

There are other tools for each of these tasks including wireshark (which will keep the contents of all packets, not just alerts) , barnyard (as an alternate to mysql) etc.

---

### Post by Sarmacid on 2008-10-23
> **bodhi.zazen said:**
> [COLOR=red]Although snort is in the repositories you will need to compile snort yourself. This is because the binary in Ubuntu does not have support for snort logging to a mysql database enabled.[/COLOR]
Just wanted to point out that there is a package with mysql logging support, I did it as indicated in the [[COLOR="gray"]guide by djhedges[/COLOR]]("http://ubuntuforums.org/showthread.php?t=483488&highlight=oinkmaster") and works great.

> apt-get install snort-mysql

---

### Post by bodhi.zazen on 2008-10-23
> **Sarmacid said:**
> Just wanted to point out that there is a package with mysql logging support, I did it as indicated in the [[COLOR=gray]guide by djhedges[/COLOR]]("http://ubuntuforums.org/showthread.php?t=483488&highlight=oinkmaster") and works great.


OK, I will add that information in to the original post.

The version in the repos is 2.7, and snort is on 2.8.3.

IMO, as we are talking about security, in this case it is better to compile form source (and compiling snort is quite easy (as well as downloading a  more up-to-date rule set).

One advantage of installing from the repos, it will include an init script for snort.

---

### Post by Sarmacid on 2008-10-24
I agree that in security you should be the most up to date you can be, however, getting snort through synaptic has its advantages. It's easier and it gets updated, and really, the most important thing to keep up to date are the rules themselves, and that, as you mention in the guide is done with oinkmaster. Don't wanna start up a discussion, but I think for the users that use snort at home getting it from the repos should be enough.

---

### Post by Girya on 2008-11-02
Thanks for the tutorial. I've wanted to install snort and now this tutorial will get me there.

One thing might need to be updated, when I pasted the download for snort I found the address didn't work on my computer. So I went over to snort's website and copied the link and pasted that onto my command line. 

The command that worked for me is: 

> wget http://www.snort.org/dl/snort-2.8.3.1.tar.gz && tar -zxvf snort-2.8.3.1.tar.gz

---

### Post by qrst472 on 2008-11-03
The real evils, indeed, of [wow gold](http://www.wowpowerleveling-wow.com/) Emma's situation were the power of having rather too much her own way, and a disposition to think a little [wow gold](http://www.wow-wowpowerleveling.com/) too well of herself; these were the disadvantages which threatened alloy to her many enjoyments. The danger, however, was at [wow power leveling](http://www.powerleveling-wowgold.com/wow-power-leveling.html) present so unperceived, that they did not by any means rank as misfortunes with her. Sorrow came--a gentle sorrow--but not at all in the shape of any disagreeable consciousness.--Miss Taylor married. It was Miss Taylor's loss which first brought grief. It was on the [wow powerleveling](http://www.wow-wowpowerleveling.com/) wedding-day of this beloved friend that Emma first sat in mournful thought of any continuance. The wedding over, and the bride-people gone, her father and herself were left to dine together, with no prospect of a third to cheer a long evening. Her father composed himself to sleep after dinner, as usual, and she had then only to sit and think of what she had lost.weiwei1978123

---

### Post by devoda on 2008-11-05
Thank you bodhi.zazen. I am a 4th year student for a information security systems and computer science degree and found your post informative and interesting. The majority of classes that deal with intrusion detection, network fortification, and common security practices apply the aforementioned concepts to Windows Server. This of course is useful for someone looking for a job because there are a fair amount of Windows Servers. But for the rest of us who would like to secure a Linux server and get paid to do so, they do not inform quite as well. Thank you for this post. The use of NIDS is much more interesting on an open system.

---

### Post by Etlaesium on 2008-11-14
I had run into a problem which resulted in the following error on "make":
```
attribute error: open with O_CREAT in second argument needs 3 arguments
```

This seems to be a programmatic error.  I fixed this by doing the following.

You must be root to perform the following procedure. You may also open the file below and save it in your home folder, then copy it (as root) to its original directory (../snort2.8.*/src/preprocessors/flow/portscan/).

After "./configure --with-mysql --enable-dynamicplugin", locate the file "server_stats.c" in "../snort-2.8.*/src/preprocessors/flow/portscan/" and open it in a text editor or IDE. Identify the following section:
```
int server_stats_save(SERVER_STATS *ssp, char *filename)
```

In this section, identify the line:
```
fd = open(filename, O_CREAT|O_TRUNC|O_SYNC|O_WRONLY);
```

and change it to:
```
fd = open(filename, O_CREAT|O_TRUNC|O_SYNC|O_WRONLY, 0600);
```

Then you may run "make && make install".

This resulted in other problems related to MySQL using Snort-2.8.3.  I then attempted to use the current Snort-2.8.3.1 and it compiled and installed beautifully on my Intrepid server.

---

### Post by aquadawg on 2008-11-15
I'm having a problem downloading the init script via wget command line on my server installation. Can someone please detail instructions on the procedure to get the file via CLI?

thanks


[I][B]
Write a script to start snort :

The only "problem" with installing snort from source is that we now need a script to start snort. The other issue is that if there are no alerts, snort will lose it's connection with the mysql database.

To solve this, I wrote a script to start / restart snort.

The script is attached to this post and is called "ubuntu.snort.init.txt"

Copy this file to your computer and copy/move it to /etc/init.d/snort

Now lets look at the code. You need to look at two lines.

   1. The first is your interface. The default is eth0. If you wish to use snort on an alternate interface, such as eth1, you will need to edit the line IFACE="eth0" and change "eth0" to "eth1"
          * Note : Snort will not work with wireless interfaces, you need to use airsnort instead.
   2. The second option is to whitelist ip addresses. I advise you do this with caution, but you *may* wish to white IP addresses such as your router and your public ip address.

      To white list an IP , add it to the line WHITELIST='' (note that is two single quotes, ' ' and not a double quote " ) , one ip at a time, separated by a space, like this :

      Code:

      WHITELIST='127.0.0.1 192.168.1.1'


Now that you are done editing the file, set ownership and permissions :

Code:

chown root.root /etc/init.d/snort
chmod 500 /etc/init.d/snort

Starting snort on boot

My script has a 20 second sleep built in (sometimes when you start snort it will fail after a 10-15 second delay). To avoid adding a 20 second longer boot time, use the "boot" option.

With this factoid in mind, edit /etc/rc.local and add :

Code:

exec /etc/init.d/snort boot

Add this single line above "exit 0" if your have an exit 0 in the file[/I][/B]

---

### Post by bodhi.zazen on 2008-11-16
yes, you can not wget directly from the forums.

Try this :

```
wget http://bodhizazen.net/ubuntu.snort.init.txt
```

---

### Post by MaindotC on 2008-11-16
> **Etlaesium said:**
> I had run into a problem which resulted in the following error on "make":
```
attribute error: open with O_CREAT in second argument needs 3 arguments
```


I ran into the same issue.  I didn't have any problems following the [Howto Forge](http://www.howtoforge.com/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated) for 7.10 on an 8.04 machine. I thought maybe some of the packages in the Howto Forge tutorial may been outdated or whatever and I wanted to try an 8.10 tutorial.  I'm not a developer - I'm a user - so I don't know the affect of what appears to be adding one more argument of value 0600 to the fd function, which I believe is a kernel function, has to do with this but I guess that type of uncertainty is one of the downfalls of not learning and understanding the operating system and how it is created.

In any event, I did this and followed the rest of the tutorial without any problems.  OP, you may want to change this line:
```

tar zxvf ../snrotrules*
[code]
to
[code]
tar zxvf ./snortrules*

```

---

### Post by bodhi.zazen on 2008-11-16
Thanks, fixed the typo. using .. vs . depends on what directory you are in and where you saved the archive. I *think* if you are following my directions steep-by-step it is indeed a double dot (..)

---

### Post by MaindotC on 2008-11-17
I'm sorry - I wasn't really pinpointing the use of the dot versus double dot and I didn't even notice that I used a single instead of a double.  I meant to point out the misspelling of snortrules which I see you corrected :)  Thanks again for the tutorial.

---

### Post by ray33 on 2008-11-20
Thank you for this information. Being a novice, it all sounds a bit complicated, but at least I now have the guide to follow when my particular paranoia peaks.

---

### Post by scribbles on 2008-11-24
```
cp -R /usr/src/snort-2.8.3/doc/signatures .
``` Using snort-2.8.3.1 there is not a /signatures and am not sure where to point it. I have browsed the dirs and do not see anything relative...

---

### Post by lapio on 2008-11-25
> **scribbles said:**
> ```
cp -R /usr/src/snort-2.8.3/doc/signatures .
``` Using snort-2.8.3.1 there is not a /signatures and am not sure where to point it. I have browsed the dirs and do not see anything relative...


```
cp -R /usr/src/snort-2.8.3.1/doc/signatures .
```

---

### Post by lapio on 2008-11-25
thank you very much for this great article.

i have a question though. i did the nmap portscan (from 192.168.0.100 to 192.168.0.100) and snort blocked my further pings as expected. however, i then wasn't able to refresh the base and ossec web interfaces for a small period - even though i have 192.168.0.100 whitelisted in /etc/init.d/snort. base web interface doesn't show any info on this, have i misinterpreted the guide at some point?


thank you

---

### Post by bodhi.zazen on 2008-11-25
> **lapio said:**
> thank you very much for this great article.

i have a question though. i did the nmap portscan (from 192.168.0.100 to 192.168.0.100) and snort blocked my further pings as expected. however, i then wasn't able to refresh the base and ossec web interfaces for a small period - even though i have 192.168.0.100 whitelisted in /etc/init.d/snort. base web interface doesn't show any info on this, have i misinterpreted the guide at some point?


thank you

Snort does not block access, OSSEC does.

So you would need to whitelist your IP address in OSSEC (it is in the config file).

Try this: Disable (stop) ossec and re-scan. You *should* also see more alerts in snort.

```
sudo /etc/init.d/ossec stop
```

scan ...

Notice your IP is not blocked

restart ossec

```
sudo /etc/init.d/ossec start
```

scan again

Your IP is now blocked, and you may not see as many alerts in snort :twisted:

---

### Post by Sarmacid on 2008-12-03
I have a script for updating the rules automatically with oinkmaster running on cron. ¿Do I have to restart snort every time it gets updated for the new rules to work or can I just leave it running?

---

### Post by bodhi.zazen on 2008-12-03
> **Sarmacid said:**
> I have a script for updating the rules automatically with oinkmaster running on cron. ¿Do I have to restart snort every time it gets updated for the new rules to work or can I just leave it running?

I am not sure, but I would restart snort.

---

### Post by Orange Luna on 2008-12-04
bodhi, just a quick bit on rules.

Rules can be commented out though there is a better way to do this.  Commentating rules is problematic because rules by an admin get updated periodically (hopefully everyone is using oinkmaster).  When these new rules are put into [FONT="Courier New"]/etc/snort/rules[/FONT] they erase the previous commented out versions.  

If people are using oinkmaster this can be done very easily.  In [FONT="Courier New"]/etc/oinkmaster.conf[/FONT] look at the section for SIDs down toward the bottom.  Each rule has a unique SID (Snort ID) enter in the SID's:

```
disablesid 8427,8428,8426   # cipher overflow for older openssl
```

and oinkmaster will comment the section on update.

more can be read [here]("http://oinkmaster.sourceforge.net/avoiding_snort_alerts.txt")

Nice guide bodhi, thank you.

---

### Post by bodhi.zazen on 2008-12-04
Thank you for the information Orange Luna

I was going to make a post on oinkmaster, but this was already too long.

And you did a better, much more succinct tutorial then I would have written :twisted:

---

### Post by peterhof on 2008-12-05
First of all thank you very much for this great post,after spending two weeks trying to install snort finally got it done with this post.

Now for the question, when I fire up BASE I see no activity whatsoever, yet I know there are things happening because if I type snort -v I get screenfulls of activity.

If anyone has any ideas that would be great.

Last but not least first time in Ubuntu and revisiting *nix after 10 years of not having used it.

---

### Post by bodhi.zazen on 2008-12-05
Snort is a packet sniffer, so each packet you receive will be analyzed or tested against the snort rules. If a packet triggers a rule you will have an alert on BASE.

So when you start BASE, do you see your senor ?

The other problem I have seen is that if there is no activity they mysql database loses it's connection. In that case you need to restart snort.

Try performing a port scan (or similar) from a remote box.

---

### Post by peterhof on 2008-12-05
Yes I do see my sensor. Now to go and find a port scanning tool.
Thanks!

---

### Post by Kinstonian on 2008-12-05
Sometimes a port scan won't fire an alert when I'm testing Snort for some reason so I add a rule to local.rules similar to this:

alert icmp any any -> any any (msg: "ICMP Test Rule";sid: 1000005;)

Then stop and restart snort, and start pinging a computer.  If you want to get even simpler, just go to:
[http://www.testmyids.com](http://www.testmyids.com)

---

### Post by peterhof on 2008-12-05
Ok, found a portscan tool and yes!!! I now get something displaying in BASE.

Thanks for the rule tip, will have to investigate some more on the rules section as there is more work to be done there, in addition I am behind a firewall which most likely stops 98% of stuff but I would like to find out what is getting through.

Thanks to both for the help, really appreciate it.

---

### Post by newbux on 2009-01-04
hello and thanks for the great help with security on linux. i am new to linux. i installed snort as directed by post 20 and 21 but now how do i use snort? i dont know how to launch it?

---

### Post by bodhi.zazen on 2009-01-04
> **newbux said:**
> hello and thanks for the great help with security on linux. i am new to linux. i installed snort as directed by post 20 and 21 but now how do i use snort? i dont know how to launch it?

If you installed snort from the repos it will start automatically.

You can start / stop it manually with :

Start :

```
sudo /etc/init.d/snort start
```

Stop :

```
sudo /etc/init.d/snort stop
```

Snort is confusing at first. Network activity is broken into packets of information. Snort analyzes each packet and if there is a violation of the snort rules then an alert is generated.

If you followed my how to you also installed mysql (a database) and base (a front end for the data). If not I am not sure where and how snort (from the repos) will send alerts.

Try looking at this post (It is a little technical)

[http://ubuntuforums.org/showthread.php?t=483488](http://ubuntuforums.org/showthread.php?t=483488)

---

### Post by MaindotC on 2009-01-05
> **newbux said:**
> hello and thanks for the great help with security on linux. i am new to linux. i installed snort as directed by post 20 and 21 but now how do i use snort? i dont know how to launch it?

Snort will gather data for you and store it in the mysql database you installed.  This data is usually "who scanned me" and "what type of scan was it" by default.  I think what you want to know is HOW to view this information.  I took a security class and I had this very same question - I installed Snort but I didn't know what snort was doing or how to view what it detects.  The common way of viewing this data is to install apache and a customized view of the Snort data called BASE.  BASE will put the data in a nice graphical format, fully customizable, so you can see this information.  I just typed "snort base" in google images and here's the first picture returned.  Let me know if that makes sense.  [img]http://homepage.mac.com/duling/halfdozen/resources/snort-base1.png[/img] There are also some tricks to installing BASE that aren't mentioned - a couple php-pear modules you need to install that aren't installed by default (or at least weren't when I installed snort/mysql/apache/base).

What I'd really like is some type of auditory alarm like we did in the windows-portion of the Snort lab.  With base, you have to keep looking at /localhost/base-php4 and hitting refresh to catch someone attacking.

---

### Post by newbux on 2009-01-05
hello could you supply me with the all the terminal commands you use to install base and apache and also the pear modules that is if thats all you have to do to install if other instructions needed please feel free to tell me those too. i dont know any terminal commands on my own yet also if you can install the mysql database from terminal can you tell me how to do that too still reading up on that and if you could it would save me alot of time. that is if its not too much trouble for you so far commands that i have seen have been pretty short thank you

---

### Post by bodhi.zazen on 2009-01-05
> **newbux said:**
> hello could you supply me with the all the terminal commands you use to install base and apache and also the pear modules that is if thats all you have to do to install if other instructions needed please feel free to tell me those too. i dont know any terminal commands on my own yet also if you can install the mysql database from terminal can you tell me how to do that too still reading up on that and if you could it would save me alot of time. that is if its not too much trouble for you so far commands that i have seen have been pretty short thank you

:lolflag:

See the first few posts in this thread as well as the link I gave in my last post.

---

### Post by newbux on 2009-01-05
zzzzzzz

---

### Post by MaindotC on 2009-01-06
> **newbux said:**
> hello could you supply me with the all the terminal commands you use to install base and apache and also the pear modules

[_This guide_](http://howtoforge.net/intrusion-detection-with-snort-mysql-apache2-on-ubuntu-7.10-updated) is the one I used to install snort - it's not much different than the OP.  The comment on the bottom by Angry shows which perl commands to execute in order for BASE to work properly.

---

### Post by newbux on 2009-01-12
thanks for the link i tried but i guess it didnt work because i have intrepid or something. so i went and tried to do the OP again but got an error when i tried to compile snort i think i did everything as described in the post i don't know why i received the error message can you help me out.

terminal code in OP:

cd /usr/src/snort-2.8.3
./configure -enable-dynamicplugin --with-mysql
make
make install

error:

In function ‘open’,
    inlined from ‘server_stats_save’ at server_stats.c:349:
/usr/include/bits/fcntl2.h:51: error: call to ‘__open_missing_mode’ declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[4]: *** [server_stats.o] Error 1
make[4]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors/flow/portscan'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors/flow'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/snort-2.8.3.1/src'
make: *** [install-recursive] Error 1

---

### Post by MaindotC on 2009-01-12
Anything dealing with libraries or source code is a little over my head.  I know how to *use* Ubuntu, but I don't know anything about development.  Try dev section or devs on irc?

---

### Post by topimiring on 2009-01-12
is it possible to deploy snort as distributed IDS ?

---

### Post by bodhi.zazen on 2009-01-12
> **topimiring said:**
> is it possible to deploy snort as distributed IDS ?

Yes.

[http://www.securityfocus.com/infocus/1640](http://www.securityfocus.com/infocus/1640)

[http://www.securityfocus.com/infocus/1643](http://www.securityfocus.com/infocus/1643)

---

### Post by topimiring on 2009-01-14
@bodhi.zazen : THANKS bro .. :)

---

### Post by bodhi.zazen on 2009-01-14
> **topimiring said:**
> @bodhi.zazen : THANKS bro .. :)

You are most welcome.

---

### Post by newbux on 2009-01-14
i decided to try and finish the tutorial even though i received a error when compiling snort and when i was editing /etc/snort/snort.conf i couldnt save the changes because i didnt have the permissions. im logged in as administrator do you know why maybe thats why the errors are thier when i try to compile it thanks

---

### Post by bodhi.zazen on 2009-01-14
> **newbux said:**
> i decided to try and finish the tutorial even though i received a error when compiling snort and when i was editing /etc/snort/snort.conf i couldnt save the changes because i didnt have the permissions. im logged in as administrator do you know why maybe thats why the errors are thier when i try to compile it thanks

You have to run the commands in this tutorial as root.

Either prefix every command with sudo

sudo command

or obtain a root shell with

```
sudo -i
```

---

### Post by newbux on 2009-01-14
the directions in the tutorial i was working on were

Open /etc/snort/snort.conf with your favorite text editor (nano, vi, vim, etc.).

when i made the changes i tried to save them and close the document but a pop box said that i did not have the correct permissions.

so i did not use the terminal to edit it how come i dont have permissions even if im logged in as administrator.thanks

---

### Post by topimiring on 2009-01-15
guys,
is there any way to integrate snort and sms gateway ? just in case I want to send all the alerts via sms.
Thanks b4 :)

---

### Post by bodhi.zazen on 2009-01-15
> **newbux said:**
> the directions in the tutorial i was working on were

Open /etc/snort/snort.conf with your favorite text editor (nano, vi, vim, etc.).

when i made the changes i tried to save them and close the document but a pop box said that i did not have the correct permissions.

so i did not use the terminal to edit it how come i dont have permissions even if im logged in as administrator.thanks

The administrator account on Linux (Ubuntu) is called root. If you are and administrator that means you can access root via sudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In a terminal either use 

sudo nano /file/to/edit #you can use emacs, nano, vim, ....

To use grapgical applications, such as gedit, use gksu

gksu gedit /file/to/edit

I would caution you against using word processors such as OpenOffice or Abiword to edit config files as config files are text files and we want to keep them that way (not convert them to OOO or Abiword formated documents).

---

### Post by bodhi.zazen on 2009-01-15
> **topimiring said:**
> guys,
is there any way to integrate snort and sms gateway ? just in case I want to send all the alerts via sms.
Thanks b4 :)

Yes you can. I have not done this so I can give you some links :

[http://www.linux.com/feature/29856](http://www.linux.com/feature/29856)

[http://www.linuxsecurity.com/content/view/117377/171/](http://www.linuxsecurity.com/content/view/117377/171/)

---

### Post by topimiring on 2009-01-17
> **bodhi.zazen said:**
> Yes you can. I have not done this so I can give you some links :

[http://www.linux.com/feature/29856](http://www.linux.com/feature/29856)

[http://www.linuxsecurity.com/content/view/117377/171/](http://www.linuxsecurity.com/content/view/117377/171/)

Thx for this......... :guitar:

---

### Post by newbux on 2009-01-20
i went to development/compiling forum and nobody was able to help me. so i thought i'd post here again in case thier is anybody who knows what is wrong when i compile snort as i posted above. it's really confusing youd think that someone wouldve have posted this problem before. 

but when i try to compile snort like the OP said above i get errors like: 

terminal code in tutorial:

cd /usr/src/snort-2.8.3
./configure -enable-dynamicplugin --with-mysql
make
make install

error:

In function &#8216;open&#8217;,
inlined from &#8216;server_stats_save&#8217; at server_stats.c:349:
/usr/include/bits/fcntl2.h:51: error: call to &#8216;__open_missing_mode&#8217; declared with attribute error: open with O_CREAT in second argument needs 3 arguments
make[4]: *** [server_stats.o] Error 1
make[4]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors/flow/portscan'
make[3]: *** [install-recursive] Error 1
make[3]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors/flow'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/usr/src/snort-2.8.3.1/src/preprocessors'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/usr/src/snort-2.8.3.1/src'
make: *** [install-recursive] Error 1


some compiling goes on but at the end thier are the errors above. also i have ubuntu 8.10 i was thinking that maybe its because i have the new version and some people have the old one?

thx

---

### Post by Francesco67 on 2009-01-27
Hi all,
many thanks to bodhi.zazen. 
Followed this tutorial, snort+base+mysql up & working in about 3hrs, on a stand alone box. Tested by enabling a p2p rule, with Azureus running, also tested with [http://testmyids.com/](http://testmyids.com/). Excellent tutorial. Next: binary output & barnyard; refine config; then OSSEC.

Best regards
Francesco
Italy

---

### Post by bmwman on 2009-01-29
Question: If I install in a virtual machine, I'm using VMware, amd set up the intrusion detection in it, would that detect attacs agains the Host or just the Virtual machine? Having the network bridged gives two separate IPs so I'm not sure if this would only protect the VMware?

Thanks

---

### Post by The Tronyx on 2009-01-29
> **bmwman said:**
> Question: If I install in a virtual machine, I'm using VMware, amd set up the intrusion detection in it, would that detect attacs agains the Host or just the Virtual machine? Having the network bridged gives two separate IPs so I'm not sure if this would only protect the VMware?

Thanks

Cool question bmwman!  A lot of it is going to have to deal with how it is bridged.  I just woke up but I will do my best to try and explain this clearly but please forgive me if I fall short in doing so.

When you set up snort, there is a config file.  In this config file you declare the IP(s), range, or block that you want snort to listen on.  Obviously, in order for snort to listen on these IPs, they generally need to be bound to the box on which Snort is snorting ;)

I understand that when you bridge the IP, you get two separate IPs but how is traffic treated?  If I have read your question properly, there may be 2 separate IPs but the host IP and the virtual machine IP are bridged and as such, traffic should be able to move freely.  This means that any traffic directed to the host/main computer should hit the virtual machine as well.  And since the virtual machine is listening on the IPs declared in the var HOME_NET it should log alerts.

If you wanted to test this easily, I would recommend doing:
sudo apt-get install nikto
nikto -h 127.0.0.1

If that doesn't give you the information you were looking for, try directing hostile traffic to the host machine from another machine on the network.

---

### Post by bmwman on 2009-01-29
Thanks for the answer. So I can specify the two IPs in the config file and I'm good. I asked this because it would be great if I just set up a VM and use it home and at work, rather then installing/configuring everything twice.. I'll give it a shot. BTW, somebody was trying to hack into my PC couple of days ago so I'm all pumped up about it :). Also what kind of information is caputered in case of attack attemp? Is there a way to set up some kinda of a trap so this person can be caught or at least I can get back on him?

I would really apreciate any input. Thank you.

---

### Post by bodhi.zazen on 2009-01-29
> **bmwman said:**
> Thanks for the answer. So I can specify the two IPs in the config file and I'm good. I asked this because it would be great if I just set up a VM and use it home and at work, rather then installing/configuring everything twice.. I'll give it a shot. BTW, somebody was trying to hack into my PC couple of days ago so I'm all pumped up about it :). Also what kind of information is caputered in case of attack attemp? Is there a way to set up some kinda of a trap so this person can be caught or at least I can get back on him?

I would really apreciate any input. Thank you.

Well, if an IP is giving you problems, just black list the IP.

I do not advise you retaliate as that will get you into trouble. Search the IP (look up) and report it to the IP provider.

---

### Post by bmwman on 2009-01-29
I would report him, but it's an ISP in Mexico.

---

### Post by bodhi.zazen on 2009-01-29
> **bmwman said:**
> I would report him, but it's an ISP in Mexico.

:lolflag:

Well, that is what black listing is for ;)

---

### Post by tnnn on 2009-01-30
Since I'm not a big fan of adding several resource hungry services (apache, mysql) when they are not essential, I decided to go for the sqlless snort + ossec. I used the "snort" ubuntu package from repository which installed and started flawlessly (it detected my own nmap scans, and even some random port scans from internet). However, when Ubuntu is booting, I can see that snort starting script has "failed" and snort doesn't start. But if I run "/etc/conf.d/snort start" from console it starts without any issues. I've tried running it with both original and bodhi.zazens scripts but the result is always the same - snort fails during boot, but starts and works perfectly when started from console... Executing from rc.local changes nothing. I've tried "snort -T -c /etc/snort/snort.conf" but it doesn't report any errors. 

Any ideas why is it happening? Or at least how to find out what is failing during boot?

---

### Post by topimiring on 2009-01-31
I'm sorry for asking such a noob question ,
Is there any way to translate honeypot captured data into a SNORT signature ?
I'd like to deploy self-learning IDS with snort based on data caputred by honeypot softwares.
THank you

---

### Post by KEE on 2009-02-10
wondering if this is for me. i think i get hacked almost on a daily bases. everytime i install any ubuntu 7.10 to 8.10 (i give up on 8.04 and 8.10 since  i get systems 32 file along the installation process) . that same day my drive becomes "read only" and cannot save or anything. its either that or malicious software. going to reinstall sometime soon so wondering if i should install this before updates or after? i seem tobe getting hacked or getting malicious software during installation. i need to try something. please help

---

### Post by bodhi.zazen on 2009-02-10
> **KEE said:**
> wondering if this is for me. i think i get hacked almost on a daily bases. everytime i install any ubuntu 7.10 to 8.10 (i give up on 8.04 and 8.10 since  i get systems 32 file along the installation process) . that same day my drive becomes "read only" and cannot save or anything. its either that or malicious software. going to reinstall sometime soon so wondering if i should install this before updates or after? i seem tobe getting hacked or getting malicious software during installation. i need to try something. please help

Sounds like a hard ware problem to me, my guess is your hard drive is old and/or failing. When there are disk errors they are remounted read only.

---

### Post by catolh on 2009-02-11
For some reason the ossec webui doesnt ask for a password when i access the site. Even though i set a username and password when i installed ossec.

Is this a known issue? (when i installed apache i only did apt-get apache2 and php modules).

---

### Post by bodhi.zazen on 2009-02-11
> **catolh said:**
> For some reason the ossec webui doesnt ask for a password when i access the site. Even though i set a username and password when i installed ossec.

Is this a known issue? (when i installed apache i only did apt-get apache2 and php modules).

I use https / .htaccess for the webui

---

### Post by catolh on 2009-02-12
> **bodhi.zazen said:**
> I use https / .htaccess for the webui
Ah, i figured there was something about .htaccess. But how do i go about and make it require https ?

---

### Post by bodhi.zazen on 2009-02-12
> **catolh said:**
> Ah, i figured there was something about .htaccess. But how do i go about and make it require https ?

You have to install / configure ssl and apache :

[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html](http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html)

---

### Post by catolh on 2009-02-13
> **bodhi.zazen said:**
> You have to install / configure ssl and apache :

[http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html](http://www.tc.umn.edu/~brams006/selfsign_ubuntu.html)
Thanks alot :)

---

### Post by topimiring on 2009-02-21
is there any way to automatically import honeycomb signatures to snort ?
thx

---

### Post by menschtx on 2009-02-21
bodhi, 
I tried to follow your tutorial for protection, but for some reason the security level set from I believe compliance to enforce has blocked firefox 3. Is there a way to reverse this? Or clear the process and go back to the beginning?

---

### Post by bodhi.zazen on 2009-02-21
> **menschtx said:**
> bodhi, 
I tried to follow your tutorial for protection, but for some reason the security level set from I believe compliance to enforce has blocked firefox 3. Is there a way to reverse this? Or clear the process and go back to the beginning?

Are you asking about apparmor ?

---

### Post by KEE on 2009-03-07
hi,

 i got a thread about my problem with snort here [http://ubuntuforums.org/showthread.php?p=6853015#post6853015](http://ubuntuforums.org/showthread.php?p=6853015#post6853015) please help and thank you

---

### Post by drubin on 2009-03-07
> **KEE said:**
> hi,

 i got a thread about my problem with snort here [http://ubuntuforums.org/showthread.php?p=6853015#post6853015](http://ubuntuforums.org/showthread.php?p=6853015#post6853015) please help and thank you

Please don't cross post. You have linked to a thread that is even in the same forum about 7 threads down the list from this one.

You have waited less then 3 hours to get a reply. Problems can take some time to get a reply.

---

### Post by bodhi.zazen on 2009-03-07
> **menschtx said:**
> bodhi, 
I tried to follow your tutorial for protection, but for some reason the security level set from I believe compliance to enforce has blocked firefox 3. Is there a way to reverse this? Or clear the process and go back to the beginning?

Are you asking about apparmor ?

If so see the sticky on apparmor.

sudo aa-complain firefox

---

### Post by rodney757 on 2009-04-01
I was just reading this tutorial and it says to use airsnort if you use wireless. When I go to the airsnort site it says that the project is dead. Is there an alternitive I should use? Thanks

---

### Post by shahin on 2009-04-01
Is there any way to verify that my database if being populated with data?  I run snort -v, and I see it capturing data.  I have also set up the database, and I see the tables in it.  How do I run snort to push data to the database, and then what command do I run in the database to see the data just collected please?  Oh btw, the bleeding rules url does not work.  Does anyone have another link where these rules can be downloaded for snort2.8.3.2?

---

### Post by bodhi.zazen on 2009-04-01
> **shahin said:**
> Is there any way to verify that my database if being populated with data?  I run snort -v, and I see it capturing data.  I have also set up the database, and I see the tables in it.  How do I run snort to push data to the database, and then what command do I run in the database to see the data just collected please?  Oh btw, the bleeding rules url does not work.  Does anyone have another link where these rules can be downloaded for snort2.8.3.2?

I use base to look at alerts generated by snort. You can look at mysql directly or what ever you wish.

If you want to test it, hit your box (snort) with a port scanner.

Snort does not, buy default, capture all packets. To do that use wireshark.

---

### Post by shahin on 2009-04-04
Thanks bodhi.  Something else is puzzling me now.  I am trying to download rules.  So I right clicked on the "download" link for the rule, and selected "copy link location", then I move to xterm window, and pasted the clipboard content in front of wget and pressed return.  All I get is a 10K file.  I seem to be able to download the same file fine using the browser.  Any idea?

---

### Post by shahin on 2009-04-04
I downloaded your script, and put it in the right directory, but when I run it I see the following error from snort:
```

Uh, you need to tell me to do something...

Fatal Error, Quitting..

```
Here is where the script is:
```

@thunder:/etc/init.d$ ls -al snort
-r-x------ 1 root root 4077 2009-04-04 13:14 snort
@thunder:/etc/init.d$ 

```
I think the permissions and everything else is as you stated.  I am not sure why I get this error.

---

### Post by shahin on 2009-04-05
I am running into some problems trying to activate snort.  I seem to be able to run it fine from my Ubuntu's /usr/src/snort/snort-2.8.3.2 and /etc/snort directory, but when I try to run it from /usr/local/bin, I get the fullowing error message:
```

@thunder:/usr/local/bin$ snort -v
Running in packet dump mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Verifying Preprocessor Configurations!
ERROR: Failed to lookup for interface: no suitable device found. Please specify one with -i switch
Fatal Error, Quitting..

```

Here is what it looks like when I run it successfully:
```

root@thunder:/etc/snort# snort -v
Running in packet dump mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Verifying Preprocessor Configurations!
***
*** interface device lookup found: eth0
***

Initializing Network Interface eth0
Decoding Ethernet on interface eth0

        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.3.2 (Build 22)  
   ''''    By Martin Roesch & The Snort Team: http://www.snort.org/team.html
           (C) Copyright 1998-2008 Sourcefire Inc., et al.
           Using PCRE version: 7.8 2008-09-05

Not Using PCAP_FRAMES

```

---

### Post by TheRoot on 2009-04-07
Hi, 

Thank you very much for the tutorial it was more than great.

I have a strange issue, after I installed everything with no problems at all, and Snort + BASE + OSSEC are all working and I can access BASE + OSSEC from a browser, I don't see any activity in the BASE page !!!

Isn't that strange?

I even disabled my firewall to make sure that the sensor of snort is not being blocked (if I'm correct) and still nothing !!!

What do you think is the problem?

---

### Post by bodhi.zazen on 2009-04-08
This is a common question. Most likely you are not getting much traffic which violates the snort rules.

If snort does not log an alert to mysql, the connection times out. I am not sure how long it takes, but I re-start snort every 6 hours.

Hit your machine with a port scanner to test snort. And yes, iptables and ossec will block traffic so turn them off when you test snort.

---

### Post by TheRoot on 2009-04-08
> **bodhi.zazen said:**
> This is a common question. Most likely you are not getting much traffic which violates the snort rules.

If snort does not log an alert to mysql, the connection times out. I am not sure how long it takes, but I re-start snort every 6 hours.

Hit your machine with a port scanner to test snort. And yes, iptables and ossec will block traffic so turn them off when you test snort.

Thank you very much for your reply. I do the same as you do "restart snort every 6 hours" using the cron jobs you explained in your tutorial.

It seems that my network is cleaner than I imagined, today I got my first ALERT :)

BTW: what are the best tutorials, papers or useful information to go beyond what is displayed here? (Ex: advance config, writing rules, howto know which rule raised the alert, etc). I only asked because I see you have great experience in SNORT.

Thank you in advance for your help and support.

---

### Post by wmmccoy on 2009-04-08
Thank you ever so much for such a well written and complete tutorial! I went through seven others before discovering yours.
't 
I am having one problem though and forgive me in advance if it turns up being a semi-noob error.

After following your instructions and placing commands in the proper startup files, snort never starts as a daemon; it doesn't start at all. The thing is I can run snort from a command line with no problems.

I'll be grateful for anything you can do to set me in the right direction.

Very best regards,

Mike McCoy

---

### Post by bodhi.zazen on 2009-04-08
Yes, you need to start snort manually. Once you start it it will run in the background (if you use the commands in my tutorial).

I re-start snort every 6 hours with a cron script.

I would just add the command to start snort in /etc/rc.local , then it will start on boot.

---

### Post by wmmccoy on 2009-04-08
I am trying to start snort from local.rc, thats why I'm perplexed.

---

### Post by wmmccoy on 2009-04-08
I am starting from rc,local rather...

---

### Post by wmmccoy on 2009-04-08
I am so sorry for being dense, but I configured my rc.local file per your instructions in your tutorial and snort doesn't start. I edited my cron file to match yours as well. I don't have to start manually every time I restart do I?

Signed,
Truly a noob

---

### Post by TheRoot on 2009-04-08
BTW: bodhi.zazen

I think the current setup shall only monitor the traffic going into the IDS system, or going out of the IDS system, if we are in a switched network. If we want to monitor the whole network? then we need a TAP, or a switch with monitoring ports enabled.

If the network is built on HUBs then there is no problem, everything shall be monitored weather destined to the system holding the IDS or not.

Q: Does the white list mean: don't monitor these systems? IF yes? then I think it is wrong to assign such an IP, because SNORT shall not monitor it.

---

### Post by bodhi.zazen on 2009-04-08
> **wmmccoy said:**
> I am so sorry for being dense, but I configured my rc.local file per your instructions in your tutorial and snort doesn't start. I edited my cron file to match yours as well. I don't have to start manually every time I restart do I?

Signed,
Truly a noob

Perhaps it would help if you were to provide a more detailed description of the problem.

For example the command you start snort is .....

you have what in rc.local .....

you have what as a cron job ....

what makes you think snort is not running ? what is the output of

```
ps aux | grep snort
```

simply stating that it is not working does not seem to be an effective means of communication.

---

### Post by bodhi.zazen on 2009-04-08
> **TheRoot said:**
> BTW: bodhi.zazen

I think the current setup shall only monitor the traffic going into the IDS system, or going out of the IDS system, if we are in a switched network. If we want to monitor the whole network? then we need a TAP, or a switch with monitoring ports enabled.

If the network is built on HUBs then there is no problem, everything shall be monitored weather destined to the system holding the IDS or not.


yes, easiest way is to use a switch with a monitoring port.

> Q: Does the white list mean: don't monitor these systems? IF yes? then I think it is wrong to assign such an IP, because SNORT shall not monitor it.

yes a white list , as with other white lists, basically means do not monitor traffic from ip address. White lists have their uses ;)

In terms of your previous question re: snort info : Either buy a book on snort or google.

After you run snort for a while though you should be good to go.

---

### Post by john.soper on 2009-04-08
> **bodhi.zazen said:**
> 

```
ps aux | grep snort
```


Is "ps aux" equivalent to "ps -ef"?

Thanks,
John

---

### Post by bodhi.zazen on 2009-04-08
yes. man ps goes into some gory details :twisted:

---

### Post by wmmccoy on 2009-04-08
> **bodhi.zazen said:**
> Perhaps it would help if you were to provide a more detailed description of the problem.

For example the command you start snort is .....  **[B][COLOR="Red"]snort -c /etc/snort/snort.conf**[/COLOR]
[/B]
you have what in rc.local ..... [COLOR="Red"]/etc/init.d//snort boot[/COLOR]

you have what as a cron job [COLOR="Red"][COLOR="Red"]/etc/init.d/snor....t restart
[/COLOR][/COLOR]
what makes you think snort is not running ? what is the output of

```
ps aux | grep snort
``` [COLOR="Red"]this command returns nothing [/COLOR]

simply stating that it is not working does not seem to be an effective means of communication. [COLOR="Blue"]I thought I was a little clearer than that, but my apologies for making things hard for you[/COLOR].

---

### Post by wmmccoy on 2009-04-08
In my haste to get a message to you, I noticed a couple of things that are obvious typos - please ignore them...

MM

---

### Post by bodhi.zazen on 2009-04-09
> **wmmccoy said:**
> In my haste to get a message to you, I noticed a couple of things that are obvious typos - please ignore them...

MM

No problem . Did you get it working ?

---

### Post by KEE on 2009-04-09
can someone help me how to remove snort and all it's little bugs...i cant install anything or update linux intrepid anymore =( ```
E: snort: subprocess post-installation script returned error exit status 1

``` details here -->```
Setting up snort (2.7.0-19ubuntu)...
update-rc.d: warning: /erc/init.d/snort missing LSB style header
invoke-rc.d: initscript snort, action &#8220;stop&#8221; failed.
Dpkg: error processing snort (--configure):
 subprocess post-installation script returned error exit status 1 
Setting uplibsdl-net1.2.7-2)...

```

---

### Post by KEE on 2009-04-09
> **KEE said:**
> can someone help me how to remove snort and all it's little bugs...i cant install anything or update linux intrepid anymore =( ```
E: snort: subprocess post-installation script returned error exit status 1

``` details here -->```
Setting up snort (2.7.0-19ubuntu)...
update-rc.d: warning: /erc/init.d/snort missing LSB style header
invoke-rc.d: initscript snort, action “stop” failed.
Dpkg: error processing snort (--configure):
 subprocess post-installation script returned error exit status 1 
Setting uplibsdl-net1.2.7-2)...

```

i think i got it, i have to try to install something to see if works =D```
$sudo -i
$cd /usr/src/snort-2.8.3.2
$make uninstall
```

---

### Post by KEE on 2009-04-09
> **KEE said:**
> i think i got it, i have to try to install something to see if works =D```
$sudo -i
$cd /usr/src/snort-2.8.3.2
$make uninstall
```

well heck i cant remove it xD cant remove it in the repositories ?!?! is this malicious software!?!?!

---

### Post by shahin on 2009-04-11
Hi Bodhi,
   I seem to be able to run snort using the command you used in the script ie. when I do this:
```

/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort -D

```
I get this:
```

root@thunder:/usr/share/doc# ps aux | grep snort
root     25753  0.0  0.0   3220   844 pts/1    S+   17:35   0:00 more snort
root     25759  0.0  0.0   2076   540 pts/2    R+   17:36   0:00 grep snort
root     30336  0.0  0.1   6464  2552 pts/0    S+   12:50   0:00 mysql -u snort -p snort
root@thunder:/usr/share/doc# 

```
But when I issue the two commands that run the script, nothing happens:
```

@thunder:~$ sudo /etc/init.d/snort restart
@thunder:~$ sudo /etc/init.d/snort boot
@thunder:~$ ps -ef | grep snort
root     30336 30272  0 12:50 pts/0    00:00:00 mysql -u snort -p snort
31127 30529  0 12:56 pts/1    00:00:00 grep snort
@thunder:~$ cd /etc/init.d/
@thunder:/etc/init.d$ ls

```

---

### Post by shahin on 2009-04-11
My mistake.  It runs when I use snort -v command
```

root@thunder:/usr/share/doc# snort -v
Running in packet dump mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Verifying Preprocessor Configurations!
***
*** interface device lookup found: eth0
***

Initializing Network Interface eth0
Decoding Ethernet on interface eth0

        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.3.2 (Build 22)  
   ''''    By Martin Roesch & The Snort Team: http://www.snort.org/team.html
           (C) Copyright 1998-2008 Sourcefire Inc., et al.
           Using PCRE version: 7.8 2008-09-05

Not Using PCAP_FRAMES
04/11-17:43:07.562835 169.254.1.125:21302 -> 255.255.255.255:21302
UDP TTL:64 TOS:0x0 ID:20024 IpLen:20 DgmLen:628
Len: 600
=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+

04/11-17:43:09.511187 ARP reply 169.254.1.125 is-at 0:15:9A:FA:F3:B (0:15:9A:D3:3A:D9)

04/11-17:43:10.781693 74.125.47.17:80 -> 192.168.1.3:60524
TCP TTL:251 TOS:0x0 ID:61537 IpLen:20 DgmLen:68
***AP*** Seq: 0x13472EBF  Ack: 0x5D0D2F63  Win: 0x37DC  TcpLen: 20
=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+

04/11-17:43:10.781742 192.168.1.3:60524 -> 74.125.47.17:80
TCP TTL:64 TOS:0x0 ID:51708 IpLen:20 DgmLen:40 DF
***A**** Seq: 0x5D0D2F63  Ack: 0x13472EDB  Win: 0x6FB8  TcpLen: 20
=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+

^C*** Caught Int-Signal
Run time prior to being shutdown was 5.798422 seconds
===============================================================================
Packet Wire Totals:
   Received:            7
   Analyzed:            7 (100.000%)
    Dropped:            0 (0.000%)
Outstanding:            0 (0.000%)
===============================================================================
Breakdown by protocol (includes rebuilt packets):
      ETH: 7          (100.000%)
  ETHdisc: 0          (0.000%)
     VLAN: 0          (0.000%)
     IPV6: 0          (0.000%)
  IP6 EXT: 0          (0.000%)
  IP6opts: 0          (0.000%)
  IP6disc: 0          (0.000%)
      IP4: 3          (42.857%)
  IP4disc: 0          (0.000%)
    TCP 6: 0          (0.000%)
    UDP 6: 0          (0.000%)
    ICMP6: 0          (0.000%)
  ICMP-IP: 0          (0.000%)
      TCP: 2          (28.571%)
      UDP: 1          (14.286%)
     ICMP: 0          (0.000%)
  TCPdisc: 0          (0.000%)
  UDPdisc: 0          (0.000%)
  ICMPdis: 0          (0.000%)
     FRAG: 0          (0.000%)
   FRAG 6: 0          (0.000%)
      ARP: 1          (14.286%)
    EAPOL: 0          (0.000%)
  ETHLOOP: 0          (0.000%)
      IPX: 0          (0.000%)
    OTHER: 3          (42.857%)
  DISCARD: 0          (0.000%)
InvChkSum: 0          (0.000%)
   S5 G 1: 0          (0.000%)
   S5 G 2: 0          (0.000%)
    Total: 7         
===============================================================================
Action Stats:
ALERTS: 0
LOGGED: 0
PASSED: 0
===============================================================================
Snort exiting
root@thunder:/usr/share/doc# 


```

---

### Post by shahin on 2009-04-11
Please ignore the previous post, I am geting closer.  Now I see this when I run snort with -c option pointing the the snort.conf file:
```

Initializing Network Interface eth0
Decoding Ethernet on interface eth0
database: compiled support for ( )
database: configured to use mysql
database: 'mysql' support is not compiled into this build of snort

ERROR: If this build of snort was obtained as a binary distribution (e.g., rpm,
or Windows), then check for alternate builds that contains the necessary
'mysql' support.

If this build of snort was compiled by you, then re-run the
the ./configure script using the '--with-mysql' switch.
For non-standard installations of a database, the '--with-mysql=DIR'
syntax may need to be used to specify the base directory of the DB install.

See the database documentation for cursory details (doc/README.database).
and the URL to the most recent database plugin documentation.
Fatal Error, Quitting..

```

I am going to recompile.  I know for sure I used the -mysql option during the compilation.

---

### Post by shahin on 2009-04-11
Seems my install is working, but I am not sure.  I see the following:
```

root@thunder:/etc/snort# ps aux |  grep snort
snort    14473  7.1  7.1 144468 110520 ?       Ss   18:52   0:05 snort -c /etc/snort/snort.conf -u snort -g snort -D
root     30336  0.0  0.1   6464  2564 pts/0    S+   12:50   0:00 mysql -u snort -p snort
root@thunder:/etc/snort# 

```
I downloaded nmap, and issued nmap x.x.x.x ( ip of my snort machine ).  But I do not see any alerts in /var/log/snort 
```

root@thunder:/var/log/snort# more snort.log.1239490353 
root@thunder:/var/log/snort# more alert 

```
I also do not see anything collecting my my snort database:
```

mysql> select * from event;
Empty set (0.00 sec)

mysql> select * from data;
Empty set (0.00 sec)


```

Help please.

Oh the machine that is doing the nmap scan is connected through a wireless, and going through a hub/router with firewall functionality.  I also have firewall turned on at the host that runs the snort.  I use fireStarter to manage the Ubuntu firewall.  Should I disable it to test?

---

### Post by wmmccoy on 2009-04-11
> **bodhi.zazen said:**
> No problem . Did you get it working ?

I haven't had any success yet. As I stated earlier, I am able to start snort from the command line, but when I attempt to start when I boot (from rc.local), it does not start (no PID). I have backtracked my work, and it looks like I have mirrored your tutorial step by step. (The best by far anywhere) I am continuing to investigate. Are there any environmental situations that could cause my problem (like a mis-configured network, etc.)?

Thanks for your time and assistance!

Best regards,
Mike McCoy

---

### Post by over_my_head on 2009-04-13
thanks for writing the tutorial - i haven't tried it yet but it looks very detailed. 
I intended to go ahead and try it out, using airsnort since i'm on a wireless connection. i went to the airsnort page, it says: "This software is old. It is no longer maintained or supported. Besides, there are much better tools out there. You really should be trying something like aircrack-ng." 
???
aircrack-ng seems to be some way of cracking wireless network encryption keys... and then it says it can "audit" wireless networks...
i'm very confused now.

---

### Post by gyterpena on 2009-04-17
> **bodhi.zazen said:**
> [SIZE=4]** Install base**[/SIZE]



Code:

cd
wget [http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz](http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz)

Note : Later versions of base do not work (with Ubuntu at least).

Open a web browser and navigate to [http://your_ip_address/base](http://your_ip_address/base)


[Back to top]("http://ubuntuforums.org/showthread.php?t=919472")

Great tutorial

I have it running with base 1.4.1

setup is done from [http://your_ip_address/base/setup](http://your_ip_address/base/setup)

you also need to install pear Mail Mail_Mime Net_SMTP
[Reference]("http://www.snort.org/archive-1-6544.html")

---

### Post by bodhi.zazen on 2009-04-18
Thanks for the information [gyterpena]("http://ubuntuforums.org/member.php?u=125304")

I shall try it and update my post ;)

---

### Post by shahin on 2009-04-19
Hi Bodhi,
  I see alerts in my alerts file in /var/logs/snort directory, but I do not see them in base page.  Here is what I have in the alerts files:

```

[**] [1:382:7] ICMP PING Windows [**]
[Classification: Misc activity] [Priority: 3] 
04/19-09:43:20.987089 192.168.1.4 -> 192.168.1.3
ICMP TTL:128 TOS:0x0 ID:24149 IpLen:20 DgmLen:60
Type:8  Code:0  ID:512   Seq:16128  ECHO
[Xref => http://www.whitehats.com/info/IDS169]

[**] [1:384:5] ICMP PING [**]
[Classification: Misc activity] [Priority: 3] 
root@thunder:/var/log/snort# 

```

but base page is blank.  Any idea?

---

### Post by tronnix75 on 2009-04-19
need help getting the rules downloaded, i use your commands i get a permission denied i typed in this"

wget [http://www.snort.org/pub-bin/downloads.cgi/snortrules-snapshot-2.8.tar.gz:(](http://www.snort.org/pub-bin/downloads.cgi/snortrules-snapshot-2.8.tar.gz:()

---

### Post by bodhi.zazen on 2009-04-19
> **shahin said:**
> Hi Bodhi,
  I see alerts in my alerts file in /var/logs/snort directory, but I do not see them in base page.  Here is what I have in the alerts files:

```

[**] [1:382:7] ICMP PING Windows [**]
[Classification: Misc activity] [Priority: 3] 
04/19-09:43:20.987089 192.168.1.4 -> 192.168.1.3
ICMP TTL:128 TOS:0x0 ID:24149 IpLen:20 DgmLen:60
Type:8  Code:0  ID:512   Seq:16128  ECHO
[Xref => http://www.whitehats.com/info/IDS169]

[**] [1:384:5] ICMP PING [**]
[Classification: Misc activity] [Priority: 3] 
root@thunder:/var/log/snort# 

```but base page is blank.  Any idea?

No idea ;)

snort logs according to rules. So I am guessing a problems with mysql.

> **tronnix75 said:**
> need help getting the rules downloaded, i use your commands i get a permission denied i typed in this"

wget [http://www.snort.org/pub-bin/downloads.cgi/snortrules-snapshot-2.8.tar.gz:(]("http://www.snort.org/pub-bin/downloads.cgi/snortrules-snapshot-2.8.tar.gz:%28")

tronnix : You need to register with snort before you can download rules.

---

### Post by tronnix75 on 2009-04-19
I am registered with snort and logged in.

---

### Post by bodhi.zazen on 2009-04-19
Well then download the rules :)

Notice, they limit how often you can download, I think there is a 10 or 15 minute time out.

[http://www.snort.org/pub-bin/downloads.cgi](http://www.snort.org/pub-bin/downloads.cgi)

---

### Post by tronnix75 on 2009-04-19
i will try again.  is your guide pretty up to date? i am using ubuntu 8.04 right now and trying to learn more!!

---

### Post by shahin on 2009-04-19
I had a lot of trouble using wget.  So I just downloaded the file to my desktop using Firefox, then copied the file to the directory that I wanted like /usr/src/snort or /etc/snort/ .

Good luck

---

### Post by shahin on 2009-04-19
Hi Bodhi,
  My problem is not mysql.  I see alerts there:
```

mysql> show tables;
+------------------+
| Tables_in_snort  |
+------------------+
| acid_ag          | 
| acid_ag_alert    | 
| acid_event       | 
| acid_ip_cache    | 
| base_roles       | 
| base_users       | 
| data             | 
| detail           | 
| encoding         | 
| event            | 
| icmphdr          | 
| iphdr            | 
| opt              | 
| reference        | 
| reference_system | 
| schema           | 
| sensor           | 
| sig_class        | 
| sig_reference    | 
| signature        | 
| tcphdr           | 
| udphdr           | 
+------------------+
22 rows in set (0.00 sec)

mysql> select * from event;
+-----+-----+-----------+---------------------+
| sid | cid | signature | timestamp           |
+-----+-----+-----------+---------------------+
|   1 |   2 |         1 | 2009-04-12 15:24:20 | 
|   1 |   3 |         1 | 2009-04-12 15:24:20 | 

```

I just do not see them in BASE.  I also do not see a sensor.  BTW, I did not see anything about us having to install ACID.  Did I miss a step?  Other procedures I have seen about this, involves installing ACID.

---

### Post by tronnix75 on 2009-04-19
this part is confusing:  
I mostly copy and pasting but the URL i copy are not correct.


wget [http://www.snort.org/the_rules_you_wish_to_use](http://www.snort.org/the_rules_you_wish_to_use)

---

### Post by shahin on 2009-04-19
If you downloaded snort 2.8.x ( x = whatever revision ), then you want this url:
```

http://www.snort.org/pub-bin/downloads.cgi/Download/vrt_os/snortrules-snapshot-2.8.tar.gz

```

Bodhi just wrote it that way, meaning you need to select which version or rules matches your snort file.

---

### Post by shahin on 2009-04-19
I think I have an issue with the way I set up the permissions.  I see a couple of other posts regarding missing sensor id in mysql, which causes BASE not to show anything.  How can I get more information about this and troubleshoot it please?

---

### Post by tronnix75 on 2009-04-19
thanks for the URL that worked now i went to the next command 
cd snort2.8.3 what does this mean there is no directory for that

I downloaded that latest snort 2.8.4

---

### Post by tronnix75 on 2009-04-19
ok i tared the snort 2.8.4 and then changed directory but now what is with this command:


tar zxvf ../snortrules*   i need step by step like baby steps thank you in advance.

---

### Post by tronnix75 on 2009-04-20
I did exactly what you said to do with that URL it downloads really quick then i try to use the tar command does not work errors out what am i doing wrong?

---

### Post by MarnickV on 2009-04-21
Some minor problems here:

in your guide:
```

cp -R /usr/src/snort-2.8.3/doc/signatures .

```

I am using snort 2.8.4 and there is no such directory (doc/signatures). What should I do here?

Another thing: I only downloaded the community rules so if I issue:
```

snort -c /etc/snort/snort.conf

```
I get errors stating that I don't have the appropriate rules (local.rules, icmp.rules, ...). I commented out the includes of those files in snort.conf, and inserted includes for all the community rules. Maybe it would be helpfull to also incorporate that in your guide.

Another small thing: the machine I am installing on is my gateway, so it only has 2 NICs. Currently I configured snort to run on eth1 which is my internet interface, but I guess since snort puts eth1 in promiscuous mode, it would kill performance (however it's only my home network so not too much traffic)... Is it possible to deploy snort on this machine or should I buy an extra NIC; or worse: should I have an inline machine in front of my gateway?

I tried snort on the internet interface and started snort via:
```

/etc/init.d/snort start

```
This resulted in:
```

Snort failed to start ...

```
My entry in /var/log/messages:
```

Apr 21 14:43:32 artoo kernel: [158473.114012] device eth1 entered promiscuous mode
Apr 21 14:43:32 artoo kernel: [158473.114040] audit(1240317812.170:22): dev=eth1 prom=256 old_prom=0 auid=4294967295
Apr 21 14:43:32 artoo kernel: [158473.143981] device eth1 left promiscuous mode
Apr 21 14:43:32 artoo kernel: [158473.143999] audit(1240317812.200:23): dev=eth1 prom=0 old_prom=256 auid=4294967295
Apr 21 14:43:32 artoo kernel: [158473.174009] device eth1 entered promiscuous mode
Apr 21 14:43:32 artoo kernel: [158473.174041] audit(1240317812.230:24): dev=eth1 prom=256 old_prom=0 auid=4294967295
Apr 21 14:43:32 artoo kernel: [158473.204105] device eth1 left promiscuous mode
Apr 21 14:43:32 artoo kernel: [158473.204138] audit(1240317812.260:25): dev=eth1 prom=0 old_prom=256 auid=4294967295

```

Why isn't this working?

Then I tried:
```

snort -v &

```
I let this run for a couple minutes and my packet wire totals were:
```

===============================================================================
Packet Wire Totals:
   Received:           11
   Analyzed:           10 (90.909%)
    Dropped:            0 (0.000%)
Outstanding:            1 (9.091%)
===============================================================================
Breakdown by protocol (includes rebuilt packets):
      ETH: 6          (100.000%)
  ETHdisc: 0          (0.000%)
     VLAN: 0          (0.000%)
     IPV6: 6          (100.000%)

```
All the rest was 0%. I find this weird, since I pinged from another machine and since I am remotely logged in on my machine through SSH and I was surfing the web. Isn't this weird since the amount of packets from SSH/web traffic coming through for example? On top of that, nothing logged in BASE (mysql).

Thanks in advance & kudos for your guide mate.

---

### Post by polecat409 on 2009-04-21
> **shahin said:**
> I think I have an issue with the way I set up the permissions.  I see a couple of other posts regarding missing sensor id in mysql, which causes BASE not to show anything.  How can I get more information about this and troubleshoot it please?

I am having the same problems.  I followed the snort/base instructions exactly on a fresh install of Hardy server. 

Does anyone have any suggestions?  I've been trying to troubleshoot this for a week, and I'm about ready to install the package from the repos (but I don't want to!)...

---

### Post by bodhi.zazen on 2009-04-21
The community rules are very very old and IMO outdated.

You really should register with snort so that you may download a more updated set of rules.

The community rules do not have signatures, so you will have to live without them if you use the community rules. Signatures are nothing more then an explanation of alerts, and the same information is available on line if you wish. You will see links in Base when you look at an alert. "Local" == signatures.

As far as configuration, I am not sure you will need to look at your config file. Snort places your network card in promiscuous mode (snort is a packet sniffer after all, lol), which is fine with modern switches.

---

### Post by polecat409 on 2009-04-21
> **polecat409 said:**
> I am having the same problems.  I followed the snort/base instructions exactly on a fresh install of Hardy server. 

Does anyone have any suggestions?  I've been trying to troubleshoot this for a week, and I'm about ready to install the package from the repos (but I don't want to!)...

Just to clarify, snort is running, I've made another database and also installed base 1.4.1 (which works fine!), but I still get a big-fat-zero for sensors in base:

```
Sensors/Total: 0 / 0
Unique Alerts: 0
Categories: 0
Total Number of Alerts: 0
```

I have snort set to run as a daemon (which it is), but I'll try 'snort -v' anyway, and run 'nmap -v -A my_snort_machine's_ip' from my windows machine, and here's what I get:

```

root@guinness:~# snort -v

04/21-05:49:02.911991 10.1.1.132:22 -> 10.1.8.21:6012
TCP TTL:64 TOS:0x10 ID:64889 IpLen:20 DgmLen:444 DF
***AP*** Seq: 0x83C77398  Ack: 0x8D825380  Win: 0x2180  TcpLen: 20
=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+=+

*** Caught Term-Signal
Run time prior to being shutdown was 451.369952 seconds
===============================================================================
Packet Wire Totals:
   Received:      3095040
   Analyzed:      2606794 (84.225%)
    Dropped:       488103 (15.770%)
Outstanding:          143 (0.005%)
===============================================================================
Breakdown by protocol (includes rebuilt packets):
      ETH: 2606794    (100.000%)
  ETHdisc: 0          (0.000%)
     VLAN: 0          (0.000%)
     IPV6: 24         (0.001%)
  IP6 EXT: 0          (0.000%)
  IP6opts: 0          (0.000%)
  IP6disc: 0          (0.000%)
      IP4: 2604165    (99.899%)
  IP4disc: 62835      (2.410%)
    TCP 6: 0          (0.000%)
    UDP 6: 0          (0.000%)
    ICMP6: 0          (0.000%)
  ICMP-IP: 0          (0.000%)
      TCP: 2539817    (97.431%)
      UDP: 1448       (0.056%)
     ICMP: 65         (0.002%)
  TCPdisc: 0          (0.000%)
  UDPdisc: 0          (0.000%)
  ICMPdis: 0          (0.000%)
     FRAG: 0          (0.000%)
   FRAG 6: 0          (0.000%)
      ARP: 2204       (0.085%)
    EAPOL: 0          (0.000%)
  ETHLOOP: 0          (0.000%)
      IPX: 0          (0.000%)
    OTHER: 401        (0.015%)
  DISCARD: 62835      (2.410%)
InvChkSum: 0          (0.000%)
   S5 G 1: 0          (0.000%)
   S5 G 2: 0          (0.000%)
    Total: 2606794
===============================================================================
Action Stats:
ALERTS: 0
LOGGED: 0
PASSED: 0
===============================================================================
Snort exiting
root@guinness:~#

```

---

### Post by bodhi.zazen on 2009-04-21
I you do not see any sensors in base, than base is not working.

Possibilities are :

1. mysql is not set up properly.

2. snort lost it's connection with mysql. To test this, clear the database in base (from the admin panel) even though it reads "0", then restart snort. You should now see 1 sensor in base.

3. Base is not working, ie base is not connecting to the mysql database.

---

### Post by MarnickV on 2009-04-21
I managed to get my snort working with your script bodhi.zazen, my /var/log/daemon.log showed that snort didn't have the right permissons for /var/log/snort/alert. So after I changed that, everything started like it should.

However, I too have problems in BASE seeing the sensor. I believe BASE _can_ connect to mysql, since I can log in (I have enabled authentication on BASE, table base_users in database snort).

I connected to mysql and I checked some tables:
*tcphdr
*event

Both have one row (the latter has a timestamp from just moments ago).
However, table "sensor" does not have any rows.

Number 2 of your list does not work at my setup, I cleared data tables (from the Cache & Status menu) and then restarted snort. Still no sensor.

Any advice?

---

### Post by shahin on 2009-04-21
> **tronnix75 said:**
> ok i tared the snort 2.8.4 and then changed directory but now what is with this command:


tar zxvf ../snortrules*   i need step by step like baby steps thank you in advance.

Hi Tronnix
.. refers to a directory above where you are currently.  Bodhi wants you to unpack all the tar files that start with snortrules from the parent directory, into the directory you are in.  So if you downloaded a couple (I just downloaded one, but there is different ones like bleeding edge, current etc.  - I say for now just download one. ) of tar files containing the rules into:
/usr/src/snort2.8.4, then I believe the procedures call for creating a directory called /usr/src/snort2.8.4/rules.  So from the rules directory the command tar zxvf ../snortrules* would unpack all the rules and place them in the rules directory.  I hope I got all the directory names right; I am trying to do it from memory.  Good luck.

---

### Post by sw34963 on 2009-04-22
Great Tutorial,  thanks its much appreciated someone going into such detail other than just 'sudo apt-get install snort' :)

Thanks

---

### Post by JK3mp on 2009-04-23
Don't get too dependent on step by step. It'll be very difficult for once you have airsnort /aircrack-ng running to find a step by step tutorial. You'll have the commands and what they do and its up to you most of the time to figure out the best way to put them together to come to the solution/conclusion you want.

---

### Post by MarnickV on 2009-04-27
Yet another small problem here ;)

Snort ran fine for a couple of days, including the restart in the cron job. Now snort doesn't start anymore because of this:

```

Apr 27 09:25:55 blob snort[16022]: Snort exiting
Apr 27 09:25:55 blob snort[16022]: Could not remove pid file /var/run//snort_eth1.pid: Permission denied

```

I changed the ownership to "snort.snort" on the pid files (includign pid.lck) but it seems this file gets deleted and remade, thus giving the new file root ownership (as the start command is ran by root).

Any suggestions? Or should I just start snort through its own user?

---

### Post by jcostom on 2009-04-27
Anyone deployed snort on their external network at home using a passive tap?

I've been working on this configuration, and it works, but I'm surprised that it doesn't seem to be as popular..

I had a really old Intrusion PDS that I pulled the HDD out of, and loaded up Hardy on it.  Before returning it to the system, I configured a serial console port.  After returning the HDD to the box and hooking up to the console, I fiddled with the 3 onboard 10/100 ethernets, so that eth0 and eth1 are hooked up to the tap, bonded together using the bonding module, so that snort can see full-duplex traffic, with eth2 used to connect back to the internal network for logging, etc.  Check out the diagrams attached for the tap construction as well as the deployment scenario..

My /etc/network/interfaces looks like this:

```
auto bond0
iface bond0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  down ifconfig $IFACE down
  post-up ifenslave bond0 eth0 eth1
  pre-down ifenslave -d bond0 eth0 eth1

auto eth2
iface eth2 inet static
  address x.y.z.100
  netmask 255.255.255.0
  gateway x.y.z.1
```

Of course, snort is sniffing on bond0.  Logging is done to a mysql db on an internal server on the x.y.z.0/24 network, which is running BASE to put a somewhat prettier face on things..

Regarding the construction of the tap, the Snort docs have a nice bit on the [wiring diagram for a passive tap]("http://www.snort.org/docs/tap/"), which is where that wiring diagram came from.  I grabbed a 14 cu inch electric box (blue plastic type) from home depot (get the "old work" kind and remove the anchor flaps), and 4 Cat 5e jacks (2 white colored, 2 blue colored).  I used the white jacks for the "Host" jacks, and the blue ones for the "Tap" jacks, as shown in the diagram.

---

### Post by caseinpoint on 2009-05-05
@bodhi.zazen 

I changed the default username to idsuser and now I'm having problems with line 85 of the startup script that reads:

```
SNORT='/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort -D'
```

I know the problem is now with my group because I've changed the username.  How do I check for the proper group name? I've attempted the following with no luck:

[LIST=1]
[*]root
[*]idsuser
[*]snort
[/LIST]

I know this has got to be something simple.  Is it looking to use the username/group from mysql or from the host itself?  Please help =)

---

### Post by caseinpoint on 2009-05-05
I'm having the same problem you are.  Did you ever get this resolved?

---

### Post by bodhi.zazen on 2009-05-05
The syntax is -u user -g group

both user and group must exist on the system, so from your post I am guessing :

```
SNORT='/usr/local/bin/snort -c /etc/snort/snort.conf -u **idsuser** -g **idsuser** -D'
```

Edit the script to make those changes.

---

### Post by MarnickV on 2009-05-06
@bodhi.zazen

Do you have any idea how I can fix my [previously mentioned problem](http://ubuntuforums.org/showpost.php?p=7157967&postcount=142)?

I guess the problem still is that that the /var/run/snort_eth*.pid file gets made by root, but snort tries to delete it, thus failing because of permissions. Is there any way I can let the snort user make the pid file, or another workaround?

Thanks

---

### Post by bodhi.zazen on 2009-05-06
Snort sometimes leaves a stale file if it terminates abnormally. Simply stop snort and delete the file. 

It should work again.

---

### Post by MarnickV on 2009-05-07
bodhi.zazen: I've tried that, but still the same error + /var/run//snort_eth1.pid could not be deleted (root:root while snort runs as 'snort').

I start snort with: sudo /etc/init.d/snort start (your startup script). Maybe it's because of the "sudo" that root makes the file and then delegates the rest to snort? I'm just thinking wild here..

---

### Post by pheonixace_7 on 2009-06-11
For starters I would like to thank you, Bodhi for all of your help so far in my other thread. After carefully reading through your guide in this thread I have gotten much further. I still have a couple of problems though.

BASE will not pull any of the sensors (like many other people here), but I feel like my problem may be on the snort side. If I try and run "/etc/init.d/snort start" I get "Snort failed to start". But if I run "snort -v" it starts up just fine. I have a feeling there is some piece of the puzzle i'm missing, but i'm not sure what diagnostics I can do to find it. 

You mentioned:
P> ossibilities are :

1. mysql is not set up properly.

2. snort lost it's connection with mysql. To test this, clear the database in base (from the admin panel) even though it reads "0", then restart snort. You should now see 1 sensor in base.

3. Base is not working, ie base is not connecting to the mysql database.
I'm reasonably sure mysql is setup correctly due to the amount of time I spent quintuple checking everything. I tried clearing the db in BASE and restarting it, but it still did not find a sensor. Number three is possible and I'm not entirely sure how to test that. 

I still just can't get past the /etc/init.d/snort commands though. I copied over your script and did not make any changes (the default eth0 is fine and I didn't bother with a whitelist until i can at least get it up and running), but still cannot get it to launch. Anybody have any ideas? If you need any more info please just let me know.

---

### Post by bodhi.zazen on 2009-06-11
From your post I am guessing snort is not properly configured.

How did you install snort ?

/etc/init.d/snort would be a start script to start snort (obviously), but that script is part of the ubuntu package and not part of snort . So if you installed snort from source you can not use that init script to start snort.

So, if you installed snort from source, start it manually :

```
/usr/local/bin/snort -c /etc/snort/snort.conf
```If snort now starts, go to base and you will see it register as a senor.

If that works go the next step :

```
/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort -D
```With a cron job to restart it every 6-12 hours.

If that fails, post the error message.

---

### Post by pheonixace_7 on 2009-06-11
I installed word for word from the guide at the beginning of this thread with one exception. I installed snort-2.8.4.1 instead of the version listed. I was using the /etc/init.d/snort commands because I had installed your script.It finally dawned on me that installing a different version probably made that script invalid. 

I did however try and start it manually as you recommended. It did not work, but here are the errors:
```
Tagged Packet Limit: 256
Loading dynamic engine /usr/local/lib/snort_dynamicengine/libsf_engine.so... done
Loading dynamic detection library /usr/local/lib/snort_dynamicrules/bad-traffic.so... ERROR: Failed to load /usr/local/lib/snort_dynamicrules/bad-traffic.so: /usr/local/lib/snort_dynamicrules/bad-traffic.so: cannot open shared object file: No such file or directory
Fatal Error, Quitting..
sbevill7@sbevill7-desktop:~$
```

The more I think about it the more I wonder if I shouldn't try and find the exact version you had in your guide. I know some other people mentioned they were using 2.8.4.1, but they also mentioned they were having problems too :-/.

Edit: I am actually running this on two different networks (one at work and one at home). I'm doing this mostly just so I can really learn it, but it is providing a good practice in action consistency. They are both acting in the same manner.

---

### Post by Cyked on 2009-06-17
So I'm stuck on setting this up, and not sure what I am doing wrong...

When I get to the part below, this is where I get hung up.... Is this correct, to copy the txt file to **/etc/init.d/snort,** since its not really a dir?

> Write a script to start snort :

The only "problem" with installing snort from source is that we now need a script to start snort. The other issue is that if there are no alerts, snort will lose it's connection with the mysql database.

To solve this, I wrote a script to start / restart snort.

The script is attached to this post and is called "ubuntu.snort.init.txt"

Copy this file to your computer and copy/move it to /etc/init.d/snort

Now lets look at the code. You need to look at two lines.

   1. The first is your interface. The default is eth0. If you wish to use snort on an alternate interface, such as eth1, you will need to edit the line IFACE="eth0" and change "eth0" to "eth1"
          * Note : Snort will not work with wireless interfaces, you need to use airsnort instead.
   2. The second option is to whitelist ip addresses. I advise you do this with caution, but you *may* wish to white IP addresses such as your router and your public ip address.

      To white list an IP , add it to the line WHITELIST='' (note that is two single quotes, ' ' and not a double quote " ) , one ip at a time, separated by a space, like this :



At any rate, I followed the instructions through to the part where you do a restart on snort and i get an error snort failed to start.

Please let me know what I need to post or where I should be looking for specific errors.  Maybe its unable to use the rules file when its starting?

---

### Post by bodhi.zazen on 2009-06-17
You need to post at least your snort error.

The command to start snort would help as well.

---

### Post by Cyked on 2009-06-17
> **bodhi.zazen said:**
> You need to post at least your snort error.

The command to start snort would help as well.


The error I get is just snort failed to start.  Is there an error log in /var/log/snort I'm assuming.  Sorry, I'm a little slow this morning, haven't had enough coffee.  Perhaps this may have something to do with it.  When I went to go into the /log/snort directory I'm getting permission denied.

I'm starting snort with sudo /etc/init.d/snort restart

---

### Post by bodhi.zazen on 2009-06-17
did you compile from source or install from the ubutnu repositories ?

where did you get the init.d script ?

open the init.d script with any editor, find the line that actually starts snort, start snort from the command line

```
sudo /usr/local/bin/snort -c /etc/snort/snort.conf
```

---

### Post by Cyked on 2009-06-17
> **bodhi.zazen said:**
> did you compile from source or install from the ubutnu repositories ?

where did you get the init.d script ?

open the init.d script with any editor, find the line that actually starts snort, start snort from the command line

```
sudo /usr/local/bin/snort -c /etc/snort/snort.conf
```

From source, which was fine from what I could tell.

the init.d script?  Are you referring to the .txt file on the first page?  

I have this line in the .txt file.... 
```
# Declair variables
SNORT='/usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort -D'

```

---

### Post by bodhi.zazen on 2009-06-17
Open a terminal.

Enter that snort command :

```
sudo [FONT=monospace]/[/FONT]usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort
```

post any error messages.

---

### Post by Cyked on 2009-06-17
> **bodhi.zazen said:**
> Open a terminal.

Enter that snort command :

```
sudo [FONT=monospace]/[/FONT]usr/local/bin/snort -c /etc/snort/snort.conf -u snort -g snort
```

post any error messages.

Perhaps I screwed this part up:

```
cd /usr/src/snort-2.8.3
mkdir -p /etc/snort/rules /var/log/snort
chown -R root.snort /var/log/snort
chmod -R 770 /var/log/snort
cp etc/* /etc/snort/
cp rules/* /etc/snort/rules
```

Because I am getting this.....


```
Running in IDS mode

        --== Initializing Snort ==--
Initializing Output Plugins!
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file /etc/snort/snort.conf
PortVar 'HTTP_PORTS' defined :  [ 80 ]
PortVar 'SHELLCODE_PORTS' defined :  [ 0:79 81:65535 ]
PortVar 'ORACLE_PORTS' defined :  [ 1521 ]
Frag3 global config:
    Max frags: 65536
    Fragment memory cap: 4194304 bytes
Frag3 engine config:
    Target-based policy: FIRST
    Fragment timeout: 60 seconds
    Fragment min_ttl:   1
    Fragment ttl_limit (not used): 5
    Fragment Problems: 1
Stream5 global config:
    Track TCP sessions: ACTIVE
    Max TCP sessions: 8192
    Memcap (for reassembly packet storage): 8388608
    Track UDP sessions: INACTIVE
    Track ICMP sessions: INACTIVE
    Log info if session memory consumption exceeds 1048576
Stream5 TCP Policy config:
    Reassembly Policy: FIRST
    Timeout: 30 seconds
    Min ttl:  1
    Maximum number of bytes to queue per session: 1048576
    Maximum number of segs to queue per session: 2621
    Options:
        Static Flushpoint Sizes: YES
    Reassembly Ports:
      21 client (Footprint)
      23 client (Footprint)
      25 client (Footprint)
      42 client (Footprint)
      53 client (Footprint)
      80 client (Footprint)
      110 client (Footprint)
      111 client (Footprint)
      135 client (Footprint)
      136 client (Footprint)
      137 client (Footprint)
      139 client (Footprint)
      143 client (Footprint)
      445 client (Footprint)
      513 client (Footprint)
      514 client (Footprint)
      1433 client (Footprint)
      1521 client (Footprint)
      2401 client (Footprint)
      3306 client (Footprint)
HttpInspect Config:
    GLOBAL CONFIG
      Max Pipeline Requests:    0
      Inspection Type:          STATELESS
      Detect Proxy Usage:       NO
      IIS Unicode Map Filename: /etc/snort/unicode.map
      IIS Unicode Map Codepage: 1252
    DEFAULT SERVER CONFIG:
      Server profile: All
      Ports: 80 8080 8180
      Server Flow Depth: 300
      Client Flow Depth: 300
      Max Chunk Length: 500000
      Max Header Field Length: 0
      Max Number Header Fields: 0
      Inspect Pipeline Requests: YES
      URI Discovery Strict Mode: NO
      Allow Proxy Usage: NO
      Disable Alerting: NO
      Oversize Dir Length: 500
      Only inspect URI: NO
      Normalize HTTP Headers: NO
      Normalize HTTP Cookies: NO
      Ascii: YES alert: NO
      Double Decoding: YES alert: YES
      %U Encoding: YES alert: YES
      Bare Byte: YES alert: YES
      Base36: OFF
      UTF 8: OFF
      IIS Unicode: YES alert: YES
      Multiple Slash: YES alert: NO
      IIS Backslash: YES alert: NO
      Directory Traversal: YES alert: NO
      Web Root Traversal: YES alert: YES
      Apache WhiteSpace: YES alert: NO
      IIS Delimiter: YES alert: NO
      IIS Unicode Map: GLOBAL IIS UNICODE MAP CONFIG
      Non-RFC Compliant Characters: NONE
      Whitespace Characters: 0x09 0x0b 0x0c 0x0d
rpc_decode arguments:
    Ports to decode RPC on: 111 32771
    alert_fragments: INACTIVE
    alert_large_fragments: ACTIVE
    alert_incomplete: ACTIVE
    alert_multiple_requests: ACTIVE
Portscan Detection Config:
    Detect Protocols:  TCP UDP ICMP IP
    Detect Scan Type:  portscan portsweep decoy_portscan distributed_portscan
    Sensitivity Level: Low
    Memcap (in bytes): 10000000
    Number of Nodes:   36900

[B]ERROR: Unable to open rules file: /etc/snort/rules/local.rules or /etc/snort//et                                                                             c/snort/rules/local.rules
Fatal Error, Quitting.[/B].

```


Not sure why everything ended up in /etc/snort.  its running now after moving the files to the right place... will see what happens.  Right now its sitting at "Not using PCAP_FRAMES"

---

### Post by Cyked on 2009-06-17
I finished installing base.  I can get to localhost/base and go through the setup.  when I click on continue at step 5 I get this error in red text:

> Can't write base_conf.php file!
Please copy the below info into your base_conf.php file

And then lists what appears to be the same info in base_conf.php.dist

If I do create the base_conf.php myself I get this error when trying to get to localhost/base

> Parse error: syntax error, unexpected ';' in /var/www/base/base_conf.php on line 37

Here is the first part of what is currently in base_conf.php

```
<?php
/*******************************************************************************
** Basic Analysis and Security Engine (BASE)
** Copyright (C) 2004 BASE Project Team
** Copyright (C) 2000 Carnegie Mellon University
**
** (see the file "base_main.php" for license details)
**
** Project Leads: Kevin Johnson <kjohnson@secureideas.net>
**                Sean Muller <samwise_diver@users.sourceforge.net>
** Built upon work by Roman Danyliw <rdd@cert.org>, <roman@danyliw.com>
**
** Purpose: Vanilla Config file
********************************************************************************
** Authors:
********************************************************************************
** Kevin Johnson <kjohnson@secureideas.net
**
********************************************************************************
*/
    session_start();
    $BASE_VERSION = '1.3.9 (anne)';

    /*
     Set the below to the language you would like people to use while viewing
     your install of BASE.
    */
    $BASE_Language = '';

    /*
     Set the $Use_Auth_System variable to 1 if you would like to force users to
     authenticate to use the system.  Only turn this off if the system is not
     accessible to the public or the network at large.  i.e. a home user testing it
     out!
    */

    $Use_Auth_System = ;

    /*
     Set the below to 0 to remove the links from the display of alerts.
    */
    $BASE_display_sig_links = 1;

    /*
     Set the base_urlpath to the url location that is the root of your BASE install.
     This must be set for BASE to function! Do not include a trailing slash!
     But also put the preceding slash. e.g. Your URL is http://127.0.0.1/base
     set this to /base

     */
    $BASE_urlpath = '/base';
```

---

### Post by savedlatin23 on 2009-06-22
Let me first say thank you for the great tutorial.  I am hoping some one can help me with a problem I am having installing the ossec wui. My problem occurs when i try to ```
cd /var/www

``` I get a "No such file or directory" error.  Any suggestions would be deeply appreciated to this ubuntu newbie. 

Merci

---

### Post by Cyked on 2009-06-22
> **savedlatin23 said:**
> Let me first say thank you for the great tutorial.  I am hoping some one can help me with a problem I am having installing the ossec wui. My problem occurs when i try to ```
cd /var/www

``` I get a "No such file or directory" error.  Any suggestions would be deeply appreciated to this ubuntu newbie. 

Merci

Sounds like you do not have apache installed.  Try this. 

```
cd /etc/init.d
```

and then 

```
ls
```

See if you have apache or apache2 in the list.

---

### Post by savedlatin23 on 2009-06-22
Thank you I am missing apache, now when i'm having trouble installing that.  Before I get told that google is my friend I've tried: ```
sudo apt-get install apache2
``` and I get ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2

```Once again all help is deeply appreciated.

Edit:  Google was my friend [http://ubuntuforums.org/showpost.php?p=3744949&postcouhttp://ubuntuforums.org/showpost.php?p=3744949&postcount=2nt=2](http://ubuntuforums.org/showpost.php?p=3744949&postcouhttp://ubuntuforums.org/showpost.php?p=3744949&postcount=2nt=2)

---

### Post by Cyked on 2009-06-22
Can you post the contents of your /etc/apt/sources.list?

---

### Post by savedlatin23 on 2009-06-22
I would If I could, I was getting system errors and couldn't connect to [http://myip/ossec](http://myip/ossec) so I just barely started from scratch.  Hopefully third time is the charm.

---

### Post by Cyked on 2009-06-22
bodhi.zazen, any insite regarding what I have posted with the issue I am having?

Thanks

---

### Post by bodhi.zazen on 2009-06-22
Is your version of apache trying to download php instead of running it as a script ?

What version of base ?

---

### Post by Cyked on 2009-06-23
Not sure what you are referring to initially, or what to check.  Sorry.

I'm using base-1.3.9.

---

### Post by bodhi.zazen on 2009-06-23
When you go to your base directory with your browser

[http://localhost/base](http://localhost/base)

does your browser try to download the file ? Or does it display a page with an error message ?

If the browser can not write the file, that is a permissions problem.

Change the ownership and permissions of the base directory so www-data can rw the files.

sudo chown -R www-data.www-data /var/www/base
sudo chmod -R 660 /var/www/base

---

### Post by Cyked on 2009-06-23
Back on the previous page.....

I was getting 

```
Parse error: syntax error, unexpected ';' in /var/www/base/base_conf.php on line 37 
```


Now I am getting 403 forbidden afer changing permissions when access /base.  Both these errors are from accessing externally with IP/base.

If I use links via putty and go to /base I get the same thing.

---

### Post by Cyked on 2009-06-25
This is what I am seeing in access.log

```
[25/Jun/2009:11:17:44 -0700] "GET /base HTTP/1.1" 403 268 "-" "Mozilla/5.0
```

---

### Post by bodhi.zazen on 2009-06-25
Where did you put base ?

/var/www/???

---

### Post by Cyked on 2009-06-25
/var/www/base

---

### Post by bodhi.zazen on 2009-06-25
And what then are the permissions of /base ?

---

### Post by Cyked on 2009-06-25
You asked me to do this previously....

```
sudo chown -R www-data.www-data /var/www/base
sudo chmod -R 660 /var/www/base
```


This what you are looking to find....?
```
drw-rw---- 13 www-data www-data 4096 2009-06-17 14:05 base
```

---

### Post by bodhi.zazen on 2009-06-25
The directory and files in it should be owned by www-data

The directory itself needs permissions of 770 and files in the directory permissions of 660.

---

### Post by Cyked on 2009-06-25
I don't think file permissions are the issue.  I suspect if the permissions are correct I will still get the below error I reported earlier....

```
Parse error: syntax error, unexpected ';' in /var/www/base/base_conf.php on line 37
```


This is the original line
 ```
$Use_Auth_System = ;
```

If I change the value to 1 I get this...

---

### Post by bodhi.zazen on 2009-06-25
I do not know what is causing those errors in base.

---

### Post by subhaikav on 2009-06-26
It is a great post.Thanks for sharing.

---

### Post by Cyked on 2009-06-26
So I'm starting over and have a dumb question.  I've gone through the removed a lot of things and am wondering, at what point is snort installed, now that I have started over?  More specifically when is /etc/init.d/snort created)?  I'm at that point where I am supposed to cp the .txt file there and I don't have it....  after going through everything again and reading all output to make sure I'm not missing errors.  Not sure why /etc/init.d/snort isn't there.  I'm also kinda confused on copying the .txt file there when its not a directory.

I uninstalled snort and a lot of other things when starting over....

---

### Post by Cyked on 2009-06-30
Any thoughts?

---

### Post by bodhi.zazen on 2009-06-30
It depends on how you install snort. If you install snort form source there is no init.d script included and you need to either write your own or use my script or write your own script.

If you install snort from the Ubuntu repositories an init script is included (and there is some additiona automation as well).

You can not use the snort init script from the repositories with snort installed from source. You would need to modify it / re-write it.

---

### Post by Cyked on 2009-06-30
Is it obvious where I went wrong?  I installed from source and followed the howto.  I managed to get this part right the first time.  Don't know what I missed the second time around.

---

### Post by Cyked on 2009-07-02
So something new occurred.  I don't know for sure what got me to this point, but my syslog blew up the other day with mysl errors (see below).

Obviously I'm in over my head, and I think having a better understanding of how logging works in general, how I can tweak it, etc. would go a long way.  I've been toying with iptables logging, where things go, adding an entry to syslog.conf to have iptables logs go there.  So I guess I will see where I ended up.

```
Jul  1 10:54:54 tux snort[19444]: database: Problem inserting a new signature '(portscan) Open Port': INSERT INTO signature (sig_name,sig_priority,sig_sid,sig_gid) VALUES ('(portscan) Open Port',3,27,122)
Jul  1 10:54:54 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=INSERT INTO event (sid,cid,signature,timestamp) VALUES (2, 46196, 0, '2009-07-01 10:54:54')
Jul  1 10:54:54 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=ROLLBACK
Jul  1 10:54:54 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=BEGIN
Jul  1 10:54:54 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jul  1 10:54:54 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=INSERT INTO signature (sig_name,sig_priority,sig_sid,sig_gid) VALUES ('(portscan) Open Port',3,27,122)
Jul  1 10:54:54 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jul  1 10:54:54 tux snort[19444]: database: Problem inserting a new signature '(portscan) Open Port': INSERT INTO signature (sig_name,sig_priority,sig_sid,sig_gid) VALUES ('(portscan) Open Port',3,27,122)
Jul  1 10:54:54 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=INSERT INTO event (sid,cid,signature,timestamp) VALUES (2, 46197, 0, '2009-07-01 10:54:54')
Jul  1 10:54:54 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=ROLLBACK
Jul  1 10:54:57 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=BEGIN
Jul  1 10:54:57 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jul  1 10:54:57 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=INSERT INTO signature (sig_name,sig_priority,sig_sid,sig_gid) VALUES ('(portscan) Open Port',3,27,122)
Jul  1 10:54:57 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
Jul  1 10:54:57 tux snort[19444]: database: Problem inserting a new signature '(portscan) Open Port': INSERT INTO signature (sig_name,sig_priority,sig_sid,sig_gid) VALUES ('(portscan) Open Port',3,27,122)
Jul  1 10:54:57 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=INSERT INTO event (sid,cid,signature,timestamp) VALUES (2, 46198, 0, '2009-07-01 10:54:57')
Jul  1 10:54:57 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=ROLLBACK
Jul  1 10:54:58 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2) SQL=BEGIN
Jul  1 10:54:58 tux snort[19444]: database: mysql_error: Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)

```

So I ended up stopping mysql and snort.

---

### Post by iTrascurato on 2009-07-07
Hi,

I'd like to add in a few things.

a)  In your configuration of snort, you have a typo.  It should be $HOME_NET not !$HOME_NET, as it is lower in the configuration file multiple times.

b)  I have a question:  Why is my Firefox trying to download a file instead of going to the page that should be displayed?  I went through the snort setup just fine from my laptop, however afterwards the computer I set snort up on is still not going to /base correctly.   EDIT: Now I can't access /base from any machine.  What is wrong?

---

### Post by S4L4Z on 2009-07-08
Hello there,

i have problem in this command. the 'signature' is not exist. do i have to create it?
```
root@salax-laptop:/var/www/base# cp -R /usr/src/snort-2.8.4.1/doc/signatures .
cp: cannot stat `/usr/src/snort-2.8.4.1/doc/signatures': No such file or directory

```

---

### Post by iTrascurato on 2009-07-08
> **S4L4Z said:**
> Hello there,

i have problem in this command. the 'signature' is not exist. do i have to create it?
```
root@salax-laptop:/var/www/base# cp -R /usr/src/snort-2.8.4.1/doc/signatures .
cp: cannot stat `/usr/src/snort-2.8.4.1/doc/signatures': No such file or directory

```

Same issue here, had to leave that part out.

---

### Post by Cyked on 2009-07-08
So I've been playing around with this, and have no issues, until again, I get to the snort script, making it bootable, and then restarting... I'm still getting this.

 ```
/etc/init.d/snort restart
/etc/init.d/snort: line 39: syntax error near unexpected token `then'
/etc/init.d/snort: line 39: `  D="z" fi uid=$(/usr/bin/id -u) if [ ! "$uid" = "0" ];then'

```

Any ideas?

---

### Post by zahidraf on 2009-07-10
very useful discussion .and helpful as well.

---

### Post by glbrtsoms on 2009-07-17
This gives us new idea thanks for sharing this post I've something new here..

---

### Post by grayn0de on 2009-07-17
> **Cyked said:**
> So I've been playing around with this, and have no issues, until again, I get to the snort script, making it bootable, and then restarting... I'm still getting this.

 ```
/etc/init.d/snort restart
/etc/init.d/snort: line 39: syntax error near unexpected token `then'
/etc/init.d/snort: line 39: `  D="z" fi uid=$(/usr/bin/id -u) if [ ! "$uid" = "0" ];then'

```Any ideas?

Just a shot in the dark here, but have you tried moving 'then' to another line and removing the ';'?

Semicolons act as a terminator, thus the if statement ends after the conditions.

---

### Post by Cyked on 2009-07-19
> **grayn0de said:**
> Just a shot in the dark here, but have you tried moving 'then' to another line and removing the ';'?

Semicolons act as a terminator, thus the if statement ends after the conditions.

I'll play around some more with the code.  I had went through it when I posted here.  I had moved around some ; and {} I belive in several places to get rid of errors, only to get to the last few lines in the file and get errors I have no clue....  Like I said, I'll go through it again and post my results.

---

### Post by Cyked on 2009-07-21
I just get this...

```
/etc/init.d/snort: line 40: syntax error near unexpected token `then'
/etc/init.d/snort: line 40: `  D="z#" fi uid=$(/usr/bin/id -u) if [ ! "$uid" = "0" ];then'

```

When I do the same on line 40 I get...

```
/etc/init.d/snort: line 41: syntax error near unexpected token `then'
/etc/init.d/snort: line 41: `then'

```




When I get all the way end after "fixing" the above (probably incorrectly), I get this...

```
/etc/init.d/snort: line 156: syntax error near unexpected token `exit'
/etc/init.d/snort: line 156: `    ;; esac exit 0'

```

---

### Post by reds098 on 2009-08-04
Thanx buddy,
Very lucid explanation of the steps to secure with snort.
good job done.........

---

### Post by abrrymnvette on 2009-08-26
This is a great tutorial. I'm going to have to install this tomorrow on one of my VM's. I work with Snort on a daily basis and just learning to write snort rules now. It's kinda fun and pretty simple once you get past the fear of doing it. Although we're on a later release than the free/public version. Snort is an amazing IDS tool.

---

### Post by abrrymnvette on 2009-08-28
I have an issue. I'm running Ubuntu 9.04 in a VM in Citrix Xen. I'm trying to run the command 

>  mysql> grant all privileges on snort.* to 'snort'@'localhost' identified by 'snort_password';


and I keep getting the following error. 

> ERROR 1064  (42000): You have an error in your SQL syntax; check the manual that corresponds to your MYSQL server version for the right syntax to use near '?snort'@'localhost' identified by 'snort_password' at line 1

I'm thinking it has to do with the fact that I have to hit ' twice before it'll show up on the screen in the VM terminal? I initially didn't set a password when I did the install of mysql, so I thought that was the reason. So, I then used the 
mysqladmin -u root password NEWPASSWORD

command to change the password. 

Any suggestions?

---

### Post by unutbu on 2009-08-28
Are you by chance, cutting and pasting? The question mark in the error message
may be indicating there is a hidden control character sneaking into the command:
> 
use near '[COLOR="Red"]?[/COLOR]snort'@'localhost' 

Perhaps try typing the command manually. Otherwise, the syntax is correct...

---

### Post by abrrymnvette on 2009-08-28
> **unutbu said:**
> Are you by chance, cutting and pasting? The question mark in the error message
may be indicating there is a hidden control character sneaking into the command:


Perhaps try typing the command manually. Otherwise, the syntax is correct...


That's what I thought too, but I'm not cutting pasting. I'm figuring it has something to do with the fact that it's a VM in Citrix and I'm using the Citrix console.

Here's a screenshot of my screen.

---

### Post by abrrymnvette on 2009-08-28
I got it. It dawned on me to open up openoffice write and try the ' in that. It works by only hitting it once. So, I typed the command in write then copy/paste and it worked. So, it's something to do with my terminal not taking the ' on the first time. I have to hit it twice for some reason.


Now I'm having another issue. Seems to be the user doesn't have permissions. Didn't I just grant him all the permissions?

---

### Post by unutbu on 2009-08-28
It might have to do with not running
```

mysql> flush privileges;

```

Maybe go back into mysql
```

sudo mysql -u root -p
```
and running```

mysql> flush privileges;
mysql> quit;

```

Then try the ```

mysql -D snort -u snort -p < ...
```
command again.

If that does not work, try running 
```
sudo /etc/init.d/mysql restart
```

---

### Post by abrrymnvette on 2009-08-28
no dice. If I use the user of root instead of -u snort, it works and says 0 rows affected.

---

### Post by unutbu on 2009-08-28
Try

```
% mysql -u root -p
mysql> use mysql
mysql> select user,host,password from user where user='snort';

```
Do you see something like this?
```
+--------+-----------+-------------------------------------------+
| user   | host      | password                                  |
+--------+-----------+-------------------------------------------+
| snort  | localhost | *XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 
+--------+-----------+-------------------------------------------+

```

---

### Post by abrrymnvette on 2009-08-28
> **unutbu said:**
> Try

```
% mysql -u root -p
mysql> use mysql
mysql> select user,host,password from user where user='snort';

```Do you see something like this?
```
+--------+-----------+-------------------------------------------+
| user   | host      | password                                  |
+--------+-----------+-------------------------------------------+
| snort  | localhost | *XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX | 
+--------+-----------+-------------------------------------------+

```


Error 1146 (42S02): Table 'mysql.usr' doesn't exist

---

### Post by unutbu on 2009-08-28
Change usr to user.

```
select user,host,password from [COLOR="Red"]user[/COLOR] where user='snort';
```

---

### Post by abrrymnvette on 2009-08-28
> **unutbu said:**
> Change usr to user.

```
select user,host,password from [COLOR=Red]user[/COLOR] where user='snort';
```

Rebooted and the user showed up. But I still get the access denied for user 'snort'@'localhost'

---

### Post by unutbu on 2009-08-28
Okay, you have a snort user on localhost, and it has a password.
I'm guessing the saved password is not the intended password. Perhaps an
invisible control character slipped in there too? 

Try typing
```

grant all privileges on snort.* to 'snort'@'localhost' identified by 'snort_password'; 
```

in gedit, rather than openoffice. Maybe it is just my superstition, but I think gedit is more of a plain text editor, while openoffice is more of a "fancy" text editor. 

When you copy and paste into the gnome-terminal, make sure your quotation marks look like 
the one circled in green, rather than the one in red.

---

### Post by abrrymnvette on 2009-08-28
> **unutbu said:**
> Okay, you have a snort user on localhost, and it has a password.
I'm guessing the saved password is not the intended password. Perhaps an
invisible control character slipped in there too? 

Try typing
```

grant all privileges on snort.* to 'snort'@'localhost' identified by 'snort_password'; 
```in gedit, rather than openoffice. Maybe it is just my superstition, but I think gedit is more of a plain text editor, while openoffice is more of a "fancy" text editor. 

When you copy and paste into the gnome-terminal, make sure your quotation marks look like 
the one circled in green, rather than the one in red.


That's actually what I did this time. But, I "think" I may have gotten it. I just used a different user instead of snort. So, wherever else it says snort, I used the other user name. I've got snort running according to ps and am logged into Base. Now it's time to test.

---

### Post by bodhi.zazen on 2009-08-28
Thank you [unutbu]("http://ubuntuforums.org/member.php?u=518895")

---

### Post by abrrymnvette on 2009-08-31
So, I have snort running somewhat. When I do a "ps -wef | grep 'snort' " I get the snort process, but it increments every second, like it's starting and immediately dying and restarting. But when I look at /var/log/messages or syslog there are no errors like snort is dying. Am I looking in the wrong spot?

---

### Post by -_- Joseph -_- on 2009-09-09
Thanks alot this was a really helpful thread. Keep up the good work :)

---

### Post by Aetixintro on 2009-09-14
Excuse me for interrupting, but I have just been having issues with ./configure of snort-2.8.4. To this I have made the blunder to report it as a bug in the make project. Now I've just running make again and it seems to have run smoothly. I've been having great use of this thread! Thanks a lot to the author. Warning: There may be issues in compiling snort!

---

### Post by plutonium45 on 2009-10-06
very good tutorial :)

Thanks !

---

### Post by JohnWesleyMethodist on 2009-10-06
When I punch these two commands in (installing Ossec-Hids versions 2.2 and 0.3 GUI) on Ubuntu Jaunty, I get error messages:

```

chown -R www-data.www-data ossec
usermod -G ossec -a www-data

```

 How come?

 Also with this tutorial, for Ossec the command to add an agent is missing, so when you start Ossec the first time, it tries to start the 0:0:0:0 80 ip address which doesn't work. So I found additional instructions on the Ossec-Hids website which I can't get to work either. That question is in another thread of mine here:

 [http://ubuntuforums.org/showthread.php?t=1269022](http://ubuntuforums.org/showthread.php?t=1269022)

 I also get this message when I try to use the Ossec-GUI command which is my ip address/ossec:

```

 Not Found

The requested URL /ossec was not found on this server.
Apache/2.2.11 (Ubuntu) Server at 172.18.158.10 Port 80

```

---

### Post by abrrymnvette on 2009-10-08
I'm using this tutorial but I'm installing Snort 2.8.5, the latest version. Newer snort versions use dynamic engines and dynamic preprocessors. So, this is what I've done so far that I think might want to be updated in the tut. 

1. Created a symlink in /usr/local/lib with the command **ln -s /usr/src/snort-2.8.5/so_rules/precompiled/Ubuntu-6.01.1/i386/2.8.4.1 snort_dynamicrules**

 
This symlinks the .so rules to the snort_dynamicrules that snort looks in when it starts up. 

Then I was getting and error when I tried start snort of: **FATAL ERROR: /etc/snort/rules/exploit.rules(23): Couldn't resolve hostname HOME_NET **

So, I looked in the snort.conf file and saw I had my EXTERNAL_NET set at
var EXTERNAL_NET !HOME_NET

When it should be set to var EXTERNAL_NET !**$**HOME_NET


Then when I tried to start snort, it actually started. 


All the error logging is done to /var/log/syslog for those who don't know. 

I'm going to start testing it now with 2.8.5 and see what I can find. But, I have to get back to my real job of testing Snort 2.8.5 on our equipment. :)

---

### Post by eXPeri3nc3 on 2009-11-10
Hi, I'm new to this.

I am confused on where you download this base file to.

```
cd
wget http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz
```

Is it to /var/www?

As I get an error when I tried to do this command at /var/www:
tar zvxf ~/base-1.3.9.tar.gz

Saying that:

```
root@alex-laptop:/etc/init.d/snort# cd /var/www
root@alex-laptop:/var/www# ls
base-1.3.9.tar.gz  index.html
root@alex-laptop:/var/www# tar zvxf ~/base-1.3.9.tar.gz
tar: /root/base-1.3.9.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@alex-laptop:/var/www# 

```

Anyone please help? Thanks. Clueless.

---

### Post by abrrymnvette on 2009-11-10
> **eXPeri3nc3 said:**
> Hi, I'm new to this.

I am confused on where you download this base file to.

```
cd
wget http://easynews.dl.sourceforge.net/sourceforge/secureideas/base-1.3.9.tar.gz
```Is it to /var/www?

As I get an error when I tried to do this command at /var/www:
tar zvxf ~/base-1.3.9.tar.gz

Saying that:

```
root@alex-laptop:/etc/init.d/snort# cd /var/www
root@alex-laptop:/var/www# ls
base-1.3.9.tar.gz  index.html
root@alex-laptop:/var/www# tar zvxf ~/base-1.3.9.tar.gz
tar: /root/base-1.3.9.tar.gz: _[COLOR=Red]***Cannot open: No such file or directory***[/COLOR]_
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
root@alex-laptop:/var/www# 

```Anyone please help? Thanks. Clueless.


The error is telling you the exact problem. You are trying to untar it from the /root/  but it isn't there. You need to put the path to where the file is located. Leaving out the ~/ would do it, but I don't remember (without looking) where you want to untar it to.

---

### Post by eXPeri3nc3 on 2009-11-10
> **abrrymnvette said:**
> The error is telling you the exact problem. You are trying to untar it from the /root/  but it isn't there. You need to put the path to where the file is located. Leaving out the ~/ would do it, but I don't remember (without looking) where you want to untar it to.

Hi abrrymnvette,

I see. Then I shall assume that it should be extracted to /var/www and work on from there.

Thanks.

---

### Post by guimaster on 2009-11-20
> **bodhi.zazen said:**
> When the script is finished running, change ownership of the directory and add www-data to the ossec group 

```
cd /var/www
chown -R www-data.www-data ossec
usermod -G ossec -a www-data
```Restart apache

```
/etc/init.d/apache2 restart
```Log in at [http://your_ip_address/ossec](http://your_ip_address/ossec)

From the web interface you can see any changes to system files and alerts.

[Back to top]("http://ubuntuforums.org/showthread.php?t=919472")

 Hey all,

 Everything has worked perfectly in this tutorial up until this point:

```

root@xyzpc:/var/www# chown -R www-data.www-data ossec
chown: cannot access `ossec': No such file or directory

```I also type my ip addy/ossec and get this error:
[B]
Not Found[/B]
The requested URL /ossec was not found on this server.
  
I have apache installed. Is there anything I am missing?

 Thanks (running 8.04 Hardy)

---

### Post by cariboo on 2009-11-20
Do you have anything in /var/www called ossec?

---

### Post by BigCityCat on 2009-12-24
never mind

---

### Post by Hopping_Ubu on 2009-12-28
bodi.zazen,

This was a most enlightened post. I learned a lot about running Snort on Ubuntu. Your directions throughout this thread helped me with clearing my final hurdles.

---

### Post by bodhi.zazen on 2009-12-29
> **Hopping_Ubu said:**
> bodi.zazen,

This was a most enlightened post. I learned a lot about running Snort on Ubuntu. Your directions throughout this thread helped me with clearing my final hurdles.

Awesome , glad it worked for you.

---

### Post by oceania68 on 2010-01-03
Hey Bodhi

Ok i am not the best cow in the paddock but I could not get this working on KK (Ubuntu 9:10) I am not that fluent and I was following the instructions.. but for some reason I kept getting "Can't access mysql" blah blah blah...

So instead of going moo I decided to remove it and wait for someone with better knowledge to get me step by step guide... tho I found your instructions quiet easy, I just didnt understand Y or what was happening.. Cheers Bodhi... and thanks for the instructions...



o.

---

### Post by bodhi.zazen on 2010-01-04
> **oceania68 said:**
> Hey Bodhi

Ok i am not the best cow in the paddock but I could not get this working on KK (Ubuntu 9:10) I am not that fluent and I was following the instructions.. but for some reason I kept getting "Can't access mysql" blah blah blah...

So instead of going moo I decided to remove it and wait for someone with better knowledge to get me step by step guide... tho I found your instructions quiet easy, I just didnt understand Y or what was happening.. Cheers Bodhi... and thanks for the instructions...



o.


Sorry 8it did not work out for you. Sounds as if you were unable to set up mysql.

---

### Post by mocha on 2010-01-05
This guide is a great reference, thanks.

I did not read though all 23 pages of posts to this thread, so I'm not sure if my question has been addressed.

I'm looking for something very simple to monitor connections to a few specific ports.  Snort seems very heavy for my purposes.  Is there some easier application(s) that can send messages to a log whenever network activity occurs on some user-specified ports?

I installed and tinkered with snort, but it just seems a bit overwhelming.  Is there a way to tell it I simply want a log entry when any type of connection is attempted or successful to ports 890, 45000, and 61289 (for example).  I don't want to log any of the other large ruleset packs that come with it.  Thanks.

---

### Post by Hackuin on 2010-01-05
> **mocha said:**
> This guide is a great reference, thanks.

I did not read though all 23 pages of posts to this thread, so I'm not sure if my question has been addressed.

I'm looking for something very simple to monitor connections to a few specific ports.  Snort seems very heavy for my purposes.  Is there some easier application(s) that can send messages to a log whenever network activity occurs on some user-specified ports?

I installed and tinkered with snort, but it just seems a bit overwhelming.  Is there a way to tell it I simply want a log entry when any type of connection is attempted or successful to ports 890, 45000, and 61289 (for example).  I don't want to log any of the other large ruleset packs that come with it.  Thanks.
I guess, you could use IPTables for that.

---

### Post by bodhi.zazen on 2010-01-05
> **mocha said:**
> This guide is a great reference, thanks.

I did not read though all 23 pages of posts to this thread, so I'm not sure if my question has been addressed.

I'm looking for something very simple to monitor connections to a few specific ports.  Snort seems very heavy for my purposes.  Is there some easier application(s) that can send messages to a log whenever network activity occurs on some user-specified ports?

I installed and tinkered with snort, but it just seems a bit overwhelming.  Is there a way to tell it I simply want a log entry when any type of connection is attempted or successful to ports 890, 45000, and 61289 (for example).  I don't want to log any of the other large ruleset packs that come with it.  Thanks.

Snort is about as simple as it gets. 

You can do what you are asking with ufw/GUFW/iptables , but then you are going to be looking through logs. And what will you look for ? simply blocked connections ? you can get this information with a portscanner. How are you going to recognize problematic traffic ?

Snort monitors network traffic and, using a set of rules, "alerts" you of worrisome traffic. This is in fact exactly what you want in NIDS.

If you wish to "lighten up", and not run base, you can look at barnyard.

---

### Post by running_rabbit07 on 2010-01-05
This is an awesome thread. I am prepping for a Network Security class that I am taking for the Spring semester and I am sure this thread will be helpful for researching the topic. My text for the class uses Unix in most of the examples, which will be helpful.

If I learn anything in my class not covered here, which is doubtful, I will let you know. I will also point my classmates in this direction, so they can take advantage of your expertise.

Thanks.:)

---

### Post by Hackuin on 2010-01-05
> **bodhi.zazen said:**
> Snort is about as simple as it gets. 

You can do what you are asking with ufw/GUFW/iptables , but then you are going to be looking through logs. And what will you look for ? simply blocked connections ? you can get this information with a portscanner. How are you going to recognize problematic traffic ?

Snort monitors network traffic and, using a set of rules, "alerts" you of worrisome traffic. This is in fact exactly what you want in NIDS.

If you wish to "lighten up", and not run base, you can look at barnyard.
Hello Bodhi.
I agree with you completely, and I guess, he just seems to view/log the attempted connections to specific ports [blocked/permitted/dropped], I am not sure why is he just up-to it? because I don't see much performance/somekind of issue with snort/ossec, and what he is looking for is obviously, easily done by OSSEC.
I totally agree firewalls will not be total replacement for IDS/IPS, but for certain scenarios, I did see "fwsnort" being employed.

@mocha, if interest you, you could take a look at simple "fwsnort" [ [http://cipherdyne.org/fwsnort/](http://cipherdyne.org/fwsnort/) ].

---

### Post by mocha on 2010-01-05
Thanks for the info.  I guess snort is what I really need now that I think about it, because just simply setting up iptables log only rules doesn't tell me what kind of traffic was occurring.

I guess my new question therefore is, how do you restrict snort to only monitor specifc ports?  When I had it installed it kept filling the alert log with messages about port 80 traffic for webpages I was viewing.  I also need to filter out anything to do with my lan IP.

---

### Post by bodhi.zazen on 2010-01-05
If you look at this post : [http://ubuntuforums.org/showpost.php?p=5786252&postcount=3](http://ubuntuforums.org/showpost.php?p=5786252&postcount=3)

you will see how to white list your ip address =)

you can use the script in that post or (easily) modify it.

---

### Post by oldmankit on 2010-01-06
> **bodhi.zazen said:**
> [SIZE=4]**Using ossec**[/SIZE] :

Once you log into the web interface you will have a number of tabs. 

_Main_ ~ This is where you will see alerts.

_Integrity checking_ ~ Will show you recent changes to system files.

[[IMG]http://bodhizazen.net/img/IDS/OSSEC_1_sm.JPG[/IMG]]("http://bodhizazen.net/img/IDS/OSSEC_1.JPG")


[SIZE=2]**Understanding and modifying rules**[/SIZE]

_Listing of rules_ (it is incomplete): [http://www.ossec.net/wiki/index.php/Rule](http://www.ossec.net/wiki/index.php/Rule)

_Modifying rules_ : [http://www.ossec.net/wiki/index.php/Know_How:Ignore_Rules](http://www.ossec.net/wiki/index.php/Know_How:Ignore_Rules) 

I did find this wiki page on integrating base + ossec, but I have not tried it.

ossec + base : [http://www.ossec.net/wiki/index.php/OSSEC_&_BASE](http://www.ossec.net/wiki/index.php/OSSEC_&_BASE)


[SIZE=2]**Example of ossec active response**[/SIZE] :

[Back to top]("http://ubuntuforums.org/showthread.php?t=919472")

[COLOR=green]# Start by pinging the server:[/COLOR]

root@hardy:~#ping 192.168.0.3
PING 192.168.1.3 (192.168.0.3) 56(84) bytes of data.
64 bytes from 192.168.0.3: icmp_seq=1 ttl=64 time=0.378 ms
64 bytes from 192.168.0.3: icmp_seq=2 ttl=64 time=0.377 ms
64 bytes from 192.168.0.3: icmp_seq=3 ttl=64 time=0.359 ms

--- 192.168.0.3 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2005ms
rtt min/avg/max/mdev = 0.359/0.371/0.378/0.018 ms

Portscan the server :
[COLOR=red]root@hardy:~#nmap -sS -sV -O -PI -PT 192.168.0.3[/COLOR]

[COLOR=red]Starting Nmap 4.53 ( [http://insecure.org]("http://insecure.org/") ) at 2008-09-11 17:27 MDT[/COLOR]

[COLOR=red]<-- Notice how Nmap hangs ? -->[/COLOR]

[COLOR=blue]# Now ping the server again[/COLOR]:

root@hardy:~#ping 192.168.0.3
PING 192.168.0.3 (192.168.0.3) 56(84) bytes of data.

**[SIZE=2][COLOR=blue]<-- Notice how your pings are blocked ? -->[/COLOR][/SIZE]**

--- 192.168.0.3 ping statistics ---
[COLOR=blue]4 packets transmitted, 0 received, 100% packet loss, time 2999ms[/COLOR]

Here's my situation: running a laptop in a university network littered with security problems.  Viruses fly around everywhere (one reason I switched from windows), and basically I want to feel secure using my email, internet banking, etc.  I don't want people putting root kits or trojans on this happy ubuntu installation.  I want to be safe from crackers trying to steal my information.

I think a very important step was to install no-script in firefox.  The other one is of course ensuring ufw or something is operating and denying everything! Finally, I have avg anti-virus installed, purely to clean flash drives which get infected when I use them in university computers, and to help friends clean theirs.  I'm in Thailand, and viruses and trojans are found at every step.

Do I actually need ossec?  I'm not running any servers. I'm not paranoid, I just want to be safe.

I got ossec up-and-running thanks to the great instructions, though I still can't get email notifications.  Perhaps that's a problem with my email provider.  Anyway, how do I actually test that it's working? As in the original post,  I tried ```
ping 192.168.0.3
```, but it was denied in the first place, without going to the next step.

If I actually need ossec (and if I don't, it would save me some time learning about it!), I would like to know what it is doing, what it is blocking, how to understand logs and alerts.

Many thanks.

---

### Post by bodhi.zazen on 2010-01-06
If you are not running any servers, you should be just fine without ossec.

---

### Post by oldmankit on 2010-01-06
> **bodhi.zazen said:**
> If you are not running any servers, you should be just fine without ossec.

Thank you Bodhi Zazen.  You have the uncommon gift of real clarity!

Do I need to bother with periodic checks such as rkhunter or chkrootkit?  Are they only for people running servers, too?

---

### Post by mocha on 2010-01-06
I think I have something setup incorrectly.

When I make an SSH connection from an outside IP to my machine running snort (192.168.0.2), I get this in the alert log:

```
[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
01/06-08:16:01.301279 XXX.XXX.XXX.XXX:2369 -> 192.168.0.2:XXX
TCP TTL:115 TOS:0x0 ID:54614 IpLen:20 DgmLen:92 DF
***AP*** Seq: 0x5D48F098  Ack: 0x5B19DC73  Win: 0xFD5C  TcpLen: 20
```

Attempted denial of service?  Simply for making an authenticated SSH connection?

Similarly, I see a log of messages like this simply when browsing websites:

```
[**] [1:100000160:2] COMMUNITY SIP TCP/IP message flooding directed to SIP proxy [**]
[Classification: Attempted Denial of Service] [Priority: 2] 
01/06-06:51:03.411603 XXX.XXX.XXX.XXX:80 -> 192.168.0.2:40322
TCP TTL:57 TOS:0x0 ID:7101 IpLen:20 DgmLen:1440 DF
***A**** Seq: 0xA55381E0  Ack: 0xC513FA5F  Win: 0x237E  TcpLen: 32
TCP Options (3) => NOP NOP TS: 574475743 29379010
```

These alerts are useless.  What am I doing wrong?  Thanks.

---

### Post by bodhi.zazen on 2010-01-06
> **oldmankit said:**
> Thank you Bodhi Zazen.  You have the uncommon gift of real clarity!

Do I need to bother with periodic checks such as rkhunter or chkrootkit?  Are they only for people running servers, too?

Depends on how paranoid you are. I know coming from windows you feel the need to check these things, but, root kit checkers and antivirus give so many warnings and false positives they just do not help that much.

As I see you are interested in security I suggest you look at the big security sticky and work you way though it.

Then go ahead and run tiger (see security stick for info on tiger) and the root kit checks, and antivirus on a FRESH INSTALL OR LIVE CD, then on your desktop, if nothing else to get a sense of how these tools work, what a "normal system" looks like, what the reports from these tools look like.

Then decide for yourself if you wish to use them long term.

My experience was, in the absence of running a server, relax and enjoy Linux.

For your situation, I advise you look at :

ufw, noscript, and apparmor, those will give you more bang for you time then rk hunters, tiger, or antivirus.

ufw, noscript, and apparmor prevent the damage in the first place, the other tools detect the problem (if you are lucky) after it is too late. Anyone with more experience then a "script kiddie" will evade the rk hunters anyway, and the logs I have seen from compromised systems were:

1. not discovered by a rk hunter or antivirus. The were detected by somebody who knows their system, what "normal" is, and that "something" was different.

2. The actions of the crackers would not trip a rk hunter.

In order to detect a modern intruder you need to be able to read the logs, read bash_history, identify who is logged in, or recognize that those files have been altered.

Learn these commands :

```
w
last
ps aux #(or variants)
top
```Learn to read the logs !!!

---

### Post by bodhi.zazen on 2010-01-06
> **mocha said:**
> These alerts are useless.  What am I doing wrong?  Thanks.

You are not doing anything "wrong"

Alerts are generated by rule sets, and in general are designed to err on the side of false positives rather then false negatives. Only you can determine how you use your box and what activity is normal. You need to 

1. Understand the rule sets are generic, some are even for windows boxes. Not at first this may seem useless, but, someone performing recon on yoru server may start with Windows vulnerabilities (especially script kiddies) and this may be an early warning.

2. Learn how the rules work and fine tune them to your use. Understand the risk / benefit of inactivating a rule.

3. Give feed back to those who write the rules (notify them of a false positive so they can modify the rule set).

4. Decide what to do. Are you going to blacklist an ip because of one ssh attempt ? two ? ten ?

I find most traffic is from script kiddies and they go away or change IP fast, so I ignore them.

I am more concerned with a successful attempt then a blocked one.

I block ip with persistent, prolonged, or diverse alerts (ones that start with a port scan, then they try ssh, then a few mysql injections ... ). Again usually script kiddies, but at least determined ones or crackers that like to make a lot of noise.

You can also deploy strategies to make these people "waste their time" or you can crack the crackers (honey pots).

See, security is fun =)

---

### Post by oldmankit on 2010-01-07
> **bodhi.zazen said:**
> Depends on how paranoid you are. I know coming from windows you feel the need to check these things, but, root kit checkers and antivirus give so many warnings and false positives they just do not help that much.

As I see you are interested in security I suggest you look at the big security sticky and work you way though it.

Then go ahead and run tiger (see security stick for info on tiger) and the root kit checks, and antivirus on a FRESH INSTALL OR LIVE CD, then on your desktop, if nothing else to get a sense of how these tools work, what a "normal system" looks like, what the reports from these tools look like.

Then decide for yourself if you wish to use them long term.

My experience was, in the absence of running a server, relax and enjoy Linux.

For your situation, I advise you look at :

ufw, noscript, and apparmor, those will give you more bang for you time then rk hunters, tiger, or antivirus.

ufw, noscript, and apparmor prevent the damage in the first place, the other tools detect the problem (if you are lucky) after it is too late. Anyone with more experience then a "script kiddie" will evade the rk hunters anyway, and the logs I have seen from compromised systems were:

1. not discovered by a rk hunter or antivirus. The were detected by somebody who knows their system, what "normal" is, and that "something" was different.

2. The actions of the crackers would not trip a rk hunter.

In order to detect a modern intruder you need to be able to read the logs, read bash_history, identify who is logged in, or recognize that those files have been altered.

Learn these commands :

```
w
last
ps aux #(or variants)
top
```Learn to read the logs !!!

Many thanks.  I will do just that.

---

### Post by mocha on 2010-01-07
Thanks for the feedback.  This is going to require further research on my part.

---

### Post by ubuchignome on 2010-01-12
Thanks much for the post. How do you remove ossec if needed?

---

### Post by bodhi.zazen on 2010-01-12
> **ubuchignome said:**
> Thanks much for the post. How do you remove ossec if needed?

You can deactivate it

```
sudo /etc/init.d/osssec stop
```

use update-rc.d to stop it from running on boot.

In terms of removal, I do not recall if they include a removal script or option in the install script, look in the extracted filed for an uninstall.sh.

If not, they you wil need to search for all ossec files and manually delete them.

---

### Post by ubuchignome on 2010-01-17
Would these programs be server specific, or would you recommend installing on a desktop machine ? 
 
Thanks.

---

### Post by bodhi.zazen on 2010-01-17
> **ubuchignome said:**
> Would these programs be server specific, or would you recommend installing on a desktop machine ? 
 
Thanks.

You may install them on a desktop if you wish, but it would almost certainly be over kill to install snort on a desktop.

---

### Post by ubuchignome on 2010-01-17
Thanks much for your time and experience.
 
odaatgnome

---

### Post by user2010 on 2010-01-18
hi! Thank you very much for that topic and your explanations. 
I am a very beginner in Ubuntu and Snort as well. 

Could you tell me, please, what does mean tar zxvf ../snortrules* in this context:
wget [http://www.snort.org/the_rules_you_wish_to_use](http://www.snort.org/the_rules_you_wish_to_use)
cd snort-2.8.3
tar zxvf ../snortrules* 
I've downloaded rules and have now a zip-package  *[FONT=Fixedsys]snortrules-snapshot-CURRENT.tar.gz[/FONT]*

What do I have to do now with this rules - unpack them in snort-x.x.x.x directory? Under which name?

---

### Post by bodhi.zazen on 2010-01-18
> **user2010 said:**
> hi! Thank you very much for that topic and your explanations. 
I am a very beginner in Ubuntu and Snort as well. 

Could you tell me, please, what does mean tar zxvf ../snortrules* in this context:
wget [http://www.snort.org/the_rules_you_wish_to_use](http://www.snort.org/the_rules_you_wish_to_use)
cd snort-2.8.3
tar zxvf ../snortrules* 
I've downloaded rules and have now a zip-package  *[FONT=Fixedsys]snortrules-snapshot-CURRENT.tar.gz[/FONT]*

What do I have to do now with this rules - unpack them in snort-x.x.x.x directory? Under which name?

Rules for snort are obtained from the web site and there are several options depending on if you wish to register or pay or not. Basically ther are 3 sets

free, no registration required.

free, registration required.

Paid rule set.

You downloaded a tar , not a zip.

Extract the rules (it is like unziping a zip archive) and move them into place.

In the commands . = current directory, .. = one directory up.

---

### Post by user2010 on 2010-01-18
Thank you. The last line is what I didn't understand before.. Now it's clear.

Next problem :) 

No, I didn't write my mysql password. Did the system give it to me or ..? My root-password (of course) doesn't match. Should I uninstall snort and start from the beginning? :(

---

### Post by bodhi.zazen on 2010-01-18
No, just re-set your mysql password.

[http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/](http://ubuntu.flowconsult.at/en/mysql-set-change-reset-root-password/)

---

### Post by fetanyl on 2010-01-24
.

---

### Post by abrrymnvette on 2010-02-03
I would like to add that the way this tutorial has you configure snort is outdated and doesn't allow the use of the preprocessor or decoder or so rules. 

When compiling, I'd suggest using 
./configure --enable-dynamicplugin --with-mysql --enable-decoder-preprocessor-rules --enable-gre-ipv6


Then you have to copy the decoder, preprocessor, and so rules to the $RULE_PATH you specify to get the most out of the rule set.

---

### Post by abrrymnvette on 2010-02-04
I'm getting this error when I tail the syslog. Snort seems to start fine. I deleted a bunch of events from Base, is that why I'm getting the error?

Feb  4 12:15:45 ubuntu-snort snort[3970]: database: mysql_error: Duplicate entry '2-182661' for key 1#012SQL=INSERT INTO event (sid,cid,signature,timestamp) VALUES (2, 182661, 30, '2010-02-04 12:15:45')




EDIT: Found my answer. I had more than one instance of snort running. The /etc/init.d/snort restart command didn't kill the initial instance before it started the new one.

When I run the restart script I get this error:

/etc/init.d/snort restart
/etc/init.d/snort: line 171: kill: 4097 4091: arguments must be process or job IDs

Any ideas?

---

### Post by abrrymnvette on 2010-02-18
> **abrrymnvette said:**
> I'm getting this error when I tail the syslog. Snort seems to start fine. I deleted a bunch of events from Base, is that why I'm getting the error?

Feb  4 12:15:45 ubuntu-snort snort[3970]: database: mysql_error: Duplicate entry '2-182661' for key 1#012SQL=INSERT INTO event (sid,cid,signature,timestamp) VALUES (2, 182661, 30, '2010-02-04 12:15:45')




EDIT: Found my answer. I had more than one instance of snort running. The /etc/init.d/snort restart command didn't kill the initial instance before it started the new one.

When I run the restart script I get this error:

/etc/init.d/snort restart
/etc/init.d/snort: line 171: kill: 4097 4091: arguments must be process or job IDs

Any ideas?


Fixed my issue by editing /etc/init.d/snort and adding the path to snort in all the variables. 

Problem was caused b/c I have BotHunter running on the box too. So there are two snort instances running. The script wouldn't restart snort correctly b/c it couldn't figure out which process to kill. So it wouldn't kill either and just start a new one.

---

### Post by Hopping_Ubu on 2010-02-22
I installed an instance of Snort running on Ubuntu 9.10 64 bit (Karmic Koala) on an VMware ESX server running the 3.5 infrastructure client. I have made it all the way to the starting of Snort and Barnyard but Snort doesn't do anything. I have tried to remove the network adapter and reinstall it. When I was running it using the VMware Server 2, I used the bridged and the host on the network adapters and it worked beautifully. Now in the ESX server, there is no choices to do that.

Rocket2DMn wrote about how do to it using VirtualBox, but I am not sure it transposes into VMware ESX very well.

Any information you can provide will be greatly appreciated.

](*,)

---

### Post by bodhi.zazen on 2010-02-22
> **Hopping_Ubu said:**
> I installed an instance of Snort running on Ubuntu 9.10 64 bit (Karmic Koala) on an VMware ESX server running the 3.5 infrastructure client. I have made it all the way to the starting of Snort and Barnyard but Snort doesn't do anything. I have tried to remove the network adapter and reinstall it. When I was running it using the VMware Server 2, I used the bridged and the host on the network adapters and it worked beautifully. Now in the ESX server, there is no choices to do that.

Rocket2DMn wrote about how do to it using VirtualBox, but I am not sure it transposes into VMware ESX very well.

Any information you can provide will be greatly appreciated.

](*,)

Hard to tell from your description.

What is it you are expecting snort to do exactly ? Snort does not log all network traffic, it only logs "alerts" or suspicious traffic based on a rule set. If no suspicious traffic is on your network nothing will happen.

---

### Post by Hopping_Ubu on 2010-02-22
> **bodhi.zazen said:**
> Hard to tell from your description.

What is it you are expecting snort to do exactly ? Snort does not log all network traffic, it only logs "alerts" or suspicious traffic based on a rule set. If no suspicious traffic is on your network nothing will happen.

MMMMM; Snort requires a second network adapter that passively sits and monitors to alert according to rule sets as you stated. In the virtual Ubuntu system that I installed, it is set to DHCP and therefore is my network connection to Snort. The second network adapter is supposed to be bridged (at least in VMware Server 2 it is bridged) and gives back information once Snort starts up. It is not suspicious traffic but it gives some data. How do I make sure that Snort starts monitoring using the second adapter? 

I hope this clarifies it a bit.

---

### Post by bodhi.zazen on 2010-02-22
You may run snort with a single network card if you wish.

If you have two network cards, you specify which card to listen on when starting snort with the -i option .

snort -i eth0 ....

Is that what you are asking ?

---

### Post by Hopping_Ubu on 2010-02-22
> **bodhi.zazen said:**
> You may run snort with a single network card if you wish.

If you have two network cards, you specify which card to listen on when starting snort with the -i option .

snort -i eth0 ....

Is that what you are asking ?

Yes, that is exactly what I am asking. I started snort using the -i on the listening card, but nothing seems to happen. When I was running it VMware Server 2, it would generate some data after the start, then just wait until there was suspicious traffic and then log some more. Should I not have used the 64 bit version of Koala and used the 32 bit?

---

### Post by bodhi.zazen on 2010-02-22
Can you post the output you are getting when you start snort from the command line ? Do you know how to test snort, make it generate an alert ?

---

### Post by Hopping_Ubu on 2010-02-22
> **bodhi.zazen said:**
> Can you post the output you are getting when you start snort from the command line ? Do you know how to test snort, make it generate an alert ?

Yes, I tried testing, but it didn't like the local rule I created.... Here is what I have from the Network Interface initializing. This happens even when I run 2 network adapters and start with the -i ethX command.

Initializing Network Interface eth0
Decoding Ethernet on interface eth0
fpBuildServicePortGroups: adding protocol-ordinal=13 as service=netbios-ssn
fpBuildServicePortGroups: adding protocol-ordinal=21 as service=pop3
fpBuildServicePortGroups: adding protocol-ordinal=14 as service=nntp
fpBuildServicePortGroups: adding protocol-ordinal=15 as service=dns
fpBuildServicePortGroups: adding protocol-ordinal=11 as service=netbios-dgm
fpBuildServicePortGroups: adding protocol-ordinal=36 as service=font-service
fpBuildServicePortGroups: adding protocol-ordinal=32 as service=ssl
fpBuildServicePortGroups: adding protocol-ordinal=7 as service=telnet
fpBuildServicePortGroups: adding protocol-ordinal=35 as service=ident
fpBuildServicePortGroups: adding protocol-ordinal=6 as service=ftp
fpBuildServicePortGroups: adding protocol-ordinal=18 as service=imap
fpBuildServicePortGroups: adding protocol-ordinal=33 as service=rtsp
fpBuildServicePortGroups: adding protocol-ordinal=34 as service=ldap
fpBuildServicePortGroups: adding protocol-ordinal=5 as service=http
fpBuildServicePortGroups: adding protocol-ordinal=10 as service=dcerpc
fpBuildServicePortGroups: adding protocol-ordinal=26 as service=sunrpc
fpBuildServicePortGroups: adding protocol-ordinal=24 as service=x11
fpBuildServicePortGroups: adding protocol-ordinal=31 as service=mysql
fpBuildServicePortGroups: adding protocol-ordinal=8 as service=smtp
fpBuildServicePortGroups: adding protocol-ordinal=8 as service=smtp
fpBuildServicePortGroups: adding protocol-ordinal=32 as service=ssl
fpBuildServicePortGroups: adding protocol-ordinal=18 as service=imap
fpBuildServicePortGroups: adding protocol-ordinal=5 as service=http
fpBuildServicePortGroups: adding protocol-ordinal=26 as service=sunrpc
fpBuildServicePortGroups: adding protocol-ordinal=13 as service=netbios-ssn
fpBuildServicePortGroups: adding protocol-ordinal=31 as service=mysql
fpBuildServicePortGroups: adding protocol-ordinal=24 as service=x11
fpBuildServicePortGroups: adding protocol-ordinal=7 as service=telnet
fpBuildServicePortGroups: adding protocol-ordinal=21 as service=pop3
fpBuildServicePortGroups: adding protocol-ordinal=15 as service=dns
fpBuildServicePortGroups: adding protocol-ordinal=26 as service=sunrpc
fpBuildServicePortGroups: adding protocol-ordinal=37 as service=kerberos
fpBuildServicePortGroups: adding protocol-ordinal=11 as service=netbios-dgm
fpBuildServicePortGroups: adding protocol-ordinal=13 as service=netbios-ssn
fpBuildServicePortGroups: adding protocol-ordinal=10 as service=dcerpc
fpBuildServicePortGroups: adding protocol-ordinal=22 as service=snmp
fpBuildServicePortGroups: adding protocol-ordinal=13 as service=netbios-ssn
fpBuildServicePortGroups: adding protocol-ordinal=11 as service=netbios-dgm
fpBuildServicePortGroups: adding protocol-ordinal=26 as service=sunrpc
fpBuildServicePortGroups: adding protocol-ordinal=15 as service=dns
fpBuildServicePortGroups: adding protocol-ordinal=22 as service=snmp
fpBuildServicePortGroups: adding protocol-ordinal=10 as service=dcerpc

[ Port and Service Based Pattern Matching Memory ]
+-[AC-BNFA Search Info Summary]------------------------------
| Instances        : 853
| Patterns         : 273022
| Pattern Chars    : 5254023
| Num States       : 2694297
| Num Match States : 276907
| Memory           :   79.61Mbytes
|   Patterns       :   15.42M
|   Match Lists    :   32.32M
|   Transitions    :   31.54M
+-------------------------------------------------

        --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.5.1 (Build 114)  
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/snort/snort-team](http://www.snort.org/snort/snort-team)
           Copyright (C) 1998-2009 Sourcefire, Inc., et al.
           Using PCRE version: 7.8 2008-09-05

           Rules Engine: SF_SNORT_DETECTION_ENGINE  Version 1.11  <Build 17>
           Rules Object: web-misc  Version 1.0  <Build 1>
           Rules Object: web-client  Version 1.0  <Build 1>
           Rules Object: sql  Version 1.0  <Build 1>
           Rules Object: smtp  Version 1.0  <Build 1>
           Rules Object: p2p  Version 1.0  <Build 1>
           Rules Object: nntp  Version 1.0  <Build 1>
           Rules Object: netbios  Version 1.0  <Build 1>
           Rules Object: multimedia  Version 1.0  <Build 1>
           Rules Object: misc  Version 1.0  <Build 1>
           Rules Object: imap  Version 1.0  <Build 1>
           Rules Object: exploit  Version 1.0  <Build 1>
           Rules Object: dos  Version 1.0  <Build 1>
           Rules Object: chat  Version 1.0  <Build 1>
           Rules Object: bad-traffic  Version 1.0  <Build 1>
           Preprocessor Object: SF_SSLPP  Version 1.1  <Build 3>
           Preprocessor Object: SF_SSH  Version 1.1  <Build 2>
           Preprocessor Object: SF_SMTP  Version 1.1  <Build 8>
           Preprocessor Object: SF_FTPTELNET  Version 1.2  <Build 12>
           Preprocessor Object: SF_DNS  Version 1.1  <Build 3>
           Preprocessor Object: SF_DCERPC2  Version 1.0  <Build 2>
Not Using PCAP_FRAMES

Stops right here!

Thank you.

---

### Post by bodhi.zazen on 2010-02-23
Looks good to me =)

[http://leonward.wordpress.com/2008/07/18/not-using-pcap_frames-aka-when-good-verbosity-goes-bad/](http://leonward.wordpress.com/2008/07/18/not-using-pcap_frames-aka-when-good-verbosity-goes-bad/)

---

### Post by Hopping_Ubu on 2010-02-23
Thanks, Now that it has been running for almost 24 hours, it is showing signs of life. My snorting koala lives.

---

### Post by oshea85 on 2010-02-23
Man, wish I'd found this forum thread two weeks ago.  I finally have Snort-2.8.5.2 from source, built with mysql, base and barnyard-2.1.7, as per Ubunutu directions on snort.org... a little rough, but the marks are all scabbed over by now.  Running Karmic 9.10.  Everything pretty much works, but...

I can't get barnyard2 to start at boot.  I've googled much, tried init scripts that I've found, but I can only get it to run by issuing from the command line:

/usr/local/bin/barnyard2 -c /etc/snort/barnyard2.conf -G /etc/snort/gen-msg.map -S /etc/snort/sid-msg.map -d /var/log/snort -f snort.log -w /var/log/snort/barnyard.waldo

This same command doesn't work for me in an init script. Anyone have any ideas on how to get barnyard2 to run at boot, or have a script they can share?

Edit:
Posting this here for future googlers and linux noobs like me.  the barnyard init script command needed an '&' at the end and the whole command had to be inserted into /etc/rc.local ... that did the trick.

---

### Post by Zapisto on 2010-02-25
> **bodhi.zazen said:**
> Basically ther are 3 sets

free, no registration required.

free, registration required.

Paid rule set.

Unless i miss something there is no more free version 
Quete from snort site :

> There are three ways to obtain these rules:

Subscribers
Real-time access to VRT Certified Rules Updates requires a paid subscription.
For more information on VRT subscriptions click here.

Registered Users
Registered users of Snort.org are able to download and use VRT rules free of charge 30 days after their initial release date.

Integrators
This subscription type is an OEM license for businesses that intend to distribute Sourcefire VRT Certified Rules as part of an integrated product or service offering. For more information on the Snort Integrator program visit: Snort Integrators.

---

### Post by bodhi.zazen on 2010-02-25
> **Zapisto said:**
> Unless i miss something there is no more free version 
Quete from snort site :

You are missing something.

Read this carefully:

> Registered Users
Registered users of Snort.org are able to download and use VRT rules **[SIZE=4] free of charge[/SIZE]** 30 days after their initial release date.Emphasis added by me.

So, when a new set of rules is available it becomes available to Subscribed users (fee for service).


30 days later then then become available for Registered users, no cost.

So registered uses get a 30 delay in the availability of rule sets, but, after the delay, the rules are available at no cost.

You are not the only one to mis read the terms, it is a common mistake.

---

### Post by espressobeanie on 2010-02-27
When I got to this part in the third post:

mysql -u root -p
I keep getting an error message that says: 

ERROR 2002 (HY0000): Can't connect to local MySQL server through socket  '/var/run/mysqld/mysqld.sock' (2)

I found the problem to be associated with the mysql-server-5.0 package, so I installed mysql-server-5.1. However, I'm a total n00b with mysql and your command for granting all privleges to localhost for the 'snort' database doesn't work.

---

### Post by Zapisto on 2010-03-01
> **bodhi.zazen said:**
> 
You are not the only one to mis read the terms, it is a common mistake.

Thanks for your answer.

I actualy want to run snort on my publically exposed system and Apache+base on  an internal system not exposed.
is that possible ?
Z.

---

### Post by bodhi.zazen on 2010-03-01
> **Zapisto said:**
> Thanks for your answer.

I actualy want to run snort on my publically exposed system and Apache+base on  an internal system not exposed.
is that possible ?
Z.

It can be done yes. You either configure mysql to accept external connections and tell snort to connect with the server.

It may be easeir to install snort + apache + base all on the external server, and limit connections in iptables (or apache).

---

### Post by Zapisto on 2010-03-01
> **bodhi.zazen said:**
> It can be done yes. You either configure mysql to accept external connections and tell snort to connect with the server.

It may be easeir to install snort + apache + base all on the external server, and limit connections in iptables (or apache).
thanks i will look at it.
aLso Bleeding Threats is defunct unfortunately, and have been replace by [http://www.emergingthreats.net/](http://www.emergingthreats.net/)

you may want to update your doc.

ref : 
[http://ubuntuforums.org/showthread.php?t=935099](http://ubuntuforums.org/showthread.php?t=935099)

---

### Post by bodhi.zazen on 2010-03-01
Thank you.

I need to update both this thread and the Virtualization thread with 10.04 ...

---

### Post by abrrymnvette on 2010-03-02
> **unutbu said:**
> Okay, you have a snort user on localhost, and it has a password.
I'm guessing the saved password is not the intended password. Perhaps an
invisible control character slipped in there too? 

Try typing
```

grant all privileges on snort.* to 'snort'@'localhost' identified by 'snort_password'; 
```in gedit, rather than openoffice. Maybe it is just my superstition, but I think gedit is more of a plain text editor, while openoffice is more of a "fancy" text editor. 

When you copy and paste into the gnome-terminal, make sure your quotation marks look like 
the one circled in green, rather than the one in red.


I had to start fresh again and trying to reinstall. I'm somehow having the same issue. I've even tried using gedit and then copy/paste. No luck. I've tried the flush privileges and even rebooted a couple times. Nothing. 


Any help would be great.

mysql> grant all privileges on snort.* to 'snort'@'localhost' identified by 'snort_password';
Query OK, 0 rows affected (0.00 sec



mysql> use mysql
Reading table information for completion of table and column names
You can turn off this feature to get a quicker startup with -A

Database changed
mysql> select user,host,password from user where user='snort';
+-------+-----------+-------------------------------------------+
| user  | host      | password                                  |
+-------+-----------+-------------------------------------------+
| snort | localhost | *7368BE1E9EBE6CE295CC9AB6EBD01FAB363E5A2A | 
+-------+-----------+-------------------------------------------+
1 row in set (0.00 sec)

mysql>

---

### Post by bodhi.zazen on 2010-03-02
What problem are you having ? The output looks fine.

You should change "snort" to the user you wish to use, snort is fine 

You should also change "snort_password" to the actual password you use.

You then put the user name and password into the snort config file.

---

### Post by abrrymnvette on 2010-03-02
> **bodhi.zazen said:**
> What problem are you having ? The output looks fine.

You should change "snort" to the user you wish to use, snort is fine 

You should also change "snort_password" to the actual password you use.

You then put the user name and password into the snort config file.


The "0 lines affected" part. Doesn't that mean it didn't give that user privileges on the snort DB?

---

### Post by bodhi.zazen on 2010-03-02
> **abrrymnvette said:**
> The "0 lines affected" part. Doesn't that mean it didn't give that user privileges on the snort DB?

I can not tell from that output alone, but I see no errors or problems, and I get the same output from mysql in terms of 0 rows affected.

Is it working ? If so , no problem then.

Try:

```
mysql -u snort_user -p
```

enter your password.

---

### Post by Saif24 on 2010-03-03
Hello,
i have installed snort + mysql + acid base,i add some rules into /etc/snort/rules/local.rules  to test the alert:

alert icmp 192.168.1.20 any -> 192.16.1.21 any (flags:A;ack:0;msg:"NMap icmp ping")\

alert icmp 192.168.1.20 any -> 192.16.1.21 any (content:"abcdefgh";;msg:"ping de windows")\

alert icmp 192.168.1.20 any <> 192.16.1.21 any (flags: S; msg: &#8220;HOULA SYN Packet!&#8221;;)\

after i restart snort and i tied 2 pc by *cross cable ( 192.168.1.20 for windows and the victim is 192.168.1.21 for Linux where the snort is installed ) , my HOME_NET* *192.168.1.21 and the EXTEREL_NET !$HOME_NET. The problem is  *when i run

 snort -dvi eth0 -c /etc/snort/snort.conf

 i see the packet transsmited and recived (the recived conten "abcdefgh" ), when i stoped snort CTRL+C i don't found any alert in the result!!!
Run time prior to being shutdown was 218.523030 seconds
===============================================================================
Packet Wire Totals:
   Received:         1346
   Analyzed:         1342 (99.703%)
    Dropped:            0 (0.000%)
Outstanding:            4 (0.297%)
===============================================================================
Breakdown by protocol (includes rebuilt packets):
      ETH: 1342       (100.000%)
  ETHdisc: 0          (0.000%)
     VLAN: 0          (0.000%)
     IPV6: 0          (0.000%)
  IP6 EXT: 0          (0.000%)
  IP6opts: 0          (0.000%)
  IP6disc: 0          (0.000%)
      IP4: 1213       (90.387%)
  IP4disc: 394        (29.359%)
    TCP 6: 0          (0.000%)
    UDP 6: 0          (0.000%)
    ICMP6: 0          (0.000%)
  ICMP-IP: 0          (0.000%)
      TCP: 0          (0.000%)
      UDP: 35         (2.608%)
     ICMP: 390        (29.061%)
  TCPdisc: 0          (0.000%)
  UDPdisc: 0          (0.000%)
  ICMPdis: 0          (0.000%)
     FRAG: 394        (29.359%)
   FRAG 6: 0          (0.000%)
      ARP: 129        (9.613%)
    EAPOL: 0          (0.000%)
  ETHLOOP: 0          (0.000%)
      IPX: 0          (0.000%)
    OTHER: 0          (0.000%)
  DISCARD: 394        (29.359%)
InvChkSum: 0          (0.000%)
   S5 G 1: 0          (0.000%)
   S5 G 2: 0          (0.000%)
    Total: 1342      
===============================================================================
Action Stats:
ALERTS: 0
LOGGED: 0
PASSED: 0
===============================================================================
Frag3 statistics:
        Total Fragments: 394
      Frags Reassembled: 0
               Discards: 0
          Memory Faults: 0
               Timeouts: 0
               Overlaps: 0
              Anomalies: 0
                 Alerts: 0
     FragTrackers Added: 394
    FragTrackers Dumped: 394
FragTrackers Auto Freed: 0
    Frag Nodes Inserted: 394
     Frag Nodes Deleted: 394
===============================================================================
Stream5 statistics:
            Total sessions: 0
              TCP sessions: 0
              UDP sessions: 0
             ICMP sessions: 0
                TCP Prunes: 0
                UDP Prunes: 0
               ICMP Prunes: 0
TCP StreamTrackers Created: 0
TCP StreamTrackers Deleted: 0
              TCP Timeouts: 0
              TCP Overlaps: 0
       TCP Segments Queued: 0
     TCP Segments Released: 0
       TCP Rebuilt Packets: 0
         TCP Segments Used: 0
              TCP Discards: 0
      UDP Sessions Created: 0
      UDP Sessions Deleted: 0
              UDP Timeouts: 0
              UDP Discards: 0
                    Events: 0
           TCP Port Filter
                   Dropped: 0
                 Inspected: 0
                   Tracked: 0
           UDP Port Filter
                   Dropped: 0
                 Inspected: 0
                   Tracked: 0
===============================================================================
===============================================================================
dcerpc2 Preprocessor Statistics
  Total sessions: 0
===============================================================================
===============================================================================
database: Closing connection to database "snort"
database: Closing connection to database "snort"
Snort exiting


Please if someone can teel me where's the problem! thanks.

---

### Post by Zapisto on 2010-03-03
i am getting a strange error when snort start :

first i  get 
```
FATAL ERROR: /etc/snort/snort.conf(273) Config option "detection" can only be configured once.
```

in my confile 

```
# Configure the detection engine
# ===============================
#
# Use a different pattern matcher in case you have a machine with very limited
# resources:
#
# config detection: search-method lowmem

config detection: search-method ac-bnfa
config detection: max_queue_events 5
config event_queue: max_queue 8 log 3 order_events content_length
```

then now :

```
FATAL ERROR: parser.c(5050) Could not stat dynamic module path "/usr/local/lib/snort_dynamicrules/bad-traffic.so": No such file or directory.
```

any help ?

---

### Post by bodhi.zazen on 2010-03-03
What and where are you looking for an alter ? BASE ? Barnyard ? logs ?

---

### Post by Zapisto on 2010-03-03
> **bodhi.zazen said:**
> What and where are you looking for an alter ? BASE ? Barnyard ? logs ?
those quetsion is for who ?
if it is for me i was planning instal Base.

---

### Post by bodhi.zazen on 2010-03-03
> **Zapisto said:**
> those quetsion is for who ?
if it is for me i was planning instal Base.

Sorry, that was for [Saif24]("http://ubuntuforums.org/member.php?u=1022503").

For you problem change these two lines :
> config detection: search-method ac-bnfa[FONT=monospace]
[/FONT]config detection: max_queue_events 5

To (one line):

```
config detection: search-method ac-bnfa[FONT=monospace][/FONT] max_queue_events 5
```

---

### Post by Zapisto on 2010-03-03
Thanks that's fix the first error but snort still failed to start with :

```
FATAL ERROR: parser.c(5050) Could not stat dynamic module path "/usr/local/lib/snort_dynamicrules/bad-traffic.so": No such file or directory.
```

look like none of the rles get installed ....
thanks

---

### Post by bodhi.zazen on 2010-03-03
Did you install a rule set ?

[http://seclists.org/snort/2009/q3/422](http://seclists.org/snort/2009/q3/422)

[https://forums.snort.org/forums/snort-newbies/topics/error-parser-c-5047-could-not-stat-dynamic-module-path-usr-local-lib-snort_dynamicrules-bad-traffic-so-no-such-file-or-directory](https://forums.snort.org/forums/snort-newbies/topics/error-parser-c-5047-could-not-stat-dynamic-module-path-usr-local-lib-snort_dynamicrules-bad-traffic-so-no-such-file-or-directory)

---

### Post by Zapisto on 2010-03-03
> **bodhi.zazen said:**
> Did you install a rule set ?

[http://seclists.org/snort/2009/q3/422](http://seclists.org/snort/2009/q3/422)

[https://forums.snort.org/forums/snort-newbies/topics/error-parser-c-5047-could-not-stat-dynamic-module-path-usr-local-lib-snort_dynamicrules-bad-traffic-so-no-such-file-or-directory](https://forums.snort.org/forums/snort-newbies/topics/error-parser-c-5047-could-not-stat-dynamic-module-path-usr-local-lib-snort_dynamicrules-bad-traffic-so-no-such-file-or-directory)
was following the guide.
i will check that.

---

### Post by abrrymnvette on 2010-03-04
> **Zapisto said:**
> was following the guide.
i will check that.


You need to download the so rules for your distro or compile them yourself on your box. Here is a quick guide from snort on how to do it. 


[http://www.snort.org/snort-rules/about-so_rules](http://www.snort.org/snort-rules/about-so_rules)

Your error is telling you there are no rules in the directory listed.

---

### Post by bodhi.zazen on 2010-03-04
> **abrrymnvette said:**
> You need to download the so rules for your distro or compile them yourself on your box. Here is a quick guide from snort on how to do it. 


[http://www.snort.org/snort-rules/about-so_rules](http://www.snort.org/snort-rules/about-so_rules)

Your error is telling you there are no rules in the directory listed.

Nice link, thank you =)

---

### Post by Zapisto on 2010-03-15
Hello, I manage to start snort 
but i have nothing in base.
nada, zero entry.

where do i start looking ?
thanks

---

### Post by bodhi.zazen on 2010-03-15
> **Zapisto said:**
> Hello, I manage to start snort 
but i have nothing in base.
nada, zero entry.

where do i start looking ?
thanks

It is perfectly normal NOT to have any alerts in base. 

Post a screen shot of base and I can give you perhaps better advice.

If snort goes too long without an alert , it disconnects from the database, and needs to be restarted.

---

### Post by Zapisto on 2010-03-15
here is the requested screenshot.
let me know

---

### Post by bodhi.zazen on 2010-03-15
I see nothing wrong.

You either have to hit snort with something or wait, but your sensor is registering (the 0/1 line) and I can see no problem with your installation.

---

### Post by Zapisto on 2010-03-15
tried ssh failure
and get any alert :)

---

### Post by bodhi.zazen on 2010-03-15
Generating snort alerts is grey hat at best and as such is beyond what we support on these forums.

A simple google search will answer your question on how to generate a snort alert as will time.

The most important thing is that you see your sensor in base, the line reads "0/1"

The 0 means you have had no alerts, the 1 means base is connected to snort.

Everything is working as expected, beyond that you will need to read.

---

### Post by Zapisto on 2010-03-15
thnaks a lot
i will

---

### Post by espressobeanie on 2010-03-28
How do I get adodb installed to work with base? When I setup base and it asks for the adodb path, I enter what you provided, but this didn't work. It tells me file not found.

---

### Post by bodhi.zazen on 2010-03-28
> **espressobeanie said:**
> How do I get adodb installed to work with base? When I setup base and it asks for the adodb path, I enter what you provided, but this didn't work. It tells me file not found.

Did you install adobd ?

---

### Post by shahin on 2010-07-16
My set up was working fine until I upgraded to LTS.  Now I get the following error messages:
Deprecated: Function ereg_replace() is deprecated in /var/www/base/includes/base_state_common.inc.php  on line 184

Deprecated: Function ereg_replace() is deprecated in /var/www/base/includes/base_state_common.inc.php on line 184

Deprecated: Function ereg_replace() is deprecated in /var/www/base/includes/base_state_criteria.inc.php on line 255

I know you mentioned not to run new versions of base, but 1.4.4 was working fine for me.  Any idea what happened?

---

### Post by shahin on 2010-07-16
Seems I need to apply a patch discussed here:
[https://sourceforge.net/tracker/?func=detail&aid=3009648&group_id=103348&atid=635584]("https://sourceforge.net/tracker/?func=detail&aid=3009648&group_id=103348&atid=635584")
Can you help me with this?  I have not applied patches before.

---

### Post by baguahsing on 2010-07-16
For wireless you recommended airsnort. I clicked on the link and it said that it was old an no longer supported. The site said there are better alternatives and gave 1 or 2 recommendations. Should I stick with airsnort or look for something else? I have an older laptop, Toshiba Satellite Pro 6100, P4 1.6GHz cpu, 1Gb mem, and a 40Gb hard drive. Will Apache be too much for me? If so, what NID and HID would you recommend?

---

### Post by espressobeanie on 2010-07-23
I'm running into problems with starting snort:

> dave@dms:~$ sudo /etc/init.d/snort start

And a pop-up box comes up and says:

> Snort failed to start...Not sure where I went wrong. Everything after 'make install' worked fine and there were two errors that I encountered. The first was when I was installing updated packages, like mysql-server-5.1, and I got this error:

> libphp-adodb is no longer installed in /usr/share/adodb. New installation path is now /usr/share/php/adodb.

Please update your php.ini file. Maybe you must also change your web-server configuraton.And the second was that I couldn't import the mysql schemas for snort. I kept getting this error: 

> ERROR 1045 (28000): Access denied for user 'snort'@'localhost' (using password: YES)
A file create_mysql is already there. 

Not sure how to fix these problems. Also, snort has updated to version 2.8.6.1 and already includes your startup script.

Bodhi, I was able to fix that other issue above. one of the php5 packages changed the way it referenced adobd and I failed to realize it.

---

### Post by shahin on 2010-07-23
You are going to have to update the php files stated during the install process.  But I do not think snort issue is related to that.  I would suggest you test each component separately.  ( you are doing that actually ) try to start snort, and have it report to screen.  You can see the alerts go by, or collect them into a file.  Once you know you are generating alerting alerts, then you can collect them into the mysql database.  You can run snort in test mode, or use another switch to send the alerts to a file or console.  Once you see alerts, then you should specify the location of your snort.conf file, which is the command that author of this document gave us.  You snort.conf file causes snort to report to the mysql.  Then you can jump in the mysql, and run a query to see if your alerts make it to your database.  Once you are sure that is happening, then the fun begins with php new paths etc.  I hope this helps.  It may seem a lot of work, but it is fun as heck and in the end you come out with a great understanding of how this valuable tool works.   

> **espressobeanie said:**
> I'm running into problems with starting snort:

And a pop-up box comes up and says:

Not sure where I went wrong. Everything after 'make install' worked fine and there were two errors that I encountered. The first was when I was installing updated packages, like mysql-server-5.1, and I got this error:

And the second was that I couldn't import the mysql schemas for snort. I kept getting this error: 

A file create_mysql is already there. 

Not sure how to fix these problems. Also, snort has updated to version 2.8.6.1 and already includes your startup script.

Bodhi, I was able to fix that other issue above. one of the php5 packages changed the way it referenced adobd and I failed to realize it.

---

### Post by uRock on 2010-07-23
The following code will attempt to start SNORT and send any errors to a newly created snort_errors file in your /home folder. You do not have to create the file. The terminal will create it for you. Then you can post the contents of the folder here. Most likely the problems is coming from a conflicting SNORT rule. Hopefully this will show what that rule is. ```
sudo /etc/init.d/snort start 2> snort_errors
```

---

### Post by bodhi.zazen on 2010-07-23
> **espressobeanie said:**
> I'm running into problems with starting snort:

And a pop-up box comes up and says:

Not sure where I went wrong. Everything after 'make install' worked fine and there were two errors that I encountered. The first was when I was installing updated packages, like mysql-server-5.1, and I got this error:

And the second was that I couldn't import the mysql schemas for snort. I kept getting this error: 

A file create_mysql is already there. 

Not sure how to fix these problems. Also, snort has updated to version 2.8.6.1 and already includes your startup script.

Bodhi, I was able to fix that other issue above. one of the php5 packages changed the way it referenced adobd and I failed to realize it.

OK, so you fixed the adodb error by updating the path.

The second error looks like a mysql problem. Did you set up the mysql database and edit /etc/snort/snort.conf ?

Did you make a mysql user, "snort" ? Did you make a database ?

Can you connect to mysql using snort ?

```
mysql -u snort -p
```

---

### Post by espressobeanie on 2010-07-24
Woohoo! I figured it out. Bodhi, I did create a user named snort, and all of that. It seemed that importing the schemas was the problem. When you did that mysql command, I kept using my login password and not the mysql one. Now, I get snort is running successfully while whitelisting those two ip addresses.

---

### Post by bodhi.zazen on 2010-07-24
> **espressobeanie said:**
> Woohoo! I figured it out. Bodhi, I did create a user named snort, and all of that. It seemed that importing the schemas was the problem. When you did that mysql command, I kept using my login password and not the mysql one. Now, I get snort is running successfully while whitelisting those two ip addresses.

Well done =)

---

### Post by UnrealMiniMe on 2010-08-19
> **rodney757 said:**
> I was just reading this tutorial and it says to use airsnort if you use wireless. When I go to the airsnort site it says that the project is dead. Is there an alternitive I should use? Thanks

> **over_my_head said:**
> thanks for writing the tutorial - i haven't tried it yet but it looks very detailed. 
I intended to go ahead and try it out, using airsnort since i'm on a wireless connection. i went to the airsnort page, it says: "This software is old. It is no longer maintained or supported. Besides, there are much better tools out there. You really should be trying something like aircrack-ng." 
???
aircrack-ng seems to be some way of cracking wireless network encryption keys... and then it says it can "audit" wireless networks...
i'm very confused now.

> **baguahsing said:**
> For wireless you recommended airsnort. I clicked on the link and it said that it was old an no longer supported. The site said there are better alternatives and gave 1 or 2 recommendations. Should I stick with airsnort or look for something else? I have an older laptop, Toshiba Satellite Pro 6100, P4 1.6GHz cpu, 1Gb mem, and a 40Gb hard drive. Will Apache be too much for me? If so, what NID and HID would you recommend?

I want to second what all these guys are saying:  According to the airsnort website, airsnort is outdated and no longer developed or maintained.  It refers people to aircrack-ng, but that seems to be cracking software, not intrusion-detection software.

Here is my issue:  System Monitor is showing a conspicuously high amount of data that has been sent over the network from my computer, and even after I restarted X, I noticed I was constantly uploading data at a few KB/s.  I want to know who my computer is/has been communicating with and why, but I'm not sure how.

After initially posting this, I've realized this is probably what OSSEC was made for, not Snort.  Am I correct here?

If not, has Snort been updated to include wireless support, or is there another viable software package that does?  I understand if Snort is not able to monitor every packet crossing over the wireless network, but I at least want to determine who my own computer is sending packets to.  What's the best way to do this?

---

### Post by lumore22 on 2010-10-11
Greetings-

I am a newbie to Linux and security on a dual-boot AMD_x86 Gateway machine running Lucid Lynx, 2.6.32.24.

1. I installed ossec and used the install.sh script. My installation is agentless and ossec is running.

But  maybe because I am a newbie I missed something such as ::

How would I know that anything is wrong unless I manually read the logs?
 
I read the installation instructions but beyond running install.sh I am not sure what to configure next, so that I get some sort of notification more frequently than 6 hours (the default time between ossec checks). I guess the instructions are okay if you already know  how to do it.  I 'm afraid I'll mess something up. 

2. I downloaded airsnort from voxel.sourceforge.net to cover any possible network intrusion. Here's my dilemma::

I already have a LAMPP stack installed on my system in /opt. It has to be started  manually when I want to use it.  :confused:  Should I still install another copy of Apache and MySQL?    :confused:(I don't use the LAMPP stack on the network - no reason to. )   Will it affect anything on the LAMPP stack?   

Thank-you in advance.

Regards-

---

### Post by Saeros3 on 2010-12-03
I installed ossec as described in [post #6]("http://ubuntuforums.org/showpost.php?p=5786503&postcount=6"), and the web interface in [post #7]("http://ubuntuforums.org/showpost.php?p=5786522&postcount=7"). After doing this, I rebooted my computer, and as it was loading, an error message was displayed.

> There is a problem with the configuration server.

(/usr/bin/libgconf2-4/gconf-sanity-check-2 exited with status 256)I [googled]("http://www.google.com.au/search?hl=en&client=firefox-a&hs=6UL&rls=org.mozilla:en-GB:official&&sa=X&ei=PYL5TJuhDsLirAf5icG7Cw&ved=0CBgQvwUoAQ&q=gconf-sanity-check-2+exited+with+status+256&spell=1") the error message, and found only [this]("http://ubuntuforums.org/showthread.php?t=917306") forum post. On the post, the following command was suggested:

> sudo chmod 755 /etc/gconf/gconf.xml.systemI entered the terminal, and logged in, by pressing ctrl+alt+f1. I assume that the fact i was able to do that means that it is a problem with gnome(?). However, the error message only started appearing after i installed ossec, and the web interface. At the terminal, I entered the above command, but it didn't resolve the problem.

Any ideas? has anyone else had the same problem?

---

### Post by DarkTide on 2011-04-12
I intended to go ahead and try it out, using airsnort since i'm on a  wireless connection. i went to the airsnort page, it says: "This  software is old. It is no longer maintained or supported. Besides, there  are much better tools out there. You really should be trying something  like aircrack-ng."

---

### Post by starz677 on 2012-05-31
Does anyone know if the original posts here are still applicable or are they outdated ?

thx

---

### Post by shahin on 2012-05-31
This is a popular setup. I think you will run into some issues related to difference in software packages and etc. I would suggest that you install one component at a time. There is other information online about this setup. Here is what I would suggest you do:
1- Install Snort first, and run it by itself and verify that you can view packet captures
2- See if you can store the traffic in the database
3- install the management interfaces. I think BASE is no longer used. 
Keep in mind that I did this a couple of years ago, and the above steps are just to give you an idea of what I would suggest. My point is that I don't think you can do every step, and get the exact output stated. But overall the procedures rocked. I learned so much by doing this. 
Good Luck

---

### Post by SSOMaster on 2012-11-21
I've just installed AlienVault and can't start snort. I'm a newbie. Maybe you can provide some help.

This is the error i get: After everything seems to work fine.

server snort[26207]: FATAL ERROR: Failed to initialize dynamic engine: SF_SNORT_DETECTION_ENGINE version 1.16.18

AlienVault 4.1 , everything up to date.

thank in advance, and sorry for the near off-topic.

---

### Post by OpSecShellshock on 2012-11-21
I'm not sure if Alienvault has a special way of setting things up for its version of Snort, but in my experience when they dynamic engine is being loaded it gives the actual path to the library which is typically somewhere in /usr/lib. The first place I'd check is in /etc/snort/snort.conf to see if there is a properly configured path to the dynamic engine.

This may be something better suited for Alienvault support forums, though.

---

