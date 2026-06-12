---
title: "Is there a way to automatically create root's crontab?"
date: 2009-08-20
forum: Server Platforms
---

### Post by PryGuy on 2009-08-20
Good day, my old friends! :)
I make a server postinstall script that copies my config files and all... I want to create an empty crontab for root if needed. My solution is very awkward. Here is it:```
createCrontab() {
if [ ! -f /var/spool/cron/crontabs/root ]; then
sudo EDITOR=vi crontab -e 2>/dev/null <<END-OF-INPUT
:g/hello/s//bye/g
:w
:q!
END-OF-INPUT
fi
}
```If you have any idea how to handle it in a more civilized way - please tell me! Thank you in advance!

---

### Post by koenn on 2009-08-20
don't really understand what you're trying to do.

There _is_ a systemwide crontab : /etc/crontab. 
Normally you'd just add to that, no ?

if you just want to make an empty file (from a script), you'd go

```
touch /path/to/file
```. That creates a file if it doesn't exist yet ' if it exists, it just modifies the 'last accessed' date)

you can also do ```
echo > /path/to/file
``` this creates an empty file, overwriting /path/to/file if it already exists

to add text to a file, you'd go something like
```

cat >>path/to/file <<EOF

blah
blah blah
bla...

EOF

```

---

### Post by PryGuy on 2009-08-21
> **koenn said:**
> if you just want to make an empty file (from a script), you'd go

```
touch /path/to/file
```. That creates a file if it doesn't exist yet ' if it exists, it just modifies the 'last accessed' date)Touch creates REALLY empty file with zero length. Can you explain me how to add anything with sed to an empty file?> you can also do ```
echo > /path/to/file
``` this creates an empty file, overwriting /path/to/file if it already existsThis doesn't work with sudo.> to add text to a file, you'd go something like
```

cat >>path/to/file <<EOF

blah
blah blah
bla...

EOF

```This doesn't work with sudo also...

---

### Post by koenn on 2009-08-22
> **PryGuy said:**
> Touch creates REALLY empty file with zero length. Can you explain me how to add anything with sed to an empty file?
- you said you *want* an empty file
- it's beyond me why you'd use sed to add text an empty file, and I don't know how to do that anyway. 


> **PryGuy said:**
> This doesn't work with sudo.This doesn't work with sudo also...
so why not run the entire script with sudo ?

---

