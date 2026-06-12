---
title: "CNR Plugin for Ubuntu out? (Beta)"
date: 2007-09-28
forum: The Cafe
---

### Post by xArv3nx on 2007-09-28
Ubuntu 7.04 
 
Steps to install the cnr-client .deb file in Ubuntu 7.04: 
Using apt-get: 
1) Open a console (Menu for starting a terminal emulator> Shell in the Quick Launch Menu or Programs > System > Terminal Program 
2) From the command prompt: sudo apt-get update 
3) From the command prompt: sudo apt-get install cnr-client 
Note: This process will create a desktop CNR icon and a menu entry under Programs > System 


OR 


Using the Download Client page: 
1) Downloaded the file 
2) Open a console (Menu for starting a terminal emulator> Shell in the Quick Launch Menu or Programs > System > Terminal Program 
3) From the command prompt: sudo dpkg -i cnr-client.deb 
Note: This might require downloading and installing dependencies via the native package installation system and running the command again. Steps 4 and 5 are not required if there are no errors . 
4) From the command prompt: sudo apt-get -f install 
5) From the command prompt: sudo dpkg -i cnr-client.deb 


Once the Client installs correctly: 
1) Open Firefox Web Browser 
2) From CNR.com select Install Now for a product 
3) When the dialog box opens select Open with: Browse to File System > usr > bin and chose cnr (location /usr/bin/cnr) 
Note: We recommend selecting "Do this automatically for files like this from now on". 
Note: This might require to log-out then back in for the permissions to be set correctly 


 Additional Steps Needed: (Maybe?)

ADD THIS TO /etc/apt/sources.list

# Additional Sources
deb     [http://apt2.freespire.org/CNRUbuntuExtra](http://apt2.freespire.org/CNRUbuntuExtra) feisty-extra main restricted
deb-src [http://apt2.freespire.org/CNRUbuntuExtra](http://apt2.freespire.org/CNRUbuntuExtra) feisty-extra main restricted

CNR Plugin is in BETA stage. BTW, can anyone confirm this works? If so, I'll move to Ubuntu until 6.1 comes out. 

Please respond. :)

P.S., if this is in the wrong section, I apologize. Please, move it if it is in the wrong section, mods. TY.

EDIT: Sources:
[http://www.cnr.com/supportPages/communityDownloadPluginInstructions.seam#Linspire](http://www.cnr.com/supportPages/communityDownloadPluginInstructions.seam#Linspire)
[http://wiki.freespire.org/index.php/Sources_list#CNR.com_Sources](http://wiki.freespire.org/index.php/Sources_list#CNR.com_Sources)

EDIT2: I just needed to go to the cnr.com website, download the plugin, install it, run apt-get -f install, install cnr again, then run it. =D

Works perfectly with the exception of Lsongs not working when trying to install. It's that package only, though, because I tried another package and it worked fine. ;)

Works fine for me. Few bugs here and there, nothing bad.

---

### Post by dasunst3r on 2007-09-28
For some reason, this CNR doesn't seem too worthwhile to me.  If one is capable of searching on the web, they can surely find later versions of the software being offered.

---

### Post by GSF1200S on 2007-09-28
While I guess I cant necessarily find a specific thing wrong with CNR, I just dont like it. I dont know why, I just dont.

Ubuntu has cost me a total of like 30 somethin dollars, and thats a book I bought on it. Despite all the cool stuff ive done and the fun moments, I havent spent anything. I think this is where my problem is- i dont want a salesman bundled with my buntu.

Maybe im just being paranoid, but I really just dont get a good feeling about CNR.

---

### Post by starcraft.man on 2007-09-28
Seems like a lot of steps to get an alternate way to install things, especially when I can "sudo aptitude install x" in one step.

Anyway, beta software won't be touching my stable Feisty partition...

---

### Post by jrusso2 on 2007-09-28
This should be interesting.  Its really buggy on Freespire 2,  should be even more buggy on Ubuntu

---

### Post by xArv3nx on 2007-09-28
> **starcraft.man said:**
> Seems like a lot of steps to get an alternate way to install things, especially when I can "sudo aptitude install x" in one step.

Anyway, beta software won't be touching my stable Feisty partition...
Just download the CNR package, then install it with GDebi. (Or whatever it's named.)

@ at above poster, hence why it's called beta software. =X

Trust me, it's improved a lot since pre-alpha. -_- BTW, aren't you on the Freespire forums? =D

---

### Post by RAV TUX on 2007-09-28
I have embraced the terminal and apt-get/aptitude. CNR just does not seem worth the effort.

I do hope that someone out there finds it useful.

---

### Post by starcraft.man on 2007-09-28
> **xArv3nx said:**
> Just download the CNR package, then install it with GDebi. (Or whatever it's named.)
I'm well aware of how to install packages. It's still more effort than me installing things from regular methods. Plus, it's beta software, and like I said my Feisty partition is stable and I work on it, I've no need to cause problems nor do I imagine would other people. Frankly, I also don't like the idea of depending on a third party service to install things, they can always go down...

> **RAV TUX said:**
> I have embraced the terminal and apt-get/aptitude. CNR just does not seem worth the effort.
Welcome aboard, I love terminal. Makes me feel all warm and fuzzy like back in the DOS days (minus the frustration) :).

---

### Post by RAV TUX on 2007-09-28
> **starcraft.man said:**
> 
Welcome aboard, I love terminal. Makes me feel all warm and fuzzy like back in the DOS days (minus the frustration) :).
Thanks for the welcome, I came to embrace the terminal a bit of a round about way. I first embraced emerge in a Gentoo system(Sabayon) then I grew to appreciate the simplicity and beauty of apt-get & aptitude.

---

### Post by reyfer on 2007-09-28
All that is needed for installing packages is apt-get or synaptic. CNR is a waste of resources and hard drive space.

---

### Post by jrusso2 on 2007-09-29
> **xArv3nx said:**
> Just download the CNR package, then install it with GDebi. (Or whatever it's named.)

@ at above poster, hence why it's called beta software. =X

Trust me, it's improved a lot since pre-alpha. -_- BTW, aren't you on the Freespire forums? =D

I have an install of Freespire here and the new plugin but still has lots of issues

---

### Post by jrusso2 on 2007-09-29
> **reyfer said:**
> All that is needed for installing packages is apt-get or synaptic. CNR is a waste of resources and hard drive space.

Don't be surprised if Ubuntu comes out with something like CNR and Linux Mint is working on one too.

Its the easy way for the new user to install codecs and other things they need.

---

### Post by reyfer on 2007-09-29
> **jrusso2 said:**
> Don't be surprised if Ubuntu comes out with something like CNR and Linux Mint is working on one too.

Its the easy way for the new user to install codecs and other things they need.

Maybe they will, and since CNR is nothing more than synaptic with screenshots and "user reviews", it is not difficult. And again, I ask people to not generalize by saying "new users need this" as if every new user has the same needs. My grandmother is using Ubuntu, she come from Windows, and she's perfectly fine with synaptic.

---

### Post by jrusso2 on 2007-09-29
> **reyfer said:**
> Maybe they will, and since CNR is nothing more than synaptic with screenshots and "user reviews", it is not difficult. And again, I ask people to not generalize by saying "new users need this" as if every new user has the same needs. My grandmother is using Ubuntu, she come from Windows, and she's perfectly fine with synaptic.

Well I help new users and most don't even know what synpatic is.  They download some tar file and ask me how to install K3B.  They download java from Sun and ask how to install it and get flash off the adobe web site.

---

