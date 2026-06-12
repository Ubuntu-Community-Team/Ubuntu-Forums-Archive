---
title: "Web Server Stopped Working"
date: 2010-09-21
forum: Server Platforms
---

### Post by Vegan on 2010-09-21
earlier today, my web server stopped working. 

Any suggestions, I am scanning the server for malware just in case.

When I open the home page, it wants to save a file.

Opening the file in notepad, shows the HTML as expected. The browser seems to not render it. I wonder if apache2 has been borked?

---

### Post by arrrghhh on 2010-09-21
Is it a PHP page?  I've seen this happen with PHP before... it's usually the client tho and not the server in my experience.

---

### Post by Vegan on 2010-09-21
All of my pages are PHP, and it was working fine until 2 hours ago.

I had to use localhost, all remote access was down

including webmin and SSL terminal

---

### Post by arrrghhh on 2010-09-21
You tried from a different machine?  Like I said before, usually when this happens it's the client.  Lemme do a quick search, I **swear** I've seen a thread on this before...

Ok, based on the [ApacheMySQLPHP Community Page](https://help.ubuntu.com/community/ApacheMySQLPHP) it does appear to be a server thing.  Check out the "Troubleshooting PHP 5" section.

---

### Post by LinuxPhreak on 2010-09-21
Why not check the Firefox Preferences. This happens if Firefox is told to download files that end in certain extension. In your case php.

Why don't you post the URL to see if others are getting the same problem. 

Firefox under Ubuntu.

Edit > Preferences and check the configurations. 

Firefox for Windows

Tools > Options and check the configurations.

---

### Post by Vegan on 2010-09-21
I tried  from the LAN etc. So I now see my server is rebooting rather often so something deep is wrong.

I ran some tests and php5 seems to be borked, so I tried fixing it, and a part of apache2 was sick so I fixed that.

Still not working. So back to zilch and format the disk try again.

---

### Post by arrrghhh on 2010-09-21
Have you figured out what's causing the reboots?  If something else is wrong, that's definitely an odd side-effect...

---

### Post by Vegan on 2010-09-21
I was able to make a SQL dump from MySQL so now the fun of restoring all the databases.

No other way to backup the files that I know of.

---

### Post by arrrghhh on 2010-09-22
> **Vegan said:**
> I was able to make a SQL dump from MySQL so now the fun of restoring all the databases.

No other way to backup the files that I know of.

Ah you're just goin for the reboot reimage... Fair enough.  Shame tho, it always bugs me when crap like this happens and is completely unexplained... makes me start worryin' about hardware and such... :p

---

### Post by SeijiSensei on 2010-09-22
While your problems sound more profound than just the fact that PHP stopped interpreting your pages, that's what generates the error you reported in your original post.  Typically this occurs when Apache has no handler defined for the .php or .php5 extensions, or the handler software is broken in some way.  Since the file doesn't have a known handler, Apache tells the browser to download the file directly.

---

