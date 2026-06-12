---
title: "HOWTO: Griffith 0.13  with bar code scanning / Ubuntu 12.04.3 LTS 64bit"
date: 2013-09-18
forum: Tutorials
---

### Post by FlyingMG on 2013-09-18
I have been looking for a solution to manage my DVD collection and after some dicsussion with friends and some search in forums and google, I decided to use Griffiths. What I wanted to do was to build a solution that allows me to scan the bar code of the DVD, get the DVD infos from the web so that I could quickly populate my database with my 250+ DVDs...
My Griffith installation is connected to a MySQL database on my NAS and gets its information from the Amazon product advertising database.
I want now to share my experience and the way I did that, as I saw on some forums, that I was not the only one who looked at such a solution.
I will present the scripts and tools I used. I didn't create anything, but only put some founds together to get it done. I will reference all sites I have gathered information from.
I did the installation on ubuntu 12.04.3 LTS 64bit and use a MySQL as a repository database for Griffith (v 0.13). The installation works also on ubuntu 13.04 64bit.


_Overview Movie Collection Managers:_
First, if you want to have an overview of some tools like Griffth, then this site is where you should look at first: [http://www.junauza.com/2013/01/best-movie-collection-managers-for-linux.html](http://www.junauza.com/2013/01/best-movie-collection-managers-for-linux.html) - Thanks to the author.


_Griffith:_
Install Griffith - It is in the repository. Use synaptic or ```
sudo apt-get install griffith
```.
If you want to connect Griffith to MySQL as I did, then first create the user "griffith" first and then let Griffith do the rest (create database, etc...) or let griffith work with its local database. This is not really the challenge here.


_Movie Information from the Web_
Now you'll have to setup Griffith to get information from the web for the DVD. I use the Amazon Product Advertising API ([https://affiliate-program.amazon.com/gp/advertising/api/detail/main.html](https://affiliate-program.amazon.com/gp/advertising/api/detail/main.html)) for which you have to register and get the key pair you then enter in Griffith in *Tools/Preferences/Extensions/Amazon v1*. Using Amazon as the Web Servive provider allows to not only search for DVD titles but also using the code bar (in the title field as well).


_Bar Code reader:_
I was already looking for a special bar code reader device, as I found a forum post describing how a web cam can be used to achieve that. I wanted to give it a try. My SmartPhone is able to do that, so why shouldn't it be possible with my web cam... If you search google you will find several description, the one I took and that worked immediately for me is this one: [http://askubuntu.com/questions/195191/could-i-use-my-webcam-as-a-barcode-reader](http://askubuntu.com/questions/195191/could-i-use-my-webcam-as-a-barcode-reader) (third post).

    Install crikey:
```

wget biblio.comxa.com/ztools.sh
chmod +x ztools.sh
./ztools.sh 

```

This will get the tools and lib and install them for you (see link for more details)


    Is your USB webcam supported by V4L1 (Video4Linux1)? Then, open again a terminal and type in:
```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so zbarcam --raw --prescale=320x240 /dev/video1 | crikey -i
```

    Is your USB webcam suported by V4L2 (Video4Linux2)? Then, open a terminal and type in:
```
zbarcam --raw --prescale=320x240 /dev/video0 | crikey -i
```

In my case I use the second call, as my webcam supported by V4L2.


My internal WebCam is on video0 (you can check it with ll /dev/video*). But at it does not allow to focus and some bar code couldn't be recognized very well. So I used a small external one and the result was really good! I just changed video0 to video1 in the command above.


To use it in Griffith, click on "Add a new Film" (the big + in the icon bar), make sure the search provider is set to Amazon, then put the cursor in the title field and scan a bar code. You do not have to do anything Griffith will start looking at the DVD in the Amazon database.


I have several french and german movies I had to scan. I had to switch between Amazon.de and Amazon.fr in the Griffith setting and could not found where I could do it in a more convenient way... Another point is the way I start zbarcam. Starting it in a Terminal window works very good, I wanted to start it using a launcher, but this still does not work...

---

