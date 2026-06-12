---
title: "Trying to configure a CA"
date: 2011-11-19
forum: Server Platforms
---

### Post by jaywatkins on 2011-11-19
Hello,

I am trying to setup a CA on my Ubuntu Server (11.10) VM for purposes of secure Postfix/Dovecot. I started by following the tutorial on the Ubuntu Server Guide at;

[https://help.ubuntu.com/11.10/serverguide/C/certificates-and-security.html#certificate-authority](https://help.ubuntu.com/11.10/serverguide/C/certificates-and-security.html#certificate-authority)

I have followed the instructions on the page verbatim (literally via copy and paste) and requesting a cert from the CA fails with the following output.

root@ns:/home/spongebob# sudo openssl ca -in server.csr -config /etc/ssl/openssl.cnf
Using configuration from /etc/ssl/openssl.cnf
Enter pass phrase for /etc/ssl//private/cakey.pem:
CA certificate and CA private key do not match
3074242712:error:0B080074:x509 certificate routines:X509_check_private_key:key values mismatch:x509_cmp.c:318:

I am not great with certificates, which is why I am trying to learn, but would like to figure this one out. I have tried repeating the steps for creating a public/private key then moving them to the associated directories, with no luck. Anyone out there come across this error. I did report this to the ubuntu-docs folks as a possible bug.

Thanks

---

### Post by hawkmage on 2011-11-19
OK, this is a bit involved.  Playing around with OpenSSL to create a three level set of CA certificates which involve a Root, intermediary and issuing certificates.   

What I did was the following to establish the Root CA config:
```
mkdir ~/CA
mkdir ~/CA/root
cd ~/CA/root
cp /usr/lib/ssl/openssl.cnf .
mkdir certs crl newcerts private
touch index.txt
echo "01" > serial

```
Edit the following values in openssl.cnf:
```
HOME            = $ENV::HOME
dir        = $HOME/CA/root
default_days    = 3650
default_bits        = 4096
```
The rest of these should be what your default info for certs are:
```
countryName_default
stateOrProvinceName_default
localityName_default
0.organizationName_default
organizationalUnitName_default
```

Here is what I did to make the Intermediary and Issuing CA config:
```
mkdir ~/CA/inter
mkdir ~/CA/issue
cp -R ~/CA/root/* ~/CA/inter/
cp -R ~/CA/root/* ~/CA/issue/
```

Edit the ~/CA/inter/openssl.cnf file as follows:
```
dir        = $HOME/CA/inter
default_days    = 1825
```

Edit the ~/CA/issue/openssl.cnf file as follows:
```
dir        = $HOME/CA/issue
 default_days    = 730
default_bits        = 2048
```

Now to establish the Root, intermediary and issuing certificates.

The Root CA cert:
```
cd ~/CA/root
openssl genrsa -des3 -out private/cakey.pem 4096
openssl req -config openssl.cnf -new -x509 -nodes -sha1 -days 1825 -key private/cakey.pem -out cacert.pem
```

Intermediary cert:
```
cd ~/CA/inter/
openssl genrsa -des3 -out private/cakey.pem 4096
openssl req -config openssl.cnf -new -sha1 -key private/cakey.pem -out inter.csr
cp inter.csr ~/CA/root/
cd ../root/
openssl ca -config openssl.cnf -extensions v3_ca -days 3650 -out inter.cer -in inter.csr 
cp inter.* ~/CA/inter/cacert.pem
```

Issuing cert:
```
cd ~/CA/issue/
openssl genrsa -out private/cakey.pem 2048 -nodes
openssl req -config openssl.cnf -new -sha1 -key private/cakey.pem -out issue.csr
cp issue.csr ~/CA/inter/
cd ~/CA/inter/
openssl ca -config openssl.cnf -extensions v3_ca -days 3650 -out issue.cer -in issue.csr 
cp issue.cer ~/CA/issue/cacert.pem

```

Once you have done this you have everything you need to sign your own certificates.  

Just copy the CSR you want to sign into the ~/CA/issue directory and run the command:
```
openssl ca -config openssl.cnf -days 730 -out YourCert.cer -in YourCert.csr
```
Where YourCert.csr is the name of the CSR you just generated.

---

### Post by jaywatkins on 2011-11-20
Hi,

Thanks for the detailed reply! Will I have to, or should I, remove my existing damage to the server?

---

### Post by jaywatkins on 2011-11-20
Also, were these commands done as root, or as the regular user? I usually 'su' as root while entering commands to avoid password fatigue and exit-out, when I am finished?

---

### Post by jaywatkins on 2011-11-20
The command;  "openssl ca -config openssl.cnf -extensions v3_ca -days 3650 -out inter.cer -in inter.csr" produced...

"Error opening CA certificate /home/n74jw/CA/root/CA/cacert.pem
3074119832:error:02001002:system library:fopen:No such file or directory:bss_file.c:398:fopen('/home/n74jw/CA/root/CA/cacert.pem','r')
3074119832:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:400:
unable to load certificate

---

### Post by jaywatkins on 2011-11-20
Same thing for the Issuing cert creation sequence

"n74jw@ns:~/CA/inter$ openssl ca -config openssl.cnf -extensions v3_ca -days 3650 -out issue.cer -in issue.csr 
Using configuration from openssl.cnf
Enter pass phrase for /home/n74jw/CA/inter/private/cakey.pem:
Error opening CA certificate /home/n74jw/CA/inter/CA/cacert.pem
3074275480:error:02001002:system library:fopen:No such file or directory:bss_file.c:398:fopen('/home/n74jw/CA/inter/CA/cacert.pem','r')
3074275480:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:400:
unable to load certificate"

This path seems wrong;  "/home/n74jw/CA/inter/CA/cacert.pem", but I do not know how to correct it or in what file.

---

### Post by jaywatkins on 2011-11-20
This is my openssl.cnf from ~/CA/root/
-------------------------------------------------------------------------------


#
# OpenSSL example configuration file.
# This is mostly being used for generation of certificate requests.
#

# This definition stops the following lines choking if HOME isn't
# defined.
HOME			= $ENV::HOME
RANDFILE		= $ENV::HOME/.rnd

# Extra OBJECT IDENTIFIER info:
#oid_file		= $ENV::HOME/.oid
oid_section		= new_oids

# To use this configuration file with the "-extfile" option of the
# "openssl x509" utility, name here the section containing the
# X.509v3 extensions to use:
# extensions		= 
# (Alternatively, use a configuration file that has only
# X.509v3 extensions in its main [= default] section.)

[ new_oids ]

# We can add new OIDs in here for use by 'ca', 'req' and 'ts'.
# Add a simple OID like this:
# testoid1=1.2.3.4
# Or use config file substitution like this:
# testoid2=${testoid1}.5.6

# Policies used by the TSA examples.
tsa_policy1 = 1.2.3.4.1
tsa_policy2 = 1.2.3.4.5.6
tsa_policy3 = 1.2.3.4.5.7

####################################################################
[ ca ]
default_ca	= CA_default		# The default ca section

####################################################################
[ CA_default ]

dir		= $HOME/CA/root		# Where everything is kept
certs		= $dir/certs		# Where the issued certs are kept
crl_dir		= $dir/crl		# Where the issued crl are kept
database	= $dir/CA/index.txt	# database index file.
#unique_subject	= no			# Set to 'no' to allow creation of
					# several ctificates with same subject.
new_certs_dir	= $dir/newcerts		# default place for new certs.

certificate	= $dir/CA/cacert.pem 	# The CA certificate
serial		= $dir/CA/serial 		# The current serial number
crlnumber	= $dir/crlnumber	# the current crl number
					# must be commented out to leave a V1 CRL
crl		= $dir/crl.pem 		# The current CRL
private_key	= $dir/private/cakey.pem # The private key
RANDFILE	= $dir/private/.rand	# private random number file

x509_extensions	= usr_cert		# The extentions to add to the cert

# Comment out the following two lines for the "traditional"
# (and highly broken) format.
name_opt 	= ca_default		# Subject Name options
cert_opt 	= ca_default		# Certificate field options

# Extension copying option: use with caution.
# copy_extensions = copy

# Extensions to add to a CRL. Note: Netscape communicator chokes on V2 CRLs
# so this is commented out by default to leave a V1 CRL.
# crlnumber must also be commented out to leave a V1 CRL.
# crl_extensions	= crl_ext

default_days	= 3650			# how long to certify for
default_crl_days= 30			# how long before next CRL
default_md	= default		# use public key default MD
preserve	= no			# keep passed DN ordering

# A few difference way of specifying how similar the request should look
# For type CA, the listed attributes must be the same, and the optional
# and supplied fields are just that :-)
policy		= policy_match

# For the CA policy
[ policy_match ]
countryName		= match
stateOrProvinceName	= match
organizationName	= match
organizationalUnitName	= optional
commonName		= supplied
emailAddress		= optional

# For the 'anything' policy
# At this point in time, you must list all acceptable 'object'
# types.
[ policy_anything ]
countryName		= optional
stateOrProvinceName	= optional
localityName		= optional
organizationName	= optional
organizationalUnitName	= optional
commonName		= supplied
emailAddress		= optional

####################################################################
[ req ]
default_bits		= 4096
default_keyfile 	= privkey.pem
distinguished_name	= req_distinguished_name
attributes		= req_attributes
x509_extensions	= v3_ca	# The extentions to add to the self signed cert

# Passwords for private keys if not present they will be prompted for
# input_password = secret
# output_password = secret

# This sets a mask for permitted string types. There are several options. 
# default: PrintableString, T61String, BMPString.
# pkix	 : PrintableString, BMPString (PKIX recommendation before 2004)
# utf8only: only UTF8Strings (PKIX recommendation after 2004).
# nombstr : PrintableString, T61String (no BMPStrings or UTF8Strings).
# MASK:XXXX a literal mask value.
# WARNING: ancient versions of Netscape crash on BMPStrings or UTF8Strings.
string_mask = utf8only

# req_extensions = v3_req # The extensions to add to a certificate request

[ req_distinguished_name ]
countryName			= Country Name (2 letter code)
countryName_default		= AU
countryName_min			= 2
countryName_max			= 2

stateOrProvinceName		= State or Province Name (full name)
stateOrProvinceName_default	= Some-State

localityName			= Locality Name (eg, city)

0.organizationName		= Organization Name (eg, company)
0.organizationName_default	= Internet Widgits Pty Ltd

# we can do this but it is not needed normally :-)
#1.organizationName		= Second Organization Name (eg, company)
#1.organizationName_default	= World Wide Web Pty Ltd

organizationalUnitName		= Organizational Unit Name (eg, section)
#organizationalUnitName_default	=

commonName			= Common Name (eg, YOUR name)
commonName_max			= 64

emailAddress			= Email Address
emailAddress_max		= 64

# SET-ex3			= SET extension number 3

[ req_attributes ]
challengePassword		= A challenge password
challengePassword_min		= 4
challengePassword_max		= 20

unstructuredName		= An optional company name

[ usr_cert ]

# These extensions are added when 'ca' signs a request.

# This goes against PKIX guidelines but some CAs do it and some software
# requires this to avoid interpreting an end user certificate as a CA.

basicConstraints=CA:FALSE

# Here are some examples of the usage of nsCertType. If it is omitted
# the certificate can be used for anything *except* object signing.

# This is OK for an SSL server.
# nsCertType			= server

# For an object signing certificate this would be used.
# nsCertType = objsign

# For normal client use this is typical
# nsCertType = client, email

# and for everything including object signing:
# nsCertType = client, email, objsign

# This is typical in keyUsage for a client certificate.
# keyUsage = nonRepudiation, digitalSignature, keyEncipherment

# This will be displayed in Netscape's comment listbox.
nsComment			= "OpenSSL Generated Certificate"

# PKIX recommendations harmless if included in all certificates.
subjectKeyIdentifier=hash
authorityKeyIdentifier=keyid,issuer

# This stuff is for subjectAltName and issuerAltname.
# Import the email address.
# subjectAltName=email:copy
# An alternative to produce certificates that aren't
# deprecated according to PKIX.
# subjectAltName=email:move

# Copy subject details
# issuerAltName=issuer:copy

#nsCaRevocationUrl		= [http://www.domain.dom/ca-crl.pem](http://www.domain.dom/ca-crl.pem)
#nsBaseUrl
#nsRevocationUrl
#nsRenewalUrl
#nsCaPolicyUrl
#nsSslServerName

# This is required for TSA certificates.
# extendedKeyUsage = critical,timeStamping

[ v3_req ]

# Extensions to add to a certificate request

basicConstraints = CA:FALSE
keyUsage = nonRepudiation, digitalSignature, keyEncipherment

[ v3_ca ]


# Extensions for a typical CA


# PKIX recommendation.

subjectKeyIdentifier=hash

authorityKeyIdentifier=keyid:always,issuer

# This is what PKIX recommends but some broken software chokes on critical
# extensions.
#basicConstraints = critical,CA:true
# So we do this instead.
basicConstraints = CA:true

# Key usage: this is typical for a CA certificate. However since it will
# prevent it being used as an test self-signed certificate it is best
# left out by default.
# keyUsage = cRLSign, keyCertSign

# Some might want this also
# nsCertType = sslCA, emailCA

# Include email address in subject alt name: another PKIX recommendation
# subjectAltName=email:copy
# Copy issuer details
# issuerAltName=issuer:copy

# DER hex encoding of an extension: beware experts only!
# obj=DER:02:03
# Where 'obj' is a standard or added object
# You can even override a supported extension:
# basicConstraints= critical, DER:30:03:01:01:FF

[ crl_ext ]

# CRL extensions.
# Only issuerAltName and authorityKeyIdentifier make any sense in a CRL.

# issuerAltName=issuer:copy
authorityKeyIdentifier=keyid:always

[ proxy_cert_ext ]
# These extensions should be added when creating a proxy certificate

# This goes against PKIX guidelines but some CAs do it and some software
# requires this to avoid interpreting an end user certificate as a CA.

basicConstraints=CA:FALSE

# Here are some examples of the usage of nsCertType. If it is omitted
# the certificate can be used for anything *except* object signing.

# This is OK for an SSL server.
# nsCertType			= server

# For an object signing certificate this would be used.
# nsCertType = objsign

# For normal client use this is typical
# nsCertType = client, email

# and for everything including object signing:
# nsCertType = client, email, objsign

# This is typical in keyUsage for a client certificate.
# keyUsage = nonRepudiation, digitalSignature, keyEncipherment

# This will be displayed in Netscape's comment listbox.
nsComment			= "OpenSSL Generated Certificate"

# PKIX recommendations harmless if included in all certificates.
subjectKeyIdentifier=hash
authorityKeyIdentifier=keyid,issuer

# This stuff is for subjectAltName and issuerAltname.
# Import the email address.
# subjectAltName=email:copy
# An alternative to produce certificates that aren't
# deprecated according to PKIX.
# subjectAltName=email:move

# Copy subject details
# issuerAltName=issuer:copy

#nsCaRevocationUrl		= [http://www.domain.dom/ca-crl.pem](http://www.domain.dom/ca-crl.pem)
#nsBaseUrl
#nsRevocationUrl
#nsRenewalUrl
#nsCaPolicyUrl
#nsSslServerName

# This really needs to be in place for it to be a proxy certificate.
proxyCertInfo=critical,language:id-ppl-anyLanguage,pathlen:3,policy:foo

####################################################################
[ tsa ]

default_tsa = tsa_config1	# the default TSA section

[ tsa_config1 ]

# These are used by the TSA reply generation only.
dir		= ./demoCA		# TSA root directory
serial		= $dir/tsaserial	# The current serial number (mandatory)
crypto_device	= builtin		# OpenSSL engine to use for signing
signer_cert	= $dir/tsacert.pem 	# The TSA signing certificate
					# (optional)
certs		= $dir/cacert.pem	# Certificate chain to include in reply
					# (optional)
signer_key	= $dir/private/tsakey.pem # The TSA private key (optional)

default_policy	= tsa_policy1		# Policy if request did not specify it
					# (optional)
other_policies	= tsa_policy2, tsa_policy3	# acceptable policies (optional)
digests		= md5, sha1		# Acceptable message digests (mandatory)
accuracy	= secs:1, millisecs:500, microsecs:100	# (optional)
clock_precision_digits  = 0	# number of digits after dot. (optional)
ordering		= yes	# Is ordering defined for timestamps?
				# (optional, default: no)
tsa_name		= yes	# Must the TSA name be included in the reply?
				# (optional, default: no)
ess_cert_id_chain	= no	# Must the ESS cert id chain be included?
				# (optional, default: no)

--------------------------------------------------------------------------------

---

### Post by hawkmage on 2011-11-20
I ran the set of commands as a regular user, one that I specifically created for doing certificates.

Also I would get out of the habit of doing stuff as root unless you absolutely have to.

In the openssl.cnf you posted you have the lines 
```
certificate	= $dir/CA/cacert.pem 	# The CA certificate
serial		= $dir/CA/serial 		# The current serial number
```
The $dir was already set to the proper directory for the base of the CA directory.  Change it to:
```
certificate	= $dir/cacert.pem 	# The CA certificate
 serial		= $dir/serial 		# The current serial number
```

---

### Post by jaywatkins on 2011-11-20
I understand the sensitivity of the root account, but entering a password (one that is rather complex, nonetheless) gets very tedious every time some kind of configuration change has to be made. I don't actually log in as root, just use 'su'.

Same deal with the intermediate CA and the issuing CA;

"n74jw@ns:~/CA/root$ openssl ca -config openssl.cnf -extensions v3_ca -days 3650 -out inter.cer -in inter.csr 
Using configuration from openssl.cnf
Enter pass phrase for /home/n74jw/CA/root/private/cakey.pem:
/home/n74jw/CA/root/CA/index.txt: No such file or directory
unable to open '/home/n74jw/CA/root/CA/index.txt'
3075225752:error:02001002:system library:fopen:No such file or directory:bss_file.c:398:fopen('/home/n74jw/CA/root/CA/index.txt','r')
3075225752:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:400:"

"n74jw@ns:~/CA/inter$ openssl ca -config openssl.cnf -extensions v3_ca -days 3650 -out issue.cer -in issue.csr 
Using configuration from openssl.cnf
Enter pass phrase for /home/n74jw/CA/inter/private/cakey.pem:
Error opening CA certificate /home/n74jw/CA/inter/CA/cacert.pem
3074721944:error:02001002:system library:fopen:No such file or directory:bss_file.c:398:fopen('/home/n74jw/CA/inter/CA/cacert.pem','r')
3074721944:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:400:
unable to load certificate"

I only made your suggested changes to the openssl.conf in ~/CA/root/ and not the others.

Thanks again!

---

### Post by hawkmage on 2011-11-20
By using su you become root and operate as root is just like logging in as root.  Have you thought about using sudo and configuring it to allow you to run commands without a password.

The error:
```
unable to open '/home/n74jw/CA/root/CA/index.txt'
```Tells me that there were other paths that I missed seeing.  I looked again and saw the following:
```
certificate    = $dir/CA/cacert.pem     # The CA certificate
serial        = $dir/CA/serial         # The current serial number
```You may want to search for other occurrences of "$dir/CA/" and fix them.

You will need to make the same changes to the other openssl.cnf for them to work.

---

### Post by jaywatkins on 2011-11-20
I wasn't aware that it was possible to sudo without entering a password, but to that end, what is the point? If I can sudo without a password, isn't that just a detrimental to the computer's security posture?

Holy sh*t! that worked (awesome)

cp inter.* ~/CA/inter/cacert.pem  produced an error stating cacert.pem is not a directory. Just copy to ~/CA/inter/ instead?

The issuing sequence seems to be expecting something else.

n74jw@ns:~/CA/inter$ openssl ca -config openssl.cnf -extensions v3_ca -days 3650 -out issue.cer -in issue.csr 
Using configuration from openssl.cnf
Enter pass phrase for /home/n74jw/CA/inter/private/cakey.pem:
unable to load certificate
3075192984:error:0906D06C:PEM routines:PEM_read_bio:no start line:pem_lib.c:696:Expecting: TRUSTED CERTIFICATE

Not sure where the trusted certificate should come from. That is what I am trying to create.

---

### Post by hawkmage on 2011-11-20
OK, that command should have been:
```
cp inter.cer ~/CA/inter/cacert.pem
```

On the other error Is there a the issue.scr in the ~/CA/inter directory?  If so is the first line look like this:
```
-----BEGIN CERTIFICATE REQUEST-----
```
And the last line look like this:
```
-----END CERTIFICATE REQUEST-----
```

---

### Post by toshko3 on 2011-11-21
You may want to try this: [http://xca.sourceforge.net/](http://xca.sourceforge.net/)
I used this to configure a CA and key pairs for outlook encryption. It is great and graphical. Waaay easier and very mature program.
Other alternative is may be to use the openvpn scripts in /usr/share/doc/openvpn/examples/easy-rsa folder when you install it. I don't know, but they may be of help to you. You can read in the openvpn community howto for creating a CA and keys.

---

### Post by hawkmage on 2011-11-21
I'll have to take a look at that XCA, the command line stuff I posted for using openssl was more of an education exercise for my self to figure out the nuts an bolts of a CA.

---

### Post by jaywatkins on 2011-11-21
The modified command allowed me to finish running through the sequence of commands successfully. The certificate did have the proper beginning and ending sequences, with a very large hash in the middle. Thanks for the help, it is very much appreciated. I clearly need to do more research and reading on this subject. Just following a set of commands is not enough for me to get the gist of what is going on and what I should be doing. 

Thanks again

---

### Post by rhford2 on 2013-04-09
I know this was an old forum post but I'm hoping this is seen.

Following the step I came upon "cp inter.* ~/CA/inter/cacert.pem".  There were two files created under ~/CA/root, inter.cer and inter.csr following the previous steps.  

So I ask, which is the correct file that should be copied to ~/CA/inter/cacert.pem.

Thank you

Never mind.  I should have read all the posts.  My mistake... Sorry

---

### Post by QIII on 2013-04-09
Hello.  Thank you for sharing.

This is an old thread.  From the Forum Rules at ***[http://ubuntuforums.org/misc.php?do=showrules:](http://ubuntuforums.org/misc.php?do=showrules:)***

> If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.
[I]
Thread **closed.**[/I]

---

