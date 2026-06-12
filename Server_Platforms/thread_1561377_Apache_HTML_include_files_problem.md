---
title: "Apache HTML include files problem"
date: 2010-08-26
forum: Server Platforms
---

### Post by nickmcg on 2010-08-26
I seem to be unable to use the html ```
<!--#include virtual="test.txt" -->
```

I have tried following the advice in this thread [http://ubuntuforums.org/showthread.php?t=1510098](http://ubuntuforums.org/showthread.php?t=1510098) but it makes no difference.

The file is there, but the line is delivered to the browser as-is.

Using Lucid and a new install of apache 2.2 from the repository.

Any help greatly appreciated.

TIA

Nick

---

### Post by craigp84 on 2010-08-26
Hi Nick,

Please confirm your apache configuration includes the following lines -->

```

LoadModule include_module modules/mod_include.so
...
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
...
<Directory "/var/www/...">  # Wherever you want the includes to be active
  Options ... +Includes ... # And other options you want

```

Please then confirm that the apache error_log -- /var/log/apache2/error_log (or wherever it's located, i don't have an ubuntu machine to hand to check) contains no errors when you restart apache.

Finally confirm that test.txt is in the same directory (this is what you have specified with your virtual= path) as the file you are calling the include from, whilst also verifying that filename ends in .shtml

This covers pretty much everything, unless you are using a MAC (mandatory access controls) implementation such as AppArmour or SELinux.

---

### Post by nickmcg on 2010-08-26
Many thanks.

I did have those settings correct, and it turns out that it was down to my stupidity. I thought that the file to be included needed the shtml extension, rather than the main file.

Thanks again 

Nick

---

### Post by craigp84 on 2010-08-26
Glad it was an easy fix.

P.s. nothing stupid about it, the configuration to instruct apache is necessarily complex for such a feature-full application, it's unreasonable to expect to get a handle on all parts of the configuration first time round

---

### Post by nickmcg on 2010-08-26
The stupid part is that I should have known - I went through this with php scripts (although in a much shorter time)!

---

### Post by craigp84 on 2010-08-26
:)

---

### Post by Lars Noodén on 2010-08-27
One reason to use SSI over PHP is improved security, so a refinement in that regard to @craigp84's pointer is to be sure to use **[IncludesNOEXEC](http://httpd.apache.org/docs/current/mod/core.html#options)** rather than **Includes**.

```

LoadModule include_module modules/mod_include.so
...
AddType text/html .shtml
AddOutputFilter INCLUDES .shtml
...
<Directory "/var/www/...">  # Wherever you want the includes to be active
  Options ... +**[IncludesNOEXEC](http://httpd.apache.org/docs/current/mod/core.html#options)** ... # And other options you want

```

That allows you to include text and html from other files without the risk of running scripts.

---

### Post by nickmcg on 2010-08-30
Thanks for that tip, although as I'm generating the included files, there *should* be no risk of any script running.

Nick

---

