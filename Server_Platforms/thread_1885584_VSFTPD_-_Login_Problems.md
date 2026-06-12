---
title: "VSFTPD - Login Problems"
date: 2011-11-23
forum: Server Platforms
---

### Post by ItsZach on 2011-11-23
I posted this on Gen. Help but thought it might be more suited to this board.

I'm currently setting up a Linode VPS to run  Drupal on as  test environment.  I'm trying to install modules and it  gave me an error that the FTP file transfer failed to the server.  On  the advice of a colleague I installed vsftpd.  It installed without any  errors and left the default config except local_enable=YES.

I start the service and I've attempted to login from root several times  on the server it always gives me login incorrect.  I have no clue how to  setup vsftpd and there doesn't seem like there's a lot of configuration  for it, and there's not a lot of tutorials out there that aren't  extremely brief.  Any assistance would be greatly appreciated.

[edit] I know about security, right now I'm setting it up and I don't  care outside of I don't want anon enabled, which it isn't.  To  reiterate, do. not. care. about. security. at. this. time.

---

### Post by lisati on 2011-11-23
With Ubuntu, the "root" user is usually disabled. Are you able to log in using the credentials of one of the "regular" users of the server?

---

### Post by kevinthecomputerguy on 2011-11-23
vsftp, here you go.
[http://woodel.com/page3](http://woodel.com/page3)

---

