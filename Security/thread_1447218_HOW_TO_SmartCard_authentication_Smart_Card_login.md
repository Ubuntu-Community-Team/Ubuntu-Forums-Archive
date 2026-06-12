---
title: "HOW TO: SmartCard authentication Smart Card login"
date: 2010-04-05
forum: Security
---

### Post by Berduchwal on 2010-04-05
Dear All,

Some time ago I decided to set up smart card authentication to login to my Ubuntu machine. What I wanted to achieve is use this smart card to:
- Login 
- authenticated PGP signature into emails
- enable Firefox stored passwords to be used
- use when calling sudo

My system:
```

Ubuntu 9.10 karmic
Linux 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 04:38:19 UTC 2010 x86_64 GNU/Linux

```

So what I did is I purchased necessary hardware:
1) Akasa - internal smart card reader AK-ICR-05 ([Amazon]("http://www.amazon.co.uk/Akasa-AK-ICR-05-Internal-Card-Reader/dp/B001KZH6EC"))
Card reader is plugged directly into main board USB pin header not usb port. 
lsusb:
```
Bus 001 Device 002: ID 0bda:0161 Realtek Semiconductor Corp. Mass Stroage Device

```
Interesting spelling error here :)

2) Aladdin eToken Pro Smartcard 32k - security smart card ([Alladdin]("http://www.aladdin.com/etoken/devices/pro-smartcard.aspx"))

There are few things that need:
1) Hardware with drivers
2) Middleware to handle smartcard
3) Application to use smartcard

There are some applications that are needed and you can install those by:

```
sudo apt-get install coolkey pcscd pcsc-tools pkg-config libpam-pkcs11 opensc libengine-pkcs11-openssl
```

and then you can see if your reader and card are recognised:
```
:~$ pcsc_scan
PC/SC device scanner
V 1.4.15 (c) 2001-2009, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.4.102
Scanning present readers...
0: MSI StarReader SMART (20070818000000000) 00 00

Mon Apr  5 09:42:22 2010
 Reader 0: MSI StarReader SMART (20070818000000000) 00 00
  Card state: Card removed, 

```
I inserted the card (the one described above):
```
Mon Apr  5 09:44:34 2010
 Reader 0: MSI StarReader SMART (20070818000000000) 00 00
  Card state: Card inserted, 
  ATR: 3B F2 98 00 FF C1 10 31 FE 55 C8 03 15

ATR: 3B F2 98 00 FF C1 10 31 FE 55 C8 03 15
+ TS = 3B --> Direct Convention
+ T0 = F2, Y(1): 1111, K: 2 (historical bytes)
  TA(1) = 98 --> Fi=512, Di=12, 42.6667 cycles/ETU
    93750 bits/s at 4 MHz, fMax for Fi = 5 MHz => 117187 bits/s
  TB(1) = 00 --> VPP is not electrically connected
  TC(1) = FF --> Extra guard time: 255 (special value)
  TD(1) = C1 --> Y(i+1) = 1100, Protocol T = 1 
-----
  TC(2) = 10 --> Work waiting time: 960 x 16 x (Fi/F)
  TD(2) = 31 --> Y(i+1) = 0011, Protocol T = 1 
-----
  TA(3) = FE --> IFSC: 254
  TB(3) = 55 --> Block Waiting Integer: 5 - Character Waiting Integer: 5
+ Historical bytes: C8 03
  Category indicator byte: C8 (proprietary format)
+ TCK = 15 (correct checksum)

Possibly identified card (using /usr/share/pcsc/smartcard_list.txt):
3B F2 98 00 FF C1 10 31 FE 55 C8 03 15
	Siemens CardOS M 4.01 (SLE66CX320P)

```

when card removed:

```
Mon Apr  5 09:46:14 2010
 Reader 0: MSI StarReader SMART (20070818000000000) 00 00
  Card state: Card removed, 

```


Now time to get opensc (SmartCard management software) to see my card reader.

```
$ opensc-tool --list-readers
[opensc-tool] reader-pcsc.c:1015:pcsc_detect_readers: returning with: No readers found
No smart card readers found.

```

There is apparently a known bug lurking here and it is solved by:
```
sudo gedit /etc/opensc/opensc.conf
```

search for the line starting with 'provider_library' and remove # and modify it to be:
```
		provider_library = /lib/libpcsclite.so.1
```

Then also
search for the line starting with 'reader_drivers' and remove # and modify it to be:
```
	        reader_drivers = pcsc;
```

after doing this we can try again:
```
$ opensc-tool --list-readers
Readers known about:
Nr.    Driver     Name
0      pcsc       MSI StarReader SMART (20070818000000000) 00 00
```

Next thing to do is test if the card is detected:

```
$ opensc-tool --reader 0 --atr
3b:f2:98:00:ff:c1:10:31:fe:55:c8:03:15

$ opensc-tool --reader 0 --name
CardOS M4

$ opensc-explorer
OpenSC Explorer version 0.11.8
Using reader with a card: MSI StarReader SMART (20070818000000000) 00 00
OpenSC [3F00]> ls
FileID	Type  Size
[6666]	  DF 26285	Name: AKS

```

It appears that this one is!


Next step is to initialise the card.

```
$ pkcs15-init --create-pkcs15
About to create PKCS #15 meta structure.
New Security Officer PIN (Optional - press return for no PIN).
Please enter Security Officer PIN: 
Please type again to verify: 
Unblock Code for New User PIN (Optional - press return for no PIN).
Please enter User unblocking PIN (PUK): 
Please type again to verify: 

```

and then the user pin
```
$ pkcs15-init --store-pin --auth-id 01 --label "Your Name"
Using reader with a card: MSI StarReader SMART (20070818000000000) 00 00
New User PIN.
Please enter User PIN: 
Please type again to verify: 
Unblock Code for New User PIN (Optional - press return for no PIN).
Please enter User unblocking PIN (PUK): 
Please type again to verify: 
Security officer PIN required.
Please enter Security officer PIN: 
```

RSA private key:
```
$ pkcs15-init --generate-key rsa/1024 --auth-id 01
Using reader with a card: MSI StarReader SMART (20070818000000000) 00 00
User PIN required.
Please enter User PIN: 
Security officer PIN required.
Please enter Security officer PIN: 
Security officer PIN required.
Please enter Security officer PIN: 


$ pkcs15-tool --list-keys
Using reader with a card: MSI StarReader SMART (20070818000000000) 00 00
Private RSA Key [Private Key]
	Com. Flags  : 3
	Usage       : [0x4], sign
	Access Flags: [0x1D], sensitive, alwaysSensitive, neverExtract, local
	ModLength   : 1024
	Key ref     : 16
	Native      : yes
	Path        : 3f005015
	Auth ID     : 01
	ID          : 45

```

Now public key using openssl:
```
$openssl
```

and then:
```
OpenSSL> [COLOR="Red"]engine dynamic -pre SO_PATH:/usr/lib/engines/engine_pkcs11.so -pre ID:pkcs11 -pre LIST_ADD:1 -pre LOAD -pre MODULE_PATH:opensc-pkcs11.so
[/COLOR]
(dynamic) Dynamic engine loading support
[Success]: SO_PATH:/usr/lib/engines/engine_pkcs11.so
[Success]: ID:pkcs11
[Success]: LIST_ADD:1
[Success]: LOAD
[Success]: MODULE_PATH:opensc-pkcs11.so
Loaded: (pkcs11) pkcs11 engine

OpenSSL> [COLOR="Red"]req -engine pkcs11 -new -key id_45 -keyform engine -x509 -out cert.pem -text[/COLOR]
engine "pkcs11" set.
[COLOR="Lime"]PKCS#11 token PIN: [/COLOR]
You are about to be asked to enter information that will be incorporated
into your certificate request.
What you are about to enter is what is called a Distinguished Name or a DN.
There are quite a few fields but you can leave some blank
For some fields there will be a default value,
If you enter '.', the field will be left blank.
-----
Country Name (2 letter code) [AU]:
State or Province Name (full name) [Some-State]:
Locality Name (eg, city) []:
Organization Name (eg, company) [Internet Widgits Pty Ltd]:
Organizational Unit Name (eg, section) []:
Common Name (eg, YOUR name) []:
Email Address []:
OpenSSL> exit

```

You need to copy&paste the red highlighted parts and put user pin in the green part.

You can verify self signing of the certificate by:
```
$ openssl verify -CAfile cert.pem cert.pem
cert.pem: OK

```

openssl public certificate needs to be stored on the card now:

```
$pkcs15-init --store-certificate cert.pem --auth-id 01 --id 45 --format pem
Using reader with a card: MSI StarReader SMART (20070818000000000) 00 00
User PIN required.
Please enter User PIN: 
Security officer PIN required.
Please enter Security officer PIN:
```

Card is ready to be used now!
Next step is to get different application and services using it!

Thunderbird with OpenPGP
1) Adding Security Device 
1.1) Thunderbird click on: Preferences, Advances, Security Devices, Load
1.2) Type in name: OpenSC PKCS#11 Module
1.3) Type in filename: /usr/lib/opensc-pkcs11.so
1.4) Click OK, OK, OK
See attached file for graphical help (Thunderbird.png).
This does not do the trick yet but I am working on it.

Additional reading:
List of card readers and their descriptions: [http://www.hjreggel.net/cardspeed/speed-readers.html](http://www.hjreggel.net/cardspeed/speed-readers.html)
Lots of resources about SmartCards: [http://www.opensc-project.org/](http://www.opensc-project.org/)
Large part of this HOW TO is based on: [http://www.opensc-project.org/opensc/wiki/QuickStart](http://www.opensc-project.org/opensc/wiki/QuickStart)
Supported hardware: [http://www.opensc-project.org/opensc/wiki/SupportedHardware](http://www.opensc-project.org/opensc/wiki/SupportedHardware)
Supported applications: [http://www.opensc-project.org/opensc/wiki/ApplicationSupport](http://www.opensc-project.org/opensc/wiki/ApplicationSupport)

---

### Post by Objekt on 2010-04-06
I don't have any answers for you yet, but I am definitely interested in this topic.  I keep meaning to set up smartcard auth on my home machine so I can get to some work stuff without having to come in the office.  

I have a document on setting up smartcards on Linux, but it is so old (2006) that I doubt most of it applies any more.  

I expect the major problem will be finding a smartcard reader for which Linux drivers exist.  That is about the only reason hardware ever fails to work in Linux, and is usually due to manufacturer non-cooperation.

---

### Post by Berduchwal on 2010-04-08
I am about half way thought now :)
Hopefully the rest will go smoothly.

Regarding drivers there is a list of supported hardware in the additional reading above check it out. Alternatively you can go for the same hardware as I did. It can be bought using eBay and Amazon.

---

### Post by yeleek on 2010-04-08
Very interested in this!

Can you please continue to update this thread with your discoveries?

Thanks

---

### Post by Objekt on 2010-04-16
Well, so much for that.  All the take-home smartcard readers here at work are already checked out.  Our organization has grown hugely in the past year, so spare gear is much more scarce than it once was.  

Not only that, but I am changing jobs within a few weeks, so I will no longer have anything to log into with a smartcard, or the smartcard to do it with.   Maybe I'll give it a go if my next job requires smartcard-access websites.

---

### Post by yeleek on 2010-06-16
Berduchwal - Any further updates or progress on this?  Still interested :)

Thanks

---

### Post by Bachstelze on 2010-08-19
I'll send Berduchwal an email to see if he's still able to update it. Otherwise I could "take it over".

*EDIT:* Only a PM actually, he has disabled forum emails.

---

### Post by yeleek on 2010-08-19
> **Bachstelze said:**
> I'll send Berduchwal an email to see if he's still able to update it. Otherwise I could "take it over".

*EDIT:* Only a PM actually, he has disabled forum emails.

Sounds good! :)

---

### Post by Berduchwal on 2010-08-19
Thank you for all of the responses.
To be honest I got stuck with the TrueCrypt and put this aside for a while.

Now however it is becoming important again for my work. I plan to upgrade to 10.04 next week and subsequently will commit half day a week to get it all running.

Anyhow in a meanwhile help is appreciated.

---

### Post by Bachstelze on 2010-08-19
If you want to use OpenSC for SSH authentication, Lucid has OpenSSH 5.3p, which does not support smartcards.  I backported OpenSSH 5.5p from Maverick on [my PPA]("https://launchpad.net/~firas/+archive/ppa").

---

### Post by Bachstelze on 2010-08-20
Got PAM authentication working too (works for logins, both console and graphical, sudo and a lot of other things--see /etc/pam.d for the list of PAM services).  Works fine in Lucid, probably earlier versions too.

@Berduchwal: I'll start a thread in Tutorial & Tips, send me a PM/email if you would like to add something.

---

### Post by Bachstelze on 2010-08-21
HOWTO posted here: [http://ubuntuforums.org/showthread.php?t=1557180](http://ubuntuforums.org/showthread.php?t=1557180)

---

