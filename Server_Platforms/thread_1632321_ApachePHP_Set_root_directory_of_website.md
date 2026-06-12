---
title: "Apache/PHP Set root directory of website"
date: 2010-11-27
forum: Server Platforms
---

### Post by Lucky. on 2010-11-27
Hello,

In my website, I'm putting shared files in a "/global" folder.  Both "styles.css" and "library.php" are in this global folder.

HTML code seems to be working ok - the following bit works great to pick up a style sheet:

```

<link rel="stylesheet" type="text/css" href="/global/styles.css" />

```

However PHP does not seem to understand my root directory.  Using the following does not work:

```

include_once("/global/library.php");

```

I receive a "failed to open stream:  No such file or directory" error.

Spelling out the entire full path works, like so:

```

include_once("/srv/www/mysite/global/library.php");

```

But this type of code is no good as I may change servers in the future.

I have my "DocumentRoot" set correctly in my sites-available file.  It seems as if PHP is ignoring it.  Is there a config file someplace (htaccess?  Local php.ini?) where I should update my root directory for *this site only*?  Or am I following bad form and there's a better way to do this?  Relative paths don't seem like the answer here though...

---

### Post by Lucky. on 2010-11-27
I see that I can edit my local php.ini and set the following:

```

include_path = ".:/usr/share/php:/srv/www/mysite/global"

```

This adds my global directory to the list of paths to check, so the following now works from any of my pages:

```

include_once("library.php");

```

However this isn't the exact functionality I was looking for.  I would really like to specify that my site is the root, and find my additional files that way, like so:

```

include_once("/global/library.php");

```

Maybe I'm being picky here, please tell me if this is just a silly requirement that nobody uses.  But if it is possible, I'd like this.

---

### Post by CharlesA on 2010-11-27
Ran into the same problems with the paths to php files when using root addressing. I'm just using relative addresses now, since it'll be easy to deal with for me.

---

### Post by SeijiSensei on 2010-11-27
> But this type of code is no good as I may change servers in the future.

I usually build sites that run an initialization script that sets a number of globals like the root of the scripts directory.  I just change this variable if I need to relocate the sites.  Works well where you have a production and a development version in different locations.

> However this isn't the exact functionality I was looking for. I would really like to specify that my site is the root

Just remove the "/global" from the include_path entry you posted.  Then you can run "include_once('/global/script.php')" and have it be correctly rooted.

I generally use paths that end with a trailing slash.  Then I can write includes like:

```

$incl="/some/path/to/include/dir/";
include($incl.'script.php');

```

---

### Post by czr114 on 2010-11-28
File resolution works differently in PHP than in CSS/HTML.

In CSS/HTML, / can't go any higher than the root of the site.

PHP operates in the standard filesystem environment unless it's been put in a chroot jail. Unless it has, / goes higher than the web server's DocumentRoot.

When you code /global in PHP, it's looking for global off of the FS root ( / ).

If you change that path to './global/foo.php' (notice the dot), that will resolve the path off the current directory.

There are better ways of handling this in larger projects, but you'll get to those in time.

For now, just begin your PHP path resolution with the current directory '.'

---

### Post by Lucky. on 2010-11-28
Thanks a bunch everyone, these are some great answers & explanations.  I have a lot to choose from.

---

