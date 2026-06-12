---
title: "I can't install Firefox on Fedora Core 2"
date: 2004-12-20
forum: The Cafe
---

### Post by BWF89 on 2004-12-20
HORRAY!
I just got Fedora Core 2 to run on my Windows backup partition which has 2.6 gigs...

Anyway, I downloaded Firefox but when I clicked on the installation file I got this:
[IMG]http://img.photobucket.com/albums/v399/BWF89/install.png[/IMG]

How do I make it so when I click on the Firefox installation it installs as it would with Windows?

I also need a Redhat driver for a Cannon S520 printer...

---

### Post by jdong on 2004-12-20
yum install firefox

---

### Post by jdong on 2004-12-20
Why FC2, not FC3? Why FC? Why not another Ubuntu, say, Hoary? Why am I asking you? Why am I asking you why I am asking you? Why am I asking you why I am asking you why am I asking you?

---

### Post by BWF89 on 2004-12-20
[QUOTE=jdong]yum install firefox[/QUOTE]
I have Up2date. And it doesn't say anything about Firefox on it...
[QUOTE=jdong]Why FC2, not FC3? Why FC? Why not another Ubuntu, say, Hoary? Why am I asking you? Why am I asking you why I am asking you? Why am I asking you why I am asking you why am I asking you?[/QUOTE]
Because Ubuntu's partitioning software scared me and Fedora's was easy. And because I only have 2.6 gigs of hdd space and FD3 is probably bigger than FC2. And because I just happened to have FD2 laying around the house...

---

### Post by jdong on 2004-12-20
Use some 3rd party repository, whether freshrpms or dag. Use APT if possible, too. Firefox is prepackaged in a lot of those repositories.

---

### Post by ChrisP on 2004-12-20
because a teenager is asking an adult for advice and said teenager has got under aldults skin. Like duh?....................  :)

---

### Post by BWF89 on 2004-12-20
I tried Freshrpms...

Can someone just give me the link to a good site that has Redhat compatible software that installs right out of the box?

---

### Post by eBopBob on 2004-12-20
BWF89, you so should have gone for SuSE!
It'd have been so much easier to install Firefox there.


> How do I make it so when I click on the Firefox installation it installs as it would with Windows?
Sorry, I've not used FC2 although do have it on four CDs (Darn, paid £5 for it and never used it!!). But I know in SuSE with YaST, it was pretty much like in Windows. Not looking exactly the same, however just as easy. Although, TBH, I found compiling from source was also just as easy.
However if you have a .tar.gz you must compile from source (I think), which is very easy to do. You shouldn't be afraid of the command line - Once you face your fears, you'll really learn in Linux and it'll help you in the future too.


> Because Ubuntu's partitioning software scared me
Is it that hard?! (Is having second thoughts...)
I read though that the Ubuntu team are working on a graphical installed like that of FC, Mandrake or SuSE. Is this true?

---

### Post by BWF89 on 2004-12-20
I downloaded a Firefox RPM and it still doens't work [http://www.linuxquestions.org/questions/history/255845](http://www.linuxquestions.org/questions/history/255845)...

How do I get it to work? How do I compile the source as you would say?

---

### Post by eBopBob on 2004-12-20
[http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=15](http://www.linuxquestions.org/questions/answers.php?action=viewarticle&artid=15)

Follow the instructions there. Very easy.

The only problem I had with SuSE was, and am told this is actually the same no matter what distro or package management, once I started installing some things by RPM with YaST and some things compiling from source, it would just mess up in the end and I'd have two versions of something one working here for this I installed via RPM and one for the one I compiled via source and in the end it was a real mess and some things wouldn't work. :P
So be careful!!! :P

---

### Post by Quest-Master on 2004-12-20
Oh wow.. Ubuntu's partitioning is as easy as anything. x_x!!!

All you do is make some free space on your hard drive and select the option to automatically repartition the space for Ubuntu and it is done.

---

### Post by BWF89 on 2004-12-20
Ok, I didn't understand one thing on that compliling source code page. Is there something I can download that will make things install like on Windows...

Sorry if I'm sound like a newb but all I want is for my OS to "just work" with as little amount of work done by me as possible...

---

### Post by jdong on 2004-12-20
then you'd want Ubuntu.

---

### Post by BWF89 on 2004-12-20
[QUOTE=jdong]then you'd want Ubuntu.[/QUOTE]
Are programs for it easy to install. As in I click the file and it starts up the setup wizard?

---

### Post by jdong on 2004-12-20
A lot fewer questions and a LOT more straightforward than fedora's.

---

### Post by bob k on 2004-12-20
[QUOTE=BWF89]I downloaded a Firefox RPM and it still doens't work [http://www.linuxquestions.org/questions/history/255845](http://www.linuxquestions.org/questions/history/255845)...

How do I get it to work? How do I compile the source as you would say?[/QUOTE]

I belive that the correct fourm is www/fedoraforum.org/
and good luck on that work of bloat. All fedora is a beta for the next RH release ant the odds on getting a stable os are slim to nill.

---

### Post by eBopBob on 2004-12-21
> Ok, I didn't understand one thing on that compiling source code page. Is there something I can download that will make things install like on Windows...

Sorry if I'm sound like a newb but all I want is for my OS to "just work" with as little amount of work done by me as possible...
Oh... alright then. Lemme explain. :)

You download your file to somewhere. You then CD to the folder the file is in.
You then do: **tar zxf file.tar.gz**
Remember that you replace file with the file's name.
That should create a new folder, so you then do: **cd folder**
However replace folder with the newly created folders name.
Then type: **./configure**
This will tell you if you're missing anything AFAIK.
Then type: **make**
This will tell you more. Here you'll know if it fails or not AFAIAA,
Then type: **make install**
Now, if all went well - You've just installed Firefox! :)


You may think the above is very hard or complicated, but trust me, it'll be useful in the end.



> then you'd want Ubuntu.
Would you say it's easier to install things with Ubuntu than it is with SuSE using YaST?



> I believe that the correct forum is www/fedoraforum.org/
and good luck on that work of bloat. All fedora is a beta for the next RH release ant the odds on getting a stable os are slim to nill.
Yet another thing I find hilarious about the Linux community. Would you rather someone use Windows or any Linux distro? I mean, so many Linux people say you cannot use Windows, but you cannot use any Linux distro. Shouldn't you be thankful that it's one more person moving to Linux, regardless of the distro, than using Windows?

---

### Post by BWF89 on 2004-12-21
> You download your file to somewhere. You then CD to the folder the file is in.
You then do: tar zxf file.tar.gz
Remember that you replace file with the file's name.
That should create a new folder, so you then do: cd folder
However replace folder with the newly created folders name.
Then type: ./configure
This will tell you if you're missing anything AFAIK.
Then type: make
This will tell you more. Here you'll know if it fails or not AFAIAA,
Then type: make install
Now, if all went well - You've just installed Firefox!
Could you please be a little bit clearer? I "CD the folder"? I "do tar zxf file.tar.gz"? Where exactly do I do it? How EXACTLY do I do everything?

---

### Post by rbrimhall on 2004-12-21
[QUOTE=BWF89]Could you please be a little bit clearer? I "CD the folder"? I "do tar zxf file.tar.gz"? Where exactly do I do it? How EXACTLY do I do everything?[/QUOTE]

See this site:
[http://freespace.virgin.net/kevin.pearson/fedora/010.html](http://freespace.virgin.net/kevin.pearson/fedora/010.html)

By the way FC3 comes with Firefox 1.0 already...

---

### Post by rbrimhall on 2004-12-21
[QUOTE=eBopBob]Oh... alright then. Lemme explain. :)

You download your file to somewhere. You then CD to the folder the file is in.
You then do: **tar zxf file.tar.gz**
Remember that you replace file with the file's name.
That should create a new folder, so you then do: **cd folder**
However replace folder with the newly created folders name.
Then type: **./configure**
This will tell you if you're missing anything AFAIK.
Then type: **make**
This will tell you more. Here you'll know if it fails or not AFAIAA,
Then type: **make install**
Now, if all went well - You've just installed Firefox! :)


Firefox does not need configure,make, or make install... you just extract and run it from the folder.

---

### Post by eBopBob on 2004-12-21
Oh right. Sorry 'bout that. :D



- You download the file

- You open up xterm, Konsole or terminal (read: the command line)

- You type: **cd folder**
-- This means you're going to the folder which you downloaded firefox.tar.gz into; remember to replace folder with the actual folder you downloaded it into!

- You then type: **tar zxf file.tar.gz**
-- You type this in the command line. Basically here you're telling it to "unzip" the .tar.gz file; also remember to replace file with the actual file's name!

- Type: **cd folder**
-- Here again in the command line, you're saying you want to go to the folder that the step above has just created. Remember to replace "folder" with the newly created folder's name.

- Type: **./configure**
- Now wait until this command has been completed. You'll know when it's completed. You'll then be able to type again. It should take a while.

- Type: **make**
-- Again, wait until this has been completed. It should take a while.

- Type: **su**
-- Here you are entering root. I've no idea the diff. between su and sudo. I only know of su. It'll ask for your root password. You enter it and press enter.

- Type: **make install**
-- Here you are installing... this has to be done in root, and above you've just su'd into root so it's fine. This should also take a while.



Now, if all has gone well, you've installed Firefox.
This all needs to be done in terminal (the command line). Maybe you want to use xterm, I'm not sure. I've forgotten Gnome's terminal (I however often used xterm before though).

If you need anymore help, let me know.

---

### Post by eBopBob on 2004-12-21
> Firefox does not need configure,make, or make install... you just extract and run it from the folder.
Oh!
Didn't realise this. I remember when I installed Firefox (however it wasn't v1.0) I did all that. Didn't know you don't have too.  :oops:

---

### Post by BWF89 on 2004-12-21
> Firefox does not need configure,make, or make install... you just extract and run it from the folder.
That doesn't work on Fedora, it extracts but when you click on and of the files it either does nothing or says something like "GNOME can assist in opening packages". And when I choose the package program to open the pakage with it doesn't do anything...

---

### Post by rbrimhall on 2004-12-21
You would need to do that only if compiling source tarballs but you'd have to search for those I would think ;)  I've been using firefox since 0.5 and you just untarred/unzipped the folder, moved it were you wanted it, and run the binary. The only time I did configure, make, make install was when I was building optimized packages from the trunk.

---

### Post by rbrimhall on 2004-12-21
[QUOTE=BWF89]That doesn't work on Fedora, it extracts but when you click on and of the files it either does nothing or says something like "GNOME can assist in opening packages". And when I choose the package program to open the pakage with it doesn't do anything...[/QUOTE]

You'll need to use the terminal to launch... also, to put the binary in your path. The link I posted has how to do all of this. Just use the terminal for the commands.

like,

cd firefox-installer (after you've untarred it)
./firefox-installer

This runs the installer. Then,
 
./firefox

This launches the browser

You then move the folder to wherever (/usr/local is good) and set up symlinks for the binary.

cd (this returns you to home)
sudo mv firefox-installer /usr/local

cd /usr/local/bin
sudo ln -s /usr/local/firefox-installer/firefox firefox

Now you can just type firefox in a terminal and it will launch.

---

### Post by BWF89 on 2004-12-21
[QUOTE=rbrimhall]You'll need to use the terminal to launch... also, to put the binary in your path. The link I posted has how to do all of this. Just use the terminal for the commands.

like,

cd firefox-installer (after you've untarred it)
./firefox-installer

This runs the installer. Then,
 
./firefox

This launches the browser

You then move the folder to wherever (/usr/local is good) and set up symlinks for the binary.

cd (this returns you to home)
sudo mv firefox-installer /usr/local

cd /usr/local/bin
sudo ln -s /usr/local/firefox-installer/firefox firefox

Now you can just type firefox in a terminal and it will launch.[/QUOTE]

[SIZE=7]IT WORKED!!!
NOW I FEEL LIKE A REAL LINUXER![/SIZE]

---

### Post by rbrimhall on 2004-12-21
awesome!

---

### Post by BWF89 on 2004-12-21
I set Firefox as my defult browser. But how do I get Mozilla back so I can use it with FIrefox,  Why don't I have the official Firefox icon on my desktop? All I have is the systems defult internet icon...

And does anyone know a good programs I can use to play MPG and MPEG movies? And anywhere I can download SETI@Home for GNU/Linux? I just don't feel right about leaving my computer on for hours and not scanning for extra terestrial lifeforms...

---

### Post by DouglasAWh on 2008-01-06
I'm assuming this guys questions were answered or he stopped caring...

but, the use of the Firefox logo is forbidden in modified versions of Firefox.

---

### Post by Polygon on 2008-01-06
HOLY BUMP BATMAN

notice the date =P

---

