---
title: "tips from a newbie for newbies"
date: 2008-11-10
forum: The Cafe
---

### Post by irish66 on 2008-11-10
okay, just been using ubuntu for a short period, so more experienced users, please tell me where I'm wrong, or add in stuff
Hi, I had much more detail before, but firefox crashed, so talking like james ellroy writes.
1. many programs in synaptic (what an awkward word).SYn for short from now on
go to system/administration./SYN.
green boxes beside program means program already installed.
don't know what other symbols mean
to run program installed .click applications on top, then look for program.
if not there open terminal, click applications/accesserories/terminal.
type program name. shutting down terminal also shuts down program.
if can't run program either way.sorry don't know what you do.
for programs that run in terminal, best to add to appplications.
right click icon beside applications, choose edit menus, type in name of program. if program runs from terminal. YOU SHOULD be able to get it run in  applications by just typing whatever name you like in name box and actual name of program in command box. No need to search for executible file.

NOTE. you don't have to install one prog at a time from syn, but once programs installed, syn closes, or at least goes back to top of screen, so take note of last program installed, go back there by dragging slider, or type in first few letters of program, then when get to program title, hit esc.
M

---

### Post by starcannon on 2008-11-10
If you need to run an application that is for whatever reason not showing up in the menu, you may do so without having a terminal open by using Alt+F2.

If you would like to use the terminal to open an application and then have the option of using the same terminal to run other commands or you would like the option to close the terminal without closing the program then include an & after the command. We'll use gedit for an example (though its in the menu as text editor in appications>accessories>text editor).
```

gedit &

```Now you see that you get the cursor again, this will allow you to run other commands from the same terminal, or to close the terminal without closing the program; however, if you close the terminal using the [x] in the upper right hand corner it will take the program with it; so, instead to gracefully exit the terminal without killing the progam you type "exit"
```

exit

```Taaaa Daaa nice eh?
Okay, Okay heres another useful terminal trick for you to play with. Lets say you want to run 2 commands consecutively in the same terminal in one command; we'll use gedit and gcalctool (the calculator).
```

gedit & gcalctool &

```Alright one more trick, lets say you want to run one application, then when it has been closed you want to run another application, and you want to do it with one command line; easy peasy lemon squeezy just use &&.
```

gedit && gcalctool &

```
Okay so the text editor came up but wheres the calculator? AHA! when you closed gedit pop! up comes the calculator!
Anyway enjoy theres a whole wide world of commands and bash scripting out there, and in this conversation we haven't even scratched the surface.
GL and have fun

---

### Post by irish66 on 2008-11-10
nice, thanks for the tips.
m

---

### Post by Chris Edgell on 2008-11-10
The synaptic site was brought up earlier today in response to mlotfi asking Where to learn Linux commands.  I had thought about mentioning it to him but realized I really knew next to nothing about it.  At that time I went and clicked around to see what I could see.  

So I was pleasantly surprised to see what was looking to be a definitive view.  Imagine my disappointment that you began to write like James Ellroy.

I followed the first couple of sentences because you were saying something I knew.  But then you said something I didn't know....eh, and I still didn't know it.  Which is to say, I missed the extra words that would have supplied the meaning to the newbie who doesn't know.

You began with point one, so I guess I'm quoting (copying) point five:   to run program installed .click applications on top, then look for program.

See how you lost me?  I liked what you tried to do but when you sped things up because your firefox had failed you once, your brevity due to frustration, caused your excellent endeavor to cloud.

That response to your post by Starcannon is one I'll save until I know better what I'm doing, well, I'll be saving them both. I thank you both.

---

### Post by irish66 on 2008-11-10
bed now, will try to do out info more clearly at a later date.

---

### Post by DougieFresh4U on 2008-11-11
Does the 
```
**nohup 'program'**
```
command still work for making program run from terminal and not closing when terminal is closed?

---

### Post by Simey on 2008-11-11
Here's a translation that I have attempted, with some additions;

1 - Many useful programs can be found in a program named Synaptic, this program is essentially a less graphical but more featureful equivalent to Add/Remove. Synaptic may be found by using the menus; 
System >> Administration >> Synaptic Package Manager
Simply use the search functions within the program to find whatever you are looking for. 
If a package (All programs and libraries are contained within 'packages') has a green box next to it, that means it is installed, most other symbols will become apparent as you use the program. Be sure to click the 'Apply' button after you have selected the desired changes, otherwise the changes will not be made.
As a general rule, allow synaptic to install all dependencies it requests.

2 - When you have installed a new application it can often be hard to find it in the menus. Sometimes a program may create an entry in the Applications menu, sometimes in the Preferences or Administration menus depending on how it is intended to be used. Sometimes it will not create menu item at all.

Alternatively, use Alt-F2 to bring up the application launcher and start typing the name of the program. The application launcher will attempt to auto-fill in the rest of the program's name for you, this can be helpful with programs with longer names. 

Another method, and one that must be used for applications without graphical interfaces is to use the terminal, simply type the name of the program into the terminal. The terminal is usually found under;
Applications >> Accessories >> Terminal
Command line only programs often require arguments to be used when the application is run, but that is probably a topic for somewhere else. Generally, while an application is running, the terminal that it was launched from is tied to the program and if the terminal is closed the program will be closed also.

3 - If you can run a program using the application launcher or terminal but it is not in the menus, you may add it yourself. There is a graphical editor for doing this;
System >> Preferences >> Main Menu
Alternatively, you may right-click on the 'Applications' word in the top left and select 'Edit Menus'.
Simply add a new item wherever you would like it, input the exact command used to run the program into the command box for the new item and give the application a name by which you will recognise it by. Within a few seconds of closing the dialogue box the application should appear within the menus. 

Please feel free to butcher this, use whatever you want in the OP, Irish, it's more use at the start than lost in the middle. :)

Oh, another thing that newbies might like to know. The vanilla Ubuntu's file browser's program name is 'Nautilus' - not very intuitive.

---

### Post by jespdj on 2008-11-11
> **DougieFresh4U said:**
> Does the 
```
**nohup 'program'**
```
command still work for making program run from terminal and not closing when terminal is closed?
Why don't you try it out yourself?

Answer: Yes, it 'still' works. Why would it not work anymore?

---

### Post by irish66 on 2008-11-11
Thanks folks.
Things any clearer at your end, Chris
M

---

### Post by billgoldberg on 2008-11-11
> **DougieFresh4U said:**
> Does the 
```
**nohup 'program'**
```
command still work for making program run from terminal and not closing when terminal is closed?

Yes it does.

---

### Post by billgoldberg on 2008-11-11
Someone should really write a Absolute beginners guide to using 
Ubuntu for people totally new to Ubuntu.

I'll get started and post it here to ask for tips to improve it.

---

