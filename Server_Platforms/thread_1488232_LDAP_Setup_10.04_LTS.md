---
title: "LDAP Setup 10.04 LTS"
date: 2010-05-19
forum: Server Platforms
---

### Post by th3 mant1s on 2010-05-19
Hi Everyone,

I've been working though this[http://www.opinsys.fi/setting-up-openldap-on-ubuntu-10-04-alpha2]("http://www.opinsys.fi/setting-up-openldap-on-ubuntu-10-04-alpha2") tutorial trying to get openldap working. 

When I get to the point where i'm setting up the client. More specifically when I do ldapaddgroup testgroup I am sent this error 

"You must have OpenLDAP client commands installed before running these scripts"

I have installed the ldapscripts package along with all the required ones. Has anyone been through this, I imagine it's some little nuance that I am missing. 

Thanks!

Mant1s

---

### Post by bluelightav on 2010-05-28
Hi mantis,

We changed the existing runtime.debian to also include the variable declarations. After this we can use the ldapscripts again.

good luck

/usr/share/ldapscripts/runtime.debian
```
### This file predefine some ldapscripts variables for Debian boxes.
#
#  Copyright (c) 2005 Gana&#65533;l LAPLANCHE - Linagora
#  Copyright (c) 2005-2007 Pierre Habouzit
#  Copyright (c) 2009 Alexander GQ Gerasiov
#
#  This program is free software; you can redistribute it and/or
#  modify it under the terms of the GNU General Public License
#  as published by the Free Software Foundation; either version 2
#  of the License, or (at your option) any later version.
#
#  This program is distributed in the hope that it will be useful,
#  but WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#  GNU General Public License for more details.
#
#  You should have received a copy of the GNU General Public License
#  along with this program; if not, write to the Free Software
#  Foundation, Inc., 59 Temple Place - Suite 330, Boston, MA 02111-1307,
#  USA.

##### Beginning of ldapscripts configuration #####

getfield() {
    local field="$1"
    local nssconffile='/etc/libnss-ldap.conf'
    if [ -f "$nssconffile" ];then
	local value=$(awk "/^\s*$field/ {print \$2}" /etc/libnss-ldap.conf)
    else
	local value="$2"
    fi
    echo ${value:-$2}
}

getsuffix() {
    field="$1"
    value="$(getfield "$1" | sed -e "s/,.*$//")"
    echo ${value:-$2}
}

# LDAP Configuration
SERVER=$(getfield uri "$(getfield host '')")
BINDDN=$(getfield rootbinddn '')
if [ -f /etc/libnss-ldap.secret ];then
	BINDPWDFILE=/etc/libnss-ldap.secret
elif [ -f /etc/ldap.secret ];then
	BINDPWDFILE=/etc/ldap.secret
fi

SUFFIX=`getfield base`
GSUFFIX=`getsuffix nss_base_group   'ou=Group'`
USUFFIX=`getsuffix nss_base_passwd  'ou=People'`
MSUFFIX=`getsuffix nss_base_hosts   'ou=Hosts'`

# User properties
[ -f /etc/adduser.conf ] && . /etc/adduser.conf
USHELL=${DSHELL:-"/bin/bash"}
UHOMES=${DHOME:-"/home"}"/%u"
HOMESKEL=${SKEL:-"/etc/skel"}
HOMEPERMS=${DIR_MODE:-"0755"}


# Where to log
LOGFILE="/var/log/ldapscripts.log"

# Various binaries used within scripts
LDAPSEARCHBIN=`which ldapsearch`
LDAPADDBIN=`which ldapadd`
LDAPDELETEBIN=`which ldapdelete`
LDAPMODIFYBIN=`which ldapmodify`
LDAPMODRDNBIN=`which ldapmodrdn`
LDAPPASSWDBIN=`which ldappasswd`

# Getent command to use - choose the ones used on your system. Leave blank or comment for auto-guess.
# GNU/Linux
GETENTPWCMD="getent passwd"
GETENTGRCMD="getent group"


TMPDIR="/tmp"
##### End of configuration #####
```

---

### Post by jetole on 2010-09-23
> **bluelightav said:**
> We changed the existing runtime.debian to also include the variable declarations. After this we can use the ldapscripts again.

I ran into the same problem following the Ubuntu LDAP guide in server configuration for 10.04 ( [https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html](https://help.ubuntu.com/10.04/serverguide/C/openldap-server.html) ).

bluelightav, I don't actually understand the answer you just gave. Can you explain that a little more please?

---

### Post by jetole on 2010-09-27
After looking at this message again, I understand what you meant. You were saying that we should replace /usr/share/ldapscripts/runtime.debian with the one you posted. This fixed the problem for me.

---

### Post by Vazhnov Alexey on 2013-02-10
Bugreport: [https://bugs.launchpad.net/ubuntu/+source/ldapscripts/+bug/803441](https://bugs.launchpad.net/ubuntu/+source/ldapscripts/+bug/803441)

---

