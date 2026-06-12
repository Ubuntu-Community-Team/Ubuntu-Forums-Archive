---
title: "aptitude error - setting up libgtk2.0-0 (2.24.8-0ubuntu2)"
date: 2011-12-02
forum: Ubuntu +1 (Precise Pangolin)(Closed)
---

### Post by paul_in_london on 2011-12-02
libgtk2.0-0 seems to have been upgraded ok:

```
paul@precise-64:~$ apt-cache policy libgtk2.0-0
libgtk2.0-0:
  Installed: 2.24.8-0ubuntu2
  Candidate: 2.24.8-0ubuntu2
  Version table:
 *** 2.24.8-0ubuntu2 0
        500 http://archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
        100 /var/lib/dpkg/status
paul@precise-64:~$
```

but I did get this error:

```
Setting up libgtk2.0-0 (2.24.8-0ubuntu2) ...
Cannot load module /usr/lib/gtk-2.0/2.10.0/immodules/*.so: /usr/lib/gtk-2.0/2.10.0/immodules/*.so: cannot open shared object file: No such file or directory
/usr/lib/gtk-2.0/2.10.0/immodules/*.so does not export GTK+ IM module API: /usr/lib/gtk-2.0/2.10.0/immodules/*.so: cannot open shared object file: No such file or directory
Setting up gtk2-engines-pixbuf (2.24.8-0ubuntu2) ...
Setting up libgail18 (2.24.8-0ubuntu2) ...
Setting up libnautilus-extension1 (1:3.2.1-0ubuntu5) ...
Setting up nautilus-data (1:3.2.1-0ubuntu5) ...
Setting up nautilus (1:3.2.1-0ubuntu5) ...
Setting up libprotobuf7 (2.4.1-1ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 0 KiB

                                         
Current status: 2 updates [-7].
paul@precise-64:~$
```

From a quick google it doesn't seem to be much of a big deal (and it isn't ubuntu-specific). See this page for example:

[http://forums.fedoraforum.org/showthread.php?t=267511](http://forums.fedoraforum.org/showthread.php?t=267511)

---

### Post by dino99 on 2011-12-02
i have this "immodules" warning since ages, but cant find a workaround.

---

### Post by paul_in_london on 2011-12-02
> **dino99 said:**
> i have this "immodules" warning since ages, but cant find a workaround.

Thanks for the quick reply. I can't remember if I've seen this "immodules" warning before actually. I'd have to read more about it.

---

### Post by paul_in_london on 2011-12-02
Now upgraded to 2.24.8-0ubuntu3, but still the same error (haven't looked into it any further yet):

```
paul@precise-64:~$ sudo aptitude safe-upgrade
Resolving dependencies...
The following packages will be upgraded:
  dpkg gtk2-engines-pixbuf libgail18 libgtk2.0-0
The following packages are RECOMMENDED but will NOT be installed:
  libgtk2.0-bin libgtk2.0-bin
4 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 4,653 kB of archives. After unpacking 1,024 B will be used.
Do you want to continue? [Y/n/?] Y
Get: 1 http://archive.ubuntu.com/ubuntu/ precise/main dpkg amd64 1.16.1.2ubuntu2 [1,835 kB]
Get: 2 http://archive.ubuntu.com/ubuntu/ precise/universe gtk2-engines-pixbuf amd64 2.24.8-0ubuntu3 [128 kB]
Get: 3 http://archive.ubuntu.com/ubuntu/ precise/main libgail18 amd64 2.24.8-0ubuntu3 [16.6 kB]
Get: 4 http://archive.ubuntu.com/ubuntu/ precise/main libgtk2.0-0 amd64 2.24.8-0ubuntu3 [2,673 kB]
Fetched 4,653 kB in 3s (1,355 kB/s)
(Reading database ... 214605 files and directories currently installed.)
Preparing to replace dpkg 1.16.1.2ubuntu1 (using .../dpkg_1.16.1.2ubuntu2_amd64.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
Setting up dpkg (1.16.1.2ubuntu2) ...
(Reading database ... 214605 files and directories currently installed.)
Preparing to replace gtk2-engines-pixbuf 2.24.8-0ubuntu2 (using .../gtk2-engines-pixbuf_2.24.8-0ubuntu3_amd64.deb) ...
Unpacking replacement gtk2-engines-pixbuf ...
Preparing to replace libgail18 2.24.8-0ubuntu2 (using .../libgail18_2.24.8-0ubuntu3_amd64.deb) ...
Unpacking replacement libgail18 ...
Preparing to replace libgtk2.0-0 2.24.8-0ubuntu2 (using .../libgtk2.0-0_2.24.8-0ubuntu3_amd64.deb) ...
Unpacking replacement libgtk2.0-0 ...
Setting up libgtk2.0-0 (2.24.8-0ubuntu3) ...
Cannot load module /usr/lib/gtk-2.0/2.10.0/immodules/*.so: /usr/lib/gtk-2.0/2.10.0/immodules/*.so: cannot open shared object file: No such file or directory
/usr/lib/gtk-2.0/2.10.0/immodules/*.so does not export GTK+ IM module API: /usr/lib/gtk-2.0/2.10.0/immodules/*.so: cannot open shared object file: No such file or directory
Setting up gtk2-engines-pixbuf (2.24.8-0ubuntu3) ...
Setting up libgail18 (2.24.8-0ubuntu3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
localepurge: Disk space freed in /usr/share/locale: 3916 KiB
localepurge: Disk space freed in /usr/share/man: 268 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB

Total disk space freed by localepurge: 4184 KiB

                                         
Current status: 2 updates [-4].
paul@precise-64:~$
```

---

### Post by mc4man on 2011-12-02
It's not an 'error', just a statement. Likely comes from a postinst script on 64 bit installs.

---

### Post by paul_in_london on 2011-12-02
> **mc4man said:**
> It's not an 'error', just a statement. Likely comes from a postinst script on 64 bit installs.

Yep, I was using the term a bit loosely. This seemed to be what a post on the Fedora page was suggesting (see my original post - just one of the first pages I hit when I looked up the output message).

---

### Post by mc4man on 2011-12-02
If you wanted to take a look just browse to /var/cache/apt/archives & right click on the libgtk2.0-0 .deb > open with > archive manager
(open, not extract

Then browse to Debian & open postinst in a text editor

---

### Post by paul_in_london on 2011-12-02
> **mc4man said:**
> If you wanted to take a look just browse to /var/cache/apt/archives & right click on the libgtk2.0-0 .deb > open with > archive manager
(open, not extract

Then browse to Debian & open postinst in a text editor

Thanks. Ok, this was the bit at the end of the postinst script:

```
# Also handle the initial installation
if [ -d /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules ] \
   || [ -d /usr/lib/gtk-2.0/2.10.0/immodules ]
then
     /usr/lib/x86_64-linux-gnu/libgtk2.0-0/gtk-query-immodules-2.0 \
         /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/*.so \
         /usr/lib/gtk-2.0/2.10.0/immodules/*.so \
     > /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/gtk.immodules || true
fi
```

so no harm no foul in A || B if A "fails". My /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/gtk.immodules currently contains these entries:

```
paul@precise-64:~$ cat /usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/gtk.immodules
# GTK+ Input Method Modules file
# Automatically generated file, do not edit
# Created by /usr/lib/x86_64-linux-gnu/libgtk2.0-0/gtk-query-immodules-2.0 from gtk+-2.24.8
#
"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-am-et.so" 
"am_et" "Amharic (EZ+)" "gtk20" "/usr/share/locale" "am" 

"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-cedilla.so" 
"cedilla" "Cedilla" "gtk20" "/usr/share/locale" "az:ca:co:fr:gv:oc:pt:sq:tr:wa" 

"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-cyrillic-translit.so" 
"cyrillic_translit" "Cyrillic (Transliterated)" "gtk20" "/usr/share/locale" "" 

"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-inuktitut.so" 
"inuktitut" "Inuktitut (Transliterated)" "gtk20" "/usr/share/locale" "iu" 

"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ipa.so" 
"ipa" "IPA" "gtk20" "/usr/share/locale" "" 

"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-multipress.so" 
"multipress" "Multipress" "gtk20" "" "" 

"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-thai.so" 
"thai" "Thai-Lao" "gtk20" "/usr/share/locale" "lo:th" 

"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ti-er.so" 
"ti_er" "Tigrigna-Eritrean (EZ+)" "gtk20" "/usr/share/locale" "ti" 

"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ti-et.so" 
"ti_et" "Tigrigna-Ethiopian (EZ+)" "gtk20" "/usr/share/locale" "ti" 

"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-viqr.so" 
"viqr" "Vietnamese (VIQR)" "gtk20" "/usr/share/locale" "" 

"/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-xim.so" 
"xim" "X Input Method" "gtk20" "/usr/share/locale" "ko:ja:th:zh" 

```

which makes me wonder if that redirect in the postinst script is supposed to be an append (">>" instead of ">").

EDIT: I know "fails" isn't really the right word here.

I remember, btw, when dpkg or apt or aptitude was hanging at some point and having to remove /var/lib/dpkg/info/<some_package>.* to get things going again.

---

### Post by paul_in_london on 2011-12-02
> **mc4man said:**
> It's not an 'error', just a statement. Likely comes from a postinst script on 64 bit installs.

Forgot to say I think I saw the same thing when I updated a 32 bit PP install earlier on my other box.

---

