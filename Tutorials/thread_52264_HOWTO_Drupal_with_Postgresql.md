---
title: "HOWTO: Drupal with Postgresql"
date: 2005-07-27
forum: Tutorials
---

### Post by jimcooncat on 2005-07-27
This howto is currently in the draft stage; possibly incomplete as I need to test it again. But if you're looking to install Drupal with a Postgresql backend, these tips will help. I found most of the info on a now-defunct web page, and thanks to Adrian who wrote it. Link to Google's cache of his page: [http://shortify.com/1217](http://64.233.161.104/search?q=cache:gVQO2s1Cz6cJ:www.smop.co.uk/node/2+drupal+postgres&hl=en) 

Install in order with apt-get, aptitude, or whatever you like:
[list=1]
[*]apache or apache2
[*]postgresql
[*]php4-pgsql
[*]drupal
[/list] 

Drupal will accept Postgresql as a dependency, but the current package (4.5.2-3) doesn't create the required Postgres user, database, or language. It looks as if running 'sudo dpkg-reconfigure drupal' after installation would be the way to go, but it didn't work for me; apparently the permissions weren't set up correctly.

[list=1]
[*]Su to the postgres user.```
sudo su - postgres
``` 
[*]Create the drupal user and supply a password for it when prompted.```
createuser --no-adduser --no-createdb --pwprompt --encrypted drupal

# or

createuser -A -D -P -E drupal
``` 
[*]Create the drupal database. ```
createdb --owner=drupal drupal
``` 
[*]Edit Postgresql's authentication file to allow drupal to use the database. This was the part that tripped me up. Lines in this file are processed in order, so the drupal lines **must** be placed before any lines of the same TYPE which the user is "all". You can just add the lines at the top of the file to avoid any hassles.```
# log back out, and edit the file
exit
sudo gedit /etc/postgresql/pg_hba.conf

# add this line before any "local * all" (using sockets)
local   drupal      drupal                                          md5

# add this line before any "host * all" (using tcp)
host    drupal      drupal      127.0.0.1         255.255.255.255   md5

# then save and exit the editor.

``` 
[*]Restart the database server. Be careful to check out if this will mess up other database users!?! If you didn't have a Postgresql install before now, then no worries.```
sudo /etc/init.d/postgresql restart
``` 
[*]Log back in as postgres.```
sudo su - postgres
``` 
[*]Check that the drupal user can connect. If you get errors on this command, you'll have to recheck your setup. 
```
# runs psql with user drupal, prompts for password, opens database drupal
psql -U drupal -W drupal

# Watch for any errors here

# Quit psql
\q
```
[*]Start psql using the database; the user will be 'postgres', as that's the current linux user, and it's the superuser of the database. We then run two SQL commands to teach postgresql to use the PL/pgSQL language. 
```
psql drupal

CREATE FUNCTION plpgsql_call_handler() RETURNS language_handler AS
    '$libdir/plpgsql' LANGUAGE C;

CREATE TRUSTED PROCEDURAL LANGUAGE plpgsql
    HANDLER plpgsql_call_handler;

# Quit psql
\q

```
[*]Now we load the database with the default tables and stuff. You'll see two errors at the end; these are actually the two language commands we just ran as the postgres user. That's the main reason for this howto, because when the Debian devs went to fix a bug, they just slapped the two commands on the end of this file, without adjusting the install to run them as the database superuser. ```
 psql -U drupal -W drupal </usr/share/drupal/database/database.pgsql
```
[*]You should be set now to run Drupal!```
# Get back to your own user prompt.
exit

# Run drupal. Substitute your hostname and browser appropriately.
firefox http://localhost/drupal &

```
[/list]
On Adrian's page, he ran into a couple more things which I didn't.
> 
Trying to browse [http://hostname/drupal/](http://hostname/drupal/) failed - no configuration defined. So I copied /usr/share/doc/drupal/examples/conf.php to /etc/drupal and edited it - setting $db_url and $base_url appropriately (don't forget the "/drupal" on $base_url).

Now I got a complaint that pg_connect was not defined, so I installed php4-pgsql and restarted Apache


---

### Post by jimcooncat on 2005-07-28
Have filed a bug about the installation not creating the drupal user and database. If they fix this bug, there will be no need for this howto.
[https://launchpad.ubuntu.com/malone/bugs/1599/](https://launchpad.ubuntu.com/malone/bugs/1599/)

---

### Post by dude2425 on 2005-07-28
I did a quick sudo dpkg-reconfigure drupal and it worked just fine for me. It took me some screwing around to finally try it though.

I would have never tryed to get it to work if I didn't see this post. I was looking for something to do.

---

### Post by jimcooncat on 2005-07-28
Wow. I wonder what the heck I did so that it didn't work for me! Conversely, I wonder if you might have had something already set up that allowed it to work.

Next week, hopefully, I'll try this out on my Ubuntu server at work, and verify the results.

---

### Post by dude2425 on 2005-07-28
did you try a sym link from /usr/share/drupal to /var/www/drupal?
I think I did that before I finaly figured it out. dpkg-reconfigure sets up a database for you though as long as you enter the usernames and passwords and all that jazz for it. I tryed a few things before hand too, I just don't remember what they all were, and I think I undid a few of them after they didn't work. also make sure when you reconfigure, choose apache or apache2 depending on what you have installed. I had a drupal.conf in my /etc/apache/conf.d, so I think it automaticaly chose apache and not apache2 or something.

I'm just playing with apache and php and all that stuff on localhost so I have something to do. I don't really know how to publish anything onto the web or anything, and my dad'll kick my strait in the arse if I did.

---

### Post by jimcooncat on 2005-07-28
[QUOTE=dude2425]did you try a sym link from /usr/share/drupal to /var/www/drupal?[/QUOTE]

Nope, I never did that. I still don't have a symlink there. It works, though, as it sets the directory up in apache's conf.

[QUOTE=dude2425]I don't really know how to publish anything onto the web or anything, and my dad'll kick my strait in the arse if I did.[/QUOTE]

LOL! My ISP has port 80 blocked, so I can't either from my house! Guess I'll be getting a web host, probably one of those with UML so I can have an Ubuntu live on the wire.

---

### Post by mok0 on 2012-06-22
When upgrading to postgresql 9.1, be aware that the default port number of the server has changed from 5432 to 5433.

Therefore, in the file sites/default/settings.php, you need to specify the correct port number.

---

