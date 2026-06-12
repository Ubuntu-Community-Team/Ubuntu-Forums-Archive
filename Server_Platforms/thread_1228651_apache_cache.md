---
title: "apache cache??"
date: 2009-08-01
forum: Server Platforms
---

### Post by mambra on 2009-08-01
ok so i'm very new to apache.  and i'm going a little nuts trying to figure this out.

i have Ubuntu 8.04.2 and apache2 loaded haven't changed any of the configs.  now i needed to be able to download some very small files from a url.  so i added a symlink under my /var/www to my home folder, where i can upload the files, and then download them with [http://mydomain/symlink](http://mydomain/symlink).  

now this worked fine, until i realized that if i upload a new file with ftp or scp,  and download the file from the url, it is still the old version.  so i thought it must be cache in my browser or apache.  but the cache on my browser is cleared and the cache modules is not loading.

how do i fix this?  does apache do caching automatically?  help will be so much appreciated!

---

### Post by Thirtysixway on 2009-08-02
Perhaps it's cacheing in your browser? Unless I'm reading the issue incorrectly.

Why don't you look into mod_dir?  then you can create a public_html folder in your home directory, and then the url becomes [http://yourdomain.com/~username/](http://yourdomain.com/~username/)

---

