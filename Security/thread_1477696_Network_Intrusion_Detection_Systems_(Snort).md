---
title: "Network Intrusion Detection Systems (Snort)"
date: 2010-05-09
forum: Security
---

### Post by bodhi.zazen on 2010-05-09
[size=6][center]Intro - What is snort and who should use it ?[/size][/center]

Snort is a [NIDS](http://en.wikipedia.org/wiki/Network_intrusion_detection_system) tool. NIDS tools monitor network traffic for suspicious activity. While there are other tools (system (firewall) logs, wireshark, tcpdump, etc) the "problem" with these tools is the sheer volume of network packets makes it difficult to impossible to detect suspicious network activity. Snort monitors your network traffic and generates "alerts" based on the snort rule set. One then reviews a smaller number of alerts, although by it's nature snort often generates a large volume of "false positives".

_Note_: IMO, in general, snort is used to monitor network traffic on large LAN and/or to public servers such as LAMP. If you are wanting to use snort it is assumed you understand at least the basics of networking protocols (udp/tcp/icmp). If you need a review [This site](http://security.maruhn.com/) has some outstanding tutorials (see the [networking concepts](http://security.maruhn.com/networking-concepts/) and [Tutorial](http://security.maruhn.com/iptables-tutorial/) links).

_Note_: Installing, configuring, and monitoring snort will take some time and effort, especially with the initial installation. Learning to use snort, understanding alerts, and customizing the snort rules is beyond this tutorial and comes with practice, Google, and reading the [snort documentation](http://www.snort.org/docs).

[Snort users manual (PDF)](http://www.snort.org/assets/125/snort_manual-2_8_5_1.pdf)

_Note_: By design, snort generates "False positives" and to use snort one will need to become familiar with snort rules. Responding to snort alerts is as much an art as a science and although I can give you a few general tips, nothing replaces hands on experience with snort. 

_Note_: Using snort or reading the (iptables) logs may induce an acute paranoid state in susceptible individuals. Take a deep breath, Don't panic, and read / google search the alerts. 

In this set of posts I will show you how to install and configure snort using postgresql and [BASE](http://base.secureideas.net/screens.php). BASE is a web based a graphical tool to monitor snort alerts. Postgresql is a database used to log snort alerts. You could use mysql as an alternate if you prefer.

[color=darkred]**While apt-get will install the necessary packages from the Ubuntu repositories, there is a  moderate amount of post-install configuration that is required.**[/color]

My advice is to install a minimal Ubuntu system using the server CD (select install a minimal system) or the [minimal CD](https://help.ubuntu.com/community/Installation/MinimalCD).

There is an overview of how to use the minimal CD [here](http://www.psychocats.net/ubuntu/minimal) .

This will result in a small command line only system. You may then install openssh-server and ssh into your snort machine (makes it easier to copy and paste the commands).

Most of the commands in this tutorial are run as root, so if you do not want to keep typing sudo, open a root shell with:

```
sudo -i
```


_Contents_ :

[Helpful commands / alternates to snort]("http://ubuntuforums.org/showpost.php?p=9265754&postcount=2")
[Install Snort]("http://ubuntuforums.org/showpost.php?p=9265768&postcount=3")
[Configure Snort]("http://ubuntuforums.org/showpost.php?p=9265786&postcount=4")
[BASE (Web interface)]("http://ubuntuforums.org/showpost.php?p=9265794&postcount=5")
[Rules / Oinkmaster - Keep snort rules up to date]("http://ubuntuforums.org/showpost.php?p=9265804&postcount=6")
[so rules]("http://ubuntuforums.org/showpost.php?p=9265811&postcount=7")
[Test snort]("http://ubuntuforums.org/showpost.php?p=9265815&postcount=8")
[Managing alerts]("http://ubuntuforums.org/showpost.php?p=9265825&postcount=9")


[Discussion Thread](http://ubuntuforums.org/showthread.php?p=9265855#post9265855) - The discussion thread is for comments / feedback. Please do not use the discussion tread for support questions, start a support thread in the security forums.

---

### Post by bodhi.zazen on 2010-05-09
[size=6][center]Useful commands / Alternates to snort[/size][/center]

This post serves as a *very brief* overview of useful commands.

PSAD ***may*** be a viable alternate to snort.

[size=4]NMAP[/size]

[NMAP "beginners" tutorial](http://nmap.org/bennieston-tutorial/)

nmap is a port scanner and is very feature rich.

```
nmap -p1-65535 -sV -sS -O ip_address
nmap -PN -sT -sU -p- -sV -O ip_address
```

-p- == -p1-65535
-sT == tcp
-dU == udp

Graphical front ends [Zenmap](http://nmap.org/zenmap/)


[size=4]Ntop[/size]

ntop can be used for network monitoring. It is similar to top , but for network connections.

[ntop](http://www.ntop.org/overview.html)

[How to ntop](http://www.cyberciti.biz/faq/debian-ubuntu-install-ntop-network-traffic-monitoring-software/)

[size=4]Wireshark[/size]

[Network Analysis With Wireshark On Ubuntu 9.10](http://www.howtoforge.com/network-analysis-with-wireshark-on-ubuntu-9.10)

**Please do NOT run wireshark as root !!!**

[Sniffing with Wireshark as a Non-Root User](http://packetlife.net/blog/2010/mar/19/sniffing-wireshark-non-root-user/)

[bodhizazen's wireshark aa profile](http://bodhizazen.net/aa-profiles/bodhizazen/ubuntu-10.04/usr.bin.wireshark)


[size=4]tcpdump[/size]

tcpdump is considered by some to be the defacto gold standard.

[Here is a nice primer on tcpdump](http://danielmiessler.com/study/tcpdump/)


[size=4]psad / fwsnort[/size]

PSAD / fwsnort are light weight alternatives to snort.

[PSAD home page](http://cipherdyne.org/psad/)

From the psad home page:

> psad is a collection of three lightweight system daemons (two main daemons and one helper daemon) that run on Linux machines and analyze iptables log messages to detect port scans and other suspicious traffic.

fwsnort incorporates snort rules into psad.

[fwsnort home page](http://cipherdyne.org/fwsnort/)

[Bodhizazen's psad primer](http://bodhizazen.net/Tutorials/psad)

[Back to top](http://ubuntuforums.org/showthread.php?t=1477696)

---

### Post by bodhi.zazen on 2010-05-09
[size=6][center]Install snort + postgresql + Apache[/size][/center]

The following command will install snort, apache, php5, and postgresql as well as dependencies and some goodies such as oinkmaster.

**[color=darkred]Automatic configuration of snort via apt-get will not work. We need to configure snort, postgresql manually (see the rest of this thread).**[/color]

```
sudo apt-get install -y postgresql apache2 php5 php-pear php5-gd php5-adodb php5-pgsql libphp-adodb snort-pgsql
```

While installing the above packages, you will asked a few questions and given some information. When asked if you would like to configure a database for snort, select no (yes will fail as above, so it does not matter).

You will see post-install configuration instructions, don't worry about that as you complete the installation of the packages, the remainder of this tutorial will cover post-install configuration.

[Back to top](http://ubuntuforums.org/showthread.php?t=1477696)

---

### Post by bodhi.zazen on 2010-05-09
[size=6][center]Configure postgresql and snort[/size][/center]

[size=4]**Configure postgresql[/size]**

First we shall make a database for snort. As you proceed with the configuration you might wish to use alternate database names, database user, and password. For this tutorial I will use :

snort postgresql database = [color=navy]snort_db[/color]
snort postgresql user = [color=navy]snort[/color]
snort posgresql password = [color=navy]snort_password[/color]

```
sudo su postgres
```

**At the postgres user prompt :**

```
# Create the database for snort
createdb snort_db

# Configure the database
zcat /usr/share/doc/snort-pgsql/create_postgresql.gz | psql snort_db

# Create a postgresql user for snort
createuser -P snort
```

Enter and confirm a password for snort, answer n to the next 3 questions :

> Enter password for new user: snort_password
Enter it again: snort_password
Shall the new user be a superuser? (y/n) n
Shall the new user be allowed to create databases? (y/n) n
Shall the new user be allowed to create more new users? (y/n) n

Log into the new database 

```
psql snort_db
```

At the psql prompt ( snort_db=# ) enter ( copy - paste ) the following long command:

[color=blue]**Note: "snort_db=#" indicates the prompt, the command you want to copy-paste starts with "Grant All ..." and ends with a ;[/color]**

```
snort_db=# GRANT ALL ON TABLE data, detail, encoding, event, icmphdr, iphdr, opt, reference, reference_ref_id_seq, reference_system, reference_system_ref_system_id_seq, schema, sensor, sensor_sid_seq, sig_class, sig_class_sig_class_id_seq, sig_reference, signature, signature_sig_id_seq, tcphdr, udphdr TO snort;
```

\q to exit psql

```
snort_db=#\q
```


exit to return to a root shell (exit the "sudo su postgres")
```
exit
```

[size=4]**Configure snort[/size]**

Remove the "db-pending-config" file.

```
cd /etc/snort
sudo rm db-pending-config
```

Using any editor, open /etc/snort/snort.conf

```
sudo nano -B /etc/snort/snort.conf
```

Find and change the following lines:

Use the search function (Ctrl-W) search for "var HOME_NET any" , note HOME_NET is used more then once, you want the line var HOME_NET any , as below ...

Change "var HOME_NET any" to "var HOME_NET 192.168.0.0/16,127.0.0.0/8"
Comment out (add a # in front of) "var EXTERNAL_NET any"
Uncomment (remove the #) "var EXTERNAL_NET !$HOME_NET

so it looks similar this:

```
var HOME_NET 192.168.0.0/24,127.0.0.0/8
#var EXTERNAL_NET any
var EXTERNAL_NET !$HOME_NET
```

[color=blue]You may need to change "192.168.0.0/24" to a range appropriate for your LAN.[/color]

Next, find the line "output database: alert, postgresql ...."

_Hint_: Search as above for "localhost" .

Uncomment (remove the #) the line and update it to include the database and user you set up.

```
output database: alert, postgresql, user=snort dbname=snort_db password=snort_password host=localhost
```


Save the file and close nano (Ctrl-X , when asked to save answer yes).

You can test snort with the following command :

```
sudo snort -c /etc/snort/snort.conf -T
```

[color=navy]**If you see the ascii pig, it is working![/color]**


>         --== Initialization Complete ==--

   ,,_     -*> Snort! <*-
  o"  )~   Version 2.8.5.2 (Build 121)  
   ''''    By Martin Roesch & The Snort Team: [http://www.snort.org/snort/snort-team](http://www.snort.org/snort/snort-team)
           Copyright (C) 1998-2009 Sourcefire, Inc., et al.
           Using PCRE version: 7.8 2008-09-05
		   
<clip>

Snort successfully loaded all rules and checked all rule chains !
database: Closing connection to database "snort_db"
Snort exiting

**[color=darkred]YOU DO NOT NEED TO DO ANYTHING ELSE TO "TEST SNORT" !!!![/color]**

[Back to top](http://ubuntuforums.org/showthread.php?t=1477696)

---

### Post by bodhi.zazen on 2010-05-09
[SIZE=6][CENTER]Install && Configure base[/CENTER]
[/SIZE]
BASE is a web based graphical front end for snort alerts.

[About BASE]("http://base.secureideas.net/about.php")
[BASE screen shots]("http://base.secureideas.net/screens.php")

**[size=4]Download and extract BASE[/size]**

```
cd /var/www
sudo wget http://sourceforge.net/projects/secureideas/files/BASE/base-1.4.5/base-1.4.5.tar.gz/download
sudo tar xvf base-1.4.5.tar.gz
sudo rm base-1.4.5.tar.gz
sudo mv base-1.4.5 base
sudo chown -R www-data.www-data base
```[SIZE=4]**Configure php**[/SIZE]

Open /etc/php5/apache2/php.ini

```
sudo nano -B /etc/php5/apache2/php.ini
```change the line: 
error_reporting = E_ALL & ~E_DEPRECIATED

to:
> error_reporting = E_ALL & ~E_NOTICESave and close nano.

**[SIZE=4]Install a few pear modules[/SIZE]**

```
sudo pear install Image_Color Image_Canvas-alpha Image_Graph-alpha Mail Mail_Mime
```**[SIZE=4]Restart apache[/SIZE]**

```
sudo service apache2 restart
```**[SIZE=4]Configure BASE via the web interface[/SIZE]**

Open a web browser and go to your snort ip_address/base

Follow the instructions (**click on the thumbnails for a larger image**):

_Step 1_: Confirm your base directory is writeable by apache.

[[IMG]http://bodhizazen.net/img/Base/Base1_thumb.png[/IMG]]("http://bodhizazen.net/img/Base/Base1.png")

If all is well (no error messages) click "Continue".

_Step 2_: Enter the path to ADODB /usr/share/php/adodb .

[[IMG]http://bodhizazen.net/img/Base/Base2_thumb.png[/IMG]]("http://bodhizazen.net/img/Base/Base2.png")

Click "Continue"

_Step3_: Postgresql .

Enter the appropriate values

Database type -> Select "PostgreSQL" from the pull down menu.
Dataase Name -> snort
Database Host -> localhost
Database Port -> leave blank
Database User Name -> snort
Database Password -> snort_password

[[IMG]http://bodhizazen.net/img/Base/Base3_thumb.png[/IMG]]("http://bodhizazen.net/img/Base/Base3.png")

Click "Continue"


_Step 4_: Set user authentication.

I encourage you to say "yes" and set up a user and password.

[[IMG]http://bodhizazen.net/img/Base/Base4_thumb.png[/IMG]]("http://bodhizazen.net/img/Base/Base4.png")


_Step 5_: Create database .

Click "Create BASE AG" button on the right

[[IMG]http://bodhizazen.net/img/Base/Base5_thumb.png[/IMG]]("http://bodhizazen.net/img/Base/Base5.png")


_Step 6_: You should see this screen -

[[IMG]http://bodhizazen.net/img/Base/Base6_thumb.png[/IMG]]("http://bodhizazen.net/img/Base/Base6.png")

Click "step 5..." at the bottom

_Step 7_: Log in to base .

[[IMG]http://bodhizazen.net/img/Base/Base7_thumb.png[/IMG]]("http://bodhizazen.net/img/Base/Base7.png")


You should now see Base:

[[IMG]http://bodhizazen.net/img/Base/Base8_thumb.png[/IMG]]("http://bodhizazen.net/img/Base/Base8.png")


[COLOR=darkred]**So long as you see the line "Sensors/Total 0/1" snort and base are working!!!**[/COLOR]

**[SIZE=4]Bonus : Change the theme[/SIZE]**

You can list your available themes with

```
ls /var/www/base/styles
```Open /var/www/base/base_conf.php

```
sudo nano -B /var/www/base/base_conf.php
```Find the line 
$base_style ="base_default_style.css"

And change it to what you like (I prefer black or red).

```
$base_style ="base_red_style.css"
```[Back to top]("http://ubuntuforums.org/showthread.php?t=1477696")

---

### Post by bodhi.zazen on 2010-05-09
[size=6][center]Update Snort Rules[/size][/center]

There are basically two ways to update your snort rules.

**[color=darkred]You must register with snort (on the website) to obtain an updated set of rules.**[/color]

[Download Snort Rules](http://www.snort.org/snort-rules/)

Please note there are two types of "Registration" :

**Users new to snort often find the registration process confusing.**

1. Subscription Release : This is _fee for service_ and subscription users have immediate access to new rules.

2. Registered-user-release : **This is FREE , but there is a 30 day delay between when a rule set is released and is available to registered users.**

> Registered Users
Registered users of Snort.org are able to download and use VRT rules **free of charge** 30 days after their initial release date.

Emphasis added by me =)

**[size=2]Manual update[/size]**

After registering with snort, you download snortrules-snapshot-CURRENT.tar.gz 

You can extract it with

tar xvf snortrules-snapshot-CURRENT.tar.gz

This will give you several directories including rules , so_rules , and doc

- rules -

This directory contains the updated set of rules.

Simply copy them to /etc/snort/rules

```
sudo cp rules/* /etc/snort/rules
```

- doc -

This directory contains documentation. We are most interested in the signatures.

The signatures are explanations of the alerts and can be used by BASE

Copy the signatures to the base directory (for alerts)

```
sudo cp -R doc/signatures /var/www/base/
sudo chown -R www-data.www-data /var/www/base/signatures
```

- so_rules -

You can also configure the .so rules (see below)

See Oinkmaster below for how to automate the process.


[size=6][center]Oinkmaster - Automagic[/size][/center]

Oinkmaster automates the process of updating your rules, but takes a few minutes to configure.

See /usr/share/doc/oinkmaster/README.Debian

```
apt-get install libio-zlib-perl
```

Register with snort and obtain an oink code :

[http://www.snort.org/](http://www.snort.org/)
[http://oinkmaster.sourceforge.net/install.shtml](http://oinkmaster.sourceforge.net/install.shtml)
[http://oinkmaster.sourceforge.net/](http://oinkmaster.sourceforge.net/)
[http://oinkmaster.cvs.sourceforge.net/oinkmaster/oinkmaster/FAQ?view=markup](http://oinkmaster.cvs.sourceforge.net/oinkmaster/oinkmaster/FAQ?view=markup)

Log into the snort website, click the "My Account" tab -> "Subscriptions and Oinkcodes" tab.


You then edit /etc/oinkmaster.conf , update the url line to read

http://www.snort.org/pub-bin/oinkmaster.cgi/<your oink code here>/snortrules-snapshot-2.8.tar.gz

To run oinkmaster and update your snort rules run the following commands :

```
sudo bash -c "/usr/share/oinkmaster/makesidex.pl /etc/snort/rules/ >/etc/autodisable.conf"
sudo oinkmaster -C /etc/oinkmaster.conf -C /etc/autodisable.conf -o /etc/snort/rules/
```

Output looks like this :

> Loading /etc/oinkmaster.conf
Loading /etc/autodisable.conf
Downloading file from [http://www.snort.org/pub-bin/oinkmaster.cgi/*oinkcode*/snortrules-snapshot-2.8.tar.gz](http://www.snort.org/pub-bin/oinkmaster.cgi/*oinkcode*/snortrules-snapshot-2.8.tar.gz)... done.

< clip>oinkmaster will give you a long output, especially the first time you run it ...< /clip>


[+] Added files (consider updating your snort.conf to include them if needed): [+]

    -> content-replace.rules
    -> open-test.confDownloading file from [http://www.snort.org/pub-bin/oinkmaster.cgi/*oinkcode*/snortrules-snapshot-2.8.tar.gz](http://www.snort.org/pub-bin/oinkmaster.cgi/*oinkcode*/snortrules-snapshot-2.8.tar.gz)... done.

< clip>oinkmaster will give you a long output, especially the first time you run it ...< /clip>


[+] Added files (consider updating your snort.conf to include them if needed): [+]

    -> content-replace.rules
    -> open-test.conf
    -> scada.rules
    -> specific-threats.rules
    -> spyware-put.rules
    -> voip.rules
    -> VRT-License.txt

At the bottom of /etc/snort.conf you will see a number of "include" statements. These instruct snort which rules to use.

You may activate/inactivate rule sets by adding or removing the # or adding new include statements.

With the above output I added content-replacement.rules , scada.rules , spcific-threats.rules , spyware-put.rules, and voip.rules

[Back to top](http://ubuntuforums.org/showthread.php?t=1477696)

---

### Post by bodhi.zazen on 2010-05-09
[size=6][center]so_rules[/size][/center]

See : [http://www.snort.org/snort-rules/about-so_rules](http://www.snort.org/snort-rules/about-so_rules)

To add these rules you will need to download the current snort rules and performs some additional configuration.

When you extract the snort rules you will find a so_rules directory.

Using any editor, open /etc/snort/snort.conf and uncomment add/edit the following lines (use the search function of your editor to find the lines)

> dynamicpreprocessor directory /usr/lib/snort_dynamicpreprocessor/
dynamicengine /usr/lib/snort_dynamicengine/libsf_engine.so
dynamicdetection directory /usr/lib/snort_dynamicrule/

Watch the syntax , there is a /usr/lib/snort_dynamicrule and /usr/lib/snort_dynamicrules (with an s).

```
mkdir -p /usr/lib/snort_dynamicrule
```

*.so rules are precomiled and depend on if you are running 32 (i686) or 64 (x86_64) bit. See so_rules/src/README for details:

i686: ```
sudo cp so_rules/precompiled/Debian-Lenny/i386/2.8.5.1/*.so /usr/lib/snort_dynamic_rule
```

x86_64: ```
sudo cp so_rules/precompiled/Ubuntu-8.04/x86_64/2.8.5.1/*.so /usr/lib/snort_dynamic_rule
```


```
sudo mkdir /etc/snort/so_rules
sudo snort -c /etc/snort/snort.conf --dump-dynamic-rules=/etc/snort/so_rules
```

This last command will generate the rules in /etc/snort/so_rules.

Next we need to configure snort to use these rules:

Open /etc/snort/snort.conf with any editor,

```
gksu gedit /etc/snort/snort.conf
```

Add this line to the end of /etc/snort/snort.conf
> var SO_RULE_PATH /etc/snort/so_rules

I next added all the so_rules with a script :

```
sudo -i
for i in `ls /etc/snort/so_rules`;do echo include '$SO_RULE_PATH/'${i} >> /etc/snort/snort.conf; done
```

Test with snort -c /etc/snort/snort.conf -T

Note you will get "Warnings" (flowbits key) which can be ignored or disabled :

[http://www.winsnort.com/index.php?name=PNphpBB2&file=viewtopic&p=3356](http://www.winsnort.com/index.php?name=PNphpBB2&file=viewtopic&p=3356) 

[Back to top](http://ubuntuforums.org/showthread.php?t=1477696)

---

### Post by bodhi.zazen on 2010-05-09
[size=6][center]- Testing snort - [/size][/center]

Despite all I have told you , if you *still* wish to test snort , lets make some noise ...

If you installed Base, log in to the web interface as above.

On the home page you will see a line "Sensors/Total 0/1"

The first number, 0 , is the number of sensors that have generated an alert. So long as the second number is 1 or greater you are good to go. If the second number, Total, is zero (0), restart snort and reload your base page.

_Note_: If you clear your alerts (in BASE), you will need to restart snort.

```
nmap -p1-65535 -sV -sS -O snort_ip_address
```

You will see some new alerts :lolflag:

_Note_: You do NOT need to turn your firewall off to generate alerts.

[Back to top](http://ubuntuforums.org/showthread.php?t=1477696)

---

### Post by bodhi.zazen on 2010-05-09
[size=6][center]Where to go from here[/size][/center]

[size=4]**Snort rules**[/size]

Understanding and managing snort rules / alerts takes some time and experience.

Log into base. Chances are you will see one or more alerts.

Click on the alerts and you will see more detailed information. The [snort] box contains a link to the snort web site explaining the alerts in more detail. If you copied the signatures directory (from the snort rules) to /var/www/base you will see a [local] where you can view the same information from your local server.

You may need to use google to research the alerts / vulnerabilities further =)

Other then the above advice , managing snort rules is beyond this post and is somewhat of an art.

You may disable rules by commenting them out and re-starting snort.

You may modify rules by editing the *.rules file.

You should probably at least read [this link](http://packetstormsecurity.nl/papers/IDS/snort_rules.htm) .

[size=4]**Responding to alerts**[/size]

Blacklisting an IP address

Keep in mind snort generates a large number of false positives. Your first task should be simply to watch the alerts and get a sense of what is "Normal".

Personally I blacklist ip addresses that:

1. The server/desktop may be vulnerable to (ie mysql injections). You will notice a number of alerts for non-Linux OS (which helps if you are monitoring a LAN with mixed Windows/Linux desktops/servers). After discovering a potential vulnerability you need to check you HIDS to determine if you were compromised ...

2. Persistent IP addresses. For example, they may start with a port scan then proceed to additional attack vectors.

3. Continued alerts from an ip address over hours, days, or weeks (ie "slow attack").

[Back to top](http://ubuntuforums.org/showthread.php?t=1477696)

---

