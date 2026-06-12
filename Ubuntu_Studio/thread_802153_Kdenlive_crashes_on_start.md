---
title: "Kdenlive crashes on start"
date: 2008-05-21
forum: Ubuntu Studio
---

### Post by Sain on 2008-05-21
I've installed Kdenlive from repos, but it wont't start... :-/

This is what I get when I try to run it from terminal:
```

kdenlive:  + + YOUR MLT INSTALL WAS FOUND IN: /usr
kdenlive: //  INIT EFFECT SEARCH
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: WARNING: KLocale: trying to look up "" in catalog. Fix the program
kdenlive: ---------  close 1b
kdenlive: ---------  close 2b
kdenlive: Mlt inited
kdenlive: Creating new document
kdenlive: deleting contents...
kdenlive: Creating new document DONE
kdenlive: ---------  close 3b
kdenlive: ****************  INIT DOCUMENT VIEW ***************
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive:
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
kdenlive:  + + CREATING CONSUMER WITH PROFILE: pal_dv
kdenlive: --------  INIT SCENE LIST ------_
kdenlive: <westley>
 <tractor>
  <multitrack>
   <playlist>
    <producer in="0" out="0" id="black" colour="black" resource="colour" />
   </playlist>
   <playlist/>
   <playlist/>
   <playlist/>
   <playlist/>
  </multitrack>
 </tractor>
</westley>
kdenlive:
kdenlive: WARNING: //////  RENDER, SET SCENE LIST
Unable to start Dr. Konqi

```

I've found that similar bug report exists([https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/223260](https://bugs.launchpad.net/ubuntu/+source/kdenlive/+bug/223260))... Could it be that Ubuntu package for Kdenlive is broken? Is there another way to install it?

---

### Post by imon9 on 2008-05-21
u can delete the config file in your user folder, then when kdenlive start, it will ask u to choose the correct video type...choose the correct type will make it not crash

---

### Post by Sain on 2008-05-21
What is the name of the configuration file? I can't seem to find it anywhere in my home folder...

---

### Post by SlappyPappy on 2008-05-21
I can get it to start but it croaks itself after 4 minutes or so. Damn shame! It looks like it's got all the nice little tweaks to be a decent program. 

It could take them a long to figure out the crashes though and might even be machine specific for all I know.

Oh well, back to my Mac for some video editing!  :(

---

### Post by imon9 on 2008-05-23
> **Sain said:**
> What is the name of the configuration file? I can't seem to find it anywhere in my home folder...

/home/(username)/.kde/share/config/kdenliverc

usually i will also delete the folder "kdenlive" under /home/edric/.kde/share/apps

---

### Post by Malcy on 2008-05-23
Every time I use Kdenlive, it's a very frustrating crash filled experience.

---

### Post by jlindbergh on 2008-11-14
> **Malcy said:**
> Every time I use Kdenlive, it's a very frustrating crash filled experience.

Sorry to say the same. I've tried it from the repositories in both Hardy and Intrepid, with and without compiz, but it's always unstable and crashes when you least expect it.
Works better than cinerella though.

---

### Post by nowardev on 2008-11-15
try with this open a terminal and write (working on my computer )

kdesudo kdenlive 

if it crashes try to see this 

1 : sudo apt-get install libxcb-composite0 libxcb1-dbg libxcb1-dev
2: delete configuration files (~/.kde/share/config/kdenliverc)
3: try to disalble compiz (gnome user run this :     metacity --replace  ;  kde user      kwin --replace)

---

### Post by Toadinator on 2008-11-15
well I bet these crashes are just part of 0.6/0.5/whatever version is in the repos. 0.7 just came out and looks amazing. I'm working on compiling it for my ppa; I'll post later with it so you guys can have a less frustrating video editing experience ;P

---

### Post by Malcy on 2008-11-16
I've been trying to install 0.7. I am using the builder wizard but get stuck at the point that it wants to use sox-dev which is not used in Intrepid. Any ideas?

[http://www.kde-apps.org/content/show.php?content=85826&forumpage=0&PHPSESSID=22472764dbf079761a5aa374aa977cfd](http://www.kde-apps.org/content/show.php?content=85826&forumpage=0&PHPSESSID=22472764dbf079761a5aa374aa977cfd)

---

### Post by Ubuntiac on 2008-11-22
Just open the Builder Wizard and:

1. Go through to the page titled "Compile Options"
2. Click "Advanced"
3. Make sure that "Disable SOX support" is checked and continue.

I build every day with this on Kubuntu 8.10 as I love seeing all the new features and fixes coming in.

I know... Weird addictions... ;)

---

### Post by Malcy on 2008-11-22
Thanks for the tip but I have done this and it still brings up the issue about sox-dev. :confused:

---

### Post by Malcy on 2008-11-22
I just tried again and it worked!!!!

However, in my first try to load some clips, it crashed. :cry:

I will report back crashes as it looks really good IMO.

---

### Post by Dalem50 on 2009-03-09
> **imon9 said:**
> u can delete the config file in your user folder, then when kdenlive start, it will ask u to choose the correct video type...choose the correct type will make it not crash

That worked well.

---

