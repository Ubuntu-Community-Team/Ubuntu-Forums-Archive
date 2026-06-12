---
title: "I hate building guis'..."
date: 2010-08-14
forum: The Cafe
---

### Post by Legendary_Bibo on 2010-08-14
Yesterday I had an inkling to write a program, and it was going to be a super awesome Periodic Table to use for my chemistry class this semester. Now I could have done it in python and make things readable and dare I say pretty by just printing boxes to make a visual representation of the table. Then my friend wanted me to give him a copy. The whole use-this-in-the-DOS-command-prompt thing didn't go over so well. The script confused him (I wrote clear instructions of what to do!). I couldn't figure out to use glade. By that I mean I couldn't figure out how to make it so buttons didn't fill up the entire menu. Also I couldn't figure our if there was an event sheet like what Visual Basic has. So I started writing it in Visual Basic. I'm almost done building the gui, and then I'll finally get to program! I hate that I'll have to use it in my virtual box in order to use it unless there's some way to easily convert a VB program to a GTK, or even the gui would be fine.

On a side note: How come Wine can't run my own application written in Visual Basic?!

---

### Post by theraje on 2010-08-14
GUI programming is always a headache, indeed! It's always nice to have something like Visual Basic or Qt or wxWidgets/wxSmith to ease the pain... even then, it can still be a chore.

As for Visual Basic not running in Wine, try finding the MSVBVM60.DLL file from Microsoft. You will need this DLL to run any Visual Basic 6.0 application (assuming you're using 6.0, and not a .NET or some older version), even in Windows.

---

### Post by murderslastcrow on 2010-08-14
That's a bit odd- are you using a very recent version of VisualBasic?

There are many different tools for creating a GUI program easily for GTK, Qt, or otherwise (wxWidgets is a good one to use since it has wxPython). Qt4 has a visual IDE for putting all of it together, similar to what you may be familiar with.

I encourage you to file a bug report to Wine if possible and learn a bit more about the tools available to you for producing native GUI applications in Linux. If cross-platform compatibility is important, using something portable is a good idea.

On the other hand, you could help your friend be comfortable typing some things into a black space. Perhaps the fonts or backgrounds in Windows command prompts are groaty and discouraging?

I'm sorry that the fact that there are multiple ways to approach this in Linux is troublesome for you. I hope you find the method that works best for you. Glade/Ruby tends to be pretty popular with new devs.

---

### Post by Legendary_Bibo on 2010-08-14
> **theraje said:**
> GUI programming is always a headache, indeed! It's always nice to have something like Visual Basic or Qt or wxWidgets/wxSmith to ease the pain... even then, it can still be a chore.

As for Visual Basic not running in Wine, try finding the MSVBVM60.DLL file from Microsoft. You will need this DLL to run any Visual Basic 6.0 application (assuming you're using 6.0, and not a .NET or some older version), even in Windows.

I'm writing it in VB 2010. Will it still work?

The GUI took me freaking hours! I was then curious and looked at the code for the GUI...ehhh. If I were to handwrite it I would probably have shot myself.

---

### Post by yabbadabbadont on 2010-08-14
It will probably require that you have the .NET runtime installed in WINE.  (and I don't know if that is possible, check the WINE website)

---

### Post by Legendary_Bibo on 2010-08-14
> **murderslastcrow said:**
> That's a bit odd- are you using a very recent version of VisualBasic?

There are many different tools for creating a GUI program easily for GTK, Qt, or otherwise (wxWidgets is a good one to use since it has wxPython). Qt4 has a visual IDE for putting all of it together, similar to what you may be familiar with.

I encourage you to file a bug report to Wine if possible and learn a bit more about the tools available to you for producing native GUI applications in Linux. If cross-platform compatibility is important, using something portable is a good idea.

On the other hand, you could help your friend be comfortable typing some things into a black space. Perhaps the fonts or backgrounds in Windows command prompts are groaty and discouraging?

I'm sorry that the fact that there are multiple ways to approach this in Linux is troublesome for you. I hope you find the method that works best for you. Glade/Ruby tends to be pretty popular with new devs.

Well I'm going to learn how to use glade, and then just rebuild it from scratch. I have google, and I could build it in a day. The time consuming part is finding all the Info for the elements (atomic elements).

---

### Post by cariboo on 2010-08-14
Have a look at BoaConstructer, it's in the repositories.

---

### Post by murderslastcrow on 2010-08-15
Holy crap! I never heard of Boa Constructor. =_= ; All those wasted minutes, what a lifesaver.

---

### Post by Legendary_Bibo on 2010-08-15
Oh wait I figured out glade, at least on how to build the gui hehe. Turns out I was looking for the layout widget. Now I can lay the buttons and stuff down now. Turns out a tutorial is great place of information. Odd, I usually just figure things out on my own. Now to figure out how to set up events and what not.

---

### Post by Legendary_Bibo on 2010-08-15
> **murderslastcrow said:**
> Holy crap! I never heard of Boa Constructor. =_= ; All those wasted minutes, what a lifesaver.

It looked complicated. It didn't have a drag and drop WYSIWYG type of application editor, for that matter the buttons, and stuff wasn't doing anything for me.

---

### Post by NMFTM on 2010-08-15
> **murderslastcrow said:**
> On the other hand, you could help your friend be comfortable typing some things into a black space. Perhaps the fonts or backgrounds in Windows command prompts are groaty and discouraging?
If my only experience with the command line was cmd.exe I'd hate using it as well. Nothing is color coded and you can't even copy/cut text to and from it. Bash is much more advanced.

---

### Post by schauerlich on 2010-08-15
[But, can you track the bad guy's IP address?](http://www.youtube.com/watch?v=hkDD03yeLnU)

---

### Post by Paqman on 2010-08-15
Quickly is pretty good for building GUI Python apps, it's in the repos.

---

### Post by Legendary_Bibo on 2010-08-15
> **schauerlich said:**
> [But, can you track the bad guy's IP address?]("http://www.youtube.com/watch?v=hkDD03yeLnU")

:lolflag:

---

### Post by Legendary_Bibo on 2010-08-15
I'll try Quickly. I liked Glade for its drag and droppiness, but I didn't like how you had to write the code separately and then compile them together. There was no preview mode like what you get with VB.

I'll probably just write everything in a Python script as well, I can just copy the VB code, and use emacs to replace the syntax pieces.

---

### Post by fatality_uk on 2010-08-15
If you are writing a gui, there are MUCH better options all in the repos:

GAMBAS - Is an excelent VB "clone" very little difference in the langauage format. You could pick it up in a matter of minutes. Needs run times like VB

Lazarus (What I use for Linux/Cross platform development) based on Pascal. Compiles native apps without the need for run times.

cariboo907 is also correct with BoaConstructor.

---

### Post by Legendary_Bibo on 2010-08-15
> **fatality_uk said:**
> If you are writing a gui, there are MUCH better options all in the repos:

GAMBAS - Is an excelent VB "clone" very little difference in the langauage format. You could pick it up in a matter of minutes. Needs run times like VB

Lazarus (What I use for Linux/Cross platform development) based on Pascal. Compiles native apps without the need for run times.

cariboo907 is also correct with BoaConstructor.

You sir have made me very happy! Gambas is awesome!!

---

### Post by Nick_Jinn on 2010-08-15
I had an idea to make a generic GUI, one that could be customized by its own GUI. You simply ascribe values and commands to various buttons with add-ons for advanced scripting, drag and drop search bars and other modules and gadgets and tell them what to do, using a basic toolkit to tell them how to interact.....this of course would be an expansion of a 'command keyring' that allows you to store common commands on a list and you point and click on them instead of type them out....that evolved into the idea of using those saved commands for a customizable GUI.


Then ANYBODY could spit out professional looking GUI apps if you can think of a single command...You could make a GUI that installs a certain program by dragging and dropping a button, right click and a menu pops up, click command and inside the box that opens type in Apt-get whatever, or aptitude install whatever....You now have a button that installs a program. Not a very useful app, but a really basic example.


It would be a huge boon for app development if somebody were to make something like that. I would do it myself if I had the skills.

---

### Post by fatality_uk on 2010-08-15
> **Legendary_Bibo said:**
> You sir have made me very happy! Gambas is awesome!!

You're welcome :)

---

### Post by Åtta on 2010-08-15
> **Nick_Jinn said:**
> I had an idea [...]
That's exactly what Glade and other visual interface builders do. You place your widgets where you want them, set up signals, have your app parse the XML to draw the UI, and then create callbacks that are run whenever the signals are received. That's exactly what you're talking about.

---

### Post by Nick_Jinn on 2010-08-15
Cool. It must have been a good idea then.

Does it have easy drag and drop functionality and right-click menu methods of assigning values though?

---

### Post by schauerlich on 2010-08-15
> **Nick_Jinn said:**
> Cool. It must have been a good idea then.

Does it have easy drag and drop functionality and right-click menu methods of assigning values though?

The example you gave can easily be done with zenity.

A ten second adaption of the example from [wikipedia](http://en.wikipedia.org/wiki/Zenity)

```
#!/bin/bash
 
if zenity --question --text="Install (some package)?."; then
    gksudo apt-get install (some package)
    zenity --info --text="Hooray\!"
else
    zenity --error --text="Well\, fine then\."
fi
```

---

### Post by Legendary_Bibo on 2010-08-15
> **Åtta said:**
> That's exactly what Glade and other visual interface builders do. You place your widgets where you want them, set up signals, have your app parse the XML to draw the UI, and then create callbacks that are run whenever the signals are received. That's exactly what you're talking about.

Can you imagine being able to make all your guis dynamic in that you can move any element to wherever you want to? That would be hard I'm guessing.

---

### Post by murderslastcrow on 2010-08-15
What I think would be very interesting is to find what people typically code and write those into visual, plain English, in a mouse-oriented interface. It might take people way longer to program, but it also means total noobs could grasp the basics of programming without learning a real language. The application would become their language.

While we have programs that help to create interfaces, we don't seem to have many that make all of the code visual and obscure the programming language. Perhaps because showing the language is beneficial, and not very painful with things like Python, but it may also be because we don't want noobs writing crappy programs.

However, I think in the near future we may have something that makes creating a program so natural and light that we forget the language.

I mean, there is so much versatility in writing the code yourself, and there isn't just one set of actions a developer may want. But what if we made it more visual, and let you control the process with your voice and your hands? What if we developed some way to code that just blew away the conventions we use today?

Where coding could be so convenient you could take it with you and do it on your phone, even?

Lol, enough speculation, I think we have a pretty sweet deal as it is.

---

### Post by Mr. Picklesworth on 2010-08-15
> **Legendary_Bibo said:**
> Oh wait I figured out glade, at least on how to build the gui hehe. Turns out I was looking for the layout widget. Now I can lay the buttons and stuff down now. Turns out a tutorial is great place of information. Odd, I usually just figure things out on my own. Now to figure out how to set up events and what not.

I complain about it, but GTK is a really excellent UI toolkit. Glade is trickier than VB's GUI builder, but it is also much more powerful. The UI you put together will be very scalable and, just as importantly, *accessible*. For example, anyone can use whatever font sizes or themes they want. If you want your main window to be resizable, you can do that and the widgets you have added will do the right thing. Supporting keyboard shortcuts (like the underlined letters when you hold Alt, or menu accelerators) is also incredibly easy, because it's all handled within GTK.

Follow some tutorials, get to know the tools, and you won't regret it!

---

### Post by Legendary_Bibo on 2010-08-15
> **murderslastcrow said:**
> What I think would be very interesting is to find what people typically code and write those into visual, plain English, in a mouse-oriented interface. It might take people way longer to program, but it also means total noobs could grasp the basics of programming without learning a real language. The application would become their language.

While we have programs that help to create interfaces, we don't seem to have many that make all of the code visual and obscure the programming language. Perhaps because showing the language is beneficial, and not very painful with things like Python, but it may also be because we don't want noobs writing crappy programs.

However, I think in the near future we may have something that makes creating a program so natural and light that we forget the language.

I mean, there is so much versatility in writing the code yourself, and there isn't just one set of actions a developer may want. But what if we made it more visual, and let you control the process with your voice and your hands? What if we developed some way to code that just blew away the conventions we use today?

Where coding could be so convenient you could take it with you and do it on your phone, even?

Lol, enough speculation, I think we have a pretty sweet deal as it is.

I was actually thinking about that the other day. What if we built a set of rules layered on top of programming languages? So let's say you write in plain english "When I click this make the value in the first text box equal this variable and then...". When you go to compile it your computer runs through your sentences and analyzes it for words that match up to certain syntax, coverts certain declared instances to labels or properties, or events. It can even understand if you're using synonyms. It would also need a database for what commands certain words would equal. Programming languages are evolving actually so it might not be speculation. The languages they had back in the 60s and 70s far more complicated in their syntax then languages we have now like Python, Visual Basic/.NET, C, C#, Perl, Ruby, Java, etc.

IIRC a lot of the easier to use modern programming languages today are built/layered on top of older languages with some modifications.

---

### Post by Mr. Picklesworth on 2010-08-15
> **Legendary_Bibo said:**
> I was actually thinking about that the other day. What if we built a set of rules layered on top of programming languages? So let's say you write in plain english "When I click this make the value in the first text box equal this variable and then...". When you go to compile it your computer runs through your sentences and analyzes it for words that match up to certain syntax, coverts certain declared instances to labels or properties, or events. It can even understand if you're using synonyms. It would also need a database for what commands certain words would equal. Programming languages are evolving actually so it might not be speculation. The languages they had back in the 60s and 70s far more complicated in their syntax then languages we have now like Python, Visual Basic/.NET, C, C#, Perl, Ruby, Java, etc.

IIRC a lot of the easier to use modern programming languages today are built/layered on top of older languages with some modifications.

Done!
[http://inform7.com/](http://inform7.com/)

(And interactive fiction is awesome, too)

---

### Post by murderslastcrow on 2010-08-15
Interesting. Well, just think how horrible debugging would get when you say something you didn't mean. Seriously, using Python might be a lot easier in the long run. XD

---

### Post by linux18 on 2010-08-15
> **schauerlich said:**
> [But, can you track the bad guy's IP address?](http://www.youtube.com/watch?v=hkDD03yeLnU)
LOL! movies and TV shows have no idea what real programming is, nor do they know linux, command lines, the difference between hacking and cracking.

---

### Post by Legendary_Bibo on 2010-08-15
> **murderslastcrow said:**
> Interesting. Well, just think how horrible debugging would get when you say something you didn't mean. Seriously, using Python might be a lot easier in the long run. XD

True, I've grown fond of python. It's easier on the eyes to read through, but I don't quite understand how to build a gui that uses it. I just haven't found anything that matches Visual Basic IDE with Python in terms of easiness. If someone took Gambas and could get it to use Python then I would be in heaven.

I like python for a script language. I make a bunch of applications for stuff I do in science classes that involve a lot of number crunching that I find it's easier to just write a menu that says push this number to do this thing. I actually could have cut out a lot of time by not building a gui for my periodic table program, but I had to consider that my friend wanted to use it, and so I had to use visual basic because I know how to use it, and he would probably have an aneurysm if he had to run a program in the DOS command line and install python. Luckily I have Gambas now, which is great when I need to make a simple application that my friend won't need. I do need to learn GTK though so I can just cut out having to do things for one side or the other, or redoing some things just so it works for all.

---

### Post by Legendary_Bibo on 2010-08-15
AAAGGGHHHH!!! Some people need to keep their mouths shut!

My other friend decided to inform people of my skills and upon going to my facebook messages I had acquired 3 requests for applications to "help" them with their schoolwork. One was a request for the Periodic Table, okay that's fair I don't mind sharing that since how I'm already making it. Another was one for physics, okay not an issue, I'm taking physics, I guess I could use it, and it would help, so we'll throw this in the maybe pile. The third one was an application that the way she described it sounded like she wanted some sort of database for history complete with a timeline and other crap. I start school in a week and figured I could get my periodic table done in a few days and then work on the calculator portion after school has started. I kindly informed her of this site called Wikipedia unless she wanted to pay me a fair estimated price of $20,000 to build her such an advanced and time consuming application.

---

### Post by schauerlich on 2010-08-16
> **murderslastcrow said:**
> What I think would be very interesting is to find what people typically code and write those into visual, plain English, in a mouse-oriented interface. It might take people way longer to program, but it also means total noobs could grasp the basics of programming without learning a real language. The application would become their language.

While we have programs that help to create interfaces, we don't seem to have many that make all of the code visual and obscure the programming language. Perhaps because showing the language is beneficial, and not very painful with things like Python, but it may also be because we don't want noobs writing crappy programs.

However, I think in the near future we may have something that makes creating a program so natural and light that we forget the language.

I mean, there is so much versatility in writing the code yourself, and there isn't just one set of actions a developer may want. But what if we made it more visual, and let you control the process with your voice and your hands? What if we developed some way to code that just blew away the conventions we use today?

Where coding could be so convenient you could take it with you and do it on your phone, even?

Lol, enough speculation, I think we have a pretty sweet deal as it is.

[http://en.wikipedia.org/wiki/Visual_programming_language](http://en.wikipedia.org/wiki/Visual_programming_language)

---

### Post by Nick_Jinn on 2010-08-16
> **schauerlich said:**
> [http://en.wikipedia.org/wiki/Visual_programming_language](http://en.wikipedia.org/wiki/Visual_programming_language)


Thats a start. The next step would be to write a linux app using it so that its attached to a GUI that makes GUIs.....as is, noobs are not going to know how to download that language and use it to create apps.....I dont know how to do that.

---

### Post by Nick_Jinn on 2010-08-16
Id be interested in checking out your periodic table app.

You should start charging people to make apps.

---

### Post by Legendary_Bibo on 2010-08-16
> **Nick_Jinn said:**
> Id be interested in checking out your periodic table app.

You should start charging people to make apps.

I'm building it in Visual Basic as a Windows application. I could easily convert it to Linux using Gambas. Do people need to download gambas to use use gambas programs? For instance, when I make a program in gambas it's given the name *someapplication*.gambas
Will people be able to use it without installing Gambas2 from the repositories?

I'm doing the really unfun part and that's getting all the information for the elements as well as building a unit converter (e.g. moles to grams and vice-versa). Lots of tedious coding. I just can't wait to finish it. It'll be a great feeling to step back and look at such an awesomely helpful program I've accomplished.

---

### Post by fatality_uk on 2010-08-17
I think you need runtime libs (Similar to VB) I used it a while ago and had to install this to run it on another machine. I now use Lazarus which doesn't ned these.

---

### Post by Legendary_Bibo on 2010-08-17
> **fatality_uk said:**
> I think you need runtime libs (Similar to VB) I used it a while ago and had to install this to run it on another machine. I now use Lazarus which doesn't ned these.

Ah that's probably what it does when it packages it as a .deb.

---

