---
title: "Permissions for /var/www"
date: 2011-01-05
forum: Server Platforms
---

### Post by lkejke on 2011-01-05
I use Ubuntu on my desktop and run Apache, MySQL and PHP for WordPress theme development. I only use the default /var/www folder for the website. What group/user permissions should I set on /var/www? I want to be able to copy, move, edit and delete files/folders in /var/www using the file browser (i.e. without sudo from the command line). I want WordPress to be able to download and update automatically (from within the WordPress Dashboard). I also want to use the WordPress media upload feature. I don't know how I should assign group/user permissions. Should I be using the 'www-data' group, or 'apache' group? Any advice would be great.

---

### Post by kevinthecomputerguy on 2011-01-06
user = %you%
group = nogroup
 
permissions on folders = 755
 
permissions on files = 644
 
I don't use wordpress, but you cant go wrong with above.

---

### Post by mdlueck on 2011-01-06
I took a slightly different approach. First, I have /var on its own small partition, so I changed to using /srv/www as the place Apache files end up.

I add users to the www-data group that need to be allowed to write files to this area of the server.

Perms on /srv/www are as follows:

Start with non-ACL perms:

sudo mkdir /srv/www
sudo chown -R www-data:www-data /srv/www
sudo chmod 0775 /srv/www
sudo sudo chmod g+s /srv/www

With ACL support on the filesystem:

sudo setfacl -d -m mask::rwx /srv/www

Check the ACL perms:

sudo getfacl -d /srv/www
getfacl: Removing leading '/' from absolute path names
# file: srv/www
# owner: www-data
# group: www-data
user::rwx
group::rwx
mask::rwx
other::r-x

<><><>

As for WordPress specifically, it is insisting that files/dirs be www-data:www-data to allow the plugin auto update to work. So I must chown -R the WordPress area of the site to/from userid:www-data to www-data:www:data each time I upgrade WordPress. So make sure what ever ID you admin WordPress with is able to sudo.

---

### Post by sprosty on 2011-03-07
Michael, 

With your permission scheme you are giving ownership as well as write permissions to all files in your web directory to apache. That's not a very safe setup in my opinion. 

I would give apache write access to files/directories on a need-only basis (i.e. file upload folder for a website).

Drupal for example has a page dedicated to this topic here: [http://drupal.org/node/244924](http://drupal.org/node/244924)

With respect to setting up a web developer permission scheme on your server...

I'm having a similar issue with a group of developers who need access to /var/www however I need to keep things secure... so I'm trying to balance ease of use with security.

One possibility is to create a webdev group and have www-data as a member of that group. Your developers by default will have the same access as apache, which should default to r-x 

The owner of a directory then should be the current developer, who woudl have rwx access.

It creates more work for the sys admin but it's more secure imho.

If anyone has a better scheme that increases ease of use but doesn't compromise security I'd love to see it.

---

