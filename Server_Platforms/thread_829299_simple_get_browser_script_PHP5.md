---
title: "simple get_browser script PHP5"
date: 2008-06-14
forum: Server Platforms
---

### Post by magpy on 2008-06-14
Hi all

Need help using a server side get_browser detection script in either .php or .html files.  My attempt does not work - only the last 'else' code block linking to main-2.css works, any advice much appreciated.  The script below is located within php tags in the header section of either the .html or .php file.

  $browser = get_browser( );

  if ($browser == IE && (majorver <= 6)) {

     print '<link rel="stylesheet" type="text/css" href="main-0.css">';

  } elseif ($browser == IE && (majorver >= 7)) {

     print '<link rel="stylesheet" type="text/css" href="main-1.css">';

  } else {

     print '<link rel="stylesheet" type="text/css" href="main-2.css">';

  }

what I really want is a statement a bit like this:

'if browser IE and version <=6 use this .css file'

'if browser IE and version >=7 use this .css file'

'else use this .css file'

Cheers

---

### Post by koenn on 2008-06-15
[http://www.htmlforums.com/php-programming/t-php-detect-browser-21283.html](http://www.htmlforums.com/php-programming/t-php-detect-browser-21283.html)
[http://apptools.com/phptools/browser/](http://apptools.com/phptools/browser/)
[http://apptools.com/phptools/browser/source.php](http://apptools.com/phptools/browser/source.php)

& a google search for php browser detect returns tons of results, most of them have code samples

---

### Post by magpy on 2008-06-15
Hi - thanks for the urls!

I have seen these and many others like them.  They are however
a bit too complex for the php beginner.  I am looking for a simple
if statement that achieves similar results.

I understand that these examples are probably more scalable/logical
though I was hoping that an old hand in php5 could tell me how to make my simple statement work.

Many thanks once again!!

---

### Post by koenn on 2008-06-15
post #9 in the 1st link is a very basic example that looks very much like what you're trying to do.

and even as a php beginner, you'd be able to read the other examples, understand most of what they do, and strip them down / take out the parts you need/ want. 

In your code, I see you're trying to distinguish between IE 6 and IE 7 by having  ' && majorver <= ... ' , but your code doesn't say how your majorver gets a value. 
I'd leave that out to see if you can distinguish between IE and 'the others', then if that works see how you can distinguish between IE 6 and IE7, eg by looking in the Agent string and extracting the part you need - same as looking for "msie".

But then again,  I don't know any php.
Maybe you're better of in the programming forum

---

### Post by magpy on 2008-06-15
Hi thanks for the follow up!

Post #9 of link 1 looks a close match but uses headers - I'll have to poke under the hood of those other longer code blocks and try to find out what makes them work.

Thanks for the tip about the programming forum.  I'm sure the fix is quite small, if I manage to solve it I will post the results.

Cheers all

---

### Post by magpy on 2008-06-18
Hi all!

I have a working solution (code below) which works provided that the browscap.ini directive is uncommented in php.ini and that the browscap.ini file exists at the specified path of the browscap directive.

Unfortunately the solution only works in .php files and not .html.  When using same code in .html files it returns all html markup, some php code and uses the default stylesheet (main-2.css).  Has anyone encountered this before or know why this happens.  It would be nice to use .html files rather than .php.  could it be because I am using the php code in the html <head></head> sections?

Cheers all





<?php

$browser = get_browser( );

if ($browser->browser == 'IE' && $browser->version == 7.0) {

    print '<link rel="stylesheet" type="text/css" href="main-0.css" />';

} elseif ($browser->browser == 'Firefox' && $browser->version > 7.0) {

    print '<link rel="stylesheet" type="text/css" href="main-1.css" />';

} else {

    print '<link rel="stylesheet" type="text/css" href="main-2.css" />';

}
?>

note: this has been tested:

php.ini \\located at C:\WINDOWS
browscap.ini \\located at C:\WINDOWS

---

### Post by mbeach on 2008-06-21
a solution programed inside of php tags will only work in php files by definition - its a php file.

Using that post #9 as a basis you don't have to use the headers.  Use the logic.


Original:
[PHP]<?php 
$br = strtolower($_SERVER['HTTP_USER_AGENT']); // what browser they use.
if(ereg("msie", $br)) {
    header("location: originalhomepage.php");
} else {
    header("location: alteredhomepage.php");
}
?>[/PHP]

amend for your needs to be something like:

[PHP]
<?php
$br = strtolower($_SERVER['HTTP_USER_AGENT']); // what browser they use.
if(ereg("msie", $br)) {
    $usecssFile = "main-0.css";
} else {
    $usecssFile = "main-1.css";
}
?>[/PHP]
Then in your css line use something like:
```
<link rel="stylesheet" type="text/css" href="<?php echo $usecssFile; ?>" />

```

---

### Post by magpy on 2008-07-10
Hi there!

Cheers this is a good solution!!

Many thanks

---

