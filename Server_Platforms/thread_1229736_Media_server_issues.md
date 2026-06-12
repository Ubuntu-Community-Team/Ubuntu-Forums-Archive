---
title: "Media server issues"
date: 2009-08-02
forum: Server Platforms
---

### Post by doomsayer97 on 2009-08-02
I've got an old Dell Inspiron 1150, and I was hoping to turn it into a media server. I've been using [this](http://rubbervir.us/projects/ubuntu_media_server/) guide. I'm using Ubuntu 9.04 Jaunty. On the second page (setting up Jimzora), I type in the internal IP address in FireFox, but it just says "It works!" instead of what the guy says it should. I can't figure out what to change in the MySQL file (step five). Anyone have any ideas?

---

### Post by bmathis on 2009-08-02
You can try putting jinzora2 in the url, i.e. [http://ip.of.local.server/jinzora2](http://ip.of.local.server/jinzora2) and see what that does for you. The "It Works!" page is the default page when apache is installed. You can delete that by issueing the command 

> sudo rm /var/www/index.html

and it should show you a directory listing of all files inside of /var/www/ which then should allow you to select jinzora2.

---

### Post by doomsayer97 on 2009-08-02
Thank you very much :)

I typed in my IP followed by /jinzora2 and now I'm on the setup for Jinzora screen. I'll finish up this and then post back with my results :D

Thanks for helping me get past that little issue. 


And thanks for telling me how to get rid of that 'It works!' screen.


EDIT 2

Alright so I got the server up!!! Yay!!! :D

The problem is...
Nobody outside my network can access the site.
Not a major problem, but a problem nevertheless.

I've read [his]("http://rubbervir.us/projects/ubuntu_media_server/part3.php") instructions, but I always get stuck at this part: 

> 
3. Create a homepage

    Create a simple homepage. I made an image based one, you can find it right here (Username is "USERNAME" and Password is "PASSWORD"), and download it right here. For a link to Jinzora create a link which points to "jinzora2/", that's your Jinzora directory obviously. For html help visit W3Schools. 


Any ideas on what he means here?



EDIT 3

Alright.
So I've been trying to work at this all day.

I read online that I needed to forward port 8888 as well. So I did. Still doesn't let other poeple connect (used my-ip-address:8888/jinzora2). 

Anyone have a clue?

---

### Post by bmathis on 2009-08-04
It looks like the homepage part is optional. You just need to make sure that the [ports on your router are forwarded]("http://portforward.com/") to your server and that the server has a [static IP address]("http://lani78.wordpress.com/2008/08/07/change-to-static-ip-on-my-ubuntu-server/"). If you want, PM me your external IP and ill see if I can access it from where I am.

---

### Post by doomsayer97 on 2009-08-05
Actually, I managed to figure it out :D

Took two tries, but I got it to work. Turns out that the ports weren't being forwarded to the right IP address. Just one number off! 

If you would like to check out the server, you can do so by going here:
mymediaserver.homelinux.com
(Hooray for DynDNS!!!). 

But, you won't be able to get anywhere past the login screen for Jinzora :P



I'm going to write a guide on how I did this, that why people like me who have no idea what they're doing can actually figure it out!



You wouldn't happen to know how I could change my dynamic IP address on my server to a static one, do you? The link you gave me has a comment that says that it totally ruins the internet connection, and I don't really wanna risk it.


EDIT

OK so someone got me a link to a video on Systm for DynDNS.com (service that I used for my server). Now, do I have to compile the ddclient myself, or is there one in Synaptic...

---

