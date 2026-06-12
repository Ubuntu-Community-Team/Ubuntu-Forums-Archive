---
title: "How to start a program from a different dir?"
date: 2016-01-06
forum: Server Platforms
---

### Post by Higgins909 on 2016-01-06
I've got this super long line of code.
```

/home/admin-ben/Steam/steamapps/common/Arma\ 3\ Server/arma3server >>/home/admin-ben/gameserver/logs/log.rpt 2>&1 -mod=@Exile\;@mas\;@NATO_Rus_Vehicle -servermod=@ExileServer -config=@ExileServer/config.cfg -port=2302 -profiles=SC -cfg=@ExileServer/basic.cfg -name=SC -autoinit -filePatching

```
If I go into the dir that the "arma3server" is in (this file seems to have no extension?)
```

./arma3server >>/home/admin-ben/gameserver/logs/log.rpt 2>&1  -mod=@Exile\;@mas\;@NATO_Rus_Vehicle -servermod=@ExileServer  -config=@ExileServer/config.cfg -port=2302 -profiles=SC  -cfg=@ExileServer/basic.cfg -name=SC -autoinit -filePatching

```
Works fine, but everything that I've tried with the other dir part hasn't worked.
I've also tried to get it to work without the home/admin-ben part too.  Was just trying.
Trying to get it to work before adding it to a screen, that will run a crontab script. (think I said that right)

But yeah, how do I run this file from a different dir, while in terminal?

Thanks,
Higgins909

---

### Post by darkod on 2016-01-06
If that "Arma 3 Server" is a folder name including spaces, be careful with that. The \ in theory can be used, but I have never trusted it. What happens if you wrap it in double quotes? The path would be something like "/home/admin-ben/Steam/steamapps/common/Arma 3 Server/arma3server".

I know you can use cd with double quotes like that but honestly I have never tried running a program wrapped in double quotes. I never needed to have one in such a complex path.

If that doesn't work, what you could do in the script is first use cd "/path" to take you to the correct destination folder and then run the command from there.

Also, is this how it installs by default, can you choose another destination folder when installing? I am asking because I don't think it's good practice to install stuff in users home folder. But that's another topic.

---

### Post by nerdtron on 2016-01-06
Better yet rename the "Arma 3 Server" folder to "Arma_3_Server" then try to run the program using full path again.

---

### Post by Skaperen on 2016-01-06
any filesystem name that needs quotes (spaces in the name) can be put in quotes (directory, symlink, regular file) either single or double.  the difference is how shell scripts parse them (variable substitution is not done inside single quote so they are used for '$' for example). backslashes might need to be doubled depending on how they are inputted (test it and change if needed).

i like the renaming strategy.

---

### Post by ian-weisser on 2016-01-06
File extensions are a Windows convention. Any file extenstions you find in Linux are purely decorative, or to help users.

You can run anything you want, from any directory.

Example: I want to run the 'hello' application, located at /usr/bin/hello

```
me:/var/log$ cd /usr/bin         ## Let's try it from within hello's dir
me:/usr/bin$ /usr/bin/hello      ## This works from everywhere
Hello, world!                             
me:/usr/bin$ ./hello             ## ./ means 'run this application that is in this directory'
Hello, world!

me:/usr/bin$ cd ~                ## Let's try them from my home directory ('~' means 'my home dir')
me:~$ /usr/bin/hello
Hello, world!
me:~$ ./hello                    ## There is no 'hello' application in  my home directory, so this should fail
bash: ./hello: No such file or directory

me:~$ cd /var/log                ## Let's try someplace else on the system
me:/var/log$ /usr/bin/hello
Hello, world!
me:/var/log$ ./hello
bash: ./hello: No such file or directory
```

Play with some smaller pieces first, and you'll figure it out faster. The 'df' command (/bin/df) or 'date' command (/bin/date) are good applications to start with.

---

### Post by Higgins909 on 2016-01-07
Seems I failed to refresh the page.
Yeah I ended up renaming it, but then ran into other issues that I have no idea how hard it would be
to fix them.  

I can get "Steam/steamapps/common/Arma3Server/arma3server" to kinda work, when in /home/admin-ben.
But it ends up giving out a error, because it can't find steam.  I'm not really sure why it can find steam, when
run from the arma 3 folder tho.  As its not installed in there. (it ends up trying to look for the steamcmd folder,
which i've renamed the steam folder to, to temp see how it would work.  It went from not being able to find it,
with a few errors, to a lot of errors.)

I think that will be it for now.  Don't think I can find a easy fix for it, when there is a 2nd way to do what I'm
trying to do with the script, which is cd to the Arma 3 Server dir.

Yeah I can install it to a different dir, but after all this about steam, I'm not sure how it would work.
common is the folder that steamcmd default installs stuff to, starts out in a folder called downloads, which is
in the same dir as common, then when its done downloading it moves to common.  I've got a few server apps
installed, not sure how easy it will be to move them, because of steam.

Thanks.

---

