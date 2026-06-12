---
title: "Samba share for a specific user - set up but not working"
date: 2005-11-30
forum: Server Platforms
---

### Post by rapha on 2005-11-30
Hi all!

I've got Samba set up here on a server so everybody can access it as they're used from Windows. However, there's one share that requires to be set-up for one specific user only and with a specific password as well.

I've created that user and gave it a password through `passwd'. My samba configuration is below. The problem is that when you try to connect from a Windows machine using that user and password, it says you don't have permission. Maybe somebody can give me a clue? :-)

---< snip >---
```

[global]
  workgroup = LINUX
  server string = Gott der grossen Kraft
  os level = 2
  time server = Yes
  unix extensions = Yes
  encrypt passwords = Yes
  log level = 1
  syslog = 0
  printing = CUPS
  printcap name = CUPS
  socket options = SO_KEEPALIVE IPTOS_LOWDELAY TCP_NODELAY
  wins support = No
  veto files = /*.eml/*.nws/riched20.dll/*.{*}/
  guest account = pcoadmseth
  share modes = yes
  mangle case = yes
  mangled names = yes
  default case = lower
  case sensitive = no
  preserve case = yes
  short preserve case = yes

# Public shares here -- these work just like they should

[Formularbereich]
  path = /home/pcoadmseth/Webroot/external/formularbereich
  comment = Modifizierung Formularbereich
  public = no
  guest ok = no
  writeable = yes
  browseable = yes
  available = yes
  valid users = RedDotUser

```
---< snap >---

---

### Post by manicka on 2005-11-30
only a guess, it may have something to do with the use of case in the user name (RedDotUser) and the way windows is passing the username to the samba server. Try all lower case.

---

### Post by rapha on 2005-12-01
[QUOTE=manicka]... (RedDotUser) ...Try all lower case.[/QUOTE]

Changed passwd (through deleting and adding a new user) and smb.conf to read 'reddotuser' and also tried logging in through Windows Explorer with all lower-case letters. Same error message still... :-(

---

