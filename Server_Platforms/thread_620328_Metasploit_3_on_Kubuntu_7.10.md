---
title: "Metasploit 3 on Kubuntu 7.10"
date: 2007-11-22
forum: Server Platforms
---

### Post by Tie_Domi on 2007-11-22
This is a quick howto. I run Kubuntu on a T61 everyday so I may have other packages installed, you may or **may not** be able to run this verbatim. If you can't install the dependences.

download Metasploit 3
tar -zxf framework-3.0.tar.gz
cd framework-3.0.tar.gz
sudo apt-get install subverion
sudo svn update
framework-3.0$ sudo ./msfweb #(You get this error)
./lib/rex/socket/ssl_tcp_server.rb:4:in `require': no such file to load -- openssl (LoadError)
        from ./lib/rex/socket/ssl_tcp_server.rb:4
        from ./lib/rex/socket/comm/local.rb:5:in `require'
        from ./lib/rex/socket/comm/local.rb:5
        from ./lib/rex/socket.rb:22:in `require'
        from ./lib/rex/socket.rb:22
        from ./lib/rex.rb:71:in `require'
        from ./lib/rex.rb:71
        from ./lib/msf/core.rb:16:in `require'
        from ./lib/msf/core.rb:16
        from ./lib/msf/base.rb:19:in `require'
        from ./lib/msf/base.rb:19
        from ./msfweb:11:in `require'
        from ./msfweb:11
framework-3.0$ sudo apt-get install libzlib-ruby libopenssl-ruby ruby libruby rdoc ruby libruby rdoc libyaml-ruby libzlib-ruby libdl-ruby libreadline-ruby rubygems
framework-3.0$ sudo gem install rails 
Successfully installed rails-1.2.5 <===(At the end of this you should see this, if not run the command again)
framework-3.0$ sudo ./msfweb #(Run msfweb again and you get this)

[*] Starting msfweb v3.0 on [http://127.0.0.1:55555/](http://127.0.0.1:55555/)

Cannot find gem for Rails ~>1.2.2.0:
    Install the missing gem with 'gem install -v=1.2.2 rails', or
    change environment.rb to define RAILS_GEM_VERSION with your desired version.

framework-3.0$ sudo nano data/msfweb/config/environment.rb (EDIT THIS FILE)

#
# Force the application into production mode
#
ENV['RAILS_ENV'] = 'production'


# Specifies gem version of Rails to use when vendor/rails is not present
RAILS_GEM_VERSION = '**1.2.2**' unless defined? RAILS_GEM_VERSION

Change 1.2.2 to the VERSION YOU INSTALLED I INSTALLED rails-1.2.5 hence I put in 1.2.5, This is a poorly written script.

#
# Force the application into production mode
#
ENV['RAILS_ENV'] = 'production'

# Specifies gem version of Rails to use when vendor/rails is not present
RAILS_GEM_VERSION = '**1.2.5**' unless defined? RAILS_GEM_VERSION

....

Save the file and exit

sudo ./msfweb #(Run again and should work, if not use Google to fix your problem)

[*] Starting msfweb v3.0 on [http://127.0.0.1:55555/](http://127.0.0.1:55555/)

---

