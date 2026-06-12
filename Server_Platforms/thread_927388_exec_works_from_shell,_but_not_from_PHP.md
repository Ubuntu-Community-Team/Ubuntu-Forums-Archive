---
title: "exec works from shell, but not from PHP?"
date: 2008-09-22
forum: Server Platforms
---

### Post by pr0fess0r on 2008-09-22
Hi :)
I have a command a I need to trigger from a PHP script - it uploads a file to a content distribution network using a command line utility called vxup.
I'm running Apache/2.2.4 (Ubuntu) PHP/5.2.3-1ubuntu6.4 mod_perl/2.0.2 Perl/v5.8.8 on Ubuntu 7.10
I've given www-data permission to run this file as root in sudoers:
www-data ALL=(ALL) NOPASSWD: /usr/local/bin/vxup

The command I'm trying to run is

sudo /usr/local/bin/vxup add -c "/home/administrator/.xxx/yyy.pem" -K "8" "8.flv" "zzz" "/var/.kkk/8/8.flv"

So from PHP I'm calling it like this:

$output=shell_exec('sudo '.$vxup_path.' add -c "'.$vxup_certfile.'" -K "'.$id.'" "'.$name.'" "zzz" "'.$filename.'"');

If I run it I get an error in the Apache log:
An error occurred:  basic_string::_S_construct NULL not valid

However if I run it from the shell like this:

sudo -u www-data /usr/local/bin/vxup add -c "/home/administrator/.xxx/yyy.pem" -K "8" "8.flv" "zzz" "/var/.kkk/8/8.flv"

It runs fine! Does anyone know what "basic_string::_S_construct NULL not valid" means and what might be going wrong? 

Many thanks in advance

Lucas

---

### Post by ghostdog74 on 2008-09-22
construct you shell command and print it out, make sure its correct, before passing it to shell_exec(). ie 
```

$cmd="sudo ....";
echo $cmd; # << make sure its correct 
shell_exec($cmd);

```

---

### Post by pr0fess0r on 2008-09-22
Yup I did that, and I copied and pasted that output into the shell and it ran fine...

---

### Post by Yon_demon on 2009-06-30
It's 2009, and I have the same problem with vxup execution from PHP... How did you solve it pr0fess0r?

I have give +x to all the people on vxup
I've done a a shell script and works fine, but when I exec the script I get the same error

If I echo the script to a file ( set -x ) I can read and copy-paste the command, and it works from command line...

Maybe it's a environement variable of the user?

Any idea? thanks in advance

---

### Post by pr0fess0r on 2009-06-30
Hi
What I did, in the end, was use PHP to create a .php file with my vxup commands in it for each file that got uploaded. For example, my code would write out a file with commands like:


```
$remaddr = getenv("HOME"); 
putenv("HOME=$remaddr"); 
$output=shell_exec(\''.$vxup_path.' add -c "'.$vxup_certfile.'" -K "'.$id.'" "'.$name.'" "Blah" "'.$filename.'"\');
```


I think you need to get the HOME environment variable from within the file. 
Then, once the file was written, I'd call it with

```
file_put_contents($uploadfile,$command);
$remaddr = getenv("HOME"); 
putenv("HOME=$remaddr");
exec('/usr/bin/php '.$uploadfile.' >> /dev/null &');
```

and that seemed to work...

Hope that helps!

---

### Post by Yon_demon on 2009-07-01
It works!

I don't know why... but it works... THANKS ;)

---

