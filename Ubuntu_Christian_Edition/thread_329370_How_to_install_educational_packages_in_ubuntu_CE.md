---
title: "How to install educational packages in ubuntu CE"
date: 2007-01-01
forum: Ubuntu Christian Edition
---

### Post by spainmiami on 2007-01-01
I've googled all around and read where one can add educational packages from Edubuntu to the unbuntu CE.

Also read where someone said "In fact Ubuntu CE comes with a special installer that allows you to install many of the educational packages that come with Edubuntu."

I'm sure i'm just one command away, also am a bit rusty with ubuntu at the moment.



BTW, this is for my niece, and I love the filtering in CE and love the educational programs of edubuntu.

Thanx, in case this has been covered already and I missed it in my search, don't flame just post link:)  Thanx in advance.

---

### Post by bruenig on 2007-01-01
```
sudo apt-get install edubuntu-desktop
```

That should do it.

---

### Post by spainmiami on 2007-01-02
> **bruenig said:**
> ```
sudo apt-get install edubuntu-desktop
```

That should do it.
Thanx for the reply but I am hoping to have those educational apps/games with it's filtering via ubuntu CE.

In other words I want to keep CE but add all the educational stuff. 

I guess I could just download them one at a time, however a lot of them are KDE based and being that CE is a Gnome environment:


Could anyone give me the command so I can paste it in the CE terminal and download the KDE desktop environment, withing ubuntu CE?

I tried sudo apt-get install kde" and "sudo apt-get kde" and it's a no go. Any help is greatly appreciated.

---

### Post by doobit on 2007-01-02
Under the Administration menu on your Ubuntu Desktop there is a selection called "Ubuntu Christian Edition Installer" Click on that and you will get options to install the educational software.

---

### Post by spainmiami on 2007-01-02
> **doobit said:**
> Under the Administration menu on your Ubuntu Desktop there is a selection called "Ubuntu Christian Edition Installer" Click on that and you will get options to install the educational software.
TY, very much.

BTW, as much as I love edubuntu, I'm am hesitant to install it for my niece because I don't know how to configure the Parental Filtering. 

Perhaps there's some tutorial out there that i'm not aware of. But from everything i've read it's complex process that I don't want to taking chances with my 9 year old niece's linux kid safe PC.

---

### Post by LaserJock on 2007-01-02
Well, you could do a couple things:
[LIST]
[*] install Edubuntu and then "convert" it to Ubuntu CE
[*] install Ubuntu CE and then install the edubuntu-desktop package (as was mentioned before)
[/LIST]

The first way will give you an Ubuntu CE look (as it is installed last) and the second will give you an Edubuntu look, by default. You can "mix-and-match" many Ubuntu flavors. For instance, you can install Edubuntu and Kubuntu on the same machine by installing from an Edubuntu disk and then installing kubuntu-desktop. Generally the one you install last sets the default artwork but you can change it later if you want.

-LaserJock

---

### Post by doobit on 2007-01-02
> **spainmiami said:**
> TY, very much.

BTW, as much as I love edubuntu, I'm am hesitant to install it for my niece because I don't know how to configure the Parental Filtering. 

Perhaps there's some tutorial out there that i'm not aware of. But from everything i've read it's complex process that I don't want to taking chances with my 9 year old niece's linux kid safe PC.

Parental controls are not really that complex. One secret is to first get the latest script for the updated GUI:

[http://www.ubuntuforums.org/attachment.php?attachmentid=20528&d=1165221070](http://www.ubuntuforums.org/attachment.php?attachmentid=20528&d=1165221070)

Jereme should put this on his website if he hasn't already.

There is a button there which lets you do a basic configuration just using a number between 50 and 200 to set limits according to the age range of your child.

---

### Post by bruenig on 2007-01-02
Installing edubuntu-desktop doesn't remove any of your CE stuff. All it will do is add all the apps and packages that are in edubuntu but weren't in CE. Therefore that means that all the games and educational stuff with be installed. You won't lose parental filtering or anything like that, I assure you. Also for kde
```
sudo apt-get install kubuntu-desktop
```

---

### Post by spainmiami on 2007-02-04
> **bruenig said:**
> ```
sudo apt-get install edubuntu-desktop
```

That should do it.
TY.

On the other hand, what if I had edubuntu installed 1st then I want to add CE?

What the command in the terminal? 

I've tried several variations sudo apt-get install CE-desktop and sudo apt-get install ubuntu-CE

I just can't figure it out. How do u guys know all the terminal commands? Is there a site or cheat-chit out there somewhere.

Or can it be found in the repositories?

---

### Post by dakotadare2b on 2007-02-06
You could just use the convert me scripts at the following link. You will need to choose the correct script, depending on which version of Ubuntu that you have 6.06 or 6.10, download the script and run it.

The link is [http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html](http://www.whatwouldjesusdownload.com/christianubuntu/2006/07/download.html)

God Bless,
Randy

---

