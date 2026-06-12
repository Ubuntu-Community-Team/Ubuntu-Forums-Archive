---
title: "SquirrelMail: Change SQL Password Bug"
date: 2011-09-08
forum: Server Platforms
---

### Post by piine on 2011-09-08
Hi all, 

I had been having a problem, which I have somewhat solved. The problem is with the change sql passwd plugin. For some reason, it would not query the DB and due to the error string, it was not exactly indicating that the problem was a syntax error in the query string to the DB. Well, the problem (for anyone else having troubles with this plugin) is in the csp_validate_input() function in /usr/share/squirrelmail/plugins/change_sqlpass.php. 

In this piece of code (around line 740), 
[PHP]
      $sql = $lookup_password_query;
      $sql = str_replace(array('%1', '%2', '%3', '%4', '%5'), 
                         array($full_username, $user, $dom, $encrypted_pwd, $db->escapeSimple($cp_oldpass)),
                        $sql);
      
$db_password = $db->getAll($sql);


[/PHP]it is wrapping quotations around the sql encrypt function to the db which is causing the error. I changed the code to:

[PHP]
      $sql = $lookup_password_query;
      $sql = str_replace(array('%1', '%2', '%3', '%4', '%5'), 
                         array($full_username, $user, $dom, $encrypted_pwd, $db->escapeSimple($cp_oldpass)),
                        $sql);
   
   $sql = str_replace('"encrypt','encrypt',$sql);
$sql = str_replace('))"','))',$sql);

$db_password = $db->getAll($sql);


[/PHP]and now the plug in works without error. 

I just thought I would post my solution here for anyone else who has been banging their head against the wall trying to figure out how to get the plugin to work. Also, if anyone could tell me how exactly to report this bug to SquirrelMail, that would be wonderful... Thank you, and hope I help some one out with this...

---

