---
title: "Getting started with Ubuntu Server 8.04 command prompt"
date: 2008-06-15
forum: Server Platforms
---

### Post by Ed_Ziffel on 2008-06-15
Hello,

I am new to Ubuntu.  I've been looking but could not find anywhere that shows you specifically what to type at the command prompt to view directories, files, etc.  Also needed are instructions to see hardware installed, etc. and what to type to start the console. Another item is how to get out of the man command page.  How do you get back to the command prompt after you read the information?  This information should pertain to server 8.04.

Thanks

Ed

---

### Post by samosamo on 2008-06-15
Google for "linux command line reference" for a list of useful commands.  typing q (quit) usually exits out of any program that tookover your console and an ungraceful way to immediately kill it is ctrl+c.  lspci and lshw will list hardware.

---

### Post by windependence on 2008-06-16
[http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html](http://www.tldp.org/LDP/Bash-Beginners-Guide/html/index.html)

[http://linuxcommand.org/](http://linuxcommand.org/)

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

[http://www.linuxdevcenter.com/linux/cmd/](http://www.linuxdevcenter.com/linux/cmd/)

[http://www.freesoftwaremagazine.com/articles/command_line_intro](http://www.freesoftwaremagazine.com/articles/command_line_intro)

[http://fosswire.com/wp-content/uploads/2007/08/fwunixref.pdf](http://fosswire.com/wp-content/uploads/2007/08/fwunixref.pdf)

Enjoy.

-Tim

---

### Post by lordrapturez on 2009-06-10
i'm new to Ubuntu 8.04.... how to boot up and login to ubuntu in the command prompt i mean teminate th X11.

---

### Post by LepeKaname on 2009-06-10
If you just want to access a console without graphics, press:

"CTRL+ALT+F#" (where # is usually a number between 1 to 6)

Also you can turn off X doing:

sudo /etc/init.d/gdm stop

---

### Post by Iowan on 2009-06-10
If you use CTRL-ALT-F# to get to a console, you can use CTRL-ALT-F7 to return to the desktop. There's also a terminal under Applications>Accessories... although it behaves a bit differently with some of the function keys.

---

