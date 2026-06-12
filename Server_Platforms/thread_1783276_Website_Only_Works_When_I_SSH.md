---
title: "Website Only Works When I SSH"
date: 2011-06-15
forum: Server Platforms
---

### Post by flyingsuperhigh on 2011-06-15
My ISP provided me with a static IP and I went and bought a domain name with godaddy.com. The issue I'm having now is that I am getting a 403 forbidden error (You don't have permission to access / on this server). The strange part is that when I ssh into my server, and try to go to my website, everything works fine. Anyone have any ideas what I should do?

---

### Post by flyingsuperhigh on 2011-06-15
I just wanted to add something to my previous post. Even when I'm connected to the local network and type in the server's LAN address I get the same error. Similarly, if I ssh into the server and type in the server's LAN address into the browser, I get directed to the index.html page. I have a feeling that I did not set the permissions correctly for the public_html folder in the first place. 

This is what I did:
chmod 755 ~/public_html/
chmod 644 ~/public_html/index.html/

---

### Post by arrrghhh on 2011-06-15
So is the website in ~?  Why isn't in in /var/www?  You need to chown www-data to any file/folder the web server needs to hit from the outside... Which is why putting it in ~ seems like a bad idea to me (but it should work if you get the permissions correct...)

---

### Post by flyingsuperhigh on 2011-06-15
If I use the /var/www directory then everything works fine. However, I don't understand why I cannot use the /home/root_user_name/public_html directory.

1)I've modified the /etc/apache2/sites-available/default file and wherever there I found the /var/www/ directory, I replaced it by the /home/root_user_name/public_html directory.

2)I've set the permissions on the /home/root_user_name/public_html directory to 755.

I don't see why it doesn't work when I store the files in the /home/root_user_name/public_html if I have the right permissions.

---

### Post by dtfinch on 2011-06-15
Are you sure the 403 error is coming from your server? Do you use an http proxy on your desktop machine?

---

### Post by arrrghhh on 2011-06-15
> **flyingsuperhigh said:**
> If I use the /var/www directory then everything works fine. However, I don't understand why I cannot use the /home/root_user_name/public_html directory.

1)I've modified the /etc/apache2/sites-available/default file and wherever there I found the /var/www/ directory, I replaced it by the /home/root_user_name/public_html directory.

2)I've set the permissions on the /home/root_user_name/public_html directory to 755.

I don't see why it doesn't work when I store the files in the /home/root_user_name/public_html if I have the right permissions.

Did you miss the part where I mention www-data must own it?  That's in addition to perms.

```
chown -R www-data:www-data /home/root_user_name/public_html
```

---

