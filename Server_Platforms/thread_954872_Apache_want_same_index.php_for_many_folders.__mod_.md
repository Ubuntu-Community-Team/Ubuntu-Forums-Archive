---
title: "Apache: want same index.php for many folders.  mod_rewrite?"
date: 2008-10-21
forum: Server Platforms
---

### Post by Youresorock on 2008-10-21
I have a new website I'm setting up, where I have an index.php file which pulls content from either a text file or a mysql query and displays it.

I currently have this identical file in 10 folders off the root.  eg:

index.php             // main site
/about/index.php      // about us
/contact/index.php    // contact info

You get the idea.  I'd like to just use one copy of that file so I don't need to redistribute it if I need a change.

I want the URL to be eg: [www.example.com/about/](www.example.com/about/)
not [www.example.com/index.php?i=about](www.example.com/index.php?i=about)

There's gotta be a way to do this.  I don't know what to search for for ideas.

---

### Post by MJN on 2008-10-23
Apache's 'Alias' function is what you need. See [here](http://httpd.apache.org/docs/2.0/mod/mod_alias.html) for details.
 
You're probably already using in by default in apache2.conf for things like documentation, icons etc.
 
Mathew

---

### Post by Youresorock on 2008-10-23
Thanks!  I know where to start at least now.

I've tried a number of directives on that site, but haven't had success yet.

I took the index.php out of my /about/ folder, and get a 403 Forbidden for /about/   

And 404 Not Found for /about/index.php

```
Alias ^/index.php /index.php
```
```
AliasMatch ^/index.php /index.php$1
```

Naturally, I reload apache after each thing I try.  The apache error log makes it look like the alias line isn't being used.  I made sure the alias module was loaded with a2enmod.

```

[Thu Oct 23 15:42:07 2008] [error] [client 127.0.0.1] Directory index forbidden by Options directive: /home/jduffy/www/duffy/about/
```

---

### Post by Youresorock on 2008-10-23
I've found if I'm painfully explicit, it works.

```
AliasMatch /about/index.php /home/jduffy/www/duffy/index.php

```

However this doesn't help me, because I'd have to make an alias for every folder.  I want every folder to appear as if it had the index.php in it.

---

### Post by Youresorock on 2008-10-23
I realize I've been talking to myself all morning, but I made some progress and wanted to update the thread:

```
AliasMatch (.*)/index.php /home/jduffy/www/duffy/index.php

```

I don't really understand the (.*) part, but it works.

Now if I go to /about/ it works.

---

### Post by MJN on 2008-10-23
The .* is a regular expression which basically means 'any character, zero or more times' hence it matches everything. The brackets could be omitted - they are only used if you want to refer to the 'everything' later in the expression.
 
Are you all sorted with regards to your original requirement?
 
Mathew

---

### Post by Youresorock on 2008-10-23
Thanks MJN--

Yeah, whichever folder I go to, pulls the index.php off the root like I wanted.  

I do have one other problem however.  I need to remove the index.php from the URL if someone types it in for some reason.

There are tons of hits on google for "remove index.php" but they're all doing something wierd.  I just want:

website.com/about/index.php  --> website.com/about/

I've only managed to give myself redirect loops.  :D

---

### Post by Youresorock on 2008-10-23
For now, since I've been unable to do it in apache, I added the following lines to the start of my index.php file:

```
<?php if (strstr($_SERVER['REQUEST_URI'] , 'index.php')) { 
$location = trim($_SERVER['REQUEST_URI'] , "index.php");
header("HTTP/1.1 301 Moved Permanently"); header("Location: $location");}?>

```

This works fine, but it seems like doing it in apache would make more sense.

---

