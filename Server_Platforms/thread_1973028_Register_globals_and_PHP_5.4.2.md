---
title: "Register_globals and PHP 5.4.2"
date: 2012-05-04
forum: Server Platforms
---

### Post by A2llex on 2012-05-04
hi,

Is there any solution how to enable register_globals in PHP 5.4.2?
One site needs it to be enabled.

Thank you.

---

### Post by SeijiSensei on 2012-05-04
Nope, it's finally gone for good.  Whatever site is still using globals had, what, half-a-dozen years or more now to fix the code?

The quickest solution is to create the globals from scratch by running this code at the beginning of the app:

```

foreach ($_REQUEST as $key=>$val) {
    ${$key}=$val;
}

```

You have to be careful that any variable created this way isn't already defined in the remainder of the script.

You can force this code to be run ahead of every page on the site by using the [auto_prepend_file]("http://www.php.net/manual/en/ini.core.php#ini.auto-prepend-file") directive in an .htaccess file.

---

### Post by A2llex on 2012-05-06
> **SeijiSensei said:**
> Nope, it's finally gone for good.  Whatever site is still using globals had, what, half-a-dozen years or more now to fix the code?

The quickest solution is to create the globals from scratch by running this code at the beginning of the app:

```

foreach ($_REQUEST as $key=>$val) {
    ${$key}=$val;
}

```You have to be careful that any variable created this way isn't already defined in the remainder of the script.

You can force this code to be run ahead of every page on the site by using the [auto_prepend_file]("http://www.php.net/manual/en/ini.core.php#ini.auto-prepend-file") directive in an .htaccess file.

thank you mate!

---

