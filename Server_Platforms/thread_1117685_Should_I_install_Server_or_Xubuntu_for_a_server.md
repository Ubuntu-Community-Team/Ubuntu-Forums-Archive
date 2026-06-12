---
title: "Should I install Server or Xubuntu for a server?"
date: 2009-04-06
forum: Server Platforms
---

### Post by cmwslw on 2009-04-06
I know the title sounds a little obvious, but it's a little more complicated than that. I am going to set up a server using Ubuntu on a low end PC (256 MB RAM). I have no experience setting up a server on Linux, so I would like to be able to use a GUI my first time. Should I install the Server distribution and then install XFCE, and then switch into it during maintenence? Another option is to install Xubuntu and just set it to not start XFCE by default. This method would start me off with the right programs I needed, so that would be a benifit. I have heard that installing a GUI can pose a security risk - is this only a risk when the GUI is running?

Thanks in advance,
Cory Walker

---

### Post by kestrel1 on 2009-04-06
Depends on why you want to run a server. I would have thought that 256mb ram would be a bit on the low side for a server. Xubuntu should run fine, but it is recommended that you do not have a GUI. For first time use I supose you could, but you would get too used to using the GUI & not run the server in a terminal.
GUI's are more comfortable to use though.

---

### Post by Simian Man on 2009-04-06
Install the server and then install xfce on top of that (not xubuntu-desktop).  Firstly because Xubuntu is a heavily modified version of Xfce that is heavier than the real thing.  Secondly because it installs a lot of software you don't need like a music player, office software and so on.

---

### Post by volkswagner on 2009-04-06
What will your server be serving?  Most all configuration is done by editing a text file.  I don't think the gui will gain much. 

So to answer first your question:  I think you should install the Sever Edition and add XFCE later.  This will give you the optimized server Kernel, and your resources will only take a hit while running XFCE.

I would test yourself.  See how long you can run before installing the XFCE.  There is a lot of help available.

---

### Post by jamesrfla on 2009-04-06
I might be doing the same exact thing except I will disable the GUI when I am done configuring everything and only turn the GUI on when I need to change something. You can setup basically everything through the CLI it just depends on what you will be hosting on that server. The only reason I use the GUI for is moving files around and system-config-samba GUI utility I use so I can set up permissions on folders easily.

---

### Post by bigbearomaha on 2009-04-06
On a 256 mb ram system, I would say to not use a GUI at all.  Install buntu server and add a remote admin tool like Webmin.  That will give you a GUI feel but not actually using Xserver or gui apps on the server itself.

If the server is on a LAN only, not web facing, I would say it's safer to run a GUI server.  If it's web facing, I wouldn't risk it.

Big Bear

---

### Post by cmwslw on 2009-04-06
But what if the GUI is not running? Would it not be safe to have XFCE on the server but still not running? Also, can I easily switch between XFCE and the terminal without stopping the server processes? I think I made a mistake by saying the computer had only 256MB RAM. I can't check right now, but I think it might have 512MB.

Also, would it be easier to go ahead and install the 9.04 Beta or should I install 8.04 and then upgrade?

---

### Post by kestrel1 on 2009-04-06
512mb makes some difference. I would go with 8.04 server, but not upgrade. You could always use 8.10 & upgrade at a later date.
8.04 is in LTS state & is supported until 2011 I believe. I think the next LTS version will be 9.10.
I wouldn't upgrade from an LTS to a standard Ubuntu personally.

---

### Post by ugm6hr on 2009-04-06
Consider very carefully what you expect your server to do.

I made this mistake, and having an Ubuntu background on my PCs, I figured Ubuntu (with ebox) would be a good choice.

However, some wider searching revealed FreeNAS, which is designed for home use.

Ubuntu is popular for home use, but is not the easiest to use unless you already know what you are doing.

---

### Post by Linuxwho? on 2009-04-06
"For first time use I supose you could, but you would get too used to using the GUI & not run the server in a terminal.
GUI's are more comfortable to use though."

I agree with this comment.  I was using the GUI and it actually put me behind.  Its very easy to fall into that trap lol.

---

### Post by bigbearomaha on 2009-04-06
Again, even with 512 mb, if it is a server, there is no need for a gui.  Mind you ,  I said "need".

If you want a GUI, by all means, put one on there.

it's your server, run it how you like.

again, the biggest risk is web facing vs local.


if it's just a local network and the server won't access the internet, I wouldn't worry about it.  if you want a GUI, knock yourself out.

security wise, having a GUI on a web facing server probably wouldn't be recommended by a lot of people.

Big Bear

---

