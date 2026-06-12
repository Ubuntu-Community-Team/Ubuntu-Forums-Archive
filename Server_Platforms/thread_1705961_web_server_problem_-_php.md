---
title: "web server problem - php"
date: 2011-03-13
forum: Server Platforms
---

### Post by Teh_Messiah on 2011-03-13
Hi
I dont know alot about php or even if that is the problem.

I have a file/webserver using torrentflux-b4rt.
I just used the multiple upload section of it to add about 10 .torrent files and when the page finally refreshed it asked me download the /index.php file instead of loading the page.
I restarted the server and still the same error.
I restarted apache2 and tried again. Again I got the same error.

I had this error with torrentflux a couple of years ago and cant remember what i did to fix it.
I know over the years i have reinstalled Xubuntu a couple of times so I might have done that to fix it but surely there should be a better/easier way to fix it.
I cant login to check my downloads which I assume aren't working.

Please help

---

### Post by Teh_Messiah on 2011-03-13
I needed the downloads so I moved all the torrent files from the tf-b4rt/.transfer dir to the torrentflux/.torrent dir and all the data files from /tf-b4rt/root/ to /torrentflux/root/ and now i cant login to torrentflux either.

I could before but now its not working :confused:

Also I can now login to tf-b4rt
I mv all the data files back to tf-b4rt and it still works.
So It has to be a problem with the *.torrent files surely.
I'll keep you posted

---

### Post by Teh_Messiah on 2011-03-13
Who would have thought that 1 bad torrent file would cause so much trouble!
What a damn head ache.

I moved the data files back to the tf-b4rt/.transfer/ dir and then shifted the *.torrent files to my ~/Downloads dir.

I then proceeded to add the torrent files back 1 at a time until I found the faulty file. As soon as I hit the upload button the page refreshed and told me that the file already existed. I hit the back button and it asked me if I wanted to download the index.php file again!
I then deleted that file and it let me login again!

---

