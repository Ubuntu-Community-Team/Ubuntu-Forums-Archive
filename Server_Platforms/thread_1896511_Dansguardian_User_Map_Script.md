---
title: "Dansguardian User Map Script"
date: 2011-12-17
forum: Server Platforms
---

### Post by kurtisp on 2011-12-17
Hi,I have just setup a Squid & Dansguardian server and successfully joined a Server 2003 domain and all is fine. However I cannot get the Usermap script ([http://dansguardian.org/downloads/agawronski/usermap2](http://dansguardian.org/downloads/agawronski/usermap2)) to work. I have filled in the varibles at the top of the script but when i run it with the "sudo bash usermap2" it does not run, i get a load of syntax errors:

usermap2: line16: $'\r' : command not found
usermap2: line23: $'\r' : command not found
usermap2: line31: $'\r' : command not found
usermap2: line64: syntax error near unexpected token `$#{\r''
'sermap2: line64: `{


etc...

The varibles that i have entered into the script are:


# First define some variables (You may need to adjust these to match your context.)...
uinfo="-U=administrator%MYPASSWORD";                           # User account that has access to query directory
sinfo="-S=192.168.1.2";                                   # Server to connect to
pwdfile="";                                             # Initialize password file path/name
domain="HOMENET";                                      # domain name prefix in front of username (leave off .local)
dgrestart=0;                                            # Initialize restart variable to 0 (No restart)
dggroupfile="/etc/dansguardian/lists/filtergroupslist"; # Path/name of filtergroupslist file
dgtempfile="/tmp/dgtempfile";                           # Path/name of a temporary file

# Declare array with all security groups you want queried. Add as many as you want.
group=( 'iNetFull' 'iNetLimited' 'iNetBanned' 'iNetStandard' )

# Declare array with all corresponding Dansguardian filter groups. NOTE: Must have the same number of elements as the security group array above. 
dggroup=( 'filter1' 'filter2' 'filter3' 'filter4' )

---

### Post by nothingspecial on 2011-12-17
Moved to Server Platforms.

---

### Post by kurtisp on 2011-12-18
I've sorted it now. Had to convert the file to dos to unix

> **kurtisp said:**
> Hi,I have just setup a Squid & Dansguardian server and successfully joined a Server 2003 domain and all is fine. However I cannot get the Usermap script ([http://dansguardian.org/downloads/agawronski/usermap2](http://dansguardian.org/downloads/agawronski/usermap2)) to work. I have filled in the varibles at the top of the script but when i run it with the "sudo bash usermap2" it does not run, i get a load of syntax errors:

usermap2: line16: $'\r' : command not found
usermap2: line23: $'\r' : command not found
usermap2: line31: $'\r' : command not found
usermap2: line64: syntax error near unexpected token `$#{\r''
'sermap2: line64: `{


etc...

The varibles that i have entered into the script are:


# First define some variables (You may need to adjust these to match your context.)...
uinfo="-U=administrator%MYPASSWORD";                           # User account that has access to query directory
sinfo="-S=192.168.1.2";                                   # Server to connect to
pwdfile="";                                             # Initialize password file path/name
domain="HOMENET";                                      # domain name prefix in front of username (leave off .local)
dgrestart=0;                                            # Initialize restart variable to 0 (No restart)
dggroupfile="/etc/dansguardian/lists/filtergroupslist"; # Path/name of filtergroupslist file
dgtempfile="/tmp/dgtempfile";                           # Path/name of a temporary file

# Declare array with all security groups you want queried. Add as many as you want.
group=( 'iNetFull' 'iNetLimited' 'iNetBanned' 'iNetStandard' )

# Declare array with all corresponding Dansguardian filter groups. NOTE: Must have the same number of elements as the security group array above. 
dggroup=( 'filter1' 'filter2' 'filter3' 'filter4' )

---

