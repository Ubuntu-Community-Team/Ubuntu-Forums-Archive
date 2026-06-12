---
title: "Symfony, Apache and UserDir Module"
date: 2007-06-14
forum: Server Platforms
---

### Post by LebowskiT1000 on 2007-06-14
Anyone out there using Apache with the UserDir module enabled along with the Symfony PHP framework together?  I'm attempting to make the three of them play nicely but it just isn't working out.

I seem to be able to get Apache and the UserDir Module to work correctly, I go to [http://www.domain.com/~user](http://www.domain.com/~user) and it takes me the appropriate place (although I have to call out the file specifically i.e. [http://www.domain.com/~user/index.php](http://www.domain.com/~user/index.php).  I get a 404 Not Found if I don't put index.php in the URL.  I've checked the permissions on all the directories and files several times, perhaps I'm missing something.  That's the first of my many problems with this set up.

My second problem is that symfony doesn't seem to know where any of my javascript/css/images are when I try to load the site in this method (calling the file out specifically).  Some path/to/something is screwed up something, I'm sure.

Lastly, I've read online that I need to disable options in the .htaccess file that is in my root web directory, in this case it is the default symfony web directory: /home/user/public_html/dir1/web.

So, I commented out the line: "Options +FollowSymLinks +ExecCGI " form the .htaccess the symfony creates in the web directory.

Anyone have any helpful hints, walk through, explanations, links to read or suggestions?  Getting very frustrated here.  Thanks.

---

