---
title: "Ubuntu auth against Cisco ACS"
date: 2008-04-01
forum: Security Discussions
---

### Post by mikeduffy13 on 2008-04-01
Hey guys, 

I want to be able to have my Ubuntu box (used as a SFTP server mainly) to be able to authenticate against our Cisco ACS.  I have no clue where to start.  Any help would be appreciated.

---

### Post by The Cog on 2008-04-02
I found this package that I think you probably need.
[http://packages.ubuntu.com/gutsy/libpam-radius-auth](http://packages.ubuntu.com/gutsy/libpam-radius-auth)

But I can't find a howto. Hopefully there is a readme in the package?

---

### Post by mikeduffy13 on 2008-04-03
thanks for the link.  i downloaded and installed via synaptics, and have read through the config files.  It seems like this is an add on module for PAM, which I'm not sure exactly what that is.  I am pretty new to the whole Linux side of the world, so I can't exactly figure out how to get this module to run.  

I also downloaded FreeRADIUS but I haven't been able to figure out how to use it as a client to authenticate against an external RADIUS server...

---

### Post by The Cog on 2008-04-04
I think FreeRadius is an radius authentication server, which you don't need since you want to authenticate against an external Radius server in the ACS. Sorry I can't help more. Maybe you should ask in one of the more noisy forums, general help perhaps.

---

### Post by mikeduffy13 on 2008-04-09
well i installed lib_pam_auth, but i haven't quite figured out the whole configuration yet.  Not sure if anyone can help with this portion of it, but I'll post the code here anyways so you can see what I have.

```

#  pam_radius_auth configuration file.  Copy to: /etc/raddb/server

#  server[:port] secret [timeout]
#
#  the port name or number is optional.  The default port name is
#  "radius", and is looked up from /etc/services The timeout field is
#  optional.  The default timeout is 3 seconds.
#
#  If multiple RADIUS server lines exist, they are tried in order.  The
#  first server to return success or failure causes the module to return
#  success or failure.  Only if a server fails to response is it skipped,
#  and the next server in turn is used.
#
#  The timeout field controls how many seconds the module waits before
#  deciding that the server has failed to respond.
#
# server[:port] shared_secret      timeout (s)
127.0.0.1       secret             1
10.16.x.x    other-secret       3

```

I'm not sure what the secret should be, it doesn't seem wise to put a password in this field since it is visible.  

Also the /lib/security/pam_radius_auth.so file seems to encrypted when I open it so I can't make any changes to the options...

---

