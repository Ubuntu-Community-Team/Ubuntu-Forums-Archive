---
title: "Saving to /var/www directories from Aptana"
date: 2010-03-30
forum: Server Platforms
---

### Post by nightmicu on 2010-03-30
Hi everyone,

 Designing a website locally on Ubuntu for the first time, Apache 2, PHP, MySQL, and PHP My Admin are all up and running fine.

I have been using Gedit to modify pages by opening them after navigating to the /var/www folder using gksudo naultilus. This works fine but I decided this morning that I wanted to use Aptana instead..

Aptana runs fine but when I try to save to anything under /var/www I get a permissions error. I tried giving myself read/write permissions both via terminal (chown) and in gksudo nautlius.. no change.

How can I write to these folders from Aptana? Also, is there any way to link to /var/www from my home folder so that I don't have to keep going there "the long way?"

Thanks!

Ben

---

### Post by s_ø on 2010-03-30
you could run Aptana with gksudo
```
gksudo aptana
```If it is just for local development you could give write permission to everyone.
```
sudo chmod o+w /var/www
```This is insecure.

You could setup (s)ftp acces and use a (s)ftp client to connect. It would make remote development easier.


I think this post [http://ubuntuforums.org/showthread.php?t=355559](http://ubuntuforums.org/showthread.php?t=355559) is one of the better regarding permissions and /www

What do you mean by link? Like a desktop shortcut or so apache serves your home folder to the world?

---

### Post by nightmicu on 2010-03-30
> **s_ø said:**
> you could run Aptana with gksudo
```
gksudo aptana
```If it is just for local development you could give write permission to everyone.
```
sudo chmod o+w /var/www
```This is insecure.

You could setup (s)ftp acces and use a (s)ftp client to connect. It would make remote development easier.


I think this post [http://ubuntuforums.org/showthread.php?t=355559](http://ubuntuforums.org/showthread.php?t=355559) is one of the better regarding permissions and /www

What do you mean by link? Like a desktop shortcut or so apache serves your home folder to the world?

Okay, firstly Aptana is an EXE, from what I understand it runs using Java 6. I have a link to the program .exe on my desktop, command is "/home/benjamin/Aptana Studio 2.0/AptanaStudio" (with quotes)

I tried adding "gksudo" (no quotes) before the above command but then the launcher did not work. Suggestions?

This is indeed for local purposes only, so perhaps I will try the ```
sudo chmod o+w /var/www
```

And by a link, I meant being able to open up /var/www easily without having to go to File System > Var > [WWW..](WWW..) only having a link in my Home folder or desktop

Thanks!

Ben

---

### Post by s_ø on 2010-03-31
You can make a link by creating a launcher. Then select 'place' instead of 'program' and type the path - /var/www

In your launcher for aptana change from 'program' to 'program in terminal'.

---

### Post by nightmicu on 2010-03-31
> **s_ø said:**
> You can make a link by creating a launcher. Then select 'place' instead of 'program' and type the path - /var/www

In your launcher for aptana change from 'program' to 'program in terminal'.

Okay... can you be more specific? I see "program in terminal" as an option when I create a new launcher, but how do I get it to actually launch Aptana? I tried ```
gksudo /home/benjamin/Aptana Studio 2.0/AptanaStudio
``` but all this does is open Terminal, prompt me for a password, and then nada. Also tried with the directory in quotes.

Thanks..

---

### Post by s_ø on 2010-03-31
You need to escape the spaces with '\'.
```
 gksudo /home/benjamin/Aptana\ Studio\ 2.0/AptanaStudio
```You can try it in a terminal.
Press Alt+F2 and type 'gnome-terminal' to get a terminal.
You can tab-complete in the terminal. Start by typing the above code, when you get to '/ho' press tab. Continue typing the first letters and press tab.
That way you avoid typos.

Edit:
I just downloaded it and tried running with gksudo. For some reason that dont work. Instead use sudo, then it works.
```
sudo /home/benjamin/Aptana\ Studio\ 2.0/AptanaStudio
```

---

