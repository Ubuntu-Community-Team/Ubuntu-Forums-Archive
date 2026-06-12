---
title: "Ubuntuzilla disabled my flash?"
date: 2009-06-01
forum: Ubuntuzilla
---

### Post by shoeheight on 2009-06-01
Hey all,

I can't get flash to work with my usual "flashplugin-installer".  

It was working find prior to my install of ubuntuzilla.  When I installed ubuntuzilla, my first problem was an IPv6 problem:
[http://ubuntuforums.org/showthread.php?t=1136912](http://ubuntuforums.org/showthread.php?t=1136912)

Now, after that is fixed I find my flash isn't working.  I am running a relatively fresh install of 9.04 on my 64bit. I've confirmed install of the "flashplugin-installer" on my synaptic package manager, and a reinstall has changed nothing. 

Any ideas?

Should I go back to swfdec?

---

### Post by nanotube on 2009-06-02
hmm, does it show up in "about:plugins" ?

---

### Post by shoeheight on 2009-06-03
All I can find in "about: plugins" is:
"video/flv Flash video"

Nothing about adobe, etc.

Is this any help?

---

### Post by nanotube on 2009-06-05
> **shoeheight said:**
> All I can find in "about: plugins" is:
"video/flv Flash video"

Nothing about adobe, etc.

Is this any help?

yes, it is very helpful indeed, shows that libflashplayer is not being seen by firefox.... i wonder where the plugin gets stuck by the installer... 

can you run the following command, and then post the complete output here:
```
locate libflash
```
this will show where the flashplugin is located.

also, the following:
```
update-alternatives --display xulrunner-flashplugin
```
this will show what your default flashplugin alternative is

and also this:
```
ls -al /opt/firefox/plugins
```
to see where firefox points for plugins.

---

### Post by shoeheight on 2009-06-08
> **nanotube said:**
> ...post the complete output here:
```
locate libflash
```
this will show where the flashplugin is located.

/usr/lib/flashplugin-installer/libflashplayer.so
/usr/lib/openoffice/basis3.0/program/libflashlx.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so


> **nanotube said:**
> also, the following:
```
update-alternatives --display xulrunner-flashplugin
```
this will show what your default flashplugin alternative is

xulrunner-flashplugin - status is auto.
 link currently points to /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
/var/lib/flashplugin-installer/npwrapper.libflashplayer.so - priority 50
Current `best' version is /var/lib/flashplugin-installer/npwrapper.libflashplayer.so.

> **nanotube said:**
> and also this:
```
ls -al /opt/firefox/plugins
```
to see where firefox points for plugins.

lrwxrwxrwx 1 root root 33 2009-05-29 17:19 /opt/firefox/plugins -> /usr/lib/xulrunner-addons/plugins


Let me know. 

Seamonkey is working fine...I'm using that for now.

FYI, I'll be away from June 12-22nd....climbing mountains in Alaska....

Thanks

---

### Post by nanotube on 2009-06-12
well, that's strange, it seems that everything points where it should as far as the plugin goes... the only thing different is that it points to npwrapper.libflashplayer, which i think has to do with you being on 64bit.

try using update-alternatives to change your default flash alternative to the plain /usr/lib/flashplugin-installer/libflashplayer.so

something like ```
sudo update-alternatives xulrunner-flashplugin
``` should let you choose it.

---

### Post by retkeur on 2009-06-22
I am having exactly the same problem like shoeheight. I executed the same commands and got the same output. 

Afterwards, I tried the latest solution proposed by nanotube, but I get the following error > update-alternatives: unknown argument `xulrunner-flashplugin'.

Any suggestions?

---

### Post by shoeheight on 2009-06-25
Same issue with me...must be the wrong command...but I can't figure out the right one....:confused:

---

### Post by nanotube on 2009-06-26
hmm, maybe the alternative is named differently in jaunty..
look in directory /etc/alternatives/ and see what's in there. for starters, just try running a 
```
ls -al /etc/alternatives/ | grep flash
```
and post the complete output here...

---

### Post by shoeheight on 2009-06-26
Here is the output
```
ls -al /etc/alternatives/ | grep flash
lrwxrwxrwx   1 root root    58 2009-05-30 22:03 firefox-flashplugin -> /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
lrwxrwxrwx   1 root root    58 2009-05-30 22:03 iceape-flashplugin -> /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
lrwxrwxrwx   1 root root    58 2009-05-30 22:03 iceweasel-flashplugin -> /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
lrwxrwxrwx   1 root root    58 2009-05-30 22:03 midbrowser-flashplugin -> /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
lrwxrwxrwx   1 root root    58 2009-05-30 22:03 mozilla-flashplugin -> /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
lrwxrwxrwx   1 root root    58 2009-05-30 22:03 xulrunner-addons-flashplugin -> /var/lib/flashplugin-installer/npwrapper.libflashplayer.so
lrwxrwxrwx   1 root root    58 2009-05-30 22:03 xulrunner-flashplugin -> /var/lib/flashplugin-installer/npwrapper.libflashplayer.so

```

---

### Post by nanotube on 2009-06-27
ah, heh, my bad, forgot to add the '--config' option. so, try this:
```
sudo update-alternatives --config xulrunner-flashplugin
```
and see if you can change it to /usr/lib/flashplugin-nonfree/libflashplayer.so, instead of the npwrapper thing. 

then restart firefox, and see if firefox likes that better. :)

---

### Post by shoeheight on 2009-06-29
No luck

```
sudo update-alternatives --config xulrunner-flashplugin

There is only 1 program which provides xulrunner-flashplugin
(/var/lib/flashplugin-installer/npwrapper.libflashplayer.so). Nothing to configure.

```

---

### Post by nanotube on 2009-06-30
Hi
well... time to resort to some heavy measures, then. :)

create a "plugins" subdirectory inside your firefox profile directory. your firefox profile is located in ~/.mozilla/firefox/somerandomnumbers.default/
so you'd create a plugins dir inside there.

then, grab the flash plugin .tar.gz file from adobe. go here:
[http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)
and select the "tar.gz" version.
(or, here's a direct link: [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz) )

open it up with archive manager - you'll see two files in there, one of them is a "libflashplayer.so". take that one, and stick it into that plugins directory you just created in your profile.

then, restart firefox, and (hopefully) watch the flash magic. :)

---

### Post by neufena on 2009-07-01
I had the same problem and that didn't work for me but copying libflashplayer to /opt/firefox/plugins did.

---

### Post by Jungleboss on 2009-07-03
Same problem for me. Flash working in FF 3 bit not in 3.5 after using the Ubuntuzilla script. Running Flash 10, native 64-bit version [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I've tried copying my libflashplayer.so (from /usr/lib/mozilla/plugins) to ~/.mozilla/firefox/xxx.default/plugins, but it doesn't work. /opt/firefox/plugins didn't work either.

---

### Post by Jungleboss on 2009-07-03
I have one more problem after the upgrade. Text in Firefox 3.5 doesn't change according to text rendering settings in "System/Preferences/Appearance/Fonts/Rendering"

---

### Post by nanotube on 2009-07-03
> **Jungleboss said:**
> Same problem for me. Flash working in FF 3 bit not in 3.5 after using the Ubuntuzilla script. Running Flash 10, native 64-bit version [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

I've tried copying my libflashplayer.so (from /usr/lib/mozilla/plugins) to ~/.mozilla/firefox/xxx.default/plugins, but it doesn't work. /opt/firefox/plugins didn't work either.

Hi
since mozilla build of firefox is 32bit, you have to use the 32bit flash plugin for it. so try getting the 32bit zip from adobe, and putting that libflashplayer.so into the profile plugins, or /opt/firefox/plugins

---

### Post by nanotube on 2009-07-03
> **Jungleboss said:**
> I have one more problem after the upgrade. Text in Firefox 3.5 doesn't change according to text rendering settings in "System/Preferences/Appearance/Fonts/Rendering"

Hi
this issue is a known bug. See here:
[http://ubuntuforums.org/showthread.php?t=1200992](http://ubuntuforums.org/showthread.php?t=1200992)

---

### Post by Jungleboss on 2009-07-03
> **nanotube said:**
> Hi
since mozilla build of firefox is 32bit, you have to use the 32bit flash plugin for it. so try getting the 32bit zip from adobe, and putting that libflashplayer.so into the profile plugins, or /opt/firefox/plugins

Thanks! Will try that.

Are there any nagative sides running 32 bit Firefox on a 64 bit OS?

---

### Post by nanotube on 2009-07-04
no not that i know of... except maybe it's a little slower than a native 64bit build.

---

### Post by shane2peru on 2009-07-05
If anyone figures this out I would be greatly interested too.  I downgraded back to the repo version, I couldn't get any of the plugins enabled with firefox 3.5.  I have java for 64bit and flash 10 for 64bit installed with current repo version of firefox.  I put them all into the /opt/firefox/plugin folder and nothing.  Real weird.  Any solid proven solutions would be great!  

Shane

---

### Post by nanotube on 2009-07-06
> **shane2peru said:**
> If anyone figures this out I would be greatly interested too.  I downgraded back to the repo version, I couldn't get any of the plugins enabled with firefox 3.5.  I have java for 64bit and flash 10 for 64bit installed with current repo version of firefox.  I put them all into the /opt/firefox/plugin folder and nothing.  Real weird.  Any solid proven solutions would be great!  

Shane

did you try using the 32bit flash plugin, as I suggested a couple posts ago?

---

### Post by shane2peru on 2009-07-06
> **nanotube said:**
> did you try using the 32bit flash plugin, as I suggested a couple posts ago?

Nope, I guess I overlooked it.  I'm not that great at all this 64bit, 32bit stuff.  All I know is that with my current version of firefox flash works, java works.  Flash I could careless about, I don't use it that much, but java I need for a few sites.  I honestly don't have time to mess around with it right now, or be the guinea pig to figure it out.  My seamonkey is messed up too since I started messing around with this stuff, and I don't know how to fix that either.  Also swiftweasel that I was using for a bit, is also messed up.  So the only option I have to use at the moment is my firefox.  It is weird because when I put in ```
about:plugins
``` in seamonkey or the 3.5firefox it shows that no plugins are configured!  Well that is about annoying because I know I had plugins configured before and seamonkey hasn't changed!  Arggh.  I don't think it is a 32, 64 issue, I think something is messed up, permissions, or where the plugins are put, or that I have tried so many locations that I have messed up everything, so for the time being I will have to stick with what is working.  I'm currently using Java64 and Flash10-for 64 with firefox everything working.  If someone posts positive results of something foolproof working I would be willing to give that a try.  I'm somewhat limited on time, or I would mess around with this.

Shane

---

### Post by strife25 on 2009-07-08
I just wanted to let people here know that downloading the 32-bit build of flash palyer and placing it into the /opt/firefox/plugins directory will solve this problem.

---

### Post by shane2peru on 2009-07-08
> **strife25 said:**
> I just wanted to let people here know that downloading the 32-bit build of flash palyer and placing it into the /opt/firefox/plugins directory will solve this problem.

Are you running Ubuntu 64bit version?  Just curious if this would work for me too.  Thanks for posting.

Shane

---

### Post by heltoupee on 2009-07-17
You guys are all touching on a much larger problem with Ubuntuzilla in general.  Automated package managers on x86_64 versions of Ubuntu (which I run, and curse daily) are set up to accept 64bit versions of plugins.  Ubuntuzilla installs the 32bit version of the browser, along with some libraries required to run it on 64bit OSes (the OS already has 64bit versions of these libraries, but 32bit firefox needs 32bit libraries).  If you were running firefox from the repository, none of your plugins will work because you've got the 64bit versions of all of them.

The far worse problem is that, once you go with Ubuntuzilla on a 64bit machine, you won't be able to use ANY plugins from Synaptic, apt, .debs, etc. because your system will either grab the 64bit version, which will be incompatible, or complain (in the case of the .deb) that you've downloaded the 32bit version, but 32bit is the wrong architecture.  So, you are completely on your own once you go this route.

I am uninstalling Ubuntuzilla due to these issues, and reverting to ff 3.0.11 until Ubuntu gets it's act straight and packages updated versions of the browser for older versions of its OS.

---

### Post by shane2peru on 2009-07-18
> **heltoupee said:**
> You guys are all touching on a much larger problem with Ubuntuzilla in general.  Automated package managers on x86_64 versions of Ubuntu (which I run, and curse daily) are set up to accept 64bit versions of plugins.  Ubuntuzilla installs the 32bit version of the browser, along with some libraries required to run it on 64bit OSes (the OS already has 64bit versions of these libraries, but 32bit firefox needs 32bit libraries).  If you were running firefox from the repository, none of your plugins will work because you've got the 64bit versions of all of them.

The far worse problem is that, once you go with Ubuntuzilla on a 64bit machine, you won't be able to use ANY plugins from Synaptic, apt, .debs, etc. because your system will either grab the 64bit version, which will be incompatible, or complain (in the case of the .deb) that you've downloaded the 32bit version, but 32bit is the wrong architecture.  So, you are completely on your own once you go this route.

I am uninstalling Ubuntuzilla due to these issues, and reverting to ff 3.0.11 until Ubuntu gets it's act straight and packages updated versions of the browser for older versions of its OS.

Well, that certainly sounds like a viable explanation of this.  And is probably the cause of my problems.  Thanks for the explanation.  I have to wonder how difficult it would be just to install the 64bit version of Firefox from their (Mozilla's) web site?  I will have to look into it later.  From the Ubuntuzilla script, doesn't seem that difficult.  We will have to see.  

Shane

---

### Post by anonymous_user on 2009-07-19
> **nanotube said:**
> Hi
since mozilla build of firefox is 32bit, you have to use the 32bit flash plugin for it. so try getting the 32bit zip from adobe, and putting that libflashplayer.so into the profile plugins, or /opt/firefox/plugins
Thank you! That worked great.

---

### Post by nanotube on 2009-07-21
> **shane2peru said:**
> Well, that certainly sounds like a viable explanation of this.  And is probably the cause of my problems.  Thanks for the explanation.  I have to wonder how difficult it would be just to install the 64bit version of Firefox from their (Mozilla's) web site?  I will have to look into it later.  From the Ubuntuzilla script, doesn't seem that difficult.  We will have to see.  

Shane

Well, that /would/ be a great solution, but unfortunately mozilla does not release 64bit builds, only 32bit builds. So it would not be logically possible to install a "64bit mozilla build". 

If you guys want, try pestering the mozilla folks to make 64bit releases - if enough people request it, maybe it will happen, and then ubuntuzilla can pull 64bit versions for 64bit os, and everything will be peachy. :)

---

### Post by shane2peru on 2009-07-24
> **nanotube said:**
> Well, that /would/ be a great solution, but unfortunately mozilla does not release 64bit builds, only 32bit builds. So it would not be logically possible to install a "64bit mozilla build". 

If you guys want, try pestering the mozilla folks to make 64bit releases - if enough people request it, maybe it will happen, and then ubuntuzilla can pull 64bit versions for 64bit os, and everything will be peachy. :)

Ha ha:lolflag:  good point!!!  There is no FF for 64 bit.  I guess I need to look into this stuff a little more.  Will have to do that later.  

Shane

---

### Post by nanotube on 2009-08-05
hi all

i have added a new section to the ubuntuzilla faq detailing the procedure for sticking the latest flash into ubuntuzilla's firefox for 64-bit users.

Here's the faq: [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Ubuntuzilla_FAQ)

---

### Post by shane2peru on 2009-08-06
Thanks!  Much appreciated!

Shane

PS:  how about java?

PSS.  That is kind of annoying, Mozilla should make a 64bit Firefox.  Adobe finally goes through the process of making a Flash for 64bit, and java too, and we can't even use them because Mozilla is now lagging behind.  Nothing against Ubuntuzilla, just my complaining against Mozilla.

---

### Post by nanotube on 2009-08-06
Hi

Don't know yet about java... should theoretically be possible same way as for flash.

yea, mozilla is dropping the ball on 64bit build... i asked on the mozilla irc channel today, it seems that they're not planning on 64bit builds any time soon, at least until firefox4. presumably they don't have the new tracemonkey javascript engine ready for 64bit yet...

---

### Post by buzzi on 2010-01-24
> **nanotube said:**
> Hi
since mozilla build of firefox is 32bit, you have to use the 32bit flash plugin for it. so try getting the 32bit zip from adobe, and putting that libflashplayer.so into the profile plugins, or /opt/firefox/plugins

 thank you very much nanotube!!!! I tried to download the 32 bit version (that appears automatically, you must only select che type of file to download such as .deb. tar.gz etc), I copied it to /opt/firefox/plugins, restart firefox and it works perfectly!!!!  now I have 2 add-ons: future splash and shockwave flash  PS sorry for the errors, but i am not english...  byeeeeeeeeeeeeee

---

### Post by nanotube on 2010-01-24
> **buzzi said:**
> thank you very much nanotube!!!! I tried to download the 32 bit version (that appears automatically, you must only select che type of file to download such as .deb. tar.gz etc), I copied it to /opt/firefox/plugins, restart firefox and it works perfectly!!!!  now I have 2 add-ons: future splash and shockwave flash  PS sorry for the errors, but i am not english...  byeeeeeeeeeeeeee

glad it worked out for you :)

---

### Post by buzzi on 2010-01-28
there is a new problem now](*,)
flash player disables everytime I close firefox: if I want to enable it, I must write in the terminal ```
cp /home/buzzi/Scrivania/libflashplayer.so /opt/firefox/plugins

``` and flash appears.
this is not a big problem, but it's a bit boring always write it...
have you a solution for this problem???

bye;)

---

### Post by nanotube on 2010-01-28
> **buzzi said:**
> there is a new problem now](*,)
flash player disables everytime I close firefox: if I want to enable it, I must write in the terminal ```
cp /home/buzzi/Scrivania/libflashplayer.so /opt/firefox/plugins

``` and flash appears.
this is not a big problem, but it's a bit boring always write it...
have you a solution for this problem???

bye;)

probably best to just stick your libflashplayer.so in ~/.mozilla/plugins
```
mkdir -p ~/.mozilla/plugins
cp ~/Scrivania/libflashplayer.so ~/.mozilla/plugins

```

---

### Post by buzzi on 2010-01-28
wow!!!it work perfetcly now! but it's strange because some days ago I tried to copy that in ~/.mozilla/plugins and it didn't work...maybe because I use ubuntuzilla and i did't copy libflashpalyer.so in /op/firefox/plugins;)

bye and thank you:D

---

### Post by nanotube on 2010-01-28
> **buzzi said:**
> wow!!!it work perfetcly now! but it's strange because some days ago I tried to copy that in ~/.mozilla/plugins and it didn't work...maybe because I use ubuntuzilla and i did't copy libflashpalyer.so in /op/firefox/plugins;)

bye and thank you:D

glad it worked out for you :)

btw, shouldn't matter if you have it in /opt, as long as you have it in ~/.mozilla/plugins, that takes precedence.

but at any rate, now that it works, it's all good. :)

---

### Post by buzzi on 2010-01-28
> **nanotube said:**
> but at any rate, now that it works, it's all good. :)


yes, this is the most important ;);)

mysteries of linux and PCs:D

---

