---
title: "Setting up Apache2 to run CGI scripts on Ubuntu"
date: 2006-02-04
forum: Server Platforms
---

### Post by wildscribe on 2006-02-04
I cannot seem to get Apache2 on Ubuntu 5.10 to recognize CGI Perl scripts. I keep getting "File Not Found" errors. I suspect it is a permission error, but I have tried a bunch of things and nothing seems to work.

Here is what I did and hopefully someone can help me out.

I created a cgi-bin in the /var/www/ folder so the full extenstion is now /var/www/cgi-bin

I then chmod 755 cgi-bin so it is readable.

Then, I created a test script, ptest.pl using this code 

#!/usr/bin/perl
print "Content-type:text/html|n\n";
print "<html>\n\n";
print "<h1>Hi!</h1>\n;
print "</html>\n\n>"

And then I used the command "sudo chmod 755 ptest.pl" to make the
script readable.

Then I edited the apache2.conf file and removed the "#" from the "AddHandler cgi-bin .gci" So this file can be seen by Apache2. I also added the .pl extension so it now reads "AddHandler cgi-script .cgi .pl"

Next, I restarted Apache2 and I cannot get any script to work in a browser. 

I know this sounds so basic and I have been working with Linux for more than a year as a workstation, but I am really puzzled with this one.

Thank you!

- - - WiLd

---

### Post by herrpoon on 2006-02-04
Hi, I didn't think you could just create a cgi-bin and start putting .pl (for example) files in there and for it to work.  The cgi-bin which you are supposed to use is /usr/lib/cgi-bin unless you edit the apache2 config file to allow cgi scripts to be executed outside this directory - I can't quite remember how to do that right now, but I'm sure it is around here somewhere!

---

### Post by Horndog on 2006-02-04
I know this is a basic question but did you install Perl?

---

### Post by wildscribe on 2006-02-04
Yes. Perl is installed and it works fine from the command line.

- - - WiLd

---

### Post by wildscribe on 2006-02-04
And I just moved my test script into the /usr/lib/cgi-bin and it works! Now if I can just figured out how to change the apache2.conf file. As I mentioned in my first post, I did remove the '#' before * AddHandler cgi-script .cgi* but that does not work. It has got to be something else.

Thanks for pointing out the cgi-bin.

- - Wild

---

### Post by Horndog on 2006-02-05
[QUOTE=wildscribe]Yes. Perl is installed and it works fine from the command line.

- - - WiLd[/QUOTE]

I mean do you have mod_perl installed?

---

### Post by wildscribe on 2006-02-05
No. Mod_Perl has not been installed. Would that make a difference?

---

### Post by LordHunter317 on 2006-02-05
First off, the file couldn't be found because Apache wasn't ever looking there.

The virtual path [http://example.com/cgi-bin/](http://example.com/cgi-bin/) is ScriptAliased to /usr/lib/cgi-bin by default on Debian and derivatives.  Apache followed that alias and didn't find the script there.

Second, you would have needed to edit sites-enabled/000-default, and added a Directory section for /var/www/cgi-bin.  You then would have had to add 'Options ExecCGI' to that section, plus any other options you wanted.

For CGI, just enabling the handler isn't enough, you need to either make the directory a ScriptAlias (/usr/lib/cgi-bin) is, or enable script execution via options.

Finally, don't place cgi-bin in the webroot where you can help it, alias it in.  Also, make sure the Apache user (www-data) can never write to it, just read and execute.

---

### Post by wildscribe on 2006-02-05
Thank you Lord! Now I understand what is going on. Since my Kubutu box is a single user machine that I use for learning how to program, I am going to leave the cgi-bin where it is /usr/lib/cgi-bin and I will do as you suggested, just point to the scripts by [http://mysite/cgi-bin/HelloMom.cgi](http://mysite/cgi-bin/HelloMom.cgi) 

Thanks again for your help!

- - - - WiLd

---

### Post by TomH on 2006-02-06
Hi this thread has been very informative, however how do i copy the file across as if i drag and drop it it says permision denied :???: 

Ta Tom

---

### Post by jrobinson5 on 2006-05-20
[QUOTE=TomH]Hi this thread has been very informative, however how do i copy the file across as if i drag and drop it it says permision denied :???: 

Ta Tom[/QUOTE]

Open the terminal.

```
sudo nautilus
```

---

### Post by bribera on 2006-05-24
Hi-

I don't know if you've worked this problem out yet or not, but here's my two cents:

If this code is vebatim, that could very well be your problem.  There are two typos that would prevent it from working.  Line 2 is incorrectly escaping the first newline, and line four is missing a terminating quotation mark.  Line 4 will prevent perl from executing the script, while line 2 will prevent apache from printing out the page (a malformed header).
[QUOTE=wildscribe]#!/usr/bin/perl
**print "Content-type:text/html|n\n";**
print "<html>\n\n";
**print "<h1>Hi!</h1>\n;**
print "</html>\n\n>"[/QUOTE]

Those lines should read:
[INDENT]
*print "Content-type:text/html**\**n\n";*
and
*print "<h1>Hi!</h1>\n**"**;*
[/INDENT]

---

### Post by jimcooncat on 2006-05-24
Took me a couple minutes to figure out the difference in line 2. The original poster used a pipe character (|) instead of a backslash (\). Almost identical with the font I'm reading the forum with.

---

