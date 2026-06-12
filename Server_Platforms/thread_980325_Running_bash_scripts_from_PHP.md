---
title: "Running bash scripts from PHP"
date: 2008-11-12
forum: Server Platforms
---

### Post by craigp on 2008-11-12
I am using this code to call a bash script on the computer

```
$last_line = system('/home/www/public_html/something/scripttesting/ls', $retval);

// Printing additional info
echo '
</pre>
<hr />Last line of the output: ' . $last_line . '
<hr />Return value: ' . $retval;
```

and it works for simple things like ls

However when i start to do things like mkdir it doesnt work due to permission issues. I understand that this is because it is being ran from the user www-data but how can i get that command to run as sudo?

Cheers

---

### Post by spiderbatdad on 2008-11-12
there are way to get the command to touch a plain text password directory, which is not considered very secure. Why not just change the permissions of the directory you want the script to write to, to 777?

---

### Post by craigp on 2008-11-12
i ran chmod 777 on the directory that the script is sitting in and it actually still says the same thing... and the bash script and php file has full permissions..

---

