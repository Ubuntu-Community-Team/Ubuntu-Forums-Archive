---
title: "How do I allows apache2 read-only access to a folder in my home directory"
date: 2009-11-04
forum: Server Platforms
---

### Post by rick3878894 on 2009-11-04
I recently got interested in setting up a ampache on my box for light use from time to time. In order for ampache to work correctly it has to have read access (at least maybe write as well) to a folder full of music and rather then move that folder to /var/www/ I want to leave it where it is and give apache2 permission to display what is inside.

I have been at this for hours and not combination of key words has shown me useful information in my searching. I tried a symlink but [http://localhost/Music](http://localhost/Music) returns as a 403. 

Thoughts?

---

### Post by rick3878894 on 2009-11-05
I tried a symlink work around and it turns out apache2 can't fallow symlinks at all. At least not right now any way.

New question. Can I make apache load the contents of something like "/home/user_name/apache2www". I have given it a go with setting servers root directory to apache2www in my home folder using phpmyadmin. No luck, I am missing some thing.

Thoughts?

---

### Post by Lars Noodén on 2009-11-05
You'll want to look at the [UserDir](http://httpd.apache.org/docs/2.2/mod/mod_userdir.html) and [Directory](http://httpd.apache.org/docs/2.2/mod/core.html#directory) or Location directives.  

See also,
  [http://httpd.apache.org/docs/2.2/howto/public_html.html](http://httpd.apache.org/docs/2.2/howto/public_html.html)

A second way would involve aliases.

---

### Post by lisati on 2009-11-05
<aside>This thread is fine where it is. Setting up a server is something that some beginners would find daunting.</aside>

---

### Post by Lars Noodén on 2009-11-05
> **rick3878894 said:**
> I tried a symlink work around and it turns out apache2 can't fallow symlinks at all. At least not right now any way.


Apache could follow symlinks if the Directory [options](http://httpd.apache.org/docs/2.2/mod/core.html#options) permit it, but the better way is either UserDir as above, or an alias.

---

### Post by rick3878894 on 2009-11-15
So I have enabled user dir and now [http://localhost/~kanada/](http://localhost/~kanada/) is coming up 403. I have done some searching and every thing is a bit over my head. Does some one know what to do?

---

### Post by jd65pl on 2009-11-15
Do you have a public_html in ~?

Are the permissions of the directory and any files you want to serve 755? Apache will require read and execute access but not write to serve your files correctly.

Check permissions
```
ls-l ~/public_html
```

Change permissions
```
chmod 755 -R ~/public_html
```

---

### Post by Lars Noodén on 2009-11-16
> **jd65pl said:**
> Do you have a public_html in ~?

Are the permissions of the directory and any files you want to serve 755? Apache will require read and execute access but not write to serve your files correctly.

Check permissions
```
ls-l ~/public_html
```

Change permissions
```
chmod 755 -R ~/public_html
```

That changes also the files, not just the directories.  

Somewhere there are some instructions for this in Ubuntu, but they say something like this:

```

# set permissions for directories: rwxr-xr-x
find ~/public_html -type -d exec chmod 755 {}  \;

# set permissions for regular files: rw-r--r--
find ~/public_html -type -f exec chmod 644 {}  \;

```

---

