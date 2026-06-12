---
title: "setup postfix to send activation/subscription emails"
date: 2017-12-10
forum: Server Platforms
---

### Post by micahpage on 2017-12-10
I am trying to setup postfix so my website can send its own activation emails and subscription emails. I was using SMTP Google but i think i am being blocked by sending too many emails. 

I am going through this tutorial
[https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-16-04)

although i do have ubuntu 14.04

I am having trouble at the end install s-nail package. It said it doesnt exist in the repos. 

```
metulburr ~ $ sudo dpkg-reconfigure postfix

* Stopping Postfix Mail Transport Agent postfix                                                  [ OK ] 
setting synchronous mail queue updates: false
changing /etc/mailname to python-forum.io
setting myorigin
setting destinations: 
setting relayhost: 
setting mynetworks: 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
setting mailbox_command
setting mailbox_size_limit: 0
setting recipient_delimiter: +
setting inet_interfaces: all
setting inet_protocols: all

Postfix is now set up with the changes above.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
* Stopping Postfix Mail Transport Agent postfix                                                  [ OK ] 
* Starting Postfix Mail Transport Agent postfix                                                  [ OK ] 
Processing triggers for libc-bin (2.19-0ubuntu6.13) ...
```

```
metulburr ~ $ sudo postconf -e 'home_mailbox= Maildir/'
metulburr ~ $ sudo postconf -e 'virtual_alias_maps= hash:/etc/postfix/virtual'
metulburr ~ $ sudo vim /etc/postfix/virtual
metulburr ~ $ sudo postmap /etc/postfix/virtual
metulburr ~ $ sudo systemctl restart postfix
sudo: systemctl: command not found
metulburr ~ $ /etc/init.d/postfix reload
* Reloading Postfix configuration...                                                                    postfix: error: to submit mail, use the Postfix sendmail command
postfix: fatal: the postfix command is reserved for the superuser
                                                                                                 [fail]
metulburr ~ $ sudo !!
sudo /etc/init.d/postfix reload
* Reloading Postfix configuration...                                                                    postfix/postfix-script: fatal: the Postfix mail system is not running
                                                                                                 [fail]
metulburr ~ $ sudo ufw allow Postfix
Rule added
Rule added (v6)
```

```
metulburr ~ $ echo 'export MAIL=~/Maildir' | sudo tee -a /etc/bash.bashrc | sudo tee -a /etc/profile.d/mail.sh
export MAIL=~/Maildir
metulburr ~ $ source /etc/profile.d/mail.sh
metulburr ~ $ sudo apt-get install s-nail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package s-nail
metulburr ~ $ echo "deb http://in.archive.ubuntu.com/ubuntu/ xenial universe" | sudo tee -a /etc/apt/sources.list
deb http://in.archive.ubuntu.com/ubuntu/ xenial universe
metulburr ~ $ sudo apt-get update
```

but i dont get a s-nail package at all
```
metulburr ~ $ sudo apt-get install s-nailReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package s-nail



```

so if i add it ro the repos
```
#deb http://in.archive.ubuntu.com/ubuntu/ xenial universe#deb http://in.archive.ubuntu.com/ubuntu/ xenial universe



```

i get this
```
metulburr ~ $ sudo apt-get install s-nail
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
s-nail : Depends: libssl1.0.0 (>= 1.0.2~beta3) but 1.0.1f-1ubuntu2.23 is to be installed
         Depends: libtinfo5 (>= 6) but 5.9+20140118-1ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.
```

I am assuming you need this package as if i try to do this
```
echo 'init' | mail -s 'init' metulburr
```
it completes but does not make the Maildir structure in my home

---

