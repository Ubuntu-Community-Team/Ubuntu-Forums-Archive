---
title: "Recent 15.04 &quot;security upgrade&quot; breaks OpenSSH"
date: 2015-06-02
forum: Security
---

### Post by Jon_Ribbens on 2015-06-02
Since a security fix that was pushed very recently, which I think was described as "disabling export ciphers", OpenSSH has now had all MACs disabled except:

  MD5,SHA1,UMAC-64,hmac-ripemd160,hmac-ripemd160@openssh.com,SHA1-96,MD5-96

i.e. the security fix, rather than disabling the bad algorithms and leaving the good ones, disabled the good ones and left the bad ones!

Does anyone know what's going on?

(Before anyone asks, no my /etc/ssh/ssd_config does not contain any directives specifying MACs.)

---

### Post by qfissler on 2015-06-03
So which package(s)?

openssh-server?

---

### Post by matt_symes on 2015-06-04
Hi

> **Jon_Ribbens said:**
> Since a security fix that was pushed very recently, which I think was described as "disabling export ciphers", OpenSSH has now had all MACs disabled except:

  MD5,SHA1,UMAC-64,hmac-ripemd160,hmac-ripemd160@openssh.com,SHA1-96,MD5-96

i.e. the security fix, rather than disabling the bad algorithms and leaving the good ones, disabled the good ones and left the bad ones!

Does anyone know what's going on?

(Before anyone asks, no my /etc/ssh/ssd_config does not contain any directives specifying MACs.)

Are you sure of this ? That would be a major mistake for any developer to make.

Please can you post links to where you got this information from. I would like to take a look.

Kind regards

---

### Post by cariboo on 2015-06-05
I don't see any openssh-server problems [here]("http://www.ubuntu.com/usn/vivid/").

---

