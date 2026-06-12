---
title: "Metasploit 3.0 Installation"
date: 2007-01-17
forum: Server Platforms
---

### Post by k2pow on 2007-01-17
So I downloaded the metasploit 3.0 file and extracted it to my home folder. I am having a lot of trouble installing it because there is no installation instructions. Any help would be much appreciated. (sorry for such a newb question)

---

### Post by Ufo on 2007-01-18
Do you have libzlib-ruby and libopenssl-ruby installed?
Then you should be able to start msfconsole, or which work environment you prefer.
No other installation needed.
Hope this helped :)

---

### Post by k2pow on 2007-01-19
Yeh I installed those, so all I have to do is double click on that console .exe?

Edit: I got the regular msfconsole to work by double clicking it and choosing run in terminal. I want to use the webconsole and I tried the same thing by double clicking and nothing happened.

---

### Post by Ufo on 2007-01-20
I never used msfweb interface, but it is supposed to start web server on port 55555 by default. Then you can connect to that server with browser.
I found this tutorial from web about msfweb:

[http://www.ethicalhacker.net/content/view/81/24/](http://www.ethicalhacker.net/content/view/81/24/)

It's for older version, so there could be some little differences.

---

### Post by k2pow on 2007-01-21
So Ive downloaded all those ruby things you need but I am having trouble with rubygems which is said to be what you need.

---

### Post by k2pow on 2007-01-22
I have been trying to install ruby gems and rails and this is the error output I recieve> /framework$ gem install -v=1.1.6 rails
Need to update 22 gems from [http://gems.rubyforge.org](http://gems.rubyforge.org)
......................
complete
Install required dependency activesupport? [Yn]  yn
ERROR:  While executing gem ... (Errno::EACCES)
    Permission denied - /usr/lib/ruby/gems/1.8/cache/activesupport-1.3.1.gem
shawn@CLaptop:~/framework$ sudo gem install -v=1.1.6 rails
Install required dependency activesupport? [Yn]  yn
Install required dependency activerecord? [Yn]  Yn
Install required dependency actionpack? [Yn]  Yn
Install required dependency actionmailer? [Yn]  Yn
Install required dependency actionwebservice? [Yn]  y
Successfully installed rails-1.1.6
Successfully installed activesupport-1.3.1
Successfully installed activerecord-1.14.4
Successfully installed actionpack-1.12.5
Successfully installed actionmailer-1.2.5
Successfully installed actionwebservice-1.1.6
/usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require': no such file to load -- rdoc/rdoc (LoadError)
        from /usr/local/lib/site_ruby/1.8/rubygems/custom_require.rb:27:in `require'
        from /usr/local/lib/site_ruby/1.8/rubygems/doc_manager.rb:71:in `load_rdoc'
        from /usr/local/lib/site_ruby/1.8/rubygems/doc_manager.rb:41:in `generate_ri'
        from /usr/local/lib/site_ruby/1.8/rubygems/gem_commands.rb:299:in `execute'
        from /usr/local/lib/site_ruby/1.8/rubygems/gem_commands.rb:298:in `execute'
        from /usr/local/lib/site_ruby/1.8/rubygems/gem_commands.rb:236:in `execute'
        from /usr/local/lib/site_ruby/1.8/rubygems/command.rb:70:in `invoke'
        from /usr/local/lib/site_ruby/1.8/rubygems/cmd_manager.rb:120:in `process_args'
        from /usr/local/lib/site_ruby/1.8/rubygems/cmd_manager.rb:91:in `run'
        from /usr/local/lib/site_ruby/1.8/rubygems/gem_runner.rb:30:in `run'
        from /usr/bin/gem:23


Any Ideas what is wrong?

---

### Post by k2pow on 2007-01-22
Alright so I did a fresh install of rubygems and rails, but now I am getting this problem and msfweb is not launching >  sudo ./msfweb
./script/../config/boot.rb:28:Warning: require_gem is obsolete.  Use gem instead.
=> Booting WEBrick...
./script/../config/../config/../../../lib/msf/core/db_manager.rb:34:Warning: require_gem is obsolete.  Use gem instead.
=> Rails application started on [http://127.0.0.1:55555](http://127.0.0.1:55555)
=> Ctrl-C to shutdown server; call with --help for options
[2007-01-22 10:16:24] INFO  WEBrick 1.3.1
[2007-01-22 10:16:24] INFO  ruby 1.8.4 (2005-12-24) [i486-linux]
[2007-01-22 10:16:24] INFO  WEBrick::HTTPServer#start: pid=5372 port=55555
[2007-01-22 10:17:10] INFO  going to shutdown ...
[2007-01-22 10:17:10] INFO  WEBrick::HTTPServer#start done.


Any help would be greatly appreciated

---

### Post by Monoxide on 2007-02-18
I am also having problems with the Metasploit Console & Web Interface. I have installed Open SSL, Ruby, Perl and alot of the other things that are needed to run this application. I have also visited that ethical hacker site and done as they had said for the 2.x firmware and I can get the 2.x working fine just not the 3.0 beta 3

This is the error code I get when trying to launch the web interface or the console
```
./msfweb
./lib/rex/socket/ssl_tcp_server.rb:4:in `require': no such file to load -- openssl (LoadError)
        from ./lib/rex/socket/ssl_tcp_server.rb:4
        from ./lib/rex/socket/comm/local.rb:5:in `require'
        from ./lib/rex/socket/comm/local.rb:5
        from ./lib/rex/socket.rb:22:in `require'
        from ./lib/rex/socket.rb:22
        from ./lib/rex.rb:71:in `require'
        from ./lib/rex.rb:71
        from ./msfweb:9:in `require'
        from ./msfweb:9

```

All the file are in the correct Directory 
```
lib/rex/socket$ ls
comm                   ssl_tcp.rb.ut.rb         tcp.rb
comm.rb                ssl_tcp_server.rb        tcp.rb.ut.rb
parameters.rb          ssl_tcp_server.rb.ut.rb  tcp_server.rb
parameters.rb.ut.rb    subnet_walker.rb         tcp_server.rb.ut.rb
range_walker.rb        subnet_walker.rb.ut.rb   udp.rb
range_walker.rb.ut.rb  switch_board.rb          udp.rb.ut.rb
ssl_tcp.rb             switch_board.rb.ut.rb

```
```
/lib/rex$ ls
arch                 logging             service_manager.rb.ut.rb
arch.rb              logging.rb          service.rb
assembly             nop                 services
codepage.map         parser              socket
compat.rb            payloads            socket.rb
constants.rb         payloads.rb         socket.rb.ut.rb
encoder              peparsey            struct2
encoders             peparsey.rb         struct2.rb
encoding             pescan              sync
evasion.rb           pescan.rb           sync.rb
evasion.rb.ut.rb     poly                test.rb
exceptions.rb        poly.rb             text.rb
exceptions.rb.ut.rb  post                text.rb.ut.rb
exploitation         post.rb             time.rb
file.rb              proto               transformer.rb
file.rb.ut.rb        proto.rb            transformer.rb.ut.rb
io                   proto.rb.ts.rb      ui
job_container.rb     script.rb           ui.rb
LICENSE              service_manager.rb

```

---

### Post by fakie_flip on 2007-03-04
You are missing a few things.

---

### Post by fakie_flip on 2007-03-19
Here are the commands you need to get metasploit running.

```
wget http://metasploit.org/projects/Framework/msf3/download.html?Release=framework-3.0-beta-3-svn.tar.gz

sudo apt-get install ruby ri rdoc mysql-server libmysql-ruby irb
sudo wget http://rubyforge.org/frs/download.php/11289/rubygems-0.9.0.tgz

tar -xvzf rubygems-0.9.0.tgz
cd rubygems-0.9.0
sudo ruby setup.rb

sudo apt-get install libopenssl-ruby1.8
sudo gem install -v=1.1.6 rails

```

---

