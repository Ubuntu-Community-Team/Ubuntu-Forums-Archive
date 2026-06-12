---
title: "GUIs for Server Apps"
date: 2008-07-07
forum: Server Platforms
---

### Post by sjrlaw on 2008-07-07
I have installed the server version of Hardy Heron, and naturally was left without a GUI.  I am told that although I could install one, it presents some security issues.  The question I have is, if I download and install GNOME, KDE, or some of the server admin GUIs I am hearing about, are there GUIs for the individual server apps for configuration, etc., that could take advantage of the system GUI, or would I just end up in the shell anyway?

---

### Post by adam_kimber on 2008-07-07
For a server most things can be done remotely by logging in securely through a shell or by using something web based like PHPMyAdmin. There are quite a few web based utitities around these days.

---

### Post by sjrlaw on 2008-07-07
Thanks, Adam.  However, I am quite the Linux newbie, and although logging in remotely through a secure shell is something I understand generally, in theory, it just adds an additional layer of knowledge (knowing how to log in remotely to the server through a secure shell) that I do not have in order to solve my problem.  I am already having trouble  just logging onto the server to begin with through Connect to Server on the Ubuntu GNOME Places Menu.  Is there a way that I can do it on some sort of GUI console directly on the server without having to go thru the network?

---

### Post by sp00ki on 2008-07-07
correct me if i'm wrong, but it sounds like what you need is to install a desktop manager after all.  since you're running a server and will most likely have very little need for things like 3d effects, et al, i'd recommend xfce.
i'd also look into using ssh with X redirection.  what this does is allows you to launch gui based apps remotely without having to start the desktop on the server (this will be native if administering from a linux or os x system, but if you're running windows you'll need to look into something like xming; there are others which escape my memory at the moment, but you should be able to find a few that work for  you).
what is it you're planning to configure @ the server?  like adam_kimber mentioned, there are tons of gui utilities for configuring pretty much all the major services.  being specific might help get recommendations from those who've used them (though configuring via the shell is what most tutorials will cover and what most admins have experience with; starting off this way is most likely your best bet as you'll need to turn to someone for help more than just once or twice as you familiarize yourself with the OS!).

---

### Post by windependence on 2008-07-07
> **sjrlaw said:**
> Thanks, Adam.  However, I am quite the Linux newbie, and although logging in remotely through a secure shell is something I understand generally, in theory, it just adds an additional layer of knowledge (knowing how to log in remotely to the server through a secure shell) that I do not have in order to solve my problem.  I am already having trouble  just logging onto the server to begin with through Connect to Server on the Ubuntu GNOME Places Menu.  Is there a way that I can do it on some sort of GUI console directly on the server without having to go thru the network?

Actually, rather than adding a "layer of knowledge" as you say, you would be adding a crutch that will prevent you from really learning what you need to know to become a good admin and use the true power of the OS. Please don't take this the wrong way. I was where you are several years ago and I know it seems daunting. Trust me, if you avoid using a GUI, you will be light years ahead of where you would have been otherwise, and if you have a major failure, you will be able to recover with ease. What happens if your GUI goes south? What if you can't log in to your box or if you are not at your terminal when something goes wrong? Almost all of these problems have to be fixed from the command line. This is something to think about.

-Tim

---

### Post by forger on 2008-07-07
As said above, that layer of knowledge will prove a worthy investment which will help you manipulate and make the most out of your server, not to mention security issues. :) 
Security issues aren't a big problem if you update frequently. But security is a risk, a risk that is analogous to the number of applications you have running - the less programs you have and the more specific is the server you use for one application (e.g. a web server with only apache/php, a server for mysql database, etc.), the less security issues will you have to worry about and this way your servers will be more efficient for your work.

After all, if you want a good stable server, you need to use as less resources as possible, to provide more for your users/clients.

---

### Post by wilbbe01 on 2008-07-07
I too feel avoiding GUIs as much as possible is a good thing.  When you are trying to configure services it is often really easy to search google or the projects website for other people who have tried to configure something in a similar way.  If you don't have access to a terminal on the server then you probably have a big problem, no access to GUI = try the terminal.  The terminal is always there to use, so why not learn how to use it if there is the possibility of having to learn to use it when your gui fails you anyway.

I agree with the web configuration post as well.  A few days back I was getting really annoyed with my samba configuration file on my server.  To fix the issue I wanted a gui, as I knew it was something minor I was missing the gui could do for me very easily.  However, I did use the terminal to install the web configuration utility.

Basically what I'm trying to say is to use the terminal, ask questions, learn, and when you feel comfortable at the terminal maybe throwing in a gui to do something would be fine.  Understanding the underlying structure of things goes a long way even when GUIs don't necessarily show the underlying things to you.  What are you trying to configure?

---

### Post by ixus_123 on 2008-07-07
don't be afraid of the command line - there really isn't that much to learn to get by.

You'll need to know

man [command] - brings up the manual page for the command

apt-get install [package-name]

nano - a friendly text editor (easier than vim) to edit config files

cp  - to copy files

mv  - to move files

-r or -R  - add to the above to do recursively (folders & subfolders)

and that's about it.

If I were you, I'd follow a few guides to set up a server of some sort - it doesn't matter what - just do it for the practice and you'll be flying along on the command line in no time.  The only way to learn is by doing :)

---

### Post by ixus_123 on 2008-07-07
actually, slackware has a pretty good book that can walk you through the basics.

I've only skimmed it, but it seems well laid out, and an easy read.

[http://www.slackbook.org/]("http://www.slackbook.org/")

You can apply the vast majority of the book to Ubuntu or any linux distro

---

### Post by windependence on 2008-07-07
As ixus_123 has mentioned, plenty of help here if you need it. One of us is almost always logged on here.

-Tim

---

### Post by sjrlaw on 2008-07-07
Wow!  Thanks, guys!  As a little more information, I am a solo attorney and computer geek in a prior life.  A lot of what you describe doing is stuff I loved to do: lifting the hood and tinkering.  Linux came along after I had gotten away from that, and I saw it as a way of getting back in touch with that part of my life ([www.knightblogger.com/2007/06/21/ubuntu-linux/](www.knightblogger.com/2007/06/21/ubuntu-linux/)).

I have fun with that at home, but in the office, the computer is a tool that I need to just work.  I don't have the time to lift the hood.  I also blog on legal technology for the small firm ([www.lawtech.wordpress.com](www.lawtech.wordpress.com)) and have been pushing the Linux server as a way of having an inexpensive, stable server in a small firm.  I decided to set up a test Linux server in my basement computer lab to see whether this was something the average attorney could do or whether a good consultant is needed.  I did that in hopes of convincing attorneys to try it.  I wrote a post on installing the software:

[www.lawtech.wordpress.com/2008/06/05/can-average-lawyer-install-linux-server/](www.lawtech.wordpress.com/2008/06/05/can-average-lawyer-install-linux-server/)

Now that I have the server software installed, I am trying to get it to work.  For some reason, I can't even log onto it, let alone configure and set up the apps. Maybe I do need that extra "knowledge layer" of figuring out how to connect to the server first, and then learning how to configure it remotely, as that is the most logical way to maintain one.  Any guides on connecting to a Linux server from a Linux workstation on a closed intranet?  It looks like I need to take this one step at a time.  Thanks!

---

### Post by ixus_123 on 2008-07-11
well, if you can get a keyboard and screen up on the server you built, log in and run 

```
ifconfig
```

(you might have to sudo to run this command - I can't remember of it's redhat or ubuntu that needs admin rights)

that command will give you your machines IP, once you have that, you should be able to remotely access it from a local machine on your network provided you have SSH installed.

To check if SSH is installed and working

```
ssh 0
```

If it spits out some text asking for a yes/no then ssh is installed and running. you can type CTRL + C to clear this.

If SSH is not installed then

```
sudo apt-get install openssh-server openssh-client
```

Then, from a local linux machine, you should be able to remote in to the LAN IP which will probably be in the 192.168.x.x or 10.2.x.x
format.

```
ssh username@192.168.1.5
```

where username is the name of the box you want to access with it's IP.  If you want to access from Windows, then Putty is a good client [http://www.chiark.greenend.org.uk/~sgtatham/putty/]("http://www.chiark.greenend.org.uk/~sgtatham/putty/")

You probably wont be able to access the linux server from outside as I suspect your work will be firewalled and blocking port 22 needed for SSH.

After that is up and working, then next thing to look to do would be to set a static IP to the server if it doesn't have one already.

I think the best way to get to grips with it is to perhaps follow a tutorial while you have the box in a test environment.  There are a few here and also over at howtoforge.com.

Since you already use Wordpress (I do too), you should perhaps try installing that. You'll need to install a LAMP server first, and then Wordpress of which there is great documentin floating about :)

---

