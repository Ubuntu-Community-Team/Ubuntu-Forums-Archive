---
title: "ScriptAlias and cgi-bin symbolic link"
date: 2011-10-10
forum: Server Platforms
---

### Post by banjopotato on 2011-10-10
I've got mysqldumper set up to run a perl script backing up my databases and sending me an e-mail with the backups.

I'm a relative noob to this. Running Ubuntu 10.04 on a remote server in a datacentre. 

I understand that Ubuntu has /var/www as its default directory for web sites. I also understand the default location for cgi-bin executables is in /usr/lib. It was my understanding that the ScriptAlias command
```
ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
```

in /etc/apache2/sites-available/http was supposed to have the effect of setting up a symbolic link between calls to [http://www.thewebsite.com/cgi-bin](http://www.thewebsite.com/cgi-bin) and the actual location of the executables in /usr/lib/cgi-bin

Only thing is, it doesn't seem to work. When I try to run the mysqldumper perl script via the web, I'm told it cannot be found.

I can set up a symbolic link myself by running "sudo ln -s /usr/lib/cgi-bin" while in /var/www, but:

1) should this really be necessary? I thought ScriptAlias handled this
2) are their any risks to doing it this way?

The executables directory has the following config in /etc/apache2/sites-available/http:

```
<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

```

Sorry if this is an obvious question. Like I said, I'm a bit of a noob.

---

### Post by SeijiSensei on 2011-10-12
Can you post the actual error entries in /var/log/error.log?

---

