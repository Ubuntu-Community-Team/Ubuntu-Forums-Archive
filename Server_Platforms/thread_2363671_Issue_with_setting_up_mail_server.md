---
title: "Issue with setting up mail server"
date: 2017-06-13
forum: Server Platforms
---

### Post by JoltSystems on 2017-06-13
I have never posted here...so to post a new thread, I have not found where to do that. I am not really new to Ubuntu...about 10 years, but im a bit of a wuss...I tend to seek out tutorials in preference to real learning...and in my attempt to setup a mail server based on several tutorials, all of which have failed miserably, the one I found that I like the setup the most...uhm...failed naturally...this is the one I have been following most recently: [https://www.exratione.com/2016/05/a-mailserver-on-ubuntu-16-04-postfix-dovecot-mysql/](https://www.exratione.com/2016/05/a-mailserver-on-ubuntu-16-04-postfix-dovecot-mysql/) .

Now, the problem that I am running into (one month into this trek, about 3 weeks past due) is the following:

I get to the point titled "Restart Everything, and Test the Server". Everything restarts as expected except Amavis and Dovecot, and I cant help to think the failure is related based on the errors presented. For example.

```
Jun 12 19:41:37 mail.inteljunky.com systemd[1]: Starting Dovecot IMAP/POP3 email server...
Jun 12 19:41:37 mail.inteljunky.com dovecot[1912]: doveconf: Fatal: Error in configuration file /etc/dovecot/conf.d/10-master.conf line 105: Unknown setting: service
Jun 12 19:41:37 mail.inteljunky.com systemd[1]: dovecot.service: Control process exited, code=exited status=89
Jun 12 19:41:37 mail.inteljunky.com systemd[1]: Failed to start Dovecot IMAP/POP3 email server.
Jun 12 19:41:37 mail.inteljunky.com systemd[1]: dovecot.service: Unit entered failed state.
Jun 12 19:41:37 mail.inteljunky.com systemd[1]: dovecot.service: Failed with result 'exit-code'.
root@mail:/home/administrator# jed /etc/dovecot/conf.d/10-master.conf
root@mail:/home/administrator# systemctl status dovecot.service
&#9679; dovecot.service - Dovecot IMAP/POP3 email server
   Loaded: loaded (/lib/systemd/system/dovecot.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2017-06-12 19:41:37 EDT; 14min ago
     Docs: man:dovecot(1)
           [http://wiki2.dovecot.org/](http://wiki2.dovecot.org/)
  Process: 1912 ExecStart=/usr/sbin/dovecot (code=exited, status=89)

```
and

```
&#9679; amavis.service - LSB: Starts amavisd-new mailfilter
   Loaded: loaded (/etc/init.d/amavis; bad; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2017-06-12 21:45:28 EDT; 3h 13min ago
     Docs: man:systemd-sysv-generator(8)
  Process: 2152 ExecStart=/etc/init.d/amavis start (code=exited, status=1/FAILURE)


Jun 12 21:45:24 mail.inteljunky.com systemd[1]: Starting LSB: Starts amavisd-new mailfilter...
Jun 12 21:45:27 mail.inteljunky.com amavis[2160]: starting. /usr/sbin/amavisd-new at mail.inteljunky.com amavisd-new-2.10.1 (20141025), Unicode aware, LC_ALL="C", LANG="en_CA.UTF-8"
Jun 12 21:45:27 mail.inteljunky.com amavis[2152]: Starting amavisd: ERROR: MISSING REQUIRED ADDITIONAL MODULES:
Jun 12 21:45:27 mail.inteljunky.com amavis[2152]:   DBD::mysql
Jun 12 21:45:28 mail.inteljunky.com amavis[2152]: (failed).
Jun 12 21:45:28 mail.inteljunky.com systemd[1]: amavis.service: Control process exited, code=exited status=1
Jun 12 21:45:28 mail.inteljunky.com systemd[1]: Failed to start LSB: Starts amavisd-new mailfilter.
Jun 12 21:45:28 mail.inteljunky.com systemd[1]: amavis.service: Unit entered failed state.
Jun 12 21:45:28 mail.inteljunky.com systemd[1]: amavis.service: Failed with result 'exit-code'.

```

When I investigate the files listed, I make changes that would pass just to find the error, yet nothing I try works. If I had hair, id pull it out...but I dont, well not much anyways...so hopefully someone will decide to help me with this issue. Thanks in advance.

---

### Post by wildmanne39 on 2017-06-13
I am posting a screenshot of how to start a new thread, when you go into any sub-forum you will see a red button that says Post New Thread in the top left corner of the forum.

---

### Post by TheFu on 2017-06-18
Please use code tags when posting code and output. Hard to read otherwise.

Did you fix the error:
```
doveconf: Fatal: Error in configuration file /etc/dovecot/conf.d/10-master.conf line 105: Unknown setting: service
``` ??

I'd look for missing/extra {}.

---

### Post by JoltSystems on 2017-06-18
No not fixed. I appreciate your suggestion, as a programmer...I have at multiple times had to search for extra/missing brackets...as I have done in this case. I can find no instance of this occurring.

---

### Post by lisati on 2017-06-18
> **TheFu said:**
> Please use code tags when posting code and output. Hard to read otherwise.

I've added the tags.

@JoltSystems: please see the link in my signature.

---

### Post by JoltSystems on 2017-06-18
I could experiment with that...I will let you know.

---

### Post by JoltSystems on 2017-06-19
> **lisati said:**
> I've added the tags.

@JoltSystems: please see the link in my signature.

I just realized what you meant. However, unless it is with the use of the <> option, I have no idea how to do that.

---

### Post by lisati on 2017-06-19
> **JoltSystems said:**
> I just realized what you meant. However, unless it is with the use of the <> option, I have no idea how to do that.

The [link]("http://ubuntuforums.org/showthread.php?p=12776168#post12776168") to instructions is in my signature.

---

### Post by TheFu on 2017-06-19
Perhaps if you posted the config file, another set of eyes would see the problem?

---

### Post by JoltSystems on 2017-06-19
> **TheFu said:**
> Perhaps if you posted the config file, another set of eyes would see the problem?


I hope I got this right as to not stress out the admins too much...but here we go...

/etc/dovecot/conf.d/10-master.conf

```


#default_process_limit = 100
#default_client_limit = 1000
# Default VSZ (virtual memory size) limit for service processes. This is mainly
# intended to catch and kill processes that leak memory before they eat up# everything.
#default_vsz_limit = 256M
# Login user is internally used by login processes. This is the most untrusted
# user in Dovecot system. It shouldn't have access to anything at all.
#default_login_user = dovenull
# Internal user is used by unprivileged processes. It should be separate from# login user, so that login processes can't disturb other processes.
#default_internal_user = dovecot
service imap-login {  inet_listener imap {    #port = 143  
}  


inet_listener imaps 
{    
#port = 993    #ssl = yes  
}
  # Number of connections to handle before starting a new process. Typically  
# the only useful values are 0 (unlimited) or 1. 1 is more secure, but 0  
# is faster. <doc/wiki/LoginProcess.txt>  
#service_count = 1
# Number of processes to always keep waiting for more connections.  
#process_min_avail = 0
# If you set service_count=0, you probably need to grow this.  
#vsz_limit = $default_vsz_limit
}
service pop3-login {  
inet_listener pop3 {    
#port = 110  
}  
inet_listener pop3s {    
#port = 995    
#ssl = yes  
}
}
service lmtp {  unix_listener lmtp {    
#mode = 0666  
}
  # Create inet listener only if you can't use the above UNIX socket  
#inet_listener lmtp {    
# Avoid making LMTP visible for the entire internet    
#address =    
#port =   
#}
}
service imap {  
# Most of the memory goes to mmap()ing files. You may need to increase this  
# limit if you have huge mailboxes.  
#vsz_limit = $default_vsz_limit
# Max. number of IMAP processes (connections)  #process_limit = 1024}
service pop3 {  
# Max. number of POP3 processes (connections)  
#process_limit = 1024}
service auth {  
# auth_socket_path points to this userdb socket by default. It's typically  
# used by dovecot-lda, doveadm, possibly imap process, etc. Users that have  
# full permissions to this socket are able to get a list of all usernames and  
# get the results of everyone's userdb lookups.  
#  
# The default 0666 mode allows anyone to connect to the socket, but the  
# userdb lookups will succeed only if the userdb returns an "uid" field that  
# matches the caller process's UID. Also if caller's uid or gid matches the  
# socket's uid or gid the lookup succeeds. Anything else causes a failure.  
#  
# To give the caller full permissions to lookup all users, set the mode to  
# something else than 0666 and Dovecot lets the kernel enforce the  
# permissions (e.g. 0777 allows everyone full permissions).  
unix_listener auth-userdb {    
mode = 0666    
user = vmail    group = mail  
}
# Postfix smtp-auth  
unix_listener /var/spool/postfix/private/auth {    
mode = 0666  
}
# Auth process is run as this user.  
user = postfix  group = postfix
}
service auth-worker {  
# Auth worker process is run as root by default, so that it can access  
# /etc/shadow. If this isn't necessary, the user should be changed to  
# $default_internal_user.  
#user = root
}
service dict {  
# If dict proxy is used, mail processes should have access to its socket.  
# For example: mode=0660, group=vmail and global mail_access_groups=vmail  


unix_listener dict {    
#mode = 0600    
#user =     
#group =   
}
}





```

There is the amavis error, but I suspect that if the dovecot error is fixed this one will probably be fixed also, plus that config file is like 10,000 lines or something...if you want it, ill serve it up to you...but I hope not.

---

### Post by TheFu on 2017-06-19
Any chance you could use normal code tags, not html?  Most Unix config files care about line wrap and sometimes they care about spacing.

---

### Post by Hugo_Serrano on 2017-06-20
Hello!

This seems to be your config:

```
cat dovecot.conf | grep -v "#"
service pop3-login {  inet_listener pop3 {    
service lmtp {  unix_listener lmtp {    
service imap {  
service pop3 {  
service auth {  
service auth-worker {  
service dict {  
}
}



```

You are opening { but not closing them.

Here you can find an example:
[https://www.dovecot.org/doc/dovecot-example.conf](https://www.dovecot.org/doc/dovecot-example.conf)

```
$ cat dovecot-example.conf | grep -v "#" | awk /./


protocol imap {
}
  
protocol pop3 {
}
protocol lda {
}
auth default {
  mechanisms = plain
  passdb pam {
  }
  userdb passwd {
  }
  user = root
}
dict {
}
plugin {
}

```

---

### Post by TheFu on 2017-06-20
# is a comment start character. This extremely common in Unix config files.  Anything after that on a line is not parsed.

Check your {} open/close blocks.

---

### Post by JoltSystems on 2017-06-24
> **TheFu said:**
> # is a comment start character. This extremely common in Unix config files.  Anything after that on a line is not parsed.

Check your {} open/close blocks.


Sorry for the delay in response...I did not see page 2 and I would not have, had my son not pointed it out to me :eek:

I will attempt to put the file in an editor that checks for quotes...I will get back to you on the results thank you.

---

### Post by lisati on 2017-06-24
> **TheFu said:**
> Check your {} open/close blocks.

> **Hugo_Serrano said:**
> You are opening { but not closing them.

This is what I am seeing too.

A quick count can be helpful. If you start at 0 (zero), adding 1 for every {, and taking off for every }, you should arrive at zero by the time you reach the end of the file.

---

### Post by JoltSystems on 2017-06-24
> **lisati said:**
> This is what I am seeing too.

A quick count can be helpful. If you start at 0 (zero), adding 1 for every {, and taking off for every }, you should arrive at zero by the time you reach the end of the file.

My apologies, I have gone over the file 3 or 4 times with another set of eyes that was counting separately...and since I have been programming for 30 years, I have become quite accustomed to finding just these kinds of errors...I can only find the exact number of open brackets for closed brackets...and I don't use the entire file...I treat a section (similar to a function) as one section, since using the entire file as a guide can run into problems...for example...

```


service auth {  <---- Opening bracket for service auth
  # auth_socket_path points to this userdb socket by default. It's typically
  # used by dovecot-lda, doveadm, possibly imap process, etc. Users that have
  # full permissions to this socket are able to get a list of all usernames and
  # get the results of everyone's userdb lookups.
  #
  # The default 0666 mode allows anyone to connect to the socket, but the
  # userdb lookups will succeed only if the userdb returns an "uid" field that
  # matches the caller process's UID. Also if caller's uid or gid matches the
  # socket's uid or gid the lookup succeeds. Anything else causes a failure.
  #
  # To give the caller full permissions to lookup all users, set the mode to
  # something else than 0666 and Dovecot lets the kernel enforce the
  # permissions (e.g. 0777 allows everyone full permissions).
  unix_listener auth-userdb { <---- Opening bracket for unix_listener auth-userdb
    mode = 0666
    user = vmail
    group = mail
  } <---- Closing bracket for unix_listener auth-userdb


  # Postfix smtp-auth
  unix_listener /var/spool/postfix/private/auth { <---- Opening bracket for unix_listener /var/spool/postfix/private/auth
    mode = 0666
  }  <---- Closing bracket for unix_listener /var/spool/postfix/private/auth


  # Auth process is run as this user.
  user = postfix
  group = postfix
}  <---- Closing bracket for service auth




```

This is how I systematically eliminate the problem of the brackets...and I am only seeing the exact number of open brackets that I am closed brackets...those that are not commented out I might add...please, if you are seeing something that I am missing, please point it out.

---

