---
title: "Listing registered nodes from a remote machine"
date: 2011-04-13
forum: Ubuntu Cloud and Juju
---

### Post by rabinnh on 2011-04-13
Just thought that I would post this.  

Currently, Eucalyptus only allows you to list registered nodes locally on the cloud controller with:

euca_conf --list-nodes

Looking at the bash script, I realized that if you replace the URL, access key, and secret key, it could work from anywhere, since it is constructing a URL and using wget.  I hacked it up and tested it out.  This script does the job using (the constant "eucalyptus" could be hard coded, but this may work on other EC2 platforms, so why cripple it?).  On my systems, it only seems to work with the keys from the "admin" account.

euca_list_nodes.sh *url access_key secret_key* eucalyptus

And here is the script:
```

#!/bin/bash
# Copyright (c) 2009  Eucalyptus Systems, Inc.	
#
# Modified 4/13/2011 by Richard Bross, SilverSpore LLC
#   List registered nodes on a remote controller: euca-list-nodes url accesskey secretkey version
#   (example; for Eucalyptus, "version" is "eucalyptus")
#
#This program is free software: you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by 
#the Free Software Foundation, only version 3 of the License.  
# 
#This file is distributed in the hope that it will be useful, but WITHOUT
#ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or
#FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License
#for more details.  
#
#You should have received a copy of the GNU General Public License along
#with this program.  If not, see <http://www.gnu.org/licenses/>.
# 

check_ws() {
	local URL="$1"
	local ret=""
	local soap_error=""

	if [ -z "$URL" ]; then
		echo "check_ws: need a URL!"
		return 1
	fi
	
	if [ -n "${FAKEREG}" ]; then
		ret=""
	elif [ "$2" != "" ]; then
		if [ "$VERBOSE" = "Y" ]; then
			echo   "$WGET -q -T 10 -t 1 -O - \"$URL\"" "|sed 's/<euca:registered>\\(.*\\)<\\/euca:registered>/\\n\\1\\n/g;s/<euca:name>/\\n>/g;s/<\\/*euca:item>//g;s/<\\/*euca:[^>]*>/ /g'|awk -F\">\" '/>/{print \"   \"$2}')"
		fi
		E=$($WGET -q -T 10 -t 1 -O - "$URL"|\
			sed 's/<euca:registered>\(.*\)<\/euca:registered>/\n\1\n/g;s/<euca:name>/\n>/g;s/<\/*euca:item>//g;s/<\/*euca:[^>]*>/ /g'|\
			awk -F">" '/>/{print "   "$2}')
		eval "$2=\"${E}\""
	else
		if [ "$VERBOSE" = "Y" ]; then
			echo "$WGET -q -T 10 -t 1 -O - \"$URL\" |grep faultstring | sed 's:.*<faultstring>\(.*\)</faultstring>.*:\1:'"
		fi
		soap_error="`$WGET -q -T 10 -t 1 -O - \"$URL\"`"
		ret="$?"
		soap_error="`echo $soap_error |grep faultstring | sed 's:.*<faultstring>\(.*\)</faultstring>.*:\1:'`"
		if test -n "$soap_error" ; then
			echo $soap_error
			ret="1"
		fi
	fi
	return $ret
}


createCloudURL () {
    ARGS="AWSAccessKeyId=$AKEY"
    KEY=$1
    shift
    VAL=$1
    shift
    while ( test -n "$KEY" -a -n "$VAL")
    do
	ARGS="${ARGS}&${KEY}=${VAL}"
	KEY=$1
	shift
	VAL=$1
	shift
    done
    if [ -z "$SKEY" ]; then
	echo "ERROR: SKEY parameter is not set."
	export URL=""
	return 1
    fi
    ARGS="${ARGS}&SignatureMethod=HmacSHA256&SignatureVersion=2&Timestamp=$(date -u '+%Y-%m-%dT%H%%3A%M%%3A%S.000Z')&Version=$VERSION"
    SIGNATURE=$(echo -en "GET\n$IP\n/services/Configuration\n${ARGS}" | openssl dgst -sha256 -hmac ${SKEY} -binary | openssl base64)
    export URL="http://$IP:8773/services/Configuration?${ARGS}&Signature=${SIGNATURE}"

	if [ "$VERBOSE" = "Y" ]; then
		echo $URL
	fi
    return 0
}

# Build the URL and do the call
IP="$1"
AKEY="$2"
SKEY="$3"
VERSION="$4"

if ! createCloudURL "Action" "DescribeNodes" ; then
    exit 1
fi
if ! check_ws "$URL" LIST_RES ; then
    exit 1
fi
if [ -n "$LIST_RES" ]; then
    echo "registered nodes:"
fi
    echo "$LIST_RES"


```

---

### Post by kim0 on 2011-04-18
Hi, Thanks for the patch! Looks like you should open a bug on [https://launchpad.net/eucalyptus](https://launchpad.net/eucalyptus)
Attach your patch for the bug, and hopefully it will be merged :)

---

### Post by rabinnh on 2011-04-18
You know, it's kind of interesting.  I was thinking about why Amazon doesn't include a command to list the nodes attached to a controller, and then I realized that from their point of view, what's on the back end should be relatively invisible to their customers.  

So I think this is only really valuable for UEC users ;-)

---

