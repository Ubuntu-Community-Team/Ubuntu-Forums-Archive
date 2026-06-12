---
title: "Ubuntu server/desktop log monitoring via email without the need of a mail server."
date: 2009-09-16
forum: Tutorials
---

### Post by ukripper on 2009-09-16
**[SIZE="4"][B]_[COLOR="Blue"]Ubuntu server/desktop log monitoring via email without the need of a mail server.[/COLOR]_**[/SIZE][/B]

I wanted a solution which would allow me to send emails to my normal email address without the hassle of having a mail server running alongside my ftp and mysql server. Also for security reason I didn't want to open any extra port (25) just for this purpose.

Please read before proceeding:
This tutorial is for people who don't like to have unnecessary mailserver or MTA installed just for sending out emails via terminal or shell script.

Taken from Sendemail's website : [http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)
> "About SendEmail
SendEmail is a lightweight, command line SMTP email client. If you have the need to send email from a command line, this free program is perfect: simple to use and feature rich. It was designed to be used in bash scripts, batch files, Perl programs and web sites, but is quite adaptable and will likely meet your requirements. SendEmail is written in Perl and is unique in that it requires NO MODULES. It has an intuitive and flexible set of command-line options, making it very easy to learn and use.
[Supported Platforms: Linux, BSD, OS X, Windows 98, Windows NT, Windows 2000, & Windows XP]"




This guide has been tested against Ubuntu 8.04-LTS server 32bit and 64bit and Ubuntu 9.04 Desktop 64bit.

First of all we need to install sendEmail package for sending out emails to Gmail or yahoo or whichever email provider you have account with. SendEmail is not like sendmail, for SendEmail you don't need mail server or MTA setup. Only thing you need is your account with some email provider that's all. For this purpose I'd rather create an additional account (for security purposes) with some provider and use the new account as sending emails to my normal email address. This way we won't have to place our normal email password when sending out logs, instead we use new password for the newly created email account.

So let's begin with our logs monitoring -

Create a new account with gmail (I prefer gmail to other providers you may choose any of your choice). Make sure you remember new userid and password for it.

Install logwatch package from ubuntu repos:
```
sudo apt-get install logwatch
```

[COLOR="Red"]**Note:**[/COLOR] Here postfix will be installed by default but we won't be using it, let it install.

Once logwatch is installed we will install the latest version of SendEmail package as below:


```
wget http://caspian.dotconf.net/menu/Software/SendEmail/sendEmail-v1.55.tar.gz
```

Unpack it:
```
tar zxvf sendEmail-v1.55.tar.gz
```

Copy it to /usr/local/bin/
```
sudo cp sendEmail-v1.55/sendEmail /usr/local/bin
```

Apply the correct Permissions:
```
sudo chmod +x /usr/local/bin/sendEmail
```


We also need to install some other packages it depends upon:
```
sudo apt-get install libio-socket-ssl-perl libnet-ssleay-perl perl
```

Now your sendEmail and logwatch is installed, we are going to test sending out email:

In terminal type:

> sendEmail -v -f [email]username@gmail.com[/email] -s smtp.gmail.com:587 -xu username -xp yourpassword -t your-normal-emailaddress -o tls=yes -u title goes here -m Message goes here -a attachment goes here

Replace the above accordingly, see below for details-

**-v** means verbose incase you want to see what is happening for more verbose you can use -vvvv.

**-f** means Mailfrom
username@gmail is your newly created account with an email provider.

**-s** option is for your outgoing smtp server for gmail it is either port 587 or 465
Outgoing Mail (SMTP) Server - requires TLS: smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: **465 or 587**

**-t** is the target email address where you want to send the email to.

**-o** is to set tls which is yes for gmail.

**-u** is for subject line.

**-m** is for message you want to type

**-a** is to attach your logwatch file which we will see next how to do that.


Now after testing if you are receiving emails from SendEmail we can proceed to next step. Before proceeding any further, make sure till here you are receiving emails in your normal email account.

Backup the default configuration of logwatch:
```
sudo cp -v /usr/share/logwatch/default.conf/logwatch.conf /usr/share/logwatch/default.conf/logwatch.conf_backup
```


open logwatch default configuration:
```
sudo vi /usr/share/logwatch/default.conf/logwatch.conf
```

Change/copy-paste the configuration as below:

```
########################################################
# This was written and is maintained by:
#    Kirk Bauer <kirk@kaybee.org>
#
# Please send all comments, suggestions, bug reports,
#    etc, to kirk@kaybee.org.
#
########################################################

# NOTE:
#   All these options are the defaults if you run logwatch with no
#   command-line arguments.  You can override all of these on the
#   command-line.

# You can put comments anywhere you want to.  They are effective for the
# rest of the line.

# this is in the format of <name> = <value>.  Whitespace at the beginning
# and end of the lines is removed.  Whitespace before and after the = sign
# is removed.  Everything is case *insensitive*.

# Yes = True  = On  = 1
# No  = False = Off = 0

# Default Log Directory
# All log-files are assumed to be given relative to this directory.
LogDir = /var/log

# You can override the default temp directory (/tmp) here
TmpDir = /var/cache/logwatch

# Default person to mail reports to.  Can be a local account or a
# complete email address.  Variable Print should be set to No to
# enable mail feature.
# MailTo = root
# WHen using option --multiemail, it is possible to specify a different
# email recipient per host processed.  For example, to send the report
# for hostname host1 to user@example.com, use:
#Mailto_host1 = user@example.com
# Multiple recipients can be specified by separating them with a space.

# Default person to mail reports from.  Can be a local account or a
# complete email address.
# MailFrom = Logwatch

# If set to 'Yes', the report will be sent to stdout instead of being
# mailed to above person.
Print = No

# if set, the results will be saved in <filename> instead of mailed
# or displayed.
Save = /tmp/logwatch

# Use archives?  If set to 'Yes', the archives of logfiles
# (i.e. /var/log/messages.1 or /var/log/messages.1.gz) will
# be searched in addition to the /var/log/messages file.
# This usually will not do much if your range is set to just
# 'Yesterday' or 'Today'... it is probably best used with
# By default this is now set to Yes. To turn off Archives uncomment this.
#Archives = No
# Range = All

# The default time range for the report...
# The current choices are All, Today, Yesterday
Range = yesterday

# The default detail level for the report.
# This can either be Low, Med, High or a number.
# Low = 0
# Med = 5
# High = 10
Detail = Med


# The 'Service' option expects either the name of a filter
# (in /usr/share/logwatch/scripts/services/*) or 'All'.
# The default service(s) to report on.  This should be left as All for
# most people.  
Service = All
# You can also disable certain services (when specifying all)
Service = "-zz-network"     # Prevents execution of zz-network service, which
                            # prints useful network configuration info.
Service = "-zz-sys"         # Prevents execution of zz-sys service, which
                            # prints useful system configuration info.
Service = "-eximstats"      # Prevents execution of eximstats service, which
                            # is a wrapper for the eximstats program.
# If you only cared about FTP messages, you could use these 2 lines
# instead of the above:
#Service = ftpd-messages   # Processes ftpd messages in /var/log/messages
#Service = ftpd-xferlog    # Processes ftpd messages in /var/log/xferlog
# Maybe you only wanted reports on PAM messages, then you would use:
#Service = pam_pwdb        # PAM_pwdb messages - usually quite a bit
#Service = pam             # General PAM messages... usually not many

# You can also choose to use the 'LogFile' option.  This will cause
# logwatch to only analyze that one logfile.. for example:
#LogFile = messages
# will process /var/log/messages.  This will run all the filters that
# process that logfile.  This option is probably not too useful to
# most people.  Setting 'Service' to 'All' above analyizes all LogFiles
# anyways...

#
# By default we assume that all Unix systems have sendmail or a sendmail-like system.
# The mailer code Prints a header with To: From: and Subject:.
# At this point you can change the mailer to any thing else that can handle that output
# stream. TODO test variables in the mailer string to see if the To/From/Subject can be set
# From here with out breaking anything. This would allow mail/mailx/nail etc..... -mgt
# mailer = "sendmail -t"

#
# With this option set to 'Yes', only log entries for this particular host
# (as returned by 'hostname' command) will be processed.  The hostname
# can also be overridden on the commandline (with --hostname option).  This
# can allow a log host to process only its own logs, or Logwatch can be
# run once per host included in the logfiles.
#
# The default is to report on all log entries, regardless of its source host.
# Note that some logfiles do not include host information and will not be
# influenced by this setting.
#
#HostLimit = Yes

# vi: shiftwidth=3 tabstop=3 et

```


The above config had been modified to only save logwatch output in a file called logwatch in the tmp directory. sendEmail will do the rest for us to deliver it to you via email.

Now you have changed the config file. Save it and run following command in terminal to test the logwatch in operation.
```
sudo logwatch
```

After the command has finished running, check your logwatch file in your tmp directory.
```
vi /tmp/logwatch
```

if there is output and you can see your logs then congratulation you have successfully setup logwatch.

Now for sending email to yourself follow my previous annotation for sendEmail posted above in this post.
for example:
> sudo sendEmail -v -f [email]username@gmail.com[/email] -s smtp.gmail.com:587 -xu username -xp yourpassword -t your-normal-emailaddress -o tls=yes -u title goes here -m Message goes here -a /tmp/logwatch

Next thing  to check is your normal email account whether you have received the logwatch file or not.

After you have confirmed you are getting your logs via emails it is time to create a shell script to run automatically for you every day using cron.

So first create a shell script.
sudo vi logwatch-sendemail.bash

```
#!/bin/bash

/usr/sbin/logwatch

sendEmail -v -f username@gmail.com -s smtp.gmail.com:587 -xu username -xp yourpassword -t your-normal-emailaddress -o tls=yes -u title goes here -m Message goes here -a /tmp/logwatch

exit

```
save and exit.

make it executable:
```
sudo chmod +x logwatch-sendemail.bash
```


Now let's crontab the job.

```
sudo crontab -e
```

while in crontab add the following entry to run everyday at 11:00am
```
00 11 * * * /home/skynet/logwatch-sendemail.bash
```

save and exit.

Now you'll receive email everyday at 11:00am with your logs.

That's it for now.


References:

[http://caspian.dotconf.net/menu/Software/SendEmail/](http://caspian.dotconf.net/menu/Software/SendEmail/)

[http://www.debianhelp.co.uk/logwatch1.htm](http://www.debianhelp.co.uk/logwatch1.htm)

[http://www.stellarcore.net/logwatch/tabs/docs/logwatch.8.html](http://www.stellarcore.net/logwatch/tabs/docs/logwatch.8.html)

[http://ubuntuforums.org/showthread.php?p=7084234](http://ubuntuforums.org/showthread.php?p=7084234)

---

### Post by fullmoonguru on 2013-02-11
Bringing this one back from the dead.  Trying this on 12.04.  I got through the first part OK, but logwatch is not creating the file in the tmp directory.  Actually, the directory in the script is different than what it says in the directions, but even after changing that there's no file there.  

Any advice, or link to updated instructions?

---

