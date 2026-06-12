---
title: "CUPS and Kerberos"
date: 2008-10-28
forum: Server Platforms
---

### Post by platinummonkey on 2008-10-28
**linked to [http://usalug.org/phpBB2/viewtopic.php?t=13679](http://usalug.org/phpBB2/viewtopic.php?t=13679)**

Okay, so quite a picky question, but I've searched all over the net and the lack of non-repetitive documentation amazes me x.x

The situation:
one ubuntu 8.04 printserver (were calling it "LP") Protocol: IPP
one opensuse 10.3 printserver (calling it "LP-SUSE") Protocol: IPP
a KDC server
a LDAP server

pretty standard setup as far as users on a lab goes. The KDC and LDAP are set up correctly, and all boxes we are talking about run linux (either opensuse 10.3 or ubuntu 8.04 [we are migrating to ubuntu slowly])
Users log in (authenticate and retrieve fileserver space, etc etc)..

Now when they print on the current opensuse boxes (from LP_SUSE), it does not ask for a password using standard lpr command (or some other form) which is what we want. I am setting up LP, and ran into a problem getting CUPS to use the existing kerberos ticket when printing. instead it authenticates against the KDC every time you want to print, prompting for a password x.x very annoying, and we know this can be avoided.

The issue is, for some reason, I cannot get this to work, all of the docs describe how to enabled Kerberos authentication, but they all require a password to re-authenticate for every printjob... x.x

I'm at a loss on how to resolve this :(


Sources:
[http://www.cups.org/documentation.php/kerberos.html](http://www.cups.org/documentation.php/kerberos.html)
[http://localhost:631/help/kerberos.html?QUERY=kerberos](http://localhost:631/help/kerberos.html?QUERY=kerberos) (if you have cups installed that is easier to read)

cupsd.conf on LP is attached (i've hidden some ip address in both files, but they are correct ;))
cupsd.conf from LP-SUSE is attached as well... what confuses me is it has cups 1.2, using authtype of basic...

someone has mentioned samba, but from my understanding samba is mainly used to integrate AD and winders... unless im mistaken?

Thanks for any and all help :D

---

### Post by platinummonkey on 2008-10-30
[ bump ]

---

### Post by platinummonkey on 2008-11-02
[bump]

really? no ideas at least? :/

using pam seems more and more appropriate here; but, I'm not sure how to create an entry for cups unfortunately. there is a cupsys in /etc/pam.d that @includes common-{auth,account,passwd} but nothing else. I would assume cups would fallback on the pam entry for authentication. (Meaning, that even if I set the defaultauthtype to basic, the pam entry would properly check validation without password prompt using the existing cached kerberos ticket for that user)... but, how to do that I am unsure.

source:
[http://www.kernel.org/pub/linux/libs/pam/]("http://www.kernel.org/pub/linux/libs/pam/")
[http://www.centos.org/docs/5/html/Deployment_Guide-en-US/ch-pam.html]("http://www.centos.org/docs/5/html/Deployment_Guide-en-US/ch-pam.html")

Edit: added source link

---

### Post by platinummonkey on 2008-11-20
[bump]

still nothing :/


I am willing to listen to solutions involving using samba to print (since samba already has the desired kerberized authentication method), or perhaps, there is a setting required in the kdc.conf or the krb5.conf?  There is very little documentation on this, and its becoming increasingly frustrating. :P

---

### Post by platinummonkey on 2008-11-24
Dear diary,

I found a kludge of a solution. I plan on testing it tuesday on a virtualized printserver and a real ubuntu 8.04 box.

[http://www.spearce.org/2005/08/kerberos_printi.html](http://www.spearce.org/2005/08/kerberos_printi.html) - from an rpi grad student on mac os, but it should work on linux (maybe a few tweaks required, we'll see.)

Sincerely,
platinummonkey

P.S. if you didn't get the joke... this has turned into a journal pretty much.. <sarcasm>thx guys! :D </sarcasm>

---

### Post by platinummonkey on 2008-12-02
Notes on install:

to configure:```
./configure --prefix=/usr/local/lprng --enable-ssl --enable-force_localhost --enable-kerberos CPPFLAGS=-I/usr/src/linux-headers-`uname -r`/include/config/rpcsec/gss LDFLAGS=-L/usr/lib --with-gnu-ld
```

make:```
$make
if [ "UTILS" = po ] ; then \
	    for i in po/Makefile* ; do \
		if [ -f "$i" ] ; then \
		    if grep '^mkinstalldirs.*=.*case' $i ; then \
			echo "fixing broken $i which causes wrong path to mkinstalldirs to be used"; \
			perl -spi -e 's:^mkinstalldirs\s*=\s*.*:mkinstalldirs = \$(SHELL) \$(MKINSTALLDIRS):' $i; \
		    fi \
		fi \
	    done \
	fi
/bin/sh: Syntax error: end of file unexpected (expecting "fi")
/bin/sh:     for i in po/Makefile* ; do \: not found
/bin/sh: 	if [ -f "$i" ] ; then \: not found
/bin/sh: 	    if grep '^mkinstalldirs.*=.*case' $i ; then \: not found
/bin/sh: 		echo "fixing broken $i which causes wrong path to mkinstalldirs to be used"; \: not found
/bin/sh: 		perl -spi -e 's:^mkinstalldirs\s*=\s*.*:mkinstalldirs = \$(SHELL) \$(MKINSTALLDIRS):' $i; \: not found
/bin/sh: 	    fi \: not found
/bin/sh: 	fi \: not found
/bin/sh:     done \: not found
/bin/sh: Syntax error: "fi" unexpected
make: *** [UTILS] Error 2

```crap... -- working on it :P

using mit kerberos 5, heimdal does not work... missing necessary libraries for configure.

*kludging away*

---

### Post by Masuran on 2008-12-02
I think this quote from the CUPS documentation lists your problem:
*In order to support printing to a shared printer, CUPS has to ask the KDC for a copy of your credentials (this is called delegation) that can be sent to the remote server for authenticatation. Delegation only works when the system has a stable hostname which maps to the current address of the system, which is why you need a static IP address or DHCP that updates the DNS entry for your system.*

Is it possible that delegation fails because the client hostname can't be resolved correctly?

---

### Post by platinummonkey on 2008-12-11
> **Masuran said:**
> 
Is it possible that delegation fails because the client hostname can't be resolved correctly?

No, this is not the issue at hand. The issue is authenticating once, and only once (at login, much like single-sign-on setup) and using those credentials to verify printing, instead of authenticating for each print job (as the current method built into cups uses gssapi over https) (meaning it asks you for your password on each print request).

But to answer your question, all such said machines resolve without issues. (Static IP)

Thanks for the reply though :D

EDIT: I have been busy with Finals this last week, so I am finally getting back into it with perhaps a fresh mind :P

---

### Post by platinummonkey on 2009-02-22
SOLVED!

[http://tamulug.tamu.edu/wiki/cups_kerberos](http://tamulug.tamu.edu/wiki/cups_kerberos)

---

### Post by HermanAB on 2009-02-22
You were really breaking new ground here!

Cheers,

Herman

---

### Post by -ph3nix- on 2010-03-03
> **platinummonkey said:**
> SOLVED!

[http://tamulug.tamu.edu/wiki/cups_kerberos](http://tamulug.tamu.edu/wiki/cups_kerberos)

This really helped put me in the right direction - however the script did not seem to work well with my Ubuntu systems. I modified the script as follows and it seems to work beautifully:

```

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
strPrintCommand="smbclient //$strServer/$strPrinter -k -E -U \"$strUserName\" -c \"print $strTmpFile\""
echo "Print command used is: $strPrintCommand" >> $output
`su -c "$strPrintCommand" $strUserName`
intReturn=$?
echo "Return code from smbclient: $intReturn" >> $output

# clean up
if [ -f $strTmpFile ]; then
    rm $strTmpFile
fi
unset KRB5CCNAME

# Hw do we exit?
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

```

---

### Post by platinummonkey on 2010-04-09
workaround for FF3+!!! (you can use kprinter or another printing dialog of your choice, the script uses kprinter though)

[http://tamulug.tamu.edu/wiki/firefox_print_kerberos](http://tamulug.tamu.edu/wiki/firefox_print_kerberos)

this will still let your other programs print without double dialogs ;)

---

