---
title: "How to compile Password Gorilla from source code."
date: 2007-04-30
forum: Tutorials
---

### Post by GiveLove on 2007-04-30
Hello people,

This was done successfully on both Ubuntu v6.10 and v7.04 using "Password Gorilla" v1.4.
Here is the link to the web site for Password Gorilla:
[http://www.fpx.de/fp/Software/Gorilla/]("http://www.fpx.de/fp/Software/Gorilla/")


First you'll need to go into the "Synaptic Package Manager" (System -> Administration -> Synaptic Package Manager),  and install the following software dependencies:

tcl8.4
tcl8.4-dev
tk8.4
tk8.4-dev
itk3
itk3-dev
bwidget

Use the "Search" button in Synaptic Package Manager. Type in "tcl" and then press the "Enter" key. All of the required software packages show up in the long list of results that you will have to scroll through to find. Single right mouse click on each package that you need and select "Mark for Installation". Some of the packages will have other dependent packages that it will need, and it will ask you "Mark additional required changes?" Click on the "Mark" button to say yes to this.



Instructions for installing system wide.

Open a terminal and type the following, one line at a time, and pressing the enter key after each line. Do not enter the # sign and the space after it. That just signifies that it is a command line. Make sure you have an internet connection ready as the second command line downloads the source code file from the internet into the /opt directory.

```
# cd /opt
# sudo wget http://www.fpx.de/fp/Software/Gorilla/download/gorilla-1.4.tar.gz
# sudo tar -xf gorilla-1.4.tar.gz
```

You'll then have to change the owner and group.

```
# sudo chown -R root:root /opt/gorilla-1.4
```

Next you have to add "group" read and execute permissions for the whole gorilla-1.4 directory.

```
# sudo chmod -R g+rx /opt/gorilla-1.4
# sudo chmod -R 777 /opt/gorilla-1.4
```

Change the working directory.

```
# cd gorilla-1.4/
```

The following command configures the program.

```
# sudo ./configure
```

Then you should be able to run the program from the terminal with the command:

```
# /opt/gorilla-1.4/./gorilla
```

More than likely though you will prefer to run it by clicking an icon in the Applications menu.
To do so, open the "System -> Preferences -> Main Menu". Select which menu you want it in on the left hand side. Then click on the "New Item" button, Type in the name of the program(Password Gorilla), and the command which is the last command above this paragraph. Then click on the "No Icon" button and type in the following path in the top part of the window:

/opt/gorilla-1.4/pics

Select "gorilla-48x48.gif", then click on the "Ok" button and your done. 


Enjoy! :)

---

### Post by Didjit on 2007-05-02
Any advantage over just grabbing the kit and runnig the 1.4X version? 

[http://www.glump.net/dokuwiki/howto/ubuntu_feisty_on_thinkpad_x41](http://www.glump.net/dokuwiki/howto/ubuntu_feisty_on_thinkpad_x41)

It works fine on Feisty.

Didjit

---

### Post by GiveLove on 2007-05-25
Hello Didjit,

My apologies for not answering your question sooner. I don't check this that often as it is so far my only post here.

      The reason why I did not use the kit version was because when I first started using Linux running Fedora Core 5, I was unable to get the kit version to work. So I had to laboriously learn to compile it from source. So with each successive version and/or distribution of Linux that I have used. Out of habit I always compiled Password Gorilla from source. Knowing that it would work. In the process I completely forgot about making it work from kit when I switched to Ubuntu.

       As far as any advantage, I have no idea as I've never been able to use it from kit. But on an unrelated note, I will say that just about everything appears to perform faster and/or load faster in Ubuntu v7.04, versus Fedora Core 5 and 6. LOL And that definitely includes Password Gorilla.   

Thank you for letting me know that the kit version of Password Gorilla works fine with v7.04. I'll save myself some time and labor next time I reinstall to a new version of Ubuntu, and use the kit version.

Take care :)

---

### Post by n.aggel on 2007-07-29
> **GiveLove said:**
> Hello people,

This was done successfully on both Ubuntu v6.10 and v7.04 using "Password Gorilla" v1.4.
Here is the link to the web site for Password Gorilla:
[http://www.fpx.de/fp/Software/Gorilla/]("http://www.fpx.de/fp/Software/Gorilla/")


First you'll need to go into the "Synaptic Package Manager" and install the following software dependencies:

tcl8.4
tcl8.4-dev
tk8.4
tk8.4-dev
itk3
itk3-dev
bwidget

If I remember correctly, if you just do a search for "tcl", all of these software packages show up in the long list of results.



Instructions for installing system wide.

Open a terminal and type the following, one line at a time, and pressing the enter key after each line. Do not enter the # sign and the space after it. That just signifies that it is a command line. Make sure you have an internet connection ready as the second command line downloads the source code file from the internet into the /opt directory.

# cd /opt
# sudo wget [http://www.fpx.de/fp/Software/Gorilla/download/gorilla-1.4.tar.gz](http://www.fpx.de/fp/Software/Gorilla/download/gorilla-1.4.tar.gz)
# sudo tar -xf gorilla-1.4.tar.gz

My apologies. In the second command line above, the last half of the command gets tagged as a URL, and I can't seem to find a way to not make that happen. So you will have to type "sudo wget", then a space, and then copy that link and paste it in the terminal to have the full command.

You'll then have to change the owner and group.

# sudo chown -R root:root /opt/gorilla-1.4

You then will have to add "group" read and execute permissions for the whole gorilla-1.4 directory.

# sudo chmod -R g+rx /opt/gorilla-1.4

The following command configures the program.

# sudo ./configure

Then you should be able to run the program from the terminal with the command:

# /opt/gorilla-1.4/./gorilla

More than likely though you will prefer to run it by clicking an icon in the Applications menu.
To do so, open the "System -> Preferences -> Main Menu". Select which menu you want it in on the left hand side. Then click on the "New Item" button, Type in the name of the program(Password Gorilla), and the command which is the last command above this paragraph. Then click on the "No Icon" button and type in the following path in the top part of the window:

/opt/gorilla-1.4/pics

Select "gorilla-48x48.gif", then click on the "Ok" button and your done. 


Enjoy! :)

Hi, great guide! I compile the program correctly, but i can run it only as sudo user..... any ideas?

Thanks in advnace,
N.A

---

### Post by n.aggel on 2007-08-03
i found it you simply have to do this::

```

sudo chmod -R 777 /opt/gorilla-1.4

```

type it to change  the permissions of this folder recursively....

---

### Post by GiveLove on 2007-08-22
Hello again,

I just recently had to re-install Ubuntu 7.04 again due to a hardware failure. So I went back and made some corrections and additions in the instructions. 

Out of curiosity I wanted to try the Starkit method of installing Password Gorilla that Didjit mentioned. 

Reference:
[http://www.fpx.de/fp/Software/Gorilla/#Download]("http://www.fpx.de/fp/Software/Gorilla/#Download")

What stopped me from attempting it was that I could not find the required "tclkit" in Synaptic. Does anyone know how, or if this program is listed in Synaptic? Or what component packages it consists of? I realize that I could download and install tclkit manually. But I was hoping it would be in Synaptic to keep things simple.

I was thinking that maybe all of the required packages for compiling Password Gorilla from source might be what tclkit is made up of. But it doesn't appear to be, as when I ran the following command:

tclkit gorilla-1.4.kit

from terminal. I got the following error:

bash: tclkit: command not found


If anyone has any thoughts concerning this, it would be much appreciated. Thanks. :)

---

### Post by Didjit on 2007-08-22
Go here [http://www.equi4.com/tclkit/](http://www.equi4.com/tclkit/).  Follow the DL instructions and choose tgz from the Download Matrix.

HTH

Didjit

---

### Post by Tuan Tran on 2007-08-22
great work on the guide. love this program now :)

---

### Post by n.aggel on 2007-08-22
another way to install it, without any need to change folder permissions is if you install it in folder, you "own" i.e.  ~/bin/gorilla ....

---

### Post by 2RichLand on 2007-10-27
Thank you soooo much for this clear and concise guide...you have saved me a lot of grief. I have been using Ubuntu for less than a week but my dual booting experiment wasn't too successful. So now Windows Vista won't load which made it a little tough to access the Password Safe file I've used. This program allowed me to retrieve it and save all the entries as a text file. Now I just need to figure out what to do about printing as it appears the Lexmark isn't supported. Much more to learn I know. Forward.

---

### Post by stuartsierra on 2007-11-04
I just upgraded to Ubuntu 7.10 Gutsy Gibbon, and the Password Gorilla Starkit stopped working:

```
$ tclkit gorilla-1.4.kit 
Floating point exception (core dumped)
```

So I followed the instructions here, and it worked just fine.  Thanks!
-Stuart

---

### Post by sksbir on 2008-03-01
A really nice work !!

just guess how I could retrieve my forum password to add a reply here ;) (using a password database under ubuntu, which was previously created under windows works fine)

a big big thanks for you work

just one little suggestion : 
*/opt/gorilla-1.4/./gorilla*  : /./ is not necessary.

*/opt/gorilla-1.4/gorilla* works fine.

---

### Post by GiveLove on 2008-05-10
Hello People, :)

Thank you for everyones help and input into making this a successful and productive post. 

I just recently upgraded to Ubuntu v8.04 and was absolutely delighted to find out that some kind soul added Password Gorilla as a package in Synaptic Package Manager. I installed it with no effort involved. And as far as I can tell it works great! 

A gigantic THANK YOU goes out to the person/people that added this program to the repository!!!


For those of you who are new to Ubuntu...
To install Password Gorilla on Ubuntu 8.04:

Open your "System" menu at the top left corner of the screen. 
Then select "Administration", and then "Synaptic Package Manager".
If it asks you for a password, enter your password that you use to log onto Ubuntu. This will open a separate window called "Synaptic Package Manager".

Within this window, click on the "Search" button at the top. This opens a small window called "Find". In this window type in "password-gorilla" (minus the quotes) in the "Search:" field. It may take a minute or two to complete the search depending on how fast your computer is. The end result should list one file called "password-gorilla". 

Single right mouse click on that file and select "Mark for Installation". It will tell you that it needs to load some dependencies to install this program. Allow it to do so. And then click on the "Apply" button at the top of the window. Once it has downloaded and installed the program and its dependencies. You can close Synaptic Package Manager. 

To run the program, open your "Applications" menu at the top left of your screen. You will find "Password Gorilla" in the "Accessories" folder.

Enjoy!  :)

---

### Post by GiveLove on 2008-10-10
Hello people,

I just wanted to let you know that I have stopped using Password Gorilla as of about a month ago. It's not that it is not functional. But more so because it is not being actively developed, is quite light on features, and occasionally brings up error messages upon start up. 

I've since moved to KeepassX, and I've been much happier. It has so far run solid, no errors. And has much more features and options. I'm very happy with it. :)

[http://www.keepassx.org](http://www.keepassx.org)

KeepassX is a cross platform password manager(Linux, Windows, Mac OSX) that is open source and is being actively developed. It is a fork of KeePass Password Safe that is only made for Windows. 

You can find and install KeePassX in the repositories via Synaptic Package Manager. Just use the instructions in my previous post. Except that you will search for "keepassx" (minus the quotes) instead.

Enjoy!

---

### Post by sksbir on 2012-07-03
> **GiveLove said:**
> Hello people,

I just wanted to let you know that I have stopped using Password Gorilla as of about a month ago. It's not that it is not functional. But more so because it is not being actively developed, is quite light on features, and occasionally brings up error messages upon start up. 

I've since moved to KeepassX, and I've been much happier. It has so far run solid, no errors. And has much more features and options. I'm very happy with it. :)

[http://www.keepassx.org](http://www.keepassx.org)
KeepassX is a cross platform password manager(Linux, Windows, Mac OSX) that is open source and is being actively developed. It is a fork of KeePass Password Safe that is only made for Windows. 
You can find and install KeePassX in the repositories via Synaptic Package Manager. Just use the instructions in my previous post. Except that you will search for "keepassx" (minus the quotes) instead.
Enjoy!


4 years after, I just did the same : gorilla --> keepass (not keepassX ) : link : [http://keepass.info/help/v2/setup.html#mono](http://keepass.info/help/v2/setup.html#mono)
better late has never ;)

---

