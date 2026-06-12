---
title: "HOWTO: Using denyhosts.py to automatically block invalid SSH login attempts"
date: 2005-06-30
forum: Tutorials
---

### Post by intangible on 2005-06-30
Ok, so someone out there if trying to connect to your machine through SSH (brute force against common login names like "john, owen, claire, etc"). Not sure people are trying to get into your machine? Why don't you check?:
**echo `cat /var/log/auth.log|grep sshd|grep "Invalid user"|wc -l` invalid SSH login attempts**

Your password is secure right?  They don't guess your username, right?  Well, it doesn't hurt to block them anyway, and now it's easy thanks to **denyhosts.py**!

Here's a quick overview of how to get to my setup:
[list=1]
[*] Download denyhosts-0.6.0.tar.gz from [http://sourceforge.net/project/showfiles.php?group_id=131204](http://sourceforge.net/project/showfiles.php?group_id=131204)
[*] Extract downloaded file using file-roller or **tar -xzvf denyhosts-0.6.0.tar.gz**
[*] Copy denyhosts.py to /usr/bin
**sudo cp denyhosts.py /usr/bin**
and **sudo chmod 755 /usr/bin/denyhosts.py**
[*] denyhosts.cfg-dist is the default config, you can use mine below for some decent default options, put this in **/etc/denyhosts.cfg**
```

# SECURE_LOG: the log file that contains sshd logging info
SECURE_LOG = /var/log/auth.log

# HOSTS_DENY: the file which contains restricted host access information
HOSTS_DENY = /etc/hosts.deny

# BLOCK_SERVICE: the service name that should be blocked in HOSTS_DENY
# man 5 host_access for details
#
BLOCK_SERVICE = ALL
# To block only sshd:
#BLOCK_SERVICE  = sshd   

# DENY_THRESHOLD: block each host after the number of failed login
# attempts has exceeded this value.
DENY_THRESHOLD = 5

# WORK_DIR: the path that DenyHosts will use for writing data to
# (it will be created if it does not already exist).       
WORK_DIR = denyhosts

# SUSPICIOUS_LOGIN_REPORT_ALLOWED_HOSTS=YES|NO
# If set to YES, if a suspicious login attempt results from an allowed-host
# then it is considered suspicious.  If this is NO, then suspicious logins 
# from allowed-hosts will not be reported.  All suspicious logins from 
# ip addresses that are not in allowed-hosts will always be reported.
SUSPICIOUS_LOGIN_REPORT_ALLOWED_HOSTS=NO

# HOSTNAME_LOOKUP=YES|NO
# If set to YES, for each IP address that is reported by Denyhosts,
# the corresponding hostname will be looked up and reported as well
# (if available).
HOSTNAME_LOOKUP=YES

# ADMIN_EMAIL: if you would like to receive emails regarding newly
# restricted hosts and suspicious logins, set this address to 
# match your email address.  If you do not want to receive these reports
# leave this field blank (or run with the --noemail option)
ADMIN_EMAIL = root

SMTP_HOST = localhost
SMTP_PORT = 25
SMTP_FROM = DenyHosts@localhost.localdomain
SMTP_SUBJECT = DenyHosts Report

```
[*] Let's test it: **sudo denyhosts.py -c /etc/denyhosts.cfg**
[*] Now we add it to root's crontab to run periodically: 
**export EDITOR=nano** (Optional, some systems open vi, pico's a little simpler)
**sudo crontab -e**
```
0,20,40 * * * * /usr/bin/denyhosts.py -c /etc/denyhosts.cfg
```
[/list]

*This howto was inspired by [http://rootprompt.org/article.php3?article=8735](http://rootprompt.org/article.php3?article=8735)*

Be forwarned, if you mistype your password too many times, you could lock one of your own computers out :evil:

It wouldn't hurt to look over the FAQ for denyhosts.py either: [http://denyhosts.sourceforge.net/faq.html](http://denyhosts.sourceforge.net/faq.html)

---

### Post by marks_linux on 2005-12-17
DenyHosts version 1.1.3 allows you to run daemon rather than cron using the --daemon flag.

M

---

### Post by Stryker777 on 2006-01-20
1.1.4 is out now.  Anyone get it to work?  Ive been trying all morning.
Seems like a cool concept.
Laterz

---

### Post by Stryker777 on 2006-01-20
Got it working.  Definately use the tar.  The directory you put your config file in is the one you have to have the extra scripts in.  Then you can add the daemon control to init.d and set your links in runlevels.  Dont forget to edit your config before launching.  Thanks for the howto.
Laterz

---

### Post by debernardis on 2006-01-27
How do I know if some a55h013 has found my password by brute force?

---

### Post by shawnzyoo on 2006-02-03
i followed this HOWTO 
and received this error

user@foxhole:~/DenyHosts-1.1.4$ sudo denyhosts.py -c /etc/denyhosts.cfg
Traceback (most recent call last):
  File "/usr/bin/denyhosts.py", line 5, in ?
    import DenyHosts.python_version
ImportError: No module named DenyHosts.python_version

any know whats going on ?
thanks

---

### Post by DigitalDuality on 2008-02-06
d

---

### Post by Noccy on 2012-09-14
Only step missing in the howto to make it current is the...

```
sudo python setup.py install
```

...needed to get the stuff in place. Besides that, it works. Thanks for the tip :)

---

### Post by SlugSlug on 2012-09-14
this is really old. 

now you just 

```
sudo apt-get install denyhosts
```

---

### Post by BrianBlaze on 2012-09-14
> **SlugSlug said:**
> this is really old. 

now you just 

```
sudo apt-get install denyhosts
```

thanks for the update :)

---

### Post by Noccy on 2012-09-14
> **SlugSlug said:**
> this is really old. 

now you just 

```
sudo apt-get install denyhosts
```

Is that version more current than the tarball from 2008? Doesn't seem like much has happened with the project lately so is there any practical difference between the two approaches? Besides the automatic updates if there would ever be one for it after 4 years idle? :)

Thanks for the tip tho :) Will keep that in mind for the next setup.

---

