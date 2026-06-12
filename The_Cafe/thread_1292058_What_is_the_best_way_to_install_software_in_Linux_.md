---
title: "What is the best way to install software in Linux without an internet connection?"
date: 2009-10-15
forum: The Cafe
---

### Post by emigrant on 2009-10-15
hi guys,
iv been wondering for sometime,
that even though Linux is open source and is aimed at highly cutting down expenses and thus making the OS affordable even to the poorest part of the world.
but again if the person installing doesnt have an internet connection (most of the time a connection with a fair speed) then the installation is virtually no use.

on the other hand, MS softwares can be downloaded (cracked ones) from a high speed internet cafe or other machines and can be brought to the installation machine.

is there anyway that we can do this same thing for linux?
ie. downloading the necessary things from a high speed connection and installing them back in the home machine?

i mean the applications, not the OS.
for ex, is it possible to download eclipse and bring it home and install in the machine? what about the dependencies?

i hope you understand my question.

thank you.:KS

---

### Post by toupeiro on 2009-10-15
sudo apt-get install -d <package_name>

e.g.

> toupeiro@mobius:~$ sudo apt-get install -d am-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libamu4
Suggested packages:
  nis am-utils-doc
The following NEW packages will be installed:
  am-utils libamu4
0 upgraded, 2 newly installed, 0 to remove and 543 not upgraded.
Need to get 583kB of archives.
After this operation, 1,155kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://mirrors.easynews.com](http://mirrors.easynews.com) karmic/universe libamu4 6.1.5-12ubuntu1 [167kB]
Get:2 [http://mirrors.easynews.com](http://mirrors.easynews.com) karmic/universe am-utils 6.1.5-12ubuntu1 [416kB]
Fetched 583kB in 1s (404kB/s) 
Download complete and in download only mode


Trust me on this, if there is one thing Windows DEFINITELY doesn't beat linux on, its app and patch delivery mechanisms.  Be prepared to spend thousands for an aptitude equivalent on windows in an enterprise, and the best ones are not built by Microsoft.

---

### Post by Capt. Blackwood on 2009-10-15
that is a good question. I can only say that doing good things comes at a price.
 
I don't know if that'll answer it. But, that's my reason.

---

### Post by emigrant on 2009-10-15
so you mean,
after installing the main package we have to check what are the depenedecies, and note them down and go the the cafe againd and download them? :-([-(
> **toupeiro said:**
> sudo apt-get install -d <package_name>

e.g.



Trust me on this, if there is one thing Windows DEFINITELY doesn't beat linux on, its app and patch delivery mechanisms.

---

### Post by toupeiro on 2009-10-15
> **arshad3m said:**
> so you mean,
after installing the main package we have to check what are the depenedecies, and note them down and go the the cafe againd and download them? :-([-(

No.  Apt-get still does this.  as you can see, I requested to download am-utils, it also grabbed a dependency called libamu4.  when I get home, I will just do an apt-get install am-utils without the -d and since they will be in the local cache, it will just install them.  processing the installs doesn't take a great deal of time though, and in most cases wont interrupt your work.  I *wouldn't* you install right after you downloaded, unless you were downloading from one machine to install on another (which I wouldn't recommend unless you are 100% sure of the architecture type and version.)

everything gets downloaded into /var/cache/apt/archives.

---

### Post by CharlesA on 2009-10-15
Any package manager will check dependencies and download them (if needed) when you go to install any application.

---

### Post by emigrant on 2009-10-15
no bro, i mean how can i download the application together with the dependencies from a windows machine?
all the cafes are running in windows :(

---

### Post by toupeiro on 2009-10-15
oh, sorry that wasn't exactly clear that you WANTED to do it from a windows client.  You implied you just wanted the network connection at the cafe.

well, it would take some time but you could browse the repo from a web browser if its not secured down, which has header files containing dependencies.

Alternatively, bring a keychain bootable version of ubuntu.

I think you are basically asking for aptitude for windows.  To my knowledge that doesn't exist, and I can't really think of a good reason for it to as it doesn't benefit windows in the slightest.

---

### Post by TiredBird on 2009-10-15
I think I must be misunderstanding the question. It seems to me that whether it is MS Windows or Ubuntu, you have to either have to have the CD's or a suitable internet connection. 

It seems to me that whether taking if from a CD or from the Internet, that the 'deb' packaging scheme is far superior to anything offered by Redmond or its friends, for the initial install itself, for add-on applications and for updates.

Am I missing something?

---

### Post by diesch on 2009-10-15
Have a look at [Keryx](http://keryxproject.org/).

---

### Post by toupeiro on 2009-10-15
Also, you can always hit the application you want's project page.  Most of them will offer you a link to download the .deb file.  The dependencies you need should be listed there.  Google them.  It's not as easy as aptitude, but what you are trying to accomplish is a lot like someone using a potato peeler instead of a screwdriver to screw in a bolt.

EDIT, I'll be damned, looks like keryx can do it.  But now you are banking that your internet cafe will allow you to install a program on their computer. :P

---

### Post by Screwdriver0815 on 2009-10-15
maybe some how to's to create an offline repository help?

[http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html](http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html)

[http://ubuntuforums.org/archive/index.php/t-1045375.html](http://ubuntuforums.org/archive/index.php/t-1045375.html)

---

### Post by emigrant on 2009-10-15
thank you for your replies,
to simplify my question...
a windows machine has internet connection. ubuntu machine doesnt have internet.
how can i download the applications/softwares from the windows machine and install it in the ubuntu one.?
thank you.

---

### Post by unoodles on 2009-10-15
I had the same issue as you. I had dialup at home, so I had to make a list and download them all on a fast connection elseware, and then bring them all back home.

The two things that I came up with were:
1. Use AptOnCD.
2. Get A large external drive, and download the entire repository.

---

### Post by CharlesA on 2009-10-15
> **unoodles said:**
> I had the same issue as you. I had dialup at home, so I had to make a list and download them all on a fast connection elseware, and then bring them all back home.

The two things that I came up with were:
1. Use AptOnCD.
2. Get A large external drive, and download the entire repository.

AptOnCD sounds promising.

---

### Post by howefield on 2009-10-15
> **arshad3m said:**
> how can i download the applications/softwares from the windows machine and install it in the ubuntu one.?

diesch has given you an answer, as have others.

Btw, what has the question got to do with the thread title ?

---

### Post by emigrant on 2009-10-15
> **howefield said:**
> diesch has given you an answer, as have others.



thank you all :),

> **howefield said:**
> 
Btw, what has the question got to do with the thread title ?

if you are asking why id say ms is less costly than ubuntu,
its my personel experience and may be differ to others depending on their location.
if i need to install a windows app, most of the time i just borrow a cracked cd from a friend,
but with ubuntu i need a fast internet.

---

### Post by howefield on 2009-10-15
> **arshad3m said:**
> if you are asking why id say ms is less costly than ubuntu,

No I wasn't asking that.

---

### Post by TiredBird on 2009-10-15
Maybe I am beginning to understand now - you want to download the software at an internet cafe that runs only windows machines and then take it home and install it on your ubuntu system that is not connected to the internet.

Assuming that is the question, it is almost exactly what I was recently faced with. I lost my high speed internet connection for several weeks. I had new software I wanted to install and stuff that needed to be updated but no high-speed connection.

I took my laptop to a local hotspot, connected a USB harddrive to it and, using apt-mirror, built my own software repository. Then I took it home and without an internet connection, was able to get new software and update the old stuff.

Yes its a long down-load. It actually took me several days. But I was able to get the hot spot provider to allow me to leave my machine, unattended, even when they were closed, and keep the download going. (Apt-mirror is smart enough to restart near where it was when interrupted. It does not have to start over.)

Now that I have the high-speed internet connection back up, I still maintain the mirror. It updates each night while I sleep and then my updates and installs are super fast. I like it!

"Necessity is the motherhood of invention." "Where there's a will there's a way." "May the wind always be at your back." and other important admonitions.

---

### Post by CharlesA on 2009-10-15
> **arshad3m said:**
> 
if you are asking why id say ms is less costly than ubuntu,
its my personel experience and may be differ to others depending on their location.
if i need to install a windows app, most of the time i just borrow a cracked cd from a friend,
but with ubuntu i need a fast internet.

Cuz cracked apps are awesome, right? :-#

---

### Post by emigrant on 2009-10-15
> **howefield said:**
> No I wasn't asking that.

do you mind briefing,i think others understand the title, though my eng is weak.

---

### Post by emigrant on 2009-10-15
> **TiredBird said:**
> Maybe I am beginning to understand now - you want to download the software at an internet cafe that runs only windows machines and then take it home and install it on your ubuntu system that is not connected to the internet.

Assuming that is the question, it is almost exactly what I was recently faced with. I lost my high speed internet connection for several weeks. I had new software I wanted to install and stuff that needed to be updated but no high-speed connection.

I took my laptop to a local hotspot, connected a USB harddrive to it and, using apt-mirror, built my own software repository. Then I took it home and without an internet connection, was able to get new software and update the old stuff.

Yes its a long down-load. It actually took me several days. But I was able to get the hot spot provider to allow me to leave my machine, unattended, even when they were closed, and keep the download going. (Apt-mirror is smart enough to restart near where it was when interrupted. It does not have to start over.)

Now that I have the high-speed internet connection back up, I still maintain the mirror. It updates each night while I sleep and then my updates and installs are super fast. I like it!

"Necessity is the motherhood of invention." "Where there's a will there's a way." "May the wind always be at your back." and other important admonitions.

thank you very much for your reply,
yes thats what i exactly mean.
i think i have to get more used to linux to understand what you did :P
for the time being, id try [http://keryxproject.org/](http://keryxproject.org/) or [http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html](http://blog.mypapit.net/2007/03/put-apt-get-repository-on-dvdcd-ubuntudebian.html) or [http://ubuntuforums.org/showthread.php?t=1045375](http://ubuntuforums.org/showthread.php?t=1045375) (which i think is what you are talking about)

---

### Post by Warpnow on 2009-10-15
There is a DVD version of ubuntu which has more packages and is more likely to meet random dependencies of .deb files you download, isn't there?

---

### Post by TiredBird on 2009-10-15
> **arshad3m said:**
> ...i think i have to get more used to linux to understand what you did :P
I followed directions I found on the internet. Google 'ubuntu local repository'. That will give you a good start. Its not rocket science. Most of its point and click from most Ubuntu installations. A small amount of command line is probably necessary.

---

### Post by TiredBird on 2009-10-15
There is an attempt underway to bring together the relevant pieces necessary to create a local repository as well as some other nifty things with Ubuntu but its not all there yet. If you want to look at what there is so far, [click here]("http://only4geeks.net/").

---

### Post by samigina on 2009-10-15
Very very easy...

1. In your Ubuntu machine open **Synaptic**, select the program you want to install, it will select the dependencies; then go to the synaptic ma**in menu and choose Generate download script**, this will create a text file in your home with the urls of all the .debs selected with the dependencies.

2. Copy the text file to your usb stick.

3. In the Windows machine open the text file and, copy and paste every url to download or just use a download manager and go for a cofee.

4. Copy the downloades packages to your usb stick.

5. Back in your ubuntu machine, go to **Synaptic**, in the main menu choose **Add downloades packages** and select the directory where are the downloaded .debs.

Synaptic boys has already thinked about the people without internet connection. They arent so evil :D

---

### Post by TiredBird on 2009-10-15
> **samigina said:**
> Very very easy..

I've used Ubuntu for several years now and had no idea this was available. Thanks.

---

### Post by emigrant on 2009-10-15
> **samigina said:**
> Very very easy...

1. In your Ubuntu machine open **Synaptic**, select the program you want to install, it will select the dependencies; then go to the synaptic ma**in menu and choose Generate download script**, this will create a text file in your home with the urls of all the .debs selected with the dependencies.

2. Copy the text file to your usb stick.

3. In the Windows machine open the text file and, copy and paste every url to download or just use a download manager and go for a cofee.

4. Copy the downloades packages to your usb stick.

5. Back in your ubuntu machine, go to **Synaptic**, in the main menu choose **Add downloades packages** and select the directory where are the downloaded .debs.

Synaptic boys has already thinked about the people without internet connection. They arent so evil :D

:P
thank you very much,
thats great,
yum extender (fedora's counterpart for synaptic) doesnt have that generate download script function,
but doesnt matter iv to shift to ubuntu with the coming 9.10 release. ;)

---

### Post by papangul on 2009-10-15
> **samigina said:**
> Very very easy...

Some programs are not available in synaptic unless extra repos are added and 'apt-get update' is run.

---

### Post by JillSwift on 2009-10-15
> **samigina said:**
> Very very easy...

1. In your Ubuntu machine open **Synaptic**, select the program you want to install, it will select the dependencies; then go to the synaptic ma**in menu and choose Generate download script**, this will create a text file in your home with the urls of all the .debs selected with the dependencies.

2. Copy the text file to your usb stick.

3. In the Windows machine open the text file and, copy and paste every url to download or just use a download manager and go for a cofee.

4. Copy the downloades packages to your usb stick.

5. Back in your ubuntu machine, go to **Synaptic**, in the main menu choose **Add downloades packages** and select the directory where are the downloaded .debs.

Synaptic boys has already thinked about the people without internet connection. They arent so evil :D
'Tiz a thing of beauty.

---

### Post by m4tic on 2009-10-16
WTF, lol i've also been using Ubu for a year now and didnt even notice it. I also do not have internet and sometimes rely on my SE phone as a modem but it's cost me a lot. But i was just checking the script it generated for Amarok. A lot of dependencies there. 

A simple q i'd like answered is, the packagers surely know what the program depends on. so why not, like windows, include them in the main pack instead of us having to hunt them down. Its proving to cost us a lot more time and money hunting for information and ending up with a bad package build.

I know everything is done for us for free but somethings just should be there regardless because its getting annoying. There's a movie player called Gom player, would love to see an ubuntu version coming up (that i won't mind spending time hunting dependencies for)

---

### Post by Chame_Wizard on 2009-10-16
> **samigina said:**
> Very very easy...

1. In your Ubuntu machine open **Synaptic**, select the program you want to install, it will select the dependencies; then go to the synaptic ma**in menu and choose Generate download script**, this will create a text file in your home with the urls of all the .debs selected with the dependencies.

2. Copy the text file to your usb stick.

3. In the Windows machine open the text file and, copy and paste every url to download or just use a download manager and go for a cofee.

4. Copy the downloades packages to your usb stick.

5. Back in your ubuntu machine, go to **Synaptic**, in the main menu choose **Add downloades packages** and select the directory where are the downloaded .debs.

Synaptic boys has already thinked about the people without internet connection. They arent so evil :D
good to know.:guitar:

---

### Post by MaxIBoy on 2009-10-16
You can mirror the repositories. They are about 30 gigabytes compressed; if you have that much hard drive space floating around. Spend a solid few days (or a week depending on your speed) downloading snapshot of the repositories, then use that.

I recommend creating a separate partition for it if possible.

---

