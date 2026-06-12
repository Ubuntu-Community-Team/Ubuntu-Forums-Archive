---
title: "HOWTO:FreeRadius+EAP/PEAP"
date: 2007-06-19
forum: Server Platforms
---

### Post by reauthor on 2007-06-19
Since it appears that many people could not setup RADIUS server for users authentication in wireless networks on Ubuntu because of licensing problems whit libraries such is rlm_eap_tls.so library, I was writing my first HOWTO and explain how I was able to install and configure FreeRadius on Ubuntu Server 7.04

I must say that Iam not expert or power user or something like that.

Ok,hey ho,lets go!

WPA is a big step up from WEP, security-wise. WPA's Pre-Shared Key mode (sometimes called WPA Personal) is handy and easy to set up. WPA2 too!
However, it allows only one key for all users. If you want to have different passwords for different users, or if you want real authentication,
you'll need to use the full 802.11x-based WPA2 Enterprise protocol, and that means that you'll need a RADIUS server.

In this HOWTO we will setting up EAP/PEAP authentication via FreeRADIUS.EAP/PEAP isn't the only flavor of authentication protocol, 
but it is the easiest to set up and has the lowest per-client overhead.EAP/TTLS is comparable to EAP/PEAP which I will show you nex time.
EAP/TLS is also good, but it requires each client to have its own certificate.

STEP 1

1.First,we need some packages for building and install Debian packages from source code.

```
# apt-get install build-essential
...
# apt-get install apt-src

```

2.Now,we will update the lists of available packages. Identical to apt-get update, really, and must be run as root in the default configuration.

```
# apt-src update

```


3.Then create directory for building ,point to that directory and download FreeRadius.

```
# mkdir ~/build_freeradius
# cd ~/build_freeradius
# apt-src install freeradius

```
4.If we list curent directory we will see few  files

```
# ls -l

drwxr-xr-x 15 root root 4096 2007-01-11 16:35 freeradius-1.1.3
-rw-r--r-- 1 root root 15130 2006-09-01 20:07 freeradius_1.1.3-3.diff.gz
-rw-r--r-- 1 root root 975 2006-09-01 20:07 freeradius_1.1.3-3.dsc
-rw-r--r-- 1 root root 2587376 2006-09-01 20:07 freeradius_1.1.3.orig.tar.gz
```

STEP 2

1.Now point to **~/build_freeradius/freeradius-1.1.3/debian** directory  where is file** rules** which we must edit.Please,read this
carefuly. Find this lines and uncoment like this..

```
# If you want to use SSL and/or the postgres module, comment
# out these two lines and uncomment the two after
# You will also need to add a Build-Depends on libssl-dev and libpq-dev
# and remove the Build-Conflicts on libssl-dev
# Finally you need to cat debian/control.postgresql >> debian/control

#buildssl=--without-rlm_eap_peap --without-rlm_eap_tls --without-rlm_eap_ttls --without-rlm_otp 
          --without-rlm_sql_postgresql --without-snmp
#modulelist=krb5 ldap sql_mysql sql_iodbc

buildssl=--with-rlm_sql_postgresql_lib_dir=`pg_config --libdir` 
         --with-rlm_sql_postgresql_include_dir=`pg_config --includedir`
modulelist=krb5 ldap sql_mysql sql_iodbc sql_postgresql

```
2.Edit control file in same directory to look like this

```
Source: freeradius
Build-Depends: debhelper (>= 5), libltdl3-dev, libpam0g-dev, libmysqlclient15-dev | libmysqlclient-dev, libgdbm-dev,
               libldap2-dev, libsasl2-dev, libiodbc2-dev, libkrb5-dev, snmp, autotools-dev, dpatch (>= 2),
               libperl-dev, libtool, dpkg-dev (>= 1.13.19),[B] *[COLOR="Red"]libssl-dev, libpq-dev[/COLOR]*
[/B]
Build-Conflicts:        
```  


3.Just type this command:)

```
# cd ~/build_freeradius/freeradius-1.1.3/debian
# cat control.postgresql >> control
```

4.Now when we edited this files we can install aditional packages without conflicts.

```
# apt-get install libssl-dev libpq-dev
```

5.in **~/build_freeradius/freeradius-1.1.3/debian/** find **changelog** file and edit,something like this

```
freeradius (1.1.3-3ubuntu1tls) feisty; urgency=low

* Add tls support for compilation

 -- reauthor <reauthor@gmail.com>  Fri, 16 Mar 2007 20:22:40 +0200
```

6.Than,go to **~/build_freeradius** and build a deb packages..

```
# cd ~/build_freeradius
# apt-src build freeradius
...
...
...
I: Successfully built in /root/build_freeradius/freeradius-1.1.3

```
7.Now list curent directory and you will see lots of stuff.We need just one.(if you font to work whit SQL,now is time to install)

```
# ls -l | grep deb

-rw-r--r--  1 root root  774000 2007-06-15 11:58 freeradius_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root  774026 2007-06-15 12:20 freeradius_1.1.3-3ubuntu1tls_i386.deb
-rw-r--r--  1 root root  115910 2007-06-15 11:58 freeradius-dialupadmin_1.1.3-3ubuntu1_all.deb
-rw-r--r--  1 root root  115914 2007-06-15 12:19 freeradius-dialupadmin_1.1.3-3ubuntu1tls_all.deb
-rw-r--r--  1 root root   32120 2007-06-15 11:58 freeradius-iodbc_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   32120 2007-06-15 12:20 freeradius-iodbc_1.1.3-3ubuntu1tls_i386.deb
-rw-r--r--  1 root root   32852 2007-06-15 11:58 freeradius-krb5_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   32852 2007-06-15 12:20 freeradius-krb5_1.1.3-3ubuntu1tls_i386.deb
-rw-r--r--  1 root root   47452 2007-06-15 11:58 freeradius-ldap_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   47462 2007-06-15 12:20 freeradius-ldap_1.1.3-3ubuntu1tls_i386.deb
-rw-r--r--  1 root root   32004 2007-06-15 11:58 freeradius-mysql_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   32002 2007-06-15 12:20 freeradius-mysql_1.1.3-3ubuntu1tls_i386.deb
-rw-r--r--  1 root root   32506 2007-06-15 11:58 freeradius-postgresql_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   32502 2007-06-15 12:20 freeradius-postgresql_1.1.3-3ubuntu1tls_i386.deb


```
8.time to install

```
# dpkg -i freeradius_1.1.3-3ubuntu1tls_i386.deb
```


9.check installation and you will see something like this.

```
# ps aux | grep radius

freerad 4118 0.0 0.8 44608 2224 ? Ssl 18:16 0:00 /usr/sbin/freeradius

```

STEP 3

Configuring FreeRADIUS

1.The configuration files can be found under **/etc/freeradius/**.Edit** radiusd.conf **file and make sure the following settings are set:

```
# under MODULES, make sure mschap is uncommented!
    mschap {
      # authtype value, if present, will be used
      # to overwrite (or add) Auth-Type during
      # authorization. Normally, should be MS-CHAP
      authtype = MS-CHAP

      # if use_mppe is not set to no, mschap will
      # add MS-CHAP-MPPE-Keys for MS-CHAPv1 and
      # MS-MPPE-Recv-Key/MS-MPPE-Send-Key for MS-CHAPv2
      #
      use_mppe = yes

      # if mppe is enabled, require_encryption makes
      # encryption moderate
      #
      require_encryption = yes

      # require_strong always requires 128 bit key
      # encryption
      #
      require_strong = yes

      authtype = MS-CHAP
      # The module can perform authentication itself, OR
      # use a Windows Domain Controller. See the radius.conf file
      # for how to do this.
    }
```
    


Also make sure the "authorize" and "authenticate" contains:

```
authorize {
        preprocess
        mschap
	suffix
	eap
	files
    }
    
    authenticate {
         
         #
         #  MSCHAP authentication.    
         Auth-Type MS-CHAP {
               mschap
          }
	
	 #
         #  Allow EAP authentication.
         eap
     }
```

2. Then, change the **clients.conf** file to specify what network it's serving:

    Here, is address of our AP,secret and name of the network

 ```
  client 192.168.1.100/24 { 
        # This is the shared secret between the Authenticator (the 
	# access point) and the Authentication Server (RADIUS).
        secret          = SharedSecret99
        shortname       = myhomewireless
    }
```
   
 

3. The **eap.conf** should also be pretty straightforward.

   

      a)   Set "default_eap_type" to "peap":

            ```
default_eap_type = peap

```

      b)   Since PEAP is using TLS, the TLS section must contain:
           
       ```
tls { 
        # The private key password
        private_key_password = SecretKeyPass77
	# The private key
        private_key_file = ${raddbdir}/certs/cert-srv.pem
        #  Trusted Root CA list
        CA_file = ${raddbdir}/certs/demoCA/cacert.pem
        dh_file = ${raddbdir}/certs/dh
        random_file = /dev/urandom
	}
```

      c)   Find the "peap" section, and make sure it contain the following:


     ```
 peap {
        #  The tunneled EAP session needs a default
        #  EAP type, which is separate from the one for
        #  the non-tunneled EAP module.  Inside of the
        #  PEAP tunnel, we recommend using MS-CHAPv2,
        #  as that is the default type supported by
        #  Windows clients.
        default_eap_type = mschapv2
      }
```
 
4. The user information is stored in a plain text file **users**. A more sophisticated solution to store user information may be preferred (SQL, LDAP, PDC, etc.).

Just add your username and password like this on the end in **users** file


```

"testuser"      User-Password == "Secret149"
```

STEP 4

Configuring AP

[[IMG]http://img528.imageshack.us/img528/1118/untitleddj4.th.jpg[/IMG]](http://img528.imageshack.us/my.php?image=untitleddj4.jpg)

STEP 5

run freerdius in debuging mode
```

# freeradius -X
```
 

and that is all folks..

For setup supliciant (your machine) see wieman01 post "**HOWTO: Wireless Security - WPA1, WPA2, LEAP, etc.**" ( [http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539) )

I tested whit Feisty  and Windows XP as supliciant and works OK!

---

### Post by fide321 on 2007-06-25
Hi,
 Nice work but  I´m not able to work for me :( . This is the problemm that appears when Itry to start freeradius -X
rlm_eap: Unable to load EAP-Type/peap, as EAP-Type/TLS is required first.
radiusd.conf[10]: eap: Module instantiation failed. 
radiusd.conf[1942] Unknown module "eap".
radiusd.conf[1889] Failed to parse authenticate section

---

### Post by reauthor on 2007-06-26
Hy fide321..

I think that setup inside your  eap.conf file is problem...Can you put here your eap.conf

---

### Post by thavisak on 2007-06-26
Hi

I have same error :(, but I configure for EAP-TTLS. My eap.conf is

#       $Id: eap.conf,v 1.4.4.3 2006/04/28 18:25:03 aland Exp $
#
        eap {
                default_eap_type = ttls
                timer_expire     = 60
                ignore_unknown_eap_types = no
                cisco_accounting_username_bug = no

                gtc {
                        challenge = "test"
                        auth_type = PAP
                }

                tls {
                        private_key_password = test
                        private_key_file = ${raddbdir}/certs/masterkeys/master_cert.pem
                        certificate_file = ${raddbdir}/certs/masterkeys/master_cert.pem
                        CA_file = ${raddbdir}/certs/masterkeys/cacert.pem
                        dh_file = ${raddbdir}/certs/dh
                        random_file = ${raddbdir}/certs/random
                        fragment_size = 1024
                        include_length = yes

                }

                ttls {
                        default_eap_type = mschapv2
                        copy_request_to_tunnel = no
                        use_tunneled_reply = no
                }

                mschapv2 {
                }
        }

Please help me ...

---

### Post by reauthor on 2007-06-27
Hy,I did not tetsted EAP-TTLS yet.I have clients whit XP and Ubuntu.PEAP is protocol designed by Microsoft and Cysco and is more practical for me to use EAP-PEAP because of my XP clients..I will play whit ttls in the future...SORRY.

---

### Post by fide321 on 2007-06-27
Hi reauthor,
This is my eap.conf  file 
	eap {
		default_eap_type = peap
		timer_expire     = 60
		ignore_unknown_eap_types = no
		cisco_accounting_username_bug = no
		md5 {
		}
		leap {
		}
		gtc {
			auth_type = PAP
		}

		peap {
			default_eap_type = mschapv2
		}
		mschapv2 {
		}
	}
Is there any error ?
Thanks a lot for your help

---

### Post by fide321 on 2007-06-27
Sorry I see the TLS section (it was commented out). 
But now appears the follow error message when I try to runnn freeradius -X
rlm_eap_tls: Loading the certificate file as a chain
rlm_eap: SSL error error:0200100E:system library:fopen:Bad address
rlm_eap_tls: Error reading certificate file
rlm_eap: Failed to initialize type tls
radiusd.conf[10]: eap: Module instantiation failed. 
radiusd.conf[1942] Unknown module "eap".
radiusd.conf[1889] Failed to parse authenticate section.

---

### Post by reauthor on 2007-06-28
> **fide321 said:**
> Sorry I see the TLS section (it was commented out). 
But now appears the follow error message when I try to runnn freeradius -X
rlm_eap_tls: Loading the certificate file as a chain
rlm_eap: SSL error error:0200100E:system library:fopen:Bad address
rlm_eap_tls: Error reading certificate file
rlm_eap: Failed to initialize type tls
radiusd.conf[10]: eap: Module instantiation failed. 
radiusd.conf[1942] Unknown module "eap".
radiusd.conf[1889] Failed to parse authenticate section.

Did you compile freeradius from source code whit tls suport such as in this HOWTO or you install from ubuntu repos?Can you put here your all eap.conf so I can check if you missing something...

---

### Post by thavisak on 2007-06-28
Dear Reauthor

Today, I try to make clear install by install Ubuntu 7.04 Server.
Then follow the step to install FreeRadius.
Anyways, after I completed to build freeradius (#apt-src build freeradius) I found there are only some deb file on that directory and there is not "freeradius_1.1.3-3ubuntu1tls_i386.deb" file.
What happend and how to correct it?

The following are files I found that that directory.
##################################
root@ubuntu:~/build_freeradius# ls -l
total 3628
drwxr-xr-x 15 root root    4096 2007-06-28 16:30 freeradius-1.1.3
-rw-r--r--  1 root root   17141 2007-03-31 07:03 freeradius_1.1.3-3ubuntu1.diff.gz
-rw-r--r--  1 root root    1087 2007-03-31 07:03 freeradius_1.1.3-3ubuntu1.dsc
-rw-r--r--  1 root root    1724 2007-06-28 16:31 freeradius_1.1.3-3ubuntu1_i386.changes
-rw-r--r--  1 root root  774474 2007-06-28 16:31 freeradius_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root 2587376 2006-09-02 03:07 freeradius_1.1.3.orig.tar.gz
-rw-r--r--  1 root root  117042 2007-06-28 16:30 freeradius-dialupadmin_1.1.3-3ubuntu1_all.deb
-rw-r--r--  1 root root   32110 2007-06-28 16:31 freeradius-iodbc_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   32834 2007-06-28 16:31 freeradius-krb5_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   47464 2007-06-28 16:31 freeradius-ldap_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   31988 2007-06-28 16:31 freeradius-mysql_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   32480 2007-06-28 16:31 freeradius-postgresql_1.1.3-3ubuntu1_i386.deb
root@ubuntu:~/build_freeradius# 
###################################

---

### Post by reauthor on 2007-06-28
> **thavisak said:**
> Dear Reauthor

Today, I try to make clear install by install Ubuntu 7.04 Server.
Then follow the step to install FreeRadius.
Anyways, after I completed to build freeradius (#apt-src build freeradius) I found there are only some deb file on that directory and there is not "freeradius_1.1.3-3ubuntu1tls_i386.deb" file.
What happend and how to correct it?

The following are files I found that that directory.
##################################
root@ubuntu:~/build_freeradius# ls -l
total 3628
drwxr-xr-x 15 root root    4096 2007-06-28 16:30 freeradius-1.1.3
-rw-r--r--  1 root root   17141 2007-03-31 07:03 freeradius_1.1.3-3ubuntu1.diff.gz
-rw-r--r--  1 root root    1087 2007-03-31 07:03 freeradius_1.1.3-3ubuntu1.dsc
-rw-r--r--  1 root root    1724 2007-06-28 16:31 freeradius_1.1.3-3ubuntu1_i386.changes
-rw-r--r--  1 root root  774474 2007-06-28 16:31 freeradius_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root 2587376 2006-09-02 03:07 freeradius_1.1.3.orig.tar.gz
-rw-r--r--  1 root root  117042 2007-06-28 16:30 freeradius-dialupadmin_1.1.3-3ubuntu1_all.deb
-rw-r--r--  1 root root   32110 2007-06-28 16:31 freeradius-iodbc_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   32834 2007-06-28 16:31 freeradius-krb5_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   47464 2007-06-28 16:31 freeradius-ldap_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   31988 2007-06-28 16:31 freeradius-mysql_1.1.3-3ubuntu1_i386.deb
-rw-r--r--  1 root root   32480 2007-06-28 16:31 freeradius-postgresql_1.1.3-3ubuntu1_i386.deb
root@ubuntu:~/build_freeradius# 
###################################

in ~/build_freeradius/freeradius-1.1.3/debian/ find changelog file and add,something like this,dont change anything,just add this red lines



```
[COLOR="Red"]freeradius (1.1.3-3ubuntu1tls) feisty; urgency=low

  
  * Add tls support for compilation
  
 -- reauthor <reauthor@gmail.com>  Fri, 30 Mar 2007 20:22:40 +0200
[/COLOR]
freeradius (1.1.3-3) unstable; urgency=medium

  * Fix POSIX compliance problem in init script.  Closes: #403384. 

 -- Mark Hymers <mark@hymers.org.uk>  Sat, 16 Dec 2006 20:45:11 +0000....
```

---

### Post by fide321 on 2007-06-28
Hi Reathor
I compiled freeradius from source code  such as in this HOWTO . And this is my complete eap.conf. Thanks a lot for your help

# -*- text -*-
#
#  Whatever you do, do NOT set 'Auth-Type := EAP'.  The server
#  is smart enough to figure this out on its own.  The most
#  common side effect of setting 'Auth-Type := EAP' is that the
#  users then cannot use ANY other authentication method.
#
#	$Id: eap.conf,v 1.4.4.3 2006/04/28 18:25:03 aland Exp $
#
	eap {
		#  Invoke the default supported EAP type when
		#  EAP-Identity response is received.
		#
		#  The incoming EAP messages DO NOT specify which EAP
		#  type they will be using, so it MUST be set here.
		#
		#  For now, only one default EAP type may be used at a time.
		#
		#  If the EAP-Type attribute is set by another module,
		#  then that EAP type takes precedence over the
		#  default type configured here.
		#
		default_eap_type = peap

		#  A list is maintained to correlate EAP-Response
		#  packets with EAP-Request packets.  After a
		#  configurable length of time, entries in the list
		#  expire, and are deleted.
		#
		timer_expire     = 60

		#  There are many EAP types, but the server has support
		#  for only a limited subset.  If the server receives
		#  a request for an EAP type it does not support, then
		#  it normally rejects the request.  By setting this
		#  configuration to "yes", you can tell the server to
		#  instead keep processing the request.  Another module
		#  MUST then be configured to proxy the request to
		#  another RADIUS server which supports that EAP type.
		#
		#  If another module is NOT configured to handle the
		#  request, then the request will still end up being
		#  rejected.
		ignore_unknown_eap_types = no

		# Cisco AP1230B firmware 12.2(13)JA1 has a bug.  When given
		# a User-Name attribute in an Access-Accept, it copies one
		# more byte than it should.
		#
		# We can work around it by configurably adding an extra
		# zero byte.
		cisco_accounting_username_bug = no

		# Supported EAP-types

		#
		#  We do NOT recommend using EAP-MD5 authentication
		#  for wireless connections.  It is insecure, and does
		#  not provide for dynamic WEP keys.
		#
		md5 {
		}

		# Cisco LEAP
		#
		#  We do not recommend using LEAP in new deployments.  See:
		#  [http://www.securiteam.com/tools/5TP012ACKE.html](http://www.securiteam.com/tools/5TP012ACKE.html)
		#
		#  Cisco LEAP uses the MS-CHAP algorithm (but not
		#  the MS-CHAP attributes) to perform it's authentication.
		#
		#  As a result, LEAP *requires* access to the plain-text
		#  User-Password, or the NT-Password attributes.
		#  'System' authentication is impossible with LEAP.
		#
		leap {
		}

		#  Generic Token Card.
		#
		#  Currently, this is only permitted inside of EAP-TTLS,
		#  or EAP-PEAP.  The module "challenges" the user with
		#  text, and the response from the user is taken to be
		#  the User-Password.
		#
		#  Proxying the tunneled EAP-GTC session is a bad idea,
		#  the users password will go over the wire in plain-text,
		#  for anyone to see.
		#
		gtc {
			#  The default challenge, which many clients
			#  ignore..
			#challenge = "Password: "

			#  The plain-text response which comes back
			#  is put into a User-Password attribute,
			#  and passed to another module for
			#  authentication.  This allows the EAP-GTC
			#  response to be checked against plain-text,
			#  or crypt'd passwords.
			#
			#  If you say "Local" instead of "PAP", then
			#  the module will look for a User-Password
			#  configured for the request, and do the
			#  authentication itself.
			#
			auth_type = PAP
		}

		## EAP-TLS
		#
		#  To generate ctest certificates, run the script
		#
		#	../scripts/certs.sh
		#
		#  The documents on [http://www.freeradius.org/doc](http://www.freeradius.org/doc)
		#  are old, but may be helpful.
		#
		#  See also:
		#
		#  [http://www.dslreports.com/forum/remark,9286052~mode=flat](http://www.dslreports.com/forum/remark,9286052~mode=flat)
		#
		#tls {
			private_key_password = cteresepare90
			private_key_file = ${raddbdir}/certs/cert-srv.pem

			#  If Private key & Certificate are located in
			#  the same file, then private_key_file &
			#  certificate_file must contain the same file
			#  name.
		#	certificate_file = ${raddbdir}/certs/cert-srv.pem

			#  Trusted Root CA list
			CA_file = ${raddbdir}/certs/demoCA/cacert.pem
                        dh_file = ${raddbdir}/certs/dh
			random_file = ${raddbdir}/certs/random

			#
			#  This can never exceed the size of a RADIUS
			#  packet (4096 bytes), and is preferably half
			#  that, to accomodate other attributes in
			#  RADIUS packet.  On most APs the MAX packet
			#  length is configured between 1500 - 1600
			#  In these cases, fragment size should be
			#  1024 or less.
			#
		#	fragment_size = 1024

			#  include_length is a flag which is
			#  by default set to yes If set to
			#  yes, Total Length of the message is
			#  included in EVERY packet we send.
			#  If set to no, Total Length of the
			#  message is included ONLY in the
			#  First packet of a fragment series.
			#
		#	include_length = yes

			#  Check the Certificate Revocation List
			#
			#  1) Copy CA certificates and CRLs to same directory.
			#  2) Execute 'c_rehash <CA certs&CRLs Directory>'.
			#    'c_rehash' is OpenSSL's command.
			#  3) Add 'CA_path=<CA certs&CRLs directory>'
			#      to radiusd.conf's tls section.
			#  4) uncomment the line below.
			#  5) Restart radiusd
		#	check_crl = yes

		       #
		       #  If check_cert_issuer is set, the value will
		       #  be checked against the DN of the issuer in
		       #  the client certificate.  If the values do not
		       #  match, the cerficate verification will fail,
		       #  rejecting the user.
		       #
		#       check_cert_issuer = "/C=GB/ST=Berkshire/L=Newbury/O=My Company Ltd"

		       #
		       #  If check_cert_cn is set, the value will
		       #  be xlat'ed and checked against the CN
		       #  in the client certificate.  If the values
		       #  do not match, the certificate verification
		       #  will fail rejecting the user.
		       #
		       #  This check is done only if the previous
		       #  "check_cert_issuer" is not set, or if
		       #  the check succeeds.
		       #
		#	check_cert_cn = %{User-Name}
		#
			# Set this option to specify the allowed
			# TLS cipher suites.  The format is listed
			# in "man 1 ciphers".
		#	cipher_list = "DEFAULT"
		#}

		#  The TTLS module implements the EAP-TTLS protocol,
		#  which can be described as EAP inside of Diameter,
		#  inside of TLS, inside of EAP, inside of RADIUS...
		#
		#  Surprisingly, it works quite well.
		#
		#  The TTLS module needs the TLS module to be installed
		#  and configured, in order to use the TLS tunnel
		#  inside of the EAP packet.  You will still need to
		#  configure the TLS module, even if you do not want
		#  to deploy EAP-TLS in your network.  Users will not
		#  be able to request EAP-TLS, as it requires them to
		#  have a client certificate.  EAP-TTLS does not
		#  require a client certificate.
		#
		#ttls {
			#  The tunneled EAP session needs a default
			#  EAP type which is separate from the one for
			#  the non-tunneled EAP module.  Inside of the
			#  TTLS tunnel, we recommend using EAP-MD5.
			#  If the request does not contain an EAP
			#  conversation, then this configuration entry
			#  is ignored.
		#	default_eap_type = md5

			#  The tunneled authentication request does
			#  not usually contain useful attributes
			#  like 'Calling-Station-Id', etc.  These
			#  attributes are outside of the tunnel,
			#  and normally unavailable to the tunneled
			#  authentication request.
			#
			#  By setting this configuration entry to
			#  'yes', any attribute which NOT in the
			#  tunneled authentication request, but
			#  which IS available outside of the tunnel,
			#  is copied to the tunneled request.
			#
			# allowed values: {no, yes}
		#	copy_request_to_tunnel = no

			#  The reply attributes sent to the NAS are
			#  usually based on the name of the user
			#  'outside' of the tunnel (usually
			#  'anonymous').  If you want to send the
			#  reply attributes based on the user name
			#  inside of the tunnel, then set this
			#  configuration entry to 'yes', and the reply
			#  to the NAS will be taken from the reply to
			#  the tunneled request.
			#
			# allowed values: {no, yes}
		#	use_tunneled_reply = no
		#}

		#
		#  The tunneled EAP session needs a default EAP type
		#  which is separate from the one for the non-tunneled
		#  EAP module.  Inside of the TLS/PEAP tunnel, we
		#  recommend using EAP-MS-CHAPv2.
		#
		#  The PEAP module needs the TLS module to be installed
		#  and configured, in order to use the TLS tunnel
		#  inside of the EAP packet.  You will still need to
		#  configure the TLS module, even if you do not want
		#  to deploy EAP-TLS in your network.  Users will not
		#  be able to request EAP-TLS, as it requires them to
		#  have a client certificate.  EAP-PEAP does not
		#  require a client certificate.
		#
		peap {
			#  The tunneled EAP session needs a default
			#  EAP type which is separate from the one for
			#  the non-tunneled EAP module.  Inside of the
			#  PEAP tunnel, we recommend using MS-CHAPv2,
			#  as that is the default type supported by
			#  Windows clients.
			default_eap_type = mschapv2

			#  the PEAP module also has these configuration
			#  items, which are the same as for TTLS.
		#	copy_request_to_tunnel = no
		#	use_tunneled_reply = no

			#  When the tunneled session is proxied, the
			#  home server may not understand EAP-MSCHAP-V2.
			#  Set this entry to "no" to proxy the tunneled
			#  EAP-MSCHAP-V2 as normal MSCHAPv2.
		#	proxy_tunneled_request_as_eap = yes
		}

		#
		#  This takes no configuration.
		#
		#  Note that it is the EAP MS-CHAPv2 sub-module, not
		#  the main 'mschap' module.
		#
		#  Note also that in order for this sub-module to work,
		#  the main 'mschap' module MUST ALSO be configured.
		#
		#  This module is the *Microsoft* implementation of MS-CHAPv2
		#  in EAP.  There is another (incompatible) implementation
		#  of MS-CHAPv2 in EAP by Cisco, which FreeRADIUS does not
		#  currently support.
		#
		mschapv2 {
		}
	}

---

### Post by reauthor on 2007-06-29
> **fide321 said:**
> Hi Reathor
I compiled freeradius from source code  such as in this HOWTO . And this is my complete eap.conf. Thanks a lot for your help

# -*- text -*-
#
#  Whatever you do, do NOT set 'Auth-Type := EAP'.  The server
#  is smart enough to figure this out on its own.  The most
#  common side effect of setting 'Auth-Type := EAP' is that the
#  users then cannot use ANY other authentication method.
#
#	$Id: eap.conf,v 1.4.4.3 2006/04/28 18:25:03 aland Exp $
#
	eap {
		#  Invoke the default supported EAP type when
		#  EAP-Identity response is received.
		#
		#  The incoming EAP messages DO NOT specify which EAP
		#  type they will be using, so it MUST be set here.
		#
		#  For now, only one default EAP type may be used at a time.
		#
		#  If the EAP-Type attribute is set by another module,
		#  then that EAP type takes precedence over the
		#  default type configured here.
		#
		default_eap_type = peap

		#  A list is maintained to correlate EAP-Response
		#  packets with EAP-Request packets.  After a
		#  configurable length of time, entries in the list
		#  expire, and are deleted.
		#
		timer_expire     = 60

		#  There are many EAP types, but the server has support
		#  for only a limited subset.  If the server receives
		#  a request for an EAP type it does not support, then
		#  it normally rejects the request.  By setting this
		#  configuration to "yes", you can tell the server to
		#  instead keep processing the request.  Another module
		#  MUST then be configured to proxy the request to
		#  another RADIUS server which supports that EAP type.
		#
		#  If another module is NOT configured to handle the
		#  request, then the request will still end up being
		#  rejected.
		ignore_unknown_eap_types = no

		# Cisco AP1230B firmware 12.2(13)JA1 has a bug.  When given
		# a User-Name attribute in an Access-Accept, it copies one
		# more byte than it should.
		#
		# We can work around it by configurably adding an extra
		# zero byte.
		cisco_accounting_username_bug = no

		# Supported EAP-types

		#
		#  We do NOT recommend using EAP-MD5 authentication
		#  for wireless connections.  It is insecure, and does
		#  not provide for dynamic WEP keys.
		#
		md5 {
		}

		# Cisco LEAP
		#
		#  We do not recommend using LEAP in new deployments.  See:
		#  [http://www.securiteam.com/tools/5TP012ACKE.html](http://www.securiteam.com/tools/5TP012ACKE.html)
		#
		#  Cisco LEAP uses the MS-CHAP algorithm (but not
		#  the MS-CHAP attributes) to perform it's authentication.
		#
		#  As a result, LEAP *requires* access to the plain-text
		#  User-Password, or the NT-Password attributes.
		#  'System' authentication is impossible with LEAP.
		#
		leap {
		}

		#  Generic Token Card.
		#
		#  Currently, this is only permitted inside of EAP-TTLS,
		#  or EAP-PEAP.  The module "challenges" the user with
		#  text, and the response from the user is taken to be
		#  the User-Password.
		#
		#  Proxying the tunneled EAP-GTC session is a bad idea,
		#  the users password will go over the wire in plain-text,
		#  for anyone to see.
		#
		gtc {
			#  The default challenge, which many clients
			#  ignore..
			#challenge = "Password: "

			#  The plain-text response which comes back
			#  is put into a User-Password attribute,
			#  and passed to another module for
			#  authentication.  This allows the EAP-GTC
			#  response to be checked against plain-text,
			#  or crypt'd passwords.
			#
			#  If you say "Local" instead of "PAP", then
			#  the module will look for a User-Password
			#  configured for the request, and do the
			#  authentication itself.
			#
			auth_type = PAP
		}

		## EAP-TLS
		#
		#  To generate ctest certificates, run the script
		#
		#	../scripts/certs.sh
		#
		#  The documents on [http://www.freeradius.org/doc](http://www.freeradius.org/doc)
		#  are old, but may be helpful.
		#
		#  See also:
		#
		#  [http://www.dslreports.com/forum/remark,9286052~mode=flat](http://www.dslreports.com/forum/remark,9286052~mode=flat)
		#
		[COLOR="Red"]tls {
			private_key_password = cteresepare90
			private_key_file = ${raddbdir}/certs/cert-srv.pem[/COLOR]

			#  If Private key & Certificate are located in
			#  the same file, then private_key_file &
			#  certificate_file must contain the same file
			#  name.
			[COLOR="Red"]certificate_file = ${raddbdir}/certs/cert-srv.pem
[/COLOR]
			#  Trusted Root CA list
			CA_file = ${raddbdir}/certs/demoCA/cacert.pem
                        dh_file = ${raddbdir}/certs/dh
			random_file = ${raddbdir}/certs/random

			#
			#  This can never exceed the size of a RADIUS
			#  packet (4096 bytes), and is preferably half
			#  that, to accomodate other attributes in
			#  RADIUS packet.  On most APs the MAX packet
			#  length is configured between 1500 - 1600
			#  In these cases, fragment size should be
			#  1024 or less.
			#
		#	fragment_size = 1024

			#  include_length is a flag which is
			#  by default set to yes If set to
			#  yes, Total Length of the message is
			#  included in EVERY packet we send.
			#  If set to no, Total Length of the
			#  message is included ONLY in the
			#  First packet of a fragment series.
			#
		#	include_length = yes

			#  Check the Certificate Revocation List
			#
			#  1) Copy CA certificates and CRLs to same directory.
			#  2) Execute 'c_rehash <CA certs&CRLs Directory>'.
			#    'c_rehash' is OpenSSL's command.
			#  3) Add 'CA_path=<CA certs&CRLs directory>'
			#      to radiusd.conf's tls section.
			#  4) uncomment the line below.
			#  5) Restart radiusd
		#	check_crl = yes

		       #
		       #  If check_cert_issuer is set, the value will
		       #  be checked against the DN of the issuer in
		       #  the client certificate.  If the values do not
		       #  match, the cerficate verification will fail,
		       #  rejecting the user.
		       #
		#       check_cert_issuer = "/C=GB/ST=Berkshire/L=Newbury/O=My Company Ltd"

		       #
		       #  If check_cert_cn is set, the value will
		       #  be xlat'ed and checked against the CN
		       #  in the client certificate.  If the values
		       #  do not match, the certificate verification
		       #  will fail rejecting the user.
		       #
		       #  This check is done only if the previous
		       #  "check_cert_issuer" is not set, or if
		       #  the check succeeds.
		       #
		#	check_cert_cn = %{User-Name}
		#
			# Set this option to specify the allowed
			# TLS cipher suites.  The format is listed
			# in "man 1 ciphers".
		#	cipher_list = "DEFAULT"
		[COLOR="Red"]}[/COLOR]

		#  The TTLS module implements the EAP-TTLS protocol,
		#  which can be described as EAP inside of Diameter,
		#  inside of TLS, inside of EAP, inside of RADIUS...
		#
		#  Surprisingly, it works quite well.
		#
		#  The TTLS module needs the TLS module to be installed
		#  and configured, in order to use the TLS tunnel
		#  inside of the EAP packet.  You will still need to
		#  configure the TLS module, even if you do not want
		#  to deploy EAP-TLS in your network.  Users will not
		#  be able to request EAP-TLS, as it requires them to
		#  have a client certificate.  EAP-TTLS does not
		#  require a client certificate.
		#
		#ttls {
			#  The tunneled EAP session needs a default
			#  EAP type which is separate from the one for
			#  the non-tunneled EAP module.  Inside of the
			#  TTLS tunnel, we recommend using EAP-MD5.
			#  If the request does not contain an EAP
			#  conversation, then this configuration entry
			#  is ignored.
		#	default_eap_type = md5

			#  The tunneled authentication request does
			#  not usually contain useful attributes
			#  like 'Calling-Station-Id', etc.  These
			#  attributes are outside of the tunnel,
			#  and normally unavailable to the tunneled
			#  authentication request.
			#
			#  By setting this configuration entry to
			#  'yes', any attribute which NOT in the
			#  tunneled authentication request, but
			#  which IS available outside of the tunnel,
			#  is copied to the tunneled request.
			#
			# allowed values: {no, yes}
		#	copy_request_to_tunnel = no

			#  The reply attributes sent to the NAS are
			#  usually based on the name of the user
			#  'outside' of the tunnel (usually
			#  'anonymous').  If you want to send the
			#  reply attributes based on the user name
			#  inside of the tunnel, then set this
			#  configuration entry to 'yes', and the reply
			#  to the NAS will be taken from the reply to
			#  the tunneled request.
			#
			# allowed values: {no, yes}
		#	use_tunneled_reply = no
		#}

		#
		#  The tunneled EAP session needs a default EAP type
		#  which is separate from the one for the non-tunneled
		#  EAP module.  Inside of the TLS/PEAP tunnel, we
		#  recommend using EAP-MS-CHAPv2.
		#
		#  The PEAP module needs the TLS module to be installed
		#  and configured, in order to use the TLS tunnel
		#  inside of the EAP packet.  You will still need to
		#  configure the TLS module, even if you do not want
		#  to deploy EAP-TLS in your network.  Users will not
		#  be able to request EAP-TLS, as it requires them to
		#  have a client certificate.  EAP-PEAP does not
		#  require a client certificate.
		#
		peap {
			#  The tunneled EAP session needs a default
			#  EAP type which is separate from the one for
			#  the non-tunneled EAP module.  Inside of the
			#  PEAP tunnel, we recommend using MS-CHAPv2,
			#  as that is the default type supported by
			#  Windows clients.
			default_eap_type = mschapv2

			#  the PEAP module also has these configuration
			#  items, which are the same as for TTLS.
		#	copy_request_to_tunnel = no
		#	use_tunneled_reply = no

			#  When the tunneled session is proxied, the
			#  home server may not understand EAP-MSCHAP-V2.
			#  Set this entry to "no" to proxy the tunneled
			#  EAP-MSCHAP-V2 as normal MSCHAPv2.
		#	proxy_tunneled_request_as_eap = yes
		}

		#
		#  This takes no configuration.
		#
		#  Note that it is the EAP MS-CHAPv2 sub-module, not
		#  the main 'mschap' module.
		#
		#  Note also that in order for this sub-module to work,
		#  the main 'mschap' module MUST ALSO be configured.
		#
		#  This module is the *Microsoft* implementation of MS-CHAPv2
		#  in EAP.  There is another (incompatible) implementation
		#  of MS-CHAPv2 in EAP by Cisco, which FreeRADIUS does not
		#  currently support.
		#
		mschapv2 {
		}
	}

Look the red line and change it in you eap.conf..

---

### Post by thavisak on 2007-06-29
Dear Reauthor

Thank you very much for your advice, now I can install freeradius.
Anyways, after configure and start freeradius, I found another problem.
#freeradius -X
..
..
rlm_eap_tls: Loading the certificate file as a chain
rlm_eap: SSL error error:0200100E: system library:fopen:Bad address
rlm_eap_tls: Error reading certificate file
rlm_eap: Failed to initialize type tls
radiusd.conf[10]: eap: Module instantiation failed.
radiusd.conf[1949] Unknown module "eap".
radiusd.conf[1896] Failed to parse authenticate section
#

What's wrong with my program? :(

Help me please ... :(:(:(

---

### Post by reauthor on 2007-06-29
> **thavisak said:**
> Dear Reauthor

Thank you very much for your advice, now I can install freeradius.
Anyways, after configure and start freeradius, I found another problem.
#freeradius -X
..
..
rlm_eap_tls: Loading the certificate file as a chain
rlm_eap: SSL error error:0200100E: system library:fopen:Bad address
rlm_eap_tls: Error reading certificate file
rlm_eap: Failed to initialize type tls
radiusd.conf[10]: eap: Module instantiation failed.
radiusd.conf[1949] Unknown module "eap".
radiusd.conf[1896] Failed to parse authenticate section
#

What's wrong with my program? :(

Help me please ... :(:(:(

Did you made your own certificate?As I see you have problem whit certificate.Please put the default certificate(dont change default freeradius certificate before everything works ok)).In this section leave default configuration,just uncomment.

private_key_password = cteresepare90 
private_key_file = ${raddbdir}/certs/cert-srv.pem

# If Private key & Certificate are located in
# the same file, then private_key_file &
# certificate_file must contain the same file
# name.
certificate_file = ${raddbdir}/certs/cert-srv.pem

# Trusted Root CA list
CA_file = ${raddbdir}/certs/demoCA/cacert.pem
dh_file = ${raddbdir}/certs/dh
random_file = ${raddbdir}/certs/random

---

### Post by fide321 on 2007-06-29
Hi reathor thank you  I have made the changes but now apeears the follow error message:

rlm_eap_tls: Loading the certificate file as a chain
rlm_eap: SSL error error:06065064:digital envelope routines:EVP_DecryptFinal_ex:bad decrypt
rlm_eap_tls: Error reading private key file
rlm_eap: Failed to initialize type tls
radiusd.conf[10]: eap: Module instantiation failed. 
radiusd.conf[1942] Unknown module "eap".
radiusd.conf[1889] Failed to parse authenticate section.

---

### Post by reauthor on 2007-06-29
> **fide321 said:**
> Hi reathor thank you  I have made the changes but now apeears the follow error message:

rlm_eap_tls: Loading the certificate file as a chain
rlm_eap: SSL error error:06065064:digital envelope routines:EVP_DecryptFinal_ex:bad decrypt
rlm_eap_tls: Error reading private key file
rlm_eap: Failed to initialize type tls
radiusd.conf[10]: eap: Module instantiation failed. 
radiusd.conf[1942] Unknown module "eap".
radiusd.conf[1889] Failed to parse authenticate section.


Ok,it seems that you had been overwrite your default freeradius certiftcations,maybe it is easier way to remove completaly freeradius whit ```
sudo dpkg  -r  freeradius & sudo dpkg --purge freeradius
``` and than just install...I dont know..Sorry.

---

### Post by thavisak on 2007-07-04
Dear Reauthor

Thank you very much.
Follow your advise, I can start freeradius now and test by using #radtest test test localhost 0 testing123
It's work.

Anyways, can I test EAP/PEAP authentication from localhost; for example using command #radtest ? How to?
and if I want to test from client in windowXP, do I have to create new CA? How to?

Best regards,
Thavisak

---

### Post by thavisak on 2007-07-11
Hi Reauthor and fide321.

I'm now trying to test FreeRadius from windowXP client after test by radtest command.
I copy file cert-clt.der and install in window XP, but I was warm that it's expired since 2006. So, I design to create new certification by using OpenSSL. After create using CA.sh, I copy cert-srv.pem to ~/certs/ and cacert.pem to ~/certs/demoCA, then run freeradius -X

This time I get the same problem as fide321.
I was trying to re-install follow reauthor's advice, but after configure radiusd.conf and eap.conf and run freeradius -X, the same probme occur.

What's wrong?


error message:

rlm_eap_tls: Loading the certificate file as a chain
rlm_eap: SSL error error:06065064:digital envelope routines:EVP_DecryptFinal_ex:bad decrypt
rlm_eap_tls: Error reading private key file
rlm_eap: Failed to initialize type tls
radiusd.conf[10]: eap: Module instantiation failed. 
radiusd.conf[1942] Unknown module "eap".
radiusd.conf[1889] Failed to parse authenticate section.

---

### Post by eric_stewart on 2007-09-11
Just wanted to thank you for this marvelous how-to.  I too was frustrated at the lack of OpenSSL support in the version of FreeRADIUS from the standard 7.04 repositories.  I am a much happier camper now, since I now have WPA/WPA2-Enterprise working on my home network test setup.

I've got a link to my posting on this subject here: [http://www.breezy.ca/?q=node/220](http://www.breezy.ca/?q=node/220)
Note that I have a link in the article to LinuxJournal.com where there is a good how-to on setting up Windows XP to connect to authenticate to the FreeRADIUS server.

Again thanks!  It's efforts like yours that make Ubuntu not just an OS but also a community!

/Eric
webmaster, the Breezy! Site
[http://www.breezy.ca](http://www.breezy.ca)

---

### Post by ccornett on 2008-01-14
I ran into a problem early. I had already installed freeradius to another directory when I decided to follow your directions step-by-step, so I uninstalled it with synaptic. Then when I tried to download it with sudo apt-src install freeradius (also tried it logged in as root) I get the error E: source freeradius not found. When I do the apt-get and apt-src update I'm told they are already the most current versions.

Any idea what went wrong?

---

### Post by flade on 2008-01-29
Is this freeradius built with mysql support?



reg,

---

### Post by Usta_AsH on 2008-02-16
at the end of the step 1-4

"dpkg-buildpackage: source package is freeradius
dpkg-buildpackage: source version is 1.1.6-2
dpkg-buildpackage: source changed by reauthor <reauthor@gmail.com>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 1.1.6-2
dpkg-checkbuilddeps: Unmet build dependencies: Libssl-dev Libpq-dev
dpkg-checkbuilddeps: Build conflicts: libssl-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)
E: Building failed
"

---

### Post by Usta_AsH on 2008-02-18
hello how can I uninstall this application?

---

