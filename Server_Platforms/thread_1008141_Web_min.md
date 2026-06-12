---
title: "Web min"
date: 2008-12-11
forum: Server Platforms
---

### Post by ttallos on 2008-12-11
I have several web sites to add in webmin each site is in its own directory how do I link all the sites so they work on my new apache server using webmin?

---

### Post by volkswagner on 2008-12-11
You will want to read up on virtual hosts.

Creating virtual hosts inside Webmin is very easy.

To get you started from within Webmin...The following works for me you may need to alter things like port number, ip address, etc. :
[LIST=1]
[*]Open Apache servers tab
[*]Select create new virtual host
[*]I use the "any address" for all virtual hosts-Connections Address.  Important thing here, is use the same format for all hosts.  You cant mix choices here.  Check boxes for "Add name virtual server address" & "Listen on address".  I select the "default port" where Apache is listening.
[*]Document Root-here you enter the root folder where site is stored.  Box is checked by default to allow access to this folder, I am not sure of the security risk nor functionality here.
[*]Server Name-I use my own names here.  I always name the virtual host the actual domain, such as sub.mydomain.com
[*]Add virtual server to file-Here you have some choices.  You can copy directive from the default.  I think it is best to create a new file. 
[/LIST]

This should give you a working virtual host.

You should go back into the newly created virtual host, then select edit directives.  Here you can verify all paths are correct.  You must also make sure any referred path here actually exists.  Depending on how you want you logs setup, verify the path is correct.

Good Luck

---

### Post by ttallos on 2008-12-11
Thank you for that I have alot of work ahead apache is real picky about cabs or lower case where windows is not so picky. I do like apache. This is a small problem to fix.

---

