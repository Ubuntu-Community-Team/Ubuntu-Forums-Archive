---
title: "shell script to ftp from a file (daily)"
date: 2007-11-10
forum: Server Platforms
---

### Post by miesnerd on 2007-11-10
So im relatively new to shell scripts, and im defiately new to using shell scripts to grab a file from a ftp. I already found a script which I think will work once I edit it a little bit, but I would like to add one more feature:
-I want the script to automatically run every day to pull down data from this ftp that I'll use. How do I add that in?
I'll copy and paste the script that I just got off the web that Im planning to edit:

:
##########################################################################
# Title      :	transfer.ftp - transfer a file using FTP
# Author     :	Heiner Steven <heiner.steven@odn.de>
# Date       :	1994-02-03
# Requires   :	ftp
# Category   :	System Administration
# SCCS-Id.   :	@(#) transfer.ftp	1.2 03/12/19
##########################################################################
# Description
#    -	transfers the file to the given host using FTP (binary
#	mode)
#    -	To automate the transfer, a temporary file "$HOME/.netrc"
#	will be created (if not already present)
##########################################################################

PN=`basename "$0"`			# Program name
VER='1.2'

Netrc=$HOME/.netrc

if [ \( $# -lt 1 \) -o \( ! -r "$1" \) ]
then
    echo >&2 "usage: $PN file [hostname]"
    exit 1
fi

File="$1"
Host="${2:-`uname -n`}"
Base=`basename "$File"`

# If $HOME/.netrc is readable and contains the target host name,
# try an automatic FTP transfer. Otherwise, create the file
# temporarily, and remove it later on.

[ -r $Netrc ] && grep "$Host" $Netrc > /dev/null || {
    User=`id | sed 's/uid=[0-9][0-9]*(\([^)]*\)).*/\1/'`
    echo -n "$PN: password ($User@$Host): "
    stty -echo
    read PW || { stty echo; exit 1; }
    stty echo
    echo " OK"

    if [ -r "$Netrc" ]
    then				# Create backup of old .netrc
    	mv "$Netrc" "$Netrc".$$
	trap 'mv "$Netrc".$$ "$Netrc"' 0
    else
        > "$Netrc"
	trap 'rm -f "$Netrc"' 0
    fi
    trap "exit 2" 1 2 3 15
    echo "machine $Host login $User password $PW" >> "$Netrc" || exit 1
    chmod 600 "$Netrc"
    ls -l "$Netrc"
}

ftp $Host <<!
bin
put $File $Base
quit
!

---

### Post by HermanAB on 2007-11-10
Here is a much simpler example for scripting FTP in Bash:

# Launch a scripted FTP session
Server="10.10.10.10"
Password="guest"
User="anonymous"
ftp -n $Server <<End-Of-Session
user "$User" "$Password"
binary
prompt off
cd wherever
mget *
bye
End-Of-Session

---

### Post by miesnerd on 2007-11-10
Herman-
Thanks for replying to me with a simpler script. How do I get it to run daily, automatically?

---

### Post by MJN on 2007-11-10
The main problem with scripting FTP connections/transfers is that should there be any issues with it (e.g. stalled transfer etc) then a strict command sequence would fail unless it has built-in error checking.

Hence, I would recommend you using lftp instead - it functions just like a normal FTP client but can handle most, if not all, non-fatal errors and will handle them automatically and appropriately.

On the very same basis as HermanAB's script (repeated as lftp uses slightly different command switches):

```
lftp -u <username>,<password> <ftp.server.address> <<EOF
   get <filename>
   ...<any other commands>...
   quit
EOF
```Stick that in a script (run **chmod u+x <script>** to make it executable) and use cron to execute it regularly as required (search for cron as there are a million and one examples of how to do this).

Mathew

P.S. I don't know if lftp is installed by default, if not install it with **apt-get install lftp**

---

### Post by HermanAB on 2007-11-10
Put the script in /usr/local/bin (the first line should be "#! /bin/bash") and make it executable.  Ensure that every command in the script uses the full path starting at '/', since cron doesn't search paths.  Then make a soft link from /etc/cron.daily to the script and it will run each morning at about 1 minute past 4am.

Cheers,

Herman

---

### Post by HermanAB on 2007-11-10
BTW, I agree that lftp and wget are both better than straight old fashioned ftp.  The best way to do backups is with rsync over ssh, but starting with ftp is not a bad idea since ftp servers are so common.

Cheers,

Herman

---

