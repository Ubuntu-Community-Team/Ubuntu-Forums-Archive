---
title: "Allow alias to read sub folders"
date: 2007-03-19
forum: Server Platforms
---

### Post by qwert231 on 2007-03-19
Let's say I have in my virtual hosts file:
Alias /images "/someFolder/fooImages"

And /someFolder/fooImages has sub folders, like Group1 and Group2.

I want to be able to link to those sub folders in this way:
[www.foo.com/images/Group1/file.jpg](www.foo.com/images/Group1/file.jpg)

Beyond the Alias I already have, what do I need to do?

---

### Post by wray.justin on 2007-03-19
Sorry, after re-reading your original post, I see I had made a mistake.

---

### Post by MJN on 2007-03-19
Having read [http://httpd.apache.org/docs/2.0/mod/mod_alias.html#aliasmatch](http://httpd.apache.org/docs/2.0/mod/mod_alias.html#aliasmatch) it looks like AliasMatch is what you're after e.g.

```
AliasMatch ^/images(.*) /someFolder/fooImages$1
```

Mathew

---

### Post by qwert231 on 2007-03-20
Ok... that didn't work... let's try it again.
I have a tree structure like this:

/fileshare
[indent].... bunch of files and folders
/movies
[indent]someMovie.mp4
  /Funny
[indent]firstFunny.mp4
   anotherOne.avi
[/indent]
  /Commercials
[indent]Whazzup.mp4
   SomeCommercial.mov
[/indent]
[/indent]
[/indent]
So, let's say I have a page in my root, called movies.php, and I want links to these 3 files:
/fileshare/movies/someMovie.mp4
/fileshare/movies/Funny/firstFunny.mp4
/fileshare/movies/Commercials/Whazzup.mp4

AliasMatch didn't work for me.

---

### Post by MJN on 2007-03-20
I'm not sure then - from the AliasMatch description it sounded like it would do exactly what you wanted (i.e. alias one directory to another, whilst keeping the sub-path including filename intact).
 
Perhaps I got the syntax wrong? What did your logs say when you tried it? And what happened at the client?
 
Mathew
 
P.S. Please stick to the one example scanario - mixing and matching will only result in misunderstanding!

---

### Post by qwert231 on 2007-03-20
Okay in my mark.phillk.net virtual host file I am now using:
AliasMatch ^/movies(.*) /fileshare/movies$1

(I commented out the alias statements.)

[http://mark.phillk.net/movies.php](http://mark.phillk.net/movies.php)

The movies example is the real deal. Let's stick with that one.

---

### Post by MJN on 2007-03-20
And it works... does it not?
 
For example, I can download [http://mark.phillk.net/movies/Commercials/blindref.mov](http://mark.phillk.net/movies/Commercials/blindref.mov) whereas presumably the movie is actually (on disk) in /fileshare/movies/Commercials/blindref.mov.
 
Incidentally, the file movies.php doesn't exist however that's not relevent here.
 
Mathew

---

### Post by qwert231 on 2007-03-20
Hmm... doesn't work like I want. I don't want an index view. I want the .php page to come up when you do [http://mark.phillk.net/movies.php](http://mark.phillk.net/movies.php), but I don't want [http://mark.phillk.net/movies](http://mark.phillk.net/movies) to show anything.

---

### Post by MJN on 2007-03-20
Okay.. perhaps I misunderstood your original question. Although now the alias mapping is working exactly as your initial post requested... :confused: 
 
Moving on however, where is movies.php actually located?
 
To turn directory listings off you use the **Options -Indexes** directive, and locate it depending on how widespread you want this option e.g. inside <Virtualhost> for the whole site, inside <Directory /somewhere/or/other> for /somewhere/or/other and below, etc.
 
See [http://httpd.apache.org/docs/2.0/mod/core.html#options](http://httpd.apache.org/docs/2.0/mod/core.html#options) for further details.
 
Mathew

---

### Post by qwert231 on 2007-03-20
Sorry, guess I could have worded it better, but thank you for your help.
movies.php is located here:
DocumentRoot /web/

(I have a separate drive mounted as /web. / is on one drive, /fileshare on another, and /web on a third.)

So, now I have this in my Virt Host file:
        AliasMatch ^/movies(.*) /fileshare/movies$1p
	<Directory /fileshare/movies>
		Options -Indexes
	</Directory> 

I believe the /movies(.*) is causing movies.php not to work. I'm not sure how the AliasMatch line is working... maybe an explanation of reg expressions would help me. Is there a site that would help explain it?

---

### Post by MJN on 2007-03-20
Ah I see now...

In that case change it to:

```

AliasMatch ^/movies/(.*) /fileshare/movies/$1

```

So now the URL must contain the trailing slash on movies. This is why seeing your (error) logs is useful as it would've said exactly what was missing when the aliasmatch failed.

By the way, I take it that 'p' is a copy-and-paste typo at the end of your AliasMatch statement?

For regexp just Google - you'll find a more thorough explanation than I could give here (particularly as I'm not that good at 'em! ;))

Mathew

---

### Post by qwert231 on 2007-03-20
Ok... so I've got that... 
Now, if you will, please follow these links:
[http://mark.phillk.net/movies.php](http://mark.phillk.net/movies.php)
From there, try the link to:
[http://mark.phillk.net/moviesCommercials.php](http://mark.phillk.net/moviesCommercials.php)

Should be a list of Commercials.
Then try any of them... tell me what you get.

---

### Post by MJN on 2007-03-20
> **qwert231 said:**
> Ok... so I've got that... 
Now, if you will, please follow these links:
[http://mark.phillk.net/movies.php](http://mark.phillk.net/movies.php)


That's fine - I get your movies page with the three links to categorised clips...

However..

> From there, try the link to:
[http://mark.phillk.net/moviesCommercials.php](http://mark.phillk.net/moviesCommercials.php)
I'm getting the links but clicking on them is revealing File not Found errors.

What is your error log saying?

Mathew

---

### Post by qwert231 on 2007-03-20
[Tue Mar 20 15:02:28 2007] [error] [client 82.46.99.50] Directory index forbidden by rule: /fileshare/movies
[Tue Mar 20 15:02:38 2007] [error] [client 82.46.99.50] File does not exist: /fileshare/moviesCommercials
[Tue Mar 20 15:02:42 2007] [error] [client 82.46.99.50] Directory index forbidden by rule: /fileshare/movies
[Tue Mar 20 15:03:04 2007] [error] [client 82.46.99.50] File does not exist: /fileshare/moviesCommercials, referer: [http://mark.phillk.net/moviesCommercials.php](http://mark.phillk.net/moviesCommercials.php)

---

### Post by MJN on 2007-03-20
Were there no other errors? There should be a whole stack of .mov file errors too!

Mathew

---

### Post by qwert231 on 2007-03-20
Here is what else I've gotten:
[Tue Mar 20 14:58:43 2007] [error] [client 82.46.99.50] File does not exist: /fileshare/moviesFunny, referer: [http://mark.phillk.net/moviesWow.php](http://mark.phillk.net/moviesWow.php)
[Tue Mar 20 15:02:28 2007] [error] [client 82.46.99.50] Directory index forbidden by rule: /fileshare/movies
[Tue Mar 20 15:02:38 2007] [error] [client 82.46.99.50] File does not exist: /fileshare/moviesCommercials
[Tue Mar 20 15:02:42 2007] [error] [client 82.46.99.50] Directory index forbidden by rule: /fileshare/movies
[Tue Mar 20 15:03:04 2007] [error] [client 82.46.99.50] File does not exist: /fileshare/moviesCommercials, referer: [http://mark.phillk.net/moviesCommercials.php](http://mark.phillk.net/moviesCommercials.php)
[Tue Mar 20 15:12:24 2007] [error] [client 82.46.99.50] File does not exist: /fileshare/moviesCommercials, referer: [http://mark.phillk.net/moviesCommercials.php](http://mark.phillk.net/moviesCommercials.php)
[Tue Mar 20 15:12:26 2007] [error] [client 192.168.15.3] File does not exist: /fileshare/moviesCommercials, referer: [http://mark.phillk.net/moviesCommercials.php](http://mark.phillk.net/moviesCommercials.php)
[Tue Mar 20 15:24:37 2007] [error] [client 192.168.15.3] File does not exist: /fileshare/moviesCommercials, referer: [http://mark.phillk.net/moviesCommercials.php](http://mark.phillk.net/moviesCommercials.php)
[Tue Mar 20 15:33:42 2007] [error] [client 141.211.187.11] File does not exist: /fileshare/moviesFunny, referer: [http://mark.phillk.net/moviesWow.php](http://mark.phillk.net/moviesWow.php)
[Tue Mar 20 15:33:49 2007] [error] [client 141.211.187.11] File does not exist: /fileshare/moviesFunny, referer: [http://mark.phillk.net/moviesWow.php](http://mark.phillk.net/moviesWow.php)
[Tue Mar 20 15:33:55 2007] [error] [client 141.211.187.11] File does not exist: /fileshare/moviesFunny, referer: [http://mark.phillk.net/moviesWow.php](http://mark.phillk.net/moviesWow.php)

---

### Post by MJN on 2007-03-20
Hmmm...

Can you confirm exactly what AliasMatch directive you've now got?

Mathew

---

### Post by qwert231 on 2007-03-20
#
#  mark.phillk.net (/etc/apache2/sites-available/mark.phillk.net)
#
<VirtualHost *>
        ServerAdmin 
        ServerName  mark.phillk.net
        ServerAlias mark.phillk.net

        # Indexes + Directory Root.
        DirectoryIndex index.html index.php index.htm
        DocumentRoot /web/

        # CGI Directory
        # ScriptAlias /cgi-bin/ /web/cgi-bin/
        # <Location /cgi-bin>
        #         Options +ExecCGI
        # </Location>
    
        AliasMatch ^/movies/(.*) /fileshare/movies$1
        #Alias /movies "/fileshare/movies"
        #Alias /movies/Funny "/fileshare/movies/Funny"
        #Alias /movies/Commercials "/fileshare/movies/Commercials"
	<Directory /fileshare/movies>
		Options -Indexes
	</Directory> 


	 <Location /GreatWhite>
		Order Deny,Allow
		Deny from all
	</Location>
        # Logfiles
        ErrorLog  /home/www/web/logs/error.log
        CustomLog /home/www/web/logs/access.log combined
</VirtualHost>

---

### Post by MJN on 2007-03-20
You certainly need an extra slash on your aliasmatch line i.e:

```

        AliasMatch ^/movies/(.*) /fileshare/movies/$1

```

I may have initially missed it in my post, when you received the e-mail confirmation (is there where you copied it from?), bit I soon added it in...

Mathew

---

### Post by qwert231 on 2007-03-21
Ah, yes!!! Thank you... I knew I forgot something small!!! Try it out.

---

### Post by MJN on 2007-03-21
Working! Phew!
 
Must now go and lie down.... ;)
 
Mathew
 
P.S. You might want to remove your e-mail address from the config on here to stop it getting scraped by spambots...

---

