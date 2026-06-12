---
title: "Caught the Server-Hell blues..."
date: 2009-06-12
forum: Server Platforms
---

### Post by SirrKitt on 2009-06-12
Well, here's the problem: at my school, the networking part of our Computer Science department is switching to a Linux only setup, running primarily KUbuntu and Ubuntu. In the back of the room, we have an older Dell that we've managed to revive (seems someone turned off raid in BIOS and so that was Hell to try and partition because it had an LVM on top of it, but thankfully turning raid back on and redoing the raid helped) and we're running a RAID 5 setup with 4 hard drives with about ~20GBs on each. I'll probably add a few more drives to the array, and then a few extra drives on top of that. Anyways, the problem we've been having is that we're trying to setup an Ubuntu mirror (for most of the core programs, updates, security stuff, etc.) and Apt-Mirror tends to like to fail. Not positive if the update will occur any more since I've purged and cleaned the conf file a few times. (We're running Debian Lenny/Sid on the server by the way) But, now, the main few problems I'm really having, is I'm having trouble getting LDAP to work. We're trying to setup a central domain-like login system so that all the other students (not having the admin password) can login to the computers from any other computer and still retain their home folders and most of their settings. I've tried setting up LDAP but I'm kind of going at it blind, though the server is up and running. I'm not quite positive on how to add extra users to the database, and it seems like a hell trying to get any of the computers to connect to the server and use the LDAP. I've installed KDE and Gnome on the server (so I could migrate the groups and passwd settings) and ran migrate_group and the migrate_passwd and imported those into LDAP. I've got the group and people containers setup, but I'm still not even positive on what I'm doing , as most of the guides seem a little too copy + paste, or no-english, techie-only speak. I'm kind of a newb with this stuff, but I am a bit familiar with Linux. I'd switch the server to an Ubuntu, though, I don't understand AT ALL using Slapd with Ubuntu, so I've stuck to the older Debian version of Slapd. I was also wondering, if I want the hosts all to be known by all computers, would I put that in DNS if I didn't want to manually edit that on all computers. Also, I've KIND of setup an Ubuntu machine to authenticate to the LDAP, but then it went into the problem of not finding the homes and all that junk. Any help would be appreciated. I'll post my slapd.conf and ldap.conf


ldap.conf
```

BASE    dc=techat231,dc=com
#URI    ldap://192.168.1.4/
URI     ldap://localhost/
TLS_REQCERT allow

```
slapd.conf
```

#                                                                
# LDAP Defaults                                                  
#                                                                

# See ldap.conf(5) for details
# This file should be world readable but not world writable.

BASE    dc=techat231,dc=com
#URI    ldap://192.168.1.4/
URI     ldap://localhost/  
TLS_REQCERT allow          
#SIZELIMIT      12         
#TIMELIMIT      15         
#DEREF          never      
Reams-Server:~# cat /etc/ldap/slapd.conf 
# This is the main slapd configuration file. See slapd.conf(5) for more
# info on the configuration options.                                   

#######################################################################
# Global Directives:                                                   

# Features to permit
#allow bind_v2      

# Schema and objectClass definitions
include         /etc/ldap/schema/core.schema
include         /etc/ldap/schema/cosine.schema
include         /etc/ldap/schema/nis.schema   
include         /etc/ldap/schema/inetorgperson.schema

# Where the pid file is put. The init.d script
# will not stop the server if you change this.
pidfile         /var/run/slapd/slapd.pid      

# List of arguments that were passed to the server
argsfile        /var/run/slapd/slapd.args         

# Read slapd.conf(5) for possible values
loglevel        none                    

# Where the dynamically loaded modules are stored
modulepath      /usr/lib/ldap                    
moduleload      back_hdb                         

# The maximum number of entries that is returned for a search operation
sizelimit 500                                                          

# The tool-threads parameter sets the actual amount of cpu's that is used
# for indexing.                                                          
tool-threads 1                                                           

#######################################################################
# Specific Backend Directives for hdb:                                 
# Backend specific directives apply to this backend until another      
# 'backend' directive occurs                                           
backend         hdb                                                    

#######################################################################
# Specific Backend Directives for 'other':                             
# Backend specific directives apply to this backend until another      
# 'backend' directive occurs                                           
#backend                <other>                                        

#######################################################################
# Specific Directives for database #1, of type hdb:                    
# Database specific directives apply to this databasse until another   
# 'database' directive occurs                                          
database        hdb                                                    

# The base of your directory in database #1
suffix          "dc=techat231,dc=com"      

# rootdn directive for specifying a superuser on the database. This is needed
# for syncrepl.                                                              
rootdn "cn=admin,dc=techat231,dc=com"  
rootpw (omitted)                           

directory       "/var/lib/ldap"                                

                                      
dbconfig set_cachesize 0 2097152 0                                       
                                                       

# Number of objects that can be locked at the same time.
dbconfig set_lk_max_objects 1500                        
# Number of locks (both requested and granted)          
dbconfig set_lk_max_locks 1500                          
# Number of lockers                                     
dbconfig set_lk_max_lockers 1500                        

# Indexing options for database #1
index           objectClass eq    
lastmod         on                                           
                             
checkpoint      512 30                                             

            
  
access to attrs=userPassword,shadowLastChange      
        by dn="cn=admin,dc=techat231,dc=com" write 
        by anonymous auth
        by self write
        by * none


access to dn.base="" by * read
access to *
        by dn="cn=admin,dc=techat231,dc=com" write
        by * read

```

Any suggestions for this environment would be appreciated too.
If I could get help with using Ubuntu's LDAP and if I could get it working, I'd gladly switch to Ubuntu.

---

