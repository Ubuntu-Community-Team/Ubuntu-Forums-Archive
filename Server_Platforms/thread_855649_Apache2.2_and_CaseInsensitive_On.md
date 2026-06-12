---
title: "Apache2.2 and CaseInsensitive On"
date: 2008-07-10
forum: Server Platforms
---

### Post by altonbr on 2008-07-10
I'm currently moving a website from a shared environment to a dedicated and I'm having trouble with [an Apache directive called CaseInsensitive]("http://www.google.ca/search?q=apache+%22caseinsensitive+on%22&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a").

The website runs - on both machines - in a standard LAMP environment using Apache 2.2, MySQL 5.0 and PHP 5.2.4.

Both machines are mirrored and thus have a .htaccess file in the root directory that contains the directive 'CaseInsensitive On'.

When sitting on the new dedicated, Ubuntu server, it returns with a 500 internal script error. When I comment the line out, it goes away.

I can find absolutely zero documentation for this directive, but it works perfectly in the shared environment.

I did find an article that stated mod_speling had to be enabled with 'CheckSpelling On' in /etc/apache2/mods-available/speling.conf

It works, sort of, but it doesn't work as well as 'CaseInsensitive On', which is still giving me errors.

CheckSpelling On -- allows you to spell a canonical URL such as
**[http://example.com/TEST](http://example.com/TEST)** and have it redirect to **[http://example.com/test](http://example.com/test)**. However, when the URL ends in a forward slash '/', indicating a directory, Apache will literally look for /TEST/ and not offer any case-insensitivity unlike when the 'CaseInsensitive On' directive is enabled.

Does anyone have experience with 'CaseInsensitive On'?

---

### Post by Kleenux on 2008-07-10
I don't think there is a CaseInsensitive directive in Apache.
Case sensitivity depends upon the OS... Linux is case sensitive, Windows is not.

CheckSpelling search case-insensitively for the documents in a given directory. So the directory itself must be "rightly-cased".

If you only worry about all-big or all-small chars for directory names, you could create sym-links in the document tree:

# ln -s test TEST

(and possibly adjust options to authorize follow-symbolic-links, something like
<Directory /...>
  Options FollowSymLinks
  AllowOverride None
</Directory>
or in .htaccess )

Thus, 
[http://x.y.z/test/mydoc.html](http://x.y.z/test/mydoc.html)
and
[http://x.y.z/TEST/mydoc.html](http://x.y.z/TEST/mydoc.html)

would equally work.

---

### Post by cariboo on 2008-07-10
Have a look at this page:

[http://httpd.apache.org/docs/1.3/misc/FAQ-H.html](http://httpd.apache.org/docs/1.3/misc/FAQ-H.html)

It may lead to a solution.

Jim

---

### Post by altonbr on 2008-07-11
> **cariboo907 said:**
> Have a look at this page:

[http://httpd.apache.org/docs/1.3/misc/FAQ-H.html](http://httpd.apache.org/docs/1.3/misc/FAQ-H.html)

It may lead to a solution.

Jim

Thanks for the link and the following paragraph:

> How can I make all my URLs case-insensitive with mod_rewrite?

You can't! The reasons are: first, that, case translations for arbitrary length URLs cannot be done via regex patterns and corresponding substitutions. One needs a per-character pattern like the sed/Perl tr|..|..| feature. Second, just making URLs always upper or lower case does not solve the whole problem of case-INSENSITIVE URLs, because URLs actually have to be rewritten to the correct case-variant for the file residing on the filesystem in order to allow Apache to access the file. And the Unix filesystem is always case-SENSITIVE.

But there is a module named mod_speling.c in the Apache distribution. Try this module to help correct people who use mis-cased URLs.

Still doesn't explain why the one Apache server is allowing case-insensitivity with that declaration and why the new Ubuntu-based server is failing because of it. Then, mod_speling only works slightly like the 'CaseInsensitivty On' declaration as it can't re-write URLs with a trailing slash as it takes them literally.

---

### Post by MountainX on 2009-02-16
[http://yost.com/computers/apache-redirect/apache-patch.html](http://yost.com/computers/apache-redirect/apache-patch.html)

warns against using mod_speling

---

### Post by altonbr on 2009-02-17
> **MountainX said:**
> [http://yost.com/computers/apache-redirect/apache-patch.html](http://yost.com/computers/apache-redirect/apache-patch.html)

warns against using mod_speling

Ya, I know, when work needs something, work needs something, right? Even with all my knowledge of security, they'd rather get stuff done than do it right.

I left them partly for that reason.

Thanks for the link though!

---

