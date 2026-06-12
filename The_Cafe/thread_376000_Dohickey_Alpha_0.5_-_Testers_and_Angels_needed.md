---
title: "Dohickey Alpha 0.5 - Testers and Angels needed"
date: 2007-03-04
forum: The Cafe
---

### Post by DoctorMO on 2007-03-04
Hello All,

[http://dohickey-project.com/](http://dohickey-project.com/)

I'm struggling a bit making sure the client for the Dohickey project works on machines other than Ubuntu Edgy and also I've had people asking me about updates and so forth so today I release a client alpha which can be downloaded at sourceforge: [https://sourceforge.net/project/showfiles.php?group_id=177020](https://sourceforge.net/project/showfiles.php?group_id=177020)

I invite you all to download it and cause it problems and let me know via bug tracker.

The server portion (where votes are collected and hardware information collect / distributed) is turned off (commented out of /etc/dohickey.conf) as you can see it points to localhost as I haven't a solid server with perl/apache/xapian if anyone has a bit of spare space to run alpha tests on it would so very much help the testing and fixing of problems.

Hopefully I can get this project out of the doldrums of single developer syndrome so if any of you fancy your hand at the python client or perl server sides I'd kiss your feet so to speak.

Best Regards, DoctorMO

---

### Post by DoctorMO on 2007-03-04
Haha, can you believe I've got a sweedish translation already! talk about speedy.

I hope More people will see this, I got a lot of interest last time and more emails and messages asking me to continue and how was it going so the hope is that those waiting on progress will be able to see it for them sevles.

---

### Post by Crashmaxx on 2007-03-04
Compiling tips please? Some of us are a little too dependent on apt-get, lol.

This is a great project. I can only hope you can get the word out and really get this going. How is the outlook for other distros? You said it only works on Edgy so far.

---

### Post by maniacmusician on 2007-03-04
> **Crashmaxx said:**
> Compiling tips please? Some of us are a little too dependent on apt-get, lol.

This is a great project. I can only hope you can get the word out and really get this going. How is the outlook for other distros? You said it only works on Edgy so far.
The plan is for it to work on all Linux distros, as it has very few dependencies. As of now, I'm pretty sure it's just GTK, some python packages, and HAL.

---

### Post by bastiegast on 2007-03-04
When I installed feisty it asked me to run some sort of hardware survey, isn't that similair to your   project? Except that your project is cross-distro.

---

### Post by maniacmusician on 2007-03-04
> **bastiegast said:**
> When I installed feisty it asked me to run some sort of hardware survey, isn't that similair to your   project? Except that your project is cross-distro.
It's similar, yes, but I'd like to think that Dohickey is going to be more versatile. As you said, it is cross-distro, and the database for the info gathered will be hosted online.The goal of this is really to create something that is user-created and user-maintained. It'll also be a good place to check to see what hardware has working drivers in what Linux distro, etc. Of course, this may be a few months into the future. The short term goal right now is putting in lots and lots of work into the client, so that is either for users to use and maximized the amount of useful info that we can get out of them. 

By the way, I'm not the developer of this project, DoctorMO is. I was the website maintainer for a while, but I've recently gotten tied up with work and school so I've had to step down for a while. Hopefully when I have more free time, I can start helping out again.

---

### Post by migla on 2007-03-04
> **Crashmaxx said:**
> Compiling tips please? Some of us are a little too dependent on apt-get, lol.

In addition to the build-essential package, when what is needed for compiling is mentioned, it means the -dev packages of the mentioned packages, I gather.

---

### Post by Polygon on 2007-03-04
lol i think it was me that asked about the updates =P

anyway ill compile now and see if it makes my comp explode

EDIT: is there anything that i have to compile? because i just extracted the folder to my home folder, tried to ./configure it, but it didnt do anything. So i just ran ./dohickey and i got this:

> 
mark@ubuntu:~/dohickey$ ./dohickey
Directory 'None' does not exist!
We regret that Dohickey can only be run in administrator mode.
mark@ubuntu:~/dohickey$ sudo ./dohickey
Password:
Directory 'None' does not exist!

(dohickey:5790): libglade-WARNING **: could not find glade file '/home/doctormo/SVN/dohickey_client/do.glade'
Traceback (most recent call last):
  File "./dohickey", line 495, in ?
    manager = HillManager()
  File "./dohickey", line 34, in __init__
    self.initGUI()
  File "./dohickey", line 45, in initGUI
    self.wTree = gtk.glade.XML(install_dir + 'do.glade', 'mainWindow')
RuntimeError: could not create GladeXML object
mark@ubuntu:~/dohickey$ 



---

### Post by Crashmaxx on 2007-03-04
I tried to compile it and got it to checkinstall, but when i try to run it I get this:
```
crash@crashtop:~/Desktop/dohickey$ sudo dohickey

(dohickey:13592): libglade-WARNING **: could not find glade file '/home/doctormo/SVN/dohickey_client/do.glade'
Traceback (most recent call last):
  File "/usr/bin/dohickey", line 495, in ?
    manager = HillManager()
  File "/usr/bin/dohickey", line 34, in __init__
    self.initGUI()
  File "/usr/bin/dohickey", line 45, in initGUI
    self.wTree = gtk.glade.XML(install_dir + 'do.glade', 'mainWindow')
RuntimeError: could not create GladeXML object
crash@crashtop:~/Desktop/dohickey$ 

```

---

### Post by Polygon on 2007-03-04
well im guessing that since its a python program nothing needs to compile, you  just did "sudo make install" which installed the files to the correct places

and you have the same error as me which means something went wrong with the code =P

---

### Post by DoctorMO on 2007-03-04
Looks like a locals file problem, I've been bitten by this before and even created a clean on the make. I must confess to not beeing very experienced with packaging.

So hold off and I'm gathering all the package problems I've had reported and some helpful advice from the hal lists.

thanks guys.

---

### Post by DoctorMO on 2007-03-05
Hey all!

You should find a new package which allows you to do normal installs and run it from uninstalled; give it a try. oh and a new screen shot.

[http://sourceforge.net/projects/dohickey/](http://sourceforge.net/projects/dohickey/)

Packaging has hellish btw, I still have to work out how to compile the language po files so I can have it multi language; do let me know anyone if you know.

---

### Post by maniacmusician on 2007-03-05
Damn, I just wrote a long post, but it got wiped out! Damn. [sigh] What a hassle. So, here I go again.

The client needs to take a more Damn, I just wrote a long post, but it got wiped out! Damn. [sigh] What a hassle. So, here I go again.

The client needs to take a more input-oriented approach towards the user, rather than just giving them fields to fill in. I hate to say it, but it needs to be a little more like the Ubuntu Device Database program.

For example, the first thing users should see when they start Dohickey is "Welcome to Dohickey" or something like that, a little paragraph explaining what the program does, what its goal is, etc. Then, the user clicks next; here, the questions start. The way the questions are asked should determine the interface of Dohickey.

The first question should be, obviously, **"Is your computer a Desktop or a Laptop?"** This is for diagnostical purposes, a bit of data to be attached as classification for the profile.

Then, ask a question like **"Did you build this computer yourself, or did you buy it prebuilt from a company?" **If they answer prebuilt, then the Dohickey interface should take a broader, "whole-computer" overview of the situation. For instance, after that, It would ask the name of the company, the model of the computer, etc. The user would answer, "Dell Inspiron E1505." This data would also be classification. This can seem silly, but it allows for a very convenient way of tagging stuff for the database. This way, instead of searching individual parts, users can go to the Dohickey website and search for a computer model, like the Dell Inspiron E1505, and have a complete profile come up. 

However, if the user answers "I built my computer," you can forego the niceties, and lead them to the interface of Dohickey that you have built right now, with individual devices listed. Then, these advanced users that built their own system, know it inside and out, can quickly fill out the information for each piece of Hardware. See, what this innovative design would do is create environments suited to the user. A user with a prebuilt computer may not know every little detail of it, so they get the survey type questions. People who built their computers get the detailed version.

I'd also suggest Autodetection of more devices. For example, I've noticed that the first device listed is always a Motherboard, but it has a long, nonsensical name like **"82801EB/ER (ICH5/ICH5R) LPC Interface Bridge, 82801EB/ER (ICH5/ICH5R) IDE Controller, 82801EB (ICH5) SATA Controller, 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller, 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1, 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2, 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3, 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller, 82865G/PE/P DRAM Controller/Host-Hub Interface, 82865G Integrated Graphics Controller"** Not even kidding. Yes, those are all the parts of the motherboard, but it shouldn't be labeled like that. Since it is always first, make the label say "Motherboard" and let the user fill in the details of the mobo, like the manufacturer, model, etc. 

I noticed that you've already done that with some devices like optical drives and whatnot. My suggestion is, Instead of having the Name of the device, and then the classification, put the classification first. So, for instance, it should say "Optical Drive - HL-DT-ST CD-ROM GCR-8486B", not "HL-DT-ST CD-ROM GCR-8486B - Optical Drive"

My last suggestion is, do not leave the compatibility "star" rating to the user. That's a subjective evaluation. One user may say 3 for functionality while another user thinks that it deserves a 1. You need to ask the user evalutative questions about that hardware and then derive from the answers an objective rating.

Phew. that was a lot of writing. Hope it helped.

---

### Post by DoctorMO on 2007-03-05
> The client needs to take a more input-oriented approach towards the user, rather than just giving them fields to fill in. I hate to say it, but it needs to be a little more like the Ubuntu Device Database program.

No thanks! I hate that stupid program with it's 'Next', 'Next' I'm think your stupid gui. No this is a tool for telling you what the computer contains; a user must have the remit for handling the gui currently there or I don't believe their data is going to be of any use any how. General position won't change but if you do see a road block in the flow I will have a look at how to fix it.

> For example, the first thing users should see when they start Dohickey is "Welcome to Dohickey" or something like that, a little paragraph explaining what the program does, what its goal is, etc. Then, the user clicks next; here, the questions start. The way the questions are asked should determine the interface of Dohickey.

It might be worth putting in a welcome screen, but then again that is supposed to be what the help button is for (if it worked, which it doesn't because no one will write the help file)

> The user would answer, "Dell Inspiron E1505." This data would also be classification. This can seem silly, but it allows for a very convenient way of tagging stuff for the database. This way, instead of searching individual parts, users can go to the Dohickey website and search for a computer model, like the Dell Inspiron E1505, and have a complete profile come up.

You should see my initial notes from 2 years ago, they have a striking similarity; but I dropped this idea because it would take too long to program. getting the structures for just the hardware and devices was hard enough. It remains on my list though.

> I'd also suggest Autodetection of more devices. For example, I've noticed that the first device listed is always a Motherboard, but it has a long, nonsensical name like "82801EB/ER (ICH5/ICH5R) LPC Interface Bridge, 82801EB/ER (ICH5/ICH5R) IDE Controller, 82801EB (ICH5) SATA Controller, 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller, 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1, 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2, 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3, 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller, 82865G/PE/P DRAM Controller/Host-Hub Interface, 82865G Integrated Graphics Controller" Not even kidding. Yes, those are all the parts of the motherboard, but it shouldn't be labeled like that. Since it is always first, make the label say "Motherboard" and let the user fill in the details of the mobo, like the manufacturer, model, etc.

There is no such thing as auto-detection, this program does not auto detect things it simply attempts to understand what has been detected already by your system. this long string is because your hardware isn't known and no one has edited the information in that hardware profile. eventually all motherboards will be identified and you won't see strings like this. btw, not only with the motherboard not always be first, sometimes it's split into a number of parts. I have a way of telling it that one part is a fragment of another but not in the gui yet can't quite figure out how to do that.

> I noticed that you've already done that with some devices like optical drives and whatnot. My suggestion is, Instead of having the Name of the device, and then the classification, put the classification first. So, for instance, it should say "Optical Drive - HL-DT-ST CD-ROM GCR-8486B", not "HL-DT-ST CD-ROM GCR-8486B - Optical Drive"

This information is available in your system, there is a lot of work in hal to do with disks and optical drives.

> My last suggestion is, do not leave the compatibility "star" rating to the user. That's a subjective evaluation. One user may say 3 for functionality while another user thinks that it deserves a 1. You need to ask the user evalutative questions about that hardware and then derive from the answers an objective rating.

I agree, what about a task bar button for 'rate this' and a drop down menu which says 'Doesn't Work (0), Some Works (2), Most Works (4), Fully Works (5) and perhaps put it on a right click menu too?
> 
Phew. that was a lot of writing. Hope it helped.

Lets talk some more about how to organise things.

---

### Post by Crashmaxx on 2007-03-05
It works now, and it looks good. Only three things I think need to be improved:

1. Better install an usage tips. Like how do I upgrade this later? Or remove it all together? And how do I run it without install? And when it is running, what stuff should I be editing and what not? But I'm sure this will come in time, its still very alpha

2. I feel you should be able to double click or right click on devices to edit them. Or maybe the button needs to be next to them. Something, cause its not intuitive that you can even change the details nor how. And the stars are nice, but it is not obvious you can change them. And as mention, a guide to what they mean, or maybe a drop down instead would be better. And maybe it was just me, but the window was small and descriptions cut off.

3. There should be an option to opt out for devices you are unsure what are, if they work, or just don't use. I don't want to give a score of 0 just because I didn't recognize it. Nor do I want to give a 5 to something I am assuming works, but may not even use. And along with this, hopefully you can have the names and details sync with the server at some point and then you can just confirm the "known" details of it and only have to change something when you had different results or the details are wrong. But I don't know how to do that, or what your plan was with that.

I hope that is some helpful feedback. And it seems like it didn't detect a lot of my stuff. But I don't know how you are doing that, and some things may have been there but just called strange things, especially since its a laptop. Let me know if that is strange or what is the deal here.

---

### Post by DoctorMO on 2007-03-05
> 1. Better install an usage tips. Like how do I upgrade this later? Or remove it all together? And how do I run it without install? And when it is running, what stuff should I be editing and what not? But I'm sure this will come in time, its still very alpha

Better install and running documentation? care to edit the INSTALL file and pass it back to me; developers are always quite bad at docs anyway so I copied the current one from gaspachio.

> 2. I feel you should be able to double click or right click on devices to edit them. Or maybe the button needs to be next to them. Something, cause its not intuitive that you can even change the details nor how. And the stars are nice, but it is not obvious you can change them. And as mention, a guide to what they mean, or maybe a drop down instead would be better. And maybe it was just me, but the window was small and descriptions cut off.

a) Double click, right will do that to view more details
b) right click should have an edit entry right.
c) stars as mentioned

> 3. There should be an option to opt out for devices you are unsure what are, if they work, or just don't use. I don't want to give a score of 0 just because I didn't recognize it. Nor do I want to give a 5 to something I am assuming works, but may not even use. And along with this, hopefully you can have the names and details sync with the server at some point and then you can just confirm the "known" details of it and only have to change something when you had different results or the details are wrong. But I don't know how to do that, or what your plan was with that.

The opt out is: you don't have to rate things or set information for things you don't understand. simple as that. there isn't a need for a disruptive opt out because its passive anyway.

> I hope that is some helpful feedback. And it seems like it didn't detect a lot of my stuff. But I don't know how you are doing that, and some things may have been there but just called strange things, especially since its a laptop. Let me know if that is strange or what is the deal here.

It detected stuff is my guess but since there isn't a server to collect information from your not going to get much more information at the moment. the server is finished I just have to beg for someone to host it... still could be worse.

---

### Post by DoctorMO on 2007-03-05
As well as working on the above problems I've set up the beginnings of a wiki:

[http://dohickey.wikispaces.com/](http://dohickey.wikispaces.com/)

So if there are any kind souls who want to document a few things, including problems and feature requests please help yourself.

---

### Post by DoctorMO on 2007-03-06
OK Crashmaxx and maniacmusician the attached screen shots have a lot of your ideas in them.

I managed to find a way to get the motherboard thing to work although I would like it if some people were to test it and let me know by creating a screenshot and a log listing of list-hardware.py (comes with) for debugging if your motherboard is still split into a number of parts.

Couple of bugs left, one to do with firewire devices as you can see it says iPo instead of iPod. but the optical drive is now at the start and we have a computer information section as well as a welcome screen and a place to set what computer you have.

---

### Post by DoctorMO on 2007-03-06
Is anyone else trying this alpha? I need feedback to solidify the code and I'm working on some translation improvements so that should be interesting too.

---

### Post by DoctorMO on 2007-03-12
Hey all, it's me again the echo thread poster *hellow big empty caven of users*

I've personal invested in a web service to host dohickey and it's server implementation as a result I've redone the website (not a great deal but enough) and got us a spanking new home at [http://dohickey-project.com/](http://dohickey-project.com/)

I'm a terrible speller so it's most likely there are spelling mistakes in there.

also you can see the screenshots posted above there and I still need more people to post their complete device listings so I know the client won't chop hardware into little bits.

---

### Post by maniacmusician on 2007-03-12
> **DoctorMO said:**
> Hey all, it's me again the echo thread poster *hellow big empty caven of users*

I've personal invested in a web service to host dohickey and it's server implementation as a result I've redone the website (not a great deal but enough) and got us a spanking new home at [http://dohickey-project.com/](http://dohickey-project.com/)

I'm a terrible speller so it's most likely there are spelling mistakes in there.

also you can see the screenshots posted above there and I still need more people to post their complete device listings so I know the client won't chop hardware into little bits.
holy CRAP  martin, you've gotten a lot more done with that site. A wiki and everything, huh? Looking good. a hell of a lot faster than sourceforge as well.

---

### Post by Polygon on 2007-03-13
maybe you can negotiate and try to get your own sub-forum here so people can post bugs, give suggestions, and the like.

btw i tried the 5.2 release, it finally runs (lol) and the gui loads fine, the only thing that does not work currently is actually rating the hardware (clicking the stars does nothing... the rate button does nothing)

and what do you mean post complete device listings? post screenshots of what dohickey shows? or something else?

---

### Post by DoctorMO on 2007-03-13
> and what do you mean post complete device listings? post screenshots of what dohickey shows? or something else?

that is exactly what I mean, the 0.5.2 release has some bug fixes for motherboards but I only have one so it's not a very wide-ly tested bit of code. I need to make sure that your motherboard appears as a) a motherboard b) in once piece and c) doesn't eat any other devices by mistake.

The more people the better, and yes 0.5.2 I have disabled the ratings while I fix the shoddy translation problems; in fact you should see fields labelled 'SName' (sweedish) but that is to be expected with an alpha and things are coming along nicly.

this morning I got the perl site up, you can go to [http://dohickey-project.com/](http://dohickey-project.com/) and click on the administration link and request a user account, I'll see users on this forum get accounts to test the server side too.

Thanks for giving it a go Polygon

---

### Post by Polygon on 2007-03-13
the two attached pictures show exactly what dohickey displays for my computer

and consider asking ubuntu-geek or whatever for a sub forum, its going to be hard having everything related to dohickey in just one post :D

---

### Post by Iarwain ben-adar on 2007-03-13
I'm getting the same as Polygon..

When i try to go to preferences, i can't 'save' anything.


Iarwain

---

### Post by DoctorMO on 2007-03-13
> When i try to go to preferences, i can't 'save' anything.

Yes, that part isn't coded yet, sorry bit of a distraction while other things are fixed. I do beg your pardon.

> the two attached pictures show exactly what dohickey displays for my computer

Most interesting, your computer points out two problems, 1) that nforce motherboards aren't combined correctly and that 2) IDE zip drives arn't dealt with correctly.

Could you email me the output from list-hardware.py? I'll try and decode what information about nForce I have to go on. (Sometimes I think I'll just patch the kernel instead of messing around lol)

---

### Post by maniacmusician on 2007-03-13
neither 0.5.1 or 0.5.2 are working for me. I get this error:

```
Traceback (most recent call last):
  File "/usr/bin/dohickey", line 5, in <module>
    from Dohickey.fields.set import FieldsSet
  File "/usr/lib/python2.5/site-packages/Dohickey/fields/set.py", line 10, in <module>
    sys.exit(1)
NameError: name 'sys' is not defined

```
Pardon me if it's obvious, but I am kind of tired so thinking is slow tonight.

---

### Post by Polygon on 2007-03-14
> **DoctorMO said:**
> 
Could you email me the output from list-hardware.py? I'll try and decode what information about nForce I have to go on. (Sometimes I think I'll just patch the kernel instead of messing around lol)


attached is the output

---

### Post by DoctorMO on 2007-03-14
@All: see attached to see if your bugs are fixed (apart from the prefs which isn't coded)

@Polygon: Motherboard should apear now, if not email me

@MM: you should now see a real error as to what is wrong.

---

### Post by Crashmaxx on 2007-03-14
Great work I have to say. And I'm glad to help out, although I'm disappointed I don't see you getting a lot more help. Particularly when there is so much response in threads that end up wanting to do essentially what you are trying to do already.

Anyway, I tested 0.52 on the computer I just built. Some stuff showed up great. The GeForce 6200, the Dell 1100 printer, and the Intellimouse Explorer. Other stuff was good, but only for someone who built there own machine. I am pretty sure that is the correct hard drive model number, but if you didn't know that it would look odd. The wireless is the exact chipset and all, which I suppose is the best you could imagine you could get. And the USB DVD burner is totally vague, I don't remember it ever being called that. But the motherboard is still a mess. I don't know if its within reason to have it show as a Abit IS-85.

The interface is better though, but rate doesn't work now. And their seem to be less details I can enter about the part.

I hope that helps. And I think a lot of this stuff would be improved if it was connected to the proposed database and could cross reference that with what people have already identified. Good luck.

---

### Post by Polygon on 2007-03-14
i attached two screenshots of what dohickey shows after i installed the  updated version you posted doctor

---

### Post by DoctorMO on 2007-03-15
> i attached two screenshots of what dohickey shows after i installed the updated version you posted doctor

Hmm that doesn't look like the new one... perhaps I attached the old version by mistake let me double check EDIT ... yes the sdist didn't seem to update right, but this has all the right files (see attached)

> Great work I have to say. And I'm glad to help out, although I'm disappointed I don't see you getting a lot more help. Particularly when there is so much response in threads that end up wanting to do essentially what you are trying to do already.

This is a user forum and most importantly this is a user tool which means that A) users aren't in a position to program and B) normal programmers don't care about it because it's not technical enough; which is a shame because if they got into it they would see it's got some interesting technical ideas.

> Anyway, I tested 0.52 on the computer I just built. Some stuff showed up great. The GeForce 6200, the Dell 1100 printer, and the Intellimouse Explorer. Other stuff was good, but only for someone who built there own machine. I am pretty sure that is the correct hard drive model number, but if you didn't know that it would look odd. The wireless is the exact chipset and all, which I suppose is the best you could imagine you could get. And the USB DVD burner is totally vague, I don't remember it ever being called that. But the motherboard is still a mess. I don't know if its within reason to have it show as a Abit IS-85.

Yes it's working with the best data it can, could you email me the results of running the list-hardware.py script? just pipe it ./list-hardware.py > ~/Desktop/crashmaxx-list.txt and send us the file off your desktop.

> The interface is better though, but rate doesn't work now. And their seem to be less details I can enter about the part.

Yes thats not a surprise, 1) rate is disabled until further notice and 2) The fields aren't fixed you can add more, and sub fields too but no one seems to play around enough to figure it out, so while development in alpha continues I've not settled on one fields definition until everything is set in stone.

> I hope that helps. And I think a lot of this stuff would be improved if it was connected to the proposed database and could cross reference that with what people have already identified. Good luck.

Your pre-empting me good sir, take a look at dohickey-project.com what is the first thing you see? a search bar for looking up hardware. soon it will work and soon the browse feature will allow you to browse through  directories. it's all in hand but it's not instant and I needed feedback before I finished Everything.

---

### Post by Polygon on 2007-03-15
i dont think its installing right as i get the exact same thing with that one, where are the files installed to so i can just clear my system of dohickey and then reinstall freshly to see if it is working or not?

---

### Post by DoctorMO on 2007-03-15
You can always just run it from the install directory ./dohickey that will run that version, you can tell it's the new version because the pc icon should be there and the zip drive should say so.

To uninstall...  I'll build a deb file installer would that help?

---

### Post by Iarwain ben-adar on 2007-03-15
Hi DoctorMO,

I installed the updated version, and got a newer screen but it's still the same..

Except now i get these errors
> iarwain@iarwain-laptop:~/Desktop/dohickey-0.5.2$ sudo dohickey
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Loading dohickey-project.com/STATUS
Using server dohickey-project.com server is enabled.
Attempting to update pci:8086:27D0:27D2:27D4:27D6
Attempting to update pci:8086:27B9:27C4:27D8:27DA
Attempting to update pci:14E4:0592:0822:0832:0843:0852:1600:27A0:27B9:27C4:27C8:27C9:27CA:27CB:27CC:27D8:27DA
Attempting to update pci:8086:27B9:27C4:27DA
Attempting to update pci:8086:2448
Attempting to update pci:1180:0592:0822:0832:0843:0852:27A0:27B9:27C4:27C8:27C9:27CA:27CB:27CC:27D8:27DA
Attempting to update pci:8086:4222
Attempting to update usb:0B97:7761
Attempting to update pci:1180:0592:0822:0832:0843:0852
Attempting to update usb:0B97:7762
Attempting to update pci:10DE:0298
Attempting to update pci:8086:27D8
Attempting to update pci:8086:27B9:27C4:27C8:27C9:27CA:27CB:27CC:27D8:27DA
Attempting to update usb:046D:C01E
Attempting to update pci:8086:27A1
Attempting to update pci:14E4:1600
Attempting to update pci:8086:27A0:27B9:27C4:27C8:27C9:27CA:27CB:27CC:27D8:27DA
Attempting to update pci:8086:27C8:27C9:27CA:27CB:27CC
Attempting to update pci:8086:27A0
Attempting to update usb:413C:A005
Sending cgi-bin/hardware/update.pl to server.
Save Response:  404 Not Found
Save headers:  Date: Thu, 15 Mar 2007 05:24:21 GMT
Server: Apache/2.0.54 (Unix) PHP/4.4.4 mod_ssl/2.0.54 OpenSSL/0.9.7e mod_fastcgi/2.4.2 DAV/2 SVN/1.3.2
Vary: Accept-Encoding
Content-Length: 343
Connection: close
Content-Type: text/html; charset=iso-8859-1

LANG: ('nl_BE', 'UTF8')
Getting language for sv_se
LANG: ('nl_BE', 'UTF8')
Getting language for sv_se
LANG: ('nl_BE', 'UTF8')
Getting language for sv_se
LANG: ('nl_BE', 'UTF8')
Getting language for sv_se
LANG: ('nl_BE', 'UTF8')
Getting language for sv_se
Traceback (most recent call last):
  File "/usr/bin/dohickey", line 302, in preferences
    self.prefs = DoPreferences(self.config)
  File "/usr/bin/dohickey", line 325, in __init__
    self.initGUI()
  File "/usr/bin/dohickey", line 341, in initGUI
    if not self.config.has_key('servers'):
AttributeError: DoPreferences instance has no attribute 'config'
LANG: ('nl_BE', 'UTF8')
Getting language for sv_se
LANG: ('nl_BE', 'UTF8')
Getting language for sv_se
Traceback (most recent call last):
  File "/usr/bin/dohickey", line 242, in itemSelectModel
    item.setModel(model)
  File "/usr/lib/python2.5/site-packages/Dohickey/hardware.py", line 251, in setModel
    self.devices[0].setProperty('do.model', name)
  File "/usr/lib/python2.5/site-packages/Dohickey/device.py", line 60, in setProperty
    return self.device.SetProperty(pname, value, dbus_interface="org.freedesktop.Hal.Device")
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.Hal.TypeMismatch: Type mismatch setting property do.model on device with id /org/freedesktop/Hal/devices/pci_10de_298



Iarwain

---

### Post by Polygon on 2007-03-15
ok i ran it from the folder and now its just stuck on "loading"

> mark@ubuntu:~/Desktop/dohickey-0.5.2$ sudo ./dohickey 
Password:
Loading dohickey-project.com/STATUS
Using server dohickey-project.com server is enabled.
Traceback (most recent call last):
  File "./dohickey", line 152, in addItems
    self.hardware = hardware.List(mainConfig)
  File "/home/mark/Desktop/dohickey-0.5.2/Dohickey/hardware.py", line 31, in __init__
    dev = device.Device(udi, self)
  File "/home/mark/Desktop/dohickey-0.5.2/Dohickey/device.py", line 30, in __init__
    self.extend = DeviceStorage(self)
  File "/home/mark/Desktop/dohickey-0.5.2/Dohickey/device.py", line 181, in __init__
    self.set_type()
  File "/home/mark/Desktop/dohickey-0.5.2/Dohickey/device.py", line 204, in set_type
    self.icon = types[type][1]
IndexError: list index out of range


---

### Post by bravemosquito on 2007-03-26
Dohickey 0.5.2

```
root@a-desktop:/usr/local/dohickey/bin# ./dohickey
Traceback (most recent call last):
  File "./dohickey", line 3, in <module>
    import Dohickey
ImportError: No module named Dohickey
```

I'm really :confused:

---

### Post by DoctorMO on 2007-03-28
That is quite interesting, forgive my delay in responding to your errors polygon, Iarwain ben-adar and bravemosquito.

Firstly there is an up and coming 0.6 release that I'm sure you'll all enjoy testing (screenshot attached) with much improved GUI and organisation including multiple language support.

bravemosquito - you install seems to have gone a bit weird, it'll expect the python libs in either the current directory or the normal libs directories on env. try and run from the package directory and let me know what distribution your using.

Polygon - That looks like the zip drive problem, fixed ages ago but not released yet.

Iarwain ben-adar - did you try and set the model of a device to get that error?

---

### Post by Iarwain ben-adar on 2007-03-28
I tried about anything and just got those errors..


Iarwain

---

### Post by DoctorMO on 2007-03-28
I'm sorry to hear your having such problems Iarwain, if you wanted to be daring you could download the cvs version: [http://dohickey-project.com/client/download.shtml](http://dohickey-project.com/client/download.shtml)

I have a question for everyone in my current layout I have the view mode as a separate window, you click on an item then the view button and it pops up a window with all the information.

I was thinking is it better to have a popup panel to the right of the tree view that appears when you click on an item?

Compare the attached screen-mock with the above screenshot and tell me which one is better.

---

### Post by Iarwain ben-adar on 2007-03-28
Hi there,
i tried installing via cvs, but i get this error:
> iarwain@iarwain-laptop:~$ export CVSROOT=:pserver:anonymous@dohickey.cvs.sourceforge.net:/cvsroot/dohickey
iarwain@iarwain-laptop:~$ cvs login
Logging in to :pserver:anonymous@dohickey.cvs.sourceforge.net:2401/cvsroot/dohickey
CVS password:
iarwain@iarwain-laptop:~$ cvs -z3 co -P dohickey-client
cvs server: cannot find module `dohickey-client' - ignored
cvs [checkout aborted]: cannot expand modules
iarwain@iarwain-laptop:~$    


Iarwain

---

### Post by DoctorMO on 2007-03-28
you've used a dash instead of an underscore.

---

### Post by Iarwain ben-adar on 2007-03-28
Well now, 
with that pretty stupid mistake out of the way,

The program gives me the wrong pc :?
I can't rate anything aswell..

> iarwain@iarwain-laptop:~/dohickey_client$ sudo ./dohickey
SERVER: dohickey-project.com ONLINE:READ
SERVER: dohickey.localhost DISABLED
SERVER: not.a.real.server DISABLED
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Attempting to update pci:14E4:1600
Attempting to update pci:10DE:0298
Attempting to update usb:0B97:7761
Attempting to update usb:0B97:7762
Attempting to update pci:1180:0852
Attempting to update pci:8086:4222
Attempting to update usb:046D:C01E
Attempting to update motherboard:dell:27DA
Attempting to update usb:413C:A005
Traceback (most recent call last):
  File "./dohickey", line 322, in itemClicked
    self.viewSelection(view)
  File "./dohickey", line 343, in viewSelection
    self.infowindow = ViewerGUI(item, self)
  File "/home/iarwain/dohickey_client/Dohickey/viewer.py", line 26, in __init__
    self.fields = HardwareFields(None)
TypeError: __init__() takes exactly 1 argument (2 given)
Traceback (most recent call last):
  File "/home/iarwain/dohickey_client/Dohickey/preferences.py", line 70, in savePrefs
    self.closeWindow(widget)
AttributeError: PreferencesGUI instance has no attribute 'closeWindow'
Traceback (most recent call last):
  File "./dohickey", line 322, in itemClicked
    self.viewSelection(view)
  File "./dohickey", line 343, in viewSelection
    self.infowindow = ViewerGUI(item, self)
  File "/home/iarwain/dohickey_client/Dohickey/viewer.py", line 26, in __init__
    self.fields = HardwareFields(None)
TypeError: __init__() takes exactly 1 argument (2 given)
iarwain@iarwain-laptop:~/dohickey_client$     


Iarwain

---

### Post by DoctorMO on 2007-03-28
Er a screen shot would be nice, what computer where you expecting? and yes you just downloaded the pre alpha cvs, it bound to not work. you didn't answer my original question about design, which is better the side view or the separate window?

---

### Post by Iarwain ben-adar on 2007-03-28
Euhm,

I find the new dohickey nicer :D

And i am using a Dell XPS M1710


Iarwain

---

### Post by DoctorMO on 2007-03-28
Ah yes your computer is defined and correct, only the information stored in your bios isn't what you think it is; thanks to the id though when you edit the computer node you'll be able to correct this information.

The side panel is good or the one you have now (the separate window)?

---

### Post by Iarwain ben-adar on 2007-03-28
I like the window as it is now :D


Iarwain

---

### Post by bravemosquito on 2007-03-28
> **DoctorMO said:**
> bravemosquito - you install seems to have gone a bit weird, it'll expect the python libs in either the current directory or the normal libs directories on env. try and run from the package directory and let me know what distribution your using

I'm with Feisty from a couple of days. Updated every 4 hours by hand...
Whatever, I just ask you is there any chance to be released a .deb package?

For the problem I just tested it from /home and package dirs with the same error...

---

### Post by DoctorMO on 2007-03-28
bravemosquito, it would take me 5 seconds to produce a deb install; but I won't because it's pre 0.6 and the code is in a transitional state. so you will get your wish with 0.6 because I'll also be testing delivery methods and putting icons in the gnome/kde menus etc.

---

### Post by slimdog360 on 2007-03-30
Okay so Ive installed it. Ive got it up and running via the /usr/bin/dohickey script, now what? Im unable to rate anything, though it will let me edit my computer type. But I didn't do this as its custom built.

I suppose my question is, what now?

edit: I should have mentioned that I browsed through some of your code and I must say you have done a nice little job of it. Couple of things I may have done differently but its still pretty good. Better then what I could have done.

---

### Post by %hMa@?b&lt;C on 2007-03-30
> **slimdog360 said:**
> Okay so Ive installed it. Ive got it up and running via the /usr/bin/dohickey script, now what? Im unable to rate anything, though it will let me edit my computer type. But I didn't do this as its custom built.

I suppose my question is, what now?

edit: I should have mentioned that I browsed through some of your code and I must say you have done a nice little job of it. Couple of things I may have done differently but its still pretty good. Better then what I could have done.

same exact thing for me.

---

### Post by DoctorMO on 2007-03-30
Er right, now you wait for 0.6 I think; you've got the choice of either, downloading the cvs version and having a play with that to look at the development direction or just seeing if you can help out in any way.

I not only need some svg images of a cpu, pci card etc in order to make the graphics better (icons and images defaults) but anyone who can read code and offer even suggestions for what you consider could be done better is worth having.

I'll give you a few pointers as to the direction and the use you can get from the application when it's done:

* You'll be able to cataloug your hardware, including all of it's information and have some fun expanding the information structures if your that sort of person.
* You can use if for general enqueries to see what is in the computer since it will attempt to download hardware profiles for detected hardware and thus give you more information.
* You should have access to a new feature for quering the database for the best hardware upgrade path (this includes the new feature of being able to switch on empty slots, mem, pci, cpu etc) which should be good for non hardware technical users.
* CPU, Memory, Motherbaord and a couple of other things are improved.

Suggestions are welcome.

---

### Post by %hMa@?b&lt;C on 2007-03-30
I would love to help, but I am still on the "STRINGS" chapter from my python book, I read about 1/2 a section a night, I am on the 6th.  I would be happy to do graphics for you though!

---

### Post by DoctorMO on 2007-03-31
> I would be happy to do graphics for you though!

Checkout open clip art see if they have good images, reform what ever you need to to make it all the same style.

PCI Card (no sockets), PCMCIA Card, Hard Drive, CD ROM Drive, USB Memory Stick, CPU, Memory Stick, ISA Card, AGP card and then I'll use the blue box existing vector image as a total fallback,

---

### Post by plb on 2007-03-31
Hrm, DoctorMo...is that any relation to Doctor Who? =)

---

### Post by Yfrwlf on 2007-04-14
Doing awesome work DoctorMO, I'll certainly contribute hardware functionality information to your project at some point, and I'm sorry I don't have the time to help out more but I'm too focused on my own project.

Keep it up!! :)

---

### Post by DoctorMO on 2007-04-14
Ah well you should see the latest code, so clean and fresh and modular. will be a real treat.

---

### Post by zorkerz on 2007-11-12
Is there a current thread in ubuntu forums for dohickey? I have not found one from searching yet. This thread [http://ubuntuforums.org/showthread.php?t=451470&highlight=dohickey](http://ubuntuforums.org/showthread.php?t=451470&highlight=dohickey) has the most recent post but it has been closed. I have a similar problem mentioned on the thread and am trying to install from cvs.

thanks

---

### Post by DoctorMO on 2007-11-12
zorkerz: hey there, thanks for giving the cvs version a try, I'm working through moving the project to launchpad but while that is pending can you report the bug in sourceforge:

[http://sourceforge.net/tracker/?group_id=177020&atid=879565](http://sourceforge.net/tracker/?group_id=177020&atid=879565)

I can track is properly then, there isn't a consolidated thread in ubuntu forums for this project, just a dispersed few announcement threads, we have mailing lists that I encourage everyone interested in the project to sign up to; they're ultra low verging on desolate lists. so don't worry about being overwhelmed, all problems and talk can be directed there.

---

### Post by zorkerz on 2007-11-15
How do I use the CVS version?
I don't really know much about CVS in general, I really just starting in that realm.
thanks

---

### Post by DoctorMO on 2007-11-15
The CVS version is the current version being developed on so it's in constant movement; there is instructions for downloading the cvs version here:

[http://dohickey-project.com/client/download.shtml](http://dohickey-project.com/client/download.shtml)

---

### Post by zorkerz on 2007-11-15
sorry I have found that page installed cvs and entered the three commands.

I just pressed enter when it asked me for a password, is that ok?

I guess what I really just don't know how/if i am now using the cvs version. 

If i open dohicky from applications -> system tools or by 'dohicky' in a terminal the about says I am using version 0.6.1. Previously I had installed 0.6.2 but it does not show up as that.

---

### Post by DoctorMO on 2007-11-15
sorry yes you need to use the terminal to bring up the cvs version

cd dohickey-client/
sudo ./dohickey

That should load the cvs version.

---

### Post by zorkerz on 2007-11-15
Oh this is great im not getting the error I had with the normal version. I will mess around and see what i can come up with.

also mine goes to dohickey_client/ not dohickey-client/

looks like a miss timed shift. :~)

---

### Post by DoctorMO on 2007-11-15
What are you up to again? It's good that you've gotten it to work too :-)

---

### Post by zorkerz on 2007-11-15
nothing yet. Ive kinda crazily decided to learn python in the last week as my first programming language. Been using ubuntu since its beginning but wanted to do some programming. So really I just want to get a feel for what a real program looks like and bumped into dohickey which i find an interesting idea so i thought I start there.

---

### Post by matchstich on 2008-05-25
ok, i installed 8.04 on another machine.  installed dohicky.

also got an update. for dohicky.  is that normal.

thanks

---

