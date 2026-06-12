---
title: "User Friendly?"
date: 2008-05-26
forum: Testimonials &amp; Experiences
---

### Post by Mister URL on 2008-05-26
[FONT=Arial][SIZE=2]:mad: [/SIZE][/FONT][FONT=Arial][SIZE=2]I have been around a looong time, but [/SIZE][/FONT][FONT=Arial][SIZE=2]I [/SIZE][SIZE=2]am a noob Ubuntu user. I started with PC-DOS, through MS-DOS up to version 6.2 and have gone through all the versions of Windows. I even used to do some assembly language programming before MPU's passed 16 bit word length.

I like Ubuntu, but perhaps there needs to be a bigger effort to make it user invisible. I know there is a certain satisfaction in forcing a computer to do your bidding with complex command line options. But there is a reason most of us changed away from command line OS's. They are hard to use. If it's not easy, people won't use them. I read most of the posts in the "Security" forum, and I find that there are only a few GUI offerings for security (firewalls, rootkit detectors, and spyware detectors). 

Am I just a Cranky Old Coot or would it not spread Linux further to make it hidden behind GUI's? I know the skillful programmers here could do that.

Thanks for listening.


[/SIZE][/FONT]

---

### Post by pointone on 2008-05-26
I always liked this explanation:

[quote=http://linuxcommand.org/learning_the_shell.php]Why do you need to learn the command line anyway? Well, let me tell you a story. Not long ago we had a problem where I used to work. There was a shared drive on one of our file servers that kept getting full. I won't mention that this legacy operating system did not support user quotas; that's another story. But the server kept getting full and stopping people from working. One of the software engineers in our company spent the better part of a day writing a C++ program that would look through the directories of all the users and add up the space they were using and make a listing of the results. Since I was forced to use the legacy OS while I was on the job, I installed a version of the bash shell that works on it. When I heard about the problem, I realized I could do all the work this engineer had done with this single line:

du -s * | sort -nr > $HOME/space_report.txt

Graphical user interfaces (GUIs) are helpful for many tasks, but they are not good for all tasks. I have long felt that most computers today do not use electricity. They instead seem to be powered by the "pumping" motion of the mouse! Computers were supposed to free us from manual labor, but how many times have you performed some task you felt sure the computer should be able to do? You ended up doing the work by tediously working the mouse. Pointing and clicking, pointing and clicking.

I once heard an author remark that when you are a child you use a computer by looking at the pictures. When you grow up, you learn to read and write. Welcome to Computer Literacy 101. Now let's get to work.[/quote]

There are GUI offerings for most everything you need to do, but the command line is MUCH more flexible and efficient in many cases. Hiding the command line would probably make Linux more appealing to Windows/Mac users, but the powerful command line is one of the reasons I love Linux so much.

---

### Post by Joeb454 on 2008-05-26
Nearly *all* new users say this. But most things can be done without the use of a command line.

The fact is, it's easier to give out a command that will do it all for you, than guide people through a GUI - plus GUI's vary incredibly on Linux, so you also need to know what people are using (Gnome, KDE, XFCE, Flux etc.etc.)

---

### Post by aysiu on 2008-05-26
I don't see why new users should be bothered with configuring IPTables and such. Just use a strong password. Are these users who are afraid of the command-line also installing Apache and OpenSSH Server?

---

### Post by dasunst3r on 2008-05-26
There seems to exist a stigma of command line -- that everything has to be point-and-click for the Average Joe/Jane/User in order for it to be friendly.  Sure, command line has been around for a long, long time, but I honestly do not see anything wrong with copy-and-paste.  As a matter of fact, I have reason to believe that copy-and-paste is easier than point-and-click to some extent because:
[list=1]
[*]Screenshots take up a lot more bandwidth than text
[*]Copy-and-paste will not require much hunting down of menu options in the absence of screenshots
[/list]
It particularly irritates me when people claim expertise at IT administration, yet they balk at using the command line.  They just don't understand that they might not have the luxury of remote desktop or web interfaces.  If you're 1,000 miles away from the server and are on a cellular connection, what then?

---

### Post by Mister URL on 2008-05-26
[SIZE=2]I am disappointed. When I switch to Ubuntu, I lose my printer, my local network, and my sound. I don't have time to spend days sorting out what is wrong and rounding up drivers and setting parameters. [/SIZE][SIZE=2]I have read dozens of posts here and most of what I see are problems, and often surly responses to "work harder" to get your printer, or wireless, or whatever, to work with Ubuntu[/SIZE]. [SIZE=2]Hey, if it was Easy, anyone could do it.[/SIZE]

[SIZE=2]I could learn the innards of Linux and use the command line syntax, but speaking as a common user, why should I? It's going backward, back to when you had to set up a serial port with baud rate, stop bits, and parity, and set up your config.sys and win.sys with a text editor.[/SIZE][SIZE=2]
[/SIZE][SIZE=2]
I have a working system, and I will stay with it until, inevitably, someone comes out with a real Windows competitor Linux package.[/SIZE][SIZE=2]

[/SIZE][SIZE=2]I really do appreciate the responses to my inquiry. I will be back sometime in the future. Thanks.
[/SIZE]

---

### Post by dasunst3r on 2008-05-26
So tell us more about the things that are not working.  In particular:
[list]
[*]What brand and model of computer do you own?
[*]What brand and model are your sound card, printer, and network card?
[*]What makes you think your local network is gone?
[/list]
Also, it is important to note that in a Windows-entrenched world, the very people who wrote software for Linux really had to "try harder" to get things to work because the manufacturers refuse to help them.  The fact is: computing is still hard, even in the Windows world.  By your logic, if anybody could do something "easy," then we wouldn't have the likes of Geek Squad or Firedog charging out your nose to do what you and I may consider "easy."

---

### Post by MNICY on 2008-05-27
Really, the command line is not hard..
for example, to edit a text file you just use 
gedit /file location
to move a file, you just
mv /file source /file destination
(also, make a launcher with this: "gksudo nautilus", and it will open a file browser with root access. There you go. You can now move files around in the GUI!)

However, there is no reason to learn the command line. The only time i actually have had to use the command like (other then by choice) is when following instructions from people in tutorials.
Just copy and paste. You really cant get more user friendly then that.

yes, it would be nice if everything was GUI. Having everything GUI and CLI would make everyone happy.
However, i am willing to bet almost all tutorials would still use terminal commands. Why? because it is a much easier way to give someone instructions, and much less chance of confusion.

---

### Post by azimuth on 2008-05-27
> **Mister URL said:**
> [FONT=Arial][SIZE=2]:mad: [/SIZE][/FONT][FONT=Arial][SIZE=2]I have been around a looong time, but [/SIZE][/FONT][FONT=Arial][SIZE=2]I [/SIZE][SIZE=2]am a noob Ubuntu user. I started with PC-DOS, through MS-DOS up to version 6.2 and have gone through all the versions of Windows. I even used to do some assembly language programming before MPU's passed 16 bit word length.

I like Ubuntu, but perhaps there needs to be a bigger effort to make it user invisible. I know there is a certain satisfaction in forcing a computer to do your bidding with complex command line options. But there is a reason most of us changed away from command line OS's. They are hard to use. If it's not easy, people won't use them. I read most of the posts in the "Security" forum, and I find that there are only a few GUI offerings for security (firewalls, rootkit detectors, and spyware detectors). 

Am I just a Cranky Old Coot or would it not spread Linux further to make it hidden behind GUI's? I know the skillful programmers here could do that.

Thanks for listening.


[/SIZE][/FONT]
I'm a Cranky Old Coot also, but I have a somewhat different take on my move to GNU/Linux in general and Ubuntu in particular. I am tired of using OS's that hide behind a GUI, where I have no idea of what is actually going on. I didn't move away from DOS and Basic to get away from the command line. I moved to GUI OS's because that is where the software I wanted moved. The tables have turned with Linux. The software is available to do pretty much anything I want to do with a computer and the command line is there to let me use that software in ways that even the author of the software never envisioned.
 
I have no illusions about Linux CLI being "programing". The programing and coding has already been done. The command line is just a way for me to use that code in ways that are specific to my needs and wants. I just need to learn more about the actual commands. I have already seen that they are so much more powerful than anything I ever used in DOS or Basic.

The GUI in Ubuntu is so capable, that the command line is almost never needed for daily use, but the CLI is there when I need to trouble shoot or create a task that is unique to me. Knowing that I am somewhat lazy and will use the GUI rather than learn more of the commands, I have dedicated an old P200 to a command line only Ubuntu install. I should buy a book, but there is so much knowledge available online and more up-to-date than anything that has been to the publishers. 

I am using, among others, [Ubuntu Server Guide]("https://help.ubuntu.com/8.04/serverguide/C/index.html") and [Linux Commands]("http://www.linuxcommand.org/index.php"). Us "Old Coots" need to remember, when we stop learning, we're as good as dead.

---

### Post by ukripper on 2008-05-27
> **Joeb454 said:**
> Nearly *all* new users say this. But most things can be done without the use of a command line.

The fact is, it's easier to give out a command that will do it all for you, than guide people through a GUI - plus GUI's vary incredibly on Linux, so you also need to know what people are using (Gnome, KDE, XFCE, Flux etc.etc.)

+1 on that one mate!

---

### Post by hyper_ch on 2008-05-27
> **MNICY said:**
> Just copy and paste. You really cant get more user friendly then that.

They could provide a bash script so that you have to copy'n'paste only once and then run it ;)

---

### Post by vincentvee on 2008-05-27
dude, if he has other machines there and they are connected then his local network must still be there, maybe he went blind or something

> **dasunst3r said:**
> So tell us more about the things that are not working.  In particular:
[LIST]
[*]What brand and model of computer do you own?
[*]What brand and model are your sound card, printer, and network card?
[*]What makes you think your local network is gone?
[/LIST]
Also, it is important to note that in a Windows-entrenched world, the very people who wrote software for Linux really had to "try harder" to get things to work because the manufacturers refuse to help them.  The fact is: computing is still hard, even in the Windows world.  By your logic, if anybody could do something "easy," then we wouldn't have the likes of Geek Squad or Firedog charging out your nose to do what you and I may consider "easy."

---

### Post by 3rdalbum on 2008-05-27
> **Mister URL said:**
> 
I like Ubuntu, but perhaps there needs to be a bigger effort to make it user invisible. I know there is a certain satisfaction in forcing a computer to do your bidding with complex command line options. But there is a reason most of us changed away from command line OS's. They are hard to use.

Well, no. Most people switched away from the command-line because Microsoft put a GUI into their operating system to compete with Apple.

> I read most of the posts in the "Security" forum, and I find that there are only a few GUI offerings for security (firewalls, rootkit detectors, and spyware detectors).

You know what makes an operating system even more user-invisible? Not having to run maintainance on it. Firewalls are unnecessary if your router has a firewall in it, which they usually do. Rootkit detectors are completely unnecessary unless you've got ports open, and the people with ports open don't mind typing "chkrootkit" in a terminal. It's not brain surgery.

When this is taken into account, what exactly requires use of the command-line? Printers don't. If you've done the right thing and bought a wireless card that works out-of-the-box with Linux (not difficult, seriously), you can just use Network Manager. If you do something dumb to your Apt sources, then you need a command-line - but the solution is to not fiddle with your Apt sources unless you know what you're doing.

You might need to put in a small number of commands to set up incompatible hardware with your computer, but then the idea is that you buy compatible hardware to begin with. You wouldn't dream of running Vista on incompatible hardware, so why run Ubuntu on incompatible hardware? Back when Windows had as much marketshare as Linux does today, you had to be very very careful what you bought. If you didn't buy the right thing, you were stuffed. Even if you bought the right thing, you needed to use the command-line anyway.

---

### Post by zetetic on 2008-05-27
> **Mister URL said:**
> [SIZE=2]I am disappointed. When I switch to Ubuntu, I lose my printer, my local network, and my sound. I don't have time to spend days sorting out what is wrong and rounding up drivers and setting parameters. [/SIZE][SIZE=2]I have read dozens of posts here and most of what I see are problems, and often surly responses to "work harder" to get your printer, or wireless, or whatever, to work with Ubuntu[/SIZE]. [SIZE=2]Hey, if it was Easy, anyone could do it.[/SIZE]

[SIZE=2]I could learn the innards of Linux and use the command line syntax, but speaking as a common user, why should I? It's going backward, back to when you had to set up a serial port with baud rate, stop bits, and parity, and set up your config.sys and win.sys with a text editor.[/SIZE][SIZE=2]
[/SIZE][SIZE=2]
I have a working system, and I will stay with it until, inevitably, someone comes out with a real Windows competitor Linux package.[/SIZE][SIZE=2]

[/SIZE][SIZE=2]I really do appreciate the responses to my inquiry. I will be back sometime in the future. Thanks.
[/SIZE]

Point, click and grunt is the caveman way.

For the Homo Sapiens we have de language (the command line, in terms of computers).

Note: Those are not my words. Those are the words of Eben Moglen.
Eben Moglen is a professor of law and legal history at Columbia University, and is the founder, Director-Counsel and Chairman of Software Freedom Law Center, whose client list includes numerous pro bono clients, such as the Free Software Foundation.

---

### Post by 3rdalbum on 2008-05-28
> **zetetic said:**
> Point, click and grunt is the caveman way.

That's a rude, elitist comment and I don't think it has any place on Ubuntu Forums.

---

### Post by jrusso2 on 2008-05-28
> **zetetic said:**
> Point, click and grunt is the caveman way.

For the Homo Sapiens we have de language (the command line, in terms of computers).

Note: Those are not my words. Those are the words of Eben Moglen.
Eben Moglen is a professor of law and legal history at Columbia University, and is the founder, Director-Counsel and Chairman of Software Freedom Law Center, whose client list includes numerous pro bono clients, such as the Free Software Foundation.

See now you went and offended all the cavemen. :)

---

### Post by hyper_ch on 2008-05-28
> **3rdalbum said:**
> That's a rude, elitist comment and I don't think it has any place on Ubuntu Forums.

Nevertheless it holds some truth...

Same goes about text filtering... some people do it manually and others use regex...

---

### Post by mdsmedia on 2008-05-28
> **Joeb454 said:**
> Nearly *all* new users say this. But most things can be done without the use of a command line.

The fact is, it's easier to give out a command that will do it all for you, than guide people through a GUI - plus GUI's vary incredibly on Linux, so you also need to know what people are using (Gnome, KDE, XFCE, Flux etc.etc.)I only wish others would see this. I don't use the command line much, because I still don't know even the basics, but if I ask a question and someone gives me a command line solution, it's so much easier than a GUI solution.

I don't know what it is with people. Are they Windows users who want to be lost in a Windows world, where the OS does everything you think you want but not what you really want it to do?

I'm happy that I can do nearly everything I want in Linux with GUI.... because that's simple, for things that I can find in the menus, but what if I want to do something that's not in the menus? A simple CLI command does the job.

I really can't understand people wanting to do away with any part of the CLI.

---

### Post by Joeb454 on 2008-05-28
I'm glad you can understand that :D

I think a lot of people come to Ubuntu/Linux expecting it to be a Windows clone...naturally they clearly get a big surprise ;)

---

### Post by lisati on 2008-05-28
GUI or CLI? Does it matter? Surely what matters most is that we have a way of getting the job done quickly and efficiently.

I wonder how more intense these discussions would be if we had to resort to punched cards, paper tape, magnetic tape, or, horror of horrors, toggling switches on a console just to get a bootloader entered into the system!!!!!

---

### Post by mdsmedia on 2008-05-28
> **Joeb454 said:**
> I'm glad you can understand that :D

I think a lot of people come to Ubuntu/Linux expecting it to be a Windows clone...naturally they clearly get a big surprise ;)I'm a Linux newb, after using Ubuntu for 3 years as my main OS.

I'm still scratching the surface. But that's something I love about Linux. In Windows I was scratching the surface, but everywhere I turned the surface revealed mud. In Linux, everytime I learn something new it actually reveals something.

Come to Linux with an open mind. Don't expect it to be what you expect it to be. Be willing to learn something new. If you realise those things, Linux can be frustrating, but so can Windows. The difference is that Linux provides answers. Windows continues to be frustrating.

---

### Post by Joeb454 on 2008-05-28
I couldn't agree more :)

It's fun to explain to people that I haven't used Windows for a long time :) Usually it's just because "I don't particularly like it that much" "So you use Mac's?" "Noooo......"

---

