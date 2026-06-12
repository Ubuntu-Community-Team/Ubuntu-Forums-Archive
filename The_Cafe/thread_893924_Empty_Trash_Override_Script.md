---
title: "Empty Trash Override Script"
date: 2008-08-18
forum: The Cafe
---

### Post by dennismoore1 on 2008-08-18
I've had problems with the trash bin before (files dont have the permission to be moved or deleted).  So I came up with a simple shell script to take care of this problem.  Install it to /usr/local/sbin/.  If you do not have permissions to do so you can change the permisions on the folder. To do that you can use the following code:

sudo chmod a+rwx /usr/local/sbin

Open gedit and type the following code:

sudo rm -Rf /home/(your username/.local/share/Trash
mkdir /home/(your username)/.local/share/Trash
mkdir /home/(your username)/.local/share/Trash/info
mkdir /home/(your username)/.local/share/Trash/files

Save it to /usr/local/sbin/ and name it empty-trash.  Now whenever you need to empty your trash bin you can type empty-trash then enter the sudo password and your trash will be completely emptied, no questions asked.

---

### Post by aysiu on 2008-08-18
> **dennismoore1 said:**
> I've had problems with the trash bin before (files dont have the permission to be moved or deleted).  So I came up with a simple shell script to take care of this problem.  Install it to /usr/local/sbin/.  If you do not have permissions to do so you can change the permisions on the folder. To do that you can use the following code:

sudo chmod a+rwx /usr/local/sbin

Open gedit and type the following code:

sudo rm -Rf /home/(your username/.local/share/Trash
mkdir /home/(your username)/.local/share/Trash
mkdir /home/(your username)/.local/share/Trash/info
mkdir /home/(your username)/.local/share/Trash/files

Save it to /usr/local/sbin/ and name it empty-trash.  Now whenever you need to empty your trash bin you can type empty-trash then enter the sudo password and your trash will be completely emptied, no questions asked.
You probably won't have problems with the trash bin and permissions if you stick with *sudo* for terminal applications and *gksudo* for graphical applications.

Also, in order for someone to save your script to /usr/local/sbin, she'd have to open Gedit with *gksudo* instead of just opening Gedit: ```
gksudo gedit /usr/local/sbin/empty-trash
``` Any reason it's *sbin* instead of *bin*?

It also seems to add in an extra step to delete the Trash directory and then reconstruct it. Why not make it this instead? ```
#!/bin/bash
sudo rm -r ~/.local/share/Trash/info/*
sudo rm -r ~/.local/share/Trash/files/*
```

---

### Post by dennismoore1 on 2008-08-18
you could just chmod the /usr/local/sbin/ directory without gksudo so you can drag and drop your files into it

no reason that its sbin instead of bin i just liked the sounds of sbin to hold all my scripts

if you tryed to reconstruct the trash bin as preposed it will not work because the parent directory has to be their first before you make another directory inside of it

Example:

mkdir /home/username/.local/share/Trash/files
mkdir /home/username/.local/share/Trash/info

that will not work you need the parent directory "Trash" first.

---

### Post by aysiu on 2008-08-18
I'm not trying to reconstruct the trash bin at all. I don't think it should be deleted in the first place.

My proposal would be to delete only what's in the trash.

---

### Post by Lord Xeb on 2008-08-18
I support what you say and I will actually use your script since I like it >_> good idea.

---

### Post by dennismoore1 on 2008-08-18
yes deleting just the contents would work aswell i suppose just the way your/my mind work differently aisyu

and thank you lord xeb

---

### Post by chris4585 on 2008-08-19
nice, funny thing though I already use this script, or a script i came up with that does the same thing, why not go a step further and delete the root's trash too?

:lolflag:

---

### Post by koenn on 2008-08-19
> **dennismoore1 said:**
> I've had problems with the trash bin before (files dont have the permission to be moved or deleted).  So I came up with a simple shell script to take care of this problem.  Install it to /usr/local/sbin/.  If you do not have permissions to do so you can change the permisions on the folder. To do that you can use the following code:

sudo chmod a+rwx /usr/local/sbin

Open gedit and type the following code:

sudo rm -Rf /home/(your username/.local/share/Trash
mkdir /home/(your username)/.local/share/Trash
mkdir /home/(your username)/.local/share/Trash/info
mkdir /home/(your username)/.local/share/Trash/files

Save it to /usr/local/sbin/ and name it empty-trash.  Now whenever you need to empty your trash bin you can type empty-trash then enter the sudo password and your trash will be completely emptied, no questions asked.

I'm with Aysiu on this one: if files in your own home directory, i.e. /home/(your username)/.../Trash/... are inaccessible to you, you've done something wrong, like using sudo the wrong way or do normal computer use while logged in as root.
Better learn to do it right, in stead of having to create a fix for it.

deleting a directory and then recreate it, while in fact you want to delete the contents of a directory, also seems a bit clumsy


lastly, your suggestion to use /usr/sbin for such a script is bad advice.
/usr/sbin is for sysadmin tools that should only be accessible to the sysadmin account / superuser / root. 
by giving any account write access to such a directory, you're poking holes in your OS's basic security : any user can now save any script there ...

if you have to tamper with filesystem permissions in order for a normal activity such as running a user-created script to work, that's a sure sign you're doing something wrong. Linux is designed so that a normal user never needs write access anywhere outside his home dir (and maybe a very limited number of other locations, such as /tmp.)


Of course, you're free to mess with your system any way you like,
I just wanted to point out some caveats for others who may read this thread and think it's a great idea.

---

### Post by dennismoore1 on 2008-08-19
koeen, I am sorry that i didnt think of the security.  I am the only user on both of my computers so it seems more obvious to me to put the file whereever i want. so you could use this if you are the admin and dont want other users to use the folder 

chmod a-rwx /usr/local/sbin/

chris how can i empty root trash?

---

### Post by aysiu on 2008-08-19
> **dennismoore1 said:**
> koeen, I am sorry that i didnt think of the security.  I am the only user on both of my computers so it seems more obvious to me to put the file whereever i want. so you could use this if you are the admin and dont want other users to use the folder 

chmod a-rwx /usr/local/sbin/

chris how can i empty root trash?
Is this a recurring problem for you, dennismoore1 that you need to create a script for it and run it often? If so, maybe we can figure out what the problem is.

There really shouldn't be things in your trash can you aren't able to empty. The fact that there are means something is wrong - either there's a bug in Ubuntu or you're doing something incorrectly.

In answer to your question, the root trash is probably in /root/.local/share/Trash/files

---

### Post by dennismoore1 on 2008-08-19
it indeed is a recurring problem...sometimes when i delete a file for some reason their permissions get changed so i cannot move or delete them.  i needed to come up with a script that would delete the directory because 
trash:///
does not technically exist as a directory.
so sure, we can find out the problem

---

### Post by aysiu on 2008-08-19
What program are you using to delete these files? Do you ever run this program as root?

---

### Post by chris4585 on 2008-08-19
what aysiu said, its the same place just in /root/ and you'd need gksu to do so

---

### Post by dennismoore1 on 2008-08-19
i usualy just press the delete key after highlighting the file through the file browser.. so basicaly i do it graphicaly.  Either that or I drag and drop them to the trash bin icon on my desktop.

---

### Post by aysiu on 2008-08-19
These are files you're deleting from your /home/*username* directory? They're not root-owned files?

Are you in Xfce or Gnome, by the way?

---

### Post by dennismoore1 on 2008-08-19
they're not root owned no
im in gnome also

---

### Post by aysiu on 2008-08-19
So you have non-root-owned files deleted in Nautilus that you are not able to empty from the trash?

What kind of error message do you get when you try to empty the trash with these files in them?

---

### Post by dennismoore1 on 2008-08-19
either it doesnt give me an error message at all or it says i dont have the permissions
i think when i right click and select empty trash then it doesnt
and when i open it and try deleting a single file it gives the error message

---

### Post by aysiu on 2008-08-19
> **dennismoore1 said:**
> either it doesnt give me an error message at all or it says i dont have the permissions
i think when i right click and select empty trash then it doesnt
and when i open it and try deleting a single file it gives the error message
Maybe the trash itself has the wrong permissions or ownership on it? Can you try ```
sudo chown -R *username*:*username* /home/*username*/.local/share/Trash
``` and see if you still have the same problem?

---

### Post by dennismoore1 on 2008-08-19
no its not the trash's permissions its the files within it
i think its a problem with the nautilus trash applet becuase i can navigate to the directory and move them then rm -Rf them
the trash's permissions have been verifyed as a=rwx\
the problem only occurs somethimes though

---

### Post by aysiu on 2008-08-19
Maybe it's a bug. I've never experienced it myself, but you aren't the only person I've seen with this problem. It'd be great to get that fixed instead of having to rely on a script to clean up the mess.

---

### Post by dennismoore1 on 2008-08-19
agreed but untill then I'll just use the script.
i hope they could solve it soon

---

### Post by koenn on 2008-08-20
> **dennismoore1 said:**
> they're not root owned no
im in gnome also

Then who owns these files that you can't delete from trash, and what are the permissions ?

---

### Post by koenn on 2008-08-20
> **dennismoore1 said:**
> ... so you could use this if you are the admin and dont want other users to use the folder 

chmod a-rwx /usr/local/sbin/


would this not remove all permissions, for any account ?

---

### Post by dennismoore1 on 2008-08-20
root can never lose permissions for this folder no.  i dont think anyone but root could change it to rwx once its -rwx though.  once the root password is entenred into terminal permissions are granted for 15 mins

---

### Post by koenn on 2008-08-20
> **dennismoore1 said:**
> root can never lose permissions for this folder no.  i dont think anyone but root could change it to rwx once its -rwx though.  once the root password is entenred into terminal permissions are granted for 15 mins
yes, sure, root can fix it, by why would you deliberately break it to begin with.

---

### Post by dennismoore1 on 2008-08-20
i dont really think it is breaking it...where do you suggest putting my scripts?

---

### Post by koenn on 2008-08-20
> **dennismoore1 said:**
> i dont really think it is breaking it...where do you suggest putting my scripts?

removing all permissions from a directory so that root has to chmod it every time you need to add or remove something sounds broken to me. 

If your scripts are real tools for all users, they can go in /usr/bin, like other executables. 
If you prefer to keep them  separate from distro-executables, /usr/local/bin is a reasonable alternative, but you shouldn't be messing with the permissions. root can write to it, and all users can read it, which is just right.  

If it's just small stuff or things only you will use, you can use a dedicated subdirectory in your home directory, say ~/bin. it's added to your $PATH so executables there will work anywhere.

---

### Post by dennismoore1 on 2008-08-20
Im the only user on my computer so I don't really need to worry about other users so I did overlook the permissions again. You could use

sudo mv /directory/of/script /usr/local/sbin/

that would make it so that you didn't have to chmod the folder each time.

---

### Post by koenn on 2008-08-20
> **dennismoore1 said:**
> Im the only user on my computer so I don't really need to worry about other users so I did overlook the permissions again. You could use

sudo mv /directory/of/script /usr/local/sbin/

that would make it so that you didn't have to chmod the folder each time.

I think you misunderstand. 
Sounds like you're trying to teach me how to run scripts and how to deal with file and directory permissions. I already know how to do that. 
I was just pointing out that your approach is flawed, because it's a pile  of workarounds for problems that wouldn't even exist if you do things the right way. 

Besides, this whole scripting issue is only a side step. 
Your real problem is that you have files in your trash, but you don't own them or have sufficient rights to delete them.

To diagnose the problem, I asked you, a couple of posts ago, who owns those files and what are their permissions. 
You haven't answered that.

---

### Post by aysiu on 2008-08-20
dennismoore1, the next time you have a trash you can't empty, instead of running your script, can you post back here and tell us what the exact situation was (where the files were deleted from using what program) and what the output of these commands are? ```
ls -l ~/.local/share/Trash
ls -l ~/.local/share/Trash/files
ls -l ~/.local/share/Trash/info
```

---

### Post by stormtrooprdave on 2008-08-20
Any chance people can take a look a my trash bin problem? Seems like there are some knowledgeable people in this thread and my problem never got solved.

[http://ubuntuforums.org/showthread.php?t=885545]("http://ubuntuforums.org/showthread.php?t=885545")

---

### Post by psyncho on 2008-10-01
[QUOTE=aysiu;5617259]You probably won't have problems with the trash bin and permissions if you stick with *sudo* for terminal applications and *gksudo* for graphical applications.

This makes sense to me. Can you gksudo to empty your trash right from the desktop, and if so, how would you go about that?

I do most everything in terminal - accidentally deleted a file as root which was placed in trash and then I couldn't empty trash as my normal user. Oh the silliness.

Right now I'm just manually changing permissions on the files and getting rid of them. 

On that note, why is there a .local/share/Trash and .Trash and can you tell me the difference - or point me to some esoteric documentation?

cheers, 
John

---

