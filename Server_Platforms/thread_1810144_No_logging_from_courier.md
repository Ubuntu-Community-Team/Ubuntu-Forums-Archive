---
title: "No logging from courier"
date: 2011-07-22
forum: Server Platforms
---

### Post by ninja9578 on 2011-07-22
I have spent an entire day trying to set up courier to work with our system, there is something wrong, but I can not for the life of me figure out what because there is absolutely zero logs.

Here is the /etc/syslog.conf
```
auth,authpriv.*                 /var/log/auth.log
*.*;auth,authpriv.none          -/var/log/syslog
#cron.*                         /var/log/cron.log
daemon.*                        -/var/log/daemon.log
kern.*                          -/var/log/kern.log
lpr.*                           -/var/log/lpr.log
mail.*                          /var/log/mail.log
user.*                          -/var/log/user.log

# Logging for INN news system
#
news.crit                       /var/log/news/news.crit
news.err                        /var/log/news/news.err
news.notice                     -/var/log/news/news.notice

#
# Some `catch-all' logfiles.
#
*.=debug;\
        auth,authpriv.none;\
        news.none;      -/var/log/debug
*.=info;*.=notice;*.=warning;\
        auth,authpriv.none;\
        cron,daemon.none;\
        news.none               -/var/log/messages

#
# Emergencies are sent to everybody logged in.
#
*.emerg                         *


daemon.*;\
        news.err;\
        *.=debug;*.=info;\
        *.=notice;*.=warning    |/dev/xconsole

```

Here is my /etc/courier/maildroprc
```
#
# Import variables
#
LOGNAME=tolower("$LOGNAME")
EXTENSION="$1"
RECIPIENT=tolower("$2")
USER="$3"
HOST="$4"
SENDER="$5"

DEFAULT="$HOME/$DEFAULT"
SPAMDIR="$DEFAULT.Spam/"

LOGUSERSETTINGS=1

#
# Autocreate logfile, if not existant
#

`test -e /var/log/mailfilter_log`
if ( $RETURNCODE != 0 )
{
    `touch /var/log/mailfilter_log`
}

logfile "/var/log/mailfilter_log"

if ( "$EXTENSION" ne "" )
{
    DELIMITER="+"
}

if (!$SENDER)
{
    SENDER = "<>"
}

#
# Autocreate maildir, if not existant
#
`test -e $DEFAULT`
if ( $RETURNCODE != 0 )
{
    `/bin/mkdir -p $DEFAULT`
    `/bin/rmdir $DEFAULT`
    if ( $MAILDIRQUPTA !=  )
    {
        `/usr/bin/maildirmake.courier -q $MAILDIRQUOTA $DEFAULT`
    }
    else
    {
        `/usr/bin/maildirmake.courier $DEFAULT`
    }
}
else
{
     if ( $MAILDIRQUOTA !=  )
    {
        `/usr/bin/maildirmake.courier -q $MAILDIRQUOTA $DEFAULT`
    }
    else
    {
        `test -e $DEFAULT/maildirsize`
        if ( $RETURNCODE == 0 )
        {
            `rm $DEFAULT/maildirsize`
        }

    }
}

#
# Check that user has his own maildrop include,
# if not available, check if $DEFAULT is set
# (newer maildrop get's that from the DB and updates
# it) and deliver or fail temporarily if not available
#
`test -f $HOME/.mailfilters/$LOGNAME`
if ( $RETURNCODE == 0 )
{
    include "$HOME/.mailfilters/$LOGNAME"
}

if ( /^X-Spam-Flag: YES/ )
{
    `test -d $SPAMDIR`
    if ( $RETURNCODE == 1 )
    {
        `maildirmake $SPAMDIR`
    }

    exception {
        to $SPAMDIR
    }

}
else
{
    if ( "$DEFAULT" ne "" )
    {
        exception {
            to "$DEFAULT"
        }
    }
    else
    {
        EXITCODE=75
        exit
    }
}
```

Here is my /etc/courier/authmysqlrc
```
MYSQL_SERVER            localhost
MYSQL_USERNAME          <removed>
MYSQL_PASSWORD          <removed>

MYSQL_DATABASE          <removed>

MYSQL_USER_TABLE        COURIER_PHONE_NUMBERS

# needs to be commented
#MYSQL_CRYPT_PWFIELD    crypt

MYSQL_CLEAR_PWFIELD     PASSWORD

MYSQL_UID_FIELD         UID

MYSQL_GID_FIELD         GID

MYSQL_LOGIN_FIELD       EMAIL

MYSQL_HOME_FIELD        HOMEDIR

# needs to be commented
#MYSQL_NAME_FIELD       name

MYSQL_MAILDIR_FIELD     MAILDIR

```

The <removed> parts have nothing to do with the problem, I am 100% sure that these are correct, as they are used everywhere.

---

