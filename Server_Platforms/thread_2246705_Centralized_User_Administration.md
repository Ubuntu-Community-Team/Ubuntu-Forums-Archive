---
title: "Centralized User Administration"
date: 2014-10-02
forum: Server Platforms
---

### Post by matt_fussell2 on 2014-10-02
I've been searching for a while for a centralized administration server to manage users on the network. Most of the information I've come across when searching for a user friendly all-linux solution leads down one of three paths: Windows integration, complicated solutions from RHEL, or some version of the question "Why are you even trying? (Is your network big enough? Do you really *need* that? Why not just have an open network? [My personal favorite] Why not just use Windows/AD?)"

So here's the question:
Can I use a Ubuntu 14.04 server to centrally manage Ubuntu 14.04 desktop clients, and what is the easiest mechanism to do this (LDAP, SAMBA, Kerberos, not NIS - too insecure)?

---

### Post by TheFu on 2014-10-02
For an Ubuntu-only solution, LDAP with Kerberos is probably the best answer. 
NIS is very insecure and shouldn't be used anywhere.

I don't know of any "easy" or GUI method to handle openLDAP administration. In the end, I decided to use Zimbra's LDAP server as the central authentication, but only because we needed the enterprise calendaring aspect of Zimbra. 

If I were trying to do this in a 50+ user corporate environment, I'd strongly consider running a CentOS auth server inside a VM and use FreeIPA. There are clients for all platforms, but the server has too many redhat specific dependencies to be easily ported to debian.

Any network is big enough for this if you have 1 userid and 2 servers.

Oh - and anyone thinking that using AD/Windows for this is just crazy. AD **with Kerberos** is not secure. Someone in my defcon group was approached by government agents after proposing a talk about defeating this configuration. That was over 2 yrs ago. Don't think any patches have solved the root issue there.

Samba? Huh?  That's just for file/print stuff and the back-end authentication can be changed.

I suppose knowing what you mean by user administration would be helpful. We use it for 
* normal logins (including ssh access w/ keys)
* web application authentication - about 10 webapps use LDAP

We do NOT use LDAP for file/print, as we don't use CIFS in the company, just NFS.

---

### Post by matt_symes on 2014-10-02
Hi

> **matt_fussell2 said:**
>  Windows integration, complicated solutions from RHEL, or some version of the question "Why are you even trying? (Is your network big enough? Do you really *need* that? Why not just have an open network? [My personal favorite] Why not just use Windows/AD?)"

That would seriously irritate me as well. It's as useless as someone asking a question on a forum, later posting 'I've found the answer' and not posting their solution. THat happened to me the other day when i was trying to find the solution to a problem i was having :|

> 
So here's the question:
Can I use a Ubuntu 14.04 server to centrally manage Ubuntu 14.04 desktop clients, and what is the easiest mechanism to do this (LDAP, SAMBA, Kerberos, not NIS - too insecure)?

Yes.

> **TheFu said:**
> For an Ubuntu-only solution, LDAP with Kerberos is probably the best answer. 
NIS is very insecure and shouldn't be used anywhere.

This is the best advice you will hear all day, connected with your question.

> Any network is big enough for this if you have 1 userid and 2 servers.

Exactly. I don't use LDAP (although i have thought about it).

But I do run Kerberos with NFSv4 at home with authentication security only. 

My PCs (media server, laptop, and other PCs ) and my main backup computer all shares files using NFSv4 with authentication. Files are exported from my media server as ro SAMBA shares and the only way any PC can write to the media shares (or any of the other NFS shares apart from the PXE boot shares) is by being an authenticated Kerberos principle.

Completely overkill, i know, but i wanted the challenge of setting it up.

> Oh - and anyone thinking that using AD/Windows for this is just crazy. AD **with Kerberos** is not secure. Someone in my defcon group was approached by government agents after proposing a talk about defeating this configuration. That was over 2 yrs ago. Don't think any patches have solved the root issue there.

Useful information. I was not aware of this; thanks.

> Samba? Huh?  That's just for file/print stuff and the back-end authentication can be changed.

I suppose knowing what you mean by user administration would be helpful. We use it for 
* normal logins (including ssh access w/ keys)
* web application authentication - about 10 webapps use LDAP

We do NOT use LDAP for file/print, as we don't use CIFS in the company, just NFS.

I believe that SAMBA can use Kerberos but i have not investigated it as it was never part of the setup i wanted to create.

Anyway, I thought i would post some of the very useful an pretty accurate online tutorials i came across when setting up my system. They are for Ubuntu so if you decide to go down the Redhat, CentOS (etc) route they may not be so useful.

[www.danbishop.org]("http://www.danbishop.org") (Check out  the small business server tutorials)
[https://help.ubuntu.com/community/Kerberos](https://help.ubuntu.com/community/Kerberos)
[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

Kerberos can be tricky to setup only because there are a number of poor tutorials on the net however once you set it up it's pretty simple. The way you set it up for Redhat and its ilk is different from Ubuntu and Debian.

Document what you do as you go along. You'll thank yourself later.

Keep every machine time synced :)

At the first sign of trouble enable all the logging you can.

That's my input into this thread anyway.

Kind regards

---

### Post by matt_fussell2 on 2014-10-03
I apologize for the vaguery in the post; I should have stepped away before typing it out as it came after a long and ultimately unsuccessful day of trying to variations on the services I initally mentioned to work - the frustration was apparent, now that I read it.

I'll continue pursuing the FreeIPA solution, but if there is a forum thread or a howto regarding how to connect Ubuntu to that solution that either of you are aware of, I would be all ... well, eyes, as it were. If I can get a replicable, cohesive process together for prepping the server and client, I would be more than happy to post the scripts and the write-up on the forums so that other people won't have to go through the headache of getting it to work.

> I suppose knowing what you mean by user administration would be helpful.

Put as simply as I can, I've basically been tasked with putting together the linux equivalent of Microsoft Server, both in regards of setup and post administration as most of the solutions I'm putting together are going to get handed off to people who most likely don't have the linux savvy to do much other than 'GUI around', so to speak.

> If I were trying to do this in a 50+ user corporate environment, I'd  strongly consider running a CentOS auth server inside a VM and use  FreeIPA. There are clients for all platforms, but the server has too  many redhat specific dependencies to be easily ported to debian.

Again, if you have any resources regarding how to plug Ubuntu in to the FreeIPA server, I would be ever so grateful if you passed those along. Again, if I can boil it down to a script, I will be more than happy to post it back to the forums to simpify it for other people.

Thanks for the response, guys.

---

### Post by TheFu on 2014-10-03
An ansible playbook would be appreciated.

I don't think you will be able to setup anything that is point-n-click. Sorry.  Actually, if you do, I'd be worried that the people who take over it will p-n-c their way into being hacked.  OTOH - if support calls are time + materials, great!

Have you looked at those all-in-one distros like Zentyal?  I wouldn't put this on the internet - people call me paranoid - but it may be just what your client wants?  If support calls are time+materials ...

---

### Post by matt_fussell2 on 2014-10-06
The GUIs that we have implemented so far are simple and subsequently restrictive - we've been tying bash scripts and commands to Python buttons with the scripts making all the decisions for the end users. The only real vulnerability is human behaviour - and there's no patch for that.

I have attempted to deploy Zentyal, but it finds a way to disappoint me and not work in just about every instance. I'm currently working with clearOS, but the support community has been (thus far) lacking. That said, the clearOS server wouldn't be a web-facing server, but it is just sufficient enough for some of the small business tasks for which we're developing solutions.

---

### Post by lingpanda on 2014-10-09
> **matt_fussell2 said:**
> I've been searching for a while for a centralized administration server to manage users on the network. Most of the information I've come across when searching for a user friendly all-linux solution leads down one of three paths: Windows integration, complicated solutions from RHEL, or some version of the question "Why are you even trying? (Is your network big enough? Do you really *need* that? Why not just have an open network? [My personal favorite] Why not just use Windows/AD?)"

So here's the question:
Can I use a Ubuntu 14.04 server to centrally manage Ubuntu 14.04 desktop clients, and what is the easiest mechanism to do this (LDAP, SAMBA, Kerberos, not NIS - too insecure)?

You can use Samba as an AD/DC to centrally manage usernames and passwords for Ubuntu 14.04 desktop users. You can't use GPO's however. You could look at [http://www.beyondtrust.com](http://www.beyondtrust.com) I thought at one point they offered a solution to manage Ubuntu machines. I could be wrong however.

---

### Post by matt_fussell2 on 2014-10-10
> **lingpanda said:**
> You can use Samba as an AD/DC to centrally manage usernames and passwords for Ubuntu 14.04 desktop users. You can't use GPO's however. You could look at [http://www.beyondtrust.com](http://www.beyondtrust.com) I thought at one point they offered a solution to manage Ubuntu machines. I could be wrong however.

They did, but I'm not looking to do anything with Windows machines - I'm wanting a pure linux (preferably Ubuntu) environment.

Thanks for the tip, though.

---

### Post by lingpanda on 2014-10-10
> **matt_fussell2 said:**
> They did, but I'm not looking to do anything with Windows machines - I'm wanting a pure linux (preferably Ubuntu) environment.

Thanks for the tip, though.

What about Ubuntu landscape? [http://www.ubuntu.com/management/](http://www.ubuntu.com/management/)

---

### Post by matt_fussell2 on 2014-10-10
> **lingpanda said:**
> What about Ubuntu landscape? [http://www.ubuntu.com/management/](http://www.ubuntu.com/management/)

While [Landscape]("http://www.ubuntu.com/management/landscape-features") is certainly a useful tool and does assist with IT management, it doesn't address the specific concerns I'm attempting to simplify. If you've been in IT long enough, you might remember Novell Netware or you may be familiar with a number of the user management and group policy controls of Microsoft Active Directory; in both cases, the control element (AD or Netware) were easy to deploy for average people. Average people need their tools to work for them so they can work on their business, not their tools. While the 'RTFM' stigma is slowly being replaced by people who want to help new users (and subsequently increase adoption), there is still much ground to cover.

---

### Post by matt_fussell2 on 2014-10-28
A quick note - I'm not giving up on this just yet - I may have some solutions worked out to the LDAP side of this, but I need to spend some more time verifying it before I post it here as a fix. I will be including setup scripts to get everything rolling. Once I get the LDAP side working, I'll come back and approach the Kerberos side, and then look at unifying the two. A set of scripts to handle client and server setup is the overall goal; most GUI programming is a little beyond my current grasp.

---

### Post by TheFu on 2014-10-28
I've done some GUI programming - years and years ago - used Visix Galaxy (a cross platform toolkit) and with TK/TCL. Meh ... 

There are CLI interface tools that aren't too hard to use for common scripting languages.
* zenity
* dialog (think there is xdialog and kdialog variants)
* [https://sites.google.com/site/easybashgui/](https://sites.google.com/site/easybashgui/)

OTOH, a tool that maps 100% to what useradd (or is it adduser?) would be great too. ;)

---

### Post by Jonathan L on 2014-10-28
Hi ...

Doubtless will be laughed at heartily, but you can get a very long way with scp of the password and group files, if that's all that needs to be kept in sync.  On locked-down desktops, of course.  Just adding a dirty solution to the elegant overkill of Mr Symes.

Best wishes, Jonathan.

---

### Post by matt_fussell2 on 2014-10-30
>     I've done some GUI programming - years and years ago - used Visix Galaxy (a cross platform toolkit) and with TK/TCL. Meh ...

    There are CLI interface tools that aren't too hard to use for common scripting languages.
    * zenity
    * dialog (think there is xdialog and kdialog variants)
    * [https://sites.google.com/site/easybashgui/](https://sites.google.com/site/easybashgui/)

    OTOH, a tool that maps 100% to what useradd (or is it adduser?) would be great too. 



I'll keep those in mind - most of what I've done has utilized Python to push out simple options.

> Doubtless will be laughed at heartily, but you can get a very long way with scp of the password and group files, if that's all that needs to be kept in sync. On locked-down desktops, of course. Just adding a dirty solution to the elegant overkill of Mr Symes.

No laughing necessary - it would work fairly well if not for the severe limitations of scope and time involved; I want to let the computers do the work so sysadmins get more done.

---

### Post by SeijiSensei on 2014-10-31
> **Jonathan L said:**
> Doubtless will be laughed at heartily, but you can get a very long way with scp of the password and group files, if that's all that needs to be kept in sync.  On locked-down desktops, of course.  Just adding a dirty solution to the elegant overkill of Mr Symes.

I'm not laughing, Jonathan.  I improvised a similar solution to keep three servers' password files in sync for a small company.  I used rsync to copy the files and did some integrity checks before writing any updates.  If there were any errors, the script aborted and notified the admins by email.

---

### Post by matt_fussell2 on 2014-11-07
The scripts for establishing a simple client-server LDAP environment are ready. This has been tested and verified on fresh installs of Ubuntu 14.04 Server and Ubuntu 14.04 desktop.

We'll start with the server - no GUI controls yet, but by using *ldapscripts*, the administration is greatly simplified versus using LDIF injections.
**EDIT: Server script updated to include some indexing control.**

```

#!/bin/bash
# written for Ubuntu 14.04 Server
# distilled from instructions found at
# http://theurbanpenguin.com/wp/?p=347
# http://theurbanpenguin.com/wp/?p=367
# http://www.danbishop.org/2011/10/29/ubuntu-11-10-sbs-small-business-server-setup-part-1-%E2%80%93-dhcp-and-dns/3/#ldap-indices

# You will need to make sure you have given your server
# a static IP and decided on a host name to which you'll 
# need to add a domain (example.com) and make sure that
# variables below match what your domain.
# This means you'll need to have things set in:
# /etc/hostname
# /etc/network/interfaces
# /etc/hosts

# This script must be executed as root.
if [[ $EUID -ne 0 ]]; then
    echo -e "\e[31mYOU MUST BE ROOT TO RUN THIS SCRIPT! \e[0m \n"
    exit 1
    else echo -e "Root privileges verified; proceeding. \n"
fi

# Control backup files
tmstamp=`date --rfc-3339=ns | sed 's/ /./g'`

# variables for deployment details
serverIP="localhost" # default: localhost
dc1="test" # default: example
dc2="local" # default: com
admin="admin" # default: admin
ldapPass="password" # your LDAP admin password
userVar="users" # your default user ou
groupVar="groups" # your default group ou
machVar="machines" # your default machines ou

# variable for controlling ldapscripts defaults
# default location for file to be written:
# /etc/ldapscripts/ldapscripts.conf
ldapScrCnf="/etc/ldapscripts/ldapscripts.conf"

# variable for controlling default OUs
struct="structure.ldif"

# variable for controlling LDAP Indexing options
index="index.ldif"

# variable for controlling the default LDAP password file
# default location: /etc/ldapscripts/ldapscripts.passwd
passFile="/etc/ldapscripts/ldapscripts.passwd"

# Install required software - there will be prompts to
# set required variables for LDAP; remember - what you
# put in when prompted must match the variables in this
# script.
apt-get update
aptitude install slapd ldap-utils ldapscripts -y 
aptitude safe-upgrade -y
apt-get autoremove -y
apt-get autoclean -y

# Write default structure file
touch $struct
echo "dn: ou=$userVar,dc=$dc1,dc=$dc2" >> $struct
echo "objectClass: organizationalUnit" >> $struct
echo "ou: $userVar" >> $struct
echo "" >> $struct
echo "dn: ou=$groupVar,dc=$dc1,dc=$dc2" >> $struct
echo "objectClass: organizationalUnit" >> $struct
echo "ou: $groupVar" >> $struct
echo "" >> $struct
echo "dn: ou=$machVar,dc=$dc1,dc=$dc2" >> $struct
echo "objectClass: organizationalUnit" >> $struct
echo "ou: $machVar" >> $struct

# Write default index file
touch $index
echo "dn: olcDatabase={1}hdb,cn=config" >> $index
echo "changetype: modify" >> $index
echo "add: olcDbIndex" >> $index
echo "olcDbIndex: uidNumber eq" >> $index
echo "olcDbIndex: gidNumber eq" >> $index
echo "olcDbIndex: loginshell eq" >> $index
echo "olcDbIndex: uid eq,pres,sub" >> $index
echo "olcDbIndex: memberUid eq,pres,sub" >> $index
echo "olcDbIndex: uniqueMember eq,pres" >> $index

# Add the structure file to LDAP
ldapadd -x -D cn=$admin,dc=$dc1,dc=$dc2 -W -f $struct
mv $struct $struct.back

# Run the indexing modification
ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f index.ldif
mv $index $index.back

# Write password file for ldapscripts
touch $passFile
echo -n "$ldapPass" > $passFile

# Backup original file
mv $ldapScrCnf $ldapScrCnf.back.$tmstamp
# Write ldapscripts.conf
touch $ldapScrCnf
echo "SERVER=\"ldap://$serverIP\"" >> $ldapScrCnf
echo "SUFFIX=\"dc=$dc1,dc=$dc2\"" >> $ldapScrCnf
echo "GSUFFIX=\"ou=$groupVar\"" >> $ldapScrCnf
echo "USUFFIX=\"ou=$userVar\"" >> $ldapScrCnf
echo "MSUFFIX=\"ou=$machVar\"" >> $ldapScrCnf
echo "SASLAUTH=\"\"" >> $ldapScrCnf
echo "BINDDN=\"cn=$admin,dc=$dc1,dc=$dc2\"" >> $ldapScrCnf
echo "BINDPWDFILE=\"$passFile\"" >> $ldapScrCnf
echo "GIDSTART=\"10000\"" >> $ldapScrCnf
echo "UIDSTART=\"10000\"" >> $ldapScrCnf
echo "MIDSTART=\"20000\"" >> $ldapScrCnf
echo "GCLASS=\"posixGroup\"" >> $ldapScrCnf
echo "CREATEHOMES=\"no\"" >> $ldapScrCnf
echo "PASSWORDGEN=\"pwgen\"" >> $ldapScrCnf
echo "RECORDPASSWORDS=\"no\"" >> $ldapScrCnf
echo "PASSWORDFILE=\"/var/log/ldapscripts_passwd.log\"" >> $ldapScrCnf
echo "LOGFILE=\"/var/log/ldapscripts.log\"" >> $ldapScrCnf
echo "LDAPSEARCHBIN=\"/usr/bin/ldapsearch\"" >> $ldapScrCnf
echo "LDAPADDBIN=\"/usr/bin/ldapadd\"" >> $ldapScrCnf
echo "LDAPDELETEBIN=\"/usr/bin/ldapdelete\"" >> $ldapScrCnf
echo "LDAPMODIFYBIN=\"/usr/bin/ldapmodify\"" >> $ldapScrCnf
echo "LDAPMODRDNBIN=\"/usr/bin/ldapmodrdn\"" >> $ldapScrCnf
echo "LDAPPASSWDBIN=\"/usr/bin/ldappasswd\"" >> $ldapScrCnf
echo "LDAPSEARCHOPTS=\"-o ldif-wrap=no\"" >> $ldapScrCnf
echo "GETENTPWCMD=\"\"" >> $ldapScrCnf
echo "GETENTGRCMD=\"\"" >> $ldapScrCnf
echo "GTEMPLATE=\"\"" >> $ldapScrCnf
echo "UTEMPLATE=\"\"" >> $ldapScrCnf
echo "MTEMPLATE=\"\"" >> $ldapScrCnf

```

One thing to note: if you need to change your master password, when creating the new */etc/ldapscripts/ldapscripts.passwd* file, make sure to use [COLOR=#008000]*echo -n ""*[/COLOR] and not just [COLOR=#008000]*echo ""*[/COLOR]; the newline character will cripple ldapscripts' functionality.

As for your client machines, this should get your started.
```

#!/bin/bash
# written for Ubuntu 14.04 Desktop
# distilled from instructions found at
# https://www.youtube.com/watch?v=l0e8rG0mku8
# Basic usuage instructions for ldapscripts can 
# be found here: 
# http://www.navdeepbagga.com/2012/10/user-and-group-management-in-ldap-through-command-line/

# This script must be executed as root.
if [[ $EUID -ne 0 ]]; then
    echo -e "\e[31mYOU MUST BE ROOT TO RUN THIS SCRIPT! \e[0m \n"
    exit 1
    else echo -e "Root privileges verified; proceeding. \n"
fi

# Variable for PAM file modification
pammod="/usr/share/pam-configs/mkhomedir" # default: /usr/share/pam-configs/mkhomedir

# Variable for modifying LightDM login variables
ldmmod="/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf" # default: /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf

# Install required software; note that there will be prompts
# to set necessary variables for LDAP. Most of the defaults work
# for selection choices, however, you will likely want to change
# the default LDAP address as follows:
# ldapi:///
# to
# ldap://
# Additionally, you will need the set your your administrative user
# and domain components (DCs). You will also need your administrative user's
# password to authenticat the client to LDAP.
apt-get update
apt-get install aptitude ldap-auth-client nscd -y
aptitude safe-upgrade -y
apt-get autoremove -y
apt-get autoclean -y
auth-client-config -t nss -p lac_ldap

# Allow for local home directories to be created
# for new LDAP users.
sudo touch $pammod
echo "Name: active mkhomedir" >> $pammod
echo "Default: yes" >> $pammod
echo "Priority: 900" >> $pammod
echo "Session-Type: Additional" >> $pammod
echo "Session:" >> $pammod
echo "    required    pam_mkhomedir.so umask=0022 skel=/etc/skel" >> $pammod

# Modify LightDM login settings
echo "allow-guest=false" >> $ldmmod
echo "greeter-hide-users=true" >> $ldmmod
echo "greeter-show-manual=true" >> $ldmmod

# Commit PAM changes
pam-auth-update

# Reboot system
reboot

```


If you wish to double check the connectivity prior to attempting login via LDAP, consider the following process. On your LDAP server, create a new organizational unit (read group) for your new users:

**On the server:**

```
sudo ldapaddgroup mycompany
```
Next, add a user to this group:
```
sudo ldapaddgroup testuser mycompany
```
The password that it automatically generates for the user is garbage, so give your test user a password that is a little more human-friendly:
```
sudo ldapsetpasswd testuser
```

**Back on your client machine:**

Login as the local user you established during setup, and open a command terminal (typically CTRL+ALT+T) and type the following:
```
getent passwd
``` and look at the bottom of the list - you should see *testuser* listed there. At this point, you should be able to logout and log back in as testuser, and you'll know your LDAP server is working.

**Looking Ahead:**
As previously posted, next I'll be moving on to Kerberos, and updating the scripts appropriately.

---

### Post by matt_fussell2 on 2014-11-10
**A quick note on why I'm doing this in chunks:**

The "Single Sign-On" issue is one that requires many moving parts to address; Mr. Symes provided some excellent resources, but they need some updating (things have changes since 11.04). As I go through and update everything part by part, it helps to understand how these parts interact. Additionally, I hope that this thread will be able to be used as a tool for others to address this same issue while understanding how everything works together.

That aside, breaking out individual components should provide a resource for modularizing this issue - i.e. running two (or more) hypervisors and establishing redundancy ... at any rate, I'll work on that after a complete answer to the original question is established.

---

### Post by matt_fussell2 on 2014-12-04
I've made progress on this - I'm working out some of the bugs on the client side. LDAP, Kerberos, DNSMasq, and NTP are all working, but I'm working through bugs in NFSv4: at the moment, my client is still having issues mounting the shared home directory.

---

### Post by matt_fussell2 on 2014-12-05
I've been fighting this all day, so here's the point where everything is stuck. I can't get the shared NFSv4 home directory to mount via autofs. I've been using the guide found [here]("http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/7/#part-7-connecting-ubuntu-clients") and updating as I go along because things have changed since Ubuntu 12.04. I can see the NFSv4 mount points on the server from the client:
```
matt@aspire1:/$ showmount -e main1.test.local
Export list for main1.test.local:
/export/home *
/export      *

```

/etc/auto.master
```

/home    /etc/auto.home

```

/etc/auto.home
```

*    -fstype=nfs4,rw,hard,intr,sec=krb5    main1.test.local:/home/&

```

Logging into the GUI isn't working, but logging in to the virtual terminal is; upon login to the virtual terminal I receive this notification:
```

No directory, logging in with HOME=/

```

At this point I stopped autofs and attempted to manually mount the NFS share:
```

matt@aspire1:/$sudo mount -t nfs main1.test.local:/export/home home
mount.nfs: access denied by server while mounting main1.test.local:/export/home

```

On the server, the exports file looks like this:
```

/export *(rw,fsid=0,crossmnt,insecure,async,no_subtree_check,sec=krb5p:krb5i:krb5)
/export/home *(rw,insecure,async,no_subtree_check,sec=krb5p:krb5i:krb5)

```

So yeah ... if the bugs can be worked out of this, I have already written the automation scripts for the rest of the server (1st draft - I'll test against VMs to make sure they're as bug-free as possible before posting). Any help is appreciated; if more config files need posted, please let me know and I'll get them up ASAP.

---

### Post by TheFu on 2014-12-05
Layered mounts could be the issue.  Is /export always mounted before /export/home?
Also - isn't nfs4 the mount type, not just nfs?  That's what the manpage shows here.

---

### Post by bab1 on 2014-12-06
> **TheFu said:**
> Layered mounts could be the issue.  Is /export always mounted before /export/home?
Also - isn't nfs4 the mount type, not just nfs?  That's what the manpage shows here.
I believe that later Linux kernels can use *nfs*.  The need to specify ntfs4 is only for earlier kernels.  See this from the current man page```
Under Linux 2.6.32 and *_later kernel versions,_* mount.nfs can mount all NFS file system ver&#8208;
       sions.  Under*_ earlier Linux kernel versions, mount.nfs4 must be used  for  mounting  NFSv4_*
       file systems while mount.nfs must be used for NFSv3 and v2.
```

To me that means you can safely use this with current kernels```
mount -t nfs blah blah blah
```

---

### Post by TheFu on 2014-12-06
> **bab1 said:**
> I believe that later Linux kernels can use *nfs*.  The need to specify ntfs4 is only for earlier kernels.  See this from the current man page```
Under Linux 2.6.32 and *_later kernel versions,_* mount.nfs can mount all NFS file system ver&#8208;
       sions.  Under*_ earlier Linux kernel versions, mount.nfs4 must be used  for  mounting  NFSv4_*
       file systems while mount.nfs must be used for NFSv3 and v2.
```

To me that means you can safely use this with current kernels```
mount -t nfs blah blah blah
```

I'm not seeing that 2.6.32 and later statement on my 3.13.xx system manpages (checked carefully for it).  OTOH, if it works ... ;)

Also - it could be a typo, but ntfs4 and nfs4 are not the same.  Did you mean to say ntfs4 above?

---

### Post by bab1 on 2014-12-06
> **TheFu said:**
> I'm not seeing that 2.6.32 and later statement on my 3.13.xx system manpages (checked carefully for it).  OTOH, if it works ... ;)

Also - it could be a typo, but ntfs4 and nfs4 are not the same.  Did you mean to say ntfs4 above?

No, I meant nfs4.  I'm so used to typing ntfs that "my little fingers" just do that.  Sorry :-(

[COLOR="#0000FF"]Edit: Try ```
 man mount.nfs
```... to see where I got the reference. [/COLOR]

---

### Post by TheFu on 2014-12-06
Ah ...  they are even linked to the same program.

```
-rwsr-xr-x 1 root root 88412 Jul 17 20:13 /sbin/mount.nfs*
lrwxrwxrwx 1 root root     9 Jul 17 20:13 /sbin/mount.nfs4 -> mount.nfs*

```
Nice catch.

This isn't helping the OP. I'm out of ideas.  I use nfsv3 and autofs constantly. Haven't screwed with kerberos here.

---

### Post by matt_symes on 2014-12-06
Hi

i will not attempt to help you today as the only Internet access is my phone.

however I will be near a PC tomorrow so I will post more then as I have a working Kerberos, nfs, DNS, dhcp setup.

firstly though, identify if this is a Kerberos issue by removing the sec parameters from the exports file and trying to mount the nfs share after restarting the nfs kernel server service. Try remounting after a reboot if that does not work.

That'll identify a Kerberos issue or not. I'm using the MIT version of Kerberos.

kind regards

---

### Post by matt_fussell2 on 2014-12-08
> **matt_symes said:**
> Hi

i will not attempt to help you today as the only Internet access is my phone.

however I will be near a PC tomorrow so I will post more then as I have a working Kerberos, nfs, DNS, dhcp setup.

firstly though, identify if this is a Kerberos issue by removing the sec parameters from the exports file and trying to mount the nfs share after restarting the nfs kernel server service. Try remounting after a reboot if that does not work.

That'll identify a Kerberos issue or not. I'm using the MIT version of Kerberos.

kind regards

So I disabled Kerberos on the shares:

**/etc/exports**

before:
```

/export *(rw,fsid=0,crossmnt,insecure,async,no_subtree_check,sec=krb5p:krb5i:krb5)
/export/home *(rw,insecure,async,no_subtree_check,sec=krb5p:krb5i:krb5)

```

after:
```

/export *(rw,fsid=0,crossmnt,insecure,async,no_subtree_check)
/export/home *(rw,insecure,async,no_subtree_check)

```

**/etc/default/nfs-common**

before:
```

# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
#   Should rpc.statd listen on a specific port? This is especially useful
#   when you have a port-based firewall. To use a fixed port, set this
#   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
#   For more information, see rpc.statd(8) or http://wiki.debian.org/SecuringNFS
STATDOPTS=

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_GSSD=yes

```

after:
```

# If you do not set values for the NEED_ options, they will be attempted
# autodetected; this should be sufficient for most people. Valid alternatives
# for the NEED_ options are "yes" and "no".

# Do you want to start the statd daemon? It is not needed for NFSv4.
NEED_STATD=

# Options for rpc.statd.
#   Should rpc.statd listen on a specific port? This is especially useful
#   when you have a port-based firewall. To use a fixed port, set this
#   this variable to a statd argument like: "--port 4000 --outgoing-port 4001".
#   For more information, see rpc.statd(8) or http://wiki.debian.org/SecuringNFS
STATDOPTS=

# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_GSSD=   

```

[B]/etc/default/nfs-kernel-server
[/B]
before:
```

# Number of servers to start up
RPCNFSDCOUNT=8

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or http://wiki.debian.org/SecuringNFS
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
RPCMOUNTDOPTS="--manage-gids"

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD="yes"

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=""

# Options for rpc.nfsd.
RPCNFSDOPTS=""

```

after:
```

# Number of servers to start up
RPCNFSDCOUNT=8

# Runtime priority of server (see nice(1))
RPCNFSDPRIORITY=0

# Options for rpc.mountd.
# If you have a port-based firewall, you might want to set up
# a fixed port here using the --port option. For more information,
# see rpc.mountd(8) or http://wiki.debian.org/SecuringNFS
# To disable NFSv4 on the server, specify '--no-nfs-version 4' here
RPCMOUNTDOPTS="--manage-gids"

# Do you want to start the svcgssd daemon? It is only required for Kerberos
# exports. Valid alternatives are "yes" and "no"; the default is "no".
NEED_SVCGSSD="no"

# Options for rpc.svcgssd.
RPCSVCGSSDOPTS=""

# Options for rpc.nfsd.
RPCNFSDOPTS=""

```

I rebooted the server and the test client. For consistency, I attempted login from the terminal, and the system again reported that no home directory was available. I stopped the autofs daemon and manually remounted the drive:
```

sudo service autofs stop
sudo mount -t nfs main1.test.local:/export/home home

```

It did take some time, but it mounted. At that point, I was able to login to another virtual terminal without issue, and subsequently I was able to login to the graphical prompt, with all files populating properly.

---

### Post by matt_fussell2 on 2014-12-08
Since the manual mounting worked, I made changes to the auto.home settings on the client:
```
*    -fstype=nfs4,rw,hard,intr    main1.test.local:/home/&
```

and I changed the line in /etc/default/nfs-common that read NEED_GSSD=yes as follows:
```
NEED_GSSD=
```

At this point, the client is connecting correctly. I'm going to reboot and test it a few times more.

---

### Post by TheFu on 2014-12-08
[https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1270445](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1270445) is a bug report that seems very much related. A few other options in the link.

---

### Post by matt_fussell2 on 2014-12-08
The client was missing it's .keytab file. That's been fixed, and everything is working. I'm going to get to work on the scripts and I will post them up as soon I've verified their functionality. Just so that it doesn't get overlooked, thank you to everyone who has contributed to this thread.

---

### Post by matt_symes on 2014-12-09
Hi

> **matt_fussell2 said:**
> The client was missing it's .keytab file. That's been fixed, and everything is working. I'm going to get to work on the scripts and I will post them up as soon I've verified their functionality. Just so that it doesn't get overlooked, thank you to everyone who has contributed to this thread.

Well done :)

It can be a pain to set up so i detailed all the steps i took on my personal wiki.

I though you might have replied on Sunday but i seems you didn't really need much help anyway.

Make sure you lock it down from the Internet though with your firewall rules.

Kind regards

---

### Post by matt_fussell2 on 2014-12-09
> **matt_symes said:**
> Hi

Well done :)

It can be a pain to set up so i detailed all the steps i took on my personal wiki.

I though you might have replied on Sunday but i seems you didn't really need much help anyway.

Make sure you lock it down from the Internet though with your firewall rules.

Kind regards

Having a group of people off of whom I can bounce ideas helps jumpstart my brain; my local office is thin on tech personnel.

---

### Post by matt_fussell2 on 2014-12-15
After testing the scripts to rebuild both the client and the server, the kerberized NFS mounts are a problem (I have a limited testing environment; the only way to test the server was to rebuild it). The client build script functioned within the environment after multiple rebuilds. The server script has the error I mentioned above. I fixed it on Friday, but what I thought fixed the issue didn't fix it when I ran the scripts again today to test the build. When disabling the kerberos requirements in **/etc/exports**, **/etc/default/nfs-common**, and **/etc/default/nfs-kernel-server** on the server and **/etc/auto.home** and **/etc/default/nfs-common** on the client, the shared home directory works again.

Admittedly I'm fairly new to LDAP and Kerberos, so there is likely something simple that I'm missing or misunderstanding.  Here are the scripts as they are - I'll continue pursuing the problem tomorrow, but if anyone can offer some help, I'd be ever so grateful.

the client script:
```
#!/bin/bash
# written for Ubuntu 14.04 Desktop
# distilled from:
# http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/7/#part7-connecting-ubuntu-clients
# with assistance from the Ubuntu Forums
# http://www.ubuntuforums.org

# This script must be executed as root.
if [[ $EUID -ne 0 ]]; then
    echo -e "\e[31mYOU MUST BE ROOT TO RUN THIS SCRIPT! \e[0m \n"
    exit 1
    else echo -e "Root privileges verified; proceeding. \n"
fi

echo "NOTE: You must authenticate to Kerberos via kinit (USERNAME)/admin"
echo "on the server before proceeeding. Press CTRL-C to terminate this"
echo "script or ENTER to continue; failure to do so will result in the"
echo "inability to use this machine on the domain. If you have already"
echo "authenticated to the server, it is recommended to log back into"
echo "the server and type 'klist' to ensure your ticket is still valid"
echo "before proceeding."
read configureThisDomainClient

# Variable for blacklisting rpcsec_gss_krb5 to speed up nfs mounts
# default /etc/modprobe.d/blacklist.conf
rpcblk="/etc/modprobe.d/blacklist.conf"

# Variable for adding host to Kerberos
hname=`hostname -f`

# Variable for modifying LightDM login variables
# default: /usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf
ldmmod="/usr/share/lightdm/lightdm.conf.d/50-ubuntu.conf" 

# Variable for controlling krb5.conf
# default location /etc/krb5.conf
k5conf="/etc/krb5.conf"

# Variable for controlling sssd.conf
# This file is not generated by default; a generic sample file
# can be found in /usr/share/doc/sssd-common/examples/sssd-example.conf
sdcnf="/etc/sssd/sssd.conf"

# variable for controlling nfs-common
# default: /etc/default/nfs-common
nfscmn="/etc/default/nfs-common"

# variables for controlling autofs
# default: /etc/auto.master
atmstr="/etc/auto.master"
athome="/etc/auto.home"

# Variable for modifying polkit
# default: /etc/polkit-1/localauthority.conf.d/51-ubuntu-admin.conf
polmod="/etc/polkit-1/localauthority.conf.d/51-ubuntu-admin.conf"

# Variable for controlling nsswitch.conf
nswcnf="/etc/nsswitch.conf"

# control backup files
tmstamp=`date --rfc-3339=ns | sed 's/ /./g'`

krbadmin="administrator" # default Kerberos administrator
admin="administrator" # default administrative user
srvrName="main1" # server name
dc1="test" # default: example
dc2="local" # default: com

#============================================#
#     Derived variables in this section      #
#============================================#
newDom="$dc1.$dc2" # concatenated domain name
newDomUp=`echo $newDom | tr '[:lower:]' '[:upper:]'` # capitalized newDom

apt-get update
apt-get install aptitude sssd libsss-sudo autofs krb5-user nfs-common -y
aptitude safe-upgrade -y
apt-get autoremove -y
apt-get autoclean -y

# Rewrite nsswitch file to address potential name resolution issues.
mv $nswcnf $nswcnf.back.$tmstamp
touch $nswcnf
echo "" >> $nswcnf
echo "passwd:        compat sss" >> $nswcnf
echo "group:        compat sss" >> $nswcnf
echo "shadow:        compat" >> $nswcnf
echo "" >> $nswcnf
echo "hosts:        files mdns4_minimal dns" >> $nswcnf
echo "network:    files" >> $nswcnf
echo "" >> $nswcnf
echo "protocols:    db files" >> $nswcnf
echo "services:    db files" >> $nswcnf
echo "ethers:        db files" >> $nswcnf
echo "rpc:        db files" >> $nswcnf
echo "" >> $nswcnf
echo "netgroup:    nis sss" >> $nswcnf
echo "sudoers:    files sss" >> $nswcnf

# Restart dhcp to pick up changes in nsswitch.conf
sudo service network-manager restart

# Modify LightDM login settings
# This will allow domain login, disallow the guest account,
# and hide the available users from the login screen.
echo "allow-guest=false" >> $ldmmod
echo "greeter-hide-users=true" >> $ldmmod
echo "greeter-show-manual=true" >> $ldmmod

# Create the sssd.conf file
touch $sdcnf
echo "[sssd]" >> $sdcnf
echo "config_file_version = 2" >> $sdcnf
echo "reconnection_retries = 3" >> $sdcnf
echo "sbus_timeout = 30" >> $sdcnf
echo "services = nss, pam, sudo" >> $sdcnf
echo "domains = $newDom" >> $sdcnf
echo "" >> $sdcnf
echo "[nss]" >> $sdcnf
echo "filter_groups = root" >> $sdcnf
echo "filter_users = root" >> $sdcnf
echo "reconnection_retries = 3" >> $sdcnf
echo "" >> $sdcnf
echo "[pam]" >> $sdcnf
echo "reconnection_retries = 3" >> $sdcnf
echo "" >> $sdcnf
echo "[domain/$newDom]" >> $sdcnf
echo "; Using enumerate = true leads to high load and slow response" >> $sdcnf
echo "enumerate = false" >> $3sdcnf
echo "cache_credentials = false" >> $sdcnf
echo "" >> $sdcnf
echo "id_provider = ldap" >> $sdcnf
echo "auth_provider = krb5" >> $sdcnf
echo "chpass_provider = krb5" >> $sdcnf
echo "" >> $sdcnf
echo "ldap_uri = ldap://ldap.$newDom" >> $sdcnf
echo "ldap_search = dc=$dc1,dc=$dc2" >> $sdcnf
echo "ldap_sudo_search_base = ou=sudoers,dc=$dc1,dc=$dc2" >> $sdcnf
echo "ldap_tls_reqcert = never" >> $sdcnf
echo "" >> $sdcnf
echo "krb5_kdcip = kerberos.$newDom" >> $sdcnf
echo "krb5_realm = $newDomUp" >> $sdcnf
echo "krb5_changepw_principle = kadmin/changepw" >> $sdcnf
echo "krb5_auth_timeout = 15" >> $sdcnf
echo "krb5_renewable_lifetime = 5d" >> $sdcnf

# ensure proper permissions and start the sssd daemon
chmod 600 $sdcnf
service sssd restart

# This step may not be necessary since the krb5.conf file will
# be rewritten, but is included in an effort to ensure completion.
# This step with will ask for the realm (EXAMPLE.COM). If prompted
# to add the realm information to /etc/krb5.conf, select YES. If
# prompted to enter the kerberos server and admin server (should be
# the same [12/8/14]), enter (SERVER.EXAMPLE.COM)
dpkg-reconfigure krb5-config

# Modify krb5.conf
mv $k5conf $k5conf.back.$tmstamp
touch $k5conf
echo "[libdefaults]" >> $k5conf
echo "    default_realm = $newDomUp" >> $k5conf
echo "    krb4_config = /etc/krb.conf" >> $k5conf
echo "    krb4_realms = /etc/krb.realms" >> $k5conf
echo "    kdc_timesync = 1" >> $k5conf
echo "    ccache_type = 4" >> $k5conf
echo "    forwardable = true" >> $k5conf
echo "    proxiable = true" >> $k5conf
echo "    allow_weak_crypto = true" >> $k5conf
echo "    v4_instance_resolve = false" >> $k5conf
echo "    vr_name_convert = {" >> $k5conf
echo "        host = {" >> $k5conf
echo "            rcmd = host" >> $k5conf
echo "            ftp = ftp" >> $k5conf
echo "        }" >> $k5conf
echo "        plain = {" >> $k5conf
echo "            something = something-else" >> $k5conf
echo "        }" >> $k5conf
echo "    }" >> $k5conf
echo "    fcc-mit-ticketflags = true" >> $k5conf
echo "" >> $k5conf
echo "[realms]" >> $k5conf
echo "    $newDomUp = {" >> $k5conf
echo "        kdc = $srvrName.$newDom" >> $k5conf
echo "        admin_server = $srvrName.$newDom" >> $k5conf
echo "        master_kdc = $srvrName.$newDom" >> $k5conf
echo "        default_domain = $newDom" >> $k5conf
echo "    }" >> $k5conf
echo "" >> $k5conf
echo "[domain_realm]" >> $k5conf
echo "" >> $k5conf
echo "[login]" >> $k5conf
echo "    krb4_convert = true" >> $k5conf
echo "    krb4_get_tickets = false" >> $k5conf

# Next, a principle entry will be created for the new client machine
kadmin -p $krbadmin/admin -q "addprinc -randkey nfs/$hname"
kadmin -p $krbadmin/admin -q "ktadd nfs/$hname"

# Modify nfs-common
mv $nfscmn $nfscmn.back.$tmstamp
touch $nfscmn
echo "NEED_STATD=" >> $nfscmn
echo "STATDOPTS=" >> $nfscmn
echo "NEED_GSSD=yes" >> $nfscmn

# Modify and configure autofs
mv $atmstr $atmstr.back.$tmstamp
echo "/home    $athome" >> $atmstr
touch $athome
echo "*    -fstype=nfs4,rw,hard,intr,sec=krb5    $srvrName.$newDom:/home/&" >> $athome
service autofs restart

# Allow the use of graphical programs as administrator
mv $polmod $polmod.back.$tmstamp
touch $polmod
echo "[Configuration]" >> $polmod
echo "AdminIdentities=unix-group:admin;unix-group:10000" >> $polmod

# Speed up nfs mounting
#echo "" >> $rpcblk
#echo "# blacklist rpcsec_gss_krb5 to speed up NFS mounting" >> $rpcblk
#echo "blacklist rpcsec_gss_krb5" >> $rpcblk

# Reboot the client to complete domain configuration
reboot
```

The server script:
```
#!/bin/bash
# this script was written for Ubuntu 14.04 server
# distilled from instructions found at:
# http://www.danbishop.org/2011/10/29/ubuntu-11-10-sbs-small-business-server-setup-part-1-%E2%80%93-dhcp-and-dns/#part-1-dhcp-and-dns (full article)
# http://www.danbishop.org/2012/06/02/ubuntu-12-04-ultimate-server-guide/#the-installation (full article)
# http://unix.stackexchange.com/questions/128220/how-do-i-set-my-dns-on-ubuntu-14-04
# http://ubuntuforums.org/showthread.php?t=1706192
# http://askubuntu.com/questions/87665/how-do-i-change-the-hostname-without-a-restart
# http://theurbanpenguin.com/wp/?p=347
# http://theurbanpenguin.com/wp/?p=367
# This script should be ran as root.

# this script must be executed as root.
if [[ $EUID -ne 0 ]]; then
    echo -e "\e[31mYOU MUST BE ROOT TO RUN THIS SCRIPT! \e[0m \n"
    exit 1
    else echo -e "Root privileges verified; proceeding. \n"
fi

# Variable for controlling backup files
tmstamp=`date --rfc-3339=ns | sed 's/ /./g'`
# Variable for augmenting resolvconf
# default: /etc/resolvconf/resolv.conf.d/head
rslvConf="/etc/resolvconf/resolv.conf.d/head"
# Variable for rewriting dnsmasq.conf
# default: /etc/dnsmasq.conf
dnsConf="/etc/dnsmasq.conf"
# Variable for rewriting ntp.conf 
# default /etc/ntp.conf
ntpCfg="/etc/ntp.conf"
# Variable for adding ntp synchronization to CRON
# default /etc/cron.daily/ntpdate
cronDF="/etc/cron.daily/ntpdate"
# Variable for controlling sudoers file entry
# default: /etc/sudoers
sudrs="/etc/sudoers"
# Variable for controlling ldapscripts defaults
# default: /etc/ldapscripts/ldapscripts.conf
ldapScrCnf="/etc/ldapscripts/ldapscripts.conf"
# Variable for controlling default OUs
struct="structure.ldif"
# Variable for controlling LDAP Indexing options
index="index.ldif"
# Variable for controlling autofs LDIF
afsl="autofs.ldif"
# Variable for controlling automount LDIF
atml="automount.ldif"
# Variable for controlling sudo schema
sudl="sudo.ldif"
# Variable for implementing sudo schema
sudml="sudoMaster.ldif"
# Variable for controlling the default LDAP password file
# default: /etc/ldapscripts/ldapscripts.passwd
passFile="/etc/ldapscripts/ldapscripts.passwd"
# Variable for controlling kadm5.acl
# default: /etc/krb5kdc/kadm5.acl
k5acl="/etc/krb5kdc/kadm5.acl"
# Variable for controlling krb5.conf
# default /etc/krb5.conf
k5conf="/etc/krb5.conf"
# Variable for controlling sssd.conf
# This file is not generated by default; a generic sample file
# can be found in /usr/share/doc/sssd-common/examples/sssd-example.conf
sdcnf="/etc/sssd/sssd.conf"
# Variable for controlling the sshd_conf file
# default: /etc/ssh/sshd_config
sshFile="/etc/ssh/sshd_config"
# Variable for controlling fstab file
# default: /etc/fstab
fstb="/etc/fstab"
# Variable for controlling export file
# default: /etc/exports
xprts="/etc/exports"
# Variable for controlling nfs-common
# default: /etc/default/nfs-common
nfscmn="/etc/default/nfs-common"
# Variable for controlling nfs-kernel-server
# default: /etc/default/nfs-kernel-server
nksrv="/etc/default/nfs-kernel-server"
# Variable for controlling idmapd.conf
# default: /etc/idmapd.conf
idmpd="/etc/idmapd.conf"

# These are variables to be adjusted as necessary
serverIP="localhost" # default: localhost
krbadmin="administrator" # default Kerberos administrator
ldadmin="admin" # default LDAP administrator
admin="administrator" # default system administrative user
srvrName="main1" # server name
dc1="test" # default: example
dc2="local" # default: com
newIP="192.168.1.50" # new machine IP
newMask="255.255.255.0" # new netmask
newGate="192.168.1.1" # new network gateway
newNet="192.168.1.0" # new network address
newBrd="192.168.1.255" # new broadcast address
newDNS1="192.168.1.50" # new primary DNS
newDNS2="8.8.8.8" # new secondary DNS
newDNS3="8.8.4.4" # new tertiary DNS
intf="eth0" # primary ethernet interface
ldapPass="password" # your LDAP admin password
userVar="users" # your default user ou
groupVar="groups" # your default group ou
machVar="machines" # your default machines ou
users="domainusers" # default user group
admins="domainadmins" # default admin group
#ntpSrvr="" # use to define external NTP server
dhcpUp="192.168.1.250" # upper DHCP limit
dhcpLw="192.168.1.100" # lower DHCP limit
leaseTm="8h" # dhcp lease time
#============================================#
#     Derived variables in this section      #
#============================================#
newDom="$dc1.$dc2" # concatenated domain name
oct1=`echo $newIP | cut -d. -f1`
oct2=`echo $newIP | cut -d. -f2`
oct3=`echo $newIP | cut -d. -f3`
oct4=`echo $newIP | cut -d. -f4`
newIPRev="$oct4.$oct3.$oct2.$oct1" # reversed IP Address
newDomUp=`echo $newDom | tr '[:lower:]' '[:upper:]'` # capitalized newDom

# Create update script
upd8="/home/$admin/bin/updateServer.sh"
mkdir /home/$admin/bin
touch $upd8
echo "#!/bin/bash" >> $upd8
echo "# This script written for Ubuntu 14.04 Server" >> $upd8
echo "sudo apt-get update" >> $upd8
echo "sudo aptitude safe-upgrade -y" >> $upd8
echo "sudo apt-get autoremove -y" >> $upd8
echo "sudo apt-get autoclean -y" >> $upd8
chmod +x $upd8
chown $admin:$admin /home/$admin/bin
chown $admin:$admin $upd8

# Install updates for base system
apt-get update
aptitude install -y openssh-server
aptitude safe-upgrade -y
apt-get autoremove -y
apt-get autoclean -y

# Backup and replace /etc/hosts
newHosts="/etc/hosts"
mv $newHosts $newHosts.back.$tmstamp
touch $newHosts
echo "127.0.0.1    localhost.localdomain    localhost" >> $newHosts
echo "$newIP    $srvrName.$newDom    $srvrName" >> $newHosts
echo "" >> $newHosts
echo "::1    localhost    ip6-localhost    ip6-loopback" >> $newHosts
echo "ff02::1    ip6-allnodes" >> $newHosts
echo "ff02::2    ip6-allrouters" >> $newHosts

# Backup and replace /etc/network/interfaces
newIF="/etc/network/interfaces"
mv $newIF $newIF.back.$tmstamp
touch $newIF
echo "auto lo" >> $newIF
echo "iface lo inet loopback" >> $newIF
echo "" >> $newIF
echo "auto eth0" >> $newIF
echo "iface eth0 inet static" >> $newIF
echo "    address $newIP" >> $newIF
echo "    netmask $newMask" >> $newIF
echo "    gateway $newGate" >> $newIF
echo "    network $newNet" >> $newIF
echo "    broadcast $newBrd" >> $newIF
echo "    dns-nameservers $newIP, $newDNS2, $newDNS3" >> $newIF

# Add information to resolvconf
mv $rslvConf $rslvConf.back.$tmstamp
touch $rslvConf
echo "domain $dc1.$dc2" >> $rslvConf
echo "search $dc1.$dc2" >> $rslvConf
echo "nameserver $newIP" >> $rslvConf

# Change hostname and restart interface
hostnamectl set-hostname $srvrName.$newDom
service network-interface restart INTERFACE="$intf"

# Install dnsmasq
aptitude install dnsmasq -y

# Add an external host file for dnsmasq
touch /etc/hosts.dnsmasq

# Reconfigure dnsmasq
mv $dnsConf $dnsConf.back.$tmstamp
touch $dnsConf
echo "# Use a specific hosts file for dnsmasq" >> $dnsConf
echo "no-hosts" >> $dnsConf
echo "addn-hosts=/etc/hosts.dnsmasq" >> $dnsConf
echo "" >> $dnsConf
echo "# DNS settings for the network" >> $dnsConf
echo "server=/localnet/$newIP" >> $dnsConf
echo "server=/#/$newDNS2" >> $dnsConf
echo "server=/#/$newDNS3" >> $dnsConf
echo "" >> $dnsConf
echo "# set dhcp options" >> $dnsConf
echo "dhcp-option=19,0                # option ip-forwarding off" >> $dnsConf
echo "dhcp-option=44,0.0.0.0             # set netbios-over-TCP/IP nameserver(s) aka WINS ser$" >> $dnsConf
echo "dhcp-option=45,0.0.0.0            # netbios datagram distribution server" >> $dnsConf
echo "dhcp-option=46,8                # netbios node type" >> $dnsConf
echo "" >> $dnsConf
echo "domain=$newDom                # sets domain to be used" >> $dnsConf
echo "dhcp-range=$dhcpLw,$dhcpUp,$leaseTm    # sets IP lease range and lease time" >> $dnsConf
echo "dhcp-option=option:router,$newGate        # sets gateway address" >> $dnsConf
echo "dhcp-option=option:ntp-server,$newIP    # sets the NTP server for the network" >> $dnsConf
echo "dhcp-authoritative                # make this the authoritative DHCP server" >> $dnsConf
echo "" >> $dnsConf
echo "# DNS settings for this server" >> $dnsConf
echo "# (required for Kerberos)" >> $dnsConf
echo "ptr-record=$newIPRev.in-addr.arpa.,\"$srvrName.$newDom\"" >> $dnsConf
echo "address=/$srvrName.$newDom/$newIP" >> $dnsConf
echo "" >> $dnsConf
echo "# Kerberos and LDAP automatic settings" >> $dnsConf
echo "# automatically maps Kerberos and LDAP" >> $dnsConf
echo "# to DHCP Clients, making them realm-aware" >> $dnsConf
echo "address=/kerberos.$newDom/$newIP" >> $dnsConf
echo "address=/ldap.$newDom/$newIP" >> $dnsConf
echo "" >> $dnsConf
echo "txt-record=_kerberos.$newDom,\"$newDomUp\"" >> $dnsConf
echo "srv-host=_udp.$newDom,\"kerberos.$newDom\",88" >> $dnsConf
echo "srv-host=_tcp.$newDom,\"kerberos.$newDom\",88" >> $dnsConf
echo "srv-host=_kerberos-master._udp.$newDom,\"kerberos.$newDom\",88" >> $dnsConf
echo "srv-host=_kerberos-adm._tcp.$newDom,\"kerberos.$newDom\",749" >> $dnsConf
echo "srv-host=_kpasswd._udp.$newDom,\"kerberos.$newDom\",464" >> $dnsConf
echo "" >> $dnsConf
echo "srv-host=_ldap._tcp.$newDom,ldap.$newDom,389" >> $dnsConf

# Restart dnsmasq
service dnsmasq restart

# install NTP    
apt-get install ntp ntpdate -y

# back up and re-write NTP config file
mv $ntpCfg $ntpCfg.back.$tmstamp
touch $ntpCfg
# enable statistics logging
echo "statsdir /var/log/ntpstats" >> $ntpCfg
echo "driftfile /var/lib/ntp/ntp.drift" >> $ntpCfg
echo "statistics loopstats peerstats clockstate" >> $ntpCfg
echo "filegen loopstats file loopstats type day enable" >> $ntpCfg
echo "filegen peerstats file peerstats type day enable" >> $ntpCfg
echo "filegen clockstats file clockstats type day enable" >> $ntpCfg
# specify NTP servers, including local NIST for US (this one for CST)
echo "server 0.ubuntu.pool.ntp.org" >> $ntpCfg
echo "server 1.ubuntu.pool.ntp.org" >> $ntpCfg
echo "server 2.ubuntu.pool.ntp.org" >> $ntpCfg
echo "server 3.ubuntu.pool.ntp.org" >> $ntpCfg
echo "server pool.ntp.org" >> $ntpCfg
echo "server ntp.ubuntu.com" >> $ntpCfg
# put additional local time servers here
echo "server nist.time.nosc.us" >> $ntpCfg # Carrollton, TX 96.226.242.9
# set access control
echo "restrict -4 default kod notrap nomodify nopeer noquery" >> $ntpCfg
echo "restrict -6 default kod notrap nomodify nopeer noquery" >> $ntpCfg
echo "restrict 127.0.0.1" >> $ntpCfg
echo "restrict ::1" >> $ntpCfg
# provide time for local subnet
echo "broadcast $newBrd" >> $ntpCfg

touch $cronDF
echo "ntpdate ntp.ubuntu.com pool.ntp.org nist.time.nosc.us" >> $cronDF
chmod 755 $cronDF

# Restart the NTP server
service ntp restart

# Install required software - there will be prompts to
# set required variables for LDAP; remember - what you
# put in when prompted must match the variables in this
# script.
aptitude install slapd ldap-utils ldapscripts libnss-ldapd libpam-ldapd -y 

# Write default structure file
touch $struct
echo "dn: ou=$userVar,dc=$dc1,dc=$dc2" >> $struct
echo "objectClass: organizationalUnit" >> $struct
echo "ou: $userVar" >> $struct
echo "" >> $struct
echo "dn: ou=$groupVar,dc=$dc1,dc=$dc2" >> $struct
echo "objectClass: organizationalUnit" >> $struct
echo "ou: $groupVar" >> $struct
echo "" >> $struct
echo "dn: ou=$machVar,dc=$dc1,dc=$dc2" >> $struct
echo "objectClass: organizationalUnit" >> $struct
echo "ou: $machVar" >> $struct

# Write default index file
touch $index
echo "dn: olcDatabase={1}hdb,cn=config" >> $index
echo "changetype: modify" >> $index
echo "add: olcDbIndex" >> $index
echo "olcDbIndex: uidNumber eq" >> $index
echo "olcDbIndex: gidNumber eq" >> $index
echo "olcDbIndex: loginshell eq" >> $index
echo "olcDbIndex: uid eq,pres,sub" >> $index
echo "olcDbIndex: memberUid eq,pres,sub" >> $index
echo "olcDbIndex: uniqueMember eq,pres" >> $index

# Write autofs.ldif file
touch $afsl
echo "dn: cn=autofs,cn=schema,cn=config" >> $afsl
echo "objectClass: olcSchemaConfig" >> $afsl
echo "cn: autofs" >> $afsl
echo "olcAttributeTypes: {0}( 1.3.6.1.1.1.1.25 NAME 'automountInformation' DESC 'Information used by the autofs automounter' EQUALITY caseExactIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 SINGLE-VALUE )" >> $afsl
echo "olcObjectClasses: {0}( 1.3.6.1.1.1.1.13 NAME 'automount' DESC 'An entry in an automounter map' SUP top STRUCTURAL MUST ( cn \$ automountInformation \$ objectclass ) MAY description )" >> $afsl
echo "olcObjectClasses: {1}( 1.3.6.1.4.1.2312.4.2.2 NAME 'automountMap' DESC 'An group of related automount objects' SUP top STRUCTURAL MUST ou )" >> $afsl

# Write the automount.ldif
touch $atml
echo "dn: ou=$ldadmin,dc=$dc1,dc=$dc2" >> $atml
echo "ou: $admin" >> $atml
echo "objectClass: top" >> $atml
echo "objectClass: organizationalUnit" >> $atml
echo "" >> $atml
echo "dn: ou=automount,ou=$ldadmin,dc=$dc1,dc=$dc2" >> $atml
echo "ou: automount" >> $atml
echo "objectClass: top" >> $atml
echo "objectClass: organizationalUnit" >> $atml
echo "" >> $atml
echo "dn: ou=auto.master,ou=automount,ou=$ldadmin,dc=$dc1,dc=$dc2" >> $atml
echo "ou: auto.master" >> $atml
echo "objectClass: top" >> $atml
echo "objectClass: automountMap" >> $atml
echo "" >> $atml
echo "dn: cn=/home,ou=auto.master,ou=automount,ou=$ldadmin,dc=$dc1,dc=$dc2" >> $atml
echo "cn: /home" >> $atml
echo "objectClass: top" >> $atml
echo "objectClass: automount" >> $atml
echo "automountInformation: ldap:ou=auto.home,ou=automount,ou=$ldadmin,dc=$dc1,dc=$dc2 --timeout=60 --ghost" >> $atml
echo "" >> $atml
echo "dn: ou=auto.home,ou=automount,ou=$ldadmin,dc=$dc1,dc=$dc2" >> $atml
echo "ou: auto.home" >> $atml
echo "objectClass: top" >> $atml
echo "objectClass: automountMap" >> $atml
echo "" >> $atml
echo "dn: cn=/,ou=auto.home,ou=automount,ou=$ldadmin,dc=$dc1,dc=$dc2" >> $atml
echo "cn: /" >> $atml
echo "objectClass: top" >> $atml
echo "objectClass: automount" >> $atml
echo "automountInformation: -fstype=nfs4,rw,hard,intr,fsc,sec=krb5 $srvrName.$dc1.$dc2:/home/\$" >> $atml

# Write sudo.ldif
touch $sudl
echo "dn: cn=sudo,cn=schema,cn=config" >> $sudl
echo "objectClass: olcSchemaConfig" >> $sudl
echo "cn: sudo" >> $sudl
echo "olcAttributeTypes: {0}( 1.3.6.1.4.1.15953.9.1.1 NAME 'sudoUser' DESC 'User(s) who may  run sudo' EQUALITY caseExactIA5Match SUBSTR caseExactIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 )" >> $sudl
echo "olcAttributeTypes: {1}( 1.3.6.1.4.1.15953.9.1.2 NAME 'sudoHost' DESC 'Host(s) who may run sudo' EQUALITY caseExactIA5Match SUBSTR caseExactIA5SubstringsMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 )" >> $sudl
echo "olcAttributeTypes: {2}( 1.3.6.1.4.1.15953.9.1.3 NAME 'sudoCommand' DESC 'Command(s) to be executed by sudo' EQUALITY caseExactIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 )" >> $sudl
echo "olcAttributeTypes: {3}( 1.3.6.1.4.1.15953.9.1.4 NAME 'sudoRunAs' DESC 'User(s) impersonated by sudo (deprecated)' EQUALITY caseExactIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 )" >> $sudl
echo "olcAttributeTypes: {4}( 1.3.6.1.4.1.15953.9.1.5 NAME 'sudoOption' DESC 'Option(s) followed by sudo' EQUALITY caseExactIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 )" >> $sudl
echo "olcAttributeTypes: {5}( 1.3.6.1.4.1.15953.9.1.6 NAME 'sudoRunAsUser' DESC 'User(s) impersonated by sudo' EQUALITY caseExactIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 )" >> $sudl
echo "olcAttributeTypes: {6}( 1.3.6.1.4.1.15953.9.1.7 NAME 'sudoRunAsGroup' DESC 'Group(s) impersonated by sudo' EQUALITY caseExactIA5Match SYNTAX 1.3.6.1.4.1.1466.115.121.1.26 )" >> $sudl
echo "olcAttributeTypes: {7}( 1.3.6.1.4.1.15953.9.1.8 NAME 'sudoNotBefore' DESC 'Start of time interval for which the entry is valid' EQUALITY generalizedTimeMatch ORDERING generalizedTimeOrderingMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 )" >> $sudl
echo "olcAttributeTypes: {8}( 1.3.6.1.4.1.15953.9.1.9 NAME 'sudoNotAfter' DESC 'End of time interval for which the entry is valid' EQUALITY generalizedTimeMatch ORDERING generalizedTimeOrderingMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.24 )" >> $sudl
echo "olcAttributeTypes: {9}( 1.3.6.1.4.1.15953.9.1.10 NAME 'sudoOrder' DESC 'an integer to order the sudoRole entries' EQUALITY integerMatch ORDERING integerOrderingMatch SYNTAX 1.3.6.1.4.1.1466.115.121.1.27 )" >> $sudl
echo "olcObjectClasses: {0}( 1.3.6.1.4.1.15953.9.2.1 NAME 'sudoRole' DESC 'Sudoer Entries' SUP top STRUCTURAL MUST cn MAY ( sudoUser \$ sudoHost \$ sudoCommand \$ sudoRunAs \$ sudoRunAsUser \$ sudoRunAsGroup \$ sudoOption \$ sudoOrder \$ sudoNotBefore \$ sudoNotAfter \$ description ) )" >> $sudl

# Write sudoMaster.ldif
touch $sudml
echo "dn: ou=sudoers,dc=$dc1,dc=$dc2" >> $sudml
echo "objectclass: organizationalUnit" >> $sudml
echo "objectclass: top" >> $sudml
echo "ou: sudoers" >> $sudml
echo "" >> $sudml
echo "dn: cn=defaults,ou=sudoers,dc=$dc1,dc=$dc2" >> $sudml
echo "objectClass: top" >> $sudml
echo "objectClass: sudoRole" >> $sudml
echo "cn: defaults" >> $sudml
echo "description: Default sudoOptions go here" >> $sudml
echo "sudoOption: env_reset" >> $sudml
echo "sudoOption: mail_badpass" >> $sudml
echo "sudoOrder: 1" >> $sudml
echo "" >> $sudml
echo "dn: cn=root,ou=sudoers,dc=$dc1,dc=$dc2" >> $sudml
echo "objectClass: top" >> $sudml
echo "objectClass: sudoRole" >> $sudml
echo "cn: root" >> $sudml
echo "sudoUser: root" >> $sudml
echo "sudoHost: ALL" >> $sudml
echo "sudoRunAsUser: ALL" >> $sudml
echo "sudoRunAsGroup: ALL" >> $sudml
echo "sudoCommand: ALL" >> $sudml
echo "sudoOrder: 2" >> $sudml
echo "" >> $sudml
echo "dn: cn=%admin,ou=sudoers,dc=$dc1,dc=$dc2" >> $sudml
echo "objectClass: top" >> $sudml
echo "objectClass: sudoRole" >> $sudml
echo "cn: %admin" >> $sudml
echo "sudoUser: %admin" >> $sudml
echo "sudoHost: ALL" >> $sudml
echo "sudoRunAsUser: ALL" >> $sudml
echo "sudoCommand: ALL" >> $sudml
echo "sudoOrder: 3" >> $sudml
echo "" >> $sudml
echo "dn: cn=%sudo,ou=sudoers,dc=$dc1,dc=$dc2" >> $sudml
echo "objectClass: top" >> $sudml
echo "objectClass: sudoRole" >> $sudml
echo "cn: %sudo" >> $sudml
echo "sudoUser: %sudo" >> $sudml
echo "sudoHost: ALL" >> $sudml
echo "sudoRunAsUser: ALL" >> $sudml
echo "sudoRunAsGroup: ALL" >> $sudml
echo "sudoCommand: ALL" >> $sudml
echo "sudoOrder: 4" >> $sudml
echo "" >> $sudml
echo "dn: cn=%$admins,ou=sudoers,dc=$dc1,dc=$dc2" >> $sudml
echo "objectClass: top" >> $sudml
echo "objectClass: sudoRole" >> $sudml
echo "cn: %$admins" >> $sudml
echo "sudoUser: %$admins" >> $sudml
echo "sudoHost: ALL" >> $sudml
echo "sudoRunAsUser: ALL" >> $sudml
echo "sudoRunAsGroup: ALL" >> $sudml
echo "sudoCommand: ALL" >> $sudml
echo "sudoOrder: 5" >> $sudml

# Add the structure file to LDAP
ldapadd -x -D cn=$ldadmin,dc=$dc1,dc=$dc2 -W -f $struct
mv $struct $struct.back

# Run the indexing modification
ldapmodify -Q -Y EXTERNAL -H ldapi:/// -f $index
mv $index $index.back

# Run the autofs modification
ldapadd -Y EXTERNAL -H ldapi:/// -f $afsl
mv $afsl $afsl.back

# Run the autmount modification
ldapadd -D cn=$ldadmin,dc=$dc1,dc=$dc2 -W -f $atml
mv $atml $atml.back

# Run the sudo modification
ldapadd -Y EXTERNAL -H ldapi:/// -f $sudl
mv $sudl $sudl.back

# Run the sudoMaster modification
ldapadd -f $sudml -D "cn=$ldadmin,dc=$dc1,dc=$dc2" -W -x
mv $sudml $sudml.back

# Write password file for ldapscripts
touch $passFile
echo -n "$ldapPass" > $passFile

# Rewrite ldapscripts.conf
mv $ldapScrCnf $ldapScrCnf.back.$tmstamp
touch $ldapScrCnf
echo "SERVER=\"ldap://$serverIP\"" >> $ldapScrCnf
echo "SUFFIX=\"dc=$dc1,dc=$dc2\"" >> $ldapScrCnf
echo "GSUFFIX=\"ou=$groupVar\"" >> $ldapScrCnf
echo "USUFFIX=\"ou=$userVar\"" >> $ldapScrCnf
echo "MSUFFIX=\"ou=$machVar\"" >> $ldapScrCnf
echo "SASLAUTH=\"\"" >> $ldapScrCnf
echo "BINDDN=\"cn=$ldadmin,dc=$dc1,dc=$dc2\"" >> $ldapScrCnf
echo "BINDPWDFILE=\"$passFile\"" >> $ldapScrCnf
echo "GIDSTART=\"10000\"" >> $ldapScrCnf
echo "UIDSTART=\"10000\"" >> $ldapScrCnf
echo "MIDSTART=\"20000\"" >> $ldapScrCnf
echo "GCLASS=\"posixGroup\"" >> $ldapScrCnf
echo "CREATEHOMES=\"yes\"" >> $ldapScrCnf
echo "PASSWORDGEN=\"pwgen\"" >> $ldapScrCnf
echo "RECORDPASSWORDS=\"no\"" >> $ldapScrCnf
echo "PASSWORDFILE=\"/var/log/ldapscripts_passwd.log\"" >> $ldapScrCnf
echo "LOGFILE=\"/var/log/ldapscripts.log\"" >> $ldapScrCnf
echo "LDAPSEARCHBIN=\"/usr/bin/ldapsearch\"" >> $ldapScrCnf
echo "LDAPADDBIN=\"/usr/bin/ldapadd\"" >> $ldapScrCnf
echo "LDAPDELETEBIN=\"/usr/bin/ldapdelete\"" >> $ldapScrCnf
echo "LDAPMODIFYBIN=\"/usr/bin/ldapmodify\"" >> $ldapScrCnf
echo "LDAPMODRDNBIN=\"/usr/bin/ldapmodrdn\"" >> $ldapScrCnf
echo "LDAPPASSWDBIN=\"/usr/bin/ldappasswd\"" >> $ldapScrCnf
echo "LDAPSEARCHOPTS=\"-o ldif-wrap=no\"" >> $ldapScrCnf
echo "GETENTPWCMD=\"\"" >> $ldapScrCnf
echo "GETENTGRCMD=\"\"" >> $ldapScrCnf
echo "GTEMPLATE=\"\"" >> $ldapScrCnf
echo "UTEMPLATE=\"\"" >> $ldapScrCnf
echo "MTEMPLATE=\"\"" >> $ldapScrCnf

# Give the new admin groups SUDO access
echo "" >> $sudrs
echo "# Entry to allow LDAP $admins group to have SUDO access:" >> $sudrs
echo "%$admins    ALL=(ALL) ALL" >> $sudrs

# Establish LDAP groups for our users
ldapaddgroup $admins
ldapaddgroup $users

# Store backup files
mkdir ldap_config_backups
chown $admin:$admin *.back
mv *.back ldap_config_backups/
chown $admin:$admin ldap_config_backups

# Install Kerberos
aptitude install krb5-kdc krb5-admin-server -y
krb5_newrealm

# Create a Kerberos administrative user
kadmin.local -q "addprinc $krbadmin/admin"

# Modify the Kerberos ACL 
mv $k5acl $k5acl.back.$tmstamp
touch $k5acl
echo "# This file is the access control list for krb5 administration." >> $k5acl
echo "# To enable adminstration rights to any principle ending in /admin," >> $k5acl
echo "# ensure the following line is uncommented:" >> $k5acl
echo "*/admin *" >> $k5acl

# Modify krb5.conf
mv $k5conf $k5conf.back.$tmstamp
touch $k5conf
echo "[libdefaults]" >> $k5conf
echo "    default_realm = $newDomUp" >> $k5conf
echo "    krb4_config = /etc/krb.conf" >> $k5conf
echo "    krb4_realms = /etc/krb.realms" >> $k5conf
echo "    kdc_timesync = 1" >> $k5conf
echo "    ccache_type = 4" >> $k5conf
echo "    forwardable = true" >> $k5conf
echo "    proxiable = true" >> $k5conf
echo "    allow_weak_crypto = true" >> $k5conf
echo "    v4_instance_resolve = false" >> $k5conf
echo "    vr_name_convert = {" >> $k5conf
echo "        host = {" >> $k5conf
echo "            rcmd = host" >> $k5conf
echo "            ftp = ftp" >> $k5conf
echo "        }" >> $k5conf
echo "        plain = {" >> $k5conf
echo "            something = something-else" >> $k5conf
echo "        }" >> $k5conf
echo "    }" >> $k5conf
echo "    fcc-mit-ticketflags = true" >> $k5conf
echo "" >> $k5conf
echo "[realms]" >> $k5conf
echo "    $newDomUp = {" >> $k5conf
echo "        kdc = $srvrName.$newDom" >> $k5conf
echo "        admin_server = $srvrName.$newDom" >> $k5conf
echo "        master_kdc = $srvrName.$newDom" >> $k5conf
echo "        default_domain = $newDom" >> $k5conf
echo "    }" >> $k5conf
echo "" >> $k5conf
echo "[domain_realm]" >> $k5conf
echo "" >> $k5conf
echo "[login]" >> $k5conf
echo "    krb4_convert = true" >> $k5conf
echo "    krb4_get_tickets = false" >> $k5conf

# Restart Kerberos to pick up the changes
service krb5-admin-server restart

# Install SSSD
aptitude install -y sssd

# Create the sssd.conf file
touch $sdcnf
echo "[sssd]" >> $sdcnf
echo "config_file_version = 2" >> $sdcnf
echo "reconnection_retries = 3" >> $sdcnf
echo "sbus_timeout = 30" >> $sdcnf
echo "services = nss, pam, sudo" >> $sdcnf
echo "domains = $newDom" >> $sdcnf
echo "" >> $sdcnf
echo "[nss]" >> $sdcnf
echo "filter_groups = root" >> $sdcnf
echo "filter_users = root" >> $sdcnf
echo "reconnection_retries = 3" >> $sdcnf
echo "" >> $sdcnf
echo "[pam]" >> $sdcnf
echo "reconnection_retries = 3" >> $sdcnf
echo "" >> $sdcnf
echo "[domain/$newDom]" >> $sdcnf
echo "; Using enumerate = true leads to high load and slow response" >> $sdcnf
echo "enumerate = false" >> $3sdcnf
echo "cache_credentials = false" >> $sdcnf
echo "" >> $sdcnf
echo "id_provider = ldap" >> $sdcnf
echo "auth_provider = krb5" >> $sdcnf
echo "chpass_provider = krb5" >> $sdcnf
echo "" >> $sdcnf
echo "ldap_uri = ldap://ldap.$newDom" >> $sdcnf
echo "ldap_search = dc=$dc1,dc=$dc2" >> $sdcnf
echo "ldap_sudo_search_base = ou=sudoers,dc=$dc1,dc=$dc2" >> $sdcnf
echo "ldap_tls_reqcert = never" >> $sdcnf
echo "" >> $sdcnf
echo "krb5_kdcip = kerberos.$newDom" >> $sdcnf
echo "krb5_realm = $newDomUp" >> $sdcnf
echo "krb5_changepw_principle = kadmin/changepw" >> $sdcnf
echo "krb5_auth_timeout = 15" >> $sdcnf
echo "krb5_renewable_lifetime = 5d" >> $sdcnf

# ensure proper permissions and start the sssd daemon
chmod 600 $sdcnf
service sssd restart

# Authenticate as the Kerberos administrative user
kinit $krbadmin/admin

# Kerberize ssh
mv $sshFile $sshFile.back.$tmstamp
touch $sshFile
echo "port 22" >> $sshFile
echo "protocol 2" >> $sshFile
echo "HostKey /etc/ssh/ssh_host_rsa_key" >> $sshFile
echo "HostKey /etc/ssh/ssh_host_dsa_key" >> $sshFile
echo "HostKey /etc/ssh/ssh_host_ecdsa_key" >> $sshFile
echo "HostKey /etc/ssh/ssh_host_ed25519_key" >> $sshFile
echo "UsePrivilegeSeparation yes" >> $sshFile
echo "KeyRegenerationInterval 3600" >> $sshFile
echo "ServerKeyBits 1024" >> $sshFile
echo "SyslogFacility AUTH" >> $sshFile
echo "LogLevel INFO" >> $sshFile
echo "LoginGraceTime 30" >> $sshFile
echo "PermitRootLogin no" >> $sshFile
echo "StrictModes yes" >> $sshFile
echo "RSAAuthentication yes" >> $sshFile
echo "PubkeyAuthentication yes" >> $sshFile
echo "IgnoreRhosts yes" >> $sshFile
echo "RhostsRSAAuthentication no" >> $sshFile
echo "HostbasedAuthentication no" >> $sshFile
echo "PermitEmptyPasswords no" >> $sshFile # may not be necessary; need to check
echo "ChallengeResponseAuthentication yes" >> $sshFile
echo "PasswordAuthentication yes" >> $sshFile # may not be necessary; need to check
echo "GSSAPIAuthentication yes" >> $sshFile
echo "GSSAPICleanupCredentials yes" >> $sshFile
echo "X11Forwarding yes" >> $sshFile
echo "X11DisplayOffset 10" >> $sshFile
echo "PrintMotd no" >> $sshFile
echo "PrintLastLog yes" >> $sshFile
echo "TCPKeepAlive yes" >> $sshFile
echo "AcceptEnv LANG LC_*" >> $sshFile
echo "Subsystem sftp /usr/lib/openssh/sftp-server" >> $sshFile
echo "UsePAM yes" >> $sshFile

# Create kerberos principle for SSH service
kadmin.local -q "addprinc -randkey host/$srvrName.$newDom"
kadmin.local -q "ktadd host/$srvrName.$newDom"

# install NFSv4
aptitude install -y nfs-kernel-server nfs-common

# make required directories
mkdir /export
mkdir /export/home

# Add shared directory to fstab
sudo cp $fstb $fstb.back.$tmstamp
echo "/home    /export/home    none    bind    0    0" >> $fstb

# configure exports file
sudo cp $xprts $xprts.back.$tmstamp
echo "/export *(rw,fsid=0,crossmnt,insecure,async,no_subtree_check,sec=krb5p:krb5i:krb5)" >> $xprts
echo "/export/home *(rw,insecure,async,no_subtree_check,sec=krb5p:krb5i:krb5)" >> $xprts

# tell NFS to use Kerberos
mv $nfscmn $nfscmn.back.$tmstamp
touch $nfscmn
echo "NEED_STATD=" >> $nfscmn
echo "STATDOPTS=" >> $nfscmn
echo "NEED_GSSD=yes" >> $nfscmn

# adjust settings in nfs-kernel-server
mv $nksrv $nksrv.back.$tmstamp
touch $nksrv
echo "RPCNFSDCOUNT=8" >> $nksrv
echo "RPCNFSDPRIORITY=0" >> $nksrv
echo "RPCMOUNTDOPTS=\"--manage-gids\"" >> $nksrv
echo "NEED_SVCGSSD=\"yes\"" >> $nksrv
echo "RPCSVCGSSDOPTS=\"\"" >> $nksrv
echo "RPCNFSDOPTS=\"\"" >> $nksrv

# Add domain to idmapd.conf
mv $idmpd $idmpd.back.$tmstamp
touch $idmpd
echo "[General]" >> $idmpd
echo "" >> $idmpd
echo "Verbosity = 0" >> $idmpd
echo "Pipefs-Directory = /var/lib/nfs/rpc_pipefs" >> $idmpd
echo "Domain = $newDom" >> $idmpd
echo "" >> $idmpd
echo "[Mapping]" >> $idmpd
echo "" >> $idmpd
echo "Nobody-User = nobody" >> $idmpd
echo "Nobody-Group = nogroup" >> $idmpd

# Create Kerberos principles for NFS Server
kadmin.local -q "addprinc -randkey nfs/$srvrName.$newDom"
kadmin.local -q "ktadd nfs/$srvrName.$newDom"

# Restart NFS
service nfs-kernel-server restart
```

---

### Post by matt_fussell2 on 2014-12-16
Well, it only took two days of testing to work out the details, but the scripts work 99% as one would expect, and that last 1% is a matter of a bit of patience and a reboot as testing proved. The keys to proper setup are as follows:
[LIST]
[*]when configuring libnss-ldapd, you **must** select **group**, **passwd**, and **shadow** for name services to configure; the rest of the defaults that get picked up should be correct 
[*]when configuring kerberos, the default realm should be picked up correctly, but you will still be prompted for the default kerberos server; you'll need to put in **[servername].[example].[com]**. What had been continually failing during testing for the past two days was that I had been putting in kerberos.example.com; this misconfiguration results in the shared home directories failing to mount when secured by kerberos. 
[/LIST]

The 99% functionality is when you first log in as a new user on the client machine - it seems as though the login has failed, but then the mouse pointer showed back up onscreen. Rebooting the client machine from a virtual terminal after the mouse re-appeared and logging in again (which took a minute or two [testing on old gear]), everything worked. I'll plan on working to figure out this issue after Christmas.

---

