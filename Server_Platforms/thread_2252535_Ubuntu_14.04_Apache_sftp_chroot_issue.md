---
title: "Ubuntu 14.04 Apache sftp chroot issue"
date: 2014-11-12
forum: Server Platforms
---

### Post by darkapec on 2014-11-12
Hopefully someone here has run into a similar situation. 

I have a chroot jail setup for a directory "/home/jail/Videos/" I am trying to also make that directory visible via apache without removing the chroot jail. Apache was able to view this directory prior to setting up the chroot, so I assume this has something to do with permissions.  

```
The current permissions are:

/home/jail/videos | jake:jake 0755
/home/jail        | root:root 0755
```

```
Relevant Apache Config:

<VirtualHost *:80>
DocumentRoot /home/jail
ServerName media.****.net
IndexOptions FancyIndexing FoldersFirst
IndexOrderDefault Ascending Name


# Other directives here


</VirtualHost>

```

The strange part is I created a index.html file that simply says "It Works!" in the /home/jail directory and I am able to successfully see that file using a web browser. But I am unable to navigate into any sub-directories. I am however able to access a file if I know the whole path though.

For example:
I can access /home/jail/index.html by vising media.****.net 
I cannot access /home/jail/Videos/Personal/ by changing the address in the address bar. 
I can access /home/jail/Videos/Personal/Movie.mp4 if I manually type the entire file path in the address bar. 

This to me says that mod_dir is unable to index the folder contents (probably because of the permissions). I do not want to create index.html files in each sub-directory containing the contents of the directory. Anyone have another solution? 

Thanks
Jake

---

### Post by Lars Noodén on 2014-11-12
From the symptoms, you're probably missing an [Options](http://httpd.apache.org/docs/2.4/mod/core.html#options) directive for that directory.  

```

<Directory "/home/jail">
  Options Indexes
</Directory>

```

---

### Post by darkapec on 2014-11-12
You sir are a genius!!! I can't believe how many hours I spent trying to fix such an easy issue. Thank you so much!

---

