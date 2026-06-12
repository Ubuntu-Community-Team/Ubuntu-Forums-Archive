---
title: "Modding PHP5 for development chain..."
date: 2012-09-16
forum: Ubuntu Studio
---

### Post by SilentThunderStorm on 2012-09-16
What I want to do is to turn on PHP5 interpretation for both .css and .js files, while still returning the proper MIME header.

I want to do this so that I can keep the pages I design extremely neat, minimize http requests, and maximize caching.

In other words:

<link rel='stylesheet' href='dynamicsheet.css'>
<script src='dynamicscript.js'></script>

The requested files would be interpreted as .php allowing them to determine the client platform, browser, and the page requested (as well as anything else you might think of), and intelligently load and concatenate the files, as well as handle load order, dependencies, etc. etc. etc.

Basically, I want to be able to handle these files the same way one handles a make file, or a manifest.

This way, I could tailor the css sheets for the device that was loading the site (for example, tablets would get the tablet .css, etc.) and would cache the sheet needed for that device.

Same with scripts... the scripts loaded by the backend would be dynamically built to match the client device and browser, and would be cached on that machine.

Similarly, it would allow me to break down the .css and .js into more easily manageable files on server side, while the file that the browser actually loaded ('dynamicsheet.css', for example) would then properly manage and compile the required stylesheets and scripts needed for that specific page.

In this way, I could have a single http request load up jQuery, Less, Bootstrap, and both site-wide and page specific scripts...all in a single file, and including proper caching.

Currently, the normal solution to this is requesting and transmitting huge chunks of code that don't even apply to that machine, only to not used it... and doing so through a ton of http requests.

There are so many good reasons for dynamically generating .css and .js that I can't believe it has not been a standard practice for years already.

My problem is that while I can program both client side and web stuff... I have very little knowledge or experience when it comes down to the actual internals of a web server.

Everywhere that I have seen someone ask a question even remotely like this they are told "don't do that", or "just name them all .php".  Often the server overhead of interpreting any file other than .php is seen as a "waste of server resources"... but for the resons listed above, I disagree.

Naming all the .css and .js files to .php would leave them with the wrong header information, which would generate ugly errors on the client end.

As for 'wasting server resources' by interpreting files that don't require it?  Two points...First, *MY* files would require it, so there is no waste... but also Secondly, it should be possible to allow .css and .js to remain as is, but to allocate new file types, such as .ccss and .cjs (compiled css and compiled javascript), which *are* interpreted and which have their own proper MIME type.

Does anyone know how to convince the server to do so?

I have heard that I need to modify the httpd.conf, OR the php5.ini, OR etc, etc etc.... yet in each case, no accurate or explicit instructions follow.

Does anyone have a clue how to get this done?

I can't believe it is really THAT hard to do.

Any help would be greatly appreciated, with much kharmic love being fed to Buddha in your name and all.... puppies will smile.

---

### Post by SilentThunderStorm on 2012-09-17
OK... got it.

There are a few basic ways to do this:

Easiest is to simply call the file .php, and insert into the code the line <?php header('Content-type: text/css'); ?>.... then the file returns with the proper MIME type for the browser.

I can also set up a new file type by modding the .htaccess file by adding the line 'AddHandler application/x-httpd-php .ccss'... then any files named XXXXX.ccss will be interpreted by php5; but will still require the header line within their code.

Last remaining hurdle to really polish this off is to figure out a way to get .htaccess (or whichever other apache file) to automatically attach the appropriate header to these new file types.

Will file it here if I find the rest of this solution.

---

### Post by SilentThunderStorm on 2012-09-17
OK.. think I have it here:

AddHandler application/x-httpd-php .ccss
AddHandler application/x-httpd-php .cjs
AddType text/css .ccss
AddType application/x-javascript .cjs 

Add this to .htaccess file, and any .ccss or .js files served from underneath it will be interpreted as PHP, but return with the proper MIME types.

Still untested (as I just found the answer), but will be updated here if it fails.

---

### Post by SilentThunderStorm on 2012-09-21
Well, so far, adding the line in the .css or .js file works, but still must be named .php.

Still working on getting a cleaner solution to work (such as adding file types).

Will keep working till I get it right.

---

