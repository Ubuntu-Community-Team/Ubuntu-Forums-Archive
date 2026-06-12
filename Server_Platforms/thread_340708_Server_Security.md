---
title: "Server Security"
date: 2007-01-17
forum: Server Platforms
---

### Post by kramerkeller on 2007-01-17
I have a webhost set up and everything is working just fine.  I have all the proper permissions except I am not sure how to prevent one thing.

If I have a file that is an action or javascript file, at the top if the user were to type in the name like

company/folder/thisaction.php

and it will execute the action, I tried to change the permissions, but then I can't execute the actions at all

I don't know if there is a way to make it so certain files can be executed but not seen or typed in the url at the top.  Maybe I need to learn more about sessions.  Any help would be great

---

### Post by jtc on 2007-01-17
Well, there are lots of diffrent ways to solve this, but no matter what I'd suggest you impliment some controll-code in the php-script itself, preventing it from doing any action except under the right conditions. Except that it's kind of hard to advice about other suitible actions, since they all depend on how the rest of the site is built.

---

### Post by kramerkeller on 2007-01-17
I guess I could just set up a session in the action file, that checks first to see where it came from or if someone is logged in, but what if there is a simple javascript or css file on the server and it is file.css

Is there a way to make sure it cannot be viewed just by typing it in the url

Or maybe a picture, I don't know why you would want to block a picture, but how would you put a file in 

folder/myfile and folder/mypicture

Then allow myfile to access mypicture, but not allow users to type mypicture in the url bar

This makes more sense with other files, like javascript, or php, but there must be a way to block users from accessing the file directly through the URL

---

### Post by jtc on 2007-01-17
Well, you can always set up mod_rewrite so it tests if the file request has any of your pages as refer. In case the user simply types in the path to the file, it won't have any refer. If mod_rewrite detects no refer, or simply a bad one, it simply redirect to some well suited errorpage.

This is far from a perfect solution.

1) Some users might have refers disabled. If I'm not totally misstaken I belive Norton Internet Security and its like has this as a default, to protect privacy, they claim. Those users wouldn't really be able to browser your site at all.

2) Refer-check should never really be used as site-security, since refers is sent by the client, and can be faked. What it can do is to protect you from the casual curious.

A better and more secury is to store all files you want to protect outside the webroot. Instead the files will have to be included through a php-script,  in which you do have the appropiate security-checks. When you serve files through a php-script you generally use header('Content-Type: ....') and readfile("/path/to/included/file").

---

### Post by Wim Sturkenboom on 2007-01-18
Not sure what an action file is, but I use jtc's last solution on my sites to hide stuff fopr the visitor.
My tree looks like:
```

some_folder
  |
  +-- site1
   |      |
   |      +---- www
   |      +---- inc
  +-- site2
   |      |
   |      +---- www
   |      +---- inc 

```The document root for each site is set so *some_folder/siteX/www*
Anything that you don't want the visitor to see goes in *some_folder/siteX/inc* (for include). In my case that's i.e. login scripts used to connect to a mysql database.

---

