---
title: "Smarty config problems"
date: 2006-08-30
forum: Server Platforms
---

### Post by TokyoUbuntu on 2006-08-30
I'm just starting to learn PHP and MySQL.  I'm using a book by O'Reilly and there is a section in there about setting up smarty.
I did apt-get install smarty and it's installed.  However, in the book it is telling me to make a file called index.php at my www root with something like this in it:

?php
// use the absolute path for Smarty.class.php
require($_SERVER["DOCUMENT_ROOT"].'/Smarty/Smarty.class.php');
$smarty = new Smarty();
$smarty->template_dir = $_SERVER["DOCUMENT_ROOT"].'/myapp/smarty/templates';
$smarty->compile_dir = $_SERVER["DOCUMENT_ROOT"].'/myapp/smarty/templates_c';
$smarty->cache_dir = $_SERVER["DOCUMENT_ROOT"].'/myapp/smarty/cache';
$smarty->config_dir = $_SERVER["DOCUMENT_ROOT"].'/myapp/smarty/configs';
?>

Well, my problem is I run WordPress and my index.php is alredy there for my blog.  Does this kind of file have to be created, named index.php, and sit at the top of www?

---

