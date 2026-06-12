---
title: "firestudio project?"
date: 2010-03-03
forum: Ubuntu Studio
---

### Post by deankovell on 2010-03-03
Hello everyone,
   I was wondering if anyone has gotten the firestudio project to work with ffado. It has an entry in the config files from the ffado svn download, but I haven't gotten anything going yet. If it can be made to work, I'll keep trying, but if not , I'll wait a couple months before continuing.  I was thinking that maybe firestudio support is  something the ffado people are  working on, but it's not ready yet? 

Thanks for any input.
edit:
If anyone's interested
a week later and It's working!!!!! 
halfway.
I have the mic inputs working, but no output sound to get output I have to use the built in soundcard with the command in qjackctl   setup/ options/ execute script on startup

" alsa_out -d hw:0 -c 6" 

I figured out how to get it working from this guys website, although you no longer need to change the config files in ffado the way he did-- they're now now included in the ffado-svn. just compile it with "sudo scons PREFIX=/usr ENABLE_DICE=yes ENABLE_OPTIMIZATIONS=True"

[http://](http://)[bobhamil.com/PreSonus/]("http://bobhamil.com/PreSonus/")

If someone else is having trouble with this, post a comment and I'll try to help. but hopefully someone more qualified will help too.

---

### Post by MroFo on 2010-03-13
Did you get any errors or warnings when trying to compile with 

```
sudo scons PREFIX=/usr ENABLE_DICE=yes ENABLE_OPTIMIZATIONS=True
```  ?

I ended up running into this, myself.

```
/usr/local/ffado/libffado$ sudo scons PREFIX=/usr ENABLE_DICE=yes ENABLE_OPTIMIZATIONS=True
[sudo] password for USER: 
scons: Reading SConscript files ...

scons: warning: The Options class is deprecated; use the Variables class instead.
File "/usr/local/ffado/libffado/SConstruct", line 38, in <module>

scons: warning: The BoolOption() function is deprecated; use the BoolVariable() function instead.
File "/usr/local/ffado/libffado/SConstruct", line 43, in <module>

scons: warning: The PathOption() function is deprecated; use the PathVariable() function instead.
File "/usr/local/ffado/libffado/SConstruct", line 45, in <module>

scons: warning: The EnumOption() function is deprecated; use the EnumVariable() function instead.
File "/usr/local/ffado/libffado/SConstruct", line 73, in <module>
Checking for a working C-compiler yes
Checking for a working C++-compiler yes
Checking for pkg-config (at least version 0.0.0)... yes
Checking for C header file expat.h... yes
Checking for XML_ExpatVersion() in C library expat... yes
/usr/local/ffado/libffado/admin/pkgconfig.py:80: DeprecationWarning: os.popen2 is deprecated.  Use the subprocess module.
  out = os.popen2( "pkg-config --cflags --libs %s" % name )[1]
Checking for libraw1394 (1.3.0 or higher)... 	yes
Checking for dbus-1 (1.0 or higher)... 	no
Checking for libxml++-2.6 (2.13.0 or higher)... 	yes
Checking for libiec61883 (1.1.0 or higher)... 	yes

(At least) One of the dependencies is missing. I can't go on without it, please
install the needed packages for each of the lines saying "no".
(Remember to also install the *-devel packages!)

And remember to remove the cache with "rm -Rf .sconsign.dblite cache" so the
results above get rechecked.
```

I screwed around with SConstruct some and I either made progress or bricked it even further haha. I'm getting this currently...


```
USER@SYSTEM:/usr/local/ffado/libffado$ sudo scons PREFIX=/usr ENABLE_DICE=yes ENABLE_OPTIMIZATIONS=True
scons: Reading SConscript files ...
AttributeError: Variables instance has no attribute 'AddOptions':
  File "/usr/local/ffado/libffado/SConstruct", line 40:
    opts.AddOptions(
```

I added a closing parentheses to 'AddOptions(' to make it 'AddOptions()' bringing me to here...

```
USER@SYSTEM:/usr/local/ffado/libffado$ sudo scons PREFIX=/usr ENABLE_DICE=yes ENABLE_OPTIMIZATIONS=True
scons: Reading SConscript files ...
  File "/usr/local/ffado/libffado/SConstruct", line 41

    BoolOption( "DEBUG", """\

   ^

IndentationError: unexpected indent

andrew@daedalus:/usr/local/ffado/libffado$ sudo scons PREFIX=/usr ENABLE_DICE=yes ENABLE_OPTIMIZATIONS=True
scons: Reading SConscript files ...
  File "/usr/local/ffado/libffado/SConstruct", line 41

    BoolOption( "DEBUG", """\

   ^

IndentationError: unexpected indent
```

I am now currently out of ideas. Anything you can tell me about your struggle to get the Firestudio Project to function even halfway decent would be much obliged!

---

### Post by deankovell on 2010-03-16
MroFo,
   I just recompiled to see if I got the same warnings, and I did, but everything still works. I don't think those warnings are a big deal. It failed because of a dependency. It says that dbus isn't installed. install that and start over.  

```
sudo rm -Rf .sconsign.dblite cache

```also, I would change the stuff you changed back to how it was
and then compile again
```
sudo scons PREFIX=/usr ENABLE_DICE=yes ENABLE_OPTIMIZATIONS=True
```
It might be a good idea to add this to it.
```
sudo scons PREFIX=/usr DEBUG=yes ENABLE_DICE=yes ENABLE_OPTIMIZATIONS=True 
```
after just run 
```
sudo scons install
```to test the thing turn it on and then run the command
```
ffado-dbus-server
```Once you get it working, you're also going to have to compile jack from source with firewire enabled. You're also going to have to look into which firewire modules to load. my advice on that would be to google it and start another thread if you don't figure that part out. It was confusing for me and I'll probably lead you astray. but I'm pretty sure the right modules are going to need to be loaded before ffado-dbus-derver will work right.



Hope this helps.

---

