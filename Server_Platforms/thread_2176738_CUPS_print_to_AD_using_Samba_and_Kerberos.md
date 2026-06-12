---
title: "CUPS print to AD using Samba and Kerberos"
date: 2013-09-25
forum: Server Platforms
---

### Post by Peter_Watkins on 2013-09-25
I'm running Ubuntu Server Precise 12.04. I'm authenticating all my users to a Windows Active Directory server using PBIS--that part works just fine. Kerberos works as far as I can tell. Now I'd like to print to the Windows printer servers without prompting users for their password (if they've already logged in).

I have a couple questions:
1) Do I need to enable Kerberos in CUPS? i.e. check "Use Kerberos authentication" in the web interface. BTW, I've tried this but all it does is lock me out the web interface.

2) Do I need to mess up the permissions of my cups backends like this user did:
[http://permalink.gmane.org/gmane.comp.printing.cups.general/23095](http://permalink.gmane.org/gmane.comp.printing.cups.general/23095)

3) Is CUPS broken in 12.04? Does it require a wrapper backend like this user wrote?
[http://tamulug.tamu.edu/wiki/cups_kerberos](http://tamulug.tamu.edu/wiki/cups_kerberos)
See "Alternative CUPS Backend Solution Updated"

It seems like there are a number of hacky solutions out there--some of them are for setting up a print server to which other Linux client can print--that's not what I'm looking for. I just want users who are logged into my Linux box to not have to enter a password when they print.

To show that Samba and Kerberos are working, the following works fine:
```
export DEVICE_URI=smb://ds-print2-1/PR-G-08
/usr/lib/cups/backend/smb 234 me test 1 none hello.txt
```

The print job completes and doesn't prompt me for a password.

---

### Post by Peter_Watkins on 2013-09-27
So I ended up going with the backend wrapper approach. It's a hack but it works. Here's my wrapper (just a slight modification on all the others). Notice the commented out line with smbclient--this is if you don't have access to smbspool (i.e. [https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/293608](https://bugs.launchpad.net/ubuntu/+source/samba4/+bug/293608)).

[CODE]
#!/bin/sh
# To be put in the /usr/lib/cups/backend/
# Allow Samba kerberized printing on Ubuntu.

# Created by Sam Mousa - July 2009
# Based on code by A. Martins-Melo.
# 2010/03/03: Updated by Andre Dill

# Debuging
booDebug=1
strDebugFile="/tmp/printlog"
if [ $booDebug -eq 0 ]; then
    output=/dev/null
else
    output=$strDebugFile
fi

# check arguments recieved
if [ $# -eq 0 ]; then
    echo 'network ksmb "Unknown" "Windows Printer via SAMBA with Kerberos support"'
    exit 0
elif [ $# -lt 4 ]; then
    echo "Usage: $0 job-id user title copies options [file]\n"
    exit 1
elif [ $# -gt 6 ]; then
    echo "Usage: $0 job-id user title copies options [file]\n"
    exit 1
fi

# Username
strUserName=$2

# Extract Windows printer name and server
strPrinter=`echo $DEVICE_URI | sed 's,k*smb://,,g'`
strServer=`echo $strPrinter | sed 's,/.*$,,g'`
strPrinter=`echo $strPrinter | sed 's,.*/,,g'`
# fix a space in printer name
strPrinter=`echo $strPrinter | sed 's,%20,\\\ ,g'`

# Set environment variable to ticket cache of user.
strTicketName=/tmp/krb5cc_`id -u "$strUserName"`
KRB5CCNAME=`ls $strTicketName*`

# Debugging:
if [ $booDebug -eq 1 ]; then
    echo "Printer: $strPrinter"      >> $output
    echo "Server: $strServer"        >> $output
    echo "Ticket cache: $KRB5CCNAME" >> $output
fi

# Export it so smbclient uses it.
export KRB5CCNAME

# data file
strTmpFile=/tmp/print.$$

if [ $# -eq 5 ]; then
    # There are 5 arguments input will follow on stdin.
    echo "Five arguments received. Tempfile created at $strTmpFile." >> $output
    cat - > $strTmpFile

else
    # There are 6 arguments, the 6th is the filename.
    echo "Six arguments received." >> $output
    if [ -f $6 ]; then
        cp $6 $strTmpFile
    fi
fi

# print the file
chown $strUserName $strTmpFile
#strPrintCommand="smbclient //$strServer/$strPrinter -k yes -E -c \"print $strTmpFile\""
strPrintCommand="smbspool smb://$strServer/$strPrinter $1 $2 $3 $4 \"$5\" $strTmpFile"
echo "Print command used is: $strPrintCommand" >> $output
`su -c "$strPrintCommand" $strUserName`
intReturn=$?
echo "Return code from smbclient: $intReturn" >> $output

# clean up
if [ -f $strTmpFile ]; then
    rm $strTmpFile
fi
unset KRB5CCNAME

# How do we exit?
if [ $intReturn -eq 0 ]; then
    # If smbclient finished successfully return 0.
    echo "Exiting with exit code 0." >> $output
    exit 0
else
    # In all other cases return error code 1 which means Failed -- Note: this is not the same as returning $intReturn!
    echo "Exiting with exit code 1." >> $output
    echo "Note: If smbclient reports permission errors on the ticket cache" >> $output
    echo "      check the permissions on this file to make sure it is run " >> $output
    echo "      as root." >> $output
    echo "Dumping environment." >> $output
    env >> $output
    exit 1
fi

# END
[CODE]


I put this in /usr/lib/cups/backend/smb and renamed the old smb (a symbolic link to smbspool). Permissions are important on this file since CUPS uses file permissions to determine whether or not to run it as root (http://www.cups.org/documentation.php/doc-1.6/api-filter.html#PERMISSIONS). You need cups to run this as root since it'll switch to the user given in the print job info.

I wonder if the user-switching scheme based on the user-info with the print job is a security hole--any opinions?

This whole issue is already in a 2-year old bug: https://bugs.launchpad.net/ubuntu/+source/cups/+bug/788167

---

