---
title: "Running web scripts as user instead of user who executes"
date: 2011-10-04
forum: Server Platforms
---

### Post by lcman on 2011-10-04
Hi,

So, I have this server with Nginx on port 80 and Apache on 8080 to serve scripts. I have a user called webmaster and I have my web app files in a directory in the user's home. I added nginx's and apache's users to the webmaster group. I used Wordpress as a test.

Basically, I want the PHP scripts to run as webmaster instead of apache's user because the scripts will need regular write access to the directory. So, if apache's user creates a file, the owner of the directory won't be able to work with the file freely right!

I know this is doable because I've seen it on some shared hosting companies that use Apache with fastcgi. But I'm sure this is doable for my setup as well. Too bad setuid doesn't work on scripts.

I could add webmaster to apache's group and tweak the permissions but I don't want to do that because I will add more users who are going to server websites on this server later!

So, is there a way to tweak the config files to do that?

---

### Post by lcman on 2011-10-05
Ok I forgot there was suEXEC for apache. I'm gonna use that and tweak my setup as per my needs. :popcorn:

---

