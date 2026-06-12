---
title: "Arguments for and against net cafe change to linux"
date: 2008-06-11
forum: The Cafe
---

### Post by tadcan on 2008-06-11
I was talking to the owner of a cyber cafe which uses XP as its OS. I mentioned I use Linux and he was curious about changing over. On reflection he was against changing because most people only know windows.

Since I don't have enough knowledge to explain the full implications of changing. I told him I'd start a thread and let you guys and girls put forward the arguments. He has heard about Linux but knows nothing about it.

He has openoffice and firefox and uses open source because its free.

I told him it would be more secure, faster, but might have issues with setting up some windows based software, e.g msn.

Secondly I strongly disagree with one aspect of his business. The clients have access to XP running in admin mode. Openoffice and firefox are two year plus outdated version. He argues that because he resets the network every few days any changes made the the system are fixed.

I argued strongly that his system was in a time freeze which will affect him further behind as time passed. That he is denying his customers the benefits of softwares newest versions.   

So please tell him some of the options he has because in my opinion he needs to be proactive. 
.

---

### Post by original_jamingrit on 2008-06-11
Here's one very good reason; save on hardware: [http://linuxgazette.net/124/smith.html](http://linuxgazette.net/124/smith.html)

mind you, it's still experimental.  but it's possible.

---

### Post by cardinals_fan on 2008-06-11
Even if he doesn't switch, he shouldn't let people run as admin.  Switch them over to a limited user account, and delete every link to IE that he can find.  Firefox or Opera ONLY.

---

### Post by original_jamingrit on 2008-06-11
Sorry if this makes a double post.

> **tadcan said:**
> I told him it would be more secure, faster, but might have issues with setting up some windows based software, e.g msn.
I have a buddy who uses aMSN.  It looks and acts exactly like windows MSN, nudges and all.

> ...because he resets the network every few days any changes made the the system are fixed.
Does this apply to windows and IE updates as well?  For the past two years?  Each of his machines are probably accumulating any malware, over and over again, every two days.

---

### Post by tadcan on 2008-06-11
I presume its the same for windows updates. Didn't think to ask that. He believes that when he re-images the machines he creates a fresh slate. 

If that is not true is there something you can ask him to do check if it is true.

---

### Post by shadylookin on 2008-06-11
If his internet cafe is solely so people can use the internet then linux would be fine. It can do anything on the internet that MS can do plus there is not as many security issues.

If however he lets them use the computer to run windows programs it's probably best he keep windows. Teaching people wine probably wouldn't work out so well and not everything works on it.

---

### Post by rickyjones on 2008-06-11
Another aspect to consider before promoting Linux in this case is the management capabilities. Does your friend use a central server to manage the computers? Does he use a system of login accounts for his customers?

I used to own a computer gaming center/cyber cafe and while it would have been nice to save money on licenses it just would not have been feasible to have several "free" computers that anyone could use. In addition I would have had to invest in a separate system for managing patches and software updates (one for Windows, one for Linux).

Although keeping Windows just because most people are familiar with it is slightly flawed, in my opinion. I go to a cyber cafe to surf the internet, type up a small document, check my email, and possibly print a web page. As long as those functions are possible, and the manager is willing to document HOW to do these items, then there should be no issues from the customers.

Sincerely,
Richard

---

### Post by the_darkside_986 on 2008-06-11
Well then, he could AT LEAST upgrade to XP SP2, as any older version is highly vulnerable to malware, running as root or not. I upgraded my dad's system to SP 2 and he hasn't had any trouble since, even though he runs things as root, but he uses IE7 not 6 so it's alright. Last time I checked, SP2 was a free upgrade from SP1 for valid copies of Windows XP.

Or a KDE based Linux distro would be better. Or Gnome, if the cafe owner wishes to confuse and scare away users.

---

### Post by Bou on 2008-06-11
I can see several drawbacks:

-Gaming may be more difficult to set up, if it's the kind of place where kids go to play WoW and stuff.
-Pidgin does not support videochat, which many of his customers might want. I'm not sure if Kopete does, though.
-It's not easy to set up a system to bill computer use and block terminals, like the ones that you always see on Windows Internet cafes.

---

### Post by tadcan on 2008-06-11
I don't know if he has a server, but all the client machines are networked to the PC at his desk. Where the client machines are re-imaged from (My best guess)

He doesn't allow the computer to run in admin mode to allow people to use other programs. But because re-imaging removes programs.

I imagined someone could hi-jack his system and ransom it. Far fetched yes, but he is relying on people to never ever be malicious. I could go in and install a linux distribution, would the system stop me. Would he know I was doing it. I don't think so.  

Would thin clients be a way to go. Since he would just have to update the sever.

Talked to my g/f who argued that he runs a low cost place to browse. No one will really care that the rollerball mouses are clogged with dirt, Firefox has no x buttons on the tabs etc. If it works it works. I would feel bad for not providing a better service. 

There are no games, to stop loud kids being well loud. Video chat would be an issue. Youtube would have to work.

---

### Post by koenn on 2008-06-11
> **the_darkside_986 said:**
> he runs things as root, but he uses IE7 not 6 so it's alright. 
Don't count on it.

---

### Post by stoodleysnow on 2008-06-11
Youtube just needs the swfdec plugin for mozilla firefox.
Video chat, depends on the webcams. Have a look at the list of webcams that work on wiki.ubuntu.com

---

### Post by koenn on 2008-06-11
> **tadcan said:**
> I presume its the same for windows updates. Didn't think to ask that. He believes that when he re-images the machines he creates a fresh slate. 

If that is not true is there something you can ask him to do check if it is true.
re-imaging just reverts the machines to the state the image is in. They'd need to download and install all updates again. 
But I guess he just disabled automatic updates


I think this is an excellent case for Linux, if you can set it up with the required apps that do what his customers expect (like video chat, multimedia websites with problematic codecs, "you need silverlight", ... )


With Linux, 
he could have users with limited rights, a customized desktop with only the applications he wants to provide (browser, chat client). Less trouble, more secure.

in stead of re-imaging, he could have start_of_session, end_of_session and startup/shutdown scripts that clear the user home and set a fresh one with all sensible defaults.

the machines could be kept up to date (security- and feature-wise) by logging in remotely and let apt update & upgrade. With passwordless ssh sessions, this can be automated easily. Or Ubuntu's update manager could probably be set to just update without user intervention, I think.



One thing to look out for : if he's using some sort of cybercafe management software eg for reservations, timing of sessions, forced logout when credit is used up, or what ever, he's going to need a linux-compatible alternative. Finding that might be a challenge.

---

### Post by tadcan on 2008-06-11
I'll have to ask what kind of management stuff he uses. It doesn't log people in or out. From what I observed there is a screen with the computers on the network and the ones in use are highlighted. 

Wonder how long the imaging takes. Is there an argument that the effort put in know would mean the system is easier to run once set up?

---

### Post by imronak on 2008-06-11
One piece of advice,

He can use both OSes and offer lower price on the machine with linux :lolflag:, so that people start using that as an incentive ;) and see the difference

---

### Post by zmjjmz on 2008-06-11
> **tadcan said:**
> I'll have to ask what kind of management stuff he uses. It doesn't log people in or out. From what I observed there is a screen with the computers on the network and the ones in use are highlighted. 


LinNeighborhood?

---

### Post by madjr on 2008-06-11
> **tadcan said:**
> I was talking to the owner of a cyber cafe which uses XP as its OS. I mentioned I use Linux and he was curious about changing over. On reflection he was against changing because most people only know windows.

Since I don't have enough knowledge to explain the full implications of changing. I told him I'd start a thread and let you guys and girls put forward the arguments. He has heard about Linux but knows nothing about it.

He has openoffice and firefox and uses open source because its free.

I told him it would be more secure, faster, but might have issues with setting up some windows based software, e.g msn.

Secondly I strongly disagree with one aspect of his business. The clients have access to XP running in admin mode. Openoffice and firefox are two year plus outdated version. He argues that because he resets the network every few days any changes made the the system are fixed.

I argued strongly that his system was in a time freeze which will affect him further behind as time passed. That he is denying his customers the benefits of softwares newest versions.   

So please tell him some of the options he has because in my opinion he needs to be proactive. 
.

as a co-owner of a cyber cafe, i have great experience with the use of linux to substitute windows (lots of trial and error)

First off, you need to setup one test machine.

1- Looks (first impressions):
The default ubuntu look is no go. Everything is different (alien), specially the 2 panels.

for a 1 panel setup You could use linuxmint 5 or kubuntu (with a smaller panel).

2- Theme:
the default themes are no go also. Get something that looks "cool" and is similar to windows vista. It's necessary for acceptance. Else every user will be a bit frustrated and asking tons of questions.

If they feel at "home" it's easy for them to master something completely new.

3- Hardware:
make sure everything is compatible. especially webcams, etc.

list of compatible webcams (ones in green work):
[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

4- Apps (install all the ones listed):

-MSN-
emesene
aMSN (for video chat)

-multi-protocol-
Pidgin
Galaxium messenger (for many who won't like pidgin)
[http://code.google.com/p/galaxium/](http://code.google.com/p/galaxium/)

-other-protocol-
skype

-office-
openoffice (has the option to save in .doc format if needed or could be set as default)

-web-
firefox3
flash

-graphics-
google picassa
kolourpaint
rgbpaint

-misc. tools-
ubuntu-tweak
wine


5- program Shortcuts:
Big icons on the desktop (very important), but not every program, only the most "used". **Calculator and text editor**, should also have a shortcut in the panel.

6- share it :)

share your programs so others can use them at home and become familiar. latest **OOo** windows version for example.

7- questions:
feel free to PM me with your doubts

8- what country is this and what are the specs of the PCs with windows?

---

### Post by Lostincyberspace on 2008-06-11
Good Idea's, Makes me want to almost open up a cyber cafe myself.

---

### Post by gletob on 2008-06-11
One tip he should set up [OpenDNS]("http://www.opendns.com/")

---

### Post by Moustacha on 2008-06-11
LTSP would be useful, in the repos :)

---

### Post by tadcan on 2008-06-12
@ madjr, wow that sounds like great advice. 

Being an infrequent customer with a huge bugbear! I'm not familiar with  the specs of the machines. Its in Ireland. I'll talk to him again and ask has if he is following the thread. If he is interested he can sign in and PM you.

Out of curiosity I would like to see how an internet cafe would do. Not sure I'd put my money where my mouth is!

---

### Post by Bou on 2008-06-12
> **madjr said:**
> as a co-owner of a cyber cafe, i have great experience with the use of linux to substitute windows (lots of trial and error)

Hey madjr, how did you solve the issue of logging people in / out, and billing them?

---

### Post by billgoldberg on 2008-06-12
> **tadcan said:**
> I was talking to the owner of a cyber cafe which uses XP as its OS. I mentioned I use Linux and he was curious about changing over. On reflection he was against changing because most people only know windows.

Since I don't have enough knowledge to explain the full implications of changing. I told him I'd start a thread and let you guys and girls put forward the arguments. He has heard about Linux but knows nothing about it.

He has openoffice and firefox and uses open source because its free.

I told him it would be more secure, faster, but might have issues with setting up some windows based software, e.g msn.

Secondly I strongly disagree with one aspect of his business. The clients have access to XP running in admin mode. Openoffice and firefox are two year plus outdated version. He argues that because he resets the network every few days any changes made the the system are fixed.

I argued strongly that his system was in a time freeze which will affect him further behind as time passed. That he is denying his customers the benefits of softwares newest versions.   

So please tell him some of the options he has because in my opinion he needs to be proactive. 
.

The benefits of ubuntu on the desktop in a net cafe are pretty obvious.

1) safe from viruses/malware/spyware, ... 

This goes hand in hand with better performance (no anti-x software)

2) he already uses openoffice and firefox, 2 default apps in ubuntu

3) there is a piece of software that prevents users to make any changes to the system, for its name, but it's in the repo

4) for msn you emesene (gtk msn clone), or galaxium (for multiple services), they are easier to use then pidgin

5) the medibuntu repo has everything media wise (skype, vlc, ...)

6) newer version run faster then the previous version, so his hardware has a longer life span without having to run outdated operating systems 
(like windows xp).

Everything is free.

Updates are easy.

Just place some icons on the desktop with names like "instant messenger", "internet", ...

People will have no problem using it.

The only downside could be that he don't know how to set it up.

He could use it on 1 machine to test and hear the user feedback.

---

### Post by hoboken on 2008-06-12
Lately linux has been having problems with MSN messenger clients - all the programs I tried (aMSN, Gaim and Pidgin) failed to log in even using HTTP method. To be fair, this was quite a while ago, but if I remember correctly the problem was on microsoft's end.

If that still hasn't been fixed, it's a showstopper.

---

### Post by Pettman on 2008-06-12
Kickin people out when their time is up shouldn't be too hard to have a script do. He could even have some graphical notification that time was running out (a little polite info-box saying "your time will be up in 2 minutes")

> **hoboken said:**
> Lately linux has been having problems with MSN messenger clients - all the programs I tried (aMSN, Gaim and Pidgin) failed to log in even using HTTP method. To be fair, this was quite a while ago, but if I remember correctly the problem was on microsoft's end.

If that still hasn't been fixed, it's a showstopper.

I've never had any problems using msn under GNU/Linux to chat with some of my less enlightened friends and relatives. The file transfer is slow as hell in Pidgin but I can live with that.

---

### Post by madjr on 2008-06-24
> **Bou said:**
> Hey madjr, how did you solve the issue of logging people in / out, and billing them?

here:

[http://zeiberbude.sourceforge.net/](http://zeiberbude.sourceforge.net/)

there's also another program (in spanish) that has a native client and the server runs on Wine (if it freezes when connecting to the client you may need to test it with different Wine versions).

[http://www.cbm.com.ar/](http://www.cbm.com.ar/)

---

### Post by marialice on 2008-06-24
> **madjr said:**
> here:

[http://zeiberbude.sourceforge.net/](http://zeiberbude.sourceforge.net/)

there's also another program (in spanish) that has a native client and the server runs on Wine (if it freezes when connecting to the client you may need to test it with different Wine versions).

[http://www.cbm.com.ar/](http://www.cbm.com.ar/)

And there's more: [http://openkiosk.sourceforge.net/index.html](http://openkiosk.sourceforge.net/index.html)
It works with a KDE applet on the clients, but can also be used with Windows. 
(I don't have any personal experience with it, but it looks promising).

---

### Post by quinnten83 on 2008-06-24
> **original_jamingrit said:**
> Sorry if this makes a double post.


I have a buddy who uses aMSN.  It looks and acts exactly like windows MSN, nudges and all.


Does this apply to windows and IE updates as well?  For the past two years?  Each of his machines are probably accumulating any malware, over and over again, every two days.

I think he means that the computers are reinstalled through the network on a daily basis. So they always go back to a state where everything was originally installed.
I actually think he should at the very least create new images to reset his pc's tho.
Anyway, the same system he has now can be applied to linux systems, and linux is free (it only requires some knowledge), is safer, requires less resources and is more stable.
Also users in internet cafe, they get used to the computer interface pretty fast. And the interface can be completely configured to look like windows, if he so wants.

---

