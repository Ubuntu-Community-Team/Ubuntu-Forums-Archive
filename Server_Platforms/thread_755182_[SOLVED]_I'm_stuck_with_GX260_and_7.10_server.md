---
title: "[SOLVED] I'm stuck with GX260 and 7.10 server"
date: 2008-04-14
forum: Server Platforms
---

### Post by cleanfacets on 2008-04-14
Ok, here goes.

1) I downloaded 7.10, verified via MD5, and created boot CD
2) I installed 7.10, chose LAMP, Mail Server, and OpenSSL
3) Went through install ok, and rebooted

During the boot process, there are several startups and all verify with [OK]on the far right side of the screen, such as MySQL [OK], Apache2 [OK], etc.
Everything is fine till it gets to 'running local boot scripts' and it just hangs!
Actually, it is more than likely just after that because there's a [OK] on the right side of the screen on the same line, and the cursor is one line below also on the right side of the screen.
If I hit the Enter key, I just get a command prompt.

Searching other forum entries, here's what I have tried:
1) Set the BIOS video memory to 8Mb
2) run the command 'sudo dpkg-reconfigure xserver-xorg'  When I type in this command, it asks for a password, then I receive the following error:
Package 'xserver-xorg is not installed and no info is available

Please let me know if there's anything else I can try.  The Dell GX260 is all I have to work with for the web server right now and will not be able to change hardware at this point.

Thanks in advance.

---

### Post by cheeseboy2010 on 2008-04-14
I'm not sure if I understand your problem, but the server distro comes with now x-server. It's just command line. If you wanted one you would have to apt-get it. (I don't know the exact package, but you should be able to find it)

---

### Post by cleanfacets on 2008-04-14
Thanks for the reply.

During boot, everything is fine till it gets to 'running local boot scripts' and it just hangs.  No prompt, nothing, it just hangs.

If I press the Enter key, the cursor moves to the left side of the screen and I get a command prompt.  It acts just like I aborted the script and returns control to the command processor.

Does the server version have a GUI interface?  Or, is it just a command line?


cleanfacets

Oh, by the way, this is really a GX280 (tower version of the Dell) with a BIOS version of A03.

---

### Post by adamos on 2008-04-17
just press enter...
then login

if you dont feel comfortable with cli do **sudo apt-get install xserver-xorg xfonts* gnome**


go to documentation in ubuntu.com and read about 7.1 servers


good luck

---

### Post by cleanfacets on 2008-04-17
Thanks for the reply.

I guess, when the startup script (or whatever) runs, 'it' should end at a command prompt letting the user know everything worked ok and I'm ready for commands.  (The documentation needs to specifically state "The server version does not come with a graphical user interface, you have to install that separately"  It should also state "When the startup script ends, you need to press the Enter key to get a prompt"  But, the way it stops, there's no way to tell if it really finished completely or not")

After two days of reading posts, I fould one little sentence.
"If you installed the server version, it does not come with a gui."
So then, I used apt-get and installed GNOME and everything was ok after that.

I installed the LAMP option and have verified Apache and PHP work by setting up a little web page and displaying it in FireFox.

Now, I'm just trying to get past all the errors with MySQL.  This is not very intuitive.  Depending which directory I'm in, I receive varrious errors.  I can start a window with Accessories | Terminal and type:
sudo mysqld --help
and get a help screen, but I can not get a mysql prompt anywhere, anyhow.

I think MySQL is installed ok, but I will more than likely need to change the root password and none, I mean none of the posts have helped.  I have tried typing in all of the commands and each one has an error associated with it.  I have yet to be able to get a MySQL prompt anywhere.

:confused:

---

### Post by adamos on 2008-04-17
do a sudo dpkg-reconfigure for mysql and when you want to login do a mysql -u root -p whatever you enter in the conf as a passwd

install phpmyadmin to manage your sql better

pick the book from Apress, beginning ubuntu server from begining to professional. Its short and a very good start to deploy your server but dont expect production servers development. 

gui server is a no go imo. pick another old computer and install ubuntu server and leave it headless to control it remotely to get a sense of what is a server.

---

### Post by cleanfacets on 2008-04-18
Thanks adamos,
I'll pick up the book and see how things proceed.  This server is for an inhouse web server which will be used to support our sustainability group and end up running FreeEMF, Free Energy Management Framework.
If anyone is up for helping, it's:

[http://www.freeemf.org]("http://www.freeemf.org")

I did start another thread called MySQL or MySQLD.  For this thread, I think it's closed.

cleanfacets

---

