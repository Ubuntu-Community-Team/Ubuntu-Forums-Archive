---
title: "can not get into vmware virtual machine console"
date: 2008-09-25
forum: Virtualisation
---

### Post by bzimage on 2008-09-25
hi,

I have installed vmware server2, that's ok, poweron a vmx ok, switch to the console page , and installed a plugin ok, then there is a hint "click anywhere to open virtual machine" I did, but get a warning dialog as follow:

------------------------------------
Cannot access virtual machine console. The request timed out.

The attempt to acquire a valid session ticket for "winxp" took longer than expected. If this problem persists, contact your system administrator.
------------------------------------

what's wrong with it, anyone can help me, thanks a lot.

---

### Post by tinyviking on 2008-09-25
Hey.  I've just installed VM Server 2 as well.  when I started the console from the terminal it sprang up a new Firefox window which then prompted me with an error about certificates not being authorised.  I followed the prompts to add an exception for the vmware console "https://127.0.0.1:8333" to firefox.

This may be a complete red herring but it's probably making sure you have this configured in Firefox (or your preferred browser).

Small side note is - during the install of VMWare Server 2; when asked if I wanted to change the currently configured administrator from '' I entered my own username.
not sure if this might make a difference - all other settings were left at defaults.

Hope you find a solution!

---

### Post by bzimage on 2008-09-25
thank you tinyviking,

I'm sure I have done what you mentioned, including changing the admin user name.
Now I'm doubting if it is because I'm using the 64bit ubuntu and 64bit vmserver2, is yours 64bit version?

---

### Post by trmentry on 2008-09-26
I'm running 64 bit and have no issues.


remember the web interface is on 
http - tcp/8222
https - tcp/8333

but you need this as well
console - tcp/902

so if you have some type of firewall or filter up, you need to forward both 8333 and 902



also you need to restart firefox after install of the addon... i'm sure you did.. but just mentioning it.

when I installed mine... it said that my default admin was going to be  ' '   and I was logged on as root... so I just gave it my name (logon) as I wasn't sure how it would react to the the 'blank' name later on.

you should be able to re-config vmware by issuing the following as root or sudo'ing it.

/usr/bin/vmware-config.pl

---

### Post by bdmeyer on 2008-09-28
I think you can rule all of that out.
I have the esact same error. I am running Vista Ultimate, which is supposed to be a supported host.

My guest it fedora 9.

WHen I try to connect to their of the vm's (which worked in vmplayer, and do work in server 1.07 running on XP)

I get:
cannot access viortual machine console. The request timed out. 
The attemtp top acquire a valid session ticket for "(vm name)" took longer than expected. If this problem persists, contaft the system admin.

I get this error when lauching VMWare server 2 console in internet explorer 7.

When launching it in Firefox 3.02 I get:
Unable to connect to the MKS: Timeout while attempting to read.

After turning off the firewall, I tried to connect to the console again, and received :
Unable to connect to the MKS: Cannot connect to the host (name): No connection could be made because the target machine actively refused it.



Hope it helps a bit. If anyone finds the fix, I sure would appreciate an email.



--Bruce D. Meyer

---

### Post by tkho on 2008-10-19
I came across the same problem, and found that disabling Flashblock did the trick.

Credit goes to this guy: [http://communities.vmware.com/thread/140776](http://communities.vmware.com/thread/140776)

---

### Post by tman148 on 2008-11-03
Noscript can also be the problem. It was for me.A quick reset of Noscript and I was able to bring up the remote console.. Why must I tinker with everything?

---

### Post by psypher on 2008-11-12
in my case I tried disabling all add-ons and also re-installed the plug-in module. worked after that and re-enabled all add-ons and everything still worked. So i think it was just the plug-in.

---

### Post by bnuytten on 2009-05-21
Similar experience as psypher.

Uninstall the "VMware Remote Console Plug-in" add-on, restart firefox, try to open the console to install the add-on, restart firefox. It now works like it used to.

Just for the record:
```
uname -a
Linux jupiter 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:58:03 UTC 2009 x86_64 GNU/Linux
lsb_release -d
Description:	Ubuntu 9.04
```

---

### Post by jimi_cook on 2009-11-16
Hey guys, thanks for the tips, it was NoScript that was blocking me when I had the same problem.

---

### Post by dcstar on 2009-11-18
> **jimi_cook said:**
> Hey guys, thanks for the tips, it was NoScript that was blocking me when I had the same problem.

Yet another reason why I stay with Server 1.0.10 using the old console.....

Using a web browser for things like this is just getting more and more difficult as security keeps bashing up against functionality.

---

### Post by RazorV on 2009-12-08
> **tman148 said:**
> Noscript can also be the problem. It was for me.A quick reset of Noscript and I was able to bring up the remote console.. Why must I tinker with everything?

I had tried the removal of the VMware plugin and that didn't work.  I also reconfigured vmware and that didn't work.  I still cannot get to the console in Firefox using:  [https://127.0.0.1:8333](https://127.0.0.1:8333).  All I get is a blank screen and the tab in firefox says, "Loading..."

No login appears.

What is "Noscript: and how do I fix it?

thanks
Greg

---

### Post by RazorV on 2009-12-08
well after searching i found that Noscrip was a plugin in FireFox (yea I'm a newbie).  I added the plugin and then added the exception for the local host and boom up came vmware console.  what a pain the *****  cheers, Greg

---

### Post by tricolorpoa on 2010-01-21
> **trmentry said:**
> I'm running 64 bit and have no issues.


remember the web interface is on 
http - tcp/8222
https - tcp/8333

but you need this as well
console - tcp/902

so if you have some type of firewall or filter up, you need to forward both 8333 and 902



also you need to restart firefox after install of the addon... i'm sure you did.. but just mentioning it.

when I installed mine... it said that my default admin was going to be  ' '   and I was logged on as root... so I just gave it my name (logon) as I wasn't sure how it would react to the the 'blank' name later on.

you should be able to re-config vmware by issuing the following as root or sudo'ing it.

/usr/bin/vmware-config.pl
Very thanx!!!

---

### Post by Chipolata on 2010-02-27
I'm having this exact problem, however I have tried uninstalling all my add-ons in firefox and reinstalling the vmware console plugin with no luck. I'm running Ubuntu 64bit, 2.6.31-19-generic, with 64 bit firefox v3.6. The VM is 32bit windows XP, sitting on an NTFS partition - not sure if that matters (yes, ntfs write is enabled). I've also tried forwarding ports 8333, 8222 on my router and 902 with no luck. I also cannot get access to the vmware access page using https, only http.  
 
Any ideas?

EDIT: I ended up just installing VMWare Player and accessing the vm from that - I can't say I'm too fond of that web interface.

---

### Post by jweierman on 2010-04-07
Definitely some sort of Firefox issue. I launched the console in IE 7 and was able to get the Virtual Machine window to launch OK.

---

### Post by ojosdeperro on 2010-05-10
I have the same problem. my desktop:

```

Linux martin-desktop 2.6.32-21-generic 
#32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

```

I have install again my SO, here is running with the vmware server 2.0.1.
Mi browser is the firefox 3.6.3. I haven't got install any plugin or firewall, when i go to [https://localhost:8333](https://localhost:8333) the browser still waiting, when i refresh it, i receive a message who said that the connexion has been restored. :(

Anybody have a solution for this?

---

### Post by damytzeus on 2010-05-27
> **ojosdeperro said:**
> I have the same problem. my desktop:

```

Linux martin-desktop 2.6.32-21-generic 
#32-Ubuntu SMP Fri Apr 16 08:09:38 UTC 2010 x86_64 GNU/Linux

```

I have install again my SO, here is running with the vmware server 2.0.1.
Mi browser is the firefox 3.6.3. I haven't got install any plugin or firewall, when i go to [https://localhost:8333](https://localhost:8333) the browser still waiting, when i refresh it, i receive a message who said that the connexion has been restored. :(

Anybody have a solution for this?

Try this:
1.) In the address bar, enter "about:config:
2.) search for "security.enable_ssl2"
3.) toggle it to "true"

close and access vmware.  this worked for me.

---

### Post by flavio.vani on 2010-06-01
I am running the very same problem. None of the above sugestions helped me to solve the problem.
Did I miss something? Can anyone help me?
Ubuntu 10.04, 65bits.
Thanks.

---

### Post by flavio.vani on 2010-06-01
Ops... 65bits it's not my problem... Ubuntu is 64bits, really!

---

### Post by useResa on 2010-06-02
I have had the same issue, the way I was able to workaround the issue I have described in [this post]("http://ubuntuforums.org/showpost.php?p=9400498&postcount=2") in another thread.

---

### Post by tixetsal on 2010-06-04
> **useResa said:**
> I have had the same issue, the way I was able to workaround the issue I have described in [this post]("http://ubuntuforums.org/showpost.php?p=9400498&postcount=2") in another thread.

Kudos to you, useResa, for figuring that one out.  After installing FF 3.5.9, uninstalling the Remote Console Plug-in, killing all running instances of 3.6.x, and reinstalling the plug-in from 3.5.9, VMW Server 2 is now happy.  Thanks for the tip.

---

### Post by flavio.vani on 2010-06-06
Yeah! Thanx, useResa! Just got back to FF 3.5.9 and the problem gone way.

---

### Post by useResa on 2010-06-08
> **tixetsal said:**
> Kudos to you, useResa, for figuring that one  out.

> **flavio.vani said:**
> Yeah! Thanx, useResa! Just got back to FF 3.5.9 and the problem gone way.

Thank you for your reactions.
Glad that I could provide a working tip to get the VMware Server console up and running again.

Nevertheless I do hope that the issues with the console will be ironed out and that we can get back to one version of firefox.

---

### Post by gorostas on 2010-06-19
Hi useResa, 

I'm also greatfull to youre tip for installing older ff and it works... I can open console, yeeees!

Did managed desperatly to get mac guest to successfully run on ubuntu x64 finaly.. 

cheers!

---

### Post by Thilips on 2010-06-19
If the suggestions above didn't work these do. I am posting the instructions and original website. VMWare is getting harder and harder to use with Ubuntu, may have to find something else soon.

-Download Firefox 3.5.9 from:
[http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)
                 or
[http://www.adrive.com/public/e1348b5df7b15971ce26bec2abcfee43b0e774e9dab697749ec218b673a9a43c.html](http://www.adrive.com/public/e1348b5df7b15971ce26bec2abcfee43b0e774e9dab697749ec218b673a9a43c.html)
(note: even when the Mozilla site expires the adrive site will still be available. This is my online storage)

-Extract the .tar file and rename the extracted folder from firefox to firefox-3.5.9.
-Type or copy the following command: sudo mv -r firefox-3.5.9 /../usr/lib
-In a terminal go to the /usr/lib directory: cd /usr/bin
-Create a symbolic link to firefox in the firefox-3.5.9 folder:
ln -s /usr/lib/firefox-3.5.9/firefox firefox-old.
-As root or using "sudo" edit the /etc/vmware/config file by adding the following line:
xkeymap.nokeycodeMap = "TRUE"
-Remove the VMWare console plugin from the current Firefox.
-From a terminal type the following: firefox-old
-Reinstall the VMWare console plugin.

This fix is guranteed even if using about:config, which is suggested from VMWare, does not work. The site below is where I received the original fix from. Give this lady her props. Again I agree with her, VMWare is become more of a hassle to work with Ubuntu.

[http://resa.linux-hardcore.com/?p=547](http://resa.linux-hardcore.com/?p=547)

---

### Post by useResa on 2010-06-20
> **gorostas said:**
> Hi useResa, 
I'm also greatfull to youre tip for installing older ff and it works... I can open console, yeeees!
Glad that the tip helped.

> **Thilips said:**
> note: even when the Mozilla site expires the adrive site will still be available. This is my online storageGreat idea to make this old version available from a different location.

> **Thilips said:**
> The site below is where I received the original fix from. Give this lady her props. Again I agree with her, VMWare is become more of a hassle to work with Ubuntu.

[http://resa.linux-hardcore.com/?p=547](http://resa.linux-hardcore.com/?p=547)A minor note .... I am a MALE.  :lolflag:
But glad that you have got it working and that you can use the console again.

---

### Post by Vinas on 2010-06-22
> **Thilips said:**
> If the suggestions above didn't work these do. I am posting the instructions and original website. VMWare is getting harder and harder to use with Ubuntu, may have to find something else soon.

-Download Firefox 3.5.9 from:
[http://www.mozilla.com/en-US/firefox/all-older.html](http://www.mozilla.com/en-US/firefox/all-older.html)
                 or
[http://www.adrive.com/public/e1348b5df7b15971ce26bec2abcfee43b0e774e9dab697749ec218b673a9a43c.html](http://www.adrive.com/public/e1348b5df7b15971ce26bec2abcfee43b0e774e9dab697749ec218b673a9a43c.html)
(note: even when the Mozilla site expires the adrive site will still be available. This is my online storage)

-Extract the .tar file and rename the extracted folder from firefox to firefox-3.5.9.
-Type or copy the following command: sudo mv -r firefox-3.5.9 /../usr/lib
-In a terminal go to the /usr/lib directory: cd /usr/bin
-Create a symbolic link to firefox in the firefox-3.5.9 folder:
ln -s /usr/lib/firefox-3.5.9/firefox firefox-old.
-As root or using "sudo" edit the /etc/vmware/config file by adding the following line:
xkeymap.nokeycodeMap = "TRUE"
-Remove the VMWare console plugin from the current Firefox.
-From a terminal type the following: firefox-old
-Reinstall the VMWare console plugin.

This fix is guranteed even if using about:config, which is suggested from VMWare, does not work. The site below is where I received the original fix from. Give this lady her props. Again I agree with her, VMWare is become more of a hassle to work with Ubuntu.

[http://resa.linux-hardcore.com/?p=547](http://resa.linux-hardcore.com/?p=547)This worked like an absolute treat with ubuntu 10.04 amd64... THANK YOU PEOPLE ):P :popcorn::guitar::p):P\\:D/:-\"=D>

---

### Post by shubes on 2010-07-03
I came across this problem yesterday when I upgraded my firefox to v3.6.6, which was released last week to Hardy (8.04 LTS). So much for LTS stability. :( Although to be fair, I suspect at this point that VMware needs to tweak the plugin a tad to restore functionality under FF3.6.

I was able to work around this problem doing 2 things found on this thread: [http://support.mozilla.com/en-US/forum/1/570224?forumId=1&comments_threshold=0&comments_parentId=570224&comments_offset=0&comments_per_page=20&thread_style=commentStyle_plain](http://support.mozilla.com/en-US/forum/1/570224?forumId=1&comments_threshold=0&comments_parentId=570224&comments_offset=0&comments_per_page=20&thread_style=commentStyle_plain)

First thing was to enable all ssl2 related settings in about:config, as suggested by Alan Doyle on the 5th page. That allowed me to log in, but the console was still unaccessible.

Then I executed the plugin directly from the command line, as described by Mike Masseo on the 4th page. I created an application launcher for vmware-vmrc, and I'm back in business. :)

To be honest, I think I like this separate launcher for vmware-vmrc, because I don't need to log into the webui first to get a console. Still need to login, but it's a bit faster this way.

On a side note, the webui appears to have lost some of its sluggishness with the FF3.6 upgrade. The webui is noticeably faster now in some parts, but there's still a delay in some portions of the window. FWIW. I do dislike going backwards, so this workaround is ok with me.

---

### Post by useResa on 2010-07-04
> **shubes said:**
> Then I executed the plugin directly from the command line, as described by Mike Masseo on the 4th page. I created an application launcher for vmware-vmrc, and I'm back in business. :)Personally I have used this workaround as well. ;) 
I did need to do some tweaking, both for Ubuntu and Fedora (that I use as well). Posted how I did achieve this for Fedora on [my blog]("http://resa.linux-hardcore.com/?p=577"), but for Ubuntu it was not that much different.

> **shubes said:**
> To be honest, I think I like this separate launcher for vmware-vmrc, because I don't need to log into the webui first to get a console. Still need to login, but it's a bit faster this way.I fully agree, the separate launcher is an easier way and does not make you dependent on the browser for using the console

---

### Post by davekenny on 2010-07-29
using vmware-vmrc worke for me.
I did need to change some permissions on files in the lib and bin directories in the pluggins directory.

also I had to use the localhost:8333 not the localhost:8222..minor point
since it works

thanks

Davekenny

---

### Post by Asif786i on 2010-10-18
Hi All

First post as I am new to vmware and ubuntu. :)

I have tried to implement the Resa workaround by dowloading firefox 3.5.9 and creating a symbolic link to firefox-old. However I get this error message when running firefox-old

usr/lib/firefox-3.5.9/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

Can somebody tell whats going on and how to fix it please
Thanx
Asif

---

### Post by Asif786i on 2010-10-20
> **Asif786i said:**
> Hi All
 
First post as I am new to vmware and ubuntu. :)
 
I have tried to implement the Resa workaround by dowloading firefox 3.5.9 and creating a symbolic link to firefox-old. However I get this error message when running firefox-old
 
usr/lib/firefox-3.5.9/firefox-bin: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
 
Can somebody tell whats going on and how to fix it please
Thanx
Asif
 
Hi All
 
Got this sorted by installing the 32bit libraries. ie.
 
sudo apt-get install ia32-libs
 
Now works from the command line.
Regards
Asif

---

### Post by santan on 2010-10-31
> **tixetsal said:**
> Kudos to you, useResa, for figuring that one out.  After installing FF 3.5.9, uninstalling the Remote Console Plug-in, killing all running instances of 3.6.x, and reinstalling the plug-in from 3.5.9, VMW Server 2 is now happy.  Thanks for the tip.

Thanks so much. This is the only fix for the "Cannot open console" problem!!.. You rock  useResa!!

---

### Post by dcstar on 2010-11-05
> **Asif786i said:**
> Hi All
 
**Got this sorted by installing the 32bit libraries**. ie.
 
sudo apt-get install ia32-libs
 
Now works from the command line.
Regards
Asif

That is because you incorrectly installed a 32-bit version on your 64-bit system.

Just install the native 64-bit version from Ubuntu:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by galaxy4public on 2010-11-23
I just wanted to point out that one can get into VMware VM's console by using VMware Player (e.g. vmplayer -h).  VMware Player is available for both 32/64-bit architectures.

However, if you are a security concerned person and you don't want to run VMware Player's installation as root, there is an option how to create [_a stripped down version of VMware Player_]("http://dmitry.khlebnikov.net/2010/11/howto-vmware-player-as-remote-console.html") with just remote console support, yet it runs under a non-privileged account.

---

### Post by mclooker on 2010-12-21
i've found the script to launch firefox vmware-vmrc plugin directly (you have to install it at first with firefox, i did with older one firefox-3.5.16).

then edited the script by chaging "tail" to "head", since it tries to activate vmware-vmrc directly, while in firefox extension folder there's a bash wrapper for connecting the binary with libraries which came to gether with a plugin

and placed it in >>
/usr/local/bin/vmware-console.sh



script:


#!/bin/bash
################################################################################
# Call VMWare Server's Remote Console in a clean GTK setup.                    #
# Author: Holger                                                               #
# URL: [http://shellack.de/info/content/vmware-server-20-console-failure](http://shellack.de/info/content/vmware-server-20-console-failure)        #
################################################################################

# Clean GTK setup for VMWare
export VMWARE_USE_SHIPPED_GTK=yes
#export GDK_NATIVE_WINDOWS=1

# Find console executable in Firefox plugins.
vmrc="$(find "$HOME/.mozilla/firefox" -name vmware-vmrc -type f -perm -111 | head -1)"
echo "$vmrc found - launching...:)"
[ -x "$vmrc" ] || exit 1

set -x
cd "$(dirname "$vmrc")" && "$vmrc" -h 127.0.0.1:8333

---

### Post by Thund3rstruck on 2011-03-14
> **galaxy4public said:**
> I just wanted to point out that one can get into VMware VM's console by using VMware Player (e.g. vmplayer -h).  VMware Player is available for both 32/64-bit architectures.

I tried the other solutions mentioned here and found them pretty tedious and cumbersome. The VMWare Player solution works great and removes the constant need to fool around with the browser. 

I put together a [quick walkthrough here ]("http://www.nealosis.com/blog/post/Firefox-36x-Unable-to-Connect-to-VMWare-Remote-Console.aspx")on setting up VMWare Player to use as a remote console for a VMWare Server.

---

### Post by djkadu on 2011-08-16
Another thing I had to do to get it working,

After installing old version of FF (3.5.9) I still could not open the console.
When trying to run the script mentioned earlier to call the plugin directly from the .mozilla folder I was getting some missing lib errors, so fiddled with it a bit and got it to work. 

```

sudo ln -s /usr/lib/vmware/lib/libexpat.so.0/libexpat.so.0 /var/lib/libexpat.so.0
sudo ln -s /home/kadu/.mozilla/firefox/gaktbnas.default/extensions/VMwareVMRC@vmware.com/plugins/lib/libview.so.2/libview.so.2 /var/lib/libview.so.2

```

It only works via the browser thou, I still get the error of missing libs via the script

Kadu

---

