---
title: "HOTP authentication at log in question"
date: 2011-06-25
forum: Security
---

### Post by raevin on 2011-06-25
Does anyone know if/how its possible to integrate HOTP authentication into GDM login manager?

Basically what I want to do is have it ask for the password of the account, then another prompt come up asking for the code for the account.

I know how to set it up, but I'm know if modifying the PAM module for requiring OATH/HOTP authentication will make this happen or if it will just break the system...and this is one thing I don't want to have to fix.

---

### Post by gzarkadas on 2011-07-14
Your options are:

-- Use a dedicated module, either made by others or made by you. There appear to exist implementations of one-time-password modules (see [http://www.kernel.org/pub/linux/libs/pam/modules.html](http://www.kernel.org/pub/linux/libs/pam/modules.html), section "One-time password authentication") but I only managed to reach one link; rest gave errors. The one link I saw claims that the module is not production-grade yet. 

-- Use a database with user-OTP pairs and the pam_userdb module. An example gmd (or gdm3) configuration file inside /etc/pam.d would then look like:
```

... previous entries

# standard unix password authenication
@include common-auth
auth    required    pam_userdb.so db=/path/database [... possibly other options; see [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_userdb.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_userdb.html) for details ]

... next entries

```You will probably also need to use the pam_exec module to update the database after succesful authentication (either before or after the above line, depending on how you populate the database). See the documentation of pam_exec module for details: [http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_exec.html](http://www.kernel.org/pub/linux/libs/pam/Linux-PAM-html/sag-pam_exec.html). See also the PAM page [http://www.kernel.org/pub/linux/libs/pam/](http://www.kernel.org/pub/linux/libs/pam/) for further documentation links.

Therefore, the fisrt option definitely has the potential to scrue things up. You will use immature or custom-made code. But so do the others; if you misconfigure PAM you typically end-up locked out of your system. 

The second option uses a more standard and thus possibly better tested approach. But you need to implement code to populate and keep in sync the database with one-time passwords.

In any case, since you will only be modifying files inside /etc/pam.d, it will be relatively easy to restore the system, by copying back the old versions (provided of course that you manage to login into the system). Now if the system in question is local, then one can always boot with a rescue disk and restore the old configuration back. If the system is remote, then one must ensure that a root shell console remains open while testing the new configuration, so that the old configuration can be restored right away.

There is also a third option if you are interested in local logins only: instead of using HOTP, use pamusb (that is the presence of a usb dongle in addition to password), which also features a one time pad mechanism, so that it is not easy to forge device serials. It is not the same thing, but it works and it may be adequate for your security needs.

---

