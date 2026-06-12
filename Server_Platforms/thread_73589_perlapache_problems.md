---
title: "perl/apache problems"
date: 2005-10-09
forum: Server Platforms
---

### Post by herrpoon on 2005-10-09
Hi, I installed the mod libapache2-mod-perl2 so I could execute a few cgi scripts  on my webserver.

The problem I'm having is that I'm getting an internal error 500 whenever I try and access them in a web browser.  I checked my apache logs and found that when executing them I had the following error:

"premature end of script headers: trial.cgi"

Having googled this it turns out it could be a number of things:

> 
(1) The script file was created by a Windows program like Notepad and didn't get uploaded in Unix/ASCII format. Some FTP programs will translate Windows/DOS text files into Unix/ASCII on the fly with a proper setting. Otherwise you'll need a text editor that can save the files in the proper format on your computer.

(2) The script file's permissions were set improperly. Use the CHGMOD command in your FTP program to set the permissions on the script file to 755, or set it to allow Owner RWX permissions, Group RX permissions, and Other RX permission (where R = Read, W = Write, and X = Execute).

(3) There is a syntax error in the script. often caused when a user customizes a public script for his site. All it takes is a stray keystroke, or an unescaped "@" to stop execution before it starts. 

I'm pretty sure it can't be the top two problems as although I did orignally upload the script from my windows box to the cgi-bin directory, since then I created the file in ubuntu and copied it over.  Likewise it can't be the permissions as I've checked these over and over again!  Also it can't be the third option as when I try and execute the script in console it's fine but on any web browser it doesn't work, any help would be much appreciated!

---

### Post by herrpoon on 2005-10-09
Fixed!  It was a problem with the script I was using after all :rolleyes: 

Sorry about that, should have fiddled with it more before posting :???:

---

