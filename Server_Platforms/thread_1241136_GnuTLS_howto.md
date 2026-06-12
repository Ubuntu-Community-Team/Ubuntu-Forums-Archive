---
title: "GnuTLS howto"
date: 2009-08-15
forum: Server Platforms
---

### Post by Despot on 2009-08-15
Hi all,

I haven't been able to find much in the way of documentation for using GnuTLS. So I took it upon myself to write a howto. Hope it helps somebody.

Comments, corrections and additions welcome.

[B] WARNING: these instructions are provided as-is. No warranty expressed or implied, etc. Please be sure to educate yourself on the security issues involved before deploying.
[/B] 
GnuTLS ([http://www.gnu.org/software/gnutls/](http://www.gnu.org/software/gnutls/)) is an LGPL-licensed implementation of Transport Layer Security. Using GnuTLS avoids the licensing issues that can arise from employing the more common OpenSSL package. For this reason, certain packages in Ubuntu have disabled support for OpenSSL in favor of GnuTLS.

Before reading this guide, you should be familiar on the concepts behind SSL/TLS. The Ubuntu Server Guide has a decent explanation: [https://help.ubuntu.com/9.04/serverguide/C/certificates-and-security.html](https://help.ubuntu.com/9.04/serverguide/C/certificates-and-security.html).

[SIZE=3]**Preparation**[/SIZE]

First, we need to install the necessary tools to generate certificates and debug connections:

```
$ sudo apt-get install gnutls-bin
```More information on the gnutls toolkit can be found here: [http://www.gnu.org/software/gnutls/manual/html_node/Included-programs.html](http://www.gnu.org/software/gnutls/manual/html_node/Included-programs.html)

**A Word on Naming**

Keeping track of keys and certificates can become difficult after a while. I recommend the following naming scheme for keys and certificates, but the keys and certs will work the same with whatever name you use.


[LIST]
[*] Private keys named after the servers or services, plus the domain name, plus a ".key" suffix. For instance, if I have my LDAP server running on "ldap.example.com", I would name my private key "ldap.example.com.key".
[*] Certificates named after the servers or services they will be used for with a ".cert" suffix. For instance, if I have my LDAP server running on "ldap.example.com", I would name my certificate "ldap.example.com.cert".
[*] I consider Certificate Authorities to be a service, so a CA keyname would take the form "ca.example.com.key" and the certificate name would be "ca.example.com.cert"
[/LIST]
   
**Fully Qualified Domain Names**

It is important to pick a Fully Qualified Domain Name to use for when connecting to your server. This is important because the FQDN that your clients connect to *must* match the FQDN in the certificate.

[SIZE=3]**Generating Certificates**[/SIZE]

There are three paths to acquiring the necessary certificates:


[LIST=1]
[*] Generate a self-signed certificate. Easiest method, but not very secure or scalable.
[*] Get a certificate from a Certificate Authority (CA). More secure and easy to deploy, but can cost money.
[*] Be your own CA. Secure, scalable, but requires more work initially.
[/LIST]
 
Each method has a section dedicated to it below. But first, we must generated a private key.

[SIZE=3]** Generating a Private Key**[/SIZE]

The private key is the secret that the server will use to identify itself to clients. We use the GnuTLS utility certtools to generate the private key like this:

```
$ certtool --generate-privkey --outfile <keyname>
```

Pick a descriptive name to use in place of <keyname> (see the **Naming** section). Other options for the private key exist, as detailed here: [http://www.gnu.org/software/gnutls/manual/html_node/Invoking-certtool.html#Invoking-certtool](http://www.gnu.org/software/gnutls/manual/html_node/Invoking-certtool.html#Invoking-certtool)

Generating the key will take time, often 15-30 minutes depending on computer usage. This is not due to heavy computations but rather the need for highly random numbers. If the key generation process is not satisfied with the randomness of the numbers it has generated for your key, it will continue to get more random numbers until it finds something suitably random. You can create more randomness by using your computer while you wait for the key to generate.

Once the key is generated, we need to make sure it is secure by changing its permissions:
        
```
$ chmod 600 <keyname>
```This will keep unauthorized parties from reading our private key and using it to fake the server's identity.

[SIZE=3]**Self-Signing**[/SIZE]

A self-signed certificate is generated like this:

    ```
$ certtool --generate-self-signed --load-privkey <keyname> --outfile <certificatename>

```<keyname> is the name of the private key file from the "Generating a Key" section. Pick a descriptive name to use in place of <certificatename> (see Naming section). 

See the **Certificate Options** section for information on how to answer the questions presented by the tool.

[B][SIZE=3]Using a Certificate Authority[/SIZE]
[/B] 
To generate a certificate using a Certificate Authority, we must generate a private key (see above). Once we have the private key in hand, we must generate a Certificate Signing Request (CSR) and submit it to the Certificate Authority. To generate a CSR, use the following command:

```
$ certtool --generate-request --load-privkey <keyname> --outfile <csrname>
```<keyname> is the name of the private key file from the "Generating a Private Key" section. Pick a descriptive name to use in place of <csrname>--I recommend the FQDN of the server with the extension ".csr"

You will need to send the CSR and other relevant information to your Certificate Authority for verification. The details of this process vary and are beyond the scope of this tutorial. When the CA has verified your identity, it will digitally sign your CSR and return it to you.

Once you have received the signed request, you can generate a certificate from it:

```
$ certtool --generate-certificate --load-request <signedcsrname> \
 --outfile <certificate> \
 --load-ca-certificate <cacert> --load-ca-privkey <caprivkey>

```**NOTE:** I have not tested this functionality myself, and the --load-ca-privkey option does not make sense to me, even though it's specified in the certtools documentation. I would appreciate input on whether or not this option is required.
        
<keyname> is the name of the private key file from the **Generating A Key** section. Pick a descriptive name to use in place of <certificatename> (see Naming section). 

Answer the questions as detailed in the Certificate Options section.

[B][SIZE=3]Being a Certificate Authority[/SIZE]
[/B] 
To generate a certificate using our own Certificate Authority, we must first generate a private key (see above) and a self-signed certificate for use in establishing the Certificate Authority's identity.

First, follow the procedure for generating a self-signed certificate, making sure to clearly identify the key and certificate as belonging to the Certificate Authority, not the server. **Be *very careful* to secure the CA's private key--if it is compromised, your entire chain of trust is compromised!**

Now, generate a private key for the server (see above). Use this key and your CA's key and cert to generate a certificate for the server like this:

```
$ certtool --generate-certificate --load-privkey <keyname> \
--outfile <servercertname> \
--load-ca-certificate <cacert> --load-ca-privkey <cakey>

```<keyname> is the name of the server's private key file. Pick a descriptive name to use in place of <servercertname>. See the Naming section for recommended naming conventions.

Answer the questions as detailed in the **Certificate Options** section.

[SIZE=2][B][SIZE=3]Certificate Options[/SIZE]
[/B][/SIZE] 
The certificate generation process will ask several questions about the nature of the certificate. The various options are explained in the sample template file in the certtool documentation: [http://www.gnu.org/software/gnutls/manual/html_node/Invoking-certtool.html#Invoking-certtool](http://www.gnu.org/software/gnutls/manual/html_node/Invoking-certtool.html#Invoking-certtool)

The following options are required for server certificates:

[LIST]
[*] the certificate must *not* be marked as a CA certificate. (ca = false)
[*] the DNS name *must* match the FQDN that the clients will use to access the server. Matching the FQDN of the connection to the FQDN on the certificate is part of how the client verifies the server's identity.
[*] the certificate must be marked as usable for encryption. (encryption_key)
[*] the certificate must be marked as usable for a TLS server. (tls_www_server)
[/LIST]
 
The following options are required for Certificate Authority certificates:

[LIST]
[*] must be marked as a CA certificate. (ca = true)
[*] must be marked as usable for signing other certificates. (signing_key)
[*] must be marked as usable for signing Certificate Revocation Lists (CRLs). (crl_signing_key)
[/LIST]
 
The other fields are not critical, but very useful in certificate identification. It is particularly important to configure the CA's certificate properly, since it will be used to sign other certificates.
[SIZE=3]
**Deploying the Certificates**[/SIZE]
Now that you've got your shiny new certificate(s), you'll want to put them somewhere accessible to programs and services. The default directory for SSL certificates is [FONT=Courier New]/etc/ssl/certs/[/FONT]. Move the certificates here and make sure the permissions are set to 755 like this:

```
$ chmod 755 /etc/ssl/certs/<certname>
```Make sure the files are owned by root and the group is set to ssl:

```
$ chown root:ssl /etc/ssl/certs/<certname>
```By default, private keys are placed in [FONT=Courier New]/etc/ssl/private/[/FONT]. I find this practice to be inflexible and difficult to manage in terms of access control.  I recommend placing private keys in the relevant subdirectory of [FONT=Courier New]/etc/[/FONT]. For instance, a private key for LDAP would be placed in /etc/ldap/, and the private key for a Web server in [FONT=Courier New]/etc/apache2/[/FONT].

**Be sure to change the permissions on the private key so that only the owner can read/write, and only the owner and group can read:**

```
$ chmod 640 <keyname>
```Best practice is to assign file ownership to root, and set the group to the same group that the service is run as. For instance, a Web key would be set to group "www-data" since the Apache daemon runs under this group.

**[SIZE=2]AppArmor[/SIZE]**
Various services have further access control set by AppArmor. Make sure to properly configure AppArmor to allow services like LDAP to access the appropriate files.

[B][SIZE=2]Certificate Deployment on the Client
[/SIZE][/B]For self-signed certificates, clients that must verify the server's identity should have a copy of the server's self-signed certificate in their [FONT=Courier New]/etc/ssl/certs/[/FONT] directory.

For certificates signed by a Certificate Authority, use a copy of the Certificate Authority's certificate instead.

---

### Post by mushroomblue on 2009-08-22
just for the sake of us that need our hands held, would it be possible to expand a bit on each certificate generated? of particular usefulness would be a template of what to enter at each prompt when creating certificates (for instance, what's my URI for the CRL Distribution Point?).

seeing as OpenLDAP is built against GnuTLS rather than OpenSSL, and nothing in the Ubuntu Server Guide provides us with any help on GnuTLS certificates, you're our only hope for setting up a PDC in Ubuntu 9.04

thanks a bunch for the howto.

---

### Post by mushroomblue on 2009-08-26
using [this link]("http://libvirt.org/remote.html"), I've been able to get GnuTLS working as a proper CA that OpenLDAP can use for TLS authentication. a few things needed to be modified (/etc/ssl/certs is where I put my keys), but it seems to be working fine.

---

### Post by Despot on 2009-10-07
Odd that I wasn't notified when you posted...I thought I was subscribed to this thread.

Anyway, I'd be happy to incorporate any new info you can provide. I'm not completely clear on the operation of CRLs myself, although I assume it's meant to be a list of certificates that have been revoked, and should no longer be considered valid.

---

### Post by aravamudan on 2010-03-23
:pHi 

Request if you can post a step by step approach for generating a self-signed TLS certificate for access and replication 

Thanks in Advance

---

### Post by Despot on 2010-12-25
I've made quite a few revisions to this guide and posted in the Ubuntu documentation wiki:

[https://help.ubuntu.com/community/GnuTLS](https://help.ubuntu.com/community/GnuTLS)

Comments/questions/additions welcome.

---

