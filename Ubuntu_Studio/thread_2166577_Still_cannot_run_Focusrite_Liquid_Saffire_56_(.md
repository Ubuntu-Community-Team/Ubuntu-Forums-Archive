---
title: "Still cannot run Focusrite Liquid Saffire 56 :("
date: 2013-08-10
forum: Ubuntu Studio
---

### Post by Mr3CY4N on 2013-08-10
to be deleted

---

### Post by davetv on 2013-08-10
It would have been better to leave your question and post the solution.

---

### Post by Mr3CY4N on 2013-08-10
You're right, sorry, I deleted this text too fast...

So - I had problems with installing Saffire Liquid 56, this is how I got it to work:
First, I followed the solution from [http://www.ffado.org/?q=node/2062](http://www.ffado.org/?q=node/2062), that is downloaded ffado source - [http://www.ffado.org/?q=node/5](http://www.ffado.org/?q=node/5), extraced it, edited the "configuration" file, adding comments ( # symbol at the beggining of each line) for Saffire Pro10IO, and pasting the part from the ffado page.

- installed scons (ubuntu software center)
- run some commands from webpage: [http://subversion.ffado.org/wiki/Dependencies/Ubuntu](http://subversion.ffado.org/wiki/Dependencies/Ubuntu)
sudo apt-get build-dep libffado
sudo apt-get install build-essential libavc1394-dev python-qt4-dev subversion libtool
(now in the directory where the ffado source with configuration file is)
scons PREFIX=/usr
sudo scons install

(if it won't work you can also try:
scons DEBUG=yes
sudo scons install
)

I had jackd already installed, so after rebotting, I just ran 
ffado-dbus-server &
(just first time, after next rebotting I just opened QJackCtl and started the driver with freebob and unchecked "realtime" setting (when I had it checked, there were some interruptions in sound).

sorry for bad english :)

---

### Post by cub on 2013-08-10
Thanks!

---

