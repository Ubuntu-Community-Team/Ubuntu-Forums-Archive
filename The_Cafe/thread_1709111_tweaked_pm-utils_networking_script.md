---
title: "tweaked pm-utils networking script"
date: 2011-03-17
forum: The Cafe
---

### Post by nerdy_kid on 2011-03-17
Basically, I am trying to do the todo found in the top of /usr/lib/pm-utils/sleep.d/55NetworkManager:

```

# TODO: Make NetworkManager smarter about how to handle sleep/resume
#       If we are asleep for less time than it takes for TCP to reset a
#       connection, and we are assigned the same IP on resume, we should
#       not break established connections.  Apple can do this, and it is
#       rather nifty.

```

I am looking for some constructive criticism ;)
This is what I have come out with so far.  It can't handle multiple networks (yet...), so if someone moves the computer to another wireless connection it's going to mess things up.  Also, I am working around this bug: [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/620318](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/620318)  which is why I am using dhclient instead of using the dbus calls -- putting network-manager to sleep triggers the bug.

I don't know how long it takes for a tcp connection to reset, I have it set to 30 mins, but maybe that is too long.

I haven't scripted much, so beware of messy bashing ;)


```


#!/bin/sh
# If we are running NetworkManager, tell it we are going to sleep.
# TODO: Make NetworkManager smarter about how to handle sleep/resume
#       If we are asleep for less time than it takes for TCP to reset a
#       connection, and we are assigned the same IP on resume, we should
#       not break established connections.  Apple can do this, and it is
#       rather nifty.

TIME_FILE=/usr/lib/pm-utils/NetworkManagerSavedTime

. "${PM_FUNCTIONS}"

suspend_nm()
{
	# Tell NetworkManager to shut down networking
        echo "This is a customized script"
	echo "Saving $TIME_FILE"
	date +%m%d%y%H%M > $TIME_FILE
	if [ -f $TIME_FILE ]
	then echo "$TIME_FILE saved"
	else echo "$TIME_FILE NOT saved"
	fi

	    echo Done. || echo Failed.
}

resume_nm()
{
	# Wake up NetworkManager and make it do a new connection
	echo "This is a customized script"
	echo "Checking $TIME_FILE"

	if [ -f $TIME_FILE ]
        then SAVED_TIME=$(cat $TIME_FILE)
		if ! [ $(date +%m%d%y%H%M) -lt $(echo $SAVED_TIME+30 | bc) ]
		then echo "running dhclient"
			dhclient &
		else echo "reusing old connection"
		fi


	 else echo "ERROR, $TIME_FILE not found, refreshing IP address..."
		dhclient &
        fi 


	    echo Done. || echo Failed.
}

case "$1" in
	hibernate|suspend)
		suspend_nm
		;;
	thaw|resume)
		resume_nm
		;;
	*) exit $NA
		;;
esac

```

---

