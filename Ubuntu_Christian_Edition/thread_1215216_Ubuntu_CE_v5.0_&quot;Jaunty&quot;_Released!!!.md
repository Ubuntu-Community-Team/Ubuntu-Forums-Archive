---
title: "Ubuntu CE v5.0 &quot;Jaunty&quot; Released!!!"
date: 2009-07-16
forum: Ubuntu Christian Edition
---

### Post by mhancoc7 on 2009-07-16
****Great news!! Ubuntu CE is alive again! A huge thanks goes out to [David Kuntadi]("http://ubuntuforums.org/member.php?u=187249") who has taken on the task of developing the debs for the [Dansguardian]("http://dansguardian.org/") GUI, [e-Sword]("http://www.e-sword.net/") Installer, Bible Trivia, [OpenSong]("http://www.opensong.org/"), linBread, etc. He is also keeping our new repository organized and updated. 

The release of Ubuntu CE v5.0 based on Ubuntu 9.04 is now available for download as well as from our repos. This has been a request from the very beginning. We are excited that now standard Ubuntu users cans simply install Ubuntu CE using apt-get or Synaptic. 

[Download Here]("http://ubuntuce.com/download.htm")
[Installation Instructions Here]("http://ubuntuce.com/convert.htm")

This release is a back to basics release and should be considered beta at this point. We are focusing on the functionality for now and will work towards the aesthetics.

The full package list can be found [here]("http://ubuntuce.com/repos/Ubuntu_CE/dpkg/dpkg-l_UbuntuCE_v5.0.txt").

I will continue to be the Project Lead and will be in charge of the iso builds and website. [David Kuntadi]("http://ubuntuforums.org/member.php?u=187249") is now the Development Lead and will be in charge of the deb packages and repos. We will be looking for a person who is willing to take charge of the themes, graphics, and artwork for the next release. If you are interested you can send a note to [email]support@ubuntuce.com[/email].
 
God Bless, Jereme
Project Lead

---

### Post by yaiyuy8W on 2009-07-17
Yea... NTY

---

### Post by newruler on 2009-07-17
Glad to hear, I was sad when I heard it was being discontinued.  Thanks to all who have put forth their efforts to continue this project on further.  Downloading it now to try it out, the graphical dan's guardian configuration works pretty good in church enviroments as well I must say.  No complaints thus far.  (of course using previous release)

---

### Post by beta.tester on 2009-07-17
Superb news to hear you are back and that there will continue to be a Christian version!

---

### Post by Caraibes on 2009-07-17
I want to congratulate the team ! I am glad to see Christian Linuxeros, as one feels a bit lonely from time to time in the FLOSS community ;)

I will install your work from the repos, on my Ubuntu partition.

Those days I am mostly using CentOS 5.3, as it is very stable & reliable, and I noticed the complete lack of any Bible software for RHEL clones...

I am wondering if there's a way to have GnomeSWORD, or BibleTIME backported for EL5...

Anyway, keep on the good works, God bless you all !!!

---

### Post by stevendbrady on 2009-07-17
Glad to see you back!  Ubuntu CE was missed!

---

### Post by IamWayne on 2009-07-17
I will have to say it's about time and God Bless You Jereme!:P:D:D

---

### Post by mhancoc7 on 2009-07-17
> **IamWayne said:**
> I will have to say it's about time and God Bless You Jereme!:P:D:D


I agree! :) It would not have been possible without david_kt.

God Bless, Jereme

---

### Post by stvdel on 2009-07-18
Thanks every one who took time to put out the new version. It is especially nice to know it can be upgraded to Christian Edition from a normal Ubuntu now. God Bless you brothers and sisters.

---

### Post by lisati on 2009-07-18
[SIZE="2"]Congrats to the team.[/SIZE] [SIZE="1"]2 tim 1:7[/SIZE]

---

### Post by WorkingOnWise on 2009-07-18
Is there any work being done on a 64 bit version? The main trunk or Ubuntu is quite stable, I am hoping it is a fairly simple matter to get a 64 bit UCE running....

Thanks for all the great work! I missed UCE and was sad to see it slip away.

---

### Post by jflaker on 2009-07-19
Great news....I was going to acquire a PC or a few from my company for donation to my church...but when the project was stopped, I put those plans aside....now I must see if I could get my own project started!

---

### Post by RevJack on 2009-07-19
What are the chances of a 64-bit version of UbuntuCE becoming available? I have a 64-bit system and am currently running Ubuntu 9.04 (64-bit version).

---

### Post by david_kt on 2009-07-19
> **RevJack said:**
> What are the chances of a 64-bit version of UbuntuCE becoming available? I have a 64-bit system and am currently running Ubuntu 9.04 (64-bit version).

Once we have a production release of 32-bit, I will take a look whether or not I could release 64-bit version.

DK

---

### Post by mhancoc7 on 2009-07-19
> **david_kt said:**
> Once we have a production release of 32-bit, I will take a look whether or not I could release 64-bit version.

DK

That would be really cool. That has been a big request for some time now.

Thanks, Jereme

---

### Post by RevJack on 2009-07-19
> Once we have a production release of 32-bit, I will take a look whether or not I could release 64-bit version.

DK

That would be great!

---

### Post by Caraibes on 2009-07-19
A 64-bit CE would be very nice ! I am right now back to my Ubuntu 64-bit, only to be able to run those fantastic Bible apps... Most of them run just fine under 64-bit... I took them direct from the repos here: 
[http://ubuntuce.com/repos/Ubuntu_CE/binary/](http://ubuntuce.com/repos/Ubuntu_CE/binary/)

---

### Post by david_kt on 2009-07-19
> **Caraibes said:**
> A 64-bit CE would be very nice ! I am right now back to my Ubuntu 64-bit, only to be able to run those fantastic Bible apps... Most of them run just fine under 64-bit... I took them direct from the repos here: 
[http://ubuntuce.com/repos/Ubuntu_CE/binary/](http://ubuntuce.com/repos/Ubuntu_CE/binary/)

Could you tell me which application works under 64-bit? I will take a look at the rest and skip those already work.

DK

---

### Post by hotstepperk on 2009-07-20
Can someone give me the repository so I can download it straight from synaptic. I'd really Like to get it as a theme.

---

### Post by david_kt on 2009-07-20
> **hotstepperk said:**
> Can someone give me the repository so I can download it straight from synaptic. I'd really Like to get it as a theme.

To add the repository, open terminal and :

```
wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/387EE263.gpg -O- | sudo apt-key add - && wget -q http://ubuntuce.com/repos/Ubuntu_CE/apt/crosswire-launchpad-ppa.asc -O- | sudo apt-key add - && sudo wget http://ubuntuce.com/repos/Ubuntu_CE/apt/sources.list.d/jaunty.list -O /etc/apt/sources.list.d/ubuntuce.list; sudo apt-get update
```

If you are using 32 bit, you could run sudo apt-get isntall ubuntu-ce afterward.

DK

---

### Post by Caraibes on 2009-07-20
> **david_kt said:**
> Could you tell me which application works under 64-bit? I will take a look at the rest and skip those already work.

DK
David,

I am happily using Xiphos, e-Sword (from your installer), Dansguardian (although I haven't yet figured out how to set it up...), Today's Bible Verse and Trivia.

Note that I didn't try to install Virtual Rosary as I am Protestant.

I do have a question about e-Sword. When I try to download Bibles (I need Bibles in French & Spanish), nothing happens. I am stuck with the English Bibles that came out of the box...

-How can I add Bibles in French & Spanish in "Wine's" e-Sword ?

-How can I go back to the original "first boot" script that asked me which Bible version I wanted, so I can add more ?

Anyway, David, thank you for your excellent work, I also happily installed it on my kids 32-bit PC... Very good !

God bless you & your family !

---

### Post by Nevon on 2009-07-20
Is there any possibility that I could see what websites are being blocked without actually having to install it?

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> David,

I am happily using Xiphos, e-Sword (from your installer), Dansguardian (although I haven't yet figured out how to set it up...), Today's Bible Verse and Trivia.

Note that I didn't try to install Virtual Rosary as I am Protestant.

I do have a question about e-Sword. When I try to download Bibles (I need Bibles in French & Spanish), nothing happens. I am stuck with the English Bibles that came out of the box...

-How can I add Bibles in French & Spanish in "Wine's" e-Sword ?

-How can I go back to the original "first boot" script that asked me which Bible version I wanted, so I can add more ?

Anyway, David, thank you for your excellent work, I also happily installed it on my kids 32-bit PC... Very good !

God bless you & your family !

The dansguardian gui comes with autoconfiguration. What you have to do is just select/click autoconfiguration, and all is done.

For downloaded e-Sword module, you have to install it using the installer. Run the installer and select manual, it would open a browser to locate your downloaded module. Select it to install.

If you still unable to isntallit, give me the download link and I will add it to the installer.

For xiphos, if you want to isntall more things just go to:
Edit >> Module manager >> Install/Update

By the way, the repos is not available for 64 bit as well. Please see my post here:

[http://ubuntuforums.org/showthread.php?t=1218055](http://ubuntuforums.org/showthread.php?t=1218055)

DK

---

### Post by david_kt on 2009-07-20
> **Nevon said:**
> Is there any possibility that I could see what websites are being blocked without actually having to install it?

Could you elaborate more? Is it about dansguardian?

DK

---

### Post by Nevon on 2009-07-20
> **david_kt said:**
> Could you elaborate more? Is it about dansguardian?

DK

I haven't actually used the distribution, but it said on the website that it was preconfigured to block certain websites. I would like to see a list of the blocked websites. Or perhaps I misunderstood, and it only means that dansguardian comes with the installation - and that you yourself have to pick what websites to block.

---

### Post by Caraibes on 2009-07-20
> **david_kt said:**
> The dansguardian gui comes with autoconfiguration. What you have to do is just select/click autoconfiguration, and all is done.
Then I guess I don't have th GUI...

> **david_kt said:**
> For downloaded e-Sword module, you have to install it using the installer. Run the installer and select manual, it would open a browser to locate your downloaded module. Select it to install.

If you still unable to isntallit, give me the download link and I will add it to the installer.
I just did that... I can indeed add modules available "out of the box" from the "first boot" script. But I tried to install the "French Louis Segond" Bible, from the .exe file that I downloaded, it looked like it worked, but once in e-Sword, it was not available...

Here's the link: [http://www.e-sword.net/bibles.html](http://www.e-sword.net/bibles.html)

David, thanks for your help :)

---

### Post by david_kt on 2009-07-20
> **Nevon said:**
> I haven't actually used the distribution, but it said on the website that it was preconfigured to block certain websites. I would like to see a list of the blocked websites. Or perhaps I misunderstood, and it only means that dansguardian comes with the installation - and that you yourself have to pick what websites to block.

Yes, dansguardian comes preinstalled and what websites are blocked are depend on the filter setting. Dansguardian do not list the website to be block but use certain rules to determine whether or not those website are allowed or not. It is call 'true' content filtering, not just url blocking:


[http://sourceforge.net/docman/display_doc.php?docid=27215&group_id=131757#14](http://sourceforge.net/docman/display_doc.php?docid=27215&group_id=131757#14)
14. Why is DansGuardian called 'true' content filtering?

DansGuardian actually filters the content of web pages and requests by phraselist as well as others. Some commercial web filters call themselves content filters when they are not - they are just glorified URL filters. They are pointless, especially when one has access to the free and brilliant squidGuard. They are lying through their teeth. People who don't realise this waste a lot of money on them. 

But again, that still dependent of filter setting you are going to set.

I hope that would answer your question.

DK

---

### Post by Nevon on 2009-07-20
> **david_kt said:**
> I hope that would answer your question.

DK

I see. What filter settings are available?

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> Then I guess I don't have th GUI...


I just did that... I can indeed add modules available "out of the box" from the "first boot" script. But I tried to install the "French Louis Segond" Bible, from the .exe file that I downloaded, it looked like it worked, but once in e-Sword, it was not available...

Here's the link: [http://www.e-sword.net/bibles.html](http://www.e-sword.net/bibles.html)

David, thanks for your help :)

Download and install it from here:

[http://ubuntuce.com/repos/Ubuntu_CE/binary/dansguardian-gui_1.4_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/binary/dansguardian-gui_1.4_all.deb)

Then you could find it in system >> administration >> dansguardian gui

For French bible, I know you want to install French Louis Segond Bible. But for spanish one, which one you want to install?

Spanish La Biblia de las Américas
Spanish Nueva Biblia Latinoamericana de Hoy
Spanish Reina-Valera 
Spanish Reina Valera Gómez
Spanish Sagradas Escrituras

Do you want to install all 5?

DK

---

### Post by david_kt on 2009-07-20
> **Nevon said:**
> I see. What filter settings are available?

From 50 ( young children) to 160 (young adult). In addition to that, you could also add blacklist and whitelist.

DK

---

### Post by Caraibes on 2009-07-20
> **david_kt said:**
> Download and install it from here:

[http://ubuntuce.com/repos/Ubuntu_CE/binary/dansguardian-gui_1.4_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/binary/dansguardian-gui_1.4_all.deb)

Then you could find it in system >> administration >> dansguardian gui
Not there... I guess it was 32-bit only (I am on 64-bit on my main box...) I'll check on my kids PC (32-bit...)

> **david_kt said:**
> For French bible, I know you want to install French Louis Segond Bible.
-How about all available French translation ? (I guess we also have the French Darby... Maybe more...

> **david_kt said:**
> But for spanish one, which one you want to install?

Spanish La Biblia de las Américas
Spanish Nueva Biblia Latinoamericana de Hoy
Spanish Reina-Valera 
Spanish Reina Valera Gómez
Spanish Sagradas Escrituras

Do you want to install all 5?

DK
Of course ;)  All 5 will be great !

Thanks & God bless !!!

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> Not there... I guess it was 32-bit only (I am on 64-bit on my main box...) I'll check on my kids PC (32-bit...)

-How about all available French translation ? (I guess we also have the French Darby... Maybe more...


Of course ;)  All 5 will be great !

Thanks & God bless !!!

Dansguardian GUI is available for 64 bit as well. You have to install it first.

For e-Sword installer, I will prepare first and update it soon.

DK

---

### Post by Nevon on 2009-07-20
> **david_kt said:**
> From 50 ( young children) to 160 (young adult). In addition to that, you could also add blacklist and whitelist.

DK

Uhm. I don't quite get that point system, or whatever it is. Is there anywhere that I could see the actual rules applied?

---

### Post by david_kt on 2009-07-20
> **Nevon said:**
> Uhm. I don't quite get that point system, or whatever it is. Is there anywhere that I could see the actual rules applied?

If you really want to study, please see here:

[http://dansguardian.org/](http://dansguardian.org/)

But if you just want to use, download the gui, will save you a lot of trouble studying it:

[http://ubuntuce.com/repos/Ubuntu_CE/binary/dansguardian-gui_1.4_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/binary/dansguardian-gui_1.4_all.deb)

DK

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> 
Of course ;)  All 5 will be great !


Please upgrade e-sword-installer, if you install it using repository just run sudo apt-get update && sudo apt-get upgrade.

Otherwise, download it here:

[http://ubuntuce.com/repos/Ubuntu_CE/binary/e-sword-installer_1.4_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/binary/e-sword-installer_1.4_all.deb)

I have added 2 French bibles and 5 Spanish bible. Please try it in case I made some mistakes when typing.

DK

---

### Post by Nevon on 2009-07-20
> **david_kt said:**
> But if you just want to use, download the gui, will save you a lot of trouble studying it:

[http://ubuntuce.com/repos/Ubuntu_CE/binary/dansguardian-gui_1.4_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/binary/dansguardian-gui_1.4_all.deb)

DK

Oh no. I'm very much opposed to censoring. I'm just curious to see what types of websites are being blocked. I thought that Ubuntu CE had its own filter set up, and I wanted to see what they were filtering out.

> **david_kt said:**
> If you really want to study, please see here:

[http://dansguardian.org/](http://dansguardian.org/)

Thank you.

---

### Post by Caraibes on 2009-07-20
> **david_kt said:**
> Please upgrade e-sword-installer, if you install it using repository just run sudo apt-get update && sudo apt-get upgrade.

Otherwise, download it here:

[http://ubuntuce.com/repos/Ubuntu_CE/binary/e-sword-installer_1.4_all.deb](http://ubuntuce.com/repos/Ubuntu_CE/binary/e-sword-installer_1.4_all.deb)

I have added 2 French bibles and 5 Spanish bible. Please try it in case I made some mistakes when typing.

DK
David, it works great, thanks a lot ! Good job !!!

---

### Post by Caraibes on 2009-07-20
> **david_kt said:**
> Then you could find it in system >> administration >> dansguardian gui
I just found it, thank you... I was mistaken, because searching for "Dansguardian", but it is called "Parental control"
I will set it up for my kids PC, and leave it running on mine, to check if it doesn't interfere with my browsing (I don't visit XXX sites anymore, I am cured from that addiction now, thanks God :)  )

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> I just found it, thank you... I was mistaken, because searching for "Dansguardian", but it is called "Parental control"


The "Parental control" is not the one I make, may be it is another package. The one I make called "dansguardian gui".

DK

---

### Post by Caraibes on 2009-07-20
> **david_kt said:**
> The "Parental control" is not the one I make, may be it is another package. The one I make called "dansguardian gui".

DK
The one I have is called "Configure Parental Controls", with a littlew yellow icon, like a street sign of kids crossing the street in front of a scool...

I don't see any Dansguardian-gui package, in spite of having it installed...

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> The one I have is called "Configure Parental Controls", with a littlew yellow icon, like a street sign of kids crossing the street in front of a scool...

I don't see any Dansguardian-gui package, in spite of having it installed...

Look at:

System >> Administration

and NOT

Applications >> System Tools.

You could also try to open terminal and run:

dansguardian_gui

DK

---

### Post by Caraibes on 2009-07-20
> **david_kt said:**
> Look at:

System >> Administration

and NOT

Applications >> System Tools.

You could also try to open terminal and run:

dansguardian_gui

DK
David, I confirm I did just that... I just re-checked...

---

### Post by Caraibes on 2009-07-20
David, it seems to me that the above mentionned "Configure Parental Controls" is indeed the Dansguardian-GUI... It seems to be working very well. I will give you feedback as time goes by, to see if it disturbs my regular browsing... I used the "autoconfigure" option, as I never used any such app before...

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> David, it seems to me that the above mentionned "Configure Parental Controls" is indeed the Dansguardian-GUI... It seems to be working very well. I will give you feedback as time goes by, to see if it disturbs my regular browsing... I used the "autoconfigure" option, as I never used any such app before...

What a relief .... at least it appears in the menu. Please do let me know if you face any difficulties in using dansguardian gui.

DK

---

### Post by Caraibes on 2009-07-20
-Is there a Dansguardian (or similar free/opensource app) for Windows ???

That might prove to be useful around me...

;)

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> -Is there a Dansguardian (or similar free/opensource app) for Windows ???

That might prove to be useful around me...

;)

I do not know such thing yet. But what you have to do is to buy additional network card and put it on the linux box so as your box running dansguardian have 2 network cards. And then you could make it as router, I could give you some instruction to do that.

Edit: I have not tried it yet, but it is possible to do so. So we will learn together to do that.
DK

---

### Post by Caraibes on 2009-07-20
> **david_kt said:**
> For French bible, I know you want to install French Louis Segond Bible. But for Spanish one, which one you want to install?

Spanish La Biblia de las Américas
Spanish Nueva Biblia Latinoamericana de Hoy
Spanish Reina-Valera 
Spanish Reina Valera Gómez
Spanish Sagradas Escrituras
David, the 2 French Bibles are running just fine... But only 2 of the Spanish ones are running (Nueva Biblia Latinoamericana de Hoy & La Biblia de las Américas).

There is an install error with Spanish Reina-Valera, Spanish Reina Valera Gómez, Spanish Sagradas Escrituras...

Just letting you know, for feedback purposes...

---

### Post by k_chupe on 2009-07-20
Ubuntu CE  is much appreciated and I'm glad that it's up and running again. currently been using Living Water OS(puppy) on my old laptop because of the resource constrictions and it works great. My HP will definitely be getting a Ubuntu CE make-over. Thanks you guys! 
                  In Christ,
                             Kevin

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> David, the 2 French Bibles are running just fine... But only 2 of the Spanish ones are running (Nueva Biblia Latinoamericana de Hoy & La Biblia de las Américas).

There is an install error with Spanish Reina-Valera, Spanish Reina Valera Gómez, Spanish Sagradas Escrituras...

Just letting you know, for feedback purposes...

What is the error? I have just tried here, all three install and displayed correctly in e-Sword.

DK

---

### Post by Caraibes on 2009-07-20
Here's the error message... But I am wondering if I have to re-install everything each time I want to add something from the installer...
[IMG]http://lh4.ggpht.com/_h1yrMDj7Ks8/SmUCrs7cVXI/AAAAAAAAAmE/N2P4V6FpvYY/s720/Capture.jpg[/IMG]

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> Here's the error message... But I am wondering if I have to re-install everything each time I want to add something from the installer...


Nope, you just need to tick the additional bible. The ones you have installed do not need to be re-install.

Your problem looks like unsuccessful download, what you have to do is launch the installer, choose "clear_cache".

After that run the installer again, choose the three bibles you want to install.

DK

---

### Post by Caraibes on 2009-07-20
No such luck:
```
/home/martin/.themes/HumanBlueMod/gtk-2.0/gtkrc:312: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Executing env WINEPREFIX=/home/martin/.wine_Esword wine /home/martin/.wineeswordcache/srv.exe
wine: could not load L"Z:\\home\\martin\\.wineeswordcache\\srv.exe": Mauvais format EXE pour 
Note: command 'env WINEPREFIX=/home/martin/.wine_Esword wine /home/martin/.wineeswordcache/srv.exe' returned status 193.  Aborting.

```

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> No such luck:
```
/home/martin/.themes/HumanBlueMod/gtk-2.0/gtkrc:312: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
Executing env WINEPREFIX=/home/martin/.wine_Esword wine /home/martin/.wineeswordcache/srv.exe
wine: could not load L"Z:\\home\\martin\\.wineeswordcache\\srv.exe": Mauvais format EXE pour 
Note: command 'env WINEPREFIX=/home/martin/.wine_Esword wine /home/martin/.wineeswordcache/srv.exe' returned status 193.  Aborting.

```

Could you open terminal and try:

```
rm /home/martin/.wineeswordcache/srv.exe
```

What is the result?

DK

---

### Post by Caraibes on 2009-07-20
```
martin@spc1:~$ rm /home/martin/.wineeswordcache/srv.exe
rm: ne peut enlever `/home/martin/.wineeswordcache/srv.exe': Aucun fichier ou dossier de ce type

```
That means there are no such file...

---

### Post by david_kt on 2009-07-20
> **Caraibes said:**
> ```
martin@spc1:~$ rm /home/martin/.wineeswordcache/srv.exe
rm: ne peut enlever `/home/martin/.wineeswordcache/srv.exe': Aucun fichier ou dossier de ce type

```
That means there are no such file...

Not sure what happen, open terminal and try this:
```

cd /home/martin/.wineeswordcache
wget http://www.e-sword.net/files/bibles/srv.exe
```

What is the result?

DK

---

### Post by Caraibes on 2009-07-21
When I do the above trick, and then install SRV from the "manual" option of the installer, I am getting the same error. 

-What is the way to delete everything & cache and then install everything again from scratch ?

---

### Post by david_kt on 2009-07-21
> **Caraibes said:**
> When I do the above trick, and then install SRV from the "manual" option of the installer, I am getting the same error. 

-What is the way to delete everything & cache and then install everything again from scratch ?

But what is the result of:

```
cd /home/martin/.wineeswordcache
wget http://www.e-sword.net/files/bibles/srv.exe
```

If you are sure that the above command executed successfully, then continue with:

```
env WINEPREFIX=/home/martin/.wine_Esword wine /home/martin/.wineeswordcache/srv.exe
```

DK

---

### Post by Caraibes on 2009-07-21
[HTML]martin@spc1:~$ cd /home/martin/.wineeswordcache
martin@spc1:~/.wineeswordcache$ wget http://www.e-sword.net/files/bibles/srv.exe
--2009-07-21 06:06:18--  http://www.e-sword.net/files/bibles/srv.exe
Résolution de www.e-sword.net... 208.67.58.170
Connexion vers www.e-sword.net|208.67.58.170|:80... connecté.
requête HTTP transmise, en attente de la réponse... 200 OK
Longueur: non spécifié [text/html]
Saving to: `srv.exe.1'

    [ <=>                                   ] 2 542       --.-K/s   in 0s      

2009-07-21 06:06:19 (9,17 MB/s) - « srv.exe.1 » sauvegardé [2542]

martin@spc1:~/.wineeswordcache$ 
[/HTML]

[HTML]martin@spc1:~/.wineeswordcache$ env WINEPREFIX=/home/martin/.wine_Esword wine /home/martin/.wineeswordcache/srv.exe
wine: could not load L"Z:\\home\\martin\\.wineeswordcache\\srv.exe": Mauvais format EXE pour 
martin@spc1:~/.wineeswordcache$ 
[/HTML]

---

### Post by david_kt on 2009-07-21
> **Caraibes said:**
> [HTML]martin@spc1:~$ cd /home/martin/.wineeswordcache
martin@spc1:~/.wineeswordcache$ wget http://www.e-sword.net/files/bibles/srv.exe
--2009-07-21 06:06:18--  http://www.e-sword.net/files/bibles/srv.exe
Résolution de www.e-sword.net... 208.67.58.170
Connexion vers www.e-sword.net|208.67.58.170|:80... connecté.
requête HTTP transmise, en attente de la réponse... 200 OK
Longueur: non spécifié [text/html]
Saving to: `srv.exe.1'

    [ <=>                                   ] 2 542       --.-K/s   in 0s      

2009-07-21 06:06:19 (9,17 MB/s) - « srv.exe.1 » sauvegardé [2542]

martin@spc1:~/.wineeswordcache$ 
[/HTML]

[HTML]martin@spc1:~/.wineeswordcache$ env WINEPREFIX=/home/martin/.wine_Esword wine /home/martin/.wineeswordcache/srv.exe
wine: could not load L"Z:\\home\\martin\\.wineeswordcache\\srv.exe": Mauvais format EXE pour 
martin@spc1:~/.wineeswordcache$ 
[/HTML]

Looks like there is srv.exe still available there so that the wget change the name ti srv.exe.1.

What you have to do is to delete srv.exe. Or you could try
```
 mv /home/martin/.wineeswordcache/srv.exe.1 /home/martin/.wineeswordcache/srv.exe
```

And then:
```
env WINEPREFIX=/home/martin/.wine_Esword wine /home/martin/.wineeswordcache/srv.exe
```

DK

---

### Post by Caraibes on 2009-07-21
```
martin@spc1:~$  mv /home/martin/.wineeswordcache/srv.exe.1 /home/martin/.wineeswordcache/srv.exe
martin@spc1:~$ env WINEPREFIX=/home/martin/.wine_Esword wine /home/martin/.wineeswordcache/srv.exe
wine: could not load L"Z:\\home\\martin\\.wineeswordcache\\srv.exe": Mauvais format EXE pour 
martin@spc1:~$ 

```

---

### Post by david_kt on 2009-07-21
> **Caraibes said:**
> ```
martin@spc1:~$  mv /home/martin/.wineeswordcache/srv.exe.1 /home/martin/.wineeswordcache/srv.exe
martin@spc1:~$ env WINEPREFIX=/home/martin/.wine_Esword wine /home/martin/.wineeswordcache/srv.exe
wine: could not load L"Z:\\home\\martin\\.wineeswordcache\\srv.exe": Mauvais format EXE pour 
martin@spc1:~$ 

```

Let's try this:

```
rm -rf /home/martin/.wineeswordcache/
ls /home/martin/.wineeswordcache/
```

What is the output?

DK

---

### Post by Caraibes on 2009-07-21
```
martin@spc1:~$ rm -rf /home/martin/.wineeswordcache/
martin@spc1:~$ ls /home/martin/.wineeswordcache/
ls: ne peut accéder /home/martin/.wineeswordcache/: Aucun fichier ou dossier de ce type
martin@spc1:~$ 

```
That means can't access ... No such file or folder.

---

### Post by david_kt on 2009-07-21
> **Caraibes said:**
> 
That means can't access ... No such file or folder.

Very good, now try e-sword-installer again, to install the remaining Spanish bibles, it should be ok of your internet connection AND e-sword server are ok.

DK

---

### Post by Caraibes on 2009-07-21
David, I am sorry to monopolize this thread with this issue... Feel free to ask the moderator to move them to a new thread...

That said, it just gives me the very same error message... (thank you for your patience)

---

### Post by david_kt on 2009-07-21
> **Caraibes said:**
> David, I am sorry to monopolize this thread with this issue... Feel free to ask the moderator to move them to a new thread...

That said, it just gives me the very same error message... (thank you for your patience)

Could you check:

```
ls /home/martin/.wineeswordcache/
```

What is the output?

Is dansguardian on? If yes you should stop it first using dansguardian gui. After that try again:


```
rm -rf /home/martin/.wineeswordcache/
ls /home/martin/.wineeswordcache/
```

Make sure it said could not find file or folder, and then launch e-sword-installer.

By the way, why don't you try to install other Spanish bibles first, skipping srv.

DK

---

### Post by Caraibes on 2009-07-21
David, I just stopped Dansguardian, and it looks like the install is working... You nailed it ;)

I hope this whole issue might help other users... 

Dansguardian prevented the install....

---

### Post by gking-vt on 2009-07-21
I'm glad this is available Thanks for all the hard work :popcorn:

---

### Post by bornagainpenguin on 2009-07-21
> **Caraibes said:**
> -Is there a Dansguardian (or similar free/opensource app) for Windows ???

Try [Bluecoat K9](http://www1.k9webprotection.com/) which is free for home use and seems to work on similar principles to Dan's Guardian.

--bornagainpenguin

---

### Post by david_kt on 2009-07-22
> **david_kt said:**
> But what you have to do is to buy additional network card and put it on the linux box so as your box running dansguardian have 2 network cards. And then you could make it as router, I could give you some instruction to do that.

Edit: I have not tried it yet, but it is possible to do so. So we will learn together to do that.
DK

Good News!!!! I have just confirmed, with additional network card you could filter other computers and the lan using ubuntu CE. May be I will add this feature for karmic koala.

What I have in mind is to make ubuntu ce able to share internet connection similar to windows xp, and on top of that the internet connection would be filtered using dansguardian.

But looks like I have to drop firehol and make a custom firewall instead.

DK

---

### Post by mhancoc7 on 2009-07-22
> **david_kt said:**
> Good News!!!! I have just confirmed, with additional network card you could filter other computers and the lan using ubuntu CE. May be I will add this feature for karmic koala.

What I have in mind is to make ubuntu ce able to share internet connection similar to windows xp, and on top of that the internet connection would be filtered using dansguardian.

But looks like I have to drop firehol and make a custom firewall instead.

DK

That is really cool. If you can put together some easy to follow instructions then I would love to add it to the website.

Thanks, Jereme

---

### Post by david_kt on 2009-07-22
> **mhancoc7 said:**
> That is really cool. If you can put together some easy to follow instructions then I would love to add it to the website.

Thanks, Jereme

I guess it would a little difficult as the procedure is a little bit long and it could make the system not functioning well if there is a mistake. So, I prefer to make a script so that people would just need to launch the script and click and ...... VIOLA you share your internet connection with dhcp-server (the client computer get everything automatically) and filtered!!

DK

---

### Post by mhancoc7 on 2009-07-22
> **david_kt said:**
> I guess it would a little difficult as the procedure is a little bit long and it could make the system not functioning well if there is a mistake. So, I prefer to make a script so that people would just need to launch the script and click and ...... VIOLA you share your internet connection with dhcp-server (the client computer get everything automatically) and filtered!!

DK

Yes that would be even cooler! 

Jereme

---

### Post by david_kt on 2009-07-22
> **mhancoc7 said:**
> Yes that would be even cooler! 

Jereme

Let me share a little bit about the steps, and may be you would agree it should be automated:

1. Remove firehol, as I am not sure what setting it does and how to configure it correctly to share internet connection. It does not mean firehol is bad, it is just I have not studied it carefully yet.

2. Create transparent proxy using iptables for the host (port redirect). This is to replace firehol function.

3. Share transparent proxy to LAN, again, using iptables. This would include forwarding traffic, port redirect, and masquerading.

4. Capture WAN's DNS and gateway to share it to LAN

5. Install and Configure dhcp to provide LAN with automatic IP address, DNS and Gateway.

DK

---

### Post by mhancoc7 on 2009-07-22
> **david_kt said:**
> Let me share a little bit about the steps, and may be you would agree it should be automated:

1. Remove firehol, as I am not sure what setting it does and how to configure it correctly to share internet connection. It does not mean firehol is bad, it is just I have not studied it carefully yet.

2. Create transparent proxy using iptables for the host (port redirect). This is to replace firehol function.

3. Share transparent proxy to LAN, again, using iptables. This would include forwarding traffic, port redirect, and masquerading.

4. Capture WAN's DNS and gateway to share it to LAN

5. Install and Configure dhcp to provide LAN with automatic IP address, DNS and Gateway.

DK

I think it would be great if we could automate this process for people. I think that could really help a lot of people.

Again, you ROCK!

Jereme

---

### Post by jan-12 on 2009-07-23
Thanks for getting this package back into the game.  Your having worked out a deb package is even better so no re-install needed! I simply had to move from 8.04 and 9.04 is really going to be much better with this deb.  Much appreciated!

---

### Post by jan-12 on 2009-07-29
I have installed the deb package and it works great!  I also installed the whole iso in a friend's pc and he is very happy.  One suggestion in case this can be implemented down the road:  Would it be possible to make the access to the parental control via root and not with user A, B or C?

---

### Post by david_kt on 2009-07-29
> **jan-12 said:**
> I have installed the deb package and it works great!  I also installed the whole iso in a friend's pc and he is very happy.  One suggestion in case this can be implemented down the road:  Would it be possible to make the access to the parental control via root and not with user A, B or C?

Presently, what you have to do is remove the administration right for user A,B and C.

system>administration>users and group

click unlock and type password.
select user A and click properties
click user privileges and un-check "administer the system"

Repeat for user B and C
DK

---

### Post by shane2peru on 2009-07-29
> **david_kt said:**
> Presently, what you have to do is remove the administration right for user A,B and C.

system>administration>users and group

click unlock and type password.
select user A and click properties
click user privileges and un-check "administer the system"

Repeat for user B and C
DK

I think you would want to leave one root user, otherwise you could end up with a sticky mess. :)  So leave user D as root.

Shane

---

### Post by david_kt on 2009-07-30
> **shane2peru said:**
> I think you would want to leave one root user, otherwise you could end up with a sticky mess. :)  So leave user D as root.

Shane

I forgot there is no root user actually, so, you are right have to have at least one user to have admin right.

DK

---

### Post by shane2peru on 2009-07-30
> **david_kt said:**
> I forgot there is no root user actually, so, you are right have to have at least one user to have admin right.

DK

One can be setup, but I've never done it.  I wonder if it would let you remove all admin users or not.  I would hope they have something in place to prevent that.  It would be very interesting to see that happen, the system would be permanently locked.

Shane

---

### Post by david_kt on 2009-07-30
> **shane2peru said:**
> One can be setup, but I've never done it.  I wonder if it would let you remove all admin users or not.  I would hope they have something in place to prevent that.  It would be very interesting to see that happen, the system would be permanently locked.

Shane
I ever experienced that in dapper, not sure for jaunty. But in dapper, it was easy to recover as recovery mode would  auto login to root without password.

DK

---

### Post by jpcjr on 2009-08-03
Finally, The CE edition was greatly missed.

---

### Post by jan-12 on 2009-08-04
Thanks for the workaround, david_kt, and thanks for the warning shane2peru. Surely important not to get locked out.


> **david_kt said:**
> I ever experienced that in dapper, not sure for jaunty. But in dapper, it was easy to recover as recovery mode would  auto login to root without password.

DK

---

