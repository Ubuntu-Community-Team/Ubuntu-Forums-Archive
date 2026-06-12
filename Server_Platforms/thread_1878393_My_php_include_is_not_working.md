---
title: "My php include is not working"
date: 2011-11-09
forum: Server Platforms
---

### Post by glennbates on 2011-11-09
I have installed LAMP and have started working on my web site.  For some reason, my include isn't working.  Here is what I have.

<?php 

$title="Study Question | Your Study Buddy"; 
$currentpage="includes/pages/index.php"; 
 include "includes/page.php";  

?>

It will include a file if it is in the same folder.  Why is it not included here?

---

### Post by SeijiSensei on 2011-11-09
> **glennbates said:**
> It will include a file if it is in the same folder.  Why is it not included here?

Yes, but what folder is it looking in?  What does /var/log/apache2/error.log tell you?  What is the "include_path" parameter set to in /etc/php.ini?

It's always a good idea to use complete file paths in your scripts.  I generally use something like this:

```

$includes="/path/to/top/of/includes";
include($includes.'somefile.php');

```

---

### Post by Ryan Dwyer on 2011-11-10
No, that's a terrible idea. Specifying the absolute path means that your site cannot be ported easily, such as between a development environment and live environment.

[http://au.php.net/manual/en/function.include.php](http://au.php.net/manual/en/function.include.php)
> 
Files are included based on the file path given or, if none is given, the include_path specified. If the file isn't found in the include_path, include() will finally check in the calling script's own directory and the current working directory before failing.


OP, if your URL is something like [http://localhost/includes/pages/index.php](http://localhost/includes/pages/index.php) then PHP's working directory will be includes/pages/. In that case your include file would be '../page.php'.

---

### Post by SeijiSensei on 2011-11-10
Every site I build runs an initialization script before the page is written.  That script includes the definition of the include location.  Porting the site to another server requires only editing this one file.  How tough is that?

(I just did this when moving a site from development to a remote hosting facility.  It took me at most two minutes to set the right file paths.)

Also, you seem to be suggesting that included files be stored in directories that are visible over the Internet.  I consider that a very insecure practice.  All my included code resides in directories outside of the DocumentRoot of the site.  I also use a different extension besides .php for included files, and have a Files directive in the Apache configuration that prohibits the direct download of files with this extension as an added security measure.

For most of my sites, index.php consists of nothing more than a couple of directory pointers and some require() statements.  All the stuff that matters is stored elsewhere.

I also never use the include_path in /etc/php.ini since I'm hosting multiple virtual sites.  Each site has it's own includes, so having a global include path is useless for me.  I could use an ini_set() command to change the include path for each site, but that's really no different in practice from the method I describe above.

---

