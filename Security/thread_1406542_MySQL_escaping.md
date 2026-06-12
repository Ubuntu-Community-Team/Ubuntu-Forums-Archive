---
title: "MySQL escaping"
date: 2010-02-14
forum: Security
---

### Post by phillw on 2010-02-14
Hi,
quite some time back, when I was learning about MySQL injections it has sorta been drilled into me to use **mysql_real_escape_string** when dealing with input from users.  ( [http://ubuntuforums.org/showthread.php?t=1258982](http://ubuntuforums.org/showthread.php?t=1258982) )

I'm running a standard LAMP installation, with no alterations to the defaults.

On the site in question, I do have this all set up, however, as part of a tutorial series on FULLTEXT, I've included the output of both "un-escaped" and "escaped" input, to show the importance.

Imagine my surprise when I input > 'E' via ```
echo '<form id="input" action="search.php" method="get" />';
echo 'I am Looking For:  ';
echo '<input type="text" size="40" name="LookFor" />';
echo '<input type="submit" value="Go Find It !!" />';

```

and find that ```
$LookFor=$_GET['LookFor'];
```
returns > \'E\' BEFORE is run it through the mysql_real_escape_string command, which then thoroughly enjoys itself and returns > \\\'E\\\'  #-o

Has someone changed the rules and not told me ??  

As you can imagine, it's playing havoc with my trying to put the MySQL query string together !!! ](*,)

I'm sure I was told **not** to use strip-slashes on input, but it looks like either I should do, or drop the mysql_real_escape_string bit :confused:

Mr O'Riley is going to be much dis-pleased...

Regards,

Phill.

---

### Post by just-work-ffs on 2010-02-14
Sounds like magic quotes may be turned on in which case you will need to call stripslashes.

You can either change your php config or check for it at runtime.

Try this and see if you get the expected result.
[PHP]
if(get_magic_quotes_gpc()) {
    $value = stripslashes($_GET['LookFor']);
}
[/PHP]Obviously calling get_magic_quotes_gpc() all the time isn't much fun so you could do something like this early on in your script's execution.
[PHP]
function magicQuotesAreEvil($value) {
    return stripslashes($value);
}

if(get_magic_quotes_gpc()) {
    array_walk($_GET, 'magicQuotesAreEvil');
    array_walk($_POST, 'magicQuotesAreEvil');
    array_walk($_COOKIE, 'magicQuotesAreEvil');
}
[/PHP]It may be obvious but you still should be cleaning/checking your input after the above.

---

### Post by phillw on 2010-02-14
> **just-work-ffs said:**
> Sounds like magic quotes may be turned on in which case you will need to call stripslashes.

You can either change your php config or check for it at runtime.

Try this and see if you get the expected result.
[PHP]
if(get_magic_quotes_gpc()) {
    $value = stripslashes($_GET['LookFor']);
}
[/PHP]Obviously calling get_magic_quotes_gpc() all the time isn't much fun so you could do something like this early on in your script's execution.
[PHP]
function magicQuotesAreEvil($value) {
    return stripslashes($value);
}

if(get_magic_quotes_gpc()) {
    array_walk($_GET, 'magicQuotesAreEvil');
    array_walk($_POST, 'magicQuotesAreEvil');
    array_walk($_COOKIE, 'magicQuotesAreEvil');
}
[/PHP]It may be obvious but you still should be cleaning/checking your input after the above.

Thanks for the reply, I also had sorta considered that, so I've just run php_info()

> GRRRRR...

I've found out that magic_quotes_gpc are turned on by deafult -- I'm now heading over to trace the person responsible and kill them.

Phill.So, as this is a standard Ubuntu Installation - there will be one less developer around when I get my hands on him.

> **Warning**This  feature has been *DEPRECATED* as of PHP 5.3.0 and *REMOVED* as of PHP 6.0.0. Relying on this feature is highly discouraged.

So, we're only on 5.2 but ....

> However, it also tries to undo a dose of magic_quotes_gpc. Now  admittedly no-one should ever be using magic quotes, as they're broken  idiotic rubbish that even the PHP devs who came up with them have been  telling us not to use for years, but if you were to add code to your  script to detect the damage that magic quotes do and undo it, this would  be the wrong place to do it.
I'll go check the hosting server now - coz if've got them turned on I'll need to alter my php.ini file to disable them.

Thanks for the help - Hopefully I can just turn the stupid things off.

I *may* even add a line of code similar to ...
> (*: my preferred approach is to sniff for magic_quotes_gpc, and if  present immediately die with an error message telling you not to use  that, you big old fool. It may not be very user friendly, but I've spent  enough time fixing naïve vulnerable PHP apps that I no longer greatly  care about being friendly.)  ;)

And, as I've just spent ages back-cheking my code - I'm **NOT** amused !!!!

Regards,

Phill.

---

