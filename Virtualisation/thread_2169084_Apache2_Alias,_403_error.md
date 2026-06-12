---
title: "Apache2 Alias, 403 error"
date: 2013-08-20
forum: Virtualisation
---

### Post by bladefallcon on 2013-08-20
Ok, so I set up an Alias in my apache2 server to point to a second harddrive. 

I had tons of problems with it, but finally had it working (when by my understanding, it shouldn't have.) Here is what I had:

Second drive was located at /media/MediaServer
Folder I wanted to access was /media/MediaServer/Videos
So the alis was pointing to that folder, but it did not work. Then after tons of looking and trying, I pointed it to /media/MediaServer and suddenly it worked...even though it was pointing to the main drive, it was opening the Videos folder. 

Then, I got a new bigger harddrive. Wanted to move all my Media files to the new drive. In an attempt to avoid problems, I transfered files, then changed names of drives so that the new drive was now /media/MediaServer, so that in theory, the alias would point now to the new drive...but alas...that was not the case....now I am stumped as to what to do to get this working again. 

Here is what I am doing:

Using a Roku and Roksbox channel, I stream my media files over to my TV. To do this, I have my apache server set up to point to the media files folder, which is as I said, on my new drive, mounted at /media/MediaServer/Videos.

Here is the alias file I have setting up the alias:


videos.conf:
```
Alias /Videos /media/MediaServer
<directory /Videos>
	options +Indexes FollowSymLinks 
		AllowOverride AuthConfig FileInfo
                Order allow,deny
		Allow from all
</directory>
```

I had another file at before, but I seem to have lost it...and worse, don't remember where it was, or what it did....

What I need, it to set it up so that localhost/Videos or 192.168.0.108/Videos will point to, and open my Videos folder on the new hard drive...please, help!


Edit:

Forgot to actually mention my problem...it does seem to be pointing to the right place...but I get a 403 forbidden error...I have checked (and changed permissions for all folders/files on the drive...nothing seems to work..
If I open up nautilus, and browse to /var/www I see a folder names Videos, which shows that it is a linked folder. If I open it, it opens the Videos folder on the new drive...so the link is working...I just can't seem to access it from a browser (and therefor can't access it from my TV either...)

---

### Post by bladefallcon on 2013-08-20
Ok...don't know what the problem was...but I fixed it...

Uninstalled my apache server completely...and reinstalled. When I did that, I opened /etc/apache2/sites-enabled/000-default and changed the DocumentRoot to point to my new drive /media/MediaServer instead of /var/www. So now the entire server looks there...rather than needing an alias...

No idea what the problem was before...but it doesn't really matter now..

---

