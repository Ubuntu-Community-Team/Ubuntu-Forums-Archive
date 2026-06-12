---
title: "apt-get Wordpress, easy enough, but what now??"
date: 2006-10-09
forum: Server Platforms
---

### Post by kpm on 2006-10-09
whoops! posted in wrong spot... never the less, I found the answer here [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

__________________

Hi,

I installed the Dapper LAMP server. I then used apt to install Wordpress. I have installed Wordpress on Widows many times, but this is a first on Lunux. So I began the search for config files... Off to /etc/wordpress, where I found the wp-config file, but it told me NOT to touch it and to go to the readme.html, which I saw to be located at '/usr/share/wordpress/readme.html'. So I open that file up using 'less readme.html' and think to myself I should really be looking at this file via a webbrowser (I am ssh'd into the bare bones old server from a laptop). But now I am stuck... I don't know what url to use to get to that readme file... I know my web server root is /var/www/ and that if I enter the url [http://192.168.1.200/index.html](http://192.168.1.200/index.html) I can see the server up and running, can access phpmyadmin to get at MySQL, etc... but with the default install of Wordpress using apt, I am left a bit confused... I know I can copy the readme.html to the root of www, but, thought, that since Wordpress placed it /usr/share/wordpress/ that I should figure out what I have to do to Apache to get it to look there for it... Having come from Windows, I am used to having all the web pages dumped in a subdirectory of the Apache2 folder... Can anyone clue me in here on this??

---

