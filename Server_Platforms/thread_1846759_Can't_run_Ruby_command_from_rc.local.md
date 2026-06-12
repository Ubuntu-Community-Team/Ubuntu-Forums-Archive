---
title: "Can't run Ruby command from rc.local"
date: 2011-09-19
forum: Server Platforms
---

### Post by datalus on 2011-09-19
Forgive an Ubuntu, but we can't seem to find a solution for this.
I need to run a Ruby script on boot, so we are trying to add the following commands to rc.local:
 
```
 
cd /var/www/Snorby
ruby script/delayed_job start

```
 
It works fine when I run those two commands from a shell, but not from rc.local. Everything else in rc.local works. 
 
The script has to run out of the Snorby directory due to some relative paths in it, so I have to use the cd command first, but I'm not sure if this actually does anything here? Here is the output when I run it manually:
 
```
$sudo ruby script/delayed_job start
Jammit Warning: Asset compression disabled -- Java unavailable.
DataObjects::URI.new with arguments is deprecated, use a Hash of URI components (/var/www/Snorby/snorby_cas_authenticatable.git/ruby/1.9.1/gems/dm-do-adapter-1.1.0/lib/dm-do-adapter/adapter.rb:231:in `new')
delayed_job: process with pid 1662 started.
```
 
If I redirect the output of the command with >> snorby.log for the rc.local script, I only get this in the log file:
 
```
/etc/rc.local: 24: ruby: not found
```

I'm sure I'm missing something a little more elemental with Linux
commands, but any help or direction is
appreciated regardless.

---

### Post by &#1052;&#1086;&#1093;&#1085;&#1072;&#1090;&#1099;&#1081; on 2011-09-22
Maybe you need to add full path to ruby binary -> /usr/bin/ruby

---

### Post by datalus on 2011-09-22
Thanks, I'll give that a shot. Had to search for it, but it looks like the full path is actually -> /usr/local/bin/ruby

---

### Post by datalus on 2011-09-22
That did the trick &#1052;&#1086;&#1093;&#1085;&#1072;&#1090;&#1099;&#1081;! The full line is now:
 

```
cd /var/www/Snorby; /usr/local/bin/ruby script/delayed_job start
```
 

Works like a charm on boot time. Thanks again.

---

