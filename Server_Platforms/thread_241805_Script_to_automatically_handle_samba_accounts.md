---
title: "Script to automatically handle samba accounts"
date: 2006-08-22
forum: Server Platforms
---

### Post by Fr0d083 on 2006-08-22
I work at a college where we are deploying samba as a domain controller. I needed a script to handle automatic account creation. Since I couldn't find anything like this I wrote it myself. I thought some other people may find it usefull.

The script below will automatically create samba accounts from an input file. It will set a disk quota of 200MB for the user and set the user's full name in the samba database.

There are two scripts which work together to make this happen, the second is written using expect, it was necessary becuase smbpasswd only works interactively.

There are some rather large sleep statements in here, they could probably be brought way down.

```

#!/bin/bash


__GROUPS="domainusers"
HOME_DIRECTORY="/store/home/samba/profiles/$USERNAME"
QUOTA="200000"
PASSWORD="password"
ADD_USER=""
DELETE_USER=""
FULL_NAME=""
USER_LIST=""
USERNAME=""

print_usage()
{
    echo "smbuseradd"
    echo "purpose: to manage samba users"
    echo "usage:"
    echo "      -u     username"
    echo "      -a     add a new user to the system"
    echo "      -x     remove a user from the system entirely, use with caution"
    echo "      -n     the full name of the user enclosed in quotes"
    echo "      -g     list of domain groups for the user to belong to, comma seperated, defaults to domainusers"
    echo "      -d     home directory, defaults to /store/home/samba/profiles/USERNAME, THIS DESN'T WORK YET!!"
    echo "      -q     the size of the disk quota for the new user in kilobytes, defaults to 200000KB"
    echo "      -p     the new user's password, defaluts to \"password\""
    echo "      -f     the location of a file containing a list of users to add"
    echo "      -h     print this help"
    exit 1;
}

add_user()
{
    #add the user to the unix database
    useradd -d $HOME_DIRECTORY -G $__GROUPS -m -s /bin/false $USERNAME 1>/dev/null 2>/dev/null
    if [[ $? -eq 0 ]]
	then
	echo "User $USERNAME successfully added to unix database..."
	sleep 7
    else
	echo "Error: failed to add $USERNAME to the unix database"
	exit 1
    fi

    getent passwd 1>/dev/null

    #add the user to the samba database
    ./smb-add-passwd $USERNAME $PASSWORD
    if [[ $? = 0 ]]
	then
	echo "User $USERNAME successfully added to samba database..."
	sleep 5
    else
	echo "Error: failed to add $USERNAME to the samba database"
	userdel $USERNAME
	exit 1
    fi
    
    #set the user's disk quota
    quotatool -u "$USERNAME" -b /store -l $QUOTA:MB -q $QUOTA:MB 1>/dev/null 2>/dev/null
    if [[ $? -eq 0 ]]
	then
	echo "Set the disk qouta for user $USERNAME to $QUOTA..."
    else
	echo "Error: unable to set the disk quota for $USERNAME"
	exit 1
    fi

    #set the user's full name so russell can see it in netop
    pdbedit -u $USERNAME -f "${FULL_NAME}" 1>/dev/null
    if [[ $? = 0 ]]
	then
	echo "Set the full name of $USERNAME to $FULL_NAME..."
	else
	echo "Error: failed to set the full name of the user"
	exit 1
    fi
    
    #change the default password expiration date so the user has to change it at first logon
    pdbedit -u $USERNAME --pwd-must-change-time=`date +%s` 1>/dev/null
    if [[ $? = 0 ]]
	then
	echo "Forcing password change at first logon..."
	else
	echo "Error: could not make the password expired"
	exit 1
    fi

    echo "Success!!"
}

delete_user()
{
    smbpasswd -x $USERNAME 1>/dev/null 2>/dev/null
    if [[ $? = 0 ]]
	then
	echo "Deleted user $USERNAME from the samba database..."
	sleep 1
	else
	echo "Error: failed to delete $USERNAME from the samba database"
	exit 1
    fi
    
    userdel $USERNAME 1>/dev/null 2>/dev/null
    if [[ $? = 0 ]]
	then
	echo "Deleted user $USERNAME from the unix database..."
	sleep 1
	else
	echo "Error: failed to delete user $USERNAME from the unix database"
	exit 1
    fi
    
    rm -rf /store/home/samba/profiles/$USERNAME 1>/dev/null 2>/dev/null
    if [[ $? = 0 ]]
	then
	echo "Removed the home directory of $USERNAME..."
	else
	echo "Error: failed to delete the home directory of $USERNAME"
	exit 1
    fi

    echo "Success!!"

}

#go straight to usage if no options are specified
if [[ $# = 0 ]]
    then
    print_usage
fi

#Parse command line options
while getopts "u:g:G:d:q:p:f:n:axh" OPTS
  do
  case $OPTS in
      u) USERNAME=$OPTARG;;
      g)
	  if [[ $OPTARG -ne "" ]]
	      then
	      __GROUPS="domainusers"
	  else
	      __GROUPS=$OPTARG
	  fi
	  ;;
      d)
	  #if [[ $OPTARG -ne "" ]]
	  #    then
	  #    HOME_DIRECTORY="/store/home/samba/profiles/$USERNAME"
	  #else
	  #    HOME_DIRECTORY=$OPTARG
	  #fi
	  echo "Error: changing a users home directory does not work yet, sorry"; echo ""; print_usage
	  ;;
      q)
	  if [[ $OPTARG -eq 0 ]]
	      then
	      QUOTA="100"
	  else
	      QUOTA=$OPTARG
	  fi
	  ;;
      p)
	  if [[ $OPTARG -ne "" ]]
	      then
	      PASSWORD="password"
	      else
	      PASSWORD=$OPTARG
	  fi
	  ;;
      f) USER_LIST=$OPTARG;;
      a) ADD_USER="true";;
      x) DELETE_USER="true";;
      h) print_usage;;
      n) FULL_NAME=$OPTARG;;
      *) print_usage;;
  esac
done
shift $(($OPTIND - 1))

#this is ugly right now, figure out how to fix it
#maybe it doesn't matter, samba users should all have home directories here
HOME_DIRECTORY="/store/home/samba/profiles/$USERNAME"

#check to see if the user wants to read from a file
#this file will have to be structured
if [[ -n "$USER_LIST" ]]
    then

    #pre-parse the userlist before any real work in case there are mistakes
    LINE=0
    while read -r USERINFO
      do
      USERNAME=`echo $USERINFO | awk -F : '{ print $1 }'`
      if [[ $USERNAME == "" ]]
	  then
	  echo "Error: cannot parse userlist, no username found on line $LINE"
	  echo "       be sure that the file ends with only one blank line"
	  exit 1
      fi
      let "LINE = $LINE + 1"
    done < $USER_LIST

    while read -r USERINFO
      do
      USERNAME=`echo $USERINFO | awk -F : '{ print $1 }'`
      FULL_NAME=`echo $USERINFO | awk -F : '{ print $2 }'`
      HOME_DIRECTORY="/store/home/samba/profiles/$USERNAME"
      __GROUPS=`echo $USERINFO | awk -F : '{ print $3 }'`
      if [[ $__GROUPS == "" ]]
	  then
	  __GROUPS="domainusers"
      fi
      QUOTA=`echo $USERINFO | awk -F : '{ print $4 }'`
      if [[ $QUOTA == "" ]]
	  then
	  QUOTA="100"
      fi
      PASSWORD=`echo $USERINFO | awk -F : '{ print $5 }'`
      if [[ $PASSWORD == "" ]]
	  then
	  PASSWORD="password"
      fi
      if [[ $ADD_USER == "" ]]
	  then
	  if [[ $DELETE_USER == "" ]]
	      then
	      echo "Error: You must specify whether to add or delete users"
	      exit 1
	  fi
      fi
      if [[ $ADD_USER == "true" ]]
	  then
	  add_user
      else
	  delete_user
      fi
    done < $USER_LIST
    exit 0
fi

#at this point we should have a username to add or delete
#if we don't then blow up
if [[ $USERNAME = "" ]]
    then
    echo "Error: you must specify a username or provide a file with a list of usernames"
    echo ""
    print_usage
fi

#also check to see that the user actually wants to do something, they either have to add or delete
if [[ $ADD_USER == "" ]]
    then
    if [[ $DELETE_USER == "" ]]
	then
	echo "Error: you must specifiy either -a or -x or provide a file with a list of usernames"
	echo ""
	print_usage
    fi
fi

#Make sure that -a and -x are not specified at the same time
if [[ $ADD_USER == "true" ]]
    then
    if [[ $DELETE_USER == "true" ]]
	then
	echo "Error: you cannot specify -a and -x at the same time"
	echo ""
	print_usage
    fi
fi

#add a new user or delete a current one, based on user selection
if [[ $ADD_USER == "true" ]]
    then
    add_user
fi

if [[ $DELETE_USER == "true" ]]
    then
    delete_user
fi

exit 0

```

```

#!/usr/bin/expect

set password [lindex $argv 1]
spawn /usr/bin/smbpasswd -a -D 1 [lindex $argv 0]
expect "password:"
send "$password\r"
sleep 3
expect "password:"
send "$password\r"
expect eof

```

The format of the input file is:
```

username:full name:group1,group2,group3,:quota size:password

```

Example of an input file:
```

jsmith:John Smith:domainusers,accounting:1000000:secretpassword

```

It is possible to use only the first field in the input file, the script will fill in the rest with defaults. So you can have something like this:
```

jsmith
bdavis
ejones
gbush
crice
ajackson

```

I know this script assumes a lot about your environment, but I thought it may be usefull if someone was looking for something to modify. I would be glad to hear any suggestions/comments.

---

### Post by HTC on 2007-08-17
I am assisting a school setup a lab on a different Linux Flavour (RedHat enterprise) and would be interested in the script to add all the passwords to the various user accounts rather than one by one. 

We use an awk script to add all the users however this script on the post looks somewhat neater. 

Do you have any suggestions regarding changing/ ammending the samba passwords and a different flavour of linux?

Thanks in advance

---

