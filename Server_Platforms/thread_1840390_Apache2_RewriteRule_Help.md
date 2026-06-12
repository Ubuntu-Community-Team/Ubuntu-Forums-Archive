---
title: "Apache2 RewriteRule Help"
date: 2011-09-07
forum: Server Platforms
---

### Post by geudrik on 2011-09-07
I have a web server that forces SSL, which is exactly what I want, and it works swingingly.  The following is the rule that I am using to achieve this.
```

        RewriteEngine   on
        RewriteCond     %{SERVER_PORT} ^80$
        RewriteRule     ^(.*)$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R]

```

Now, I have a single file in the root, called stream.php that I need to serve on an HTTP (note: not HTTPS) connection.  Sadly, I have to, I really don't have an option.  Using mod-rewrite, how can I set a rule up to allow only this single file to be served on a normal unencrypted connection?

---

### Post by geudrik on 2011-09-07
Anyone have any idea? :s

---

### Post by Dangertux on 2011-09-07
Oops I'm sorry I totally meant to reply to this thread earlier and got pulled away from the computer in the middle of typing the response.

try something along these lines you will have to mess with syntax a little bit though.

```
[COLOR=#003399][COLOR=Black]
RewriteEngine On [/COLOR]
[COLOR=Black]RewriteCond %{THE_REQUEST} ^[a-z]{3,9}\ /stream\.php\ HTTP/ [NC] [/COLOR]
[COLOR=Black]RewriteRule ^.*stream\.php$[/COLOR][/COLOR] http://mysite.com:80/ [R=301,L]

```[COLOR=Black][COLOR=#000000]

That should get your most of the way there.
[/COLOR][/COLOR]

---

### Post by geudrik on 2011-09-08
Thank you Dangertux, that's awesome!  I'll start fooling around with this now.. I have one concern however...

I can work my way around regex, but I am certainly not as proficient as I'd like to be. That being said, my concern is that using that rewrite condition, will apache not pick back up on the http connection after rewrite has taken over, and force it back to SSL because of my rule?  (infinite loop?)

This is where my lack of experience screwing around with apache shines brightly...

Edit: Alright, after doing a little derping, I came up with a list of steps for my self.
a) Write Condition and Rule in my <vhost 443> block to redirect /stream.php?bla.. back to :80
b) Write Condition and Rule in my <vhost 80> block to ALLOW a :80 connection for only /stream.php?bla...

Does order matter when writing Conditions and Rules for Apache2?

---

### Post by Dangertux on 2011-09-08
That's why the [C]

If that rule is successful the next shouldnt be processed if it fails move to next etc

---

### Post by geudrik on 2011-09-08
in ```


<VirtualHost *:80>
        RewriteEngine   on

        # Need rule to allow /stream.php to serve on :80

        RewriteCond     %{SERVER_PORT} ^80$
        RewriteRule     ^(.*)$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R]

</VirtualHost>


<VirtualHost _default_:443>
        # Rewrite rule to allow stream.php to be accessed on HTTP
        RewriteCond   %{THE_REQUEST} ^[a-zA-Z0-9]{3,9}\ /stream.php%{REQUEST_URI} HTTP/ [NC]
        RewriteRule   ^.*stream\.php%{REQUEST_URI}$ http://%{SERVER_NAME}:80 [R=301,L]
...
</VirtualHost>

```

It's horribly broken, but I'm trying :D   Suggestions/Corrections more than appreciated :) I'm pretty shaky with regex

---

### Post by geudrik on 2011-09-08
Alright.. So why doesn't this work?
```
<VirtualHost *:80>
        RewriteEngine   on

        # Check to see if /stream.php is called for, and stay on :80 if so
        RewriteCond     ^(.*)$ http://%{SERVER_NAME}/stream.php%{REQUEST_URI}$
        RewriteRule     $ [L]

        # Force SSL Connection
        RewriteCond     %{SERVER_PORT} ^80$
        RewriteRule     ^(.*)$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R]

</VirtualHost>

<VirtualHost _default_:443>

        # Redirect SSL connection of /stream.php back to :80
        RewriteEngine   on
        RewriteCond %{THE_REQUEST} ^[a-zA-Z0-9]{0,200}\ /stream\.php\ HTTP/ [NC]
        RewriteRule ^.*stream\.php%{REQUEST_URI}$ http://%{SERVER_NAME}:80/ [R=301,L]

...

```

---

### Post by Dangertux on 2011-09-08
Actually - I think we're both thinking about this the wrong way... Let's try something more along these lines.
```

RewriteCond     %{SERVER_PORT}%{REQUEST_URI} ^80$ !\stream.php$         
RewriteRule     ^(.*)$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R]

```That SHOULD simply force the rewrite to apply to anything  that ISN'T stream.php. Play with it and see if you can make it work for you.

---

### Post by geudrik on 2011-09-08
I updated my last post with as far as I was able to get. Your idea I like, though sadly given my code that won't work (but I could just change my code).  But, it also doesn't work. My Apache2 refuses to start with that, and I have no idea why :( Error logs show no indication.

---

### Post by Dangertux on 2011-09-08
Hmm...Mod_Rewrite is a tempermental beast :-)

I actually think the code I posted above won't work in this scenario because it needs a -f switch. Which you can't use if you specify a URI. So that might need to be scrapped.

I'm not sure why the code that you just updated isn't working though. That should work.

Have you tried this.

```

RewriteRule   ^.*stream\.php%{REQUEST_URI}$ http://%{SERVER_NAME}%{REQUEST_URI}:80 [R=301,L]
```

---

### Post by geudrik on 2011-09-08
No dice :(  And you're quite right, it really is a pesky bugger!

Here's what I'm using currently. Trying to access FROM a :80 connection reverts :443 and accessing from :443 stays on :443.  :(

```

<VirtualHost *:80>
        RewriteEngine   on

        # Check to see if /stream.php is called for, and stay on :80 if so
        RewriteCond     ^(.*)$ http://%{SERVER_NAME}/stream.php%{REQUEST_URI}$
        RewriteRule     $ [L]

        # Force SSL Connection
        RewriteCond     %{SERVER_PORT} ^80$
        RewriteRule     ^(.*)$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R]


</VirtualHost>

<VirtualHost _default_:443>

        # Redirect SSL connection of /stream.php back to :80
        RewriteEngine   on
        RewriteCond %{THE_REQUEST} ^[a-zA-Z0-9]{0,200}\ /stream\.php\ HTTP/ [NC]
        RewriteRule   ^.*stream\.php%{REQUEST_URI}$ http://%{SERVER_NAME}%{REQUEST_URI}:80 [R=301,L]
...

```

---

### Post by Dangertux on 2011-09-08
> **geudrik said:**
> No dice :(  And you're quite right, it really is a pesky bugger!

Here's what I'm using currently. Trying to access FROM a :80 connection reverts :443 and accessing from :443 stays on :443.  :(

```

<VirtualHost *:80>
        RewriteEngine   on

        # Check to see if /stream.php is called for, and stay on :80 if so
        RewriteCond     ^(.*)$ http://%{SERVER_NAME}/stream.php%{REQUEST_URI}$
        RewriteRule     $ [L]

        # Force SSL Connection
        RewriteCond     %{SERVER_PORT} ^80$
        RewriteRule     ^(.*)$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R]


</VirtualHost>

<VirtualHost _default_:443>

        # Redirect SSL connection of /stream.php back to :80
        RewriteEngine   on
        RewriteCond %{THE_REQUEST} ^[a-zA-Z0-9]{0,200}\ /stream\.php\ HTTP/ [NC]
        RewriteRule   ^.*stream\.php%{REQUEST_URI}$ http://%{SERVER_NAME}%{REQUEST_URI}:80 [R=301,L]
...

```

Maybe...
```

RewriteCond %{REQUEST_FILENAME} -f !/stream.php$
RewriteCond %{REQUEST_URI} !(/$) 
RewriteCond %{SERVER_PORT} 80 
RewriteRule (.*) https://www.mysite.com/$1/ [R=301,L]

RewriteCond %{SERVER_PORT} 80 
RewriteRule ^(.*)$ https://www.mysite.com/$1 [R,L]	  

```

That implements the not stream.php file concept we discussed earlier.

---

### Post by geudrik on 2011-09-08
```

Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!

```

Aaaand of course, the logs have nothing to say for themselves >.< lol why does everything I do have to be so hard :P

Do we have any other takes that want to take a crack at this riddle? :P

---

### Post by geudrik on 2011-09-10
Anybody? :s  This can't be impossible to do :(  Thank you so much, Dangertux for all of the help thus far.

---

### Post by geudrik on 2011-09-13
Alright, I'm making progress...


Here is my current Apache2 redirect config. 
```

<VirtualHost *:80>
        RewriteEngine   on

        RewriteLog      /var/log/apache2/rewrite.log
        rewriteLogLevel 9

        # Force SSL Connection
        # RewriteCond   %{SERVER_PORT} ^80$
        # RewriteRule   ^(.*)$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R]

        RewriteCond     %{REQUEST_FILENAME} !stream.php
        RewriteCond     %{HTTPS} =off
        RewriteRule     ^(.*)$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R]

</VirtualHost>

<VirtualHost _default_:443>

        # Redirect SSL connection of /stream.php back to :80
        RewriteEngine   on

        RewriteLog      /var/log/apache2/rewrite.log
        rewriteLogLevel 9

        RewriteCond     %{REQUEST_FILENAME} stream.php
        RewriteRule     ^(.*)$ http://%{SERVER_NAME}%{REQUEST_URI} [L,R]

...
</VirtualHost>

```

The forcing to HTTPS seems to be working properly, but when I try to request stream.php on https, I see my error page.

Here is the log for modrewrite... Now I'm really stuck...
```

0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119abb90/initial] (2) init rewrite engine with requested uri /stream.php
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119abb90/initial] (3) applying pattern '^(.*)$' to uri '/stream.php'
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119abb90/initial] (4) RewriteCond: input='/stream.php' pattern='stream.php' => matched
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119abb90/initial] (2) rewrite '/stream.php' -> 'http://somesite.com/stream.php'
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119abb90/initial] (2) explicitly forcing redirect with http://somesite.com/stream.php
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119abb90/initial] (1) escaping http://somesite.com/stream.php for redirect
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119abb90/initial] (1) redirect to http://somesite.com/stream.php [REDIRECT/302]
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f221198f4b0/initial] (2) init rewrite engine with requested uri /stream.php
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f221198f4b0/initial] (3) applying pattern '^(.*)$' to uri '/stream.php'
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f221198f4b0/initial] (4) RewriteCond: input='/stream.php' pattern='!stream.php' => not-matched
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f221198f4b0/initial] (1) pass through /stream.php
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f2211987920/initial/redir#1] (2) init rewrite engine with requested uri /var/www/error.php
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f2211987920/initial/redir#1] (3) applying pattern '^(.*)$' to uri '/var/www/error.php'
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f2211987920/initial/redir#1] (4) RewriteCond: input='/var/www/error.php' pattern='!stream.php' => matched
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f2211987920/initial/redir#1] (4) RewriteCond: input='off' pattern='=off' => matched
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f2211987920/initial/redir#1] (2) rewrite '/var/www/error.php' -> 'https://somesite.com/var/www/error.php'
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f2211987920/initial/redir#1] (2) explicitly forcing redirect with https://somesite.com/var/www/error.php
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f2211987920/initial/redir#1] (1) escaping https://somesite.com/var/www/error.php for redirect
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116bbb48][rid#7f2211987920/initial/redir#1] (1) redirect to https://somesite.com/var/www/error.php?error=404 [REDIRECT/302]
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119a2490/initial] (2) init rewrite engine with requested uri /var/www/error.php
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119a2490/initial] (3) applying pattern '^(.*)$' to uri '/var/www/error.php'
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119a2490/initial] (4) RewriteCond: input='/var/www/error.php' pattern='stream.php' => not-matched
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119a2490/initial] (1) pass through /var/www/error.php
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119ad288/initial/redir#1] (2) init rewrite engine with requested uri /error.php
0.0.0.0 - - [13/Sep/2011:11:27:14 --0400] [somesite.com/sid#7f22116beef8][rid#7f22119ad288/initial/redir#1] (3) applying pattern '^(.*)$' to uri '/error.php'


```

---

### Post by Dangertux on 2011-09-13
Meh -- running out of ideas but have you tried 

```

!/stream.php

```instead of just

```

!stream.php

```I'm not 100% on that but it doesn't look right. Possibly needs some wildcarding. Or try filtering it by URI instead of filename... Just some suggestions. Want better alternative to mod_rewrite :-(

Alternatively if you can't get this working you could always create a VHOST and host stream.php on that server. Obviously depending on what stream.php does this could be a potential for a lot of XSS / CSRF problems.

---

### Post by geudrik on 2011-09-16
Solved!  I think we we're over thinking this, Dangertux...

```

<VirtualHost *:80>
        RewriteEngine   on

        # RewriteLog    /var/log/apache2/rewrite.log
        # rewriteLogLevel       5

        #Try #293 - ONLY redirect if !stream.php
        RewriteCond     %{SCRIPT_FILENAME} !/stream.php
        RewriteRule     ^(.*)$ https://%{SERVER_NAME}%{REQUEST_URI} [L,R=301]

        DocumentRoot    /var/www
</VirtualHost>

<VirtualHost _default_:443>

        RewriteEngine   on

        # RewriteLog      /var/log/apache2/rewrite.log
        # rewriteLogLevel 5

        # Force /stream.php to be served on HTTP, { NOT } HTTPS
        RewriteCond     %{SCRIPT_FILENAME} /stream.php
        RewriteRule     ^(.*)$ http://%{SERVER_NAME}%{REQUEST_URI} [L,R]


```

---

