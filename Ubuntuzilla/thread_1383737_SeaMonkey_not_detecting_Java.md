---
title: "SeaMonkey not detecting Java?"
date: 2010-01-17
forum: Ubuntuzilla
---

### Post by Uncle Spellbinder on 2010-01-17
Using the new Ubuntuzilla repo, I installed SeaMonkey 2.0.2. Java is not being detected. Places that use Java uploaders (Facebook  and the like) work fine in Firefox. In SeaMonkey I get a gray box telling me to install Java.

Default Ubuntu Firefox plugins:
[IMG]http://i50.tinypic.com/33u682u.jpg[/IMG]

Plugins detected by SeaMonkey. Note that there is no Java:
[IMG]http://i50.tinypic.com/352lwzc.jpg[/IMG]

Ideas??






.

---

### Post by nanotube on 2010-01-17
what's your java plugin package name?

what do you see in /usr/lib/mozilla/plugins (anything java?)

fwiw, i have seamonkey installed from the ubuntuzilla repo, and it's seeing my java plugin just fine... of course, a link to it is showing up in /usr/lib/mozilla/plugins, which may not be the case for you...

---

### Post by Uncle Spellbinder on 2010-01-17
Everything in /usr/lib/mozilla/plugins:

```
flashplugin-alternative.so
librhythmbox-itms-detection-plugin.so
libtotem-cone-plugin.so
libtotem-gmp-plugin.so
libtotem-mully-plugin.so
libtotem-narrowspace-plugin.so
nppdf.so
```

But, as you can see by the image above, Firefox has Java listed. And I have all the necessary Java installed. No issues using Facebook's Java photo uploader in Firefox. SeaMonkey shows the "add plugin waning".

Very confused. 

Nothing left to add as far as Java is concerned:
```
unclespellbinder@wombat:~$ sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin sun-java6-fonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jdk is already the newest version.
sun-java6-plugin is already the newest version.
sun-java6-fonts is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
unclespellbinder@wombat:~$
```

---

### Post by nanotube on 2010-01-17
well well, apparently on karmic the sun-java6-plugin package does not install the alternative link in /usr/lib/mozilla, but only in /usr/lib/xulrunner-addons. this really is a bug that needs to be filed on launchpad, since /usr/lib/mozilla/plugins is an officially sanctioned directory where firefox should look for plugins. 

try an 'ls -al /usr/lib/xulrunner-addons/plugins' or 'ls -al /usr/lib/xulrunner-1.9/plugins/' to see if the java link is there.

to fix this, either manually place a link to the plugin in /usr/lib/mozilla/plugins, or go all fancy and actually use update-alternatives to install an alternative location. the latter would look something like:
```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun-1.6.0.15/jre/plugin/i386/ns7/libjavaplugin_oji.so 50
```

---

### Post by nanotube on 2010-01-17
just made a comment on this launchpad bug with this problem:

[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/269136](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/269136)

no idea if anyone's going to pick up on it - it's an old bug, but since it's really right along the same lines, i figured it's better not to start a new one... but i may be wrong.

---

### Post by Uncle Spellbinder on 2010-01-18
> **nanotube said:**
> Try an 'ls -al /usr/lib/xulrunner-addons/plugins' or 'ls -al /usr/lib/xulrunner-1.9/plugins/' to see if the java link is there.

Ok here's what I get...

```
unclespellbinder@wombat:~$ ls -al /usr/lib/xulrunner-1.9/plugins/
ls: cannot access /usr/lib/xulrunner-1.9/plugins/: No such file or directory
unclespellbinder@wombat:~$ ls -al /usr/lib/xulrunner-addons/plugins
total 8
drwxr-xr-x 2 root root 4096 2010-01-10 13:25 .
drwxr-xr-x 4 root root 4096 2009-10-28 16:58 ..
lrwxrwxrwx 1 root root   46 2010-01-10 13:16 flashplugin-alternative.so -> /etc/alternatives/xulrunner-addons-flashplugin
lrwxrwxrwx 1 root root   45 2010-01-10 13:25 libjavaplugin.so -> /etc/alternatives/xulrunner-1.9-javaplugin.so
lrwxrwxrwx 1 root root   45 2010-01-10 11:01 libtotem-cone-plugin.so -> ../../mozilla/plugins/libtotem-cone-plugin.so
lrwxrwxrwx 1 root root   44 2010-01-10 11:01 libtotem-gmp-plugin.so -> ../../mozilla/plugins/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   46 2010-01-10 11:01 libtotem-mully-plugin.so -> ../../mozilla/plugins/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   52 2010-01-10 11:01 libtotem-narrowspace-plugin.so -> ../../mozilla/plugins/libtotem-narrowspace-plugin.so
unclespellbinder@wombat:~$
```

Seems Java is installed in */usr/lib/xulrunner-addons/plugins*. I tried opening that folder to make a link for copying 
to */usr/lib/mozilla/plugins* to no avail. The option to "make link" is grayed out.

[IMG]http://i50.tinypic.com/oixkj6.jpg[/IMG]

Never really understood the whole symbolic link thing. Could use some help on that.





.

---

### Post by Sleepy-zz-John on 2010-01-18
> **nanotube said:**
> 
```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun-1.6.0.15/jre/plugin/i386/ns7/libjavaplugin_oji.so 50
```
Same trouble as Uncle Spellbinder;  lost my Java in 2.0.2  when I upgraded from 1.1.17 in Karmic, whilst Java continues to work fine in FF 3.5.7.   Tried your above code and it appeared to run without error,  but hasn't fixed the problem.   
```
:$ ls /usr/lib/xulrunner-addons/plugins
flashplugin-alternative.so  libtotem-gmp-plugin.so
libjavaplugin.so            libtotem-mully-plugin.so
libtotem-cone-plugin.so     libtotem-narrowspace-plugin.so 
```
Also tried Bryce Nesbitt's workaround from bug/269136
```
john@jaspir:/usr/lib/mozilla/plugins$ sudo ln -s /usr/lib/xulrunner-addons/plugins/libjavaplugin.so
[sudo] password for john: 
ln: creating symbolic link `./libjavaplugin.so': File exists 
```
So since the symbolic link already exists,  I'm not clear now why it isn't working.
Any suggestions?

---

### Post by nanotube on 2010-01-18
> **Uncle Spellbinder said:**
> Ok here's what I get...

```
unclespellbinder@wombat:~$ ls -al /usr/lib/xulrunner-1.9/plugins/
ls: cannot access /usr/lib/xulrunner-1.9/plugins/: No such file or directory
unclespellbinder@wombat:~$ ls -al /usr/lib/xulrunner-addons/plugins
total 8
drwxr-xr-x 2 root root 4096 2010-01-10 13:25 .
drwxr-xr-x 4 root root 4096 2009-10-28 16:58 ..
lrwxrwxrwx 1 root root   46 2010-01-10 13:16 flashplugin-alternative.so -> /etc/alternatives/xulrunner-addons-flashplugin
lrwxrwxrwx 1 root root   45 2010-01-10 13:25 libjavaplugin.so -> /etc/alternatives/xulrunner-1.9-javaplugin.so
lrwxrwxrwx 1 root root   45 2010-01-10 11:01 libtotem-cone-plugin.so -> ../../mozilla/plugins/libtotem-cone-plugin.so
lrwxrwxrwx 1 root root   44 2010-01-10 11:01 libtotem-gmp-plugin.so -> ../../mozilla/plugins/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   46 2010-01-10 11:01 libtotem-mully-plugin.so -> ../../mozilla/plugins/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   52 2010-01-10 11:01 libtotem-narrowspace-plugin.so -> ../../mozilla/plugins/libtotem-narrowspace-plugin.so
unclespellbinder@wombat:~$
```

Seems Java is installed in */usr/lib/xulrunner-addons/plugins*. I tried opening that folder to make a link for copying 
to */usr/lib/mozilla/plugins* to no avail. The option to "make link" is grayed out.

[IMG]http://i50.tinypic.com/oixkj6.jpg[/IMG]

Never really understood the whole symbolic link thing. Could use some help on that.

.

try the update-alternatives command i posted above.

or if you really want to just make a link, you have to do it with sudo, because files in /usr/lib are owned by root (that's why the make link is grayed out for you - you're trying to create a symlink in a root-owned directory, which you don't have permission to do).

to make a manual link, run
```
sudo ln -s /usr/lib/xulrunner-addons/plugins/libjavaplugin.so /usr/lib/mozilla/plugins/libjavaplugin.so
```

---

### Post by nanotube on 2010-01-18
> **Sleepy-zz-John said:**
> Same trouble as Uncle Spellbinder;  lost my Java in 2.0.2  when I upgraded from 1.1.17 in Karmic, whilst Java continues to work fine in FF 3.5.7.   Tried your above code and it appeared to run without error,  but hasn't fixed the problem.   
```
:$ ls /usr/lib/xulrunner-addons/plugins
flashplugin-alternative.so  libtotem-gmp-plugin.so
libjavaplugin.so            libtotem-mully-plugin.so
libtotem-cone-plugin.so     libtotem-narrowspace-plugin.so 
```
Also tried Bryce Nesbitt's workaround from bug/269136
```
john@jaspir:/usr/lib/mozilla/plugins$ sudo ln -s /usr/lib/xulrunner-addons/plugins/libjavaplugin.so
[sudo] password for john: 
ln: creating symbolic link `./libjavaplugin.so': File exists 
```
So since the symbolic link already exists,  I'm not clear now why it isn't working.
Any suggestions?

the update-alternatives command should have installed a link in /usr/lib/mozilla/plugins. so, try 
```
ls -al /usr/lib/mozilla/plugins
``` and you should see a java plugin in there.

then try /restarting/ seamonkey, and go to about:plugins to see if it's seeing the java plugin.

---

### Post by Uncle Spellbinder on 2010-01-18
> **nanotube said:**
> to make a manual link, run
```
sudo ln -s /usr/lib/xulrunner-addons/plugins/libjavaplugin.so /usr/lib/mozilla/plugins/libjavaplugin.so
```

That worked. Just tested the Java photo uploader at Facebook, worked like a charm.

Thanks, nanotube. Really appreciate your help!

---

### Post by nanotube on 2010-01-18
> **Uncle Spellbinder said:**
> That worked. Just tested the Java photo uploader at Facebook, worked like a charm.

Thanks, nanotube. Really appreciate your help!

cool - no problem :)

---

### Post by nanotube on 2010-01-18
just for future reference, the 'proper' way to add the java plugin link using update-alternatives is:
```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
```

though functionally, a manual symlink does the same thing. the difference is that the alternatives system plays nicely if you happen to install another package providing the java plugin...

---

### Post by Sleepy-zz-John on 2010-01-18
> **nanotube said:**
> the update-alternatives command should have installed a link in /usr/lib/mozilla/plugins. so, try 
```
ls -al /usr/lib/mozilla/plugins
``` and you should see a java plugin in there.
Yes, I do
```
lrwxrwxrwx 1 root root     39 2009-11-20 19:35 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so 
```
> 
then try /restarting/ seamonkey, and go to about plugins to see if it's seeing the java plugin.
No, it isn't :(
There's Default Plugin
    File name: libnullplugin.so
Then there's a long list of VLC Multimedia Plugin (compatible Totem 2.28.2)
Then a long list of Windows Media Player Plug-in 10 (compatible; Totem)
Then DivX® Web Player
Then some QuickTime Plug-in 7.2.0
and finally a couple of Shockwave Flash

Your direct link code: ```
 sudo ln -s /usr/lib/xulrunner-addons/plugins/libjavaplugin.so /usr/lib/mozilla/plugins/libjavaplugin.so 
```
only returns:
```
 ln: creating symbolic link `./libjavaplugin.so': File exists 
``` the same as I tried previously.
Still trying to figure out why it's working for Uncle Spellbinder,and not for me.  My configuration must clearly be different somewhere #-o

---

### Post by nanotube on 2010-01-18
Sleepy-zz-John:

ok, try removing the alternative:
```
sudo update-alternatives --remove-all mozilla-javaplugin.so
```

then install again (this time using a different java .so from the earlier one):

```
sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so 50
```

---

### Post by Sleepy-zz-John on 2010-01-19
Oh wonderful!   Many thanks nanotube - that works fine and my SeaMonkey's Java is back in business again.

---

### Post by nanotube on 2010-01-19
> **Sleepy-zz-John said:**
> Oh wonderful!   Many thanks nanotube - that works fine and my SeaMonkey's Java is back in business again.

super! :)

---

### Post by nanotube on 2010-01-19
for reference: i posted a new bug report about this problem, with greater details and a patch, here:
[https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/509727)

---

### Post by nanotube on 2010-01-20
Sleepy-zz-John,Uncle Spellbinder:
by the way, it would probably be helpful if you go to that launchpad bug and post a 'me too' message, to help bring this to the attention of the packagers.

---

### Post by Sleepy-zz-John on 2010-01-20
OK, done!  Good support there.    Thanks again nanotube

---

### Post by nanotube on 2010-01-20
> **Sleepy-zz-John said:**
> OK, done!  Good support there.    Thanks again nanotube

i saw that - excellent, thanks a lot :) hopefully they'll get that fix in soon.

---

