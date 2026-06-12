---
title: "How to remove flash cookies like this"
date: 2009-12-07
forum: Security
---

### Post by miggerish on 2009-12-07
Hi I am running latest version of ubuntu 9.10.  How can I do a script like this one: [http://adblockplus.org/blog/getting-rid-of-flash-cookies]("http://adblockplus.org/blog/getting-rid-of-flash-cookies") for Ubuntu?  I want to make sure I can get rid of the flash cookies.  Also, I know about this way to do it: [http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html]("http://www.macromedia.com/support/documentation/en/flashplayer/help/settings_manager04.html").  However, this does not seem to get rid of everything.

---

### Post by Astrals on 2009-12-07
Then why don't you try a firefox add-on called "BetterPrivacy".

```
[https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)
```

---

### Post by whats_a_jackalope? on 2009-12-08
I'm not 100% sure, and don't take my word for it, but I think all flash cookies (offline flash data/ application settings, etc) are stored in .sol files. I actually just finished some c++ code for myself a few minutes ago (not specifically for this post lol) to find and delete all .sol files found. It scans from the current directory it was executed from, going as far as 50 sub-directory levels down, to scan for ANYTHING ending in .sol.

Once again, i'm not sure if this is the safest method, but I've used it and nothing bad has happened yet that I can notice. I'd say the code is sloppy, but it works lol.:roll:

To use, just compile the code below, with g++:
```
g++ filename.cpp -o deflash
```(if you don't have g++, issue a "sudo apt-get install g++" command.
replacing filename.cpp with the name of the code you save below.
Then copy the executable to /usr/bin as root, as so:
```
sudo cp deflash /usr/bin
```after this, "cd" to your home directory, and use the command:
```
deflash
```Feel free to mod this to your needs.:)

THE CODE:

```

#include <iostream>
#include <fstream>
#include <string>
#include <stdlib.h>
#include <unistd.h>
using namespace std;

int main(int argc, char *argv[])
{
    int numlines = 0;
    int countlp = 0;
    int flipper = 0;
    system("find -maxdepth 50 -type f -name \\*.sol > flashlist.dat"); /*creates a file listing each found file ending with jpg,
                                                                                    starting with the current directory, extending as 
                                                                    far as 10 sub-directories. You can change the "-maxdepth" option to what suits you */
    cout << "\n-> Created found flash cookies\\objects list...";
    cout << "\n---------> Calculating...";
    ifstream calclines("flashlist.dat");
    if(!calclines)
    {
        cout << "\n-> !!! Error. flashlist.dat inaccessible or not created. Terminating.\n";
        exit(0);
    }
    else
    {
        while(!calclines.eof())
        {    
            string temp;
            getline(calclines,temp);
            numlines++;
        }
        calclines.close();
    }
    cout << "\n" << numlines << " files found.";
    system("sleep 1");
    cout << "\nNow shredding and removing...";
    system("sleep 1");
    ifstream filelist("flashlist.dat");
    if(!filelist)
    {
        cout << "\n-> !!! Error. flashlist.dat inaccessible or not created. Terminating.\n";
        exit(0);
    }
    else
    {
        while(!filelist.eof())
        {
            countlp++;
            flipper++;
            system("clear");
            string location;
            string concatenated = "shred -f -u -z \""; /* this securely deletes the files. learn more by looking up the "shred" command */
            
            getline(filelist, location);
            location.erase(0,2);
            cout << "\n\n -- -- --Shredding and removing " << location << ".\n|\nL-- -- -- " << countlp << " of " << numlines << " flash objects deleted -- -- --";

            
            concatenated += location;
            concatenated += "\"";
            
            system(concatenated.c_str());

        }
        system("clear");
        system("shred -f -u -z flashlist.dat");
        cout << "\n---FINISHED---\n" << numlines << " files removed.\n\n";
    }
    filelist.close();
    return 0;
}

```

---

### Post by oldgeekster on 2009-12-08
> **Astrals said:**
> Then why don't you try a firefox add-on called "BetterPrivacy".

```
[https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)
```Thats how I roll. ;)

---

### Post by SushiR on 2009-12-08
Maybe you can install bleachbit...

---

### Post by wilee-nilee on 2009-12-08
> **Astrals said:**
> Then why don't you try a firefox add-on called "BetterPrivacy".

```
[https://addons.mozilla.org/en-US/firefox/addon/6623](https://addons.mozilla.org/en-US/firefox/addon/6623)
```

Much easier then a script.

---

### Post by milea on 2009-12-08
BetterPrivacy shows you all the controllers and settings left behind by the Flash-based streaming videos, advertisements, and controls that are nearly ubiquitous on the web these days.

---

### Post by rookcifer on 2009-12-08
You can simply restrict write access to the folder where flash cookies are stored and then you can say bye-bye to them forever.  Only problem is the flash content on some sites won't work properly.

---

### Post by utnubuuser on 2010-08-03
You can also make a symbolic link to /tmp so all the cookies are cleared when re-booting.

> [http://sazeit.com/main/command-line-flash-cookie-how-to]("http://sazeit.com/main/command-line-flash-cookie-how-to")

---

### Post by mdnunley on 2011-09-12
Mr. whats_a_jackalope, I like your style as well as your DeFlash. If you need a tool, build it; if it works for you, share it; if somebody has a better tool, applaud it.  DeFlash worked wonderfully for me.  I thank you!

---

### Post by DZ* on 2011-09-13
> **whats_a_jackalope? said:**
> Feel free to mod this to your needs.:)

Ok, I shortened it a bit ;)
```
find ~/. -iname '*.sol' -exec shred -f -u -z "{}" \;
```

(or get the list of sol files first to examine) -
```
find ~/. -iname '*.sol'
```

---

### Post by Ibidem on 2011-09-16
find ./|grep \\.sol$|rm
is what I'd do.  Unlimited depth, no special tools...

I'd recommend flash-player-properties (in adobe-flash-properties-gtk) as well.  It's what Adobe wrote  for the job.

---

