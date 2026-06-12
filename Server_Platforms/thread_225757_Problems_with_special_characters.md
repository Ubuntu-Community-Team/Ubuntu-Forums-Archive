---
title: "Problems with special characters"
date: 2006-07-30
forum: Server Platforms
---

### Post by iric on 2006-07-30
Had Fedora 2 before and now Ubuntu 6.06.
All special characters like € é ë ï ç are not shown on my websites!

It gets replaced by a ? or a square box.

How to get this fixed? It's a really annoying problem.

(It is on the websites, but also when I open a file in a text editor etc., but as I use Ubuntu as webserver I'd like this fixed).

Thanks in advance.

---

### Post by foxylad on 2006-07-30
Examine the source of the page. Usually this sort of problems is due to your sepecifying the wrong character set. For instance, this very page contains:

<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1" />

If you are sure the charset is correct, next you need to check your browser is doing the right thing with those characters.

---

### Post by adamkane on 2006-07-30
We need more details how you installed Ubuntu, and whether you transfered any files from one computer to another.

Do you have any recollection what language settings you chose when you installed Ubuntu?

---

### Post by iric on 2006-07-31
> **adamkane said:**
> We need more details how you installed Ubuntu, and whether you transfered any files from one computer to another.

Do you have any recollection what language settings you chose when you installed Ubuntu?

Installed ubuntu from network install, the output from locale (in the terminal) gives me:

LANG=en_US.UTF-8
LANGUAGE=en_NL:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

I transferred files directly from the Fedora server through SSH.

When I take one of the pages that has this problem and view the source it has:

 <meta http-equiv="content-type" content="text/html; charset=iso-8859-1" />
<TITLE>Forumschorum.nl - De officiële forumschorum fansite!</TITLE>

So here you see there is an "ë" in it, the title bar doesn't give the whole word "officiële" but gives "offici" and the next character is a little square box (in windows/IE) and it doesn't give the other characters in that word.

So in the source everything looks fine, but one way or another Ubuntu doesn't show this correctly, even on a Windows machine...

---

### Post by adamkane on 2006-07-31
I'm struggling along with you, so forgive me if I'm unhelpful.

It looks like there is a mismatch between your html tags and the data under the tags.

This line says that your text is iso-8859:
 <meta http-equiv="content-type" content="text/html; charset=iso-8859-1" />

But the text itself is utf-8, since it appears correctly in your text editor:
<TITLE>Forumschorum.nl - De officiële forumschorum fansite!</TITLE>

I would change to:
 <meta http-equiv="content-type" content="text/html; charset=utf-8" />

Save the file, and view again in your browser.

---

### Post by iric on 2006-07-31
> **adamkane said:**
> I'm struggling along with you, so forgive me if I'm unhelpful.

It looks like there is a mismatch between your html tags and the data under the tags.

This line says that your text is iso-8859:
 <meta http-equiv="content-type" content="text/html; charset=iso-8859-1" />

But the text itself is utf-8, since it appears correctly in your text editor:
<TITLE>Forumschorum.nl - De officiële forumschorum fansite!</TITLE>

I would change to:
 <meta http-equiv="content-type" content="text/html; charset=utf-8" />

Save the file, and view again in your browser.

ok but that's 1 page on 1 site. I have over 30 sites with all different tags and thousands of pages. Besides these settings did work under Fedora and the problems also occur in MySQL!

Transferred MySQL databases through Navicat directly under Ubuntu by the way.

---

### Post by iric on 2006-07-31
hm tried your suggestion but it doesn't help at all

---

### Post by adamkane on 2006-07-31
I think you also have to set mysql correctly. Do you know if mysql is utf-8 or iso-8859?

Do you have phpmyadmin installed?

---

### Post by iric on 2006-07-31
> **adamkane said:**
> I think you also have to set mysql correctly. Do you know if mysql is utf-8 or iso-8859?

Do you have phpmyadmin installed?

I do have phpmyadmin but I always use Navicat.
Another thing: when I post a forum message on the forum which has this problem and it contains one of the characters it is ok (but the most strange thing is: view source under windows and the characters are there!)

The problem is nog html/php specific or characterset metatag specific or mysql specific, that's the point, there are many things that go wrong...

---

### Post by adamkane on 2006-07-31
I suspect your import via Navicat. I would simply export your data to a .sql file and import with phpmyadmin assuming you've created a new database with the correct language settings using phpmyadmin.

---

### Post by iric on 2006-07-31
> **adamkane said:**
> I suspect your import via Navicat. I would simply export your data to a .sql file and import with phpmyadmin assuming you've created a new database with the correct language settings using phpmyadmin.

But it is not only mysql, that is the strange part...

Creating databases happens in my control panel.

And besides: import a 250mb sql file in phpmyadmin is no good idea ;)

---

### Post by adamkane on 2006-07-31
You could do a test run with a small part of your database. This would at least isolate the problem.

Same goes for Navicat. You could try to adjust your settings in Navicat and try some test exports.

Maintaining special characters after migrating to Ubuntu is a huge undeveloped area. I created several threads relating to loss of special characters when migrating from NTFS to ext3 in Ubuntu.

This is going to take some research and trial and error.

---

### Post by iric on 2006-07-31
> **adamkane said:**
> You could do a test run with a small part of your database. This would at least isolate the problem.

Same goes for Navicat. You could try to adjust your settings in Navicat and try some test exports.

Maintaining special characters after migrating to Ubuntu is a huge undeveloped area. I created several threads relating to loss of special characters when migrating from NTFS to ext3 in Ubuntu.

This is going to take some research and trial and error.

I'll try some stuff on navicat but that doesn't help the non-database problem (because it is also in html files). I always used EXT3, and copied the files directly from Fedora on the Ubuntu machine with SSH.

---

### Post by adamkane on 2006-07-31
When you said you had a problem viewing in your browser, I thought you meant it was a problem in all browsers.

Can you view the html pages correctly from another machine on your network.

If the problem is just your local language settings, then you are not doing too badly.

---

### Post by iric on 2006-07-31
> **adamkane said:**
> When you said you had a problem viewing in your browser, I thought you meant it was a problem in all browsers.

Can you view the html pages correctly from another machine on your network.

If the problem is just your local language settings, then you are not doing too badly.

It is on all pages, html, php, database driven or not which contain special characters on all machines, inside and outside this network, on FF, Opera, IE or IBrowse, on Windows, Linux and even on my Amiga, so it's not just one setting.

Take this example: [www.ad-it.nl](www.ad-it.nl) 
and also view it's source, it should be one of the special characters there...

---

### Post by adamkane on 2006-07-31
Thanks.

Are you able to browse your data using Navicat or phpmyadmin?

Where is the file located that you excerpted earlier. Did you view that with Nautilus and a text editor?

---

### Post by iric on 2006-07-31
> **adamkane said:**
> Thanks.

Are you able to browse your data using Navicat or phpmyadmin?

Where is the file located that you excerpted earlier. Did you view that with Nautilus and a text editor?

The site mentioned is 1 sentence in html, that's all.

When I view the sql file in GEdit under ubuntu it gives strange squares with numbers in it on the places of the special characters.

When I open the very same SQL file in Windows I do see the special characters as they should be:

INSERT INTO `*removed this*` VALUES ('site_desc', 'De officiële forumschorum fansite!');

---

### Post by adamkane on 2006-07-31
Your data is probably still iso-8859-1 (latin) encoded.

My opinion now is that you need to create an empty database with iso-8859-1 encoding, transfer a sample database and see what happens. 
---
Another option is to create a new utf-8 database and convert your data from iso-8859-1 to utf-8 during the migration.

```

iconv -f latin1 -t utf-8 %u -o %u_utf-8

```

See also:
[http://www.mkssoftware.com/docs/man1/iconv.1.asp](http://www.mkssoftware.com/docs/man1/iconv.1.asp)
---
Something is wrong with the language settings of your database. If you look at your database in phpmyadmin, you can find out what your language settings are.

Please advise.

---

### Post by kag on 2006-07-31
I don't remember exactly in which file it is (I'm not in front of my Ubuntu box), but I believe the source of the problem is from this Apache directive:

```
AddDefaultCharset utf-8
```

Try to change it to
```
AddDefaultCharset iso-8859-1
```

---

### Post by iric on 2006-08-01
> **kag said:**
> I don't remember exactly in which file it is (I'm not in front of my Ubuntu box), but I believe the source of the problem is from this Apache directive:

```
AddDefaultCharset utf-8
```

Try to change it to
```
AddDefaultCharset iso-8859-1
```

when it's httpd.conf I'm not sure if it will work as I installed VHCS2 and I tried this with indexes too (not to make directory indexes) and it didn't work.
Could you please find out which file I need to edit? Thanks

---

### Post by kag on 2006-08-02
I believe it's in [FONT="Courier New"]/etc/apache2/conf.d/charset[/FONT]

If it's not, just go in [FONT="Courier New"]/etc/apache2/[/FONT] and [FONT="Courier New"]grep AddDefaultCharset[/FONT]

---

### Post by iric on 2006-08-02
> **kag said:**
> I believe it's in [FONT="Courier New"]/etc/apache2/conf.d/charset[/FONT]

If it's not, just go in [FONT="Courier New"]/etc/apache2/[/FONT] and [FONT="Courier New"]grep AddDefaultCharset[/FONT]

/etc/apache2/conf.d/charset gives:

AddDefaultCharset UTF-8

Should I add iso-8859-1 as well?

---

### Post by kag on 2006-08-02
I commented it and added ISO-8859-1. It looked like this:

```
#AddDefaultCharset utf-8
AddDefaultCharset iso-8859-1
```

---

