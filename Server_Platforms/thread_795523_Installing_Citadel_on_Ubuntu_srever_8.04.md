---
title: "Installing Citadel on Ubuntu srever 8.04"
date: 2008-05-15
forum: Server Platforms
---

### Post by rickyslim on 2008-05-15
I'm fairly new to this Linux thing. I've got the server installed and have installed Webmin (I need a GUI, being new to this).

I now want to try Citadel but can't see an obvious way of doing it.

I go to the Command Shell in Webmin and enter the command as instructed on the Citadel site [[COLOR="Red"]here[/COLOR]](http://www.citadel.org/doku.php/installation:debian) but I get **bash: deb: command not found**

Any suggestions? I can do it direct on the server using a command if anyone can suggest the correct one to use. However, it would be useful learning how to install downloaded software onto the server via Webmin if anyone feels inclined to help.

Many thanks.

---

### Post by Ptero-4 on 2008-05-15
The "deb" part are lines you need to add to your /etc/apt/sources.list file.
Then do sudo aptitude update and sudo aptitude install citadel.

---

### Post by rickyslim on 2008-05-16
I seem to have added the deb lines and installed it by using the software menu in Webmin to find Citadel, then install it.

However, I don't seem to be able to find it to use it. What directory do programs install to? I've looked at the program list and it's not there.

---

### Post by HermanAB on 2008-05-16
Probably here:
/usr/local/citadel
/usr/local/webcit

You can probably start it with:
service citadel restart

When all else fails, use the Easy Install script on the Citadel web site.

Test it with telnet:
telnet localhost 25
telnet localhost 143

Cheers,

Herman

---

### Post by rickyslim on 2008-05-21
I tried the easy install.

I'm not entirely sure how the line should look that I need to add to the sources.list file.

I addded this line **deb [http://debian.citadel.org/debian/](http://debian.citadel.org/debian/) etch main** but it still doesn't work.

I've got Ubuntu Server 8.04.

---

### Post by motio on 2008-06-23
> **rickyslim said:**
> I tried the easy install.

I'm not entirely sure how the line should look that I need to add to the sources.list file.

I addded this line **deb [http://debian.citadel.org/debian/](http://debian.citadel.org/debian/) etch main** but it still doesn't work.

I've got Ubuntu Server 8.04.

look at [http://debian.citadel.org/](http://debian.citadel.org/)
you have to add add
deb [http://ubuntu.citadel.org/ubuntu/](http://ubuntu.citadel.org/ubuntu/) gutsy main
this will do the job

---

### Post by Vitaminico on 2008-11-19
> **Ptero-4 said:**
> The "deb" part are lines you need to add to your /etc/apt/sources.list file.
Then do sudo aptitude update and sudo aptitude install citadel.

Maybe i'm crazy but how i'm able to add lines? Where i can open sources list file?

Thanks

a noob.

---

### Post by dawbomb on 2009-03-16
Alright first of all, webmin is a fantastic tool for configuration, however, when it comes down to installing software, and some configuration, the best way of doing it is still in the shell. So, shell basics. 
To give your command administrative priviledges, type sudo before your command. nano is a decent text editor. This is followed by the path. So in your case, you would login to the server, then type sudo nano /etc/apt/sources.list , and press enter. Enter your password. Go to the end of the file, and on a new line, enter the address. Control X exits, press y followed by enter to save. Easy! I know it seems impossible, but u get used to it in the end. Other useful commands are:
cd DIRECTORY  - set directory, eg cd /etc/apt/ , and then u can just type sudo nano sources.list.
cd ..  - Will move up one directory.
mkdir FOLDER  -  makes a new directory. 
rmdir FOLDER  -  deletes a directory.
rm FILE  -  deletes a file.
rm -r FOLDER  -  deletes a folder and all contents.
where FOLDER, FILE and DIRECTORY are, well, files folders and directories.
To logout, type sudo logout, to shutdown type sudo poweroff. Easy!

---

### Post by gabak on 2010-07-25
do this

Base install of required programs.
in the terminal

sudo apt-get install clamav clamav-milter spamassassin citadel-suite amavisd-new


[http://beginlinux.com/blog/2009/01/citadel-groupware-install/](http://beginlinux.com/blog/2009/01/citadel-groupware-install/)

---

