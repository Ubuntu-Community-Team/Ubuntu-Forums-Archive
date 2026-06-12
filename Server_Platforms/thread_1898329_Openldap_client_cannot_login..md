---
title: "Openldap: client cannot login."
date: 2011-12-21
forum: Server Platforms
---

### Post by sebastian.s on 2011-12-21
so i have set up an Openldap server by following the ubuntu server guide.

[https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html](https://help.ubuntu.com/11.10/serverguide/C/openldap-server.html)

i followed the tutorial from the begining and worked my way to: Populating your database, and i added a user and a group. i never continued to the next part:Modifying the slapd configuration database.

so now i moved on to configure the client, so i followed the instruction further down on the page, under the headline: LDAP Authentication.

after that i reboot, at the login screen i select "Other"
i type in the user, which is john. itype in his password, then it tries to login for some seconds. but suddenly it puts me back at the login screen again, it doesnt give me any error message.

What could be causing this? and how do i solve it?

---

### Post by luvshines on 2011-12-23
Are you able to login with a non-ldap user ?

If yes, maybe you can find some useful logs in /var/log/auth.log files which say what might be causing LDAP user authentication to fail

---

### Post by shaneo1 on 2012-01-01
I too have the same issue. Not using TLS or Kerberos to auth with users.  Just need a simple sign in.  Spent 5 days trying to figure this out with no joy.  OpenLdap server is working very well.  Just issue with the client. Following the same document as well. Not to clued up on Ldap need some advise here is my authlog:

Clientadmin is the client machines user, spiper2 is the ldap user

```
Jan  1 15:15:28 client polkitd(authority=local): Unregistered Authentication Agent for unix-session:/org/freedesktop/ConsoleKit/Session14 (system bus name :1.160, object path /org/gnome/PolicyKit1/AuthenticationAgent, locale en_GB.UTF-8) (disconnected from bus)
Jan  1 15:15:40 client lightdm: pam_unix(lightdm:session): session closed for user clientadmin
Jan  1 15:15:42 client lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jan  1 15:15:42 client lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  1 15:15:45 client lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "clientadmin"
Jan  1 15:15:47 client dbus[383]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.184" (uid=104 pid=5074 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1066 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  1 15:15:49 client lightdm: pam_unix(lightdm:auth): conversation failed
Jan  1 15:15:49 client lightdm: pam_unix(lightdm:auth): auth could not identify password for [clientadmin]
Jan  1 15:15:49 client lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "spiper2"
Jan  1 15:15:55 client lightdm: pam_unix(lightdm:auth): authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=spiper2
Jan  1 15:15:55 client lightdm: pam_unix(lightdm:session): session closed for user lightdm
Jan  1 15:15:55 client lightdm: pam_unix(lightdm:session): session opened for user spiper2 by (uid=0)
Jan  1 15:15:55 client lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  1 15:15:57 client lightdm: pam_unix(lightdm:session): session opened for user lightdm by (uid=0)
Jan  1 15:15:57 client lightdm: pam_ck_connector(lightdm:session): nox11 mode, ignoring PAM_TTY :0
Jan  1 15:16:00 client lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "spiper2"
Jan  1 15:16:02 client dbus[383]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.193" (uid=104 pid=5178 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.14" (uid=0 pid=1066 comm="/usr/sbin/console-kit-daemon --no-daemon ")
Jan  1 15:16:05 client lightdm: pam_unix(lightdm:auth): conversation failed
Jan  1 15:16:05 client lightdm: pam_unix(lightdm:auth): auth could not identify password for [spiper2]
Jan  1 15:16:05 client lightdm: pam_succeed_if(lightdm:auth): requirement "user ingroup nopasswdlogin" not met by user "clientadmin"
Jan  1 15:16:07 client lightdm: pam_unix(lightdm:session): session closed for user lightdm
```

Any assistance would be gratefully appreciated.

---

### Post by shaneo1 on 2012-01-01
Reading a little further on you need to tell your client where to look for the ldap users home folder.  This is achieved by installing the NFS server on your LDAP server and NFS common on the client. Then fstab the folder on the server so he the ldap users see their home folder.

The reason why you are going back to the login screen is because of this reason.

I have solved my issue. 

Please note that its best to set the ldap users home folders to something like /home/ldapusers/<username> otherwise you will mount the server home folder directly over the client home folder, breaking the clients local users home folder.  (hehe I did that then realised my mistake)

Hope this helps 

regards,

Shane

---

### Post by rsvancara on 2012-01-01
First check to see if you can see your LDAP users.

getent passwd

getent groups

If you see a list of local users + ldap users, then you know LDAP is working.  If not, make sure PAM and NSS is configured properly and that you have the proper pam-ldap and nss-ldap packages installed.  

Also ensure that your /etc/ldap.conf file is configured properly.  You should see a few entries at the bottom of the file with all your configuations.  

Next make sure your /etc/nsswitch.conf file has the proper entries for passwd and groups.

Finally, ensure that your /etc/pam.d/ is configured properly to support LDAP authentication.

---

### Post by sebastian.s on 2012-01-11
Thanks for the replys, i will try the diffrent solutions as soon as i can :)

---

### Post by sebastian.s on 2012-01-18
> **rsvancara said:**
> First check to see if you can see your LDAP users.

getent passwd

getent groups

If you see a list of local users + ldap users, then you know LDAP is working.  If not, make sure PAM and NSS is configured properly and that you have the proper pam-ldap and nss-ldap packages installed.  

Also ensure that your /etc/ldap.conf file is configured properly.  You should see a few entries at the bottom of the file with all your configuations.  

Next make sure your /etc/nsswitch.conf file has the proper entries for passwd and groups.

Finally, ensure that your /etc/pam.d/ is configured properly to support LDAP authentication.

i tried "getent passwd" and i found both the local users and the ldap users. so i guess that theres nothing wrong with my configuration.

---

### Post by sebastian.s on 2012-01-18
> **shaneo1 said:**
> Reading a little further on you need to tell your client where to look for the ldap users home folder.  This is achieved by installing the NFS server on your LDAP server and NFS common on the client. Then fstab the folder on the server so he the ldap users see their home folder.

The reason why you are going back to the login screen is because of this reason.

I have solved my issue. 

Please note that its best to set the ldap users home folders to something like /home/ldapusers/<username> otherwise you will mount the server home folder directly over the client home folder, breaking the clients local users home folder.  (hehe I did that then realised my mistake)

Hope this helps 

regards,

Shane

seems lika a reasonble explanation :) i would just like to know, is it complicated to configure NFS? do you know any good tutorials?

---

### Post by luvshines on 2012-01-21
> **sebastian.s said:**
> seems lika a reasonble explanation :) i would just like to know, is it complicated to configure NFS? do you know any good tutorials?

To make sure that missing home directory is the exact reason for your users not able to login, try setting the homedir for a user (On ldap server) to some path which you know is there for sure (/home maybe) and then check if you can login.
If that's it then you can go for NFS home dir automount stuff

---

### Post by sebastian.s on 2012-01-25
> **luvshines said:**
> To make sure that missing home directory is the exact reason for your users not able to login, try setting the homedir for a user (On ldap server) to some path which you know is there for sure (/home maybe) and then check if you can login.
If that's it then you can go for NFS home dir automount stuff

i made a new user and set its home directory to **/home** but i still have the same problem.

still i know that my client can reach my server, because it fetches the users lastname from the ldap server.

---

### Post by luvshines on 2012-01-25
> **sebastian.s said:**
> i made a new user and set its home directory to **/home** but i still have the same problem.

still i know that my client can reach my server, because it fetches the users lastname from the ldap server.

When logged in with normal user, can you 'su' to an ldap user ?

---

### Post by sebastian.s on 2012-01-26
> **luvshines said:**
> When logged in with normal user, can you 'su' to an ldap user ?

This seems to work, logged in on a local account i did.

su tom -l

(tom is a ldap user) i entered the password and now i am logged in as tom.

---

### Post by sebastian.s on 2012-06-02
I first managed to solve my problem with a "dirty fix". i created the users home directory manually, now i was able to log in with my ldapusers. 

So the problem was inside /etc/pam.d/common-session

To automatically create home diretorys at login add this line.

```
session     required      pam_mkhomedir.so skel=/etc/skel umask=0022
```

All fixed! :P

---

