---
title: "Installing modules in drupal"
date: 2010-09-22
forum: Server Platforms
---

### Post by blairm on 2010-09-22
Hi,

Have installed Drupal6 and things seem to be going smoothly, but I'm not sure how to install additional modules.

The instructions on the drupal site say: "The modules folder at the top level of your Drupal installation is reserved for Drupal core modules (the ones that come with the original download of Drupal). So, you should generally create a sites/all/modules/ directory and put uploaded modules there. 

However,there doesn't appear to be a modules folder at the top level - or anywhere else.

So I'm not sure where I should be creating this folder for downloaded modules: should there be an all folder within the sites folder, and a modules folder within that? 
The absence of the modules folder mentioned in documentation is making me wonder if things are different in ubuntu.

After several failed attempts to get drupal going in past I don't really want to proceed without knowing for sure in case I ruin the installation.

Installed via synaptic and it's in /etc. In case it helps, layout of files is:
```

                            .drupal6 folder
                                  |
                                  |
                              6 folder
                                  | 
    ______________________________|_________________________________
    |                             |                    |           |  
    |                             |                    |           | 
 profiles folder              sites folder        apache.conf  htaccess
    |                             |
    |                             |  
 default folder               default folder
    |                             |
    |                      _______|_______________________________       |
 default.profile           |                     |                |
                           |                     |                | 
                        files folder(empty)  dbconfig.php  settings.php 





```
Any advice gratefully received,

Blair

---

### Post by lykwydchykyn on 2010-09-22
My situation might be a little different because I have multiple sites on my install, but under sites/all I created a "modules" folder and unzip them there.

---

### Post by bkline on 2010-09-27
> **lykwydchykyn said:**
> My situation might be a little different because I have multiple sites on my install, but under sites/all I created a "modules" folder and unzip them there.

This does not address the problem reported by the OP: there is no subdirectory named "all" under the "sites" directory in the Ubuntu installation for the drupal6 package.  The problem is a specific example of a general dilemma encountered with a number of Ubuntu packages: there is no documentation explaining what you can modify in the Ubuntu installation of a package without endangering the ability of the package manager to install updates to the package.  I'd like the same information myself: what can I add to /usr/share/drupal6 without confusing the package manager?

---

### Post by dylbud on 2011-06-07
Nobody ever answered this, huh? I'm trying to figure out the same thing. Instructions say to put new themes into /sites/all but yes it is true there is no "all" folder and more than one "sites" folders

for example:

/etc/drupal/6/sites
/usr/share/drupal6/sites

If I were to create the "all" folder, I wouldn't know which of these two places to put it.

---

### Post by eode on 2012-04-05
> **dylbud said:**
> Nobody ever answered this, huh? 

for example:

/etc/drupal/6/sites
/usr/share/drupal6/sites

If I were to create the "all" folder, I wouldn't know which of these two places to put it.

Better-late-than-never:

The simple answer that conveys the wrong idea:
It doesn't matter.

The less simple answer that conveys the right idea:
The "/etc" directory contains configuration files.  It's a little odd to have the drupal modules in /etc (as they are in debian/ubuntu), but it's way better than trying to install them in /usr, which could lead to the modules being deleted, or other problems during upgrades/installs. '/etc/drupal/6/sites' is the correct folder to use.
The "/usr" directory, except for "/usr/local", should effectively be treated as read-only as far as system administration goes.  It's ok to write to /usr/local (installs from source, wrappers, etc usually go here), but for the /usr folder and its other subfolders, The package manager handles all the files there, and it's best not to touch them.

The reason it would be okay in this case is because
/usr/share/drupal6/sites
   is a link to 
/etc/drupal/6/sites

..so either way, you're really modifying the files in '/etc/drupal/6/sites'.


A right way to do it:
```

sudo mkdir -p /etc/drupal/6/sites/all/modules
cd /etc/drupal/6/sites/all/modules
sudo tar xzf /path/to/your_module.tar.gz

```
..obviously, you replace '/path/to/your_module.tar.gz' with the path to the module you wish to add to drupal.

An overview of the Linux file hierarchy and what is supposed to go where is here:
[http://wiki.debian.org/FilesystemHierarchyStandard](http://wiki.debian.org/FilesystemHierarchyStandard)

Hope this is helpful to someone.  :-)

[edit: added description of /etc and its purpose, and a link to the Linux FHS]

---

