---
title: "Downloading through windows computers"
date: 2007-10-25
forum: Ubuntu Brainstorm
---

### Post by StephanG on 2007-10-25
My current kubuntu desktop does not have an internet connection, but I have access to several windows computers which do have internet access.  Perhaps we could create a feature for APT that would list the package and package dependancies in such a manner that a Windows PC could automatically download all the required packages.  And then simply carry it back to a linux PC on a USB disk or something, and have either Synaptic or Adept simply install them from there.

Sorry my programing skill is but a sliver cut from a small 'basics' block, would it be possible for windows to download everything required onto a single .deb file and simply have the linux user click on the file to install through synaptic?

Feedback would be appreciated. :)

Thanks

Stephan

---

### Post by smartboyathome on 2007-10-25
This is already available through packages.ubuntu.com. Check it out. :)

---

### Post by mysticmatrix on 2007-10-25
> **smartboyathome said:**
> This is already available through packages.ubuntu.com. Check it out. :)

They don't resolve any dependency though. Sort of reminds me of RPM hell.

---

### Post by smartboyathome on 2007-10-26
> **mysticmatrix said:**
> They don't resolve any dependency though. Sort of reminds me of RPM hell.

It DOES have the dependancies on there. [This is a link to cairo-clock]("http://packages.ubuntu.com/gutsy/x11/cairo-clock") which has dependancies listed with a red dot. recommended packages have a green diamond.

---

### Post by Perfect Storm on 2007-10-26
It could be quite cool if there was a box you can check/uncheck, so if you download X,Y,Z it will also download the dependecies of X,Y,Z on packages.ubuntu.com

---

### Post by Bou on 2007-10-26
> **Artificial Intelligence said:**
> It could be quite cool if there was a box you can check/uncheck, so if you download X,Y,Z it will also download the dependecies of X,Y,Z on packages.ubuntu.com

Yup, I think that's what mysticmatrix meant.

---

### Post by mysticmatrix on 2007-10-26
> **Artificial Intelligence said:**
> It could be quite cool if there was a box you can check/uncheck, so if you download X,Y,Z it will also download the dependecies of X,Y,Z on packages.ubuntu.com

Quite right. It does not "manages" dependencies. One can always follow manual method for just anything I guess.

---

### Post by StephanG on 2007-10-27
What about packages already downloaded onto another computer?  I have kubuntu on my own computer, and installed ubuntu onto my mother's.  Would it be possible to get the gnome desktop from her computer without downloading it from the internet?  Or else download Xfce desktop onto one computer and install it on both PC's.  Would it be possible to add to synaptic/adept so that is automatically download's packages from the LAN if it has already been installed on other computers.  Does it already have this capability?  Sorry, I am something of a linux noob, so for all I know it may already have been implimented.

The reason I am suggesting these things, is because a lot of people that I know struggle with either slow download speeds or capped lines.  (Living in South Africa :s)

And if ubuntu is going to serve as a free alternative in schools with low budgets, internet connection is probalbly going to play a role.  Especially in third world countries.

Stephan

---

### Post by UbuWu on 2007-10-27
You can use apt-proxy or aptoncd for that

---

### Post by mysticmatrix on 2007-10-27
> **StephanG said:**
> What about packages already downloaded onto another computer?  I have kubuntu on my own computer, and installed ubuntu onto my mother's.  Would it be possible to get the gnome desktop from her computer without downloading it from the internet?  Or else download Xfce desktop onto one computer and install it on both PC's.  Would it be possible to add to synaptic/adept so that is automatically download's packages from the LAN if it has already been installed on other computers.  Does it already have this capability?  Sorry, I am something of a linux noob, so for all I know it may already have been implimented.

The reason I am suggesting these things, is because a lot of people that I know struggle with either slow download speeds or capped lines.  (Living in South Africa :s)

And if ubuntu is going to serve as a free alternative in schools with low budgets, internet connection is probalbly going to play a role.  Especially in third world countries.

Stephan

Well if you are on LAN, on of you can set up a personal repositories which mirrors that of canonical. My college does that to save bandwidth. It's uses something called rsync(perhaps), and as I'm no Linux poweruser, I don't exactly knows how it works.
For simple user point of view, you can install Apt-on-CD on person having Net access on a Ubuntu PC and can then transfer the package through a CD and install them on your computer. Make sure you download Apt-On-CD for your desktop. It as not unsatisfied dependence, as far as I remember. 
Check out Apt-on-CD webpage for more information.[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

EDIT: AS for school problem, you can get DVD's with Ubuntu repositories if you wish to pay for one. Or you may try this: [http://ubuntuforums.org/showthread.php?t=352460](http://ubuntuforums.org/showthread.php?t=352460)

---

### Post by airtonix on 2007-10-29
I used apt on cd for your exact situation when i was without net for a week.

Check out Apt-on-CD webpage for more information.[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

