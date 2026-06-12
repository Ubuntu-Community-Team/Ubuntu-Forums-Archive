---
title: "Php 5.1.0"
date: 2005-11-25
forum: Requests
---

### Post by GothicX on 2005-11-25
Changelog:

[http://www.php.net/ChangeLog-5.php#5.1.0](http://www.php.net/ChangeLog-5.php#5.1.0)

Backport it :-) it has some many bug fixes and features...

---

### Post by jdong on 2005-11-25
PHP5 is a supported main package; I'd like errata/security fixed to be handled by Ubuntu developers, unless there's a serious amount of neglect in the area....

---

### Post by ember on 2005-11-25
From what I hear, 5.1 breaks compatibility with some PEAR-class (I knew of date). Not that it's PHPs fault, but maybe only a semi-good idea to have it backported.

---

### Post by akurashy on 2005-11-25
well im really looking for this :)

---

### Post by GothicX on 2005-11-25
Jdong, sorry =)

---

### Post by akurashy on 2005-11-25
ok i don't think i can get it working compiling it, so i guess i wait for jdong till he decides

---

### Post by whatever on 2005-11-25
# PHP5.1 for Ubuntu breezy
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.1 breezy
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.1 breezy

---

### Post by GothicX on 2005-11-27
Nice, but I will wait until someone copies it to backports =)

---

### Post by jdong on 2005-11-27
Sadly, that's probably not going to happen. The developers are also very opposed to backporting newer PHP, and prefer that any gripes with the current PHP be addressed with the Ubuntu team.

---

### Post by GothicX on 2005-11-27
So PHP 5.1.0 won't be included in breezy !? I'm also a PHP developer, and I'm coding a new website for my company and it doesn't breaks.. tomorrow I'll check more at work, but 5.1.0 are more bugfixes than features.. it deserves the update.

---

### Post by akurashy on 2005-11-27
[quote=jdong]Sadly, that's probably not going to happen. The developers are also very opposed to backporting newer PHP, and prefer that any gripes with the current PHP be addressed with the Ubuntu team.[/quote]

but it will be in dapper right?

---

### Post by jdong on 2005-11-27
correct. Most likely, with a bit of using ubp-build.py, once php 5.1.0 hits Dapper you can build a copy yourself, like a "personal backport" if you will... I just can't decide for all Ubuntu users that everyone wants the latest and greatest PHP 5.1.0, nor will I pretend to know how PHP works well enough to apply a security patch properly to Ubuntu/Debian modified PHP sources if such a situation arises!

---

### Post by akurashy on 2005-11-28
just a notice to people reading this,

> The PHP Development Team would like to announce the immediate release of
PHP 5.1.1.

This is a regression correction release aimed at addressing several
issues that may cause issues for some applications. The main fixes
found in this release include the following:

* Native date class is withdrawn to prevent namespace conflict with
PEAR's date package.
* Fixed fatal parse error when the last line of the script is a PHP comment.
* eval() hangs when the code being evaluated ends with a comment.
* Usage of \{$var} in PHP 5.1.0 resulted in the output of {$var} instead
of the $var variable's value enclosed in {}.
* Fixed inconsistency in the format of PHP_AUTH_DIGEST between Apache 1
and 2 sapis.
* Improved safe_mode/open_basedir checks inside the cURL extension.

The full details of the changes in PHP 5.1.1 can be found here:
[http://www.php.net/ChangeLog-5.php#5.1.1]("http://www.php.net/ChangeLog-5.php#5.1.1")


PHP Development Team.

--
PHP Announcements Mailing List ([http://www.php.net/]("http://www.php.net/"))
To unsubscribe, visit: [http://www.php.net/unsub.php]("http://www.php.net/unsub.php")

---

### Post by svyatogor on 2005-12-02
[QUOTE=whatever]# PHP5.1 for Ubuntu breezy
deb [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.1 breezy
deb-src [http://people.debian.org/~dexter](http://people.debian.org/~dexter) php5.1 breezy[/QUOTE]


Thank you! Finally they fixed the ze1_compatibilty and I can keep on working on some applications that require it :)

For general education purposes, why did you call it php-5.1 and not php5 with just a new version number 5.1.0?

---

### Post by whatever on 2005-12-02
[QUOTE=svyatogor]For general education purposes, why did you call it php-5.1 and not php5 with just a new version number 5.1.0?[/QUOTE]
i did neither call it anything, nor did i build these packages.

---

