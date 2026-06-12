---
title: "Non-interactive LDAP configuration?"
date: 2014-12-17
forum: Server Platforms
---

### Post by leslie4 on 2014-12-17
I've got a setup shell script I run on new CentOS systems to customize them for our environment.  One of the commands configures LDAP to talk to our server:
```
authconfig --enableshadow --passalgo=sha512 --enableldap --enableldapauth --enableldaptls --ldapbasedn=dc=aaa,dc=bbb,dc=ccc,dc=ddd --ldapserver=eee.fff.ggg.hhh --ldaploadcacert=http://iii.jjj.kkk.lll/ldap/slapd.pem --enablelocauthorize --enablesssdauth --enablecachecreds --updateall
```
(The names have been changed to protect the innocent.)  I now need to create a similar script for Ubuntu 14 systems.  However, Ubuntu doesn't have the authconfig command.  Does anyone know what command or commands I can use to perform the same LDAP configuration?  The catch, of course, is that the commands can not prompt the user for any input, as the configuration script has to be able to run unattended and/or remotely.  This seems to rule out dpkg-reconfigure, auth-client-config and all other commands I've come across in Googling this issue.

Any suggestions would be greatly appreciated.

---

### Post by schragge on 2014-12-17
I would be interested in knowing this, too. A week ago a colleage of mine was trying to get LDAP authentication right on a fresh Ubuntu install. I suggested that she installs CentOS instead which she did. The only Ubuntu way we could find was to do it by editing config files like described in [uhelp]community/LDAPClientAuthentication[/uhelp], also [here]("http://naidutrk.blogspot.de/2012/03/setting-up-ldap-client-authentication.html") and [here]("http://wiki.ubuntuusers.de/Archiv/LDAP_Client_Authentifizierung") (in German).

---

### Post by leslie4 on 2015-01-05
Bump.  Thanks in advance to all who respond.

I'm beginning to get the impression that Ubuntu is simply a less capable distro than CentOS, or at least is oriented towards a less technically proficient user base.  However, I'm willing to be proved wrong. :)

---

### Post by schragge on 2015-01-06
Well TBH, there *are* some automation tools on Ubuntu (see [pam-auth-update]("http://manpages.ubuntu.com/manpages/trusty/en/man8/pam-auth-update.8.html") and [auth-client-config]("http://manpages.ubuntu.com/manpages/trusty/en/man8/auth-client-config.8.html")), but they are rather limited in scope. Besides, most authentication packages shipped with Ubuntu don't use *auth-client-config* at all. If you want it to be used with them, you will need to create auth-client-config profiles for them yourself.

---

### Post by leslie4 on 2015-01-13
After some experimentation, this is the code I am currently using:

```
# Configure LDAP
echo -e "\nConfiguring for LDAP authentication..."
echo ""
echo "Values you will need to enter:"
echo ""
echo "        Server: ldap://aaa.bbb.ccc.ddd"
echo "        Base DN: dc=eee,dc=fff,dc=ggg,dc=hhh"
echo "        Version: 2"
echo "        Use local database: No"
echo "        Use password: No"
echo ""
echo -n "Press Control-C to abort, or press Enter to continue: "
read _FOO
echo "apt-get -y install libnss-ldap ldap-utils libpam-ldap autofs-ldap nslcd"
apt-get -y install libnss-ldap ldap-utils libpam-ldap autofs-ldap nslcd
echo ""
echo ""
echo "auth-client-config -t nss -p lac_ldap"
auth-client-config -t nss -p lac_ldap
echo ""
echo ""
echo "pam-auth-update"
pam-auth-update
```

When the install prompts for values, I enter them by hand.  It's obviously not something that can be run non-interactively, but I don't see any other way to do what I need.  It's disappointing, really.

---

### Post by schragge on 2015-01-13
Hopefully, [this answer]("http://unix.stackexchange.com/a/106553") may be of some help.

---

### Post by leslie4 on 2015-01-14
> **schragge said:**
> Hopefully, [this answer]("http://unix.stackexchange.com/a/106553") may be of some help.That looks promising.  I had to do an apt-get install of debconf-utils to get debconf-set-selections, but I will definitely experiment with this.  Thanks!

---

