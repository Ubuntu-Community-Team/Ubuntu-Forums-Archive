---
title: "SSL setup on 8.04 desktop version"
date: 2008-05-08
forum: Server Platforms
---

### Post by nxfs on 2008-05-08
Hello everybody, thanks for your help.

I have a problem setting up SSL, I've followed the instruction here

Creating the Certificate Authority
[https://help.ubuntu.com/community/OpenSSL#head-0cd0e88006ce6e9baae4b8cf4ab4bc56ea41de4c](https://help.ubuntu.com/community/OpenSSL#head-0cd0e88006ce6e9baae4b8cf4ab4bc56ea41de4c)

but came across this problem

MYSERVER1:invalid type in 'policy' configuration

where "MYSERVER" is the name of my server.



=========this is my config, i'm not too sure about the "DNS" part because i don't ahve a domain name, could that be the problem?

# My sample caconfig.cnf file.
#
# Default configuration to use when one is not provided on the command line.
#
[ ca ]
default_ca      = local_ca
#
#
# Default location of directories and files needed to generate certificates.
#
[ local_ca ]
dir             = /home/jondole/myCA
certificate     = $dir/cacert.pem
database        = $dir/index.txt
new_certs_dir   = $dir/signedcerts
private_key     = $dir/private/cakey.pem
serial          = $dir/serial
#       
#
# Default expiration and encryption policies for certificates.
#
default_crl_days        = 365
default_days            = 1825
default_md              = md5
#       
policy          = local_ca_policy
x509_extensions = local_ca_extensions
#       
#
# Default policy to use when generating server certificates.  The following
# fields must be defined in the server certificate.
#
[ local_ca_policy ]
commonName              = MYSERVER
stateOrProvinceName     = CA
countryName             = US
emailAddress            = [email]jondole@gmail.com[/email]
organizationName        = MYSERVER
organizationalUnitName  = MYSERVER
#       
#
# x509 extensions to use when generating server certificates.
#
[ local_ca_extensions ]
subjectAltName          = DNS:alt.tradeshowhell.com
basicConstraints        = CA:false
nsCertType              = server
#       
#
# The default root certificate generation policy.
#
[ req ]
default_bits    = 2048
default_keyfile = /home/<username>/myCA/private/cakey.pem
default_md      = md5
#       
prompt                  = no
distinguished_name      = root_ca_distinguished_name
x509_extensions         = root_ca_extensions
#
#
# Root Certificate Authority distinguished name.  Change these fields to match
# your local environment!
#
[ root_ca_distinguished_name ]
commonName              = MYSERVER
stateOrProvinceName     = CA
countryName             = US
emailAddress            = [email]jondole@gmail.com[/email]
organizationName        = MYSERVER
organizationalUnitName  = MYSERVER
#       
[ root_ca_extensions ]
basicConstraints        = CA:true

---

### Post by Ocelaris on 2008-10-06
I'm working on the same thing, but I noticed that one thing you have wrong is:

> [ req ]
default_bits = 2048
default_keyfile = /home/[COLOR="Red"]<username>[/COLOR]/myCA/private/cakey.pem
default_md = md5

<username> should be your jondole or whatever location you have the root of your certificates... 

Keep tooling with it! I'm in the same boat, something in the config file is wrong I assume. Will report back if I figure it out.

---

