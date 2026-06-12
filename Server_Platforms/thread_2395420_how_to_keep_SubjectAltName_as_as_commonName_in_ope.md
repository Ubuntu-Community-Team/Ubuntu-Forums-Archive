---
title: "how to keep SubjectAltName as as commonName in openssl conf file"
date: 2018-07-02
forum: Server Platforms
---

### Post by kunalv-shah on 2018-07-02
I am working on building a Certificate Authority on my centos server. I have completed the setup following OpenSSL Cookbook (great stuff) from [https://www.feistyduck.com/books/openssl-cookbook/](https://www.feistyduck.com/books/openssl-cookbook/) The concepts explained in the book and procedure is very simple and worked like charm. However, I feel it was a bit outdated and chrome browser changed the behavior to require Subject Alternative Name otherwise it gives browser warning even though the certificate is perfectly valid.
After reading the documentation at [https://www.openssl.org/docs/man1.0.2/apps/x509v3_config.html#Subject-Alternative-Name](https://www.openssl.org/docs/man1.0.2/apps/x509v3_config.html#Subject-Alternative-Name) I could understand that I need to include that in my conf file of root CA and sub-ca (intermediate Certificate Authority).


Now what I want to do is to use the commonName as SAN. That means instead of hardcoding SAN, I want to take whatever the value I get from CSR for CommonName and use that as SAN. What should I put in conf file to achieve this? I tried to put 

```
subjectAltName = $commonName
``` 

and it is telling me that it is not a valid way of defining SAN.

Here is my actual conf file

```


[default]
name                    = sub-ca
domain_suffix           = kunalshah.local
aia_url                 = http://$name.$domain_suffix/$name.crt
crl_url                 = http://$name.$domain_suffix/$name.crl
ocsp_url                = http://ocsp.$name.$domain_suffix:9081
default_ca              = ca_default
name_opt                = utf8,esc_ctrl,multiline,lname,align

[ca_dn]
countryName             = "IN"
organizationName        = "Kunal Shah Local"
commonName              = "Kunal Shah Sub CA"

[ca_default]
home                    = .
database                = $home/db/index
serial                  = $home/db/serial
crlnumber               = $home/db/crlnumber
certificate             = $home/$name.crt
private_key             = $home/private/$name.key
RANDFILE                = $home/private/random
new_certs_dir           = $home/certs
unique_subject          = no
copy_extensions         = copy
default_days            = 365
default_crl_days        = 30
default_md              = sha256
policy                  = policy_c_o_match

[policy_c_o_match]
countryName             = match
stateOrProvinceName     = optional
organizationName        = match
organizationalUnitName  = optional
commonName              = supplied
emailAddress            = optional

[req]
default_bits            = 4096
encrypt_key             = yes
default_md              = sha256
utf8                    = yes
string_mask             = utf8only
prompt                  = no
distinguished_name      = ca_dn
req_extensions          = ca_ext

[ca_ext]
basicConstraints        = critical,CA:true
keyUsage                = critical,keyCertSign,cRLSign
subjectKeyIdentifier    = hash

[sub_ca_ext]
authorityInfoAccess     = @issuer_info
authorityKeyIdentifier  = keyid:always
basicConstraints        = critical,CA:true,pathlen:0
crlDistributionPoints   = @crl_info
extendedKeyUsage        = clientAuth,serverAuth
keyUsage                = critical,keyCertSign,cRLSign
nameConstraints         = @name_constraints
subjectKeyIdentifier    = hash

[crl_info]
URI.0                   = $crl_url

[issuer_info]
caIssuers;URI.0         = $aia_url
OCSP;URI.0              = $ocsp_url

[name_constraints]
permitted;DNS.0=kunalshah.local
#permitted;DNS.1=example.org
excluded;IP.0=0.0.0.0/0.0.0.0
excluded;IP.1=0:0:0:0:0:0:0:0/0:0:0:0:0:0:0:0

[ocsp_ext]
authorityKeyIdentifier  = keyid:always
basicConstraints        = critical,CA:false
extendedKeyUsage        = OCSPSigning
noCheck                 = yes
keyUsage                = critical,digitalSignature
subjectKeyIdentifier    = hash

[server_ext]
authorityInfoAccess     = @issuer_info
authorityKeyIdentifier  = keyid:always
basicConstraints        = critical,CA:false
crlDistributionPoints   = @crl_info
extendedKeyUsage        = clientAuth,serverAuth
keyUsage                = critical,digitalSignature,keyEncipherment
subjectKeyIdentifier    = hash
subjectAltName          = $commonName 

[client_ext]
authorityInfoAccess     = @issuer_info
authorityKeyIdentifier  = keyid:always
basicConstraints        = critical,CA:false
crlDistributionPoints   = @crl_info
extendedKeyUsage        = clientAuth
keyUsage                = critical,digitalSignature
subjectKeyIdentifier    = hash



```

---

