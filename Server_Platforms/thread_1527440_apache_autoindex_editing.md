---
title: "apache autoindex editing"
date: 2010-07-09
forum: Server Platforms
---

### Post by buckley310 on 2010-07-09
hi, i want to edit my change the format of the auto-index page to something different. (preferably something more iPhone friendly) i have been looking around on the web and i managed to find /etc/apache2/mods-enabled/autoindex.load and .conf and /usr/lib/apache2/modules/mod_autoindex.so. i believe these 3 files are responsible for auto-indexing but i dont know how to manually edit them. help?

---

### Post by Hanzerik on 2010-07-09
You can change autoindex.conf

[http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html](http://httpd.apache.org/docs/2.0/mod/mod_autoindex.html)

Not sure what you want to change to make it more iPhone friendly, but the apache docs are pretty good about explaining the "IndexOptions" directive. You can also change the way the items will be ordered with the "IndexOrderDefault" directive.

The "IndexOptions" directive is the first active line in autoindex.conf, all of your options will be on one line seperated by a space.
```

IndexOptions SuppressHTMLPreamble SuppressDescription SuppressRules FancyIndexing HTMLTable NameWidth=* Charset=UTF-8

```

These settings (along with custom HEADER/README files) gives me this:
[http://hanzerik.servehttp.com/~hanzerik/gallery/](http://hanzerik.servehttp.com/~hanzerik/gallery/)
A basic auto indexing of files, without the use of fancy html or php.

There are only two php pages on my site, everything else is done through the HEADER and README files as far as formating. I edit files on my server using vi, but you can use whatever editor you are comfortable with. Make a backup of the file before you start editing it if you are worried about messing it up. The "files" in mods-enabled are just symbolic links to the files in mods-available, so make a backup of the file in mods-available.

You enable a module by using the a2enmod command:
```

sudo a2enmod autoindex

```

---

### Post by buckley310 on 2010-07-09
this is helpful but im looking for a bit more...somewhere there is code that apache executes. this code lists the files, processes them and returns a formatted html page. im looking for a way to edit that on a level for instance where if i wanted to add a text smiley face at the beginning of every line i could. perhaps im asking too much of this mod and i need to either use another mod or create my own? all im looking to do is to create a page that lists the files and thats it. maybe display the current directory at the top.

---

