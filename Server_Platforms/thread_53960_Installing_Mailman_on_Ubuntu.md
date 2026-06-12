---
title: "Installing Mailman on Ubuntu"
date: 2005-08-02
forum: Server Platforms
---

### Post by Puracepa23 on 2005-08-02
Hi All,

I'm a noob to this linux flavor. I've been trying to install Mailman on rel. 5.04 without success. I wonder if someone has successfully installed the Mailman package and has found a less painful way to set the Postfix configurations; perhaps some quick install instructions.

I went through the setup instructions, but I can't get the aliases to be created automatically and emails sent to the mailing list they are bouncing back by the exchange server. I've have installed Mailman successfully on Redhat, but this is kicking my butt. I'm not waisting time troubleshooting it. I'm going to re-do the server and and install the packages from scratch.  ](*,) 

Any info or link (besides list.or) from someone that has done it before will be greatly appreciated.

Thanks
~Pete

---

### Post by jasmuz on 2005-08-03
Here is a nice little link for your mailing pleasure, i hope it helps:

[http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Its based on Ubuntu 5.04 "Hoary Hedgehog"

---

### Post by Puracepa23 on 2005-08-05
Jasmuz, thanks for the link. I was able to setup the account and create mailing list, etc... However, if I sent emails to the mailing list owners I get a message from my exchange server saying that my message did not reached the intended recipient. Thanks again!  :) 

If anyone have installed Mailman + Postfix on Ubuntu or Debian, your links and guidance will be greatly appreciated.

Regards,
~Pete

---

### Post by deuce868 on 2005-08-05
[QUOTE=Puracepa23]Jasmuz, thanks for the link. I was able to setup the account and create mailing list, etc... However, if I sent emails to the mailing list owners I get a message from my exchange server saying that my message did not reached the intended recipient. Thanks again!  :) 

If anyone have installed Mailman + Postfix on Ubuntu or Debian, your links and guidance will be greatly appreciated.

Regards,
~Pete[/QUOTE]
I have it setup on debian. I just walked through the installation manual on the mailman site and skipped the steps that the deb package already did for me. It's been a while, but if you have specific questions I can check my current config. 

It sounds like you might not have the mailman aliases setup in postfix?

---

### Post by Puracepa23 on 2005-08-05
Thanks guys for your help. I was able to finally install Mailman + Postfix on Ubuntu. I will post complete/quick instructions on Monday. It took me two weeks, but it is finally done. I'm getting out of here... Once again thanks for the replies.

 \\:D/   To enjoy the weekend!!!

~Pete

---

### Post by Puracepa23 on 2005-08-09
This is what worked for me:


Mailman + Postfix + Apache2 on Ubuntu 5.04
Pedro Martinez: [email]puracepa23@gmail.com[/email]

1. Install Ubuntu 5.04 Desktop (not the server option).

2. Make sure to use fully-qualified hostname and domain name.

As root:

3. Set network information. In my case, I used static IPs.

4. Install Apache Server

apt-get install apache2

5. Install GCC, 

apt-get install gcc

6. Install Python

apt-get install python

7. Install Postfix

apt-get install postfix

8. Download the latest stable Mailman version. I used mailman-2.1.6.tgz. Use you browser to go to [http://sourceforge.net/project/showfiles.php?group_id=103](http://sourceforge.net/project/showfiles.php?group_id=103)

9. Create a new folder in /usr (I called mind “mydownloads”).

10. Extract mailman-2.1.6.tgz to that newly created folder.

11. Create mailman group and user:

groupadd mailman
useradd -c''GNU Mailman'' -s /no/shell -d /no/home -g mailman mailman

12. Create installation directory. I found it is a lot easier using the file browser and right-clicking the folder (like in Windows), but the script goes like this:

mkdir /usr/local/mailman
cd /usr/local/mailman
chgrp mailman .
chmod a+rx,g+ws .

13. Install Mailman. Remember that I called my folder “mydownloads.” You can call it how ever you want.

cd /usr/mydowloads/mailman-2.1.6 
./configure --with-groupname=mailman
make install 

When you run ./configure it will inspect all requirements, etc. If you miss to install something, configure will tell you what it is. Remember that to install packages you may type apt-get install and the package name.

14. Check your installation:

cd /usr/local/mailman
bin/check_perms

If there are errors, type:

bin/check_perms –f

Repeat previous step until no more errors are reported!

15. Setup web server

cd /etc/apache2
nano –w main.cf

Add this at the bottom:

ScriptAlias /mailman/       $prefix/cgi-bin/
Alias   /pipermail/     usr/local/mailman/archives/public/

Copy icons to apache:

cp /usr/local/mailman/icons/*.{jpg,png} /etc/apache2/icons

16. Setup Postfix

My main.cf file looks as such (I changed the domain name and IP for this example):

# See /usr/share/postfix/main.cf.dist for a commented, more complete version
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
# appending .domain is the MUA's job.
append_dot_mydomain = no
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
myhostname = mailman.domainname.com
alias_maps = hash:/etc/aliases, hash:/usr/local/mailman/data/aliase
alias_database = hash:/etc/aliases, hash:/usr/local/mailman/data/aliases

myorigin = /etc/mailname
mydestination = $myhostname, domain.domainname.com, mail. domain.domainname.com
relayhost = mail.domainname.domain.com
relay_domains = mailman.domainname.com, domainname.com
mynetworks = 127.0.0.0/8, XX.XX.XXX.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
owner_request_special = no
unknown_local_recipient_reject_code = 550
smtp_sender_restrictions = permit_mynetworks, reject_unknown_sender_domain, permit

17. Integrating Postfix & Mailman

Add this to the bottom of the /usr/local/mailman/Mailman/mm_cfg.py file: 

MTA = 'Postfix'

18. Run the bin/genaliases script to initialize your aliases file. 

cd /usr/local/mailman
bin/genaliases
chown mailman:mailman data/aliases*

19. Create a site-wide mailing list

bin/newlist mailman
bin/config_list -i data/sitelist.cfg mailman

20. Setup Cron

cd cron
crontab -u mailman crontab.in

21. Setup mailman q runner

cd ..
bin/mailmanctl start

cp scripts/mailman /etc/init.d/mailman
update-rc.d mailman defaults

22. Check hostname

bin/fix_url.py

23. Passwords

prefix/bin/mmsitepass <your-site-password>
prefix/bin/mmsitepass -c <list-creator-password>

25. Create redirection file for Apache2

Create a file in /var/www called index.html with the following content

<html>
<title>Mailman</title>
<meta http-equiv="refresh" content="0; url=mailman.domainname.com/mailman/listinfo">
</meta>
</html>

26. Reboot

27. For How-to-use instructions, go to [http://list.org/mailman-install/node45.html](http://list.org/mailman-install/node45.html).

28. My files:
[URL=http://www.nachos4u.com/pics/apache2.conf_example.txt]
Apache.conf[/URL] 
[Defaults.py](http://www.nachos4u.com/pics/Defaults.py_example.txt) 
[main.cf](http://www.nachos4u.com/pics/main.cf_example.txt) 
[master.cf](http://www.nachos4u.com/pics/master.cf_example.txt) 
[URL=http://www.nachos4u.com/pics/mm_cfg.py_e
xample.txt]mm_cfg.py[/URL]

---

### Post by Hendry on 2005-12-15
I'm running on Ubuntu 5.10 and followed these instructions. When installing I get the error:

checking that Python has a working distutils... yes
checking for a BSD compatible install... /usr/bin/install -c
checking whether make sets ${MAKE}... no
checking for true... /bin/true
checking for --without-gcc... no
checking for gcc... gcc
checking whether the C compiler (gcc  ) works... no
configure: error: installation or configuration problem: C compiler cannot create executables.

What can I do?

---

### Post by Puracepa23 on 2005-12-15
I'm not a SME on the subject, but I would reboot and try step 5 again to see if gcc installs correctly:

apt-get install gcc

Then, reboot again and try installing Mailman.

---

### Post by mikec13 on 2006-06-02
Thanks for the step-by-step, it helped a TON!!  Here's a slightly modified version of how I got it to work on Dapper server:


Mailman + Postfix + Apache2 on Ubuntu 6.06
Pedro Martinez: [email]puracepa23@gmail.com[/email]
updated: Mike Cochran [email]mcochran@gmail.com[/email]

1. Install Ubuntu 6.06 Server

2. Make sure to use fully-qualified hostname and domain name.

As root:

3. Set network information. In my case, I used static IPs.

4. Install mailman (this will also install apache2, postfix, python, etc):
```
apt-get install mailman
```

5. Check your installation:

```
cd /usr/lib/mailman
bin/check_perms
```

If there are errors, type:

```
bin/check_perms &#8211;f
```

Repeat previous step until no more errors are reported!

(When I did this, there were still 10 errors, but they were just links owned by root and didn't prove to be an issue)

6. Setup web server

```
cd /etc/apache2
vi apache2.conf
```

Add this to bottom:

```
ScriptAlias /mailman/ /usr/lib/cgi-bin/mailman/
ScriptAlias /cgi-bin/mailman/ /usr/lib/cgi-bin/mailman/

<Directory /usr/lib/cgi-bin/mailman/>
   AllowOverride None
   Options ExecCGI
   Order allow,deny
   Allow from all
</Directory>
Alias /pipermail/ /var/lib/mailman/archives/public/
<Directory /var/lib/mailman/archives/public>
   Options Indexes MultiViews FollowSymLinks
   AllowOverride None
   Order allow,deny
   Allow from all
</Directory>

<Directory /var/lib/mailman/archives/public>
   Options Indexes MultiViews FollowSymLinks
   AllowOverride None
   Order allow,deny
   Allow from all
</Directory>
```

Copy icons to apache:

```
cp /var/lib/mailman/icons/*.{jpg,png} /usr/share/apache2/icons
```

7. Setup Postfix

My main.cf file looks as such (I changed the domain name and IP for this example):

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version
smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
# appending .domain is the MUA's job.
append_dot_mydomain = no
# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h
myhostname = mailman.domainname.com
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases

myorigin = /etc/mailname
mydestination = $myhostname, domain.domainname.com, mail. domain.domainname.com
relayhost = 
mynetworks = 127.0.0.0/8, XX.XX.XXX.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
owner_request_special = no
unknown_local_recipient_reject_code = 550
smtp_sender_restrictions = permit_mynetworks, reject_unknown_sender_domain, permit
```

Make sure myhostname is an FQDN and that you add the mailman related hashes to alias_maps and alias_database.


8. Integrating Postfix & Mailman

Add this to the bottom of the /etc/mailman/mm_cfg.py file: 

```
MTA = 'Postfix'
```

I also had to edit the following line to have a slash at the end to get the URLS to send out correctly:
```

DEFAULT_URL_PATTERN = 'http://%s/cgi-bin/mailman/'
```

9. Run the bin/genaliases script to initialize your aliases file. 

But first I had to change the permissions of aliases.db

```
chmod 0664 /var/lib/mailman/data/aliases.db
```

Then:

```
cd /usr/lib/mailman
bin/genaliases
chown list:list /var/lib/mailman/data/aliases*
```

10. Create a site-wide mailing list

The config_list command assigns the configuration of this list from the sitelist.cfg file.  By default, it sets the list to not be advertised, if you want to change that, edit sitelist.cfg.

```
bin/newlist mailman
bin/config_list -i /var/lib/mailman/data/sitelist.cfg mailman
```

11. Setup Cron

```
cd cron
crontab -u list crontab.in
```

12. Setup mailman q runner

```
cd ..
bin/mailmanctl start

```

I originally had the following here as well, but this seems to break the init scripts.  With the Ubuntu 6.06 mailman installation, the init scripts should already be correct.  If you've already done this step, you can grab the correct init script from my post later in this thread.  DO NOT DO THESE STEPS:  cp scripts/mailman /etc/init.d/mailman                       update-rc.d mailman defaults


13. Check hostname

```
bin/fix_url.py
```

(Didn't work for me?)

14. Passwords

```
/usr/lib/mailman/bin/mmsitepass <your-site-password>
/usr/lib/mailman/bin/mmsitepass -c <list-creator-password>
```

15. Create redirection file for Apache2

Create a file in /var/www called index.html with the following content

```
<html>
<title>Mailman</title>
<meta http-equiv="refresh" content="0; url=http://mailman.domainname.com/mailman/listinfo">
</meta>
</html>
```

16. Reboot

17. For How-to-use instructions, go to [http://list.org/mailman-install/node45.html](http://list.org/mailman-install/node45.html).

---

### Post by lancer674 on 2006-06-13
Hello, newbie here, first time posting so please forgive any mistakes I make. 

Am trying to install mailman, have tried it on about every howto I could find. Tried it on on different distros and since we like Ubuntu best for our situation we are hoping to get it to work. My boss is wanting to get mailman up for our company and we are having a terrible time with it. First we tried the original howto in this thread and for the last few days we have been trying it with Ubuntu 6.06 Server. We have completed every step to the T and are having no luck. This is on a fresh install of Ubuntu 6.06 server in our lab environment.

This is the output when we restart:

File "/var/lib/mailman/bin/mailmanctl", line 554 ? in main()

File "/var/lib/mailman/bin/mailmanctl", line 389, in main lock = acquire_lock(force)

File "/var/lib/mailman/bin/mailmanctl", line 213, in acquire_lock lock = acquire_lock_1(force)

File "/var/lib/mailman/bin/mailmanctl", line 198, in acquire_lock_l lock.lock(0.1)

File "/usr/lib/mailman/Mailman/LockFile.py", line 243, in lock self._write()

File "/usr/lib/mailman/Mailman/LockFile.py", line 422, in _write fp =open(self._tmpfname, 'w')

IOError: [Errno 2] No such file or directory: '/var/lib/mailman/locks/master-qrunner.list.fqdn.3538.1'

Thank you so much for help in advance

---

### Post by mikec13 on 2006-06-13
Do you get any errors when you check the permissions?

---

### Post by lancer674 on 2006-06-13
Ya, 10 of them, at the time i had assumed that they were the same 10 that you had recieved, so I proceeded on.

---

### Post by mikec13 on 2006-06-15
Check in /var/lib/mailman/locks.  Is there anything there?  If so, what are the permissions.  Do an 'ls -al' and copy and paste the results here.

-mike

---

### Post by jayg25 on 2006-06-21
Mike,

I have been trying to get mailman to work and had the same error as the previous poster. When I try to get into the locks directory it wont let me but here is an ls-al of the above directory and a screenshot of my putty session:


root@list:/var/lib/mailman# ls -al
total 36
drwxrwsr-x  9 root list 4096 Jun 21 10:00 .
drwxr-xr-x 19 root root 4096 Jun 21 10:00 ..
lrwxrwxrwx  1 root root   24 Jun 21 10:00 Mailman -> /usr/lib/mailman/Mailman
drwxrwsr-x  4 root list 4096 Jun 21 10:00 archives
lrwxrwxrwx  1 root root   20 Jun 21 10:00 bin -> /usr/lib/mailman/bin
lrwxrwxrwx  1 root root   24 Jun 21 10:00 cgi-bin -> /usr/lib/cgi-bin/mailman
lrwxrwxrwx  1 root root   21 Jun 21 10:00 cron -> /usr/lib/mailman/cron
drwxrwsr-x  2 root list 4096 Jun 21 10:17 data
lrwxrwxrwx  1 root root   25 Jun 21 10:00 icons -> /usr/share/images/mailman
drwxrwsr-x  3 root list 4096 Jun 21 10:13 lists
lrwxrwxrwx  1 root root   18 Jun 21 10:00 locks -> ../../lock/mailman
lrwxrwxrwx  1 root root   17 Jun 21 10:00 logs -> ../../log/mailman
lrwxrwxrwx  1 root root   21 Jun 21 10:00 mail -> /usr/lib/mailman/mail
drwxrwsr-x 29 root list 4096 Jun 21 10:00 messages
drwxrwsr-x 11 list list 4096 Jun 21 10:15 qfiles
lrwxrwxrwx  1 root root   24 Jun 21 10:00 scripts -> /usr/lib/mailman/scripts
drwxrwsr-x  2 root list 4096 Apr  3 08:35 spam
lrwxrwxrwx  1 root root   12 Jun 21 10:00 templates -> /etc/mailman
drwxrwsr-x  4 root list 4096 Jun 21 10:00 tests

[IMG]http://www.jerryandmissy.com/work/putty.png[/IMG]

---

### Post by mikec13 on 2006-06-22
For those of you having permissions problems on the lock files/folders.  Replace the /etc/init.d/mailman file with the following:

```

#! /bin/sh
#
# mailman       starts up the qrunner for mailman

#               Based on skeleton, by those listed below.  Customizations
#               done by Tollef Fog Heen <tfheen@debian.org>
#
#               Written by Miquel van Smoorenburg <miquels@cistron.nl>.
#               Modified for Debian GNU/Linux
#               by Ian Murdock <imurdock@gnu.ai.mit.edu>.
#
# Version:      @(#)skeleton  1.9.1  08-Apr-2002  miquels@cistron.nl
#

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/lib/mailman/bin/mailmanctl
PIDFILE=/var/lib/mailman/data/master-qrunner.pid
NAME=mailman
DESC="mailman queue runner"

test -x $DAEMON || exit 0

set -e

if ! [ -d /var/run/mailman ]; then
    install -d -o list -g list /var/run/mailman
fi

if ! [ -d /var/lock/mailman ]; then
    install -d -o root -g list -m 2775 /var/lock/mailman
fi

case "$1" in
  start)
        if [ "$(/var/lib/mailman/bin/list_lists -b | grep ^mailman$ )" = "" ]; then
            echo "Site list for mailman (usually named mailman) missing"
            echo "Please create it; until then, mailman will refuse to start"
            exit 0
        fi
        $DAEMON -s start
        ;;
  stop)
        $DAEMON stop
        ;;
  reload)
        #
        #       If the daemon can reload its config files on the fly
        #       for example by sending it SIGHUP, do it here.
        #
        #       If the daemon responds to changes in its config file
        #       directly anyway, make this a do-nothing entry.
        #
        echo -n "Reloading $DESC configuration..."
        $DAEMON restart
  ;;
  restart|force-reload)
        #
        #       If the "reload" option is implemented, move the "force-reload"
        #       option to the "reload" entry above. If not, "force-reload" is
        #       just the same as "restart".
        #
        PID=`cat $PIDFILE 2>/dev/null` || true
        echo -n "Restarting $DESC: $NAME"
        $DAEMON stop
        if test -n "$PID" && kill -0 $PID 2>/dev/null ; then
                echo -n "Waiting "
                for cnt in `seq 1 5`; do
                        sleep 1
                        kill -0 $PID 2>/dev/null || break
                        echo -n "."
                done;
                if kill -0 $PID 2>/dev/null ; then
                        echo " Failed"
                else
                        echo " Done"
                fi
        fi
        $DAEMON start
        ;;
  *)
        N=/etc/init.d/$NAME
        # echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
        echo "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```

I've updated the how-to to reflect the changes needed to avoid this problem.

---

