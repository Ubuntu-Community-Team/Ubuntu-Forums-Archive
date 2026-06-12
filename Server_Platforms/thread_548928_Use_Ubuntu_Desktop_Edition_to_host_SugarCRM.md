---
title: "Use Ubuntu Desktop Edition to host SugarCRM?"
date: 2007-09-11
forum: Server Platforms
---

### Post by texplorer on 2007-09-11
We have two servers in the office; one is running Windows Small Business Server 2003 to go with office PCs that have XP pro and Outlook 2003. 

I want to host a CRM on the other server which provide CRM service to the office PCs. Is Ubuntu Desktop Edition up for this task? I am not good at command line environment in Ubuntu Server Edition. 

Is there a limit on the number of connections to Ubuntu Desktop Edition (server) from our office PCs. Windows Server has this kind of limit. If you want to have more computers on your network, you have to buy more licences. 

I want to put this CRM server with Ubuntu Desktop Edition on the internet one day. So it can capture leads from our website, hosted with a hosting co. now directly to our CRM server. 
What do I need to do protect it from attacks on the internet please?

Thanks,
Tom

---

### Post by southernman on 2007-09-11
> What do I need to do protect it from attacks on the internet please?

For starters, don't use a Desktop system to run your server.

---

### Post by Brazen on 2007-09-12
> **southernman said:**
> For starters, don't use a Desktop system to run your server.

Using Ubuntu desktop is going to be just fine for a server, though I would highly suggest just using it in testing.  Once you get SugarCRM up and working on the Desktop edition, Try installing the server edition, read some of the server docs on help.ubuntu.com and see how if you can get it running on that.  But there are no artificial restrictions built into the desktop edition, just a different set of default software.

By the way, SugarCRM is available in the Conanical commercial repos.  Not sure if you would want to install it that way though, I would personally probably rather install something like that from source since I don't believe you do any compiling.  I think it's just text files with php code that you dump into your web server directory.

As for securing it, Ubuntu comes secured by default.  There really isn't much you can do, unless you want to be really paranoid and install some extras like tripwire, snort, and... mmm.... there is another app that analyzes your log files and temporarily blocks ips when they look like they are trying to do nasty things, but I forget the name now....

The other thing about security and using the Desktop edition, there is more software installed on the Desktop edition which is unneccessary and more software means more possible exploits.  I use the server edition and then install as few applications as I need to get the job done.

---

### Post by southernman on 2007-09-12
> **Brazen said:**
> Using Ubuntu desktop is going to be just fine for a server, though I would highly suggest just using it in testing.  Once you get SugarCRM up and working on the Desktop edition, Try installing the server edition, read some of the server docs on help.ubuntu.com and see how if you can get it running on that.  But there are no artificial restrictions built into the desktop edition, just a different set of default software.

By the way, SugarCRM is available in the Conanical commercial repos.  Not sure if you would want to install it that way though, I would personally probably rather install something like that from source since I don't believe you do any compiling.  I think it's just text files with php code that you dump into your web server directory.

As for securing it, Ubuntu comes secured by default.  There really isn't much you can do, unless you want to be really paranoid and install some extras like tripwire, snort, and... mmm.... there is another app that analyzes your log files and temporarily blocks ips when they look like they are trying to do nasty things, but I forget the name now....

The other thing about security and using the Desktop edition, there is more software installed on the Desktop edition which is unneccessary and more software means more possible exploits.  I use the server edition and then install as few applications as I need to get the job done.

I am going on the fact of all the PAGES of info on securing and hardening of the "server" itself. Servers don't come with gnome (or any DE for that matter) as it makes for a larger target with more potential points of access to the www.

I suppose those server devs just don't understand what their doing though.

Besides, I answered to a specific question which I quoted in my reply. As for doing this strictly on a LAN that is 100% secured (no such thing unless you unplug from the pipe and turn your computers/server off) then by all means... get jiggy.

;)

I'd really love to see some documentation for confirming it's ok to run a server on top of a desktop and it be totally secure by default. Anyone can help a brother out?

---

### Post by SomethingCronic on 2007-09-13
The SugarCRM website offer ready to run vmimages that you boot using vmware player and it's all done for you - type in the web address and your away!

For testing this is excellent, in fact, I can't see many disadvantages to using it in a production environment depending on the size of you business.

---

### Post by Brazen on 2007-09-13
> **southernman said:**
> I am going on the fact of all the PAGES of info on securing and hardening of the "server" itself. Servers don't come with gnome (or any DE for that matter) as it makes for a larger target with more potential points of access to the www.

I suppose those server devs just don't understand what their doing though.

Besides, I answered to a specific question which I quoted in my reply. As for doing this strictly on a LAN that is 100% secured (no such thing unless you unplug from the pipe and turn your computers/server off) then by all means... get jiggy.

;)

I'd really love to see some documentation for confirming it's ok to run a server on top of a desktop and it be totally secure by default. Anyone can help a brother out?

hmm, I suspect you didn't read my entire post, since what you just said is pretty much the same thing I said in my final paragraph.  But yeah, it really can't be stressed enough that there are NUMEROUS advantages to keeping a minimal amount of software on your production servers including saving resources and having a smaller attack target.  And this isn't coming "pages" of info (though I have read them) but from also being a server administrator for several years.

---

