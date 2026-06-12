---
title: "SwiftWeasel for 9.04"
date: 2009-05-04
forum: The Cafe
---

### Post by thraxsa on 2009-05-04
I was reading about this browser in a local magazine - I was looking to give it a try but noticed no repository for 9.04 distro ... 

Iam able to install this browser somehow, other than compiling from source ??

---

### Post by kpkeerthi on 2009-05-04
Download and extract the tar from [here]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=679632") (choose the one that is appropriate for your CPU architecture). Extract the file. cd to the folder and run ./swiftweasel

---

### Post by thraxsa on 2009-05-04
> **kpkeerthi said:**
> Download and extract the tar from [here]("http://sourceforge.net/project/showfiles.php?group_id=195473&package_id=230717&release_id=679632") (choose the one that is appropriate for your CPU architecture). Extract the file. cd to the folder and run ./swiftweasel

cool ... thanks : )

---

### Post by d_yat on 2009-09-05
Did you get SwiftWeasel to work on 9.04? I've had problems trying to get it to run. (command line says "Illegal Instruction")
the tarball works for my Hardy install, but not for my Jaunty (9.04) install.

---

### Post by Jesus_Valdez on 2009-09-05
Im currently using swiftweasel 3.5.2 and its great.

Some  previous version, 3.5 I guess, broke some stuff (bookmarks, history, and I think even flash and add-ons) but this recent build its great as usual.

Like someone said you just have to extract the tar and doubleclick on the "switfweasel" file. I put a launcher on my upper panel to that file so its always at hand.

---

### Post by bodhi.zazen on 2009-09-05
A little off topic, I like icecat 

[http://www.gnu.org/software/gnuzilla/](http://www.gnu.org/software/gnuzilla/)

The only problem is I can not get it to run on 64 bit arch :(

---

### Post by dragos240 on 2009-09-05
Is swiftweasel a mix of swiftfox and icewesel?

---

### Post by RabbitWho on 2009-09-05
Is there a big performance difference between swiftweasel and swiftfox?

---

### Post by RabbitWho on 2009-09-05
bump!

---

### Post by KushedVapors on 2009-09-06
> **RabbitWho said:**
> Is there a big performance difference between swiftweasel and swiftfox?



hell yes it is. i personally think swiftfox is a placebo. only thing is i dont know whcih version to run on my amd athlon xp 2500+

---

### Post by RabbitWho on 2009-09-06
Cool, so does anyone know an idiot-proof guide for installing tar.gz files? 
Sorry I'm such a newbie.

[http://forum.codecall.net/linux-tutorials-guides-tips/18755-spoonfed-linux-tutorials-installing-software-source.html](http://forum.codecall.net/linux-tutorials-guides-tips/18755-spoonfed-linux-tutorials-installing-software-source.html)

I'm following that, only maybe the spoon is too big for me. 

rabbit@penguincounter:~$ tar -zxvf swiftweasel
tar: swiftweasel.tar: Cannot open: No such file or directory

also I tried it with the thingys.. 
rabbit@penguincounter:~$ tar -zxvf <swiftweasel>
bash: syntax error near unexpected token `newline'

I assume that means that the > is a newline command. 

I'm in the right folder, that's how the file is listed.. as in it's called swiftweasel all lower case no extensions or anything.

---

### Post by RabbitWho on 2009-09-06
Bump

---

### Post by Jesus_Valdez on 2009-09-06
So heres what I do.

I select the proper file from this [http://download.tuxfamily.org/swiftweasel/](http://download.tuxfamily.org/swiftweasel/)

That would be [http://download.tuxfamily.org/swiftweasel/swiftweasel-35/3.5.2-tar.gz/swiftweasel-3.5.2_intel-pgo_x86_64-ubuntu.tar.gz](http://download.tuxfamily.org/swiftweasel/swiftweasel-35/3.5.2-tar.gz/swiftweasel-3.5.2_intel-pgo_x86_64-ubuntu.tar.gz)   Wich means the Ubuntu build, for x86_64 the version 3.5.2

After the download completes, I just untar it (rigth click,extract here) double click on the folder that its create and another double click on the "swiftweasel" file, I say that I want to run it et voila, swiftweasel opens with all the stuff from Firefox, then I just grab my bookmarks and I'm lock'nload.

EDIT. I don't do any fancy install, I used to install it from the repos, but I prefer this way because I think they are out of line of something.

---

### Post by RabbitWho on 2009-09-07
> **Jesus_Valdez said:**
> So heres what I do.

I select the proper file from this [http://download.tuxfamily.org/swiftweasel/](http://download.tuxfamily.org/swiftweasel/)

That would be [http://download.tuxfamily.org/swiftweasel/swiftweasel-35/3.5.2-tar.gz/swiftweasel-3.5.2_intel-pgo_x86_64-ubuntu.tar.gz](http://download.tuxfamily.org/swiftweasel/swiftweasel-35/3.5.2-tar.gz/swiftweasel-3.5.2_intel-pgo_x86_64-ubuntu.tar.gz)   Wich means the Ubuntu build, for x86_64 the version 3.5.2

After the download completes, I just untar it (rigth click,extract here) double click on the folder that its create and another double click on the "swiftweasel" file, I say that I want to run it et voila, swiftweasel opens with all the stuff from Firefox, then I just grab my bookmarks and I'm lock'nload.

EDIT. I don't do any fancy install, I used to install it from the repos, but I prefer this way because I think they are out of line of something.


Hee hee cool, I did all that, but when I extracted the folder and looked in it I couldn't see any obviously clickable files, and i clicked on a few and nothing happened.. so when you said that I tried some more..And bobs your uncle! 
Ha ha sometimes things are harder when you expect them to be. 

[IMG]http://imgs.xkcd.com/comics/tech_support_cheat_sheet.png[/IMG]
Just click on everything!

Edit: 

I've done scragz's rendering test in both browsers, with two tabs open, and each time swift fox has won.. 

?

[http://scragz.com/archived/mozilla/test-rendering-time](http://scragz.com/archived/mozilla/test-rendering-time)

---

### Post by Sealbhach on 2009-09-07
Swiftweasel 3.5.2  is definitely better than the default Ubuntu Firefox - much faster and more stable, I think.

The way I install it is download the tar.gz, extract it in my /home directory - it creates a folder called "swiftweasel". Then I create a launcher in my menu that has this command:

```
/home/username/swiftweasel/swiftweasel
```Where you substitute "username" for your own username. 

Simple.

.

---

