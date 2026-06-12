---
title: "Possibe break-in via saslauthd?"
date: 2008-10-01
forum: Server Platforms
---

### Post by volkswagner on 2008-10-01
I have a LAMP server for hobby connected via router/WRT54G.

I have setup ssh security via allow and not allow.  Seems to work well.  Now I am starting to see the following in auth.log.

```
Sep 30 23:07:03 Web postfix/smtpd[9559]: sql_select option missing
Sep 30 23:07:03 Web postfix/smtpd[9559]: auxpropfunc error no mechanism available
Sep 30 23:07:03 Web postfix/smtpd[9559]: _sasl_plugin_load failed on sasl_auxprop_plug_init for plugin: sql
Sep 30 23:07:08 Web saslauthd[4897]: (pam_unix) check pass; user unknown
Sep 30 23:07:08 Web saslauthd[4897]: (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=
Sep 30 23:07:10 Web saslauthd[4897]: DEBUG: auth_pam: pam_authenticate failed: User not known to the underlying authentication module
Sep 30 23:07:10 Web saslauthd[4897]: do_auth         : auth failure: [user=admin] [service=smtp] [realm=] [mech=pam] [reason=PAM auth error]
```
  

Should I be concerned?  What can I do to add security?

I am going to read up on NAT and DMZ.  Will either help with the above or general security?

---

### Post by lykwydchykyn on 2008-10-01
EDIT: nevermind, I don't read close enough this late at night.  I don't know what I'm writing, it's the ice cream talking.

I don't think NAT would help, because you still need the port open to communicate with the outside.

---

### Post by windependence on 2008-10-02
You're gonna see lots of that, it's nothing to be concerned about. Now if you see actual successful logins, then you'll need to worry. 

I have run Linux and Unix boxes for months completely open to the net and never had anyone be able to successfully log in. Just make sure you don't use dictionary words for user names or passwords.

-Tim

---

