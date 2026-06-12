---
title: "Snort"
date: 2014-02-20
forum: Security
---

### Post by linuxyogi on 2014-02-20
Hi,

These are the steps I have completed so far :

Installed snort
Configured /etc/snort/snort.conf
Installed oinkmaster
Registered to get the rules
configured oinkmaster
updated the rules using oinkmaster

Now when I start snort using 

```
sudo snort -q -A console -c /etc/snort/snort.conf -i eth0
```

there is no output.

I have only 1 PC. Is there any way to test if snort is working ?

I tried 

```
wget http://www.testmyids.com 
```

but snort didnt respond.

---

### Post by fugu2 on 2014-02-22
if you add this to your local.rules, just temporarily, then restart snort.
You should see a ton of alerts from any traffic over eth0
```

alert ip any any -> any any (msg: "IP Packet detected";)

```

---

### Post by linuxyogi on 2014-02-23
> **fugu2 said:**
> if you add this to your local.rules, just temporarily, then restart snort.
You should see a ton of alerts from any traffic over eth0
```

alert ip any any -> any any (msg: "IP Packet detected";)

```

Sorry I am not at all familiar with snort.

Where is this local.rules located ? 

Is this a separate file or a line in /etc/snort/snort.conf ?

I found this line in /etc/snort/snort.conf

```
###################################################
# Step #7: Customize your rule set
# For more information, see Snort Manual, Writing Snort Rules
#
# NOTE: All categories are enabled in this conf file
###################################################

# site specific rules
# include $RULE_PATH/local.rules


```


When I insert the line like this 

```
###################################################
# Step #7: Customize your rule set
# For more information, see Snort Manual, Writing Snort Rules
#
# NOTE: All categories are enabled in this conf file
###################################################

# site specific rules
# include $RULE_PATH/local.rules
alert ip any any -> any any (msg: "IP Packet detected";)


```

I get 
```
$ sudo snort -q -A console -c /etc/snort/snort.conf -i eth0
ERROR: /etc/snort/snort.conf(546) Each rule must contain a rule sid.
Fatal Error, Quitting..


```

---

### Post by fugu2 on 2014-02-23
> **linuxyogi said:**
> Sorry I am not at all familiar with snort.

Where is this local.rules located ? 

Is this a separate file or a line in /etc/snort/snort.conf ?

I found this line in /etc/snort/snort.conf

```
###################################################
# Step #7: Customize your rule set
# For more information, see Snort Manual, Writing Snort Rules
#
# NOTE: All categories are enabled in this conf file
###################################################

# site specific rules
# include $RULE_PATH/local.rules


```


When I insert the line like this 

```
###################################################
# Step #7: Customize your rule set
# For more information, see Snort Manual, Writing Snort Rules
#
# NOTE: All categories are enabled in this conf file
###################################################

# site specific rules
# include $RULE_PATH/local.rules
alert ip any any -> any any (msg: "IP Packet detected";)


```

I get 
```
$ sudo snort -q -A console -c /etc/snort/snort.conf -i eth0
ERROR: /etc/snort/snort.conf(546) Each rule must contain a rule sid.
Fatal Error, Quitting..


```
I'm not sure if you can add a rule directly to the snort.conf or not, i've never tried that. What version of snort are you running?
Ok, I'm assuming that you've already downloaded the snortrules-snapshot-xxxx.tar.gz from snort.org, wherever you've extracted your rules at,
there should be a file located at /path/to/snortrules-snapshot/rules/local.rules. if your not sure where you have extracted them at, you can search your
harddrive for them with:
```

$ find / -type f -size -5k -name local.rules 2> /dev/null

```
as for the sid thing, usually its recommended that custom rules use an sid of 1,000,000 or higher. So you could try
```

alert ip any any -> any any (msg: "IP Packet detected"; sid:1000001;)

```

---

### Post by linuxyogi on 2014-02-23
> **fugu2 said:**
> I'm not sure if you can add a rule directly to the snort.conf or not, i've never tried that. What version of snort are you running?
Ok, I'm assuming that you've already downloaded the snortrules-snapshot-xxxx.tar.gz from snort.org, wherever you've extracted your rules at,
there should be a file located at /path/to/snortrules-snapshot/rules/local.rules. if your not sure where you have extracted them at, you can search your
harddrive for them with:
```

$ find / -type f -size -5k -name local.rules 2> /dev/null

```
as for the sid thing, usually its recommended that custom rules use an sid of 1,000,000 or higher. So you could try
```

alert ip any any -> any any (msg: "IP Packet detected"; sid:1000001;)

```

Snort ver 2.9.6.0 GRE (Build 47)
The rules are located at /etc/snort/rules
The file local.rules is not there. Tried searching with that command. Its not on the disk.

---

### Post by fugu2 on 2014-02-23
Okay, change your snort.conf so that loacl.rules is uncommented:
```

###################################################
# Step #7: Customize your rule set
# For more information, see Snort Manual, Writing Snort Rules
#
# NOTE: All categories are enabled in this conf file
###################################################

# site specific rules
include $RULE_PATH/local.rules

```
you can create a local.rules file and create the rule inside of that file in one command:
```

$ echo 'alert ip any any -> any any (msg: "IP Packet detected"; sid:1000001;)' | sudo tee /etc/snort/rules/local.rules

```
when your done testing with that custom rule, you can recomment 
that one line in your snort.conf, and remove the local rule with:
```

$ sudo rm /etc/snort/rules/local.rules

```

---

### Post by linuxyogi on 2014-02-23
It worked. :guitar:

One last thing ..... since snort can be used in 3 modes namely sniffer, packet logger and network intrusion detection I wanted ti know about the commands of each mode.

I came to know about the command ```
sudo snort -q -A console -c /etc/snort/snort.conf -i eth0
``` by visiting #snort at freenode.

In which mode is running with the above command ? If its NID then please give me the commands for the other 2 modes.

I found [this]("http://usuaris.tinet.cat/sag/lsnort.htm") link but the commands here are a bit different to the one I am using.

I am behind my router's firewall and there is no LAN. Do you think snort will ever detect something ? I mean is it really useful to run snort in such a scenario ?

---

### Post by fugu2 on 2014-02-23
> **linuxyogi said:**
> It worked. :guitar:
One last thing ..... since snort can be used in 3 modes namely sniffer, packet logger and network intrusion detection I wanted ti know about the commands of each mode.
I came to know about the command ```
sudo snort -q -A console -c /etc/snort/snort.conf -i eth0
``` by visiting #snort at freenode.
In which mode is running with the above command ? If its NID then please give me the commands for the other 2 modes.
I found [this]("http://usuaris.tinet.cat/sag/lsnort.htm") link but the commands here are a bit different to the one I am using.
I am behind my router's firewall and there is no LAN. Do you think snort will ever detect something ? I mean is it really useful to run snort in such a scenario ?
Those commands must be for a really old version of snort. I would start by looking over:
http://s3.amazonaws.com/snort-org/www/assets/166/snort_manual.pdf
Section 1.5 Packet Acquisition has a lot of info about the various modes for snort 2.9.6, like pcap/afpacket for IDS, or nfq/ipq for IPS 

The snort website has a lot of useful ideas and great documentation. For getting traffic to your sensor you might try (I can't vouch for this because I've never tried it):
http://s3.amazonaws.com/snort-org/www/assets/217/Mirror_Traffic_With_Home_Router.pdf

"Peering over the wall - snort readonly cable"
http://www.linuxjournal.com/article/6985

or a comercial grade read-only
https://hakshop.myshopify.com/collections/gadgets/products/throwing-star-lan-tap

a little later on you may consider setting up snort to not run using sudo. running network apps as root is usually considered bad.
This is a tutorial on how to set up a different packet capture software to run as non-root, but It should also work for snort as well.
But I would only work on this after you get things set up that way you want them first.
https://blog.wireshark.org/2010/02/running-wireshark-as-you/

---

### Post by linuxyogi on 2014-02-24
> **fugu2 said:**
> Those commands must be for a really old version of snort. I would start by looking over:

[http://s3.amazonaws.com/snort-org/www/assets/166/snort_manual.pdf](http://s3.amazonaws.com/snort-org/www/assets/166/snort_manual.pdf)
Section 1.5 Packet Acquisition has a lot of info about the various modes for snort 2.9.6, like pcap/afpacket for IDS, or nfq/ipq for IPS 

The snort website has a lot of useful ideas and great documentation. For getting traffic to your sensor you might try (I can't vouch for this because I've never tried it):
[http://s3.amazonaws.com/snort-org/www/assets/217/Mirror_Traffic_With_Home_Router.pdf](http://s3.amazonaws.com/snort-org/www/assets/217/Mirror_Traffic_With_Home_Router.pdf)

"Peering over the wall - snort readonly cable"
[http://www.linuxjournal.com/article/6985](http://www.linuxjournal.com/article/6985)

or a comercial grade read-only
[https://hakshop.myshopify.com/collections/gadgets/products/throwing-star-lan-tap](https://hakshop.myshopify.com/collections/gadgets/products/throwing-star-lan-tap)

a little later on you may consider setting up snort to not run using sudo. running network apps as root is usually considered bad.
This is a tutorial on how to set up a different packet capture software to run as non-root, but It should also work for snort as well.
But I would only work on this after you get things set up that way you want them first.
[https://blog.wireshark.org/2010/02/running-wireshark-as-you/](https://blog.wireshark.org/2010/02/running-wireshark-as-you/)

I have enabled service snort so that it starts on boot. I have decided not to go into the mysql and web interface thing coz by running snort (IDS mode) for the last 3-4 days I have realized that if your firewall is functioning okay you are going to get alerts very rarely. I will just check the log files every weekend.

After googling I found that wireshark is needed to view the log files created by snort. I have installed wireshark. The next step is to run it as a regular user.

I visited [https://blog.wireshark.org/2010/02/running-wireshark-as-you/](https://blog.wireshark.org/2010/02/running-wireshark-as-you/) and followed the first solution but problem is (I guess) because the log files are owned by root giving wireshark its own group and user is not working.

BTW

Right after installing snort I did this

```
groupadd snort
mkdir -p /var/log/snort
useradd -g snort -d /var/log/snort snort
chown -R snort:snort /var/log/snort
```

---

### Post by fugu2 on 2014-02-26
The point I was trying to make was that using almost the same procedure you should be able to run snort as you also.
assuming that the snort binary is located at /usr/bin/snort:
```

$ sudo -s
# sudo apt-get install libcap2-bin
# groupadd -g snort
# usermod -a -G snort username
# chmod 750 /usr/bin/snort
# setcap cap_net_raw,cap_net_admin=eip /usr/bin/snort
```
I would think this should work, and if your log directory is readable and writable by you, then the log files that show up will be owned by you, and wireshark will be able to see them too.

Edit:
I would think this would be a good way to operate for IDS, maybe not for IPS. Running as root vs you has both pro's and con's and I'm sure one could debate the merits of both.

---

