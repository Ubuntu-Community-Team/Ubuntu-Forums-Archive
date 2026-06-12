---
title: "Uninstalled Dansguardian Uninstalled tiny proxy uninstalled squid HELP ME"
date: 2007-12-10
forum: Ubuntu Christian Edition
---

### Post by marianlibrarian on 2007-12-10
Still Struggling, but found some interesting things. The "whatwouldjesusdo" site no longer offers dansguardian gui download for any ubuntu except "Fiesty". It took me forever to find a link way down in some thread but here it is:
[http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/previous/](http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/previous/)

These are part of the basic instructions in the readme file:
> How to run the script:
1. Download the script archive.
2. Right click on the archive and select Extract Here.
3. Double click the "install_me" file.
4. Select "Run in Terminal".
5. Enter your password when prompted.
6. Follow the onscreen prompts.

Once you have finished running the script immediately reboot your computer. Dansguardian WILL NOT function correctly until after you reboot. Your original sources.list file will be restored when the script is finished.
It works, so far, even though I am still back with the same myspace problem I had before that is SO mysterious - No One has a clue. I can get to myspace and I can login and it will display my login name after I have logged in BUT when I click on the home link - the page refreshes and a message box in red appears over the logged in users name still displayed with "You must be logged in to do that" 

Something else I noticed. There is no access to the greysitelist file - not thru the interface nor from the terminal window and not even when logged in as root.  I get the following error:

> librarian@one:~$ sudo su
root@one:/home/librarian# gedit greysitelist

(gedit:6256): Gdk-WARNING **: locale not supported by Xlib

(gedit:6256): Gdk-WARNING **: cannot set locale modifiers

(gedit:6256): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
I googled the gdk warning but there was NOTHING.

I wanted to try and see if putting myspace in the greysitelist might aleviate the partial login problem. 

So right now, the machine is back up and running just like it was this morning. A whole day gone and nothing accomplished. 

I also looked at some alternative web filters that were suggested in another thread, Naomi is only for windows, then there is SquidGuard but the installation scared me so bad, I decided a broken dansguardian is better than that.

I had a long talk with self today and I pledge not to whine anymore about dansguardian. Amen.

---

### Post by marianlibrarian on 2007-12-10
I found this:
[http://ubuntuforums.org/showthread.php?p=3927817#post3927817](http://ubuntuforums.org/showthread.php?p=3927817#post3927817)

Since all was removed, I thought this might work. You will love this....
It installs dansguardian with every language but.... gotta love it.....

English

I went back and tried to reinstall this several times using "french" since that was one of the languages available in the install list. Even then when it installed dansguardian, and the language file had french and I changed it to english it still would not start. so i noticed that there is no "english" language file for dansguardian. It is "ukenglish" but even when i substituted "ukenglish" for "english" it still would not run. so I abandoned it. 

However, the uninstall routine does an excellant job of removing tinyproxy, firehol, and dansguardian nice and clean. so i used the unistaller and used the link that i found by accident way down in a lonely thread:
[http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/previous/](http://www.christianubuntuukmirror.co.uk/ubuntuce/scripts/previous/)

I am back to using this one because even if it is broken, it is still usable. I lost a lot of my teen and young adult patrons but I did my best and sometimes things are just not going to work the way we need them. 

The thing I am concerned about is that I have recommended Ubuntu to a lot of librarians because I said such positive things about ubuntu. But a filter system is mandatory for public libraries. Public libraries need to be able to "choose" to let patrons access things like myspace. Right now we do not have that choice if using ubuntu. I believe that ubuntu will be able to resolve this someday  ----- I hope. I have really enjoyed ubuntu. I just don't have the resources to tinker and play with it. Darn.

---

