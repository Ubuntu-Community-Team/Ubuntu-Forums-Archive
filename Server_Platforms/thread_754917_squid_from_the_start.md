---
title: "squid from the start"
date: 2008-04-14
forum: Server Platforms
---

### Post by insurin on 2008-04-14
hello
I want to setup squid to cache traffic and log internet usage. So far  I have installed squid (apt-get install squid) and changed a few lines in squid.conf to get me up and running. I can browse the web through squid.

My network is active directory based. I am using ubuntu server 7.10. I want to be able to log internet activity by active directory usernames and maybe PC name if possible. I have read loads so far but I am struggling. 
At the moment I am just seeing if I can communicate with my ldap server from ubuntu via ldap_auth, i.e.

ldap_auth -b "DC=mydomain,DC=com" -D CN=administrator,CN=Users,DC=mydomain,DC=com -w password -f "uid=%s" -h ip_address
 when I hit enter, the command just hangs there and I get no response

so before I move on, I need to get this bit working as I will need to to work from within squid.conf.

any ideas?

---

### Post by ikonia on 2008-04-14
looks like your machine can't communicate with your ad server

try running basic ldap queires against it first before moving onto more complex auth solutions.

---

### Post by insurin on 2008-04-14
I can ping ldap IP from ubuntu and ldap is defo working as its serving live, also from a Windows box I have softerra ldap browser connected.

---

### Post by ikonia on 2008-04-14
so your already authenticating your ubuntu users against AD sucessfully in this environment ?

---

### Post by insurin on 2008-04-14
no sorry, It's all Microsoft based, I have just installed ubuntu to see if I can get squid up and running. All I have done so far is install squid, got it working at a basic level. I set the ip of squid server in a workstation pc and managed to browse the web though squid, I seen logs in squid. Now I want the logs in squid to refer to AD usernames. So to start with, I thought I would see if I could talk to ldap server as suggested 

(Make sure squid can talk to LDAP server

Before configuring makes sure that the squid is working with LDAP auth. Type the following command:

"# /usr/lib/squid/squid_ldap_auth -b "dc=nixcraft,dc=com" -f "uid=%s" ldap.nixcraft.com")  

As I have not been able to communicate I have not got passed this bit.

---

### Post by ikonia on 2008-04-14
right - so as I said,

use the ubuntu box to do some queries against the AD, 

make sure it's communiting ok at a basic level before progressing on to try to get auth situations working.

---

### Post by insurin on 2008-04-14
can you give me an example of auth situations, not done much with linux to windows communication, or basic level communication rather

---

### Post by insurin on 2008-04-14
I have tried 'netcat ip_of_ldap_server 389 and it hangs.

be back in the morning anyway, in a bit

---

### Post by ikonia on 2008-04-14
I don't understand why you do everything EXCEPT try a simple ldap query against the AD.

I've seen setups that won't let you query the AD unless your a member, others that are wide open, running ldap queries will give you a better idea rather than trying other things.

---

### Post by insurin on 2008-04-15
Right then, I have installed ldap tools and had success with ldapsearch.  I have pulled info about a user so I can confirm that a can communicate with AD from ubuntu.

now I need to get communication working from 'ldap-auth' as I have not had any sucess with this so far. 
to start with, just to get the program working, I have to type the full path in to get ldap_auth working, i.e. even if my current working directory is /usr/lib/squid (where ldap_auth resides), I stilll have to type /usr/lib/squid/ldap_auth <parameters> otherwise I get command not found. 

I must be typing in the wrong command as it just hangs upon hitting enter

---

### Post by insurin on 2008-04-15
lets say as an example

username = administrator
sits in the default contatiner of 'users' within AD
AD server = 192.168.1.1
domain = mycompany.co.uk

I run the followng

./ldap_auth -b dc=mycompany,dc=co,dc=uk -D cn=administrator,cn=users,dc=mycompany,dc=co,dc=uk -w adminpassword -H ldap://192.168.1.1 -f sAMAccountName=administrator
 
I have tried other variants after -f switch, i.e. uid=%s etc

---

### Post by insurin on 2008-04-16
can anyone help with this, 

I just want to setup a squid proxy server that can log active directory usernames, if there are other ways to achieve this then suggest.

---

