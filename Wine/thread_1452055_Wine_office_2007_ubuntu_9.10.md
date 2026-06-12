---
title: "Wine office 2007 ubuntu 9.10"
date: 2010-04-11
forum: Wine
---

### Post by kaenlsp on 2010-04-11
I have a bit of a problem here, with *Ubuntu* and *Microsoft Office.*
I want to install 2007 on Karmic. I'll describe the process I&#8217;ve followed and that way &#8211;and hopefully- someone will be able to solve it.
  I downloaded the latest *wine* version from the official website and installed it. Then I looked for *playonlinux *in the *Ubuntu Software Center*, downloaded and installed it. I looked for *Microsoft Office 2007 *and started the installation process. When it asked for me to insert the software in my drive, instead, I used an .iso.
  I am 100% sure the .iso file isn&#8217;t corrupt. I used *GmountISO *to mount this image and I did it in */(myuser)/public/mounted*. The installation went on without any issues and both the installer and *playonlinux* told me it had been successfully installed. 
  When I try to execute it now a message that says something similar to &#8216;this app wasn&#8217;t installed for your user, reinstall it&#8217; pops up.
  Any ideas?
  Could it have something to do with my *Users and Groups*?
  I am also sure that *playonlinux* works fine, I&#8217;ve used it to install *Spotify* as well.
   
  By the way, neither am I an expert on *Wine* nor on *Ubuntu*.
   
  PS: Please don&#8217;t tell me to use *OpenOffice*, *Abiword, Kword or Symphony*. I just need *M.Office*.
   
  Thanks!

---

### Post by stilling on 2010-04-11
my way
install playon linux
sudo wget [http://deb.playonlinux.com/playonlinux_karmic.list](http://deb.playonlinux.com/playonlinux_karmic.list) -O /etc/apt/sources.list.d/playonlinux.list
sudo apt-get update
sudo apt-get install playonlinux

go to game tab in you application menu open playonlinux see in his menu microsoft office 2007 provide the cd when he ask for it and follow the steps that is all

hope this helps you

---

### Post by kaenlsp on 2010-04-12
I've already used playonlinux and it was helpless...
It says everything's ok and no icon appears when I open it. It seems that its done nothing. No office icons that i can launch


JUST AT THE BEGINNING IT OPENS INTERNET EXPLORER AND TRIES TO OPEN " ///RegServer.html " OR STH SIMILAR, BUT FAILS TO DO SO. THE REST OF THE INSTALLATION PROCESS WORKS FLAWLESSLY.
could that be the reason?

---

