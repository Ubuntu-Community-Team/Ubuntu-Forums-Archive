---
title: "Need help for adding userss and groups in Openldap server."
date: 2012-10-23
forum: Server Platforms
---

### Post by honey_bee on 2012-10-23
hi,
 
I am using ubuntu to configure my openldap server.Every thing is going ok .The problem which I am facing is how to add users and group in my ldap server.
 
1- My slapd.conf is 
 
database bdb 
 
suffix "dc=test,dc=local" 
 
rootdn "cn=Manager,dc=test,dc=local" 
 
rootpw 123 
 
 
 
2- Now I start my LDAP service 
 
[COLOR=magenta]service ldap start [/COLOR]
 
Checking configuration files for slapd: bdb_db_open: Warning - No DB_CONFIG file found in directory 
 
Expect poor performance for suffix dc=test,dc=local. 
 
config file testing succeeded 
 
[ OK ] 
 
Starting slapd: [ OK 
 
3- Now I perform search
 
[COLOR=magenta]ldapsearch -x -b "dc=test,dc=local" "(objectclass=*)"[/COLOR] 
 
 
 
# extended LDIF 
 
# 
 
# LDAPv3 
 
# base <dc=test,dc=local> with scope subtree 
 
# filter: (objectclass=*) 
 
# requesting: ALL 
 
# 
 
 
 
# search result 
 
search: 2 
 
result: 32 No such object 
 
 
 
# numResponses: 1 
 
 
 
4- I create a ldif file inside /etc/openldap folder 
 
[COLOR=magenta]vim base.ldif[/COLOR] 
 
 
 
# base.ldif 
 
 
# Build the root node 
 
dn: dc=test,dc=local 
 
dc: test 
 
objectClass: top 
 
objectClass: domain 
 
 
 
 
 
5- Now I create add two OUs following is my file inside in /etc/openldap/
 
[COLOR=magenta]vim Add_2_OUs.ldif [/COLOR]
 
 
 
# To add two OUs i.e Sales and Marketing 
 
dn: ou=Sales,dc=test,dc=local 
 
ou: Sales 
 
objectClass: organizationalUnit 
 
 
 
dn: ou=Marketing,dc=test,dc=local 
 
ou: Marketing 
 
objectClass: organizationalUnit 
 
 
 
6-Using ldapadd command to add OUs 
 
[COLOR=magenta]ldapadd -D "cn=Manager,dc=test,dc=local" -W -x -f Add_2_OUs.ldif[/COLOR]
[COLOR=magenta]Enter LDAP Password: [/COLOR]
adding new entry "ou=Sales,dc=test,dc=local"
 
adding new entry "ou=Marketing,dc=test,dc=local"
 
 
7- Now I perform search 
 
[COLOR=magenta]ldapsearch -x -b "dc=test,dc=local" "(objectclass=*)"[/COLOR] 
 
 
 
# extended LDIF 
 
# 
 
# LDAPv3 
 
# base <dc=test,dc=local> with scope subtree 
 
# filter: (objectclass=*) 
 
# requesting: ALL 
 
# 
 
 
 
# test.local 
 
dn: dc=test,dc=local 
 
dc: test 
 
objectClass: top 
 
objectClass: domain 
 
 
 
# Sales, test.local 
 
dn: ou=Sales,dc=test,dc=local 
 
ou: Sales 
 
objectClass: organizationalUnit 
 
 
 
# Marketing, test.local 
 
dn: ou=Marketing,dc=test,dc=local 
 
ou: Marketing 
 
objectClass: organizationalUnit 
 
 
 
# search result 
 
search: 2 
 
result: 0 Success 
 
 
 
# numResponses: 4 
 
# numEntries: 3 
 
 
 
 
 
If you think that there is some technical or logical mistake please guide me so I may improve it more. 
 
Also please guide me that How can I add groups and users in my ldap server ? 
 
 
Thanks, 
honey

---

