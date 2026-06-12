---
title: "LDAP Broken in 7.10?"
date: 2007-10-25
forum: Server Platforms
---

### Post by Termina on 2007-10-25
I am running slapd on a Debian Etch server. Uses encryption (TLS). Debian, Ubuntu 7.04, and SuSe 10.x work perfectly fine with it. Only 7.10 fails.

I have tried 7.04 upgraded to 7.10 (with 7.04 working before the upgrade) as well as a fresh 7.10 install. In both cases I am unable to successfully log in as a user.

I copy the ldap.conf, pam_ldap.conf/secret, libnss_ldap.conf/secret, nsswitch.conf, the /etc/pam.d files, etc. all to their respective places (Debian/Ubuntu 7.04 places. I have a script to do this for multiple machines that are Debian-based).

I even copy ldap.conf to /etc/ldap and /etc (since apparently the conf file has moved... would be interested in knowing the reason from this. To break compatibility with Debian?)

However, even after reboot, ldap does not work. 

I see no error messages when trying to log in (auth.log, syslog); authentication just fails. I can 'su - user' if I log in with the pam username/password of root however.

Logging into GDM or via the terminal fail.

Does anyone know if this is a bug, or had 7.10 changes the location of more files than /etc/ldap/ldap.conf?

---

### Post by Termina on 2007-10-26
I'll be switching these machines over to Debian or SuSe 10.x

7.04 has it's own host of ldap problems (slow firefox load, etc.). Is Ubuntu not recommended for a business/networked environment?

---

### Post by kesomir on 2007-10-28
I'm hoping (hehe) that ldap will be sorted in Ubuntu for the LTS coming next now that apparently, 7.10 server is supported as an ldap client.

I have a gusty install which authenticates against ldap, so it does work. I did an install, manually edited files and then copied the configs I use for building the feisty boxes.

That said, the /etc/security/groups on-fly group assignment didn't seem to work - and unlike you, I don't use TLS.

Just a shame that probs with HAL when using LDAP authentication stop USB sticks from being mounted as non-local users. Plus the experience fills me with as much joy as having teeth pulled.

It's a shame, because opensuse, fedora et al. All work without problems on ldap and provide tools on installation to easily configure this.

..and Ubuntu in standalone is a champ.

The repositories, apt and faith in the platform's future are keeping me here atm (that + beagle making firefox slow and nfs mounts not being mounted on startup on suse10.3).

I'm still waiting for the 7.10 documentation in the hope for ldap client setup guides -working ones? perhaps that's asking too much :)

I don't have / notice your firefox issue under feisty btw -> what sort of hardware are you running?

---

### Post by anselm13 on 2007-10-28
I am working on setting up ldap with gutsy server and clients.  Perhaps auth-client-config might help you with your problems.  Look it up on google.  I believe it is new to gutsy and changes how clients are configured to utilize ldap.

---

### Post by fnjordy on 2007-10-29
/etc/libnss-ldap.conf has moved to /etc/ldap.conf so that needs updating.

Other than that some username or group must be missing in the startup procedure as I find that I must use a static IP address on the client or the boot process will hang.  i.e. trying to resolve some name before the networking subsystem is up and connectivity to the LDAP server is available.

---

