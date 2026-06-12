---
title: "Editing apache2 security.conf to block access to /, winds up blocking site!"
date: 2014-10-14
forum: Server Platforms
---

### Post by MechaMechanism on 2014-10-14
# Disable access to the entire file system except for the directories that
# are explicitly allowed later.
#
# This currently breaks the configurations that come with some web application
# Debian packages.
#
<Directory />
   AllowOverride None
   Order Deny,Allow
   Deny from all
</Directory>

This causes visitors to see an error page that says you don't have permission to access /
I've used this before with no problems.  The only thing that's different about this release of 14.04 that I'm aware of is that new html dir /var/www/html.

I'm just getting my feet wet and if you would be so kind as to share the best placecs to go on the web to learn about apache that would be great.  See, I don't really know what the about config means.  I think it means dir / and allow overide I don't know.  Order is the order of operations I assume and that deny / comes first.  Deny from all might mean everybody on the web.

So can you help me out?  And some Ubuntu web server noob resources would be nice.

---

