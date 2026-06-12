---
title: "Open VPN cannot run ./build-ca"
date: 2014-04-22
forum: Server Platforms
---

### Post by dcorwin822 on 2014-04-22
When I try to run I get the following error:
```
error on line 198 of /etc/openvpn/easy-rsa/openssl-1.0.0.cnf
140224783447712:error:0E065068:configuration file routines:STR_COPY:variable has no value:conf_def.c:618:line 198

```

line 198 of openssl-1.0.0.cnf reads:
```
subjectAltName=$ENV::KEY_ALTNAMES
```

---

### Post by dcorwin822 on 2014-04-22
I'm a idiot. I just added the following line to the vars file. working correctly now.

export KEY_ALTNAMES="something"

---

### Post by jeremiah-l-marks on 2014-05-21
you may call yourself an idiot, but your comment certinaly helped me. Thank you.

---

### Post by Jacob_Tennant on 2014-06-19
I have the same problem and tried adding exportKEY_ALTNAMES="something" to my VARS file but I am still getting the same error?

---

### Post by spamjunkie on 2014-06-19
> **Jacob_Tennant said:**
> I have the same problem and tried adding exportKEY_ALTNAMES="something" to my VARS file but I am still getting the same error?


yep it works. THANKS OP!

make sure there is a space between export and key in your VARS... unlike your post.

then rerun:

 source vars
./clean-all
./build-ca

---

### Post by linuxuser600 on 2014-07-08
This is the first time I have logged in since probably about 2009. I had to login because your post helped me out so much. I have been searching forever for this answer!! And for that I thank you. :KS

---

### Post by shag00 on 2014-08-22
Ditto above comment.

---

### Post by darren-hobbs-l on 2014-09-26
> **dcorwin822 said:**
> I'm a idiot. I just added the following line to the vars file. working correctly now.

export KEY_ALTNAMES="something"

Has nobody asked why a clean install of openVPN is broken out of the box? That doesn't seem right.

---

### Post by nerdtron on 2014-09-28
> **darren-hobbs-l said:**
> Has nobody asked why a clean install of openVPN is broken out of the box? That doesn't seem right.

Haha...now that you pointed it out a fresh install is indeed broken, at least on my experience. I expected things to be configured after the installation that I did not even question the fact that the config is broken on first trial of generating certificates.
I mean, it doesn't even ship with a default working config.

---

### Post by robobenklein on 2014-10-22
On [https://help.ubuntu.com/14.04/serverguide/openvpn.html](https://help.ubuntu.com/14.04/serverguide/openvpn.html) the steps should also be updated to include setting that variable. This thread helped me!

---

### Post by krupier on 2014-12-15
> **robobenklein said:**
> On [https://help.ubuntu.com/14.04/serverguide/openvpn.html](https://help.ubuntu.com/14.04/serverguide/openvpn.html) the steps should also be updated to include setting that variable. This thread helped me!

It doesn't! It is this very server guide that led me here!

In my case exporting KEY_ALTNAMES didn't help. Or should I say it did, but I had to do something more. As I don't live in the US I commented out the KEY_PROVINCE key and of course  build-ca script complained. So I had to put a hash sign before lines 118 & 119 in /etc/openvpn/easy-rsa/openssl-1.0.0.cnf.

I could use a better guide. Something explaining what's needed for :-)

---

