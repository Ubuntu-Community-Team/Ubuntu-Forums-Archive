---
title: "OS Management"
date: 2010-07-28
forum: Server Platforms
---

### Post by Thyagaraj on 2010-07-28
Hey guys I need help to accomplish the following goals:

- Apply security patches and update OS according to predefined schedule (daily or weekly, or any time when critical patch is available) 

- Email or sms to inform the administrator that there is a new patch or update available

- Email or sms to inform the administrator that is a possible attack or security breach

---

### Post by Thyagaraj on 2010-07-28
I'm getting following error when i try to install " apt-get install apticron" 


Reading package lists... Done
Building dependency tree       
Reading state information... Done
apticron is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 81 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up postfix (2.6.5-3) ...

Postfix configuration was not changed.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
newaliases: warning: valid_hostname: numeric hostname: 10
newaliases: fatal: file /etc/postfix/main.cf: parameter mydomain: bad parameter value: 10
dpkg: error processing postfix (--configure):
 subprocess installed post-installation script returned error exit status 75
dpkg: dependency problems prevent configuration of bsd-mailx:
 bsd-mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing bsd-mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on bsd-mailx; however:
  Package bsd-mailx is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apticron:
 apticron depends on mailx; however:
  Package mailx is not configured yet.
  Package bsd-mailx which provides mailx is not configured yet.
dpkg: error processing apticron (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    No apport report written because MaxReports is reached already
                                  ldconfig deferred processing now taking place
Errors were encountered while processing:
 postfix
 bsd-mailx
 mailx
 apticron
E: Sub-process /usr/bin/dpkg returned an error code (1)




Plz need help...

---

### Post by Thyagaraj on 2010-07-29
Plz anyone help me...

---

### Post by Thyagaraj on 2010-07-30
Hey guys I could not resolve this dependency error!

---

### Post by Thyagaraj on 2010-08-01
Have a little aspire that any one could help me...

---

### Post by inphektion on 2010-08-01
What server version?

---

### Post by FuturePilot on 2010-08-01
Try 
```
sudo dpkg --configure -a
```
first.

---

### Post by Thyagaraj on 2010-08-02
My ubuntu version is 9.10 karmic
I tried 'dpkg --configure -a' still I'm getting same error messages

---

### Post by FuturePilot on 2010-08-02
Try
```
sudo apt-get install -f
```
That will try to sort out any dependency problems that could be holding those 4 packages up.

---

### Post by Thyagaraj on 2010-08-02
Thanks for reply!

I'm still getting same error message.

---

### Post by inphektion on 2010-08-03
it looks like all you really need to do is configure postfix.  However I'd use unattended upgrades over apticron.

[https://help.ubuntu.com/9.10/serverguide/C/automatic-updates.html](https://help.ubuntu.com/9.10/serverguide/C/automatic-updates.html)

but also configure postfix: ```
sudo dpkg-reconfigure postfix
```

---

### Post by Thyagaraj on 2010-08-03
To use unattended-upgrades the file ***/etc/apt/apt.conf.d/10periodic*** is needed to specify the following 

APT::Periodic::Enable "1";
APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "5";
APT::Periodic::Unattended-Upgrade "1";

but /etc/apt/apt.conf.d/10periodic is missing
I'll get back to you again trying dpkg-reconfigure postfix

---

