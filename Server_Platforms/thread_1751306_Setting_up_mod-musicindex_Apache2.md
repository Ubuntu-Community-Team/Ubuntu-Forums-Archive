---
title: "Setting up mod-musicindex Apache2"
date: 2011-05-06
forum: Server Platforms
---

### Post by Cyked on 2011-05-06
So, I followed this initially:
[http://ubuntuforums.org/showthread.php?t=34359&highlight=mod-musicindex](http://ubuntuforums.org/showthread.php?t=34359&highlight=mod-musicindex)

Now going through the readme here:
[http://www.parisc-linux.org/~varenet/musicindex/README](http://www.parisc-linux.org/~varenet/musicindex/README)

I setup /var/www/music in apache with a symlink to a mountpoint (the mount point points to a folder on a windows box. mnt/falconu points to something like U:\files\mp3).  The symlink is /var/www/music/p.

When I go to mysite/music everything seems to load fine, I see icons, etc. However, when I click on "p" symlink dir I get 403 forbidden You don't have permission to access /music/p/ on this server.  

Here is what I put in sites-available:

```
<Directory /var/www/music>
    Options             Indexes MultiViews FollowSymlinks
     AllowOverride All

    Order allow,deny
    allow from all

</Directory>

```

here is httpd.conf:
```
<Directory /var/www/music>
    Options             Indexes MultiViews FollowSymlinks
    AllowOverride       Indexes
# Can be overriden in .htaccess
    MusicIndex          On +Stream +Download +Search -Rss -Tarball
    MusicSortOrder      album disc track artist title length bitrate freq filetype filename uri
    MusicFields         title artist album length bitrate
    MusicPageTitle      Myname
    MusicDefaultCss     musicindex.css
    MusicDirPerLine     3
# Can only be set in apache configuration
    MusicDefaultDisplay HTML
    MusicIndexCache     file://tmp/musicindex
    MusicIceServer      [ice.domain.my]:8000
    MusicCookieLife     300

</Directory>

```


So indexes is on (most all other dirs are set to not allow directory browsing.  Symlinks shouldn't be a problem either (I have another symlink that is in /var/wwww/misc that works fine and it also points to a mount that is to another drive on the same windows box.

This is in the apache error logs:
```
Symbolic link not allowed or link target not accessible: /var/www/music/p
```

And finally, this happens when I restart apache:
```
Restarting web server apache2                                                                                                                             [Fri May 06 11:02:46 2011] [error] [mod_musicindex] (cache_file_setup) Not a directory
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
 **... waiting [Fri May 06 11:02:47 2011] [error] [mod_musicindex] (cache_file_setup) Not a directory**
apache2: Could not reliably determine the server's fully qualified domain name, using 127.0.1.1 for ServerName
```

Any thoughts on this?

Thanks!

---

### Post by Cyked on 2011-05-09
Has anyone used this mod before, or have a suggestion for something else to use with apache?  I *think* what I need to figure out is how to get this mod to follow symlinks correctly.  If I put music files in /home/user/Music it sees them and will play them.  If I put in a symlink there, there.  If I use an alias to the mount point where my music is on the windows box I still get the 403 forbidden.

Thanks.

---

