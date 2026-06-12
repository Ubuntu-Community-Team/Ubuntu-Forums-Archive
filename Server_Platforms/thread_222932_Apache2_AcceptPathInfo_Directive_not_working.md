---
title: "Apache2 AcceptPathInfo Directive not working"
date: 2006-07-25
forum: Server Platforms
---

### Post by Hank Montgomery on 2006-07-25
I just got Ubuntu up with Apache2 and PHP running in order to support development for an outside site.

PHP seems to work fine EXCEPT for passing variables via ? appended to the url.

I maintain some web pages that pass variables to a PHP page by appending ?variable=something to the end of the called url.
As in   [http://mysite/nextpage/?name=hank](http://mysite/nextpage/?name=hank)

If the code for nextpage says :  My name is  <?php echo $name ?>
It then resolves to           :  My name is hank

This works fine on the original web site running Apache2 and PHP4
But not on my my new server running Apache2 and PHP5.
I have found references in several places regarding putting "AcceptPathInfo On" in an .htaccess file in the html directory, or adding it to the appache2.conf file.

I can't get either of those to work (yes I remembered to restart the server.)

I know I can use $_SERVER['QUERY_STRING'] to get at the passed variable but I don't want to have to rewrite the existing pages.

Suggestions PLEASE.

Thanks,
Hank

---

### Post by gruepig on 2006-07-26
> **Hank Montgomery said:**
> 
I know I can use $_SERVER['QUERY_STRING'] to get at the passed variable but I don't want to have to rewrite the existing pages.


You really, really, really should rewrite your pages.

Old versions of PHP defaulted to register globals.  That is, anything that was passed in via ENV, GET, POST, SERVER, or COOKIE was immediately part of your global namespace.  This is horribly insecure, because it means any user accessing your webpage can set any variable in the global namespace of your application (variable poisoning).  This gets exploited quite frequently.  Fortunately, newer versions of PHP fixedthis insecure default.  If you override this default, it is likely only a matter of time before your server gets cracked.  Don't do this! 

You should rewrite your pages to use something like $_GET['name'] rather than $name.  It is well worth doing.

For more info, see [http://www.php.net/manual/en/security.globals.php](http://www.php.net/manual/en/security.globals.php).

---

### Post by Hank Montgomery on 2006-07-26
Thanks gruepig,

The "production" server is running PHP4 while I loaded PHP5 on the local server I just built at home.  My next step is to ask the ISP when they are going to PHP5 - I may be learning how to back out an install of PHP5 so I can install PHP4 !

Is PHP4 an "Old" version ?  (i.e. do you think that's why it works on the production server but no on my home server?)

Now that I have a local server to work with I will eventually get around to changing a number of things but for now I doubt there is any security exposure in this particular situation. 

The passed variable is used as a key to lookup information in a table, which is then displayed in a popup window to the user.  For example the first page might be a list of items for sale with each item being a URL.  Clicking the item would pass the key as a tag on the url and the PHP code in the second page would find the item and display it's information in a popup window.

If the variable doesn't match a key there is no popup and  indication to a hacker as to what might have been done.  If it does match a key the only action is to display the requested information.

Thanks,
Hank

---

