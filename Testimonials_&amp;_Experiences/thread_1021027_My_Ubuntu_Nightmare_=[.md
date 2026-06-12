---
title: "My Ubuntu Nightmare =["
date: 2008-12-24
forum: Testimonials &amp; Experiences
---

### Post by Krisando on 2008-12-24
Ok I thought of uploading screen shots but it its much to irritating doing this within Ubuntu.

I have thought of using Ubuntu 3 times all thinking, Hey time for change or windows corrupted so on.. Each time I just gave up for various reasons mainly been totally illogical.

So I installed today I was excited I hadn't been this excited installing an operating system since windows 3.11 =] (Which is very good).

A New background and icons which pop out of the screen when click on hehe :D this is cool, hey maybe Ill install my favorite browser Opera and play Youtube videos. Ok so I download the opera .deb file "Error: Wrong architecture 'i386'"..
Oh ok so compatibility between 32-bit and 64-bit is pretty bad, lets try the 64-bit version.
So I download that and run, I get in big red text "Error: Wrong architecture 'i386'".
=/ Ok then Ill just whatch youtube videos, okay I need flash (goes to download that) for Ubuntu.. "Error: Wrong architecture 'i386'".

Ok so I can't run linux programs maybe Ill just download Wine to run some windows apps.. It requires installing so I read the readme, It made as much sense as "010010 111001 001011" means to most people.

='[ Why does Ubuntu and Unix operating systems as a whole have to be > x10 worse then Vista when it first came out?

Can somebody shed some light on my missery and get me on the right track, my brain has turned to mush.

Thankyou.

---

### Post by damis648 on 2008-12-24
You are trying to install software of the wrong architecture. Post the output of
```
uname -a
```

---

### Post by Skripka on 2008-12-24
> **Krisando said:**
> Ok I thought of uploading screen shots but it its much to irritating doing this within Ubuntu.

I have thought of using Ubuntu 3 times all thinking, Hey time for change or windows corrupted so on.. Each time I just gave up for various reasons mainly been totally illogical.

So I installed today I was excited I hadn't been this excited installing an operating system since windows 3.11 =] (Which is very good).

A New background and icons which pop out of the screen when click on hehe :D this is cool, hey maybe Ill install my favorite browser Opera and play Youtube videos. Ok so I download the opera .deb file "Error: Wrong architecture 'i386'"..
Oh ok so compatibility between 32-bit and 64-bit is pretty bad, lets try the 64-bit version.
So I download that and run, I get in big red text "Error: Wrong architecture 'i386'".
=/ Ok then Ill just whatch youtube videos, okay I need flash (goes to download that) for Ubuntu.. "Error: Wrong architecture 'i386'".

Ok so I can't run linux programs maybe Ill just download Wine to run some windows apps.. It requires installing so I read the readme, It made as much sense as "010010 111001 001011" means to most people.

='[ Why does Ubuntu and Unix operating systems as a whole have to be > x10 worse then Vista when it first came out?

Can somebody shed some light on my missery and get me on the right track, my brain has turned to mush.

Thankyou.

Any NEW way of doing things can be confusing.  Ubuntu is not Windows, for better or worse.


If you installed Ubuntu 32bit  (i386), then you need the i386 debian file from Opera.  If you insalled Ubuntu 64bit (amd64)--then you need the amd64 debian from Opera-luuk under UNIX/X86-64

Same with Flash.  Flash is most easily installed via Synaptic (flashplugin-nonfree), you can install of a debian--but MOST things you'll want are already in Synaptic for easy download/install.

---

### Post by Krisando on 2008-12-24
Do I open up the unix shell command prompt thingy

Ir do I paste this code into some sort of text document? :KS

This will help me also understand these readme's.

---

### Post by Skripka on 2008-12-24
> **Krisando said:**
> Do I open up the unix shell command prompt thingy

Ir do I paste this code into some sort of text document? :KS

This will help me also understand these readme's.

Open up Terminal and type or copy/paste, as damis648, instructed.  It should be somewhere under Applications>Accessories....

---

### Post by Sef on 2008-12-24
>  		Do I open up the unix shell command prompt thingy

Applications > Accessories > Terminal   then type in ```
uname -a
```

---

### Post by damis648 on 2008-12-24
Go to Applications>Accessories>Terminal and paste in that command. By the way, the way of installing software in Ubuntu is different, all the software is available on servers. Go to Applications>Add/Remove or System>Administration>Synaptic Package Manager and search for any software you are looking for.

---

### Post by Krisando on 2008-12-24
Wow guys :D quick responses thankyou.

If you insalled Ubuntu 64bit (amd64)--then you need the amd64 debian from "Linux UB3R 2.6.27-7-generic #1 SMP Fri Oct 24 06:40:41 UTC 2008 x86_64 GNU/Linux"

And to the Opera amd 64 bit version I got the "Dependency is not satisfied" error ;P

Oh boy would using the 32-bit make things slightly easier?

---

### Post by damis648 on 2008-12-24
If you are not doing very intensive tasks such as encoding video or have >4GB of RAM, it might very well make things a bit easier. Just download the 32-bit ISO, burn it, and install it over the 64-bit installation. (Back up your files first!):popcorn:

---

### Post by Krisando on 2008-12-24
I have no files to backup xD
I wiped my hdd since my windows was corrupted and couldn't see dos using plug and play device such as my flash drive ;P

But I actually wiped by mistake, had nothing important.

I won't be doing any encoding of videos as I probably wouldn't be able to get an encoder program working in the first place :P

I have 4gb ram in this laptop.
Hmm okay Ill download 32bit now, Ill have alot of problems I bet.
So in the meantime could someone explain all this gnome, compiling programs, .deb kinda things are :D

And key differences such as where has my recycle bin gone lol do I even have one?

---

### Post by Sef on 2008-12-24
>  And to the Opera amd 64 bit version I got the "Dependency is not satisfied" error ;POpera 64-bit works fine on my system.   What dependency is missing?

---

### Post by Skripka on 2008-12-24
> **Krisando said:**
> I have no files to backup xD
I wiped my hdd since my windows was corrupted and couldn't see dos using plug and play device such as my flash drive ;P

But I actually wiped by mistake, had nothing important.

I won't be doing any encoding of videos as I probably wouldn't be able to get an encoder program working in the first place :P

I have 4gb ram in this laptop.
Hmm okay Ill download 32bit now, Ill have alot of problems I bet.
So in the meantime could someone explain all this gnome, compiling programs, .deb kinda things are :D

And key differences such as where has my recycle bin gone lol do I even have one?

If a dependency is missing, tell us what and we'll tell you how to install it.  There is no reason yet to nuke your system.  64bit is very well supported in Linux-just as well as 32bit.

---

### Post by Krisando on 2008-12-24
Ohh Dependency lets see "libqt3-mt"

(also)Is there a device manager? I may need a driver to get my ethernet cable working?

---

### Post by sintacto on 2008-12-24
did you try
sudo apt-get opera

---

### Post by Krisando on 2008-12-24
krisando@UB3R:~$ sudo apt-get opera
E: Invalid operation opera

=/

---

### Post by theozzlives on 2008-12-24
> **Krisando said:**
> So in the meantime could someone explain all this gnome, compiling programs, .deb kinda things are :D

And key differences such as where has my recycle bin gone lol do I even have one?

GNOME is your Window Manager (the part you see).
Don't worry about compiling programs right now.
A .deb file is kinda like "setup.exe" it's a package that contains a program.
Your "Trash" is in the lower right corner of your screen.

---

### Post by theozzlives on 2008-12-24
> **sintacto said:**
> did you try
sudo apt-get opera

sudo apt-get install opera

---

### Post by jerome1232 on 2008-12-24
Okay you are goiong about this the wrong way. Genarlly software is installed from an online repository than going to individual sites.


Flash (well this will get you java and alot of other goodies too)
```
sudo apt-get install ubuntu-restricted-extras
### or if you just wanted flash
sudo apt-get install flashplugin-nonfree
```

For opera, I think it's easier if you just add their repo, this way opera get's checked for an update everyday when your  system does.

System->Administration->Software Sources, click Third Party Software, click add, copy past the line in code below.
```
deb http://deb.opera.com/opera etch non-free
```
click add source, click close, don't tell it to reload

Now download their gpg key and add it so their software is signed, reload your sources and install opera
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
sudo apt-get update
sudo apt-get install opera
```

---

### Post by Krisando on 2008-12-24
Thankyou for your help wiht the trash can :P I like it.
Oh apt will install dependencies? x] I think

krisando@UB3R:~$ sudo apt-get install opera
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate

Oh boy :S is there a reason Ubuntu doesn't come with these dependencies?

Ill try the 2nd post

Woaaah Seemed like it was working then got this large message not sure if it worked. I kinda clicked reload missread

---

### Post by jerome1232 on 2008-12-24
That's fine you'll just get a warning about their software not being signed, just keep following and you'll stop getting the warning when you update your sources.



just for future reference this is a little how to about repositories [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by Krisando on 2008-12-24
Woah dont ask me what happened I have no clue

/*
krisando@UB3R:~$ wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add -[sudo] password for krisando: --2008-12-25 17:26:01--  [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key)
Resolving deb.opera.com... 
195.189.143.183
Connecting to deb.opera.com|195.189.143.183|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1742 (1.7K) [application/pgp-keys]
Saving to: `STDOUT'

 0% [                                       ] 0           --.-K/s   in 0s      


Cannot write to `-' (Broken pipe).
krisando@UB3R:~$ wget -O - [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key) | sudo apt-key add ---2008-12-25 17:26:13--  [http://deb.opera.com/archive.key](http://deb.opera.com/archive.key)
Resolving deb.opera.com... [sudo] password for krisando: 195.189.143.183
Connecting to deb.opera.com|195.189.143.183|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1742 (1.7K) [application/pgp-keys]
Saving to: `STDOUT'

100%[======================================>] 1,742       --.-K/s   in 0.05s   

2008-12-25 17:26:17 (37.0 KB/s) - `-' saved [1742/1742]
*\
WOOW I CAN INSTALL!!! THANKS
I hope every program is not so complicated to install, thats insane if they expect users to already know that woah :O

---

### Post by jerome1232 on 2008-12-24
Well opera has their own how-to (which sucks btw) but usually adding a repository is very easy. 

You could have actually adding their key via the gui too (under authentication) but they don't list a download on their site in a good format for that so I just gave you command line instructions for the last part.


Winehq has a well put together how to for example: (wine lets you run *some* Windows programs.

[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

I guess the guys at opera just didn't feel like putting together a good how to really. For the most part software is installed via synaptic System->Adminitstation->Synaptic Package manager. Have a look around at the software available.

---

### Post by Krisando on 2008-12-24
I thought since they had a version for Ubuntu Linux it'd work.
So every program I download, I will need to find out how to download there repository woah xD

Ill follow the guide as best I can with Wine, they say it can run windows programs in native language. Does that mean all programs or some wasn't sure. If its native then it could run just as good as windows right?

---

### Post by jerome1232 on 2008-12-24
Oh no you don't have to add individual repositories lol, that would be horrible, I was just linking that as an example of a decent how-to. Those are beta versions and you probably actually don't want them.

If you want something easier to use than synaptic for now then check out add/remove... under Applications, it'll list out most of the gui apps avaible to you in an easy to find manner. It's easier to use but not as powerful as synaptic is.

Actually you already have wine in your list, if you opened synaptic (or add/remove...), clicked in the right hand pane and typed "wine" you'll bring it up and you can mark it for installation.

---

### Post by Krisando on 2008-12-24
WHAAATTT!!! :O THATS WICKED wow a database full of Ubuntu programs :D
Im learning alot =D, I thought that was like windows add/remove very basic but woah!! Im surprised at how much is stored there.

=] Thankyou once again

---

### Post by Krisando on 2008-12-25
Ok it now works :D

---

### Post by Landra on 2008-12-25
I need help, this is my first time using Ubuntu. I have a used Dell Inspiron 8200 with 2ghz 512mb RAM 70g hdd. I am able to play audio CDs (doesn't include burned CDs) but not a DVD movie (including burned DVDs). I receive an error message (for thr CD) that read,"unable to mount local disk,No media in drive". When I try to play a DVD, the message reads,"an error occurred could not open location: you might not have permission to open file". Please help me to utilize my CD-RW/DVD Rom drive.  Ubuntu wasn't pre-installed. The laptop came with Windows XP Home (which I have the license for), looks like the HDD was formatted and Ubuntu was installed. I was able to purchased a burned XP Home CD (since the previous owner lost the original) from a pc/laptop fix it establishment. I am trying to install XP but since the CD drive will does not read the CD, how can I resolve this without purchasing another DVD drive licence? This there a way I can find out if a license was already used/assigned to his laptop? 

I want to run both Ubuntu and XP so I can accomplish what I need to as well as learn more about Ubuntu.

Take me slow, I am a newbie.

---

### Post by Skripka on 2008-12-25
> **Landra said:**
> I need help, this is my first time using Ubuntu. I have a used Dell Inspiron 8200 with 2ghz 512mb RAM 70g hdd. I am able to play audio CDs (doesn't include burned CDs) but not a DVD movie (including burned DVDs). I receive an error message (for thr CD) that read,"unable to mount local disk,No media in drive". When I try to play a DVD, the message reads,"an error occurred could not open location: you might not have permission to open file". Please help me to utilize my CD-RW/DVD Rom drive.  Ubuntu wasn't pre-installed. The laptop came with Windows XP Home (which I have the license for), looks like the HDD was formatted and Ubuntu was installed. I was able to purchased a burned XP Home CD (since the previous owner lost the original) from a pc/laptop fix it establishment. I am trying to install XP but since the CD drive will does not read the CD, how can I resolve this without purchasing another DVD drive licence? This there a way I can find out if a license was already used/assigned to his laptop? 

I want to run both Ubuntu and XP so I can accomplish what I need to as well as learn more about Ubuntu.

Take me slow, I am a newbie.

Have you read and or done the following?

[http://ubuntuguide.org/wiki/Ubuntu:Intrepid#CDs_and_DVDs](http://ubuntuguide.org/wiki/Ubuntu:Intrepid#CDs_and_DVDs)

---

### Post by Landra on 2008-12-25
I haven't tried, wasn't aware of that site, but I will try it.  Thank you, I will let you know if this resolves my problem.

---

### Post by Krisando on 2008-12-25
I managed to dual boot XP, Vista and Ubuntu easily with FreeBCD
And there are codecs in Add/Remove under Applications for playing Dvd's and other media.

Now my Opera does not start it only started just after I installed it :S
another bug?

---

### Post by Landra on 2008-12-26
Re: No media in drive, unable to mount local disk 

Everytime I try any function in Terminal the message reads:
[sudo] password for (username) 

I already tried the password that was used to log into the system but it did not work, is there a separate password that may have been used by the previous owner?  Is there a way to just reformat the HDD and start from scratch? Would that possibly get the CDRW/DVD to work? I just had surgery and this has been an added pain because I am not familiar with it. 
            

:popcorn:

---

### Post by Landra on 2008-12-26
I have a program called Nero on my XP desktop pc, can i use that program to transfer Windows on the laptop running Ubuntu with a file transfer cable or can it be done with a USB flash drive.  Before installing XP I want to wipe the hard drive and install a fresh installation of ubuntu.  My ultimate goal is to still run XP and Ubuntu on the laptop.

---

### Post by Landra on 2008-12-30
Issued resolved under thread "No media in drive, unable to mount local disk"

---

### Post by shagbark on 2009-08-16
> **Krisando said:**
> Woah dont ask me what happened I have no clue
...

WOOW I CAN INSTALL!!! THANKS
I hope every program is not so complicated to install, thats insane if they expect users to already know that woah :O

Reading this thread should help people understand why Linux is never going to go mainstream without some drastic attitude adjustments.  This guy did not know how to open a terminal.

I have been using linux for 14 years. I've installed Linux maybe a dozen times.  It has never taken less than a week.  Every time, there are at least 2 major hangups: The wireless card won't work; the CD drive won't work; the audio won't work; the kernel needs a -noapic argument; I have to read a bunch of READMEs to configure the graphics card or the monitors; whatever.  The Linux install failure rate, by which I mean that the average user would have to give up and install Windows, is still 100%.

Whereas, if you surveyed a thousand Windows users, you would not find a single one for which any of those things failed to work immediately out-of-the-box.

If at ANY POINT during the LIFE OF THE OPERATING SYSTEM, the user has to either open up a terminal and type something in at the prompt, or edit a system file with a text editor, YOU HAVE LOST.  Almost no Windows users have *ever* had to do either of those things.

Linux will never be usable until its developers get that through their heads.

---

### Post by overdrank on 2009-08-16
Ok let is rest in peace. :) thread closed.

---

