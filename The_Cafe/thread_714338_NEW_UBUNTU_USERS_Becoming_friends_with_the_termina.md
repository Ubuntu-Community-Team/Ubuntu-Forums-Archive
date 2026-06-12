---
title: "NEW UBUNTU USERS: Becoming friends with the terminal..."
date: 2008-03-03
forum: The Cafe
---

### Post by Mazza558 on 2008-03-03
For all the new people, just starting out on Ubuntu, if you're wondering why the people here tend to solve your problems using code rather than giving you directions, this short guide is for you.

**PART 1: What's the Terminal?**

A pretty good way of describing the terminal is a window into the core of your PC. What I mean by that is, with the right knowledge, you can modify ANY aspect of Ubuntu. If you're not sure what it looks like, open a **terminal window** now! 

**Head to Applications, then Accessories, then "Terminal". **

Looks scary? Yes, it can be. To anyone but the experienced computer users among us, the terminal can seem way out of your depth. Luckily, when using Ubuntu, you barely need to touch it unless you are having problems and need to ask for help here. In the terminal, you will see your username as text, looking slightly like the format used in an email, for example:

```
name@name-desktop$

or 

name@name-desktop$
```

Now, you're probably thinking this is a bit archaic. In this day and age, with windows, buttons and graphics, who on earth would want to use this?

The truth is, the terminal is, with the right frame of mind,** SIMPLER** to use than navigating endless menus and selections. It is simpler because it is simply a **faster** way of doing things. It does things **automatically** for you. It is a friend, not an enemy. It wants to help you, as long as you give it respect.

**PART 2: Why does it help me?**

The terminal helps you because it allows people helping you to give you a **standardised code** to solve your problems. This means that whatever version of Ubuntu you use, this code will, in the vast majority of cases, work fine. So, rather than helpful forum members having to tell you to click "here, here, down here, right there, here, there, where, there", the code will do the **whole thing **for you. 

In fact, as a normal user who just wants to use his/her computer, you don't need to understand** one bit **of code. The vast majority of time, it's a simple copy and paste of what may seem like garbled nonsense, but it'll do the trick. Of course, it can help if you understand some of the lingo used, but by and large, you don't necessarily have to do all that much. 

**PART 3: How do I add code to the terminal from guides on Ubuntu Forums?**

It's pretty simple. Select the whole of a line of code on the page,** select** the code (e.g click and drag the mouse), **copy it** (ctrl + C is fastest, but you can also right-click and copy from there). How do you know what a line of code is like? Most guides put them in **quotes or code boxes**, like this:

```
Hello!
```

Please note that if you see multiple lines of code at once in a guide, copy and paste them **one at a time.**

Once you've copied the line of code, go to your terminal window, and, if you have a middle mouse button, you can press it with the cursor hovering over the terminal window, and it'll appear in the terminal. If you don't, press CTRL + SHIFT + V to paste it. To run that code, simply press** enter**. 

Okay, let's give this a test drive!

Here's the code you need for Ubuntu to check for updates to programs.

```
sudo apt-get update
```

Copy this line of code, and paste it into the terminal. Then press enter. You should see something scary. You'll get a response like:

```
[sudo] password for (your name):
```

In the terminal. The terminal is simply asking for your permission to do this. It's asking if you are really you, and not some random person. Enter your password - note that it gives no recognition that you're entering anything in, so if you think you've gone wrong, hold backspace down for a few seconds and re-enter.

Press enter once you've entered your password.

Boom... lots of code zooming past you now. What Ubuntu is doing here is going to all the addresses of all the software you use (provided you're connected to the internet) and asking if there's a new version available. If it asks whether you want to update (it'll have a Y/N option, Y being "Yes" and N being "No"), make your choice by** typing Y or N**. This command actually does **exactly the same thing** as the Update Manager found in System > Administration, except this method shows more detail. Remember, it's entirely **your choice** whether you use this method or open the program - you may, in time, find this method more efficient.

So now you know how to copy, paste and run code from guides...

**PART 4: "Sudo"? Is that a new brand of soap?**

The answer is no. You may see this often in lines of code. It is a literal abbreviation of **"SUper-user DO"**. Still confused?

SUDO is the way of telling lines of code that this line of code is important, because it wants to do something which modifies the system (e.g install something, remove it). By entering the password for SUDO, you are effectively giving the terminal access to your whole PC for a temporary time. Remember that it is only you who can do this, as long as only you know your password. Why do we need SUDO? Because, unlike Windows XP, which gives you access to your PC **all the time**, Ubuntu only gives access to those who** it can trust - you.** You may, from time to time, especially when opening programs in the system menu, see a popup box asking for your password. This is also SUDO but in a popup rather than in the terminal. 

**PART 5: Rogue commands**

Now you have some basic knowledge of the terminal, it is very important that you understand a particularly dangerous line of code. It is very powerful (and can be useful in a minority of cases), but as they say, with great power comes great responsibility. 

The name of this infamous and legendary command is:

> **SUDO RM -RF /**

Do not run this command, **ever.**

**I repeat - never, ever run this command, unless you absolutely know what you are doing! **

I know this seems like scaremongering, there have been a few cases in the past of malicious users posting this code for people to copy and paste, especially in "guides" which aren't really that. I'd like to take this opportunity to explain exactly **what** it is about this command that makes it particularly nasty. Luckily for you, if you enter this code accidentally, it will give you one last safeguard - SUDO. Remember, in this case, SUDO is a guardian. It'll ask for your permission. Make sure that if you see this code, do **NOT** give your password. SUDO is one of the greatest security features ever added to an OS, but it **cannot** protect you from your own mistakes.

One such mistake is if you have run a command using SUDO within 15 minutes previously. Ubuntu will allow commands to be run without you having to enter your password for up to **15 minutes** after entering the first SUDO command. This means that if you accidentally enter this code, **SUDO won't always be there to save you!**

Okay, here's a breakdown of what this command will do to your PC. You can find this information out for yourself if you want by typing:

```
man rm
```

However, for everyone else, this is what the command will do.

**SUDO:** Gives the code the permission to do anything to your PC, but remember, only with **your** permission first.

**RM:** **R**e**M**ove a file or multiple files (Can you guess where this is going?)

**-R** **R**ecursive - this option will remove any subfolders as well. For example, if you did **RM -R /home/bob**, then any folders contained within "bob" would be deleted too.

**F** (part of -RF) - **F**orce. This means that despite any protests by the system, this command has **absolute power**. It **WILL** be run, no matter what. It will not ask for any confirmation at all either.

**/** By far the most dangerous bit of the command. Whereas 

> sudo rm -rf /home/bob/downloads

...could be useful if bob wanted to get rid of his downloads folder for whatever reason, the "/" means **EVERYTHING.** every system file and folder you have. So, in summary, this command will trash Ubuntu, rendering it unusable when you restart. Note that, unbeliveably, you will still be able to use your PC until you restart - this is because everything is already loaded into memory. It is possible to recover files from your home folder by using a LiveCD, but everything else will have to be reinstalled. **Not good.**

The best way to describe this nasty command is **the 10-character code of death**.

_____________________


Thanks for reading this guide - it was intended for the newest of new users, as I don't think there's much help given for people who are just starting out. :)

---

### Post by Vitamin-Carrot on 2008-03-03
Also become friendly with the user and groups management system
there are apps out there that require the user to be part of a specific group i.e virtualbox.

this has a nice gui and isnt too complicated

if all else fails especially with folder access

sudo chown

should see you right

PS: I love you mazza

---

### Post by ferdostar on 2008-03-03
Nice guide! Considering that the gui is made for new people who are coming maybe you can also add the "Tab" buton as giving all the commands and "-help" after a command for more information about how to use it. 
Regards!

---

### Post by Joeb454 on 2008-03-03
Good guide...might need a little work/addition, but so far so good :)

---

### Post by Mazza558 on 2008-03-04
Thanks for all the comments guys, I hope this helped someone :)

---

### Post by ellalan on 2008-03-04
Thank you mazza558, 
It is very nice of you to write this useful information.

---

### Post by Cadmus on 2008-03-04
Nicely written, also remember that typing

```
man foobar
```

Will show you the manual for the command 'foobar' (if it existed), replacing 'foobar' with any other command will show you the manual page. This is handy if you're trying to remember a particular option for a command, though some man pages are a bit dense, try reading the ones for rsync too early on and you'll never use the terminal again ;)

---

### Post by LeAstrale on 2008-03-04
I think this guide has a great potential :) as a common Terminal help guide. 

However only if you keep it updated and listen to fellow users ideas.

/Astral-1

---

### Post by hyper_ch on 2008-03-04
maybe add also a warning with regard to certain commands, especially:

```

sudo rm -Rf /

```

And maybe also say how to find out more what a command does (reference to the man pages).

---

### Post by Andavane on 2008-03-04
> **Cadmus said:**
> Nicely written, also rememeber that typing

```
man foobar
```

Will show you the manual for the command 'foobar', this is handy if you're trying to remember a particular option for a command, though some man pages are a bit dense, try reading the ones for rsync too early on and you'll never use the terminal again ;)

Oooeerrr... When I type this I get:

> No manual entry for foobar

Regards
John

---

### Post by ByteJuggler on 2008-03-04
Yes, there is no command "foobar" of course, it was used as a placeholder for you to put an actual command in. :)  

Btw, the terms "foo" and "bar" have a long tradition of serving as random names for things in Unix and computer science documentation and articles.

---

### Post by Cadmus on 2008-03-04
I realise I wasn't very clear, so I've edited it a little.

Also, is using [metasyntactic variables]("http://catb.org/jargon/html/M/metasyntactic-variable.html") (foo, bar, baz, foobar) worthwhile? Discuss

---

### Post by Mazza558 on 2008-03-04
I intended this guide to be for people who really don't care for using the terminal - as such, it's really about explaining some basic things which may help users if they need to enter code.

---

### Post by Andavane on 2008-03-04
> **ByteJuggler said:**
> Yes, there is no command "foobar" of course, it was used as a placeholder for you to put an actual command in. :)  

Btw, the terms "foo" and "bar" have a long tradition of serving as random names for things in Unix and computer science documentation and articles.
Oh I see!
Thanks for the explanation.... I often wondered what the mysterious "foo" was...;)
PS: In your example, could you included a few examples which the user can read, type and see

---

### Post by Mazza558 on 2008-03-04
Just added part 5, warning people about "sudo rm -rf /". :)

If there's anything inaccurate, please let me know.

---

### Post by CaptainCabinet on 2008-03-04
Very useful post this. :D
Great for terminal noobs like myself.

---

### Post by justin whitaker on 2008-03-04
Nice work.

---

### Post by bobbocanfly on 2008-03-04
Brilliant guide. Would have helped me when i first started out with Linux.

---

### Post by days_of_ruin on 2008-03-04
> **CaptainCabinet said:**
> Very useful post this. :D
Great for terminal noobs like myself.
*Looks at avatar*you can say that again :P

---

### Post by CaptainCabinet on 2008-03-04
> **days_of_ruin said:**
> *Looks at avatar*you can say that again :P

My avatar is the perfect example of how bored I can get. :)

---

### Post by roshm on 2008-03-04
One handy little item I have just found is, in the Terminal with the cursor active I can browse previous commands. I can look for command I have forgotten and check for keyed errors. Just by using the up or the down arrow .

---

### Post by ByteJuggler on 2008-03-04
> **roshm said:**
> One handy little item I have just found is, in the Terminal with the cursor active I can browse previous commands. I can look for command I have forgotten and check for keyed errors. Just by using the up or the down arrow .

Another tip: Try pressing ctrl-r, then try typing part of a previous command.  The first closest matching command containing what you've type will be displayed.  Press esc to cancel the search and resume normal editing of the command, or enter to accept and execute it directly without further editing.  That's an even quicker way to get back to a previous command.

---

### Post by hyper_ch on 2008-03-05
> **Mazza558 said:**
> The best way to describe this nasty command is **the 10-character code of death**.


:lolflag: but still true ;)

---

### Post by Mazza558 on 2008-03-05
12 thanks from 1 guide... I'm flattered :)

---

### Post by acidsolution on 2008-03-05
pretty useful guide for newbie 
good effort :)

---

### Post by aaaantoine on 2008-03-05
> Luckily for you, if you enter this code accidentally, it will give you one last safeguard - SUDO. Remember, in this case, SUDO is a guardian. It'll ask for your permission. Make sure that if you see this code, do NOT give your password. SUDO is one of the greatest security features ever added to an OS, but it cannot protect you from your own mistakes.

One note of concern: If a reader has already tested their sudo powers on "sudo apt-get update", they will probably get to the rogue command and may even type it within the 15-minute sudo grace period.

---

### Post by Mazza558 on 2008-03-05
> **aaaantoine said:**
> One note of concern: If a reader has already tested their sudo powers on "sudo apt-get update", they will probably get to the rogue command and may even type it within the 15-minute sudo grace period.

Good point. I've added it to the original post.

---

### Post by Mazza558 on 2008-03-15
Just a minor update, I've elaborated a bit on what 

```
sudo apt-get update
```

does, and clarified a few other things in the guide.

---

### Post by clanky on 2008-03-15
Very useful, I have just started using ubuntu and have managed to use the terminal by blindly cutting and pasting from guides, but that was really useful in terms of actually starting to have some tiny understanding of what things do.

---

### Post by Daveski on 2008-03-15
Nice work. I know that someone already mentioned using man, but can I suggest you add this to the original post. After you have said:

> 
Okay, here's a breakdown of what this command will do to your PC:

**SUDO**: Gives the code the permission to do anything to your PC, but remember, only with your permission first.

**RM**: ReMove a file or multiple files (Can you guess where this is going?)

**-R** Recursive - this option will remove any subfolders as well. For example, if you did RM -R /home/bob, then any folders contained within "bob" would be deleted too.

**F** (part of -RF) - Force. This means that despite any protests by the system, this command has absolute power. It WILL be run, no matter what. It will not ask for any confirmation at all either.

/ By far the most dangerous bit of the command.


... I think you should add that running

```
man rm
```

will give you all this info and more.
Perhaps you could reiterate that users should check the man page for each command they are copying from a post:
 - don't try to understand it all, but run an eye over the page to see if you can get the gist of what the command in the post is supposed to do. Be on the lookout for commands that are malicious - this is unusual to find in the forums as most people are there to help, but it pays to be cautious.

It might be worth mentioning that the man page can be scrolled with the cursor keys or the mouse wheel. Pressing q will Quit from the manual page.

---

### Post by cristovaum on 2008-03-16
I don't understand binary but i'm fascinated with what it does :confused::)

I just started using ubuntu, starring reason: BLENDER3D.org :KS and i say, THANK YOU Mazza558:)

---

### Post by kk0sse54 on 2008-03-16
Thanks for the post mate it really helped me out. Do you think that you  could add some more basic commands?

---

### Post by bruce89 on 2008-03-16
> **cristovaum said:**
> I don't understand binary but i'm fascinated with what it does :confused::)

Binary? I don't see what knowing what 0s and 1s mean being useful.

---

### Post by Andavane on 2008-03-17
> **Daveski said:**
> Nice work. I know that someone already mentioned using man, but can I suggest you add this to the original post. After you have said:



... I think you should add that running

```
man rm
```

will give you all this info and more.
Perhaps you could reiterate that users should check the man page for each command they are copying from a post:
 - don't try to understand it all, but run an eye over the page to see if you can get the gist of what the command in the post is supposed to do. Be on the lookout for commands that are malicious - this is unusual to find in the forums as most people are there to help, but it pays to be cautious.

It might be worth mentioning that the man page can be scrolled with the cursor keys or the mouse wheel. Pressing q will Quit from the manual page.

What a very sound point you are making, Daveski.
Thanks

---

### Post by RedNikon on 2008-03-17
> **bruce89 said:**
> Binary? I don't see what knowing what 0s and 1s mean being useful.

As they say there are 10 type of people in the world those who understand binary and those who don't.

---

### Post by hyper_ch on 2008-03-17
> **RedNikon said:**
> As they say there are 10 type of people in the world those who understand binary and those who don't.

Sounds like my sig ^^

---

### Post by LaRoza on 2008-03-17
> **RedNikon said:**
> As they say there are 10 type of people in the world those who understand binary and those who don't.

There are 10 types of people in the world: those who understand trinary, those who don't, and those that confuse it with binary.

---

### Post by Daveski on 2008-03-17
> **C!oud said:**
> Thanks for the post mate it really helped me out. Do you think that you  could add some more basic commands?

What sort of basic commands? Here is a quick list of the real basics - check the man pages for each if you want more information:

**cd**    -    Change Directory
**pwd** -    Print Working Directory (current directory)
**ls**     -    LiSt files / directories
**cp**   -    CoPy
**mv**  -    MoVe / rename

**mkdir** - MaKe DIRectory
**rmdir** - ReMove DIRectory

**cat**  -  conCATinate (view contents of file)

---

### Post by Lantesh on 2008-03-17
Nice guide.  I've been using Ubuntu for about a year, and am no stranger to the terminal, but I did learn something by reading this.  Thanks for taking the time and effort to help others out.  How do I give thanks in this forum?  Most forums I visit have a thanks button to click, but I don't see one here.

---

### Post by Terry S on 2008-03-17
Thanks Massa a good intro to Terminal. 
Question: Why only copy & paste one line at a time?:

---

### Post by ice60 on 2008-03-17
great post!

i think i use the **info** command more than **man**. there's also **man -k**, or **apropos** (they give the same results) for "searching the manual page names and descriptions" e.g. -
**info info**
**apropos bash**

there's the **help** command that prints out the names of all the builtin commands, then typing **help *the name of a builtin command*** e.g. -
**help alias**

to paste in to the terminal, one way of doing it is with the **shift-insert** keys; and the keys for copying are **ctrl-insert**

pressing **cd** takes you back to your home directory

to search through your bash history press **ctrl-r** then start typing until you get to the command you want

to get back to the last directory you were in type **cd -** e.g. try this -
**cd /usr/share/icons/ *<enter>***
**cd *<enter>***
**cd -*<enter>***

**lsof** is a great command, here's a link explaining it -
[http://dmiessler.com/study/lsof/](http://dmiessler.com/study/lsof/)

also, here's another ubuntuforums post caled "Terminal for Beginners"
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

---

### Post by Twitch6000 on 2008-03-17
thank you to the topic starter,for telling me what that 10 character code of death does :).I was about to put ubuntu on a spare computer and try it out lol until I seen that.

---

### Post by bruce89 on 2008-03-17
> **Twitch6000 said:**
> thank you to the topic starter,for telling me what that 10 character code of death does :).I was about to put ubuntu on a spare computer and try it out lol until I seen that.

I wonder if this "campaign" on the forums has made people more likely to use it now.

I quite like backticks, and also the !thing. e.g.

```
sudo aptitude remove `deborphan`
```

Puts the output of *deborphan* in its place.

```
!ssh
```

Finds the last use of the command "ssh", for me it's *ssh -CX bruce@Scooby-Doo*.

---

### Post by Mazza558 on 2008-03-17
> **Terry S said:**
> Thanks Massa a good intro to Terminal. 
Question: Why only copy & paste one line at a time?:

It's due to the way text formatting works - if you copy the whole thing at once, the terminal will (if I recall correctly) only run the first line.

---

### Post by bruce89 on 2008-03-17
> **Mazza558 said:**
> It's due to the way text formatting works - if you copy the whole thing at once, the terminal will (if I recall correctly) only run the first line.

Not if you stick a \ at the end of each line.

---

### Post by which_chick on 2008-03-20
If you're referring people to man pages (like using "man sed" to read the sed man page), you might mention that a person can get back *out* of the man page by typing 'q' for 'quit'.  This is non-obvious to new users -- ask me how I know.  :)

Also, I apparently can't read.  It's already been covered.

---

### Post by cardinals_fan on 2008-03-20
Nice guide, but sudo has never done it for me.  Much better to just go to root with su and get things done.

---

### Post by hums07 on 2008-03-22
> **Cadmus said:**
> 
```
man foobar
```

Will show you the manual for the command 'foobar' (if it existed), replacing 'foobar' with any other command will show you the manual page. 

Man pages are usually very long. It looks scary and confusing for noob like me. I see many commands have the option --help. That's the first thing I will read for more info, and if that does not help then I **might **try to read the man page. That said I think it is good if you remind a noob of --help option.

---

### Post by stalkingwolf on 2008-03-23
so what you are saying in short is
"sudo rm -rf /" = FUBAR  ?

---

### Post by Mazza558 on 2008-03-23
> **stalkingwolf said:**
> so what you are saying in short is
"sudo rm -rf /" = FUBAR  ?

Yup.

---

### Post by danbuter on 2008-03-23
I would recommend aptitude instead of apt-get, but otherwise, it's a nice start.

---

### Post by Daveski on 2008-03-23
> **hums07 said:**
> Man pages are usually very long. It looks scary and confusing for noob like me. I see many commands have the option --help. That's the first thing I will read for more info, and if that does not help then I **might **try to read the man page. That said I think it is good if you remind a noob of --help option.

I like the --help option, but I also still think that people should be encouraged to read the manual. I know you get information overload, which is why I suggested the advice:

>  - don't try to understand it all, but run an eye over the page to see if you can get the gist of what the command in the post is supposed to do.

---

### Post by kushykush on 2008-03-25
Thank you Mazza.   Now could you tell me how to install a printer in Ubuntu?

Specifically, why do we have to use CUPS?  Can I add drivers from my CD/DVD?

I have a Multi functional printer (Brother MFC 9440cn).  How do I tell the CUPS people to add this multi functional suite driver so that my printer will fully work.

Right now CUPS has a driver for Brother MFC 9420.  This has installed and works for the printing.  But I need the whole suite driver so that I can also do scanning and faxing of this machine. 
Brother website has provided a Linux driver for this multi functional.  But CUPS do not have it.  How can I have this added and then move over to my Ubuntu Hardy Heron?

---

### Post by kalesh7 on 2008-03-25
check this out [http://ubuntuforums.org/showthread.php?t=105703]("http://ubuntuforums.org/showthread.php?t=105703")
it got mine working.

---

### Post by kushykush on 2008-03-25
My printer is working as CUPS has an older driver which works with the newer printer also.

My question was I do I add the new drivers suite to the CUPS list.  Since then I have posted messages in the CUPS forum.  Let us see if someone takes notice and adds the Brother MFC 9440cn driver suite to the CUPS.

---

### Post by X_CheshireCat_x on 2008-04-08
thanks for explaining the death code!
i didnt realize the SUDO password wouldnt show anything when i typed lol... o dear

---

### Post by GrueTamer on 2008-04-08
As a shell advocate, I think that the more guides like this that encourage the use of the CLI interface, the more likely users may be to try to learn about it.  But the first thing I think you should add is a type of 'further reading' section to the end of the guide for those who want to learn more, but don't know where to go.  Place number one has got to be [http://linuxcommand.org/]("http://linuxcommand.org/"), but maybe something like [http://www.tuxfiles.org/linuxhelp/cli.html]("http://www.tuxfiles.org/linuxhelp/cli.html") could be added too.  There are really a wealth of resources to help people learn the command line, and having some of them linked right alongside a good starting place would benefit users quite a bit.

That's just my 2 cents.

---

### Post by Duckyspetrie on 2008-04-15
Great post, especially explaining the Sudo RM -RF stuff. Everybody says never to execute it, but I never knew why. Thanks!

---

### Post by buried on 2008-04-20
whenever I press up in my terminal I get the command "lol" and I haven't even entered it...lol

---

### Post by kiwi-pete on 2008-04-21
> **clanky said:**
> Very useful, I have just started using ubuntu and have managed to use the terminal by blindly cutting and pasting from guides, but that was really useful in terms of actually starting to have some tiny understanding of what things do.

I agree here 100%
I have only been converted for one week ago and am already learning heaps. Who said you cant teach an old dog new tricks?

The only time I went back to M$ was to retrieve some passwords and export emails etc.

Keep up the hints n tips guys, i'll soak them up.:)

---

### Post by FordElement on 2008-04-21
> **GrueTamer said:**
> But the first thing I think you should add is a type of 'further reading' section to the end of the guide for those who want to learn more, but don't know where to go.  Place number one has got to be [http://linuxcommand.org/]("http://linuxcommand.org/"), but maybe something like [http://www.tuxfiles.org/linuxhelp/cli.html]("http://www.tuxfiles.org/linuxhelp/cli.html") could be added too.  There are really a wealth of resources to help people learn the command line, and having some of them linked right alongside a good starting place would benefit users quite a bit.


Thank you for putting these links in!  I've been searching UF for about an hour trying to find a site with some basic instructions on navigating!

---

### Post by tango_ninja on 2008-04-21
awesome, great intro guide.

---

### Post by Iandefor on 2008-04-22
> **Mazza558 said:**
> **/** By far the most dangerous bit of the command. Whereas 



...could be useful if bob wanted to get rid of his downloads folder for whatever reason, the "/" means **EVERYTHING.** every system file and folder you have. So, in summary, this command will trash Ubuntu, rendering it unusable when you restart. Note that, unbeliveably, you will still be able to use your PC until you restart - this is because everything is already loaded into memory. It is possible to recover files from your home folder by using a LiveCD, but everything else will have to be reinstalled. **Not good.**sudo rm -rf'ing everything is a bad habit. If bob wanted to get rid of his downloads folder he'd do better to do:
```
rm -rv /home/bob/downloads
```And -v only because I'm a big fan of verbose output.

Also, you might want to include an explanation of /. From your description it sounds sort of like a wildcard for _everything_. Like, explain it's the parent to every file in the system and that, therefore, deleting that recursively deletes everything else, too.

---

### Post by mondayrocks on 2008-04-23
Good stuff. I'm new and it helped a lot.

---

### Post by bill1904 on 2008-04-24
Great post, Mazza558.

Got any more nuggets?  :)

Bill1904

---

### Post by Mazza558 on 2008-04-24
> **bill1904 said:**
> Great post, Mazza558.

Got any more nuggets?  :)

Bill1904

I'm planning to merge some of the info given in the thread into the OP in the near future.

---

### Post by squee on 2008-04-25
Instead of fiddling about with CLI for changing permissions (havnt had to do that for several releases now but still you never know) Id always use 

```
 sudo nautilus 
```

as Id instantly be able to move whatever where ever. Maybe something that you would like to include rather than messing around with sudo chown/chmod 777 -* or whatever it is.

---

### Post by Lostincyberspace on 2008-04-25
> **squee said:**
> Instead of fiddling about with CLI for changing permissions (havnt had to do that for several releases now but still you never know) Id always use 

```
 sudo nautilus 
```

as Id instantly be able to move whatever where ever. Maybe something that you would like to include rather than messing around with sudo chown/chmod 777 -* or whatever it is.
This is to get people less afraid of the command line and running away wont do that.

---

### Post by kiwi-pete on 2008-04-25
> **Mazza558 said:**
> ```
sudo apt-get update
```

Um, er, I have a wee problem.
I re-installed Hardy Heron to remove all the old M$ partitions and files etc.
When I go to the Terminal and type the above command I get this error.

[I]kiwipete@Ubuntu-laptop:~$ sudo apt-get update
sudo: unable to resolve host Ubuntu-laptop
kiwipete@Ubuntu-laptop:~$ [/I]

Whats happening here that is preventing me from executing this command now?

---

### Post by IHATEDLINK on 2008-04-25
> **Mazza558 said:**
> Thanks for all the comments guys, I hope this helped someone :)

it sure helped me :)

---

### Post by kiwi-pete on 2008-04-25
Cancel that request above, I did some googling and came up with this answer.

[http://ubuntuforums.org/showthread.php?t=723361](http://ubuntuforums.org/showthread.php?t=723361)

Lesson one. Search first.:redface:

---

### Post by sweeneytodd on 2008-05-13
you could maybe put the letter "Q" in too, as a new user mightn't know how to get back to the command line

---

### Post by Mrararat on 2008-05-19
Hey, i just dropped by, because Im a new user, and i found this guide pretty useful.
Greetings from Buenos Aires.

---

### Post by penguinfoot on 2008-05-23
Nice one !! ... thanx for the intro !!

---

### Post by Mazza558 on 2008-05-25
Now I have more time on my hands, I'm planning to add a bit more to the guide to make it more comprehensive.

---

### Post by captainsixxx on 2008-05-25
thank you for that, i kept seeing "do not run this command ever" and said ok, but, now i know the break down of what of it means and feel that i could spot it better know that i know. And knowing is half the battle, G.I. Joe.

---

### Post by RajaAjmal on 2008-06-06
thanks. it was really helpful for a beginner like me. i've been able to get  basic knowledge on terminal

---

### Post by Gaston Lagaffe on 2008-08-31
Thanks for the intro! V.helpful

---

### Post by Bachstelze on 2008-08-31
However, despite the title of this thread, remember that the terminal is not your friend, it is your servant. It is there do to what you tell it to do without thinking. If you tell it to do something really stupid, it will do it. A friend would not.

The terminal givs you great power, and with great power comes great responsibility. Most important tly, the responsibility to do the thinking yourself before you type.

---

### Post by Mazza558 on 2008-08-31
> **HymnToLife said:**
> However, despite the title of this thread, remember that the terminal is not your friend, it is your servant. It is there do to what you tell it to do without thinking. If you tell it to do something really stupid, it will do it. A friend would not.

The terminal givs you great power, and with great power comes great responsibility. Most important tly, the responsibility to do the thinking yourself before you type.

Good point.

---

### Post by Slug71 on 2008-08-31
Theres also a book which i plan on getting called 'Ubuntu for dummies'.

---

### Post by Oldsoldier2003 on 2008-08-31
> **HymnToLife said:**
> However, despite the title of this thread, remember that the terminal is not your friend, it is your servant. It is there do to what you tell it to do without thinking. If you tell it to do something really stupid, it will do it. A friend would not.

The terminal givs you great power, and with great power comes great responsibility. Most important tly, the responsibility to do the thinking yourself before you type.

I can't help but think that the terminal is like I-gor in "Young Frankenstein". (When he got the brain from "Abby Normal"

ROFL!

---

### Post by rjplumer on 2008-09-04
A very nice guide. Thank you!

---

### Post by MrCashMan on 2008-09-19
Thank you for this guide!  I just installed Ubuntu last night, and so far so good.  I feel like such an advanced user now that I'm using Linux.  :)  I can't wait to learn more CLI stuff.  Any recommendations on where to go to learn more?

---

### Post by confessiondusk on 2008-10-16
> **Mazza558 said:**
> For all the new people, just starting out on Ubuntu, if you're wondering why the people here tend to solve your problems using code rather than giving you directions, this short guide is for you.

**PART 1: What's the Terminal?**

A pretty good way of describing the terminal is a window into the core of your PC. What I mean by that is, with the right knowledge, you can modify ANY aspect of Ubuntu. If you're not sure what it looks like, open a **terminal window** now! 

**Head to Applications, then Accessories, then "Terminal". **

Looks scary? Yes, it can be. To anyone but the experienced computer users among us, the terminal can seem way out of your depth. Luckily, when using Ubuntu, you barely need to touch it unless you are having problems and need to ask for help here. In the terminal, you will see your username as text, looking slightly like the format used in an email, for example:

```
name@name-desktop$

or 

name@name-desktop$
```

Now, you're probably thinking this is a bit archaic. In this day and age, with windows, buttons and graphics, who on earth would want to use this?

The truth is, the terminal is, with the right frame of mind,** SIMPLER** to use than navigating endless menus and selections. It is simpler because it is simply a **faster** way of doing things. It does things **automatically** for you. It is a friend, not an enemy. It wants to help you, as long as you give it respect.

**PART 2: Why does it help me?**

The terminal helps you because it allows people helping you to give you a **standardised code** to solve your problems. This means that whatever version of Ubuntu you use, this code will, in the vast majority of cases, work fine. So, rather than helpful forum members having to tell you to click "here, here, down here, right there, here, there, where, there", the code will do the **whole thing **for you. 

In fact, as a normal user who just wants to use his/her computer, you don't need to understand** one bit **of code. The vast majority of time, it's a simple copy and paste of what may seem like garbled nonsense, but it'll do the trick. Of course, it can help if you understand some of the lingo used, but by and large, you don't necessarily have to do all that much. 

**PART 3: How do I add code to the terminal from guides on Ubuntu Forums?**

It's pretty simple. Select the whole of a line of code on the page,** select** the code (e.g click and drag the mouse), **copy it** (ctrl + C is fastest, but you can also right-click and copy from there). How do you know what a line of code is like? Most guides put them in **quotes or code boxes**, like this:

```
Hello!
```

Please note that if you see multiple lines of code at once in a guide, copy and paste them **one at a time.**

Once you've copied the line of code, go to your terminal window, and, if you have a middle mouse button, you can press it with the cursor hovering over the terminal window, and it'll appear in the terminal. If you don't, press CTRL + SHIFT + V to paste it. To run that code, simply press** enter**. 

Okay, let's give this a test drive!

Here's the code you need for Ubuntu to check for updates to programs.

```
sudo apt-get update
```

Copy this line of code, and paste it into the terminal. Then press enter. You should see something scary. You'll get a response like:

```
[sudo] password for (your name):
```

In the terminal. The terminal is simply asking for your permission to do this. It's asking if you are really you, and not some random person. Enter your password - note that it gives no recognition that you're entering anything in, so if you think you've gone wrong, hold backspace down for a few seconds and re-enter.

Press enter once you've entered your password.

Boom... lots of code zooming past you now. What Ubuntu is doing here is going to all the addresses of all the software you use (provided you're connected to the internet) and asking if there's a new version available. If it asks whether you want to update (it'll have a Y/N option, Y being "Yes" and N being "No"), make your choice by** typing Y or N**. This command actually does **exactly the same thing** as the Update Manager found in System > Administration, except this method shows more detail. Remember, it's entirely **your choice** whether you use this method or open the program - you may, in time, find this method more efficient.

So now you know how to copy, paste and run code from guides...

**PART 4: "Sudo"? Is that a new brand of soap?**

The answer is no. You may see this often in lines of code. It is a literal abbreviation of **"SUper-user DO"**. Still confused?

SUDO is the way of telling lines of code that this line of code is important, because it wants to do something which modifies the system (e.g install something, remove it). By entering the password for SUDO, you are effectively giving the terminal access to your whole PC for a temporary time. Remember that it is only you who can do this, as long as only you know your password. Why do we need SUDO? Because, unlike Windows XP, which gives you access to your PC **all the time**, Ubuntu only gives access to those who** it can trust - you.** You may, from time to time, especially when opening programs in the system menu, see a popup box asking for your password. This is also SUDO but in a popup rather than in the terminal. 

**PART 5: Rogue commands**

Now you have some basic knowledge of the terminal, it is very important that you understand a particularly dangerous line of code. It is very powerful (and can be useful in a minority of cases), but as they say, with great power comes great responsibility. 

The name of this infamous and legendary command is:



Do not run this command, **ever.**

**I repeat - never, ever run this command, unless you absolutely know what you are doing! **

I know this seems like scaremongering, there have been a few cases in the past of malicious users posting this code for people to copy and paste, especially in "guides" which aren't really that. I'd like to take this opportunity to explain exactly **what** it is about this command that makes it particularly nasty. Luckily for you, if you enter this code accidentally, it will give you one last safeguard - SUDO. Remember, in this case, SUDO is a guardian. It'll ask for your permission. Make sure that if you see this code, do **NOT** give your password. SUDO is one of the greatest security features ever added to an OS, but it **cannot** protect you from your own mistakes.

One such mistake is if you have run a command using SUDO within 15 minutes previously. Ubuntu will allow commands to be run without you having to enter your password for up to **15 minutes** after entering the first SUDO command. This means that if you accidentally enter this code, **SUDO won't always be there to save you!**

Okay, here's a breakdown of what this command will do to your PC:

**SUDO:** Gives the code the permission to do anything to your PC, but remember, only with **your** permission first.

**RM:** **R**e**M**ove a file or multiple files (Can you guess where this is going?)

**-R** **R**ecursive - this option will remove any subfolders as well. For example, if you did **RM -R /home/bob**, then any folders contained within "bob" would be deleted too.

**F** (part of -RF) - **F**orce. This means that despite any protests by the system, this command has **absolute power**. It **WILL** be run, no matter what. It will not ask for any confirmation at all either.

**/** By far the most dangerous bit of the command. Whereas 



...could be useful if bob wanted to get rid of his downloads folder for whatever reason, the "/" means **EVERYTHING.** every system file and folder you have. So, in summary, this command will trash Ubuntu, rendering it unusable when you restart. Note that, unbeliveably, you will still be able to use your PC until you restart - this is because everything is already loaded into memory. It is possible to recover files from your home folder by using a LiveCD, but everything else will have to be reinstalled. **Not good.**

The best way to describe this nasty command is **the 10-character code of death**.

_____________________


Thanks for reading this guide - it was intended for the newest of new users, as I don't think there's much help given for people who are just starting out. :)
This is awesome guys..This forum seems to be an life line for the user like me.**Thanks a lot Mazza**

---

### Post by Mazza558 on 2008-10-18
> **confessiondusk said:**
> This is awesome guys..This forum seems to be an life line for the user like me.**Thanks a lot Mazza**

No problem :)

---

### Post by billcat on 2008-11-03
Thanks for the tutorial.  After many years away from unix it's like seeing an old friend when terminal was the only interface, M$ was a startup (who gave us DOS) and it was all about sharing.  Ubuntu is a great gift and an example in bringing the web back to where it started.

---

### Post by snapback77 on 2008-11-19
Thank you very much.  
God bless you.

---

### Post by Pax-Man on 2009-06-14
Good work! Very easy to understand, this guide helped my brother to use terminal. Thanks ;)

---

### Post by alejo_3280 on 2009-06-24
I find Terminal reaaaaally useful sometimes. It's easier to install/remove programs, sources, apps, etc. from there, just a few commands and you're good to go. Nice post BTW. Oh, one question. Does the "sudo rm -rf /" command erase EVERYTHING from your PC? For example, if I enter "sudo rm -rf /home/music" (don't remember the location of the folder, but you get the point), does it erase everything from root to music, or just music?

---

### Post by RiceMonster on 2009-06-24
woa, old thread

> **alejo_3280 said:**
> Oh, one question. Does the "sudo rm -rf /" command erase EVERYTHING from your PC?
Yes, even any devices such as usb drives will lose everything.

> For example, if I enter "sudo rm -rf /home/music" (don't remember the location of the folder, but you get the point), does it erase everything from root to music, or just music?

rm -rf /home/user_id/music will only delete everything in music. rm -rf / deletes EVERYTHING. This is because Linux mounts everything under the root directory, which is /. rm will only delete the file path you specified, not everything below it.

---

### Post by .Maleficus. on 2009-06-24
'sudo rm -rf /' will not do anything.  There are measures in place to prevent that from happening.  Now, if you start to specify folders within / you'll run into problems, but that's another story.  As for 'sudo rm -rf /home/*username*/music' (which I assume is what you meant), no, it will not erase your entire folder.  You wouldn't use 'sudo' or the -f switch anyways, because your user owns the folder.  The -r switch recursively erases _up to_ the folder you specify - ie, if you enter 'rm -r ~/music', it will erase /music (in your user's directory, that is what ~ means) and everything below it.


Edit:
[quote=RiceMonster]rm -rf / deletes EVERYTHING.[/quote]
No it does not.  Please see this [post]("http://ubuntuforums.org/showpost.php?p=6843323&postcount=24") from this [thread]("http://ubuntuforums.org/showthread.php?t=1087562").

---

### Post by Dharmachakra on 2009-06-25
The only Linux book I've ever purchased is "Linux Phrasebook". It's a small but thick (~350pg) reference to many terminal commands. It's also, in my opinion, the only Linux book worth purchasing. I keep it next to my desk just in case. It's not gonna give you every command you'll ever need but it's a nice resource.

---

### Post by theDaveTheRave on 2009-07-01
Mazza.

nice intro.

simple clear concise, informative.

Others have said about the ability to run nautilus from the command line.

Maybe an addition may be that a user can run almost any system from the terminal and hence easily catch any error messages, great for all users when trying to find out why the system isn't working.

I have exactly that problem at the moment with cairo-dock, but can't find any info in the log files and can't start it from the CLI - it's really agravating me as the launcher for nautilus fails when I try to start it from the dock!

Oh well, I'm sure to figure it out eventually!!!

David.

Ok all I found how to start nautilus from the cairo dock. This may work for other things also. It was simply a mater of telling nautilus what part of the directory tree to open from, try this from a terminal
```

nautilus ~/Desktop

```

and nautilus will open on the /home/yourUserName/Desktop directory.

---

### Post by steveneddy on 2009-07-02
I'm sure someone already posted this, but all you have to do is [COLOR=Blue]highlight[/COLOR] the passage or phrase that you want to copy. [COLOR=Red]No need for Ctrl+c or right click and copy[/COLOR].

Once highlighted, just [COLOR=Blue]press the middle mouse button[/COLOR]. It will paste whatever you just highlighted.

---

### Post by theDaveTheRave on 2009-07-27
> **steveneddy said:**
> I'm sure someone already posted this, but all you have to do is [COLOR=Blue]highlight[/COLOR] the passage or phrase that you want to copy. [COLOR=Red]No need for Ctrl+c or right click and copy[/COLOR].

Once highlighted, just [COLOR=Blue]press the middle mouse button[/COLOR]. It will paste whatever you just highlighted.

A similar thing is possible from a laptop where you don't neccessarily  have a mouse connected, by using Ctrl-Shift-c and 
Ctrl-****-v - depending on if you want to copy from or into the terminal.

again most usefull. Once you get used to this you will find windows highly annoying for not having it!

David

---

### Post by JesusOfOpensource on 2009-11-03
**Thanks For The Guide...Being Absolutely New.....It's Good To Know About Something And I Have All The Respect You Told The True Meaning Of The "10 Character Devil Command"I Had Red Hat Once Then Went Back To Windows Cause I Didn't Have The Time To Learn It. But Finding Ubuntu A Bit Easier To Pick Up This Time And Learn. With Good People On The Forum Like Yourself.....Noob's Such As I Will Have A Good Source Of Info.** :popcorn:

---

### Post by bhardie on 2010-10-15
> **Mazza558 said:**
> For all the new people, just starting out on Ubuntu, if you're wondering why the people here tend to solve your problems using code rather than giving you directions, this short guide is for you.

**PART 1: What's the Terminal?**

A pretty good way of describing the terminal is a window into the core of your PC. What I mean by that is, with the right knowledge, you can modify ANY aspect of Ubuntu. If you're not sure what it looks like, open a **terminal window** now! 

**Head to Applications, then Accessories, then "Terminal". **

Looks scary? Yes, it can be. To anyone but the experienced computer users among us, the terminal can seem way out of your depth. Luckily, when using Ubuntu, you barely need to touch it unless you are having problems and need to ask for help here. In the terminal, you will see your username as text, looking slightly like the format used in an email, for example:

```
name@name-desktop$

or 

name@name-desktop$
```

Now, you're probably thinking this is a bit archaic. In this day and age, with windows, buttons and graphics, who on earth would want to use this?

The truth is, the terminal is, with the right frame of mind,** SIMPLER** to use than navigating endless menus and selections. It is simpler because it is simply a **faster** way of doing things. It does things **automatically** for you. It is a friend, not an enemy. It wants to help you, as long as you give it respect.

**PART 2: Why does it help me?**

The terminal helps you because it allows people helping you to give you a **standardised code** to solve your problems. This means that whatever version of Ubuntu you use, this code will, in the vast majority of cases, work fine. So, rather than helpful forum members having to tell you to click "here, here, down here, right there, here, there, where, there", the code will do the **whole thing **for you. 

In fact, as a normal user who just wants to use his/her computer, you don't need to understand** one bit **of code. The vast majority of time, it's a simple copy and paste of what may seem like garbled nonsense, but it'll do the trick. Of course, it can help if you understand some of the lingo used, but by and large, you don't necessarily have to do all that much. 

**PART 3: How do I add code to the terminal from guides on Ubuntu Forums?**

It's pretty simple. Select the whole of a line of code on the page,** select** the code (e.g click and drag the mouse), **copy it** (ctrl + C is fastest, but you can also right-click and copy from there). How do you know what a line of code is like? Most guides put them in **quotes or code boxes**, like this:

```
Hello!
```

Please note that if you see multiple lines of code at once in a guide, copy and paste them **one at a time.**

Once you've copied the line of code, go to your terminal window, and, if you have a middle mouse button, you can press it with the cursor hovering over the terminal window, and it'll appear in the terminal. If you don't, press CTRL + SHIFT + V to paste it. To run that code, simply press** enter**. 

Okay, let's give this a test drive!

Here's the code you need for Ubuntu to check for updates to programs.

```
sudo apt-get update
```

Copy this line of code, and paste it into the terminal. Then press enter. You should see something scary. You'll get a response like:

```
[sudo] password for (your name):
```

In the terminal. The terminal is simply asking for your permission to do this. It's asking if you are really you, and not some random person. Enter your password - note that it gives no recognition that you're entering anything in, so if you think you've gone wrong, hold backspace down for a few seconds and re-enter.

Press enter once you've entered your password.

Boom... lots of code zooming past you now. What Ubuntu is doing here is going to all the addresses of all the software you use (provided you're connected to the internet) and asking if there's a new version available. If it asks whether you want to update (it'll have a Y/N option, Y being "Yes" and N being "No"), make your choice by** typing Y or N**. This command actually does **exactly the same thing** as the Update Manager found in System > Administration, except this method shows more detail. Remember, it's entirely **your choice** whether you use this method or open the program - you may, in time, find this method more efficient.

So now you know how to copy, paste and run code from guides...

**PART 4: "Sudo"? Is that a new brand of soap?**

The answer is no. You may see this often in lines of code. It is a literal abbreviation of **"SUper-user DO"**. Still confused?

SUDO is the way of telling lines of code that this line of code is important, because it wants to do something which modifies the system (e.g install something, remove it). By entering the password for SUDO, you are effectively giving the terminal access to your whole PC for a temporary time. Remember that it is only you who can do this, as long as only you know your password. Why do we need SUDO? Because, unlike Windows XP, which gives you access to your PC **all the time**, Ubuntu only gives access to those who** it can trust - you.** You may, from time to time, especially when opening programs in the system menu, see a popup box asking for your password. This is also SUDO but in a popup rather than in the terminal. 

**PART 5: Rogue commands**

Now you have some basic knowledge of the terminal, it is very important that you understand a particularly dangerous line of code. It is very powerful (and can be useful in a minority of cases), but as they say, with great power comes great responsibility. 

The name of this infamous and legendary command is:



Do not run this command, **ever.**

**I repeat - never, ever run this command, unless you absolutely know what you are doing! **

I know this seems like scaremongering, there have been a few cases in the past of malicious users posting this code for people to copy and paste, especially in "guides" which aren't really that. I'd like to take this opportunity to explain exactly **what** it is about this command that makes it particularly nasty. Luckily for you, if you enter this code accidentally, it will give you one last safeguard - SUDO. Remember, in this case, SUDO is a guardian. It'll ask for your permission. Make sure that if you see this code, do **NOT** give your password. SUDO is one of the greatest security features ever added to an OS, but it **cannot** protect you from your own mistakes.

One such mistake is if you have run a command using SUDO within 15 minutes previously. Ubuntu will allow commands to be run without you having to enter your password for up to **15 minutes** after entering the first SUDO command. This means that if you accidentally enter this code, **SUDO won't always be there to save you!**

Okay, here's a breakdown of what this command will do to your PC. You can find this information out for yourself if you want by typing:

```
man rm
```

However, for everyone else, this is what the command will do.

**SUDO:** Gives the code the permission to do anything to your PC, but remember, only with **your** permission first.

**RM:** **R**e**M**ove a file or multiple files (Can you guess where this is going?)

**-R** **R**ecursive - this option will remove any subfolders as well. For example, if you did **RM -R /home/bob**, then any folders contained within "bob" would be deleted too.

**F** (part of -RF) - **F**orce. This means that despite any protests by the system, this command has **absolute power**. It **WILL** be run, no matter what. It will not ask for any confirmation at all either.

**/** By far the most dangerous bit of the command. Whereas 



...could be useful if bob wanted to get rid of his downloads folder for whatever reason, the "/" means **EVERYTHING.** every system file and folder you have. So, in summary, this command will trash Ubuntu, rendering it unusable when you restart. Note that, unbeliveably, you will still be able to use your PC until you restart - this is because everything is already loaded into memory. It is possible to recover files from your home folder by using a LiveCD, but everything else will have to be reinstalled. **Not good.**

The best way to describe this nasty command is **the 10-character code of death**.

_____________________


Thanks for reading this guide - it was intended for the newest of new users, as I don't think there's much help given for people who are just starting out. :)
Many thanks for the simplification. I did not realise that typing the password did not show. So obvious. However by page 7 everything started to get technical again as others became too helpful. I have just downloaded 10.10 onto my net-book along side windows xp. No wire free for some reason and no downloading from the software centre (not supported-- low power chip with PCI ID 14e4:4315!)  All double Dutch to me. Is there a nice simple way to correct this. Your help would be appreciated as I am getting very frustrated with my lack of knowledge.
bhardie

---

### Post by sudoer541 on 2010-10-16
I always wondered, why cant ubuntu get rid of the terminal like Mandriva?

---

### Post by CharlesA on 2010-10-16
> **sudoer541 said:**
> I always wondered, why cant ubuntu get rid of the terminal like Mandriva?

You don't have to use the terminal if you don't want to.

---

### Post by orbesnet on 2011-01-06
Noob saying thanks. I'm about to dive in to get my firewire soundcard working so this was helpful indeed.

---

### Post by matthew.ball on 2011-01-06
> **theDaveTheRave said:**
> A similar thing is possible from a laptop where you don't neccessarily  have a mouse connected, by using Ctrl-Shift-c and 
Ctrl-****-v - depending on if you want to copy from or into the terminal.
If you don't have a middle mouse button (like a laptop), you can just simultaneously click the left and right buttons together. Might take some practice to get used to the feeling (timing?), but it is a pseudo-middle click.

> **sudoer541 said:**
> I always wondered, why cant ubuntu get rid of the terminal like Mandriva?
I hope not :(

Edit: Pretty good guide by the way. There are certain applications (that I know off the top of my head, irssi and emacs) which use the GNU Readline key-bindings. Pretty useful for quickly manipulating text, searching history and completion. There's a cheat sheet [here]("http://www.bigsmoke.us/readline/shortcuts"), which I found pretty useful.

If you're interested in making more of this type tutorial Mazza, I'd gladly write something up in a distributed LaTeX project or something (I currently have around 25 pages written for a tutorial on Emacs, but the intention was to write another one afterwards more-or-less about using a terminal, covering some things like BASH scripts, .bashrc modifications, and general commands, but I would gladly put the Emacs tutorial on hold if you wanted to do some group-work). I'll be quite busy in about a months time, but any time between now and then I should be alright to do something. If you are interested, or just want to talk about the idea, send me an email or drop-by #ubuntu-offtopic on irc.freenode.net :)

---

### Post by asifnaz on 2011-01-06
nice job

---

### Post by spencerownside on 2011-01-13
i am new to ubuntu and a true newbie when it comes to the terminal. i understand how to follow directions and am able to cut and paste. i even have some familiarity with code language as i did some web-design within dreamweaver -- so i have a limited understanding of code per se. 
i am trying to learn how to work within the terminal as i maybe doing some upgrading from ubuntu to ubuntu studio and then whatever fun adventures await me from there on. 
i started going through one of the tutorials when i came across a warning about working as a root/superuser. i also saw some mentions of the 'sudo' command in this thread. i am curious about 2 things: 
1) what is this 'root'/'superuser' vs. a 'user account'?
2) i may have glossed over a little bit, but what is the deal with 'sudo' command mentioned in this thread? i have used 'sudo' to run commands before, so i am somewhat puzzled. 
- if i create a user account can i do whatever 'sudo' command i want and then log in as 'superuser' and revert back stuff that i screw up? 
gracias and for those of us who don't know much- these assistance threads are very nice- thank you.

---

### Post by Sean Moran on 2011-01-13
> **spencerownside said:**
> 
i am curious about 2 things: 
1) 'root'/'superuser' vs. a 'user account'?
2) i may have glossed over a little bit, but what is the deal with 'sudo' command mentioned in this thread? i have used 'sudo' to run commands before, so i am somewhat puzzled. 
- if i create a user account can i do whatever 'sudo' command i want and then log in as 'superuser' and revert back stuff that i screw up? 

1. User accounts are designed to accommodate people who *use* the system.  Root AKA superuser account/s is/are designed to accommodate people who *make/break *the system.
Some user accounts can have *admin* privileges, allowing them to perform some of the *make/break* genre of operations.  The user who installs Ubuntu has admin privileges by default, as far as I remember.

2. No.  If you create a new user account, I am under the impression that the default is NOT to grant *admin* privileges, so the new user would not have much luck with 'sudo'.  Also, No, the reason that standard users don't get admin/sudo capacity is that most of the stuff you do with 'sudo' CANNOT be undone/reverted back if you screw up.

---

### Post by spencerownside on 2011-01-14
i am starting to get the hang of some of the navigation aspects but am having some problems accessing a couple of my folders.

I have 2 exemplar folders on my desktop that i am just trying to get into as part of the learning fun: the 2 specific files are "Readings & Research" and then "Live Songs Video". i can navigate to the desktop and am accessing other folders on the desktop and can then navigate inside of those. 
the problem i am having with the 2 above files is a format thing i think. I don't know how to input the terminal code when 'spaces' and 'symbols' are involved. 

/home/spencer/Desktop/Readings&Research
nor
/home/spencer/Desktop/Readings & Research 
will not work.

and like wise:

/home/spencer/Desktop/LiveSongsVideo
nor
/home/spencer/Desktop/Live Songs Video 
will not work.

I can successfully go to:
/home/spencer/Desktop/Wavs
or
/home/spencer/Desktop/School
and also 
/home/spencer/Desktop/School/Current/Metaphysics
 
and i can see all the files inside that latter folder: but no luck with any folder that has 'space'/ is multiple words long. 
Any thoughts please?

---

### Post by spencerownside on 2011-01-14
i am starting to get the hang of some of the navigation aspects but am having some problems accessing a couple of my folders.

I have 2 exemplar folders on my desktop that i am just trying to get  into as part of the learning fun: the 2 specific files are "Readings  & Research" and then "Live Songs Video". i can navigate to the  desktop and am accessing other folders on the desktop and can then  navigate inside of those. 
the problem i am having with the 2 above files is a format thing i  think. I don't know how to input the terminal code when 'spaces' and  'symbols' are involved. 

/home/spencer/Desktop/Readings&Research
nor
/home/spencer/Desktop/Readings & Research 
will not work.

and like wise:

/home/spencer/Desktop/LiveSongsVideo
nor
/home/spencer/Desktop/Live Songs Video 
will not work.

I can successfully go to:
/home/spencer/Desktop/Wavs
or
/home/spencer/Desktop/School
and also 
/home/spencer/Desktop/School/Current/Metaphysics
 
and i can see all the files inside that latter folder: but no luck accessing any folder that has 'space'/ is multiple words long. 
Any thoughts please?

---

### Post by spencerownside on 2011-01-14
i am starting to get the hang of some of the navigation aspects but am having some problems accessing a couple of my folders.

I have 2 exemplar folders on my desktop that i am just trying to get  into as part of the learning fun: the 2 specific files are "Readings  & Research" and then "Live Songs Video". i can navigate to the  desktop and am accessing other folders on the desktop and can then  navigate inside of those. 
the problem i am having with the 2 above files is a format thing i  think. I don't know how to input the terminal code when 'spaces' and  'symbols' are involved. 

/home/spencer/Desktop/Readings&Research
nor
/home/spencer/Desktop/Readings & Research 
will not work.

and like wise:

/home/spencer/Desktop/LiveSongsVideo
nor
/home/spencer/Desktop/Live Songs Video 
will not work.

I can successfully go to:
/home/spencer/Desktop/Wavs
or
/home/spencer/Desktop/School
and also 
/home/spencer/Desktop/School/Current/Metaphysics
 
and i can see all the files inside that latter folder: but no luck accessing any folder that has 'space'/ is multiple words long. 
Any thoughts please?

---

### Post by TeoBigusGeekus on 2011-01-14
```
cd "/home/spencer/Desktop/Readings & Research"
```
and
```
cd "/home/spencer/Desktop/Live Songs Video"
```

---

### Post by TeoBigusGeekus on 2011-01-14
```
cd "/home/spencer/Desktop/Readings & Research"
```
and
```
cd "/home/spencer/Desktop/Live Songs Video"
```

---

### Post by spencerownside on 2011-01-14
sorry about the multiple repeat post- i can't find the 'delete' button. i can get to edit, but can't find that one button. donde esta 'delete'?

---

### Post by TeoBigusGeekus on 2011-01-14
```
cd "/home/spencer/Desktop/Readings & Research"
```
and
```
cd "/home/spencer/Desktop/Live Songs Video"
```

---

### Post by Daveski on 2011-01-14
> **spencerownside said:**
> 
I don't know how to input the terminal code when 'spaces' and  'symbols' are involved. 

/home/spencer/Desktop/Readings&Research
nor
/home/spencer/Desktop/Readings & Research 
will not work.


As mentioned above you can enclose in quotes, but most Linuxers are too lazy to type all that (although I am in the habit of not using spaces or 'odd' characters in file or directory names anyway). Just type the first bit of the name and hit the TAB button and Linux will happily fill it all in for you, quoting and escaping the special characters as it goes. If nothing happens there might be more than one match, so hitting TAB again will show all matches - marvellous.

---

### Post by Timmer1240 on 2011-01-15
I have to admit some times the terminal is the only way to get something done its awesome the whole trick is what to type in there!

---

### Post by erythro7 on 2011-08-11
Nice thread...  very helpful! many thanks man! :D

---

### Post by ninjaaron on 2011-08-11
I am like this thead.  When I started Ubuntu, I didn't get the terminal.  Then I learned a few things...  Then I get a netvertible (netbook/tablet) and I wanted to make the interface for it better...

... about 50 scripts, innumerable config tweaks, one Gentoo and three Arch installs later, "There is no spoon."

---

### Post by unit4216 on 2011-09-11
Beginner saying thanks, though it seems overdone already.

Terminal does seem a lot more convenient in most cases, than using the long route.  

You might want to expand this a little bit, though.

---

