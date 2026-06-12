---
title: "Server with GUI? (was: server 6.10 startx)"
date: 2007-02-28
forum: Server Platforms
---

### Post by coolmarine24 on 2007-02-28
Hello to all I jsut downloaded and installed Ubuntu Server 6.10 ....but when i type startx to get to the gui interface i get an error "command not found"...im very new to linux, can anyone tell me how to get to the gui interface please?? Thanks

---

### Post by Iarwain ben-adar on 2007-02-28
Hi there,
the server edition doesn't have a GUI. 
To install one, type this
```
sudo aptitude install ubuntu-desktop
```

and then you just type
```
 sudo gdm
``` if the GUI isn't started yet.


Iarwain

---

### Post by coolmarine24 on 2007-02-28
Thanks so much I did what you suggested, after the first command a long installation took place with no problems at all.....but when i type the commands sudo gdm i get an command not found message:-(....do you know why that is?

---

### Post by Brunellus on 2007-02-28
> **coolmarine24 said:**
> Thanks so much I did what you suggested, after the first command a long installation took place with no problems at all.....but when i type the commands sudo gdm i get an command not found message:-(....do you know why that is?
gdm is a service, not a regular program.  you must use init to start it:

sudo /etc/init.d/gdm start

will start it.

---

### Post by coolmarine24 on 2007-02-28
what i did first was typed sudo aptitude install ubuntu-desktop
that command installed a whole bunch of things and then it took me back to the command shell........at that point i entered the sudo gdm command but got the error : sudo: gdm: command not found..........did i do anything wrong?

---

### Post by jkeyes0 on 2007-02-28
> **coolmarine24 said:**
> what i did first was typed sudo aptitude install ubuntu-desktop
that command installed a whole bunch of things and then it took me back to the command shell........at that point i entered the sudo gdm command but got the error : sudo: gdm: command not found..........did i do anything wrong?

no, you didn't do anything wrong. What Brunellus meant was that now that you've installed ubuntu-desktop, you can start the GUI by typing in:

```
sudo /etc/init.d/gdm start
```

---

### Post by coolmarine24 on 2007-02-28
thanks alot for the clarification.....ok i typed sudo /etc/init.d/gdm start at the root@myserver:`# .....but i still get the message ...sudo: /etc/init.d/gdm: command not found :-(......please help

---

### Post by coolmarine24 on 2007-02-28
one thing that i should mention, not sure if it will help but when i did the installation of the desktop by typing sudo aptitude install ubuntu-desktop ....in one of the blue screen i got asked something about "no configuration" "internet" "internet with ***".........i selected "no configuration".........could that be the problem??

---

### Post by Iarwain ben-adar on 2007-02-28
It wouldn't pose a problem i think,
as you already downloaded and installed ubuntu-desktop.

Could you show us the output of this command?
```
ls /etc/init.d/ |grep gdm
```
(just copy paste the code :D )

If it brings back no results, type this
```
sudo aptitude install gdm
```


Iarwain

---

### Post by coolmarine24 on 2007-02-28
Thanks so much, the first command had no errors and no results at all.......i then tried the second command and it started an installation...it is currently at 5%....so I guess I should wait until is complete ?...

---

### Post by Iarwain ben-adar on 2007-02-28
Probabely best :wink:

And after that, just start gdm via the command
```
sudo /etc/init.d/gdm start
```


Iarwain

---

### Post by coolmarine24 on 2007-02-28
ok , installation is complete....but now when i reboot the server i get an error that says ""failed to start the X server,,,,it is likely thatis not setup correcly. Would you like to view the x server output to diagnose the problem???"

i select "yes" and get a  X: cannot stat /etc/X11/X ( no such file or directory), aborting

i then select ok and get the message "the x server isnow dsiabled . Restart GDM when it is configured correcly.

and select "ok' and it takes me back to the login screen on the shell :-(..........

---

### Post by coolmarine24 on 2007-02-28
(continue from my last post.).....on the shell i type sudo /etc/init.d/gdm start and i get the message *starting GNOME display manager.....and the it takes me back to the root@myserver:!# shell......

i type sudo gdm and get a message GDM already riunning. Aborting! :-(

---

### Post by coolmarine24 on 2007-02-28
dont know if this helps but i also tried typing "startx" and get  the result below:

xauth: creating new authority file /root/.serverauth.38.66
xauth: creating new authority file /root/Xauthority
xauth: creating new authority file /root/Xauthority

X: cannot stat /etc/X11/X (no such file or directory), aborting
giving up
xinit: Connection refused (errno111): unable to connect the x server
xinit: No such process (errno 3): Server Error.

---

### Post by coolmarine24 on 2007-02-28
is there anything at all that i should do to make this work??......all i want is to be able to get to the gui interface lol...are these problems normal?

---

### Post by Brunellus on 2007-02-28
> **coolmarine24 said:**
> is there anything at all that i should do to make this work??......all i want is to be able to get to the gui interface lol...are these problems normal?
have you tried simply rebooting?
if all you want is a GUI, why not just install the Ubuntu desktop cd?

---

### Post by coolmarine24 on 2007-02-28
yes i've tried rebooting....i need the server version because i need to install the  DNS option plus i need it for a file server:-(

---

### Post by Brunellus on 2007-02-28
> **coolmarine24 said:**
> yes i've tried rebooting....i need the server version because i need to install the  DNS option plus i need it for a file server:-(
if you need a GUI (debatable for a real server), then it's easier to install the desktop cd, add the services you want, and remove the ones you don't.  

If you know what you're doing, you can run headless, but

---

### Post by coolmarine24 on 2007-03-01
maybe i should try using the 6.6 version instead of 6.10?

---

### Post by Brunellus on 2007-03-01
> **coolmarine24 said:**
> maybe i should try using the 6.6 version instead of 6.10?
If you are unwilling or unable to run command-line only, you should not install the "server" version.  

It's all the same Ubuntu, anyway--all that matters is what packages are installed.  For you, I'd recommend going with the standard desktop install and adding the software you need.  That will give you the GUI you want, and allow you to add the services you may also require.

---

### Post by coolmarine24 on 2007-03-01
> **Brunellus said:**
> If you are unwilling or unable to run command-line only, you should not install the "server" version.  

It's all the same Ubuntu, anyway--all that matters is what packages are installed.  For you, I'd recommend going with the standard desktop install and adding the software you need.  That will give you the GUI you want, and allow you to add the services you may also require.

Thanks again, Will I be able to install LAMP on the desktop version??.....will i be able to bood to the deskto version with out the installation cd being in the cd drive?....reason why i want a gui is because i will use MySQL, Apache, and PHP.......i figured it would be better to confogure those services using a gui interface....am i wrong?

---

### Post by Brunellus on 2007-03-01
you can install them.  You may or may not still have to hack up the config files with a text editor.

---

### Post by coolmarine24 on 2007-03-01
I see,... I am  a novice Ubuntu/Linux User, ( I am sure you were able to tell )I don't think I will be able to hack some files and make changes to them. I guess I will have to deal with having the server with LAMP and not having a gui interface.....is it difficult to configure php apache and mysql from the dos like interface?? ( i guess its called the shell? )....if not does this website have guides on how to setup those services? ( Apache, My Sql,  PHP ).....It would be so nice being able to use php, mysql, and apache on this machine that already has Ubuntu Server loaded

---

### Post by Brunellus on 2007-03-01
I am bumping this to Server talk.  I don't really know much about servers myself--last time I did this was to set up a server for a netboot install--  but I'm comfortable with the command line, so am not scared of the 'server' install.

---

### Post by coolmarine24 on 2007-03-01
> **Brunellus said:**
> I am bumping this to Server talk.  I don't really know much about servers myself--last time I did this was to set up a server for a netboot install--  but I'm comfortable with the command line, so am not scared of the 'server' install.

OK, thanks so much for all of your help.

---

