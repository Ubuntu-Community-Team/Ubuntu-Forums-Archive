---
title: "Spanish Bible Software"
date: 2007-09-23
forum: Ubuntu Christian Edition
---

### Post by egtech on 2007-09-23
I am a missionary in a Spanish speaking country. I am working with the pastors there and trying to get them software and computers to work with. We have some older laptops and have been looking at loading them up with Ubuntu set up in Spanish. That will work good, cause it lets them check e-mails online and write documents and things. The problem is I would also like them to have some Bible study software on there. I know there are some Bible software projects out there, but I am wondring if there is some that not only have Bibles for the software in Spanish, but also the interface of the software program is in Spanish as well. That way when they have Ubuntu in Spanish on the laptop all the programs, especially the Bible program they will be able to read in Spanish. I think this would really be a big help to them for studying the word. Please write me and let me know if such a thing exists and how I can get it on thier Spanish enabled Ubuntu laptops.

THanks

---

### Post by jonathonblake on 2007-09-23
[QUOTE=egtech]The problem is I would also like them to have some Bible study software on there. I know there are some Bible software projects out there, but I am wondering if there is some that not only have Bibles for the software in Spanish, but also the interface of the software program is in Spanish as well. [/quote]

I thought that both Bibletime and GnomeSword were available with a Spanish UI.  I don't see the language packs on either Sourceforge or Crosswire.  :(

Nor I don't know how much material for them is available in Spanish. :(

e-Sword has a number of resources in Spanish, but the UI is in English. I'm not sure if Rick will rewrite e-Sword so that it can have a UI in a language other than English.  OTOH, some of the utility programs have a Spanish UI. There is some documentation for using e-Sword in Spanish. There are three yahoogroups in Spanish for e-Sword support.   

xan

jonathon

---

### Post by egtech on 2007-09-25
> **jonathonblake said:**
> I thought that both Bibletime and GnomeSword were available with a Spanish UI.  I don't see the language packs on either Sourceforge or Crosswire.  :(

Nor I don't know how much material for them is available in Spanish. :(

e-Sword has a number of resources in Spanish, but the UI is in English. I'm not sure if Rick will rewrite e-Sword so that it can have a UI in a language other than English.  OTOH, some of the utility programs have a Spanish UI. There is some documentation for using e-Sword in Spanish. There are three yahoogroups in Spanish for e-Sword support.   

xan

jonathon

Thanks I appreciate the response. So where do I get these programs and how do I install them in Unbuntu??

---

### Post by jonathonblake on 2007-09-25
[QUOTE=egtech]So where do I get these programs and how do I install them in Unbuntu?[/QUOTE]

They are included in *Ubuntu Christian Edition*.

The e-Sword installer can be downloaded from
[http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html](http://www.whatwouldjesusdownload.com/christianubuntu/2007/05/popular-packages.html)
(Note: A working Internet connection is required to install e-Sword)

GnomeSword and other programs that use the Sword Project API are listed in Synaptic. I just found the Spanish language pack for the Sword Project API in synaptic.

For GnomeSword and the other programs that use the Sword Project API, you may have to add repositories, for the Spanish material. (I don't remember how to that, or what the URLs for the other sword project resource repositories are.)

For e-Sword, you'll have to download the other Spanish resources from various sites, than use the module installation program.

My suggestion would be:
* Install the e-Sword Spanish language resources into a Windows computer;
* Burn a copy of the e-sword directory to CD or DVD;
* Copy from the CD or DVD to the e-Sword directory on the Linux box;

xan

jonathon

---

### Post by egtech on 2007-09-28
Well, not sure if I mentioned it before, but I am new to this Ubuntu stuff. I gotta tell you I do not get it. I have tried and tried and wasted days, but I canthinnot figure  out how to install stoftware on this thing. I am trying to download and install the Bibletime and Gnomesword program, have not even looked at the E-sword yet, and I have no idea how to install any of it. You have to go from site to site and look for this part and that part and then save them and add them tp repositpories or something like that, then compile them and then configure and what not. Why are things so difficult in Ubuntu?? Why are there just not executable files you download and install. I am really thinking to give up willll this. I am a computer tech (PC) and I c  would probablyannot figure this out, I cannot imagine what a regular computer user would do. They would probably give up. Please Help. Is ther some place that give a general, what to do to install program. What is the syntax?? About ready to give up on this. Thanks

---

### Post by jonathonblake on 2007-09-28
> **egtech]
I am trying to download and install the Bibletime and Gnomesword program, have not even looked at the E-sword yet, [/quote]

">Start >System >Administration >Synaptic Package Manager"

When Synaptic is open, then ">Edit >Search" or <CTRL><F> will open the search screen.

Type "sword" in the search bar.  Hit<ENTER>.
Scroll down until you find "BibleTime".  Click on that.Then click "Mark for Installation" said:**
>  You have to go from site to site and look for this part and that part and then save them and add them tp repositories or something like that, 

All of the non-Windows software that Ubuntu Christian Edition has installers for, is listed in the repositories for Ubuntu, and Kubuntu.  

The only Bible Study tool that might require one to go search from site to site is e-Sword.   I say "might", because there is no central repository of user created resources for e-Sword. All official resources can be found at either  e-sword.net or eStudySources.

IOW, the only repository you might have to add for Ubuntu/Kubuntu, is the one for Ubuntu Christian Edition, and then only if you want to run the Windows Software on your Linux box.

If the issue is with software distributed for another distro, then look at this way:  Would you expect to obtain science lab equipment from K-Mart?  

> then compile them and then configure and what not. 

The only time you need to compile something are:
* When you have modified the source code;
* When you are using the absolute bleeding edge of a program;

> Why are things so difficult in Ubuntu?

From your description, it looks like you deliberately made things more difficult for yourself.

>  Why are there just not executable files you download and install. 

Given a choice between installing software on an Ubuntu box, and on a Windows box, I'll take the Ubuntu box any day of the year.   

Here is why:
* Using Synaptic,I can easily find programs that have been compiled , and are known to work with Ubuntu.  Or,if I am feeling adventurous, I can search Google,Freshmeat,Sourceforge, etc.  
* For Windows, if I want FLOSS, I either have to know the specific name of the program, or do boolean searches on Google, Tucows, Sourceforge, and half a dozen other sites. (I'll also point out that if find something on sourceforge, odds are that I will have to compile it for Windows.  Linux binaries are usually available;
* For non-FlOSS, I have to know the specific name of the program, regardless of platform.   
* For non-FLOSS software, if I run into an issue, I have to find the software support site, and pay for support;
* For FLOSS software, if I run into an issue, there usually is a support group, with a FAQ, that will be able to help solve the problem. There are some exceptions,but those occur either with arcane issues, or a11y related issues.  

(I've received far more help with a11y issues from users group, than from paid support. from the vendor. (This includes _Freedom Scientific_.) )

(Remember the days of WangWriter: It was fairly common for users to ask how to use it as a spreadsheet.  The typical response from Wang Support was "You can't".  Whereupon somebody in the audience would stand up, and give step by step instructions on how to create and use spreadsheets, using WangWriter.)

> I cannot imagine what a regular computer user would do. 

My experience is that regular users find it easier to use Ubuntu, than to use Windows.

> They would probably give up. Please Help. Is their some place that give a general, what to do to install program. 

Have you looked at [https://help.ubuntu.com/](https://help.ubuntu.com/)
Or more specifically:
* [https://help.ubuntu.com/7.04/add-applications/C/index.html](https://help.ubuntu.com/7.04/add-applications/C/index.html)
* [https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
* [https://help.ubuntu.com/community/CommonQuestions](https://help.ubuntu.com/community/CommonQuestions)
* [https://help.ubuntu.com/community/CommonQuestions#head-6be30a969fe9cb743f9da5148db0f5b89409ee3d](https://help.ubuntu.com/community/CommonQuestions#head-6be30a969fe9cb743f9da5148db0f5b89409ee3d)
* [https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
* [https://help.ubuntu.com/community/Applications](https://help.ubuntu.com/community/Applications)
* [https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)
* [https://help.ubuntu.com/community/Software](https://help.ubuntu.com/community/Software)
* [https://help.ubuntu.com/community/SoftwareFromOtherOperatingSystems](https://help.ubuntu.com/community/SoftwareFromOtherOperatingSystems)

xan

jonathon

---

### Post by egtech on 2007-09-29
JOn,

Thanks for your reply. 

FYI I am not trying to make this more difficult than it is. It is different than what I am used to and in a way it makes no sense. I can see that you have used it for quite some time and you "get it", good.

 I really do appreciate your help and it is really good help, you need to have them put it on the first page of the area where people want to add new programs. 

I apologize if I am a person that seems too slow for you, but I do appreciate your help and time and efforts.

God Bless

---

### Post by jonathonblake on 2007-09-29
> It is different than what I am used to and in a way it makes no sense

This is the difference between learning general principles,and learning for a specific task on a specific system.  (This is also the reason that HR departments consider me to be computer illiterate.  I do not "know" any specific software. That I can teach people how to use any software I've **never** heard of, the first time I use it, is irrelevant.)

> 
I can see that you have used it for quite some time and you "get it", 

Operating systems I've used:
* Ubuntu Christian Edition:  6 months;
* UCSD P-System:  3 years;
* DrDos 5.0 : 1 year;
* DrDos 6.0 : 2 years;
* DrDos 7.0 : 4 years
* DrDos 7.01 :  10 years;
* DrDos 7.03 : 5 years;
* Win2K : 7 years;
* Win NT 3.5 : 1 year;
* Win NT 4.0 : 1 year;
* OS 2 Warp 3.0 : 1 year;
* Win XP : 1 Year;
* Red Hat 5.2:  5 years;

I'll let somebody else decide if I've used Ubuntu Christian Edition for  "quite some time".

Most of my life I have had at least two, and usually three systems in simultaneous use on my desk.

> 
 you need to have them put it on the first page of the area where people want to add new programs. 

Maybe Jeremy can do that.  :)

xan

jonathon

---

### Post by pwn2king on 2008-04-29
Greetings Egtech: Don’t give up on Ubuntu, it has gotten much better with the new release. What country are you in? I am currently using BibleTime which is available on Add/Remove. 
It is a good program, but the versions do not containt Reina Valera 1960, which is the more popular one. I find the antigua to be just that sometimes. But what it does have is useable, as it has a search function which is indenspensable. 
Just type “Bible” in the search box and it will take you to what is available. The programs in the Add/Remove don’t need as much tweaking, or so I have found. 
I’m also surfing the net for any ubuntu friendly programs. Plus if you have some like Caribe, they may work under the WINE program, also available on Add/Remove, and you can also go to their webpage. If like me your still not proficient in installing linux programs, it is good to stick to the ones on the Add/Remove and practice as time permits. 
WINE is able to run windows programs, but not all. 
Ubuntu may drain your brain, but not your wallet. I’ve re-installed it six times already, just from over tweaking it. But hey that is part of learning. 
Hope this helps. Dios te Bendiga.

---

### Post by shane2peru on 2008-04-30
> **egtech said:**
> JOn,

Thanks for your reply. 

FYI I am not trying to make this more difficult than it is. It is different than what I am used to and in a way it makes no sense. I can see that you have used it for quite some time and you "get it", good.

 I really do appreciate your help and it is really good help, you need to have them put it on the first page of the area where people want to add new programs. 

I apologize if I am a person that seems too slow for you, but I do appreciate your help and time and efforts.

God Bless

egtech,

I know exactly where you are coming from.  Here is what I have found, [The Word]("http://www.theword.gr")  is the program you are looking for.  It is for windows, but runs very well, and very easily under wine.  Also there is a Spanish Language file to change the interface of the program to Spanish, if you can't find it, let me know and I can send it to you.  You will want to get the version 3 beta, it is a great program.  If you need any help post back and let me know and I can see what I can do to help.  Also there is an import program that lets you import e-Sword modules that are made by users.  That actual e-Sword modules are password protected, and protected by a copyright to protect the format they are in.  However the user modules you are able to import.  Works great. 

Shane

---

