---
title: "HOWTO: Configure mod_ruby and eRuby with apache2 on edgy"
date: 2007-02-08
forum: Server Platforms
---

### Post by kson on 2007-02-08
I had some problem finding any good information about this issue but got it to work so I decided to share my knowledge.

The goal for this project is to configure apache so that it opens .rbx files with mod_ruby and .rhtml with eRuby and preferably run eRuby through mod_ruby for better speed.

First install:
```
sudo apt-get install ruby libapache2-mod-ruby eruby
```

Then activate the apache module (dont remember if this is done automaticly)
```
sudo a2enmod ruby
```

Now the tricky part. Create a file in /etc/apache2/conf.d/ (preferably 'ruby.conf' or similar) with this content:
```

AddType text/html .rhtml

<IfModule mod_ruby.c>
  RubyRequire apache/ruby-run
  RubyRequire apache/eruby-run

  # Execute *.rbx files as Ruby scripts
  <Files *.rbx>
  SetHandler ruby-object
  RubyHandler Apache::RubyRun.instance
  </Files>

  # Handle *.rhtml files as eRuby files
  <Files *.rhtml>
  SetHandler ruby-object
  RubyHandler Apache::ERubyRun.instance
  </Files>
</IfModule>

```

Then restart apache
```
sudo /etc/init.d/apache2 restart 
```

Thats it! (I think :))

You can test your installation with two files like these:
***rubyTest.rbx***
```
puts "<html><body><h1>Hello World</h1></body></html>"
```
***eRubyTest.rhtml***
```
<html><body><h1><% puts "Hello World" %></h1></body></html>
```

If someone uses this and think it works or if I forgot something, please post it here. And if this is wrong forum for this kind of stuff, then please move the thread to a better position. I couldnt find any.

---

### Post by theorem_hunter on 2007-02-08
this looks great, I'm going to try it now :) 

thanks for the how to, much appreciated

---

### Post by kson on 2007-02-09
> **theorem_hunter said:**
> this looks great, I'm going to try it now :) 

thanks for the how to, much appreciated

Thanks alot! Makes it worth the effort :popcorn: 

Is everything working as it should?

---

### Post by cime on 2007-03-21
I get error "403 Forbidden" - You don't have permission to access /ruby/test.rbx on this server.
But the file is chmoded to 777 so it should work. I have done what you said in first post. What could be wrong?
OS: Edgy
Apache2

edit: the second version (with rhtml file is working, but first one don't)

---

### Post by Brazen on 2007-03-21
You would probably be better off using mod_fcgid

---

### Post by tweak on 2007-03-26
> **cime said:**
> I get error "403 Forbidden" - You don't have permission to access /ruby/test.rbx on this server.
But the file is chmoded to 777 so it should work. I have done what you said in first post. What could be wrong?


I have exactly the same issue, and the apache error log reports this:

```
[Tue Mar 27 13:23:03 2007] [error] access to /var/www/index.rbx failed for (null), reason: Options ExecCGI is off in this directory
```
The solution is to add the following to your ruby.conf:

```
AddType text/html .rhtml

<IfModule mod_ruby.c>
   RubyRequire apache/ruby-run
   RubyRequire apache/eruby-run

   <Files *.rbx>
      [COLOR=Red]**Options +ExecCGI**[/COLOR]
      SetHandler ruby-object
      RubyHandler Apache::RubyRun.instance
   </Files>

   <Files *.rhtml>
      SetHandler ruby-object
      RubyHandler Apache::ERubyRun.instance
   </Files>
</IfModule>
```The html doesn't appear to get parsed by the browser however, so YMMV :)

---

### Post by hasimir44 on 2007-05-11
Here's what I did to get eruby and apache2 to work (and parse): 

# install apache2 and eruby (if you haven't already - no harm trying)
sudo apt-get install apache2 eruby

# enable actions in apache2 (disabled by default in Ubuntu)
sudo a2enmod actions

# declare eruby as an action in apache2
sudo echo 'Action application/x-httpd-eruby /cgi-bin/eruby' >> /etc/apache2/conf.d/ruby.conf

# link eruby to cgi-bin
sudo ln -s `which eruby` /usr/lib/cgi-bin/eruby

# add a system wide mime type for .rhtml files
sudo echo 'application/x-httpd-eruby  rhtml' >> /etc/mime.types

# reload settings to apache2
sudo /etc/init.d/apache2 reload


i'm using ubuntu 6.10 and it's working for me. someone else should test it though...

---

### Post by GutsGravel on 2007-10-03
Thanks for the easy guide! :-D

Anyone knows how can you enable debugging?

---

### Post by deadrabbit on 2007-10-04
Thank you! I was having a terrible time trying get this to work - I love using Ruby, but I don't like it on Rails, and it's impossible to find information about using Ruby without tons of Ruby on Rails related answers.

---

### Post by GutsGravel on 2007-10-07
Here's a little more enhanced version of ruby.conf:

```
AddType text/html .rhtml

<IfModule mod_ruby.c>
  RubyRequire apache/ruby-run
  #RubyRequire apache/ruby-debug

  RubyRequire apache/eruby-run
  #RubyRequire apache/eruby-debug

  # Execute *.rbx files as Ruby scripts
  <Files *.rbx>
    Options ExecCGI
    SetHandler ruby-object
    RubyHandler Apache::RubyRun.instance
    #RubyHandler Apache::RubyDebug.instance
  </Files>

  # Handle *.rhtml files as eRuby files
  <Files *.rhtml>
    SetHandler ruby-object
    RubyHandler Apache::ERubyRun.instance
    #RubyHandler Apache::ERubyDebug.instance
  </Files>
</IfModule>
```

To enable debugging, comment the run lines and uncomment the debug lines:

```
AddType text/html .rhtml

<IfModule mod_ruby.c>
  #RubyRequire apache/ruby-run
  RubyRequire apache/ruby-debug

  #RubyRequire apache/eruby-run
  RubyRequire apache/eruby-debug

  # Execute *.rbx files as Ruby scripts
  <Files *.rbx>
    Options ExecCGI
    SetHandler ruby-object
    #RubyHandler Apache::RubyRun.instance
    RubyHandler Apache::RubyDebug.instance
  </Files>

  # Handle *.rhtml files as eRuby files
  <Files *.rhtml>
    SetHandler ruby-object
    #RubyHandler Apache::ERubyRun.instance
    RubyHandler Apache::ERubyDebug.instance
  </Files>
</IfModule>
```

Don't forget to make all the .rbx (or .rb) files executable.

Also you guys may want to take a look in the /usr/lib/ruby/1.8/apache folder for all the goodies (open the files for details).

Note:
Using something like this

```
  <Location /ruby>
    Options ExecCGI
    SetHandler ruby-object
    RubyHandler Apache::RubyRun.instance
  </Location>
```

might cause some problems.
To fix it see the installation guide on the official web page [http://wiki.modruby.net/en/?InstallGuide](http://wiki.modruby.net/en/?InstallGuide)

Links:
Official modruby/eruby page: [http://www.modruby.net/en/](http://www.modruby.net/en/)
There's also: [http://www.eruby.info/](http://www.eruby.info/)
Some eRuby tutorials: [http://www.hiveminds.co.uk/taxonomy/term/603/eRuby](http://www.hiveminds.co.uk/taxonomy/term/603/eRuby)

Shugo Maeda, thanks man!  &#12354;&#12426;&#12364;&#12392;&#12358; :-D

---

### Post by auxbuss on 2007-11-11
Note that for .rbx files, as well as:

```
AddType text/html .rhtml
```

you also need

```
AddType text/html .rbx
```

So, for me, this works (on Gutsy):

```

AddType text/html .rhtml
AddType text/html .rbx

<IfModule mod_ruby.c>
  RubyRequire apache/ruby-run
  #RubyRequire apache/ruby-debug

  RubyRequire apache/eruby-run
  #RubyRequire apache/eruby-debug

  # Execute *.rbx files as Ruby scripts
  <Files *.rbx>
    Options +ExecCGI
    SetHandler ruby-object
    RubyHandler Apache::RubyRun.instance
    #RubyHandler Apache::RubyDebug.instance
  </Files>

  # Handle *.rhtml files as eRuby files
  <Files *.rhtml>
    SetHandler ruby-object
    RubyHandler Apache::ERubyRun.instance
    #RubyHandler Apache::ERubyDebug.instance
  </Files>
</IfModule>

```

-- 
Cheers,
Marc

---

