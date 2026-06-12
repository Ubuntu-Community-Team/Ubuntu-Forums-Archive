---
title: "Installing Wine without having internet connection on ubuntu 10.04"
date: 2010-09-01
forum: Wine
---

### Post by pinkfolio on 2010-09-01
hello there
 
i have just installed ubuntu 10.04 LTS on my system. previously i have installed 
windows 7 professional 32bits. my internet service provider requires me to run
an exe file which provides internet access through usb modem. now i want to 
install wine on ubuntu so that i could run the exe file in ubuntu but the problem
is that i can only access the internet from windows 7. so how can i download the
perfect version of wine for 10.04 and how to install it in ubuntu?
 
many thanks
 
pF

---

### Post by lukeiamyourfather on 2010-09-01
Most internet service providers require an application to run only for the first use to setup everything. Typically once it has been run once it doesn't need to be run again and whatever machine you want should be able to connect.

---

### Post by cwwilson721 on 2010-09-01
A few questions:

[LIST=1]
[*]Do you still have Windows installed on your computer? If so, you can get the .deb file somewhere, and copy it over (Either burn to a cd/dvd, or through a shared folder). Also, you can get the internet settings you need for Ubuntu that way (IP Address, dhcp settings, whether or not it's PPOE, whatever).
[*]What kind (Brand, Model) of modem? Many work fine in Ubuntu. (You might be amazed). Google the model/brand of modem like "ubuntu Motorola 5100". You might get some clues there.
[/LIST]
Unless you have Windows, or a working internet connection, it would be near impossible to install wine.

---

### Post by AllRadioisDead on 2010-09-02
Use whatever you're posting on now to download the .deb?

---

### Post by pinkfolio on 2010-09-02
> **cwwilson721 said:**
> A few questions:

[LIST=1]
[*]Do you still have Windows installed on your computer? If so, you can get the .deb file somewhere, and copy it over (Either burn to a cd/dvd, or through a shared folder). Also, you can get the internet settings you need for Ubuntu that way (IP Address, dhcp settings, whether or not it's PPOE, whatever).
[*]What kind (Brand, Model) of modem? Many work fine in Ubuntu. (You might be amazed). Google the model/brand of modem like "ubuntu Motorola 5100". You might get some clues there.
[/LIST]Unless you have Windows, or a working internet connection, it would be near impossible to install wine.
 
hi , 
 
point 1, yes i have windows 7 installed on my system, previously i downloaded the deb 
file but when i run it in ubuntu it say dependency not satisfiable : libaudio2 , so i thought
may be there is some problem with deb file, then i downloaded the code of wine and
tried to complie it, it give the error of flex not installed, how can i install flex if i dont
have access to internet, and for internet access i need to install wine, ahhh, kinda deadlock :(
 
point 2, tried but in vain 
 
thanks for your time !

---

### Post by Dalo9 on 2010-09-02
i'm a total noobee and am trying to do the same thing (install Wine on Ubuntu at home without internet connection). I found this link useful and will try these commands when I get home this evening.
 
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
 
hope it helps
 
here are the instructions in a shell-of-a-nut
 
[FONT=Times New Roman][SIZE=3]Open the Software Sources menu by going to **System->Administration->Software Sources**. Then select the **Other Software** tab and click **Add**.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Then, **copy and paste the line below**.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]*ppa:ubuntu-wine/ppa* [/FONT][/SIZE]
[FONT=Times New Roman]Click close to finish, and then **reload the package information** when prompted. If you have Wine installed already, update manager will offer to upgrade you to the stable Wine 1.2[/FONT]

---

### Post by cwwilson721 on 2010-09-02
> **Dalo9 said:**
> i'm a total noobee and am trying to do the same thing (install Wine on Ubuntu at home without internet connection). I found this link useful and will try these commands when I get home this evening.
 
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)
 
hope it helps
 
here are the instructions in a shell-of-a-nut
 
[FONT=Times New Roman][SIZE=3]Open the Software Sources menu by going to **System->Administration->Software Sources**. Then select the **Other Software** tab and click **Add**.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]Then, **copy and paste the line below**.[/SIZE][/FONT]
[SIZE=3][FONT=Times New Roman]*ppa:ubuntu-wine/ppa* [/FONT][/SIZE]
[FONT=Times New Roman]Click close to finish, and then **reload the package information** when prompted. If you have Wine installed already, update manager will offer to upgrade you to the stable Wine 1.2[/FONT]And just WHERE do you think it will get the software from? The internet.

Thus, no net, no install.

---

### Post by lukeiamyourfather on 2010-09-02
> **cwwilson721 said:**
> And just WHERE do you think it will get the software from? The internet.

Thus, no net, no install.

They're posting here, so they obviously have a connection somewhere.

---

### Post by alaukikyo on 2010-09-02
[SIZE=2]> **pinkfolio said:**
> hello there

i have just installed ubuntu 10.04 LTS on my system. previously i have installed [/SIZE]  [SIZE=2]
windows 7 professional 32bits. my internet service provider requires me to run
an exe file which provides internet access through usb modem. now i want to 
install wine on ubuntu so that i could run the exe file in ubuntu but the problem
is that i can only access the internet from windows 7. so how can i download the
perfect version of wine for 10.04 and how to install it in ubuntu?
many thanks
pF

If it is a driver it won't work anyway  i had a similar modem so instead of connecting using the usb cable you can use  ethernet cable (if there is a slot in modem but no cable try to buy one)[/SIZE] [SIZE=2]

But you can install wine just download all these pakages and and then copy them to /var/cache/apt/archives/ in ubuntu [/SIZE] [SIZE=2]
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3_1.3.1-0ubuntu1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3_1.3.1-0ubuntu1_i386.deb)[/SIZE] [SIZE=2]

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3-dbg_1.3.1-0ubuntu1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3-dbg_1.3.1-0ubuntu1_i386.deb)[/SIZE]  [SIZE=2]

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3-dev_1.3.1-0ubuntu1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3-dev_1.3.1-0ubuntu1_i386.deb)[/SIZE]  [SIZE=2]

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/g/gnome-exe-thumbnailer/gnome-exe-thumbnailer_0.5-0ubuntu1~lucidppa1_all.deb]("http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/g/gnome-exe-thumbnailer/gnome-exe-thumbnailer_0.5-0ubuntu1%7Elucidppa1_all.deb")[/SIZE]  [SIZE=2]

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/ttf-symbol-replacement_1.2-0ubuntu1~lucidppa1_all.deb]("http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/ttf-symbol-replacement_1.2-0ubuntu1%7Elucidppa1_all.deb")[/SIZE]  [SIZE=2]

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/wine_1.2-0ubuntu1~lucidppa1_all.deb]("http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/wine_1.2-0ubuntu1%7Elucidppa1_all.deb")[/SIZE]  [SIZE=2]
[URL="http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/wine-gecko_1.2-0ubuntu1%7Elucidppa1_all.deb"]
http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/wine-gecko_1.2-0ubuntu1~lucidppa1_all.deb[/URL][/SIZE]  [SIZE=2]

then [/SIZE] [SIZE=2]
[/SIZE] [SIZE=2]Open the Software Sources menu by going to **System->Administration->Software Sources**. Then select the **Other Software** tab and click **Add**.
[/SIZE] [SIZE=2]Then, **copy and paste the line below**.
[/SIZE] [SIZE=2]*ppa:ubuntu-wine/ppa* [/SIZE]

THEN CLICK [THIS LINK ]("apt://wine1.3")

and then if there is any error report back here

but using ethernet is recoomended

---

### Post by cwwilson721 on 2010-09-02
> **lukeiamyourfather said:**
> They're posting here, so they obviously have a connection somewhere.But NOT within Ubuntu, so that method (that I quoted previously) will NOT work.

However, the method by alaukikyo may work (if dependancy hell doesn't rear it's many-fanged-and-drooling head)

---

### Post by Dalo9 on 2010-09-02
thanks[URL="http://ubuntuforums.org/member.php?u=1126040"][COLOR=#000000] alaukikyo 
[/COLOR][/URL]
great pointers.

are you saying that if I download these debs to flash drive, take them home and then copy them to /var/cache/apt/archives/ in ubuntu, I can install wine (with no internet connection)??

bear in mind I have only loaded Ubuntu a week and NEVER worked on Linux before... so wilson can keep his sarcasm to him/herself.

---

### Post by cwwilson721 on 2010-09-02
You misunderstood, [Dalo9]("http://ubuntuforums.org/member.php?u=1141691")

Your post was clear, and difficult to come up with a solution. It was other posters that didn't seem to understand you don't have a 'net connection in Ubuntu, so without copying all those deb files that [[COLOR=#000000]alaukikyo[/COLOR]]("http://ubuntuforums.org/member.php?u=1126040") posted, it would have been nigh impossible (because where would it get the files?). Running Software Center *without* 'net or pre-downloading the files and telling it to install wine won't work.

But with the deb files, it SHOULD work using [[COLOR=#000000]alaukikyo[/COLOR]]("http://ubuntuforums.org/member.php?u=1126040")'s post. Just remember to copy them over with root privileges (or they won't copy)
Try (in a terminal) ```
gksudo nautilus
```to get a root GUI File Manager. (I find this easiest way, myself). Or open a terminal, and cd to where the deb files are, and type```
su cp *.deb [SIZE=2] /var/cache/apt/archives/[/SIZE]
```

If using Software Center doesn't work, you might try Synaptic Package Manager, too. Search for 'wine' in the search box. Hopefully, it will find everything.

Keep us updated. This IS a very interesting thing. Not only might it install wine, but possibly other software, too.

Also, you might want to try posting in the Networking Forum about your modem issue.

And you're doing a GREAT job.

---

### Post by u9q5 on 2011-06-26
This information seems outdated, and the links are non-existent. I am facing the same issues. Are there up-to-date files I can use? I appreciate all attempts to help.


> **alaukikyo said:**
> [SIZE=2]

If it is a driver it won't work anyway  i had a similar modem so instead of connecting using the usb cable you can use  ethernet cable (if there is a slot in modem but no cable try to buy one)[/SIZE] [SIZE=2]

But you can install wine just download all these pakages and and then copy them to /var/cache/apt/archives/ in ubuntu [/SIZE] [SIZE=2]
[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3_1.3.1-0ubuntu1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3_1.3.1-0ubuntu1_i386.deb)[/SIZE] [SIZE=2]

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3-dbg_1.3.1-0ubuntu1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3-dbg_1.3.1-0ubuntu1_i386.deb)[/SIZE]  [SIZE=2]

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3-dev_1.3.1-0ubuntu1_i386.deb](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.3/wine1.3-dev_1.3.1-0ubuntu1_i386.deb)[/SIZE]  [SIZE=2]

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/g/gnome-exe-thumbnailer/gnome-exe-thumbnailer_0.5-0ubuntu1~lucidppa1_all.deb]("http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/g/gnome-exe-thumbnailer/gnome-exe-thumbnailer_0.5-0ubuntu1%7Elucidppa1_all.deb")[/SIZE]  [SIZE=2]

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/ttf-symbol-replacement_1.2-0ubuntu1~lucidppa1_all.deb]("http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/ttf-symbol-replacement_1.2-0ubuntu1%7Elucidppa1_all.deb")[/SIZE]  [SIZE=2]

[http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/wine_1.2-0ubuntu1~lucidppa1_all.deb]("http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/wine_1.2-0ubuntu1%7Elucidppa1_all.deb")[/SIZE]  [SIZE=2]
[URL="http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/wine-gecko_1.2-0ubuntu1%7Elucidppa1_all.deb"]
http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.2/wine-gecko_1.2-0ubuntu1~lucidppa1_all.deb[/URL][/SIZE]  [SIZE=2]

then [/SIZE] [SIZE=2]
[/SIZE] [SIZE=2]Open the Software Sources menu by going to **System->Administration->Software Sources**. Then select the **Other Software** tab and click **Add**.
[/SIZE] [SIZE=2]Then, **copy and paste the line below**.
[/SIZE] [SIZE=2]*ppa:ubuntu-wine/ppa* [/SIZE]

THEN CLICK [THIS LINK ]("apt://wine1.3")

and then if there is any error report back here

but using ethernet is recoomended

---

