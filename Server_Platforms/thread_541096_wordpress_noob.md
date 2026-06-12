---
title: "wordpress noob"
date: 2007-09-02
forum: Server Platforms
---

### Post by tronica on 2007-09-02
I'm installing wordpress for some friends to play with, however i get to one step of the install and i get an error. The guide im following wants me to run this command

> sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n (your mysql user) localhost 

so i fill in my mysql user and i get this

> tronica@web:/var/www$ sudo sh /usr/share/doc/wordpress/examples/setup-mysql -n root localhost
/usr/share/doc/wordpress/examples/setup-mysql: 37: Syntax error: Bad substitution
tronica@web:/var/www$ 


any ideas? thanks

---

### Post by dunno on 2007-09-02
Hi tronica,

I am also setting up wordpress and had that same error on the command line after using that same command from [https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

instead of using that command, open up /usr/share/doc/wordpress/examples/setup-mysql using a text editor.

Look at line #20

copy it, open a terminal, paste it.  change the username and url to your own, then run it.


hope that helps:):)

---

### Post by tronica on 2007-09-03
i tried that, still didn't work i get 

> bash: setup-mysql: No such filre or directory

---

### Post by dunno on 2007-09-03
I'm certainly not an expert.  that's what i did and it worked.

some suggestions:
check that you used the correct Fully Qualified Domain Name (FQDN) on the command line when you entered "sudo bash setup-mysql..."?
check that wordpress is installed or linked into your website service path.  for instance, if you are serving from /var/www/, then in that folder should be a folder containing the wordpress install or links to that folder.  the name of that folder depends on what you called it when you installed it.

truly sorry i can't be more help!  best of luck.:confused:
don't give up!

---

### Post by tronica on 2007-09-03
Thanks for the info, i really appreciate it.

---

### Post by tronica on 2007-09-04
i got it to work by downloading it directly from wordpress, and dropping it in /var/www, and extracting it. works great. One question though, How do make it i dont' have to type [www.site.com/wordpress?](www.site.com/wordpress?) If i extract it in /var/www, then phpmyadim will won't work right?

---

### Post by conjur3r on 2007-09-05
Move all of the files in /var/www/wordpress into /var/www.  You should still be able to access /var/www/phpmyadmin though.  A word of warning though, moving the folder after you have it running will render your wordpress inoperable.  You must edit your configuration files, especially the options found on mysql for wordpress.

---

### Post by dpm on 2007-09-10
At least on the Gutsy version of the setup-mysql of the script you must use **bash** instead of **sh**, otherwise you will get the funny "Bad substitution" error message. That is, you must execute:

```
sudo bash /usr/share/doc/wordpress/examples/setup-mysql -n (your mysql user) localhost
```

Just have a look at the script itself on a text editor, the example it shows is executed with bash.

I hope this helps.

Cheers.

---

