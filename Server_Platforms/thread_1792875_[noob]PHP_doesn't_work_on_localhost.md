---
title: "[noob]PHP doesn't work on localhost"
date: 2011-06-28
forum: Server Platforms
---

### Post by SirKonstantine on 2011-06-28
OK, I have a fresh install of Ubuntu and changed out Unity for GNOME3. I installed LAMP via "apt-get install lamp*" or something like that. The '*' was suppose to be the carrot.

Then I changed my default public_http from "/var/www/" to "~/website/" and it works. If I load a HTML website, I can see it just fine.

The problem is that I can't see my PHP websites. I checked and made sure PHP was installed with "php -v" and it shows I have PHP 5.3.5.

I'm guessing I'm missing an entry into a PHP config file or something. Thanks.

---

### Post by Bachstelze on 2011-06-28
What happens when you try to load a PHP site? Also paste the output of

```
dpkg -l | grep php
```

---

### Post by SirKonstantine on 2011-06-28
When I try to load up a PHP site, it only loads up the HTML part and ignores any PHP parts. ie, my title is <title>$TitleName</title> and it appears as "Untitled Doc"

```
sirkonstantine@Chode3000:~/Websites$ dpkg -l | grep php
ii  libapache2-mod-php5                   5.3.5-1ubuntu7.2                                               server-side, HTML-embedded scripting language (Apache 2 module)
ii  php5                                  5.3.5-1ubuntu7.2                                               server-side, HTML-embedded scripting language (metapackage)
ii  php5-cli                              5.3.5-1ubuntu7.2                                               command-line interpreter for the php5 scripting language
ii  php5-common                           5.3.5-1ubuntu7.2                                               Common files for packages built from the php5 source
ii  php5-mysql                            5.3.5-1ubuntu7.2                                               MySQL module for php5

```

---

### Post by Bachstelze on 2011-06-29
That's weird, generally when PHP is not properly installed, the user is given a "download" option for .php files (since Apache does not know the extension). Can you give some more detail? How is the file named? Where is it located? How are you trying to access it?

---

### Post by SeijiSensei on 2011-06-29
> <title>$TitleName</title> and it appears as "Untitled Doc"

Is that really what you're using, or an incorrect example?  You don't have any tags to invoke the parser like this:

```
<title><?=$TitleName?></title>
```

The "<?" and "?>" tags mark the beginning and end of a PHP script.  "<?=" is a shorthand for "<? echo".

(Technically, you should use <?php at the beginning if you're using multiple parsers, but most people just run PHP so <? is acceptable if the PHP option "short_tags" is enabled in php.ini, which is usually the default.)

---

