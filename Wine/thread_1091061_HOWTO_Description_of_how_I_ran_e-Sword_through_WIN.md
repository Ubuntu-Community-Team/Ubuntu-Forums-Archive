---
title: "HOWTO: Description of how I ran e-Sword through WINE"
date: 2009-03-09
forum: Wine
---

### Post by amylase on 2009-03-09
The following is a description of how I set up e-Sword on Ubuntu 8.10 through WINE. The process is quite straightforward with just one or two small twists but nothing lethal. The intended audience is absolute n000bies to Ubuntu and WINE like myself. A bit of background: e-Sword is a free (free of charge) software that allows you to access a dozen different versions of the bible and another dozen different commentaries on your computer. Commercially there is another package called "PC Study Bible" with friendlier user interface and similar content at $100-700 depending on how many bibles/commentaries you get. Needless to say how happy I was to find e-Sword for free. Here is how to get it running on Ubuntu.

1) System -> Administration -> Synaptic Package Manager -> Search -> Wine -> Select wine, wine-dev, wine-gecko -> Apply.
This should install WINE for you. Maybe you don't need all three packages but I wasn't sure so I just clicked all of them.

2) Download e-Sword application installation from [http://www.e-sword.net/downloads.html](http://www.e-sword.net/downloads.html)
This is the reader. At the time of writing, the version is 8.0.6 and is this file [http://www.e-sword.net/files/setup806.exe](http://www.e-sword.net/files/setup806.exe)
Save it somewhere you can find eg. desktop.

3) Right click on it to "Open with 'Wine Windows Program Loader'". Follow the prompts and click as many "ok" or "next" as necessary. This should install the reader under this directory:
home/<user>/.wine/drive_c/Program Files/e-sword

where <user> is user name.
e-sword is the directory I specified during installation. 
You should now have the reader installed and it contains King James version of the bible with no commentaries. You can run it the way it is by going to home/<user>/.wine/drive_c/Program Files/e-sword and right click on e-Sword.exe to "Open with 'Wine Windows Program Loader'".

Note 1: If you have trouble seeing the .wine folder, just go to Edit -> Preference -> tick "Show hidden and backup files". 
Note 2: If you don't know where your home folder is, just click on Places -> Home folder. That's your home.

4) So far everything has been straightforward. Next I tried to install other bible versions on top of the existing King James. This is where things started to not work. To do it in native Windows one would simply download whatever additional bible version he/she likes from [http://www.e-sword.net/bibles.html](http://www.e-sword.net/bibles.html) and double click on them to self-install. Turns out when I tried that, WINE wasn't prepared to automatically combine everything and just run things as desired. So what I did was I installed the reader onto a normal Windows XP computer first. Downloaded additional bibles (in my case I like contemporary English version so I downloaded this file [http://www.e-sword.net/files/bibles/cev.exe](http://www.e-sword.net/files/bibles/cev.exe)) and double clicked for it to self-install on the Windows XP computer. Next I grabbed all free commentaries from [http://www.e-sword.net/commentaries.html](http://www.e-sword.net/commentaries.html)
There are a total of about 16 free commentaries and half a dozen non-free ones. I just downloaded all free ones, saved onto desktop and clicked on each one of them one by one to install again on the Windows XP computer. So basically I installed the reader, add-on bible and commentaries on a native Windows computer per usual.

5) Next I tried a bit of transplantation. I copied the folder C:\Program Files\e-Sword onto an USB key. Took it to my Ubuntu machine and copied the content into <user>/.wine/drive_c/Program Files/e-sword

6) Once again I tried to load up the reader by right clicking on e-Sword.exe to "Open with 'Wine Windows Program Loader'". I was happy to see it up and running with add-on bible and commentaries all in place. But something wasn't quite right. As I clicked on the tabs for different bibles and commentaries, the software decided to screw up displaying all sorts of malbehaviour. Before the program died it actually told me something important and that was it could not find "msls31.dll". I don't know what that file does but was able to find it on my Windows XP computer under C:\WINDOWS\system32
So I copied it over and placed under <user>/.wine/drive_c/windows/system32
This time I tried again right clicking on e-Sword.exe to "Open with 'Wine Windows Program Loader'" and everything worked like a charm.

There's probably a quicker way to do things. I'd be interested to learn. But anyway this approach above will get your e-sword up and running on Ubuntu. Hope you like it.

---

