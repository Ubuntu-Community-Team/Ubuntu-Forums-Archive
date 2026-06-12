---
title: "Apache2 svn with SSL"
date: 2011-11-21
forum: Server Platforms
---

### Post by Bradburts on 2011-11-21
I want to run Subversion SVN with SSL under Apache2.
 
I have http:// access running fine. My dav_svn.conf is:
```

 [FONT=Courier New, monospace][SIZE=2]<Location /svn>[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]DAV svn[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]SVNParentPath /srv/svn[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]SVNListParentPath On[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]AuthType Basic[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]AuthName "Subversion Repository"[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]AuthUserFile /etc/subversion/passwd[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]<LimitExcept GET PROPFIND OPTIONS REPORT>[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]Require valid-user[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]</LimitExcept>[/SIZE][/FONT]
[FONT=Courier New, monospace][SIZE=2]</Location>[/SIZE][/FONT]

```
 
I am not sure about the structure of Apache2 configuration but holding the SVN locations in the DAV configuration seemed a little strange. 
Seemed better to move this configuration to a new vhost whilst enabling SSL.
Copied default-ssl and pasted above & a2ensite. Reverted dav_svn.conf to its default state (mostly commented out). Did not dis the dav mod.
 
This gives me:
IE 'Cannot display the webpage'
 
Any ideas?
Cannot find an upto date article covering this.
Could also do with some pointers on Apache2 configuration, it seems better to place all settings in a vhost, certainly if I end up with several sites.

---

