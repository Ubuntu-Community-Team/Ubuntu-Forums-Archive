---
title: "newb questions strikes again re: webmin"
date: 2008-06-25
forum: Server Platforms
---

### Post by chuck jessup on 2008-06-25
Ok, I have decided to go with peoples advice about useing a webbased webadmin program instead of a GUI, I chose Webmin, the one that recieved rave reviews... Man I must be stupid or somthing, I found a guide on how to install webmin 1.420.. I installed the lib files needed, and then when I went to dl the package I typed in what it told me...

wget [http://prdownloads.sourceforge.net/webadmin/webmin_1.420_all.deb](http://prdownloads.sourceforge.net/webadmin/webmin_1.420_all.deb) 

after strikeing the enter key, the screen fills up with failed attempts to download the .deb package. 
On my XP system I typed in the address, and it returned that it couldnt display the page... on the server I tried again and it did the same thing with one change, it was wanting some further action... my attempts have failed, and would really like to have this software installed so that I can give it a shot... 

so my question is two fold. 
1. is there a better way to download the latest webmin software? possibly by use of a cd?
2. How would i go about installing it? The guide had a code to install(#sudo dpkg -i webmin_1.420_all.deb)... but is there another way?

any advice would greatly welcomed :)

---

### Post by littlegreiger on 2008-06-25
That command should work, when I open the link you posted with Firefox on Vista I get the download prompt and it allows me to download it. Make sure you issue the full url, not the one that shows up in your post with the .... in the middle of it. 

Also the command that the guide gave you is the best way to install the package.

---

### Post by cariboo on 2008-06-25
Install links it is a text based web browser and see if you can connect that way. links is in the repository. You can install it from a command line by typing:

```
sudo apt-get install links
```

Jim

---

### Post by lodp on 2008-06-25
That wget command works fine for me also.

But if wget is acting up for you, you might want to try the direct download link on that page. Just hit the following:

> wget [http://surfnet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.420_all.deb](http://surfnet.dl.sourceforge.net/sourceforge/webadmin/webmin_1.420_all.deb) (you can't mark/copy/paste this URL directly because the forum software cuts it short. Right-click the above url and select "copy link location", then paste it into the command prompt after the wget command).

---

### Post by chuck jessup on 2008-06-25
i did the forum post added the '...' i  dont have ANY GUI installed, and should i have a web browser installed like firefox or the one sugested by Caraboo907? im at work for now but will try it when i get home... also google search gave me a million different posts about setting up and installing webmin on my server box. but they all were like the same, i will have to play with it when i get home. Thanks Guys!

---

### Post by lodp on 2008-06-25
the wget command should be able to fetch the file for you. you just have to get the URI straight, mind you it's got to be the one pointing to the actual .deb file, not some download page.

i don't see any need for installing a browser.

if you stick to the official webmin instructions, you shouldn't have too many problems installing it. it's really quite straightforward.

---

### Post by chuck jessup on 2008-06-25
see thats the thing it acted like it was going to do the download, then gave me an error "awaiting further action"... any attempts to install useing the code in my original post said that the package was not found. i got fed up and went to bed... i will try the second dl link this evening when i get home.

---

### Post by lodp on 2008-06-25
as a rule, when using wget to download stuff without a GUI, you have to use the "direct download link" that you're offered on sourceforge:

> Your download should begin shortly. If you are experiencing problems with the download please use **this direct link**. 

---

### Post by chuck jessup on 2008-06-25
this is the direct link for the download from sourceforge... [http://internap.dl.sourceforge.net/sourceforge/webadmin/webmin_1.420_all.deb](http://internap.dl.sourceforge.net/sourceforge/webadmin/webmin_1.420_all.deb) so i use this in place of the [http://prdownload.sourceforge.net/webadmin/webmin_1.420_all.deb](http://prdownload.sourceforge.net/webadmin/webmin_1.420_all.deb) ?
(mostly a redundant question... so taht i will have the link...:P

---

### Post by lodp on 2008-06-25
yes, that way it should work with wget..

---

### Post by chuck jessup on 2008-06-26
Ok i got it! Thanks a bunch Guys! im gonan have fun...

---

