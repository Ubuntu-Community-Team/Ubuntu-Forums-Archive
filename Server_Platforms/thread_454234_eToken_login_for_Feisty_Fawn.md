---
title: "eToken login for Feisty Fawn"
date: 2007-05-25
forum: Server Platforms
---

### Post by pbarbier on 2007-05-25
[CENTER][SIZE="5"]**eToken login for Feisty Fawn**[/SIZE][/CENTER]


In this document, I show the steps we have to carry out in order to be able to log on with our eToken.

This applies to the following environment:
- Ubuntu Feisty Fawn 7.04
- eToken Linux PKI client 3.65
- eTokenPro 32K hardware 
- also quickly tested with an NG/OTP 64k token but should I say this ?

I have used user root ;-) to do all this work ("su root" once and for all) but feel free to use sudo instead if you prefer.

To install the eToken software under Feisty, one can follow the steps of document “eToken PKI client 3.65 installation under Feisty Fawn” in this same Forum.

Note that the Ubuntu distribution is not officially supported by Aladdin software “eToken Linux PKI client 3.65”. This does not prevent the software to run fine, but in case of problems, we are on our own.

[SIZE="5"]**Certificate Authority**[/SIZE]

The first task is to build a Certificate Authority (CA) with which we'll later sign the user certificates we'll use for login.

# cd /etc/ssl
/etc/ssl# echo "01" > serial
/etc/ssl# cp /dev/null index.txt

Edit **openssl.cnf** and adapt the defaults to your needs.

The contents are self-explanatory and the modifications are quite easy.
For example, if you decided to put your certificates directly under /etc/ssl, you may turn
 line "dir = ./demoCA" into "dir = ./" 

If you live in the US, you'll put "countryName_default  = US" instead of "countryName_default = AU".
For testing, I suggest to leave the line "default_bits = 1024" to its default. First, this key size works fine with most tokens and second, it will avoid issues that can be hard to debug. For example, when importing a 2048 bits key into a token that only supports 1024 bits keys, you get  a non-meaningful error message that can take a long time to be debugged.

[SIZE="4"]**Creation of the CA keypair and self-signed certificate**[/SIZE]

Let's generate a key pair and a seld-signed 10 years certificate:
etc/ssl# openssl req -new -x509 -keyout ca.key -out ca.crt -days 3650

< Output >
[INDENT]Generating
a 1024 bit RSA private key
.....++++++
.....++++++
writing new private key to 'ca.key'
Enter PEM pass phrase:
Verifying - Enter PEM pass phrase:
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [FR]:
State or Province Name (full name) [Ile de France]:
Locality Name (eg, city) [Paris]:
Organization Name (eg, company) [ABCD]:
Organizational Unit Name (eg, section) [ABCD France]:
Common Name (eg, YOUR name) []:ABCD CA
Email Address []:ca@abcd.fr[/INDENT]
< /Output >

**CSR**
Let's create a key pair and certificate signing request (CSR) for a Linux user called “**test**
”:
**/etc/ssl# openssl req -new -out test.req -keyout test.key**

< Output >
[INDENT]Generating a 2048 bit RSA private key
........................................................+++
............................................................................................................+++
writing new private key to 'test.key'
Enter PEM pass phrase:
Verifying - Enter PEM pass phrase:
-----
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [FR]:
State or Province Name (full name) [Ile de France]:
Locality Name (eg, city) [Paris]:
Organization Name (eg, company) [ABCD]:
Organizational Unit Name (eg, section) [ABCD France CA Unit]:
Common Name (eg, YOUR name) []:test
Email Address []:

Please enter the following 'extra' attributes
to be sent with your certificate request
A challenge password []:
An optional company name []:[/INDENT]
< /Output >

**CA signature of the previous CSR**
**/etc/ssl# openssl ca -out test.crt -infiles test.req**
< Output >
[INDENT]Using configuration from /usr/lib/ssl/openssl.cnf
Enter pass phrase for .//ca.key:
Check that the request matches the signature
Signature ok
Certificate Details:
        Serial Number: 2 (0x2)
        Validity
            Not Before: May 25 08:04:15 2007 GMT
            Not After : May 22 08:04:15 2017 GMT
        Subject:
            countryName               = FR
            stateOrProvinceName       = Ile de France
            organizationName          = ABCD
            organizationalUnitName    = ABCD France CA Unit
            commonName                = test
        X509v3 extensions:
            X509v3 Basic Constraints: 
                CA:FALSE
            Netscape Comment: 
                OpenSSL Generated Certificate
            X509v3 Subject Key Identifier: 
                88:90:19:02:16:AE:14:9F:CF:74:6F:40:E4:CF:97:37:90:06:3E:8E
            X509v3 Authority Key Identifier: 
                keyid:2B:3A:51:EE:53:04:01:67:4C:B2:B7:4B:CF:21:2A:7D:36:51:13:FD

Certificate is to be certified until May 22 08:04:15 2017 GMT (3650 days)
Sign the certificate? [y/n]:y

1 out of 1 certificate requests certified, commit? [y/n]y
Write out database with 1 new entries
Data Base Updated[/INDENT]
< /Output >

**Hash of the CA and CRL directories**
**/etc/ssl# make_hash_link.sh /etc/ssl**

You should obtain a link that looks like this one:
lrwxrwxrwx   1 root root         6 2007-05-25 09:39 9ddb22fe.0 -> ca.crt

**/etc/ssl# make_hash_link.sh /etc/ssl/crl**

[SIZE="5"]**Export / Import Certificate and private key**[/SIZE]

**PKCS#12 export **
We are going export this user certificate and its key into an importable file:
**/etc/ssl# openssl pkcs12 -export -in test.crt -inkey test.key -certfile ca.crt  -name "test" -out test.p12**
< Output >
[INDENT]Enter pass phrase for test.key:
Enter Export Password:
Verifying - Enter Export Password:[/INDENT]
< /Output >

**Import user certificate via Firefox**
- Open Firefox
- Edit / Preferences
- Advanced / View Certificates
- Click Import
- Select file /etc/ssl/test.p12
- Choose your token instead of the software security device
- Enter your eToken PIN code
- Enter your pkcs12 password
After a few seconds, the certificate and keys are imported into your token.

[SIZE="5"]**PAM_PKCS11**[/SIZE]

Download file pam_pkcs11-0.5.3.tar.gz from [http://www.opensc-project.org/files/pam_pkcs11](http://www.opensc-project.org/files/pam_pkcs11)
Extract the file into some directory:
**# cd /opt**
**# tar zxvf  pam_pkcs11-0.5.3.tar.gz**

**Build pam_pkcs11**
[B]# ./configure
# make
# make install
# ln -s /usr/local/lib/security/pam_pkcs11.so /lib/security/pam_pkcs11.so[/B]

(I bypassed a library load issue with this link but there might be a better method like a configuration file setting ? hum!)

**/etc/pam_pkcs11/pam_pkcs11.conf  customization**

I did not change a lot of things in the default file. Here follow my main modifications:
< modifications >
 [INDENT]# Filename of the PKCS #11 module. The default value is "default"
 use_pkcs11_module = etoken;

 # Aladdin eTokenPRO 32
 pkcs11_module etoken {
 module = /usr/local/lib/libetpkcs11.so
 description = "Aladdin PKCS#11 module";
 slot_num = 0;
 support_threads = true;
 ca_dir = /etc/ssl;
 crl_dir = /etc/ssl/crl;
 cert_policy = ca,signature;
}

 # The minimum that works !
 # Here, we match the certificate cn (Common Name) with the Linux userid
 use_mappers = cn, null;[/INDENT]
< /modifications >

I chose the CN mapping because it corresponds to the Linux userid. We can display the test certificate to see this:
# openssl x509 -text -noout -in test.crt 

< Output subtract >
   Subject: C=FR, ST=Ile de France, O=ABCD, OU=ABCD France CA Unit, **CN=test**
< /Output subtract >

[SIZE="5"]**Test**[/SIZE]
Let's try our first token authentication with the command "su". If things go wrong, it will be easier to repair than a gdm authentication!

Edit file /etc/pam.d/su and add the following line at the top:
auth    sufficient pam_pkcs11.so

This means that we'll try ti use the token for authentication and if it fails, we can still use the password authentication. See the Linux PAM System Administrator's Guide at [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/Linux-PAM_SAG.html) for details about this file.

My su file looks like this (comments removed):
<su file>
[INDENT]auth    sufficient pam_pkcs11.so
auth    sufficient pam_rootok.so
session required   pam_env.so readenv=1
session required   pam_env.so readenv=1 envfile=/etc/default/locale
session optional   pam_mail.so nopen
@include common-auth
@include common-account
@include common-session[/INDENT]
</su file>

Open a terminal and try su with the userid you have been using so far (“test” in our case):
Output of such a test:

**# su test**
Password for token test: 

Type exit to leave the new shell:
**$ exit**

If su works fine, then you can modify the files gdm and gnome_screensaver (Kbuntu users will find out the equivalent for KDE) in order to use eToken for GUI login and screensaver unlocking.

Hope it helps.
:)

---

### Post by coolparty on 2007-07-08
Hello,

I'm trying use this algorithm, but when I can use 'su' I got:

> Please insert your smart card or enter your username.
Smart card inserted. 
Welcome eToken!
Smart card password: 
ERROR: pam_pkcs11.c:498: no valid certificate which meets all requirements found
su: Permission denied
Sorry.

---

