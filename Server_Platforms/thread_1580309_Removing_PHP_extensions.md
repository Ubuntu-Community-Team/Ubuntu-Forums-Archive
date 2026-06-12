---
title: "Removing PHP extensions"
date: 2010-09-23
forum: Server Platforms
---

### Post by ignas2526 on 2010-09-23
Hello,
Basically I'm trying to build PHP without some extensions like ereg. Then I tried to remove ereg folder from ext and build PHP, I got an error.
How to remove PHP extensions from PHP source before building it?
Thanks.

---

### Post by MortenA on 2010-09-23
... can't help you, but I'm a bit curious: What would the point be in doing something like that?

---

### Post by ignas2526 on 2010-09-23
@MortenA: Well first of all the more extensions you have, the slower things get.
Second: Some extensions in PHP just useless like eregi, it is deprecated, but still comes with PHP, so I really would like to wipe out it completely.

---

### Post by SeijiSensei on 2010-09-23
> **ignas2526 said:**
> @MortenA: Well first of all the more extensions you have, the slower things get.

As I recall back in the days when I built php and apache from source, you can specify which PHP modules to include in compilation while running ./configure.  

That said, I don't think you're going to see noticeable performance improvements if you build a more stripped-down version of PHP.  In my experience, other factors like overall server load, amount of graphics content, availability of links to offsite resources, and server and client bandwidth limitations all play a much greater role in determining how fast a page loads in a browser.  A couple of milliseconds savings at the level of PHP interpretation will never be noticed.  Excluding something like ereg isn't going to have much effect on the size of the PHP binary, either.

If you're concerned about performance, I suggest looking at some of the PHP "[accelerators]("http://en.wikipedia.org/wiki/List_of_PHP_accelerators")" that employ caching techniques.

I still have scripts from years past that use ereg().  If you're the only one writing scripts that will be distributed from this server, removing things is fine.  If you're hosting other peoples' content, or using PHP applications from the Internet, removing things from PHP, even deprecated modules, raises the possibility of breaking a script entirely.

---

### Post by ignas2526 on 2010-09-23
@SeijiSensei: Well I'm developer myself, and I'm right now developing highly optimized script, so I specially installed Ubuntu, because I need extension called VLD, I haven't managed to compile PHP on Windows, wasted over 6 hours. I'm aware about accelerators, they kinda mess performance results, so I have no plans using them.
Regarding to what disabling extensions doesn't improve things much is true, but I don't like long phpinfo pages :).
I have no idea how eregi gets with PHP, because I never instructed in configure to enable it, so I'm confused. How to disable it?
In windows it used to be easy, you just go to php.ini and comment line with extension, since all extensions are DLL's.

---

