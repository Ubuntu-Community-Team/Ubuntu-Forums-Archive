---
title: "cgi-bin not functional after Ubuntu 10.10 upgrade"
date: 2010-10-12
forum: Server Platforms
---

### Post by compiz addict on 2010-10-12
I'm running a web-proxy on my desktop system (and some websites), but I have a problem now.

If I try to use my proxy server, apache says that mysite/cgi-bin/nph-proxy.cgi isn't on the server!

I also added this to my configuration:
```

	<Directory "/var/www/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

```
but no effect.

This is kind of important, anyone know how to fix this?

---

### Post by compiz addict on 2010-10-12
Figured it out, lol.
For anyone else with the same problem:

Go into your configuration and replace this;
```

ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/

```

with this:

```

ScriptAlias /cgi-bin/ /var/www/

```

---

