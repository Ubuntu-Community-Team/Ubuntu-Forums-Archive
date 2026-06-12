---
title: "autofs + ldap"
date: 2008-12-02
forum: Server Platforms
---

### Post by tosehee on 2008-12-02
Hi.

I was trying to post my question to this thread, but it's apparently read-only now.

[http://ubuntuforums.org/showthread.php?t=549225](http://ubuntuforums.org/showthread.php?t=549225)

So, here is my issue(s).

I am using Redhat Enterprise Edition 5.2 (sorry it's not ubuntu), and have configured to use the Samba as the Primary Domain Controller. I have set up so all the servers can log using the pam module and ldap as the backend authentication method.

I have no problem with this so far.

My problem is, I am now trying to mount the remote /home, so they can share across the multiple servers. Here is my exports in the server.

/home ipaddress/255.255.255.0(rw,sync,insecure,no_subtree_check)
/mnt/apps/apps ip/255.255.255.0(rw,sync,insecure,no_subtree_check)

And here is my clients auto.master and auto.home

auto.master:
/home /etc/auto.home --timeout=60
/mnt /etc/auto.pub --timeout=60

auto.home:
*       -rw,hard,intr   ipaddress:/home/&

The nsswitch.conf has this.

automount: files ldap


I have established this setting up smbldap-tools.

When I login to any of these client servers, I get this.

Last login: Tue Dec  2 17:01:51 2008 from 105.63.42.25
Could not chdir to home directory /home/loginname: Permission denied
-bash: /home/loginname/.bash_profile: Permission denied

Can someone give me a hand?

Really appreciate it.

Thanks a lot in advance.

Regards

---

### Post by tosehee on 2008-12-02
autofs status shows that it's trying to use the file first..? So, if that fails, does it go to ldap like what's in nsswitch.conf?

root@app06 ~]# /sbin/service autofs status
Configured Mount Points:
------------------------
/usr/sbin/automount --timeout=60 /home file /etc/auto.home 
/usr/sbin/automount --timeout=60 /mnt file /etc/auto.pub 

Active Mount Points:
--------------------
/usr/sbin/automount --timeout=60 /home file /etc/auto.home
/usr/sbin/automount --timeout=60 /mnt file /etc/auto.pub

---

### Post by iank2112 on 2009-01-16
Yes, if the local files don't have the correct info, LDAP
will be referenced. Do you have automount maps in LDAP?
The local entries appear correct, what error are you getting
in the logs?

Ian

---

