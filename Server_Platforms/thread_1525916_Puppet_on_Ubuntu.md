---
title: "Puppet on Ubuntu"
date: 2010-07-07
forum: Server Platforms
---

### Post by Ric_ on 2010-07-07
I'm trying to set up puppet to install and configure apache on several servers. Having found:

[http://github.com/wesabe/puppet-apache2](http://github.com/wesabe/puppet-apache2)

I thought I was onto something. However I'm a little lost, does anyone know of or can anyone write a small howto on how to get this module working on certain nodes.

My current state is puppet is running and connected to the puppetmaster. I can do simple things but the apache install have lost me a little.

Thanks Ric_

---

### Post by upbeat.linux on 2010-07-07
Try the book

[http://books.google.com/books?id=BqThxxKBZt4C&pg=PA116&lpg=PA116&dq=puppet+apache+module&source=bl&ots=SkBLRtML7y&sig=xYYVfpWFLcx7YFS_yjYQz9w0HKU&hl=en&ei=gOc0TKeNLYL_8AbQr9TICw&sa=X&oi=book_result&ct=result&resnum=7&ved=0CDIQ6AEwBg#v=onepage&q=puppet%20apache%20module&f=false](http://books.google.com/books?id=BqThxxKBZt4C&pg=PA116&lpg=PA116&dq=puppet+apache+module&source=bl&ots=SkBLRtML7y&sig=xYYVfpWFLcx7YFS_yjYQz9w0HKU&hl=en&ei=gOc0TKeNLYL_8AbQr9TICw&sa=X&oi=book_result&ct=result&resnum=7&ved=0CDIQ6AEwBg#v=onepage&q=puppet%20apache%20module&f=false)

I find the README file to be quite useful:

[http://github.com/wesabe/puppet-apache2/blob/master/README](http://github.com/wesabe/puppet-apache2/blob/master/README)

and from the source:

[http://projects.reductivelabs.com/projects/puppet/wiki/Debian_Apache2_Recipe_Patterns](http://projects.reductivelabs.com/projects/puppet/wiki/Debian_Apache2_Recipe_Patterns)

---

