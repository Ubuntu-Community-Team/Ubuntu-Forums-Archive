---
title: "Howto build php 5.2.5 on Gutsy"
date: 2008-06-03
forum: Server Platforms
---

### Post by mpzarde on 2008-06-03
Need some help, trying to test a php script on Gutsy whereas the production machine is CentOS. 

I don't have access to the production machine other than uploading/downloading files and their PHP is 5.2.5. Gutsy comes with 5.2.3 and I have a few things that don't appear to be working on my Gutsy server so I'm trying to make Gutsy as close as possible to the CentOS box.

To that end I'd like to build php 5.2.5 on my Gutsy server; my question is what configure options should I be using when building php so that following "make" and "make install" php setup matches current 5.2.3 setup?

From other forums (lampbuilder.com) it seems I want these options:

./configure --with-apxs2=/usr/bin/apxs2 --with-mysql --with-config-file-path=/etc/php5/apache2/php.ini

Are these correct or am I missing anything?

Thanks.

---

