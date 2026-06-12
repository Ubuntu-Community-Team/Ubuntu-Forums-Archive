---
title: "Squirrelmail"
date: 2012-03-28
forum: Server Platforms
---

### Post by baothoaind on 2012-03-28
I have 2 problems with Squirrelmail:
1. installed plugin change_sqlpass but when i change password it said: Could not find Pear DB library.

2. I don't attack a file follow email. It said Could not move/copy file. File not attached 


Can you tell me how to config to fix them?
Thank a lot

---

### Post by SeijiSensei on 2012-03-28
For the first, try adding the **php-pear** package.

---

### Post by baothoaind on 2012-03-28
I have installed php-pear, pear DB and config like [http://www.howtoforge.com/how-to-configure-squirrelmail-to-allow-users-to-change-their-email-passwords-on-an-ispconfig-3-server](http://www.howtoforge.com/how-to-configure-squirrelmail-to-allow-users-to-change-their-email-passwords-on-an-ispconfig-3-server)
Please continue to help

---

### Post by paullorentzen on 2012-04-05
It sounds like a path problem.

At the cli, issue the command:

[INDENT]find /usr -name "DB.php"[/INDENT]

This will tell you where DB.php was installed

I'm running ISPconfig3 under Ubuntu 11.01 setup using HowTo's Perfect server guide.

To make change_sqlpass work, I had to add the line, marked with + below, to the /usr/share/squirrelmail/plugins/change_sqlpass/function.php file:

[PHP]
function csp_get_pear_db()
{

   global $csp_debug;

   load_config('change_sqlpass', array('config.php'));

   // mask include errors if not in debug mode
   //
+     ini_set('include_path',ini_get('include_path').':/usr/share/php:');

   if ($csp_debug)
      $if_statement = 'return !include_once(\'DB.php\');';
   else
      $if_statement = 'return !@include_once(\'DB.php\');';
   
   if (eval($if_statement))
   {
      global $color;
      bindtextdomain('change_sqlpass', SM_PATH . 'locale');
      textdomain('change_sqlpass');
      $text = _("Could not find Pear DB library");
      bindtextdomain('squirrelmail', SM_PATH . 'locale');
      textdomain('squirrelmail');
      plain_error_message($text, $color);
      exit;
   }

}
[/PHP]

In addition, I had to change "127.0.0.1" to "localhost" in the /usr/share/squirrelmail/plugins/change_sqlpass/config.php file.

[PHP]   // csp_dsn
   //
   // Theoretically, any SQL database supported by Pear should be supported
   // here.  The DSN (data source name) must contain the information needed
   // to connect to your database backend. A MySQL example is included below.
   // For more details about DSN syntax and list of supported database types,
   // please see:
   //   http://pear.php.net/manual/en/package.database.db.intro-dsn.php
   //
   $csp_dsn = 'mysql://dbLoginNameHere:dbPasswordHere@localhost/dbispconfig';


[/PHP]

After all this, your password should be changed by the change_sqlpass plugin.

If you get an error 

**This page request could not be verified and appears to have expired.**

but the password is still changed, follow the instructions here:

[http://blog.rtfm.co.hu/2011/03/squirrelmail-change_sqlpass-this-page-request-could-not-be-verified-and-appears-to-have-expired/]("http://blog.rtfm.co.hu/2011/03/squirrelmail-change_sqlpass-this-page-request-could-not-be-verified-and-appears-to-have-expired/")

Good Luck!

Paul

---

### Post by baothoaind on 2012-04-12
Thank for help.
the path DB.php in my server is: /usr/share/php/DB.php
I did like you said but result not different
Anyone have different way?

---

### Post by mezzoforce on 2012-07-09
not working for me, still getting error...

---

### Post by martizanosb on 2012-10-02
try this 

[http://www.howtoforge.com/how-to-configure-squirrelmail-to-allow-users-to-change-their-email-passwords-on-an-ispconfig-3-server](http://www.howtoforge.com/how-to-configure-squirrelmail-to-allow-users-to-change-their-email-passwords-on-an-ispconfig-3-server)

---

