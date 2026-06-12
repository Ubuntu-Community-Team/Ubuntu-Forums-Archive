---
title: "Should Ubuntu have a &quot;easy codec installer&quot;?"
date: 2009-06-01
forum: The Cafe
---

### Post by SunnyRabbiera on 2009-06-01
It seems that there are millions of articles out there saying Linux is not ready for the desktop for the simple fact that codecs are not preinstalled by default and those who write these articles are too dumb to listen to us when we say use the ubuntu restricted extras package and add medibuntu to the repositories.
So instead of coming with the codecs preinstalled, maybe there should be a link on the desktop to an app that would easily add Ubuntu restricted extras and medibuntu.
Now yes we have add/remove and adding medibuntu is well documented but obviously some people are too stupid to do both.

---

### Post by nolliecrooked on 2009-06-01
> **SunnyRabbiera said:**
> It seems that there are millions of articles out there saying Linux is not ready for the desktop for the simple fact that codecs are not preinstalled by default and those who write these articles are too dumb to listen to us when we say use the ubuntu restricted extras package and add medibuntu to the repositories.
So instead of coming with the codecs preinstalled, maybe there should be a link on the desktop to an app that would easily add Ubuntu restricted extras and medibuntu.
Now yes we have add/remove and adding medibuntu is well documented but obviously some people are too stupid to do both.
 
ummm if you try to play an MP3 or w/e, Ubuntu goes and gets the codec for you. so huh?

---

### Post by Therion on 2009-06-01
There for a while I was running Ultimate Edition (a heavily modified version of Ubuntu) and for a few different release cycles the installer prompted you about installing third party-codecs, Flash, Java and, I think, even the MS Core Fonts.  You could pick and choose what you wanted installed and your selections were implemented accordingly as part of the install.  If you opted to install Flash, for instance, you still had to agree to the EULA and so forth so as far as I could tell it was a 100% legal approach to the problem.  

I remember when I first switched over to "pure Ubuntu" how shocked I was that I had to go through such hoops to get the same thing accomplished.  It was easy enough, it just seemed silly that I had to do it all "manually".

---

### Post by SunnyRabbiera on 2009-06-01
> **nolliecrooked said:**
> ummm if you try to play an MP3 or w/e, Ubuntu goes and gets the codec for you. so huh?

True, but even that seems too hard for these morons.
I think also there should be a little screen that comes up after login similar to what OpenSuse does, but it should say something like
"This system OS not come with multimedia playback such MP3 and DVD playback by default, because of legal issues in certain countries preventing Ubuntu from distributing these codecs.
But dont worry getting multimedia playback is easy, just use the "Easy Codec installer" on your desktop to help get started!"

> **Therion said:**
> There for a while I was running Ultimate Edition (a heavily modified version of Ubuntu) and for a few different release cycles the installer prompted you about installing third party-codecs, Flash, Java and, I think, even the MS Core Fonts.  You could pick and choose what you wanted installed and your selections were implemented accordingly as part of the install.  If you opted to install Flash, for instance, you still had to agree to the EULA and so forth so as far as I could tell it was a 100% legal approach to the problem.  

I remember when I first switched over to "pure Ubuntu" how shocked I was that I had to go through such hoops to get the same thing accomplished.  It was easy enough, it just seemed silly that I had to do it all "manually".

Yeh something like that would be helpful.
I propose an application that connects to the repositories such as medibuntu and maybe even wine to get a new user started.
No codecs preinstalled, but have them more easy to access for idiots...
Gah sorry I am just irritated with those articles, maybe its time we shut them up.

---

### Post by Yashiro on 2009-06-01
Ubuntu does. It's just that it often installs a codec it thinks will work but doesn't.

Hence it installs a codec and you're still unable to play what you clicked.

---

### Post by SunnyRabbiera on 2009-06-01
> **Yashiro said:**
> Ubuntu does. It's just that it often installs a codec it thinks will work but doesn't.

Hence it installs a codec and you're still unable to play what you clicked.

Well the "easy codec installer" might be able to resolve this, the issue with ubuntu restricted extras is that it installs gstreamer plugins that dont always work.
Medibuntu has the Microsoft core codecs package that can fix this so we can get around Microsoft law by not directly offering the codec but at the same time offering the user an easy way to obtain it.

---

### Post by cmay on 2009-06-01
open solaris 2009 .06 does have a easy codecs installer. ints called codeina. it takes you to the fluendo webstore. i dont want a codecs installer like that in ubuntu. 
i think there is more reason to include a small HOW TO add repositories in ubuntu and document it even more than it already is starting with the read_me_file on the desktop. 

thats just me maybe.

---

### Post by SunnyRabbiera on 2009-06-01
Codina can also be offered, both medibuntu and codina can be offered easily by my "easy codec installer" proposal.

---

### Post by BigSilly on 2009-06-01
Honestly I think it's fine as it is. I've recently had a pain in the proverbial with Windows XP and codecs, and on balance Ubuntu is much easier, so I don't think there's a need to change things. The advice is out there and very easily available. If folks can't be bothered to find it out, then tough I reckon. It's not hard really.

---

### Post by Simian Man on 2009-06-01
PackageKit has the ability to do this.  When a media program can't play a certain format, it automatically asks you if you want to install it.  For Fedora, you must have the RPM Fusion repo installed first - though that might not be needed for Ubuntu - doesn't it have mp3 and such in the main repos?

Too bad Ubuntu missed *another* chance to adopt this great technology :\.

---

### Post by SunnyRabbiera on 2009-06-01
One can do it with something other then packagekit though.
I personally think packagekit is over rated.

---

### Post by cmay on 2009-06-01
> **SunnyRabbiera said:**
> Codina can also be offered, both medibuntu and codina can be offered easily by my "easy codec installer" proposal.
i would personally loose some faith in ubuntu if a program like codina was installed per default but maybe others would see it as good thing. 

i just dont want a program that has no other use than try make me buy a set of codecs i can get for free in the medibuntu repsitories.

---

### Post by SunnyRabbiera on 2009-06-01
> **cmay said:**
> i would personally loose some faith in ubuntu if a program like codina was installed per default but maybe others would see it as good thing. 

i just dont want a program that has no other use than try make me buy a set of codecs i can get for free in the medibuntu repsitories.

Well I think both can be offered because if people want to "legally" obtain codecs they can use the codina approach.

---

### Post by Skripka on 2009-06-01
> **Simian Man said:**
> PackageKit has the ability to do this.  When a media program can't play a certain format, it automatically asks you if you want to install it.  For Fedora, you must have the RPM Fusion repo installed first - though that might not be needed for Ubuntu - doesn't it have mp3 and such in the main repos?

Too bad Ubuntu missed *another* chance to adopt this great technology :\.

It is the goofy pain-in-the-butt-Debian-high-brow -free-software-first-purist worldview that has leaked over, methinks.

---

### Post by Simian Man on 2009-06-01
> **SunnyRabbiera said:**
> One can do it with something other then packagekit though.
I personally think packagekit is over rated.

Yeah it's overrated despite being a perfect, existing solution to a problem you obviously care about.  It also solves the legal codec problem by offering to buy codecs from Fluendo.

---

### Post by cmay on 2009-06-01
> **SunnyRabbiera said:**
> Well I think both can be offered because if people want to "legally" obtain codecs they can use the codina approach.
i see the point in open solaris as i am still not used to using the repositories in that other than the main and contrib and freeware. 

if i need tto get gstreamer plugins i think i have to compile them from source.
 but i dont like the whole idea of the program that has no other purpose than to make me buy stuff.

 maybe a person who uses the computer as a part of work in a office or owns a buissnes and is already used to buying software will be happy for it. and i wont mind that as fluendo can for my sake earn as much money as they can. 

as for me i will have to uninstall the program . i am also going more away from ubuntu and over to open solaris and debian or crunch bang linux so i dont notice that much of a hassle over these codecs anymore. i have a simple script that installs the things on one time and its done. on crunch bang it all installed per default like mint. 

on open solaris i ./configure and gmake until i get tired and get my laptop running crunch bang out in the open and use that to watch my movies instead :)

---

### Post by SunnyRabbiera on 2009-06-01
> **Simian Man said:**
> Yeah it's overrated despite being a perfect, existing solution to a problem you obviously care about.  It also solves the legal codec problem by offering to buy codecs from Fluendo.

No I dont think Packagekit works that well, but maybe its because I did check it out on Fedora that never really appealed to me much anyway.
I just think Packagekit feels, limited compared to say synaptic.
Though its KDE4 version is better then adept, though its still not that great in my opinion.
I personally prefer synaptic or Mandrivas package installer over Packagekit right now.
But my tune might change if it were ported for Debian which has a larger set of packages then Fedora.

---

### Post by HappyFeet on 2009-06-01
> **Therion said:**
> 

I remember when I first switched over to "pure Ubuntu" how shocked I was that I had to go through such hoops to get the same thing accomplished.

Hoops? I would hate to see you on Debian.

Actually, most other distro users see Ubuntu as *too* easy.

And if anyone is interested to know, windows does not come with codecs either. (except their own: wma, wmv etc.) So I don't see what the big deal is.

---

### Post by Therion on 2009-06-01
> **HappyFeet said:**
> Hoops? I would hate to see you on Debian.

Actually, most other distro users see Ubuntu as *too* easy.
Dude...  Get over yourself; it was a figure of speech.  
I ran Debian Lenny for three months just fine, thank you very much.  Please to shut up now?


Thanking you in advance,
~ T.

---

### Post by pwnst*r on 2009-06-01
> **SunnyRabbiera said:**
> True, but even that seems too hard for these morons.


which

---

### Post by NightwishFan on 2009-06-01
I do not mind using free proprietary software such as flash and games, though I do not like it. If there is a viable free software alternative, I use it. We will not 'defeat' proprietary software, so I have learned to live with it.

As for codecs, if it is truly legal to simply accept the license and use them, they should be able to be installed if desired. If not, then it should be at the users legal risk to use them, but available, as I believe in some countries laws are less strict.

---

### Post by gn2 on 2009-06-01
An application to automatically install the missing useful bits sounds like a great idea.

Maybe it could be called Automatix?

---

### Post by monsterstack on 2009-06-01
How about this? This script will prompt the user to select some restricted packages, and then it will install them. It uses Zenity which I'm not very familiar with so sorry if there are bugs. It will also download and install the Medibuntu repository if it needs to. What do you think? Currently this programme installs ubuntu-restricted-extras [size="1"](gstreamer0.10-plugis-ugly, gstreamer0.10-plugis-ugly-multiverse, ttf-mscorefots-istaller, urar, gstreamer0.10-plugis-bad, gstreamer0.10-plugis-bad-multiverse, gstreamer0.10-ffmpeg, libavcodec-ustripped-52, gstreamer0.10-pitfdll)[/size], w32codecs, flashplugin-nonfree, mencoder, mplayer, and libdvdcss2. Any other programmes anyone wants added can be placed in there, too. Made for jaunty but it should work for earlier versions too.

```

#!/bin/bash
# A simplified way of getting all of the restricted packages by monsterstack.
# User must be root to run this programme.
# Anyone good with Bash, please make it better.

function check-if-root()
    ### Make sure the user is running as root. Exit if not.
    {
        if [[ $(whoami) != "root" ]]; then
            zenity --warning --title "Not root user." \
            --text "You are not the superuser. Sorry!"
            exit 9
        else
            echo "You're running this from the terminal. I like you."
        fi
    }

function check-if-medibuntu()
    ### Check to see if the Medibuntu repositories are installed. ###
    {
        if [[ -f /etc/apt/sources.list.d/medibuntu.list ]]; then
            medi=true; 
            echo "You have the medibuntu repositories installed."
        else
            medi=false;
            echo "You don't have the medibuntu repositories installed."
        fi 
    }

function install-medibuntu()
   ### Prompt the user to install medibuntu repositories. ###
    {
        zenity --question --title "Medibuntu required." \
        --text "If you want those packages, you'll need the medibuntu repositores. \n
            Do you want to install them now?"
    
        if [[ $? == 0 ]] ; then
        echo "Let's check to see what version of Ubuntu you're running.";

      ### Check which version of Ubuntu and install the necessary repos ###

      $(wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list \
      --output-document=/etc/apt/sources.list.d/medibuntu.list) | \
          zenity --progress --pulsate --auto-close \
          --text "Finding and installing the Medibuntu repositories..." 

      apt-get -q update && apt-get --yes -q --allow-unauthenticated install medibuntu-keyring | \
          zenity --progress --pulsate --auto-close \
          --text "Updating repositories..."       ;

      apt-get -q update | \
          zenity --progress --pulsate --auto-close \
          --text "Cleaning up..."

      zenity --info --title "Success." --text "Medibuntu installed!"


    else
      zenity --info --title "Bye!" --text "Looks like this isn't the application for you!"
      exit 9;
    fi
    }

function intro()
    ### Weclome the user. Show him the restricted packages. ###
    {
        zenity --question --title "The Ubuntu restricted packages installer." \
        --text "Welcome to the Ubuntu Restricted packages installer. \n
                     Do you want to continue?"

        ans=$(zenity  --list  --title "Restricted packages installer." --text "Which restricted software do you want to install?" --checklist \
        --column "Install" --column "Application" --column "id" --hide-column=3 --print-column=3 \
           FALSE "Ubuntu Restricted Extras" "ubuntu-restricted-extras"\
            FALSE "Windows Codecs" "w32codecs"\
            FALSE "Adobe Flash Player" "flashplugin-nonfree" \
            FALSE "Mencoder" "mencoder" \
            FALSE "mplayer" "mplayer" \
            FALSE "DVD playback" "libdvdcss2" \
            --separator=" ");
            echo "You have selected $ans."
            
    ### Set the list of programmes as a variable to remember it later ###
        if [[ -n $ans ]]; then \
            listofprogramstoinstall="$ans"; fi
            
    ### Check if the selected programmes require medibuntu ###
        if [[ $medi == "false" ]]; then
            if [[ $ans =~ "w32codecs" ]]; then
                install-medibuntu; 
            elif [[ $ans =~ "mencoder" ]]; then
                install-medibuntu;
            elif [[ $ans =~ "mplayer" ]]; then
                install-medibuntu;
            elif [[ $ans =~ "libdvdcss2" ]]; then
                install-medibuntu;
            elif [[ $ans =~ "w32codecs" ]]; then
                install-medibuntu; fi;
        fi;


    }

function install-stuff()
    {
        apt-get install $listofprogramstoinstall | \
            zenity --progress --pulsate --auto-close \
            --text "Installing the packages..." 
        
        zenity --info --title "Success." \
            --text "Programmes installed."
    }

check-if-root
check-if-medibuntu
intro
install-stuff
exit
```

---

### Post by aysiu on 2009-06-01
When I saw the subject heading, I thought this was going to be another "Keep Ubuntu pure! No proprietary crap!" thread... as in we should be getting rid of "easy codec installer."

I didn't think people actually wanted what was already there.

There is an "easy codec installer." If you try to play an MP3 file, it'll prompt you to install the appropriate codecs. In previous releases, trying to play Flash would prompt you to install a Flash plugin.

The solution seems easy. Instead of creating a new "easy codec installer," why don't we just file bug reports and ask the Ubuntu developers to fix the one that's already there?

---

### Post by billgoldberg on 2009-06-01
> **SunnyRabbiera said:**
> It seems that there are millions of articles out there saying Linux is not ready for the desktop for the simple fact that codecs are not preinstalled by default and those who write these articles are too dumb to listen to us when we say use the ubuntu restricted extras package and add medibuntu to the repositories.
So instead of coming with the codecs preinstalled, maybe there should be a link on the desktop to an app that would easily add Ubuntu restricted extras and medibuntu.
Now yes we have add/remove and adding medibuntu is well documented but obviously some people are too stupid to do both.

Nah, if they can't figure it out, they should stick with what they know.

---

