---
title: "Frostwire on JeOS in Vista w/ VirtualBox"
date: 2009-10-25
forum: Virtualisation
---

### Post by john_van_v on 2009-10-25
Hi all,

I installed Hardy in VirtualBox on my laptop to help me develop PHP and Zend apps (still have yet to get to that).  

The Hardy JeOS has:
[LIST]
[*]an http client to the real world through (somebody else's) WiFi
[*]a local connection to an Xming X server on the Vista OS laptop
[*]httpd service to clients on the Vista laptop
[/LIST]

(BTW, the vista os is neither my idea, nor an option at them moment, and its persistence on my laptop is symbolic of the way things have become.)

I documented how I did this here: 

[http://linux-society.blogspot.com/2009/08/no-virtue-in-virtualization-vmware-qemu.html](http://linux-society.blogspot.com/2009/08/no-virtue-in-virtualization-vmware-qemu.html)

I installed the Zend components, tried a Zend CMS, which failed, and then tried some gnutella clients including gtk-gnutella, which worked in Xwindows, but didn't actually connect.  I also tried Mutella, a text gnutella client, which worked but also failed to connect.

I then tried Frostwire, which requires sun-java6-jre and sun-java6-bin, and "word is" you have to run other commands, which I did, but Frostwire crashed none-the-less complaining that the JVM was not right.  I then tried Limewire, which predictably crashed in the same way, but showed a little picture first.  

MP3 sharing is an excellent way to let crackers onto your laptop.

Just before quitting last night, I installed the Midori WebKit engine browser, and that works very well in X.  I tried Firefox before that, but it was simply too slow to be practical.

This virtualization setup seems to be the most promising, and I believe I am the first to document a working install procedure, as whiny as it sounds.  I am wondering if the VirtualBox NAT system is stopping the gnutella process.

Xming presents another problem.  The launch dialog causes an "xhost +" effect to allow x-clients to connect, making the the Vista laptop vulnerable to a "clear window" keystroke capturing attack.  From the Xming author credits, Xming seems to be a variation on Cygwin's Xserver which definately does have granular xhost protection.  

The WiFi firewall most likely blocks X traffic, and my local community so rural that I don't think anybody in WiFi range knows what X is, let alone how to launch an attack.

Xming docs suggest SSH connections, but I haven't gotten to that yet.

---

