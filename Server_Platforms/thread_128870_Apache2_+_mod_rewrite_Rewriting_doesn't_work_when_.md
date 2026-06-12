---
title: "Apache2 + mod_rewrite: Rewriting doesn't work when pattern matches existing script"
date: 2006-02-12
forum: Server Platforms
---

### Post by flod on 2006-02-12
Hey,

I'm not very experienced with mod_rewrite, however something strange happens when using it with Apache2 on the Debian sarge or Ubuntu Breezy distros. The problem is not present on FC3's Apache2, so I'm not sure yet what am I missing. Maybe you can help me.

The problem happens when the RewriteRule pattern matches an existing php script file name.
The .htaccess looks like this:
```

Options +FollowSymLinks
RewriteEngine on
RewriteBase /subdir/
RewriteRule ^profiles/browse/$  /subdir/profiles_browse.php [L]
RewriteRule ^profiles/(.*)/(.*)$  /subdir/profiles.php?id=$1 [L]

```

When I'm requesting "http://example.com/subdir/profiles/browse/", the 2nd rule is matched, executing "profiles.php", instead of matching the 1st one and going for "profiles_browse.php".

Could you please help me with this?
I repeat that this happens only on Debian & Ubuntu Apache2, and not on the one available on Fedora Core 3, which is why I decided to post this problem here. Sorry if somehow this is strictly a mod_rewrite issue and I'm a bit off topic.

Thanks in advance,
Florin.

---

### Post by valorin on 2006-02-14
I had the same problem, however, I think I've managed to solve it.
Edit your 'Sites-Enabled' config files, and remove *MultiViews* from the options list.

It's working for me, so I hope it works for you as well :)

---

