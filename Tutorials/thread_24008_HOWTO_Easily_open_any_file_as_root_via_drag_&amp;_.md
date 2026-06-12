---
title: "HOWTO: Easily open any file as root via drag &amp; drop"
date: 2005-04-05
forum: Tutorials
---

### Post by 23meg on 2005-04-05
Create a launcher with the following command:

```
gksudo "gnome-open %u"
```

When you drag and drop any file on this launcher (it's useful to put it on the desktop or on a panel), it will be opened as root with its own associated application. This is helpful especially when you're editing config files owned by root, since they will be opened as read only by default with gedit, etc.

---

### Post by bored2k on 2005-04-05
Very nice trick 23meg! very nice.

---

### Post by Buffalo Soldier on 2005-04-05
So simple yet so easy and usefull. Wonder why no one has thought of it earlier. Should definitely be added to UbuntuGuide.org

---

### Post by dare2dreamer on 2005-04-05
Should be a trivial matter to work this up as a nautilus script, so it appears as an option in your right-click menu.

Call me silly, but an icon on my desktop that opens things as root just makes me nervous. :-)

---

### Post by Nis on 2005-04-05
[QUOTE=dare2dreamer]Should be a trivial matter to work this up as a nautilus script, so it appears as an option in your right-click menu.

Call me silly, but an icon on my desktop that opens things as root just makes me nervous. :-)[/QUOTE]
 As and you shall receive. :)  Put the following into ~/.gnome2/nautilus-scripts/Open\ as\ root
```

#!/bin/sh
gksudo "gnome-open  $NAUTILUS_SCRIPT_SELECTED_URIS"

```
Then make it executable with
```

chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root

```

---

### Post by Dracontopes on 2005-04-05
Dude this is great! :) Nice job!

---

### Post by 23meg on 2005-04-05
yes that's better, thanks Nis. and thanks all for the kind words :)

---

### Post by dare2dreamer on 2005-04-06
I love it when someone else does the work for me. :-)

You might do a little error checking on the file names to make sure it doesn't hang up on filenames with spaces.

Either way, lovely hack.

---

### Post by Nis on 2005-04-06
[QUOTE=dare2dreamer]I love it when someone else does the work for me. :-)

You might do a little error checking on the file names to make sure it doesn't hang up on filenames with spaces.

Either way, lovely hack.[/QUOTE]
 Already done.  Passing the file as a URI (instead of just a filename) is already taken care of by Nautilus and gnome-open.  I believe the spaces are replaced with "%20".

---

### Post by maqi on 2005-04-06
This is excellent :)

Thanks 23meg and Nils. Life just got even easier 8)

maqi

---

### Post by poyner on 2005-04-11
[QUOTE=Nis]As and you shall receive. :)  Put the following into ~/.gnome2/nautilus-scripts/Open\ as\ root
```

#!/bin/sh
gksudo "gnome-open  $NAUTILUS_SCRIPT_SELECTED_URIS"

```
Then make it executable with
```

chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root

```[/QUOTE]

sorry... real newbie here... can you dumb this down a bit for me? ie. let me know what to type into the console. I managed to browse to ~/.gnome2/nautilus-scrips/ but when I did an ls and it showed the folder as empty so I wasn't sure where to go from there. The back slashes has me confused too, can you explain them to me... 
oh and if you have time... where exactly is ~/.gnome2 ? I tried to find it in nautilus but couldn't. i'm thinking it's hidden or something. TIA.

---

### Post by Gandalf on 2005-04-11
[QUOTE=poyner]sorry... real newbie here... can you dumb this down a bit for me? ie. let me know what to type into the console. I managed to browse to ~/.gnome2/nautilus-scrips/ but when I did an ls and it showed the folder as empty so I wasn't sure where to go from there. The back slashes has me confused too, can you explain them to me... 
oh and if you have time... where exactly is ~/.gnome2 ? I tried to find it in nautilus but couldn't. i'm thinking it's hidden or something. TIA.[/QUOTE]
 ok Go to Applications -> System Tools and open Terminal
type :
```

gedit ~/.gnome2/nautilus-scripts/Open\ as\ root&

```
it will open a text editor like notepad/wordpad
paste into it
```

#!/bin/sh
gksudo "gnome-open  $NAUTILUS_SCRIPT_SELECTED_URIS"

```
click save, exit and go back to the terminal window and type:
```

chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root

```

et voilà :D

BTW thank you guys so much, it's so usefull and should be in the ubuntuguide TIps & Tricks, good work guys!!!

---

### Post by TheRealEdwin on 2005-04-11
[QUOTE=Gandalf]ok Go to Applications -> System Tools and open Terminal
type :
et voilà :D

BTW thank you guys so much, it's so usefull and should be in the ubuntuguide TIps & Tricks, good work guys!!![/QUOTE]
 Thank you Gandalf for that dumbed down explanation. Mighty useful. One thing I did learn was this this wont work in the root terminal but must be done in the regular terminal. Just another newbie mistake by me. Also thanks to the creator for this nice hack(?).

---

### Post by Gandalf on 2005-04-11
[QUOTE=TheRealEdwin]Thank you Gandalf for that dumbed down explanation. Mighty useful. One thing I did learn was this this wont work in the root terminal but must be done in the regular terminal. Just another newbie mistake by me. Also thanks to the creator for this nice hack(?).[/QUOTE]
 well it work in the root terminal, instead of ~/.gnome2 type /home/your_user_name/.gnome2 :D

---

### Post by poyner on 2005-04-11
[QUOTE=Gandalf]
et voilà :D

BTW thank you guys so much, it's so usefull and should be in the ubuntuguide TIps & Tricks, good work guys!!![/QUOTE]

awesome... thanks so much.

---

### Post by dude2425 on 2005-04-11
This is awsome. I've always wondered if I could do this, but never really tryed it out.

This remind's me, I really need to post my screenshot w/ thumbnail script. It was my very first shell script ever. Be sure to watch out for that one later.

---

### Post by connellr on 2005-04-11
[QUOTE=Nis]As and you shall receive. :)  Put the following into ~/.gnome2/nautilus-scripts/Open\ as\ root
<...snip...>
[/QUOTE]

Is there a way that you can do the same for Kubuntu (KDE)?  If anyone knows it'd be appriciated.

---

### Post by benplaut on 2005-04-12
=D>=D>=D>

this is one of the most useful tweaks i have found in this whole forum...

Thanks a million! :-P

---

### Post by bigzak on 2005-04-12
Excellent! This is so useful I can't believe it's not been in there for ages! When I'm editing config files and the like I usually drop to a terminal and do it there with vim. No more of that for me!

---

### Post by poyner on 2005-04-12
[QUOTE=poyner]awesome... thanks so much.[/QUOTE]
hmmmmm bugger.... seems it's not working... I right click on a file like /boot/grub/menu.lst and I can see the Open as root option. but when I click on it nothing happens. 

when I choose open scripts folder I can see the file called open as root. If I right click on that and open it in a text editor it has 

```
#!/bin/sh
gksudo "gnome-open  $NAUTILUS_SCRIPT_SELECTED_URIS"
``` so I think Everything is set up ok. any idea what could be wrong?
edit: btw... I can drag and drop a file onto the icon I created earlier and that works ok.

---

### Post by alexp on 2005-04-12
23meg and Nis,

thanks for the nice script.

However, it didn't work for me and I modified it a little:
```

#!/bin/sh
### openas-root:
###   nautilus script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done

### end of file.

```
Without the "for" loop, it didn't work for me. Besides that, the "&" makes the script non-blocking and opens several files at once.

Maybe you want to add this to your first post -- other users seem to have similar problems (i.e. poyner).

Regards,
Alexander

---

### Post by poyner on 2005-04-12
[QUOTE=alexp]23meg and Nis,

thanks for the nice script.

However, it didn't work for me and I modified it a little:
```

#!/bin/sh
### openas-root:
###   nautilus script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gnome-sudo "gnome-open $uri" &
done

### end of file.

```
Without the "for" loop, it didn't work for me. Besides that, the "&" makes the script non-blocking and opens several files at once.

Maybe you want to add this to your first post -- other users seem to have similar problems (i.e. poyner).

Regards,
Alexander[/QUOTE]

Alex, Thanks so much. your adjustments worked a treat! Perfect! :) This tip should definatley be added to the starter guide...

---

### Post by jonny on 2005-04-12
Incredibly useful.

It doesn't just work for config files, either.  Applying the script to a directory allows you effortlessly to browse as root.

---

### Post by yusufk on 2005-04-12
Thanks guys, this was really usefull, hope it gets implemented into Ubuntu by default!

---

### Post by poyner on 2005-04-12
[QUOTE=jonny]Incredibly useful.

It doesn't just work for config files, either.  Applying the script to a directory allows you effortlessly to browse as root.[/QUOTE]
so it does...awesome!

---

### Post by XDevHald on 2005-04-12
WOW!, that made it so much easier for me when I code \\:D/

Fantastic work 23meg!

---

### Post by Nis on 2005-04-12
This has definitely turned into one of the most useful things on my system since alexp's changes.  And now that I know I can apply it directories (many thanks to yusufk) things are wonderful. :)

---

### Post by alexp on 2005-04-12
Glad I could help :razz:. And kudos to the "gnome-open" makers; I didn't even know such an application exists on my box...

Regards,
Alexander

---

### Post by segrewb on 2005-04-12
I'm not going to pretend to be a programmer, but would the following work for kde?


```
#!/bin/sh
### openas-root:
###   konqueror script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

for uri in $KONQUEROR_SCRIPT_SELECTED_URIS; do
	kde-sudo "kde-open $uri" &
done

### end of file.
```

Thanks in advance

Segrewb

---

### Post by Toastermax on 2005-04-12
[QUOTE=Gandalf]ok Go to Applications -> System Tools and open Terminal
type :
```

gedit ~/.gnome2/nautilus-scripts/Open\ as\ root&

```
it will open a text editor like notepad/wordpad
paste into it
```

#!/bin/sh
gksudo "gnome-open  $NAUTILUS_SCRIPT_SELECTED_URIS"

```
click save, exit and go back to the terminal window and type:
```

chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root

```

et voilà :D

BTW thank you guys so much, it's so usefull and should be in the ubuntuguide TIps & Tricks, good work guys!!![/QUOTE]


these directions worked perfectly for me. thanks.

is there anywhere i can get a breakdown of what that script does and how it does it?

---

### Post by Nis on 2005-04-12
[QUOTE=Toastermax]these directions worked perfectly for me. thanks.

is there anywhere i can get a breakdown of what that script does and how it does it?[/QUOTE]
 Sure.
```

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do

```
This is a simple for loop that goes through each of the URIS (file locations) specified in the variable $NAUTILUS_SCRIPT_SELECTED_URIS and performs the next part on each of them.
```

gnome-sudo "gnome-open $uri" &

```
This is what does the prompt for your password and, if correct, opens the variable uri (which is each file in turn as per the for loop) according to its mime-type.  The '&' puts the process "in the background" which means that each file is opened at the same time.  Without '&', each file would have to wait for the previous one to close before it was opening.  Think of it as a big field where everybody can stand at once (&) in contrast to a queue where only one person can be inside the field (no &).
```

done

```
Just closes off the for loop.

Every line starting with a '#' is a comment: this is code that will not be executed.  The first line, '#!/bin/sh', is a little different.  This is a special signal to the shell to execute the following with the 'sh' shell (usually bash).  Some scripts might have '#!/bin/ksh' or even '#!/usr/bin/perl' (which is for perl scripts).  For more information check out the [Advanced Bash-Scripting Guide](http://www.tldp.org/LDP/abs/html/).

---

### Post by Toastermax on 2005-04-12
> **Nis]Sure.
```

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS said:**
> Advanced Bash-Scripting Guide[/url].
still a bit fuzzy to me but  a bir of reading should give me some better questions to ask. thanks for the explanation.

---

### Post by connellr on 2005-04-12
[QUOTE=segrewb]I'm not going to pretend to be a programmer, but would the following work for kde?


```
#!/bin/sh
### openas-root:
###   konqueror script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

for uri in $KONQUEROR_SCRIPT_SELECTED_URIS; do
	kde-sudo "kde-open $uri" &
done

### end of file.
```

Thanks in advance

Segrewb[/QUOTE]

Thanks for your sugestion, but this doesn't seem to work in kde ...  First of all I dont think kde-sudo and kde-open exist (on my computer anyhow).  I tried modifying your script to use gksudo and gnome-open (gnome-open seems to work in KDE as well) but I couldn't find anywhere to put the script where it would work on the right-click menu.  Anyone else have any ideas?

---

### Post by 23meg on 2005-04-12
wow, i'm glad that this has been so useful to so many of you! rock on!

---

### Post by jiyuu0 on 2005-04-12
added to ubuntuguide.org
[http://ubuntuguide.org/#openfileasrootviarightclick](http://ubuntuguide.org/#openfileasrootviarightclick)

---

### Post by alexp on 2005-04-13
connellr,

[QUOTE=connellr]Thanks for your sugestion, but this doesn't seem to work in kde ... First of all I dont think kde-sudo and kde-open exist (on my computer anyhow). I tried modifying your script to use gksudo and gnome-open (gnome-open seems to work in KDE as well) but I couldn't find anywhere to put the script where it would work on the right-click menu. Anyone else have any ideas?[/QUOTE]

this won't work at all. Konqueror doesn't set the variable and AFAIK has no Nautilus-compatible scripting interface.

It might, however, be possible to do that for KDE, too, but this will involve digging deep into the Konqueror/DCOP API, which has various language bindings (including python, IIRC). If you are interested in hacking together something, you might want to have a look at [this site]("http://developer.kde.org/language-bindings/") -- good luck.

Regards,
Alexander

---

### Post by segrewb on 2005-04-13
[QUOTE=alexp]connellr,



this won't work at all. Konqueror doesn't set the variable and AFAIK has no Nautilus-compatible scripting interface.

It might, however, be possible to do that for KDE, too, but this will involve digging deep into the Konqueror/DCOP API, which has various language bindings (including python, IIRC). If you are interested in hacking together something, you might want to have a look at [this site]("http://developer.kde.org/language-bindings/") -- good luck.

Regards,
Alexander[/QUOTE]

Thanks for the link to the kde site.  Looks promising.  I'll check into it.

Thanks again,

Segrewb

---

### Post by thecrimsonking on 2005-04-17
I have been using these gems in KDE for years.


```
[Desktop Entry]
ServiceTypes=application/x-executable,application/x-shellscript,application/x-python,application/x-perl
Actions=runassu

[Desktop Action runassu]
Name=Run as Root
Name[de]=Als root ausfhren
Name[cs]=Spustit jako root
Name[sk]=Spusti&#357; ako root
Name[hu]=Futtatás rootként
Icon=kfm
Exec=kdesu -c
```

```
[Desktop Entry]
ServiceTypes=inode/directory,inode/directory-locked
Actions=Openassu

[Desktop Action Openassu]
Name=Open as Root
Name[de]=Als root &#65533;fnen
Name[cs]=Otev&#345;ít jako root
Name[sk]=Otvori&#357; ako root
Name[hu]=Megnyitás rootként
Icon=kfm
Exec=kdesu "konqueror --profile filemanagement %U"
``` 


Place the files here:
/usr/share/apps/konqueror/servicemenus

Now you will have run as root and open as root in your right click "action" menu.

---

### Post by arjay1 on 2005-07-23
crimsonking - hi I really need to have easier root access to modifying files etc as suggested in this thread.  I am using KDE

Could you explain a bit more about the two files you suggest creating?

1.  Do I just create these in a text editor?

2.  What do I call them?

3.  Do you have the english words for those in the files (!!!)

Thanks for any help you can give.

---

### Post by Tyche on 2005-07-24
My thanks.  I get tired of having to constantly either use sudo or a root terminal just to do a little configuration.  I've had as many as 4 root terminals open at a time, 3 of them locked into operating some program (such as gedit).  THIS should solve the problem.  Thanks

---

### Post by arjay1 on 2005-08-17
Anybody any idea why this script should not work in Debian?  I have faithfully created the script and it has put an "open as root" option on right click but it doesn't do anything?

Thanks from an ubuntu user who has moved on to debian but still comes back for old times sake

TIA!

---

### Post by Bomper on 2005-08-17
In my Debian Sarge:

       gksu "gedit %u" 

[http://www.ubuntuforums.org/misc.php?do=getsmilies&wysiwyg=0&forumid=58#](http://www.ubuntuforums.org/misc.php?do=getsmilies&wysiwyg=0&forumid=58#)

---

### Post by greyhound4334 on 2005-10-03
For KDE users, one trick I use is to use the fish protocol with kate to edit files as root.  To do this you need:
1. to set up a password for your root account (I don't know if this is the best/only way to do this, or what the security implications are):
% sudo -i
# passwd
2. install openssh 
apt-get install openssh-client openssh-server
3. in kate, when you want to open a file as root, "loopback" to your current machine using fish. In the location bar, type fish://root@host (<-- substitute the name of your host)
You'll be prompted to log in as root, and then be able to browse your filesystem and edit/save files as root.
BTW, fish is a secure protocol for transparently accessing files on remote systems over ssh.  It works very nicely.  Just use the uri above with the name of the host you want to access (e.g., fish://yourlogin@remotehost).  In this way you can securely read/edit/write files over the network with tools like kate and konqueror.

---

### Post by kanem on 2006-01-03
Sweet script. But I also like being able to open as root the folder I'm already in, and not have to go up one folder, then select the folder and run the script. I already had a script that did this (and only this; didn't open files as root). So I combined the two. Here's the result:
```
#!/bin/sh
### openas-root:
###   nautilus script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

if [ -n "$1" ]; then
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
        gnome-sudo "gnome-open $uri" &
done
else
gnome-sudo "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"
fi
### end of file.
```
If you have a file (or files) selected it opens it (them) with root. If no file is selected it opens the working directory with Nautilus as root.

---

### Post by hen3rz on 2006-01-17
Great tutorial. Thank you!

---

### Post by mech7 on 2006-07-09
~/.gnome2/nautilus-scripts/

Where is this ~ directory i can't find it anywhere ?:shock:

---

### Post by kanem on 2006-07-09
> **mech7 said:**
> ~/.gnome2/nautilus-scripts/

Where is this ~ directory i can't find it anywhere ?:shock:

Whenever you see a '~/' it means in your home directory, just replace '~/' with '/home/"you"/. In this case '/home/"you"/.gnome2/nautilus-scripts'

---

### Post by fulanitok on 2006-08-26
> **kanem said:**
> Sweet script. But I also like being able to open as root the folder I'm already in, and not have to go up one folder, then select the folder and run the script. I already had a script that did this (and only this; didn't open files as root). So I combined the two. Here's the result:
```
#!/bin/sh
### openas-root:
###   nautilus script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

if [ -n "$1" ]; then
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
        gnome-sudo "gnome-open $uri" &
done
else
gnome-sudo "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"
fi
### end of file.
```
If you have a file (or files) selected it opens it (them) with root. If no file is selected it opens the working directory with Nautilus as root.

Hi Kanem,

I'm new on Ubuntu (Linux), I did al what I have to do but when a right-clik on a file or folder and choose **Scripts** >> **Open as Root** nothing happens! :confused:  I'm really confused.

I'm trying to change my "**xorg.conf**" file, need to that 'cause I have 2 monitors on my PC.

It's seems to be very cool but won't work for me, I guess ... :| 

Thanks in advance guys

---

### Post by BC12398 on 2006-09-12
Here is what I do for KDE. Right click on panel, choose Add Non-KDE Application, the title and description can be anything that you like.  In the Command line arguments window type ```
kdesu konqueror
```
This will prompt you for the root password and then open Konqueror as root.

> **connellr said:**
> Thanks for your sugestion, but this doesn't seem to work in kde ...  First of all I dont think kde-sudo and kde-open exist (on my computer anyhow).  I tried modifying your script to use gksudo and gnome-open (gnome-open seems to work in KDE as well) but I couldn't find anywhere to put the script where it would work on the right-click menu.  Anyone else have any ideas?

---

### Post by BC12398 on 2006-09-12
Here is what I do for KDE. Right click on panel, choose Add Non-KDE Application, the title and description can be anything that you like.  In the Command line arguments window type ```
kdesu konqueror
```
This will prompt you for the root password and then open Konqueror as root.

> **connellr said:**
> Thanks for your sugestion, but this doesn't seem to work in kde ...  First of all I dont think kde-sudo and kde-open exist (on my computer anyhow).  I tried modifying your script to use gksudo and gnome-open (gnome-open seems to work in KDE as well) but I couldn't find anywhere to put the script where it would work on the right-click menu.  Anyone else have any ideas?

---

### Post by BC12398 on 2006-09-13
Here is what I do for KDE. Right click on panel, choose Add Non-KDE Application, the title and description can be anything that you like.  In the Command line arguments window type ```
kdesu konqueror
```
This will prompt you for the root password and then open Konqueror as root.

> **connellr said:**
> Thanks for your sugestion, but this doesn't seem to work in kde ...  First of all I dont think kde-sudo and kde-open exist (on my computer anyhow).  I tried modifying your script to use gksudo and gnome-open (gnome-open seems to work in KDE as well) but I couldn't find anywhere to put the script where it would work on the right-click menu.  Anyone else have any ideas?

---

### Post by JayTee on 2006-11-05
When I tried this out I'd get the Scripts option on the right click menu and I'd choose Open as root but nothing would happen. I had to modify it like this.
> #!/bin/sh
### openas-root:
###   nautilus script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	gksu "gnome-open $uri" &
done

### end of file.

---

### Post by NobodySpecial on 2006-11-06
Thanks for the update, Jaytee.  I've combined this with kanem's code.  It works perfectly in Edgy:

```
#!/bin/sh
### openas-root:
###   nautilus script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.
if [ -n "$1" ]; then
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
        gksu "gnome-open $uri" &
done
else
gksu "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"
fi
### end of file.

```

---

### Post by 3rdalbum on 2006-11-07
I know I'm helping along a seriously huge bump, but I'd like to suggest a modification to these scripts.

Put the attached file into /usr/share/pixmaps/

Instead of the "gksudo gnome-open %u" bit, try this:

```
gksudo -m "Enter your password to open the file as root." -i "/usr/share/pixmaps/ubuntu_gksudo.png" gnome-open %u

```

I've already gksudo'ed in the last 15 minutes, so I can't try it out yet. I think it should work though.

---

### Post by Stumpy842 on 2006-11-07
Arjay1:

For the KDE .desktop items mentioned by crimsonking, just create each one as a plain text file, but save it with a .desktop extension. The name doesn't really matter (I'm using runasroot.desktop and openasroot.desktop) but you must use the .desktop extension. Also the file(s) must be saved in the /usr/share/apps/konqueror/servicemenus folder.

Open a terminal and type:
```
kdesu konqueror
```
Enter your password.

In the location bar type:
```
/usr/share/apps/konqueror/servicemenus
```
Press Enter. You should now be in the servicemenus folder and you will see a number of files, all with the .desktop extension.

Right-click in a blank area inside the folder window and from the popup menu select Create New -> Text File. Type runasroot.desktop and press Enter. You will see a new file in the window named runasroot.desktop.

Right-click the runasroot.desktop filename and from the popup menu select Actions -> Edit as Root. The file will open in KWrite.

Now go to thecrimsonking's post (#38 in this thread) and select (highlight) all the text in the first code listing. Copy it with Ctrl-c. Switch back to KWrite and paste it in with Ctrl-v. Press Ctrl-s to save the file, and Ctrl-q to quit KWrite.

Now if you navigate to an executable file and right-click on it, you will see your new action Run as Root under the Actions menu item.

Repeat the instructions above to create the openasroot.desktop file in usr/share/apps/konqueror/servicemenus, and you should be good to go! :-D

---

### Post by frog3764 on 2007-04-11
Greetings to the Group - I just tried this launcher command and it didn't work.  Nothing happened!  I took out the %u and it worked one time, but not again.  What did I do wrong as I want to password protect a file folder and I like the way the launcher will do this?  This is a mess.  I replied to a different post and now it's not here.  I made a new launcher and used this code "gksudo gnome-open %u" and it didn't work.

Thanks from a newbie

Frog

---

### Post by nicketynick on 2007-04-13
I know this is surely a dumb question, but I'm a total nOOb hereabouts - why isn't this functionality native?  It seems to me that particularly with Linux/Ubuntu, the 'primary' user is going to be doing a lot of 'admin' work, so should have easy access to the tools to do it, rather than constantly having to mess around with sudo, etc. Am I being thick here?

---

### Post by emperorming on 2007-05-10
I tried adding this option in an attempt to quickly get at some files I'd stored on DVD that had root ownership.  I accidentally clicked on the launcher when trying to move it somewhere safe and for some reason, I can't access any DVD's or my flash drive on my normal user account anymore.  CD's are ok though. I need to restore my normal user account permissions to these devices & I'm a complete novice so ALL help is appreciated!! got any ideas? I'd hate to reinstall....Again!!

---

### Post by jcasebmw on 2007-05-10
I am still an Ubuntu pup and I am wondering if this trick will help me save this XGL script. I am unable to install beryl because I cant save this script. I can edit the script but I cant save it. It says that I don't have permission or something. I have been try to install beryl on my dell inspiron 9300 with ati x300 for a long long time with no luck.

Below is the section of the guide I am following that I cant complete because of the permission problem stated above.


* Write a script so Xgl can start on its own: 

sudo gedit /usr/local/bin/startxgl.sh

* Enter and save this script information: 

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:pbuffer &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

---

### Post by bsawler on 2007-06-18
Hi all, 

I am now a Linux user of 5 days now.  I am trying to change the bloody screen resolution but neither the i915Driver page or the FixVideoResolutionHowto page is working for me.  

Now I am trying to edit the xorg.conf file but as a user I cannot save back into the system directory.  So this topic seem to be another change for me to try and resolve my issue. 

When I type ```
gksudo "gnome-open %u"
``` in the terminal, it just drops down a line and refreshes the bottom tool bar.  Am I missing something. 

Regards,
BS

---

### Post by 3rdalbum on 2007-06-18
> **bsawler said:**
> 

When I type ```
gksudo "gnome-open %u"
``` in the terminal, it just drops down a line and refreshes the bottom tool bar.  Am I missing something. 

Yes, you are.

The command isn't intended for putting into the terminal - it's intended to create a drag and drop launcher to open files as root.

Create a launcher on your desktop, and set the command as the above. Now drag and drop the xorg.conf file to it. You will be prompted for your password, and then Gedit should open with the file.

---

### Post by bsawler on 2007-06-24
Sorry I missed the launcher part. 

I created a launcher by right clicking on the desktop > added the above code... and all works great. 

Thanks,
Bradley

---

### Post by buddah3618 on 2007-07-17
Hi

I am a new user to Linux/Ubuntu. I am having problems running certain programs, such as Firestarter, AVG Updates, ClamAV Updates. I keep getting a message that I don't have permission, that I need to run them as the "root". Will this work to resolve this issue with these programs? Also, I have already run this in "terminal", it asked me for a password, then disappeared. I'm gathering from reading the posts on here that this was supposed to create an icon on my desktop, it didn't do that. Nothing at all happened after I entered the password. I am the ONLY user on this pc. I entered the script as shown in the first entry, did I do something wrong? 

Thanks in advance
buddah3618 :)

---

### Post by scifipirate on 2007-08-02
Thank you for this :KS

---

### Post by scifipirate on 2007-08-02
> **buddah3618 said:**
> Hi

I am a new user to Linux/Ubuntu. I am having problems running certain programs, such as Firestarter, AVG Updates, ClamAV Updates. I keep getting a message that I don't have permission, that I need to run them as the "root". Will this work to resolve this issue with these programs? Also, I have already run this in "terminal", it asked me for a password, then disappeared. I'm gathering from reading the posts on here that this was supposed to create an icon on my desktop, it didn't do that. Nothing at all happened after I entered the password. I am the ONLY user on this pc. I entered the script as shown in the first entry, did I do something wrong? 

Thanks in advance
buddah3618 :)


you right click on your desktop then click "create a launcher" then put gksudo "gnome-open %u" in the command slot, give it a name and if u want a special icon. I'm thinking you were just putting the command in the terminal?

---

### Post by RoBo5050 on 2008-02-14
Hello forum members,
  I have Ubuntu 7.10 installed on my computer,but when I tried the drag and drop sudo launcher command with the create launcher dialog box, I got the following  error message:"Could not save launcher;the name of the launcher is not set."

What does this error message mean, and how do I correct it???

---

### Post by blkcat1028 on 2009-02-12
This is a great tip. I have used it to solve this little problem [http://ubuntuforums.org/showthread.php?t=827310](http://ubuntuforums.org/showthread.php?t=827310). Thank you very much op!

---

### Post by Endolith on 2009-02-13
Would xdg-open be better than gnome-open?

---

### Post by TurpoNieminen on 2009-03-08
> **kanem said:**
> Sweet script. But I also like being able to open as root the folder I'm already in, and not have to go up one folder, then select the folder and run the script. I already had a script that did this (and only this; didn't open files as root). So I combined the two. Here's the result:
```
#!/bin/sh
### openas-root:
###   nautilus script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

if [ -n "$1" ]; then
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
        gnome-sudo "gnome-open $uri" &
done
else
gnome-sudo "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"
fi
### end of file.
```
If you have a file (or files) selected it opens it (them) with root. If no file is selected it opens the working directory with Nautilus as root.

Sorry im new to this so i ask stupid questions:
Where i put this code?
Some existing file or create new one? What directory?

---

### Post by ariel on 2009-04-26
> **TurpoNieminen said:**
> Sorry im new to this so i ask stupid questions:
Where i put this code?
Some existing file or create new one? What directory?

You have to create a new file in ~/.gnome2/nautilus-scripts, give it any name and put the above as content. Then set the "Allow executing file as program" using nautilus file properties.

Then the name you chose should show up in right-click  context menu when you select a file in nautilus, under "Scripts".

However, the script above does not work in Jaunty / 9.04. I don't know why. If all you need is to edit the file as root, then this simpler script does work in 9.04:


```
#! /bin/sh

# Usage:
# 1) From Nautilus (assumes nautilus-scripts is setup): right-click on a single file, select the script link
#

gksudo gedit "$1"

```

I'd rather use the more generic solution where gnome chooses the appropriate application based on the file type instead of hardcoding to gedit. I anyone can fix the original URI + gnome-open -based script that would be awesome. For some reason in all recent ubuntu versions the generic script stopped working.

---

### Post by mc4man on 2009-04-26
Only have jaunty on a live cd and for my hardy install actually prefer using nautilus actions instead for such activities

This works fine on the live cd for both files and directories

```
#!/bin/sh
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do gksudo "gnome-open $uri" &
done
```

---

### Post by Skip Da Shu on 2009-05-19
> Originally Posted by TurpoNieminen View Post
Sorry im new to this so i ask stupid questions:
Where i put this code?
Some existing file or create new one? What directory?> **ariel said:**
> You have to create a new file in ~/.gnome2/nautilus-scripts, give it any name and put the above as content. Then set the "Allow executing file as program" using nautilus file properties.

Then the name you chose should show up in right-click  context menu when you select a file in nautilus, under "Scripts".

However, the script above does not work in Jaunty / 9.04. I don't know why. If all you need is to edit the file as root, then this simpler script does work in 9.04:


```
#! /bin/sh
# Usage:
# 1) From Nautilus (assumes nautilus-scripts is setup): right-click on a single file, select the script link
#

gksudo gedit "$1"

```
I'd rather use the more generic solution where gnome chooses the appropriate application based on the file type instead of hardcoding to gedit. I anyone can fix the original URI + gnome-open -based script that would be awesome. For some reason in all recent ubuntu versions the generic script stopped working.

There was an update to the quoted (by TurpoNieminen) code about two or 3 pages back posted by JayTee & NobodySpecial [**_[COLOR="RoyalBlue"]HERE[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=1725065&postcount=53").  The updated version changed to using "gksu" instead of "gnome-sudo" and this updated version works for me on Intrepid (v8.10):

My 'open as root' file in ~/.gnome2/nautilus-scripts
```
#!/bin/sh
### openas-root:
###   nautilus script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

if [ -n "$1" ]; then
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
        gksu "gnome-open $uri" &
done
else
gksu "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"
fi
```

PS: Thanx JayTee for the fix, NobodySpecial for updating the 'combo' script.

---

### Post by Skip Da Shu on 2009-06-02
BTW, Anybody know how to implement this in Xubuntu using Thunar?

---

### Post by Jedi Knight on 2010-01-02
Excellent information, thanks to all who contributed.

---

### Post by malty on 2010-02-18
Tried in 9.04, got......
john@john-desktop:~$ gksudo "gnome-open %u"
Error showing url: Error stating file '/home/john/%u': No such file or directory

Any suggestions please

---

### Post by h8grip on 2010-02-19
> **23meg said:**
> Create a launcher with the following command:

```
gksudo "gnome-open %u"
```When you drag and drop any file on this launcher (it's useful to put it on the desktop or on a panel), it will be opened as root with its own associated application. This is helpful especially when you're editing config files owned by root, since they will be opened as read only by default with gedit, etc.


Sorry im n00b as to Linux but I am guessing this will only work in GNOME, can it be adapted for xfce easily?

Thanks

---

### Post by airtonix on 2010-02-19
or you can just : 
```

sudo apt-get install nautilus-gksu

```

---

### Post by h8grip on 2010-02-19
Nautilus is some sort of file manager yes? What exactly is it for?

---

### Post by kdford on 2010-07-19
That is great, thanks for the tip.

I have a related question.  Sometimes I want to drag and drop a file into a protected location.  For example, I am reimaging my machine and I have backed up (from the old machine), my /etc/hosts file, which contains host entries for various virtual machines I use as test/dev targets.

Anyway, my user does not have privileges to copy files into /etc, so I would use sudo to perform that operation.  (easy enough).

When I try to drag and drop, using nautilus, from my backup file into the /etc folder, I am denied (of course).  Is there a way to drag and drop in "sudo-mode", into a location that requires root authority?

Thanks,

Kevin

---

### Post by libssd on 2010-07-19
This has been an interesting thread, and while the original idea wasn't of particular use to me (sudo gedit works just fine), I like the idea of being able to copy a file to a restricted directory just by dragging it from another directory, as this approach potentially avoids dealing with long pathnames.

---

### Post by lkjoel on 2010-07-19
> **segrewb said:**
> I'm not going to pretend to be a programmer, but would the following work for kde?


```
#!/bin/sh
### openas-root:
###   konqueror script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

for uri in $KONQUEROR_SCRIPT_SELECTED_URIS; do
    kde-sudo "kde-open $uri" &
done

### end of file.
```Thanks in advance

Segrewb
```
#!/bin/**ba**sh
### openas-root:
###   konqueror script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

for uri in $KONQUEROR_SCRIPT_SELECTED_URIS; do
    kdesudo "kde-open $uri" &
**# instead of kde-sudo**
done

### end of file.
```

---

### Post by Ricalsin on 2010-12-02
> **Nis said:**
> As and you shall receive. :)  Put the following into ~/.gnome2/nautilus-scripts/Open\ as\ root
```

#!/bin/sh
gksudo "gnome-open  $NAUTILUS_SCRIPT_SELECTED_URIS"

```
Then make it executable with
```

chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root

```

Noob to Linux - several years late.  :shock:

"~/.gnome2/nautilus-scripts" is an empty directory.  
What/where are you wanting with the "/Open\ as\ root" ??  

The chmod I get.  The gksudo line I get.  

I'm not seeing how to connect the dots.  

Thanks

---

### Post by david.rahrer on 2010-12-16
> **Ricalsin said:**
> Noob to Linux - several years late.  :shock:

"~/.gnome2/nautilus-scripts" is an empty directory.  
What/where are you wanting with the "/Open\ as\ root" ??  

The chmod I get.  The gksudo line I get.  

I'm not seeing how to connect the dots.  

Thanks

The "/Open\ as\ root" part is just the name of the script file you are supposed to create in that folder.  The "\" are to deal with the spaces in "Open as root" I believe.  You could also navigate to "~/.gnome2/nautilus-scripts" in Nautilus and Right-Click > Create Document > Empty File and name it "Open as root". Then open in gedit (left click) and past in the following (most recent version):

```
#!/bin/sh
### openas-root:
###   nautilus script for opening the selected files as superuser (uid=0),
###   utilizing the appropriate applications.

if [ -n "$1" ]; then
for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
        gksu "gnome-open $uri" &
done
else
gksu "nautilus --no-desktop $NAUTILUS_SCRIPT_CURRENT_URI"
fi
```

Make it executable, either by chmod or Right Click > Properties > Permissions and you should be set.  When you right click on a file or empty space in a folder, you can select Scripts > Open as root and it should ask for your password and then open the file or the folder respectively.

---

### Post by vikonen on 2010-12-30
> **Nis said:**
> As and you shall receive. :)  Put the following into ~/.gnome2/nautilus-scripts/Open\ as\ root
```

#!/bin/sh
gksudo "gnome-open  $NAUTILUS_SCRIPT_SELECTED_URIS"

```
Then make it executable with
```

chmod +x ~/.gnome2/nautilus-scripts/Open\ as\ root

```


As I was trying to create a send-to menu item to send files to gedit, I found your code very useful.

Here's how I modified it:

```
#!/bin/sh
gnome-text-editor $NAUTILUS_SCRIPT_SELECTED_URIS
```

saved it in ~/.gnome2/nautilus-scripts, as executable.

After this, I get a nifty right-click menu titled "Scripts" in Nautilus where I can activate the script after right clicking a file in nautilus. This is very handy when trying to open files that don't open with a text editor by default.

---

### Post by Jones235 on 2012-02-02
> **23meg said:**
> Create a launcher with the following command:

```
gksudo "gnome-open %u"
```When you drag and drop any file on this launcher (it's useful to put it on the desktop or on a panel), it will be opened as root with its own associated application. This is helpful especially when you're editing config files owned by root, since they will be opened as read only by default with gedit, etc.

I could really use this utility to open and edit my xorg file but it does not work for me...

If I run the terminal command in the first post I get multiple error messages:
"(gksudo:5330): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Nothing happens after that...

I'm too much of a newbie on ubuntu 11.1 to know wht this means and how to fix it.  Perhaps someone could help?

---

### Post by mc4man on 2012-02-02
> **Jones235 said:**
> I could really use this utility to open and edit my xorg file but it does not work for me...

If I run the terminal command in the first post I get multiple error messages:
"(gksudo:5330): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Nothing happens after that...

I'm too much of a newbie on ubuntu 11.1 to know wht this means and how to fix it.  Perhaps someone could help?
This thread is old & somewhat not maintained

For 11.10/12.04 if you want the same deal for a Desktop DnD launcher you  could try this
In terminal

```
gedit ~/Desktop/openit.desktop
```

Paste this in, save, close gedit

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=gksudo "xdg-open %u"
Name=Open as Root
Icon=gnome-panel-launcher

```

finish with
```
chmod u+x ~/Desktop/openit.desktop
```

Icon= can be generally be whatever you wish, usually best to full path if not a standard
Name= can be as desired

For a unity launcher DnD then you'd need to add an appropiate MimeType= line to the .desktop

---

### Post by klompa on 2012-06-30
> **mc4man said:**
> This thread is old & somewhat not maintained

For 11.10/12.04 if you want the same deal for a Desktop DnD launcher you  could try this
In terminal

```
gedit ~/Desktop/openit.desktop
```

Paste this in, save, close gedit

```
#!/usr/bin/env xdg-open

[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Exec=gksudo "xdg-open %u"
Name=Open as Root
Icon=gnome-panel-launcher

```

finish with
```
chmod u+x ~/Desktop/openit.desktop
```

Icon= can be generally be whatever you wish, usually best to full path if not a standard
Name= can be as desired

For a unity launcher DnD then you'd need to add an appropiate MimeType= line to the .desktop

thanks mate sorted me out to

---

### Post by Jonathan Precise on 2013-09-09
> **23meg said:**
> Create a launcher with the following command:

```
gksudo "gnome-open %u"
```

When you drag and drop any file on this launcher (it's useful to put it on the desktop or on a panel), it will be opened as root with its own associated application. This is helpful especially when you're editing config files owned by root, since they will be opened as read only by default with gedit, etc.

I have a variation that works with newer version of ubuntu (12.04+), xubuntu, and lubuntu.

For the command put in:

```
gksu "xdg-open %u"
```

for KDE/Kubuntu:

```
kdesudo "xdg-open %u"
```

[INDENT]--Hope it helps![/INDENT]

---

