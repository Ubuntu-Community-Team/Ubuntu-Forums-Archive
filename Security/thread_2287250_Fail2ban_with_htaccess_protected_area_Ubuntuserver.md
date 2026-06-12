---
title: "Fail2ban with htaccess protected area Ubuntuserver 14.04 failing 2 ban"
date: 2015-07-18
forum: Security
---

### Post by richard93 on 2015-07-18
This is me asking fail2ban what its looking for:
 
 
 ```
root@----:/etc/fail2ban/action.d# fail2ban-client status
 Status
 |- Number of jail:    2
 `- Jail list:        apache, ssh
 

``` 
 
 *****************
 
 ```

 
 root@----:/etc/fail2ban/action.d# fail2ban-client status apache
 Status for the jail: apache
 |- filter
 |  |- File list:    /var/log/apache2/error.log 
 |  |- Currently failed:    0
 |  `- Total failed:    0
 `- action
    |- Currently banned:    0
    |  `- IP list:    
    `- Total banned:    0
 
 
 

``` 
 
 
 
 
 
 ***************************
 
 
 
 
 Here are the errors in /var/log/apache2/error.log:
 ```

 
 [Fri Jul 17 00:16:23.974669  2015] [mpm_prefork:notice] [pid 13614] AH00163: Apache/2.4.7 (Ubuntu)  PHP/5.5.9-1ubuntu4.11 configured -- resuming normal operations
 [Fri Jul 17 00:16:23.974765 2015] [core:notice] [pid 13614] AH00094: Command line: '/usr/sbin/apache2'
 [Fri Jul 17 00:26:16.124260 2015] [mpm_prefork:notice] [pid 13614] AH00169: caught SIGTERM, shutting down
 [Fri Jul 17 00:26:17.219580 2015] [mpm_prefork:notice] [pid 13718]  AH00163: Apache/2.4.7 (Ubuntu) PHP/5.5.9-1ubuntu4.11 configured --  resuming normal operations
 [Fri Jul 17 00:26:17.219725 2015] [core:notice] [pid 13718] AH00094: Command line: '/usr/sbin/apache2'
 [Fri Jul 17 00:27:30.695823 2015] [auth_basic:error] [pid 13725] [client xx.x.xx.xx:45367] AH01617: user jason: authentication failure for  "/protect/": Password Mismatch
 [Fri Jul 17 00:27:34.436083 2015] [auth_basic:error] [pid 13725] [client [COLOR=black]xx.x.xx.xx[/COLOR]:45367] AH01617: user jason: authentication failure for  "/protect/": Password Mismatch
 [Fri Jul 17 00:27:36.958196 2015] [auth_basic:error] [pid 13725] [client [COLOR=black]xx.x.xx.xx[/COLOR]:45367] AH01617: user jason: authentication failure for  "/protect/": Password Mismatch
 [Fri Jul 17 00:27:40.002723 2015] [auth_basic:error] [pid 13725] [client [COLOR=black]xx.x.xx.xx[/COLOR]:45367] AH01617: user jason: authentication failure for  "/protect/": Password Mismatch
 
 
 

``` ***********************************
 
 
 So the log files show a Password Mismatch, but not banning a damn thing.
 
 
 apache-auth has it built in to look for "Password Mismatch" :
 This is the apache-auth.conf file:
 
 
 
 
 ```

 
 
 
 # Fail2Ban apache-auth filter
 #
 
 [INCLUDES]
 
 # Read common prefixes. If any customizations available -- read them from
 # apache-common.local
 before = apache-common.conf
 
 [Definition]
 
 
 failregex = ^%(_apache_error_client)s (AH01797: )?client denied by server configuration: (uri )?\S*\s*$
             ^%(_apache_error_client)s (AH01617: )?user .* authentication failure for "\S*": Password Mismatch$
             ^%(_apache_error_client)s (AH01618: )?user .* not found(: )?\S*\s*$
             ^%(_apache_error_client)s (AH01614: )?client used wrong authentication scheme: \S*\s*$
             ^%(_apache_error_client)s (AH\d+: )?Authorization of user \S+ to access \S* failed, reason: .*$
             ^%(_apache_error_client)s (AH0179[24]: )?(Digest: )?user .*: password mismatch: \S*\s*$
             ^%(_apache_error_client)s (AH0179[01]: |Digest: )user `.*' in realm `.+' (not found|denied by provide
 r): \S*\s*$
             ^%(_apache_error_client)s (AH01631: )?user .*: authorization failure for "\S*":\s*$
             ^%(_apache_error_client)s (AH01775: )?(Digest: )?invalid nonce .* received - length is not \S+\s*$
             ^%(_apache_error_client)s (AH01788: )?(Digest: )?realm mismatch - got `.*' but expected `.+\S*\s*$
             ^%(_apache_error_client)s (AH01789: )?(Digest: )?unknown algorithm `.*' received: \S*\s*$
             ^%(_apache_error_client)s (AH01793: )?invalid qop `.*' received: \S*\s*$
             ^%(_apache_error_client)s (AH01777: )?(Digest: )?invalid nonce .* received - user attempted time travel\s*$
 
 
 
 
 
 

``` ****************************************
The apache is set to true in the jail.conf:
```

#
# HTTP servers
#

[apache]

enabled  = true
port     = http,https
filter   = apache-auth
logpath  = /var/log/apache2/*error.log
maxretry = 1


```

*****************************************```

root@----:/etc/fail2ban/filter.d# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-apache  tcp  --  anywhere             anywhere             multiport dports http,https
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain fail2ban-apache (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere            

Chain fail2ban-ssh (2 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere    
```        


*******************

apache-auth.conf from filter.d
```

# Fail2Ban apache-auth filter
#

[INCLUDES]

# Read common prefixes. If any customizations available -- read them from
# apache-common.local
before = apache-common.conf

[Definition]


failregex = ^%(_apache_error_client)s (AH01797: )?client denied by server configuration: (uri )?\S*\s*$
            ^%(_apache_error_client)s (AH01617: )?user .* authentication failure for "\S*": Password Mismatch$
            ^%(_apache_error_client)s (AH01618: )?user .* not found(: )?\S*\s*$
            ^%(_apache_error_client)s (AH01614: )?client used wrong authentication scheme: \S*\s*$
            ^%(_apache_error_client)s (AH\d+: )?Authorization of user \S+ to access \S* failed, reason: .*$
            ^%(_apache_error_client)s (AH0179[24]: )?(Digest: )?user .*: password mismatch: \S*\s*$
            ^%(_apache_error_client)s (AH0179[01]: |Digest: )user `.*' in realm `.+' (not found|denied by provider): \S*\s*$
            ^%(_apache_error_client)s (AH01631: )?user .*: authorization failure for "\S*":\s*$
            ^%(_apache_error_client)s (AH01775: )?(Digest: )?invalid nonce .* received - length is not \S+\s*$
            ^%(_apache_error_client)s (AH01788: )?(Digest: )?realm mismatch - got `.*' but expected `.+\S*\s*$
            ^%(_apache_error_client)s (AH01789: )?(Digest: )?unknown algorithm `.*' received: \S*\s*$
            ^%(_apache_error_client)s (AH01793: )?invalid qop `.*' received: \S*\s*$
            ^%(_apache_error_client)s (AH01777: )?(Digest: )?invalid nonce .* received - user attempted time travel\s*$
failregex = [[]client <HOST>[]] (Digest: )?user .* (authentication failure|not found|Password Mismatch)

ignoreregex =

# DEV Notes:


```

 
 I'm at a loss.. Does anyone see something that I am missing?

---

### Post by Habitual on 2015-07-18
Use [this]("http://pastie.org/pastes/10299749/text") in /etc/fail2ban/filter.d/apache-auth.conf
Test it using 
```
fail2ban-regex /var/log/apache2/error.log /etc/fail2ban/filter.d/apache-auth.conf
```

and Let us know.

---

