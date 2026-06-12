---
title: "Subversion pos-commit hook sometimes doesnt send email"
date: 2010-09-12
forum: Server Platforms
---

### Post by sipickles on 2010-09-12
Hi 

I use subversion with post commit hook to send email when a team member commits.

It used to work flawlessly, but now, fairly frequently, no email is sent. Heres my script:

```
#!/bin/sh
REPOS="$1"
REV="$2"
/usr/bin/svnnotify -r $REV -C -O --smtp mail.btinternet.com --smtp-user rosebankgrove@btinternet.com --smtp-pass XXXXXXXX --subject-cx --subject-prefix "[Fenix Urth SVN/code]" -p $REPOS -t simon@fenixurth.net -t nicd@fenixurth.net --from svn@fenixurth.net
```

Is there any errors posted anywhere?

Thanks

---

