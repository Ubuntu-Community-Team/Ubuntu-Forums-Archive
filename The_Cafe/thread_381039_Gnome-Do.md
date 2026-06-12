---
title: "Gnome-Do"
date: 2007-09-20
forum: The Cafe
---

### Post by davidsiegel on 2007-09-20
You might want to take a look at [GNOME Do]("https://launchpad.net/gc")

---

### Post by dada1958 on 2007-09-20
> **davidsiegel said:**
> You might want to take a look at [GNOME Do]("https://launchpad.net/gc")

Thanks ... DeskbarApplet and Tracker do the job pretty well by now and without Mono :-)

---

### Post by davidsiegel on 2007-09-20
What's wrong with Mono? Don't tell me it's slow.

---

### Post by bennyp on 2007-10-28
I get a build error with GNOME Do. It says it can't find metadata file Mono.Cairo

---

### Post by Incense on 2007-10-28
Katapult is fantastic! Acts a bit strange on gnome though....

---

### Post by davidsiegel on 2007-10-28
> **bennyp said:**
> I get a build error with GNOME Do. It says it can't find metadata file Mono.Cairo

Are you building from a bzr branch (trunk-md) or from the tarball? Can you please report the bug at [http://launchpad.net/gc](http://launchpad.net/gc) so we can continue the discussion there?

---

### Post by davidsiegel on 2007-10-28
> **davidsiegel said:**
> Are you building from a bzr branch (trunk-md) or from the tarball? Can you please report the bug at [http://launchpad.net/gc](http://launchpad.net/gc) so we can continue the discussion there?

Oops, looks like you're way ahead of me. I'll take a look at it. You can try the stable tarball instead--this could be a monodevelop-related bug.

---

### Post by davidsiegel on 2007-10-28
Oh, don't forget [http://blog.davebsd.com/2007/10/04/make-gnome-do-slicker-with-compiz-animations/](http://blog.davebsd.com/2007/10/04/make-gnome-do-slicker-with-compiz-animations/). This will make Do even sexier.

---

### Post by bennyp on 2007-11-01
That is to say, I didn't install mono.cairo, and configure forgot to search.

---

### Post by ice60 on 2007-11-01
i use gnome-launch-box, i posted about it the other day. but, it seems i'm about the only person who's managed to get it installed and working, i've no idea why?? lol
[http://ubuntuforums.org/showthread.php?t=596174](http://ubuntuforums.org/showthread.php?t=596174)

---

### Post by ckempo on 2007-11-08
Now that Quicksilver has gone opensource, you might just see it in an Ubuntu installation near you...

---

### Post by daz4126 on 2007-11-08
I didn't know it had been open sourced. That sounds like brilliant news. Let's hope a linux port is not too far away...

DAZ

---

### Post by davidsiegel on 2007-11-10
It looks like a Linux port of QS is never going to happen. It is tied to the Mac platform more than most programs. GNOME Do is a viable alternative, though:

[http://launchpad.net/gc](http://launchpad.net/gc)

Here's a preliminary package: [ATTACH]49740[/ATTACH]

By the way, it trounces GNOME Launch Box; however, it's no Quicksilver... yet.

---

### Post by ice60 on 2007-11-10
> **davidsiegel said:**
> It looks like a Linux port of QS is never going to happen. It is tied to the Mac platform more than most programs. GNOME Do is a viable alternative, though:

[http://launchpad.net/gc](http://launchpad.net/gc)

Here's a preliminary package: [ATTACH]49740[/ATTACH]

By the way, it trounces GNOME Launch Box; however, it's no Quicksilver... yet.
the video's got you in it lol

---

### Post by ice60 on 2007-11-10
i'll try it when i'm next in ubuntu, suse doesn't have ndesk-dbus, what is it??

---

### Post by davidsiegel on 2007-11-10
DBus is a framework for interprocess communication. Do uses it to check if another instance of GNOME Do is already running, and if it finds one, it tells it to show its window.

---

### Post by ice60 on 2007-11-10
i know the DBus :) i'll try it on my laptop later.

---

### Post by dada1958 on 2007-11-10
I tried it, it looks nice, but here it's not even usable at its current stage.

---

### Post by davidsiegel on 2007-11-10
What's not usable about it? I'm the lead developer and your feedback is really appreciated. If you tell me what is unusable I can fix it.

Keep in mind that is is my first public release. The version is 0.0.1 - I have a long way to go until 1.0. If you tell me that it needs preferences or other niceties, all I can say is that's coming.

---

### Post by davidsiegel on 2007-11-10
You might also want to try some addins: [http://davebsd.com/do/addins](http://davebsd.com/do/addins)

Place them in ~/.do/addins and restart the program.

More instructions can be found on the project website, [http://launchpad.net/gc](http://launchpad.net/gc)

---

### Post by maruchan on 2007-11-10
How do I bind Gnome-Do to a key combo? I couldn't find the app in gconf-editor.

---

### Post by davidsiegel on 2007-11-10
By default, the key combo is <Super>space (super is your apple/windows key). Unfortunately there is no way to change this at the moment without recompiling.

Actually, once gnome-do is running, the command gnome-do will simply show the main window. Or, if you want an even faster activation:

dbus-send --session --type=method_call --print-reply --dest=[org.gnome.Do]("http://org.gnome.do/") /org/gnome/Do/Commander org.gnome.Do.Commander.Show

FYI: maruchan, I just commited a patch to the code that will let you change a value in gconf to change the keybinding. Look for an updated package in a week or so. Thanks!

---

### Post by dada1958 on 2007-11-11
> **davidsiegel said:**
> What's not usable about it? I'm the lead developer and your feedback is really appreciated. If you tell me what is unusable I can fix it.

Keep in mind that is is my first public release. The version is 0.0.1 - I have a long way to go until 1.0. If you tell me that it needs preferences or other niceties, all I can say is that's coming.
I'm using the 64-bits Gibbon and I installed the tar.gz. When I type gedit to launch it gnome-do doesn't show the app, same case with gimp. It does show others, e.g. abiword and inkscape. When I type the name of certain ducuments I often use, gnome-do doesn't show them.
Maybe it has to do with this error when I installed libmono-cairo2.0-cil, see attachment.

---

### Post by daz4126 on 2007-11-11
super + space only works for me once the app is running, could this not launch it too?

The preferences option is not available to me, is this correct?

Nice start though ... hopefully it will get more and more like quicksilver.

DAZ

---

### Post by daz4126 on 2007-11-11
> **dada1958 said:**
> I'm using the 64-bits Gibbon and I installed the tar.gz. When I type gedit to launch it gnome-do doesn't show the app, same case with gimp. It does show others, e.g. abiword and inkscape. When I type the name of certain ducuments I often use, gnome-do doesn't show them.
Maybe it has to do with this error when I installed libmono-cairo2.0-cil, see attachment.

gimp works for me. you need to type text editor to launch gedit.

What is the difference between this and the deskbar applet that is now included by default in Gutsy?

DAZ

---

### Post by davidsiegel on 2007-11-11
Yes, gedit is aliased as "Text Editor" because that is what GNOME calls it. dada, daz and I both get GIMP to come up - is your GIMP desktop file located here: /usr/share/applications/gimp.desktop? GNOME Do looks for desktop files in that folder (and some others). If you did a custom install of GIMP, you may have this desktop file in a different location.

The difference between this and the deskbar applet is that this should be faster, and it uses a different interaction model.

I'm not sure what your shortcut is set to, but if you build from the bzr development branch, it's <Super>space with the ability to change it in gconf. This shortcut only activates the program once it's running, it cannot be launched this way.

You are correct - there are no preferences yet.

GNOME Do doesn't search all of your documents. It only indexes a couple levels down in /home, ~, ~/Documents, ~/Pictures, and ~/Music.

---

### Post by daz4126 on 2007-11-11
Is there a way to launch the program in the background on startup? It just seems a bit of a pain to have to launch it first.

DAZ

---

### Post by davidsiegel on 2007-11-11
> **daz4126 said:**
> Is there a way to launch the program in the background on startup? It just seems a bit of a pain to have to launch it first.

DAZ

Sure, just add gnome-do to your login items in your sessions preferences... It will show the window, but we will have a quiet startup mode once we have a splash screen.

---

### Post by 23meg on 2007-11-11
David, are you planning to implement metadata indexing support (Tracker / Beagle / Xesam)?

---

### Post by davidsiegel on 2007-11-11
So, there's a difference between what Do does and what Tracker / Beagle / Xesam do. Do is NOT for search per se - Do is for interacting with things you know more about than something you would search for. For example, you might use Tracker to find a document with the word "Aristotle" in it. With Do, you would need to already know the thing you were looking for: Arist <ENTER> to open a document named "My Aristotle Paper.odt". So, my short answer is "no," we have no metadata indexing planned. What did you have in mind, anyway? Maybe we could provide features similar to what you want - for example, nice integration with search tools like Tracker / Beagle / Xesam.

---

### Post by 23meg on 2007-11-11
I know the difference between what Tracker / Beagle / Xesam do and what GNOME Do does.

[QUOTE=davidsiegel]nice integration with search tools like Tracker / Beagle / Xesam.[/QUOTE]

That was just what I had on mind. Say, I have a document called reeguyrewgu43g.odt, but its title is "My Aristotle Paper", or I've tagged it "Aristotle"; I type "aris.." in Do, and it brings it up. Like how Deskbar works, with the Tracker Live Search extension.

---

### Post by bash on 2007-11-11
Well does Do also index files? Tried by typing in the filename of a PDF I have in a subdirectoy of my /home. Do proposed me to open it in Firefox. But that was it.

Which kinda leeds me to the second thing Im wondering. If it does indeed index files wouldn't it be clever to use an existing tracker/beagle/watever index database, than to have a seperate indexer running. Not saying: make it like deskbar + tracker. My point is just that it would use more ressources two have two indexer running. So you could just use an existing one. Although I don't know if Tracker indexes the information about files that Do needs/looks for.

---

### Post by ripdog on 2007-11-11
I very much doubt you will ever get near the beauty of Quicksilver. It's now open source, has always been hugly extensible to do anything from launching programs to FTPing files to resizing images, with the press of a few keys. No Linux application will ever get near that kind of elegance, simplicity or usability.

Yup, im about to get flamed. Just my opinion...

---

### Post by dmber on 2007-11-11
so .... how do i pull up gnome-do?  i also can't find my ~/.do folder to put the plugins in.  i like what i'm seeing so far though, i'd just like to be able to pull gnome do up.  when i opened in from my applications/accessories i went to the down arrow in the top right and preferences was grayed out.

thanks.

---

### Post by castrojo on 2007-11-11
win-space will call it up, then just start typing.

---

### Post by dmber on 2007-11-11
got it.  can't find my ~/.do folder though.  

~ is home isn't it?  because it's not in there (i realize it's hidden).

---

### Post by Kalli on 2007-11-11
Great app, it's very promising and I'm looking forward to future release's.

One problem though, I can't find a .do folder in my home directory, do I have to create one?

---

### Post by Depressed Man on 2007-11-11
> **dmber said:**
> got it.  can't find my ~/.do folder though.  

~ is home isn't it?  because it's not in there (i realize it's hidden).

I had to create mine myself. I don't think it exists unitl you create it.

---

### Post by Depressed Man on 2007-11-11
> **ripdog said:**
> I very much doubt you will ever get near the beauty of Quicksilver. It's now open source, has always been hugly extensible to do anything from launching programs to FTPing files to resizing images, with the press of a few keys. No Linux application will ever get near that kind of elegance, simplicity or usability.

Yup, im about to get flamed. Just my opinion...

Nothing to flame you on. I agree, it is nice. But partially because it tied so well into the OSX system. Trying it on a more open environment like Windows or Linux is going lead to problems (and require programs to include some keys or plugins for it). Or have the program itself have plugins for it (like gnome-do). It's the same problem Windows quicksilver like programs have. For example in Windows I use DASH and FARR (find and run robot). Both of them require plugins to expand what they can do. For example you can't do FTP because there isn't a default FTP program in either OS. Well there's probably one in Linux but I haven't used it so I wouldn't know :P.

---

### Post by dmber on 2007-11-12
first of all i LOVE what gnome-do has going so far.  

now, i have zero programming skills, so these are just suggestions, although they are pretty obvious ones -- taken from QS:

1. i'd like a . command for the text box
2. i used the comma trick all the time with QS
3. it would be nice to get the "indirect object" involved.  i realize that would involve adding move, copy, etc. to the actions.

aside from suggestions, i have a question.  when i use the "chat" action, my IM window comes up, but it's in the background.  i expected it to be focused when i entered it as my action.

thanks for the great app...this is an awesome start.

---

### Post by davidsiegel on 2007-11-12
> **dmber said:**
> first of all i LOVE what gnome-do has going so far.  

Thank you! Positive feedback warms my heart.

> 
now, i have zero programming skills, so these are just suggestions, although they are pretty obvious ones -- taken from QS:

1. i'd like a . command for the text box
That's coming.

> 
2. i used the comma trick all the time with QS
Is this for queuing up multiple items? I've used QS a lot but I think I only used that feature once while reading a tutorial. Our Command API already supports performing commands on multiple items and multiple modifier items (e.g. send this, this, and that to him, him, and her), we just need to add this to our UI.

> 
3. it would be nice to get the "indirect object" involved.  i realize that would involve adding move, copy, etc. to the actions.It's already in the code. In fact, the modifier item pane is in our UI, it's just hidden. I need to re-write our window class as it got a bit messy as it was being passed around the project. You should see this within a couple of weeks.

> aside from suggestions, i have a question.  when i use the "chat" action, my IM window comes up, but it's in the background.  i expected it to be focused when i entered it as my action.I'm pretty sure there's nothing we can do about this. Maybe this is a compiz/metacity issue?

> thanks for the great app...this is an awesome start.You are very welcome. Thank you for the feedback and encouragement!

---

### Post by dmber on 2007-11-12
> **davidsiegel said:**
> Is this for queuing up multiple items? I've used QS a lot but I think I only used that feature once while reading a tutorial. Our Command API already supports performing commands on multiple items and multiple modifier items (e.g. send this, this, and that to him, him, and her), we just need to add this to our UI.

It's already in the code. In fact, the modifier item pane is in our UI, it's just hidden. I need to re-write our window class as it got a bit messy as it was being passed around the project. You should see this within a couple of weeks.


i'll just address the two points worth addressing:

the "comma trick" is exactly as you describe it.  i would use it for example to make a stack of multiple files then move them all to the same place.

i'm amped about getting indirect objects.  that was what i used QS for most of all.  

thanks again for your work.  as i said before, i have zero programming knowledge, but if i can be of help in any way i'm up for it.  i know the ins and outs of the user-side of QS pretty deeply, so if that knowledge can help or anything like that i'm up for it.

---

### Post by reacocard on 2007-11-12
very nice little app! not terribly useful for me yet but it shows a lot of promise. Add good integration with tracker and work on the UI and you'll have a deskbar-killer quite soon.

---

### Post by davidsiegel on 2007-11-12
> **dmber said:**
> thanks again for your work.  as i said before, i have zero programming knowledge, but if i can be of help in any way i'm up for it.  i know the ins and outs of the user-side of QS pretty deeply, so if that knowledge can help or anything like that i'm up for it.

Alright, let's see what you're made of - if you know QS so well, tell me ten things you'd improve about QS if you were a super hacker extraordinaire.

---

### Post by davidsiegel on 2007-11-12
> **reacocard said:**
> ...Add good integration with tracker and work on the UI and you'll have a deskbar-killer quite soon.

What did you have in mind? I've gotten this request a couple of times. I'm very hesitant to add something like this because it would slow the app down a lot, and search results are pre-cached. How about something like this: you bring up Do, type "something I'm looking for" and select a tracker search command. Either the tracker search command spawns Tracker and conducts a search, or maybe the Tracker results show up in Do for you to play with them? I'm thinking you want something more like the second option.

---

### Post by reacocard on 2007-11-12
> **davidsiegel said:**
> What did you have in mind? I've gotten this request a couple of times. I'm very hesitant to add something like this because it would slow the app down a lot, and search results are pre-cached. How about something like this: you bring up Do, type "something I'm looking for" and select a tracker search command. Either the tracker search command spawns Tracker and conducts a search, or maybe the Tracker results show up in Do for you to play with them? I'm thinking you want something more like the second option.

just do it like deskbar: load up your cached results immediately, and add the tracker results as they are returned. the default action could be to open the tracker search window, allowing for great speed there, but for those willing to wait another half second or so then the most relevant tracker results become easily available.

---

### Post by dmber on 2007-11-13
> **davidsiegel said:**
> Alright, let's see what you're made of - if you know QS so well, tell me ten things you'd improve about QS if you were a super hacker extraordinaire.
before i take on this challenge :) , let me make sure i understand the question:

do you want ten things from QS that i would put into gnome-DO?  or ten things about QS that i would want to make better?

because really, i'm pretty much 100% ubuntu at this point, i don't use OS X anymore...

---

### Post by daz4126 on 2007-11-13
> **dmber said:**
> i'll just address the two points worth addressing:

the "comma trick" is exactly as you describe it.  i would use it for example to make a stack of multiple files then move them all to the same place.

i'm amped about getting indirect objects.  that was what i used QS for most of all.  

thanks again for your work.  as i said before, i have zero programming knowledge, but if i can be of help in any way i'm up for it.  i know the ins and outs of the user-side of QS pretty deeply, so if that knowledge can help or anything like that i'm up for it.

Any chance somebody could explain what all this means or even better, show a video tutorial. I'm not sure I am using Gnome Do to its full potential.

Thanks,

DAZ

---

### Post by Kalli on 2007-11-13
...since we're on requests, I would love to be able to sudo command, for things that would run in terminal as well as things like synaptic and such.

---

### Post by dmber on 2007-11-13
> **daz4126 said:**
> Any chance somebody could explain what all this means or even better, show a video tutorial. I'm not sure I am using Gnome Do to its full potential.

Thanks,

DAZ
**i'll explain how they work in Quicksilver: (as far as I understand they are not available (yet) in Gnome-Do)**

the **comma trick** allows you to compile a "stack" of items...such as folders or files (or a mix of either) in the object pane.  when you search for an item, instead of tabbing, you hit comma and it puts that item in a stack, then you can search for another item and hit comma again.  once you have your stack, you tab to the actions and perform the same action on all the items.

[http://www.youtube.com/watch?v=R4p5WdssSTo](http://www.youtube.com/watch?v=R4p5WdssSTo)

if you want to move, copy, email something to someone, etc. you need an **indirect object**.  for example, if i wanted to send a file as an email attachment to my wife (again, using Quicksilver) i would search for the file (my object), hit tab and search for email to... (my action) then hit tab again and search for my wife (my indirect object).

right around the 2:00 mark of this video shows the three pane "indirect object" function of QS.

[http://www.youtube.com/watch?v=EydTYOeqIrk](http://www.youtube.com/watch?v=EydTYOeqIrk)

---

### Post by daz4126 on 2007-11-13
> **dmber said:**
> **i'll explain how they work in Quicksilver: (as far as I understand they are not available (yet) in Gnome-Do)**

the **comma trick** allows you to compile a "stack" of items...such as folders or files (or a mix of either) in the object pane.  when you search for an item, instead of tabbing, you hit comma and it puts that item in a stack, then you can search for another item and hit comma again.  once you have your stack, you tab to the actions and perform the same action on all the items.

[http://www.youtube.com/watch?v=R4p5WdssSTo](http://www.youtube.com/watch?v=R4p5WdssSTo)

if you want to move, copy, email something to someone, etc. you need an **indirect object**.  for example, if i wanted to send a file as an email attachment to my wife (again, using Quicksilver) i would search for the file (my object), hit tab and search for email to... (my action) then hit tab again and search for my wife (my indirect object).

right around the 2:00 mark of this video shows the three pane "indirect object" function of QS.

[http://www.youtube.com/watch?v=EydTYOeqIrk](http://www.youtube.com/watch?v=EydTYOeqIrk)

That looks really cool. Let's hope that Gnome Do can start to build in this functionality.

DAZ

---

### Post by davidsiegel on 2007-11-14
Yes, we plan to implement a lot of these features from Quicksilver.
 
Dmber, I want ten problems that QS has that we can remedy/improve upon in Do. [http://do.davebsd.com](http://do.davebsd.com) - we've started building a web site.

---

### Post by bash on 2007-11-14
Ok I have a couple of questions. Hope you can answer them:

[list]
[*] Is it (or will it be possible) to find documents. For example if I have an .odf document name 123.odf and I type 123.odf in Do will it be able to find and open it?
[*] Is there (or will there be) a quick way to execute terminal commands. For example I would propose if you prefix something with a ***** it is a terminal command. Like when I would type ***sudo apt-get install test** if you press enter it would open the terminal and execute that command
[*] Is there (or will there be) a way to automatically start Do minmised. Currently I have Do in my Session list so its automatically started. But it always starts with windows open. So I have to press ESC. As you can understand on login I just want it to start minimised so I can press super+space whenever I need it.
[/list]

Thanks. But besides that its looking good so far. Hopin for more plugins though. Emesene and Banshee integration would be nice.

---

### Post by dmber on 2007-11-14
> **davidsiegel said:**
> Yes, we plan to implement a lot of these features from Quicksilver.
 
Dmber, I want ten problems that QS has that we can remedy/improve upon in Do. [http://do.davebsd.com](http://do.davebsd.com) - we've started building a web site.
hmm....problems in quicksilver?  

when i said i knew quicksilver really well i guess i meant that to mean i have ideas to implement into Do.  i can't even think of one thing i would change/add to quicksilver.  if i could port it to Linux and run it on ubuntu i would delete my os x partition on my macbook right now.

the biggest things i used quicksilver for were:
sending off quick emails
moving files
appending text to a to do file
setting text alarms
launching apps/docs
setting hotkeys to do certain repetetive tasks

i will switch over to OS X for a bit because i need to update to 10.4.11 anyway and play around with QS and see if i can think of problems...

---

### Post by dmber on 2007-11-14
ok i thought of one:

the defaults of the catalog isn't the greatest.  take for example these two screenshots: 

this one is of the built-in catalogs.  take a look at the Documents folder.  It indexes the built-in Documents folder for OS X, but the user has no control as to how many levels down it indexes.

[[IMG]http://img114.imageshack.us/img114/7696/picture1xx3.png[/IMG]](http://imageshack.us)


In this image, I've had to create my own separate Documents indexer in the catalog, which just duplicates what QS did itself, except that I can make this one go down more levels.  Look at the difference in the number of files each has indexed.

[[IMG]http://img214.imageshack.us/img214/9779/picture2jl1.png[/IMG]](http://imageshack.us)

---

### Post by davidsiegel on 2007-11-14
Right. One of the things we already decided about this project is that users shouldn't have to do weird configuration like that. We want to just see that you spend a lot of time in that Documents folder, so we'll just index it for you. Or, if you browse into it in GNOME Do and open some item, we'll add that item to our index and maybe if you do that a lot we'll add more files and directories around it.

---

### Post by davidsiegel on 2007-11-14
Also, speaking of convoluted configuration, if you have the newest Do from the Launchpad repo, if you put this line:

> ~/Documents: -1

In the file ~/.do/FileItemSource.config, Do will index ~/Documents to an 'infinite' depth.

---

### Post by dmber on 2007-11-14
> **davidsiegel said:**
> Also, speaking of convoluted configuration, if you have the newest Do from the Launchpad repo, if you put this line:



In the file ~/.do/FileItemSource.config, Do will index ~/Documents to an 'infinite' depth.
i have to create that file, right?

---

### Post by drewcoll on 2007-11-14
I tried this out yesterday and liked it, but I have one question...

Is there anyway to go faster??? Can I remove anything to speed the launch time?    It takes about 3 seconds for the search to come up, and it seems almost in that time I could type whatever I needed.  It takes a lot longer if my system is doing something.  Any ideas?

I have a thinkpad T30 with a 1.8ghz processor.   Not the greatest but gnome-launch-box was much faster.

looks like youre into this gnome-do stuff, good to see someone is looking out for us linux users... projects like this help erode the paying software population... poor saps

---

### Post by davidsiegel on 2007-11-15
Hmm... It may take 3-5 seconds to start up, but it should come up instantly every time you invoke it after that. Are you using the keybinding <Super>space to bring it up. Again, the first couple searches may take a few seconds because there's a bug in the way we load icons, but after that all searches should finish as soon as you type a key. Please do some testing a describe the performance some more. If Do is really running this slow on your system, we should look further into it.

---

### Post by davidsiegel on 2007-11-15
Yes.

---

### Post by davidsiegel on 2007-11-15
Also, in my tests Do is faster than GLB because we don't wait for you to stop typing before searching.

---

### Post by zeltak on 2007-11-15
Hi David

I absolutely love your program. just to let you know that because of gnome-do i think i will make the change from KDE to Gnome..:)..Gnome do is that impressive!! i am no programmer at all but am willing to help in any other areas you may need!

A few questions/suggestions (if you dont mind ;-) )  

1.In Kde's Beagle (kerry) when i search for a contact i get a small preview with the phone number and mobile phone which is very handy, would it be possible to have something like this for gnome-do?
2.will it be possible to change the hotkey in the future (to bring up gnome-do)?
3.Ive seen you have rhythm box support, i LOVE amarok, is there any plans for an amarok plugin?

thx alot for all your hard work!!

Zeltak

---

### Post by bash on 2007-11-15
David I posted now twice in this thread the same questions in the hope I would get an answer from you. So far nothing. Im now doing this one last time. Everyone except me has sofar recieved explanations. So if this time again nothing comes, well I guess that will be the last time I use Do. Because if the programmer doesn't even bother to answer questions and or concern from the programms users I don't think such a programm is worth using.

So for the third time my questions:

[list]
[*] Is it (or will it be possible) to find documents. For example if I have an .odf document name 123.odf and I type 123.odf in Do will it be able to find and open it?
[*] Is there (or will there be) a quick way to execute terminal commands. For example I would propose if you prefix something with a ***** it is a terminal command. Like when I would type ***sudo apt-get install test** if you press enter it would open the terminal and execute that command
[*] Is there (or will there be) a way to automatically start Do minmised. Currently I have Do in my Session list so its automatically started. But it always starts with windows open. So I have to press ESC. As you can understand on login I just want it to start minimised so I can press super+space whenever I need it.
[/list]

---

### Post by graabein on 2007-11-15
Good questions **ubun-two**. 

I have not tried Gnome Do yet but I'll give it a try when I get Ubuntu back up and running. Not bothered doing a fix/reinstall since it broke before the summer vacation. 

Love the idea of executing almost anything with a few key strokes.

---

### Post by davidsiegel on 2007-11-15
> **ubun-two said:**
> David I posted now twice in this thread the same questions in the hope I would get an answer from you. So far nothing. Im now doing this one last time. Everyone except me has sofar recieved explanations. So if this time again nothing comes, well I guess that will be the last time I use Do. Because if the programmer doesn't even bother to answer questions and or concern from the programms users I don't think such a programm is worth using.

 
I'm sorry I missed your questions. Please don't chastize me, though, because I am doing my best. It is clear that I am bothering to answer questions, I just missed one. Will you please forgive me?
 
> 
So for the third time my questions:
[LIST]
[*]Is it (or will it be possible) to find documents. For example if I have an .odf document name 123.odf and I type 123.odf in Do will it be able to find and open it?[/LIST]
This is currently possible. Search our mailing list for "FileItemSource.config" to find out how to set custom folders for Do to index. I am sure that someday we'll have fancy tracker integration too, giving you more powerful search options.
> 
[LIST]
[*]Is there (or will there be) a quick way to execute terminal commands. For example I would propose if you prefix something with a ***** it is a terminal command. Like when I would type ***sudo apt-get install test** if you press enter it would open the terminal and execute that command[/LIST]
 
Typing a terminal command should give you a "Run in Shell" command - try "gnome-open /" TAB and select the run in shell command.
 
> 
[LIST]
[*]Is there (or will there be) a way to automatically start Do minmised. Currently I have Do in my Session list so its automatically started. But it always starts with windows open. So I have to press ESC. As you can understand on login I just want it to start minimised so I can press super+space whenever I need it.[/LIST]
Yes, we will have silent startup once we have a splash screen so that users know our program is starting. You can find out more about plans for this feature by searching our bug reports and blueprints on Launchpad.
 
Are you happy now, ubun-two?

---

### Post by bash on 2007-11-15
Thanks for the answers mate. Yea I saw that you tried your best to answer all the questions. So I started to wonder why I was the only not recieving answers. So I thougth putting a little rant in it might get the attention. Nothing bad meant.

As for running terminal commands: I tried it for examle with typing "sudo apt-get install" and then "Run in Shell" pops up. But if I tab -> enter it, the Do window disappears, but nothing happens. So I thougth this was just not implemented. But after you said that, might be a bug?

And for the searching for documents: Does Do currently index the files itself? Because if an indexer like Tracker is already present, wouldn't it be less ressource intensive if Do would just use the already built Tracker database, instead of running a "second" indexer and creating another database. This is just an idea. I don't know if Tracker (or any other indexer for that matter) indexes the info Do needs.

---

### Post by davidsiegel on 2007-11-15
> **ubun-two said:**
> Thanks for the answers mate. Yea I saw that you tried your best to answer all the questions. So I started to wonder why I was the only not recieving answers. So I thougth putting a little rant in it might get the attention. Nothing bad meant.

As for running terminal commands: I tried it for examle with typing "sudo apt-get install" and then "Run in Shell" pops up. But if I tab -> enter it, the Do window disappears, but nothing happens. So I thougth this was just not implemented. But after you said that, might be a bug?

Could be a bug. Run Do from the terminal (gnome-do) and see if you get an error message. If you do, report a bug at [http://launchpad.net/gc](http://launchpad.net/gc).

> 
And for the searching for documents: Does Do currently index the files itself? Because if an indexer like Tracker is already present, wouldn't it be less ressource intensive if Do would just use the already built Tracker database, instead of running a "second" indexer and creating another database. This is just an idea. I don't know if Tracker (or any other indexer for that matter) indexes the info Do needs.

Well, Do uses a very very simple sort of index. It's nowhere near as powerful as Tracker's, but it is designed to give you results instantly. Do searches only by names, not by metadata or file contents. Do isn't really a search tool; instead, it should be used to give you quick access to items whose names you already know. Tracker has its own use cases. If we were to use Tracker for file indexing, you might activate Do to open Firefox, so you type "fi" and then you wait for 3+ seconds for Tracker results when all you wanted was to open Firefox, which Do lets you do very quickly precisely because it's simpler (and less powerful for search) than Tracker.

---

### Post by Kalli on 2007-11-15
> **davidsiegel said:**
> 
Yes, we will have silent startup once we have a splash screen so that users know our program is starting. You can find out more about plans for this feature by searching our bug reports and blueprints on Launchpad.

Won't people know it's running once they press super-space? Does it really need a splash screen? I would just assume it were running until I found out otherwise.

---

### Post by davidsiegel on 2007-11-15
You can't underestimate users' stupidity.

---

### Post by davidsiegel on 2007-11-15
> **davidsiegel said:**
> You can't underestimate users' stupidity.

Or is it "overestimate"?

---

### Post by bash on 2007-11-15
Will there be an option to turn of the splash screen?

---

### Post by reacocard on 2007-11-15
> **ubun-two said:**
> As for running terminal commands: I tried it for examle with typing "sudo apt-get install" and then "Run in Shell" pops up. But if I tab -> enter it, the Do window disappears, but nothing happens. So I thougth this was just not implemented. But after you said that, might be a bug?

I have the same problem. Running Do from a terminal reveals that the application is running in Do's shell instead of its own. (eg, if I do 'sudo apt-get update', all the info is put into the terminal I started gnome-do from)

Also, there appears to be a memory leak in gnome-do. Easiest way to see it is to open do, type a single letter ('n' works well for me), and then scroll down through the list. memory use will rise, but of course, maybe that's just because its the first time? nope. scroll repeatedly up and down through the same list of results. the memory use will continue to rise, even after a large number of repetitions. it's a fairly slow leak, but it could add up to be quite significant.

---

### Post by bash on 2007-11-15
Yea can confirm this. Fiddled around with Do and as long as you run it from a terminal it pastes to output to "its own" terminal. If you don't run it from a terminal nothing happens.

---

### Post by davidsiegel on 2007-11-15
So, "Run in shell" is different from "run in terminal." If you want a "Run in terminal" command, feel free to write one.

As far as the "leak," yes, it may be a leak, but I bet it's just intermediate search objects that have not been freed by the garbage collector. As you're scrolling, it is constantly creating new lists of commands based on the selected item.

Please don't bother me with silly questions like "will I be able to turn the splash screen off in a future version of Do that hasn't been written yet?" In fact, this is my last post in this thread. Please ask all further questions on Launchpad so that other users can benefit from your questions and my answers. People are even talking about this very question: [https://answers.launchpad.net/gc/+question/17788](https://answers.launchpad.net/gc/+question/17788)

---

### Post by deuce868 on 2007-11-15
I'm getting to the party late, but glad to see some interest. I'm a big fan of gnome-do and would encourage you that if you have feature suggestions or questions to use the launchpad interface. I know I check it at least daily if not more often for questions to answer and bugs to help with. 

The big thing is that things are still early and a lot of plugins don't exist yet. We've been talking on the mailing list of our plugin wishlist and if anyone wants to take a crack go for it. I'm hoping to try to get together some notes on creating plugins in the future here. You can see our mailing list discussion on potential plugin ideas here:
[http://groups.google.com/group/gnome-do/browse_thread/thread/6b8e94b70665616f](http://groups.google.com/group/gnome-do/browse_thread/thread/6b8e94b70665616f)

As for the splash screen, if I have to read 10 mono books I'll figure out how to put in a disable checkbox I will. :) I don't get the silent startup though. When I start up my machine I normally end up launching a bunch of starter apps for my day (firefox, IM, mail, etc) and having it pop open once loaded is useful. 

Back to my mono books now.

---

### Post by reacocard on 2007-11-15
> **davidsiegel said:**
> As far as the "leak," yes, it may be a leak, but I bet it's just intermediate search objects that have not been freed by the garbage collector. As you're scrolling, it is constantly creating new lists of commands based on the selected item.


right, but I'm repeatedly going through the *same* list, so after the first pass, all such items should have been created, therefore after the first pass, memory use should be constant. It is not, which is why I think it is a leak.

---

### Post by drewcoll on 2007-11-15
> **davidsiegel said:**
> Hmm... It may take 3-5 seconds to start up, but it should come up instantly every time you invoke it after that. Are you using the keybinding <Super>space to bring it up. Again, the first couple searches may take a few seconds because there's a bug in the way we load icons, but after that all searches should finish as soon as you type a key. Please do some testing a describe the performance some more. If Do is really running this slow on your system, we should look further into it.

Played with things a little more.  I found that putting the much aforementioned > dbus-send --session --type=method_call --print-reply --dest=org.gnome.Do /org/gnome/Do/Commander org.gnome.Do.Commander.Show
method return sender=:1.76 -> dest=:1.80 reply_serial=2
into Configuration Editor got it running so that it took about 1 second to get up.  That's good enough for me!

A new issue though is that when I try to IM people using the pidgin plugin their names and all come up and when I press enter the IM never comes up, Pidgin does nothing.

Thanks.

---

### Post by deuce868 on 2007-11-15
> **drewcoll said:**
> 
A new issue though is that when I try to IM people using the pidgin plugin their names and all come up and when I press enter the IM never comes up, Pidgin does nothing.
Thanks.

Launchpad is really the place for bug reports. They get handled much faster/better and are then easier for everyone to see/find there. 

[https://bugs.launchpad.net/gc/](https://bugs.launchpad.net/gc/)

---

### Post by nnonix on 2007-11-16
> **ripdog said:**
> I very much doubt you will ever get near the beauty of Quicksilver. It's now open source, has always been hugly extensible to do anything from launching programs to FTPing files to resizing images, with the press of a few keys. No Linux application will ever get near that kind of elegance, simplicity or usability.

Yup, im about to get flamed. Just my opinion...

Um, yeah, well, um .... how long have you and Steve Jobs been dating?

---

### Post by ice60 on 2007-11-16
you might get some ideas from here, i don't know if it does anything more then QS, i've never used QS.
[http://www.youtube.com/watch?v=mkCAf5_Y8P4](http://www.youtube.com/watch?v=mkCAf5_Y8P4)

maybe you can do a demo like that too lol

i just watched it, i think plugins would be good. i like the google search operators too - define:word

this is probably something that has nothing to do with Do, but i'd like to be able to add my weather location so you can just type weather <enter> to get the weather, or calc 2+2 and get the answer. i put all those in my bashrc

now i'm getting really OT. i like the reply to the youtube video "wow, i had an idea like this for an OS i want to make based on linux code. damn dash , even though its really good.lol" lol

---

### Post by deuce868 on 2007-11-16
> **ice60 said:**
> you might get some ideas from here, i don't know if it does anything more then QS, i've never used QS.
[http://www.youtube.com/watch?v=mkCAf5_Y8P4](http://www.youtube.com/watch?v=mkCAf5_Y8P4)

maybe you can do a demo like that too lol

i just watched it, i think plugins would be good. i like the google search operators too - define:word

this is probably something that has nothing to do with Do, but i'd like to be able to add my weather location so you can just type weather <enter> to get the weather, or calc 2+2 and get the answer. i put all those in my bashrc

now i'm getting really OT. i like the reply to the youtube video "wow, i had an idea like this for an OS i want to make based on linux code. damn dash , even though its really good.lol" lol

Cool, I hadn't heard of that one before.

---

### Post by Depressed Man on 2007-11-16
DASH is pretty cool..though you gotta pay for it (I have it on my Windows computers)

---

### Post by fifth_rune on 2007-11-16
How does this work with Compiz-Fusion?  I know I've had trouble with Launch Box before due to CF's own keyboard shortcuts and whatnot.  That's really teh only thing keeping me from taking Gnome-Do for a spin (that and the name :) )

---

### Post by daz4126 on 2007-11-16
I thought that I was the only one who thought this app needed a new name. I'd also agree that a splash screen isn't needed before Do can be auto started. I would prefer my apps to just run in the background until I need them - I don't even like having an icon in the systray to show them running.

DAZ

---

### Post by deuce868 on 2007-11-16
> **fifth_rune said:**
> How does this work with Compiz-Fusion?  I know I've had trouble with Launch Box before due to CF's own keyboard shortcuts and whatnot.  That's really teh only thing keeping me from taking Gnome-Do for a spin (that and the name :) )

I konw that it works. Check out Dave's blog post here for some tricks with compiz:
[http://blog.davebsd.com/2007/10/04/make-gnome-do-slicker-with-compiz-animations/](http://blog.davebsd.com/2007/10/04/make-gnome-do-slicker-with-compiz-animations/)

---

### Post by deuce868 on 2007-11-16
> **daz4126 said:**
> I thought that I was the only one who thought this app needed a new name. I'd also agree that a splash screen isn't needed before Do can be auto started. I would prefer my apps to just run in the background until I need them - I don't even like having an icon in the systray to show them running.

DAZ

The big thing is that the project is still working on functionality vs tweaks. Patches welcome if it's something you're willing to work on, but for now, most of us are trying to get the base going as well as a decent suite of extensions.

---

### Post by davidsiegel on 2007-11-17
GNOME Do was supposed to be temporary. If you have a good idea for a name, suggest it: [http://groups.google.com/group/gnome-do/browse_thread/thread/dfb7d8a10ad756b5](http://groups.google.com/group/gnome-do/browse_thread/thread/dfb7d8a10ad756b5)

---

### Post by Vansinnesvisan on 2007-11-17
Is there a .deb available for GnomeGo?

---

### Post by deuce868 on 2007-11-17
> **Vansinnesvisan said:**
> Is there a .deb available for GnomeGo?

Sure thing, .debs are provided via the Launchpad PPA service. There are instructions on the Do website. Go down to packages section on the download page:
[http://do.davebsd.com/?q=content/download](http://do.davebsd.com/?q=content/download)

---

### Post by Vansinnesvisan on 2007-11-17
> **deuce868 said:**
> Sure thing, .debs are provided via the Launchpad PPA service. There are instructions on the Do website. Go down to packages section on the download page:
[http://do.davebsd.com/?q=content/download](http://do.davebsd.com/?q=content/download)

Cool, thanks :)

---

### Post by zeltak on 2007-11-20
Hi David !

My post was kinda lost in this huge thread (no hard feelings...:-) ) so here it is again:


I absolutely love your program. just to let you know that because of gnome-do i think i will make the change from KDE to Gnome....Gnome do is that impressive!! i am no programmer at all but am willing to help in any other areas you may need!

A few questions/suggestions (if you dont mind )

1.In Kde's Beagle (kerry) when i search for a contact i get a small preview with the phone number and mobile phone which is very handy, would it be possible to have something like this for gnome-do?
2.will it be possible to change the hotkey in the future (to bring up gnome-do)?
3.Ive seen you have rhythm box support, i LOVE amarok, is there any plans for an amarok plugin?

thx alot for all your hard work!!

Zeltak

---

### Post by deuce868 on 2007-11-20
> **zeltak said:**
> Hi David !

My post was kinda lost in this huge thread (no hard feelings...:-) ) so here it is again:


I absolutely love your program. just to let you know that because of gnome-do i think i will make the change from KDE to Gnome....Gnome do is that impressive!! i am no programmer at all but am willing to help in any other areas you may need!

A few questions/suggestions (if you dont mind )

1.In Kde's Beagle (kerry) when i search for a contact i get a small preview with the phone number and mobile phone which is very handy, would it be possible to have something like this for gnome-do?
2.will it be possible to change the hotkey in the future (to bring up gnome-do)?
3.Ive seen you have rhythm box support, i LOVE amarok, is there any plans for an amarok plugin?

thx alot for all your hard work!!

Zeltak

1) Definitely possible. Beagle has a dbus interface and the hope is down the road a plugin can be worked on to talk to that. Then again, with Ubuntu shipping tracker by default there might not be a lot of push for a beagle plugin. This is why we need people to step up and work on plugins. 

2) You can change the hotkey now. It is a setting in gconf. Check out /apps/gnome-do/...

3) Again, need for people who need a plugin to work on one. I know I hope to start work on a banshee plugin sometime since that's what I use. It's all about working on what you need at this point.

---

### Post by davidsiegel on 2007-11-20
> **zeltak said:**
> 1.In Kde's Beagle (kerry) when i search for a contact i get a small preview with the phone number and mobile phone which is very handy, would it be possible to have something like this for gnome-do?


I plan to add a feature where you can browse into a contact just like you can browse into an album and see the songs. Once inside the contact, you'll be able to see and interact with all contact details.

---

### Post by atlas95 on 2007-11-21
Hello, very good program !
I have installed it with the repository and I have add the 3 plugins, but they seem don't work, no rhythmbox function, I can't find my jabber pidgin contacts ...
Is it normal?

I have add plugins in my home ~/.do/addins and chmod +x them.

Bests regards

---

### Post by deuce868 on 2007-11-21
> **atlas95 said:**
> Hello, very good program !
I have installed it with the repository and I have add the 3 plugins, but they seem don't work, no rhythmbox function, I can't find my jabber pidgin contacts ...
Is it normal?

I have add plugins in my home ~/.do/addins and chmod +x them.

Bests regards

If they're loading correcty you should seem them listed when you start Do from the command line. It lists off each of the plugins it finds as it starts up. 

It should look like this
> 
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Applications" Item Source.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Define" Command.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Directory Scanner" Item Source.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Firefox Bookmarks" Item Source.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "GNOME Special Locations" Item Source.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Email" Command.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Open" Command.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Open Terminal Here" Command.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Open URL" Command.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Recent Files" Item Source.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Run" Command.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Run in Shell" Command.
11/21/2007 8:10:35 AM [Info]: Successfully loaded "Chat" Command.
11/21/2007 8:10:36 AM [Info]: Successfully loaded "Pidgin Buddies" Item Source.
11/21/2007 8:10:36 AM [Info]: Successfully loaded "Tomboy Note Indexer" Item Source.
11/21/2007 8:10:36 AM [Info]: Successfully loaded "Create New Note" Command.
11/21/2007 8:10:36 AM [Info]: Successfully loaded "Tomboy Note Shortcuts" Item Source.
11/21/2007 8:10:36 AM [Info]: Successfully loaded "Search Notes" Command.


Look for the Pidgin buddies line and a line for Rhythmbox.

---

### Post by daynah on 2007-11-21
> **atlas95 said:**
> Hello, very good program !
I have installed it with the repository and I have add the 3 plugins, but they seem don't work, no rhythmbox function, I can't find my jabber pidgin contacts ...
Is it normal?

I have add plugins in my home ~/.do/addins and chmod +x them.

Bests regards

It case you forgot to (or didn't know how) to fully reset gnome do: Super Space open gnomedo, click on the arrow and click closed,  Now it's REALLY closed (you can test it by trying super space.. it wont open). Now Open gnome do from the menu. It should work.

(Hope you weren't offended by the obvious posting. I just know there are so many times in life that I had just wished someone had reminded me to check and see if I had plugged the darn thing in ;) )

---

### Post by davidsiegel on 2007-11-21
> **daynah said:**
> It case you forgot to (or didn't know how) to fully reset gnome do: Super Space open gnomedo, click on the arrow and click closed,  Now it's REALLY closed (you can test it by trying super space.. it wont open). Now Open gnome do from the menu. It should work.

control-Q will also quit GNOME Do if its window is showing.

---

### Post by alephsmith on 2007-11-24
> **deuce868 said:**
> 1)2) You can change the hotkey now. It is a setting in gconf. Check out /apps/gnome-do/...

Maybe I am missing something but I cannot for the life of me get the hotkey to work.

I have remapped my alt and Super keys however even when I remove my xmodmap, <Super>space (or any other combo set in gconf) will not invoke gnome-do. Deskbar applet works fine on both <Super>space and <Alt>space.

So a couple of questions in the hope that I can finally get this working  

Does gnome-do have to be restarted every time I change a gconf key? Does it matter that I have a Super_R and Super_L?
Could another program be squatting on the key combo (compiz-fusion) and how would I find this out?
Any hints about how I could actually find out why it is not working?

BTW If is matters I am using a macbokpro

Now for some feedback about the actual program:
[LIST]
[*]In QS 'delete' resets the query field rather than deleting letter by letter. I personally think that this is a better option because it is not immediately obvious what you have typed and in what order.
[*]I like the fact that Do is not another frontend for desktop search, however I would love to be able to pipe text to tracker and run a search. For that matter, piping text in QS is my second favourite feature.
[*]Lastly, for a program in early development Do is really great. please keep up the good work.
[/LIST]

---

### Post by davidsiegel on 2007-11-24
> **alephsmith said:**
> Maybe I am missing something but I cannot for the life of me get the hotkey to work.

I have remapped my alt and Super keys however even when I remove my xmodmap, <Super>space (or any other combo set in gconf) will not invoke gnome-do. Deskbar applet works fine on both <Super>space and <Alt>space.

So a couple of questions in the hope that I can finally get this working  

Does gnome-do have to be restarted every time I change a gconf key?

No, changing your gconf key does not require you to restart.

>  Does it matter that I have a Super_R and Super_L?
Could another program be squatting on the key combo (compiz-fusion) and how would I find this out?
Any hints about how I could actually find out why it is not working?

BTW If is matters I am using a macbokproI'm on a Macbook. I have Super_L and Super_R, and everything works fine. I also have Compiz. I have never had trouble activating Do, so I'm guessing you are experiencing interference with another program. Try starting a barebones GNOME session and see what works and what doesn't.
> 

Now for some feedback about the actual program:[LIST]
[*]In QS 'delete' resets the query field rather than deleting letter by letter. I personally think that this is a better option because it is not immediately obvious what you have typed and in what order.[/LIST][LIST]
[*]This makes sense. We'll play with it.> 
[*]I like the fact that Do is not another frontend for desktop search, however I would love to be able to pipe text to tracker and run a search. For that matter, piping text in QS is my second favourite feature.If you'd love to be able to do this, consider writing a plugin for it. I'm busy working on the core feature set. This is something that many people have asked for, so your work would be appreciated, just don't hold your breath waiting for an "official" Do plugin for Tracker.> 
[*]Lastly, for a program in early development Do is really great. please keep up the good work.[/LIST]Thank you very much for your feedback. I hope we will keep up the good work!

---

### Post by davidsiegel on 2007-11-24
By the way, you need Tomboy installed to use the activate keybinding.

---

### Post by davidsiegel on 2007-11-24
> **alephsmith said:**
> [LIST]
[*]I like the fact that Do is not another frontend for desktop search, however I would love to be able to pipe text to tracker and run a search. For that matter, piping text in QS is my second favourite feature.[/LIST]By the way, what do you mean by "piping text"? As far as I know, Quicksilver doesn't have stdio piping. Do you simply mean commands that operate on input text? Do has this, but not many commands take advantage of it at the moment.

---

### Post by dmber on 2007-11-24
hey david,

just wanted to give a shout.  Gnome-Do is awesome!  i don't know anything about programming, but if i did, the first thing i'd work on is getting the old "move/copy/etc" indirect object actions going on.

is this something that needs a plugin or is it something you're (planning on) building into the core?  if it's plugin material, is it something i could possibly figure out how to code?  what i mean is, i'm a decently smart guy, i've just never tried my hand at coding -- who knows, maybe it's something my brain latches onto.

does that make sense?

thanks for this program.  it's pretty great so far.

---

### Post by davidsiegel on 2007-11-24
> **dmber said:**
> hey david,

just wanted to give a shout.  Gnome-Do is awesome!  i don't know anything about programming, but if i did, the first thing i'd work on is getting the old "move/copy/etc" indirect object actions going on.

We're pretty close to releasing the bidirectional search feature, which will let you browse and search your way through items with children (browse into a folder to see the files inside, browse into an artist in Rhythmox to see the albums by that artist). Once this is tested and ready, we'll be all set to add the third pane into the UI. The first plugins to take advantage of the third pane will be the copy/move/etc commands that operate on files. I'm just starting final exams, though, so you might not see a package including these features until the holidays. Sorry!
> 

is this something that needs a plugin or is it something you're (planning on) building into the core?  if it's plugin material, is it something i could possibly figure out how to code?  what i mean is, i'm decently smart guy, i've just never tried my hand at coding -- who knows, maybe it's something my brain latches onto.

does that make sense?

thanks for this program.  it's pretty great so far.

Thanks. Even if you can't code, you can help a lot by simply joining our mailing list, using the program, telling others about it, and reporting bugs.

---

### Post by dmber on 2007-11-25
sounds great. 

how do i join the mailing list?

good luck on finals.

---

### Post by deuce868 on 2007-11-25
> **dmber said:**
> sounds great. 

how do i join the mailing list?

good luck on finals.

Doesn't look like it's not listed on the website. It's here on the google group:
[http://groups.google.com/group/gnome-do](http://groups.google.com/group/gnome-do)

---

### Post by Depressed Man on 2007-11-25
Hmm for some reason on my desktop it doesn't work. I bring it up, then I type in my friend's name then tab over to chat and press enter. But nothing happens. Though using it to launch programs works (and I do have the plugin for Pidgin there).

---

### Post by dmber on 2007-11-25
see if it brought up the pidgin chat in the background.

---

### Post by davidsiegel on 2007-11-25
> **Depressed Man said:**
> Hmm for some reason on my desktop it doesn't work. I bring it up, then I type in my friend's name then tab over to chat and press enter. But nothing happens. Though using it to launch programs works (and I do have the plugin for Pidgin there).

I'm going to be upset if you didn't follow the directions on the website and ensure that you have libpurple-bin installed... Anyway, the current Pidgin plugin is really just a proof of concept. It will be re-written to use DBus directly rather than relying on purple-remote.

---

### Post by dmber on 2007-11-26
is Gnome-Do "learning" my tendencies the way QS does?  I figured after a week of pulling up Gnome-Do and typing "fa" to get my facebook bookmark, i figured just typing "f" would pull up facebook...it's the only "f" object i've used.

is it learning me?

---

### Post by davidsiegel on 2007-11-26
Learning is not yet enabled, but when it is, it will be much more sophisticated than QS's learning capabilities (whether this extra sophistication will yield any significant benefit over QS will be seen...).

From now on, try to "learn" these kind of things for yourself. [http://do.davebsd.com](http://do.davebsd.com) has links to our mailing list. [http://blog.davebsd.com](http://blog.davebsd.com) is where I blog about new features. [http://groups.google.com/group/gnome-do](http://groups.google.com/group/gnome-do) is where we have previously discussed the status of the learning features.

---

### Post by dmber on 2007-11-26
sweet.  thanks david.

---

### Post by bash on 2007-11-29
Is there a 64bit version available?

---

### Post by deuce868 on 2007-11-29
> **ubun-two said:**
> Is there a 64bit version available?

The current .deb build in the PPA should have a 64bit version in it. Nice thing about the PPA system, builds for three archs for me.

---

### Post by castironpants on 2007-12-05
Is there any way to configure Gnome-Do? Like change the keywords for certain applications, or disable bookmarks search? Is there any way, also, that searching for a name could bring it up in the Contact Lookup thing instead of email?

---

### Post by engla on 2007-12-05
This is totally Cool. If you search out on the forum my first posts about switching from the Mac, Qucksilver was the only wound that didn't heal.

But I lived on happily. Until I five days ago started my mac in OSX for the first time in years (really, maybe 9 months).. and used Quicksilver.

I decided that I'd had enough. Still I was waiting, why was noone doing Quicksilver for Linux.. surely those who think deskbar or others never even have used Quicksilver, much less have they lived by it. I really did.

Astounding for you (now) and for me (now), I set out to work on this 4 days ago since it hadn't been done what I knew. So I worked really, really hard for some short days since I was pretty exited. So I'm doing this replacement called **Kupfer** in python/PyGTK

I think I will continue to work with it, as it is already usable enough for me. As you can see, I didn't focus on beauty but rather on functionality first..

I didn't know about Gnome Do until late yesterday, I suppose I will exchange some experiences with David (I want that Rhythmbox thing)

I'll show you a screenshot of two invocations. Notice

* How rough it is
* You can match custom abbrevs like cv2 for freeciv 2.1 (without learning)
* You can have catalogs in catalogs (All applications, Firefox Bookmarks is a catalog), By default All Applications is both directly included and as a catalog, so you can optionally narrow the search.

Yeah and it [has a webpage too]("http://www.student.lu.se/~cif04usv/wiki/kupfer.html") :) (nothing there yet)

---

### Post by davidsiegel on 2007-12-05
Engla, that is really awesome. Could I get you to consider joining our project (GNOME Do) instead? I don't think you'd have to throw away all your hard work - it looks like you've got some interesting ideas that you could bring to Do. If you're a Python guy, you could figure out how to write plugins in python for Do. What do you think?

Also, Do does abbreviations without "learning."

David

---

### Post by deuce868 on 2007-12-05
> **castironpants said:**
> Is there any way to configure Gnome-Do? Like change the keywords for certain applications, or disable bookmarks search? Is there any way, also, that searching for a name could bring it up in the Contact Lookup thing instead of email?

These items have been brought up, but they're not yet there. 

For now I cheat. If I want an app to come up under a different name I either change the name of the shortcut or create a new one so that it gets indexed as the name I want.

---

### Post by UrK on 2007-12-05
I am unable to install gnome-do. Trying to install using apt throws the following:
```

mem@localhost:/tmp$ sudo apt-get install gnome-do
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-do: Depends: mono-mcs but it is not installable
            Depends: libmono-cairo2.0-cil but it is not installable
E: Broken packages

```
I am unable to install from sources too, *configure* script complains about lack of gmcs:
```
checking for gmcs... no
configure: error: gmcs Not found

```

Is it possible that I have old version of mono installed? Does somebody have any idea how can I fix this?

---

### Post by deuce868 on 2007-12-05
What version of ubuntu are you on? Do you have the universe repositories uncommented in your sources list?

---

### Post by awthomp on 2007-12-05
Type:

```
sudo apt-get install mono-gmcs
```

to resolve the missing gmcs dependency.

---

### Post by bruce89 on 2007-12-05
Why does this program depend on a C# compiler?

---

### Post by deuce868 on 2007-12-06
> **bruce89 said:**
> Why does this program depend on a C# compiler?

You're 100% right. Tomorrow I'll remove that dependency and update the packages in the PPA. That's my fault entirely. Thanks for the info.

Edit: actually just updated the packages and submitted them to launchpad now. They should be building soon.

---

### Post by UrK on 2007-12-07
Now it does not reqire C# compilier, but still complains about libmono-cairo2.0-cil. Where cat I get it with all its dependencies?

P.S. I feel like nineties again: DLL hell. :)

---

### Post by hito1 on 2007-12-07
Is there a way to make google or youtube searchs in gnome-do? 

In launchy we can type google (tab) word and it goes to google with the search results for "word".

Also, is there a silent start-up?

edit: Also also, is there a way to run commands at a terminal window, eg. "sudo gedit /etc/apt/sources.list"?

Keep up the good work, those programs are so great that I was avoiding using ubuntu because it didn't have launchy. :)

---

### Post by deuce868 on 2007-12-07
> **UrK said:**
> Now it does not reqire C# compilier, but still complains about libmono-cairo2.0-cil. Where cat I get it with all its dependencies?

P.S. I feel like nineties again: DLL hell. :)

Well first thanks for the info and your patience. Do is my project to help me learn how to do packaging so I'm not going to say it's perfect by any means. 

Now onto the problem. You need the cairo libraries for some of the ui. I don't get why it is that it won't install them. It's listed as a dependency in the package, the package libmono-cairo2.0-cil is available in apt. Can you provide some details on what version/repos you are running with so I can understand why it complains about the cario library instead of just installing it when you install Do?

---

### Post by deuce868 on 2007-12-07
> **hito1 said:**
> Is there a way to make google or youtube searchs in gnome-do? 

In launchy we can type google (tab) word and it goes to google with the search results for "word".

Also, is there a silent start-up?

edit: Also also, is there a way to run commands at a terminal window, eg. "sudo gedit /etc/apt/sources.list"?

Keep up the good work, those programs are so great that I was avoiding using ubuntu because it didn't have launchy. :)

So first the quick one, --quiet should do a quiet startup right now. It's a temporary hack until a better thing gets in there. I've got a man page with this info in, but I've not managed to get it included in the packages yet. 

For your other points, we'd love to get some more plugins developed. There's been talk on doing some web related stuff on the mailing list yesterday and the run commands in a terminal is definitely on our plugin wishlist. In the end, no, there's not currently a plugin to handle those things.

---

### Post by hito1 on 2007-12-07
> **deuce868 said:**
> So first the quick one, --quiet should do a quiet startup right now. It's a temporary hack until a better thing gets in there. I've got a man page with this info in, but I've not managed to get it included in the packages yet. 

For your other points, we'd love to get some more plugins developed. There's been talk on doing some web related stuff on the mailing list yesterday and the run commands in a terminal is definitely on our plugin wishlist. In the end, no, there's not currently a plugin to handle those things.
Ok, thank you for your work. :)

---

### Post by davidsiegel on 2007-12-07
> **hito1 said:**
> Is there a way to make google or youtube searchs in gnome-do? 

In launchy we can type google (tab) word and it goes to google with the search results for "word".


This Google search plugin that you suggest would amount to about 10-20 lines of code. Why don't you write it?

---

### Post by hito1 on 2007-12-07
> **davidsiegel said:**
> This Google search plugin that you suggest would amount to about 10-20 lines of code. Why don't you write it?
I can't even write a hello world program, I'm just a law student with no programming experience. ;)

---

### Post by deuce868 on 2007-12-07
> **hito1 said:**
> I can't even write a hello world program, I'm just a law student with no programming experience. ;)

Time to find some friends that do C# and offer some lunches. :)

---

### Post by UrK on 2007-12-08
**deuce868**
I use Gutsy Gibbon.
```
urk@bebecomp:~$ sudo apt-get install gnome-d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gnome-d
urk@bebecomp:~$ sudo apt-get install gnome-do
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gnome-do: Depends: libmono-cairo2.0-cil but it is not installable
E: Broken packages
```
I use usual universe/multiverese repositories for apt with addition of repos for avant window navigator, wine and gnome-do (launchpad).
Thanks for helping me.

---

### Post by blu3ness on 2007-12-08
[SIZE="4"][COLOR="DarkRed"]Need help with running gnome-do under feisty.[/COLOR][/SIZE]

I compiled Gnome-Do sucessfully, but I am struggling with getting the keybindings to work, I do not have libtomboy. 


```

08/12/2007 2:13:50 PM [Error]: Could not add global keybinding: libtomboy
No alpha support.

tomboy --version
Tomboy: A simple, easy to use desktop note-taking application.
Copyright (C) 2004-2006 Alex Graveley <alex@beatniksoftware.com>

Version 0.6.3

```

Any help here?

Now before you say "why not upgrade to gutsy", you can blame the piece of crap ATI driver that makes gusty suspend and hibernate crash my laptop, I cannot live without suspend/hibernate, hence I am still running feisty.


[SIZE="4"][COLOR="DarkRed"]Update: Problem Solved[/COLOR][/SIZE]
Yes, I found that by compiling a newer version of Tomboy, the libtomboy is included, what pisses me off is why isn't this compiled as a seperate package rather than together with tomboy.
O well... :x

---

### Post by awthomp on 2007-12-11
I had no problems installing gnome-do, but once installed on Ubuntu 7.10 with Compiz enabled, my videos (.avi files through Vlc, MPlayer, and MythTV) became really jerky.  Once I removed gnome-do, the jerkiness of my videos disappeared.  Any suggestions?

---

### Post by 50words on 2007-12-12
Just chiming in to say that Gnome Do is beautiful and exactly what I want in an application launcher. Much better than Deskbar or Katapult.

---

### Post by Mongoose.wa on 2007-12-12
I love what you're doing and I'm going to be watching this project intently.

That said, it would be nice for im tabs created through Do to automatically get focus. My Pidgin settings might be causing this, but it'd be nice for sessions started with Do to get focus without having conversations started by others get focus when they pop up.

---

### Post by mikibg on 2007-12-12
can u close gnome do in Alt+Space?
esp button is 2 far

---

### Post by deuce868 on 2007-12-12
> **awthomp said:**
> I had no problems installing gnome-do, but once installed on Ubuntu 7.10 with Compiz enabled, my videos (.avi files through Vlc, MPlayer, and MythTV) became really jerky.  Once I removed gnome-do, the jerkiness of my videos disappeared.  Any suggestions?

Sorry, I can't duplicate this, but I would encourage you to submit a bug report in launchpad. I know the main dev of the application is a compiz user so he might be able to help more. 

[https://launchpad.net/gc](https://launchpad.net/gc)

---

### Post by deuce868 on 2007-12-12
> **50words said:**
> Just chiming in to say that Gnome Do is beautiful and exactly what I want in an application launcher. Much better than Deskbar or Katapult.

Thanks, I know everyone loves to hear the good things out there. Make sure you spread the word around. The more users we can attract the more likely we are to attract some people that can help develop plugins and such which is really an important goal.

---

### Post by deuce868 on 2007-12-12
> **Mongoose.wa said:**
> I love what you're doing and I'm going to be watching this project intently.

That said, it would be nice for im tabs created through Do to automatically get focus. My Pidgin settings might be causing this, but it'd be nice for sessions started with Do to get focus without having conversations started by others get focus when they pop up.

This had been brought up a few times and if I remember correctly it's a limitation in the interaction with pidgin. 

I can't seem to find the thread in the google group mailing list though.

---

### Post by deuce868 on 2007-12-12
> **mikibg said:**
> can u close gnome do in Alt+Space?
esp button is 2 far

I'd encourage you to file a bug request on this if you really want it. 

[https://launchpad.net/gc](https://launchpad.net/gc)

---

### Post by zekopeko on 2007-12-12
any way to start gnome-do minimized?

---

### Post by deuce868 on 2007-12-12
> **zekopeko said:**
> any way to start gnome-do minimized?

Use the --quiet flag to start without it opening up.

---

### Post by Mongoose.wa on 2007-12-12
> **deuce868 said:**
> This had been brought up a few times and if I remember correctly it's a limitation in the interaction with pidgin. 

I can't seem to find the thread in the google group mailing list though.

Mmk. Thanks for the reply. I joined the mailing list yesterday, so I'll stay posted and look for opportunities to contribute.

---

### Post by deuce868 on 2007-12-12
Just to let everyone know, there's been a wiki page started up with tips/information on using GNOME Do:

[https://wiki.ubuntu.com/UsingGnomeDo](https://wiki.ubuntu.com/UsingGnomeDo)

---

### Post by BHSPitMonkey on 2007-12-14
> **davidsiegel said:**
> By default, the key combo is <Super>space (super is your apple/windows key). 

Thanks for the tip;  I've spent the last 15 minutes (at least) trying to find just that piece of information.  No documentation is included in the package itself, or explicitly on your site.  (As it turns out, you've listed that keybinding in the Source installation instructions, which is honestly not where I thought to look first).

Edit:  Of course, it is documented on the page linked in the post above mine, but I only discovered this after reading this thread anyway.

---

### Post by davidsiegel on 2007-12-14
> **BHSPitMonkey said:**
> Thanks for the tip;  I've spent the last 15 minutes (at least) trying to find just that piece of information.  No documentation is included in the package itself, or explicitly on your site.  (As it turns out, you've listed that keybinding in the Source installation instructions, which is honestly not where I thought to look first).

Edit:  Of course, it is documented on the page linked in the post above mine, but I only discovered this after reading this thread anyway.

Since this is an open source, and therefore community driven project, would you mind finding the best possible spot for us to post that info and posting it there? Or if you tell me where you think I should post it, I can put it there. I don't think there's a better spot than directly under "ATTENTION" on our project page, but if you can think of a better place I'm all ears.

---

### Post by hyperair on 2007-12-15
It would be good to display the default keybinding as a tip to those who are opening Gnome-Do for the first time.

---

### Post by hendeca on 2007-12-15
I think this is a fantastic program; keep up the great work. David, you might want to put a link to that wiki on the Gnome Do website in the "About" section.

---

### Post by UrK on 2007-12-18
After fighting for some time with installation issues (inability to install mono and libcairo) I found that my repositories were messed up.
After restoring "Canonical-supported Open Source Software (main)", totally removing all mono packages and reinstalling libxml-sax with all its dependent packages, I was able to install GnomeDo. It's great!!! :popcorn:

P.S. After installation success I compiled it on my other machine: Fedora Core after all dependencies were installed.

Thanks for great software

---

### Post by deuce868 on 2007-12-18
> **UrK said:**
> After fighting for some time with installation issues (inability to install mono and libcairo) I found that my repositories were messed up.
After restoring "Canonical-supported Open Source Software (main)", totally removing all mono packages and reinstalling libxml-sax with all its dependent packages, I was able to install GnomeDo. It's great!!! :popcorn:

P.S. After installation success I compiled it on my other machine: Fedora Core after all dependencies were installed.

Thanks for great software

Good stuff, glad to hear you've got it all running along now. 

Time to get some plugin work going. :)

---

### Post by Mortuis on 2007-12-18
I've been envying windows "Launchy" app for awhile, so I'm excited to see something similar for linux.  I'm having a problem getting it to work, though.  I have no Super key, so I tried remapping it to alt-space. When I went to test it, it didn't work, so here's my attempt to figure out what's wrong.

When I launch gnome-do, I get the following:
> mortuis@Uriel:~$ gnome-do
12/18/2007 12:48:49 PM [Info]: Successfully loaded "Applications" Item Source.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Define" Command.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Directory Scanner" Item Source.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Firefox Bookmarks" Item Source.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "GNOME Special Locations" Item Source.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Email" Command.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Open" Command.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Open Terminal Here" Command.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Open URL" Command.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Recent Files" Item Source.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Run" Command.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Run in Shell" Command.
12/18/2007 12:48:50 PM [Info]: Successfully loaded "Internal GNOME Do Items" Item Source.
12/18/2007 12:48:50 PM [Error]: Could not read addins directory /home/mortuis/.do/addins: Directory '/home/mortuis/.do/addins' not found.
12/18/2007 12:48:50 PM [Error]: libtomboy not found - keybindings will not work.
12/18/2007 12:48:50 PM [Info]: Binding key '<Alt>Space' for '/apps/gnome-do/preferences/key_binding'. You may change this keybinding with Configuration Editor (gconf-editor).
12/18/2007 12:48:50 PM [Error]: Could not add global keybinding: libtomboy


As you can see, it says it can't find libtomboy, I thought I had it installed, so I did a sudo aptitude install tomboy and it said I already had it.  When search for the file, it's in there:
> mortuis@Uriel:~$ locate libtomboy.so
/usr/lib/tomboy/libtomboy.so
mortuis@Uriel:~$ 


At this point, I'm stuck. I figure my libtomboy.so is in a non-standard location (for whatever reason) and I need to point gnome-do to it, but I don't know how.  Any help would be appreciated.

---

### Post by deuce868 on 2007-12-18
> **Mortuis said:**
> I've been envying windows "Launchy" app for awhile, so I'm excited to see something similar for linux.  I'm having a problem getting it to work, though.  I have no Super key, so I tried remapping it to alt-space. When I went to test it, it didn't work, so here's my attempt to figure out what's wrong.

When I launch gnome-do, I get the following:


As you can see, it says it can't find libtomboy, I thought I had it installed, so I did a sudo aptitude install tomboy and it said I already had it.  When search for the file, it's in there:


At this point, I'm stuck. I figure my libtomboy.so is in a non-standard location (for whatever reason) and I need to point gnome-do to it, but I don't know how.  Any help would be appreciated.

I tried out your shortcut. It seems it doesn't like having space capitalized. Try it with a lowercase 's' in space. 

<Alt>space

---

### Post by Mortuis on 2007-12-19
Changed it to a lowercase s,  no dice.  It still says: > [Error]: libtomboy not found - keybindings will not work.Trying it anyway didn't work either.

---

### Post by macogw on 2007-12-19
> **daz4126 said:**
> I didn't know it had been open sourced. That sounds like brilliant news. Let's hope a linux port is not too far away...

DAZ

Um no.  It's Cocoa and Objective-C, for one thing, so GNUStep is the nearest thing to GNOME with any chance in hell of running it.  Second, it's spaghetti code.

---

### Post by 50words on 2007-12-19
The only thing I don't like is that Gnome-Do doesn't seem to learn which application I want launched. Launchy, for example, will eventually learn that I want OpenOffice.org to launch when I type "o" if I always select that from the drop-down menu.

---

### Post by deuce868 on 2007-12-19
> **50words said:**
> The only thing I don't like is that Gnome-Do doesn't seem to learn which application I want launched. Launchy, for example, will eventually learn that I want OpenOffice.org to launch when I type "o" if I always select that from the drop-down menu.

It's definitely in the works. There are a couple of guys working on a learning system and it's part of the roadmap.

---

### Post by crazybilly on 2007-12-20
I think you commented on my blog about Launchy for Linux, David--I watched the video.  It certainly did help.

At the same time, coming from Launchy, the keybidings in Gnome-Do feel really strange to me.  Is there any way to configure them?  I'd like to change tab and right-arrow around, for example.

Also, my home directory isn't at /home/me.  For various reasons, it's at /media/Data/me.

When I type in my username, though, it only picks up /home/me.  If I type in media, it doesn't find the /media directory at all (typing in /media doesn't help, nor does /media/Data, etc).  Is there a way to configure what files get indexed?

---

### Post by deuce868 on 2007-12-20
> **crazybilly said:**
> 
At the same time, coming from Launchy, the keybidings in Gnome-Do feel really strange to me.  Is there any way to configure them?  I'd like to change tab and right-arrow around, for example.


Not currently. Someone has started some work with some configuration options, but it's not currently in trunk and working properly. 

> 
Also, my home directory isn't at /home/me.  For various reasons, it's at /media/Data/me.

You can tweak the config file ~/.do/FileItemSource.config 

That specifies directories to parse and how deep to parse them to. For instance, my config is setup this way:
```
 
/home: 1
/home/rharding: 1
/home/rharding/Desktop: 1
/home/rharding/documents: 3
/home/rharding/src/: 1

```

---

### Post by deuce868 on 2007-12-20
> **Mortuis said:**
> Changed it to a lowercase s,  no dice.  It still says: Trying it anyway didn't work either.

Sorry, I can't seem to duplicate this. My libtomboy is in the same path as yours. Are you on gutsy installing from the PPA packages? You might try submitting a bug report in launchpad. 

I could only get it to break with the S being capital. Do me a favor and also try <Control>space. Just see if that works so we can see if it's something with the keyboard layout you have or actually the library?

---

### Post by TheOm3ga on 2007-12-20
With "<Control>space" (s lowercase) it works for me. Anyway, I prefer "<Shift>BackSpace". This program rocks!

BTW, this is my first post here :lolflag:

---

### Post by davidsiegel on 2007-12-20
> **crazybilly said:**
> I think you commented on my blog about Launchy for Linux, David--I watched the video.  It certainly did help.

At the same time, coming from Launchy, the keybidings in Gnome-Do feel really strange to me.  Is there any way to configure them?  I'd like to change tab and right-arrow around, for example.

Also, my home directory isn't at /home/me.  For various reasons, it's at /media/Data/me.

When I type in my username, though, it only picks up /home/me.  If I type in media, it doesn't find the /media directory at all (typing in /media doesn't help, nor does /media/Data, etc).  Is there a way to configure what files get indexed?

See here: [https://answers.launchpad.net/gc/](https://answers.launchpad.net/gc/)

---

### Post by sk8dork on 2007-12-22
> **deuce868 said:**
> Sorry, I can't seem to duplicate this. My libtomboy is in the same path as yours. Are you on gutsy installing from the PPA packages? You might try submitting a bug report in launchpad. 

I could only get it to break with the S being capital. Do me a favor and also try <Control>space. Just see if that works so we can see if it's something with the keyboard layout you have or actually the library?

i am having the same problem. if i do gnome-do --verbose it says it can't find libtomboy, but i have tomboy installed and i can find it when i do a locate. i have changed my keybinding to <Control>space, still nogo. could it be that i'm in feisty? if so, damn that sucks. i used the feisty repo to install gnome-do at first, then i thought i'd try purging it and installing from the gutsy repo, and while it looks prettier in black, it still has problems with libtomboy... i tried installing the latest gutsy version of tomboy from getdeb, but it is requiring (a probably newer version of) libc6 and friends. alas, it looks like i won't be using gnome-do unless this gets fixed. i really don't like the other alternatives.

---

### Post by davidsiegel on 2007-12-22
Please point me to all of the places you are getting GNOME Do from. Some of them are "official" (the launchpad PPA) and others are not affiliated with the project. For example, you said you are using a package with a black interface. Where is that from?

---

### Post by davidsiegel on 2007-12-22
Also, you don't need libtomboy. Assign a keybinding (with compiz or something) to the command gnome-do. This will bring the window up (without running a duplicate process). This command does it faster:

> 
$ dbus-send --session --type=method_call --dest=org.gnome.Do /org/gnome/Do/Controller org.gnome.Do.Controller.Summon


---

### Post by deuce868 on 2007-12-22
> **sk8dork said:**
>  i used the feisty repo to install gnome-do at first, then i thought i'd try purging it and installing from the gutsy repo, and while it looks prettier in black, it still has problems with libtomboy... i tried installing the latest gutsy version of tomboy from getdeb, but it is requiring (a probably newer version of) libc6 and friends. alas, it looks like i won't be using gnome-do unless this gets fixed. i really don't like the other alternatives.

I'm thinking you might be in feisty. RU nthis and let me know what you get:
dpkg -l | grep tomboy

It's been reported that the shortcut only exists > 0.8. So if it's less than that I'm going to bet you're on Feisty. 

Unfortunately, I only created the Feisty package to see if it could be done (wasn't sure how far back a PPA would let you go) and there's no way in a PPA to remove a package. My apologies for the trouble if this is indeed a feisty issue.

---

### Post by sk8dork on 2007-12-22
heh, i was going to make the comment that i am in feisty (gutsy does not work so well on my hardware) but i guess i forgot to mention that. and in case it still matters, tomboy appears to be 0.6.3-0ubuntu1. i have only used the repositories listed on the gnome-do site. i know there is no real mention of the feisty version, but i navigated the repo in firefox and did see a feisty version, so i tried it. the version i got from the feisty repo had a kind of purple UI, and the one from the gutsy repo had a black UI.

i am going ahead and reinstalling using the version in the gutsy repo, version 0.1~bzr113-ubuntu1_i386. i'll try using the keybinding trick that's not dependent on a more recent version of tomboy. fyi, i'm using openbox with gnome stuff (no panel, but i run the gnome-settings-daemon). i'll see what i can come up with. i am going to try to make the keybinding in my openbox rc.xml, not sure if there's another way.

edit:
got the keybinding to work by adding this in my rc.xml
```
    <keybind key="A-space">
     <action name="Execute">
        <startupnotify>
          <enabled>false</enabled>
          <name>Gnome-Do</name>
        </startupnotify>
        <execute>dbus-send --session --type=method_call --dest="org.gnome.Do" "/org/gnome/Do/Controller" "org.gnome.Do.Controller.Summon"</execute>
      </action>
    </keybind>
```
note the quotes i had to add to things. it wouldn't work otherwise.

---

### Post by deuce868 on 2007-12-22
Very cool, I'm glad you got it to work out.

---

### Post by sk8dork on 2007-12-22
thanks. i am very much looking forward to the continued development of this project. =)

---

### Post by davidsiegel on 2007-12-23
Hey, will you please post your solution on our answers page so other openbox users can benefit? [https://answers.launchpad.net/gc/](https://answers.launchpad.net/gc/)

Thanks.

---

### Post by Mortuis on 2007-12-24
> **deuce868 said:**
> Sorry, I can't seem to duplicate this. My libtomboy is in the same path as yours. Are you on gutsy installing from the PPA packages? You might try submitting a bug report in launchpad. 

I could only get it to break with the S being capital. Do me a favor and also try <Control>space. Just see if that works so we can see if it's something with the keyboard layout you have or actually the library?
Thanks deuce, I suppose my problem was that I wasn't running Gutsy. I just updated the OS and now gnome-do is working just fine.  I feel a little silly now. :-)

---

### Post by WaySensei on 2007-12-26
Dave,

I have an issue with my gnome-do. I am starting it up at boot with gnome-do --quiet. However, fairly commonly, the gnome-do interface will be transparent when I bring it up with my key command. I have compiz enabled. Restarting the X session may or may not fix the issue. However, killing gnome-do from the terminal and restarting it from my applications menu always fixes the issue. Your program is GREAT, and is an essential part of my Ubuntu, but I just wanted you to be aware of this problem I'm having.

---

### Post by hyperair on 2007-12-26
Eh, isn't it supposed to be transparent? I think I prefer it when it's transparent compared to when it's not.

---

### Post by WaySensei on 2007-12-27
It's completely transparent. The blue ish border that I have normally becomes clear and very difficult to use the program with.

---

### Post by davidsiegel on 2007-12-27
Hey, can you try to get a screenshot of it? I've never seen this before.

I'm guessing it's a compiz bug, though. On that note, if you're on Gutsy, set your desktop effects to the most basic settings in Appearance preferences and see if you still have this problem.

---

### Post by WaySensei on 2007-12-28
I've attached a screenshot of what gnome-do looks like when it starts up transparent. I think you're right, it most likely is a bug with Compiz.

---

### Post by DjBones on 2007-12-28
it looks pretty nice so far..
compiled fine for me, i was pretty impressed for a first release haha

do you guys think that you can work it into hardy's repo's (ergo debian unstable) when the time comes?

---

### Post by davidsiegel on 2007-12-29
> **DjBones said:**
> do you guys think that you can work it into hardy's repo's (ergo debian unstable) when the time comes?

That's the plan!

---

### Post by MaX on 2008-01-06
I read about Gnome-Do today and I wanted to try it out. But for some reason I can't installl Mono? Am I the only one with this problem or is it just a temporary hickup for Hardy?

---

### Post by hyperair on 2008-01-06
Excellent observation! I've filed a bug report in launchpad, although it isn't really a bug. AND I've modified their deb, removing mono dependencies. See, mono is just a meta-package. It doesn't really matter if it's not installed.

---

### Post by MaX on 2008-01-07
Thanks!
Now all I need is for the program not to quit on me after I've run it the first time....
No wonder my keyboard shortcut didn't work when the program quits when it looses focus...

---

### Post by hyperair on 2008-01-07
You have to make sure it doesn't conflict with any other keyboard shortcuts. The keyboard shortcut you set is system-wide.

---

### Post by davidsiegel on 2008-01-07
> **MaX said:**
> Thanks!
Now all I need is for the program not to quit on me after I've run it the first time....
No wonder my keyboard shortcut didn't work when the program quits when it looses focus...

It's not designed to do that. Does it print anything out when it quits? Does it crash? It should stay running.

---

### Post by MaX on 2008-01-08
Well if something was set to <Super>space it would have shown up right?

I also set it to Ctrl+F2 and that didn't work either...

Nothing happens. I'll wait to try it again when it doesn't index my firefox bookmarks, and when I can start gedit by typing gedit instead of text...

---

### Post by Perpetual on 2008-01-11
I love it.  Thanks for sharing!

---

### Post by mrblue182 on 2008-01-16
I had that same problem with the program crashing. I went to [https://wiki.ubuntu.com/GnomeDo/Installation]("https://wiki.ubuntu.com/GnomeDo/Installation")
and everything works great now, I've got the google calculator and opensearch plugin, and its great! I've never used quicksilver, but I can't imagine its much better then gnome-do =]

---

### Post by WaySensei on 2008-01-18
As of the version 0.3~bzr173, plugins added to my .do/addins directory do not seem to work. They worked fine prior to the latest revision. Has anyone else been having this issue?

---

### Post by deuce868 on 2008-01-18
> **WaySensei said:**
> As of the version 0.3~bzr173, plugins added to my .do/addins directory do not seem to work. They worked fine prior to the latest revision. Has anyone else been having this issue?

The addins directory was moved to plugins. You'll have to change the name and update the plugins you use since there was some big changes in the recent revisions.

---

### Post by zeltak on 2008-01-20
Hi
Silly question, how do you get the 0.3 version? i am using the apt system for the new gnome-do versions, do you have to compile yourself to get 0.3?

thx

Zeltak

---

### Post by hyperair on 2008-01-20
No. The Apt repository at ppa.launchpad.net has 0.3

---

### Post by zeltak on 2008-01-20
mmmm...strange...


I have this in my source list:

deb [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main


and i seem to only get  0.1 (unless the about do is wrong..it says 0.1), is there any way to get verison # in the terminal?

Also btw..does anyone know how to restart gnome-do without restarting or logging out?


thx

Zeltak

---

### Post by deuce868 on 2008-01-20
> **zeltak said:**
> mmmm...strange...


I have this in my source list:

deb [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/rharding/ubuntu](http://ppa.launchpad.net/rharding/ubuntu) gutsy main


and i seem to only get  0.1 (unless the about do is wrong..it says 0.1), is there any way to get verison # in the terminal?

Also btw..does anyone know how to restart gnome-do without restarting or logging out?


Well try this out
> 
$ dpkg -l | grep gnome-do
ii  gnome-do                                   0.3~bzr171-gutsy2


And you should get that. You didn't specify what version of ubuntu you're running. I'm going to assume if you don't get .3 that it's Feisty which I've stopped building to concentrate on Gutsy/Hardy (and there were other issues with Feisty with libtomboy and such). 

As for the second item
Get the process number and then kill it. once killed you can restart from your main menu or via command line with gnome-do

To get the process number:
> 
ps aux | grep Do


---

### Post by zeltak on 2008-01-20
thx for the answer!!

I am using gutsy and it seems i do have the latest 0.3 version (even though in the 
about menu it says 0.1...)

so i guess the problem is deeper. i thought nothing worked since i have an old version. i did put the NEW plugins on the ~/.do/plugins folder but No plugin at all seem to work (other then launch programs and Ffox bookmarks...) any ideas ?

thx

Zeltak

---

### Post by deuce868 on 2008-01-20
Ok, yep. I see what you mean. The author must have updated the build version, but not the --version string. So you found a bug and I'd encourage you to report it on launchpad. 

As far as things not working, kill Do and start it from the command line. It will output the plugins found and loaded and give you some info. If you don't see the plugins listed as it starts something is wrong there. If they load and don't work, make sure you're trying to use them correctly and if you're not sure how I'd suggest you check out the docs on the wiki:
[http://wiki.ubuntu.com/GnomeDo](http://wiki.ubuntu.com/GnomeDo)
and hit up the mailing list.

---

### Post by zeltak on 2008-01-20
strange...when i run it from the terminal i get this:

1/20/2008 8:01:31 PM [Error]: Could not read addins directory /home/zeltak/.do/addins: Directory '/home/zeltak/.do/addins' not found.


Isn't  the new version supposed to look for plugins in a plugins directory?


zeltak

---

### Post by deuce868 on 2008-01-20
> **zeltak said:**
> strange...when i run it from the terminal i get this:

1/20/2008 8:01:31 PM [Error]: Could not read addins directory /home/zeltak/.do/addins: Directory '/home/zeltak/.do/addins' not found.


Isn't  the new version supposed to look for plugins in a plugins directory?


zeltak

Ok, something is officially strange. I don't think you really have .3. I read your earlier post more carefully and the about menu option shows the right 0.3.0. 

I would start with a
sudo apt-get remove --purge gnome-do

followed by reinstalling and make sure you get the .3.

---

### Post by zeltak on 2008-01-20
Wow....you wont believe this

turns out after uninstalling purging etc...that i still got 0.1 
then i realized i probably compiled from source back at v 0.1...had to manually uninstall it and it WORKS!!!
Sorry for my stupidity

thx for all your help

Zeltak

---

### Post by davidsiegel on 2008-01-20
Don't worry, you're the 7th person who had a package + source install conflict causing this confusing situation :) I recommend building from source if you're able since we're updating Do all the time.

---

### Post by jhorner on 2008-01-23
hello, 

I hope someone can assit me with an issue.  I was able to install the program, and it works.  But I am having trouble with the keyboard shortcut.  I use a T23 laptop and it has no Super (windows) button.  I tried just about every combination I can think of in Gconf-editor and I cannot get my keyboard shortcut to work.

In GConf Editor, I go to apps > gnome do > preferences and in "key_binding", I have "<Alt><Space>" (without the quotes).  I have tried this with and without the <> characters and nothing seems to work.  I basically just want GnomeDo to open when I press the Alt+Space key combination on my keyboard.  Any suggestions?

Thanks

---

### Post by deuce868 on 2008-01-23
Try
<Alt>space

I use <Control>space and it works fine.

---

### Post by jhorner on 2008-01-23
> **deuce868 said:**
> Try
<Alt>space

I use <Control>space and it works fine.

I feel like an epic fool.  Thank you much

---

### Post by deuce868 on 2008-01-23
No problem, make sure to let us know how you like it now that you can run it.

---

### Post by marko_4454 on 2008-01-24
I have been using Gnome-Do and I can say that it will help me lots. I already messed around with the config file to catalog more stuff, but I cant seem to be able to have a "play" action when it detects an .mp3.
Do you have a plugin for that? I read most of the thread and couldnt find any help.

I saw that someone mentioned that they "Loved amarok", I also use amarok and like it a lot. Do you have any plans for adding amarok plugin or something?

Again, thanks.. I (as well as many others) appreciate your work!

---

### Post by davidsiegel on 2008-01-24
> **marko_4454 said:**
> I have been using Gnome-Do and I can say that it will help me lots. I already messed around with the config file to catalog more stuff, but I cant seem to be able to have a "play" action when it detects an .mp3.
Do you have a plugin for that? I read most of the thread and couldnt find any help.

I saw that someone mentioned that they "Loved amarok", I also use amarok and like it a lot. Do you have any plans for adding amarok plugin or something?

Again, thanks.. I (as well as many others) appreciate your work!

First of all, DO NOT index all of your music. Do you really play songs by name? Try the Rhythmbox plugin - it lets you play songs by artist or album, and it lets you get to the songs easily without saturating your precious search results with mp3 files.

The reason there's a plugin system is so that anyone can write features for GNOME Do. We are busy working on the application, and we hope that others will create any plugins they can dream up. Why don't /you/ write the Amarok plugin? It would make you an instant superstar.

I'm glad you enjoy Do.

---

### Post by marko_4454 on 2008-01-24
> **davidsiegel said:**
> First of all, DO NOT index all of your music. Do you really play songs by name? Try the Rhythmbox plugin - it lets you play songs by artist or album, and it lets you get to the songs easily without saturating your precious search results with mp3 files.

The reason there's a plugin system is so that anyone can write features for GNOME Do. We are busy working on the application, and we hope that others will create any plugins they can dream up. Why don't /you/ write the Amarok plugin? It would make you an instant superstar.

I'm glad you enjoy Do.

Right now I am not indexing my music, but everyonce in a while I get new songs that are not in my "Amarok Music" folder, so I just wanna add them to my amarok library. 
The reason why I dont write the plugin is because I have really limited programming experience. I dont know C or any of its derivatives. I guess I could however, look at the code. Anyways, thanks for the fast response and keep releasing excellent software :)

---

### Post by fluid_motion on 2008-02-11
I am getting an error when running apt-get gnome-do using the instructions from [https://wiki.ubuntu.com/GnomeDo/Installation](https://wiki.ubuntu.com/GnomeDo/Installation)

I am getting the following error:
```
gnome-do: Depends: xclip but it is not installable
```

Tried using aptitude and got:
```
  gnome-do: Depends: xclip which is a virtual package.
```

I checked that xclip is installed but I can't install gnome-do. :( Any help appreciated!

Update: Finally works after using the new repository.

---

### Post by 23meg on 2008-03-06
There's now an Amarok plugin:

[https://code.launchpad.net/~bcl1713/do/plugins-amarok](https://code.launchpad.net/~bcl1713/do/plugins-amarok)
[https://wiki.ubuntu.com/GnomeDo/Plugins](https://wiki.ubuntu.com/GnomeDo/Plugins)

---

### Post by 23meg on 2008-03-06
> **50words said:**
> The only thing I don't like is that Gnome-Do doesn't seem to learn which application I want launched. Launchy, for example, will eventually learn that I want OpenOffice.org to launch when I type "o" if I always select that from the drop-down menu.

This feature is now in trunk.

---

### Post by pazkooda on 2008-03-26
Quick note for Fedora users. Gnome Do! does not find libtomboy so default keybinding method don't work out of the box.

To fix this problem issue this command as root (or with sudo)

user@workstation:~# ln -s /usr/lib/tomboy/libtomboy.so /usr/lib/libtomboy.so

---

### Post by pazkooda on 2008-03-26
Quick note for Fedora users. Gnome Do! does not find *libtomboy*, so default keybinding method don't work out of the box.

To fix this problem issue this command as root (or with *sudo*)
```
user@workstation:~# ln -s /usr/lib/tomboy/libtomboy.so /usr/lib/libtomboy.so
```

This assumes you have Tomboy installed.

---

### Post by deuce868 on 2008-03-26
> **pazkooda said:**
> Quick note for Fedora users. Gnome Do! does not find *libtomboy*, so default keybinding method don't work out of the box.

To fix this problem issue this command as root (or with *sudo*)
```
user@workstation:~# ln -s /usr/lib/tomboy/libtomboy.so /usr/lib/libtomboy.so
```

This assumes you have Tomboy installed.

Just a heads up that the newer releases no longer require tomboy for the keybinding. Get a hold of 0.4 and you should be good to go.

---

### Post by davidsiegel on 2008-03-26
Do no longer uses libtomboy. Please contact your packagers and ask them to update Do packages in Fedora :)

---

### Post by Mazza558 on 2008-03-26
> **WaySensei said:**
> I've attached a screenshot of what gnome-do looks like when it starts up transparent. I think you're right, it most likely is a bug with Compiz.

I get exactly the same problem, and it's the main reason I'm not using gnome-do right now...

---

### Post by davidsiegel on 2008-03-26
> **Mazza558 said:**
> I get exactly the same problem, and it's the main reason I'm not using gnome-do right now...

Just start Do after you log in. This would do it:
```

$ mkdir ~/bin
$ echo "sleep 5 && gnome-do --quiet" > ~/bin/start-do
```
Then add "bash /home/YOURUSERNAME/bin/start-do" to your session in your Sessions preferences. This will start Do five seconds after you login, avoiding the case where Do starts before compiz is loaded.

---

### Post by 50words on 2008-03-26
I use Gnome Do without Compiz, and as far as I can tell the only reason Gnome Do needs compositing is for the rounded corners and shadows. Can't you do that without compositing? I don't want to run Compiz, but Gnome Do is pretty unsightly without it. I want some of the glitz along with the functionality!

---

### Post by hyperair on 2008-03-26
Get xcompmgr. It's a compositing manager that works with any non-compositing window manager. Or if you're using Ubuntu Hardy, turn on Metacity's compositing in gconf. Or just use deskbar like I do. I honestly find deskbar good enough, and it's got more functionality too. =\ Perhaps if GNOME Do gets better I'll switch back. But until then Deskbar it is for me

---

### Post by anachreon_ on 2008-04-28
Forgive me if this has been asked already - didn't have time to read all 22 pages here - but I can't find out how to use Gnome-do in KDE.  I like it way better than katapult, but not enough to stick with Gnome.  I'm using KDE 3.x, not 4.x.  Can somebody please help?  I already have Gnome-do installed on my box (since I have both Gnome and KDE installed).  I'm running Hardy.  Thanks!

---

### Post by fifth_rune on 2008-04-28
Ok, I need some help.  How do I remove Gnome-do 0.1 which I installed from source? I keep trying things like installing new versions from source, installing from repos, but I can't kill this little ********.  Any help?

SOLVED

Uh, I'm an idiot.

---

### Post by Maupertus on 2008-04-29
I love Gnome-do and I like how much control it gives me without using the mouse. 

I wanted to ask one thing, in gutsy I used the following in session preferences:

Name: Gnome-Do
Command: gnome-do --quiet
Comment: Runs gnome-do at start up in the background

Since my upgrade to Hardy 2 days ago, Gnome-do doesn't (no pun intended) launch at start up.

When I run the command in terminal, I get the following output:

[quote= Terminal Output from gnome-do --quiet]4/29/2008 12:14:02 PM [Error]: Failed to load item source from /usr/lib/gnome-do/Do.exe: Method not found: 'Default constructor not found...ctor() of Do.Core.DoItemSource'.
Cannot index Thunderbird contacts because a System.ArgumentNullException was thrown: Argument cannot be null.
Parameter name: path
Cannot index Thunderbird contacts because a System.ArgumentNullException was thrown: Argument cannot be null.
Parameter name: path
36
[/quote]

Can anybody tell me what the problem is?

[SOLVED] I found out that by editing the line to: gnome-do -q, I've solved the problem. Sorry for the inconvenience.

---

### Post by readingitsideways on 2008-04-30
When I try to install Do on Gutsy with synaptic I get:

W: Failed to fetch [http://ppa.launchpad.net/do-core/ubuntu/pool/main/g/gnome-do/gnome-do_0.4.0.1-0ubuntu2~ppa3~gutsy_i386.deb](http://ppa.launchpad.net/do-core/ubuntu/pool/main/g/gnome-do/gnome-do_0.4.0.1-0ubuntu2~ppa3~gutsy_i386.deb)
404 Not Found

---

### Post by scicode on 2008-05-16
Hi there, here is a plugin for Opera bookmarks (source included, you can add this with a gpl to the rest of the plugins if you want to). I hope it will be possible to write plugins in Python soon.

---

### Post by hyperair on 2008-05-16
Well if you can write a plugin for this, I'm sure you can write a plugin that enables plugins to be written in Python ;)

---

### Post by ghindo on 2008-05-16
Just wanted to pop in to say that I love this program and use it religiously :)

My only qualm with it would be the barebones man page.  I know that a lot of documentation is available online, but it would be nice if the man page included more details on how to configure the program.  (I.e. how to set the keybindings, a mention of plugins, etc.)

---

### Post by davidsiegel on 2008-05-16
> **scicode said:**
> Hi there, here is a plugin for Opera bookmarks (source included, you can add this with a gpl to the rest of the plugins if you want to). I hope it will be possible to write plugins in Python soon.

scicode, please send this to our mailing list if you want anyone to discover it. We do not organize our project on the forums.

---

### Post by jespdj on 2008-05-16
> **davidsiegel said:**
> You might want to take a look at [GNOME Do]("https://launchpad.net/gc")
Yes, I love GNOME Do and use it all the time!

Starting apps by typing Super + space + a few letters + <Enter> is so much faster than using the mouse to navigate the menus or even a quick launch bar (which, besides being slower, also takes up screen space).

+100 for GNOME Do! =D>

---

### Post by ethanay on 2008-05-17
gnome-do has been super stable, and looks nice. super<d> gets me almost anywhere I need to go pretty quickly via keyboard.

deskbar-applet is a nice concept, but it has never been stable for me.  it regularly segfaults and/or loses tracker integration.

up until now i have had both running.  now i will only run gnome-do.  i will miss integrated search/document history functions, but will make-do :)

ok, before i posted this i just found the info on the built-in indexer.  Is it hdd/cpu intensive?  will it disable like tracker when on battery power?

is there tracker plugin integration planned?

---

### Post by scicode on 2008-05-19
> **ethanay said:**
> 
is there tracker plugin integration planned?

go and check out the gnome-do mailing list if you cant wait, somebody was so nice and submitted one

---

### Post by Musky Melon on 2008-05-21
--Delete me

---

### Post by conundrumx on 2008-05-26
I really love Gnome-Do, but sometimes when I want to do a websearch I actually work faster than it.  For example; I call Do, type in whatever I want to search my most commonly used engine (google) for, and hit enter.  But, nothing happens because the third box which specifies the search engine didn't get called.

This seems to be less of an issue in 0.4.2 (I just updated today), but perhaps if the third box doesn't get time to load it should default to the most used engine when doing a web search.

Thanks for making a great app!

---

### Post by takuhii on 2008-05-27
Gnome-do is starting everytime I hit space bar. Any ideas, as the keybinding is <Super>space???

---

### Post by conundrumx on 2008-05-27
Hit your Super key a few times, to see if it's stuck.

Then, start Gnome-Do in a terminal and watch the output.  One of the last lines displayed after loading is what key combo it's bound to.

You could also check the Configuration Editor (/apps/gnome-do/preferneces).

---

### Post by takuhii on 2008-05-27
> **conundrumx said:**
> Hit your Super key a few times, to see if it's stuck.

Then, start Gnome-Do in a terminal and watch the output.  One of the last lines displayed after loading is what key combo it's bound to.

You could also check the Configuration Editor (/apps/gnome-do/preferneces).

already tried that, seems to be ignoring the <SUPER> bit

---

### Post by conundrumx on 2008-05-27
What are you running?  Try a different key combo.

---

### Post by hotweiss on 2008-05-27
This built into Mint 5 Elyssa. I can't find a use for this app...

---

### Post by takuhii on 2008-05-28
> **conundrumx said:**
> What are you running?  Try a different key combo.

I'm running Ubunti Linux, Hardy Heron (8.04). I tried the GConf thing to re-do a keystroke combo, but trying to figure out the text version of a particular key is quite hard (ALT + SPACE) for example...

---

### Post by Sugz on 2008-05-28
Supurb App.. however i cant seem to get "Run in terminal" to work
for example if i type

"Run in terminal TAB ls -a ENTER

All i get is a flash of a terminal and then nothing.. 

Any help as this would be a very useful function
Woops. . im using XFCE

---

### Post by conundrumx on 2008-05-28
Takuhii: It is probably "<Alt>space" but beware, that is the default keybinding in Compiz (and probably Metacity) for the window menu.  How about <Ctrl><Alt>space?

Sugz: Run in terminal calls the terminal only for the process you pass to it.  If you want to see the ouput instead of just running the command to it's completion you should call the terminal first.

---

### Post by Sugz on 2008-05-29
Can i confirm the presence of a memory leak.
I run Gnome do automatically at startup i dont use it for about 3 hours apart from hibernating my laptop.
the memory usage went from 20mb - 160mb

I have no suggestions for replicating this problem apart from run it then leave it for a while

---

### Post by jonwestin on 2008-05-31
Im not sure if anyone else had this problem, but it seems Gnome DO doesnt find my Firefox bookmarks. I tried exporting them as is says on the homepage but that didnt work. Im using Ubuntu 8.04.

---

### Post by bigbrovar on 2008-05-31
> **Sugz said:**
> Can i confirm the presence of a memory leak.
I run Gnome do automatically at startup i dont use it for about 3 hours apart from hibernating my laptop.
the memory usage went from 20mb - 160mb

I have no suggestions for replicating this problem apart from run it then leave it for a while
i can confirm this especially when u install the amarok plugin .. it can use upto 500mb of ram sometimes ..

---

### Post by Sugz on 2008-06-01
> **bigbrovar said:**
> i can confirm this especially when u install the amarok plugin .. it can use upto 500mb of ram sometimes ..

Just had an experience where i left it once on hibernate came back and it took 10 mins to startup again!
i looked at the system processes and Gnome-do was taking up 600Mb of ram!
Thats 60% my current RAM capacity!
i should have taken a screenshot!

---

### Post by Pasto on 2008-06-02
Great job on Gnome-Do. Just two observations:

I was a huge fan of opening Firefox with gnome-launch-box by just typing 'fox', and rhythmbox typing 'box'. This queries do not produce firefox or rhythmbox as result. :( 

And how impossible would it be to allow gnome-do to also close apps? It would add some value for me at least.

---

### Post by Arlanthir on 2008-06-02
My Gnome-Do doesn't open url (just Creative Commons Search all the time!!!) OR gmail (with custom mail command and gmail plugin) =/ 

It's a little sad, though, it would be great if it worked :(

Just fresh installation from synaptic, on hardy.

Launching applications works, opening folders or files always opens its parent folder... Rhythmbox enqueue of albums and artists is perfect :)

Where can I get help about this?

EDIT: Trying to see if the www. misinterpretation came from WWE musics, I removed them from both the disc and Rhythmbox, cleaned .config/gnome-do, purged and reinstalled gnome-do and yet it STILL sees them SOMEWHERE. Argh!

*cries for help*

EDIT2: I managed to "up" the permissions on the actions above by pression DOWN and TAB and selecting the right action.
It seems to remember my choices :)

---

### Post by reacocard on 2008-06-02
> **Pasto said:**
> Great job on Gnome-Do. Just two observations:

I was a huge fan of opening Firefox with gnome-launch-box by just typing 'fox', and rhythmbox typing 'box'. This queries do not produce firefox or rhythmbox as result. :( 

And how impossible would it be to allow gnome-do to also close apps? It would add some value for me at least.

you can teach gnome-do what 'fox' and 'box' should mean. Here's how:

1) type in the phrase, eg 'fox'
2) press the down arrow to get a full list of matches, select the desired match, eg. 'firefox', and launch it
3) repeat 1 and 2 until gnome-do has learned what you want.

---

### Post by y0uiip on 2008-06-03
I just started using Do, and it is really awesome.  I have been doing a lot of reading and I notice three features being talked about that I cannot seem to access.  

1.  when a file is selected, they say you can use an "open with" feature, but I have gone through the whole list of options and it only gives me an "open" option

2.  the option to email a selected file.  I can email the people in my pigin and evolution contacts just fine, but when I have a file selected I cannot email it (attach it to an email)

3.  the Append Selected Text feature.  How do I get that to work?

I'd love to figure these things out, they seem like crazy useful features.  Thanks for any help you can give!

---

### Post by klange on 2008-06-03
I've always had one major problem with Gnome-Do - it doesn't work with my theme. The color detection is worse than OpenOffice's! Seriously, can't it be made an option in GConf or something? [This green definitely doesn't go with... anything else](http://random.ogunderground.com/gnome-do.png).

---

### Post by hyperair on 2008-06-03
Run GNOME Do with --glassframe. The result is a black GNOME Do, which is smaller and is surrounded by a translucent border. I prefer that interface to others.

This is the code in my Sessions:
```

gnome-do --glassframe --quiet

```

---

### Post by klange on 2008-06-03
> **hyperair said:**
> Run GNOME Do with --glassframe. The result is a black GNOME Do, which is smaller and is surrounded by a translucent border. I prefer that interface to others.

This is the code in my Sessions:
```

gnome-do --glassframe --quiet

```

--glassframe appears to be the default. --mini gives me a smaller black look.

---

### Post by hyperair on 2008-06-03
> **WindowsSucks said:**
> --glassframe appears to be the default. --mini gives me a smaller black look.

See this: [http://farm3.static.flickr.com/2083/2338961815_cfcafacda1.jpg](http://farm3.static.flickr.com/2083/2338961815_cfcafacda1.jpg)
That's glassframe.

---

### Post by klange on 2008-06-03
> **hyperair said:**
> See this: [http://farm3.static.flickr.com/2083/2338961815_cfcafacda1.jpg](http://farm3.static.flickr.com/2083/2338961815_cfcafacda1.jpg)
That's glassframe.

Guess it just doesn't work for me. :) mini works fine.

---

### Post by hyperair on 2008-06-03
I think you need a more up to date version.

---

### Post by klange on 2008-06-03
> **hyperair said:**
> I think you need a more up to date version.
It would appear I had an older installation in /usr/local, all's well. I actually prefer mini over glassframe...

---

### Post by conundrumx on 2008-06-03
I think Glassframe looks quite nice, actually.  I was using it up until recently, as Do's autotheme looks decent with Neutronium.

---

### Post by true_friend on 2008-06-06
Gnome Do is pretty maturer now. nice application

---

### Post by pkkid on 2008-06-09
I still have a memory leak using Gnome-Do with Fedora.

---

### Post by Stefanie on 2008-06-09
i have problems with the gmail plugin... i can type my contact's name and they show up in the left part of the screen, but on the right tab there isn't an option "e-mail", it says "no results found". how can i fix this?

---

### Post by pt123 on 2008-06-10
0.5 got released today
[http://blog.davebsd.com/](http://blog.davebsd.com/)

---

### Post by Bubba64 on 2008-06-10
> **ice60 said:**
> i use gnome-launch-box, i posted about it the other day. but, it seems i'm about the only person who's managed to get it installed and working, i've no idea why?? lol
[http://ubuntuforums.org/showthread.php?t=596174](http://ubuntuforums.org/showthread.php?t=596174)

Works fine for me when I can get my laptop with no windows key and the keyboard setup to stay.

---

### Post by Bou on 2008-06-10
So, what's the deal with 0.5 and shelves? I type "rhythmbox" and I get "remove from shelf" as a default action, instead of "run".

What are shelves, and how do you use them?

---

### Post by Bubba64 on 2008-06-10
> **Bou said:**
> So, what's the deal with 0.5 and shelves? I type "rhythmbox" and I get "remove from shelf" as a default action, instead of "run".

What are shelves, and how do you use them?
Just hit r then the down key and it will give you a drop down of programs.

---

### Post by smbm on 2008-06-10
> **pt123 said:**
> 0.5 got released today
[http://blog.davebsd.com/](http://blog.davebsd.com/)

I've got the new version installed but am having a couple of problems.

The new plugin repository/preferences screen deeley doesn't seem to want to install any plugins past a certain point on the list.

The new version doesn't seem to learn like the old one does.

With the old one after a couple of times pressing g and scrolling down to gmail in the list it got the hang of it and I no longer needed to scroll. No such luck so far with the new version.

Anyone got any ides?

Edit: I've just tried the gmail thing again and it seems to have remembered it so no worries on that one.

---

### Post by Arlanthir on 2008-06-10
I've got the plugin install problem too, but it seems it takes a LONG time and then changes the icon.. Then I can enable and disable it with no delay. Is it downloading the plugins or are they stored locally from the start?

---

### Post by Bou on 2008-06-10
> **Bubba64 said:**
> Just hit r then the down key and it will give you a drop down of programs.

Thanks for that :)

I would still like to know what the shelved do, though!

---

### Post by Bubba64 on 2008-06-10
This link may already be in his thread I just don't have the patience to see, but here are all the gnomedo plugins available.
[https://wiki.ubuntu.com/GnomeDo/Plugins](https://wiki.ubuntu.com/GnomeDo/Plugins)

---

### Post by smbm on 2008-06-10
I can install and have working any plugin down the list up to and including Launchpad. After that none of them work.

Anyone else finding that?

---

### Post by streetdaddy on 2008-06-10
> **Bou said:**
> Thanks for that :)

I would still like to know what the shelved do, though!

+1  !!!

I've been searching for an explanation :(

I'm also having the problem with 0.5 that I can't enable plugins...  I'm watching [this bug report]("https://bugs.launchpad.net/do/+bug/238824")

Painful how all the best plugins won't enable...

---

### Post by conundrumx on 2008-06-10
The new version is very nice, if only enabling plugins worked properly in the PPA .deb!

Compiling from source reduces the time I have to work on kernel customization.  :<

---

### Post by r2d2rogers on 2008-06-10
> **streetdaddy said:**
> +1  !!!
I'm also having the problem with 0.5 that I can't enable plugins...  I'm watching [this bug report]("https://bugs.launchpad.net/do/+bug/238824")

Painful how all the best plugins won't enable...

I found a fix that removed the plugins for the user and just used the global plugins from the package.  Try this:

```
rm -rf ~/.local/share/gnome-do/plugins/
```

---

### Post by davidsiegel on 2008-06-10
We had a small snag in the release, and at the last minute some plugins stopped working due to a change in version number. If you have 0.5.0.1 (about window won't show the .1 part, but you can check in synaptic), everything should work. If your plugins get messed up, delete them and start fresh with:

```
$ rm -rf ~/.local/share/gnome-do/plugins
```

Then re-download your plugins.

The first time you click a plugin's checkbox, it gets downloaded, which is why there is a bit of a delay.

Also, learning has been updated to perform better over time, so changes may not take effect until you repeat an action a few times.

Also, the WindowManager depends on libwnck and libwnck-cil. If you don't have these installed, the plugin won't install.

Type "default shelf RIGHT ARROW" to get your default shelf. Add to it with "add to shelf," remove items with "remove from shelf". You can create a new shelf by doing <some item> TAB add to shelf TAB <type a new shelf name>

As you can see, we're a bit behind on documentation, so if you can help out, stop by our wiki and start explaining things!

---

### Post by Arlanthir on 2008-06-10
I think the question is pertinent, *what's a shelf?*

Column of items of our choosing? What can we do with shelves?

---

### Post by Arlanthir on 2008-06-10
It seems to work now =)
I installed everything from the repositories (again) with success.

---

### Post by Mazza558 on 2008-06-10
Will 0.5 come through the PPA repo for Gutsy? I updated earlier and no new version...

---

### Post by Karl S. on 2008-06-10
I did a killall gnome-do in terminal and then ran gnome-do again. This started the new version. It rocks.

---

### Post by thisllub on 2008-06-11
I work without menus and panels. I held out great hopes that Gnome Do would be exactly the tool I want however I think you are trying to do too much.
The "Run Command" in E17 is exactly what I want to use in any DE, especially Openbox. Fast and simple it runs programs and nothing more.
Gnome Do is far too complex for me and that complexity causes instabilty.
Katapult is closer and more stable although not ideal.

Good luck with it though.
Mouse driven systems are a pain.

---

### Post by Maupertus on 2008-06-11
> **thisllub said:**
> I work without menus and panels. I held out great hopes that Gnome Do would be exactly the tool I want however I think you are trying to do too much.
The "Run Command" in E17 is exactly what I want to use in any DE, especially Openbox. Fast and simple it runs programs and nothing more.
Gnome Do is far too complex for me and that complexity causes instabilty.
Katapult is closer and more stable although not ideal.

Good luck with it though.
Mouse driven systems are a pain.

I really have to disagree with your post this1lub.
Apart from the fact that your point about Gnome-Do is largely a subjective point that will be different for each user, the point is easily made redundant by the great options Fighting 0.5 offers. 

I agree with the fact that Gnome-Do now offers an overwhelming amount of possiblities, and at first I selected evey plugin available, it is still very stable and smooth although I thought the indexing 3 levels down would be a pain. Yesterday I deselected everything and re-selected it only when I missed it in use and that works very well for me at least. 

You can make Gnome-Do as complex as you want it to be.

---

### Post by topgi on 2008-06-13
..still cannot get plug-in installed. Looking to the terminal output it seems like it cannot get access to the plug-ins repo. Any clue ?

---

### Post by Maupertus on 2008-06-14
Has anybody else had problems with Gnome-do not starting 'quiet' anymore since the update?

What should be in your sessions dialog, at the moment it's:

gnome-do --q

But Do doesn't start.

Thanks for the help!

---

### Post by Luffield on 2008-06-14
I had a problem, can't remember exactly what it was, but after I deleted Gnome-Do from my session and changed Gnome-Do's preferences to start in quiet mode it worked perfectly.

---

### Post by Arlanthir on 2008-06-14
> **Maupertus said:**
> Has anybody else had problems with Gnome-do not starting 'quiet' anymore since the update?

What should be in your sessions dialog, at the moment it's:

gnome-do --q

But Do doesn't start.

Thanks for the help!

I'd remove that Sessions command and let Gnome-Do Preferences work it out on its own ;)

---

### Post by keiichidono on 2008-06-14
I love Do, it's quite amazing. I have it set to run when i log on so when i boot up here is do sitting on my screen waiting for me to press "f" to start Firefox or similar to begin my usage. I find it **much** faster than using the GUI (as programmers who use vi/vim will know).

---

### Post by bigbrovar on 2008-06-14
hope the memory lakage issue has been sorted out .. cus that is the only thing preventing me from using it

---

### Post by brianafischer on 2008-06-15
Is there a timeline for gnome-do 0.5.0.1 showing up in the PPa repos?  I am using the sources from the ubuntu wiki [here]("https://wiki.ubuntu.com/GnomeDo/Installation") shown below:

```

Add the Gnome Do PPA Repository to your sources list. (See Repositories/Ubuntu).

deb http://ppa.launchpad.net/do-core/ubuntu hardy main
deb-src http://ppa.launchpad.net/do-core/ubuntu hardy main

```

Should I be using a different repo address?

---

### Post by Arlanthir on 2008-06-15
@ brianafischer:

I think your version should already be 0.5.0.1.
Note that ".1" won't appear on the about dialog, you can only check in Synaptic ;)

---

### Post by keiichidono on 2008-06-15
That's what i'm using, the new version is too awesome to not use. :D

---

### Post by brianafischer on 2008-06-16
I did an "upgrade" with the new gnome-do.  It looks like a reboot upgraded to the latest version.

Thanks!

---

### Post by hoboken on 2008-06-16
Gnome do rocks. Can anyone comment on how it compares to quicksilver?

---

### Post by anotherdisciple on 2008-06-17
I am not a big fan of tracker... please tell me gnome-do does it's own indexing? I want to try it out when I get home.... does it have any memory leaks remaining?


oh... and about how much RAM does it use on average?

Does it use much CPU?

---

### Post by zekopeko on 2008-06-17
> **anotherdisciple said:**
> I am not a big fan of tracker... please tell me gnome-do does it's own indexing? I want to try it out when I get home.... does it have any memory leaks remaining?


oh... and about how much RAM does it use on average?

Does it use much CPU?

for me it uses 13-14 mb of ram. and cpu is below 1%.
memory leaks are fixed. maybe some remain in one of the community plugins.
and tracker is an optional plugin. Do indexes files on it's own.

---

### Post by deuce868 on 2008-06-17
> **zekopeko said:**
> for me it uses 13-14 mb of ram. and cpu is below 1%.
memory leaks are fixed. maybe some remain in one of the community plugins.
and tracker is an optional plugin. Do indexes files on it's own.

Just to clarify, Do does not index the contents of files like beagle or tracker. You need to use those plugins for that feature set.

---

### Post by deuce868 on 2008-06-17
> **hoboken said:**
> Gnome do rocks. Can anyone comment on how it compares to quicksilver?

Try it, just don't go asking for features in QS. The team has maintained from day 1 that Gnome Do != Quicksilver and has its own goals/methods. 

The ui and the general concept if very similar though.

---

### Post by conundrumx on 2008-06-17
I think a lot of people in this thread confuse memory leaks with Do simply indexing too many files.  Do rarely goes over 45 mb for me, and I have plenty of plugins running.

As far as searching for files, I saw no benefit in Beagle or Tracker over (s)locate, so I just use the locate plugin.

---

### Post by groats on 2008-06-20
hey everyone,

i recently switched from os x and was missing quicksilver. not anymore, thanks, dave! 

but there's two things i'm still unhappy with: 

the first one is probably my fault: i hate the quicksilver look, but starting via "gnome-do -mini" or -glassframe didn't change anything. it still looks the same, big and bulky. plus, is there an option to make the mini look default? i'd hate to use the terminal to launch do, that kinda defeats the purpose:).

and, the most important thing: is there a way to make do reset the entry field after, like, 2 seconds, so i don't have to backspace whenever i make a typo? the thing i loved about qs...

kinda miss a way to configure gnome-do, a preferences menu would be a nice thing to add in a future version^^

cheers

---

### Post by Maupertus on 2008-06-20
> **groats said:**
> hey everyone,

i recently switched from os x and was missing quicksilver. not anymore, thanks, dave! 

but there's two things i'm still unhappy with: 

the first one is probably my fault: i hate the quicksilver look, but starting via "gnome-do -mini" or -glassframe didn't change anything. it still looks the same, big and bulky. plus, is there an option to make the mini look default? i'd hate to use the terminal to launch do, that kinda defeats the purpose:).

and, the most important thing: is there a way to make do reset the entry field after, like, 2 seconds, so i don't have to backspace whenever i make a typo? the thing i loved about qs...

kinda miss a way to configure gnome-do, a preferences menu would be a nice thing to add in a future version^^

cheers


I don't know if you have the newest version of Gnome-do, so maybe I misunderstand your questions but:

Start gnome-do with super-space or whatever combination you use. In the right corner is a small triangle that will give you a menu when you click it. When opened you can choose preferences. The General tab lets you set an appearance that will be used as of the next time you 'open' Do. It will also let you configure start-up. The 2nd tab lets you create key-bindings and the third tab is how you manage your plugins. I don't know which other preferences you may want to configure, but hose are the most important.

Most of these changes happend after fighting 0.5 though.

---

### Post by groats on 2008-06-20
> **Maupertus said:**
> I don't know if you have the newest version of Gnome-do, so maybe I misunderstand your questions but:

Start gnome-do with super-space or whatever combination you use. In the right corner is a small triangle that will give you a menu when you click it. When opened you can choose preferences. The General tab lets you set an appearance that will be used as of the next time you 'open' Do. It will also let you configure start-up. The 2nd tab lets you create key-bindings and the third tab is how you manage your plugins. I don't know which other preferences you may want to configure, but hose are the most important.

Most of these changes happend after fighting 0.5 though.

ahhh, my bad sorry. i installed the thing thru synaptic so i only had the 0.4 version. now upgraded to 0.5. sorry, i'm a huge newb^^

the preference thing works now, just as the mini interface. loving it more and more!

thanks, maupertus

---

### Post by ShanghaiTeej on 2008-06-20
How come that whenever I want to go to a website, like [www.google.com](www.google.com), Gnome-Do only allows me to make a Tomboy note and not actually open up my web browser?

---

### Post by Maupertus on 2008-06-20
> **groats said:**
> ahhh, my bad sorry. i installed the thing thru synaptic so i only had the 0.4 version. now upgraded to 0.5. sorry, i'm a huge newb^^

the preference thing works now, just as the mini interface. loving it more and more!

thanks, maupertus

Haha, don't thank me, thank Dave. He basicly implemented all the things you wanted to see in the application. You must be a secret visionary. ;)

---

### Post by Arlanthir on 2008-06-20
> **ShanghaiTeej said:**
> How come that whenever I want to go to a website, like [www.google.com](www.google.com), Gnome-Do only allows me to make a Tomboy note and not actually open up my web browser?

I think you'll have to train Gnome-Do.
Don't forget to select the plugins you want to use on the preferences dialog.

Then, start gnome-do and type your site, press TAB and choose (by typing it or pressing down) the option you want (Open URL) ;)

---

### Post by ShanghaiTeej on 2008-06-20
When I press TAB or down, the only option is to create a Tomboy Note.  I have also tried "Open Url www.google.com", but to no avail.  Could anyone point me in the direction of the specific commands for Gnome-Do?

---

### Post by Arlanthir on 2008-06-20
You don't press TAB _or_ down, you press TAB _then_ down, to choose :P

I'm not sure what you mean by specific commands... I use the above method for everything and Gnome-Do starts to remember after a while.

Again, make sure you have the plugins you want enabled.

If you'd like some screenshots or a different way of explaining please ask, maybe I'm not making myself clear :S

---

### Post by ShanghaiTeej on 2008-06-20
Wow, thanks.  I am a dummy!  Haha.  You can manipulate both of the boxes that pop up.  Der!  Funny how one overlooks the simplest of things.

---

### Post by Arlanthir on 2008-06-21
> **ShanghaiTeej said:**
> Wow, thanks.  I am a dummy!  Haha.  You can manipulate both of the boxes that pop up.  Der!  Funny how one overlooks the simplest of things.

Glad it's solved then! :P

---

### Post by PC_load_letter on 2008-07-09
It took me a while to get to this thread. Gnome-Do is, bar none, the best thing that happened to my desktop in years :D I have two issues though, I'd appreciate it if I could get any suggestions:

(1) Gnome-Do ver. 0.4.0.1 installed from Synaptic and runs flawlessly on hardy, the problem is it opens my pdf docs with Evince (I just hate it). I have my pdf files setup to open with epdfviewer. I followed the WIKI and deleted the .desktop launcher of Evince in /usr/share/applications but to no avail. Already posted about it here:
[http://ubuntuforums.org/showthread.php?t=853841]("http://ubuntuforums.org/showthread.php?t=853841") 

(2) I was trying to follow the WIKI and install Gnome-Do on my Feisty desktop but had a weird problem, mentioned here: [http://ubuntuforums.org/showthread.php?t=849718]("http://ubuntuforums.org/showthread.php?t=849718")

Thanks in advance.

---

### Post by barbedsaber on 2008-07-09
Hi all.

How do add more keybindings, I already have super+space to launch do (in all its great godlyness :) ) but how do I set it so that when I press super+t I get a terminal, and when I press super+f, firefox comes up etc. And, if there isn't, can you please make a gui for this.

I am running gnome-do 0.5.

Thanks in advance.

barbedsaber.

---

### Post by PC_load_letter on 2008-07-09
You don't need Gnome-Do to achieve this, at least for the terminal. Just go to "Keyboard Shortcuts" from the Preferences menu and set up a key binding for the terminal, I have it as CTL + ALT + T.
For Firefox, just writing fox in Gnome-Do brings it up.

---

### Post by reacocard on 2008-07-09
> **barbedsaber said:**
> Hi all.

How do add more keybindings, I already have super+space to launch do (in all its great godlyness :) ) but how do I set it so that when I press super+t I get a terminal, and when I press super+f, firefox comes up etc. And, if there isn't, can you please make a gui for this.

I am running gnome-do 0.5.

Thanks in advance.

barbedsaber.

there's a wonderful little program called xbindkeys that does exactly what you want. No gui, but the configuration is pretty simple. It's in the repos.

---

### Post by PC_load_letter on 2008-07-09
**UPDATE:** Regarding issue number (1) in my previous post, does Gnome-Do use gnome-open to open files? So my dilemma is related to this [bug]("https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/209714")?

---

### Post by thisllub on 2008-07-09
> **Maupertus said:**
> I really have to disagree with your post this1lub.
Apart from the fact that your point about Gnome-Do is largely a subjective point that will be different for each user, the point is easily made redundant by the great options Fighting 0.5 offers. 

I agree with the fact that Gnome-Do now offers an overwhelming amount of possiblities, and at first I selected evey plugin available, it is still very stable and smooth although I thought the indexing 3 levels down would be a pain. Yesterday I deselected everything and re-selected it only when I missed it in use and that works very well for me at least. 

You can make Gnome-Do as complex as you want it to be.


I just reinstalled it and I still have the same opinion.
Just not stable enough. 
Maybe it is because I use OpenBox.

I will be back though.
Just not yet.

---

### Post by deuce868 on 2008-07-09
> **PC_load_letter said:**
> It took me a while to get to this thread. Gnome-Do is, bar none, the best thing that happened to my desktop in years :D I have two issues though, I'd appreciate it if I could get any suggestions:

(1) Gnome-Do ver. 0.4.0.1 installed from Synaptic and runs flawlessly on hardy, the problem is it opens my pdf docs with Evince (I just hate it). I have my pdf files setup to open with epdfviewer. I followed the WIKI and deleted the .desktop launcher of Evince in /usr/share/applications but to no avail. Already posted about it here:
[http://ubuntuforums.org/showthread.php?t=853841]("http://ubuntuforums.org/showthread.php?t=853841") 

(2) I was trying to follow the WIKI and install Gnome-Do on my Feisty desktop but had a weird problem, mentioned here: [http://ubuntuforums.org/showthread.php?t=849718]("http://ubuntuforums.org/showthread.php?t=849718")

Thanks in advance.

1) It's because of the defaults setup in the OS. We use gnome-open to figure out which app to launch things with. Google /etc/alternatives and update-alternatives for methods of updating that list to use a different application. 

2) It won't run on feisty. The mono libraries aren't available for that any longer. You might be able to do some custom compiling stuff, but you're on your own.

---

### Post by deuce868 on 2008-07-09
> **barbedsaber said:**
> Hi all.

How do add more keybindings, I already have super+space to launch do (in all its great godlyness :) ) but how do I set it so that when I press super+t I get a terminal, and when I press super+f, firefox comes up etc. And, if there isn't, can you please make a gui for this.

I am running gnome-do 0.5.

Thanks in advance.

barbedsaber.

If you're using 0.5, launch Gnome Do and look for the arrow in the upper right corner of the screen. In there should be a "preferences" menu and the second tab is for shortcuts. Setup a new shortcut of your liking there. I personally use Control-space, but then again I have control mapped to be the caps lock key.

---

### Post by deuce868 on 2008-07-09
> **PC_load_letter said:**
> You don't need Gnome-Do to achieve this, at least for the terminal. Just go to "Keyboard Shortcuts" from the Preferences menu and set up a key binding for the terminal, I have it as CTL + ALT + T.
For Firefox, just writing fox in Gnome-Do brings it up.

The nice thing is that Gnome Do is more than just a launcher. Even at that, it learns your actions over time so I can run firefox with just 

ctrl-space f <enter> 

Check out the list of plugins that add much more functionality than the default launching idea. 
[https://wiki.ubuntu.com/GnomeDo/Plugins](https://wiki.ubuntu.com/GnomeDo/Plugins)

I <3 the pastebin and tomboy plugins personally.

---

### Post by deuce868 on 2008-07-09
> **PC_load_letter said:**
> **UPDATE:** Regarding issue number (1) in my previous post, does Gnome-Do use gnome-open to open files? So my dilemma is related to this [bug]("https://bugs.launchpad.net/ubuntu/+source/xdg-utils/+bug/209714")?

I don't know that nautilus changes the settings in /etc/alternatives. Stick to checking out update-alternatives and it should work out.

---

### Post by deuce868 on 2008-07-09
> **thisllub said:**
> I just reinstalled it and I still have the same opinion.
Just not stable enough. 
Maybe it is because I use OpenBox.

I will be back though.
Just not yet.

Yes, there are issues with other WM. There's a bit of hackery to do things like grab the keyboard focus, show over all windows, etc. It doesn't do well on other window managers and there just aren't enough devs running non-gnome/kde desktops to really get it going.

---

### Post by barbedsaber on 2008-07-09
> **deuce868 said:**
> If you're using 0.5, launch Gnome Do and look for the arrow in the upper right corner of the screen. In there should be a "preferences" menu and the second tab is for shortcuts. Setup a new shortcut of your liking there. I personally use Control-space, but then again I have control mapped to be the caps lock key.

thanks, buts that's not what I ment. never mind, I have found a solution anyway.

---

### Post by deuce868 on 2008-07-09
> **barbedsaber said:**
> thanks, buts that's not what I ment. never mind, I have found a solution anyway.

doh, yea sorry. Was blazing through posts there and I see you want is desktop shortcuts not Gnome Do shortcuts. Glad you got it working.

---

### Post by PC_load_letter on 2008-07-09
> **deuce868 said:**
> 1) ... 

2) It won't run on feisty. The mono libraries aren't available for that any longer. You might be able to do some custom compiling stuff, but you're on your own.

Fair enough, but I think the [installation WIKI]("https://wiki.ubuntu.com/GnomeDo/Installation") should be updated to reflect this fact.

---

### Post by deuce868 on 2008-07-09
> **PC_load_letter said:**
> Fair enough, but I think the [installation WIKI]("https://wiki.ubuntu.com/GnomeDo/Installation") should be updated to reflect this fact.


Feel free :)

---

### Post by DJ_Peng on 2008-07-28
I updated to GNOME Do 0.5.97 this morning and ever since I did I'm noticing that I keep getting notifications of updates for three plugins but they won't install.

[LIST]
[*]Firefox v2.04
[*]GMail Contacts v1.3
[*]Gmail Contacts v1.3
[/LIST]
Yes, I know the last two are dups, but they're dups on my screen as well. Is there a known issue I'm not aware of?

---

### Post by otrojake on 2008-07-29
DJ_Peng, [this]("https://bugs.launchpad.net/do/+bug/252614") link deals with the bug.

---

### Post by CbrPad on 2008-07-29
I love this app but I've just noticed a problem with mine.  

I have 0.5.97 installed and was opening .rtf files with Abiword 2.6.4.   

I've installed Openoffice to deal with some other files and now GnomeDo defaults to opening my .rtf's with OO instead of AbiWord.

I've tried an 'Open With' and selected Abiword, but that just runs Abiword and doesn't actually open the file.  Plus no matter how many times I run it, it doesn't seem to learn that I want to open with Abiword instead of OO by default.  

I've also changed the file properties in Nautilus to remove OO from the 'Open With' list there, and specified AbiWord as default, but this also makes no difference.  

Any ideas would be most appreciated !

---

### Post by deuce868 on 2008-07-29
Gnome Do uses the gnome-open command line tool to open files and such. gnome-open uses your /etc/alternatives and such for determining which application to use for different file types. You'll need to update what your system defaults to using at that level in order for Gnome Do to just open it with Abiword instead of OO. 

If the open with does not actuall open the file I'd file that as a bug. However, the Open With will not change the default application it uses to open a file.

---

### Post by DJ_Peng on 2008-07-29
> **otrojake said:**
> DJ_Peng, [this]("https://bugs.launchpad.net/do/+bug/252614") link deals with the bug.
Thanks otrojake. I knew if I came to this topic I'd find out what was happening.

---

### Post by bobbybobington on 2008-07-29
Gnome-Do rocks my socks off :guitar:, plus the recent update was a pleasant surprise.:KS

---

### Post by CbrPad on 2008-07-30
> **deuce868 said:**
> Gnome Do uses the gnome-open command line tool to open files and such. gnome-open uses your /etc/alternatives and such for determining which application to use for different file types. You'll need to update what your system defaults to using at that level in order for Gnome Do to just open it with Abiword instead of OO. 

If the open with does not actuall open the file I'd file that as a bug. However, the Open With will not change the default application it uses to open a file.

Aaah, I was searching around in there but with no luck and installed galternatives but still nothing, but I've just found /etc/gnome/defaults.list and that's sorted it at last, woohoo!  Thanks for the clue !  I'm surprised this overrides the nautilus settings but you learn something every day.

---

### Post by Duranxl on 2008-08-13
Any word on the banshee plugin not working?

---

### Post by Duranxl on 2008-09-09
I need help:

Gnome-do works fine with the rhythmbox plugin..EXCEPT for 1 album!! (the album i listen to most)

Here's a screenie

[http://wpxldk.googlepages.com/gnomedo.jpg](http://wpxldk.googlepages.com/gnomedo.jpg)

As you can see, only 1 track shows up...instead of all 4.
They all have the same artist name and album name (as you can see)

I already updated my rhythmbox library to no avail

any help?
thanks

---

### Post by zekopeko on 2008-09-09
according to gnome-do devs the new banshee is a mess because it doesn't have dbus interface Do needs, BUT Banshee 1.4 that should be released this month is going to offer Gnome Do support.

---

### Post by Arlanthir on 2008-09-09
> **Duranxl said:**
> I need help:

Gnome-do works fine with the rhythmbox plugin..EXCEPT for 1 album!! (the album i listen to most)

Here's a screenie

[http://wpxldk.googlepages.com/gnomedo.jpg](http://wpxldk.googlepages.com/gnomedo.jpg)

As you can see, only 1 track shows up...instead of all 4.
They all have the same artist name and album name (as you can see)

I already updated my rhythmbox library to no avail

any help?
thanks

My bet would be copy-paste the album name, year, etc, from one of the songs to the others, just in case...

---

### Post by marcordenis on 2008-09-09
thanks for this good news! was waiting for something like this because I love banshee and I love gnome do...

---

### Post by Duranxl on 2008-09-09
> **Arlanthir said:**
> My bet would be copy-paste the album name, year, etc, from one of the songs to the others, just in case...
Yes, i did..i selected all songs and then assigned the artist/album name for all 4 at the same time.

The thing is, other 3 songs are nowhere to be found in Gnome-do. If i enter "keith jarrett" they aren't listed under any other name either, while their artist is clearly "keith jarrett" 

:confused:

---

### Post by Duranxl on 2008-09-09
> **Duranxl said:**
> Yes, i did..i selected all songs and then assigned the artist/album name for all 4 at the same time.

The thing is, other 3 songs are nowhere to be found in Gnome-do. If i enter "keith jarrett" they aren't listed under any other name either, while their artist is clearly "keith jarrett" 

:confused:



edit: it seems there are more artists with songs missing..!!:(

whoops, hit quote instead of edit

---

### Post by Arlanthir on 2008-09-09
> **Duranxl said:**
> edit: it seems there are more artists with songs missing..!!:(

whoops, hit quote instead of edit


Have you been running Gnome-Do since before you copied those musics to your library? Try to restart gnome-do to check if it rebuilds his music library or something...

---

### Post by Duranxl on 2008-09-12
> **Arlanthir said:**
> Have you been running Gnome-Do since before you copied those musics to your library? Try to restart gnome-do to check if it rebuilds his music library or something...

No, that doesn't fix it..!:(

I'm having some more issues with gnome-do..
the locate files plugin won't work sometimes..i enter "september" in the raw text mode and press enter (locate files)..but the gnome-do screen will just disappear.
:confused:

---

### Post by conundrumx on 2008-09-12
Join #gnome-do on irc.freenode.net

Plenty of people (including developers) to help you there.

---

### Post by thomasboleyn on 2008-09-16
Sorry if this has been answered before, but has anyone got this working correctly on feisty?

---

### Post by Jakadinho on 2008-09-23
Hy.
I have installed 0.6 version on hardy.

I tried few plugins and they work fine but i have problems with Google calendar plugin

It seems like it doesnt save the pasword. I read that i have to alow mono to connect throught SLL or something but i dont know how to do it.

---

### Post by Arlanthir on 2008-10-01
Wow, gnome-do is starting to behave like a werewolf... When the night comes, it transforms and eats 40% of my CPU...

---

### Post by deuce868 on 2008-10-01
> **Arlanthir said:**
> Wow, gnome-do is starting to behave like a werewolf... When the night comes, it transforms and eats 40% of my CPU...

Yea, there's a known cpu bug that is fixed in dev, but not released yet. Hold on or try it from bzr.

---

### Post by Arlanthir on 2008-10-01
Glad to know that, I can wait ;)

---

### Post by DJ_Peng on 2008-10-02
> **deuce868 said:**
> Yea, there's a known cpu bug that is fixed in dev, but not released yet. Hold on or try it from bzr.
Damn. Is that why my CPU keeps kicking so hard when nothing else is going on? It was driving me nuts (it is a short drive) but I didn't know how to best check possibilities, although I did see that I was having to do a restart or force a kill of Do every morning.

Thanks for ID'ing the issue for me. I look forward to the update that fixes the bug.

---

### Post by sickenmcsluggets on 2008-10-06
Yay, I had to quit using gnome-do, but with today's update, maybe I can keep using it. 
From the [bugfix release]("https://launchpad.net/do/0.6/0.6.1")

> GNOME Do 0.6.1 bugfix release

Several bugfixes and small features:

Features
 * New icons
 * GConf schemas for easy distro integration

Bug fixes:
 * Small rendering fixes
 * Fix escaping of text
 * Fix libdir variable in do.dbus.pc
 *** Fix problem where Do would suddenly consume all CPU**


---

### Post by Jackelope on 2008-10-10
I tried the new release, but it still has an issue with using 50+ megs of memory after a few hours. I wish i could find a fix....Launchy just doesn't compare...

---

### Post by skankster on 2008-10-10
I'm getting cpu spikes with Gnome-Do on Hardy. A little while ago it was spiking up to 20% but seems to have settled down now and is spiking to 2-3% every 2-3 seconds. 

Does it do regular indexing updates like Launchy does, or is it something else? Anyway, I can live with 2% spikes (20% every couple of seconds kills any other cpu instensive operations though), so I'll see how it goes for now.

---

### Post by cetheriel on 2008-10-22
when i try add albums to play queue in rhythmbox, Gnome-Do adds only some random tracks... does it happen to all of you.
i use musicbrainz to tag my tracks, but i always close and re-open Do afterwards in order to refresh the index... am i doing it right?
btw, i'm using 0.6.1.0 release...

---

### Post by BionicSeahorse on 2008-10-23
I have problems with Tomboy Notes plugin v1.2.2 under Hardy x64. Anything I type in the second pane is ignored, and replaced with the default Tomboy Notes text ("Describe your new note here."). It doesn't matter which setting I use inside its preferences window.

---

### Post by lastchancetosee on 2008-10-31
> **cetheriel said:**
> when i try add albums to play queue in rhythmbox, Gnome-Do adds only some random tracks... does it happen to all of you.
i use musicbrainz to tag my tracks, but i always close and re-open Do afterwards in order to refresh the index... am i doing it right?
btw, i'm using 0.6.1.0 release...

Try selecting the missing tracks directly in Gnome Do. Do they appear in the lists? If not:

Same here. Most tracks turn up in Gnome Do, some random ones don't. Even stranger: Some tracks show up in Gnome Do, but when I open them a completely different track is opened.

(apparently the track one up in the library with the same genre-tag, i.e.:

In the Rhythmbox-library:

...
Hans Zimmer - Hoist the Colours - Genre: Soundtrack
Johannes Heil - Die Eigene Achse - Genre: Elektro
John Murphy - In The House, In A Heartbeat - Genre: Soundtrack
...

Selecting the John-Murphy-Track results in the Hans-Zimmer one being played.
But I have to test this behaviour further)

I've already tried closing&opening Gnome Do, rescanning the Rythmbox library etc.

---

### Post by conundrumx on 2008-10-31
The music player plugins are a relatively major focus of development for Do, since so many people use them.  I will make sure a developer sees this, see if we can't get some good information for you.

Edit: I just spoke with one of the lead developers, he's going to take a look tonight.

---

### Post by lastchancetosee on 2008-10-31
Perfect.
Thank you very much :-) .

[edit:
The one-above-in-genre-theory falls flat, by the way. Trying to open the moonshine sonata leads to a drum&bass track - and they are NOT the same genre :-) . Nor do they share any other easily discernable feature.]

---

### Post by cetheriel on 2008-10-31
here it sees everu single song, and plays 'em ok.
playing albums, however...
btw, why does it use the play queue? can't DO select an album and play right away??

---

### Post by paulmcfonty on 2008-11-02
Hi people,

i have some problems with the evolution plug-in of gnome-do 6.1; basically they don't work for me.

i'm working in ubuntu 8.10, with the repository versions of do (0.6.1.0-0ubuntu2) and do-plugins (0.6.0.1+dfsg-0ubuntu2), and if i try to execute the code from the terminal the messages is :

```
[Error 12:41:55.845] "Evolution Contacts" (Evolution.ContactItemSource) 
    encountered an error in UpdateItems: An exception was thrown by the type 
    initializer for Evolution.SourceList 

```

At the same time it's impossible build the bzr version of plug-in archive,
the make command return the following message: 

```
gmcs -noconfig -codepage:utf8 -warn:4 -optimize+ -debug
 "-define:DEBUG" -out:bin/Debug/Evolution.dll -target:library './src
/ContactDetailItem.cs' './src/ContactItemSource.cs' './src
/EmailContactDetailItem.cs' './src/PhoneContactDetailItem.cs'
  '-resource:./Resources/Evolution.addin.xml' '-resource:./Resources
/phone.png'    -r:System    -r:Mono.Posix    -r:/usr/lib/gnome-
do/Do.Addins.dll    -r:/usr/lib/cli/evolution-sharp-3.0/evolution-
sharp.dll  
./src/ContactItemSource.cs(84,58): error CS0246: The type or namespace 
name `AddressContactDetailItem' could not be found. Are you missing a
 using directive or an assembly reference?

```

do you have any idea ?

thanks in advance,
Paul

---

### Post by gerard67 on 2008-11-04
> **paulmcfonty said:**
> Hi people,

i have some problems with the evolution plug-in of gnome-do 6.1; basically they don't work for me.

i'm working in ubuntu 8.10, with the repository versions of do (0.6.1.0-0ubuntu2) and do-plugins (0.6.0.1+dfsg-0ubuntu2), and if i try to execute the code from the terminal the messages is :

```
[Error 12:41:55.845] "Evolution Contacts" (Evolution.ContactItemSource) 
    encountered an error in UpdateItems: An exception was thrown by the type 
    initializer for Evolution.SourceList 

```



This issue is reported on lanchpad, there is a bug report here : [https://bugs.launchpad.net/do/+bug/292622](https://bugs.launchpad.net/do/+bug/292622)
and an open question here :
[https://answers.launchpad.net/do/+question/49322](https://answers.launchpad.net/do/+question/49322)
However, it seems that it might be a problem with libevolution-cil rather than a gnome-do issue ...

Mathieu Petit

---

### Post by BionicSeahorse on 2008-11-05
> **BionicSeahorse said:**
> I have problems with Tomboy Notes plugin v1.2.2 under Hardy x64. Anything I type in the second pane is ignored, and replaced with the default Tomboy Notes text ("Describe your new note here."). It doesn't matter which setting I use inside its preferences window.

[https://answers.launchpad.net/do/+question/49688](https://answers.launchpad.net/do/+question/49688)

---

### Post by Ng Oon-Ee on 2008-11-25
Hi, has anyone here encountered a problem with Gnome-Do and *.desktop items? I have a folder full of *.desktop shortcuts to various apps that are hand-compiled and outside the normal apt-get/synaptic structure. I have added that folder to Gnome-Do using the Files and Folders plugin. Initially, I could run the shortcuts as if I were double-clicking them, but recently any attempt to run one of the shortcuts would simply open it in the text editor (gedit for me).

Any idea why this happens? I've seen the previous advise on update-alternatives but can't figure out which item refers to the *.desktop files.

---

### Post by davidsiegel on 2008-11-26
> **Ng Oon-Ee said:**
> Hi, has anyone here encountered a problem with Gnome-Do and *.desktop items? I have a folder full of *.desktop shortcuts to various apps that are hand-compiled and outside the normal apt-get/synaptic structure. I have added that folder to Gnome-Do using the Files and Folders plugin. Initially, I could run the shortcuts as if I were double-clicking them, but recently any attempt to run one of the shortcuts would simply open it in the text editor (gedit for me).

Any idea why this happens? I've seen the previous advise on update-alternatives but can't figure out which item refers to the *.desktop files.

Hey, I will commit a fix for this this weekend. The thing is, .desktop files are actually just plain files, and are treated as such. I will make it so that they are no longer treated as files (you will lose the ability to use the Open, Copy, etc. actions on them) but rather as application items. Can you please submit a bug and assign it to djsiegel? [http://bugs.launchpad.net/do](http://bugs.launchpad.net/do)

---

### Post by davidsiegel on 2008-11-26
> **lastchancetosee said:**
> Try selecting the missing tracks directly in Gnome Do. Do they appear in the lists? If not:

Same here. Most tracks turn up in Gnome Do, some random ones don't. Even stranger: Some tracks show up in Gnome Do, but when I open them a completely different track is opened.

(apparently the track one up in the library with the same genre-tag, i.e.:

In the Rhythmbox-library:

...
Hans Zimmer - Hoist the Colours - Genre: Soundtrack
Johannes Heil - Die Eigene Achse - Genre: Elektro
John Murphy - In The House, In A Heartbeat - Genre: Soundtrack
...

Selecting the John-Murphy-Track results in the Hans-Zimmer one being played.
But I have to test this behaviour further)

I've already tried closing&opening Gnome Do, rescanning the Rythmbox library etc.

This should be completely fixed in the next release (0.8). Please test trunk if you are able. [https://bugs.edge.launchpad.net/do-plugins/+bug/248916](https://bugs.edge.launchpad.net/do-plugins/+bug/248916)

---

### Post by Ng Oon-Ee on 2008-11-26
> **davidsiegel said:**
> Hey, I will commit a fix for this this weekend. The thing is, .desktop files are actually just plain files, and are treated as such. I will make it so that they are no longer treated as files (you will lose the ability to use the Open, Copy, etc. actions on them) but rather as application items. Can you please submit a bug and assign it to djsiegel? [http://bugs.launchpad.net/do](http://bugs.launchpad.net/do)

Done, at [https://bugs.launchpad.net/do/+bug/302661]("https://bugs.launchpad.net/do/+bug/302661").

Anything else I can do to help? I'd assume I need to be running trunk to test this, when you fix it?

---

### Post by Ng Oon-Ee on 2008-12-14
Hi, I see that a fix has been committed, any way I could test it out?

---

### Post by Ng Oon-Ee on 2008-12-18
Hey, if anyone knows of a repo and/or script for trunk Gnome-do I'd appreciate it, don't look forward to source compiling.

Another question, Gnome-do doesn't seem to work on my second monitor (separate X, no Xinerama). Anyone encountered that before?

---

### Post by DJ_Peng on 2008-12-19
The [Do launchpad page]("https://launchpad.net/do") has a link labeled > Installation instructions: [http://do.davebsd.com/wiki/index.php?title=Installing_Do](http://do.davebsd.com/wiki/index.php?title=Installing_Do)The page that link goes to has this:
> **  Ubuntu **

 **  8.10 (Intrepid) **
```

 $ sudo aptitude install gnome-do
```If you're not running Intrepid the page has instructions for other versions, complete with repos.

---

### Post by Ng Oon-Ee on 2008-12-19
> **DJ_Peng said:**
> The [Do launchpad page]("https://launchpad.net/do") has a link labeled The page that link goes to has this:
If you're not running Intrepid the page has instructions for other versions, complete with repos.
Um... thanks for being helpful, but from my previous post it should be clear that I've already got Gnome-Do installed from the repos, and that I found a small bug and would like now to test the fix. And so, I'd  have to test the trunk version instead of what's in the repos (as instructed by davidsiegel. So I was looking for help on installing trunk without compiling from source.

---

### Post by DJ_Peng on 2008-12-20
Sorry about that. I missed that you were looking for a trunk repo.

---

### Post by Ng Oon-Ee on 2008-12-20
> **DJ_Peng said:**
> Sorry about that. I missed that you were looking for a trunk repo.
Not a problem.

So, anyone have any idea?

---

### Post by davidsiegel on 2008-12-20
[http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source](http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source)


Let me know if you need more help.

---

### Post by Ng Oon-Ee on 2008-12-21
> **davidsiegel said:**
> [http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source](http://do.davebsd.com/wiki/index.php?title=Installing_Do#From_Source)


Let me know if you need more help.
Ah.... source compiles....

Guess its the least I could do in appreciation for the quick bug fix =). Oh, and since I mentioned that, thanks.

---

### Post by Ng Oon-Ee on 2008-12-21
Hey, tried compiling it, got these warnings/error msgs.

```
Compiling Do.exe...
warning CS8030: Deprecated: The `linq' option is no longer required and should not be used
./src/Do.Core/UniverseManager.cs(159,41): warning CS1030: #warning: `The Log is not threadsafe...'
./src/Do.Core/UniverseManager.cs(165,41): warning CS1030: #warning: `The Log is not threadsafe...'
./src/Do.UI/ColorConfigurationWidget.cs(33,31): error CS0103: The name `<Themes>k__BackingField' does not exist in the current context
./src/Do.UI/ColorConfigurationWidget.cs(33,31): error CS0103: The name `<Themes>k__BackingField' does not exist in the current context
```

Looks like its trying to compile a gnome-do executable for a whole bunch of platforms, the one where it runs into an error is at Do.exe, of all things. Didn't even know gnome-do runs on Windows? I'm running 64-bits, maybe that's confusing the script?


EDIT: Ah, [this bug]("https://bugs.launchpad.net/do/+bug/307308") says its a known issue and mentions a code migration. Will have to wait I guess? Any workarounds?

---

### Post by russo.mic on 2008-12-24
> **davidsiegel said:**
> What's not usable about it? I'm the lead developer and your feedback is really appreciated. If you tell me what is unusable I can fix it.

Keep in mind that is is my first public release. The version is 0.0.1 - I have a long way to go until 1.0. If you tell me that it needs preferences or other niceties, all I can say is that's coming.

Man I LOVE Gnome-Do...great program. My only gripe...Where is the amarok plugin?  we ever going to get it back?  

I suppose you hear this often..

Russo

---

### Post by Ng Oon-Ee on 2008-12-24
> **russo.mic said:**
> Man I LOVE Gnome-Do...great program. My only gripe...Where is the amarok plugin?  we ever going to get it back?  

I suppose you hear this often..

Russo
I've been messing with source-compiling from bazaar. Am happy to report that the plugin is fully functional in that case. Though for me, I've reverted to the repo version for a while, since the primary reason I wanted to test it out was to test some fixes on 'files and folders' but I can't seem to get it to load up without error. Will be looking back at it after the festivities are over.

Oh, and in case you want to go the compile-from-source route, you'll need mono 2.0, at [this blog]("http://eric.extremeboredom.net/2008/10/15/296") there's a ppa for it. Had me stumped, but David kindly helped me on my way. Also, you may need to symlink gcms2 to gcms, in your /usr/bin. I did, anyway.

---

### Post by russo.mic on 2008-12-24
aaahh.....thanks for the tip.  Didn't realize it was still in the source...i'm gonna get right on that.

Russo

---

### Post by directhex on 2008-12-24
> **Ng Oon-Ee said:**
> Also, you may need to symlink gcms2 to gcms, in your /usr/bin. I did, anyway.

Install mono-devel.

---

### Post by russo.mic on 2008-12-24
So, trying to build from source to get the Amarok Plugin, and I'm getting this error:

Making all in .
make[1]: Entering directory `/home/russo/gnome-do'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/russo/gnome-do'
Making all in Do.Universe
make[1]: Entering directory `/home/russo/gnome-do/Do.Universe'
Compiling Do.Universe.dll...
/bin/bash: no: command not found
make[1]: *** [../build/Do.Universe.dll] Error 127
make[1]: Leaving directory `/home/russo/gnome-do/Do.Universe'
make: *** [all-recursive] Error 1

when I make, ./autogen-sh seems to complete fine...any ideas?

Thanks in advance!
Russo


Edit: NEVER MIND...The second after I posted I read above...thanks.

---

### Post by directhex on 2008-12-24
> **russo.mic said:**
> So, trying to build from source to get the Amarok Plugin, and I'm getting this error:

Making all in .
make[1]: Entering directory `/home/russo/gnome-do'
make[1]: Nothing to be done for `all-am'.
make[1]: Leaving directory `/home/russo/gnome-do'
Making all in Do.Universe
make[1]: Entering directory `/home/russo/gnome-do/Do.Universe'
Compiling Do.Universe.dll...
/bin/bash: no: command not found
make[1]: *** [../build/Do.Universe.dll] Error 127
make[1]: Leaving directory `/home/russo/gnome-do/Do.Universe'
make: *** [all-recursive] Error 1

when I make, ./autogen-sh seems to complete fine...any ideas?

Thanks in advance!
Russo

"/bin/bash: no: command not found" is a common problem with badly formed automake nonsense.

You are missing a "gmcs", I suspect

---

### Post by russo.mic on 2008-12-24
So, I'm getting the DLL files compiled, but placing them in ~/.local/share/gnome-do/plugins seems to do nothing.

I had to make the directory,  Where do these files go after being built?

Thanks!

Russo

---

### Post by Ng Oon-Ee on 2008-12-24
> **russo.mic said:**
> So, I'm getting the DLL files compiled, but placing them in ~/.local/share/gnome-do/plugins seems to do nothing.

I had to make the directory,  Where do these files go after being built?

Thanks!

Russo
What I found was that instead of creating the directory you should use the one there (I think its plugins 8.0.0 or something). Put the DLL in, then quit and restart gnome-do. Doing this from terminal allows you to see what's happening.

---

### Post by Ng Oon-Ee on 2008-12-24
> **directhex said:**
> Install mono-devel.
Hi, I have mono-devel installed (mono-1.0-devel and mono-2.0-devel both) but I still do not have a gmcs in my /usr/bin, only a gmcs2. Anything else that's needed?

---

### Post by directhex on 2008-12-24
> **Ng Oon-Ee said:**
> Hi, I have mono-devel installed (mono-1.0-devel and mono-2.0-devel both) but I still do not have a gmcs in my /usr/bin, only a gmcs2. Anything else that's needed?

Sigh.

If I meant "mono-1.0-devel" and "mono-2.0-devel", I'd have said so.

[http://packages.ubuntu.com/search?searchon=contents&keywords=gmcs&mode=exactfilename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=gmcs&mode=exactfilename&suite=jaunty&arch=any)

If mono-devel is missing from your PPA's packages, then that repository is inherently broken.

---

### Post by Ng Oon-Ee on 2008-12-25
> **directhex said:**
> Sigh.

If I meant "mono-1.0-devel" and "mono-2.0-devel", I'd have said so.

[http://packages.ubuntu.com/search?searchon=contents&keywords=gmcs&mode=exactfilename&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=gmcs&mode=exactfilename&suite=jaunty&arch=any)

If mono-devel is missing from your PPA's packages, then that repository is inherently broken.
Sorry that I'm so tiresome, but mono-devel is a jaunty package and I'm on Intrepid, where the package that provides gmcs is mono-gmcs, which I do have installed. Unfortunately my ppa only provides gmcs2 instead of gmcs. Symlinking it seems to work though.

---

### Post by directhex on 2008-12-26
> **Ng Oon-Ee said:**
> Sorry that I'm so tiresome, but mono-devel is a jaunty package and I'm on Intrepid, where the package that provides gmcs is mono-gmcs, which I do have installed. Unfortunately my ppa only provides gmcs2 instead of gmcs. Symlinking it seems to work though.

There's no such thing as gmcs2 on any version of Debian Mono packaging prior to 2.0-1

If you have gmcs2 but no mono-devel package, then your package source is broken beyond use and should not be touched.

---

### Post by Ng Oon-Ee on 2008-12-26
Well, since compiling Gnome-Do from source on current bzr REQUIRES mono 2.0, then obviously since I'm on Intrepid I'm getting it from an external PPA. I'm using [this PPA]("http://eric.extremeboredom.net/2008/10/15/296"), as recommended by david in a bug report I made on compiling Gnome-Do.

Is the package source broken beyond use? Perhaps, you know much more than I do on this topic. Unfortunately there doesn't seem to be an alternative for me, if I want to test out the latest gnome-do. I'd be grateful for alternatives, if possible.

---

### Post by Ng Oon-Ee on 2009-01-04
> **Ng Oon-Ee said:**
> Well, since compiling Gnome-Do from source on current bzr REQUIRES mono 2.0, then obviously since I'm on Intrepid I'm getting it from an external PPA. I'm using [this PPA]("http://eric.extremeboredom.net/2008/10/15/296"), as recommended by david in a bug report I made on compiling Gnome-Do.

Is the package source broken beyond use? Perhaps, you know much more than I do on this topic. Unfortunately there doesn't seem to be an alternative for me, if I want to test out the latest gnome-do. I'd be grateful for alternatives, if possible.
Ah, after moving on from this topic, I was killing some time and decided to check the existance of mono-devel again, and this time it turned up. I was affected by the quick-search bug in the latest Synaptic, where the results don't show every correct match. A proper search did the trick.

Anyway, another question, I have two x-sessions (one per monitor), and the shortcut key (SUPER-space) only works in my main monitor, in the other one it does nothing, but when I run 'gnome-do' from alt-F2 or from terminal, the gnome-do window appears, in the MAIN monitor.

Haven't been able to find much on this in the launchpad bugs (added on to one of the existing) or indeed anywhere else.

---

### Post by Luffield on 2009-01-11
First Alpha of GNOME Do 0.8 [is ready]("https://launchpad.net/do/+announcement/1780"). Anyone tried it yet? What's new in this version?

---

### Post by DJ_Peng on 2009-01-12
I'm hoping to see a deb for 0.8 myself before too long. But one query: Did we skip a number? I'm showing I have 0.6.1.0. Did I sleep though version 0.7?

---

### Post by Luffield on 2009-01-12
0.7 was never released according to [this page]("https://launchpad.net/do").

---

### Post by Luffield on 2009-01-12
And thanks to DJ_Peng's question I also found an answer to my own question: here's [what's new in version 0.8]("https://launchpad.net/do/+milestone/0.8"). Sounds like a good release.

---

### Post by DJ_Peng on 2009-01-12
I'm looking forward to the upgrade. But for those who haven't seen it, they launched a [website]("http://do.davebsd.com/") [update]("http://groups.google.com/group/gnome-do/browse_thread/thread/612bab8663fa6551?hl=en").

---

### Post by Sugz on 2009-01-12
Hello, are there any plans to update the Gusty Version?
As there is a major memory leak in it.
Are all new releases only going to be for newer versions of Ubuntu?

---

### Post by davidsiegel on 2009-01-12
> **Sugz said:**
> Hello, are there any plans to update the Gusty Version?
As there is a major memory leak in it.
Are all new releases only going to be for newer versions of Ubuntu?

Sugz, no, we have no plans to support Gutsy.

---

### Post by DJ_Peng on 2009-01-15
Yesterday I grabbed version 0.7.95.1 from the Do testing PPA and I'm not able to launch any apps like I used to. I did see that there's an update coming from source but is there something I need to do to get the standard launch feature working again?

---

### Post by davidsiegel on 2009-01-15
> **DJ_Peng said:**
> Yesterday I grabbed version 0.7.95.1 from the Do testing PPA and I'm not able to launch any apps like I used to. I did see that there's an update coming from source but is there something I need to do to get the standard launch feature working again?

Can you please post the output of running:

```
$ gnome-do --debug
```

in a terminal? File a bug report ([http://bugs.launchpad.net/do](http://bugs.launchpad.net/do)) if an error regarding application item indexing is printed.

---

### Post by DJ_Peng on 2009-01-15
I disabled all of my plugins, ran that command, and found a shortcut on my desktop was throwing things off. As soon as I got it off my desktop I'm able to use Do properly. It's weird because I'm seeing links to UF threads dropped on my desktop from Epiphany give me errors.

I'm going to have to file a bug on the fact that I keep getting the notification icon despite having cleared the checkbox. (It looks like someone already filed a [bug]("https://bugs.launchpad.net/do/+bug/316977") against it already.)

Thanks for helping me find the main issue.

---

### Post by evilkastel on 2009-01-18
Hey i absolutely love docky. Since i put a howto install in my blog my visits tripled lol. I had an issue with it, tough, launchers won't work on click, only on right click-Execute. Running --debug i found an issue with the files plugin, so i deleted everything inside /home/meself/.local/share/gnome-do/ and it got fixed, after a reinstall. just a heads up and a ty .

---

### Post by DJ_Peng on 2009-01-18
Heh heh. You too? My traffic shot to a new all-time high after posting about it. I went from an old high of 1,574 (average about 3-500 hits per day) to 3,208 hits on Friday. *Yowza!*

---

### Post by smbm on 2009-01-19
The new version of Do in the PPA is giving me some problems, specifically the Firefox plugin, it seems to be allowing me quick and easy access to all my bookmarks except for the one that I would want to open most, Gmail. 

Is anyone else experiencing anything similar?

Does anyone have any ideas how I can fix it?

Cheers.

---

### Post by adrpater on 2009-01-23
I'm also encountering Problems with PPA.
I can not start applications anymore.
It seems Do no longer picks up my shortcuts.
When starting from terminal, I get the following error:

```

Do.Universe.Linux.ApplicationItemSource "Applications" encountered an error in UpdateItems: Object reference not set to an instance of an object.

```

Reverting back to 0.6 in Intrepid.

---

### Post by Skoezie on 2009-01-24
Gnome Do is awesome. Keep up the good work. :) Is there any way to change the size of the icons when using docky? When I put 10 icons on it, it takes up all of the space at the bottom of the screen. Bit to much.

---

### Post by twisted_steel on 2009-01-24
> **Skoezie said:**
> Gnome Do is awesome. Keep up the good work. :) Is there any way to change the size of the icons when using docky? When I put 10 icons on it, it takes up all of the space at the bottom of the screen. Bit to much.

Put your cursor over the dashed vertical line to the left of the trash can on Docky. You should see it change to a double-arrow. You can drag this up to make Docky (and the icons) larger, or down to make everything smaller.

---

### Post by Vadi on 2009-01-24
New version in ppa has a failed 64bit build and I can't upgrade the plugins.

---

### Post by gjoellee on 2009-01-24
Gnome Do is just excellent!

---

### Post by jnbptst on 2009-01-25
I'm on 8.04, and Gnome-DO doesn't start. Here is the output of the terminal:

```
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0x00004>
  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0xffffffff>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) <0x002be>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0xffffffff>
  at System.IO.File.OpenRead (string) <0x00021>
  at System.IO.StreamReader..ctor (string,System.Text.Encoding,bool,int) <0x00072>
  at System.IO.StreamReader..ctor (string) <0x00026>
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader..ctor (string) <0xffffffff>
  at Do.Paths.ReadXdgUserDir (string,string) <0x000af>
  at Do.Paths.get_ApplicationData () <0x00015>
  at Do.Paths.get_Temp () <0x0000b>
  at Do.Paths..cctor () <0x00012>
  at (wrapper runtime-invoke) Do.Paths.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Do.Core.PluginManager.Initialize () <0xffffffff>
  at Do.Core.PluginManager.Initialize () <0x00022>
  at Do.Do.Main (string[]) <0x0012f>
  at (wrapper runtime-invoke) Do.Do.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	/usr/bin/cli [0x816b1fa]
	/usr/bin/cli [0x807de81]
	[0xb7fc7440]
	/usr/bin/cli [0x810efc2]
	/usr/bin/cli [0x810f2cc]
	/usr/bin/cli [0x80d273b]
	[0xb65a2126]
	[0xb65a0df7]
	[0xb65a0b20]
	[0xb65a0adc]
	[0xb65a0a72]
	[0xb65a0913]
	[0xb65a0887]
	[0xb65a083a]
	[0xb659e890]
	[0xb659e796]
	[0xb659e744]
	[0xb659e5f3]
	[0xb659e576]
	/usr/bin/cli(mono_runtime_class_init+0x311) [0x8099ca1]
	/usr/bin/cli [0x8158647]
	/usr/bin/cli [0x807f936]
	[0xb7c09066]
	[0xb79383a0]
	[0xb79381c3]
	/usr/bin/cli(mono_runtime_exec_main+0xbb) [0x809c63b]
	/usr/bin/cli(mono_runtime_run_main+0x173) [0x809c933]
	/usr/bin/cli(mono_main+0x6a9) [0x805acd9]
	/usr/bin/cli [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d78450]
	/usr/bin/cli [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d396d0 (LWP 19785)]
[New Thread 0xb73afb90 (LWP 19792)]
[New Thread 0xb73d3b90 (LWP 19791)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7fc7410 in __kernel_vsyscall ()
  3 Thread 0xb73d3b90 (LWP 19791)  0xb7fc7410 in __kernel_vsyscall ()
  2 Thread 0xb73afb90 (LWP 19792)  0xb7fc7410 in __kernel_vsyscall ()
  1 Thread 0xb7d396d0 (LWP 19785)  0xb7fc7410 in __kernel_vsyscall ()

Thread 3 (Thread 0xb73d3b90 (LWP 19791)):
#0  0xb7fc7410 in __kernel_vsyscall ()
#1  0xb7ee3196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb7edb4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7e38e5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb73afb90 (LWP 19792)):
#0  0xb7fc7410 in __kernel_vsyscall ()
#1  0xb7edfaa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080b1c0a in ?? ()
#7  0x080cef04 in ?? ()
#8  0x0811a7c2 in ?? ()
#9  0x081317a5 in ?? ()
#10 0xb7edb4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7e38e5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7d396d0 (LWP 19785)):
#0  0xb7fc7410 in __kernel_vsyscall ()
#1  0xb7df7d89 in fork () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7ee5034 in fork () from /lib/tls/i686/cmov/libpthread.so.0
#3  0xb7f5f489 in ?? () from /usr/lib/libglib-2.0.so.0
#4  0xb7f600ad in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#5  0xb7f6056c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#6  0x0816b295 in ?? ()
#7  0x0807de81 in ?? ()
#8  <signal handler called>
#9  0x08109bf0 in ?? ()
#10 0x0810efc2 in ?? ()
#11 0x0810f2cc in ?? ()
#12 0x080d273b in ?? ()
#13 0xb65a2126 in ?? ()
#14 0xb65a0df7 in ?? ()
#15 0xb65a0b20 in ?? ()
#16 0xb65a0adc in ?? ()
#17 0xb65a0a72 in ?? ()
#18 0xb65a0913 in ?? ()
#19 0xb65a0887 in ?? ()
#20 0xb65a083a in ?? ()
#21 0xb659e890 in ?? ()
#22 0xb659e796 in ?? ()
#23 0xb659e744 in ?? ()
#24 0xb659e5f3 in ?? ()
#25 0xb659e576 in ?? ()
#26 0x08099ca1 in mono_runtime_class_init ()
#27 0x08158647 in ?? ()
#28 0x0807f936 in ?? ()
#29 0xb7c09066 in ?? ()
#30 0xb79383a0 in ?? ()
#31 0xb79381c3 in ?? ()
#32 0x0809c63b in mono_runtime_exec_main ()
#33 0x0809c933 in mono_runtime_run_main ()
#34 0x0805acd9 in mono_main ()
#35 0x0805a122 in ?? ()
#36 0xb7d78450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#37 0x0805a091 in ?? ()
#0  0xb7fc7410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================


```

Any idea about how to fix this? Thanks in advance

---

### Post by narselon on 2009-01-25
I like the docky setting as a dock, but it seems like when in this mode the main functionality is limited. You can't browse through results as easily and certain plugins don't work the same way. Before it would list files and folders amongst the search results. If they can bring back the traditional functionality or let it launch the normal two pane pop up in addition then it would be perfect.

---

### Post by cetheriel on 2009-01-26
anyone using Do with Remember the Milk (RTM)?
it rocks, best combo so far, but adding tasks is not working here...
documentation on gnome-do wiki stops before adding tasks section.
guess it is still under development.

---

### Post by jnbptst on 2009-01-26
you can install tasque, which works as a frontend for RTM, and then enable the gnome-do tasque plugin.

---

### Post by Chang An on 2009-01-31
Docky is cool but there are at least three things that it really needs for me to switch to it.

1. Docky should be able to hide behind other windows when maximized.
2. Docky should have applets for cpu, ram, weather and what not.
3. Docky should be able to browse applications, files, ect, with a similar style as the classic interface.  I made a mock up demonstrating of what I mean below.

Nail down those three and I can finally leave Cairo-Dock.  That being said, great work on this one devs.

[IMG]http://dl.getdropbox.com/u/200209/Screenshot.png[/IMG]

---

### Post by fifth_rune on 2009-01-31
Hmm, I'm getting an error using the PPA version.  Seems that Gnome-Do is no longer picking up my applications or anything else in my 'main menu' bar like 'applications' and 'system.'  Any fixes for this?

---

### Post by deathblossom on 2009-02-01
Yeah I upgraded from 0.6 to 0.8 on Intrepid right now and I can't get the power management plugin to work. As in, I try to check it and it immediately unchecks itself. Does this with the Firefox 3 bookmarks plugin as well, but I care infinitely less about that one.

---

### Post by zekopeko on 2009-02-01
> **deathblossom said:**
> Yeah I upgraded from 0.6 to 0.8 on Intrepid right now and I can't get the power management plugin to work. As in, I try to check it and it immediately unchecks itself. Does this with the Firefox 3 bookmarks plugin as well, but I care infinitely less about that one.

try running gnome-do from the terminal with

gnome-do --debug

and report a bug on do-plugins in launchpad

---

### Post by Vadi on 2009-02-01
Certainly odd to see .exe files on Linux too. I filed the bug as I was experiencing it too.

---

### Post by jnbptst on 2009-02-01
Here is what I get after adding the debug option:

```
jnbptst@jnbptst-laptop:~$ gnome-do --debug
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0x00004>
  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0xffffffff>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) <0x002be>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0xffffffff>
  at System.IO.File.OpenRead (string) <0x00021>
  at System.IO.StreamReader..ctor (string,System.Text.Encoding,bool,int) <0x00072>
  at System.IO.StreamReader..ctor (string) <0x00026>
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader..ctor (string) <0xffffffff>
  at Do.Paths.ReadXdgUserDir (string,string) <0x000af>
  at Do.Paths.get_ApplicationData () <0x00015>
  at Do.Paths.get_Temp () <0x0000b>
  at Do.Paths..cctor () <0x00012>
  at (wrapper runtime-invoke) Do.Paths.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Do.Core.PluginManager.Initialize () <0xffffffff>
  at Do.Core.PluginManager.Initialize () <0x00022>
  at Do.Do.Main (string[]) <0x0012f>
  at (wrapper runtime-invoke) Do.Do.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	/usr/bin/cli [0x816b1fa]
	/usr/bin/cli [0x807de81]
	[0xb7fdb440]
	/usr/bin/cli [0x810efc2]
	/usr/bin/cli [0x810f2cc]
	/usr/bin/cli [0x80d273b]
	[0xb65b613e]
	[0xb65b4e0f]
	[0xb65b4b38]
	[0xb65b4af4]
	[0xb65b4a8a]
	[0xb65b492b]
	[0xb65b489f]
	[0xb65b4852]
	[0xb65b28a8]
	[0xb65b27ae]
	[0xb65b275c]
	[0xb65b260b]
	[0xb65b258e]
	/usr/bin/cli(mono_runtime_class_init+0x311) [0x8099ca1]
	/usr/bin/cli [0x8158647]
	/usr/bin/cli [0x807f936]
	[0xb7c1d066]
	[0xb794c3a0]
	[0xb794c1c3]
	/usr/bin/cli(mono_runtime_exec_main+0xbb) [0x809c63b]
	/usr/bin/cli(mono_runtime_run_main+0x173) [0x809c933]
	/usr/bin/cli(mono_main+0x6a9) [0x805acd9]
	/usr/bin/cli [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d8c450]
	/usr/bin/cli [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d4d6d0 (LWP 15803)]
[New Thread 0xb73c3b90 (LWP 15810)]
[New Thread 0xb73e7b90 (LWP 15809)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7fdb410 in __kernel_vsyscall ()
  3 Thread 0xb73e7b90 (LWP 15809)  0xb7fdb410 in __kernel_vsyscall ()
  2 Thread 0xb73c3b90 (LWP 15810)  0xb7fdb410 in __kernel_vsyscall ()
  1 Thread 0xb7d4d6d0 (LWP 15803)  0xb7fdb410 in __kernel_vsyscall ()

Thread 3 (Thread 0xb73e7b90 (LWP 15809)):
#0  0xb7fdb410 in __kernel_vsyscall ()
#1  0xb7ef7196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb7eef4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7e4ce5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb73c3b90 (LWP 15810)):
#0  0xb7fdb410 in __kernel_vsyscall ()
#1  0xb7ef3aa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080b1c0a in ?? ()
#7  0x080cef04 in ?? ()
#8  0x0811a7c2 in ?? ()
#9  0x081317a5 in ?? ()
#10 0xb7eef4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7e4ce5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7d4d6d0 (LWP 15803)):
#0  0xb7fdb410 in __kernel_vsyscall ()
#1  0xb7e45881 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f741a4 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f7456c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b295 in ?? ()
#5  0x0807de81 in ?? ()
#6  <signal handler called>
#7  0x08109bf0 in ?? ()
#8  0x0810efc2 in ?? ()
#9  0x0810f2cc in ?? ()
#10 0x080d273b in ?? ()
#11 0xb65b613e in ?? ()
#12 0xb65b4e0f in ?? ()
#13 0xb65b4b38 in ?? ()
#14 0xb65b4af4 in ?? ()
#15 0xb65b4a8a in ?? ()
#16 0xb65b492b in ?? ()
#17 0xb65b489f in ?? ()
#18 0xb65b4852 in ?? ()
#19 0xb65b28a8 in ?? ()
#20 0xb65b27ae in ?? ()
#21 0xb65b275c in ?? ()
#22 0xb65b260b in ?? ()
#23 0xb65b258e in ?? ()
#24 0x08099ca1 in mono_runtime_class_init ()
#25 0x08158647 in ?? ()
#26 0x0807f936 in ?? ()
#27 0xb7c1d066 in ?? ()
#28 0xb794c3a0 in ?? ()
#29 0xb794c1c3 in ?? ()
#30 0x0809c63b in mono_runtime_exec_main ()
#31 0x0809c933 in mono_runtime_run_main ()
#32 0x0805acd9 in mono_main ()
#33 0x0805a122 in ?? ()
#34 0xb7d8c450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#35 0x0805a091 in ?? ()
#0  0xb7fdb410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

---

### Post by directhex on 2009-02-02
> **jnbptst said:**
> Here is what I get after adding the debug option:

```
jnbptst@jnbptst-laptop:~$ gnome-do --debug
Stacktrace:

  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0x00004>
  at (wrapper managed-to-native) System.IO.MonoIO.Open (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,System.IO.FileOptions,System.IO.MonoIOError&) <0xffffffff>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare,int,bool,System.IO.FileOptions) <0x002be>
  at System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0x0001f>
  at (wrapper remoting-invoke-with-check) System.IO.FileStream..ctor (string,System.IO.FileMode,System.IO.FileAccess,System.IO.FileShare) <0xffffffff>
  at System.IO.File.OpenRead (string) <0x00021>
  at System.IO.StreamReader..ctor (string,System.Text.Encoding,bool,int) <0x00072>
  at System.IO.StreamReader..ctor (string) <0x00026>
  at (wrapper remoting-invoke-with-check) System.IO.StreamReader..ctor (string) <0xffffffff>
  at Do.Paths.ReadXdgUserDir (string,string) <0x000af>
  at Do.Paths.get_ApplicationData () <0x00015>
  at Do.Paths.get_Temp () <0x0000b>
  at Do.Paths..cctor () <0x00012>
  at (wrapper runtime-invoke) Do.Paths.runtime_invoke_void (object,intptr,intptr,intptr) <0xffffffff>
  at Do.Core.PluginManager.Initialize () <0xffffffff>
  at Do.Core.PluginManager.Initialize () <0x00022>
  at Do.Do.Main (string[]) <0x0012f>
  at (wrapper runtime-invoke) Do.Do.runtime_invoke_void_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	/usr/bin/cli [0x816b1fa]
	/usr/bin/cli [0x807de81]
	[0xb7fdb440]
	/usr/bin/cli [0x810efc2]
	/usr/bin/cli [0x810f2cc]
	/usr/bin/cli [0x80d273b]
	[0xb65b613e]
	[0xb65b4e0f]
	[0xb65b4b38]
	[0xb65b4af4]
	[0xb65b4a8a]
	[0xb65b492b]
	[0xb65b489f]
	[0xb65b4852]
	[0xb65b28a8]
	[0xb65b27ae]
	[0xb65b275c]
	[0xb65b260b]
	[0xb65b258e]
	/usr/bin/cli(mono_runtime_class_init+0x311) [0x8099ca1]
	/usr/bin/cli [0x8158647]
	/usr/bin/cli [0x807f936]
	[0xb7c1d066]
	[0xb794c3a0]
	[0xb794c1c3]
	/usr/bin/cli(mono_runtime_exec_main+0xbb) [0x809c63b]
	/usr/bin/cli(mono_runtime_run_main+0x173) [0x809c933]
	/usr/bin/cli(mono_main+0x6a9) [0x805acd9]
	/usr/bin/cli [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7d8c450]
	/usr/bin/cli [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d4d6d0 (LWP 15803)]
[New Thread 0xb73c3b90 (LWP 15810)]
[New Thread 0xb73e7b90 (LWP 15809)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7fdb410 in __kernel_vsyscall ()
  3 Thread 0xb73e7b90 (LWP 15809)  0xb7fdb410 in __kernel_vsyscall ()
  2 Thread 0xb73c3b90 (LWP 15810)  0xb7fdb410 in __kernel_vsyscall ()
  1 Thread 0xb7d4d6d0 (LWP 15803)  0xb7fdb410 in __kernel_vsyscall ()

Thread 3 (Thread 0xb73e7b90 (LWP 15809)):
#0  0xb7fdb410 in __kernel_vsyscall ()
#1  0xb7ef7196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb7eef4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7e4ce5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb73c3b90 (LWP 15810)):
#0  0xb7fdb410 in __kernel_vsyscall ()
#1  0xb7ef3aa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080b1c0a in ?? ()
#7  0x080cef04 in ?? ()
#8  0x0811a7c2 in ?? ()
#9  0x081317a5 in ?? ()
#10 0xb7eef4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7e4ce5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7d4d6d0 (LWP 15803)):
#0  0xb7fdb410 in __kernel_vsyscall ()
#1  0xb7e45881 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f741a4 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f7456c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b295 in ?? ()
#5  0x0807de81 in ?? ()
#6  <signal handler called>
#7  0x08109bf0 in ?? ()
#8  0x0810efc2 in ?? ()
#9  0x0810f2cc in ?? ()
#10 0x080d273b in ?? ()
#11 0xb65b613e in ?? ()
#12 0xb65b4e0f in ?? ()
#13 0xb65b4b38 in ?? ()
#14 0xb65b4af4 in ?? ()
#15 0xb65b4a8a in ?? ()
#16 0xb65b492b in ?? ()
#17 0xb65b489f in ?? ()
#18 0xb65b4852 in ?? ()
#19 0xb65b28a8 in ?? ()
#20 0xb65b27ae in ?? ()
#21 0xb65b275c in ?? ()
#22 0xb65b260b in ?? ()
#23 0xb65b258e in ?? ()
#24 0x08099ca1 in mono_runtime_class_init ()
#25 0x08158647 in ?? ()
#26 0x0807f936 in ?? ()
#27 0xb7c1d066 in ?? ()
#28 0xb794c3a0 in ?? ()
#29 0xb794c1c3 in ?? ()
#30 0x0809c63b in mono_runtime_exec_main ()
#31 0x0809c933 in mono_runtime_run_main ()
#32 0x0805acd9 in mono_main ()
#33 0x0805a122 in ?? ()
#34 0xb7d8c450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#35 0x0805a091 in ?? ()
#0  0xb7fdb410 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

I saw someone on the forum throwing the same errors running Banshee. I'd be interested to hear if you find a solution

---

### Post by Maupertus on 2009-02-02
> **Chang An said:**
> Docky is cool but there are at least three things that it really needs for me to switch to it.

1. Docky should be able to hide behind other windows when maximized.
2. Docky should have applets for cpu, ram, weather and what not.
3. Docky should be able to browse applications, files, ect, with a similar style as the classic interface.  I made a mock up demonstrating of what I mean below.

Nail down those three and I can finally leave Cairo-Dock.  That being said, great work on this one devs.

It's hard not to agree with you, but everytime I'm disappointed with the lack of small 'widgets' like a show desktop, or desktop switcher, I realize that:

a) It's very much a beta
b) Gnome-do (which it still is, although radically different) is something very different to Cairo or AWN. 

And that makes me happy again, works every time.

---

### Post by engineer on 2009-02-02
On their webpage they say, that there is an error with ppa for 64 bit users. But they are offering a .deb package file.

[https://launchpad.net/do/+download]("https://launchpad.net/do/+download")

---

### Post by DBO on 2009-02-02
> **Chang An said:**
> Docky is cool but there are at least three things that it really needs for me to switch to it.

1. Docky should be able to hide behind other windows when maximized.
2. Docky should have applets for cpu, ram, weather and what not.
3. Docky should be able to browse applications, files, ect, with a similar style as the classic interface.  I made a mock up demonstrating of what I mean below.

Nail down those three and I can finally leave Cairo-Dock.  That being said, great work on this one devs.

you are going to love the next release

---

### Post by outphase on 2009-02-02
I just made the switch from AWN to Gnome Do. So far,
everything has been moving along nicely except for the Google Contacts
(Gmail) plugin. When I try to send an email to someone, the To line in
Gmail says "///someone@mail.com" instead of simply "someone@mail.com"

I am currently using the perl script from the wiki: ```
perl -MURI::Escape
-e '$to= shift;if ($to =~ /^([^\?]+)\?(.*)$/){$to=$1;$args="&".
$2;$args=~s/\&subject=/&su=/};$to =~ s/^mailto://i;exec
("firefox","https://mail.google.com/mail/?
view=cm&fs=1&tf=1&cmid=22&to=".URI::Escape::uri_escape($to).$args);'
%s
```

Is there something that I need to change? Mailto links still work in
firefox, but Do keeps adding /// to my To line.

edit: Turns out the problem runs deeper than Gnome Do. [https://bugs.edge.launchpad.net/bzr/+bug/291847](https://bugs.edge.launchpad.net/bzr/+bug/291847)

---

### Post by Mazza558 on 2009-02-03
DBO, I have the latest BZR running, and noticed a new option "orientation" in gconf - is this what controls docky's position?

---

### Post by ajgosling on 2009-02-05
So for an unknown reason, gnome-do has suddenly stopped working after the first instance.  It launches on startup, and if I select it from the menus it starts, but the hotkey for it (super-space) no longer launches it in any situations.

I haven't changed any settings (That I am aware of), the only changes to my system in the last couple of days have been the standard ubuntu updates (I'm using Hardy on a dell xps laptop)

--- forget the above, I found my solution, it was the super key not being mapped on my keyboard, I've rectified it and all is now good

---

### Post by smbm on 2009-02-05
Anyone got the latest trunk versions to build in Intrepid?

I'm getting errors:

```
Compiling Do.Interface.Linux.Docky.dll...
./src/Docky.Interface/DockArea_Rendering.cs(45,26): error CS0103: The name `<ActiveIconChangeTime>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_Rendering.cs(45,26): error CS0103: The name `<ActiveIconChangeTime>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_Rendering.cs(47,22): error CS0103: The name `<PainterOverlayVisible>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_Rendering.cs(47,22): error CS0103: The name `<PainterOverlayVisible>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_DragAndDrop.cs(64,27): error CS0103: The name `<DragState>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_DragAndDrop.cs(64,27): error CS0103: The name `<DragState>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_DragAndDrop.cs(66,22): error CS0103: The name `<GtkDragging>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_DragAndDrop.cs(66,22): error CS0103: The name `<GtkDragging>k__BackingField' does not exist in the current context
Compilation failed: 8 error(s), 0 warnings
make[1]: *** [../build/Do.Interface.Linux.Docky.dll] Error 1
make[1]: Leaving directory `/home/tom/do/Do.Interface.Linux.Docky'
make: *** [all-recursive] Error 1

```

Anyone got any ideas how to get it to build?

Cheers

---

### Post by andrek on 2009-02-06
I've just built the 941 build successfully and.. wow, it's fabulous!

[[IMG]http://g.imagehost.org/t/0906/docky.jpg[/IMG]](http://g.imagehost.org/view/0906/docky)
*(turned icon zoom off)*

dots color is gtk theme-dependent.

---

### Post by smbm on 2009-02-06
> **andrek said:**
> I've just built the 941 build successfully and.. wow, it's fabulous!

[[IMG]http://g.imagehost.org/t/0906/docky.jpg[/IMG]](http://g.imagehost.org/view/0906/docky)
*(turned icon zoom off)*

dots color is gtk theme-dependent.

Hmm, I'm still getting the same errors!

Are you on Intrepid?

Can you detail exactly what you did to build please?

Thanks in advance.

---

### Post by UrK on 2009-02-06
From what I've seen, CS0103 is a mono bug:
[http://www.mail-archive.com/mono-bugs@lists.ximian.com/msg48697.html](http://www.mail-archive.com/mono-bugs@lists.ximian.com/msg48697.html)
I believe, mono 2.0 installation will resolve the issue, trying it now ([http://eric.extremeboredom.net/2008/10/15/296](http://eric.extremeboredom.net/2008/10/15/296))

---

### Post by northwestuntu on 2009-02-06
how do you get plugins? i don't have any under my options?

---

### Post by OdeAd on 2009-02-06
> **smbm said:**
> Anyone got the latest trunk versions to build in Intrepid?

I'm getting errors:

```
Compiling Do.Interface.Linux.Docky.dll...
./src/Docky.Interface/DockArea_Rendering.cs(45,26): error CS0103: The name `<ActiveIconChangeTime>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_Rendering.cs(45,26): error CS0103: The name `<ActiveIconChangeTime>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_Rendering.cs(47,22): error CS0103: The name `<PainterOverlayVisible>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_Rendering.cs(47,22): error CS0103: The name `<PainterOverlayVisible>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_DragAndDrop.cs(64,27): error CS0103: The name `<DragState>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_DragAndDrop.cs(64,27): error CS0103: The name `<DragState>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_DragAndDrop.cs(66,22): error CS0103: The name `<GtkDragging>k__BackingField' does not exist in the current context
./src/Docky.Interface/DockArea_DragAndDrop.cs(66,22): error CS0103: The name `<GtkDragging>k__BackingField' does not exist in the current context
Compilation failed: 8 error(s), 0 warnings
make[1]: *** [../build/Do.Interface.Linux.Docky.dll] Error 1
make[1]: Leaving directory `/home/tom/do/Do.Interface.Linux.Docky'
make: *** [all-recursive] Error 1

```

Anyone got any ideas how to get it to build?

Cheers

I got exactly the same errors on the latest revision,so I tried the revision tagged "0.8" 
```
 bzr branch lp:do gnome-do --revision 909.1.12
```
Worked like a charm ...

---

### Post by smbm on 2009-02-06
I'm still getting errors.

Can anyone that's got it to build slap some packages together with checkinstall so I can try it?

Thanks again in advance.

---

### Post by Vadi on 2009-02-06
They already have both 32bit and 64bit packages on their site

---

### Post by smbm on 2009-02-07
Of the development version?

---

### Post by andrek on 2009-02-07
> **smbm said:**
> Hmm, I'm still getting the same errors!

Are you on Intrepid?

Can you detail exactly what you did to build please?

Thanks in advance.

I'm on Archlinux.
I just run *yaourt -S gnome-do-bzr* and it goes without any error whatsoever.

---

### Post by Islington on 2009-02-07
> **smbm said:**
> I'm still getting errors.

Can anyone that's got it to build slap some packages together with checkinstall so I can try it?

Thanks again in advance.

Getting the same errors.

---

### Post by Islington on 2009-02-07
> **OdeAd said:**
> I got exactly the same errors on the latest revision,so I tried the revision tagged "0.8" 
```
 bzr branch lp:do gnome-do --revision 909.1.12
```
Worked like a charm ...

this seems to have worked.

---

### Post by DJ_Peng on 2009-02-13
I just saw something in Do 0.8.0 that I have to ask about. I went to fire up Google Earth 5.0.11337.1968 (labeled beta but I installed it from a download from Google's server once I saw it was officially out and a check for updates shows it to be current) with Do and I saw an image I've never seen before. Does anyone know where the image is grabbed from? I don't see it in ~/google-earth (where the installer put it) nor in the icons from Mac4Lin. I love the image, I'm just trying to figure out where it came from.

---

### Post by Islington on 2009-02-13
> **DJ_Peng said:**
> I just saw something in Do 0.8.0 that I have to ask about. I went to fire up Google Earth 5.0.11337.1968 (labeled beta but I installed it from a download from Google's server once I saw it was officially out and a check for updates shows it to be current) with Do and I saw an image I've never seen before. Does anyone know where the image is grabbed from? I don't see it in ~/google-earth (where the installer put it) nor in the icons from Mac4Lin. I love the image, I'm just trying to figure out where it came from.

check your icon theme?

---

### Post by DJ_Peng on 2009-02-13
It's definitely not the icon theme. The attached icon is what Mac4Lin 1.0RC2 provides.

---

### Post by DJ_Peng on 2009-02-14
*D'oh!* I was going through the Mac4Lin RC2 icons in the process of getting ready to redo some screenshots and I found the attached in ~/.icons/Mac4Lin_Icons_v1.0_RC2/scalable/apps. I can't believe I missed that earlier this week when I was trying to chase it down. Sorry 'bout that, y'all.

---

### Post by rye_ on 2009-02-17
I've only just discovered this wonderful app, thankyou developers.

(I can only hope that ubuntu will contain this as default as soon as it is considered stable)

---

### Post by northwestuntu on 2009-02-28
i got 64bit 0.8 installed fine, but can't seem to get the plugins working? is there a version of the plugins for 64 or can you use any version?

---

### Post by northwestuntu on 2009-02-28
i installed the deb from there site and i see the plugins in the list, but none of them start?

---

### Post by jowilkin on 2009-03-03
> **northwestuntu said:**
> i got 64bit 0.8 installed fine, but can't seem to get the plugins working? is there a version of the plugins for 64 or can you use any version?

To get running on 64-bit I added the gnome-do ppa to my sources.list.  Right now the ppa has the plugins, but not gnome-do as it isn't building correctly on the ppa.  So to get installed just install gnome do from a .deb > 64-bit users! There is a bug in Launchpad's ppa that causes 64-bit mono package builds to fail, but David was in the marines for 12 years and only learned one thing- Leave no man behind. We've got a package for you at [http://launchpad.net/do/+download](http://launchpad.net/do/+download)

And then once you add the gnome-do repository do ```
sudo aptitude install gnome-do-plugins
``` and you should have the 0.8x version of gnome-do and the plugins.

---

### Post by Athropos on 2009-05-09
Hi,

Gnome Do with Docky is great!

It works very well, and allow me to get almost completely rid of Gnome panel. However, I see no way to manage a system tray, which is a pity since without it I can't access to some important icons (e.g., battery, network). Is there something I can do to solve this problem?

---

### Post by pieguy on 2009-05-11
I am trying to open Nautilus with gnome-do but it doesnt do it, nothing happens when I run nautilus.  I was wondering if its possible and if so, how?   I was able to shutdown/etc my computer with gnome-do by activating the session manager plugin, so I'm hoping theres a way(possibly through plugins) to open the nautilus manager through gnome-do.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=113347&stc=1&d=1242050502[/IMG]

---

### Post by ghindo on 2009-05-11
Try installing the Files and Folders plugin, and then just typing the name of the directory you want to access.

---

### Post by Luffield on 2009-05-11
Yes, there is: type "home" instead on "nautilus" to get to your home folder.

On my machine this doesn't actually work, IIRC it's a known bug. Instead, I use the Files and Folders plugin and type my username to open my home folder or a different folder name to open it.

---

### Post by pieguy on 2009-05-11
Home fails for me too, but with the files and folders enabled I can type my user name, or /boot, etc and it opens nautilus into that locations.  Thanks.  Gnome-do is the quickest!!

---

### Post by Mazza558 on 2009-06-03
I'm having trouble getting the Firefox plugin to work with the very latest Gnome-do on Ubuntu Karmic. I'm currently using Firefox 3.5 beta, though I still have 3.0 installed. 

Does the plugin only work with Firefox 3.0 as the default browser?

---

### Post by Viva on 2009-06-03
Weird, when I run Gnome-Do from terminal, I can open the home folder, but not when I open it through terminal

---

### Post by treesurf on 2009-06-10
Is there any way to get Gnome-Do to index more then the default 3000 files?

---

### Post by DBO on 2009-06-17
> **treesurf said:**
> Is there any way to get Gnome-Do to index more then the default 3000 files?

Nope, it gets REALLY cluttered if we allow more than that and can have negative impacts on the performance of the application

---

### Post by treesurf on 2009-06-17
Thanks for the reply, that's cool.  I messed with the depth of indexing in files/folders plugin and got it setup to work just right for me now, so no problems.  Initially I was having it index a whole mess of files that I was hardly ever going to look at anyways...

Any idea when the next update to Gnome Do will be released?  The new upcoming features look great espcially the new docklets for Docky.  The only other thing I could ask for is a Network Manager docklet...

---

### Post by Tibuda on 2009-07-02
> **treesurf said:**
> Any idea when the next update to Gnome Do will be released?  The new upcoming features look great espcially the new docklets for Docky.  The only other thing I could ask for is a Network Manager docklet...

[http://pengdeng.com/blog/2009/06/30/do-0-8-2-released/](http://pengdeng.com/blog/2009/06/30/do-0-8-2-released/)

I installed it today from the PPA. It's great! I can't find the Gmail docklet I see in the screenshots. Anyone knows if it is available only from trunk?

---

### Post by treesurf on 2009-07-02
Sweet!  Updating now!

The article you linked states the Gmail docklet and possibly the Network Manager docklet will be in a small update in a couple weeks.

---

### Post by treesurf on 2009-07-02
The new Docky features are most excellent!  Many thanks to those responsible.


Some bugs I have noticed:  the Battery docklet states "No Battery Found" and the Volume Control Docklet just shows an X

---

### Post by talent03 on 2009-07-02
Thanks Do team! This is actually the exact way I wanted docky to work. Everything is perfect for me. Although I did notice what treesurf said:

> **treesurf said:**
> 
Some bugs I have noticed:  the Battery docklet states "No Battery Found" and the Volume Control Docklet just shows an X

I do not have a use for those, so all is great here.

---

### Post by pelle.k on 2009-07-02
Hey people. Apparently, they dropped the "allow window overlap" feature of docky from 0.8.1. The HORR0R!
Fortunately i've followed the bzr revisions until now, and was prepaired for this! So this is a patched gnome-do (built from the 0.8.2 PPA), where you may activate AllowWindowOverlap in gconf, if docky is set in "Hiding: none" mode.

[http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2+dfsg-0~9.04~test1_i386.deb](http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2+dfsg-0~9.04~test1_i386.deb)

Still, you **do** need to add the official PPA to pull in the dependencies (gnome-do-plugins and optionally gnome-do-docklets), though.
The debian source (etc) is included in that same directory.
Hope someone finds it useful! (it's only for **i386**, sorry about that!)

---

### Post by Trevor Bramble on 2009-07-02
> **treesurf said:**
> Some bugs I have noticed:  the Battery docklet states "No Battery Found" and the Volume Control Docklet just shows an X

Ditto here.  I'm seeing exactly those two problems.

---

### Post by Tibuda on 2009-07-02
> **pelle.k said:**
> Hey people. Apparently, they dropped the "allow window overlap" feature of docky from 0.8.1. The HORR0R!
Fortunately i've followed the bzr revisions until now, and was prepaired for this! So this is a patched gnome-do (built from the 0.8.2 PPA), where you may activate AllowWindowOverlap in gconf, if docky is set in "Hiding: none" mode.

[http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2+dfsg-0~9.04~test1_i386.deb](http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2+dfsg-0~9.04~test1_i386.deb)

Still, you **do** need to add the official PPA to pull in the dependencies (gnome-do-plugins and optionally gnome-do-docklets), though.
The debian source (etc) is included in that same directory.
Hope someone finds it useful! (it's only for **i386**, sorry about that!)

Maybe they dropped it  because of the new inteli-hide feature, that is just great. Give it a try.

---

### Post by Mazza558 on 2009-07-02
Hmm, I get no plugins at all with 0.82.

EDIT: I have plugins but no Docklets now :(

---

### Post by SpriteSODA on 2009-07-02
> **pelle.k said:**
> Hey people. Apparently, they dropped the "allow window overlap" feature of docky from 0.8.1. The HORR0R!
Fortunately i've followed the bzr revisions until now, and was prepaired for this! So this is a patched gnome-do (built from the 0.8.2 PPA), where you may activate AllowWindowOverlap in gconf, if docky is set in "Hiding: none" mode.

[http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2+dfsg-0~9.04~test1_i386.deb](http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2+dfsg-0~9.04~test1_i386.deb)

Still, you **do** need to add the official PPA to pull in the dependencies (gnome-do-plugins and optionally gnome-do-docklets), though.
The debian source (etc) is included in that same directory.
Hope someone finds it useful! (it's only for **i386**, sorry about that!)

life saver :D

---

### Post by webgod on 2009-07-02
Hi all.

I started using GnomeDO 2 weeks ago and I'm loving it so far. There's only one feature that should be a base functionality but I never got it  working: sending emails.
For example, you select a file, hit TAB, and there are options like "Copy", "Reveal", "Run", etc. but I can't send that file by email and I know that most people can do this. I just don't know why I can't. :(

Hints? :confused:

PS: I had GnomeDO 0.8.1 and today I updated to 0.8.2, hoping that I would be able to send files by email. I guess that are some missing libraries maybe...

---

### Post by webgod on 2009-07-02
> **Mazza558 said:**
> Hmm, I get no plugins at all with 0.82.

EDIT: I have plugins but no Docklets now :(

Hi Mazza558,

Have you already downloaded the docklets from their [PPA]("https://launchpad.net/~do-core/+archive/ppa")? You just have to download the version that suits you. (search for the package with 'gnome-do-docklets - 0.8.2-0' on its name)

---

### Post by DJ_Peng on 2009-07-03
One thing I just noticed, I grabbed the update to 0.8.2+dfsg-0~9.04~ppa3 from the PPA, and I had Do running (complete with at least a single reboot between the update and the event I'm about to describe), when all of a sudden Do crashed on me without warning as I tried to summon it. When I got it relaunched it seems all of my settings were thrown out the window. Not only had every one of my plugins been disabled, my interface was change dto Docky, despite having determined a while back that I don't like Docky as it seems to duplicate too much of the functionality I have in AWN (which is always running anyway).

Should it have trashed my settings, and if so we may want to find a way to educate our users that it's about to happen. Needless to say, I wasn't all that thrilled, wspecially with the fact that my day had already been thrown into the loo.

---

### Post by bluebyt on 2009-07-05
Anybody know if gnome-do 0.8.2 (PPA) will be update for Intrepid?

Now the PPA 0.8.2 is only for Karmic and Jaunty.

---

### Post by Viva on 2009-07-06
Is there a non-mono port of gnome-do?

---

### Post by heroidi on 2009-07-06
i just l0ve it

---

### Post by pt123 on 2009-07-06
anyone else use Gnome-Do to run bash scripts they have created?

since 0.81 the default action for a .sh file is open, no matter how many times I run the script through gnome-do, open is always the first action. I have even tried deleting the config folders and reinstalling gnome-do and still the same annoying behaviour anyonse experience this?

---

### Post by Tibuda on 2009-07-06
> **Viva said:**
> Is there a non-mono port of gnome-do?

Alternatives yes, but port no. If someone port it, I doubt it would have all the plugins available on Do. Every release there are new plugins.

---

### Post by Viva on 2009-07-06
> **danielrmt said:**
> **Alternatives yes**, but port no. If someone port it, I doubt it would have all the plugins available on Do. Every release there are new plugins.

Care to share?:popcorn:

---

### Post by Tibuda on 2009-07-06
> **Viva said:**
> Care to share?:popcorn:

gnome-launch-box, deskbar, krunner... I never used krunner, but Do surely beats both launch box and deskbar.

---

### Post by pataphysician on 2009-07-08
> **danielrmt said:**
> gnome-launch-box, deskbar, krunner... I never used krunner, but Do surely beats both launch box and deskbar.

i kind of prefer the more subtle look of deskbar, and the way it presents results in a little organized menu. it also automatically searches google and includes the results in the list, which is kind of nice. plus it doesn't need mono or evolution.

i still use gnome do, anyway. i feel like i can access things just a tiny bit faster with it, and it's slightly more robust. deskbar can't read ff3 bookmarks, or traverse or manipulate the file system. gnome do also does a better and more consistent job of intuiting what i'm trying to do. with deskbar, i'd type "so" and sonata would come up as the default action, but then if i keep going and enter, "son," sonata would disappear from the list and i'd end up doing a google search for "son." what?

for the person/people looking for alternatives, there is also kupfer

[http://kaizer.se/wiki/kupfer/](http://kaizer.se/wiki/kupfer/)

which is a rather new gnome do clone written in python. i haven't used it but it seems promising enough. "Kupfer can right now summon Applications, Recent Files and Places, your chosen folders and their contents, Bookmarks, Windows and Gnu Screen sessions." not sure how many plugins it ships with.

---

### Post by Tibuda on 2009-07-08
Gnome Do can also search google and display the results.

---

### Post by pataphysician on 2009-07-08
> **danielrmt said:**
> Gnome Do can also search google and display the results.

oh i know. i just meant that i liked the way deskbar does it automatically. with gnome-do i invoke it, type "sea," <tab>, type a search term and hit enter, then it reloads. or i can keep typing until it stops suggesting other things for me to do, and hit enter, and it reloads. or i can cursor down to the last option and hit enter...

it's not that big of a deal, i know, and the reload is almost instantaneous; but with deskbar, as i'm typing it searches and it just pops up the results right there:

[http://i25.tinypic.com/25i55if.png](http://i25.tinypic.com/25i55if.png)

i guess it's just a matter of the way results are presented. and, as i was saying, even though i somewhat prefer deskbar's look and presentation, i'm still using gnome-do (i don't even keep deskbar on the panel) because its presentation isn't awful, and it functions better.

---

### Post by DBO on 2009-07-08
kupfer uses the GNOME Do search algorithm anyhow, so it is more of the same =P

---

### Post by mikebeecham on 2009-07-11
to be honest, I think it's a case of apples and oranges...what works best for you.

I've come from a mac environment, where we've got the leopard search function AND quicksilver...the latter being fantastic.  I've used deskbar on the odd occasion, but dont think it's anything fantastic...it works, but kinda does what it says on the tin.  

I then come across Gnome-Do in the past two weeks, and have become accustomed to it.  it's very much like Quicksilver in it's approach, but it just works..and does it very well.

At the end of the day, different people like different applications for different reasons.

THATS the joy of open source!

---

### Post by DJ_Peng on 2009-07-12
So *that's* what Quicksilver is. I'd seen it mentioned a few times but never checked to see what they were talking about. I'll have to talk to infra_red_dude to see if we want to add a mention of Do in the Mac4Lin docs. (Like I'm not already late in getting the docs published for Mac4Lin 1.0, but that's another matter.)

---

### Post by M1979 on 2009-07-14
Hi, I can't assign <Super>Tab to launch gnome-do - did anyone experience the same?

---

### Post by Tibuda on 2009-07-14
> **M1979 said:**
> Hi, I can't assign <Super>Tab to launch gnome-do - did anyone experience the same?

Yes, this happened to me when I had <Super> assigned to something else in gnome hotkeys manager.

---

### Post by M1979 on 2009-07-14
Mh, I was pretty sure it wasn't mapped to something else. Maybe it still was. Anyway, it works now, thanks! I have installed the latest version (0.8.2) via PPA though, maybe this is related somehow.

---

### Post by pelle.k on 2009-08-23
I did post a link to a patched gnome-do (0.8.2) previously in this thread, which allows window overlap (like docky used to, through a key in gconf), but it was 32 bit only. Since a 64bit package was requested, i thought i'd share that as well.
32bit package: [http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2%2bdfsg-0~9.04~test1_i386.deb](http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2%2bdfsg-0~9.04~test1_i386.deb)
64bit package: [http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2%2bdfsg-0~9.04~test1_amd64.deb](http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2%2bdfsg-0~9.04~test1_amd64.deb)

You will still need the "official" ppa for 0.8.2 to pull in dependencies, though. For now, this is jaunty only.

---

### Post by Stan_1936 on 2009-08-23
> **mikebeecham said:**
> ...I then come across Gnome-Do in the past two weeks, and have become accustomed to it.  it's very much like Quicksilver in it's approach, but it just works..and does it very well....**At the end of the day, different people like different application**s...

**That's true.  I've always found Gnome-Do to be far too heavy for my liking....**

**<----------RAWR.....RAWR.....**

---

### Post by stani on 2009-08-23
> **pelle.k said:**
> I did post a link to a patched gnome-do (0.8.2) previously in this thread, which allows window overlap (like docky used to, through a key in gconf), but it was 32 bit only. Since a 64bit package was requested, i thought i'd share that as well.
32bit package: [http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2%2bdfsg-0~9.04~test1_i386.deb](http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2%2bdfsg-0~9.04~test1_i386.deb)
64bit package: [http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2%2bdfsg-0~9.04~test1_amd64.deb](http://download.tuxfamily.org/pandora/temp/jaunty/gnome-do/gnome-do_0.8.2%2bdfsg-0~9.04~test1_amd64.deb)

You will still need the "official" ppa for 0.8.2 to pull in dependencies, though. For now, this is jaunty only.
Thanks a lot! It works just like I want. Is there any chance this option will get back upstream?

---

### Post by TheNessus on 2009-08-23
just tried it. works great :)

---

### Post by vickoxy on 2009-08-25
Hi, i am searching ideal desktop search tool and launcher for it:).

I have 0.8.1.3. gnome and now i am testing tracker with gnome-do. Does anyone here knows if there is maybe beagle plugin for gnome-do (or maybe planned)?
Or tracker live search?

Thanks

---

### Post by vickoxy on 2009-08-26
No one knows?

For now my gnome-do and tracker are making good job. Still, tracker is indexing data after each restart/standby (and have litlle bit less results as beagle), and the beagle-plugin would be awesome option...

---

