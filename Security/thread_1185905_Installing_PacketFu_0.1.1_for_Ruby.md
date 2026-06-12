---
title: "Installing PacketFu 0.1.1 for Ruby"
date: 2009-06-12
forum: Security
---

### Post by kballero on 2009-06-12
PacketFu v0.2.0
A mid-level packet manipulation library for Ruby (author Tod Beardsley)
[http://code.google.com/p/packetfu/](http://code.google.com/p/packetfu/)

# aptitude install ruby1.8 ruby1.8-dev irb rdoc rubygems libpcap-ruby1.8

# sudo gem install bindata 

**Download**
[http://packetfu.googlecode.com/files/packetfu-0.2.0.tar.gz](http://packetfu.googlecode.com/files/packetfu-0.2.0.tar.gz)

**Install**
See the included INSTALL file. In short:
# tar zxvf packetfu.0.x.y.tar.gz
# cd pcaprub_linux
# ruby extconf.rb && make && sudo make install
# cd ..
# sudo ruby setup.rb
Note, if you already have a version of BinData installed, this will overwrite it. There are ways around this, see ruby setup.rb --help for details.
PacketFu is reported to work on OS X, assuming you can get pcaprub installed correctly.

# cd packetfu.0.x.y/examples
# sudo irb -r packetfu-shell.rb

Other fine irb scripts and ruby files included!

---

