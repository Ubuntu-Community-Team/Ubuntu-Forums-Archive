---
title: "Can't Auth on U1 on Meerkat"
date: 2010-09-15
forum: Ubuntu One (CLOSED)
---

### Post by exile on 2010-09-15
Been using U1 since it came out. Installed Maverick a few days ago and can't authenticate anymore. I can log in and see all my files online but nothing works client side.

```

$ u1sdtool --start
$ u1sdtool -c 
(wait a minute or so)
$ u1sdtool -s
State: AUTH_FAILED
    connection: With User With Network
    description: auth failed
    is_connected: False
    is_error: True
    is_online: False
    queues: WORKING_ON_BOTH

```

I am suspecting that I might have to recreate my account for the new single sign on? I have signed in online and changed my password just to ensure that I have forced my account to refresh.

No luck, and dropbox is looking like the solution.

---

### Post by duanedesign on 2010-09-16
There was a bug causing Authentification problems. It has now been fixed. Make sure you have the latest updates then...


1. Close the Ubuntu One Preferences and open a Terminal (Applications -> Accessories -> Terminal)and run the command:

```
killall ubuntu-sso-login
```

2. Open Seahorse (System -> Preferences -> Password and Encryption keys) and delete the Ubuntu One Token.

3. Then open Ubuntu One Preferences (System -> Preferences -> Ubuntu One). You should be prompted to add your computer. this new token should work.

thank you,
duanedesign

---

### Post by exile on 2010-09-17
Yeah, I've tried all that. No luck.

Very frustrating.

---

