---
title: "New to Ubuntu, looking for answers."
date: 2010-11-08
forum: Testimonials &amp; Experiences
---

### Post by Tekno.Statik on 2010-11-08
First hand experience, I love the way Ubuntu 10.10 looks. The reason I wanna leave Windows is because I'm just bored with the way it looks... The problem is that I've been a windows XP user for over 7 years. All the programs I have and everything I use for my company, I manage my website with Dreamweaver and love it, I use Word to make sleek billing receipts for the services which my company offers, I turn files into PDF so that I can be sure that my files are not mangled when my client receives and reciprocates.

Anyways, I tried WINE but it sucks... Mainly I tried to use my favorite MP3 player (through Wine) which is Winamp, but failed... I tried listening to some of my MP3 files but turns out that MP3s are forbidden in Ubuntu, looked for the executable programs list that Wine can run, and it's MOSTLY GAMES, which is what I don't have time for right now. Sure, Minesweeper and Calculator MUST work like they show it in the screenshot, but Ubuntu already has those two -_-.

I just want to know of high-quality equivalents to all the programs I mentioned above... You guys are so passionate about Ubuntu, so I want to hear it from someone who is there and knows what they're talking about. Right now I feel like I just landed on the moon, and you guys show me the landscape that is available for me to play with.

Wine sounded like a great thing, but maybe I over-estimated it's power, and thought I could get away with just the LOOK of Ubuntu, but if Ubuntu is as flexible as it sounds, then there must be some way to make all of it work for me, as well as it does for all of you too. =]


THANKS!

---

### Post by animeshmeher on 2010-11-08
"*I manage my  website with Dreamweaver and love it, I use Word to make sleek billing  receipts for the services which my company offers, I turn files into PDF  so that I can be sure that my files are not mangled when my client  receives and reciprocates*."

1st go to '**Ubuntu Software Center(USC)**" . Its in Application->Ubuntu Software Center.
Install most of the software from there. Unlike windows , all application(95%) can and is installed from USC.
 You can Use **OpenOffice** to replace office suit. (its 95% compatible with Microsoft Office).
You can Also try **IBM Lotus Symphony. **(Have to download **.DEB**(ubuntu format similar to install.exe for windows) file from their site.
There is no grt replacement for **Dreamweaver**, its better if you can install it over wine.
CS2-3 works well under wine.
Converting to PDF is built in functionality and comes with most software(openoffice, Firefox, etc) . OpenOffice has a built in Export-to-PDF function. in Firefox: Just go to print option ->click on print to file->select .pdf extension and print.


"*Mainly I tried to use my favorite  MP3 player (through Wine) which is Winamp, but failed... I tried  listening to some of my MP3 files but turns out that MP3s are forbidden  in Ubuntu, looked for the executable programs list that Wine can run,  and it's MOSTLY GAMES, which is what I don't have time for right now*."

1st Install a pakacage called "**Ubuntu Restricted Extra**', that should take care of all the codec problem . 
For an mp3 Player similar to winamp try "**Audacious**" . For itunes like experience try banshee, the default rythembox is not bad either.
Also install **VLC Player**.

All the software are available in USC.
Importantly , dont give up on Ubuntu so easily. Keep Using it for 6 months.and take my word youll start loving it.

---

### Post by cub on 2010-11-08
As already mentioned Open Office will probably cover your Word work. It should be able to open your template or file directly. You might have to some tweaking because of different fonts and layout, but it should be easily done.

Audicious is what I use as well instead of winamp.

Wine is good for some things but a lot of time I won't get the application to work. I also want to find a native application to replace the Windows one which often is a better solution anyway.

Depending how you use Dreamweaver there are some similar applications. I use Bluefish for all my web work nowadays. Then again, I always hated Dreamweaver's "smart" code it put in all by itself so I always used the text editor only.

---

### Post by coffeecat on 2010-11-08
> **Tekno.Statik said:**
> First hand experience, I love the way Ubuntu 10.10 looks. The reason I wanna leave Windows is because I'm just bored with the way it looks...

If that's what attracted you to Ubuntu, then good, but let's hope that the better security, freedom from viruses, greater flexibility and friendly community of a Linux distro will persuade you to stay.

A few comments.

Installing Ubuntu and then wine to run all your Windows apps is bad strategy. You would be better advised to define your needs and then research what native Linux software would fulfill those needs in Ubuntu. If you can't find the answer, then ask on these forums. We've all trodden and are treading the same path. There are plenty of people willing to help. However, if there are one or two Windows apps that you can't do without and for which you can't find a satisfactory Linux alternative, then wine **might** be an option. It's a bit of a gamble though. In these circumstances some people prefer to run Windows as a virtual guest OS with Ubuntu as the host using something such as VirtualBox. There is a subforum here for virtualisation.

About multimedia:

> **Tekno.Statik said:**
> but turns out that MP3s are forbidden in Ubuntu

Not quite. Licensing issues prevent codecs for mp3 and other restricted formats being included in a default installation of Ubuntu but that is easily dealt with. See here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

As animeshmeher has mentioned, installing the package ubuntu-restricted-extras will give you most of the codecs you need. It will also give you Adobe's flash and an open-source web browser plugin (Iced Tea) for java applets. It will also install the Microsoft core fonts which you will need for serious word-processing work and to ensure fonts on many web pages render correctly.

I also like to install VLC which will play virtually anything. (If you get bored at work, download and install the Windows version of VLC. It's free.)

Also, for playback of commercial DVDs, you need the libdvdcss2 library, either by running the terminal command given in the link above or by getting it from Medibuntu:

[http://medibuntu.org/](http://medibuntu.org/)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Lastly, you meantion PDF files. If the default PDF reader doesn't suit you, and you want Acrobat reader for Ubuntu, go to System > Administration > Synaptic > Settings menu > Repositories > Other Software tab > tick the 'Canonical Partners' box. Close the repositories window and click on the 'Reload' button. You will now be able to find and install the package 'acroread' which is the Linux version of Acrobat reader.

---

### Post by Megaptera on 2010-11-08
My son uses dreamweaver at school but at home on Ubuntu he's found Bluefish to be very similar.

[http://bluefish.openoffice.nl/](http://bluefish.openoffice.nl/)

---

### Post by 3Miro on 2010-11-08
One of the most common mistakes of people migrating from windows to Ubuntu is that they try to run way too many windows programs. Wine and Virtual Box should be the last resort. For anything like web-design, multimedia, browsing, torrents and so on, you should first look at the programs that are native to Linux. There are many threads about people trying to get muTorrent working with wine, when there are Transmission, KTorrent and Deluge all of which give you all the same options, if not more.

Audacious, Rhytmbox and Bluefish are some examples of programs that you can try for your needs. Also, you may want to install Medibuntu for extra media codecs 

[http://medibuntu.org/](http://medibuntu.org/)

If MP3 is all that you care about, installing Ubuntu-restricted-extras is enough.

---

### Post by TBABill on 2010-11-08
Latex may be of interest to you for some slick looking documents. Learning curve involved, but if you are a developer it will probably come quickly. 
 
I play my MP3s with Rhythmbox but you need all the codecs from ubuntu-restricted-extras.

---

### Post by ukripper on 2010-11-08
You can also use MS office 2007 using wine without any problem. [http://www.wine-reviews.net/microsoft/microsoft-office-2007-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/microsoft-office-2007-on-linux-with-wine.html)

---

### Post by fancypiper on 2010-11-08
For a newbie, I recommend the long term support release (10.04) as it is more stable than the "bleeding edge" release.  I choose the LTS release because I host my own web site.  It seems every site that I chose to host my web site tended to suddenly vanish and I lost most of my web site as I depended upon them to stay online, so, unless all my backups on my machine fail, I ain't gonna lose them again!

If you are going to run Linux, then I recommend running native Linux programs rather than running wine.  If you want to run Windows programs, Microsoft does that best (worse??).  You can dual boot as long as you install Windows first, then Linux.

Perhaps one or more of these links may help you out.

[Linux is not Windows](http://linux.oneandoneis2.org/LNW.htm)

[LINUX: Rute User's Tutorial and Exposition](http://rute.2038bug.com/index.html.gz)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[The Windows/Linux Alternative Project](http://www.linuxalt.com/)

[The table of equivalents / replacements / analogs of Windows software in Linux](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

[The Linux Documentation Project](http://tldp.org/)

---

### Post by madmax75 on 2010-11-08
+1 for using Audacious as a replacement for WinAmp. You should feel right at home with that one :)

You can also use Sun Java with Ubuntu. You need to enable the Partner repositories in your Software Sources window (it's in the menus), then update Synaptic and install the sun-java6 stuff. I think you need to uninstall OpenJDK and the IcedTea plugins if you decide to install Sun Java, because they might conflict with each other.

---

### Post by Tamlynmac on 2010-11-08
> Tekno.Statik

I suspect it would help if you posted support question (MP3/pdf) in the help sections, as [this]("http://ubuntuforums.org/showthread.php?t=1343965") isn't a help section of the forums. Perhaps, a simple search of the help sections may have answered your MP3 & pdf issues.

Putting that aside. Ubuntu is not Windows. I would strongly suggest you  invest some time in the learning curve. Statements such as these:

> 
You guys are so passionate about Ubuntu, so I want to hear it from  someone who is there and knows what they're talking about. Right now I  feel like I just landed on the moon, and you guys show me the landscape  that is available for me to play with.

Are IMHO out of place. Member responses that identify FOSS software (you  believe represents HQ in Windows) are subjective. Your asking members  to interrupt what you consider HQ in Windows apps. and challenging them  to identify Linux apps., that "may" meet your expectations. This is  dubious at best.

I would strongly suggest you invest some time in researching the OS on  you own. Perform a personal evaluation and answer questions directly  related to the OS and it's applications - "as they apply to you".  For  example, creating a pdf in OO is accomplished by simply exporting and  saving a file as a pdf. Had you used OO and spent a few minutes  reviewing it.... :-k

Wine is not a substitute for Windows. If your fixated on Windows programs and have expectations of "duplicate"  programs being available in FOSS, or If your have no desire to invest  in the learning curve - then the outcome may already be inevitable.

Use what works for you.
Good Luck

* Just my $0.02 *

---

### Post by Tekno.Statik on 2010-11-08
> **Tamlynmac said:**
> If your have no desire to invest  in the learning curve - then the outcome may already be inevitable.

stfu man, I would not have gone through the trouble of making an account on this forum and posted a SPECIFIED question if I was not interested in learning... GOD people like u anger me.

And what the hell is 'IMHO', 'FOSS', and 'HQ in Windows'? CHALLENGING MEMBERS?? WTF? I came in as friendly as possible!!! And if I don't hear it from people who have specifically gone through the issues that I am getting, and have gained experience and WISH to submit suggestions, then where better from??

I will continue on with my Ubuntu research no thanks to your **miserable** post.

Had you nothing better to say? you should have said nothing at all, thanks for welcoming me, wonderful hospitality you've got yourself there.

*Sigh*

---

### Post by Tekno.Statik on 2010-11-08
> **cub said:**
> As already mentioned Open Office will probably cover your Word work. It should be able to open your template or file directly. You might have to some tweaking because of different fonts and layout, but it should be easily done.

Audicious is what I use as well instead of winamp.

Wine is good for some things but a lot of time I won't get the application to work. I also want to find a native application to replace the Windows one which often is a better solution anyway.

Depending how you use Dreamweaver there are some similar applications. I use Bluefish for all my web work nowadays. Then again, I always hated Dreamweaver's "smart" code it put in all by itself so I always used the text editor only.

Cool, Bluefish sounds nice, and although the "Smart" code was all I used in Dreamweaver (lol) this would be a great chance to get to know the coding of it all down to the <a href=.

Yeah, I downloaded Audacious but all I have in music was MP3's. I'll do as Animeshmeher suggested and get the Ubuntu Restricted Extra package.

Thanks!

---

### Post by Tekno.Statik on 2010-11-08
> **coffeecat said:**
> If that's what attracted you to Ubuntu, then good, but let's hope that the better security, freedom from viruses, greater flexibility and friendly community of a Linux distro will persuade you to stay.
 Yep.

> **coffeecat said:**
> A few comments.

Installing Ubuntu and then wine to run all your Windows apps is bad strategy. You would be better advised to define your needs and then research what native Linux software would fulfill those needs in Ubuntu. If you can't find the answer, then ask on these forums. We've all trodden and are treading the same path. There are plenty of people willing to help. However, if there are one or two Windows apps that you can't do without and for which you can't find a satisfactory Linux alternative, then wine **might** be an option. It's a bit of a gamble though. In these circumstances some people prefer to run Windows as a virtual guest OS with Ubuntu as the host using something such as VirtualBox. There is a subforum here for virtualisation.

Ok, nice.

> **coffeecat said:**
> About multimedia:



Not quite. Licensing issues prevent codecs for mp3 and other restricted formats being included in a default installation of Ubuntu but that is easily dealt with. See here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

As animeshmeher has mentioned, installing the package ubuntu-restricted-extras will give you most of the codecs you need. It will also give you Adobe's flash and an open-source web browser plugin (Iced Tea) for java applets. It will also install the Microsoft core fonts which you will need for serious word-processing work and to ensure fonts on many web pages render correctly.

Impressive! This is the kind of stuff that amazes me about Ubuntu, I thought that it was much less compliant with the modern world as I know it from a windows user. Also, you mentioned fonts, this is truly one aspect I should have revised before seeing how my files looked so crappy on OpenOffice.

> **coffeecat said:**
> I also like to install VLC which will play virtually anything. (If you get bored at work, download and install the Windows version of VLC. It's free.)

Also, for playback of commercial DVDs, you need the libdvdcss2 library, either by running the terminal command given in the link above or by getting it from Medibuntu:

[http://medibuntu.org/](http://medibuntu.org/)
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Lastly, you meantion PDF files. If the default PDF reader doesn't suit you, and you want Acrobat reader for Ubuntu, go to System > Administration > Synaptic > Settings menu > Repositories > Other Software tab > tick the 'Canonical Partners' box. Close the repositories window and click on the 'Reload' button. You will now be able to find and install the package 'acroread' which is the Linux version of Acrobat reader.

Cool =] Thanks for sharing!

---

### Post by marl30 on 2010-11-08
Hey, welcome to forum and to Ubuntu! :) Don't mind the guy who pissed you off. I didn't like the tone of his post either. But anyway, I just thought I would throw in a link to help you get some of the things mentioned by others. Someone gave me this very link to have a look at when I first started out with Ubuntu. It has been very helpful to me. I still follow the blog which the post is from. This blog has really helped in terms of finding a lot of the useful software I now use. 

The post is titled: 10 things to do after installing ubuntu 10.10 Maverick Meerkat: [http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/](http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/)

Hope you find it helpful. :D

---

### Post by Tekno.Statik on 2010-11-08
> **Megaptera said:**
> My son uses dreamweaver at school but at home on Ubuntu he's found Bluefish to be very similar.


[http://bluefish.openoffice.nl/](http://bluefish.openoffice.nl/)

Thanks Mega, I'll give it a try definitely =]

> **3Miro said:**
> One of the most common mistakes of people migrating from windows to Ubuntu is that they try to run way too many windows programs. Wine and Virtual Box should be the last resort. For anything like web-design, multimedia, browsing, torrents and so on, you should first look at the programs that are native to Linux. There are many threads about people trying to get muTorrent working with wine, when there are Transmission, KTorrent and Deluge all of which give you all the same options, if not more.

Audacious, Rhytmbox and Bluefish are some examples of programs that you can try for your needs. Also, you may want to install Medibuntu for extra media codecs 

[http://medibuntu.org/](http://medibuntu.org/)

If MP3 is all that you care about, installing Ubuntu-restricted-extras is enough.

Yeah, Ubuntu Restricted Extras sound sufficient enough now, but thanks! I'll try medibuntu as well if it comes down to it. =]

> **TBABill said:**
> Latex may be of interest to you for some slick looking documents. Learning curve involved, but if you are a developer it will probably come quickly. 
 
I play my MP3s with Rhythmbox but you need all the codecs from ubuntu-restricted-extras.
Not a developer here, but sure! Sounds mighty mighty. lol

> **ukripper said:**
> You can also use MS office 2007 using wine without any problem. [http://www.wine-reviews.net/microsoft/microsoft-office-2007-on-linux-with-wine.html](http://www.wine-reviews.net/microsoft/microsoft-office-2007-on-linux-with-wine.html)
Prequels... hmm... I'll try it as a last source, thanks though! I would have assumed it didn't work at all. And thanx for the link too!

> **fancypiper said:**
> For a newbie, I recommend the long term support release (10.04) as it is more stable than the "bleeding edge" release.  I choose the LTS release because I host my own web site.  It seems every site that I chose to host my web site tended to suddenly vanish and I lost most of my web site as I depended upon them to stay online, so, unless all my backups on my machine fail, I ain't gonna lose them again!

If you are going to run Linux, then I recommend running native Linux programs rather than running wine.  If you want to run Windows programs, Microsoft does that best (worse??).  You can dual boot as long as you install Windows first, then Linux.

Perhaps one or more of these links may help you out.

[Linux is not Windows](http://linux.oneandoneis2.org/LNW.htm)

[LINUX: Rute User's Tutorial and Exposition](http://rute.2038bug.com/index.html.gz)

[How to install ANYTHING in Ubuntu!](http://amitech.50webs.com/installing/index.php.html)

[How To Install Software in Linux](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)

[The Windows/Linux Alternative Project](http://www.linuxalt.com/)

[The table of equivalents / replacements / analogs of Windows software in Linux](http://www.linuxrsp.ru/win-lin-soft/table-eng.html)

[The Linux Documentation Project](http://tldp.org/)

Sure, lol. on my Windows XP I set up all my default programs to non-microsoft, and I love it, which is why I was hoping that there was a way around (Such as wine). But seeing all your comments I'm delighted to learn those Linux-native programs and to get those packages and learn to surf the Ubuntu =]. Maybe some day I might dress up as the Linux penguin for Halloween lol. Nice picture by the way.

> **madmax75 said:**
> +1 for using Audacious as a replacement for WinAmp. You should feel right at home with that one :)

You can also use Sun Java with Ubuntu. You need to enable the Partner repositories in your Software Sources window (it's in the menus), then update Synaptic and install the sun-java6 stuff. I think you need to uninstall OpenJDK and the IcedTea plugins if you decide to install Sun Java, because they might conflict with each other.

Thanks Max!

---

### Post by Tekno.Statik on 2010-11-08
> **marl30 said:**
> Hey, welcome to forum and to Ubuntu! :) Don't mind the guy who pissed you off. I didn't like the tone of his post either. But anyway, I just thought I would throw in a link to help you get some of the things mentioned by others. Someone gave me this very link to have a look at when I first started out with Ubuntu. It has been very helpful to me. I still follow the blog which the post is from. This blog has really helped in terms of finding a lot of the useful software I now use. 

The post is titled: 10 things to do after installing ubuntu 10.10 Maverick Meerkat: [http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/](http://www.omgubuntu.co.uk/2010/10/10-things-to-do-after-installing-ubuntu-10-10-maverick-meerkat/)

Hope you find it helpful. :D

Awesome! lol This is truly an OMG! xD This should totally be a Hyperlink from "Click here if you don't know what you're doing" right after the Ubuntu install!!!! xD

I'm finally getting a hold of Ubuntu 10.10 =] That link which you just gave me should be on a sticky... AUTOMATIC!

---

### Post by Tamlynmac on 2010-11-09
> Tekno.Statik
thanks for welcoming me

Your absolutely correct, I did fail to welcome you to the forums. For this I must truly apologize.

):P "WELCOME TO THE FORUMS" & "GOOD LUCK" ):P

As coffeecat stated:
> You would be better advised to define your needs and then research what  native Linux software would fulfill those needs in Ubuntu. If you can't  find the answer, then ask on these forums.

 * I simply stated my opinion and will not react to you response. Instead, I will unsubscribe to this thread. As I have no desire to debate in this section of the forums (see sectional guidelines).

---

### Post by stalkingwolf on 2010-11-09
as i recall dream weaver does work well in crossoverlinux.

as was mentioned USC has many useful applications, including a PPT and pdf editor.  even a native acrobat reader

---

### Post by Jerry N on 2010-11-10
You might want to try LinuxMint.  LinuxMint is Ubuntu with some of the rough edges smoothed off and most of the needed CODECS already included. It can be a little friendlier to new users.  The current released version is Mint 9, derived from Ubuntu 10.04, and is a Long Term Support version just like 10.04.  

Jerry

---

### Post by julianb on 2010-11-10
> I'm finally getting a hold of Ubuntu 10.10 =] That link which you just gave me should be on a sticky... AUTOMATIC!

Tekno.Static - 

I am an Ubuntu user but I have a suggestion that you can try out (if you want). If you are having difficulty giving up Windows, consider giving up Windows-only *programs* one at a time. Quit using MS Word and use OpenOffice writer instead. If you succeed at that, make a complete shift away from another MS Office program to the OpenOffice alternative. Use an open source web browser, email client, etc etc.

---

### Post by cub on 2010-11-12
> **WayneBrant said:**
> *SNIP*
I don't think this is the right thread for that problem..?

---

### Post by coffeecat on 2010-11-12
> **cub said:**
> I don't think this is the right thread for that problem..?

It's signature spam. I've reported it to the mods. If you see any signature spam - the irrelevant text in the post is a giveaway - you can report it with the report button in the left pane of the post. Like this:  [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]

---

### Post by s.fox on 2010-11-12
> **coffeecat said:**
> It's signature spam. I've reported it to the mods. If you see any signature spam - the irrelevant text in the post is a giveaway - you can report it with the report button in the left pane of the post. Like this:  [IMG]http://ubuntuforums.org/images/buttons/report.gif[/IMG]

Exactly and thank you.

---

### Post by gordintoronto on 2010-11-12
One program which has not been mentioned is cups-pdf. It provides print-to-pdf functionality in every program which can print. My preference is System/Administration/Synaptic to install it.

---

### Post by Swagman on 2010-11-13
> **s.fox said:**
> Exactly and thank you.

Yeah but I think there's been a few times when I've accidentally clicked that button. There was no feedback so I dunno if I did click them !!

---

