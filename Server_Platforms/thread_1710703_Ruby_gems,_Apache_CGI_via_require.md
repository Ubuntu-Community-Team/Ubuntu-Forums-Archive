---
title: "Ruby gems, Apache CGI via require"
date: 2011-03-20
forum: Server Platforms
---

### Post by beethamd on 2011-03-20
I hope someone can help! I've been trying to resolve this for ages.

The only way I can require a gem in a ruby CGI script is to add require
'rubygems'

I can get it to work off the command line by updating the value of
RUBYOPT, but I'm not sure what this is updating or how it works. After a
reboot, the value of RUBY OPT is not set.

It seems that on Ubuntu 10.10 ruby and gems are expecting the gems to be in different
directories.

In IRB, $: has lots of directories around /usr/local and /usr/lib, but
the gems are being installed in /var/lib/gems.

Do I need to add /var/lib/gems to my load_path? How do I do that? Would
it be possible to install the gems in the place that ruby expects?

Anyone else had these gem issues? I would appreciate any help.

---

### Post by beethamd on 2011-03-20
I tried installing gems to a directory in my $LOAD_PATH

irb> puts $:
/usr/local/lib/site_ruby/1.8
/usr/local/lib/site_ruby/1.8/x86_64-linux
/usr/local/lib/site_ruby
/usr/lib/ruby/vendor_ruby/1.8
/usr/lib/ruby/vendor_ruby/1.8/x86_64-linux
/usr/lib/ruby/vendor_ruby
/usr/lib/ruby/1.8
/usr/lib/ruby/1.8/x86_64-linux
.

From the shell - 
sudo gem install dbi --install-dir='/usr/lib/ruby/1.8'

That seems to install gems OK. But, from irb - 

irb>require 'dbi'
LoadError: no such file to load -- dbi

Same issue through cgi.

Can't figure out what the issue is now.

---

### Post by elico on 2011-03-20
a much simpler solution is to work with a script that will build the environment for the Ruby script every time it runs.

---

### Post by beethamd on 2011-03-21
You shouldn't have to add [COLOR=Blue]require 'rubygems'[/COLOR] to the top of scripts.

When ruby is called by CGI, Ruby should search the $LOAD_PATH - and pull the dbi rubygem into the script.

The gems are there, but ruby can't find them.

---

### Post by beethamd on 2011-03-23
I solved this by adding SetEnv RUBYOPT rubygems to the Apache config file. My default file is at /etc/Apache2/sites-available/default.

You just need to add - 

SetEnv RUBYOPT rubygems

between <VirtualHost></VirtualHost>, but outside the <Directory> directives.

Hope this helps.

---

