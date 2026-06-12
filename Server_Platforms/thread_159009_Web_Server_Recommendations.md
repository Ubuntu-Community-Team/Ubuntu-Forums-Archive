---
title: "Web Server Recommendations"
date: 2006-04-12
forum: Server Platforms
---

### Post by peterscj on 2006-04-12
I would like to learn to host my own website.  I have looked up information on setting up a webserver but I was wondering what type of computing power is needed to run a personal website.  I have a few extra computers that I could use.  I would like to use my 600MHz with 256MB of RAM, but I also have a 1.2GHz with 512MB of RAM that I could use.  The site I am planning on using would work as a personal site with an ftp section and a section for my resume along with a few programming examples.  I should probably note that I am about to graduate so the programs I would host would not be anything super "extraordinary"

I have found different ideas on how to set a computer up as a server but what I really don't understand is exactly what kind of computing power I would need.  Any help would be appreciated.

---

### Post by horace on 2006-04-12
If it is just for learning and unlikely to get extensive traffic, then my experience is that you can run a web server on a box with 128Mb without any problem. I am using an old and slow machine with this as my personal web server and any speed issues would be a result of the ADSL upload slowness rather than the fault of the machine.
Best plan is just to try it and see!

---

### Post by echo $USER on 2006-04-12
I run a lamp server on a Athlon 850mhz w/ 256mb RAM.  It doesn't get more than fifty hits a day, and I have never had any problems with it.  Well, with the exception of people running Perl scripts against it trying to change permissions on my .php pages.

---

### Post by heislord5 on 2006-04-12
I recommend using vhcs.  Someone has written a script that installs it completely.  It installs a complete virtual hosting software system for you.  Database, webhost, ftpserver, mailserver, smtpserver, webmail....everything.  It allows you to even create resellers under you and customers under them with domains/aliases under the customers!

I am so impressed, this is the best software I've been able to use on linux PERIOD (Except maybe GNOME itself).  So easy to install.  yes it's overkill for what you want, but it's soooo easy!  It will probably take you significantly longer to set up a very simple/limited solution by installing the servers on your own, individually.  So spend more time to get less, or just get the whole enchilada up in one night?

I don't remember where it was, but it was a color coded script for breezy.  All you do is keep hitting enter and put in a few values, when you're done, go to your home page and view!

Use the 1.2GHZ with 512MB IMO.  so so easy.  It was easier to set this up than it was to get my wireless network card to work.  Ran into two problems:

had to use some sysadminsomething password to reset root password/permissions in mysql
had to changes lines 153-155 in some "inc" file for the webmail to get it to work.

both solutions found on the forums here or at vhcs website.  One other thing not caused by the software...I had to figure out how to setup MX and A records on zoneedit.com to get my email to work.

---

### Post by grizz_granlien on 2006-05-08
vhcs is it free and does it have forums and can people upload files to your server with their web browser. also does it have a chat area to chat to others online and also can you view you E-Mails onlien as well as play games and hide areas that they don't have access to them and can you put people in groups and also set up forums /file areas with group or individual who can access them or not.

Also can you set up your E-Mail with your owne domain. eg: my domain is [www.grizzsden.ca](www.grizzsden.ca) and I would like to have my E-Mail [email]grizz@grizzsden.ca[/email] also I have a BBS and would like to have my E-Mails done the same way...

I think Ubuntu should when you install it ask if you want all these futures as well as mount other hard drives automaticaly wih a util to do so and it stays mounted and gives all access to the drive so it is like another Hard drive... DVD playback would be nice automaticaly set up as well as being able to play all video formats such as AVI and MPG and etc, as well as all music formats and CD's then maybe it would kick MS Windows but off the face of the earth... also have it play games from any OS on the market one OS called Ubuntu that can run every thing...

main question sorry is about the web server I had mine set up in Windows with Easy File Shareing and it was easy to setup and use but limmited... I wanted more...

So I am trying Ubuntu Linux it is supost to be good so far I like it but for a web server it is hard to setup to get forums etc...

I am New to Ubuntu Linux and I tried Linux years ago and it has come a long way but still needs to be more user friendly they should test there products with 10 year old kids if they can setup server as well as run games and install programs easy without asking a lot of questions it means you got a good product...

I hope Ubuntu does good....

---

### Post by az on 2006-05-08
[QUOTE=peterscj]
I have found different ideas on how to set a computer up as a server but what I really don't understand is exactly what kind of computing power I would need.  Any help would be appreciated.[/QUOTE]

Running a dynamic site with the database server and the web server running on the same machine, you could probably install LAMP on a pentium 1 (one-hundred megahertz) and would not notice a big slowdown until about ten people were visiting your site at the same time.

For what you are describing, you really don't need all that powerful a machine.

---

