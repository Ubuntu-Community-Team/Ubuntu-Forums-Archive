---
title: "HOWTO: Smart Card authentication for logins, e-mail, TrueCrypt and more!"
date: 2010-08-20
forum: Tutorials
---

### Post by Bachstelze on 2010-08-20
Because your machine hosts extremely sensitive data (or, more probably, just for the geek factor) passwords sometimes just don't cut it.  Thanks to the [OpenSC]("http://www.opensc-project.org/") project, Linux users can also use [Smart cards]("http://en.wikipedia.org/wiki/Smart_card") in lieu of passwords to authenticate against various services, which, in addition to being immune to dictionary or brute force attacks, just looks way cooler.  This guide will describe the steps needed to use Smart cards for various authentication and encryption purposes; most importantly logins (both console and graphical), e-mail signing and encryption, SSH remote logins, TrueCrypt file encryption, and more if I feel like it. ;)  I'd like to thank UF user Berduchwal for starting work (and getting me interested to it) in [this thread]("http://ubuntuforums.org/showthread.php?t=1447218").

This guide is licensed under the WTFPL: you can do whatever you want with it.  (The normal wording would be inappropriate for this forum, use your favourite search engine if you want to know more about it.)


[size="5"]**Getting Started**[/size]

The first section of this guide will describe the basic steps you will need to get your smart card ready to be used in various authentication procedures.  Each single application will be described in a separate post and linked at the end of this section.


[SIZE="4"]**The Hardware**[/SIZE]

First and foremost, you will obviously need the correct hardware.  It can be either a smart card and a smart card reader, or an USB token that provides the same functionality as a smart card, but plugs directly into an USB port, thus eliminating the need for an additional reader.  The OpenSC project's Wiki has a list of [supported smart cards and USB tokens]("http://www.opensc-project.org/opensc/wiki/SupportedHardware"), as well as a small list of [compatible readers]("http://www.opensc-project.org/opensc/wiki/CardReaders").

The hardware I will use for this guide is an Feitian EnterSafe smart card and SCR301 USB smart card reader.  [Gooze]("http://www.gooze.eu/") sells them as a bundle for 31,90 EUR plus shipping (ships only to the EU for legal reasons).


[SIZE="4"]**The Software**[/SIZE]

All the necessary software is in the Ubuntu repositories.  The packages you need are [font=monospace]opensc[/font], [font=monospace]pcsc-tools[/font], and [font=monospace]libccid[/font].  More packages might be needed for specific applications (e.g. PAM authentication), those will be covered in the relevant sections of this guide.

The OpenSC project strongly recommends using the PCSC driver. It is a good idea to set [font=monospace]reader_drivers[/font] to [font=monospace]pcsc[/font] in [font=monospace]/etc/opensc/opensc.conf[/font] so that OpenSC won't bother trying other drivers unsuccessfully.


[SIZE="4"]**First Steps**[/SIZE]

Now that you have your smart card, reader and all the packages, let's get to business.  First, make sure your reader is detected and supported.  First, the usual suspect when it comes to detecting USB devices:

```
firas@tsukino ~ % lsusb                   
Bus 004 Device 007: ID 096e:0503 Feitian Technologies, Inc. 
Bus 004 Device 004: ID 05ac:8213 Apple, Inc. 
Bus 004 Device 002: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 05ac:0237 Apple, Inc. 
Bus 003 Device 002: ID 05ac:8242 Apple, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 05ac:8403 Apple, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

My Feitian card reader appears.  The [font=monospace]opensc-tool[/font] command can give us more information:

```
firas@tsukino ~ % opensc-tool --list-readers      
Readers known about:
Nr.    Driver     Name
0      pcsc       Feitian SCR301 00 00

```

You will probably see some error messages in [font=monospace]**[COLOR="Red"]bold red[/COLOR]**[/font], don't worry, they're "normal" (i.e. I get them too, and it still works).  You can eliminate them by editing [font=monospace]/etc/opensc/opensc.conf[/font], uncommenting the [font=monospace]error_file[/font] line, and setting it to [font=monospace]/dev/null[/font].  Now to see whether your card is supported:

```
firas@tsukino ~ % opensc-tool --reader 0 --name
Card not present.
```

But insert the card first. ;)

```
firas@tsukino ~ % opensc-tool --reader 0 --name
entersafe

```

This is the name of your card.  If you run the command with the [font=monospace]-v[/font] (verbose) flag, it will also tell you the name of the driver your card uses:

```
firas@tsukino ~ % opensc-tool --reader 0 --name -v
Connecting to card in reader Feitian SCR301 00 00...
Using card driver entersafe.
Card name: entersafe
```

Now that we've made sure the card is supported, we can initialise it (roughly the same thing as formatting a filesystem) so we can store stuff on it:

```
firas@tsukino ~ % pkcs15-init -C --label "Firas Kraiem"
Using reader with a card: Feitian SCR301 00 00
New User PIN.
Please enter User PIN: 
Please type again to verify: 
Unblock Code for New User PIN (Optional - press return for no PIN).
Please enter User unblocking PIN (PUK): 
Please type again to verify: 

```

The label is optional, it will appear in some authentication prompts, so you probably want to put your name there.  Note that some smart cards, such as the Schlumberger CryptoFlex used on the [Quick Start]("http://www.opensc-project.org/opensc/wiki/QuickStart") page on the OpenSC wiki, will ask you for a "Security Officer" PIN.  This is because they support creating several users, each with his own User PIN, keys and data, that will be able to use the same smart card.  My EnterSafe, on the other hand, is single-user, so I am directly asked for the User PIN.  If your card is multi-users, you will have to create a user, as described on the wiki.

A small note on the codes: the PIN (Personal Identification Number) is the code you will need to enter when you use the smart card (for example when you store a key on it, or when you want to use a key).  The PUK (PIN Unlock Key) is used to reinitialise the PIN if you forget it or it gets compromised.

We can now see the structure of the card with:

```
firas@tsukino ~ % pkcs15-tool -D
Using reader with a card: Feitian SCR301 00 00
PKCS#15 Card [Firas Kraiem]:
	Version        : 1
	Serial number  : 2812504610040810
	Manufacturer ID: EnterSafe
	Last update    : 20100821125517Z
	Flags          : EID compliant

PIN [User PIN]
	Com. Flags: 0x3
	ID        : ff
	Flags     : [0x30], initialized, needs-padding
	Length    : min_len:4, max_len:16, stored_len:16
	Pad char  : 0x00
	Reference : 1
	Type      : ascii-numeric
	Path      : 3f005015

```


[SIZE="4"]**First Key**[/SIZE]

You generate a RSA key pair on your card with the [font=monospace]-G[/font] flag of [font=monospace]pkcs15-init[/font] (you will be asked for your PIN several times):

```
firas@tsukino ~ % pkcs15-init -G rsa/1024 --auth-id ff --label "My Private Key" --public-key-label "My Public Key"
Using reader with a card: Feitian SCR301 00 00
User PIN required.
Please enter User PIN: 
User PIN required.
Please enter User PIN: 
User PIN required.
Please enter User PIN: 
User PIN required.
Please enter User PIN: 

```

Replace 1024 with 2048 or 4096 for a longer key (if supported by your card).  Replace [font=monospace]ff[/font] with the auth-id of the user who will use the key (you can find a user's auth-id under his PIN section in the output of [font=monospace]pkcs15-tool -D[/font]).  Labels are, once again, optional.

We can use the same command as above to see our new keys in the card's structure:

```
firas@tsukino ~ % pkcs15-tool -D 
Using reader with a card: Feitian SCR301 00 00
PKCS#15 Card [Firas Kraiem]:
	Version        : 1
	Serial number  : 2812504610040810
	Manufacturer ID: EnterSafe
	Last update    : 20100821130157Z
	Flags          : EID compliant

PIN [User PIN]
	Com. Flags: 0x3
	ID        : ff
	Flags     : [0x30], initialized, needs-padding
	Length    : min_len:4, max_len:16, stored_len:16
	Pad char  : 0x00
	Reference : 1
	Type      : ascii-numeric
	Path      : 3f005015

Private RSA Key [My Private Key]
	Com. Flags  : 3
	Usage       : [0x4], sign
	Access Flags: [0x1D], sensitive, alwaysSensitive, neverExtract, local
	ModLength   : 1024
	Key ref     : 1
	Native      : yes
	Path        : 3f005015
	Auth ID     : ff
	ID          : 45

Public RSA Key [My Public Key]
	Com. Flags  : 2
	Usage       : [0x4], sign
	Access Flags: [0x0]
	ModLength   : 1024
	Key ref     : 0
	Native      : no
	Path        : 3f0050153045
	Auth ID     : 
	ID          : 45

```

Or we can use [font=monospace]--list-keys[/font] to see only the keys:

```
firas@tsukino ~ % pkcs15-tool --list-keys
Using reader with a card: Feitian SCR301 00 00
Private RSA Key [My Private Key]
	Com. Flags  : 3
	Usage       : [0x4], sign
	Access Flags: [0x1D], sensitive, alwaysSensitive, neverExtract, local
	ModLength   : 1024
	Key ref     : 1
	Native      : yes
	Path        : 3f005015
	Auth ID     : ff
	ID          : 45

firas@tsukino ~ % pkcs15-tool --list-public-keys
Using reader with a card: Feitian SCR301 00 00
Public RSA Key [My Public Key]
	Com. Flags  : 2
	Usage       : [0x4], sign
	Access Flags: [0x0]
	ModLength   : 1024
	Key ref     : 0
	Native      : no
	Path        : 3f0050153045
	Auth ID     : 
	ID          : 45

```

If you need to send the public key to other people, you can retrieve it with:

```
firas@tsukino ~ % pkcs15-tool --read-public-key 45
Using reader with a card: Feitian SCR301 00 00
-----BEGIN PUBLIC KEY-----
MIGfMA0GCSqGSIb3DQEBAQUAA4GNADCBiQKBgQClRLcuudoW62NzWO7s/HSMqhjR
edFkxqxKdTuNksi+oCG5QDmZtzOuAX5eCtXLKiAyt8cSNQWUhOlS9jK/5vpwMyee
+qWQuh2jA0wfi6eoNIWGz5ZdjDn/b2BwvsOZUtpNKOtMwnceLWtbJCcg5nTd3DyV
X+qfJsGatuLB0CgHQwIDAQAB
-----END PUBLIC KEY-----

```

Of course, replace 45 with the ID of the key you want to read (you can get it, once again, in the output of [font=monospace]pkcs15-tool -D[/font]).

Note that there is normally no way to extract the private key from the card.  If you need a backup, you must generate the key on your computer, store it on your card (see below) and back it up in a safe location (which could be on another card).

Our RSA key is now ready to be used.  I will cover each application in a separate message, so stay tuned. ;)


[size=5]**Applications**[/size]

[PAM Authentication]("http://ubuntuforums.org/showthread.php?t=1557180#2"): for logins (both console and graphical), [font=monospace]sudo[/font] and more.
[OpenSSH Authentication]("http://ubuntuforums.org/showthread.php?t=1557180#3")
[TrueCrypt]("http://ubuntuforums.org/showthread.php?t=1557180#4")


[SIZE="5"]**Other Stuff**[/SIZE]

This section will document other procedures that are not specific to a single application.


[size="4"]**Using a pre-existing key**[/size]

In some circumstances, you might want to use a pre-existing key instead of generating one directly on your card.  This can be useful, for example, if you need a backup of your key, or if you need to distribute the key to several users.

Starting with a freshly initialised card:

```
firas@tsukino ~ % pkcs15-tool -D                                                
Using reader with a card: Feitian SCR301 00 00
PKCS#15 Card [My Smart Card]:
	Version        : 1
	Serial number  : 2812504610040810
	Manufacturer ID: EnterSafe
	Last update    : 20100822165926Z
	Flags          : EID compliant

PIN [User PIN]
	Com. Flags: 0x3
	ID        : ff
	Flags     : [0x30], initialized, needs-padding
	Length    : min_len:4, max_len:16, stored_len:16
	Pad char  : 0x00
	Reference : 1
	Type      : ascii-numeric
	Path      : 3f005015

```

Generate the new key on your computer (of course skip this step if you want to use a key you already have):

```
firas@tsukino ~ % openssl genrsa -des3 -out mykey.key 1024
Generating RSA private key, 1024 bit long modulus
...........++++++
...++++++
e is 65537 (0x10001)
Enter pass phrase for mykey.key:
Verifying - Enter pass phrase for mykey.key:

```

And store the key on your card with the [font=monospace]-S[/font] flag of [font=monospace]pkcs15-init[/font]:

```
firas@tsukino ~ % pkcs15-init -S mykey.key --auth-id ff --label "My Private Key" --public-key-label "My Public Key"
Using reader with a card: Feitian SCR301 00 00
Please enter passphrase to unlock secret key: 
User PIN required.
Please enter User PIN: 
User PIN required.
Please enter User PIN: 
User PIN required.
Please enter User PIN: 
User PIN required.
Please enter User PIN: 

```

We can see the key in the output of [font=monospace]pkcs15-tool -D[/font]:

```
firas@tsukino ~ % pkcs15-tool -D
Using reader with a card: Feitian SCR301 00 00
PKCS#15 Card [My Smart Card]:
	Version        : 1
	Serial number  : 2812504610040810
	Manufacturer ID: EnterSafe
	Last update    : 20100822170433Z
	Flags          : EID compliant

PIN [User PIN]
	Com. Flags: 0x3
	ID        : ff
	Flags     : [0x30], initialized, needs-padding
	Length    : min_len:4, max_len:16, stored_len:16
	Pad char  : 0x00
	Reference : 1
	Type      : ascii-numeric
	Path      : 3f005015

Private RSA Key [My Private Key]
	Com. Flags  : 3
	Usage       : [0x4], sign
	Access Flags: [0x1D], sensitive, alwaysSensitive, neverExtract, local
	ModLength   : 1024
	Key ref     : 1
	Native      : yes
	Path        : 3f005015
	Auth ID     : ff
	ID          : 45

Public RSA Key [My Public Key]
	Com. Flags  : 2
	Usage       : [0x4], sign
	Access Flags: [0x0]
	ModLength   : 1024
	Key ref     : 0
	Native      : no
	Path        : 3f0050153045
	Auth ID     : 
	ID          : 45

```


[size=4]**Reinitialise your card**[/size]

If you want to reinitialise your card and start again, just use the same initialisation command as above, but add the [font=monospace]-E[/font] flag:

```
firas@tsukino ~ % pkcs15-init -E -C --label "Firas Kraiem"
Using reader with a card: Feitian SCR301 00 00
New User PIN.
Please enter User PIN: 
Please type again to verify: 
Unblock Code for New User PIN (Optional - press return for no PIN).
Please enter User unblocking PIN (PUK): 
Please type again to verify: 

```

Needless to say, the keys stored on the card will be lost (if you didn't back them up).


[size="4"]**OpenSSL**[/size]

You can use the private key stored on your card with OpenSSL wherever you can use an on-disk key.  Among other things, you can sign files, decrypt files encrypted with your public key, or generate X.509 certificates for your key.  Since this is not an OpenSSL guide, I will not describe those operations in detail, you can refer to the OpenSSL page in the [Ubuntu Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/certificates-and-security.html") if you are not familiar with them, the syntax is the same (except for the necessary command flags to tell OpenSSL to use your smart card, see below).

First, install the package [font=monospace]libengine-pkcs11-openssl[/font]. Then fire up the OpenSSL prompt and initialise the smart card engine with this long command (copy-and-paste is your friend):

```
firas@tsukino ~ % openssl
OpenSSL> engine dynamic -pre SO_PATH:/usr/lib/engines/engine_pkcs11.so -pre ID:pkcs11 -pre LIST_ADD:1 -pre LOAD -pre MODULE_PATH:opensc-pkcs11.so
(dynamic) Dynamic engine loading support
[Success]: SO_PATH:/usr/lib/engines/engine_pkcs11.so
[Success]: ID:pkcs11
[Success]: LIST_ADD:1
[Success]: LOAD
[Success]: MODULE_PATH:opensc-pkcs11.so
Loaded: (pkcs11) pkcs11 engine
OpenSSL> 
```

*TODO: Is there a way to automate that?*

You can now run the desired OpenSSL commands.  To use the key stored on your smart card, you must add [font=monospace]-keyform engine -engine pkcs11[/font] to your command, and use [font=monospace]id_XX[/font] as the value for the [font=monospace]-key[/font] flag (where [font=monospace]XX[/font] is the ID of your key).  For example, here's how to generate a self-signed X.509 certificate (which will be useful also for PAM authentication, among other things):

```
OpenSSL> req -new -x509 -days 365 -keyform engine -engine pkcs11 -key id_45 -out mysmartcard.cert.pem
[...]
OpenSSL> quit
```

You probably want to store the certificate on the card, this is done with the [font=monospace]-X[/font] flag of [font=monospace]pkcs15-init[/font]:

```
firas@tsukino ~ % pkcs15-init -X mysmartcard.cert.pem --auth-id ff --id 45 --format pem
Using reader with a card: Feitian SCR301 00 00
User PIN required.
Please enter User PIN: 
User PIN required.
Please enter User PIN: 
```

As usual, replace [font=monospace]ff[/font] with the auth-id of the user, and [font=monospace]45[/font] with the ID of the key.

---

### Post by Bachstelze on 2010-08-21
[size=5]**PAM Authentication**[/size]


PAM (Pluggable Authentication Modules) is an authentication framework that uses modules to authenticate users using a wide variety of methods.  A PKCS#11 PAM module exists, which allows using smart cards to authenticate against any service that uses PAM.  The most obvious usage of PAM is system logins, either console or graphical, but a lof of other services, for example [font=monospace]sudo[/font], use it (you can have a look in [font=monospace]/etc/pam.d[/font] to see all currently installed services that use PAM).

The PKCS#11 PAM module can be found in the [font=monospace]libpam-pkcs11[/font] package in the repositories.

Several methods can be used to "map" a smart card to a user, I will not describe them all here.  The only method I will cover is [font=monospace]pwent[/font], which will check the CN (Common Name) field of the X.509 certificate associated with a key, and grant access only if it matches either the login name or the real name of the user.  Other mapping methods are documented [here]("http://www.opensc-project.org/doc/pam_pkcs11/pam_pkcs11.html").


[size=4]**Initial Configuration**[/size]

The package does not do any initial configuration for you, so you will have to do it yourself.  First, create the configuration directory.  The module expects it to be at [font=monospace]/etc/pam_pkcs11[/font], so it's a good idea to put it there:

```
sudo mkdir /etc/pam_pkcs11
```

Copy the default config file in the dir:

```
zcat /usr/share/doc/libpam-pkcs11/examples/pam_pkcs11.conf.example.example.gz | sudo tee /etc/pam_pkcs11/pam_pkcs11.conf
```

Create some additional directories.  [font=monospace]cacerts[/font] will store the certificates of trusted CAs: a certificate will only be accepted if it has been signed by one of those CAs.  [font=monospace]crls[/font] will store the Certificate Revocation Lists sent by the CAs, to let the PAM module know which certificates are no longer valid (revoked).

```
sudo mkdir /etc/pam_pkcs11/cacerts /etc/pam_pkcs11/crls
```

Since we will use the [font=monospace]pwent[/font] mapper, edit the [font=monospace]use_mappers[/font] line in [font=monospace]/etc/pam_pkcs11/pam_pkcs11.conf[/font] to list only [font=monospace]pwent[/font].

If you have not done so already, generate an X.509 certificate for the key stored on your smart card and store it on the card as well, as described at the bottom of [post #1]("http://ubuntuforums.org/showthread.php?t=1557180#1").  Remember that the Common Name (CN) field will be used to match the certificate to your account, so make sure to put either your login or your real name in that field (or at least, your real name as stored on the system, if you don't know it, it's on your line in [font=monospace]/etc/passwd[/font], you can safely edit the file if you want to change it).

Finally, copy the certificate of the CA that signed your own certificate (if your certificate is self-signed, that's the certificate itself) into [font=monospace]/etc/pam_pkcs11/cacerts[/font] and rehash the list of CA certificates with:

```
cd /etc/pam_pkcs11/cacerts
sudo pkcs11_make_hash_link
```


[size=4]**First Test: [font=monospace]sudo[/font]**[/size]

We will first test PAM authentication with [font=monospace]sudo[/font].  It is a good idea to test with [font=monospace]sudo[/font] first because you will not have to log out and try to log back in in order to test your configuration.

Edit [font=monospace]/etc/pam.d/sudo[/font]. It will look like this:

```
#%PAM-1.0

@include common-auth
@include common-account

session required pam_permit.so
session required pam_limits.so

```

Modify it like this:

```
#%PAM-1.0

auth sufficient pam_pkcs11.so

@include common-auth
@include common-account

session required pam_permit.so
session required pam_limits.so

```

Test:

```
firas@tsukino ~ % sudo -i
Please insert your Smart card or enter your username.
Found the Smart card.
Welcome Firas Kraiem (User PIN)!
Smart card PIN: 
tsukino ~ # 

```

All right!  Edit [font=monospace]/etc/pam.d/sudo[/font] back to its original state, we will configure PAM to use your smart card for all login authentication mechanisms.


[size=4]**Global Login Configuration**[/size]

If you looked closely at [font=monospace]/etc/pam.d/sudo[/font], you saw that it includes [font=monospace]common-auth[/font].  Actually, all login services ([font=monospace]gdm[/font], [font=monospace]login[/font], [font=monospace]samba[/font]...) include this file, so we can just add our [font=monospace]pam_pkcs11[/font] module to it, and it will get used for all login purposes.

**NOTE:** Ubuntu uses your password for a lot of things (too many things, if you ask me).  In particular, you will have a problem if you use the "encrypted home directory" feature, because the system needs your password to decrypt your home directory: since you will not enter your password when using your smart card to authenticate, the system will not be able to automatically decrypt your home directory when you login.  The most visible result of this is that X logins will fail.  A workaround is to first switch to a virtual console, login and mount your home directory manually with [font=monospace]ecryptfs-mount-private[/font].  You will then be able to switch back to gdm and login to your X session.  A fix would be to somehow store your password on the smart card and use it to decrypt your home directory.  Probably possible, but will require some work...  The same goes for your "keyring".

Edit [font=monospace]/etc/pam.d/common-auth[/font].  It will look like this:

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]  pam_unix.so nullok_secure
auth    [success=1 default=ignore]  pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth    requisite           pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional    pam_ecryptfs.so unwrap
# end of pam-auth-update config

```

Modify it like this:

```
#
# /etc/pam.d/common-auth - authentication settings common to all services
#
# This file is included from other service-specific PAM config files,
# and should contain a list of the authentication modules that define
# the central authentication scheme for use on the system
# (e.g., /etc/shadow, LDAP, Kerberos, etc.).  The default is to use the
# traditional Unix authentication mechanisms.
#
# As of pam 1.0.1-6, this file is managed by pam-auth-update by default.
# To take advantage of this, it is recommended that you configure any
# local modules either before or after the default block, and use
# pam-auth-update to manage selection of other modules.  See
# pam-auth-update(8) for details.

auth    [success=3 default=ignore]  pam_pkcs11.so

# here are the per-package modules (the "Primary" block)
auth    [success=2 default=ignore]  pam_unix.so nullok_secure
auth    [success=1 default=ignore]  pam_winbind.so krb5_auth krb5_ccache_type=FILE cached_login try_first_pass
# here's the fallback if no module succeeds
auth    requisite           pam_deny.so
# prime the stack with a positive return value if there isn't one already;
# this avoids us returning an error just because nothing sets a success code
# since the modules above will each just jump around
auth    required            pam_permit.so
# and here are more per-package modules (the "Additional" block)
auth    optional    pam_ecryptfs.so unwrap
# end of pam-auth-update config

```

With this configuration, smart card authentication will be tried first, and if it fails, PAM will fall back to normal password authentication.  You can also disable password authentication for your account (the same way Ubuntu "disables" the root account) with:

```
sudo passwd -l `whoami`
```

And smart card authentication will be required (you will still be prompted for a password if it fails, but the password will always fail).

Note that graphical applications that need your password (e.g. [font=monospace]gksudo[/font]) will display the same prompt for password and smart card authentication.  If you use smart card authentication, enter your smart card PIN, not your password.


[size=4]**Other Services?**[/size]

I don't really use any other service that uses PAM so I can't really test it, but other individual services should be configurable in  the same way as [font=monospace]sudo[/font] above.  Feel free to report any success or failure in this thread.

---

### Post by Bachstelze on 2010-08-21
[size=5]**OpenSSH Authentication**[/size]

You can use the private key stored on your smart card to authenticate on a remote OpenSSH server using key-based authentication.  If you are not familiar with OpenSSH key-based authentication, the Ubuntu Server Guide has [a page]("https://help.ubuntu.com/10.04/serverguide/C/openssh-server.html") about it. 

PKCS#11 support was added in OpenSSH 5.4.  Maverick works fine (it has OpenSSH 5.5), but Lucid only has OpenSSH 5.3, so if you are using Lucid, you will need to install at least OpenSSH 5.4.  Note that smart card support is only needed on the client; the server can be running any version of OpenSSH.

The first thing is to get your public key in SSH format, you get it with the [font=monospace]--read-ssh-key[/font] flag of [font=monospace]pkcs15-tool[/font]:

```
firas@tsukino ~ % pkcs15-tool --read-ssh-key 45
Using reader with a card: Feitian SCR301 00 00
1024 65537 116055431367766515871214384037749817043573194021104735948712734191299536751118486318441621788122833567021065145378319790342737488231697603237477940918138523371729036365495709912942009088721246775459940528092248876288819267234423917543765877278987095909905664147689601191223161580183068940665102413370315245379
ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAAAgQClRLcuudoW62NzWO7s/HSMqhjRedFkxqxKdTuNksi+oCG5QDmZtzOuAX5eCtXLKiAyt8cSNQWUhOlS9jK/5vpwMyee+qWQuh2jA0wfi6eoNIWGz5ZdjDn/b2BwvsOZUtpNKOtMwnceLWtbJCcg5nTd3DyVX+qfJsGatuLB0CgHQw==

```

Only the last line of output interests us, copy it to your [font=monospace]~/.ssh/authorized_keys[/font] on the server, just like you would any other key.

Try connecting to the server.  You need to pass the [font=monospace]-I[/font] flag to [font=monospace]ssh[/font] to let it know where the PKCS#11 library is located:

```
firas@tsukino ~ % ssh -I /usr/lib/opensc-pkcs11.so itsuki.fkraiem.org
Enter PIN for 'Firas Kraiem (User PIN)': 
Linux itsuki 2.6.32-24-generic #39-Ubuntu SMP Wed Jul 28 06:07:29 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.1 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

0 packages can be updated.
0 updates are security updates.

No mail.
Last login: Sat Aug 21 18:44:30 2010 from ichigo.fkraiem.org

```

In order to not have to pass the [font=monospace]-I[/font] flag every time, you can add this line to your [font=monospace]~/.ssh/config[/font] (or to [font=monospace]/etc/ssh/ssh_config[/font] to apply it to all users):

```
PKCS11Provider /usr/lib/opensc-pkcs11.so
```

---

### Post by Bachstelze on 2010-08-22
[size=5]**TrueCrypt**[/size]

Configuring TrueCrypt to use your smart card as a key is pretty straightforward.  The first thing to do is tell TrueCrypt where the PKCS#11 provider library is located: you do that in Settings > Security Tokens, the library is at [font=monospace]/usr/lib/opensc/opensc-pkcs11.so[/font].  For increased security, you will probably also want to check the box below it to force TrueCrypt to log out of your card after your encrypted volume has been mounted.

If you are already familiar with using keyfiles in TrueCrypt, using a smart card works the same way, except the file will be stored on your card, not on the disk.


[size=4]**On a new volume**[/size]

Create your new volume as usual, until you reach the "password" step.  Check the "Use keyfiles" box, and click the "Keyfiles" button.  You probably want to generate a random keyfile to store on your card, so click the "Generate Random Keyfile" button, and store the generated keyfile somewhere on your disk.  Then click "Add Token Files"; a window will appear, with all the keyfiles stored on your smart card.  So far, there is none, so click "Import Keyfile to Token", and select the keyfile you just created.  Click OK in the window that appears (unless you want to store the file under a different name on your card), select the keyfile and click OK again, and again.  At this point, you probably want to delete the keyfile from your drive (you can use the [font=monospace]shred[/font] command to do it securely).

You may also enter a password for your volume.  If you do, *both* the keyfile (here, it means the smart card) and the password will be required to mount the volume.

You may also use several keyfiles.  In that case *all* keyfiles (and the password if there is one) will be required to mount the volume.  You may want to do this, for example, to have multi-factor authentication, with one keyfile stored in a hidden location on the drive, and one on your smart card: or if the volume contains secrets shared between several users (with each user having one of the keyfiles on his own card, all users must be present to decrypt the volume).

The remaining step (volume formatting) is done as usual.


[size=4]**On an existing volume**[/size]

If your volume already uses keyfiles and they are small enough to fit on your card, you can just transfer the files to your smart card as described above.  If the keyfiles are too large, you will have to remove them from your volume with Volume > Remove all keyfiles from volume (after your volume is mounted), and generate a new set of keyfiles to store on your card.  (Note that removing keyfiles from your volume can take a couple minutes.)

If your volume doesn't use keyfiles (or you have removed them because they were too large to fit on your card), you will have to generate new keyfiles for it.  Mount your volume and click Volume > Add/Remove Keyfiles.  Enter the password for your volume in the "Password" box, check the "Use keyfiles" box under "New", and click the "Keyfiles" button next to it.  Generate the keyfile(s) and store them on your card as described in the previous section, and click OK (this can also take a while).  Both the keyfile(s) and the password will now be required to mount the voume (if you want to remove the password and use only the keys, you can do so by clicking Volumes > Change Volume Passwords.


[size=4]**Mounting a volume**[/size]

This is also pretty straightforward.  After you have selected the volume and clicked mount, enter the volume password (if there is one), check the "Use keyfiles" box, and click the "Keyfiles" button.  Add all the keyfiles (with "Add keyfile" for an on-disk keyfile, and "Add token files" for a keyfile on your smartcard) and click OK.

---

### Post by yeleek on 2010-08-28
Been away - hence delay.  Very pleasing.  Thanks Bachstelze

---

### Post by Bachstelze on 2010-08-28
Sadly, I'm struggling to get it working with GnuPG.  Basically, GnuPG doesn't have built-in PKCS#11 support (and probably never will), so getting it to work is a bit of a hack... It supports OpenPGP smart cards out of the box, but they are way less flexible (1024-bit keys FTL).

---

### Post by yeleek on 2010-11-23
Hi,

Still messing around with this when i get a chance.  Have you had any joy using it with email clients?  Specifically thinking Thunderbird and the 'Master password for software security device'?

Thanks

---

### Post by Bachstelze on 2010-12-13
> **yeleek said:**
> Hi,

Still messing around with this when i get a chance.  Have you had any joy using it with email clients?  Specifically thinking Thunderbird and the 'Master password for software security device'?

Thanks

Still no joy with GnuPG. Storing S/MIME certificates for Firefox and Thunderbird on a card is easy, though. Not sure what you mean about the Master password, AFAIK it is not possible to use a card instead of a password for this.

---

### Post by srf21c on 2010-12-20
> **Bachstelze said:**
> GnuPG doesn't have built-in PKCS#11 support (and probably never will), so getting it to work is a bit of a hack... It supports OpenPGP smart cards out of the box, but they are way less flexible (1024-bit keys FTL).

The newer [[COLOR="Blue"]OpenPGP v2.0 smart cards[/COLOR]]("http://g10code.com/p-card.html") support 2048 bit RSA keys.

---

### Post by Torombolo on 2010-12-20
looks fun... i got my self a winter project now :)

---

### Post by devrandmom on 2011-02-09
Hi,
Thanks a lot for a very nice tutorial! It seems that it is actually possible to use a pkcs15 smart card with GPG (as opposed to the openpgp card).
I haven't had the opportunity to try it yet (I just ordered a few smartcards from Gooze) but it seems that it can be done using a pkcs11 plugin for gpg: [http://gnupg-pkcs11.sourceforge.net/support.html](http://gnupg-pkcs11.sourceforge.net/support.html)

Also this link might be useful: [http://rainerkeller.de/etoken.html](http://rainerkeller.de/etoken.html)
Even though it documents the necessary steps for the aladin etoken, much of it should still apply.

I someone manages to get it to work, please keep us posted!

/J

---

### Post by Bachstelze on 2011-02-09
> **devrandmom said:**
> 
I haven't had the opportunity to try it yet (I just ordered a few smartcards from Gooze) but it seems that it can be done using a pkcs11 plugin for gpg: [http://gnupg-pkcs11.sourceforge.net/support.html](http://gnupg-pkcs11.sourceforge.net/support.html)

Yes, I know about gnupg-pkcs11, this is what I have been struggling with. As I said, it's a bit of a hack, so it doesn't seem very reliable. I had issues at some point in the process of making it recognize the keys on the smart card, and I haven't been able to track the problem down.

> **devrandmom said:**
> Also this link might be useful: [http://rainerkeller.de/etoken.html](http://rainerkeller.de/etoken.html)
Even though it documents the necessary steps for the aladin etoken, much of it should still apply.


Thanks, I'm going to have a look at it whan I get the time. Classes have started again, so I don't have a lot of it right now...

---

### Post by stupid_for_a_file on 2011-06-18
hello there,

first of all thanks a lot for this very complete guidance. I'm a beginner, so I still had some difficulties getting the hardware to work etc.

I am using an openpgp 1.1 card. I managed to get 3 keys on it. my objective would be to use it for login.

I had little luck with pkcs-... , I used gpg to create the keys.

anyway, now I would need to export a certificate. this is where I fail at the moment. I tried

```
gpgsm --gen-key >x.pem

   (3) Existing key from card

then chose the third key,

   (1) sign, encrypt

Really create request? (y/N) y
Now creating certificate request.  This may take a while ...
gpgsm: about to sign CSR for key: &76D93C191A5829154E5330D85585B4F652757F8E
gpgsm: certificate request created
Ready.  You should now send this request to your CA.

```

the file created like this is not accepted when trying to load it:

```
root@x:/etc/pam_pkcs11/cacerts# pkcs11_make_hash_link
we got a problem with: x.crt

```

OK, I know this has so far nothing to do with the howto, just wanted to show both my approaches. as far I understood from the little info, the above should be OK, by the way.

anyway, I also walked the line with the howto. this looks as follows:

```
OpenSSL> engine dynamic -pre SO_PATH:/usr/lib/engines/engine_pkcs11.so -pre ID:pkcs11 -pre LIST_ADD:1 -pre LOAD -pre MODULE_PATH:opensc-pkcs11.so
(dynamic) Dynamic engine loading support
[Success]: SO_PATH:/usr/lib/engines/engine_pkcs11.so
[Success]: ID:pkcs11
[Success]: LIST_ADD:1
[Success]: LOAD
[Success]: MODULE_PATH:opensc-pkcs11.so
Loaded: (pkcs11) pkcs11 engine
OpenSSL> req -new -x509 -days 365 -keyform engine -engine pkcs11 -key id_03 -out x.pem
engine "pkcs11" set.
failed to enumerate slots
PKCS11_get_private_key returned NULL
unable to load Private Key
9314:error:80002005:PKCS11 library:PKCS11_enum_slots:General Error:p11_slot.c:312:
9314:error:26096080:engine routines:ENGINE_load_private_key:failed loading private key:eng_pkey.c:126:
error in req

```
here I got stuck, I found no solution to overcome this.

the card is accessible by

```
pkcs15-tool --read-public-key 03
```

strangely to me, here I am asked for the admin PIN.

I hope someone sees my mistake and show me how I can export and re-import that certificate.

---

### Post by Bachstelze on 2011-06-18
As its name implies, pam_pkcs11 will only work witk PKCS#11 cards, not with OpenPGP cards. The two standards are AFAIK not compatible (hence the difficulty of using PKCS#11 cards with GnuPG).

---

### Post by stupid_for_a_file on 2011-06-18
thanks for the rapid answer. as you see I am that noob. I just had this card and wanted to make use of it...

I just ordered a Feitian card.

---

### Post by stupid_for_a_file on 2011-06-23
hello again.

i got a feitian card. on lucid i had to install opensc 0.12.1 to make it work. i also had to copy over stuff from /usr/local/bin and /usr/local/lib to /usr/bin and /usr/lib. this just for the sake of the record.

ok, so i initialized the card. the next step is exactly the same, where i got stuck with the other card:

```
OpenSSL> engine dynamic -pre SO_PATH:/usr/lib/engines/engine_pkcs11.so -pre ID:pkcs11 -pre LIST_ADD:1 -pre LOAD -pre MODULE_PATH:opensc-pkcs11.so
(dynamic) Dynamic engine loading support
[Success]: SO_PATH:/usr/lib/engines/engine_pkcs11.so
[Success]: ID:pkcs11
[Success]: LIST_ADD:1
[Success]: LOAD
[Success]: MODULE_PATH:opensc-pkcs11.so
Loaded: (pkcs11) pkcs11 engine
OpenSSL> req -new -x509 -days 365 -keyform engine -engine pkcs11 -key id_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx -out mysmartcard.cert.pem
engine "pkcs11" set.
Found empty token; 
PKCS11_get_private_key returned NULL
unable to load Private Key
12695:error:26096080:engine routines:ENGINE_load_private_key:failed loading private key:eng_pkey.c:126:
error in req

```

is this something i messed up in my environment? shall i better start on another machine? thanks.

---

### Post by Bachstelze on 2011-06-23
> **stupid_for_a_file said:**
> hello again.

i got a feitian card. on lucid i had to install opensc 0.12.1 to make it work. i also had to copy over stuff from /usr/local/bin and /usr/local/lib to /usr/bin and /usr/lib. this just for the sake of the record.

You shouldn't have done that. By copying files around, you probably overwrote something important. Also it worked in Lucid with the OpenSC version from the repos when I wrote the tutorial, so it definitely should still work now. You should have posted the error message you got with the version from the repos, because now, it's hard to tell where the error comes from since your installation is potentially broken.

---

### Post by stupid_for_a_file on 2011-06-24
you won't see me giving up... so i started to follow the howto step-by-step on a clean 10.04 64-bit machine. there are packages removed from the machine, but not anything which is related to this (i hope).

so the first note is "to add myself to the scard group". this group did not exist after installing the packages opensc pcsc-tools libccid. i did not do that yet, but i guess the commands are:

addgroup scard
addgroup yourname scard

i carried on skipping the steps with initializing the card, because that was done properly on the other machine already.

after listing the id i went on to openssl to request the certificate, but loading the engine failed:

```
OpenSSL> engine dynamic -pre SO_PATH:/usr/lib/engines/engine_pkcs11.so -pre ID:pkcs11 -pre LIST_ADD:1 -pre LOAD -pre MODULE_PATH:opensc-pkcs11.so
(dynamic) Dynamic engine loading support
[Success]: SO_PATH:/usr/lib/engines/engine_pkcs11.so
[Success]: ID:pkcs11
[Success]: LIST_ADD:1
[Failure]: LOAD
7363:error:25066067:DSO support routines:DLFCN_LOAD:could not load the shared library:dso_dlfcn.c:162:filename(/usr/lib/engines/engine_pkcs11.so): /usr/lib/engines/engine_pkcs11.so: cannot open shared object file: No such file or directory
7363:error:25070067:DSO support routines:DSO_load:could not load the shared library:dso_lib.c:244:
7363:error:260B6084:engine routines:DYNAMIC_LOAD:dso not found:eng_dyn.c:450:
[Failure]: MODULE_PATH:opensc-pkcs11.so
7363:error:260AC089:engine routines:INT_CTRL_HELPER:invalid cmd name:eng_ctrl.c:134:
7363:error:260AB089:engine routines:ENGINE_ctrl_cmd_string:invalid cmd name:eng_ctrl.c:316:
OpenSSL> 
```


here i figured out i need ```
libengine-pkcs11-openssl
```. i installed it, and then the engine got properly loaded. then i wanted to reauest the certificate:

```
OpenSSL> req -new -x509 -days 365 -keyform engine -engine pkcs11 -key id_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx -out mysmartcard.cert.pem
invalid engine "pkcs11"
8663:error:25066067:DSO support routines:DLFCN_LOAD:could not load the shared library:dso_dlfcn.c:162:filename(/usr/lib/ssl/engines/libpkcs11.so): /usr/lib/ssl/engines/libpkcs11.so: cannot open shared object file: No such file or directory
8663:error:25070067:DSO support routines:DSO_load:could not load the shared library:dso_lib.c:244:
8663:error:260B6084:engine routines:DYNAMIC_LOAD:dso not found:eng_dyn.c:450:
8663:error:2606A074:engine routines:ENGINE_by_id:no such engine:eng_list.c:415:id=pkcs11
8663:error:25066067:DSO support routines:DLFCN_LOAD:could not load the shared library:dso_dlfcn.c:162:filename(libpkcs11.so): libpkcs11.so: cannot open shared object file: No such file or directory
8663:error:25070067:DSO support routines:DSO_load:could not load the shared library:dso_lib.c:244:
8663:error:260B6084:engine routines:DYNAMIC_LOAD:dso not found:eng_dyn.c:450:
no engine specified
unable to load Private Key
error in req
OpenSSL> q
```


this libpkcs11.so is not found on the filesystem. here i thought i would ask you before i do something inappropriate. thanks a lot.

---

### Post by Bachstelze on 2011-06-24
> **stupid_for_a_file said:**
> you won't see me giving up...

That's the spirit. :) I am going to try later today on a Lucid system because what you say puzzles me. I will tell you what I find.

---

### Post by stupid_for_a_file on 2011-06-24
i solved this one...

```
root@masodik:/usr/lib/ssl/engines# cp engine_pkcs11.so libpkcs11.so
```

...and then i got the following error:

```
[opensc-pkcs11] iso7816.c:99:iso7816_check_sw: Security status not satisfied
[opensc-pkcs11] card-entersafe.c:901:entersafe_compute_with_prkey: internal set security env failed: Security status not satisfied
[opensc-pkcs11] sec.c:53:sc_compute_signature: returning with: Security status not satisfied
[opensc-pkcs11] pkcs15-sec.c:273:sc_pkcs15_compute_signature: sc_compute_signature() failed: Security status not satisfied

```

this i could solve with re-commenting the line i uncommented in the beginning:

```
nano /etc/opensc/opensc.conf 
```

```
#lock_login = false;
```


now i have a certificate how nice. i keep fighting tomorrow, i guess.

---

### Post by Bachstelze on 2011-06-24
Yeah, I forgot to mention libengine-pkcs11-openssl, fixed. And the scard group does not exist, fixed that too, I probably installed some other package that creates it when I wrote the guide. However, after installing libengine-pkcs11-openssl, I don't need to copy any files.

---

### Post by stupid_for_a_file on 2011-06-25
ok, i carried on with first trying to get sudo work:

```
juzer@masodik:~$ sudo -i
Please insert your Smart card or enter your username.
Found the Smart card.
Welcome juzer juzer (User PIN)!
Smart card PIN: 
ERROR:pam_pkcs11.c:537: no valid certificate which meets all requirements found
[sudo] password for juzer:
``` 

```
pkcs11_inspect
``` says:
```
Printing data for mapper pwent:
juzer juzer
```


i changed opensc.conf, and uncommented the ```
lock_login = false;
``` line, but this does not make any difference. what next?

---

### Post by Bachstelze on 2011-06-25
Try increasing the debug value in opensc.conf, it should give a bit more info about what went wrong.

---

### Post by Bachstelze on 2011-06-25
> **stupid_for_a_file said:**
> 
```
pkcs11_inspect
``` says:
```
Printing data for mapper pwent:
juzer juzer
```

Double-check in /etc/passwd that this is actually what your real name field says, because for me, there were three commas added after it.

---

### Post by stupid_for_a_file on 2011-06-26
this is it. /etc/passwd looks as follows:

```
juzer:x:1000:1000:juzer juzer,,,:/home/juzer:/bin/bash
```

this i changed now to:

```
juzer:x:1000:1000:juzer juzer:/home/juzer:/bin/bash
```

and it works. there are a few lines of error printed, but i got sudo.

i will see now to get login working, and then to reconstruate all this on another clean system to make sure i can do it on my own.

i also ordered now an expresscard reader to make all this more convenient.

i am already very pleased with the result, and again thankful to you for working on this with me.

---

### Post by dhinu on 2011-07-26
hi,

i am trying to authenticate wpa supplicant with smart card for the network access with my Free radius server. i would like to know the steps involved to install and configure with my ubuntu lucid machine. The card reader, am using is hardware Omnikey CardMan 3121 USB and the rsa card is OpenPGP Card v2.

thanks in advance,

cheers,
D.

---

### Post by Bachstelze on 2011-07-26
> **dhinu said:**
> hi,

i am trying to authenticate wpa supplicant with smart card for the network access with my Free radius server. i would like to know the steps involved to install and configure with my ubuntu lucid machine. The card reader, am using is hardware Omnikey CardMan 3121 USB and the rsa card is OpenPGP Card v2.

thanks in advance,

cheers,
D.

This thread in general only deals with OpenSC and PKCS#11 cards, not OpenPGP cards. Also, I have not looked at Radius yet, but feel free to report if you find out how to make it work.

---

### Post by dhinu on 2011-08-09
hi,

its me again, now am using Feitian PKI card. In my lucid machine i already installed openssl 1.0.0a to create certificates for EAP authentication methods and now the problem is, when i tried to load engine_pkcs11 to create and store client certificate in smartcard for smartcard authentication, i get the following errors even after installing necessary libraries like libengine_pkcs11-openssl,


OpenSSL> engine dynamic -pre SO_PATH:/usr/lib/engines/engine_pkcs11.so -pre ID:pkcs11 -pre LIST_ADD:1 -pre LOAD -pre MODULE_PATH:/usr/lib/opensc-pkcs11.so
(dynamic) Dynamic engine loading support
[Success]: SO_PATH:/usr/lib/engines/engine_pkcs11.so
[Success]: ID:pkcs11
[Success]: LIST_ADD:1
[Failure]: LOAD
14248680:error:260B606D:engine routines:DYNAMIC_LOAD:init failed:eng_dyn.c:521:
[Failure]: MODULE_PATH:/usr/lib/opensc-pkcs11.so
14248680:error:260AC089:engine routines:INT_CTRL_HELPER:invalid cmd name:eng_ctrl.c:134:
14248680:error:260AB089:engine routines:ENGINE_ctrl_cmd_string:invalid cmd name:eng_ctrl.c:316:


is that my openssl version is not supported by the pkcs engine..? how to come out of this....

thanks in advance,
D.

---

### Post by Bachstelze on 2011-08-09
I have not tried with OpenSSL 1.0.0. I will give it a try as soon as I can get my hands on my smartcard and tell you what I find.

---

### Post by dhinu on 2011-08-10
thanks, by the way i saw a rebuild version of engine_pkcs11 for openssl 1.0.0 in,

[https://launchpad.net/ubuntu/+source/engine-pkcs11/0.1.8-2build1](https://launchpad.net/ubuntu/+source/engine-pkcs11/0.1.8-2build1)

does it make any sense to reinstall the libengine_pkcs11-openssl by this one...

cheers,
D.

---

### Post by Bachstelze on 2011-08-10
Certainly. The one from the repos is compiled with the OpenSSL version also from the repos, so it makes sense that ig you use a different OpenSSL version, you need a different PKCS#11 engine too.

---

### Post by dhinu on 2011-08-12
hi,

sorry for replying late, now i able to load the module opensc-pcs11.so after installing the rebuild version of pkcs11 engine and when i was about to create the certificate, it couldn't load the libpkcs11.so from the path, so i copied engine_pkcs11.so the directory /usr/local/lib/engines/ as libpkcs11.so as it needs to be there, but when i again tried creating certificate i get the following error,

OpenSSL> req -new -x509 -days 365 -keyform engine -engine pkcs11 -key id_xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx -out mysmartcard.cert.pem
unable to load module (null)
can't use that engine
3070696:error:260B806D:engine routines:ENGINE_TABLE_REGISTER:init failed:eng_table.c:174:
no engine specified
unable to load Private Key
error in req
 
again it shows unable to load the module, here i thought i could ask you before i go further....

many thanks,
D.

---

### Post by dhinu on 2011-08-13
hi,

now i can load pkcs11 engine and module opensc-pkcs11.so, i get the following errors when i tried creating certificates,

Organizational Unit Name (eg, section) []:testbed
Common Name (eg, YOUR name) [CA_dhinu]:CA_dhinu
Email Address [d.gunasekaran@gmail.com]:d.gunasekaran@gmail.com
problems making Certificate Request
10197736:error:0B07807C:x509 certificate routines:X509_PUBKEY_set:method not supported:x_pubkey.c:112:
Segmentation fault

i didn't get any clue to come out of this, i would like to hear from you regarding this...

thanks in advance,
Dhinu.

---

### Post by Bachstelze on 2011-08-15
It worked for me but I compiled OpenSSL 1.0 and the PKCS#11 engine from source. Maye there's a problem with the package you've been using.

---

### Post by stupid_for_a_file on 2011-10-25
hello, i'm back again.

the smartcard setup for my home machines is productive a while now, and i'm more than happy with the results. just to give an example: without the smart card i would have needed my 3 year old to memorize a password like 

"3DQEBAQUAA4GNADCBiQKBgQClRLcuudoW62NzWO7s/HSMqhjR
edFkxqxKdTuNksi+oCG5QDmZtzOuAX5eCtXLKiAyt8cSNQWUhOlS9jK/5vpwMyee
+qWQuh2jA0wfi6eoNIWGz5ZdjDn/b2BwvsOZUtpNKOtMwnce"

it's better with the pin for sure. thanks again.


now i would like to make the setup complete. the only thing missing is the full disk encryption, or encrypted lvm. truecrypt was great with windows & pre-boot auth, which is sadly not available for linux.

i googled and googled several times, but the only reference of a working setup i found here [http://blog.fraggod.net/2010/4/LUKS-dm-crypt-rootfs-without-password-via-smartcard]("http://blog.fraggod.net/2010/4/LUKS-dm-crypt-rootfs-without-password-via-smartcard") is obviously too high level for me.

thus, i encourage **Bachstelze**, or anyone else being a Jedi of this subject to share the details of a possible setup. i would be glad to test and use it if someone could lead me through the steps.

(as far i see this is the same point to which the owners of gooze.eu got)

---

### Post by Bachstelze on 2011-10-25
I am not really familiar with FDE yet so don't expect anything about it from me any time soon, I don't really have the time to go through it now.

---

### Post by stupid_for_a_file on 2011-10-31
you know you won't see me giving up this near to the finish line.

i can wait another few years, maybe in the meantime someone will come up with a working setup.

thanks anyway for letting know.

---

### Post by nikoker on 2012-10-08
Great How-to, I made it work. However this is a local authentication. 
Does anyone know how to get it work with Kerberos authentication? I have a windows server with the CA installed there. I would like to know how to specify the domain, the server IP adress and the rest of settings. Does anyone know how to do that or provide maybe a source describing how to do that in the web?

---

