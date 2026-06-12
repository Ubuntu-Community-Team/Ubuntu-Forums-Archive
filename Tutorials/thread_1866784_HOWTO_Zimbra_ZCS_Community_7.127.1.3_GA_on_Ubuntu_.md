---
title: "HOWTO: Zimbra ZCS Community 7.12/7.1.3 GA on Ubuntu server 10.04 LTS amd64"
date: 2011-10-17
forum: Tutorials
---

### Post by e79 on 2011-10-17
**[Zimbra Collaboration Suite]("http://www.zimbra.com/")** (a VMware product) is a nice email and  collaboration system; easy to administer while providing great  functionality. In this post, I will show you how to perform a standard standalone install of  the latest build (7.12 GA) of the Community Edition (free) on a Ubuntu server  operating system (latest LTS - 10.04 amd64).

* NOTE:  Zimbra also offers a commercial edition of its product called the *Zimbra Network edition* - *Collaboration Server*, more info can be found [here]("http://www.zimbra.com/products/network-collaboration-server.html").
** NOTE: Zimbra just release a newer version which is 7.1.3 GA, but the steps provided are valid for 7.1.2 and 7.1.3.

We will also install a configure a basic Bind9 DNS server that can be used by Zimbra and your LAN clients.


This little how-to assumes that you already installed a basic Ubuntu Server 10.04 LTS.

If you haven't go grab your Ubuntu Server 10.04 LTS copy [here]("http://www.ubuntu.com/start-download?distro=server&bits=64&release=lts") and perform a basic installation (no special config). I strongly suggest that you dedicate a separate disk for Zimbra (which install in /opt by default).


The following are the information for our setup:
Domain name:** domain.com**
 Server name:    **   mail.domain.com**
 Lan IP:                **192.168.0.10**


**[SIZE=3]1. Networking Setup[/SIZE]**

Input static IP information for the server:

```
# sudo nano /etc/network/interfaces
```Replace the primary interface values with:
```

auto eth0
   iface eth0 inet static
   address 192.168.0.10
   netmask 255.255.255.0
   broadcast 192.168.0.255
   network 192.168.0.0
   gateway 192.168.0.1
```Now set the hostname file:
```
# sudo nano /etc/hostname
```Replace values with:
```
mail.domain.com
```And set the hosts file as well:
```
# sudo nano /etc/hosts
```Replace values with:
```

127.0.0.1       localhost.localdomain   localhost
192.168.0.10    mail.domain.com       mail

```Now start the hostname service:
```
# sudo service hostname start
```Install SSH so we can configure the server remotely
```
# sudo apt-get install ssh
```[B][SIZE=3]


2. Bind9 Installation and Configuration[/SIZE][/B]

Log in with SSH and install and configure Bind9 to serve the domain.com domain (and possibly your LAN clients)

```
# ssh user@192.168.0.10
``````
# sudo apt-get install bind9 bind9-doc
```Define the forward zone in the named.conf.local file:
```
# sudo nano /etc/bind/named.conf.local
```and add the following lines:

```

zone "domain.com" {
         type master;
         file "/etc/bind/db.domain.com";
         allow-transfer{"none";};
         forwarders {8.8.8.8;};
 };

```Now create the forward zone database in '/etc/bind/':
```
# sudo nano /etc/bind/db.domain.com
```and add the following lines:

```

; domain.com
 $TTL  604800
 @       IN     SOA     ns.domain.com. root.domain.com. (
                                29092011 ; Serial
                                604800 ; Refresh
                                86400 ; Retry
                                2419200 ; Expire
                                604800); Negative Cache TTL
 ;
 @       IN     NS  ns
         IN     MX  10 mail
         IN     A   192.168.0.10
 ns      IN     A   192.168.0.10
 mail    IN     A   192.168.0.10
 www     IN     A   192.168.0.10

```Now restart the Bind9 service and test the DNS server:
```
# sudo service bind9 restart
``````
# dig domain.com
``````
# nslookup domain.com
```Reboot the server before the next step and make sure your logs doesn't contain any errors.


[B][SIZE=3]
3. Zimbra Installation and Configuration[/SIZE][/B]

Now download the prerequisites, the Zimbra ZCS Community for Ubuntu 64bit package and start the Zimbra installation

**[SIZE=2]Prerequisites:[/SIZE]**
```
# sudo apt-get install libperl5.10 sqlite3 sysstat
```**[SIZE=2]Zimbra download, installation and configuration (done as root):[/SIZE]**

First of all, let's get root access to make things easier
```
# sudo -i
```Then type the following commands in order (this will download, unpack and start the Zimbra installation - assuming you are installing it in /opt):

```
# cd /opt
``````
# wget http://files2.zimbra.com/downloads/7.1.2_GA/zcs-7.1.2_GA_3268.UBUNTU10_64.20110804130819.tgz
``````
# tar -zxvf zcs-7.1.2_GA_3268.UBUNTU10_64.20110804130819.tgz
``````
# cd zcs-7.1.2_GA_3268.UBUNTU10_64.20110804130819/
``````
# ./install.sh
```The following is a part of what would be the installation output. I'm not posting the full result as it would be too long, only essential parts where you need to answer. The red parts are these answers/input you will have to provide during the install (don't forget to change them accordingly with your setup):

> 
............

Do you agree with the terms of the license agreement? [N] **[COLOR=Red]Y [/COLOR]**
............

Select the packages to install :
Install zimbra-ldap [**[COLOR=Red]Y[/COLOR]**]
Install zimbra-logger [**[COLOR=Red]Y[/COLOR]**]
Install zimbra-mta [**[COLOR=Red]Y[/COLOR]**]
Install zimbra-snmp [**[COLOR=Red]Y[/COLOR]**]
Install zimbra-store [**[COLOR=Red]Y[/COLOR]**]
Install zimbra-apache [**[COLOR=Red]Y[/COLOR]**]
Install zimbra-spell [**[COLOR=Red]Y[/COLOR]**]
Install zimbra-memcached [**[COLOR=Red]N[/COLOR]**]
Install zimbra-proxy [**[COLOR=Red]N[/COLOR]**]
Checking required space for zimbra-core
checking space for zimbra-store
............

The system will be modified.  Continue? [N] **[COLOR=Red]Y[/COLOR]** 
............

Setting defaults
...........
DNS ERROR resolving MX for mail.domain.com
It is suggested that the domain name have an MX record configured in DNS
Change domain name? [Yes]  **[COLOR=Red]Yes[/COLOR]**
Create domain: [mail.domain.com]   **[COLOR=Red]domain.com[/COLOR]**
MX: mail.domain.com (192.168.0.10)

Interface: 192.168.0.10
Interface: 127.0.0.1
done.
Checking for port conflicts

Main menu

**1**- Common Configuration:
**2**- zimbra-ldap:                          **Enabled**
**3**- zimbra-store:                         **Enabled**
         +Create Admin User:                     **yes**
         +Admin user to create:             **admin@domain.com**
        ******* +Admin Password        **UNSET**
         +Anti-virus quarantine user:      **virus-quarantine.fe3cm3aj@domain.com**
         +Enable automated spam training:        **yes**
         +Spam training user:                **spam.cxlqb0ek1j@domain.com**
         +Non-spam(Ham) training user: **ham.oekwonxk30@domain.com**
         +SMTP host:                             **mail.domain.com**
         +Web server HTTP port:            **80**
         +Web server HTTPS port:          **443**
        +Web server mode:                                         **http**
         +IMAP server port:                                        **143**
         +IMAP server SSL port:                              **993**
         +POP server port:                                          **110**
         +POP server SSL port:              **995**
        +Use spell check server:                          **yes**
         +Spell server URL:                                           **[http://mail.domain.com:7780/aspell.php](http://mail.domain.com:7780/aspell.php)**
         +Configure for use with mail proxy:        **FALSE**
         +Configure for use with web proxy:         **FALSE**
         +Enable version update checks:                  **TRUE**
         +Enable version update notifications:    **TRUE**
         +Version update notification email:         **admin@domain.com**
         +Version update source email: **                    [EMAIL="admin@domain.com"]admin@domain.com[/EMAIL]**
**4**- zimbra-mta:                                                          **Enabled**
 **5**- zimbra-snmp:                                                      **Enabled**
 **6**- zimbra-logger:                                                   **Enabled**
 **7**- zimbra-spell:                                                       **Enabled**
**8**- Default Class of Service Configuration:
 **r**) Start servers after configuration    **yes**
 **s**) Save config to file
 **x**) Expand menu
 **q**) Quit

Address unconfigured (**) items  (? - help)
Let's set some important things right now(in section 3), change the following items according with your values/needs:


3- zimbra-store:                    Enabled
        +Admin Password: [COLOR=Red]**        zimbraadminpass**[/COLOR]
        +Web server HTTP port: **[COLOR=Red]8080[/COLOR]**
        +Web server mode:       **[COLOR=Red]https[/COLOR]**
        +Spell server URL: **[COLOR=Red]        [https://mail.domain.com:7780/aspell.php](https://mail.domain.com:7780/aspell.php)[/COLOR]**

Changing the Http port to 8080 would allow to run another web server on port 80 on the same machine, such as apache2 (not covered in this howto).

Now finish the installation process:

> 
*** CONFIGURATION COMPLETE - press 'a' to apply
 Select from menu, or press 'a' to apply config (? - help) **[COLOR=Red]a[/COLOR]**
 Save configuration data to a file? [[COLOR=Red]**Yes**[/COLOR]]
 Save config in file: [/opt/zimbra/config.7169]
 Saving config in /opt/zimbra/config.7169...done.
 The system will be modified - continue? [No] [COLOR=Red]**Yes**[/COLOR]

............

You have the option of notifying Zimbra of your installation.
This helps us to track the uptake of the Zimbra Collaboration Suite.
The only information that will be transmitted is:
The VERSION of zcs installed (**7.1.2_GA_3268_UBUNTU10_64**)
The ADMIN EMAIL ADDRESS created (**admin@domain.com**)

Notify Zimbra of your installation? [Yes] [COLOR=Red]**Yes**[/COLOR]
Notifying Zimbra of installation via [http://www.zimbra.com/cgi-bin/](http://www.zimbra.com/cgi-bin/)
notify.cgi?VER=7.1.2_GA_3268_UBUNTU10_64&MAIL=admin@domain.com

Notification complete

............
Moving /tmp/zmsetup.09302011-002008.log to /opt/zimbra/log

Configuration complete - press return to exit
That's it, as this point the services should be started and your server up and running.

Let's do some cleanup just to be meticulous(can be skipped if you want to keep the downloaded files)
```

# sudo rm -r /opt/zcs*    <-- this only remove the .tar.gz file and the installation folder.
# reboot

```[SIZE=3]**4. Access the Zimbra Web Administration page**[/SIZE]

You can now log into the administration panel of your server and start configuring it and setting the whole collaboration system to your liking. I won't cover that in this post as it could be quite extensive.

But I would like to suggest you to start by configuring the flow setting and access to your server, whether you allow POP, IMAP or just the Zimbra service (which runs on port 443 btw) and checking at the security settings such as DNS lookup and protocol checks.

Admin Panel (choose http/https depending on your values defined at step 3)
```
https://mail.domain.com:7071/zimbraAdmin
```Mails Web Access (choose http/https depending on your values defined at step 3)
```
https://mail.domain.com/zimbra
```Attached is a little screenshot of the Web Administration panel



I hope you enjoyed this tutorial and it could somewhat help you.

Regards

[COLOR=RoyalBlue]***e79***[/COLOR]

---

