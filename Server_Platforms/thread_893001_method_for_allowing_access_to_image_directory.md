---
title: "method for allowing access to image directory?"
date: 2008-08-17
forum: Server Platforms
---

### Post by govee on 2008-08-17
I want to link my image directory from my web page which is hosted on my LAMP server. I have lots of pics that I want to share but dont want to place them all on the page. I just want them to see a list then they can pic from there, or I guess it would be ok if the pics showed as well. I just dont want to spend a lot of time coding for all the images.

Would it be as simple as putting a link to the directory that has the images? 

Does this cause a security problem if the image directory is not in the /var/www?

Thanks

---

### Post by RealPSL on 2008-08-19
Creating a link should work fine. The default configuration has > Indexes FollowSymLinks
This should allow the pictures in your linked images directory to be displayed as a list of files in the browser. To create the link:

```
sudo ln -s /path_to_images /var/www/images
```

---

### Post by govee on 2008-08-19
thanks RealPSL.

I created the SymLink but apache will not follow it. I dont get a failure page, it just goes back to the start page instead of the startpage/images. I did check and the symlink is there and works when I use WINSCP I can see the link and it goes straight to the image folder with all the images when clicked. I checked everywhere I could and I think follow symlinks is set correctly, but not 100% percent sure.

What next??

thanks

---

### Post by RealPSL on 2008-08-20
Can you provide the output of ```
ls -l /var/www/path_to_link
```

What are you entering in the browser? Is it [http://web_server_name/path_to_link?](http://web_server_name/path_to_link?)

---

### Post by govee on 2008-08-21
> Can you provide the output of 
Code:
ls -l /var/www/path_to_link

lrwxrwxrwx 1 www-data www-data 25 2008-08-20 17:07 /var/www/node/1/images -> /server/Pictures/TheHouse
> 
What are you entering in the browser? Is it [http://web_server_name/path_to_link?](http://web_server_name/path_to_link?)  

[http://webserver.net/node/1/images](http://webserver.net/node/1/images)

I originally had the symlink in the /var/www/ but made a new one in the same folder as the rest of html docs. I changed the directory in the 000-default by adding the /node/1. I now get a http 404 failure. 

Thanks

---

### Post by RealPSL on 2008-08-21
At this point there can be only 2 problems that I can think of. First that the www-data user does not have access to the files you linked to. This is unlikely because I think you would have probably gotten a permission denied error instead. Check just the same as the www-data user needs read access to the path.

My suspicion is more that your Apache configuration is not setup to follow symlinks. In your /etc/apache2/sites-enabled do you only have the default 000-default configuration file or did you modify it? I am running 8.04 and I verified that the default configuration will work if the www-data user has read access to the entire path that you symlink to. 

The default configuration that will make this work in the 000-default file is 
```
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

```

Can you check both things and let me know?

---

### Post by govee on 2008-08-22
Here is part of my 000-default:


```
DocumentRoot /var/www
        <Directory />
                Options FollowSymLinks
                AllowOverride None
        </Directory>
        <Directory "/var/www/node/1">
                Options Indexes FollowSymLinks MultiViews
                AllowOverride All
                Order allow,deny
                allow from all
        </Directory>
```

> Check just the same as the www-data user needs read access to the path.

I am not sure what you are asking here?

---

### Post by RealPSL on 2008-08-22
You need to make sure that the wwwdata user has access to the files so that they can be displayed by Apache. Your configuration looks okay.

---

### Post by govee on 2008-08-26
I was not able to get this done via a symlink. I have with the help of RealPSL been trying to get this working and I am still not sure why it is not working. I have tried Symlinks to different folders and none work. We have been focusing on Apache setup as it relates to follow symlinks. Is there another setup requirement in apache to allow showing a directory?

I did locate a PHP file that someone wrote that I placed in the imagery folder and it does what I need.:popcorn: 
I did have to create a new folder in the html folder and put the images in there. It works, but complicates things with 2 folders with the same images.

I would still like to know for my apache Q&A rolodex what the resoultion is for following a symlink to show a directory full of images.

---

