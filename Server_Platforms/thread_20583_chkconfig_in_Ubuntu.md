---
title: "chkconfig in Ubuntu?"
date: 2005-03-17
forum: Server Platforms
---

### Post by ejms07 on 2005-03-17
How can I do a chkconfig on Ubuntu.  That's I'm trying to do...

#chkconfig dhcp on

and

#chkconfig squid on

under /etc/init.d


Thanks guys!

---

### Post by deuce868 on 2005-03-18
check out update-rc.d 

man update-rc.d

---

### Post by ejms07 on 2005-03-18
I tried update-rc.d but the services (dhcp & squid) are not starting automatically.  When I ran the command it says that "the links already exist"

---

### Post by alastair on 2005-03-18
I think chkconfig is nice as well (actually, coming from an SGI Irix background as well as Redhat). But I doubt you'll see it on Ubuntu soon.

update-rc.d is a bit more sensitive - but does work.

To see what links are around for "squid" say, try a :

find /etc/rc* -name '*squid*'

Also check the logs for startup problems (and the /etc/init.d file).

---

### Post by jbharrison on 2005-12-20
Here ya go:
```

#!/bin/bash
#----------------------------------------------------------------
# Title: rc-config
# Author: Joseph Harrison
# Date Created: 12/16/2005
# Date Modified: 12/16/2005
# Purpose: Configure services and run-levels
# Dependencies: grep, sed, update-rc.d
#----------------------------------------------------------------

USAGE="Usage: rc-config [OPTION] [SERVICE ... STATE]\n\
Information about services and run-levels, configure services and run-levels\n\
Sorts entries alphabetically\n\
\n\
Mandatory arguments to long options are mandatory for short options too.\n\
  -h,\t\t\t Show help\n\
  -l,\t\t\t List all services and run-levels\n\
  -ls <service>,\t\t List a specific service and run-levels\n\
  -s <service> <off|on>,\t Configure service\n\
  \t\t\t Ex: rc-config -s ssh off\n\
  -t,\t\t\t Terse output\n\n"
LISTSVC=0
SETSVC=0
TERSE=0

checkroot(){
  if [ $EUID -ne 0 ]
  then
    echo "you must be root to use this feature"
    exit 1
  fi
}

checkopts()
{
  while getopts "lsth" flag
  do
    case $flag in
      l ) LISTSVC=1;;
      s ) SETSVC=1;;
      t ) TERSE=1;;
      h ) echo -en $USAGE;
          exit 1;;
      * ) echo -en $USAGE
          exit 1;;
    esac
  done
  if [ -z "$1" ]
  then
    echo -en $USAGE
  fi
}

showrc(){
  if [ $TERSE -eq 0 ]
  then
    echo -en "SERVICE\t\t\tRUN-LEVELS\n"
  fi

  if [ $SETSVC -eq 0 ]
  then
    slist=`find /etc/init.d/ -perm -100 \
      | sed "s/\/etc\/init.d\///"`
  elif [ $SETSVC -eq 1 ]
  then
    svc=$2
    if [ -f "/etc/init.d/$svc" ]
    then
      slist="$svc"
    else
      echo "$svc: does not exist"
      exit 1
    fi
  fi

  for msvc in $slist
  do
    sln=18
    tsvc=$msvc
    while [ ${#tsvc} -lt $sln ]
    do
      tsvc="$tsvc "
    done
    echo -en "${tsvc:0:$sln}\t"
    for level in 0 1 2 3 4 5 6
    do
      svcs=`ls -1 /etc/rc${level}.d/S* \
        | sed "s/\/etc\/rc${level}.d\/S[0-9]*//"`
      state=0
      for svc in $svcs
      do
        if [ "$svc" = "$msvc" ]
        then
          state=1
          continue
        fi
      done
      if [ $state -eq 1 ]
      then
        echo -en "$level:on\t"
      else
        echo -en "$level:off\t"
      fi
    done
    echo
  done
}

setsvc(){
  svc=$2
  state=$3

  if [ -z "$svc" ] || [ -z "$state" ]
  then
    echo -en $USAGE
    exit 1
  fi

  if [ ! -f "/etc/init.d/$svc" ]
  then
    echo "$svc: does not exist"
    exit 1
  fi

  if [ $state = "on" ]
  then
    update-rc.d $svc defaults
  elif [ $state = "off" ]
  then
    echo "disabling service: $svc"
    /etc/init.d/$svc stop > /dev/null
    for link in `find /etc/rc* -type l -name "[S,K][0-9][0-9]$svc"`
    do
      unlink $link
    done
  else
    echo -en $USAGE
  fi
}

main(){
  checkopts "$@"
  if [ $LISTSVC -eq 1 ]
  then
    showrc "$@"
  elif [ $SETSVC -eq 1 ]
  then
    checkroot
    setsvc "$@"
  fi
}

main "$@"

```

---

### Post by xtacocorex on 2005-12-22
Thanks for the bash script. Will try it when I get home. 

This is probably a better solution than attempting to get the RedHat chkconfig source and try to compile it against Kubuntu.

---

### Post by SRu on 2006-06-26
There is an alternative for editing runlevels that can be used just like chkconfig:
[http://sysv-rc-conf.sourceforge.net/](http://sysv-rc-conf.sourceforge.net/)

*To install:*
[B]sudo apt-get install sysv-rc-conf
sysv-rc-conf[/B]

Excerpt from the manual:

DESCRIPTION

sysv-rc-conf gives an easy to use interface for managing /etc/rc{runlevel}.d/ symlinks. The interface comes in two different flavors, one that simply allows turning services on or off and another that allows for more fine tuned management of the symlinks. It's a replacement for programs like ntsysv(8) or rcconf(8).

sysv-rc-conf can also be used at the command line when the desired changes to the symlinks are already known. The syntax is borrowed from chkconfig(8).

---

### Post by tnilsson on 2006-08-04
Thank you very much!
sysv-rc-conf is almost like chkconfig! :D

---

### Post by leftcase on 2006-12-12
If you actually want the chkconfig command in ubuntu, do the following:

```

$ apt-get install libnewt0.51
$ ln -s /usr/lib/libnewt.so.0.51 /usr/lib/libnewt.so.0.50
$ wget http://www.tuxx-home.at/projects/chkconfig-for-debian/chkconfig_1.2.24d-1_i386.deb
$ dpkg --force-all -i chkconfig_1.2.24d-1_i386.deb

```

I found this whilst looking for a solution myself - It's a debian solution which works...

---

### Post by technodigifreak on 2006-12-12
> **SRu said:**
> There is an alternative for editing runlevels that can be used just like chkconfig:
[http://sysv-rc-conf.sourceforge.net/](http://sysv-rc-conf.sourceforge.net/)
.... The syntax is borrowed from chkconfig(8).

> **leftcase said:**
> If you actually want the chkconfig command in ubuntu, do the following:

```

$ apt-get install libnewt0.51
$ ln -s /usr/lib/libnewt.so.0.51 /usr/lib/libnewt.so.0.50
$ wget http://www.tuxx-home.at/projects/chkconfig-for-debian/chkconfig_1.2.24d-1_i386.deb
$ dpkg --force-all -i chkconfig_1.2.24d-1_i386.deb

```

I found this whilst looking for a solution myself - It's a debian solution which works...

I'll check both of them out.  chkconfig was the only command that I was still missing from my days of using primarily redhat.  If this works the way I remember it you'll both have made my week!

btw, apt is the reason I switched to Debian.  apt > yum :D

---

### Post by leftcase on 2006-12-12
sysv-rc-conf does rock. Personally I find it better than chkconfig, but it's nice to have both options ;)

---

### Post by technodigifreak on 2006-12-13
> **leftcase said:**
> sysv-rc-conf does rock. Personally I find it better than chkconfig, but it's nice to have both options ;)

I've only had it on a testing machine so far, but everything looks very promising!  Thanks again for the suggestion.  I'll let you know when I'm ready to move it into production.

---

### Post by leftcase on 2006-12-13
> **technodigifreak said:**
> I've only had it on a testing machine so far, but everything looks very promising!  Thanks again for the suggestion.  I'll let you know when I'm ready to move it into production.

No probs mate. Have fun. :mrgreen:

---

### Post by motin on 2007-02-25
Does any of these work as a drop-in replacement for chkconfig? I have summarized the issue here: [http://ubuntuforums.org/showthread.php?p=2212100#post2212100](http://ubuntuforums.org/showthread.php?p=2212100#post2212100)

---

### Post by gdecoster on 2007-11-23
Found a chkconfig rpm that installs clean.

1. Download chkconfig-1.2.24h-7.i386.rpm from [http://rpmfind.net//linux/RPM/PLD/dists/ac/ready/i386/chkconfig-1.2.24h-7.i386.html](http://rpmfind.net//linux/RPM/PLD/dists/ac/ready/i386/chkconfig-1.2.24h-7.i386.html)

2. Convert rpm to deb with: sudo alien chkconfig-1.2.24h-7.i386.rpm

3. Double-click on the deb file. This will invoke the package installer.

---

