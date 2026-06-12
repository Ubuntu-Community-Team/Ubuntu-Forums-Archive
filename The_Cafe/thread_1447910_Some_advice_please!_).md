---
title: "Some advice please! :)"
date: 2010-04-05
forum: The Cafe
---

### Post by mcoleman44 on 2010-04-05
Some advice for new users of Ubuntu and Linux in general. What advice would have helped you when you first installed Ubuntu?

---

### Post by mcoleman44 on 2010-04-05
My advice, for example, would be to try this before saying you cant get your wireless working:
```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```
After you log back in go to System>Administration>hardware drivers

---

### Post by Dayofswords on 2010-04-05
do some research, learn what it is, what it is used for and how it is different from windows

thats what i did in a nutshell

---

### Post by Khakilang on 2010-04-06
Get the internet to work and update all the files. Download all the movie and music codec. Read a lot and don't hesitate to experiment. Most of all enjoy yourself.

---

### Post by conradin on 2010-04-06
use a live cd. explore, tinker, etc, then install if you like it.

---

### Post by Psumi on 2010-04-06
> **conradin said:**
> use a live cd. explore, tinker, etc, then install if you like it.

...and then find out none of your old apps work by installing the windows version.

...and then find out the ubuntu version doesn't work on debian, and the debian version [might] not work on Ubuntu.

---

### Post by unknownPoster on 2010-04-06
Ubuntu isn't the only distribution out there, and many others are superior by far.

---

### Post by Crunchy the Headcrab on 2010-04-06
> **unknownPoster said:**
> Ubuntu isn't the only distribution out there, and many others are superior by far.
Subjective post is subjective.

I understand what you're saying, and I agree that Ubuntu isn't necessarily the best, although it IS my favorite distro and many other people's also.

---

### Post by sixthwheel on 2010-04-06
> What advice would have helped you when you first installed Ubuntu?

Install flash from the software center, not from the Flash website.

---

### Post by unknownPoster on 2010-04-06
> **Crunchy the Headcrab said:**
> Subjective post is subjective.

I understand what you're saying, and I agree that Ubuntu isn't necessarily the best, although it IS my favorite distro and many other people's also.

It's hardly subjective.

Ubuntu is NOT the best for ancient computers, whereas DSL, Puppy, SliTaz, are much better.

And in the corporate world RHEL is superior for servers.

---

### Post by Crunchy the Headcrab on 2010-04-06
> **unknownPoster said:**
> It's hardly subjective.

Ubuntu is NOT the best for ancient computers, whereas DSL, Puppy, SliTaz, are much better.


Is that what makes a disto superior?  Thanks for clearing that up.

One suggestion that I have for new users is to use the man command to look up information for commands that you don't understand.  There is a lot of documentation that can be helpful if you look up man and combine what you learn with a few google searches.

---

### Post by Naggobot on 2010-04-06
1. +1 for #2 post.
2. +1 for #9 post. Generally do not install anything outside of the repositories until you know how and why. I have now used Ubuntu 1.5 years and I do not yet know and have not yet deeded to install anything outside of the repositories. 

1. If your local law permits enable all repositories from 

System->Administration->Synaptic Package Manager

In Synaptic select

Settings-> Repositories

From first tab select all except source code, close window.  

Install *ubuntu-restricted-extras* by typing the name to the quick search box of the Synaptic. 

(This may be semiautomatic already, I do not remember if I had to do this manually with 9.10)

2. If your local law permits, find out how to install DVD encryption library and install it. 

3. Install VLC-media player.  

4. You can install different localization packages (languages) and you can change the language from the login screen. 

5. Get ubuntu pocket quide [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

6. Learn to use multiple desktops and configure a good shortcut keys for actions you use.

7. In terminal you can get process list by typing 

```
ps -A

```8. You can kill a process from terminal by using kill command

```
kill *psid*
```or if the process does not believe above then 

```
sudo kill -9 psid

```9. sudo is the command to execute commands as root and gksudo is for graphical applications. 

10. By pressing ctrl+alt+F(n) where n is 1 to 7 you can switch between terminals (or was it consoles). Do not be alarmed, the graphical can be found from ctrl+alt+F7. You can log in to any of those terminals and execute commands. 

11. Xsession is restarted by pressing altgr (right alt) + sysrq + k

---

### Post by velle frak on 2010-04-06
Don't give up too easy when something doesn't work. It's worth to stick with it ;).

---

### Post by Untitled_No4 on 2010-04-06
When the computer doesn't respond:
Alt + PrtSc + k
and if nothing happens after a few seconds:
Alt + PrtSc + (r -> e -> i -> s -> u -> b)

---

### Post by ssam on 2010-04-06
not to use forum subjects like "please help", "ubuntu question", "help me", "advice please"...

---

### Post by Psumi on 2010-04-06
> **Naggobot said:**
> 2. +1 for #9 post. Generally do not install anything outside of the repositories until you know how and why. I have now used Ubuntu 1.5 years and I do not yet know and have not yet deeded to install anything outside of the repositories. 

I'd rather install flash 10.1, as it takes up 10% less CPU on some flashes. Even though some functionality will not work, and the dreaded flickering flash comes back... I'd rather have less CPU consumption.

---

### Post by red_Marvin on 2010-04-06
> **unknownPoster said:**
> It's hardly subjective.

Ubuntu is NOT the best for ancient computers, whereas DSL, Puppy, SliTaz, are much better.

And in the corporate world RHEL is superior for servers.

But that is when adding constraints that were not there in the initial statement. I use and prefer arch, but it is a matter of superiority for the things *I* do and *my* views on computing.

I would say that people generally need to ditch the mantra that cli/bash is difficult. I mean there is the possibility of doing advanced stuff with it, but general stuff like *sudo apt-get ...* should be understandable by *anibody* able to interpret written English.

---

### Post by mcoleman44 on 2010-04-06
> not to use forum subjects like "please help", "ubuntu question", "help me", "advice please"...

I fail to see the problem. Maybe instead of simply posting the problem you could try offering a solution as to what it is you would rather see. If it was an actual support question I would have been more detailed, but seeing as This thread is listed under the community carfe I figured I could keep it simple.

---

### Post by shawnhcorey on 2010-04-06
> **mcoleman44 said:**
> Some advice for new users of Ubuntu and Linux in general. What advice would have helped you when you first installed Ubuntu?

Step 1: Back up your data!

---

### Post by blueturtl on 2010-04-06
My advice goes out to the neurotic tinkerer sort (the kind I am):

In Linux it's good practice to keep your files separate from the rest of the system. That's what /home is for. The beauty of it, is that you can easily map /home to another partition and/or device altogether. If you ever have to do the Linux equivalent of "format c:" (or just want to try a different distribution), your files and settings, even your wallpapers are all preserved just the way you want them.

Use the applications provided in the system repositories. Having version  1.31 instead of 1.30 is not worth the hassle in trying to manage everything yourself. Embrace package management, it is meant to make you life easier.

Don't fuss about memory use or other details of the system if everything is working fine. Comparing systems to one another only makes sense if they are identical. Linux scales to make the most of your hardware. Firefox will eat tons of RAM if you have tons of RAM.

---

### Post by sudoer541 on 2010-04-06
> **mcoleman44 said:**
> My advice, for example, would be to try this before saying you cant get your wireless working:
```
sudo apt-get update
sudo apt-get upgrade
sudo reboot
```After you log back in go to System>Administration>hardware drivers


I'd rather go work for NASA and create a rocket, instead of using this complicated code!
If you expect noobz to use codes, then ubuntu or Linux is not for them!

---

### Post by whiskeylover on 2010-04-06
Buy a mountain bike, periodically turn off your computer, and meet real people once in a while. It helps when you eventually get bored of computers.

---

