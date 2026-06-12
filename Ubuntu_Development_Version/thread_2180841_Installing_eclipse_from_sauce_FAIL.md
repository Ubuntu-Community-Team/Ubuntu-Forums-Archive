---
title: "Installing eclipse from sauce: FAIL"
date: 2013-10-14
forum: Ubuntu Development Version
---

### Post by kampowchicken on 2013-10-14
First and foremost: noob here.

I was trying to install Eclipse-kepler from the original source. I was following some directions on an obscure blog (that I guess I lost the link to) which led me to a command:

"Exec=/opt/eclipse/eclipse" 

It set the path TO the executable and now I have the insides of my computer executable in my Home folder. This source also created the eclipse.desktop file but never actually linked to it. I've googled on how to reverse this Exec path but to no avail. I'm not sure if reversing this was given in the blog because I got angry and closed it out before I could finish looiking. 

I found another source that uses the actual icon and all I had to do was copy it from the applications folder into my panel but instead I have this. My questions are:

I was not able to find anything on how to reverse this, can I reverse this? or is this a permanent feature of my very neat Home dir? I would rather connect the applications icon with the /opt/ have the nice looking icon and to be able to get rid of this ugly feature.

Is it doable, if so, how? Please help!

Emergency Edit: I just realized that I have eclipse "running?" from two different folders, it's in Downloads and in /opt/ and I have no idea, I don't recall how that happened. Doubly help!

Last Edit: I was able to fix it, I rm -r'd the directory in /opt/ and in /Downloads and I rm -rd the executable in my home dir. I renamed the .eclipse(config) file and kept the workspace untouched. Found another set of tutorials for manual install and everything is up and running(right now).

---

