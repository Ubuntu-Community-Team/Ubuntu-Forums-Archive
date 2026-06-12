---
title: "Configuration Error in Eclipse"
date: 2011-05-18
forum: Server Platforms
---

### Post by thoufiq on 2011-05-18
Hello All,
I have googlled and get these commands to install extracted .tar.gz file such as  ./configure, make and make install, after extraction it becomes a directory called eclipse. But when i giving these commands also  i got error like this
[B][COLOR=red]
~/usr/local/opt$ ls
eclipse eclipse-php-helious-linux-gtk.tar.gz

~/usr/local/opt/eclipse$ ls
about_files; artifacts.xml; dropins; eclipse.ini; features;  libcairo-swt.so; p2 readme; about.html; configuration; eclipse;  epl-v10.html; icon.xml; notice.html; plugins
[/COLOR][/B]
[B][COLOR=red]~/usr/local/opt/eclipse$ ./configre
-bash: ./configure; No such file or directory

~/usr/local/opt/eclipse$ make
make: ***No targets specified and no makefile found. Stop.

~/usr/local/opt/eclipse$ make install
make: ***No rule to make target 'install'. Stop.[/COLOR][/B]

Is there any mistake i did? If so pls let me know.


Thanks

---

### Post by GregBrannon on 2011-05-18
I suppose it's possible to download the Eclipse source code, but it is typically distributed as a Java executable.  I believe that's what you have, and you're trying to compile it which won't work, resulting in the errors you've received.

Simply unpack the distribution into the desired directory with the folder structure preserved and run the resulting eclipse executable.  The unpack process will create an 'eclipse' folder in the location you choose, so no need to create an eclipse target folder yourself.

---

### Post by thoufiq on 2011-05-19
> **GregBrannon said:**
> I suppose it's possible to download the Eclipse source code, but it is typically distributed as a Java executable.  I believe that's what you have, and you're trying to compile it which won't work, resulting in the errors you've received.

Simply unpack the distribution into the desired directory with the folder structure preserved and run the resulting eclipse executable.  The unpack process will create an 'eclipse' folder in the location you choose, so no need to create an eclipse target folder yourself.

Hello Greg,
Already, i had extracted that .tar.gz file and  also the directory named 'eclipse' has been created automatically after  extraction but while running that extracted directory 'eclipse' using  commands such as ./eclipse and eclipse &. I got segmentation fault  error as i posted in other threads. Is there any problem with owner and group  permissions. Below i have pasted the result..

[COLOR=red]~/usr/local/opt$ ls -l
total 290652
drwxrwsr-x 9 libuuid users   4096      2010-06-17 21:46 eclipse
-rw-r--r-- 1 sam-osm sam-osm 149897197 2011-05-14 14:40 eclipse-php-helios-linux-gtk.tar.gz[/COLOR]

In the above result, the eclipse directory have owner as libuuid and  group as users but the .tar.gz file has owner as sam-osm and also group  as sam-osm. Should i change the owner and group name. Is this the only  cause for the segmentation fault error.

Thanks

---

