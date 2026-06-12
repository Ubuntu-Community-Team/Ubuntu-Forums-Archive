---
title: "Mailman and suexec"
date: 2008-11-30
forum: Server Platforms
---

### Post by gecka on 2008-11-30
Hello,

I need help making mailman work with a suexec setup. Here is the apache error:

[Mon Dec 01 10:25:05 2008] [error] [client xxx.xxx.xxx.xxx] attempt to invoke directory as script: /var/lib/mailman/cgi-bin/
[Mon Dec 01 10:26:12 2008] [error] [client xxx.xxx.xxx.xxx] suexec policy violation: see suexec log for more details
[Mon Dec 01 10:26:12 2008] [error] [client xxx.xxx.xxx.xxx] Premature end of script headers: listinfo

and suexec.log

[2008-12-01 10:26:12]: uid: (500/user) gid: (502/502) cmd: listinfo
[2008-12-01 10:26:12]: command not in docroot (/usr/lib/cgi-bin/mailman/listinfo)

Here is /etc/apache2/conf.d/mailman.conf

ScriptAlias /mailman/ /var/lib/mailman/cgi-bin/
<Directory /var/lib/mailman/cgi-bin>
	AllowOverride None
	Options ExecCGI
	Order allow,deny
	Allow from all
</Directory>
Alias /mmpublic/ /var/lib/mailman/archives/public/
<Directory /var/lib/mailman/archives/public>
	Options Indexes MultiViews FollowSymLinks
	AllowOverride None
	Order allow,deny
	Allow from all
</Directory>
Alias /mmimages/ /var/lib/mailman/icons/
<Directory /var/lib/mailman/icons>
	Options Indexes MultiViews
	AllowOverride None
	Order allow,deny
	Allow from all
</Directory>

Regards.

---

