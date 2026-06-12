---
title: "password requests for user files"
date: 2009-04-27
forum: Security
---

### Post by cholericfun on 2009-04-27
Hi,

a hopefully not so serious issue but its irritating me.

some images i've got on the computer (in Home/User/Pictures) require me to type my password in order to view them.
checking for permissions all these images have -rwxrwxrwx
so i dont see why this should happen


when i just click on the image it sais:
Enter your password to perform administrative tasks
the application eog path/to/file lets you modify essential parts of the system.


when i go to the images via terminal and just type eog filename then everything is OK, eog pops up.

---

### Post by Barry Carroll on 2009-04-27
Weird...seems like the permissions are wide open but you still get problems.

if you do something like this on the terminal ```
sudo chown -r username:username /home/username/pictures
``` , replacing username with your username does it fix it?

---

### Post by cholericfun on 2009-04-28
thanks for the reply,
didn't change anything though.

still asking me for a password when clicking on the pics and just works when going via command line

---

### Post by cholericfun on 2009-04-28
ok,
on second thoughts, this seems to happen with images that have been put on the computer via USB drive etc, images that i've send via email et cet. are fine and can be opened via GUI fine.
actually i could send these images off via email without trouble.

so 2 things that irritate me:
-why ask for permission to open files that have been written to disk?
-why the discordance between terminal and GUI

anyone any ideas how to "fix" this, i've got the feeling some settings are mildly screwed up and i dont want that to build up (and i dont nearly know enaugh bout linux to even know where to look for errors).

thanks

---

### Post by cholericfun on 2009-05-03
anyone at least seen a thread somewhere that relates?

---

### Post by ooobooontooo on 2009-05-04
That is a strange problem....can you post what you see when you look at the permissions via gui? The "properties" of the images and the directorys.

---

### Post by cholericfun on 2009-05-04
hi,

yes:

owner (me - its a sinlge user PC)
read & write

group and others are
read -only

allowing to execute as program is off


actually - i just saw the problem there... - the default "open with" is gksudo
i'm 200% sure i didnt do that manually so thats strange. it explains why it doesnt ask me for permission if i type eog image into commandline though

thanks for the replies

---

### Post by ooobooontooo on 2009-05-04
Haha...I'm not exactly sure how that happened either. Anyway, congrats to getting your problem fixed; I can see how that could get very annoying.

---

