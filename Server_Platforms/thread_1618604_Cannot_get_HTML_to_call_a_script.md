---
title: "Cannot get HTML to call a script"
date: 2010-11-10
forum: Server Platforms
---

### Post by PapaNerd on 2010-11-10
This seems like a fairly straight-forward task, but I have been surfing for hours for what probably is something quite simple.  I want to have a web page call (and pass parameters) to a script. 

Here is my html test case for a perl call (file name: test-pl.html):
```

<html>
  <body bgcolor="#eeffee">
      <p><b>Test of pl form.</b></p>
    <form method="post" action="./test.pl">
      Field 1: <input type="text"	name="field_1"	value="Input A"><br>
      Field 2: <textarea		name="field_2"	>Input B</textarea><br><br>
      <input type="submit"	value="Submit">
      <input type="reset"	value="Reset">
    </form>
  </body>
</html>

```

Here is the perl script being called (file name: test.pl):
```

#!/usr/bin/perl
foreach (@ARGV)
  {
    print "$_\n";
  }

```

Here is my html test case for a shell script call (file name: test-sh.html):
```

<html>
  <body bgcolor="#eeeeff">
      <p><b>Test of sh form.</b></p>
    <form method="post" action="./test.sh">
      Field 1: <input type="text"	name="field_1"	value="Input A"><br>
      Field 2: <textarea		name="field_2"	>Input B</textarea><br><br>
      <input type="submit"	value="Submit">
      <input type="reset"	value="Reset">
    </form>
  </body>
</html>

```

Here is the shell script being called (file name: test.sh):
```

#!/bin/sh
  touch test.done
  echo "`date '+%D at %T'` - $0 $* "
exit

```

Both the perl script and the shell script execute properly from the command line, but not when called from the html.  My suspicion is that I am missing an apache2 configuration parameter of some type.  Can someone advise what that would be, the proper syntax, and where it goes?

---

### Post by Vegan on 2010-11-10
I put together a web page to submit sitemaps, and in that PHP document, I have extensive PHP and a HTML form all in the same document.

This way when post is done, the forum picks it up and processes, otherwise the forum presents a URL box for your site.

So I suggest merging your code into HTML and you choice of programming language and I suggest PHP as Perl is now fading away.

---

### Post by PapaNerd on 2010-11-10
Thanks Vegan.  I also experimented with a php version which can be called from the web page, but the syntax is new to me.  My preference would be to call a shell script, as I have a couple decades of experience in those plus there are a few other things I would like to implement with shell scripts besides form processing.

---

### Post by wongo888 on 2010-11-11
You would need to set up your Apache for CGI:

[http://httpd.apache.org/docs/2.0/howto/cgi.html](http://httpd.apache.org/docs/2.0/howto/cgi.html)

You might want to take a look at the the following as it specifically addresses shell scripts:

[http://www.yolinux.com/TUTORIALS/LinuxTutorialCgiShellScript.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialCgiShellScript.html)

Ensure that your scripts are executable (chmod 755) so that Apache can execute them.

Alternatively, PHP offers a function called 'system' which allows execution of shell commands. You could probably reformat your $_GET array variables into something resembling a shell command and just execute it. The limitation of this method is that only the last line of the shell is retained (and optionally the return code).

[http://php.net/manual/en/function.system.php](http://php.net/manual/en/function.system.php)

There is another function that sends output to the browser.

[http://www.php.net/manual/en/function.passthru.php](http://www.php.net/manual/en/function.passthru.php)

I've never tried either of these commands before.

Perl offers a few ways to do the same:

[http://perl.about.com/od/programmingperl/qt/perlexecsystem.htm](http://perl.about.com/od/programmingperl/qt/perlexecsystem.htm)

---

### Post by PapaNerd on 2010-11-11
Thank you wongo888.  The first link advised me to put this code in my httpd.conf file:```
<Directory /home/{...path...}/cgi>
  Options +ExecCGI
</Directory>
AddHandler cgi-script .cgi .pl .sh
```
After working through a "Premature end of script headers" problem, I am now successfully calling both the perl and shell scripts from the html.  Next, I need to work through why the arguments (form parameters) are not being passed to the scripts, but I am definitely past the big roadblock.

---

### Post by wojox on 2010-11-11
Try this [Trying to install cgi and perl on Ubuntu Server]("http://ubuntuforums.org/showpost.php?p=8071842&postcount=2")

---

### Post by dapperdanny77 on 2010-11-11
maybe the perl cgi module is what you're looking for

[http://perldoc.perl.org/CGI.html]("http://perldoc.perl.org/CGI.html")

---

