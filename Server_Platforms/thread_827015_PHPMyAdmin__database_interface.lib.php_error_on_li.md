---
title: "PHPMyAdmin : database_interface.lib.php error on line 383"
date: 2008-06-12
forum: Server Platforms
---

### Post by trymbill on 2008-06-12
Hi everyone!

I've got an error in PHPMyAdmin I just can't figure out.  And it's not always the same error.  And if I fix it, it just comes back after 5 minutes.

The first error was on line 383.  The file had changed from this:

[PHP]return $tables[strtolower($database)];[/PHP]

to this:

[PHP]return $tables[strtolower(,database)];[/PHP]

And I didn't do it, nor did anyone else.  PHPMyAdmin worked OK for 5 minutes, but then the same error came.  I looked at the file, and it had changed back to the error.  I fixed it again, but after 5 minutes PHPMyAdmin showed another error.

Now it changed this line from an array:

[PHP]'swedish' => 'CP1252', //'latin1',[/PHP]

to this line:

[PHP] ( 'swedish' => 'CP1252', //'latin1',[/PHP]

so I got a syntax error because that "(" isn't suppose to be there.  I fixed it and PHPMyAdmin worked OK and has been OK now for 10 minutes.

Does anyone have a clue on what is going on?! :-/

---

### Post by molotov00 on 2008-06-12
I don't know what's going on... but just make the files readable (not rw). There's no reason PHP  files like that should be getting modified.

---

