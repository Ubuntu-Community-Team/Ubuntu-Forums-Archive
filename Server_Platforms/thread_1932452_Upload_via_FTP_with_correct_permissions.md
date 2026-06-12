---
title: "Upload via FTP with correct permissions"
date: 2012-02-27
forum: Server Platforms
---

### Post by meighty on 2012-02-27
Recently I've been asked to spin up a server that has the ability to host multiple sites. Not a problem. I've set up 10.04, have apache2 running and the sites are up with no problems. 

I will be running an FTP and I have several users that will need to be uploading files. Everything that is uploaded is put under user:user. In order for things to work correctly it pretty much needs to be www-data:www-data. 

How do you allow apache to mod the files that have been uploaded under the user's own group? 

Isn't this how big hosts like Dreamhost and Hostgator do it? I've used them in the past and everything is under my own user.

---

### Post by Lars Noodén on 2012-02-27
Nothing should be owned by or in the group www-data.  That is for the web server to run under when it runs as an unprivileged user.  If the web serve can write to the directory, then there is the potential for a lot of problems, best to use another group for sharing.

To manage file permissions, you can use groups and add the users to the right group:

```

sudo addgroup team1
sudo chgrp -R team1 /var/www/website1/

sudo find /var/www/website1/ -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www/website1/ -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add meighty  team1

```

Repeat for each site.

Also, you may want to seriously reconsider FTP.  Unless there is a specific reason that you must have FTP and nothing else, I would recommend using SFTP instead.

[list]
[*] [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp)
[*] [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
[/list]

If you have the package OpenSSH-Server already installed, then you already have SFTP configured (it works over SSH) and you can then connect to it using FileZilla or Nautilus.

---

### Post by meighty on 2012-02-27
> **Lars Noodén said:**
> 

```

sudo addgroup team1
sudo chgrp -R team1 /var/www/website1/

sudo find /var/www/website1/ -type d -exec chmod g=rwxs "{}" \;
sudo find /var/www/website1/ -type f -exec chmod g=rws  "{}" \;

# repeat for each user:
sudo gpasswd --add meighty  team1

```



I totally agree and I'm pushing for SFTP and but we'll see how it goes. I use it on my own stuff. 

Just to be clear...

You're creating a group. In this case team1
Then you're changing the group recursively  to team1

After that you're changing the permissions on directories and files? 

Finally you add specific users to said group?

I'm not Ubuntu expert but I try to break things down and understand them rather just pasting in commands.

---

### Post by meighty on 2012-02-27
I'm pretty much starting over now. My plan...

Set up each sites with it's own user/group. IE site1:site1 site2:site2 etc, etc

Then add the www-data group to each usergroup (site1) thus giving apache the ability to crate files (think wordpress)

From there I should just be able to chmod -R g+rw /home/site1 and repeat for the other sites.

This, does not seem to work. ;)

---

### Post by Lars Noodén on 2012-02-28
> **meighty said:**
> From there I should just be able to chmod -R g+rw /home/site1 and repeat for the other sites.


You'll need the setgid bit and execute, too, for the groups on directories:  g+rwxs

---

### Post by meighty on 2012-02-28
> **Lars Noodén said:**
> You'll need the setgid bit and execute, too, for the groups on directories:  g+rwxs

This works! At least until Wordpress tries to update or install a plugin. Then I don't have permission. This can be fixed by doing a chown -R www-data:site1 to site's root.

---

### Post by Lars Noodén on 2012-02-28
Great!

You might want to consider chowing it back once you've made  your update or added your plugin so as to limit the time the directory is writeable to web processes.  That narrows the window during which something could go wrong or an exploit be used.

---

