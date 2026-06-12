---
title: "fail2ban regex"
date: 2012-05-31
forum: Server Platforms
---

### Post by papampi on 2012-05-31
I'm trying to make a fail2ban jail this log 
but i can not make the regex 
can some one help me please 

```
2012-05-31 23:08:49.651 WARNING -> ClusteredCache <- Internal error receiving remote cache packet [abc.xyz.abc.xyz - 01 81 00 14 07 59 3E B1]: java.io.EOFException
2012-05-31 23:08:49.657 WARNING -> ClusteredCache <- Internal error receiving remote cache packet [abc.xyz.abc.xyz - 01 81 1B BF 25 F8 6C 91]: java.io.EOFException
2012-05-31 23:08:49.819 WARNING -> ClusteredCache <- Internal error receiving remote cache packet [abc.xyz.abc.xyz - 01 80 1B D0 F5 B0 84 B8]: java.io.EOFException
2012-05-31 23:08:49.819 WARNING -> ClusteredCache <- Internal error receiving remote cache packet [abc.xyz.abc.xyz - 01 80 00 14 61 4D BA 4E]: java.io.EOFException
2012-05-31 23:08:49.855 WARNING -> ClusteredCache <- Internal error receiving remote cache packet [abc.xyz.abc.xyz - 01 81 00 83 26 5C C7 3B]: java.io.EOFException
2012-05-31 23:08:49.922 WARNING -> ClusteredCache <- Internal error receiving remote cache packet [abc.xyz.abc.xyz - 01 80 01 5F 26 95 3D 87]: java.io.EOFException
2012-05-31 23:08:49.957 WARNING -> ClusteredCache <- Internal error receiving remote cache packet [abc.xyz.abc.xyz - 01 81 00 37 CD 6E 07 1E]: java.io.EOFException
2012-05-31 23:08:49.999 WARNING -> ClusteredCache <- Internal error receiving remote cache packet [abc.xyz.abc.xyz - 01 81 15 1A 2D FF 8D 8D]: java.io.EOFException

```

---

### Post by papampi on 2012-06-18
I tried many failregexes but non work !
any one can help ?

failregex = WARNING: ClusteredCache - Internal error receiving remote cache packet [<HOST> - ([0-9a-fA-F][0-9a-fA-F](\.[0-9a-fA-F][0-9a-fA-F]){9})]: java.io.EOFException

failregex = WARNING: ClusteredCache - Internal error receiving remote cache packet [<HOST> - (\.[0-9a-fA-F][0-9a-fA-F]){9})]: java.io.EOFException

failregex = WARNING: ClusteredCache - Internal error receiving remote cache packet [<HOST>.*]: java.io.EOFException

failregex = WARNING: ClusteredCache - Internal error receiving remote cache packet [(?P<HOST>) - ([ 0-9a-fA-F]+)]: java.io.EOFException

---

### Post by unspawn on 2012-06-19
[Check your same thread in this other forum.](http://www.linuxquestions.org/questions/linux-security-4/fail2ban-regex-help-needed-4175411891/#post4706457)

---

