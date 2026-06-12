---
title: "Snort Mysql &amp; Base on Feisty"
date: 2007-06-24
forum: Tutorials
---

### Post by djhedges on 2007-06-24
I just installed a clean version of Feisty and since people were still using my old guide I'm going to create a new one for Feisty.  The old one can be found here.
[http://ubuntuforums.org/showthread.php?t=145641]("http://ubuntuforums.org/showthread.php?t=145641")

Start by switching to root because it's tedious to keep retyping sudo.
```
sudo -i
```

Update your system.  I had 60+ packages to update and it took about 10min or so.
```
apt-get update
apt-get upgrade
```

Install Snort with Mysql support.
```
apt-get install snort-mysql
```
It will ask about configuring snort to detect a certain network.  Replace this with any and it will inspect all the packets the sensor receives.  I'll show you later where you can change this in the future if you needed to.  Next it'll ask about setting up a database, just say no and we'll do it by hand later.

Before testing snort lets go ahead and install oinkmaster.  Oinkmaster is a cool tool which keeps your snort rules updated.
```
apt-get install oinkmaster
```
Now you'll need to edit the oinkmaster config file which is located /etc/oinkmaster.conf I would recommend going to snort.org and registering so you can obtain an oinkcode.
Replace
```
url = http://www.snort.org/dl/rules/snortrules-snapshot-2_2.tar.gz
```
with
url```
url = http://www.snort.org/pub-bin/oinkmaster.cgi/5a08f649c16a278e1012e1c84bdc8fab9a70e2a4/snortrules-snapshot-2.3.tar.gz
```
Make sure you replace 5a08f649c16a278e1012e1c84bdc8fab9a70e2a4 with your oink code and pay attention to which snort version your using.  In my example my snort is version 2.3.
To find your snort version.
```
snort -V
```

Update the snort rules.
```
oinkmaster -o /etc/snort/rules/
```
I recommend creating a crontab so your rules automatically update.

Lets take a look at the snort.conf file
```
nano -w /etc/snort/snort.conf
```
var HOME_NET any
Is what we configured early during the snort install.  Make sure you have a line that isn't commented (meaning no # in the front of it)
```
output log_tcpdump: tcpdump.log
```

See if snort is running
```
pgrep -l snort
```
If it's not start it with 
```
/etc/init.d/snort start
```
If you get an error about a db-pending-config then 
```
rm /etc/snort/db-pending-config
```

Lets see if snort is working properly by tailing the log file.  If you see it change or any logs at all then snort should be working fine.
```
tail -f /var/log/snort/alert
```
Windows PCs on the same network triggered my snort but you could always do a port scan from another computer using nmap (it won't do anything to run nmap on it's self.)
```
nmap -sX your_snort_ip_address
```
I believe this only works if you have at least one open port.  For this I installed ssh.
```
apt-get install ssh
```
The alert file should say something about an XMAS scan.  Press ctrl + c to kill the tail command.

Lets install msyql, it'll take a few minutes.
```
apt-get install mysql-server
```
Edit the snort.conf
```
nano -w /etc/snort/snort.conf
```
Comment out the output log_tcmpdump: tcpdump.log so it looks like
```
# output log_tcpdump: tcpdump.log
```
Change
```
# output database: log, mysql, user=root password=test dbname=db host=localhost
```
to, make sure you use something other then SNORT_PASSWORD, we'll set it in a minute.  And pay attention tot he dbname=snort.
```
output database: log, mysql, user=snort password=SNORT_PASSWORD dbname=snort host=localhost
```

I followed Patrick's Centos guide for the following because I barely understand mysql.  You can find his guide here.  Good info, even if your not using centos.
```
http://www.snort.org/docs/setup_guides/snort_base_SSL.pdf
```
```
mysql -u root
set password for root@localhost=password('PICK_A_PASSWORD');
create database snort;
grant insert,select on root.* to snort@localhost;
set password for snort@localhost=password('PASSWORD_SNORT_CONF');
grant create,delete,insert,select,update on snort.* to snort@localhost;
grant create,delete,insert,select,update on snort.* to snort;
exit
```

Lets setup the database for snort by uncompressing it and then importing it
```
gunzip /usr/share/doc/snort-mysql/create_mysql.gz
mysql -u root -p < /usr/share/doc/snort-mysql/create_mysql snort
```

Restart Snort
```
/etc/init.d/snort restart
```

Now lets grab what we need for BASE such as apache & php.
```
apt-get install apache2 php5-mysql libphp-adodb
```

Download the latest version of BASE from
[http://base.secureideas.net/]("http://base.secureideas.net/")
Extract BASE & Move BASE
```
tar -xvzf /home/username/Desktop/base-1.3.6.tar.gz
mv base-1.3.6 /var/www/base
```

Copy & Edit the BASE config
```
cd /var/www/base
cp base_conf.php.dist base_conf.php
nano -w  base_conf.php
```
Look for these lines and change so their similiar
```
$Base_urlpath = “/base”
$Dblib_path = “/usr/share/adodb/”;
$alert_dbname = 'snort';
$alert_password = 'SNORT_PASSWORD';
```

I had to restart apache before getting to BASE
```
/etc/init.d/apache2 restart
Open firefox & goto localhost/base
```
Click on the setup page link and then the Create BASE AG button
BASE should be working now.

Lets get the graphing to work
```
apt-get install php5-gd php-pear
pear install Image_Color
pear install Image_Canvas-alpha
pear install Image_Graph-alpha
```
Restart apache
```
/etc/init.d/apache2 restart
```

One more thing to look at before your done is the /etc/snort/threshold.conf.  This file can be used to limit and suppress alerts you don't want to see.  I get a lot of false positives from samba and normal windows traffic.  I'm not worried about local traffic so I can suppress my network but still generate alerts if someone out side was connecting by adding a line like so.  The config should be self explanatory.
```
suppress gen_id 1 sig_id 2466, track by_src, ip 192.168.1.0/24
```

Good luck and have fun.

---

### Post by tegwilym on 2007-06-29
Thanks for posting that guide.  I got it up and running - at least I got through all the steps without any mysterious error  messages.  
Now I just have to figure out how this Snort/Base thing works.   :p

Tom
-Former XP user.  Hehe!

---

### Post by erwall on 2007-06-29
I'm getting this on the graphs page:

Error loading the Graphing library:

Check your Pear::Image_Graph installation!

Image_Graph can be found here:at [http://pear.veggerby.dk/](http://pear.veggerby.dk/). Without this library no graphing operations can be performed.

and "pear list" yields this:

Installed packages, channel pear.php.net:
=========================================
Package        Version State
Archive_Tar    1.3.2   stable
Console_Getopt 1.2     stable
Image_Canvas   0.3.1   alpha
Image_Color    1.0.2   stable
Image_Graph    0.7.1   alpha
Log            1.9.11  stable
Numbers_Roman  0.2.0   stable
Numbers_Words  0.13.1  beta
PEAR           1.4.11  stable

any ideas?

---

### Post by djhedges on 2007-06-30
> **erwall said:**
> I'm getting this on the graphs page:

Error loading the Graphing library:

Check your Pear::Image_Graph installation!

Image_Graph can be found here:at [http://pear.veggerby.dk/](http://pear.veggerby.dk/). Without this library no graphing operations can be performed.

and "pear list" yields this:

Installed packages, channel pear.php.net:
=========================================
Package        Version State
Archive_Tar    1.3.2   stable
Console_Getopt 1.2     stable
Image_Canvas   0.3.1   alpha
Image_Color    1.0.2   stable
Image_Graph    0.7.1   alpha
Log            1.9.11  stable
Numbers_Roman  0.2.0   stable
Numbers_Words  0.13.1  beta
PEAR           1.4.11  stable

any ideas?

Interesting, have you tried restarting apache?

---

### Post by erwall on 2007-07-01
Yep, sure have, a few times...

---

### Post by KyleBrandt on 2007-07-02
After running

```
 /etc/init.d/snort start
```

I get:

```
Starting Network Intrusion Detection System: snort(eth0)No /etc/snort/snort.eth0.conf, defaulting to snort.conf
.

```

However, it doesn't appear to be running after I type: 

```
pgrep -l snort
```

I don't really know what my next step in troubleshooting should be since I have no error to work with, unless that period is an error?  Anyone have any ideas?  Thanks..

---

### Post by djhedges on 2007-07-02
> **erwall said:**
> Yep, sure have, a few times...

I remember a similar problem but it was a long time ago.  I think I fixed it by reinstalling some packages such as php or pear.  It's been a long time and I can't remember exactly which ones I removed and reinstalled.

---

### Post by djhedges on 2007-07-02
> **djhedges said:**
> I remember a similar problem but it was a long time ago.  I think I fixed it by reinstalling some packages such as php or pear.  It's been a long time and I can't remember exactly which ones I removed and reinstalled.

Have you looked at the log files?  I'm school so I don't have access to my laptop but check in /var/log/messages and some like /var/log/snort

---

### Post by tegwilym on 2007-07-03
Ok, I thought I had it all running, but now finding that I'm close, but not quite there just yet. 

At the command line, I enter: 
  snort -b -i eth0 -A fast -N -c /etc/snort/snort.conf

(I leave out the -D so I can see what happens)

I get this, which looks all fine, until I get to the very end and see the message saying:
[B][I]  command line overrides rules file alert plugin!
  ERROR: Suppress-Parse: incorrect argument count
  Fatal Error, Quitting..[/I][/B]
 
So Snort doesn't seem to be running at all.  The computer is on a DMZ port through the router exposed to raw, nasty, unfiltered interenet.  I figure that is the best way to see something actually happen!

Here is the full output of the above command. 

  root@satellite:/etc/snort# snort -b -i eth0 -A fast -N -c /etc/snort/snort.conf
Running in IDS mode

Initializing Network Interface eth0

        --== Initializing Snort ==--
Initializing Output Plugins!
Decoding Ethernet on interface eth0
Initializing Preprocessors!
Initializing Plug-ins!
Parsing Rules file /etc/snort/snort.conf

+++++++++++++++++++++++++++++++++++++++++++++++++++
Initializing rule chains...
,-----------[Flow Config]----------------------
| Stats Interval:  0
| Hash Method:     2
| Memcap:          10485760
| Rows  :          4099
| Overhead Bytes:  16400(%0.16)
`----------------------------------------------
No arguments to frag2 directive, setting defaults to:
    Fragment timeout: 60 seconds
    Fragment memory cap: 4194304 bytes
    Fragment min_ttl:   0
    Fragment ttl_limit: 5
    Fragment Problems: 0
    Self preservation threshold: 500
    Self preservation period: 90
    Suspend threshold: 1000
    Suspend period: 30
Stream4 config:
    Stateful inspection: ACTIVE
    Session statistics: INACTIVE
    Session timeout: 30 seconds
    Session memory cap: 8388608 bytes
    State alerts: INACTIVE
    Evasion alerts: INACTIVE
    Scan alerts: INACTIVE
    Log Flushed Streams: INACTIVE
    MinTTL: 1
    TTL Limit: 5
    Async Link: 0
    State Protection: 0
    Self preservation threshold: 50
    Self preservation period: 90
    Suspend threshold: 200
    Suspend period: 30
    Enforce TCP State: INACTIVE
    Midstream Drop Alerts: INACTIVE

Stream4_reassemble config:
    Server reassembly: INACTIVE
    Client reassembly: ACTIVE
    Reassembler alerts: ACTIVE
    Zero out flushed packets: INACTIVE
    flush_data_diff_size: 500
    Ports: 21 23 25 53 80 110 111 143 513 1433 
    Emergency Ports: 21 23 25 53 80 110 111 143 513 1433 
HttpInspect Config:
    GLOBAL CONFIG
      Max Pipeline Requests:    0
      Inspection Type:          STATELESS
      Detect Proxy Usage:       NO
      IIS Unicode Map Filename: /etc/snort/unicode.map
      IIS Unicode Map Codepage: 1252
    DEFAULT SERVER CONFIG:
      Ports: 80 8080 8180 
      Flow Depth: 300
      Max Chunk Length: 500000
      Inspect Pipeline Requests: YES
      URI Discovery Strict Mode: NO
      Allow Proxy Usage: NO
      Disable Alerting: NO
      Oversize Dir Length: 500
      Only inspect URI: NO
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
rpc_decode arguments:
    Ports to decode RPC on: 111 32771 
    alert_fragments: INACTIVE
    alert_large_fragments: ACTIVE
    alert_incomplete: ACTIVE
    alert_multiple_requests: ACTIVE
telnet_decode arguments:
    Ports to decode telnet on: 21 23 25 119 
Portscan Detection Config:
    Detect Protocols:  TCP UDP ICMP IP
    Detect Scan Type:  portscan portsweep decoy_portscan distributed_portscan
    Sensitivity Level: Low
    Memcap (in bytes): 10000000
    Number of Nodes:   36900

X-Link2State Config:
    Ports: 25 691 
command line overrides rules file alert plugin!
ERROR: Suppress-Parse: incorrect argument count
Fatal Error, Quitting..

---

### Post by Spudgun on 2007-07-04
Good tutorial, just a couple of points though -


1. You forgot to mention that the user need to update /etc/snort/snort.conf with his/her chosen DB password;

2. In the BASE config ```
$Dblib_path = “/usr/share/adodb/”;
``` should be ```
$Dblib_path = “/usr/share/php/adodb/”;

```

3. Suppression rules should ideally be placed in /etc/snort/threshold.conf

---

### Post by Spudgun on 2007-07-20
> **tegwilym said:**
> Ok, I thought I had it all running, but now finding that I'm close, but not quite there just yet. 

At the command line, I enter: 
  snort -b -i eth0 -A fast -N -c /etc/snort/snort.conf

(I leave out the -D so I can see what happens)

I get this, which looks all fine, until I get to the very end and see the message saying:
[B][I]  command line overrides rules file alert plugin!
  ERROR: Suppress-Parse: incorrect argument count
  Fatal Error, Quitting..[/I][/B]

In **/etc/snort/threshold.conf**, change the 4 digit number after 'sig_id' to 1852. That should solve your problem.

---

### Post by weth on 2007-07-23
Hi, I have the same problem as Miles800

after:

 ```
/etc/init.d/snort start
```

I get:

Code:

```
Starting Network Intrusion Detection System: snort(eth0)No /etc/snort/snort.eth0.conf, defaulting to snort.conf
.
```


What can I do to fix it? It seems I'm very close...

thanks :)

---

### Post by tegwilym on 2007-07-23
I did get mine running.  BASE, Snort, Ntop are all running now.
I just don't see a whole lot of activity in the BASE application though.  Of course this computer here at work is behind a firewall, so that's probably a good thing. 

I have a computer at home on the DMZ through my router, and I expected to see more in the BASE page, but there isn't much there either.  Its fully exposed to all the filth and nastiness of the internet also, so I thought I would see more.  

...of course maybe it's time that I start reading the Snort manual!   :)

Oh, I tried all this using Ubutnu 7.04 SPARC sever version on a Sunfire V100.  I couldn't get Ntop to start.  I always got a "Bus Error".  It seems to be a known issue from what I've found, and there doesn't seem to be a fix for that yet.  I'll stick with a normal x86 type machine for now. 

Tom

---

### Post by djhedges on 2007-07-24
> **weth said:**
> Hi, I have the same problem as Miles800

after:

 ```
/etc/init.d/snort start
```

I get:

Code:

```
Starting Network Intrusion Detection System: snort(eth0)No /etc/snort/snort.eth0.conf, defaulting to snort.conf
.
```


What can I do to fix it? It seems I'm very close...

thanks :)

The way snort is designed you can have multiple configs for different interfaces.  If snort doesn't find a config for a particular interface then it will default to /etc/snort/snort.conf.  If you don't want to see that message theres two things you can do.  I bet your snort is running even with that message.

See if snort is running
```
pgrep -l snort
```

Make a Copy of the default config (edit it if desired)
```
cp /etc/snort/snort.conf /etc/snort/snort.eth0.conf
```

Create a symbolic link (like a shortcut)
```
ln -s /etc/snort/snort.conf /etc/snort/snort.eth0.conf
```

---

### Post by djhedges on 2007-07-24
> **tegwilym said:**
> I did get mine running.  BASE, Snort, Ntop are all running now.
I just don't see a whole lot of activity in the BASE application though.  Of course this computer here at work is behind a firewall, so that's probably a good thing. 

I have a computer at home on the DMZ through my router, and I expected to see more in the BASE page, but there isn't much there either.  Its fully exposed to all the filth and nastiness of the internet also, so I thought I would see more.  

...of course maybe it's time that I start reading the Snort manual!   :)

Oh, I tried all this using Ubutnu 7.04 SPARC sever version on a Sunfire V100.  I couldn't get Ntop to start.  I always got a "Bus Error".  It seems to be a known issue from what I've found, and there doesn't seem to be a fix for that yet.  I'll stick with a normal x86 type machine for now. 

Tom

What is NTOP?

To test snort the easiest thing I found was to use the default logging method which was log files.  (This eliminates mysql, apahce & php problems.)

Run a port scan from another computer using nmap.  If you have the sensor scan itself it won't show anything.  You should see something in /var/log/snort/alert.
```
nmap -sX your_snort_ip_address
```

If you don't see anything I would check iptables, make sure snort is running and then check the snort config.  Make sure it's including the port scan rules and make sure your rules are installed correctly.

---

### Post by tegwilym on 2007-07-24
What is NTOP?.

[B]Look at [http://www.ntop.org/](http://www.ntop.org/)
It shows nice tables and graphs of all kinds of information that goes back and forth on the network.  I'm not sure what it all means yet, but I'm working on it!

[/B]


Run a port scan from another computer using nmap.  If you have the sensor scan itself it won't show anything.  You should see something in /var/log/snort/alert.
```
nmap -sX your_snort_ip_address
```
[B]
I've done - nmap localhost - as a check that I have snort running and it is listening on the port (I forget the number right off hand, but it does say "snort" so I know it's running).

Good idea on the port scan to the IP address, I didn't know that.  I'll try that![/B]


If you don't see anything I would check iptables, make sure snort is running and then check the snort config.  Make sure it's including the port scan rules and make sure your rules are installed correctly

[B]I think it's running, and there is something showing up in the alert log ok.  Even if snort isn't running the BASE page will come up which can be a little confusing, but of course that is just coming from apache anyway, and it won't do anything if snort isn't doing something in the background.  I just want to figure out how to see more on BASE since that would be easier than looking at the confusing alert files. 

Hmm....might be time to ask the company if I can buy a Snort for Dummies book!
Forums are great, but maybe if I read through all the steps more it could help too.

Fun stuff though!

Tom[/B]

---

### Post by djhedges on 2007-07-25
> **tegwilym said:**
> What is NTOP?.

[B]Look at [http://www.ntop.org/](http://www.ntop.org/)
It shows nice tables and graphs of all kinds of information that goes back and forth on the network.  I'm not sure what it all means yet, but I'm working on it!

[/B]


Run a port scan from another computer using nmap.  If you have the sensor scan itself it won't show anything.  You should see something in /var/log/snort/alert.
```
nmap -sX your_snort_ip_address
```
[B]
I've done - nmap localhost - as a check that I have snort running and it is listening on the port (I forget the number right off hand, but it does say "snort" so I know it's running).

Good idea on the port scan to the IP address, I didn't know that.  I'll try that![/B]


If you don't see anything I would check iptables, make sure snort is running and then check the snort config.  Make sure it's including the port scan rules and make sure your rules are installed correctly

[B]I think it's running, and there is something showing up in the alert log ok.  Even if snort isn't running the BASE page will come up which can be a little confusing, but of course that is just coming from apache anyway, and it won't do anything if snort isn't doing something in the background.  I just want to figure out how to see more on BASE since that would be easier than looking at the confusing alert files. 

Hmm....might be time to ask the company if I can buy a Snort for Dummies book!
Forums are great, but maybe if I read through all the steps more it could help too.

Fun stuff though!

Tom[/B]

If your seeing traffic in the snort alert log files then you need to edit the config & setup mysql.

Right now it's logging to a file.  In order for base to work it needs to log to a database.

---

### Post by vaineh on 2007-07-30
followed the guide to the letter but nothing is being logged in the alert logfile. did an nmap from another machine on the network and it showed me what ports were open. 

any pointers on what i should be checking?

---

### Post by draven on 2007-07-30
Also stuck with no running snort. No errors, no logs, nada.

```

root@bobo:/etc/snort# /etc/init.d/snort restart
Stopping Network Intrusion Detection System: snort(eth0).
Starting Network Intrusion Detection System: snort(eth0)No /etc/snort/snort.eth0.conf, defaulting to snort.conf
.
root@bobo:/etc/snort# /etc/init.d/snort config-check
checking  config: (eth0)...failed.

```

Also, is it possible to not specify an interface so it will monitor all? I'm not sure if leaving "DEBIAN_SNORT_INTERFACE" blank in snort.debian.conf would do it. Since I can't get snort to run, I don't know.

---

### Post by draven on 2007-07-30
Figured it out. Ubuntu uses some customizations from Debian. Inside /etc/snort/snort.conf is the following:

```

# <debian>
# Keep your paws off of these (#DBSTART#) and (#DBEND#) tokens
# or you *will* break the configure process (snort-pgsql/snort-mysql only)
# Anything you put between them will be removed on (re)configure.
# 
# (#DBSTART#)
output database: log, mysql,
# (#DBEND#) 
# 
# </debian>

```

These were lines 502 to 511 for me. You need to comment out the "output database: log, mysql" line, and then you can run snort as he describes. Once you have completed this and verified that /var/log/snort/alert is created, you can continue on. I assume you may want to reenable this line after moving forward. I'm starting that process now.

---

### Post by tegwilym on 2007-07-30
Ok, I'm making progress on this.  Snort is running, Ntop (not on the Sparc machine though), BASE, and SnortSnarf.  
I was going to install "Acid" until I realized that it was just the same thing as BASE (Kind of like chemistry, heh!).  
Anyway, just one thing left that I would like to get working.  I can't get the graphs to work in BASE.  When I try it, a little 'broken' .jpg icon shows up instead. 

I do have Pear and the graphics add-ons installed, but still not getting any pretty pictures.  Anyone else run into this problem?

Tom

---

### Post by djhedges on 2007-07-30
> **tegwilym said:**
> Ok, I'm making progress on this.  Snort is running, Ntop (not on the Sparc machine though), BASE, and SnortSnarf.  
I was going to install "Acid" until I realized that it was just the same thing as BASE (Kind of like chemistry, heh!).  
Anyway, just one thing left that I would like to get working.  I can't get the graphs to work in BASE.  When I try it, a little 'broken' .jpg icon shows up instead. 

I do have Pear and the graphics add-ons installed, but still not getting any pretty pictures.  Anyone else run into this problem?

Tom

I remember having a problem with the graphs which I fixed by reinstalling different things such as the pear packages & php.  It's been a long time so I can't exactly remember what fixed it.

You could try looking for a similar problem with pear not base or snort specific.

---

### Post by tegwilym on 2007-07-31
> **djhedges said:**
> 
You could try looking for a similar problem with pear not base or snort specific.

Good idea.  BASE isn't the only thing that would use that.  I did try reinstalling everything, and often it said "already the most current version"  - or something like that, so I know it's there.  Just doesn't make any graphs.  :confused:

---

### Post by vaineh on 2007-07-31
mines a different problem.

snort looks to be running fine, from ps:
/usr/sbin/snort -m 027 -D -d -l /var/log/snort -u snort -g snort -c /etc/snort/snort.conf -S HOME_NET=[any] -i eth0

but nothing is getting logged in the alert log. all my rules are included, out puts set.

---

### Post by djhedges on 2007-07-31
> **tegwilym said:**
> Good idea.  BASE isn't the only thing that would use that.  I did try reinstalling everything, and often it said "already the most current version"  - or something like that, so I know it's there.  Just doesn't make any graphs.  :confused:

Open up synaptic and first do a complete removal of some parts such as the pear & php.  Then install them again.

---

### Post by djhedges on 2007-07-31
> **vaineh said:**
> mines a different problem.

snort looks to be running fine, from ps:
/usr/sbin/snort -m 027 -D -d -l /var/log/snort -u snort -g snort -c /etc/snort/snort.conf -S HOME_NET=[any] -i eth0

but nothing is getting logged in the alert log. all my rules are included, out puts set.

I would focus on modifying the config instead passing options to the command line such as the HOME_NET variable or where the logs are logged to.  Theres way you can stop & start snort with
```
/etc/init.d/snort start
/etc/init.d/snort stop
```

Go back to the config and make sure it's setup to log to files and not the database.

How are you testing snort?

---

### Post by izkandare on 2007-08-01
hey..
thanks for the tutorial.my snort and base works perfectly.but how can i set authentication on the base, so that no other users could explore the base website...

---

### Post by tegwilym on 2007-08-01
> **djhedges said:**
> Open up synaptic and first do a complete removal of some parts such as the pear & php.  Then install them again.

Another fine idea. Thanks!  I'll try that too.  :)

---

### Post by djhedges on 2007-08-01
> **izkandare said:**
> hey..
thanks for the tutorial.my snort and base works perfectly.but how can i set authentication on the base, so that no other users could explore the base website...

[http://www.snort.org/docs/setup_guides/snort_base_SSL.pdf](http://www.snort.org/docs/setup_guides/snort_base_SSL.pdf)

Theres a section in there explaining exactly what you asked for.  It'll lock down the base directory so that you have to provide a username & password to get in.

Look for Securing Apache & Base directory towards the end of the how to.

---

### Post by tjsullivan1 on 2007-08-09
Is it necessary to have apache and base installed to use snort? I am on a college campus that is very restrictive of what one does on his/her computer, and running an apache server would be one of those things that is restricted.

 If it would be possible to run apache silently, that would be even better.

---

### Post by djhedges on 2007-08-09
> **tjsullivan1 said:**
> Is it necessary to have apache and base installed to use snort? I am on a college campus that is very restrictive of what one does on his/her computer, and running an apache server would be one of those things that is restricted.

 If it would be possible to run apache silently, that would be even better.

Apache is needed for base.  You can run snort without apache but it'll be very difficult to read the logs.

An easy way to hide apache is create a rule with iptables that only allows connections by the localhost.  Any packet sent to port 80 will be dropped except for the pc hosting apache & snort.  I'd post a way to set this up but I'm not very good with iptables.  Happy googling.

---

### Post by ikarma on 2007-08-31
> **djhedges said:**
> I remember having a problem with the graphs which I fixed by reinstalling different things such as the pear packages & php.  It's been a long time so I can't exactly remember what fixed it.

You could try looking for a similar problem with pear not base or snort specific.

I have no idea why but you have to install php5-gd but it doesn't enable it in php.  You must add the line in the Extentions section.... extension=gd.so

I think the file is in /etc/php5/apache2

oh and everyone should look at [aanval]("http://aanval.com") which is free for personal use.  The setup on this program is what helped me figure out what I was missing with the php-gd module.

Now I am having trouble keeping my eth1 from obtaining an ip address.    I had it working but when I rebooted the config for eth1 stayed in the file but  Ubuntu changed eth1 to eth2 with dhcp enabled :(

any suggestions?

---

### Post by splantier on 2007-09-12
I get this when I try to run the web. I follow the instructions to the t.

Warning: include(/usr/share/adodb/adodb.inc.php) [function.include]: failed to open stream: Numerical result out of range in /var/www/base/includes/base_db.inc.php on line 636
 
 Warning: include() [function.include]: Failed opening '/usr/share/adodb/adodb.inc.php' for inclusion (include_path='.:/usr/share/php:/usr/share/pear') in /var/www/base/includes/base_db.inc.php on line 636
 
 Fatal error: Call to undefined function ADOLoadCode() in /var/www/base/includes/base_db.inc.php on line 653

Any suggestion would be gratefull. 

Thanks.

---

### Post by dynamethod on 2007-09-27
well, ive made it thus far; ive managed to intall apache and base, although i think i may have done something wrong in the msyql part because i get this:

Error (p)connecting to DB : snort@localhost

Check the DB connection variables in base_conf.php

               = $alert_dbname   : MySQL database name where the alerts are stored 
               = $alert_host     : host where the database is stored
               = $alert_port     : port where the database is stored
               = $alert_user     : username into the database
               = $alert_password : password for the username
              

Database ERROR:Access denied for user 'xen'@'localhost' to database 'snort'

solved, just changed teh base_conf.php lines to root and the root password, 

i cant access mysql unless i do:
mysql -u root -p

so i have to edit the base_conf.php to use root and root's password, the site works, but its not logging anything :S, is it only meant to log alerts?

is this meant to be?

otherthing is when i try run:

snort &#8211;c /etc/snort/snort.conf

i get:
ERROR: Failed to lookup for interface: no suitable device found. Please specify one with -i switch
Fatal Error, Quitting..

??

---

### Post by djhedges on 2007-09-27
> **dynamethod said:**
> well, ive made it thus far; ive managed to intall apache and base, although i think i may have done something wrong in the msyql part because i get this:

Error (p)connecting to DB : snort@localhost

Check the DB connection variables in base_conf.php

               = $alert_dbname   : MySQL database name where the alerts are stored 
               = $alert_host     : host where the database is stored
               = $alert_port     : port where the database is stored
               = $alert_user     : username into the database
               = $alert_password : password for the username
              

Database ERROR:Access denied for user 'xen'@'localhost' to database 'snort'

solved, just changed teh base_conf.php lines to root and the root password, 

i cant access mysql unless i do:
mysql -u root -p

so i have to edit the base_conf.php to use root and root's password, the site works, but its not logging anything :S, is it only meant to log alerts?

is this meant to be?

otherthing is when i try run:

snort –c /etc/snort/snort.conf

i get:
ERROR: Failed to lookup for interface: no suitable device found. Please specify one with -i switch
Fatal Error, Quitting..

??

The ideal behind setting up a IDS is security so with security in mind you want to avoid using the root user to log the mysql alerts.  Instead look at the guide and create a user and give him permissions for the snort database.

if snort -c /etc/snort/snort.conf doesn't work for you then snort isn't running hence why theres no alerts showing up in base.  Try attaching your snort.conf & list the output from ifconfig.

---

### Post by dynamethod on 2007-09-28
ahh ok, no problems, reinstalled started again, everything is running smoothly now except for one thing, nothing is getting logged, like theres no statistics on base?

---

### Post by dynamethod on 2007-09-28
it shows some information including:

database: compiled support for ( mysql )
database: configured to use mysql
database:          user = snort
database: password is set
database: database name = snort
database:          host = localhost
database:   sensor name = 192.168.1.243
database:     sensor id = 1
database: schema version = 106
database: using the "log" facility
6420 Snort rules read...
6420 Option Chains linked into 247 Chain Headers
0 Dynamic rules

and 

+------------------------------------------------------------------------------
Rule application order: ->activation->dynamic->alert->pass->log
Log directory = /var/log/snort

and ive just used Crl C and i get this:

Snort received 178 packets
    Analyzed: 178(100.000%)
    Dropped: 0(0.000%)
===============================================================================
Breakdown by protocol:
    TCP: 163        (91.573%)         
    UDP: 13         (7.303%)          
   ICMP: 0          (0.000%)          
    ARP: 2          (1.124%)
  EAPOL: 0          (0.000%)
   IPv6: 0          (0.000%)
    IPX: 0          (0.000%)
  OTHER: 0          (0.000%)
DISCARD: 0          (0.000%)
===============================================================================
Action Stats:
ALERTS: 0
LOGGED: 0
PASSED: 0
===============================================================================
TCP Stream Reassembly Stats:
    TCP Packets Used: 15         (8.427%)
    Stream Trackers: 5         
    Stream flushes: 0         
    Segments used: 0         
    Stream4 Memory Faults: 0         
===============================================================================
Final Flow Statistics
,----[ FLOWCACHE STATS ]----------
Memcap: 10485760 Overhead Bytes 16400 used(%0.168352)/blocks (17653/8) Overhead blocks: 1 Could Hold: (58579)
IPV4 count: 7 frees: 0 low_time: 1190984761, high_time: 1190985131, diff: 0h:06:10s
    finds: 28 reversed: 11(%39.285714) 
    find_sucess: 21 find_fail: 7 percent_success: (%75.000000) new_flows: 7
 Protocol: 6 (%53.571429) finds: 15  reversed: 5(%33.333333) 
  find_sucess: 10 find_fail: 5 percent_success: (%66.666667) new_flows: 5
 Protocol: 17 (%46.428571) finds: 13  reversed: 6(%46.153846) 
  find_sucess: 11 find_fail: 2 percent_success: (%84.615385) new_flows: 2
database: Closing connection to database "ted"
Snort exiting


database "ted" ??

didnt set mysql up to log to any databse by the name of "ted", odd!?

erm i just did the same thing, started then stoped snort and it gave this:

database: Closing connection to database "s PA12 attempt"
Snort exiting

what on earth??

---

### Post by djhedges on 2007-09-28
That looks nothing like the snort config I'm familiar with.
```

# output database: log, mysql, user=root password=test dbname=db host=localhost
```

Uncomment this line and comment out the default which is logging to files.  Change it so it's using the snort db which you create if you following my directions and the user snort.

---

### Post by dynamethod on 2007-09-28
well ive tried reinstalling, thing is snort is not writing alerts at all though

are these permissions correct?

ls -l /var/log/snort/
total 0
-rw-r----- 1 snort adm 0 2007-09-29 15:42 alert
-rw-r----- 1 root  adm 0 2007-09-29 15:42 tcpdump.log.1191037357


theres nothing in the files, after i run sudo /etc/init.d/snort start

---

### Post by dynamethod on 2007-09-29
solved my problems sorry about these posts, i cant delete them :S

---

### Post by leafaiden on 2007-10-04
> **dynamethod said:**
> solved my problems sorry about these posts, i cant delete them :S

What did you find or how did you fix the problem where snort is not writing any alerts?

I'm having a similar issue.  Thanks!

---

### Post by donad on 2007-10-25
Hi,

I was using this guide to install snort-mysql on gutsy.  Everything seems to install fine, snort 2.7 just crashes the machine....  I started a thread here  [http://ubuntuforums.org/showthread.php?t=590795&highlight=snort]("http://ubuntuforums.org/showthread.php?t=590795&highlight=snort")

Anyone know if the 2.7 package is broken?

---

### Post by donad on 2007-11-06
Sorry for the bump..

I am just curious if anyone else is having this problem in gutsy!?

---

### Post by cwhitmore on 2008-03-25
I was able to get through the install okay and get the graph page to come up, but when I run:
tail -f /var/log/snort/alert  

I get nothing. I'm using this Linux box as a samba server so I would expect some alerts to come up. Also, when I run "pgrep -l snort" I get the following output:
4699 snort
4702 snort

Do I need to edit the snort.conf file to point to the eth0 card or does it already know to monitor that NIC?

---

### Post by shahin on 2008-04-08
I deleted everything in etc/snort directory and now I do not know how to get the files back.  Help please.
I tried removing and reinstalling snort and oinkmaster but it did not work.

---

### Post by resmivarma on 2008-04-27
Hello,
  Does this tutorial apply to Gutsy gibbon also.If no, can you refer us to some tutorial.
  Thanks in advance

---

### Post by cleopard on 2008-05-16
Does this block of code go in the snort.conf file right after the previous 'output database: ...' line?  It's a bit unclear about whether or not it goes there.

mysql -u root
set password for root@localhost=password('PICK_A_PASSWORD');
create database snort;
grant insert,select on root.* to snort@localhost;
set password for snort@localhost=password('PASSWORD_SNORT_CONF');
grant create,delete,insert,select,update on snort.* to snort@localhost;
grant create,delete,insert,select,update on snort.* to snort;
exit

---

### Post by cleopard on 2008-06-05
I have installed Snort on Ubuntu Linux and it appears to be running when:


root@craig-desktop:/var/log# /etc/init.d/snort stop
 * Stopping Network Intrusion Detection System  snort                                                               [ OK ] 
root@craig-desktop:/var/log# /etc/init.d/snort start
 * Starting Network Intrusion Detection System  snort                                                               [ OK ] 
root@craig-desktop:/var/log# pgrep -l snort
root@craig-desktop:/var/log# 


And in the 'syslog' file, there's a message:

Jun  5 15:54:10 craig-desktop snort[14459]: database: must enter database name in configuration file
Jun  5 15:54:10 craig-desktop snort[14459]: FATAL ERROR:


I'm not sure what configuration file it's referring to.  If it's 'snort.conf', I have the line:

output database: log, mysql, user=snort password=buttons07 dbname=snort host=localhost


So the database name 'snort' is there.  Any suggestions?  Thank you.

---

### Post by Sarmacid on 2008-09-30
I tried this tutorial in the past and it worked, but now, with BASE 1.4.1, I got some errors when I tried to get to the BASE page([http://localhost/base](http://localhost/base)). This isn't exactly my error but someone with the same problem I had posted it(Forgot to save the page with the error x_x):

```
Warning: include_once(Mail.php) [function.include-once]: failed to open stream: No such file or directory in /var/www/web/base-php4/includes/base_action.inc.php on line 29

Warning: include_once() [function.include]: Failed opening 'Mail.php' for inclusion (include_path='.:/usr/share/php') in /var/www/web/base-php4/includes/base_action.inc.php on line 29

Warning: include_once(Mail/mime.php) [function.include-once]: failed to open stream: No such file or directory in /var/www/web/base-php4/includes/base_action.inc.php on line 30

Warning: include_once() [function.include]: Failed opening 'Mail/mime.php' for inclusion (include_path='.:/usr/share/php') in /var/www/web/base-php4/includes/base_action.inc.php on line 30

Warning: Cannot modify header information - headers already sent by (output started at /var/www/web/base-php4/includes/base_action.inc.php:29) in /var/www/web/base-php4/base_common.php on line 1077
```

To solve this, I had to install a couple of things

```
pear install Mail
pear install Mail_Mime
```

And now it's working :D

---

### Post by RandomCow on 2009-02-17
So, not to revive a dead thread, but I was trying to run this process for 8.10, and now that I have, snort won't start, just saying [fail].

Also, any time I apt-get install anything, I get the following (though the install works fine):

Processing triggers for man-db ...
Setting up snort-mysql (2.7.0-19ubuntu1) ...
 * Stopping Network Intrusion Detection System  snort                                     * No running snort instance found
 * Starting Network Intrusion Detection System  snort                             [fail] 
invoke-rc.d: initscript snort, action "start" failed.
dpkg: error processing snort-mysql (--configure):
 subprocess post-installation script returned error exit status 1

I am almost positive that every other step in the guide worked. The only other thing that was wierd was that there was no snort.conf installed, only a snort.debian.conf, which I changed the name of to snort.conf and modified a bit. It currently looks like this:

# This file is used for options that are changed by Debian to leave
# the original lib files untouched.
# You have to use "dpkg-reconfigure snort" to change them.

SNORT_STARTUP="boot"
SNORT_HOME_NET="any"
SNORT_OPTIONS=""
SNORT_INTERFACE="wlan0"
SNORT_SEND_STATS="true"
SNORT_STATS_RCPT="root"
SNORT_STATS_THRESHOLD="1"
output database: log, mysql, user=snort password=(Not telling, but I have my password here) dbname=snort host=localhost

Do you think this is causing the problem? Can anyone help me rectify this, especially as the snort forums have been unresponsive.

Anything I should run and post the output of (pgrep -l snort returns nothing, btw).

Thanks!

---

### Post by SecurityMonkey on 2009-05-06
Great post!

One other note - from a 'base' install the user will need to install Mail & Mail_Mime from pear:

```
pear install Mail
```
```
pear install Mail_Mime
```

Cheers,

SM

---

### Post by juancarlospaco on 2009-09-29
I solve this problem, but i got another, i run:
**cat /var/log/syslog | grep snort**

**/var/log/snort/alert: permission denied.**

to fix it i run:
**chmod --verbose 777 /var/log/snort/alert**

**/etc/init.d/snort restart**

but now i have this:

**cat /var/log/syslog | grep snort**

snort[3445]: PID path stat checked out ok, PID path set to /var/run/ 
snort[3445]: Writing PID "3445" to file "/var/run//snort_eth0.pid" 
snort[3445]: Daemon initialized, signaled parent pid: 3444 
[B]snort[3444]: Daemon parent exiting 
snort[3445]: database: mysql_error: Unknown column 'sid' in 'field list' 
snort[3445]: database: mysql_error: Unknown column 'hostname' in 'field list' SQL=INSERT INTO sensor (hostname, interface, detail, encoding, last_cid) VALUES ('172.16.3.111','eth0',1,0, 0)[/B]



*Any HELP ...???*

---

### Post by acidblue on 2010-11-03
How do I tell snort to use wlan0 and not eth0, in thee config file ?

---

### Post by emcquaid on 2010-12-02
You probably got that figured out right after you posted, but

```
dpkg-reconfigure snort-mysql

```


Eric
empower systems 
frisco, tx

---

### Post by Matinovic on 2012-08-28
hi! :)

when I make "pgrep -l snort" nothing appears, so I suppose the snort is not running, and when I try "/etc/init.d/snort start" I get 

~$ sudo /etc/init.d/snort start
 * Starting Network Intrusion Detection System  snort                    [fail] 

just this error, I am confused about what could be the problem :confused:

tks :-)

---

