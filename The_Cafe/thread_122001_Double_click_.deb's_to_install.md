---
title: "Double click .deb's to install?"
date: 2006-01-26
forum: The Cafe
---

### Post by Kerberos on 2006-01-26
Why can't you do this?  It seems overly masochistic to require the command line, I seriously doubt it would take longer than 10 minutes to do, and would make life much easier.

Or is there a good reason why not?

---

### Post by Stormy Eyes on 2006-01-26
[QUOTE=Kerberos]Or is there a good reason why not?[/QUOTE]

**sudo dpkg -i foo.deb** isn't that difficult, and you'll *need* the output if something goes wrong.

---

### Post by Kerberos on 2006-01-26
[QUOTE=Stormy Eyes]**sudo dpkg -i foo.deb** isn't that difficult, and you'll *need* the output if something goes wrong.[/QUOTE]
But why not just alert the user with a popup if something goes wrong, or log it somewhere?  Why is typing **sudo dpkg -i foo.deb** superior to double clicking to a point where it makes the GUI method unneccesary?

---

### Post by tageiru on 2006-01-26
Installing .deb files are not really a common use case for debian derived systems. If someone wants to package something and offer it to the public they usually create a debian repository so that people that use the software can get updates automatically.

With that said I believe 6.04 will have a feature for installing .deb files by clicking on them.

---

### Post by tufkakf on 2006-01-26
[QUOTE=Kerberos]Why can't you do this?  It seems overly masochistic to require the command line, I seriously doubt it would take longer than 10 minutes to do, and would make life much easier.

Or is there a good reason why not?[/QUOTE]
Gdebi, which will be in dapper, allows you to do this.

It's even better, as it's not simply a frontend to dpkg (there are several already, btw.), but to apt, so that dependencies you need will also get automatically installed.

As to why there hasn't been such a program yet for ubuntu, I think the simple reason is that there wasn't one that worked the way the devs wanted it to work.

---

### Post by tufkakf on 2006-01-26
Oops, double post.

---

### Post by Kerberos on 2006-01-26
[QUOTE=tageiru]Installing .deb files are not really a common use case for debian derived systems. If someone wants to package something and offer it to the public they usually create a debian repository so that people that use the software can get updates automatically.

With that said I believe 6.04 will have a feature for installing .deb files by clicking on them.[/QUOTE]
That'll be nice (once they get it 6.04 stable).  I find the repos a bit iffy - half the time synaptic doesn't work or the repo is down and sometimes its only available as a .deb - and its a good metaphor people can get their heads around 'download and open this to install'.

Stormy Eyes - Don't worry I am sure you can turn off the double click install when they do add it.  ;)

---

### Post by tufkakf on 2006-01-26
[QUOTE=Kerberos]That'll be nice (once they get it 6.04 stable).  I find the repos a bit iffy - half the time synaptic doesn't work or the repo is down and sometimes its only available as a .deb - and its a good metaphor people can get their heads around 'download and open this to install'.

Stormy Eyes - Don't worry I am sure you can turn off the double click install when they do add it.  ;)[/QUOTE]
Weird.
I'm using ubuntu now since pre-warty and can only remember having troubles with the repos twice. IIRC it was also fixed quickly both times.

---

### Post by dabear on 2006-01-26
I'm looking forward to gdebi, but if you want double click install of debs (without dependencies checkin), you could try my dadebstaller.

I know it kinda suck, and I have a newer version avvailable than posted on these forums, but I just can't find the cd I burned it to :p

---

### Post by Alpha_toxic on 2006-01-26
btw, in Kubuntu/KDE when you right click on a .deb you have "Kubuntu package maneger > install package" or sth like that. So it's not even comand line any more... :)

---

### Post by Kerberos on 2006-01-26
[QUOTE=tufkakf]Weird.
I'm using ubuntu now since pre-warty and can only remember having troubles with the repos twice. IIRC it was also fixed quickly both times.[/QUOTE]
It didn't ever work initially due to the database being permenantly locked (despite nothing else using it).  Some kind person gave me a command to type which fixed it, but its been flakey ever since.  It also keeps showing me software that exists, but it isn't going to let me have unless I prod it repeatedly.

It did, however, have a version of scorched earth, which was nice.  :)

---

### Post by engla on 2006-01-26
Seriously, you could make that thing yourself. 

Make a python script that runs 'gksudo apt-get install' on the command line arguments, make the script nice and show errors with the dialog application.

Then select a deb -> open with -> choose the script. Then you can make it the default action.

---

### Post by prizrak on 2006-01-26
[QUOTE=tufkakf]Weird.
I'm using ubuntu now since pre-warty and can only remember having troubles with the repos twice. IIRC it was also fixed quickly both times.[/QUOTE]
Kerberos has an Ubuntu curse upon him, he has not been able to get anything runnig properly. Also he is the most dedicated Ubuntu user I ever heard of, all he got is problems and is STILL at it :)

---

### Post by tufkakf on 2006-01-26
[QUOTE=prizrak]Kerberos has an Ubuntu curse upon him, he has not been able to get anything runnig properly. Also he is the most dedicated Ubuntu user I ever heard of, all he got is problems and is STILL at it :)[/QUOTE]
Ah, I see. Thanks for the explanation. ;)

---

### Post by poofyhairguy on 2006-01-26
[QUOTE=tufkakf]
As to why there hasn't been such a program yet for ubuntu, I think the simple reason is that there wasn't one that worked the way the devs wanted it to work.[/QUOTE]

You nailed it.

Remember folks, if Ubuntu were a child it would only be three years old!

---

### Post by aysiu on 2006-01-26
Kerberos, you're hellbent on using Ubuntu, but Mepis seems to be more up your alley--it can do a click-install of .deb files.

I know you hate Mepis, but you're hurting only yourself...

---

### Post by Kerberos on 2006-01-26
[QUOTE=aysiu]I know you hate Mepis.[/QUOTE]
I proper hate Mepis!  :)

---

### Post by aysiu on 2006-01-26
Actually, Mepis uses KPackage to click-install .debs.
Any chance that a good old ```
sudo apt-get install kpackage
``` could solve your problem in Ubuntu--at least for KDE?

---

### Post by Paulus on 2006-01-26
it's pretty clear that this is needed, could it be an addition to synaptic? - would make sense instead of having lots of programs doing similar things

---

### Post by aysiu on 2006-01-26
[QUOTE=Paulus]it's pretty clear that this is needed, could it be an addition to synaptic? - would make sense instead of having lots of programs doing similar things[/QUOTE] Ideally, Synaptic would be made so that it includes your desktop as a virtual repository, so that if your desktop's .deb needed dependencies, those could be fetched from your regular online repositories.

---

### Post by engla on 2006-01-29
[QUOTE=engla]Seriously, you could make that thing yourself. 

Make a python script that runs 'gksudo apt-get install' on the command line arguments, make the script nice and show errors with the dialog application.

Then select a deb -> open with -> choose the script. Then you can make it the default action.[/QUOTE]

I'm learning python, so I had my try at it after bragging about this.

I made a small script that in theory gives you a double-click install of .debs. I haven't tested it a lot, but it seems to work.

The attached script is a python2.4 script. Make it executable, and name it .py and see if it works...

---

### Post by Iandefor on 2006-01-29
[quote=Kerberos]Why can't you do this? It seems overly masochistic to require the command line, I seriously doubt it would take longer than 10 minutes to do, and would make life much easier.

Or is there a good reason why not?[/quote] I wouldn't call it "overly masochistic." But it is something I've been hearing about as of late. So I whipped up a script for people who are hankering for it. It isn't a "double-click install", but it provides a GUI for the installation of .debs.

It's pretty crappy at the moment, but I'll license it under the GPL for people who want to play with it a little. 

to install it, extract the attached archive to ~, open up a terminal and type in
```

chmod 0775 ~/debinst && sudo cp /usr/bin
``` open up gedit and paste the following into a new file:

[Desktop Entry]
Encoding=UTF-8
Name=Debian Installer
Exec=gksu debinst
Type=Application

and save it with the name "Debian Installer.desktop" on the Desktop. I'll let the end user come up with an icon suitable for it. To execute it, double-click the launcher on the desktop, and select the file from the selection dialog. Enjoy!

---

### Post by mikwig on 2006-05-25
debinst is quite well made.

---

### Post by BoyOfDestiny on 2006-05-25
[QUOTE=mikwig]debinst is quite well made.[/QUOTE]

Erm. This thread got revived huh? 
Well gdebi is already with dapper. So yes, you can install by double clicking a deb, dependencies and all... :)

---

### Post by jsgotangco on 2006-05-25
gdebi is all you need. Download a deb, then just click on it (there's no menu entry for gdebi but its there when you need it).

---

### Post by ComplexNumber on 2006-05-25
just goes to show how limited debian is :D. if i double click an rpm on any distro,  it will ask me if i want to install it or not. i can also install multiple rpm's this way.

---

### Post by GarethMB on 2006-05-25
gDebi is awesome.

---

### Post by SeanTater on 2006-05-25
They can be very easily installed for me -- but I;m using Kubuntu and konq --

---

