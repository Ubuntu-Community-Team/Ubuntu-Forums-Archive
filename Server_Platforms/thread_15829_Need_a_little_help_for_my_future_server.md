---
title: "Need a little help for my future server"
date: 2005-02-17
forum: Server Platforms
---

### Post by TekZonz on 2005-02-17
Hello everyone,

First off, let me say that your distribution is really really good comparing to the previous distributions such as Fedora or Red Hat that I've had before. Keep up the good work :)

Now, I am going to set up a server on my ADSL (15/1) and for this I have chose this great distribution. Let's start with the one most basic aspect: SSH. I need to be able to have ssh start when the PC boots. I know how to install it (sudo apt-get install ssh) but how do I make it start at startup automatically.

Also, how do I make the PC boot into console mode automatically? Loading up a GUI is no use for me.

And third, can anyone show me a tutorial that explains how to install apache/MySQL because I have been unable to find one so far. But I am not very used to this site's navigation.

Thank you for your help, and I am truly sorry if one of these questions are either stupid or have been asked half a million times.

TekZone

---

### Post by ubuntu_fan on 2005-02-17
[QUOTE=TekZonz]Hello everyone,

First off, let me say that your distribution is really really good comparing to the previous distributions such as Fedora or Red Hat that I've had before. Keep up the good work :)

Now, I am going to set up a server on my ADSL (15/1) and for this I have chose this great distribution. Let's start with the one most basic aspect: SSH. I need to be able to have ssh start when the PC boots. I know how to install it (sudo apt-get install ssh) but how do I make it start at startup automatically.

Also, how do I make the PC boot into console mode automatically? Loading up a GUI is no use for me.

And third, can anyone show me a tutorial that explains how to install apache/MySQL because I have been unable to find one so far. But I am not very used to this site's navigation.

Thank you for your help, and I am truly sorry if one of these questions are either stupid or have been asked half a million times.

TekZone[/QUOTE]

Hi!

Do you still want to install X at all? If you're building a server, you might just be better doing a custom (basic) install by entering "custom" at the boot prompt of the installation Cd.

You should be able to "apt-get install mysql" and "apt-get install apache2" to install mysql and apache. You will probably also need to select the mysql interface specific to your language (such as PHP). It'll be called something like "mysql-php".

HTH,

a.

EDIT: Wrong boot param - where is my head today? ;)

---

### Post by Rottweiler on 2005-02-17
[QUOTE=TekZonz]Let's start with the one most basic aspect: SSH. I need to be able to have ssh start when the PC boots. I know how to install it (sudo apt-get install ssh) but how do I make it start at startup automatically.[/quote][font=Courier New]That's all you need to do:[/font]```
sudo apt-get install ssh
``` [font=Courier New]The install script will put the right links into /etc/init.d and /etc/rcX.d. To start it running type: [/font]```
sudo /etc/init.d/ssh start
``` [font=Courier New]But before you do that you may want to make some changes to it's configuration file: [/font]```
sudo vi /etc/ssh/sshd_config
```
 > Also, how do I make the PC boot into console mode automatically? Loading up a GUI is no use for me.Remove 'gdm' from /etc/rc2.d.
     
 But like the poster above said, you shouldn't even have X installed on a true server. Enter 'custom' at the boot prompt for the install CD.

---

### Post by TekZonz on 2005-02-17
Thank you for your great answers.

I will try to not install X in the first place and get back to you as soon as it gets done.

---

