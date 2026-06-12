---
title: "thoughts on IBM lotus symphony"
date: 2007-09-18
forum: The Cafe
---

### Post by BDNiner on 2007-09-18
[http://symphony.lotus.com](http://symphony.lotus.com)

I have not found a post on this subject in these forums yet. What are people's thoughts on IBM and their plans for open office. If there is decent integration with lotus notes and domino servers then i think this product will be great. I for one would like more products aimed at the corporate desktop market. It i9s currently only available for RPM based distros like SUSE and Redhat. Maybe someone here will figure out how to get it to run on Ubuntu.

---

### Post by dkpelder on 2007-09-18
Actually, I found that it runs with no modification on Ubuntu.  I simply downloaded the Linux file (which does require registration) and it worked as is.

---

### Post by dkpelder on 2007-09-18
One thing that I forgot to mention is that the installer seems to want to run with root privileges which isn't too unusual but the applications themselves also want to run with the same level of privilege.  I also forgot to mention that it ran fine for me from the command line.  I just tried it from the menu shortcut and did not have the same success so I'm trying to figure out how to tweak the menu item to allow a successful invocation from there.

---

### Post by gers4302 on 2007-09-18
I'm experiencing the same problem.  It installs fine on Gutsy, but must be run via sudo.

The font rendering is a bit nasty.  For me, 10pt Arial looks fine, but 10pt Arial Bold looks like a blobby mess.

---

### Post by Permafrost91 on 2007-09-18
I installed the Linux version on 32 bit Gusy which, as already mentioned, required sudo privileges. But unlike dkpelder or gers4302, my installation (into /opt/ibm/lotus/Symphony, the default install folder), I do not require sudo privileges to run LS. The menu shortcuts did not work for me at first but now they do (not sure what changed with them). The only thing I can think of is that I associated LS with all office documents on my computer (through LS's preferences). I haven't really had many problems since then (a few crashes here or there though). It's definitely still beta quality.

By the way, is this based on OpenOffice.org? IBM did send 30 some developers over to that dev-team and I was wondering whether LS uses OOo's core.

---

### Post by Permafrost91 on 2007-09-18
I just now saw that gers4302 posted a second before me and I have to agree that bold fonts don't look very pretty (although I have to admit that I'm having the same problems in OOo with MS Office documents).

---

### Post by LaRoza on 2007-09-18
Is it for anyone else downloading slowly? 4-10 kbs for me, while everything else is in th 100's.

---

### Post by kaamos on 2007-09-18
IBM seems to be rolling out every possible desktop app as eclipse add-ons.. But it was STILL a surprise to notice that it was the case with this one as well!

---

### Post by dkpelder on 2007-09-18
Yes this is based on Open Office and I figured out (for me at least) how to get the menu items working.  The installation creates a <home directory>/lotus directory.  For me the initial owner for that directory was root as was the initial group.  Once I changed the owner and group to my user name and my group, everything worked as it should have. 

It seems that IBM underestimated the amount of traffic they would receive because the download speed for this is pretty slow right now (and has been since this morning).

---

### Post by Permafrost91 on 2007-09-18
ah, that makes sense ... I deleted that directory thinking it was only needed during the install but going back to my home folder now I see that it has since been recreated. Not sure I like that though ... is there a way to not have this "lotus" folder created? Or at least keep it hidden?

---

### Post by dkpelder on 2007-09-18
I suspect that you'd have to talk to the fine folks at Lotus to get that changed.

---

### Post by stmiller on 2007-09-18
I find it interesting that it is all java based, but the release is only for x86 Linux, not PowerPC Linux. IBM sells PowerPC workstations with Suse and Redhat PPC. IBM even develops their own java for PowerPC Linux. Interesting... is all.

Apart from that, it seems like a good app. This will help prompt .odt as a standard.

---

### Post by cipheroid on 2007-09-18
First (and last) impressions on Symphony:

Ugh. This thing is a bloated piece of molasses-covered dreck compared to OpenOffice 2.2 -- at least running on an older machine like mine (1.6GHz P4 w/256MB RAM).

Typing inside a new document, I overran the keyboard buffer within a few words and had to wait a couple of seconds for the program to catch up. Every sentence. There's no way I could create a lengthy document in this program.

The same operation in OpenOffice, on the other hand, gave me no delays, as keyboard response was instantaneous and in real-time.

Font rendering was fairly equivalent between OO and Symphony, so I didn't see much difference there. But Symphony's Java-based dialog panels and menus are butt-ugly; as if GUIs were in their infancy and proportional-spaced fonts were the coming thing.

This total lack of quality in the user experience puzzled me at first.

Then I remembered the last IBM-developed word processor I used: DisplayWrite for DOS, ca. 1992. While competitors like Wordstar or MS Word were written in assembler or C for performance, DisplayWrite klunked along like some bizarre experiment in a kludgey, JCL-scripted runtime environment for DOS, an obvious port from their mainframe-oriented development model.

With Symphony, and its reliance on the Eclipse environment, I see IBM is still following the tenets of PC software engineering it used more than a decade ago: the more layers of abstraction between the application and the machine, the better -- even if they're not needed.

Yes, yes, it's quite possible that some of these performance issues will be fixed in the release candidates (I doubt it, though). And perhaps a beefier machine with more memory would remove some of the response lag. And perhaps the Windows version doesn't suffer from the horrible lack of fit and finish that the Linux version exhibits. I concede all that. But I'm not interested in running Symphony in Windows, I'm not interested in upgrading this old machine, and OpenOffice is crisp and snappy in Linux by comparison so I don't see why Symphony can't be the same.

Okay, that said, don't let this dissuade you from trying Symphony for yourself. This has been my personal experience with it, and the keyboard lag was a deal-breaker for me. Of course, YMMV. There might be some features in Symphony that make it a must-have for you. Me, I'll stick with OpenOffice.

---

### Post by jackkerouac on 2007-09-18
I can't even get the damned thing to install. Everytime I run the setup.bin, the installer launches but I get a blank dialogue box. I also get the error:

```
 Failed to parse property value " GTK_SHADOW_OUT " for `GtkScrolledWindow::shadow-type'
```

For now, I think I'll stick with OpenOffice.

---

### Post by p_quarles on 2007-09-18
Based on what I read this morning, LS basically *is* OpenOffice, with IBM's modifications. The news here is that there are new OOo developers, and a really big and trusted name behind it. Apart from that, I doubt this will really be a mature project for a few months yet. Plus, it's open-source, so when it is mature OOo will be able to incorporate any improvements. 

In short: it's great news, but won't have any impact on our lives for a while.

---

### Post by EricCFlem on 2007-09-18
> **jackkerouac said:**
> I can't even get the damned thing to install. Everytime I run the setup.bin, the installer launches but I get a blank dialogue box. I also get the error:

```
 Failed to parse property value " GTK_SHADOW_OUT " for `GtkScrolledWindow::shadow-type'
```

For now, I think I'll stick with OpenOffice.


I'd had the exact same trouble, and it wasn't until I read your post that I had an idea of what might be going on (since my error message said something about Clearlooks.

Anyway, I'd bet you have desktop effects turned on.  I did, and got that same blank dialog box.  Once I turned off desktop effects, that blank dialog box suddenly had words in it!  I'm finishing up the installation right now, but won't know for a while whether having desktop effects turned on affects how the program runs, or only how the installer behaves.

Hope that helped.

---

### Post by azarethroy on 2007-09-18
Hey guys, apologies I'm new to Ubuntu. Can you tell me how to install the Lotus Symphony file? It has a .bin extension so is not a self-executable like .debs are 

I got this error when I did sudo apt-get install

Couldn't find package IBM_Lotus_Symphony_Linux.bin

---

### Post by icksa on 2007-09-18
Hi:
I managed to get it installed, but I can't find the executable to actually run it! It installed in /opt/ibm/lotus/Symphony but there don't seem to be any executable files anywhere that I can see.

I know that it runs, because there is an option to start it when the install completes, and that works fine...

Does anyone know what the executable is called?

Thanks

---

### Post by icksa on 2007-09-18
Hi azarethroy:

Using the command line, navagate to the directory where you downloaded it. (for example, if you downloaded to the desktop, open the terminal and type "cd Desktop")

Then type the following commands:
chmod a+x IBM_Lotus_Symphony_Linux.bin
./IBM_Lotus_Symphony_Linux.bin
cd IBM_Lotus_Symphony_Linux
sudo ./setup.bin

---

### Post by rbmorse on 2007-09-19
I got it installed without any problem (thanks, collectively to this thread) but have to say it looks like the the OOo suite did back when it was still Open Office. 

Didn't like a 90,000 word document (book) that OOo 2.2 and 2.3 (Gutsy) handle with ease.  Also noticed the line spacing in headers and footers is borked.  Changing fonts is an adventure, but I like the idea of the control panel better than contextual, floating dynamic "ribbons" or toolbars.  Handles inserting graphics, but it's very slow. 

If the 35 programmers IBM is putting on the project were formerly associated with it, I'm not sure we're getting all that good of a deal. 

Hard to believe I'm saying this, but the IBM/Lotus offering lacks polish compared to it's OOo relation. 

One other thing:  IT CHANGED THE FILE ASSOCIATIONS FOR MY ODT DOCUMENTS WITHOUT ASKING. Bad, IBM. Bad, bad, bad.  The King shall hear of this!

---

### Post by dkpelder on 2007-09-19
Azarethroy,

icksa's right on the money but just in case you are very new to the *nix world, in between the chmod and cd commands you need to run:

./IBM_Lotus_Symphony_Linux.bin

Icksa,

The executable is a pain to get to.  Here it is for Documents (the Symphony word processor):

"/opt/ibm/lotus/Symphony/framework/shared/eclipse/plugins/com.ibm.productivity.tools.standalone.addin_3.0.0.20070913-1045/apps/Lotus Symphony Documents"

To launch a spreadsheet the command is exactly the same except with Spreadsheets at the end instead of Documents and the same goes for Presentations.

---

### Post by sloggerkhan on 2007-09-19
different isue here... I installed before I saw this thread, but couldn't get things to launch as my user (didn't notice the the new folder owned by root in my user folder....)
In any case, I deleted the install directory (the one in opt) but now when I try to install again, it errors out at 93%..  and doesn't make a new version of the lotus folder in my /home/$username folder....
Any chance I have to log out or something?

---

### Post by not_a_techie on 2007-09-19
Hi Guys
  I am a new convert to Linux and started using Ubuntu Feisty recently. I wanted to install and try the new Symphony suite. I followed instructions to install .bin files posted elsewhere. I extracted the files, changed directory to the correct one and tried to install via sudo, but for some reason, the installation does not go beyond the blank installation wizard. Please advise.

---

### Post by Perfex on 2007-09-19
Okay  decided to install this, well needless to say I don't care for it much.

How would I go about uninstalling it, I installed it in it's default location opt/ibm/lotus

I tried just deleting the ibm directory in opt, and removed the menu entry's, but it is still associated in the open with window, and it's associated it self with the open office icons (my files).

I put it all back where it used to be, would anyone be generous enough to how to completely uninstall this, as I am still unsure of the linux's way of directory structure on installing, etc.

Thank you in advance

---

### Post by ryno519 on 2007-09-19
> **not_a_techie said:**
> Hi Guys
  I am a new convert to Linux and started using Ubuntu Feisty recently. I wanted to install and try the new Symphony suite. I followed instructions to install .bin files posted elsewhere. I extracted the files, changed directory to the correct one and tried to install via sudo, but for some reason, the installation does not go beyond the blank installation wizard. Please advise.

Are you running compiz fusion or gutsy? Symphony's installer runs off of its own standalone JRE which appears to be too old to work with compiz fusion (which is installed on gutsy by default). Turn off your desktop effects and you should be able to see it.

---

### Post by not_a_techie on 2007-09-19
Thanks, that worked. Weird, to me anyway, since I am still learning to use a whole new OS. Thanks a lot again.

---

### Post by karellen on 2007-09-19
don't know, don't care. I find openoffice just enough for me

---

### Post by :LJ: on 2007-09-19
You know, I'd love to try Symphony, just for the gas. Unfortunately, even running the downloaded .bin I just get "permission denied". Any ideas?

---

### Post by dasunst3r on 2007-09-19
> **:LJ: said:**
> You know, I'd love to try Symphony, just for the gas. Unfortunately, even running the downloaded .bin I just get "permission denied". Any ideas?That is because you need to give it permission to execute.  To do so, you can either:
Use the terminal - *cd* into the directory the file is located in and then *chmod +x {file}*.
Use point-n-click - Right-click on the file, go to Properties, go to Permissions tab, make sure "Allow executing file as program" is checked, close out

Now, for my thoughts on Symphony: It makes OpenOffice.org feel like a rabbit.  The interface looks nice, but running it off the Eclipse platform significantly bogs it down.  I think I'll stay with OpenOffice.org for now.

---

### Post by not_a_techie on 2007-09-19
I ended up staying up late night just to install this demon. But it will not open at all. For some reason, I can right click on documents and see an option for "open with Symphony". But nothing happens, I am sure something is trying to open it. I cannot open the application through "applications>office>symphony (anything) either. I accept I am a noob with linux, I am not a tech, like I say in my username, but nothing was this frustrating so far. I even installed Bluetooth for my old laptop. I dont know if it is a memory issue, I have Pentium M with 512 MB RAM. Any suggestions/help as ususal?

edit: I apologize if it is not the appropriate thread for help, would appreciate it if someone could point me in the right direction.

---

### Post by NoWhereMan on 2007-09-19
any way to remove all of the associations along with all references? once uninstalled I still get its crappy non-alpha icon everywhere

---

### Post by icksa on 2007-09-19
Hi Sloggerkhan:
I did the same thing, and had the same problem. I discovered that the install program put a directory in /root. Once I went into /root and deleted that directory I was able to reinstall it and run it...

I hope this helps

---

### Post by kaamos on 2007-09-19
> **NoWhereMan said:**
> any way to remove all of the associations along with all references? once uninstalled I still get its crappy non-alpha icon everywhere

The icons are in /usr/share/icons/hicolor/ + ~/.local/share/icons/hicolor/ and the file associations in /usr/share/mime/application/

---

### Post by cipheroid on 2007-09-19
@perfex:

I deleted my Symphony installation this way: there's a subdirectory named _uninst somewhere under /opt/ibm/lotus/Symphony/. In a terminal window, I cd'ed to it and ran "sudo ./uninstall.bin" or whatever the name of the uninstall program was. Sorry I can't remember the exact names, as my folders are gone, but you'll be able to figure it out.

One other thing: I got some errors during the uninstall, but they did not appear to affect the final result. All associated files were removed.

---

### Post by :LJ: on 2007-09-19
> **dasunst3r said:**
> That is because you need to give it permission to execute.  To do so, you can either:
Use the terminal - *cd* into the directory the file is located in and then *chmod +x {file}*.
Use point-n-click - Right-click on the file, go to Properties, go to Permissions tab, make sure "Allow executing file as program" is checked, close out.

Been there, done that. Sorry, should've mentioned it (believe it or not, I'm not exactly a n00b). Anyway, even went so far as to "chmod 777 ...." - still get the permissions error.

Actually, scratch that. I've just copied it into /root, and it worked fine. Most odd indeed. 'Course, I then get a lovely blank window instead of an installation wizard. Time to go reading....

---

### Post by NoWhereMan on 2007-09-19
> **kaamos said:**
> The icons are in /usr/share/icons/hicolor/ + ~/.local/share/icons/hicolor/ and the file associations in /usr/share/mime/application/

thanks I had already found and removed all, I had also to clear .local/share/ ! otherwise I was still getting that crap -,-

@cipheroid I did the uninstall that way but it left all of its icons and associations wherever. yech.

---

### Post by jetpeach on 2007-09-19
wow i was interested in trying LS, but now that i've read this thread i will definitely pass. i think i'll wait till they give us a .DEB package file and at least a release candidate.

fun to read about people's first impressions though, now i don't have to spend the time dinking around going through what sounds like a terrible install (and uninstall) for this...

---

### Post by NoWhereMan on 2007-09-19
right choice, jetpeach, by the way, even though is quite slow on start I think it might be promising; still the presentation package is worse than openoffice's, it still lacks support to adding animations (I know it's in beta, but I suppose the features of a beta should be frozen)... I like the modeless feedback on the sidebar

well, we'll see...

---

### Post by dkpelder on 2007-09-19
not_a_techie,

Check your user directory (/home/<username>) for a directory called lotus using the command:

ll -d lotus

That will probably come back with an entry something like this:

drwxr-xr-x 3 root root 4096 2007-09-18 11:49 lotus

In order to get the applications to launch successfully, run the following commands:

sudo chown -R <username> lotus
sudo chgrp -R <username> lotus

After you do all of that you should be able to run the applications successfully.

---

### Post by SunnyRabbiera on 2007-09-19
well the installer definately needs work, but hey if this is opensource then the fun can begin once its out :D

---

### Post by mostwanted on 2007-09-19
What licence is it? Since OO.o is open source, I would imagine this (or parts of it) is too, but I don't see anything about the licence anywhere on IBM's website.

---

### Post by trash.eighty on 2007-09-19
> **:LJ: said:**
> Been there, done that. Sorry, should've mentioned it (believe it or not, I'm not exactly a n00b). Anyway, even went so far as to "chmod 777 ...." - still get the permissions error.

Actually, scratch that. I've just copied it into /root, and it worked fine. Most odd indeed. 'Course, I then get a lovely blank window instead of an installation wizard. Time to go reading....
If you have compiz on, switch it off.  Compiz and certain Java toolkits don't seem to get along all that well.  Symphony itself works fine, but the installer needs compiz off

---

### Post by trash.eighty on 2007-09-19
> **SunnyRabbiera said:**
> well the installer definately needs work, but hey if this is opensource then the fun can begin once its out :D
The installer doesn't need work.
The installer needs to be scrapped, and Symphony needs to be put out properly as .debs and .rpms, like most good-standing Linux citizens.

---

### Post by SunnyRabbiera on 2007-09-19
> **mostwanted said:**
> What licence is it? Since OO.o is open source, I would imagine this (or parts of it) is too, but I don't see anything about the licence anywhere on IBM's website.

currently its under IBM's license but it might go GPL

---

### Post by motang on 2007-09-19
When I tried to download it I was required to log in and so I just gave up as I tried to register yesterday with no luck.  But other than that I found the Windows installer on Softpedia and gave the Office suite a spin yesterday.  It is pretty cool, and I really like the UI, and the tab feature.

---

### Post by not_a_techie on 2007-09-19
> **dkpelder said:**
> not_a_techie,

Check your user directory (/home/<username>) for a directory called lotus using the command:

ll -d lotus

That will probably come back with an entry something like this:

drwxr-xr-x 3 root root 4096 2007-09-18 11:49 lotus

In order to get the applications to launch successfully, run the following commands:

sudo chown -R <username> lotus
sudo chgrp -R <username> lotus

After you do all of that you should be able to run the applications successfully.

Hi elder
  Thanks, that worked. I dont know about this application tho. Feels very bulky and slow. Probably wont use it very much (not at all) until someone reports a good build. Thanks all!

---

### Post by azarethroy on 2007-09-20
@icksa

You rock, mate. Worked like a charm. Thanks! :popcorn:

(Note for others: I had to also disable "Desktop Effects")

---

### Post by Plutonium on 2007-09-20
Hi every one,

I did my try on installing LS and... well, as much as you I suffer it... the built-in Java   gave me several problems. Any way I managed to install it. This is after following this thread and following some of the instructions displayed in the LS download website: 

[http://symphony.lotus.com/software/lotus/symphony/installGuide.jspa](http://symphony.lotus.com/software/lotus/symphony/installGuide.jspa)

The simple way is: 
1. follow the instructions in the web above

2. As every one has noticed, the installation demands root rights

3. Once you are in the point 5. from the web instructions: 'Execute the install command setup.bin within the local folder and follow the installation screens' ... you must open a terminal and change directory to the location were the setup.bin file is set: cd /change/directory/whatever/IBM_Lotus_Symphony_Linux

4. Being in that directory execute: sudo ./setup.bin ... this will do the job easy!

5. Follow the rest of instructions in this thread to reconfigure it ...

Best luck

---

### Post by jrusso2 on 2007-09-20
I don't know why anyone would use this over open office.  Maybe if they would have included the Lotus Notes client.

---

### Post by jimbo99 on 2007-09-20
IBM_Lotus_Symphony_Linux.bin: 1: Syntax error: "(" unexpected

That's what the installer gives me.

---

### Post by ryno519 on 2007-09-20
> **jimbo99 said:**
> IBM_Lotus_Symphony_Linux.bin: 1: Syntax error: "(" unexpected

That's what the installer gives me.

Remember to give it execute permissions before you try and execute it.

```
chmod +x IBM_Lotus_Symphony_Linux.bin
```

---

### Post by Randy Winchester on 2007-09-20
Aaaarrrrggh!

[LIST=1]
[*]Don't install this if you have Beryl running
[*]What a mess.  Have to reboot before this shows up in the Apps menu
[*]Won't run anyway if you click it in the Apps menu
[*]sudo nautilus
[*]drag it all to the trash and then select "delete from trash"
[*]Yikes!
[/LIST]

Double Aaarrrghhh!

Nice presentation templates though.

---

### Post by jimbo99 on 2007-09-20
When you attempt to sudo the install.  It will generate an error.  When you do a sudo -i and then execute the install it works.

If you have compiz active instead of say metacity as the window manager the buttons, etc on the install wizard are not visible.  If you switch it you'll be able to see the buttons.  that is if you switch from compiz to metacity.

After that, of course, it is difficult to find the icon to launch the program.

---

### Post by n3tfury on 2007-09-20
> **karellen said:**
> don't know, don't care. I find openoffice just enough for me

then why bother posting if you "don't care"

---

### Post by tronkel on 2007-09-21
Lotus Symphony has a long way to go before it could knock Office 2007 off its pedestal. It's nowhere near Openoffice  2.3 either - yet.

What it has got, is a quite attractive interface. If the basic engine was upgraded to something a bit more modern, I think it would indeed carve out a nice little niche for itself - eventually.

It was dead slow on my old Compaq 400Mhz 256MB RAM. Really needs the 1G Ram as stated in the system requirements. I wonder why they designed it to run via a Java runtime. 

Give it time though. This is only a beta version

---

### Post by louis_nichols on 2007-09-21
In my case, it runs awfully slow. I mean, my computer is not that new, but the speed LS has on it makes it seem like an abacus. The installation alone took more than 1 hour.

Then, just to start it, I saw the splash screen for about 5 minutes. And I also see the bad rendering of bold fonts.

So, for me, it's a no-no at the moment. However, I would like to see some of that artwork in OOo...

---

### Post by GooglePlexity on 2007-09-21
Could someone who knows what they're doing please be so kind as to post step-by-step directions on how to restore the OpenOffice.org icons? Thanks.

---

### Post by ryno519 on 2007-09-21
> **GooglePlexity said:**
> Could someone who knows what they're doing please be so kind as to post step-by-step directions on how to restore the OpenOffice.org icons? Thanks.

I too would be interested in this.

---

### Post by jppaynesr on 2007-09-21
It changed my file associations also, and worse, it changed all the default file ICONS. Because it simply would not run on my Ubuntu, I un-installed it, but they don't provide an uninstall script, you must do it all by hand. Yuck. Newbies, do NOT install this package. Wait for something can install & uninstall via synaptic.

Does anyone know how to put the icons back the way they were, globally?

---

### Post by NoWhereMan on 2007-09-22
> **jppaynesr said:**
> It changed my file associations also, and worse, it changed all the default file ICONS. Because it simply would not run on my Ubuntu, I un-installed it, but they don't provide an uninstall script, you must do it all by hand. Yuck. Newbies, do NOT install this package. Wait for something can install & uninstall via synaptic.

Does anyone know how to put the icons back the way they were, globally?

answer by :LJ: and me here [http://ubuntuforums.org/showthread.php?t=553953&page=4](http://ubuntuforums.org/showthread.php?t=553953&page=4)

btw there was an uninstaller in /opt/sun/Symphony/_uninstaller IIRC

anyway it didn't work for me for the icons...

---

### Post by Chilongola on 2007-09-23
I only use Lotus 123 or Quattro Pro,  cannot take excel especially its shitty printing.  This is just on time for me.

[SIZE="4"]Taken from an earlier post:

Then type the following commands:
chmod a+x IBM_Lotus_Symphony_Linux.bin
./IBM_Lotus_Symphony_Linux.bin
cd IBM_Lotus_Symphony_Linux
sudo ./setup.bin[/SIZE]

That is all it takes.  Reboot and all the three will appear on your menu.
Been using all three for almost 4 hours - no problems.

---

### Post by ryno519 on 2007-09-23
If you have removed lotus notes and are stuck with their less than ideal icons, here is how I restored openoffice.org's icon set. First, I deleted all of the icons that lotus symphany installed. They are located in the following folders:

/usr/share/icons/hicolor/16x16/mimetypes
/usr/share/icons/hicolor/32x32/mimetypes
/usr/share/icons/hicolor/48x48/mimetypes

I just opened up an instance of nautilus as root and sent the infringing icons to the trash can.

Once you have removed those icons you will have to reinstall the openoffice.org's gnome integration package and possibly the gtk integration package as well. Use the following commands.

```

sudo apt-get remove openoffice.org-gnome openoffice.org-gtk
sudo apt-get install openoffice.org-gnome openoffice.org-gtk

```

That restored them for me after 2 days of staring at those ugly icons.

---

### Post by izamryan on 2007-09-25
> **ryno519 said:**
> 
I just opened up an instance of nautilus as root and sent the infringing icons to the trash can.

Once you have removed those icons you will have to reinstall the openoffice.org's gnome integration package and possibly the gtk integration package as well. Use the following commands.

```

sudo apt-get remove openoffice.org-gnome openoffice.org-gtk
sudo apt-get install openoffice.org-gnome openoffice.org-gtk

```

That restored them for me after 2 days of staring at those ugly icons.

Sigh :confused:

Following the suggestion above, I was not able to:

1. Restore the old OpenOffice Icons; or
2. Remove Lotus symphony from the list of "Open With"

I guess Ubuntu 7.10 is around the corner, so I'll just bear with it until 7.10 is out and re-install with 7.10 :)
LOL.

---

### Post by NoWhereMan on 2007-09-25
> **izamryan said:**
> Sigh :confused:

Following the suggestion above, I was not able to:

1. Restore the old OpenOffice Icons; or
2. Remove Lotus symphony from the list of "Open With"

I guess Ubuntu 7.10 is around the corner, so I'll just bear with it until 7.10 is out and re-install with 7.10 :)
LOL.

naa, I managed to purge that s**t :P you'll do it too :)

ok, go to ~/.local/ and there you should find a defaults.list file (don't remember the name ATM), edit removing any reference to Lotus*

then edit /etc/defaults.list (IIRC) and change any Lotus* reference into the corresponding openoffice suite component (i.e. Lotus Spreadsheet.desktop = oowriter.desktop)

when you're done, yell at IBM

:P

oh, and restart the session, then IIRC you should be done (remember to delete the icons we listed in this thread they're in SUBDIRS of /usr/share/icons/hicolor <-don't delete the whole tree!)

---

### Post by Rob_H on 2007-09-28
People complaining about performance seem to forget that this is a **beta** version. It's common for beta software to perform badly, especially if it's built with optimizations turned off to ease debugging. Sheesh!

My first impression is that it shows promise. I like what they've done with the interface. Beyond that, I'm still trying to figure out what's different from OOo. Need to play with it a few days.

BTW- I have it running under Beryl. If you're having trouble, add this line to your *.bash_profile*:

```
export AWT_TOOLKIT="MToolkit"
```

That helps Beryl play better with Java. You need to log out and log back in. This should work for Compiz Fusion, too, although I haven't tested it.

---

### Post by SvenVranckx on 2007-11-21
I followed these instructions and the ugly icons are gone... however, the openoffice ones aren't back either. I even tried creating similar links to the ones that symphony creates (linking to the openoffice icons), but that didn't help

---

### Post by cogitordi on 2007-11-24
I have a question for those who are using Lotus Symphony on Ubuntu. (I use Ubuntu 64-bit and can't install Symphony.)

Is there a New>Browser menu item?

If so, when you click New>Browser, does the browser appear in a tabbed window? And if so, is it a Gecko-based browser?

---

### Post by toupeiro on 2007-11-24
Having supported Lotus Notes in the mid-late 90's, the thought of using another lotus tool chills my blood.  I'm sure I'll eventually put bias aside and test it ... but not in beta :)

best of luck to you who test it, and please continue to post your experiences.

---

### Post by cogitordi on 2007-11-25
> **cogitordi said:**
> Is there a New>Browser menu item?

If so, when you click New>Browser, does the browser appear in a tabbed window? And if so, is it a Gecko-based browser?

Answered my own question. On Windows, Lotus Symphony puts MS IE 7 on a tab. On Linux, Symphony uses Gecko. 

Cool.

---

### Post by cogitordi on 2007-11-26
IBM has removed the Draw component's ability to export to graphics formats. 

That sucks - right there is reason enough to stick with OpenOffice.

---

### Post by irielion on 2007-11-29
I like it that the font rendering in overall looks better the OOo. But when i make any font bold, it looks horrible and if i make it italic, it look tooo italic. They should fix that and improve the speed. Then i would prefer it over OOo.

---

### Post by Ocean Machine on 2007-12-22
> **NoWhereMan said:**
> naa, I managed to purge that s**t :P you'll do it too :)

ok, go to ~/.local/ and there you should find a defaults.list file (don't remember the name ATM), edit removing any reference to Lotus*

then edit /etc/defaults.list (IIRC) and change any Lotus* reference into the corresponding openoffice suite component (i.e. Lotus Spreadsheet.desktop = oowriter.desktop)

when you're done, yell at IBM

:P

oh, and restart the session, then IIRC you should be done (remember to delete the icons we listed in this thread they're in SUBDIRS of /usr/share/icons/hicolor <-don't delete the whole tree!)

OK. I couldn't find those default.list files. Anyone have a more specific location?

I tried reinstalling OpenOffice.org, but that just brought back the old Symphony icons (even though I deleted them from the mimetypes folders).

---

### Post by Ocean Machine on 2007-12-22
> **Ocean Machine said:**
> OK. I couldn't find those default.list files. Anyone have a more specific location?

I tried reinstalling OpenOffice.org, but that just brought back the old Symphony icons (even though I deleted them from the mimetypes folders).

OK, got rid of the last Lotus Symphony icons (including those link files), but still having trouble getting the OpenOffice icons back. I found default.list files at /home/user/.local/share/applications (where I removed all the lines that said Lotus Symphony), and /etc/gnome (where I changed all the IBM Lotus Symphony.desktop lines to their OpenOffice counterparts. Still don't have the icons back yet. This is really frustrating.

---

### Post by DeadSuperHero on 2007-12-23
I personally can't wait to see the final version of this. If they manage to pull it off, then more power to them! I personally would love to see something that utilizes the wonders of open source, along with being backed by a big company like IBM! Hopefully, they'll have a great developer community. I also would love to see this as a new competitor against MS Office. The irony of IBM making such a comeback against Microsoft would be truly something.

I'll probably give this a try when the stable release comes out. I'd love to see what this looks like with the Nimbus theme!

---

### Post by Chilongola on 2007-12-24
Any true "comeback"  has to be through the schools.  All they teach young folks is Microsoft this Microsoft that.  As I said earlier I only use Lotus 123, and Word Perfect when in windows.  I am presently teaching my 14 year old how to use 123.  In school they are teaching them excel.

---

### Post by SonicSteve on 2008-01-23
> **Chilongola said:**
> Any true "comeback"  has to be through the schools.  All they teach young folks is Microsoft this Microsoft that.  As I said earlier I only use Lotus 123, and Word Perfect when in windows.  I am presently teaching my 14 year old how to use 123.  In school they are teaching them excel.

I think your are bang on with this comment. I'm an IT admin in a canadian school and you're right. Any thoughts of changing from MS office -even hinting-  is met with opposition from every side. Perhaps in time!

---

### Post by laxmanb on 2008-01-23
It's based on OpenOffice 1.X (which was slow). Add to that the Eclipse platform, which is also a resource hog. It'll be a while before I even touch this....

---

