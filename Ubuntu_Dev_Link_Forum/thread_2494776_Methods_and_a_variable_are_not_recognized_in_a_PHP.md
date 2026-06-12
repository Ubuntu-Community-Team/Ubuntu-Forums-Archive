---
title: "Methods and a variable are not recognized in a PHP file"
date: 2024-01-26
forum: Ubuntu Dev Link Forum
---

### Post by gerard-lerest-o on 2024-01-26
Good evening,

In order to program a PHP application using the Model-View-Controller  architecture on Ubuntu 22.04, I first learned to create a vendor folder.  Inside this folder, there's another folder named composer, and within  that, the ClassLoader class, two methods (acpu_fetch and apcu_add), and a  variable ($hit) are not recognized. The php8.1-acpu package is properly  installed. This package is listed when running php -m. 
Attached to this message, you will find the 'phpinfo.php' file.
/etc/php/8.1/mods-available/apcu.ini contains extension=apcu.so
Thanks for your help!

---

### Post by gerard-lerest-o on 2024-01-26
I am testing this program with VSCodium and VSCode. When I disable the  "PHP Intelephense" extension, the four errors disappear. Is there a  setting to adjust to keep PHP Intelephense? How does PHP IntelliSense  compare to PHP Intelephense?

---

### Post by SeijiSensei on 2024-01-27
You need to ask these questions on a PHP mailing list. See: [https://www.php.net/support](https://www.php.net/support)

---

