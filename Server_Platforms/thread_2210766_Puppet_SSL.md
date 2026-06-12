---
title: "Puppet SSL"
date: 2014-03-12
forum: Server Platforms
---

### Post by Kirk Schnable on 2014-03-12
I've got a Puppet server here which used to work, and at some point the SSL became non-functional.

On the client, I'm getting the error:
**Exiting; no certificate found and waitforcert is disabled**

This is the full client log:
```
# puppet agent --server=auburn.domain.com --test --debug
Debug: Puppet::Type::User::ProviderPw: file pw does not exist
Debug: Puppet::Type::User::ProviderUser_role_add: file roleadd does not exist
Debug: Failed to load library 'ldap' for feature 'ldap'
Debug: Puppet::Type::User::ProviderLdap: feature ldap is missing
Debug: Puppet::Type::User::ProviderDirectoryservice: file /usr/bin/dsimport does not exist
Debug: /User[puppet]: Provider useradd does not support features libuser; not managing attribute forcelocal
Debug: Puppet::Type::Group::ProviderPw: file pw does not exist
Debug: Failed to load library 'ldap' for feature 'ldap'
Debug: Puppet::Type::Group::ProviderLdap: feature ldap is missing
Debug: Puppet::Type::Group::ProviderDirectoryservice: file /usr/bin/dscl does not exist
Debug: /Group[puppet]: Provider groupadd does not support features libuser; not managing attribute forcelocal
Debug: Failed to load library 'selinux' for feature 'selinux'
Debug: Using settings: adding file resource 'logdir': 'File[/var/lib/puppet/log]{:backup=>false, :group=>"puppet", :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :mode=>"750", :links=>:follow, :path=>"/var/lib/puppet/log"}'
Debug: Using settings: adding file resource 'ssldir': 'File[/etc/puppet/ssl]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :mode=>"771", :links=>:follow, :path=>"/etc/puppet/ssl"}'
Debug: Using settings: adding file resource 'statedir': 'File[/var/lib/puppet/state]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :mode=>"1755", :links=>:follow, :path=>"/var/lib/puppet/state"}'
Debug: Using settings: adding file resource 'hostpubkey': 'File[/etc/puppet/ssl/public_keys/hostname.domain.com.pem]{:backup=>false, :ensure=>:file, :loglevel=>:debug, :owner=>"puppet", :mode=>"644", :links=>:follow, :path=>"/etc/puppet/ssl/public_keys/hostname.domain.com.pem"}'
Debug: Using settings: adding file resource 'vardir': 'File[/var/lib/puppet]{:backup=>false, :group=>"puppet", :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :links=>:follow, :path=>"/var/lib/puppet"}'
Debug: Using settings: adding file resource 'requestdir': 'File[/etc/puppet/ssl/certificate_requests]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :links=>:follow, :path=>"/etc/puppet/ssl/certificate_requests"}'
Debug: Using settings: adding file resource 'client_datadir': 'File[/var/lib/puppet/client_data]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :mode=>"750", :links=>:follow, :path=>"/var/lib/puppet/client_data"}'
Debug: Using settings: adding file resource 'privatedir': 'File[/etc/puppet/ssl/private]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :mode=>"750", :links=>:follow, :path=>"/etc/puppet/ssl/private"}'
Debug: Using settings: adding file resource 'certdir': 'File[/etc/puppet/ssl/certs]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :links=>:follow, :path=>"/etc/puppet/ssl/certs"}'
Debug: Using settings: adding file resource 'libdir': 'File[/var/lib/puppet/lib]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :links=>:follow, :path=>"/var/lib/puppet/lib"}'
Debug: Using settings: adding file resource 'hostprivkey': 'File[/etc/puppet/ssl/private_keys/hostname.domain.com.pem]{:backup=>false, :ensure=>:file, :loglevel=>:debug, :owner=>"puppet", :mode=>"600", :links=>:follow, :path=>"/etc/puppet/ssl/private_keys/hostname.domain.com.pem"}'
Debug: Using settings: adding file resource 'confdir': 'File[/etc/puppet]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :links=>:follow, :path=>"/etc/puppet"}'
Debug: Using settings: adding file resource 'publickeydir': 'File[/etc/puppet/ssl/public_keys]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :links=>:follow, :path=>"/etc/puppet/ssl/public_keys"}'
Debug: Using settings: adding file resource 'clientyamldir': 'File[/var/lib/puppet/client_yaml]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :mode=>"750", :links=>:follow, :path=>"/var/lib/puppet/client_yaml"}'
Debug: Using settings: adding file resource 'localcacert': 'File[/etc/puppet/ssl/certs/ca.pem]{:backup=>false, :ensure=>:file, :loglevel=>:debug, :owner=>"puppet", :mode=>"644", :links=>:follow, :path=>"/etc/puppet/ssl/certs/ca.pem"}'
Debug: Using settings: adding file resource 'privatekeydir': 'File[/etc/puppet/ssl/private_keys]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :mode=>"750", :links=>:follow, :path=>"/etc/puppet/ssl/private_keys"}'
Debug: Using settings: adding file resource 'clientbucketdir': 'File[/var/lib/puppet/clientbucket]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :mode=>"750", :links=>:follow, :path=>"/var/lib/puppet/clientbucket"}'
Debug: Using settings: adding file resource 'rundir': 'File[/var/lib/puppet/run]{:backup=>false, :group=>"puppet", :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :mode=>"755", :links=>:follow, :path=>"/var/lib/puppet/run"}'
Debug: Using settings: adding file resource 'pluginfactdest': 'File[/var/lib/puppet/facts.d]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :links=>:follow, :path=>"/var/lib/puppet/facts.d"}'
Debug: Using settings: adding file resource 'graphdir': 'File[/var/lib/puppet/state/graphs]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :links=>:follow, :path=>"/var/lib/puppet/state/graphs"}'
Debug: /File[/etc/puppet/ssl/public_keys]: Autorequiring File[/etc/puppet/ssl]
Debug: /File[/etc/puppet/ssl/certificate_requests]: Autorequiring File[/etc/puppet/ssl]
Debug: /File[/var/lib/puppet/clientbucket]: Autorequiring File[/var/lib/puppet]
Debug: /File[/var/lib/puppet/client_yaml]: Autorequiring File[/var/lib/puppet]
Debug: /File[/etc/puppet/ssl/private_keys/hostname.domain.com.pem]: Autorequiring File[/etc/puppet/ssl/private_keys]
Debug: /File[/var/lib/puppet/client_data]: Autorequiring File[/var/lib/puppet]
Debug: /File[/var/lib/puppet/state]: Autorequiring File[/var/lib/puppet]
Debug: /File[/etc/puppet/ssl/certs/ca.pem]: Autorequiring File[/etc/puppet/ssl/certs]
Debug: /File[/var/lib/puppet/lib]: Autorequiring File[/var/lib/puppet]
Debug: /File[/etc/puppet/ssl/private]: Autorequiring File[/etc/puppet/ssl]
Debug: /File[/etc/puppet/ssl/public_keys/hostname.domain.com.pem]: Autorequiring File[/etc/puppet/ssl/public_keys]
Debug: /File[/var/lib/puppet/state/graphs]: Autorequiring File[/var/lib/puppet/state]
Debug: /File[/var/lib/puppet/facts.d]: Autorequiring File[/var/lib/puppet]
Debug: /File[/etc/puppet/ssl/certs]: Autorequiring File[/etc/puppet/ssl]
Debug: /File[/var/lib/puppet/log]: Autorequiring File[/var/lib/puppet]
Debug: /File[/var/lib/puppet/run]: Autorequiring File[/var/lib/puppet]
Debug: /File[/etc/puppet/ssl/private_keys]: Autorequiring File[/etc/puppet/ssl]
Debug: /File[/etc/puppet/ssl]: Autorequiring File[/etc/puppet]
Debug: Finishing transaction -611754598
Debug: Using settings: adding file resource 'logdir': 'File[/var/lib/puppet/log]{:backup=>false, :group=>"puppet", :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :mode=>"750", :links=>:follow, :path=>"/var/lib/puppet/log"}'
Debug: Using settings: adding file resource 'ssldir': 'File[/etc/puppet/ssl]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :mode=>"771", :links=>:follow, :path=>"/etc/puppet/ssl"}'
Debug: Using settings: adding file resource 'statedir': 'File[/var/lib/puppet/state]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :mode=>"1755", :links=>:follow, :path=>"/var/lib/puppet/state"}'
Debug: Using settings: adding file resource 'hostpubkey': 'File[/etc/puppet/ssl/public_keys/hostname.domain.com.pem]{:backup=>false, :ensure=>:file, :loglevel=>:debug, :owner=>"puppet", :mode=>"644", :links=>:follow, :path=>"/etc/puppet/ssl/public_keys/hostname.domain.com.pem"}'
Debug: Using settings: adding file resource 'vardir': 'File[/var/lib/puppet]{:backup=>false, :group=>"puppet", :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :links=>:follow, :path=>"/var/lib/puppet"}'
Debug: Using settings: adding file resource 'requestdir': 'File[/etc/puppet/ssl/certificate_requests]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :links=>:follow, :path=>"/etc/puppet/ssl/certificate_requests"}'
Debug: Using settings: adding file resource 'privatedir': 'File[/etc/puppet/ssl/private]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :mode=>"750", :links=>:follow, :path=>"/etc/puppet/ssl/private"}'
Debug: Using settings: adding file resource 'certdir': 'File[/etc/puppet/ssl/certs]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :links=>:follow, :path=>"/etc/puppet/ssl/certs"}'
Debug: Using settings: adding file resource 'libdir': 'File[/var/lib/puppet/lib]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :links=>:follow, :path=>"/var/lib/puppet/lib"}'
Debug: Using settings: adding file resource 'hostprivkey': 'File[/etc/puppet/ssl/private_keys/hostname.domain.com.pem]{:backup=>false, :ensure=>:file, :loglevel=>:debug, :owner=>"puppet", :mode=>"600", :links=>:follow, :path=>"/etc/puppet/ssl/private_keys/hostname.domain.com.pem"}'
Debug: Using settings: adding file resource 'confdir': 'File[/etc/puppet]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :links=>:follow, :path=>"/etc/puppet"}'
Debug: Using settings: adding file resource 'publickeydir': 'File[/etc/puppet/ssl/public_keys]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :links=>:follow, :path=>"/etc/puppet/ssl/public_keys"}'
Debug: Using settings: adding file resource 'localcacert': 'File[/etc/puppet/ssl/certs/ca.pem]{:backup=>false, :ensure=>:file, :loglevel=>:debug, :owner=>"puppet", :mode=>"644", :links=>:follow, :path=>"/etc/puppet/ssl/certs/ca.pem"}'
Debug: Using settings: adding file resource 'privatekeydir': 'File[/etc/puppet/ssl/private_keys]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :mode=>"750", :links=>:follow, :path=>"/etc/puppet/ssl/private_keys"}'
Debug: Using settings: adding file resource 'rundir': 'File[/var/lib/puppet/run]{:backup=>false, :group=>"puppet", :ensure=>:directory, :loglevel=>:debug, :owner=>"puppet", :mode=>"755", :links=>:follow, :path=>"/var/lib/puppet/run"}'
Debug: Using settings: adding file resource 'pluginfactdest': 'File[/var/lib/puppet/facts.d]{:backup=>false, :ensure=>:directory, :loglevel=>:debug, :links=>:follow, :path=>"/var/lib/puppet/facts.d"}'
Debug: /File[/var/lib/puppet/facts.d]: Autorequiring File[/var/lib/puppet]
Debug: /File[/etc/puppet/ssl/public_keys/hostname.domain.com.pem]: Autorequiring File[/etc/puppet/ssl/public_keys]
Debug: /File[/var/lib/puppet/run]: Autorequiring File[/var/lib/puppet]
Debug: /File[/var/lib/puppet/lib]: Autorequiring File[/var/lib/puppet]
Debug: /File[/etc/puppet/ssl/private]: Autorequiring File[/etc/puppet/ssl]
Debug: /File[/etc/puppet/ssl/public_keys]: Autorequiring File[/etc/puppet/ssl]
Debug: /File[/etc/puppet/ssl/certs]: Autorequiring File[/etc/puppet/ssl]
Debug: /File[/var/lib/puppet/state]: Autorequiring File[/var/lib/puppet]
Debug: /File[/var/lib/puppet/log]: Autorequiring File[/var/lib/puppet]
Debug: /File[/etc/puppet/ssl/certs/ca.pem]: Autorequiring File[/etc/puppet/ssl/certs]
Debug: /File[/etc/puppet/ssl/certificate_requests]: Autorequiring File[/etc/puppet/ssl]
Debug: /File[/etc/puppet/ssl/private_keys]: Autorequiring File[/etc/puppet/ssl]
Debug: /File[/etc/puppet/ssl/private_keys/hostname.domain.com.pem]: Autorequiring File[/etc/puppet/ssl/private_keys]
Debug: /File[/etc/puppet/ssl]: Autorequiring File[/etc/puppet]
Debug: Finishing transaction -611378078
Debug: Using cached certificate for ca
Debug: Using cached certificate for ca
Debug: Using cached certificate_request for hostname.domain.com
Debug: Using cached certificate for ca
Debug: Using cached certificate_request for hostname.domain.com
Debug: Using cached certificate for ca
Debug: Using cached certificate for ca
Exiting; no certificate found and waitforcert is disabled
```

I haven't found anything useful in the server logs yet.  The server is running Puppet through the Apache Passenger.

**error.log**
Last entry is when I restarted Apache earlier.
```
[Wed Mar 12 10:45:17 2014] [notice] Apache/2.2.22 (Ubuntu) Phusion_Passenger/2.2.11 PHP/5.3.10-1ubuntu3.10 with Suhosin-Patch mod_ssl/2.2.22 OpenSSL/1.0.1 configured -- resuming normal operations
```

**access.log**
Obviously not the right log.
```
127.0.0.1 - - [12/Mar/2014:13:38:05 -0500] "GET / HTTP/1.1" 200 491 "-" "Wget/1.13.4 (linux-gnu)"
127.0.0.1 - - [12/Mar/2014:13:40:05 -0500] "GET / HTTP/1.1" 200 491 "-" "Wget/1.13.4 (linux-gnu)"
```

**other_vhosts_access.log**
```
auburn.domain.com:8140 10.9.6.163 - - [12/Mar/2014:13:39:34 -0500] "GET /production/certificate/hostname.domain.com? HTTP/1.1" 404 4429 "-" "-"
auburn.domain.com:8140 10.9.6.163 - - [12/Mar/2014:13:39:34 -0500] "GET /production/certificate/hostname.domain.com? HTTP/1.1" 404 4429 "-" "-"
auburn.domain.com:8140 10.9.6.163 - - [12/Mar/2014:13:39:34 -0500] "GET /production/certificate/hostname.domain.com? HTTP/1.1" 404 4429 "-" "-"
auburn.domain.com:8140 10.9.6.163 - - [12/Mar/2014:13:39:34 -0500] "GET /production/certificate/hostname.domain.com? HTTP/1.1" 404 4429 "-" "-"
auburn.domain.com:8140 10.9.6.163 - - [12/Mar/2014:13:39:34 -0500] "GET /production/certificate/hostname.domain.com? HTTP/1.1" 404 4429 "-" "-"
auburn.domain.com:8140 10.9.6.163 - - [12/Mar/2014:13:39:34 -0500] "GET /production/certificate/hostname.domain.com? HTTP/1.1" 404 4429 "-" "-"
auburn.domain.com:8140 10.9.6.163 - - [12/Mar/2014:13:39:34 -0500] "GET /production/certificate/hostname.domain.com? HTTP/1.1" 404 4429 "-" "-"
auburn.domain.com:8140 10.9.6.163 - - [12/Mar/2014:13:39:34 -0500] "GET /production/certificate/hostname.domain.com? HTTP/1.1" 404 4429 "-" "-"
auburn.domain.com:8140 10.9.6.163 - - [12/Mar/2014:13:39:34 -0500] "GET /production/certificate/hostname.domain.com? HTTP/1.1" 404 4429 "-" "-"
auburn.domain.com:8140 10.9.6.163 - - [12/Mar/2014:13:39:34 -0500] "GET /production/certificate/hostname.domain.com? HTTP/1.1" 404 4429 "-" "-"
```

Any ideas?

---

