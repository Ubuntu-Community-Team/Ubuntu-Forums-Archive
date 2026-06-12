---
title: "just installed - not loading css"
date: 2010-08-27
forum: Server Platforms
---

### Post by mortona42 on 2010-08-27
I just installed wordpress on my webserver. did apt-get install wordpress, copied /usr/share/wordpress to /var/www/wordpress. set up wp-config.php, and installed. now when i go to /wordpress, it takes a while to load content, then just displays text without css. whats going on?

---

### Post by Ryan Dwyer on 2010-08-27
I just installed it. I fail to see how a new user could do this. For a start, after sudo apt-get installing it never tells you what to do next. I went to /wordpress/ expecting a directory alias to have been created in Apache's config, but no. Nothing. I restarted Apache and tried again. Still nothing. I checked Apache's config to see if anything had been changed. Nothing. I went to /usr/share/wordpress/ (through no instruction) and the files are there. Awesome.

So I copied them to ~/www/private/wordpress and browsed to [http://private/wordpress/](http://private/wordpress/) (private is already a vhost). I get an error telling me it can't read /etc/wordpress/config-private.php. I look in /etc/wordpress/ and see wp-config.php and "htaccess" (no dot). I figure maybe wordpress read the directory name it's in and looks for a similar config file. I use sudo to rename the wp-config.php to config-private.php.

After following their installation procedure it asks me to save the file wp-config.php but doesn't say where, so I figure in the wordpress directory. Oh, I can't - there's already a symlink there and it's linked to /etc/wordpress/wp-config.php which now doesn't exist. So I deleted the link and added my config file.

Finally, I click "Run the install" and it loads a page which only contains the Wordpress logo. No success or failure message. Unsure what's happened, I open a new tab and confirm Wordpress is indeed installed correctly.

How can anyone seriously expect this to be done by a beginner or even intermediate user?

Anyway, my CSS is showing up fine. I note it's using full http links for everything, so if you installed it using a different hostname then maybe it's gotten confused and is linking to the wrong hostname. Please tell us what is in the address bar, then view the page source, look for style.css (on the first few lines) and paste the full URL it's using to include it.

---

### Post by baudday on 2010-08-29
why go through all that trouble? why not just download it off the wordpress site, upload it to your server, and install it like that?

---

