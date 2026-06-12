---
title: "capistrano fails to set up"
date: 2010-09-18
forum: Server Platforms
---

### Post by jarrah-95 on 2010-09-18
i have recently been trying to set up a server, and have had the problem of trying to set up capistrano deploys with the command cap deploy:setup.
when i run the command it outputs the following error;
```
cap deploy:setup
/usr/lib/ruby/1.8/net/ssh/transport/openssl.rb:1:in `require': no such file to load -- openssl (LoadError)
	from /usr/lib/ruby/1.8/net/ssh/transport/openssl.rb:1
	from /usr/lib/ruby/1.8/net/ssh/buffer.rb:2:in `require'
	from /usr/lib/ruby/1.8/net/ssh/buffer.rb:2
	from /usr/lib/ruby/1.8/net/ssh/transport/algorithms.rb:1:in `require'
	from /usr/lib/ruby/1.8/net/ssh/transport/algorithms.rb:1
	from /usr/lib/ruby/1.8/net/ssh/transport/session.rb:7:in `require'
	from /usr/lib/ruby/1.8/net/ssh/transport/session.rb:7
	from /usr/lib/ruby/1.8/net/ssh.rb:10:in `require'
	from /usr/lib/ruby/1.8/net/ssh.rb:10
	from /usr/lib/ruby/1.8/net/ssh/gateway.rb:2:in `require'
	from /usr/lib/ruby/1.8/net/ssh/gateway.rb:2
	from /usr/lib/ruby/1.8/capistrano/configuration/connections.rb:2:in `require'
	from /usr/lib/ruby/1.8/capistrano/configuration/connections.rb:2
	from /usr/lib/ruby/1.8/capistrano/configuration.rb:4:in `require'
	from /usr/lib/ruby/1.8/capistrano/configuration.rb:4
	from /usr/lib/ruby/1.8/capistrano.rb:1:in `require'
	from /usr/lib/ruby/1.8/capistrano.rb:1
	from /usr/lib/ruby/1.8/capistrano/cli.rb:1:in `require'
	from /usr/lib/ruby/1.8/capistrano/cli.rb:1
	from /usr/bin/cap:3:in `require'
	from /usr/bin/cap:3

```

i have tryed installing both ruby and open ssl and niether helped. can you please tell me what i am doing wrong?
thanks

---

### Post by windependence on 2010-09-19
This may help:
[http://ubuntuforums.org/showthread.php?t=1075672](http://ubuntuforums.org/showthread.php?t=1075672)
 
-Tim

---

### Post by stensonb on 2010-12-29
I, too, had this problem.  The capistrano package fails to list libopenssl-ruby1.8 as a dependency...so, just add it manually:

```
sudo apt-get install libopenssl-ruby1.8
```

---

### Post by jarrah-95 on 2010-12-30
yer i did the same thing a few months back, sorry i guess i forgot to post it here

---

