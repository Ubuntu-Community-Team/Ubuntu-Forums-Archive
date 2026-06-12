---
title: "problem with apache"
date: 2010-02-06
forum: Server Platforms
---

### Post by overtone on 2010-02-06
Ok, let me start from the beginnning.

Im a computer science student have been studying nothing but java for the last two years.

im starting too htink my course is a joke because of this and theres no web development modules that cover server side stuff.

anyway, today i took the plunge and switched from windows 7t to ubuntu 9.10.

and since i was in an experimental mood, ive decided too learn php.

from what i understood, you need apache server, php, environment and mysql.

ive followed most of the tutorials i can find, some of them were severely limited in instruction but finally i found one that was very helpfull, just a simple sudo apt-get install lamp.




it installed everything i needed, now the part where the problem lies.
i use both eclipse and netbean but cannot for the life of me figure out how too run my scripts in these ides.

they both try too open up a dir [http://localhost/TestPHPSTUFF](http://localhost/TestPHPSTUFF)

but cannot access it. i dont know if i have the server set up wrong or what im doing to be honest.
also a part that scares me immensely is how do i check if ive opened up this network too the internet?

I was under the impression that apache would just set up  a virtual network on my computer that i could run php scripts from. since i dont own a website, i thought this was the best option.

so, too summarize my questions are:

how do i compile my scripts in netbeans and eclipse?
have i opened up my computer too the internet?
and is there anything i should be wary of right now?


*****************************************************************
when i type the address [http://localhost](http://localhost)

i get the messgae "it works! but nothign has been added yet" in a web style page

---

### Post by mushwars on 2010-02-06
good the itworks page means there is nothing wrong with apache.

you need to put your .php code in /var/www/ I think in ubuntu. just tab over or ls /var/www and it will be apparent where you need to put your files. 

you will also need to chown the php files as apache and chmod them to 644 and folders to 775

edit 2: as far as compiling java, I dont know I dont program java nor compile it, but I am pretty sure the command is 
```
javac file.java
```

edit 1:as far as your computer being opend to the internet dont worry, it would only be your htdocs and if you are behind a router then we cant even access it because you dont have port forwarding set up.

V I have apache running as well as php and sql. And there is no way that someone can access my computer through them

---

### Post by overtone on 2010-02-06
> **mushwars said:**
> good the itworks page means there is nothing wrong with apache.

you need to put your .php code in /var/www/ I think in ubuntu. just tab over or ls /var/www and it will be apparent where you need to put your files. 

you will also need to chown the php files as apache and chmod them to 644 and folders to 775

im sorry, but i dont understand what you mean i need too do to them.

i know you want me too put them into the directory var/www/ which was a greta help. i had no idea where the files were being saved.

but if i try the drag and drop method, it just tells me permission denied.

---

### Post by mushwars on 2010-02-06
> **overtone said:**
> im sorry, but i dont understand what you mean i need too do to them.

i know you want me too put them into the directory var/www/ which was a greta help. i had no idea where the files were being saved.

but if i try the drag and drop method, it just tells me permission denied.

do this
```
sudo cp /path/to/files.php /var/www
chown -Rc apache /var/www
chmod 0644 /var/www/file.php
```

---

### Post by overtone on 2010-02-06
I tried something very similar too your steps before hand.

when i tried yours, i get the error that apache is an invalid user, as is apache 2

---

### Post by mushwars on 2010-02-06
> **overtone said:**
> I tried something very similar too your steps before hand.

when i tried yours, i get the error that apache is an invalid user, as is apache 2

oh yea, thats right, I think in ubuntu it is www is the user not apache sorry, I havent used ubuntu server in some time now.

---

### Post by mushwars on 2010-02-06
try this as a test script you will like this one.

```
 [COLOR=#000000] [COLOR=#0000BB]<?php

[/COLOR][COLOR=#FF8000]// Show all information, defaults to INFO_ALL
[/COLOR][COLOR=#0000BB]phpinfo[/COLOR][COLOR=#007700]();

[/COLOR][COLOR=#FF8000]// Show just the module information.
// phpinfo(8) yields identical results.
[/COLOR][COLOR=#0000BB]phpinfo[/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000BB]INFO_MODULES[/COLOR][COLOR=#007700]);

[/COLOR][COLOR=#0000BB]?>[/COLOR] [/COLOR] 
     

```

save as info.php and copy it over to your /var/www

it will look like this

[http://mushwars.net/info.php](http://mushwars.net/info.php)

---

### Post by overtone on 2010-02-06
uhm ok this is unexpected.

i done what i was supposed too. change the directories and what not, 

still have no clue how to run those files in eclipse or netbeans.

but now all the files i had in var/www are gone.

sorry if im bugging you, youve been a great help so far.
im just a total noob and this is kinda confusing for me.

---

### Post by mushwars on 2010-02-06
you keep saying var/www just doubble checking that you are putting them in **/**var/www that is important otherwise they are in your home folder.

you I guess could do this, but you will have problems when apache needs to execute things. 

```
sudo chown -Rc <your user> /var/www
```

then you can open the folder with nautilus and copy all your files there most will run, and if one doesnt just chown just that file to the user www

there is an apache module for home folder www access, just need to find what its called and how to load it. just a few minutes, try ^ that first.

---

### Post by overtone on 2010-02-06
Apologies, I meant /var/www.

I have the directories set correctly. Will i always hav. Too use nautilus command?
I suppose that's not that big a deal.

Last question, how do I actually run the files from that location.

Everytome I close the folder they dissapear but I think I can handle that.

Anytime I open the files, they open in a editor, when I open them in Mozilla or operA, it asks ke if I want too save the file. When I run them in eclipse or any IDE it can't find the file because it keeps looking for localhost, when I change the address in the IDE it just can't access it.

Ai ai ai! All I wanted too do was run some scripts in a virtual server. They really should make this easier lol.

---

### Post by mushwars on 2010-02-06
IMO it is pretty easy, I forgot about look for the module sorry, got busy helping someone else. 

To run your script go to 

[http://localhost/info.php](http://localhost/info.php) for example.

if you get a 404 error then the file is not there.

if you want to see if you ahve any files in there at all and also get their permissions do this

```
sudo ls -al /var/www
```

cheers :popcorn:

---

### Post by overtone on 2010-02-07
i think i understand where most of the problems are coming from now.

all the files are there alright, but i cant access them. anytime i try too do something with the folder it gives access denied.

eg  chown -Rc overtone /var/www
chown: cannot access `/var/www/testfile1.php': Permission denied
chown: cannot access `/var/www/whatever.php': Permission denied
chown: cannot access `/var/www/phpinfo.php': Permission denied
chown: cannot access `/var/www/index.html': Permission denied


if i do

 sudo chown -Rc overtone /var/www
it changes the ownership of only one file, thats testfile.php

im guessing they all already belonged too me.

but heres the weird part, if i try too open the file using [http://localhost/phpinfo.php](http://localhost/phpinfo.php)

i get the error403 forbidden.

i fixed this with chmod 755.
its no longer forbidden but that scripts aren't running.

---

### Post by webtechquery on 2010-02-27
Hi there.

Well, may be for the files and folders permission, you should try chmod instead of chown. Try the following website to get to know how to use chmod command:

[http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/](http://www.webtechquery.com/index.php/2010/02/you-dont-have-permission-to-access-httplocalhost-files-or-folders-on-this-server-in-ubuntu-linux/)

---

### Post by gary441 on 2010-03-09
Hello,
Just trying to help, but was ubutnu installed on your desktop/laptop or on separate machine?
If it was installed on a separate machine, going to [http://localhost](http://localhost) is not going to work. You would have to go to [http://IP-address-of-server](http://IP-address-of-server) (example: [http://192.168.1.4](http://192.168.1.4)).

Thought I'd try to help.

Gary 
:)

---

