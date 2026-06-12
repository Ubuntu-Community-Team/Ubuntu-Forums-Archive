---
title: "Samba and openldap"
date: 2010-05-01
forum: Server Platforms
---

### Post by pleegor on 2010-05-01
Hi everybody I am a newbie in everything that is related to samba and ldap. I need to configure Samba to use open ldap as authentication instance. I found out some tutorials that explain how to do that. For last couple of days I am trying to resolve this issue:
  
[B]dewey@ubuntuServer:~$ sudo ldapmodify -x -D cn=admin,cn=config -W -f /home/dewey/Documents/samba_indexes_uid.ldif
Enter LDAP Password:                                                                                                                           
modifying entry "olcDatabase={1}hdb,cn=config"                                                                                                 

dewey@ubuntuServer:~$ ldapsearch -xLLL -D cn=admin,cn=config -x -b cn=config -W olcDatabase={1}hdb                                             
Enter LDAP Password:                                                                                                                           
dn: olcDatabase={1}hdb,cn=config                                                                                                               
objectClass: olcDatabaseConfig                                                                                                                 
objectClass: olcHdbConfig                                                                                                                      
olcDatabase: {1}hdb                                                                                                                            
olcDbDirectory: /var/lib/ldap                                                                                                                  
olcSuffix: dc=home,dc=com                                                                                                                      
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=home,d                                                                 
 c=com" write by anonymous auth by self write by * none                                                                                        
olcAccess: {1}to dn.base="" by * read                                                                                                          
olcAccess: {2}to * by dn="cn=admin,dc=home,dc=com" write by * read                                                                             
olcLastMod: TRUE                                                                                                                               
olcRootDN: cn=admin,dc=home,dc=com                                                                                                             
olcRootPW: 1234                                                                                                                                
olcDbCheckpoint: 512 30                                                                                                                        
olcDbConfig: {0}set_cachesize 0 2097152 0                                                                                                      
olcDbConfig: {1}set_lk_max_objects 1500                                                                                                        
olcDbConfig: {2}set_lk_max_locks 1500                                                                                                          
olcDbConfig: {3}set_lk_max_lockers 1500                                                                                                        
olcDbIndex: uid eq,pres,sub                                                                                                                    

dewey@ubuntuServer:~$ sudo ldapmodify -x -D cn=admin,cn=config -W -f /home/dewey/Documents/samba_indexes.ldif
Enter LDAP Password:                                                                                         
modifying entry "olcDatabase={1}hdb,cn=config"                                                               

dewey@ubuntuServer:~$ ldapsearch -xLLL -D cn=admin,cn=config -x -b cn=config -W olcDatabase={1}hdb
Enter LDAP Password:                                                                              
dn: olcDatabase={1}hdb,cn=config                                                                  
objectClass: olcDatabaseConfig                                                                    
objectClass: olcHdbConfig                                                                         
olcDatabase: {1}hdb                                                                               
olcDbDirectory: /var/lib/ldap
olcSuffix: dc=home,dc=com
olcAccess: {0}to attrs=userPassword,shadowLastChange by dn="cn=admin,dc=home,d
 c=com" write by anonymous auth by self write by * none
olcAccess: {1}to dn.base="" by * read
olcAccess: {2}to * by dn="cn=admin,dc=home,dc=com" write by * read
olcLastMod: TRUE
olcRootDN: cn=admin,dc=home,dc=com
olcRootPW: 1234
olcDbCheckpoint: 512 30
olcDbConfig: {0}set_cachesize 0 2097152 0
olcDbConfig: {1}set_lk_max_objects 1500
olcDbConfig: {2}set_lk_max_locks 1500
olcDbConfig: {3}set_lk_max_lockers 1500
olcDbIndex: uid eq,pres,sub
olcDbIndex: uidNumber eq
olcDbIndex: gidNumber eq
olcDbIndex: loginShell eq
olcDbIndex: memberUid eq,pres,sub
olcDbIndex: uniqueMember eq,pres
olcDbIndex: sambaSID eq
olcDbIndex: sambaPrimaryGroupSID eq
olcDbIndex: sambaGroupType eq
olcDbIndex: sambaSIDList eq
olcDbIndex: sambaDomainName eq
olcDbIndex: default sub

dewey@ubuntuServer:~$ sudo gzip -d /usr/share/doc/smbldap-tools/configure.pl.gz
dewey@ubuntuServer:~$ sudo perl /usr/share/doc/smbldap-tools/configure.pl
$# is no longer supported at /usr/share/doc/smbldap-tools/configure.pl line 314.
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
       smbldap-tools script configuration
       -=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
Before starting, check
 . if your samba controller is up and running.
 . if the domain SID is defined (you can get it with the 'net getlocalsid')

 . you can leave the configuration using the Crtl-c key combination
 . empty value can be set with the "." character
-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-
Looking for configuration files...

Samba Configuration File Path [/etc/samba/smb.conf] >[/B]                                                                                                                                                     

  
If possible can somebody provide an easy to understand tutorial that might help he?

Thank you !!!!

---

