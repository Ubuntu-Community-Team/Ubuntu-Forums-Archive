---
title: "Referer and Firefox"
date: 2006-12-18
forum: Server Platforms
---

### Post by envis on 2006-12-18
i have used this on one of my Apache virtual hosts to protect to content of the folder named "protected folder"

-------------------------------------------
SetEnvIfNoCase Referer "^http://my.domain.com/" local_ref=1
<Directory /var/www/protected_folder>
Order Allow,Deny
Allow from env=local_ref
</Directory>
-------------------------------------------------


this makes the contents of the "protected folder" only accessible when the URL request Referer header starts with "http://my.domain.com/"....
so for example, if you click a link on my website, "http://my.domain.com/", the browser will say that you have been refered by my webiste and will let you go to the protected folder. but if you try to connect to a url inside the protected folder from something else than a link on my website, it should say forbidden and block the access..
(unless you mess with the header of your url request but that would make you a hacker...)

Now i thoughed this was great and i was in business, but i had only tested it on internet explorer 7 lol!!!!

I have a Firefox on Windows and a Firefox on Ubuntu as well... they both dont work...
i have an internet explorer 7 also on the Windows comp that has Firefox and it was working with Internet Explorer 7 on that same machine...

so.. my great method doesnt seem to work with Firefox.. the protected folder stays blocked...

i first thoughed that perhaps Firefox does not use the Referer header.. but i think it does because my quick research led me to a pluggin to disable the Referer header on Firefox...

on the other hand a test that i did to try to find a solution to the new problem gave me surprising results...

on the "player.php" page (page that contains an object which has a file in the protected folder for source) i wrote (in PHP):
-----------------------------------------------------
$test=apache_getenv("local_ref");
echo 'local_ref: '.$test;
---------------------------------------------
(that is supposed to go read the "local_ref" environment variable and output it on the page)

my big surprise was that when opening player.php in Firefox it said "local_ref: 1" and the song is not loading
when opening player.php on Internet Explorer 7 it says "local_ref:" (looks as if local_ref is just not set) and the song is playing like a charm!!

the opposite would have made more sense to me
why does it not let it through if local_ref is to 1 and why does it let it through if referer appears blank when having no Referer at all (like accessing protected url directly) is correctly blocked?!?!:-k

---

### Post by MJN on 2006-12-19
Envis,
 
Far from me to say what's right and wrong here, but do you *really* need 3 threads running concurrently (they being [http://www.ubuntuforums.org/showthread.php?t=321451](http://www.ubuntuforums.org/showthread.php?t=321451) and [http://www.ubuntuforums.org/showthread.php?t=320523](http://www.ubuntuforums.org/showthread.php?t=320523)) all covering the same/related issue?
 
I know you're keen to get your idea off the ground but there's a danger your threads will overlap (if they haven't already) and the issues will be missed by others following the thread(s) both now and in the future.
 
Sorry I can't help you with your specific problem however just though I'd share my thoughts given it's the third thread asking for help around the same problem!
 
Mathew :)

---

### Post by kerry_s on 2006-12-19
I hate sites who do that->

---

