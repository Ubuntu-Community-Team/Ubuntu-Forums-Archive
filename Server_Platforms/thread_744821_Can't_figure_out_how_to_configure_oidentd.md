---
title: "Can't figure out how to configure oidentd"
date: 2008-04-04
forum: Server Platforms
---

### Post by Samutz on 2008-04-04
I have an eggdrop bot and psyBNC running on my server.
So I wanted to install an identd since some servers on Efnet won't allowed you to connect without ident.
I installed oidentd with apt-get, and can run it fine with the default settings. I also configured it as shown below and the irc servers will detect it, but sets my ident to 'samutz' for both the bot and bnc.
So when I try to add users to it so that the bot and bnc have separate idents, the identd won't start and only gives me this error:
```
[line 18] Invalid user: "samutz"
Error reading configuration file
```
I've gone over other threads, and the man:oidend pages several times and tried pretty much every example I could find, but I still keep getting this same error.

So can anyone tell me what I need to add to these config files to get one ident for the bnc and a different one for the bot?
Or at least one for the bot so that the bnc will default to "samutz" like it already does.

Here's what my current working config files look like:

/etc/oidentd.conf
```
default {
	default {
		allow spoof
		allow spoof_all
		allow spoof_privport
		allow random_numeric
		allow numeric
		allow hide
	}
}

user root {
	default {
		force reply "UNKNOWN"
	}
}
```

/etc/oidentd_masq.conf
Blank except for all the junk at the top that's commented out already.

~/.oidentd.conf
```
global {
	reply "samutz"
}
```

---

