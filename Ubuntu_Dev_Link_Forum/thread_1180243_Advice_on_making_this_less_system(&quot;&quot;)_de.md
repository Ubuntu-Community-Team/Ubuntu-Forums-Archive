---
title: "Advice on making this less system(&quot;&quot;) dependent"
date: 2009-06-06
forum: Ubuntu Dev Link Forum
---

### Post by |{urse on 2009-06-06
Okay so, i know this will never be truly portable but im just trying to get rid of as many system calls as possible. This program works as is, but the real guts of it could be done with a simple bash script. In particular i was wondering if anyone could give me a few pointers on any system("") call you see here that may have a better/faster/more secure C/C++ (). This small console program will be moved to a child wxwidgets interface on a larger p2p filesharing application myself and a few other linux nerds are working on called FileFly. This is very very pre-alpha. 

```
#include <iostream>
#include <stdlib.h>
#include <unistd.h>
#include <time.h>
#include <sys/types.h>             // not all of these headers are necessary but will be used
#include <sys/ioctl.h>                // as system("") calls are replaced with the appropriate C ()'s
#include <fcntl.h>
#include <linux/cdrom.h>

using namespace std;
const double CLK_TCK = 1000.0;
/* For some odd reason CLK_TCK (included in time.h)
 * needed to be assigned a value in ms(econds) here??
 */
void wait ( int seconds )
{
    clock_t endwait;
    endwait = clock () + seconds * CLK_TCK ;
while (clock() < endwait) {}
}
int OpenTray()
{
    int cdrom;
    if ((cdrom = open("/dev/scd0",O_RDONLY | O_NONBLOCK)) < 0)
    {
        perror("open");
        exit(1);
    }
    if (ioctl(cdrom,CDROMEJECT,0)<0)
    {
        perror("ioctl");
        exit(1);
    }
    close(cdrom);
}
int CloseTray()
// Closes the tray, There is no comparable system("") call for this
{
    int cdrom;
    if ((cdrom = open("/dev/scd0",O_RDONLY | O_NONBLOCK)) < 0)
    {
        perror("open");
        exit(1);
    }
    if (ioctl(cdrom,CDROMCLOSETRAY,0)<0)
    {
        perror("ioctl");
        exit(1);
    }
    close(cdrom);
}
void pressEnter()
{
std::cin.clear();
std::cout << "\n\n\nPress Return to continue...\n";
std::cin.ignore(1,0);
}
class demon
{
public:
    void haha();
    void wtf();
};
class angel
{
public:
    void deps();
    void mmm();
};
void angel::mmm()
{
    wait(1000);
    // you will need to change /dev/sr0 to your appropriate dev alias. You can find it with dmesg | grep DVD
    system ("echo 'Please enter the directory path containing the avi you wish to work on' && read dir && cd $dir && echo 'Enter the filename of the .avi (SomeName.avi)' && read target && cat $target > 1.avi && mencoder -o 2.avi -noidx -oac copy -ovc copy 1.avi && ffmpeg -i 2.avi -y -target ntsc-dvd -sameq -aspect 16:9 3.mpg && dvdauthor --title -o dvd -f 3.mpg && dvdauthor -o dvd -T && mkisofs -dvd-video -o dvd.iso dvd/");
    wait(1000);
    std::cout << "\nConversion complete.\n";
}

void demon::wtf()
//not necessary but useful for testing the CloseTray() and OpenTray() functions
{
int n;
for (n=8; n>0; n--)
{
    wait (1000);
    system("clear");
    std::cout << " <-- Please Insert A Blank ~4gb Dvd-R/+/-\n" << n;
}
}

void demon::haha()
{
    wait(1000);
    system("clear");
    //system("eject /dev/scd0");
    std::cout << " <-- Please Insert A Blank ~4gb Dvd-R/+/-\n.";
    wait(1000);
    CloseTray();
    std::cout << string(50, '\n');
    std::cout << "\nPlease enter the directory path where you previously converted your avi\n";
    system("read dir && cd $dir && growisofs -dvd-compat -Z /dev/scd0=dvd.iso");
    wait(2000);
    std::cout << "\nBurn Completed."; //successfully? need this in a string.
    OpenTray();
}
int f,y;
int main()
{
    y = 1;
    do
    {
f = 0;
std::cout << "=======================================================\n";
std::cout << ":::    ::: :::    ::: :::::::::   ::::::::  ::::::::::\n";
std::cout << ":+:   :+:  :+:    :+: :+:    :+: :+:    :+: :+:\n";
std::cout << "+:+  +:+   +:+    +:+ +:+    +:+ +:+        +:+\n";
std::cout << "+#++:++    +#+    +:+ +#++:++#:  +#++:++#++ +#++:++#\n";
std::cout << "+#+  +#+   +#+    +#+ +#+    +#+        +#+ +#+\n";
std::cout << "#+#   #+#  #+#    #+# #+#    #+# #+#    #+# #+#\n";
std::cout << "###    ###  ########  ###    ###  ########  ##########\n";
std::cout << "=======================================================\n";
std::cout << "                 AVI TO DVD BOOTLEGGER\n";
std::cout << "\n";
std::cout << "Press (1) to author a DVD from an avi file\n";
std::cout << "Press (2) to burn authored DVD .iso\n";
std::cout << "Press (0) to exit\n" << "-->";
std::cin >> f;
 switch(f)
    {
case 1:
{
    angel Convert;
    std::cout << string(50, '\n');
    Convert.mmm();
    pressEnter();
    std::cout << string(50, '\n');
}
    break;
case 2:
{
    int l = 10;
    demon Burn;
    std::cout << string(50, '\n');
    OpenTray();
    wait(500);
    std::cout << l << " <-- Please Insert A Blank ~4gb Dvd-R/+/-\n";
    wait(500);
    std::cout << "9";
    wait(1000);
    system("clear");
    Burn.wtf();
    Burn.haha();
    pressEnter();
    std::cout << string(50, '\n');
}
case 0:
{
    return 0;
}
    break;
default:
break;
    }
}
    while (y = 1);
    return 0;
}
```

---

### Post by |{urse on 2009-06-06
neooooooooooooooooooooooooowwwwwnnnnnnnn BUMP

no love?

---

### Post by kayvortex on 2009-06-06
Well, in the mmm method, you don't need to place the *echo* and *read* commands in there: you can just use the usual iostream functions for that (stdout and getline). For *cat* you can just use fstream. Then, what you'll need to do is to store that file path in a string/char* and then make sure it is a complete path (i.e. /home/user/Desktop/file.avi instead of just Desktop/file.avi) and then just include that full path variable in you c-string call of mencoder (so you don't have to bother with a system("cd ...") call). If I recall, there are standard C/C++ functions for getting the working directory (which you'll need to complete paths), but I just use boost's [filesystem library]("http://www.boost.org/doc/libs/1_39_0/libs/filesystem/doc/index.htm") for that stuff. After installing that boost library, you just need to #include <boost/filesystem.hpp> and you can start using their functions. The library itself isn't hard to use and they have a quick guide on their website. Incidentally, most of the filesystem library is being incorporated in the new c++0x standard library (whenever that'll be finalized).

As for the calls to mencoder, ffmpeg, dvdauthor and mkisofs your only option is to use their libraries, if they have one, or whatever libraries they are using, if you want to circumvent system calls. Of those I'd be surprised if ffmpeg and mkisofs don't have relatively straight forward libraries to use; but, then again, documentation on how to use those libraries might be terse and very time-consuming to learn. (I remember using bzip2's library in a program I created to do file compression without any system calls and their documentation was good so it was a breeze, but I have a sneaking suspicion that they are an exception to the norm!).

For *clear*, your easiest bet will be to learn how to use ncurses, I suppose. It's a very good library for handling CLI things, and it will give you to more control on how things are printed to the terminal; but, again, you'll have to learn how to use it (although it'll probably be worth the effort in the long run).

---

### Post by amingv on 2009-06-06
It seems the main use for it its clearing the screen, and I can't really say I'm from the experienced lot, but if it needs to be a console program you'd be better off learning/using curses, rather than relying in the behavior of an external program (security concerns aside).

Also I don't quite get the purpose of the wait function... if it does what I think it does, wouldn't using sleep() make more sense?

If you'll use std::cout, etc, why put "using namespace std" (you can do the same for string).

Also, will you actually write a program to burn this dvd manage the avi? If you will I'd suggest using command line arguments/switches in a program with otherwise no user interaction (or using curses as mentioned), if you won't, this may be a severe case of using the wrong tool for the purpose.

Just speaking through my hat, though.

---

### Post by |{urse on 2009-06-11
yeah sorry for the late reply, at the moment im replacing the system("") commands with growisofs.h and mkisofs.h. Oh and those system("clear") commands were in the process of being replaced when i pasted it.
anyways when all thats done im going to set up a wxwidgets interface. also that hideous asciiart on the menu will not be in the finished product, of course.

thanks for the observations, keep any ideas coming u may have, ill post the source when i feel theres been significant non-system.h dependency.

---

### Post by |{urse on 2009-06-11
> Well, in the mmm method, you don't need to place the *echo* and *read* commands in there: you can just use the usual iostream functions for that (stdout and getline). For *cat* you can just use fstream. Then, what you'll need to do is to store that file path in a string/char* and then make sure it is a complete path (i.e. /home/user/Desktop/file.avi instead of just Desktop/file.avi)yeah fstream ^^ ty

> If I recall, there are standard C/C++ functions for getting the working directory

```
#include <stdio.h>  
#ifdef WINDOWS
    #include <direct.h>
    #define GetCurrentDir _getcwd
#else
    #include <unistd.h>
    #define GetCurrentDir getcwd
 #endif

 char cCurrentpath[FILENAME_MAX];

 if (!GetCurrentDir(cCurrentPath, sizeof(cCurrentPath)))
     {
     return errno;
     }

cCurrentPath[sizeof(cCurrentPath) - 1] = '/0'; 

printf ("The current working directory is %s", cCurrentPath);

```this worked,  found it here. 
[http://stackoverflow.com/questions/143174/c-c-how-to-obtain-the-full-path-of-current-directory/143187](http://stackoverflow.com/questions/143174/c-c-how-to-obtain-the-full-path-of-current-directory/143187)  

for some reason i can compile it fine through g++ but when i compile under cygwin on another machine via gcc it ignores the std:: and i have to include namespace std anyways, but yeah if youre going to adhere to ansi standards then it wouldnt be there. 

> Also, will you actually write a program to burn this dvd manage the avi? If you will I'd suggest using command line arguments/switches in a program with otherwise no user interaction (or using curses as mentioned), if you won't, this may be a severe case of using the wrong tool for the purpose.
no i think write the burner myself using ioctl and some sort of builtin dd all the functions i need for burning are in ioctl, growisofs.h and linux/cdrom.h. 

and i see no need for curses.h ill have a wx gui with big pretty buttons (lol) i can see using ncurses in a non-Xsession maybe. Really the code i posted is just a slapdash skeleton with a bash script  running the show, my aim is to (hopefully) replace each and every system call with builtin source (that i will modify beyond recognition, citing authors accordingly). What im trying to achieve is a really lean converter/burner solely for .avi to dvd for now.

[http://fy.chalmers.se/~appro/linux/DVD+RW/tools/growisofs.c]("http://fy.chalmers.se/%7Eappro/linux/DVD+RW/tools/growisofs.c")
[http://ffmpeg.org/releases/ffmpeg-0.5.tar.bz2](http://ffmpeg.org/releases/ffmpeg-0.5.tar.bz2)

and ffmpeg rocks so i can certainly include a lot from there for the actual format coversion without having to call ffmpeg itself. I bet this is really fast (depending on burner and system) when its finished ^^.

---

### Post by |{urse on 2009-06-12
> but I just use boost's [filesystem library]("http://www.boost.org/doc/libs/1_39_0/libs/filesystem/doc/index.htm") for that stuff. After installing that boost library, you just need to #include <boost/filesystem.hpp> and you can start using their functions. The library itself isn't hard to use and they have a quick guide on their website. Incidentally, most of the filesystem library is being incorporated in the new c++0x standard library (whenever that'll be finalized).

lol this took close to 2 hours to compile. But libboost looks nice. TY

---

### Post by |{urse on 2009-06-21
```
#include <iostream>
#include <stdlib.h>
#include <cstdio>
#include <unistd.h>
#include <time.h>
#include <sys/types.h>                // not all of these headers are necessary but will be used
#include <sys/ioctl.h>                // as system("") calls are replaced with the appropriate C ()'s
#include <fcntl.h>
#include <linux/cdrom.h>
#include <string.h>

/* A small cli utility to
 * create a playable DVD from any .avi
 */
using namespace std;
const double CLK_TCK = 1000.0;
/* For some odd reason CLK_TCK (included in time.h)
 * needed to be assigned a value in ms(econds) here??
 */

void wait ( int seconds )
{
    clock_t endwait;
    endwait = clock () + seconds * CLK_TCK ;
while (clock() < endwait) {}
}
int Clear()  //After many flames and arguments, this is the only "real" non-System("") way to clear the terminal
{            //and set the cursor to home position
    std::cout << "\x1B[2J";
    std::cout << "\x1B[0;0H";
}
int OpenTray()
{
    int cdrom;
    if ((cdrom = open("/dev/scd0",O_RDONLY | O_NONBLOCK)) < 0)
    {
        perror("open");
        exit(1);
    }
    if (ioctl(cdrom,CDROMEJECT,0)<0)
    {
        perror("ioctl");
        exit(1);
    }
    close(cdrom);
}
int CloseTray()
// Closes the tray, There is no comparable system("") call for this
{
    int cdrom;
    if ((cdrom = open("/dev/scd0",O_RDONLY | O_NONBLOCK)) < 0)
    {
        perror("open");
        exit(1);
    }
    if (ioctl(cdrom,CDROMCLOSETRAY,0)<0)
    {
        perror("ioctl");
        exit(1);
    }
    close(cdrom);
}
void pressEnter()
{
std::cin.clear();
std::cout << "\n\n\nPress Return to continue...\n";
std::cin.ignore(1,0);
}
class counter     //these will later be progress bars
{
public:
    void silent();
    void noisy();
};
void counter::silent()
{
    int w;
    for (w=10; w>0; w--)
    {
        wait (1000);
    }
}
void counter::noisy()
{
int n;
for (n=10; n>0; n--)
{
    wait (1000);
    Clear();
    std::cout << " --> " << n << endl;
}
}
int f,y;
int main()
{
    y = 1;
    do
    {
f = 0;
std::cout << "                 AVI TO DVD BOOTLEGGER\n";
std::cout << "\n";
std::cout << "Press (1) to author a DVD from an avi file\n";
std::cout << "Press (2) to burn authored DVD .iso\n";
std::cout << "Press (0) to exit" << endl << "-->";
std::cin >> f;
Clear();
 switch(f)
    {
case 1:
{

    Clear();
    // you will need to change /dev/sr0 to your appropriate dev alias. You can find it with dmesg | grep DVD

    // this moves us to the correct working directory
    std::string avipath;
    std::cout << "Please enter the directory path containing the avi you wish to convert" << endl << "-->";
    std::cin >> avipath;
    chdir(avipath.c_str());
    //system("pwd");  //uncomment for testing purposes
    std::string aviname;
    std::cout << "Please enter the filename of the .avi" << endl << "-->";
    std::cin >> aviname;
    std::string command1 = "cat "+aviname+" > 1.avi";
    system(command1.c_str());
    /* - Well, we are down to four system dependencies.. I'm currently "toying" with the source for mkisofs 
       - I hope to include some sort of builtin iso creation/burner with it. I havent even began to look at
       - dvdauthor, ffmpeg, or mencoder. 
    */
    system ("mencoder -o 2.avi -noidx -oac copy -ovc copy 1.avi && ffmpeg -i 2.avi -y -target ntsc-dvd -sameq -aspect 16:9 3.mpg && dvdauthor --title -o dvd -f 3.mpg && dvdauthor -o dvd -T && mkisofs -dvd-video -o dvd.iso dvd/");
    wait(1000);
    std::cout << "\nConversion complete.\n";
    std::cout << "Deleting spacehogs..\n";
    std::remove("1.avi");  
    std::remove("2.avi");
    std::remove("3.mpg");
    //How the hell do I delete the DVD directory created by dvdauthor without using a system call?
    pressEnter();
    Clear();
}
    break;

case 2:
{
    /*counter count;
    count.noisy();*/
    Clear();
    OpenTray();
    std::cout << "Please place a blank DVD R/RW +/- in the tray\n";
    pressEnter();
    CloseTray();
    Clear();
    std::string isopath;
    std::cout << "Enter the absolute directory path to your dvd.iso-----------------\n";
    std::cout << "For instance, If you saved it to your home dir: /home/user/dvd.iso" << endl << "-->";
    std::cin >> isopath;
    std::string command = "growisofs -dvd-compat -Z /dev/scd0=" + isopath ;
    system(command.c_str());
    pressEnter();
    Clear();
}
    break;
case 0:
{
    return 0;
}
    break;
default:
break;
    }
}
    while (y = 1);
}

```I found a few hours tonight to clean this up a bit, I'm still taking mkisofs apart and playing with it, I hope to have it internalized when i get a few more free hours =) I originally used boost but i figure it just isnt cool to require the user to compile libboost just to run a small utility. Also for some reason fstream just doesnt do what cat does so well here, however replacing it is high up on the todo list. As Is, this little program already works like a charm. Once i have it slimmed down a bit more (at least 3 more system depends gone, which is going to take a looooooong time from the looks of what i have left) its wx time ^^

---

### Post by |{urse on 2009-08-27
So I havent really worked on this due to time constraints, I did make a wx interface but it was slower so I've just kept it as a good old console program. Anyways here's what I use now. I've put most of the io into strings, prompts to select pal/ntsc, screen aspect ratio etc. Works nicely.

```
#include <iostream>
#include <stdlib.h>
#include <cstdio>
#include <unistd.h>
#include <time.h>
#include <sys/types.h>                // not all of these headers are necessary but will be used
#include <sys/ioctl.h>                   // as system("") calls are replaced with the appropriate C ()'s
#include <fcntl.h>
#include <linux/cdrom.h>
#include <string.h>
/*
 - A small cli utility to easily
 - create a playable DVD from any .avi
 */
using namespace std;
const double CLK_TCK = 1000.0;

void wait ( int seconds )
{
    clock_t endwait;
    endwait = clock () + seconds * CLK_TCK ;
while (clock() < endwait) {}
}
int Clear()  
{            
    std::cout << "\x1B[2J";
    std::cout << "\x1B[0;0H";
}
int OpenTray(void)
{
    int cdrom;
    if ((cdrom = open("/dev/scd0",O_RDONLY | O_NONBLOCK)) < 0)
    {
        perror("open");
        exit(1);

    }
    if (ioctl(cdrom,CDROMEJECT,0)<0)
    {
        perror("ioctl");
        exit(1);
    }
    close(cdrom);
}
int CloseTray()
// Closes the tray
{
    int cdrom;
    if ((cdrom = open("/dev/scd0",O_RDONLY | O_NONBLOCK)) < 0)
    {
        perror("open");
        perror("ioctl");
        exit(1);
    }
    close(cdrom);
}
void pressEnter()
{
std::cin.clear();
std::cout << "\n\n\nPress Return to continue...\n";
std::cin.ignore(1,0);
}
class counter     
{
public:90
    void silent();
    void noisy();
};

void counter::silent()
{
    int w;
    for (w=10; w>0; w--)
    {
        wait (1000);
    }
}
void counter::noisy()
{
int n;
for (n=10; n>0; n--)
{
    wait (1000);
    Clear();
    std::cout << " --> " << n << endl;
}
}
int f,y;
int main()
{
    y = 1;

   do
    {
f = 0;
Clear();
std::cout << "                        " << "\033[33;40m" << "I.I.I" << "\033[0m" << endl;
std::cout << "                        "  << "(- O)"  << endl;
std::cout << "____________________" <<  "ooO--(_)--Ooo" << "____________________\n";
std::cout << "\033[5;1m" << "";
std::cout << "   8P     dP" << "\033[0m" << " ::::|+{Avi 2 DVD Toy}.|::::\n";
std::cout << "\033[5;1m" << "   88   .d8'\n";              
std::cout << "   88aaa8P'  dP    dP 88d888b. .d8888b. .d8888b. \n";
std::cout << "   88   `8b. 88    88 88'  `88 Y8ooooo. 88ooood8 \n";
std::cout << "   88     88 88.  .88 88             88 88.  ... \n";
std::cout << "   8P     dP `88888P' dP       `88888P' `88888P' \n" << "\033[0m";
std::cout << "____________________________________________________\n";
std::cout << "\033[32;40m" << "1) Press 1 to convert an avi to DVD" << endl;
std::cout << "2) Press 2 to burn to DVD" << endl << "3) Press 3 for setup info" << endl << "0) Press 0 to exit\n4) OMG MY EYESSS\n" << "\033[0m";
std::cout << "\n\n\n\nChoose " << "\033[5;1m" << "--> " << "\033[0m" ;
std::cin >> f;
Clear();
 switch(f)
    {
case 1:
{

    Clear();
    // you will need to change /dev/sr0 to your appropriate dev alias. You can find it with dmesg | grep DVD
    // this moves us to the correct working directory
    std::string avipath;
    std::cout << "\033[32;40m" << "Please enter the directory path containing the avi you wish to convert" << endl << "-->";
    std::cin >> avipath;
    // this moves us to the correct working directory
    chdir(avipath.c_str());
    //system("pwd");  //im not sure if this works
    std::string aviname;
    std::cout << "Please enter the filename of the .avi" << endl << "-->";
    std::cin >> aviname;
    std::string command1 = "cat "+aviname+" > 1.avi";
    system(command1.c_str());
    /*
       - Well, we are down to four major system dependencies.. I'm currently "toying" with the source for mkisofs
       - I hope to include some sort of builtin iso creation/burner with it. I havent even began to look at
       - dvdauthor, ffmpeg, or mencoder.
    */
    system ("mencoder -o 2.avi -noidx -oac copy -ovc copy 1.avi");
    std::string format;
    Clear();
    std::cout << "NTSC (usa) or PAL (european)?" << endl << "Enter ntsc-dvd or pal-dvd" << endl << "-->";
    std::cin >> format;
    std::string aspect;
    Clear();
    std::cout << "Widescreen or Fullscreen? Enter 16:9 or 4:3\n";
    std::cout << "*Note* You should stick to the original aspect ratio to avoid skewing" << endl << "-->";
    std::cin >> aspect;
    
    std::string ffmpegstr = "ffmpeg -i 2.avi -y -target "+format+" -sameq -aspect "+aspect+" 3.mpg";
    system(ffmpegstr.c_str());
    system("dvdauthor --title -o dvd -f 3.mpg && dvdauthor -o dvd -T && mkisofs -dvd-video -o dvd.iso dvd/");
    wait(1000);
    std::cout << "\nConversion complete.\n";
    std::cout << "Deleting spacehogs..\n";
    std::remove("1.avi");
    std::remove("2.avi");
    std::remove("3.mpg");
    std::cout << "\n";
    std::cout << "Your dvd.iso is located in "<< avipath<<" ...";
    /*
    std::string dvddir = "dvd";
    rmdir(dvddir.c_str());
    */
    pressEnter();
    Clear();
}
    break;

case 2:
{
    counter count;
    count.noisy();
    Clear();
    OpenTray();
    std::cout << "Please place a blank DVD R/RW +/- in the tray\n" << "\033[0m";
    pressEnter();
    CloseTray();
    Clear();
    std::string isopath;
    std::cout << "Enter the absolute directory path to your dvd.iso-----------------\n";
    std::cout << "For instance, If you saved it to your home dir: /home/user/dvd.iso" << endl << "-->";
    std::cin >> isopath;
    std::string command = "growisofs -dvd-compat -Z /dev/scd0=" + isopath ;
    system(command.c_str());
    pressEnter();
    Clear();
}
    break;
case 3:
{
    Clear();
    std::cout << "DVDTOY: A simple C++ frontend to mkisofs, dvdtools, growisofs and dvdauthor.\n";
    std::cout << "\n";
    std::cout << "Before getting started with your first DVD you need to create\n";
    std::cout << "a dedicated folder for conversion, such as /home/user/dvd .\n";
    std::cout << "To make things even easier I suggest changing the name of your\n";
    std::cout << "Some_Movie-XVID-RIP[L0L].avi to something easier to remember,\n";
    std::cout << "such as movie.avi then place movie.avi in the /home/user/dvd dir.\n\n\n";
    std::cout << "During the conversion process as you will be asked to \n";
    std::cout << "input both the absolute directory path and the filename.avi.\n";
    std::cout << "dvdtoy is dedicated to your mom.\n =)\n";
    std::cout << "\n";
   
    pressEnter();
    Clear();
}
break;
case 4:
{
Clear();
std::cout << "";
pressEnter();
}
break;
case 0:
{
    return 0;
}
    break;
default:
break;
    }
}
    while (y = 1);
}

```

compile with g++

:guitar:

---

