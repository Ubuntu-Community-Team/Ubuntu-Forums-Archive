---
title: "Squid, locking some users to single IP."
date: 2012-10-05
forum: Server Platforms
---

### Post by Demented ZA on 2012-10-05
I have squid running as a non-trasnparent proxy on a server running IP tables. 

My Squid users should comprise of the following:
Normal users, call them Staff.
Lets say I have a group of 5 people, and call them Managers.

Of the above, Staff already has internet access via the squid proxy, regardless of what machine they are connecting from. This works as it should.

I need to add Managers as an additional list of users. Managers may only access the internet when connecting from the computer 10.10.10.109.

I also now need to block staff from connecting from the PC 10.10.10.109.

I have tried creating acl's in squid for the above, to no avail.

All my users (Staff and Managers) are defined under ncsa_users. I then have an additional acl that consists of the usernames of the managers as they appear under ncsa_users. I then use this acl to create a rule to block/allow them. I'm obviously doing it wrong or else it would be working.

My squid config file:
```
########################################### Squid Settings #############################################################
coredump_dir /var/spool/squid
hosts_file /etc/hosts
http_port 8080

########################################### Squid Authentication settings #########################################
auth_param basic program /usr/lib/squid/ncsa_auth /etc/squid/passwd
auth_param basic children 5
auth_param basic realm Company Server Proxy
auth_param basic credentialsttl 2 hour
auth_param basic casesensitive off

######################################### Access Control Lists #########################################################
acl all src all
acl manager proto cache_object
acl localhost src 127.0.0.1/32
acl CONNECT method CONNECT
acl SSL method CONNECT

###### Authentication ########
acl ncsa_users proxy_auth REQUIRED

###### Network ###############
acl SSL_ports port 443

###### SSL Ports #############
acl SSL_ports port 563 # https
acl SSL_ports port 873 # snews
acl Safe_ports port 80 # rsync

##### Safe Ports #############
acl Safe_ports port 21 # http
acl Safe_ports port 443 # ftp
acl Safe_ports port 70 # https
acl Safe_ports port 210 # gopher
acl Safe_ports port 1025-65535 # wais
acl Safe_ports port 280 # unregistered ports
acl Safe_ports port 488 # http-mgmt
acl Safe_ports port 591 # gss-http
acl Safe_ports port 777 # filemaker
acl Safe_ports port 631 # multiling http
acl Safe_ports port 873 # cups
acl Safe_ports port 901 # rsync
acl ManagersPC src 10.10.10.109
acl Managers proxy_auth "/etc/squid/managers.acl"

###################################### Access Control Rules ##########################################################
http_access allow ManagersPC Managers
http_access deny ncsa_users ManagersPC
http_access allow ncsa_users
http_access allow SSL_ports
http_access allow Safe_ports
http_access deny !Safe_ports
http_access deny CONNECT !SSL_ports
http_access deny all

cache_mgr root@domain.com
hierarchy_stoplist trusteer
```How should I go about this?

---

### Post by Demented ZA on 2012-10-23
I solved my own problem. The solution pertains partly to a problem in another post of mine found [here]("http://ubuntuforums.org/showthread.php?t=2063087").

Lets say I have the following users set up under ncsa-auth:
Mark
Phill
Bob
Sarah
Naomi
John
Bill
Melany

Of these users, I need to set up groups, as 3 of the above users are Managers, and the others are staff.

 In my squid config, I defined the groups as:

```
acl Staff proxy_auth_regex -i Mark Phill Bob Sarah Naomi
acl Managers proxy_auth_regex -i John Bill Melany
```In order to lock Managers to a single IP/Machine, I have to tell squid what machine first. Again, an ACL definition:
```
acl ManagerPC src 10.10.10.109
```This can also seemingly be done by mac address, although I have yet to try it.
I also had to define the rest of the network, in other words the whole subnet, except 10.10.10.109:
```
acl Staff_pcs src "/etc/squid/user_pcs.acl"
```The above file, contains a linear range of IP's from 10.10.10.1 to 10.10.10.254, one entry per line. I just removed the line with the IP 10.10.10.109. Read Below for more information on generating this file.

Now all that was left was to Allow staff to use all PC's except the managers-pc, and to allow managers to use the managers-pc and be denied access on any other pc:

```

http_reply_access deny ManagerPC Staff
#http_reply_access deny Staff_pcs Managers #commented. was creating issues.
http_access deny ManagerPC Staff
http_access deny Staff_pcs Managers

# Regular ncsa_users allow rule
http_access allow ncsa_users
...
http_access deny all
```And there we have it. Managers are locked down to the managers PC.

As for the generation of the Staf_pcs file:
I needed to list the entire network, and omit 10.10.10.109.
Writing the file in the following didn't work:
```
10.10.10.1/24 !10.10.10.109
```I haven't tried the below yet.
```
10.10.10.1-10.10.10.108
10.10.10.110-10.10.10.254
```I needed to define it in a way that I'm sure of, as I had little time and needed to produce results. Hence I wrote a small perl script that generates a range of ip's:

contents of ips.pl
```
#!/bin/bash
for i in {1..254}
do
   echo "10.10.10.$i"
done
```and then piped the output to a file that squid could use:
```
sudo perl ips.pl >> Staff_pcs 
```I then opened up the file in nano and deleted the line containing 10.10.10.109, saved it and moved to the squid directory.

I know this is not the most graceful way, but as I said, I was pressed for time, and needed a file that would get the job done. 


I'll clean up my solution and try a more efficient approach, but for the time being I documented this here for thers to use, since I found nothing of the sort on the internet.

---

