---
title: "gui is impossible"
date: 2008-05-18
forum: Testimonials &amp; Experiences
---

### Post by dmizer on 2008-05-18
a painful example of why people tend to offer help with command line interface instead of giving gui directions:
> (15:46:51) tomoko: why does it always open totem movie player?
(15:46:53) tomoko: not vlc
(15:47:11) dmizer: there is a setting for it.
(15:47:15) dmizer: just a second.
(15:51:27) dmizer: okay ... are you ready?  i will teach you how to change it.
(15:51:56) tomoko: ok
(15:52:06) dmizer: open totem.
(15:52:10) dmizer: not totem.
(15:52:11) dmizer: sorry.
(15:52:13) dmizer: thunar.
(15:52:25) dmizer: start > accessories > thunar
(15:53:10) tomoko: ok
(15:53:18) dmizer: now click edit > preferences
(15:53:34) dmizer: then go to "advanced"
(15:54:10) tomoko: ok
(15:54:23) dmizer: you see where it says "enable volume management"?
(15:54:29) dmizer: there is a checkmark next to it.
(15:54:30) dmizer: no?
(15:54:44) tomoko: yes
(15:55:04) dmizer: below that, it says "configure the management of removable drives and media ...
(15:55:13) dmizer: and "configure" is underlined ... no?
(15:55:28) tomoko: yes
(15:55:35) dmizer: good ... click on "configure"
(15:56:02) dmizer: there are several tabs ... the second one says "media" right?
(15:56:09) dmizer: sorry ... multimedia
(15:56:51) tomoko: nothing happened after i clicked configure
(15:57:00) dmizer: no new window appeared?
(15:57:09) tomoko: no,,
(15:57:11) dmizer: ...
(15:57:27) dmizer: close vlc.
(15:57:36) tomoko: i did
(15:57:46) dmizer: it's still running ...
(15:58:05) dmizer: never mind ... lol
(15:58:33) tomoko: nothign happened 
(15:58:37) dmizer: in the windows list below ... there is nothing that says "removable drives and media"?
(15:59:22) tomoko: no
(15:59:56) dmizer: is it written in japanese or in english?
(16:00:00) tomoko: i mean removable drives and media 
(16:00:01) tomoko: yes
(16:00:18) tomoko: the work is blue
(16:00:22) dmizer: you have "removable drives and media"?
(16:00:25) tomoko: japanese
(16:00:29) tomoko: yes
(16:00:37) tomoko: but  blue word in there
(16:00:42) dmizer: no no no.
(16:00:43) tomoko: and when i clicked nothing happened
(16:00:56) dmizer: you have "removable drives and media" window?
(16:01:11) tomoko: it is in the wondown
(16:01:17) dmizer: it is in the what?
(16:01:28) tomoko: in detail window
(16:01:44) dmizer: is there a section in it for "multimedia"?
(16:02:07) tomoko: it is k,,,file manager
(16:02:58) dmizer: i don't understand ... you cannot have both "file manager preferences" and "removable drives and media" in the same window.
(16:03:05) dmizer: they are different windows.
(16:03:58) tomoko: it was in thurnar file manager
(16:04:32) tomoko: then i clocked preference
(16:04:35) dmizer: yes.
(16:04:40) tomoko: and four windows
(16:05:02) dmizer: one of them is "removable drives and media"/
(16:06:20) tomoko: one of them has volume something
(16:06:36) tomoko: adn under that it says removable drives and media
(16:06:44) dmizer: go to that.
(16:07:06) tomoko: so there is one word blue with underline
(16:07:18) tomoko: but nothing happened when i click
(16:07:36) dmizer: sorry ... your version is different than mine.
(16:07:41) dmizer: i have no idea what to tell you to do now.
(16:08:06) dmizer: sorry.

it doesn't get any more frustrating than that.

---

### Post by ugm6hr on 2008-05-18
> **dmizer said:**
> it doesn't get any more frustrating than that.

25 minutes to achieve nothing.  Oh dear...

Having said that - a picture can tell a thousand words when it comes to the GUI.

My Enable Repos link in my sig is a good example (I think).

Live chat is definitely not the way to do it though.  I know this because I have tried it many times with my mum on the phone.  Leaves me frustrated and her without a functioning laptop.

As an aside - my solution for her was to install Ubuntu on a dual-boot (in addition to her previous WIndows) so that she now has 2 OS to make a mess of before I get a phone call!

---

### Post by jrusso2 on 2008-05-18
> **dmizer said:**
> a painful example of why people tend to offer help with command line interface instead of giving gui directions:


it doesn't get any more frustrating than that.

Now tell us the simple way to do this using the CLI

---

### Post by Sukarn on 2008-05-18
Really... its really much simpler to just tell people to open a terminal and type something than to guide them through GUIs, but doing this makes the new users think that a lot of configuration *needs* to be done through command line and they think that there is a lack of GUI interfaces.

Its a double edged sword.

---

### Post by dmizer on 2008-05-18
> **jrusso2 said:**
> Now tell us the simple way to do this using the CLI

open a terminal, and enter the following code:
```
mousepad ~/.config/Thunar/volmanrc
```

look for the line that says:
```
AutoplayVideoCdCommand=totem dvd:/
```
and change "totem" to "vlc"

save the file and exit.
took less than 5 minutes to accomplish using this method.

note:
in my friend's case the volmanrc file was not located under her profile, so i merely had her run this command first
```
cp /etc/xdg/Thunar/volmanrc ~/.config/Thunar/volmanrc
```
in retrospect, this was the source of the problem.  since her thunar was not opened under a root account, she did not have the privileges necessary for configuring "removable drives and media"

---

### Post by bmac on 2008-05-18
I must agree with Sukarn. Many nobs have been utilizing the M$ GUI for most of their computing lives. The concept that they _must_ use a dos like terminal to achieve solutions, could result in a misinterpation regarding the Ubuntu GUI.
Helping nobs manipulate their way through the GUI provides them with a warm fuzzy feeling of confidence. Once they become familiar with the system the next logical step is utilization of the terminal.

Just a thought.....

---

### Post by dmizer on 2008-05-18
while i do somewhat agree.  i also think that any user is most happy with speedy results.

also, do you think that the lack of screenshot based gui tutorials for kubuntu and xubuntu might have a tendency to drive new users toward the gnome interface even when kde or xfce might be a better answer for their hardware or software needs?

if a new user really needs help with gui instructions, screenshots can be found for gnome easily enough, but if they are not using gnome it's a different story.  if you happen to be lucky enough to have their same release, and their window manager installed, you'll be spending the next 4 hours writing a screenshot tutorial that (as in this case) may not even work.

and that doesn't even take into consideration the fact that gnome, kde, and xfce are all completely customizable with a host of different toolbars and functionality that would make even a screenshot tutorial useless.

how else do you address these significant issues?

---

### Post by Modplanman on 2008-05-19
Surely if they're customising they're GUI to begin with, why would they need a screenshot tutorial after they've just set it up themselves? That'd be pretty dim.

And I'm sorry, but having to use the terminal is **not** infinitely simpler. For someone who has already learned a language crossed between txt speak and swahili, fine, but the whole point of a GUI was so that you didn't have to learn practically a new language just to use a PC, and to make things visually easier and nicer to take in, along with all the other things you can add in with a powerful GUI (compiz effects aren't all just complete eye candy). Being able to present people with their options and the like all nicely orgnaised in plain English or whatever language they use is far easier than teaching them a whole new set of commands, as is the point of a GUI.

The problem here is someone who doesn't seem to know their way around a/the GUI properly, trying to explain it to someone else who doesn't either.

---

### Post by dmizer on 2008-05-19
> **Modplanman said:**
> Surely if they're customising they're GUI to begin with, why would they need a screenshot tutorial after they've just set it up themselves? That'd be pretty dim.
you're suggesting that someone without a lot of knowledge cannot make changes to their gui? i've been quite surprised what my friend has been able to accomplish.

> **Modplanman said:**
> And I'm sorry, but having to use the terminal is **not** infinitely simpler. For someone who has already learned a language crossed between txt speak and swahili, fine, but the whole point of a GUI was so that you didn't have to learn practically a new language just to use a PC, and to make things visually easier and nicer to take in, along with all the other things you can add in with a powerful GUI (compiz effects aren't all just complete eye candy). Being able to present people with their options and the like all nicely orgnaised in plain English or whatever language they use is far easier than teaching them a whole new set of commands, as is the point of a GUI.
i didn't say it was infinitely simpler to use the command line. the intention of my post was to illustrate how difficult it is to give _support_ using click directions inside a gui. i even gave a head to head direct comparison to illustrate the point.

> **Modplanman said:**
> The problem here is someone who doesn't seem to know their way around a/the GUI properly, trying to explain it to someone else who doesn't either.

i beg your pardon, but i know my way around the gui perfectly well. i've been using xfce for many years.  i also have 4 years of experience with telephone support and telling users where to click in order to fix their problem.  the fact is, it is way easier to fix a problem by giving cli commands than it is to give point and click directions.

furthermore, the actual problem in this case (as outlined in post 5 under "note:") would have been difficult to diagnose without using the command line.

---

### Post by Keyper7 on 2008-05-19
> **Modplanman said:**
> And I'm sorry, but having to use the terminal is **not** infinitely simpler. For someone who has already learned a language crossed between txt speak and swahili, fine, but the whole point of a GUI was so that you didn't have to learn practically a new language just to use a PC

Well, I think that's why people tend to post the commands exactly as they should be typed: to allow the user to copy and paste them without learning a new language.

Sure, there's the issue of malicious commands and the "teaching how to fish" thing, but it's not like it's impossible to screw up your system using a GUI and if the GUI wasn't intuitive enough for the user to figure out how to use it on his own, memorizing the steps to use it properly might be as hard as learning CLI commands.

---

### Post by 23dornot23d on 2011-06-07
There are a few things that I see repeating over and over .....


**One**

....  is GRUB 2 ..... how often do you see a thread with the bootscript being requested to be used ......
[COLOR=Red]THE BOOT SCRIPT SHOULD BE INCLUDED AS A ONE PRESS OPTION IN A MENU
[/COLOR]
**Two**

... Graphics Cards ...... people never give enough information ......
[COLOR=Red]GRAPHICS CARD INFORMATION - SHOULD BE OBTAINED FROM A ONE CLICK OPERATION[/COLOR]

**Three**

UNITY ..... and the Compiz settings .... I tried to use the Cube and !!!!
[COLOR=Red]COMPIZ CUBE - A BIG WARNING - PRESS THIS AND YOU GO TO COMMAND LINE HEAVEN[/COLOR]


These discussions to me seem pointless unless ways forward to solve a problem can be obtained .....

( yes they should no they shouldn't ) ....... waste of time if you ask me ..... if we help people we help them the best we know how ......

Since UNITY came in ..... I have no idea how to answer any questions as I do not understand the desktop ......

Go to the dock on the left ...... look for a square box with a ? in that is applications
right click on it .... that will bring a menu up that I am not familiar with .....
next ...... who knows ..... we are now both lost ..... !!!! mmmmmm

Solution CLI ..... or do not bother ...... guess what's happening .... more and more ....
so complain all you like about command line answers .....

If they are all a person helping knows ..... then what other option is there ?

---

### Post by overdrank on 2011-06-07
Back to sleep thread. :)

---

