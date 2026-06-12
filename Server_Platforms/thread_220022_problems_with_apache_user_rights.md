---
title: "problems with apache user rights"
date: 2006-07-20
forum: Server Platforms
---

### Post by jkblitz on 2006-07-20
im having a problem changeing editing files this is the error im geting

Cannot move "/var/www/a...he_pb.png" to the trash because you do not have permissions to change it or its parent folder

is there any solution to this

---

### Post by scxtt on 2006-07-20
if it's your box and you have sudo rights - **sudo mv /var/www/"name_of_file" /where/ever/you/want/it** ...

---

### Post by jkblitz on 2006-07-20
ya its my box and i have sudo rights but im trying to change them in system files

---

### Post by scxtt on 2006-07-20
your initial post isn't too descriptive and actually a bit confusing - what are you trying to do?

what is "changeing editing"? :p

---

### Post by ExMachina on 2006-07-20
sudo chown <username> /var/www/
sudo chgrp <username> /var/www/

Now <username> owns that folder.

* unless im wrong?*

---

### Post by jkblitz on 2006-07-20
well scxtt im tring to add a index.html file to "/var/www/apache2
so that when i can hook up my ip to a domain name so that i can make a sit 

im tring to get rid of the files that are cuerntly defalt under my ip/localhost
but i cant becuse its giving me that msg

---

### Post by scxtt on 2006-07-20
you shouldn't need to even worry about that ... by default apache2 serves webpages from /var/www ... so adding your index.* file to /var/www will work fine, i.e. you can just type your IP into a browser window and your index.html file will be served from /var/www/index.html ...

/var/www/apache2 just holds little icon files that can be used to show mime types (like txt documents, folders, media, etc.) ...

---

### Post by jkblitz on 2006-07-20
no theres a little lock by the folder and i tryed placeing a file there no luck

---

### Post by scxtt on 2006-07-20
what do you mean "no"?

using sudo in front of any command you want to use (to cp or mv or rm a file) will work - unless you're not on the sudo list ...

at any rate, you DON'T need to put index.html in /var/www/apache2 (by default, at least) ...

---

### Post by jkblitz on 2006-07-20
so where should i put it with out useing the terminal?

---

### Post by scxtt on 2006-07-20
do a **gksudo nautilus** if you're using gnome and **kdesu konqueror** if you're using KDE (in a terminal) ... it'll ask you for YOUR password and if you are indeed on the sudo list, will allow you to move files anywhere ... or use "run as different user" ...

but don't avoid the terminal, it is your friend ...

---

### Post by jkblitz on 2006-07-20
well iv just started up again with linux becuse the first time i gave up on it the gksudo nautilus worked it gave me full controll what gksudo nautilus do and for the terminial it would be my "friend" if i knew the cmds (if you know a good site/place plz tell me)

but i also got this in the terminal 

GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by scxtt on 2006-07-20
understandable ... i'd definitely given up in the past - sometimes it would just frustruate me ... it's just a matter of time til things start clicking and you and the terminal have a nice "friendship" ...

i'm sure there's a nice list of commands out there somewhere - i know i'd seen an article on digg.com about "terminal commands for newbies" a few weeks ago ...

---

### Post by jkblitz on 2006-07-20
so do you think it a good idea useing lamp or xampp

and if i use gksudo nautilus
 is there still a need for me to know my root pass?

---

### Post by scxtt on 2006-07-20
i don't do the whole lamp thing ... i just install apache, php, and python on my desktop anyway - LAMP is just more of a scaled down, resource saving method - i don't need that ...

and i don't enable the root account - just use sudo ... i NEVER log in as root ... so technically you can forget your root password ...

---

### Post by jkblitz on 2006-07-20
is root a bad thing?

---

### Post by scxtt on 2006-07-20
i look @ it like this:

we all know root is the "administrator" whereas our non-root accounts have much less known names ... so if a "hacker" wants to start guessing passwords, (s)he can just start w/ "root" and bombard your box w/ password guesses ... therefore, not having a root account would require a hacker to "guess" your account name and "guess" your password ...

so why help them out?

---

### Post by jkblitz on 2006-07-20
well this one is compleetly of topic but i wat to set up php myadmin but iv never compiled could you help me out

---

### Post by scxtt on 2006-07-20
i see myphpadmin in the repos, w/ synaptic - in the universe section, if you have it enabled in your /etc/apt/sources.list ...

---

### Post by jkblitz on 2006-07-21
and if i want to install php again shoud i do it from a bin(dont know how to do that)or sudo apt-get install php5 or something?

and also iv gone to the snytic thing and i pressed i wanted the mysql client it did its stuff so where do i find it now?

---

### Post by scxtt on 2006-07-21
it's best to install EVERYTHING via synaptic/apt-get if you're (meaning anyone, not you specifically) not much of a configuration 'expert' ...

as for finding myphpadmin, i'm thinking you can go to [http://127.0.0.1/admin/](http://127.0.0.1/admin/) from a browser to access it ... but i've never used installed it and used it myself ... i do use it, at work, but it was already installed and all i have to do is what i said above (tho i use the boxes name, not internal IP) ...

---

