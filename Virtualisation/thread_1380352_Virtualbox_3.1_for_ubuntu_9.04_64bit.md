---
title: "Virtualbox 3.1 for ubuntu 9.04 64bit"
date: 2010-01-13
forum: Virtualisation
---

### Post by Dromedar on 2010-01-13
Now I have following problem 
 
I'll try to install virtualbox-3.1 from virtual box repository (deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free). I do the following

1. Add repository into /etc/apt/sources.list
2. Install the Sun public key for apt-secure: sudo apt-key add sun_vbox.asc
3. Remove older virtualbox 3.0: sudo apt-get remove virtualbox-3.0
4. Install virtualbox 3.1:

$ sudo apt-get install virtualbox-3.1

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  virtualbox-3.1: Depends: libqt4-opengl (>= 4.5.0~+rc1) but it is not going to be installed
E: Broken packages

5. I will try to install libqt4-opengl manually
$ sudo apt-get install libqt4-opengl 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  libqt4-opengl: Depends: libqtcore4 (= 4.5.0-0ubuntu4.3) but 4.5.1-1~ppa1~jaunty1 is to be installed
                 Depends: libqtgui4 (= 4.5.0-0ubuntu4.3) but 4.5.1-1~ppa1~jaunty1 is to be installed
E: Broken packages

Now I am confused. 

[LIST]
[*]libqtcore4 version 4.5.0-0ubuntu4.3 is needed but for some reason apt-get finds only 4.5.1-1~ppa1~jaunty1 ?
[/LIST]
Questions 

[LIST]
[*]is there some problem with my /etc/atp/sources.list ? Should I remove repositories from there
[/LIST]

[LIST]
[*]How can I see where libqtcore4 is coming from ?
[*]Can I install two version of libqtcore4 ?
[*]Is there a simple instructions for apt-get or synaptic (I am a simple person)?
[*]How can I fix this problem ?
[/LIST]

thank you in advance

---

### Post by jocampo on 2010-01-13
You will find some help about installing VBox via apt-get, here: [http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/]("http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/")

You can also install that directly, just download the package and double click (easier for you if you want a simple method) only difference is that you will not be able to update package via apt-get utility. I find this way better, because you will have more control regarding this specific program. New VBox releases are not so stable at the beginning so if you run apt-get, you could end upgrading your VBOx as well.

---

### Post by Dromedar on 2010-01-14
Thank you for your answer 
 
> **jocampo said:**
> You will find some help about installing VBox via apt-get, here: [http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/](http://www.sucka.net/2009/07/virtualbox-3-0-2-on-ubuntu-9-04-i386-or-amd64/) 
 
Page tells me to do what I have already done. The problem is still that virtualbox 3.1 package will not install into my system. (Or libqt4-opengl will not install).  There is no problem with vb 3.0
 
> **jocampo said:**
> You can also install that directly, just download the package and double click (easier for you if you want a simple method) only difference is that you will not be able to update package via apt-get utility. I find this way better, because you will have more control regarding this specific program. New VBox releases are not so stable at the beginning so if you run apt-get, you could end upgrading your VBOx as well. 
 
Earlier I did update virtualbox manually. And now I think it is better not to update with apt-get (I had some problems with 3.0 versions), so thank you for reminding me. 

If I download the package from virtualbox.org / Ubuntu 9.04 ("Jaunty Jackalope") AMD64 and double-click package manager says 'Error: Cannot install libqt4-opengl'
 
my problem is with apt-get and how to debug situation what I have: 
 
> The following packages have unmet dependencies. 
libqt4-opengl: Depends: libqtcore4 (= 4.5.0-0ubuntu4.3) but 4.5.1-1~ppa1~jaunty1 is to be installed 
Depends: libqtgui4 (= 4.5.0-0ubuntu4.3) but 4.5.1-1~ppa1~jaunty1 is to be installed 
E: Broken packages 
what should I do ? Any pointers where to look for more information. Does anyone else have the same problem ?

Maybe I should ask from other threads because this problem is not with virtualization, rather managing and debugging packages.

---

### Post by vadimxx on 2010-01-15
Hi.
I had the same problem. I solved it. Try next:

Add in /etc/apt/sources.list
deb [http://ppa.launchpad.net/c-korn/vlc/ubuntu](http://ppa.launchpad.net/c-korn/vlc/ubuntu) jaunty main

After that run in terminal:
sudo apt-get install libqt4-opengl=4.5.1-1~ppa1~jaunty1

It helped me and virtualbox-3.1 installed without problem.
My system is ubuntu 9.04 for i386 but I think the solution the same for you.

---

### Post by vadimxx on 2010-01-15
Just in case 
[https://launchpad.net/~c-korn/+archive/vlc/+build/995614](https://launchpad.net/~c-korn/+archive/vlc/+build/995614)

---

### Post by Dromedar on 2010-01-19
> **vadimxx said:**
> 
It helped me and virtualbox-3.1 installed without problem.
My system is ubuntu 9.04 for i386 but I think the solution the same for you.

Thank you. As you suspected it worked perfectly with Ubuntu 9.04 64 bit.

---

