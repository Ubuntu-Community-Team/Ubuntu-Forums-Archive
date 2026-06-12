---
title: "Can't get NIS server running"
date: 2007-08-08
forum: Server Platforms
---

### Post by mattfletcher on 2007-08-08
Hello, I've been trying for the last week or more to set up a NIS authentication system on my local network using a feisty server. I attempted to follow the instructions on [https://help.ubuntu.com/community/SettingUpNISHowTo](https://help.ubuntu.com/community/SettingUpNISHowTo) but they don't seem to work. Whenever I try to start NIS by typing /etc/init.d/nis start I get the following:

```
root@server:~# /etc/init.d/nis start
 * Starting NIS services                                                         
* binding to YP server...                                                      
* ....                                                                          
* ....                                                                         
* ....                                                                          
* ....                                                                          
* ....                                                                         
* ....                                                                          
* ....                                                                          
* ....                                                                          
* ....                                                                         
 * ....                                                                  [fail] 
                                                                         [ OK ]

```

I'm no expert in all of this so I can't really guess what to do. I have only been able to follow the instructions on the wiki and hope for the best.

---

### Post by thusi02 on 2007-08-08
Hi 

I do have some experience in setting up an NIS server to connect to an ldap server as a mode of authentication. The following are the packages you need to install: 

```
sudo apt-get install ldap-utils libldap2 libpam-ldap nis csh
```

You need to modify the following files: 
/etc/:
defaultdomain  nsswitch.conf  pam_ldap.conf  passwd  shadow  yp.conf

/etc/pam.d/:
common-account  common-auth  common-password  common-session

/etc/ldap/:
ldap.conf

But for your problem I am assuming your yp.conf file is not setup correctly thus the reason that you are unable to bind to the yp server. Your yp.conf should read something like below: 

```

ypserver 192.168.0.0 #This would be the ip of your ypserver to connect to and retrieve all the ldap credential stuff 
```

It will also help to look in the /var/log/syslog when attempting to restart the nis service to see why it is failing. 

I hope this helps. 

Cheers, 
Thusjanthan Kubendranathan

---

### Post by bencastan on 2007-09-18
I am not sure if this has been resolved. I had the same issue and symptom. I went back and checked the configurations in /etc/default/nis and found I had not set NISSERVER=master. Once I had done this (and commented out the NISCLIENT line it all works just fine.
Of course I should probably have set the NISCLIENT line to false.. !! But it works for testing purposes.

---

