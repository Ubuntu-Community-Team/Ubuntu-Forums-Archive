---
title: "/etc/apache2"
date: 2012-02-08
forum: Server Platforms
---

### Post by puf on 2012-02-08
Hi all. I did the stupidest thing ever! I rm-rf my apache2 directory and now when i try to install apache2 or lamp it says everything is okay but there is no apache2 dir. What can i do to fix it. Btw i'm with Ubuntu Server 11.10. Thank you.

---

### Post by Lars Noodén on 2012-02-08
If you're using Apache 2.2, then you could try the following:

```

sudo apt-get --reinstall install apache2.2-common

```

That should replace any missing configuration files.

---

### Post by puf on 2012-02-08
sudo /etc/init.d/apache2 start
.: 51: Can't open /etc/apache2/envvars

another error...

---

### Post by Lars Noodén on 2012-02-08
I get the same thing.  According to dpkg, it should belong to the package apache2.2-common, but re-installing had no effect.  I'm not sure of a way around.  It sure looks like a bug.

---

### Post by puf on 2012-02-08
i made to reinstall apache and get it working now i cant enable my public_html folder, i do chmode to the folder with 775 and try to 
```

cd /etc/apache2/mods-enabled
sudo ln -s ../mods-available/userdir.load
sudo ln -s ../mods-available/userdir.conf

```

but it's still give me

**Forbidden**

 You don't have permission to access /~sublime on this server.

This apache will kill me! :D

---

### Post by Lars Noodén on 2012-02-08
Try enabling the module using [a2enmod](http://manpages.ubuntu.com/manpages/oneiric/en/man8/a2enmod.8.html):

```

sudo a2enmod userdir

```

Also make sure to reload your server configuration after doing so.

---

### Post by puf on 2012-02-08
its says that module is already enabled... maybe something with permissions can be done

---

### Post by Lars Noodén on 2012-02-08
You can open up a terminal and have the error messages running realtime.  It might give more details.

```

tail -f /var/log/apache2/error.log

```

But mod_userdir should work out of the box.  Are your home directory and public_html set to 755 or 775?

---

### Post by puf on 2012-02-08
[Wed Feb 08 21:13:39 2012] [error] [client MY IP HERE] (13)Permission denied                                                                                       : access to /~sublime denied

Down errors are same, i think i must set my HOME directory to 755 or 775 but i dont know how to do that, i cant with chmod...

---

### Post by puf on 2012-02-08
i tried to chmod -R 755 or just chmod 755 * but i still cant open public_html in browser.... or i just dont know how to change permission for home directory :(

---

### Post by SeijiSensei on 2012-02-08
Try this:

```

cd /home
sudo chmod 711 sublime
cd sublime
sudo chmod 755 public_html
sudo chmod -R 644 public_html/*
cd /home
sudo chown -R sublime.sublime sublime

```

I used sudo in case you managed to create a file or directory that wasn't actually owned by the sublime user.

711 permissions let anyone list the contents of a directory, which is required to navigate to a directory below it.  I then made your public_html directory readable and listable by anyone; the following command applies the same permissions to any files and directories below /home/sublime/public_html.

Finally, just for good measure, I forced all files in /home/sublime to be owned by user sublime in group sublime.  (The -R switch to chown or chmod "recurses" down the directory tree and changes the permissions on all files and directories starting with /home/sublime.)

---

