---
title: "joomla 1.6 and/or xampp problem"
date: 2011-03-21
forum: Server Platforms
---

### Post by vitalix on 2011-03-21
Hi guys. 
I installed xampp and joomla 1.6 on my ubuntu 10.04 system.
It works but on some site pages it shows this message:
**"Strict Standards**:  Declaration of ContentModelCategory::populateState() should be compatible with that of JModelList::populateState() in **/opt/lampp/htdocs/joomla/components/com_content/models/category.php** on line **24**"

Also, depending on templages sometimes it can write something like:
**"Notice**:  Undefined property: stdClass::$catslug in **/opt/lampp/htdocs/joomla/templates/bluemin-tg/html/com_content/category/blog_item.php** on line **171**"

What can I do to fix this? Please, help!

P.S. I didn't put the smiles above, it's just combinations of : and p

---

### Post by vitalix on 2011-03-21
it terns out that the problem can be easy solved.
In the file : /opt/lampp/etc/php.ini

two following lines must be changed from:
error_reporting = E_ALL | E_STRICT
display_errors = On

to:
error_reporting = E_ALL & ~E_NOTICE
display_errors = Off

Than worked for me.:P

---

### Post by fmmarzoa on 2011-12-10
That does NOT solves the problem, it just sweeps it below the carpet...

---

