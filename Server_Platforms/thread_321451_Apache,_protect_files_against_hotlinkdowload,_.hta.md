---
title: "Apache, protect files against hotlink/dowload, .htaccess? SetEnvIf Referer? PHP?"
date: 2006-12-18
forum: Server Platforms
---

### Post by envis on 2006-12-18
Hi... im looking for ways to protect some audio files on my server that are used to play in an <object> flash mp3 player...

i want the player <object> on my player popup page to be able to play the mp3 files on my server
but i dont want ppl to be able to download or "hotlink" the mp3 files on my server

first way i found to do this is to set this <Directory> directive, which i placed inside of the <VirtualHost> tag i set for the perticular subdomain (i have a main domain(the default apache config(in /etc/apache2/available-sites/)) and a big second file to list all my subdomains (in the same folder), inside of the tag of the subdomain that hosts the radio and the protected files, i set the following <Directory> directive:

SetEnvIfNoCase Referer "^http://mysubdomain\.mydomain\.com" open_the_gates
<Directory /var/www/subdomainroot/protected_folder>
		Order Allow,Deny
		Allow from env=open_the_gates
</Directory>

(ive also tried writting the "^http://mysubdomain\.mydomain\.com" in different ways..
like just: "^http://mysubdomain.mydomain.com" or other complicated ways that looked like: "^http:\/\/mysubdomain.mydomain.com(\/|$)"...
ive also tried putting a SetEnvIfNoCase for each of the possible spelling i found all one after the other to try to be sure to hit the spot..)

result: that works perfectly on my Internet Explorer 7.. the files play, but any attempt to reach /var/www/subdomainroot/protected_folder/ or one of its subdirectories in the browser returned a Permission Denied.. or something like that... 

but on Firefox on Windows and Firefox on Linux, this doesnt seem to work, the file just doesnt load in the player, its blocked.. (i removed the directive and restart apache and songs start playing).. though at least access to /var/www/subdomainroot/protected_folder/ and beyond is successfully blocked...

i was unable to find a way to get this working on Firefox so far...
setting a:
SetEnvIfNoCase Referer "^$" open_the_gates
made it work and might still prevent most hotlinking but then ppl can access the contents of the protected_folder if they can just determine the URL of the mp3 files in there
also if someone hotlinks one of my songs on his webpage and the visitor of his webpage is on Firefox, well i guess the visitor would get the song, and my bandwidth...

----------

another way i was considering but that just doesnt work for some reason... is using a .htaccess file....

apparently if i create a file that i name .htaccess that just contains the text "deny for all" it should be supposed to block all connections to whatever is in and beyond the folder the .htaccess file is in...

so if that worked... i suppose i could try to make PHP file handle the file to remove the deny from all or maybe replace it with allow from [ip of the visitor] so the player can load the file and set it back to deny from all right after...

but when i create the .htaccess file in the protected_folder it doesnt seem to change anything...

can someone help me understand how to user the .htaccess file to do what i want to do or have any other idea how i could protect my files and my bandwidth?

---

### Post by chrisfay on 2006-12-19
I'm not completely sure I get what you're trying to do, but it sounds like protecting your files from hot linking or downloading. If so, you could try a couple things. 

You could place the files you want to protect outside your sites document root and reference them using the full path.  Files you 'want' accessible must be within your docroot though.

To block hotlinking, you can use something like this in a .htaccess file:

RewriteEngine on
RewriteCond %{HTTP_REFERER} !^$
RewriteCond %{HTTP_REFERER} !^http://(www.)?your-domain.com/.*$ [NC]
RewriteRule \.(mp3|fla|mpg)$ - [F]

This will also work for other filetypes, put in whatever you want.

---

### Post by tturrisi on 2006-12-19
See your other post about this subject.
The best way to conserve bandwidth and prevent direct linking would be to store the music files in a mysql db, query the db using php in the window that has the music player.  Or just store the mucic in a php password protected dir and use php code that passes the credentials (values) on to the music player page, or stick those values (crediantial) into a cookie and the music player page checks the valuses in the cookie & if match then the music plays else the user sees a blurb of txt "get lost!".

---

### Post by envis on 2006-12-19
well i have been working a lot on a method that im calling the "mystery folder" right now...

it is funny to see in action and is powerful against hotlinking

basically the trick is:

i have a dir for protected content
inside that dir, all i have is the "mystery folder" and inside the "mystery folder": all my protected content, happy and safe

everytime the player popup is called, a more or less complicated process of PHP and JavaScript does about this:
-retrieves the name of the mystery folder(i can use glob() or MySQL (using glob() right now))
-loads the file in the javaplayer
-and changes the name of the "mystery folder" folder to a new namd chosed randomly (after a few seconds)

i have already managed to set this up tonight and it works very well!

it is obviously 100% hotlink proof (100%? unless some hacker finds a mechaninsm to keep track of the names of your "mystery folder":-k )

i'm still gonna use the directory rules in the apache conf to help things be a bit safer, but i'll have to use a very "open" set of rules to make sure Firefox can work..

also of course this method presents many options and things to consider like either keeping track of the "mystery folder" name with MySQL for speed or using glob() for toughness... MySQL could be great, but if for some reason (too many requests at the same time for example) it loses track of the name of the "mystery folder", then im screwed... no more radio for anybody until i notice and fix it lol....

i use a javascript timer after the file is loaded.. it waits 10 seconds (could be less could be more...) and then loads a width="0" height="0" iframe that runs the PHP script that will change the name of the folder...
-just like that?
-no... actually it checks that its been at least 10 seconds since no one did any request for a song..

anyways... there is so much more i could tell you about this idea... which im sure im not the first to imagine!...

but tturrisi, what you suggested there -> having the songs saved in MySQL is very interesting and i had no idea such a thing was possible!

could it be a much simpler and efficient method to do what im trying to accomplish?

i had no idea an "audio file" could be contained into MySQL...

---

### Post by tturrisi on 2006-12-19
Well, at least you got it working, but see my last post in your other thread.  All you need is htaccess-htpasswd to prevent direct linking.  You may not realize it, but htaccess-htpasswd will lock the directory and ALL sub dirs too.  So if someone direct links to a music file in a sub dir all they will get is the login prompt.  And htaccess-htpasswd works for one session ONLY, meaning while the same browser window is opened.  Close the browser window and you need to re-login.
What you have now is overkill and probably a waste of resources.

yes, anything can be stored in a mysql db table.  See this:
[http://dev.mysql.com/doc/refman/5.0/en/blob.html](http://dev.mysql.com/doc/refman/5.0/en/blob.html)

---

### Post by chrisfay on 2006-12-19
> yes, anything can be stored in a mysql db table. See this:

Be aware that this is somewhat of a hot/debated topic. I am all for it, although there's a lot of opposition as well. Just be careful when writing your queries not to write stuff like:

```
select * from huge_files_table
```

---

### Post by envis on 2006-12-19
where can i read on those debates?

using MySQL to store files seems very interesting but im reading now on MySQL tutoial that "each BLOB requires generally to have 3 copies of it in the memory"...

i am gowing to have a vey large amount of files, space is an issue for me...

is it faster to read files from MySQL or is it faste to read just from "normal folders".....

---

### Post by tturrisi on 2006-12-19
It is faster to to grab files from a dir than an sql table.
Using a sql table to store large files IS tough on server memory & resources, and the queries should be exact, e.g. SELECT xxx.mp3 FROM blues.  Don't do SELECT * FROM blues ORDER BY ID DESC LIMIT 50.  If the server has lots & lots of ram (GBs) then you can get away with it  by using mysql_free_result or other methods of freeing memory, but all in all it's better to use dirs to store large files, esp if have many files.

---

### Post by envis on 2006-12-19
i see... i guess im gonna stick to my mystery folder then.... :P

i guess that my issues are pretty much resolved :)

thanks a lot fo all your precious help tturrisi and chrisfay

i think i will try the .htaccess for extra safety

---

### Post by envis on 2006-12-19
by the way.. the .htaccess file... do you know what permissions i should set and what user? root? www-data?

---

### Post by envis on 2006-12-19
am i supposed to write:
!^http://(www.)?your-domain.com/.*$ [NC]
with the ([www.)?](www.)?) to make it work for mydomain.com and [www.mydomain.com](www.mydomain.com) or its just something you wrote cos you werent sure if i was using the www for my domain name?

---

### Post by tturrisi on 2006-12-20
You already had htaccess in effect, you had just put it in the conf file instead of using a separate .htaccess file!

---

### Post by jawastarz on 2008-01-12
But after a listener has listened to the mp3..
it will be cached and visible in the temporary internet files folder right?

So that would be some sort of downloading..

---

