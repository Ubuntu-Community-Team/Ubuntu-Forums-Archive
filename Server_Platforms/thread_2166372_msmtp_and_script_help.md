---
title: "msmtp and script help"
date: 2013-08-09
forum: Server Platforms
---

### Post by Oscifer on 2013-08-09
I'm running ZFS on my ubuntu server NAS box.  I'd like to run a script once a week to scrub my pool.  I borrowed this FreeNAS bash script and I'm trying to get it to work properly. After some adjustments I'm still having issues with msmtp and having it send an email with the results. If anyone can help out I would appreciate it.

[PHP]#!/bin/bash

#VERSION: 0.2
#AUTHOR: gimpe
#EMAIL: gimpe [at] hype-o-thetic.com
#WEBSITE: http://hype-o-thetic.com
#DESCRIPTION: Created on FreeNAS 0.7RC1 (Sardaukar)
# This script will start a scrub on each ZFS pool (one at a time) and
# will send an e-mail or display the result when everyting is completed.

#CHANGELOG
# 0.2: 2009-08-27 Code clean up
# 0.1: 2009-08-25 Make it work

#SOURCES:
# http://aspiringsysadmin.com/blog/2007/06/07/scrub-your-zfs-file-systems-regularly/
# http://www.sun.com/bigadmin/scripts/sunScripts/zfs_completion.bash.txt
# http://www.packetwatch.net/documents/guides/2009073001.php

# e-mail variables
FROM=user@gmail.com
TO=user@gmail.com
SUBJECT="$0 results"
BODY=""

# arguments
VERBOSE=0
SENDEMAIL=1
args=("$@")
for arg in $args; do
    case $arg in
        "-v" | "--verbose")
            VERBOSE=1
            ;;
        "-n" | "--noemail")
            SENDEMAIL=0
            ;;
        "-a" | "--author")
            echo "by gimpe at hype-o-thetic.com"
            exit
            ;;
        "-h" | "--help" | *)
            echo "
usage: $0 [-v --verbose|-n --noemail]
    -v --verbose    output display
    -n --noemail    don't send an e-mail with result
    -a --author     display author info (by gimpe at hype-o-thetic.com)
    -h --help       display this help
"
            exit
            ;;
    esac
done

# work variables
ERROR=0
SEP=" - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - - "
RUNNING=1

# commands & configuration
ZPOOL=/sbin/zpool
PRINTF=/usr/bin/printf
MSMTP=/usr/bin/msmtp
MSMTPCONF=/home/user/.msmtprc

# print a message
function _log {
    DATE="`date +"%Y-%m-%d %H:%M:%S"`"
    # add message to e-mail body
    BODY="${BODY}$DATE: $1n"

    # output to console if verbose mode
    if [ $VERBOSE = 1 ]; then
        echo "$DATE: $1"
    fi
}

# find all pools
pools=$($ZPOOL list -H -o name)

# for each pool
for pool in $pools; do
    # start scrub for $pool
    _log "starting scrub on $pool"
    zpool scrub $pool
    RUNNING=1
    # wait until scrub for $pool has finished running
    while [ $RUNNING = 1 ];     do
        # still running?
        if $ZPOOL status -v $pool | grep -q "scrub in progress"; then
            sleep 60
        # not running
        else
            # finished with this pool, exit
            _log "scrub ended on $pool"
            _log "`$ZPOOL status -v $pool`"
            _log "$SEP"
            RUNNING=0
            # check for errors
            if ! $ZPOOL status -v $pool | grep -q "No known data errors"; then
                _log "data errors detected on $pool"
                ERROR=1
            fi
        fi
    done
done

# change e-mail subject if there was error
if [ $ERROR = 1 ]; then
    SUBJECT="${SUBJECT}: ERROR(S) DETECTED"
fi

# send e-mail
if [ $SENDEMAIL = 1 ]; then
    $PRINTF "From:$FROMnTo:$TOnSubject:$SUBJECTnn$BODY" | $MSMTP --file=$MSMTPCONF -t
fi

[/PHP]

The output is working correctly with the exception of "msmtp: no recipents found" at the end and no email being sent out.

---

### Post by prodigy_ on 2013-08-09
> **Oscifer said:**
> ```
$PRINTF "From:$FROMnTo:$TOnSubject:$SUBJECTnn$BODY" | $MSMTP --file=$MSMTPCONF -t
```
Never used msmtp but I guess this line should look like: ```

$PRINTF "From:${FROM}\nTo:${TO}\nSubject:${SUBJECT}\n\n$BODY" | $MSMTP --file=$MSMTPCONF -t
```

---

### Post by Oscifer on 2013-08-10
> **prodigy_ said:**
> Never used msmtp but I guess this line should look like: ```

$PRINTF "From:${FROM}\nTo:${TO}\nSubject:${SUBJECT}\n\n$BODY" | $MSMTP --file=$MSMTPCONF -t
```


Alright thanks, I'll give that a try.

---

