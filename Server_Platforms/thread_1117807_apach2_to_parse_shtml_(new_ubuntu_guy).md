---
title: "apach2 to parse shtml (new ubuntu guy)"
date: 2009-04-06
forum: Server Platforms
---

### Post by xkaliburx on 2009-04-06
ok I did google around before I asked, and things do look ok, I am a redhat guy, so still figuring out what/where things are, but basically I have a copy of a site I want to move over, the src on page load shows;

<!--#include file="header.shtml" -->
<!-- start body -->

<!--#exec cgi="/tools/xmasinsert" -->

<!-- special promotion section -->
<!--#include file="promo-home.shtml" -->

and nothing is shown, so obviously it's not parsing.  Looking more I see it 'should' be enabled, looking at the mime.conf file, I see the following;

# To parse .shtml files for server-side includes (SSI):
# (You will also need to add "Includes" to the "Options" directive.)
#
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml

In the sites-enabled/virtualhost file I do have the line;
        Options ExecCGI Indexes FollowSymLinks Includes

Anything obvious a converting RH guy needs to know/change?

Thanks

---

### Post by cdenley on 2009-04-06
```

sudo a2enmod include

```

---

