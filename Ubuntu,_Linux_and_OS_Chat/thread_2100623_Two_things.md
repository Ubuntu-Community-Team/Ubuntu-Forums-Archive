---
title: "Two things"
date: 2013-01-02
forum: Ubuntu, Linux and OS Chat
---

### Post by Gazucha on 2013-01-02
First,

 why oh why do Linux not have an easy App-install set-up such as download said .tgz.... extract .tgz to App/Program folder... et Voila!!!


 WHY? 

 Why must I waste another 2 days of my precious life trying to install (what has become) a multitude of programmes, NONE of which have been installed btw. 
 
 Where should I download the files to?
 Where should I unpack the files to?
 How do I navigate to which folder?
 Do I need sudo command?
 Do I need to be Root?
 Etcetera, etcetera, etcetera.......

 Why are Linux FORCING me to use <snip> WINDOWS????????

 All I want is a program (not installed) that generates a Square Wave that I can view in Xoscope (installed).

 How difficult should that be??

 Why am I -once again- feeling like smashing my computer and am generally thoroughly pissed off? Thanks for that.

 Why do the Linux Admin do this to people?

 The following excerpt is an example of the 'BASIC' app install instructions. Herein is the single clearest reason that unless Linux HELPS Joe Public (who are time-restricted and not Computer components), that Linux shall never evolve past the Geek and Tech world. 
 Maybe that's cool for Linux snobs but what an incredible and ironic shame that Linux FORCE people to use Widows!!!!

Anyway here's the 'Basic' instructions......

[I][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**INSTALLATION          FROM A SOURCE-CODE TARBALL** 
        [B]
        o[/B] If what I downloaded from the net is a Linux source code in the          form of a compressed tarball (*.tar.gz or *.tgz), the installation procedure          is longer and more troublesome than with the binary-only rpm. I typically          install the program as root.[/SIZE][/FONT]       [FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**First**,        I change my current working directory to /usr/local  :
      
      cd /usr/local 
      [B]
      Second[/B], I decompress the tarball that I downloaded from the net: 
      
      tar -xvzf /home/the_dir_where_the_tarball_is/my_tarball.tar.gz        
      
      This extracts (option "x") the contents of the *.tar.gz (or *.tgz) tarball,        unzips it (option "z"), while talking to me more than usual (option "v"        = verbose).  Please note that the option "f" means "file", so the filename        must immediately follow the letter "f".  The contents of the tarball        are extracted into a subdirectory which tar creates under my current        working directory, which in the typical case is /usr/local/ .         The tarball knows what the new subdirectory should be called. 
      
      If the tarball is not compressed (e.g., *.tar), I may use: 
      
      tar -xvf /home/the_dir_where_the_tarball_is/my_tarball.tar 
      
      **Third**, I have to figure how the new directory is called, then I cd        into it: 
      
      dir 
      cd the_new_program_subdir 
      
      Since some of the directories have long names, I use the great autocompletion        option to save on typing--I just type the first few letters and then press         . 
      
      **Fourth**, most programs are compiled by executing these three commands:        
      
      ./configure 
      make 
      make install 
      
      The above commands can take some time to complete (1 min? 0.5 h?). If any        of them fail, it might be an idea to read the README or INSTALL or whatever        info is provided with the new program. Some programs may require customization        of the environment (e.g. definition of their path) or installation of an        additional library, or yet something else. It can sometimes be a pain. Very        simple programs might not need the "./configure" or/and "make install" step,        in which case "make" alone will do. 
      
      **Fifth**, if everything goes well, I find the new executable which I        just compiled. The names of executables display in green when running this        command: 
      
      ls --color 
      
      Now, I can run the executable, for example: 
      
      ./the_executable 
      
      Some programs automatically install the executable to /usr/local/bin, so        I may want to try: [/SIZE][/FONT][/I]        *[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]/usr/local/bin/the_executable          [/SIZE][/FONT]*
       *[FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]**Sixth**,          if I plan to run the program more often, I create a symbolic link to the          executable from the directory /usr/local/bin :[/SIZE][/FONT]*
       [I][FONT=Verdana, Arial, Helvetica, sans-serif][SIZE=2]cd /usr/local/bin        
      ln -s /usr/local/the_new_program_subdir/the_executable . 
      
      This way, the executable (actually, a symbolic link to it) is on my PATH        and it can be run by simply typing its name (no need to type the full path        to the executable any more). Some programs will install the executable (or        a link to it) in a "bin" directory in which case you skip the last step.        [/SIZE][/FONT][/I]

..... Basically incomprehensible ??????????????????????????




So, I have an idea, 

Why don't you just write Linux instructions in the secret Klagarian code of the Universal and multi-dimensional, Great White Brotherhood?

 I shall now turn this computer off and leave the house before I put my fist through it's screen (again).

 Happy New Year!! :confused:

---

### Post by haqking on 2013-01-02
contact the developer if you dont like the way something is installed, it is nothing to do with anyone other than them

---

### Post by cariboo on 2013-01-02
What type of applications are you using, that you feel the need to download the source and compile it, can't you find what you need in the repositories?

---

### Post by Sarcastic Cows on 2013-01-25
Is there no option to try an apt-get install method?

You don't get things in life easy if you want them to be good ;) 

Nothing comes easy. I think there are ways to install different files using the terminal

---

### Post by Bucky Ball on 2013-01-25
Whilst I understand your frustration, please be aware of this from the Code of Conduct:

> **Profanity:** We have users of all age groups and of all tolerance  levels where profanity is concerned. A language filter is in place to  catch most major forms of profanity that may accidentally be used. Do  not attempt to circumvent the language filter by using variations or  slight misspellings of profanities.

Thanks.

---

### Post by Gazucha on 2013-06-10
Hi Bucky Ball...

 no probs, got slightly carried away... 

 Gave up on the Oscilloscope idea and just read the duty cycle through a reliable tester. Just a shame really. Linux is great but I am not joking when I say that I have given MONTHS of my life trying to resolve software problems. I am still on my current Boot-problem for the better part of the last year!

 It is extremely difficult to learn a new language (DOS)  when you don't have any idea of the how the foundations lie.
 How many thousands of commands have I typed in and still have NO idea why or when to use Sudo, nor where Programs are even installed to? (as in Mac Applications or MS Program Files).

 I could go on and on...

---

### Post by Bashing-om on 2013-06-10
Oh [COLOR=#000000]Gazucha; Hi !

Let me get my feet wet on this one... see if I can give direction to your perspective on "open source", ubuntu in particular.

The heart of this "movement" is the kernel, upon which everything else is applied onto. It had it's birth in the early 60's and since that time thousands of programmers in each generation have poured over this code, ever evolving this code to meet the desired applications. Anyone is allowed and expected to modify and/or enhance this code base to meet their needs and a number of systems have developed to meet the need of integration/enhancements for this code. -> one of which is the package management "system" and it is a system...fully integrated within any distribution installation.
 
Package management as a system is wonderful...there is at least 35 thousand "applications" made available, that thousands of people have done the work to make them available and tested to insure full compatibility with your chosen operating system and distribution. All available with the ease of -in the GUI, a click of a button, in terminal, "sudo apt-get install- and done !OK, so you need an application outside of the mainstream, some brilliant programmer has done the work, but his work has not to this time made it through the process to be accepted into the standard repositories ---The question now is how much work do you have to do to get his wonderful code to run on your particular machine ? It is indeed a rarity than one MUST compile from source - this is open source and that method can always be employed - but, what options has that programmer, and those supporting that program, made available to others to "install" this beautiful bit of coding ? Most often the program/application is available in the form of a "tar ball" or some other form of compression. In this instance some one has written the directions down for you ..the "readme file", after uncompression has been done.Or, maybe this brilliant programmer has gone 3 steps farther and made his work available through the package management system as his own Personal Package Archive ? Again it is but a matter of a few button clicks ...and done. The point here is that if one steps out from underneath the umbrella of the accepted software repositories, you have the work to do to attain your particular goal.... but it can be done... when all else fails, and it is that important to you.... write your own code for the benefit of all --- open source !

Comprehension and understanding this "operating system"; in it's complexity no one knows everything, but a lot can be known about somethings. Many people with great knowledge about a particular "something" make the contribution to the whole that is the operating system you have before you. In it's simplest terms -> the kernel gets loaded - the heart of the system, all else is appended in a modular fashion to this kernel that interacts and controls everything. Say a word processor, you interact with the word processor, the application interacts with the kernel to insure what you desire of the application gets done. What you ask is the means of your interaction with this kernel ? Why, the Command Line Interface ! And once more, no one knows all the commands available to interact with the kernel -literally thousands - systems are inplace to help you in the interaction ...most notable is the manual ---->man <command_name>. and the tools available within the manual system.
As said before, generations of coders to make the system you have before you... a constantly evolving system.... evolving, what was pertinent at some point in the past, may no longer be pertinent... things change and one has to keep up with how to interact with any particular.

You are correct in that one has to have a foundation to base comprehension on. The great thing about this movement is documentation is available. One has but to search and read...but read with discretion and discernment ...what does it apply to and why? ...what has changed in the operating system since the documentation was written ??? Many Many things change ...it is an evolving system. What was "then" might not even exist "now".

Millions of people have this operating system as their system of choice, there must be a solid reason for such popularity .... bottom line ...it works ! But to get beyond the point and click stage, one has to work too !
[/COLOR][INDENT=2][COLOR=#000000]
Just my opinion, open to debate

[/COLOR][/INDENT]

---

### Post by Bucky Ball on 2013-06-10
Change perspective. If you come at Linux with an MS mindset you won't get far. Clear your head and start again. You can never make Linux squeeze into a Windows/Mac-centric frame. If you don't know why you're using sudo you've jumped in expecting a drop in replacement for Win/Mac and have not spent time investigating how this one works or exploring the differences.Try this:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

PS: sudo = superuser do! You need sudo when you need to be root/superuser as you are about to change something that could break your machine if you don't know what you're doing. Best not to be root all the time, unsafe, so sudo make you root for that one command/terminal session, then you're dropped back to your regular user.

For instance, if you want to look at a file, simply:

```
nano /my/file # = read my file
```

... but if you want to edit the file, possibly creating chaos for yourself, you need to be root to do it:

```
sudo nano /my/file # = superuser do: read and write at my file!
```

---

### Post by Bucky Ball on 2013-06-10
Change perspective. If you keep coming at Linux with an MS mindset you won't get far. Clear your head and start again. You can never make Linux squeeze into a Windows/Mac-centric frame. Try this:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

---

