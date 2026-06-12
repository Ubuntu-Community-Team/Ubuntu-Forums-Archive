---
title: "password protected directories on apache, doesnt want to take my password..."
date: 2006-12-17
forum: Server Platforms
---

### Post by envis on 2006-12-17
i am trying to password protect a directory on my webserver but the login box in the browser doesnt want to accept my login...

i set the directory like that
<Directory /var/www/radio/music>
AllowOverride AuthConfig
AuthType Basic
AuthName "Restricted FIles"
AuthUserFile /home/secure/apasswords
Require test
</Directory>

restarted apache

created the "secure" folder in "home"

did sudo htpasswd -c /home/secure/apasswords test
set the password to "test"

did grep - '^User' /etc/apache2/apache2.conf to find out the type of user apache uses

it says: User www-data..

i manually set the apasswords file to www-data but i also did 
sudo chown www-data:www-data /home/secure/apasswords
sudo chmod 0660 /home.secure/apasswords
as some website recommended me too...

and what else?.. i restarted my server... "sudo /etc/init.d/apache2 reload" many, many times...

and the authentication process seems to basically work.. because it does ask me for my password. but i write "test" "test" in the box and it just comes back... on the 3rd time it doesnt come back anymore and the song doesnt play...

after that i actually *think i could make PHP login the player transparently by setting values on $PHP_AUTH_PW and $PHP_AUTH_USER.. so that no one gets to see the password, and only the music player can have axs to the songs to stream them, ppl would not be able to pick up the file by going to its url cos it would ask for a password...

well... i use a flash player to play the songs, i've learned that it save the file in its temp folder anyways... but oh well... i just wanna at least tighten the security for most normal users : ) ....

and right now im just wondering Why doesnt that password work?? it looks like it should work.... is there something extra i need to install? does any one have any idea why it doesnt take the username "test" and password "test" when, it should...

---

### Post by houstonbofh on 2006-12-17
> **envis said:**
> i am trying to password protect a directory on my webserver but the login box in the browser doesnt want to accept my login...

i set the directory like that
<Directory /var/www/radio/music>
AllowOverride AuthConfig
AuthType Basic
AuthName "Restricted FIles"
AuthUserFile /home/secure/apasswords
Require test
</Directory>

restarted apache

created the "secure" folder in "home"

did sudo htpasswd -c /home/secure/apasswords test
set the password to "test"

...
When it asks for a password you type *mypassowrd*  The file /home/secure/apasswords will have the user name 'test' and a hash for 'mypassword' in it.  How you pass this is a subject of your application, not apache.

---

### Post by envis on 2006-12-17
well, yea.. i do the htpasswd thing
"sudo htpasswd -c /home/secure/apasswords test"
it asks me "new password?" i write "test"..
it asks "type password again".. i re-type "test"...

so the user should be "test" and the password should be "test"...

the <Directory> in apache settings also says "Require test"
i tried playing with that, but if i say "Require user test" for example, it doesn't ask for password anymore...

so normally the name and password should be "test" and "test"...

though when i access that directory from another computer on internet explorer 7 or another computer with Firefox as well, it just doesnt take my login for username "test" and password "test"..

i tried accessing the directory from the Firefox in the Ubuntu "server" as well (which is actually a desktop Ubuntu).. same results..

i dont understand why this doesnt work...

---

### Post by tturrisi on 2006-12-17
it should not be:
require test
it should be:
require valid-user

Your htpasswd file should contain the username & password:
username:encryptedpassword

---

### Post by envis on 2006-12-17
Thank you so much tturrisi!!!!

i changed the "Require test" for "Require valid-user" and now its working!

---

### Post by envis on 2006-12-17
<Directory /var/www/radio/music>
AllowOverride AuthConfig
AuthType Basic
AuthName "Restricted FIles"
AuthUserFile /home/secure/apasswords
Require valid-user
</Directory>

---

### Post by envis on 2006-12-17
does anyone knwo by any chance if theres a way PHP could login the user transparently in the background?...

i would like a way to restrict access to the protected files to a "music player" popup browser window...

---

### Post by MJN on 2006-12-18
Just going back to your **require** directive, if you *did* want to restrict access to a particular user (yet have just a single password files containing all users/passwords) then the correct line to use would be **require user <username>**
 
So you weren't that far off!
 
(sorry, can't help you with your follow-on question)
 
Mathew

---

### Post by tturrisi on 2006-12-18
> **envis said:**
> does anyone knwo by any chance if theres a way PHP could login the user transparently in the background?...

i would like a way to restrict access to the protected files to a "music player" popup browser window...
Yes, you could use php to set a cookie nd the popup window could contain php code that checks if the cookie exists, read it and allow or disallow:  example:
after using htaccess & htpassword to get access to the dir, the index page in that dir would contain something like this at the very top of page:
```
php?
//prevent caching of page
header('Expires: Mon, 26 Jul 1997 05:00:00 GMT'); 

header('Cache-Control: no-store, no-cache, must-revalidate'); header('Cache-Control: post-check=0, pre-check=0', FALSE); 

header('Pragma: no-cache');
// set a cookie 
for a valid user
$user = "is-allowed";


setcookie("valid_user",$user);
?>
```
The popup window player would have this at the top:
```
//prevent caching of page
header('Expires: Mon, 26 Jul 1997 05:00:00 GMT'); 
header('Cache-Control: no-store, no-cache, must-revalidate'); 
header('Cache-Control: post-check=0, pre-check=0', FALSE); 
header('Pragma: no-cache');
$validated = $HTTP_COOKIE_VARS["valid_user"];
if(isset($_COOKIE['valid_user'])) {
?>
music player code here beginning with <html>
<?php
}
else {
?>
<p>get lost lamer!</p>
<?php
}
?>
</body>
</html>
```

Basically, if someone gets in with htaccess/htpasswd they are considered to be trusted & will receive a general cookie.  The cookie is then required to access the popup player & if it does not exist  they cannot use the player.  To prevent any issues if users have cookies disabled in their browser it is wise to first check if they have cookies enabled & inform them that they nust enable them in the event they have cookies disabled. Do this using a test-cookie script on the index page:
```

// Check if cookie has been set or not

if ($_GET['set'] != 'yes') {

// Set cookie

setcookie ('test', 'test', time()+14400,"/");

// Reload page

header ("Location: checkcookies.php?set=yes");

} 

else {



// Check if cookie exists

if (!empty($_COOKIE['test'])) {

header ("Location: ./");

} 

else {

?>
<p>Cookies are required to use this site</p>
<?php


} //end if empty cookie

} //end if set=yes

?>
</body>
</html>
```

---

### Post by envis on 2006-12-18
Thanks again tturrisi there is a lot of stuff i didnt know in what you explained there

but if i understand well, this bascally limits the access to read the code of the player?

my goal is to prevent ppl from downloading the songs (by putting the url of the mp3 file in a browser for example)
and also to prevent them from linking to my mp3s on their webpage... they would be stealing my music and my precious bandwidth!

i really thoughed about that and researched this last.. day and a half?.. and in the end i found the answer i needed to have a good basic security.
an article called: Keeping Your Images from Adorning Other Sites
found it at: [http://www.serverwatch.com/tutorials/article.php/1132731](http://www.serverwatch.com/tutorials/article.php/1132731)

and basically i did:

SetEnvIfNoCase Referer "^[http://*my.domain.com](http://*my.domain.com)*/" local_ref=1
<Directory /var/www/*protected_folder*>
    Order Allow,Deny
    Allow from env=local_ref
</Directory>

this makes the folder named *protected_folder* only accessible if linked from the website at the domain name specified *my.domain.com*

so when the player on my website loads the mp3, it plays, but if you put the url of the protected folder it says Forbidden!

---

### Post by envis on 2006-12-18
sorry made a typo!

good version:
-------------------------------------------
SetEnvIfNoCase Referer "^http://my.domain.com/" local_ref=1
<Directory /var/www/protected_folder>
Order Allow,Deny
Allow from env=local_ref
</Directory>
-------------------------------------------------

its env=local_ref, not env-local_ref.....

---

### Post by tturrisi on 2006-12-18
Ok, then that's much simpler!

---

### Post by envis on 2006-12-18
it turned out that this method was not working in Firefox, i had only tested on Internet Explorer 7 for which it worked...

i am again looking for a solution..

---

### Post by MJN on 2006-12-19
Relying on explicit referers is (as you've found) fraught with problems - some clients can't send them, some may decide not to send them, some get them wrong and finally some will even send whichever referer you happen to be looking for (e.g. your own site)!
 
Mathew

---

### Post by tturrisi on 2006-12-19
> my goal is to prevent ppl from downloading the songs (by putting the url of the mp3 file in a browser for example)
and also to prevent them from linking to my mp3s on their webpage... they would be stealing my music and my precious bandwidth!

Hold on a minute, I just realized that all you need is the original solution you implemented, the htaccess-htpasswd.  Nobody can direct link or leech content in that dir or any subdirs successfully.  Even if a site direct links to your musicplayer, the user who clicks their link to your file will get prompted for a username & password.  You had all you needed the first time around!

---

### Post by MJN on 2006-12-19
Well done tturrisi, sometimes the simplest solution is staring you right in the face! :-)
 
Mathew

---

