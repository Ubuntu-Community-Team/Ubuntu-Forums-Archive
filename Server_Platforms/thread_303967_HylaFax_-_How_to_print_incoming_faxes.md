---
title: "HylaFax - How to print incoming faxes"
date: 2006-11-21
forum: Server Platforms
---

### Post by salvo1 on 2006-11-21
Here in office I tried HylaFax to move on linux also this service (together with proxy and mail)

I can send faxes.
I found nice clients for Windows that install a virtual printer and all is ok, the modem configuration too.

When a fax arrive, i can see a new email in my root account with fax in PDF (as attachment).
But this is not good, because secretaries are not able to download attachement and print (this is sad, but real).

I need to print incoming faxes.

I already saw: [http://www.hylafax.org/content/Automatically_print_incoming_faxes](http://www.hylafax.org/content/Automatically_print_incoming_faxes)

My printer HP Laserjet 1320 works:
```
$lpr file.ps
$lpr file.pdf
$cat file.txt | lpr
```

and i can print both file.pdf and file.txt

so that i modified ```
/var/spool/hylafax/bin/faxrcvd
```
the script runned every time a fax arrive.

I added: ```
lpr $FILE
```

The file arrive by mail, but it isn't printed!!!

I modified faxrcvd:
```
serverlinux@serverlinux:/var/spool/hylafax/bin$ cat faxrcvd
tiff2ps -a -h 11.1082 -w 7.8543 $1 | lpr
```

I receive faxes there:
```
serverlinux@serverlinux:/var/spool/hylafax/recvq$ ls
fax000000012.tif  seqf
```

But nothing printed:

This is the log:
```
serverlinux@serverlinux:/var/spool/hylafax/log$ ls
c000000001  c000000006  c000000011  c000000016  c000000021  xferfaxlog
c000000002  c000000007  c000000012  c000000017  c000000022
c000000003  c000000008  c000000013  c000000018  c000000023
c000000004  c000000009  c000000014  c000000019  c000000024
c000000005  c000000010  c000000015  c000000020  seqf

serverlinux@serverlinux:/var/spool/hylafax/log$ cat c000000024
Nov 21 09:19:50.07: [ 5279]: SESSION BEGIN 000000024 878***8
[...]
Nov 21 09:20:24.27: [ 5279]: RECV send MCF (message confirmation)
Nov 21 09:20:24.27: [ 5279]: RECV FAX (000000024): from 091891***8,
page 1 in 0:25, INF, 3.85 line/mm, 1-D MH, 14400 bit/s
Nov 21 09:20:24.27: [ 5279]: RECV FAX (000000024):
recvq/fax000000012.tif from 091891***8, route to <unspecified>, 1
pages in 0:29
Nov 21 09:20:24.27: [ 5279]: <-- [9:AT+FRH=3\r]
Nov 21 09:20:25.23: [ 5279]: --> [7:CONNECT]
Nov 21 09:20:25.97: [ 5279]: --> [2:OK]
Nov 21 09:20:25.97: [ 5279]: RECV recv DCN (disconnect)
Nov 21 09:20:25.97: [ 5279]: RECV FAX: bin/faxrcvd
"recvq/fax000000012.tif" "ttyS1" "000000024" ""
Nov 21 09:20:25.97: [ 5279]: RECV FAX: end
Nov 21 09:20:25.97: [ 5279]: SESSION END
```

So that i run...:
```
serverlinux@serverlinux:/var/spool/hylafax$ bin/faxrcvd
"recvq/fax000000012.tif" "ttyS1" "000000024" ""
```

and the printer works!! The fax is printed!!!

All folders and files in */hylafax are 0777.

Ideas?

---

### Post by salvo1 on 2006-11-21
faxrcvd:

```
#! /bin/sh
#	$Id: faxrcvd.sh.in,v 1.27 2006/01/09 19:26:37 aidan Exp $
#
# HylaFAX Facsimile Software
#
# Copyright (c) 1990-1996 Sam Leffler
# Copyright (c) 1991-1996 Silicon Graphics, Inc.
# HylaFAX is a trademark of Silicon Graphics
# 
# Permission to use, copy, modify, distribute, and sell this software and 
# its documentation for any purpose is hereby granted without fee, provided
# that (i) the above copyright notices and this permission notice appear in
# all copies of the software and related documentation, and (ii) the names of
# Sam Leffler and Silicon Graphics may not be used in any advertising or
# publicity relating to the software without the specific, prior written
# permission of Sam Leffler and Silicon Graphics.
# 
# THE SOFTWARE IS PROVIDED "AS-IS" AND WITHOUT WARRANTY OF ANY KIND, 
# EXPRESS, IMPLIED OR OTHERWISE, INCLUDING WITHOUT LIMITATION, ANY 
# WARRANTY OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE.  
# 
# IN NO EVENT SHALL SAM LEFFLER OR SILICON GRAPHICS BE LIABLE FOR
# ANY SPECIAL, INCIDENTAL, INDIRECT OR CONSEQUENTIAL DAMAGES OF ANY KIND,
# OR ANY DAMAGES WHATSOEVER RESULTING FROM LOSS OF USE, DATA OR PROFITS,
# WHETHER OR NOT ADVISED OF THE POSSIBILITY OF DAMAGE, AND ON ANY THEORY OF 
# LIABILITY, ARISING OUT OF OR IN CONNECTION WITH THE USE OR PERFORMANCE 
# OF THIS SOFTWARE.
#

#
# faxrcvd file devID commID error-msg
#
if [ $# -lt 4 ]; then
    echo "Usage: $0 file devID commID error-msg [ callID-1 [ callID-2 [ ... [ callID-n ] ] ] ]"
    exit 1
fi

test -f etc/setup.cache || {
    SPOOL=`pwd`
    cat<<EOF

FATAL ERROR: $SPOOL/etc/setup.cache is missing!

The file $SPOOL/etc/setup.cache is not present.  This
probably means the machine has not been setup using the faxsetup(8)
command.  Read the documentation on setting up HylaFAX before you
startup a server system.

EOF
    exit 1
}

# These settings may not be present in setup.cache if user upgraded and
# didn't re-run faxsetup; we set them before calling setup.cache for
# backward compatibility.
ENCODING=base64
MIMENCODE=mimencode
TIFF2PDF=bin/tiff2pdf
TTYCMD=tty

. etc/setup.cache

INFO=$SBIN/faxinfo
FAX2PS=$TIFFBIN/fax2ps
TIFF2PS=tiff2ps
TOADDR=FaxMaster
FROMADDR=fax
TIFFINFO=tiffinfo
NOTIFY_FAXMASTER=always

#
# Redirect errors to a tty, if possible, rather than
# dev-nulling them or allowing them to creep into
# the mail.
#
if $TTYCMD >/dev/null 2>&1; then
    ERRORSTO=`$TTYCMD`
else
    ERRORSTO=/dev/null
fi

#
# Permit various types of attachment types: ps, tif, pdf
# Note that non-ASCII filetypes require an encoder.
# pdf requires tiff2ps and tiff2pdf
#
FILETYPE=ps
SENDTO=

#
# There is no good portable way to find out the fully qualified
# domain name (FQDN) of the host or the TCP port for the hylafax
# service so we fudge here.  Folks may want to tailor this to
# their needs; e.g. add a domain or use localhost so the loopback
# interface is used.
#
HOSTNAME=`hostname`			# XXX no good way to find FQDN
PORT=4559				# XXX no good way to lookup service

FILE="$1"; shift;
DEVICE="$1"; shift;
COMMID="$1"; shift;
MSG="$1"; shift;
COUNT=1
while [ $# -ge 1 ]; do
    # The eval has $1 set yet, and this forces a variable-to-variable
    # assignment, allowing us to not need to do escaping
    eval CALLID$COUNT='$1'
    shift
    COUNT=`expr $COUNT + 1`
done
CIDNUMBER="$CALLID1"
CIDNAME="$CALLID2"
DESTINATION="$CALLID3"

FILENAME=`echo $FILE | $SED -e 's/\.tif//' -e 's/recvq\///'`
SENDER="`$INFO $FILE | $AWK -F: '/Sender/ { print $2 }' 2>$ERRORSTO | $SED 's/^.//'`"
SUBADDR="`$INFO $FILE | $AWK -F: '/SubAddr/ { print $2 }' 2>$ERRORSTO | $SED 's/^.//'`"
[B][COLOR="Red"]
if [ -n "$SENDTO" ]; then
	echo ""
    
  	echo "The facsimile was automatically dispatched to: $SENDTO."
    else
	$TIFFBIN/fax2ps $1 | lpr -Plp	 
     fi[/COLOR][/B]

#
# Apply customizations.  All customizable variables should
# be set to their non-customized defaults prior to this.
#
if [ -f etc/FaxDispatch ]; then
    . etc/FaxDispatch		# NB: FaxDispatch sets SENDTO
fi

#
# Produce mailable encoding for binary files.
#
encode()
{
    if [ -x "$MIMENCODE" ]; then
	$MIMENCODE < $1 2>$ERRORSTO
    elif [ -x "$UUENCODE" ]; then
	if [ "$ENCODING" = "base64" ]; then
	    $UUENCODE -m $1 $1 | grep -E -v "^begin|^====$" 2>$ERRORSTO
	else
	    $UUENCODE $1 $1 | grep -E -v "^begin|^====$" 2>$ERRORSTO
	fi
    else
	# Do not use "-x" for backward compatibility; even if it fails
	# this is last chance to encode data, so there's nothing to lose.
	$MIMENCODE < $1 2>$ERRORSTO
    fi
}

if [ -f $FILE ]; then
    #
    # Don't send FaxMaster duplicates, and FaxMaster may not even
    # want a message at all, depending on NOTIFY_FAXMASTER.
    #
    case $NOTIFY_FAXMASTER$MSG in
	never*)		NOTIFY_FAXMASTER=no;;
	errors)		NOTIFY_FAXMASTER=no;;
	*)		NOTIFY_FAXMASTER=yes;;
    esac
    if [ "$TOADDR" != "$SENDTO" ] && [ "$NOTIFY_FAXMASTER" != "no" ]; then
	(echo "To: $TOADDR"
	 echo "From: The HylaFAX Receive Agent <$FROMADDR>"
	 echo "Subject: Facsimile received from $SENDER";
	 echo ""
	 echo "$FILE (ftp://$HOSTNAME:$PORT/$FILE):"; $INFO -n $FILE
	echo "ReceivedOn: $DEVICE"
	if [ "$MSG" ]; then
	    echo ""
	    echo "The full document was not received because:"
	    echo ""
	    echo "    $MSG"
	    echo ""
	    echo "    ---- Transcript of session follows ----"
	    echo ""
	    if [ -f log/c$COMMID ]; then
		$SED -e '/-- data/d' \
		 -e '/start.*timer/d' -e '/stop.*timer/d' \
		 log/c$COMMID
	    elif [ -n "$COMMID" ]; then
		echo "    No transcript available (CommID c$COMMID)."
	    else
		echo "    No transcript available."
	    fi
	else
	    echo "    CommID: c$COMMID (ftp://$HOSTNAME:$PORT/log/c$COMMID)"
	fi
	if [ -n "$SENDTO" ]; then
	    echo ""
	    echo "The facsimile was automatically dispatched to: $SENDTO." 
	fi
	) 2>$ERRORSTO | $SENDMAIL -f$FROMADDR -oi $TOADDR
    fi
    if [ -n "$SENDTO" ]; then
	(MIMEBOUNDARY="NextPart$$"
	 echo "Mime-Version: 1.0"
	 echo "Content-Type: Multipart/Mixed; Boundary=\"$MIMEBOUNDARY\""
	 echo "Content-Transfer-Encoding: 7bit"
	 echo "To: $SENDTO"
	 echo "From: The HylaFAX Receive Agent <$FROMADDR>"
	 echo "Subject: Facsimile received from $SENDER";
	 echo ""
	 echo "--$MIMEBOUNDARY"
	 echo "Content-Type: text/plain; charset=us-ascii"
	 echo "Content-Transfer-Encoding: 7bit"
	 echo ""
	 $INFO -n $FILE
	 echo "ReceivedOn: $DEVICE"
	 if [ "$MSG" ]; then
	    echo ""
	    echo "The full document was not received because:"
	    echo ""
	    echo "    $MSG"
	    echo ""
	    echo "    ---- Transcript of session follows ----"
	    echo ""
	    if [ -f log/c$COMMID ]; then
		$SED -e '/-- data/d' \
		     -e '/start.*timer/d' -e '/stop.*timer/d' \
		     log/c$COMMID
	    elif [ -n "$COMMID" ]; then
		echo "    No transcript available (CommID c$COMMID)."
	    else
		echo "    No transcript available."
	    fi
	 else
	    echo "    CommID: c$COMMID"
	 fi
	 echo ""
	 echo "--$MIMEBOUNDARY"
	 if [ "$FILETYPE" = "tif" ]; then
	     echo "Content-Type: image/tiff; name=\"$FILENAME.tif\""
	     echo "Content-Description: FAX document"
	     echo "Content-Transfer-Encoding: $ENCODING"
	     echo "Content-Disposition: attachment; filename=\"$FILENAME.tif\""
	     echo ""
	     encode $FILE;
	 elif [ "$FILETYPE" = "pdf" ]; then
	     echo "Content-Type: application/pdf; name=\"$FILENAME.pdf\""
	     echo "Content-Description: FAX document"
	     echo "Content-Transfer-Encoding: $ENCODING"
	     echo "Content-Disposition: attachment; filename=\"$FILENAME.pdf\""
	     echo ""
	     $TIFF2PDF -o $FILE.pdf $FILE
	     encode $FILE.pdf
	     $RM -f $FILE.pdf 2>$ERRORSTO
	 else #  default as Postscript
	     echo "Content-Type: application/postscript; name=\"$FILENAME.ps\""
	     echo "Content-Description: FAX document"
	     echo "Content-Transfer-Encoding: 7bit"
	     echo "Content-Disposition: attachment; filename=\"$FILENAME.ps\""
	     echo ""
	     $FAX2PS $FILE 2>$ERRORSTO
	 fi
	 echo ""
	 echo "--$MIMEBOUNDARY--"
	) 2>$ERRORSTO | $SENDMAIL -f$FROMADDR -oi $SENDTO
    fi
else
    #
    # Generate notification mail for a failed attempt.
    #
    (echo "To: $TOADDR"
     echo "From: The HylaFAX Receive Agent <$FROMADDR>"
     echo "Subject: facsimile not received"
     echo ""
     echo "An attempt to receive facsimile on $DEVICE failed because:"
     echo ""
     echo "    $MSG"
     echo ""
     echo "    ---- Transcript of session follows ----"
     echo ""
     if [ -f log/c$COMMID ]; then
	$SED -e '/-- data/d' \
	     -e '/start.*timer/d' -e '/stop.*timer/d' \
	    log/c$COMMID
     elif [ -n "$COMMID" ]; then
	echo "    No transcript available (CommID c$COMMID)."
     else
	echo "    No transcript available."
     fi
    ) 2>$ERRORSTO | $SENDMAIL -f$FROMADDR -oi $TOADDR
fi

```

But nothing again...

---

