---
title: "Install Perl"
date: 2011-06-18
forum: Server Platforms
---

### Post by poker158149 on 2011-06-18
I have a few Perl scripts I'd like to run on my LAMP server, but I can't seem to get it to work. 
I installed Perl using ```
sudo apt-get install libapache2-mod-perl2
``` like someone instructed me, and it installed, but doesn't run. I tried a simpler approach and just did ```
sudo apt-get install perl
``` but it says Perl is already in its newest version, so I know it's installed. 

When I go to my site and try to execute a Perl script, it pops up with the "download file" window like it does with files that cannot be run in the browser/on the server. I saw someone run a Perl file in the console after he installed Perl on his server, so I tried it and it did nothing. When I did it without the "sudo" it said, "bad interpreter," but when I did it with sudo it just went to the next line and I could see nothing got executed.

---

### Post by ian dobson on 2011-06-18
Hi,

You need to tell apache that cgi-bin / .pl files are scripts that should be executed.

Something like:-

```
    <VirtualHost *>
    ServerName xxxx
    ServerAdmin xxx
    DocumentRoot "/data/apache/clan-faog/htdocs"
    DirectoryIndex index.html index.htm index.php
    ErrorLog "/data/apache/clan-faog/logs/error.log"
    CustomLog "/data/apache/clan-faog/logs/access.log" combined
    CustomLog "/data/apache/clan-faog/logs/deflate.log" deflate
    ScriptAlias "/cgi-bin" "/data/apache/clan-faog/cgi-bin/"
    </VirtualHost>
```

Regards
Ian Dobson

---

### Post by poker158149 on 2011-06-18
Where do I put that? In apache2.conf?

And I assume ```
/data/apache/clan-faog/htdocs
```

Is what I replace with my website root?

---

### Post by ian dobson on 2011-06-18
Hi,

You need to add the entries to your apache2.conf.

I my example I have a virtual host with a non-standard root path/configuration.

This is in the standard /etc/apache2/apache2.conf

```
    #
    # AddHandler allows you to map certain file extensions to "handlers":
    # actions unrelated to filetype. These can be either built into the server
    # or added with the Action directive (see below)
    #
    # To use CGI scripts outside of ScriptAliased directories:
    # (You will also need to add "ExecCGI" to the "Options" directive.)
    #
    #AddHandler cgi-script .cgi
    AddHandler cgi-script .pl

```

Don't forget to add the ScriptAliased line, as in my first post, with the correct directory.

Regards
Ian Dobson

---

### Post by poker158149 on 2011-06-18
Ah, thank you.

After setting that up, when I go to the script now, it comes up with the "403 Forbidden" page. I chmoded it to 777 just to test it and I also chmod +x it, but I still get the forbidden to run this script. But at least we're getting somewhere!

---

### Post by ian dobson on 2011-06-19
Hi,

OK it it's still not working, then I think you need to add your cgi-bin directory:-


```
<Directory "/path/to/cgi-bin/">
    AllowOverride None
    Options None ExecCGI
    Order allow,deny
    Allow from all
</Directory>
```

Then that should do it. Also setting up a file with permissions 777 is not a good idea. Anyone can edit the file and execute it. Change the permission so that apache can read/execute the file and your normal user can edit/write/read the file.

Regards
Ian Dobson

---

### Post by poker158149 on 2011-06-19
I added that and it's still bringing me to the "Forbidden: You don't have permission to access /test.pl on this server."

---

### Post by ian dobson on 2011-06-19
Hi,

Did you restart apache?

Sorry but I'm starting to runout of ideas.

Just go through your configuration checking if everything is ok. Check if the apache user has access to the cgi-bin directory and that it can execute the script.

I can remember that when I setup my server it took me several hours to get cgi working.

Regards
Ian Dobson

---

### Post by poker158149 on 2011-06-19
I did restart apache. Thank you for your help, it's okay that you are out of ideas, I'm sure I just have something simple wrong somewhere. I'm sure I'll come across it soon. I'll keep playing around and come back if I still have problems. Thanks again!

---

