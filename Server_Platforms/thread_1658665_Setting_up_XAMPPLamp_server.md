---
title: "Setting up XAMPP/Lamp server"
date: 2011-01-02
forum: Server Platforms
---

### Post by wcdrotar on 2011-01-02
I am having royal issues with setting up a lamp server so I can use Joomla!  I've tried used a .vmx virtualization, and tried so many different methods of installing it.  I found some great tutorials here: [http://www.devshed.com/c/a/Administration/How-to-Install-XAMPP-on-Ubuntu-Linux/2/](http://www.devshed.com/c/a/Administration/How-to-Install-XAMPP-on-Ubuntu-Linux/2/)

I'm very happy with those tutorials, since they're very careful and thorough.  

Only issue I'm having is that when I enter: /opt/lampp/lampp restart

Everything stops properly, but when it's supposed to restart, it says another of each of them is already running.  Here is the output:

Stopping XAMPP for Linux 1.7.3a...
XAMPP: XAMPP-Apache is not running.
XAMPP: XAMPP-MySQL is not running.
XAMPP: XAMPP-ProFTPD is not running.
XAMPP stopped.
Starting XAMPP for Linux 1.7.3a...
XAMPP: Another web server daemon is already running.
XAMPP: Another MySQL daemon is already running.
XAMPP: Another FTP daemon is already running.
XAMPP for Linux started.

It's supposed to read that each of them starts up again.  There is so much going on in the synaptic I don't even know where to start in trying to remove the already running daemons, or if I'm supposed to.  

Anyone able to point me in the right direction to fixing this?

---

### Post by spynappels on 2011-01-03
What are you using to run your vmx file? You can just create a new virtual machine and select LAMP when you install a new Ubuntu server. Will make life a lot easier as you'll be working with native packages.

---

### Post by 0000_soldier on 2011-01-03
I had a similar problem with two daemons running... try this:

[http://ubuntuforums.org/showthread.php?t=1589270](http://ubuntuforums.org/showthread.php?t=1589270)

---

