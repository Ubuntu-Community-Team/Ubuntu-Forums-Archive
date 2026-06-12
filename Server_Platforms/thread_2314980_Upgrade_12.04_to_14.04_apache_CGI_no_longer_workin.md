---
title: "Upgrade 12.04 to 14.04: apache CGI no longer working.  Next thing to try?"
date: 2016-02-25
forum: Server Platforms
---

### Post by henrylaw on 2016-02-25
I did [FONT=courier new]do-release-upgrade[/FONT] on my domestic "production" server from 12.04 to 14.04.  Went pretty smoothly, thanks guys. But Apache (now at 2.4) no longer finds my perl CGI programs: "*The requested URL /cgi-bin/nfbshowlog.pl was not found on this server.*"

I have a2enmod'ed suexec, actions and cgi; "cgi" was already enabled, as is "alias" (see below)
I have installed [FONT=courier new]libapache2-mod-perl2[/FONT] (which automatically restarts Apache)
The code it can't find is definitely in [FONT=courier new]/usr/lib/cgi-bin/[/FONT] and there is a ScriptAlias for it, but I see that it is in [FONT=courier new]conf-available/serve-cgi-bin.conf[/FONT], which reads
```
<IfModule mod_alias.c>
    <IfModule mod_cgi.c>
        Define ENABLE_USR_LIB_CGI_BIN
    </IfModule>

    <IfModule mod_cgid.c>
        Define ENABLE_USR_LIB_CGI_BIN
    </IfModule>

    <IfDefine ENABLE_USR_LIB_CGI_BIN>
        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
            AllowOverride None
            Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
            Require all granted
        </Directory>
    </IfDefine>
</IfModule>
```
On the assumption that this is conditional processing in the fashion of C I see that the whole thing only fires if [FONT=courier new]mod_alias.c[/FONT] is enabled, but if "a2enmod alias" does what I think it does it's already enabled.  Then for the ScriptAlias to fire either [FONT=courier new]mod_cgi.c[/FONT] or [FONT=courier new]mod_cgid.c[/FONT] must be enabled; but "a2enmod cgi" is enabled, which is presumably what that means.  But it's clear that the ScriptAlias isn't taking effect.  I'm sure I'm close to a solution: can someone help me with one last push?

---

### Post by henrylaw on 2017-02-10
BTW, I fixed this by including
  	 	 	 	   ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
  in    	 	 	 	   sites-available/000-default.conf

---

