---
title: "LibreOffice Impress general quality"
date: 2019-05-04
forum: Ubuntu, Linux and OS Chat
---

### Post by pi-no on 2019-05-04
Hi.

I have to use a (Libre)Office tool two or three times a year, and this time it was Impress. My expectations regarding LO generally aren't high, but this time it was really a nightmare. Is this (below) a typical LO Impress user experience? Or is the LO version coming with Kubuntu 19.04 broken in some regard? Or did something went wrong with the integration into the distribution? Can you reproduce those issues? I haven't collected an exhaustive list of issues; just virtually everything I touched for my simple handful of slides was broken in some ways...


[LIST]
[*]clipboard
[LIST]
[*]sometimes ignores 'copy' 
[*]sometimes randomly duplicates some slides when it should just copy&paste some objects (happened often, even when tried via the menu) 
[*]z-axis arrangement of objects sometimes break (when copying&pasting many objects or entire slides) 
[*]sometimes (also when copying many things) the program state is broken, LO reacts weird, and eventually crashes 
[/LIST]
  
[*]interface is just fuzzy (as it always was)
[LIST]
[*]lots of (rather common) dialogs obviously were designed three decades ago 
[*]dynamically appearing toolbars let the viewport jump around when you select objects 
[*]check and radio symbols in popup menus are cropped (not in main menu) 
[*]gallery (clipart) in sidebar: how to add some to the slide? no 'insert' button, dnd seems to work at first, but does nothing, doubleclick just shows it larger, only the context menu helps 
[*]slides sidebar sometimes invisible after startup, then appearing when you scroll in the slide itself 
[*]there are tons of minor glitches, not possible/worth to list them; also logical/structural weaknesses 
[/LIST]
  
[*]'slides' sidebar (left)
[LIST]
[*]often ignores clicks (tooltip just appearing in between?!) 
[*]sometimes start dnd operations when just the scroll bar was used 
[*]dnd move operations virtually never work: sometimes just deletes slide, often get ignored, often move the slides to the beginning instead of the chosen position 
[*]the visual dnd indicator only appears if you leave the sidebar with the cursor for a moment 
[*]at some moment, i had slide 1 two times (two different slides, but labeled as no. 1 in sidebar) 
[/LIST]
  
[*]sidebar on the right
[LIST]
[*]some gaps aren't repainted reliably, occassionally leaving old window content in some 1-or-2-pixel height bars 
[*]just make a _click_ at some bad places (or in bad moments?!) lets you accidentially undock the sidebar; re-docking it was not possible at first, neither by 'dnd', nor by the menu action 'Dock'; only after restarting LO at least the menu option let me re-dock it 
[/LIST]
  
[*]freeze/crash every 5-20 min (after some time you learn what you should avoid) 
[*]elements disappear completely sometimes when just clicked on for selecting 
[*]slide show
[LIST]
[*]starts in a broken intermediate state with a black ghost window, then a key press is needed for starting 
[*]also ends in a broken intermediate state, with a black un-closable ghost window 
[/LIST]
  
[*]document recovery (on startup after crash)
[LIST]
[*]clicking 'Discard' lets it just crash again, leading to a loop 
[*]accepting it lets it recover the files in background, then opens just empty windows in foreground, not filling them with life until you click on 'Finish' in the then-background recover dialog 
[/LIST]
  
[*]changing colors of text blocks doesn't recolour enum bullets 
[*]copied text blocks (in other slides) vary slightly in rendering, though they should be perfect clones: one or two pixels off, either completely, or starting somewhere within the text
[LIST]
[*]even in the exported pdf 
[*]reloading the file helps for a moment (also regarding the pdf export) 
[/LIST]
  
[*]the 'unsaved changes' flag pops up in many situations you actually haven't touched anything, but e.g. just cancelled an erroneously started dnd operation, or just _clicked_ on something in a bad moment 
[*]falls into an endless 'insert text' mode sometimes, where each click creates a new empty text field somewhere, until you find the way out 
[*]sometimes the interface begins to ignore clicks and/or keyboard, or doesn't show a text cursor anymore
[LIST]
[*]loading the file again, or jumping a bit around helps 
[/LIST]
  
[*]clone formatting: beginning the target selection in some 'forbidden areas' (e.g. all whitespaces?!) applies the format (well, or actually something different) to the complete text block 
[*]image "edit with external tool": results in a broken blank object just showing a generic image placeholder icon 
[/LIST]


btw: Kubuntu 19.04, rather default, no experiments in system or desktop configuration, no issues in other tools (well, Gimp was also more stable in the past, but that's another story), tried on two different machines.


Greetings

pino

---

### Post by DuckHook on 2019-05-04
I don't want this to sound flippant, but perhaps LO is simply the wrong suite for you. I rarely use Impress, but consider myself a word-processor power user and am *very* happy with LO's Writer app. Libre Calc has also been great.

There's nothing wrong with running Windows and using Powerpoint. If that's what works for you, use it instead.

The LO devs do not frequent this site. A better place for your litany of woes would be LibreOffice's:

[LIST]
[*][IRC Channel]("https://irc.documentfoundation.org")
[*][Mailing Lists]("https://www.libreoffice.org/get-help/mailing-lists")
[/LIST]
Their developers do hang out around the mailing lists in particular, if you subscribe to the right one.

A final few thoughts:

You are new around here, so welcome. Perhaps you are unfamiliar with FOSS. Since you have no history with us, there's no way to tell.

The FOSS world started out as—and very much remains—a self-help one. We have an itch, we scratch it. The tool we invent to scratch that itch is generously contributed for free to the larger community, but it comes with no warranty—neither expressed nor implied—no promises, no expectations. If that tool generates sufficient interest, like-minded people join the cause and make it even better. It is always a work in progress and always in beta. Since you pay nothing for it, it's value to cost ratio is phenomenal, but it is also unrealistic and, well, somewhat surly and presumptuous to make demands of something that one paid nothing for, no?

You took the time to write a long piece. I assume this means that you are interested enough to invest the effort. Consider making yourself part of the solution by joining LO and becoming a tester or QA contributor or a document writer/translator. If you can code, so much the better. It survives and improves purely as a community effort.

However, be careful not to wear out your welcome. Lobbing peanut shells from the gallery does no more to improve anything over there than it does over here, on an unrelated forum whose members can't do anything about your laundry list even if we wanted to.

---

### Post by Claus7 on 2019-05-06
Hello,

you list a lot of issues. It seems to me that there is something wrong with your configuration (e.g. double slides, ghosts, e.t.c.). I have not faced such issues in a long list of different LO versions. Slide shows are accurate and if a crush occurs (very rarely) there is always the ability to retrieve and save the recovered file.

Maybe opening LO from command line might unveil some issues that need to get fixed: libreoffice --impress

My version is 6.2.2, yet under gnome. Also you have the ability to use the new tabbed-ribbon interface:
[https://www.omgubuntu.co.uk/2019/02/libreoffice-6-2-features](https://www.omgubuntu.co.uk/2019/02/libreoffice-6-2-features)

Regards!

---

### Post by pi-no on 2019-05-07
Hello.

@Claus7: These issues exist. It's just that you maybe haven't encountered them yet. But, hey, I list them in detail... Give it a try. And don't dance too long around one particular item (e.g. if I mention it happened _once_, it's no big surprise that you can't reproduce it by three mouse clicks).

@DuckHook: Thank you for your friendly and constructive answer. Anyway, I don't think I will install Windows and Powerpoint for that. I use FOSS only (but maybe a GPU driver) since around the beginning of the century. And yes, LO is the wrong suite for me. Because it's buggy as hell. I gave you a list (you called it "litany"). Give it a try. I'm sure you would be able to reproduce every single issue, if you want. It's not wrongly configured on both of my machines, and I'm not too stupid for selecting objects by mouse (though obviously LO is too stupid for dealing with it reliably without deleting the object sporadically).

I don't want to address the LO devs with my post. They will ignore it anyways. I hoped that at least you can tell me something about the background of this decay (I used it rarely, but I haven't used Impress for the first time, and the last time it hasn't permanently removed my objects on clicking - but hey, just a rather cosmetic regression, yeah)...

---

### Post by Claus7 on 2019-05-08
Hello,

> **pi-no said:**
> Hello.

@Claus7: These issues exist. It's just that you maybe haven't encountered them yet. But, hey, I list them in detail... Give it a try. And don't dance too long around one particular item (e.g. if I mention it happened _once_, it's no big surprise that you can't reproduce it by three mouse clicks).

I do not disagree, yet it seems to me that there might be something wrong with the version you are using. If you have the latest version you will be able to notice differences in the appeal of the program compared to the previous ones, offering more alternatives. If that is to your liking then this is another matter altogether. 

As you noticed, I mentioned different LO versions, so I'm not talking about a few clicks, yet not a tone as well, since other users might use the program much more than myself including you.

From your initial questions you mention if LO is broken in kubuntu. That's why I prompted you to use terminal. From there you might get some more information about your issues, while you are using the program. "Ghost" problems sound like a graphics card problem, yet I might be wrong. I think that this is an easy way for you to start checking, since you like to use open source software for your tasks. Of course, not facing such graphics issues from other applications, this limits the problem to LO itself, yet you could give it a try.

Lastly, I would like to inform you that some conflicts in the installation, posed issues to users independent of the application used. Maybe reinstalling might be a very simple solution to the issues you are facing. I focused on interface issues mostly, since i)these are mentioned very often from your original post ii) they sound like graphics related issues to to me.

If LO is not to your liking then maybe this link which provides alternatives will be useful:
[https://www.ubuntupit.com/top-10-best-free-office-suite-software-as-ms-office-alternative-for-linux/](https://www.ubuntupit.com/top-10-best-free-office-suite-software-as-ms-office-alternative-for-linux/)
[https://www.slant.co/topics/739/~best-office-suites-for-linux](https://www.slant.co/topics/739/~best-office-suites-for-linux)

Regards!

---

### Post by mastablasta on 2019-05-08
> **pi-no said:**
> 

@DuckHook: Thank you for your friendly and constructive answer. Anyway, I don't think I will install Windows and Powerpoint for that. I use FOSS only (but maybe a GPU driver) since around the beginning of the century. And yes, LO is the wrong suite for me. Because it's buggy as hell. I gave you a list (you called it "litany"). Give it a try. I'm sure you would be able to reproduce every single issue, if you want. It's not wrongly configured on both of my machines, and I'm not too stupid for selecting objects by mouse (though obviously LO is too stupid for dealing with it reliably without deleting the object sporadically).

I don't want to address the LO devs with my post. They will ignore it anyways. I hoped that at least you can tell me something about the background of this decay (I used it rarely, but I haven't used Impress for the first time, and the last time it hasn't permanently removed my objects on clicking - but hey, just a rather cosmetic regression, yeah)...

i would file a bug report at LO. they will resolve it. it might take a while but they will. filed one back in 2017, others joined in and it was fixed at the end of previous year.

yes impress is rather unreliable. i too had a few issues when i tried it. can't remember what they were since it has been a while since i used it. i remember basic functions worked but more advanced ones were overly complicated.

---

### Post by pi-no on 2019-05-08
Hi.

I really hope something is wrong with the version I'm using. This was explicit part of my question. But it's the version which comes with kubuntu 19.04, so nothing exotic. My workstations config's aren't exotic either.

> **Claus7 said:**
> If you have the latest version you will be able to notice differences in the appeal of the program compared to the previous ones, offering more alternatives. If that is to your liking then this is another matter altogether. 

I do use this piece of software since old staroffice times. I don't know precisely what you mean, though. It offers more alternatives in which regard since which versions?

> **Claus7 said:**
> 
As you noticed, I mentioned different LO versions, so I'm not talking about a few clicks, yet not a tone as well, since other users might use the program much more than myself including you.


It was more a general note. I posted about my perspective on LO in the past in other forums, and a typical answer is like "oh, here it works, you're an idiot who doesn't know how to use office tools". Another typical answer (also around all kinds of KDE issues) is: "that's probably a GPU issue!". Sometimes it feels like people want to see GPU issues everywhere. I don't point particularly to you, sry. ;) Though, in my original issue list, only a very few ones can remotely be read as GPU issue. The "ghost window" thing, yes, maybe... Though currently no closed source GPU driver is installed... It runs what Canonical defined as the default. The other issues are imho really behavior things and nothing which can happen on graphics layer level, or what do you think? How should the GPU driver e.g. remove slides when I drag-and-drop them in a 'wrong' way? Btw: On terminal, it doesn't output anything. I also haven't found a 'verbose' switch. Maybe I missed something?!

> **Claus7 said:**
> 
If LO is not to your liking then maybe this link which provides alternatives will be useful:
[https://www.ubuntupit.com/top-10-best-free-office-suite-software-as-ms-office-alternative-for-linux/](https://www.ubuntupit.com/top-10-best-free-office-suite-software-as-ms-office-alternative-for-linux/)
[https://www.slant.co/topics/739/~best-office-suites-for-linux](https://www.slant.co/topics/739/~best-office-suites-for-linux)


Thank you, I'll check that deeper later on. But I'm really wondering what can be wrong with my systems? The issues weren't reproducible on my corporate pc on windows. In the version shipped with kubuntu 19.04 "running" here, I could constantly continue that list after more time... Since I need office tools only once in some month, I'm now too lazy to set up an isolated environment for checking different versions (just for encountering GPU issues then due to the isolation/VM/... ^^).


Greetings
pino

---

### Post by Claus7 on 2019-05-09
Hello,> **pi-no said:**
> 

I really hope something is wrong with the version I'm using. This was explicit part of my question. But it's the version which comes with kubuntu 19.04, so nothing exotic. My workstations config's aren't exotic either.

from here 
[https://wiki.ubuntu.com/DiscoDingo/ReleaseNotes/Kubuntu](https://wiki.ubuntu.com/DiscoDingo/ReleaseNotes/Kubuntu)
this is the version of kubuntu, so both at the time are using versions 6.2.2. I suppose that this is the version you have and not one that comes from another, maybe older, installation that was not replaced during an upgrade. So I think that for the version we are on the same page. If not, just in case, someone can check from Help->About Libreoffice.

> **pi-no said:**
> 
I do use this piece of software since old staroffice times. I don't know precisely what you mean, though. It offers more alternatives in which regard since which versions? 

I'm talking about the newest versions of LO from version 6.2 at least and on. 5.x versions improved the interface a lot, yet the 6.x are even more improved with regards to polishing. Also something that I have noticed is the compatibility with commercial software like ms office. It is not by any means perfect, you should be aware, yet with previous versions the difference e.g. in format was vast. The format, if not the same or almost identical, needs a few tweaks here and there: some figures in writer need change of place, some arrows in slideshows in impress at the wrong position, yet in general, the whole picture remains the same, at least in the situations I was able to come across. Things can change however either for the better or the worse, since both versions do not remain the same, with usually added features.
One thing that I recall about LO calc was that if you wanted you could select many different cells for different scenarios, whereas in ms office for example the selected cells were limited to the number of 15 if I recall correctly, as a result the scenario was made useless since ms office did not recognize the bigger number of cells.  

Here you will be able to see a video about the new features of LO.
[https://www.omgubuntu.co.uk/2019/02/libreoffice-6-2-features](https://www.omgubuntu.co.uk/2019/02/libreoffice-6-2-features)

Among others you can come across the Ribbon like interface (or Notebook or whatever is called), which is an interface that most users seem to be more familiar with. I do not know yet whether I prefer it more or not. For example in high resolution screens all options are available at once, whereas in lower resolution screens there is an extra space with a right arrow, which brings the rest of the options available as well. The interface is smooth, yet I do not know if I will get used to it. At least it is a nice addition.

> **pi-no said:**
> 
It was more a general note. I posted about my perspective on LO in the past in other forums, and a typical answer is like "oh, here it works, you're an idiot who doesn't know how to use office tools". Another typical answer (also around all kinds of KDE issues) is: "that's probably a GPU issue!". Sometimes it feels like people want to see GPU issues everywhere. I don't point particularly to you, sry. ;) Though, in my original issue list, only a very few ones can remotely be read as GPU issue. The "ghost window" thing, yes, maybe... Though currently no closed source GPU driver is installed... It runs what Canonical defined as the default. The other issues are imho really behavior things and nothing which can happen on graphics layer level, or what do you think? 

I cannot tell for sure... I didn't know about the responses you got either, so there was no intention from me to point in the wrong direction either for solving the issues you are facing or behavior like. Some days ago some problems with LO were posted from a user and most of LO was unusable to that user. It was verified that something else was causing the issues and not LO itself.

> **pi-no said:**
> 
How should the GPU driver e.g. remove slides when I drag-and-drop them in a 'wrong' way? Btw: On terminal, it doesn't output anything. I also haven't found a 'verbose' switch. Maybe I missed something?!

This makes things harder. I hoped that since you are facing freezes often, if launching LO from terminal you could be able to see a message when weird things happened to your screen. This is not just for LO, yet a general way of identifying things that are going wrong one way or another. For LO specifically, you could use the command:
libreoffice --impress --backtrace

this will create a log file under your home folder, which can be more verbose while using LO.

In addition you could check system logs at the time of freezing. Depending of the sessions of ubuntu you are using the access to log files depends on that. For kubuntu I came across this one:
[https://kde.org/applications/system/ksystemlog/](https://kde.org/applications/system/ksystemlog/)

One more thing: have you checked memory usage of your system while using LO? There might be a memory leak that can cause these issues as well.

> **pi-no said:**
> 
Thank you, I'll check that deeper later on. But I'm really wondering what can be wrong with my systems? The issues weren't reproducible on my corporate pc on windows. In the version shipped with kubuntu 19.04 "running" here, I could constantly continue that list after more time... Since I need office tools only once in some month, I'm now too lazy to set up an isolated environment for checking different versions (just for encountering GPU issues then due to the isolation/VM/... ^^).

Whatever it might be I hope that you will be able to solve the issue, since as you mention, is a hassle to set up an isolated environment just for that. I do not know if launchpad will be of any help. If your system is new enough, maybe the very latest stable versions of LO might be more compatible to your machine. Either way, newest versions might be more ideal for your configuration. You could give them a try by using this ppa with these commands:

sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update

The latest stable version at the time of writing is 6.2.3.

These are the things that I can think of at the time. Maybe if you narrow down the most important issues to you and try to identify the causes, it might be easier. Maybe solving one issue might lead to the solution of others as well, if LO is the application that fit your needs and specifications.

Regards!

---

### Post by pi-no on 2019-05-18
Hi. Sorry, for the late answer! I had no time to answer earlier. :)

> **Claus7 said:**
> 
so both at the time are using versions 6.2.2. I suppose that this is the version you have.


Exactly. It's precisely 6.2.2-0ubuntu2, just what was installed after the kubuntu 19.04 setup (fresh one; not updated).

> **Claus7 said:**
> 
5.x versions improved the interface a lot


Ah, yes, okay. In my opinion, the UI of it is rather conservative and often does not provide the 'comfort and smoothness of nowadays', but I see it improves from time to time, yes.

> **Claus7 said:**
> 
Among others you can come across the Ribbon like interface.


Indeed a nice addition. I clicked a bit around in it since a while, and it seems to be usable today. Though, I haven't found a way to customize it. As in MSO2007, this can lead to a lot of clicking. So, I'm not sure which I would use in the future.

> **Claus7 said:**
> 
I didn't know about the responses you got either, so there was no intention from me to point in the wrong direction either for solving the issues you are facing or behavior like.


Sorry, I really don't want to blame you. ;) It was just my feelings about answers I see, lets say, very often. Not only in response to my questions.

> **Claus7 said:**
> 
libreoffice --impress --backtrace
this will create a log file under your home folder, which can be more verbose while using LO.


The crashes are just one of the problems. Many of the other ones are equally annoying. But I gave it a try and had 'luck' after a few clicks. And indeed it somehow pointed me in an interesting direction:

```

...
Thread 1 "soffice.bin" received signal SIGSEGV, Segmentation fault.
0x00007f9ea44e2429 in ?? () from /usr/lib/libreoffice/program/libsdlo.so
#0  0x00007f9ea44e2429 in  () at /usr/lib/libreoffice/program/libsdlo.so
#1  0x00007f9ee3e84ce0 in Scheduler::ProcessTaskScheduling() () at /usr/lib/libreoffice/program/libmergedlo.so
#2  0x00007f9ed8dba34a in  () at /usr/lib/libreoffice/program/libvclplug_qt5lo.so
#3  0x00007f9ed8dba435 in  () at /usr/lib/libreoffice/program/libvclplug_qt5lo.so
#4  0x00007f9ed9c97426 in QMetaObject::activate(QObject*, int, int, void**) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
#5  0x00007f9ed9ca30c7 in QTimer::timeout(QTimer::QPrivateSignal) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
#6  0x00007f9ed9c97c5b in QObject::event(QEvent*) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
#7  0x00007f9ed8f4a551 in QApplicationPrivate::notify_helper(QObject*, QEvent*) () at /lib/x86_64-linux-gnu/libQt5Widgets.so.5
#8  0x00007f9ed8f51930 in QApplication::notify(QObject*, QEvent*) () at /lib/x86_64-linux-gnu/libQt5Widgets.so.5
#9  0x00007f9ed9c6d8e9 in QCoreApplication::notifyInternal2(QObject*, QEvent*) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
#10 0x00007f9ed9cc0453 in QTimerInfoList::activateTimers() () at /lib/x86_64-linux-gnu/libQt5Core.so.5
#11 0x00007f9ed9cc0ca4 in  () at /lib/x86_64-linux-gnu/libQt5Core.so.5
#12 0x00007f9ee05dfaae in g_main_context_dispatch () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#13 0x00007f9ee05dfd48 in  () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#14 0x00007f9ee05dfddc in g_main_context_iteration () at /lib/x86_64-linux-gnu/libglib-2.0.so.0
#15 0x00007f9ed9cc1102 in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () at /lib/x86_64-linux-gnu/libQt5Core.so.5
#16 0x00007f9ed8db422b in Qt5Instance::ImplYield(bool, bool) () at /usr/lib/libreoffice/program/libvclplug_qt5lo.so
#17 0x00007f9ed8db4316 in Qt5Instance::DoYield(bool, bool) () at /usr/lib/libreoffice/program/libvclplug_qt5lo.so
#18 0x00007f9ee3e930f2 in  () at /usr/lib/libreoffice/program/libmergedlo.so
#19 0x00007f9ee3e94e75 in Application::Execute() () at /usr/lib/libreoffice/program/libmergedlo.so
#20 0x00007f9ee2f4c8a3 in  () at /usr/lib/libreoffice/program/libmergedlo.so
#21 0x00007f9ee3e9b602 in ImplSVMain() () at /usr/lib/libreoffice/program/libmergedlo.so
#22 0x00007f9ee2f6a981 in soffice_main () at /usr/lib/libreoffice/program/libmergedlo.so
#23 0x000055cd04c3907b in  ()
#24 0x00007f9ee0e4bb6b in __libc_start_main (main=0x55cd04c39070, argc=3, argv=0x7ffc801a0378, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7ffc801a0368) at ../csu/libc-start.c:308
#25 0x000055cd04c390ba in  ()
...

```

Could be just coincidentally, but most I could see was the Qt integration stuff, so I tried it without Qt (SAL_USE_VCLPLUGIN=gen). And, admittedly, I just tried it for a few minutes, but I was not able to reproduce any of the major issues I had. The slides sidebar gives now visual feedback in drag-and-drop operations! Maybe the Qt integration is just buggy. My system runs many Qt apps, and I also develop one on this system, so generally my Qt installation should be quite healthy. However, this way, it's really ugly. I will check in the future, if the gtk integration can be a compromise...

So, thank you very much for this idea!

pino

---

