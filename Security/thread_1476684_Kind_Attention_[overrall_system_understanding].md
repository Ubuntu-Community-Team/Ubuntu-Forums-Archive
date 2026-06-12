---
title: "Kind Attention [overrall system understanding]"
date: 2010-05-08
forum: Security
---

### Post by crozar on 2010-05-08
Greetings , 

i dont know how to explain this properly , but i hope you can bare with me while im writing this , in ubuntu theyr is system processes running in the background similar to [MS windows] processes accesed by Cntrl Alt Delete , 
in Windows through blackviper.com help guide i understood each processes and know whats going on in my [PC or to a better say my House] , i really wish to understand Ubuntu Gnome System Processes , to know how to make the computer Safe or BareBone user and to understand every process and know how to deal with them , forexample....
in windows System processes i have things activated like roxio for cd burning and stuff like svpool for the printer and other things that i may not be using , i keep my system processes down to 14 and then run gtalk , msn live and firefox and things are smooth and fast to mswindows, with ubuntu i see theyr are many processes , i dont know which to close im afraid to close something that is for the panel or something to do with evoloution or the date and time sync with calander , im afraid to hassle with these , right now i know you will say xubuntu is good because its a stripped system and then fromt heyr i make my own , but as for me im a user i like to do many things but sometimes i like to close these stuff and make my system smooth for what im focusing in doing yes 1 % , 5 % of resources to you may be nothign but to me its something im really delicate in such cases , the security question is , if i know whats going on in my Technologyhouse [ Back Ground Processes] i can deal with everything , but imagine theyrs something going on in the back ground wiht me knowing , how people will use this system ? i think if they knew it like they know windows , im willing to use this system more ive tried and tested many things and maybe soon have a python program written or a script to do my system objective forexample execute smooth mode , and make my system slick and only have empathy enabled and evo and rest disabled , or ect... 
i understand that linux is open source , with windows u dont know whats going on under svhosts.exe ,or more deeper saying the core of the system , atleast some1 must put an info about the layer of ubuntu about the kernel source , like in blackviper.com it explained the layer of the windows core , after this i might ask about the core just the mechanism of how things work not to understand them so atleast have a preview and maybe years later ill learn it hopefully. 
Thank you very much for reading ubuntu , ive been using ubuntu since 7.03 feisty but ive quit and went back and quit again but im back for 10.04 with wiser decision its about the elegency , ive wrote a blog here about it abit explaining why people should change in a wise decision
[read what people neglected of explaining about ubuntu]("http://norkgb.spaces.live.com/")

---

### Post by Rubi1200 on 2010-05-08
Try here for a start:

[http://www.cyberciti.biz/faq/show-all-running-processes-in-linux/](http://www.cyberciti.biz/faq/show-all-running-processes-in-linux/)

Also look here:

[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)

Finally, you might find this useful:

[http://ubuntuguide.org/wiki/Ubuntu:Lucid](http://ubuntuguide.org/wiki/Ubuntu:Lucid)

Also, read the security sticky on the forum and use Google.

---

### Post by crozar on 2010-05-08
Im sorry, i dont like the one to say this , but i have read these and it didnt help , please understand what im trying to say , look at this link for instance [MSwindows-Serviceslist]("http://www.blackviper.com/WinXP/servicecfg.htm")

now click on any service , you can see everything about it readable and clear . forexample = [http://www.blackviper.com/WinXP/Services/Alerter.htm](http://www.blackviper.com/WinXP/Services/Alerter.htm)
best thing about it , it explains everything even the dependencies of the service . 

this what you showed me is a breif , i know computers very well , im telling you i know windows and its layers but not the core , for linux ubuntu i know ubuntu but not its layers and not the core , for now just help me with the layers thats the important part , Stage 1 , then 2 then 3

what i mean by i know ubuntu means i know the GUI and how to use it fully , 
with windows i know how to use the GUI and understand its layers so even if 1 spyware or malware or anything any movement is going on in the background ESPECIIALLY in SVhost.exe i can notice and know any suspciouse movement even my kasperky security cant know such modified small corporate illegal fan boys spyware and malware when i can in windows! .
let me be clear , if u know ur house u will be happy , i know my house of windows , but not the linux world im sorry for speaking in a direct elevation but indirect talks is more respectful and slow in processing , so i hope no negative thoughts or impacts are in this conversation because i mean not by them.

---

### Post by CharlesA on 2010-05-08
Are you trying to get a list of processes running?

I do that by typing this in a terminal:

```
ps aux
```

---

### Post by crozar on 2010-05-08
i know how to see the list of processes but do you have any idea what they are , and which are important , if you told me all is important then u cant help me , 

when u buy a windows xp cd u receive 28 running processess with it but not all are important or you will be using at once , which then, i make them set to manual and have them end tasked and then it ends up with only 8 - 13 processes maybe 14 if i left shellhwdetection that is for to see anything plugged by USB and to recognize , btw ,the manually set processes will run when needed forexample Roxio CD burner , when i double click it it will activate its services ,  in linux i have no idea what to close dont tell me no one thought about explaining these , how do people of windows use windows ? as a real windows user , if i change , i will know how to bring those 10% of people that you have no idea about to come to ubuntu , im speaking from the world ,  

i need to understand each process what is it and what are theyr dependencies , and whats theyr tasks and which does the core need for the system to run .

imagine people dont know these stuff how the hell do u guys put your credit cards and save it on ur pc , with windows i know my system the only one who can steal if microsoft became a theaf one day , but how can i trust linux from this point on? .

---

### Post by OpSecShellshock on 2010-05-08
Try this:

```
sudo apt-get install bum
```

then hit Alt+F2 and enter this:

```
gksudo bum
```

This will start the boot-up manager gui. On the first tab there's a list of services running, and on the second there will be descriptions. It allows you to manage them fairly easily. If you like, you can cross-check it against something like Synaptic by entering the services in the search field of Synaptic and highlighting the packages, then look at the details to see the dependencies.

---

### Post by rookcifer on 2010-05-08
> **OpSecShellshock said:**
> Try this:

```
sudo apt-get install bum
```

then hit Alt+F2 and enter this:

```
gksudo bum
```

This will start the boot-up manager gui. On the first tab there's a list of services running, and on the second there will be descriptions. It allows you to manage them fairly easily. If you like, you can cross-check it against something like Synaptic by entering the services in the search field of Synaptic and highlighting the packages, then look at the details to see the dependencies.


Bum doesn't work on newer Ubuntu installs (Karmic, Lucid) because Ubuntu has mostly moved over to upstart jobs and is getting away from SysV.  If you uncheck a service in Bum and restart you will often find it's still enabled and vice versa.

---

### Post by CharlesA on 2010-05-08
If a process is running in Linux, it means it has a job to do.

There are processes for network monitor, firefox, pidgen, etc.

Normally you wouldn't manually go thru and kill off processes during normal operations. If an application is hung, you are usually asked if you want to close the application, or wait until it starts responding again.

---

### Post by crozar on 2010-05-08
why crossreference how come system monitor dont show it :/ , not all processes have a job to do , and all viruses and mal wares and spywares have a job to do , i dont want to have a house that i live up stairs and i dont know anything wats going down stairs while maids and butlers bring me breakfast , lunch and dinner , imagine if something went wrong and im all alone in my room ? do u get me now? i dont mean install firewall and antivirus i mean me being the firewall and antivirus of the system by understanding the system layers not the core because the core wont be touched if i maintain securing the layers of the linux core.

---

### Post by Rubi1200 on 2010-05-08
With all due respect, Linux is not Windows. Things work differently on Linux. I have been using Linux now for slightly more than 1 month and have barely scratched the surface of what is going on. You need to read documentation, do Google searches, ask specific questions on the forum, and try out different commands that offer system information.
The most common commands that help you know what is happening on your system are:
w
last
ps
lsof
netstat

this link will give you the man pages for these commands and help you decide how you wish to audit your system:
[http://www.linuxmanpages.com/](http://www.linuxmanpages.com/)

It is important to realize that Linux in general, and Ubuntu specifically, is safer out-of-the-box than a Windows installation.

Run:
sudo netstat -tap
for a list of listening services. The only one running by default in Ubuntu is cups. If you turn other services on such as ssh, vnc, or remote desktop, it is your responsibility to secure these services.

I also strongly suggest you read the security stickies at the top of the forum:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Learning Linux involves a lot of unlearning of bad Windows habits.
Sit back, relax, read up as much as you can, and enjoy what is a significantly more secure computing experience.

---

### Post by cariboo on 2010-05-08
There is a big difference between what services a Linux install runs, and what Windows services are running. With Windows there is a more or less definitive list, with a Linux variant, depending on what you have installed, your list of services will be different from your neighbors list of services, which will be different from the services running on my system.

Generally we don't worry about the number of services running,  if you check System->Administration->System Monitor->Processes, you will see what services are running, Most of the names are self evident, if you are running chrome, you will see a couple of instances of chrome in the list.  

There are no processes that have hidden functionality, if you see something you're not sure of, all it takes is a quick Google search to find out more than you want to know about it.

Keep in mind that it took you years to learn all you know about Windows, you can't expect to have the same level of knowledge of your Linux system in a couple of weeks, or even a couple of months.

---

### Post by OpSecShellshock on 2010-05-08
Interesting info about bum, and now that I think about it, it makes a lot of sense. Thanks.

So in that case, you can go to System-->Administration-->System Monitor and look on the processes tab. Also, you can look at System-->Preferences-->Startup Applications to see what's going to run automatically at the beginning of the session. Everything pretty much follows one naming convention, so you can just take the name of it and put it in a search engine to find all kinds of information about what it is/does. There is also a wealth of information available in the package manager, particularly with regard to dependencies.

The most care you should ever have to take is with the installation of software from places other than the official repositories and the installation of browser add-ons. Be aware that tweaks to look and feel will not require you to perform an installation if they are legitimate (and therefore will not ask for a password). The same is true for legitimate browser add-ons.

---

### Post by crozar on 2010-05-09
this is really hard to understand , it took me years to understand windows yes but atleast the first layers are easy , atleast give me the core's mechanism services , from the all services showing in system monitor the layers ill figure them out myself , but please some1 appoint me the services that gnome ubuntu rely on forexample the network has dhcp and dns cache and webclient , dhcp is important dns can be done manually the rest can be stopped from the services , i really need to know the core's Default Services from a slick point of view . so then i would be able to figure out the layers myself and explain it in a windows language to the people of linux which will sound better , why make things likea  zoo these days we are above technology dont be in it.

---

### Post by crozar on 2010-05-09
ill be releasing a video , of me maintaining full control of windows and then a video mockery of how ubuntu gives me a gazing satisfaction , let me be clear i love linux , but how the hell will people be using this , u think freedom is whats attracting to them ? mostly are people who studies IT or loves technology and thinks this is the key , but let me praise along with you guys and say ok lets study this , ill end up like a buffoon , most the education is really silly or a waste of time , if u studied it u want others to fall in the same miseries when others infact fall into other miseries let me scale the miseries with a point of beacon to tell you that youve missed awhole lot of miseries that tribulates in our lives , please if i study will i be the first to post this to the world ? when u guys have the knowledge overseeding me and im just asking for the hand , if you wait soon by the end of the month hopefully i will release a video , im not sure how i will be recording it for best understanding , im thinking of being in the clip just to give you metaphors and analogies of how serious this subject is.

---

### Post by CharlesA on 2010-05-09
It is only a serious subject because you don't seem to understand that Linux is not Windows. 

Like it's been said before: you don't normally kill off running processes. 

If an app is running that isn't a service (background daemon like SSHD, SMBD, etc), you can normally just close it from the application itself. Applications like that are, for example: firefox, chrome, transmission, pidgin, etc.

If you don't use a program and don't want it taking up disk space, remove the program from software center or synmaptic.

cariboo907 pretty much already covered how the system monitor works.

---

### Post by Rubi1200 on 2010-05-09
I concur with CharlesA and cariboo907; Linux is NOT Windows.

Do yourself a favor and read this article:

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Then, go here:

[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=224)

and start reading as much as you can.

Unlike Windows, which is closed source and lacks transparency, Linux can be dissected from the ground up.

Even if you see a process running which you are not sure about what do you want to do? End the process or search for information to help you better understand it?

As long as you downloaded and installed Ubuntu, following the recommended installation guide, as long as you are not running a server or unsafe programs like vnc, as long as you keep your system updated and only install software from the Ubuntu repositories, you are pretty much safe.

If what you are looking for is high-level understanding of the kernel, then you may be asking in the wrong place (somebody correct me if this is not true).

If you are looking for reassurance as an average desktop user that your system is safe, then know that the people on this forum will help you as much as they can, when they can.

Good luck!

---

### Post by crozar on 2010-05-09
my question still stands , here is an analogy , System processes are the one that strikes **** stars , system services for printers remote desktop and anything attached to the system processes mark them as *** , and the rest like pidgins , firefox etc.. mark them as ** stars , 

now suspicious behavior , malware , glitches , trojans , any anonymous thing will be marked as * 1 star , this is how i'd like explaining , if the *** or ** is acting some how strange then its an intruder either spyware or virus or anything , before letting the intrustion its the * is to be observing and killing it and blocking it before it even starts its task , im sorry , i shouldve planned this with a video to have a great answer instead of guides that i dont like to quote about them herre i have quoted how silly it is in the post before. thankyou

---

### Post by CharlesA on 2010-05-09
First off: There are no "viruses" in the wild for Linux. Same with Malware. There are a few trojans/rootkits, but if you stick to the software offered in the repositories you are pretty safe from those.

You seem to be thinking of Linux with the Windows mindset (OMG Viruses, Malware, Trojans, oh My!). Linux doesn't have the same problems as Windows when it comes to that.

As said before, there are no Viruses for Linux and viruses written for Windows won't run on Linux unless you have WINE installed (which isn't installed by default). Same for Malware.

Both the links that Rubi1200 posted are good reads. Have you read them?

---

### Post by crozar on 2010-05-09
i have went to the extremes with my stumbling in the web with linux i believe i have infected it right now , tell me how can i cure it my best option is to format , il be back later when this is solved and ill be back to my subject of system processes or services or whatever you guys want to call it , the concept is the same you guys are trying to make it complicated with your metaphors , im giving you the easiest metaphor that the brain can distinguish and not the computer world of educated sequence that your in , im really sad that this happened to my ubuntu i have installed wine yes but i have uninstalled it also , how come it got infected ? maybe a linux virus or some kind of windows virus that hit my wine that was uninstalled and reactivated it or anything linguistic to the world of linux education .
i have asked similar [question about Services at 2007]("http://ubuntuforums.org/showthread.php?p=3701364#post3701364") , ill stay here for a couple of hours before format , tell me what logs you want me to upload to you if you want proof .

---

### Post by CharlesA on 2010-05-09
Why do you think you are infected?

Windows viruses won't affect the Linux portion of the OS. If you somehow got a virus in WINE, it is confined to WINE.

---

### Post by OpSecShellshock on 2010-05-09
Hmm, I'll give it a shot with those terms, but I'll have to apologize since it's not really a standard way of explaining things.

**** processes cannot be altered in any way without privileges first being escalated, at least under a default configuration.

The same holds true for *** in most cases, though I'm a bit confused with this particular notation since I don't think they occupy that space in the implied hierarchy.

** processes run as the user, completely within the user session and are limited to user-level (i.e. non-administrative) privileges. The furthest those processes will ever reach by default is the user's home directory. Obviously it would be different if those processes were started by either logging in as root or by using a sudo prior to the command to run the applications. Those two things are bad ideas, and there's no reason at all to do them.

Now, in the unlikely event of a * issue, the most it's going to do is cause ** to crash, assuming a default configuration and that the ** is run as a regular user. At that point you just restart ** most of the time, or restart the computer entirely and it's problem solved.

If by chance you are tricked into installing something malicious, then first of all you'll need to elevate to administrative privileges to do so, and second, you'd no longer be dealing with a * but rather a **.

---

### Post by crozar on 2010-05-09
i dont think i believe because of the recent activity , my firefox spammed and keeps redirecting me to exploited websites with multiple tabs and i hear my harddisk is processing and the blink is blinking simultaneously the system is acting slow what more do u want ? im not exaggerating im impulsing my facts for you to redefine. tell me how to send u the log activity or anything u guys want for the proof enough said.

---

### Post by crozar on 2010-05-09
i just wish blackviper.com does hes tutorial for linux , if no one comes with help il be learning this myself within 2 or 5 or 10 years maybe ill be also gaining some evil side that make me ignorant like the wiz's with no potential of patience of understanding my question and helping to clarify without abnormal state of corresponding maneuvers , this is not rocket science.
MSwindows ( win32 binary code cabinet files ) <= The core => ( Svhost's and the rest that is closed source but can be altered with options ) . the above layer is above the core and can be altered with options , the layer after is the registery and system processes after that is the services . your telling me linux core and all the system and services are command lines within the file integrity without having a service for such claims ? service for the printer pool is that integerated ? or a service attached ? is linux a lasagna or a spaghetti ? or is it water ? should i be brucelee to know it =( blackviper made us understand layer below the GUI , this is what im asking for not the core's layer and not the layer between the layers just the GUI and under it fullstop .

---

### Post by OpSecShellshock on 2010-05-09
If you're talking about the kernel, well, it can't be altered on the fly. It can't be changed from within itself by a regular user or any process that runs as a regular user. There is no equivalent to the Windows registry as far as I know. Any file created by an application is owned by whatever user was running it at the time. Any process that is not run by an end user can't be changed by an end user's application.

For your browser troubles, all you'll probably need to do is go under Tools-->Clear Recent History and select "everything" from the menu. There will be a little arrow next to the word "Details" which you can expand. Check everything on the list, and then clear it. Close the browser and open it again and it should be fine.

In order for there to be persistent malware on your system, you would have to have installed it yourself or you would have to have remote desktop enabled in an insecure fashion.

---

### Post by Rubi1200 on 2010-05-09
> **crozar said:**
> Im sorry, i dont like the one to say this , but i have read these and it didnt help , please understand what im trying to say , look at this link for instance [MSwindows-Serviceslist]("http://www.blackviper.com/WinXP/servicecfg.htm")

now click on any service , you can see everything about it readable and clear . forexample = [http://www.blackviper.com/WinXP/Services/Alerter.htm](http://www.blackviper.com/WinXP/Services/Alerter.htm)
best thing about it , it explains everything even the dependencies of the service . 

this what you showed me is a breif , i know computers very well , im telling you i know windows and its layers but not the core , for linux ubuntu i know ubuntu but not its layers and not the core , for now just help me with the layers thats the important part , Stage 1 , then 2 then 3

what i mean by i know ubuntu means i know the GUI and how to use it fully , 
with windows i know how to use the GUI and understand its layers so even if 1 spyware or malware or anything any movement is going on in the background ESPECIIALLY in SVhost.exe i can notice and know any suspciouse movement even my kasperky security cant know such modified small corporate illegal fan boys spyware and malware when i can in windows! .
let me be clear , if u know ur house u will be happy , i know my house of windows , but not the linux world im sorry for speaking in a direct elevation but indirect talks is more respectful and slow in processing , so i hope no negative thoughts or impacts are in this conversation because i mean not by them.

So, let me get this straight. What you want is a website that will give you the same kind of information for services in Linux as BlackViper does for Windows?

First of all, Linux does not function in the same way as Windows; to begin with the language is different.

Second, learning Linux requires a large amount of unlearning Windows.

Example, in Windows using Ctrl+Alt+Del brings up the dialog for amongst other things Task Manager. In Ubuntu, you get the Shutdown, Restart options. Force of habit led me to use this a couple of times until I trained myself to unlearn it.

The same applies for understanding what is happening under the hood in Linux.

First read the basics before trying to jump into more complicated matters.

The only thing I can suggest is that you start here:

[http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlservices.html](http://www.comptechdoc.org/os/linux/howlinuxworks/linux_hlservices.html)

---

### Post by crozar on 2010-05-09
ubuntu is a polished linux version the one that your showing is mainstreamed from linux i thought they have armored it with layers to make the alteration quicker for ubuntu , but for me reading that i believe half of that and more can be closed now u showed me i must give it a test , for example these 
smb
nfs
ypserve
 ect..
the one that isnt run in the back ground and is run once  , does this mean its function and procedure still takes resources ? 
forexample
shell hardware detection in windows its run when pc starts after it detects my mouse and everything i can use th em but u know if i kill that process , still my mouse and everything else still works / however if i attach a new mouse or any new usb / plug it and it wont detect it but the good news i saved and gave more energy to my PC , 
talking about energy theyrs much to speak about
im here for power , and security , my monitoring way of security , i dont trust the computer world.

i hope u guys have a good morning ,  im having tea with bread and date spread

---

### Post by Jive Turkey on 2010-05-10
Actually, the advice of blackviper is overrated.  Also, there have been reports showing that disabling the unused services in windows has no significant effect on performance.  This was based on reliable benchmarks etcetera.  The closest thing to a unified list of the processes and services like that published by blackviper would be in synaptic.  

It is already on your computer unless you removed it.

I think you are wanting to do lots of hardcore tweaking of the OS, the wonderful thing about linux is that everyone has access to the source code Instead of mucking around with programs that nobody really knows for sure what they do like windows, everybody can get access to the source and tweak that instead.  What I think you should be researching is probably LFS or Linux from Scratch.

Pardon me for making this assumption, but you might do well to find an ubuntu or linux forum in your native language.

---

### Post by crozar on 2010-05-10
read my posts before imposing redirected information , you are trying to change the origin of this subject maybe because i have given the coherence with steps , i dont believe its possible to fulfill everything in 1 post from a beginner or an advanced Person with computers , let me rephrase everything and clarify in the end of the week after i give my trials into ubuntu , please do not answer if your feedback is based upon another line trying to intercept my subject without the means or with the means of satisfaction based on yourself , or contribution just looking at it from the innocent side , i dont want to be appointing or slandering with intentions , but when i see how this is going the one who's on hes free time with knowledge bricked by hes status thinking hes build is better then the building im in , im not contravening your corresponding knowledge im trying to bring the knowledge together with simplicity towards my subject and not going around in merry go round rides showing that the subject is like a gaze on the space. please ignore this post and wait for me to rephrase my question about Security using self monitoring sequenced by feel and awareness and last but not least speed and power .

---

### Post by jocko on 2010-05-10
Your question has been answered several times already.

Linux is not windows, so your ideas of viruses and malware are not really relevant.
The few known linux viruses are more proof-of-concept than real viruses, and they require you to give them root access to be able to do any real harm. Windows viruses do not run in linux, and even if some of them might be able to run in wine, they could never cause any damage outside of the users wine configuration.
Some malware that specifically targets firefox may work in linux (if you choose to install them) but they would only damage the users firefox configuration and are easily cleared by removing the ~/mozilla folder (just make sure you back up your bookmarks first).

There is nothing in linux that is analogous to the windows registry, and which "services" are run on startup depends on what programs you install.

If you want to know what a specific program/service does, there are several very simple ways of finding out:
1. Read the info about the program in synaptic.
2. Read the manual (type "man [COLOR=Blue]programname[/COLOR]" in a terminal).
3. [Google]("http://www.google.com/") and [wikipedia]("http://en.wikipedia.org/wiki/Main_Page").

---

### Post by crozar on 2010-05-10
> **jocko said:**
> 
Your question has been answered several times already.
**Thank you very much** _but_ not entirely answered.
> 
Linux is not windows, so your ideas of viruses and malware are not really relevant.
is this logical ? , to this new world of generation you oldschoollers will have it coming soon...

> 
If you want to know what a specific program/service does, there are several very simple ways of finding out:
1. Read the info about the program in synaptic.
2. Read the manual (type "man [COLOR=Blue]programname[/COLOR]" in a terminal).
3. [Google]("http://www.google.com/") and [wikipedia]("http://en.wikipedia.org/wiki/Main_Page").

i repeat my respects to your do it yourself method thankyou very much looks like i have to stitch these answer's to give my origin of question answer

---

### Post by CharlesA on 2010-05-10
> **crozar said:**
> is this logical ? , to this new world of generation you oldschoollers will have it coming soon...

I don't even really understand what you are saying here.

> i repeat my respects to your do it yourself method thankyou very much looks like i have to stitch these answer's to give my origin of question answer

Is it really that hard just to google a service, or look into synaptic? Having a master site is all well and good, but with so many different distros of Linux, it would be a pain to navigate and the information could be outdated if it wasn't monitored constantly. Why reinvent the wheel when a simple google will find you the information you seek?

---

### Post by cariboo on 2010-05-10
> **crozar said:**
> i dont think i believe because of the recent activity , my firefox spammed and keeps redirecting me to exploited websites with multiple tabs and i hear my harddisk is processing and the blink is blinking simultaneously the system is acting slow what more do u want ? im not exaggerating im impulsing my facts for you to redefine. tell me how to send u the log activity or anything u guys want for the proof enough said.

Your browser has been hijacked, it has nothing to do with services running, clear your cache, and the problem should go away.

No operating system will stop something like that be it Windows or Linux.

---

### Post by crozar on 2010-05-10
i cant trust the system until i know how to monitor it , this is getitng out of hands , i see why half the world is using windows , im going to post a wish list thread for the new 10.10 release to be really a 10/10 linux system it should have its knowledge in simplicity , having a GUI for system monitoring simple with tree's having red colored attributes for the importance , Blue for the services such as printers bluetooth eect.. and green for the app's , tell me this according to use with admin rights does the core of linux the root any way be harmed? or is it like a recovery from another partition in a way of saying?...

This thread is concluded with a reason that i have to do this easy work they say it is , and learn from scratch each and understand them do trails ect... i just wish its that simple when you have responsibilities , what i can do is donate a good amount to ubuntu . either way its just a system maybe towards the public , but when i want to put my life in the system then im just looking for trust which is me becoming above the system without even studying programing or IT education , i have enough experience to learn and read , so whatever instructions you give me about monitoring i can handle it by time i can understand it but the instructions your giving me is like telling me make  your own instructions>!.

---

### Post by Rubi1200 on 2010-05-10
If you are interested in monitoring your system then look at this link:

[http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html](http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html)

Just know that some of these tools are not installed by default and others are for very advanced users.

Also, not all parameters are shown; these are just a few examples.

I hope this helps you get a better understanding of what is going on.

Even though it says these are for monitoring servers, some of them are also relevant for standalone workstations.

---

