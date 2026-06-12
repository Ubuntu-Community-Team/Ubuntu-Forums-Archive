---
title: "ubuntu 12.04 lts (32bit) / moinmoin wiki 1.9.3 / no css"
date: 2013-11-30
forum: Server Platforms
---

### Post by eyjoel on 2013-11-30
hi community,

i am running ubuntu 12.04 lts and want to use moinmoin wiki. 
when i check my wiki i have no css. i have already searched this forum for my problem. i found one tipp to use

```
alias /moin_static193 "usr/share/moin/htdocs"
```

in the apache config. i have this. 

someone is running ubuntu 12.04 lts with moinmoin 1.9.3?

here some more infos about my config. maybe someone who run this can compare.

apache:
```
    ### moin
    ScriptAlias /oswiki "/usr/share/moin/oswiki/moin.cgi"
    alias /moin_static193 "usr/share/moin/htdocs"
    <Directory /usr/share/moin/htdocs>
       Order allow,deny
       allow from all
    </Directory>
    ### end moin
```

moinmoin wikiconfig.py
```

# -*- coding: iso-8859-1 -*-

import os

from MoinMoin.config import multiconfig, url_prefix_static

class Config(multiconfig.DefaultConfig):

    wikiconfig_dir = os.path.abspath(os.path.dirname(__file__))

    instance_dir = wikiconfig_dir

    data_dir = os.path.join(instance_dir, 'data', '') # path with trailing /

    data_underlay_dir = os.path.join(instance_dir, 'underlay', '') # path with trailing /

    url_prefix_static = '/moin_static193'

    sitename = u'Untitled Wiki'

    logo_string = u'<img src="%s/common/moinmoin.png" alt="MoinMoin Logo">' % url_prefix_static

    navi_bar = [
        # If you want to show your page_front_page here:
        #u'%(page_front_page)s',
        u'RecentChanges',
        u'FindPage',
        u'HelpContents',
    ]

    theme_default = 'modernized'

    language_default = 'en'

    page_category_regex = ur'(?P<all>Category(?P<key>(?!Template)\S+))'
    page_dict_regex = ur'(?P<all>(?P<key>\S+)Dict)'
    page_group_regex = ur'(?P<all>(?P<key>\S+)Group)'
    page_template_regex = ur'(?P<all>(?P<key>\S+)Template)'

    show_hosts = 1


```

/etc/moin/mywiki.py

```
# -*- coding: iso-8859-1 -*-
# IMPORTANT! This encoding (charset) setting MUST be correct! If you live in a
# western country and you don't know that you use utf-8, you probably want to
# use iso-8859-1 (or some other iso charset). If you use utf-8 (a Unicode
# encoding) you MUST use: coding: utf-8
# That setting must match the encoding your editor uses when you modify the
# settings below. If it does not, special non-ASCII chars will be wrong.

"""
This is a sample config for a wiki that is part of a wiki farm and uses
farmconfig for common stuff. Here we define what has to be different from
the farm's common settings.
"""

# we import the FarmConfig class for common defaults of our wikis:
from farmconfig import FarmConfig

# now we subclass that config (inherit from it) and change what's different:
class Config(FarmConfig):

    # basic options (you normally need to change these)
    sitename = u'MyWiki' # [Unicode]
    interwikiname = u'MyWiki' # [Unicode]

    # name of entry page / front page [Unicode], choose one of those:

    # a) if most wiki content is in a single language
    #page_front_page = u"MyStartingPage"

    # b) if wiki content is maintained in many languages
    page_front_page = u"FrontPage"

    ##data_dir = '/org/mywiki/data/'
    data_dir = '/usr/share/moin/oswiki/data'
    data_underlay_dir='/usr/share/moin/oswiki/underlay'


```

update 1
i have downloaded the latest 1.9.7 moinmoin package. when i look there for the static directory there are much more files than in the ubuntu 1.9.3 package.
could it be that the 1.9.3 package is not complete?

best regards

--christian

---

### Post by eyjoel on 2013-12-04
hi community,

i have found the error with the help from jim from the moinmoin mailing list (big thanks to jim).

in my apache configuration is an error. the "/" is missing. it must be 

```
alias /moin_static193 "[SIZE=5][FONT=arial]**/**[/FONT][/SIZE]usr/share/moin/htdocs"
```

best regards

--christian

---

