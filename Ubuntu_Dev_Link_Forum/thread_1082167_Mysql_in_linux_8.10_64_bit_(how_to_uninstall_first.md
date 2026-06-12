---
title: "Mysql in linux 8.10 64 bit (how to uninstall first)"
date: 2009-02-27
forum: Ubuntu Dev Link Forum
---

### Post by BramWillemsen on 2009-02-27
Hello everybody,

Yesterday i finally recieved my laptop that i intend to use for programming. I installed Ubuntu, but I'm not good at it yet. I use guides for every step that i make in the terminal. In the end i do manage to get most things working, but mysql is an exception.

The mysql book that I'm using suggested me to download the most recent server and client rpm files. when i did this i found out that ubuntu cannot treat these. A website suggested to convert them into .deb using alien. Afterwards sudo could be used to install them. Well i did this, and i try to log in into mysql but i get some strange error concerning files. 

I suddenly found out that ubuntu already had (parts ?) of mysql installed. maybe the installation that i did messed this up ? So now i'm trying to find a way to get rid of all the mysql stuff to do a clean install after (maybe use a tar file instead so i dont have to use alien). The synaptic package manager does show anything mysql related though (when i type mysql nothing appears). 

Does anyone know how i can get rid of all the mysql remnants on the system? I guess that's the only way to do a clean install again. I don't know where to look and which tools to use in Linux yet. I'm sorry if it is a dumb question.

Thanks for the help and kind regards :)

Bram

---

### Post by rharriso on 2009-03-02
I assume you want to try to set up php and Apache as well.

[Lamp Server Setup]("https://help.ubuntu.com/community/ApacheMySQLPHP")

This is the walkthrough I used to set up my companies dev server.

---

### Post by theDaveTheRave on 2009-03-25
Hi.

you may find that you need to use synaptic to get the current version of MySQL.

then if you want to remove it after, you would just select the appropriate options for "complete removal".

If however you are planing to install from source (which is in fact remarkably easy) I would recomend following the instructions on the MySQL site (these are in fact the same as can be found in the book from O'Reily).

this is the link to the [authors personal pages]("http://russell.dyerhouse.com/cgi-bin/index.cgi"), in case you are interested. But he has recently "spun off" various bits of his site and the MySQl stuff now resides [here]("http://mysqlresources.com/cgi-bin/index.cgi").

I tried remember instaling MySQL from source and it was amazingly easy! in fact it encouraged me to do so for more stuff I've installed recently!

hope this info is helpfull.

David

---

