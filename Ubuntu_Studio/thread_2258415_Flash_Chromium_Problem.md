---
title: "Flash Chromium Problem"
date: 2014-12-27
forum: Ubuntu Studio
---

### Post by simon d w on 2014-12-27
Ok I use Firefox and it never plays me up works fine always, but I use Chromium for something else, flash does not work. You tube crashes and everyting else wont work Channel 4OD jjust says install flash, gives me a ,ist of options, I am a bit of a newbie [IMG]http://i40.photobucket.com/albums/e234/simon9148966/Selection_010_zps1ac196e6.png[/IMG]  I have downloaded the YUM tar.gz .rpm and don't know what to do after. Sometimes they automatically open in the download center. Not sure why thats not the case with these files..

I've tried everything else. I know they have discontinued support, i've tried pepperflash,,wont work.  Can somebody give me a magic line of code to type in to the terminal, that is what I really want. Thanks!

---

### Post by kc1di on 2014-12-27
First off the yum file won't work in Ubuntu , you need to down load the .deb file then it would open in Software center.

But no need to do that either.  you can load flash in a terminal type the following commands to install it. along with other needed codec.

```
sudo apt-get updated
sudo apt-get install ubuntu-restricted-extras ubuntu-restricted-addons
```

That should do it. 

you could also install google's pepper flash in chromium and get a new version of flash 
follow the instruction on this[ page.]("http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04")

---

### Post by ajgreeny on 2014-12-28
That flash version from adobe will never work in chromium, only in firefox.
You must use pepperflash for chromium as naapi plugins are now not supported by chromium or chrome.

---

### Post by Bucky Ball on 2014-12-28
Yes. Software Centre and pepperflashplugin-nonfree. Or, open a terminal and:

```
sudo apt-get install pepperflashplugin-nonfree
```

---

### Post by simon d w on 2014-12-28
Ok il give it a try. Thanks

---

### Post by simon d w on 2014-12-29
No, I mean flash works in you tube but crashes and wont work on more complex players like one with adverts or the chromium APPs page wont work at all 404 error

---

### Post by mikeh789 on 2014-12-29
adobe is responsible for creating and maintaining and updating and supporting flash. its not open and cant be "Fixed" by any ubuntu team. [http://www.adobe.com/software/flash/about/](http://www.adobe.com/software/flash/about/) is where i visit to see, factually, what adobe supports, and what version i need. you'll note that, if you want the most recent version of flash, you'll want to use the version of flash created for the chrome browser. right now, that is version 16.0.0.235 vs the 11.2.202.425 version that is provided by adobe to linux operating systems. there are ways to run the chrome "pepper flash" version in chromium, and also in firefox. personally, i say, just use chrome, and see if that addresses all the issues with all the sites you are having issues with. visit the "about flash" site first, and make sure you have the latest version, and see that you are able to use the sites you want to use. if not, let the creators and maintainers of the sites you are having issues with know that you are having issues, and let them know what operating system you would like to access their sites and products from, and ask that they support that operating system. but, if you find that, like me, when using the "pepper flash" version, all content works as expected, then, you can use pepper flash in either chrome, or whatever other web browser you choose to hack it into.. cheers and good luck!

---

