---
title: "joomla does not install on xampp, Ubuntu 14.04"
date: 2014-08-29
forum: Server Platforms
---

### Post by Johanneman1 on 2014-08-29
Hi,

I am trying to install joomla 3.3.3 onto xampp/lampp server, Ubuntu 14.04 desktop.
During install step 2 I get the error message "[COLOR=#C09853][FONT=Helvetica Neue]Could not connect to the database. Connector returned number: Could not connect to MySQL.[/FONT][/COLOR]"
phpMyAdmin works so port 3306 must be open.
a Magento install works on the same MySQL install

What could be the problem here?

Thanks in advance, if more information is required, please let me know,
Johan

---

### Post by slickymaster on 2014-08-29
Moved to the **Server Platforms** sub-forum.

---

### Post by Lars Noodén on 2014-08-29
> **Johanneman1 said:**
> 
What could be the problem here?

I'd wind back and remove XAMPPP/LAMPPP and try a normal LAMP installation.  It will be a lot easier to maintain, security and maintenance updates will come automatically rather than manually.  Same for dependencies, which will also be tracked and maintained automatically.  It will not have any redundant or conflicting pieces.  The components will be in the expected places and behave in the expected way for Ubuntu.  

To install [LAMP](https://help.ubuntu.com/community/ApacheMySQLPHP) on Ubuntu, you already have the Linux and Perl parts, so you just need to add Apache2, MySQL (or Postgresql) and then PHP5.  This can be done in one line:

```

sudo apt-get install lamp-server^

```

Mind the caret ^ It is part of the metapackage name.  

Or you can install the components a la carte via apt-get, synaptic or the Software Center.  

Either way is safer and easier than doing it manually.  So my vote would be to give the Linux way a try and see how it goes with that.

---

### Post by Johanneman1 on 2014-08-30
Thanks, I will try that but that will mean I have to backup and reinstall my Magento Site as well...

---

### Post by Habitual on 2014-08-30
> **Johanneman1 said:**
>  [COLOR=#000000]"[FONT=Helvetica Neue]Could not connect to the database. Connector returned number: Could not connect to MySQL.[/FONT][/COLOR]"
[http://docs.joomla.org/Unable_to_connect_to_the_database](http://docs.joomla.org/Unable_to_connect_to_the_database)

---

