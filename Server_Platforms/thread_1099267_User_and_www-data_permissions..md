---
title: "User and www-data permissions."
date: 2009-03-18
forum: Server Platforms
---

### Post by RaymondBeaudoin on 2009-03-18
I am trying to think of a situation where you have multiple users on a server and they each need a web-accessible directory, so /home/user1/site1/www and /home/user2/site1/www but they should not be able to see each other's files through SSH/FTP whatever. I thought chown user1:www-data /home/user1/site1/www would work, but it wouldn't if you chmod 700 /home/user1 because then the upper directory is not accessible thus making a lower directory permission overridden.

I know that is a bit jumbled, or seems like it to me, so let me try and clear it up.

I have my apache server running just fine and dandy. Well now mr ftp wants to access his folder so he can upload files to /home/user1/site1/. GREAT! LET's do it! Well I create users manually (as I have not come upon the skills of being able to write a panel or sh script to do it for me), and so user1 can login to ftp and be taken to his home /home/user1. 

Yay! Now he's there! Unfortunately, based on permissions he might be able to leave him home directory and go into /home/user2's directory! That's no good!

So to combat this I chmod'd each user's home directory to 700. Well that worked great, except they have a "www" directory for webaccess! So how do I deal with that? Simple! chown user1:www-data /home/user1 right!? Nope.. Because now it DOES have access but users get a "Forbidden Access" Message on the site when they try and access it.

I'm a tad baffled, I hope someone can help me sort it out.

Last time I offered free e-popcorn, so tonight to spruce things up a bit, I am going to offer a beautiful mixture of classical and jazz guitar to whomever posts the answer!

:guitar: :-({|=

Thanks,
Ray

---

### Post by RaymondBeaudoin on 2009-03-18
I hate to bump, I know it is unfair, someone must know though and this is a pressing issue.

I appreciate all of your help and patience with me.

Thank you again,
Ray

---

### Post by ssam on 2009-03-18
maybe make www-user1, and www-user2 groups. where www-data and user1 are both members of www-user1. then
chown user1:www-user1 /home/user1
chown user1:www-user1 /home/user1/www
chmod 750 /home/user1
chmod 750 /home/user1/www

its probably best to use ACLs instead

---

### Post by RaymondBeaudoin on 2009-03-19
Thank you for your reply, ACLs? I remember dealing with those when I was setting up Mac servers, but it has been a long while, can you help me out a little? Thanks again.

Edit 1: Ahhh, ACLs, now I remember where they are from. You had to set them up on Mac OS X 10.5 when using SAMBA. Not quite sure how to set them up on Ubuntu though, looking now, but your help would be more than appreciated.

Edit 2: How does cPanel handle it? I thought it used basic User/Group/Owner permissions. I really am eager to find out though, this sounds exciting, but needs to be solved soon! Thanks again!

For your pleasure, the Imperial Theme Song on Tesla Coils.

[http://www.liveleak.com/view?i=e77_1237295597](http://www.liveleak.com/view?i=e77_1237295597)

Enjoy,
Ray

---

