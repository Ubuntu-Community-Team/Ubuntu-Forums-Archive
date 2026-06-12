---
title: "How can I connect to Live Communications Server?"
date: 2005-11-08
forum: The Cafe
---

### Post by dguy on 2005-11-08
Hi everyone, I just recently switch from Windows to Kubuntu, and it's been great so far. My first big issue is that my office is still is mainly a Windows-based LAN, including Exchange for email/groupware and Live Communications Server for internal IM. For mail I can use Web Outlook or Evolution so that's no problem, but I have not found anything that let's me communicate with my co-workers through Live Communications server. I've tried both Gaim and Kopete, but neither of them seem to support SIP messaging. If it were up to me, I would just set up a Jabber server, but for the time being, that isn't possible.

My co-workers and manager are pressuring me to find a solution quick or drop Linux and go back to Windows... I would hate to have to return to Windows because Linux has no SIP client that would let me connect to Live Communications Server, but sadly, I may have to.

Thanks in advance

---

### Post by xequence on 2005-11-08
[http://www.voip-info.org/wiki-Linux](http://www.voip-info.org/wiki-Linux)
[http://www.sipcenter.com/sip.nsf/html/User+Agents,+Source+Code](http://www.sipcenter.com/sip.nsf/html/User+Agents,+Source+Code)

I really dont understand it, but I *think/hope* those pages can help.

---

### Post by dguy on 2005-11-09
Thanks for the links but unfortunately, I am not looking into doing voice communications, but instead, just simple text messaging (like with MSN messenger or yahoo chat, but for an internal office LAN). I've looked around and everything that I could find for Linux are software phones that work over SIP to do voice calling. Is there really nothing out there that will let me connect to Live Communications Server and do plain old instant messaging?

---

### Post by mojorising on 2008-12-29
Hi. There is great news for those of us who have to log into Live Communications Server at work -- the SIPE project has resumed and has released a very functional version.

SIPE is a plug-in for Pidgin, allowing it to log in and exchange messages on an LCS server (Communicator server).

[https://sourceforge.net/projects/sipe/](https://sourceforge.net/projects/sipe/)

Installing SIPE is more of an "advanced user" operation as it currently must be compiled. I believe an unsupported DEB package for Debian/ Ubuntu will be released before very long.

Visit the SIPE project page and forums ([https://sourceforge.net/forum/forum.php?forum_id=688534](https://sourceforge.net/forum/forum.php?forum_id=688534)) for more information as well as installation instructions.

Basically, the install procedure is like this:

sudo apt-get install pkg-config libglib2.0-dev libgtk2.0-dev pidgin-dev libpurple-dev libtool intltool comerr-dev

Then do the following:
tar -xjvf pidgin-sipe-1.3.1.tar.bz2
cd pidgin-sipe-1.3.1
./configure --prefix=/usr
make
sudo make install


I'm quite sure you also need the build-essential meta package to compile the code.

If you have any questions or need any more information, post to the SIPE forum (after reading all the readmes and information already provided of course. ).


Hope this helps some people out there who may have been struggling or (worse) waiting to switch from Windows because of the lack of LCS client. Since this thread is so old, I'm betting dguy had to switch back to Windows. It's now safe to switch to Ubuntu again.  :)


Mike

---

### Post by entrapper on 2009-01-24
It might be silly, but after installing SIPE I wasted some time looking for it in the Plugin configuration dialog; you must actually be adding a new account (Menu Accounts -> Manage Accounts) selecting 'SIPE' for type in order to use this plugin.

I don't seem to be able to get through for want of TLS option.

---

### Post by mojorising on 2009-02-06
entrapper, that's right -- you do have to add your account in order to use the SIPE protocol just as you would for any other protocol like Yahoo, AIM, msn, etc, etc, etc. 

TLS support is now implemented and functional in the latest milestone release as well as all subsequent builds. You can not use the package included in the standard Ubuntu repositories yet -- you must use version 1.3.1 or later for a fully functional plug-in with TLS support. I believe a package for 1.3.1 is in the 8.10 Intrepid Ibex Universe repository but I recommend getting the latest nightly build from the project's Git repository and compiling from source (that's a lot easier than it sounds). Visit the project page at [https://sourceforge.net/projects/sipe/](https://sourceforge.net/projects/sipe/) and the forums there for more information and help if you need it. The Git repository is at [http://repo.or.cz/w/siplcs.git?a=shortlog;h=refs/heads/mob](http://repo.or.cz/w/siplcs.git?a=shortlog;h=refs/heads/mob) .  Just click the "tar.gz" link in the latest line at the top of the list to download the latest version of the plug-in. To install the snapshot, run the autoconfig script, then sudo make && make install. You may need to create a symbolic link to make it work (I'll post more on that later when I get to my work PC) and then re-start Pidgin. It might sound like a lot of work but it's really not bad and it's totally worth it to finally have access to your corporate IM from within Linux. 


Good luck, 
Mike

---

### Post by mojorising on 2009-02-27
The symlink you may need to create is from the modules in /usr/lib/pidgin to where they might not be. Try re-starting Pidgin and seeing if the new plug-in is present. If it's not, complete the following tasks:


sudo ln -s /usr/local/lib/pidgin/libsipe.so /usr/lib/pidgin/libsipe.so
sudo ln -s /usr/local/lib/pidgin/libsipe.la /usr/lib/pidgin/libsipe.la

Then re-start Pidgin again. You should be able to add MS LCS accounts at this point. 


Mike

---

### Post by zeroseven0183 on 2009-06-29
This worked, man. I have yet to document everything I did. Thank you very much for the post.

---

