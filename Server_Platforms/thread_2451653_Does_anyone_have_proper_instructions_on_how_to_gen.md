---
title: "Does anyone have proper instructions on how to generate self-signed TLS certificates?"
date: 2020-10-08
forum: Server Platforms
---

### Post by kevdog on 2020-10-08
’m using OpenLdap docker image and trying to create TLS client and server certs. I’m not sure if the process of creating self-signed TLS certs in unique to openLDAP, however I can get the client to authenticate the server but I can’t get the server to authenticate the host. I’m just wondering if anyone has a proper method of generating these types of certificates. Most of the information I can find is for SSL certs, not specifically TLS certificates.

Thanks for any direction or link you could provide.

---

### Post by LHammonds on 2020-10-08
> **kevdog said:**
> &#8217;m using OpenLdap docker image and trying to create TLS client and server certs. I&#8217;m not sure if the process of creating self-signed TLS certs in unique to openLDAP, however I can get the client to authenticate the server but I can&#8217;t get the server to authenticate the host. I&#8217;m just wondering if anyone has a proper method of generating these types of certificates. Most of the information I can find is for SSL certs, not specifically TLS certificates.

Thanks for any direction or link you could provide.
Certificates are just certificates.  They are not dependent on the TLS or SSL (deprecated) protocols.

TLS is just the handshake between the server and client that establishes the shared secret and what encryption to use.  Encryption is a feature of the server/client.

LHammonds

---

### Post by The Cog on 2020-10-08
I had a quick google and just found these that look reasonable:
[https://www.golinuxcloud.com/create-certificate-authority-root-ca-linux/](https://www.golinuxcloud.com/create-certificate-authority-root-ca-linux/)
[https://www.cyberithub.com/create-a-self-signed-certificate/](https://www.cyberithub.com/create-a-self-signed-certificate/)
[https://www.linux.com/training-tutorials/creating-self-signed-ssl-certificates-apache-linux/](https://www.linux.com/training-tutorials/creating-self-signed-ssl-certificates-apache-linux/)
They're not the ones I used when I made a self-signed cert (can't remember which one I used). I do know that many years ago I used the instructions in the OpenVPN manual, and I don't suppose they've changed much since then.

---

### Post by kevdog on 2020-10-08
Is there anything fundamentally dependent or different between server and client certs?  I thought server had to have FQDN as the CN with SANS listing possible other names.  I'm not sure how a client cert is supposed to be structured.

---

### Post by The Cog on 2020-10-08
I *think* that a server cert confirms that the subject's identity is "secure.example.com", and is checked against the URL the browser is trying to connect to. And the client cert confirms that the user is "john.doe". But I think these are just names, and there is no difference in the certificates themselves. At least, I think that's right. The certificates have to be signed by a "certificate authority" that the client or server trust. This may be a well known certificate issuer (let's encrypt for instance), or a lesser known private root certificate that is specially added to the SSL's list of trusted roots. 

Each end can choose how much checking to do. 
I think with web servers, they generally don't verify the caller's identity except perhaps for corporate servers that want the caller to have a certificate signed by the corporation's own certificate authority. Clients such as web browsers will almost always checks that the server's certificate matches the expected server name.

Someone please correct me if I'm wrong.

---

### Post by kevdog on 2020-10-08
Hey thanks for help.  Here is the openssl.cnf file I'm using.  Do I need all these for certificate generation:

[ca]
default_ca = my_ca

[ my_ca ]
dir               = /etc/docker/compose/authelia/certs/openldap2
#certs                  = $dir/certs
crl_dir                 = $dir/crl
new_certs_dir     = ./
database              = $dir/index.txt
serial                   = $dir/ca.srl
RANDFILE        = $dir/.rand

# The root key and root certificate.
private_key       = $dir/ca/ca-key.pem
certificate          = $dir/ca/ca.pem

# For certificate revocation lists.
crlnumber              = $dir/crlnumber
crl                          = $dir/crl/ca-crl.pem
crl_extensions       = crl_ext
default_crl_days   = 30

# SHA-1 is deprecated, so use SHA-2 instead.
default_md        = sha256

name_opt          = ca_default
cert_opt             = ca_default
default_days      = 3750
preserve             = no
policy                = policy_loose

copy_extensions   = copy

[ policy_loose ]
# Allow the intermediate CA to sign a more diverse range of certificates.
# See the POLICY FORMAT section of the `ca` man page.
countryName                  = optional
stateOrProvinceName     = optional
localityName                   = optional
organizationName           = optional
organizationalUnitName  = optional
commonName                  = supplied
emailAddress                   = optional

[req]
default_bits = 4096
default_md = sha256
x509_extensions = v3_ca
distinguished_name = req_distinguished_name
string_mask = utf8only

[req_distinguished_name]
# See <https://en.wikipedia.org/wiki/Certificate_signing_request>.
countryName                     = Country Name (2 letter code)
stateOrProvinceName             = State or Province Name
localityName                    = Locality Name
0.organizationName              = Organization Name
organizationalUnitName          = Organizational Unit Name
commonName                      = Common Name
emailAddress                    = Email Address

# Optionally, specify some defaults.
countryName_default             = US
stateOrProvinceName_default     = IL
localityName_default            = CH
0.organizationName_default      = domainn.com
organizationalUnitName_default  =
emailAddress_default            = [email]user@domain.com[/email]

[ v3_ca ]
basicConstraints = critical,CA:TRUE
subjectKeyIdentifier = hash
authorityKeyIdentifier = keyid:always,issuer:always
keyUsage = critical, digitalSignature, cRLSign, keyCertSign

[ client_cert ]
basicConstraints = CA:FALSE
nsCertType = client
nsComment = "OpenSSL Generated Self-Signed Client Certificate"
subjectKeyIdentifier = hash
authorityKeyIdentifier = keyid,issuer:always
keyUsage = critical, nonRepudiation, digitalSignature, keyEncipherment
extendedKeyUsage = clientAuth

[ server_cert ]
basicConstraints = CA:FALSE
nsCertType = server
nsComment = "OpenSSL Generated Self-Sign Server Certificate"
subjectKeyIdentifier = hash
authorityKeyIdentifier = keyid,issuer:always
keyUsage = critical, nonRepudiation, digitalSignature, keyEncipherment
extendedKeyUsage = serverAuth
subjectAltName = @alt_names

[alt_names]
DNS.1 = openldap.domain.com
DNS.2 = ldap.domain.com
DNS.3 = openldap
IP.1 = 127.0.0.1
IP.2 = ::1

[ crl_ext ]
# Extension for CRLs (`man x509v3_config`).
authorityKeyIdentifier=keyid:always

I'd generate the server and client certificates like this:

- Use following commands to generate CA key and cert:
openssl genrsa -aes256 -out ./ca/ca-key.pem4096
openssl req -config openssl.cnf  -key ./ca/ca.key.pem new -x509 -days 10000 -sha256 -extensions v3_ca  -out ca/ca.pem

Validate root certificate:
openssl x509 -noout -text in ./ca/ca.pem


Copy CA cert to server and client subfolder
cp ./ca/ca.pem ./client/
cp ./ca/ca.pem ./server/

Create Server and client Keys and Certificates
Generate Server and Client Keys
openssl genrsa -out ./client/key.pem 2048
openssl genrsa -out ./server/key.pem 2048

Generate the certificate Signing Requests 
openssl req -config openssl.cnf -key ./client/key.pem -new -sha256 -out ./client/cert.csr
openssl req -config openssl.cnf -key ./server/key.pem -new -sha256 -out ./server/cert.csr

Create the Server and Client Certificates
openssl ca -config openssl.cnf -extensions server-cert -days 3750 -notext -md sha256 -in ./server/cert.csr -out ./server/cert.pem
openssl ca -config openssl.cnf -extensions client-cert -days 3750 -notext -md sha256 -in ./client/cert.csr -out ./client/cert.pem

---

### Post by kevdog on 2020-10-12
So I totally figured this one out.

Here is my new openssl.conf file

```

[ca]
default_ca = my_ca

[ my_ca ]
dir               = <base_dir>
certs             = $dir/certs
crl_dir           = $dir/crl
new_certs_dir     = ./
database          = $dir/index.txt
serial            = $dir/ca/ca.srl
RANDFILE          = $dir/.rand

# The root key and root certificate.
private_key       = $dir/ca/ca-key.pem
certificate       = $dir/ca/ca.pem

# For certificate revocation lists.
crlnumber         = $dir/crlnumber
crl               = $dir/crl/ca-crl.pem
crl_extensions    = crl_ext
default_crl_days  = 30

# SHA-1 is deprecated, so use SHA-2 instead.
default_md        = sha256

name_opt          = ca_default
cert_opt          = ca_default
default_days      = 3750
preserve          = no
policy            = policy_loose

copy_extensions   = copy

[ policy_loose ]
# Allow the intermediate CA to sign a more diverse range of certificates.
# See the POLICY FORMAT section of the `ca` man page.
countryName             = optional
stateOrProvinceName     = optional
localityName            = optional
organizationName        = optional
organizationalUnitName  = optional
commonName              = supplied
emailAddress            = optional

[req]
default_bits = 4096
default_md = sha256
x509_extensions = v3_ca
distinguished_name = req_distinguished_name
string_mask = utf8only

[req_distinguished_name]
# See <https://en.wikipedia.org/wiki/Certificate_signing_request>.
countryName                     = Country Name (2 letter code)
stateOrProvinceName             = State or Province Name
localityName                    = Locality Name
0.organizationName              = Organization Name
organizationalUnitName          = Organizational Unit Name
commonName                      = Common Name
emailAddress                    = Email Address

# Optionally, specify some defaults.
countryName_default             = US
stateOrProvinceName_default     = IL
localityName_default            = CH
0.organizationName_default      = domain.com
organizationalUnitName_default  =
emailAddress_default            = [email]user@domain.com[/email]

[ v3_ca ]
basicConstraints = critical,CA:TRUE
subjectKeyIdentifier = hash
authorityKeyIdentifier = keyid:always,issuer:always
keyUsage = critical, digitalSignature, cRLSign, keyCertSign

[ client_cert ]
basicConstraints = CA:FALSE
nsComment = "OpenSSL Generated Self-Signed Client Certificate"
subjectKeyIdentifier = hash
authorityKeyIdentifier = keyid,issuer:always
keyUsage = nonRepudiation, digitalSignature, keyEncipherment
extendedKeyUsage = clientAuth

[ server_cert ]
basicConstraints = CA:FALSE
nsComment = "OpenSSL Generated Self-Sign Server Certificate"
subjectKeyIdentifier = hash
authorityKeyIdentifier = keyid,issuer:always
keyUsage = critical, nonRepudiation, digitalSignature, keyEncipherment
extendedKeyUsage = serverAuth
subjectAltName = @alt_names

[alt_names]
DNS.1 = openldap.domain.com
DNS.2 = ldap.domain.com
DNS.3 = openldap
IP.1 = 127.0.0.1
IP.2 = ::1

[ crl_ext ]
# Extension for CRLs (`man x509v3_config`).
authorityKeyIdentifier=keyid:always

```

So modify the openssl.cnf file to fit your needs.  Change the alt_names to fit your needs.  Alt_names is needed for server config.  Optionally change the defaults section and also the [ my_ca ] ->dir parameter to set your base directory.

Then I do the following steps:

```

cd <base_directory>
mkdir -p ca client server

```

Create Serial and DB text file
```

echo 01 > ./ca/ca.srl
touch index.txt

```

Use following commands to generate CA key and cert:
```

openssl genrsa -aes256 -out ./ca/ca-key.pem4096
openssl req -config openssl.cnf  -key ./ca/ca.key.pem new -x509 -days 10000 -sha256 -extensions v3_ca  -out ca/ca.pem

```

Validate root certificate:
```

openssl x509 -noout -text -in ./ca/ca.pem

```


Copy CA cert to server and client subfolder
```

cp ./ca/ca.pem ./client/
cp ./ca/ca.pem ./server/

```

Create Server and client Keys and Certificates
```

Generate Server and Client Keys
openssl genrsa -out ./client/key.pem 2048
openssl genrsa -out ./server/key.pem 2048

```

Generate the certificate Signing Requests 
```

openssl req -config openssl.cnf -key ./client/key.pem -new -sha256 -out ./client/cert.csr
openssl req -config openssl.cnf -key ./server/key.pem -new -sha256 -out ./server/cert.csr

```

Create the Server and Client Certificates
```

openssl ca -config openssl.cnf -extensions server-cert -days 3750 -notext -md sha256 -in ./server/cert.csr -out ./server/cert.pem
openssl ca -config openssl.cnf -extensions client-cert -days 3750 -notext -md sha256 -in ./client/cert.csr -out ./client/cert.pem

```

Validation steps

Keys: 
```

openssl rsa -in ./server/key.pem -check
openssl rsa -in ./client/key.pem -check

```

Examine Certs: 
```

openssl x509 -in ./server/cert.pem -text -noout
openssl x509 -in ./client/cert.pem -text -noout

```

Verify Validate chain of trust of certs against CA certificate (Make sure this step works).
```

openssl verify -CAfile ./ca/ca.pem ./server/cert.pem
openssl verify -CAfile ./ca/ca.pem ./client/cert.pem

```

Test connection to LDAP server from client (Assuming current working directory is base directory)
Client: 
```

echo | openssl s_client -showcerts -servername openldap.domain.com -cert ./client/cert.pem -key ./client/key.pem -connect openldap.domain.com:636 2>/dev/null | openssl x509 -inform pem -noout -text

```
Note the key and cert client certificates
Server: 
```

docker logs openldap

```
Example output:
```

5f833ec9 conn=1016 fd=12 ACCEPT from IP=10.0.1.86:49912 (IP=0.0.0.0:636)
5f833ec9 conn=1016 fd=12 TLS established tls_ssf=256 ssf=256
5f833ec9 conn=1016 fd=12 closed (connection lost)

```

That should be it.  Thanks for your help.

References for further reading:
[https://jamielinux.com/docs/openssl-certificate-authority/index.html](https://jamielinux.com/docs/openssl-certificate-authority/index.html)
[https://stackoverflow.com/questions/10175812/how-to-create-a-self-signed-certificate-with-openssl](https://stackoverflow.com/questions/10175812/how-to-create-a-self-signed-certificate-with-openssl)

---

