---
title: "How to: Creat a list of softwares of ubuntu repositories for downloading"
date: 2011-09-16
forum: Tutorials
---

### Post by SidebySide on 2011-09-16
Requirement: accessibility to a high speed internet (several Mb/s)
- - -
If you don't have a fast internet connection at home, but in your office/university/...: Yes, this way will be useful for you! visit [here]("http://ubuntuforums.org/showthread.php?t=352460"), too. It's a related topic.
- - -
1. Go to: [http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/) (Main Server)
You can also use the other mirrors:
```
http://**[COLOR=Red]xy[/COLOR]**.archive.ubuntu.com/ubuntu/dists
```Replace [COLOR=Red]xy[/COLOR] with the [abbreviation of the country]("http://www.greenbuilder.com/general/countries.html").
Ex:
[http://fr.archive.ubuntu.com/ubuntu/dists/](http://fr.archive.ubuntu.com/ubuntu/dists/)
[http://it.archive.ubuntu.com/ubuntu/dists/](http://it.archive.ubuntu.com/ubuntu/dists/)
[http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/)
[http://uk.archive.ubuntu.com/ubuntu/dists/](http://uk.archive.ubuntu.com/ubuntu/dists/)
[http://es.archive.ubuntu.com/ubuntu/dists/](http://es.archive.ubuntu.com/ubuntu/dists/)
...

2. Choose the correct version of Ubuntu which you are using. For example: Oneiric
Note: Just oneiric, Not oneiric-backports, Not oneiric-proposed, Not oneiric-security & Not oneiric-updates
Ex: [http://archive.ubuntu.com/ubuntu/dists/oneiric/](http://archive.ubuntu.com/ubuntu/dists/oneiric/)

3. There are 4 directories:
main/
multiverse/
restricted/
universe/
Go to the each of directories and download the both binary & debian installer documents according to your Ubuntu stracture (32 bit(i386) or 64 bit(amd64)).

4. Downloaded .gz files have probably the same name! You can change their name. However, extract and open documents. Glance lines. Deb Files addresses come in lines that start with "Filename". We'll use this point:
```
cat Packages | grep Filename >> lst.txt
```you know that "Packeges" should be replaced with the correct name of each of extracted archive files that you have downloaded.

5. Now, you have a/some text file(s). Open it/them with gedit> Ctrl+H> type below phrase in first field:
```
Filename: 
```Note: there is a space character after ":". 2nd field should be filled with the mirror you like, in this form:
Ex: 
[http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/pool/")

5. Employ a download manager and get all or some specified Debs  in one try.

_________________________________________________________________
Appendage:
CLI Download Managers: Wget, Aria2(aria2c), Axel, Curl, Prozilla, ...
```
 sudo apt-get install aria2
 sudo apt-get install axel
```GUI Download Manager: Jdownloader, Uget, FatRat, Steadyflow, Tucan Manager, ... 

Torrent Clients: Tixati, Vuze, ...


=> How to utilize Aria2 for downloading URLs which are placed into a text file: [FONT=tahoma]
[/FONT]```
[FONT=tahoma]aria2c -i name.txt[/FONT]
```

---

### Post by dino99 on 2011-09-16
why such complicated way ? is it usefull for something ?

---

### Post by Rasa1111 on 2011-09-16
yeah, there's a much, much easier way.
takes only 2 commands.

Does this do something different, or special?

---

### Post by SidebySide on 2011-09-17
> **dino99 said:**
> why such complicated way? is it usefull for something?
In some countries or zones, accessibility to internet, especially fast internet connection is so expensive or maybe unavailable and it may someone is using dialup yet. You know without internet Ubuntu dosen't mean! So in this case, the user can use internet of her/his university/office to download all packages and transfers them to her/his PC & Laptop. Moreover, you can offer a DVD(includes downloaded packages) accompanied by Ubuntu disk to someone who's using non-free OS, in such areas! I Usually prefer to search in my list for special software and download Deb file with all dependencies manually instead of using software center.

---

