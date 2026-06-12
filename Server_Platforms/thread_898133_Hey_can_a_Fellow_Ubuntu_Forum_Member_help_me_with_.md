---
title: "Hey can a Fellow Ubuntu Forum Member help me with installing IspCP Please!!!!"
date: 2008-08-22
forum: Server Platforms
---

### Post by Redneck_Michael on 2008-08-22
Ubuntu Forum Members,
   Hey I can't install cpanel onto my Ubuntu 8.04 Server. I was wondering if you could help me install it I get all the way untell it tells me that there is a package missing or something the error that pops up us actually [Click here for the error page.]("http://michaelm1119.homelinux.com/ispcp/gui/") If you can help me I would really gladly apprecitate it thanks alot

Sincerly,
Michael

---

### Post by Shazaam on 2008-08-22
I get this from your link......
```
ERROR: Unable to connect to SQL server !
SQL returned: Access denied for user 'root'@'localhost' (using password: NO)
```
Have you read this?......
[http://www.cpanel.net/docs/whm](http://www.cpanel.net/docs/whm)

---

### Post by Redneck_Michael on 2008-08-23
Yeah thats what i get it needs a DBD::MySQL Plugin or something im using the IspCP Hosting Interface i just need help get it installed

---

### Post by Shazaam on 2008-08-23
I found this.....
[http://groups.google.com/group/ispcp-users/browse_thread/thread/9f53884c5369e32a](http://groups.google.com/group/ispcp-users/browse_thread/thread/9f53884c5369e32a)

---

### Post by Redneck_Michael on 2008-08-23
Yeah i tried that im a ex red hat user and all my cpanel and everything was set up and now i want to do it all on my own and i can get it to finish installing i get it to the last step and the terminal kills and i almost want to take the cpu and through it far away from me

---

### Post by Redneck_Michael on 2008-08-23
Here is the message when i try to run the setup file in the terminal 


> Modules [DBD::mysql] WAS NOT FOUND in your system...


        Welcome to ispCP '1.0.0 RC5 OMEGA' Setup Dialog.
        This program will set up ispCP OMEGA system on your server.

        Next you are asked to enter a "fully qualified hostname" (FQHN).
        For more infos read [http://en.wikipedia.org/wiki/FQDN](http://en.wikipedia.org/wiki/FQDN).


        Please enter a fully qualified hostname. [michael-server]: 


---

### Post by Sef on 2008-08-23
Moved to Server Platforms.

---

### Post by windependence on 2008-08-23
> **Redneck_Michael said:**
> Here is the message when i try to run the setup file in the terminal

Looks to me as if you don't have MySQL installed at all.

Do this:

```
sudo apt-get install mysql-server
```

Then try your CPanel install again.

-Tim

---

### Post by crazyelf on 2008-08-23
I've actually been working with him on this, and he has webmin installed with mysql-server fully operational.  But when you goto run perl ispcp-setup in the /var/www/ispcp/engine/setup/ folder it comes back with DBD::mysql is missing.  When trying to install that perl module through cpan it returns with Cannot make.  Error status 512. I tried using fforce install DBD::mysql in cpan.  But it also returned with the same error.  Hopefully this helps some.

---

### Post by Redneck_Michael on 2008-08-24
I dont want cPanel! But yeah i finally got the DBD::mysql but i just cant seem to get the ispcp to work if someone thinks they can do it and would like to help aaron and I would greatly appreciate it we are looking for some sleep since all we do is try to work on this ispcp interface

Sincerly,
Michael

---

### Post by crazyelf on 2008-08-28
It seems once the moderator so kindly moves it to an ignored sub forum this post will no longer get attention.  Its a shame, I guess we'll look else where for help.  [-X

---

### Post by windependence on 2008-08-28
Are you trying to install ISPconfig or CPanel?

I also saw a reference to make earlier in this thread. If you want this to work, you will have better luck if you install everything from the package repositories instead of compiling from source. Mixing the two won't work. I believe this is your main issue here.

This is NOT an ignored sub forum. In fact we are quite active here. Remember, we volunteer our time here, it's not a paid gig. ;)

-Tim

---

### Post by crazyelf on 2008-09-01
> **windependence said:**
> Are you trying to install ISPconfig or CPanel?

I also saw a reference to make earlier in this thread. If you want this to work, you will have better luck if you install everything from the package repositories instead of compiling from source. Mixing the two won't work. I believe this is your main issue here.

This is NOT an ignored sub forum. In fact we are quite active here. Remember, we volunteer our time here, it's not a paid gig. ;)

-Tim

Sorry I just got a little frustrated.  I do realize its all volunteer and I shouldn't expect instant replies.  

We actually are trying to install ispCP or isp-control.  Unfortunately it doesn't have a repository.  Its seems its perl based and needed several modules that were missing.  So I installed all but DBD::mysql which failed over and over.  So this is what is needing installed.  Mysql is working fine with php.  Just not perl so we need that module.  It says cannot make, with error status 512.

If you can help me figure out how to get it installed, I would greatly appreciate it.

---

