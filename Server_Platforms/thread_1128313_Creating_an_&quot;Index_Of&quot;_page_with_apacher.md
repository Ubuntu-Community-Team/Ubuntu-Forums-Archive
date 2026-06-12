---
title: "Creating an &quot;Index Of&quot; page with apache/redhat"
date: 2009-04-17
forum: Server Platforms
---

### Post by urnumdei on 2009-04-17
I understand that this is Ubuntu and not Red Hat....  I didn't pick the server OS, I just help administrate it.  Besides, I'm sure this is a general enough question that the OS is irrelevant.

Anyways,  my organization has a website where a lot of people are going to be downloading files.  Instead of throwing 200 links onto a page, is there a [easy] way to make an Index Of page?

I did some googleing and one page said to remove the index.html page and that should display all the folders.  That didn't work, I got the Redhat Test Page saying I should now add content to my website.

But then, maybe I am going about this the wrong way.  I first thought an ftp server would be in order, however, the people doing the downloading are most likely computer illiterate.  And even if they aren't, best to assume such for ultimate user-friendliness, right?

Thanks for anything and everything.

---

### Post by xkaliburx on 2009-04-17
Yea, OS shouldn't matter as I am still switching over to Ubuntu-server so posting (about to again) post more OS questions.  But as you said this is an independant one.

As for not having an index, thats fine.  The section in your httpd.conf has a docroot and there is also a directoryindex which say's which files to load.  If none of those files are there, you should get the test page (which you are)

What you could do inside your conf file is the following;
<Directory "/location of your folder here/">
              	Options Indexes
               	Order Allow,Deny
               	Allow From all
 	</Directory>

Basically that will then show all the files in that folder.  Report back if it doesn't work along with your httpd.conf file (only the host part)

---

### Post by cdenley on 2009-04-17
The file you want to edit is /etc/apache2/sites-available/default. The file httpd.conf is no longer used. It should allow indexing by default. Just make sure "Indexes" is listed after "Options". Also, instead of deleting index.html, you can use "DirectoryIndex disabled".

You default site configuration, assuming that is the one you are configuring, should look something like
```

<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options **[COLOR="Red"]Indexes[/COLOR]** FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		[COLOR="Red"]**DirectoryIndex disabled**[/COLOR]
	</Directory>
</VirtualHost>

```

---

### Post by urnumdei on 2009-04-17
There isn't a directory /etc/apache2.  Any other places?  config.d folder is empty as well.  (I remember seeing that in one of my searches.)

---

### Post by cdenley on 2009-04-19
> **urnumdei said:**
> There isn't a directory /etc/apache2.  Any other places?  config.d folder is empty as well.  (I remember seeing that in one of my searches.)

If you don't have an /etc/apache2 directory, you either don't have apache2 installed, or you deleted it after installing apache2.
```

cat /etc/lsb-release
dpkg -l apache*
dpkg -S /etc/apache2
ls /etc/apache2

```

Are you using ubuntu or redhat? I just re-read your first post, and it wasn't very clear. If you're using redhat, I'm not sure where they put their apache config, or what scheme they use to configure it.

---

### Post by R.Bucky on 2009-04-19
You could always use php. I list my image directory with the following code:
[PHP]$dir = '/var/www/images/';
$files1 = scandir($dir);
echo '<p><h2>Image Directory</h2></p><ul>';
foreach($files1 as $file)
{
  	if($file != "." && $file != "..")
    echo "<li><a href=$file target=_blank>$file</a></li>";
}

echo '</ul>';[/PHP]

See my image gallery at [http://buckycomputing.net/images/]("http://buckycomputing.net/images/")
It integrates well into your exisiting template or page. Or, is this not what you are looking at doing?

---

### Post by urnumdei on 2009-04-20
Perhaps I should reclarify the situation I got here.

I am an admin for my organization's website.  We are going to have a page where people download a lot of files.  Instead of linking everything, we were wanting to create an Index Of page.

We use a hosting company and we just ftp into it.  We don't control our own servers.  According to the test page, I see a Redhat symbol and an Apache2 symbol.  So I am assuming it's apache2 that I work with.  I personally use Ubuntu on my laptop.

Hope that clears everything up.  I'll try the new tips and see if they work.  *crosses fingers*

---

### Post by xkaliburx on 2009-04-20
The example code regarding the Index's will work in Ubunutu just as redhat.  The RedHat default path is set at /etc/httpd *unless installed from src which will put it in /usr/local/apache.

You could always do a locate httpd.conf to find it as well.

Good luck

---

### Post by nandemonai on 2009-04-20
> **urnumdei said:**
> Perhaps I should reclarify the situation I got here.

I am an admin for my organization's website.  We are going to have a page where people download a lot of files.  Instead of linking everything, we were wanting to create an Index Of page.

We use a hosting company and we just ftp into it.  We don't control our own servers.  According to the test page, I see a Redhat symbol and an Apache2 symbol.  So I am assuming it's apache2 that I work with.  I personally use Ubuntu on my laptop.

Hope that clears everything up.  I'll try the new tips and see if they work.  *crosses fingers*

If you don't have access to the confs the best idea is to contact your host and state your case OR use the php example (or indeed something similar).

---

### Post by cdenley on 2009-04-20
> **nandemonai said:**
> If you don't have access to the confs the best idea is to contact your host and state your case OR use the php example (or indeed something similar).

Or you can try creating an .htaccess file in your upload directory.
```

Options +Indexes
DirectoryIndex disabled

```
The first line requires that Opitons overrides are allowed, and enables listing of directories. The second line requires that Indexes overrides are allowed, and prevents index.html from being used, so you always get a directory listing.

---

