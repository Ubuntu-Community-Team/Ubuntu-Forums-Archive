---
title: "samba/smb.conf   text not in there"
date: 2014-08-01
forum: Virtualisation
---

### Post by firas2 on 2014-08-01
Good day I am trying to do the HOW to  for samba File server 

and I go to                          /etc/samba/smb.conf:     to change 
  workgroup = EXAMPLE
   ...
   security = user

but cant find   ( security = user )


any help 

thank u

---

### Post by TheFu on 2014-08-01
Add it to the file, if that is the setting you want.

---

### Post by firas2 on 2014-08-01
> **TheFu said:**
> Add it to the file, if that is the setting you want.


Oh ok thanks   an other thing it wont let me save it 

it says u dont have permission   

I dont know but i am struggling with ubuntu      I have been fallowing the how to's  but every time there is some thing 

either text is not there or it say directory does not exist

Im Suffering here :mad:

---

### Post by TheFu on 2014-08-01
Ubuntu is a multi-user system, like all UNIX-based systems.
Files stored in /etc/ are system-wide settings, so access for normal end-users is only read, not write. There are other places in the file system protected like this too.

To modify/create a file under /etc, you need to ask for elevated permissions - that is done with sudo.  Do not use sudo with a GUI program.  Hopefully, this helps. [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by firas2 on 2014-08-02
Ok after editing   the   samba/smb.conf     file   

I now have  2 of them  I dont understand   witch one should i delete ??

please look at PIC 

thank u

---

### Post by TheFu on 2014-08-02
GUIs hide too many details to know which is correct, but the samba process will only look at /etc/samba/smb.conf by default. You can change that, if you like, but I never do and don't know anyone else who does unless they are testing some new, strange, odd, weird, config.

So - open a terminal, cd to the directory and post the output from **\ls -al**, please.  Text only, no pictures!

---

### Post by firas2 on 2014-08-02
Ok in the setting up samba   how to

is says     

[LIST]
[*]                                First, edit the following key/value pairs in the *[global]* section of          /etc/samba/smb.conf:         
                          workgroup = EXAMPLE
   ...
   security = user
                               The *security* parameter is farther down in the [global] section, and is commented by default.         Also, change *EXAMPLE* to better match your environment.           


But i cant find any where  were it says    

security 

any help

and i use pictures to make the reader understand what i am saying
[/LIST]

---

### Post by TheFu on 2014-08-02
Edit the file. ADD THE line you want, into the section you want. I don't understand the issue.  Sorry, it is my failure in understanding, not yours.

If the how-to you are referencing isn't working, perhaps finding a different, easier-to-understand one is necessary?  There are thousands of samba how-tos. For simple configurations, this is extremely well-understood territory. If editing a file is too hard, there is a gui way:
[http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/](http://www.howtogeek.com/74459/how-to-create-samba-windows-shares-in-linux-the-easy-way/)  I like the how-to guides there - they find the easy ways, keep it simple and to the point and don't get distracted by complexities that I often get into, which are not needed for 90% of the users.

---

### Post by firas2 on 2014-08-03
@[COLOR=#000000]theFu   I fallowed the Link u provided   and did install samba   But when i click on it to start the program  ,, it wont open 

so something got to be wrong    Please not that i am using  ubuntu 14.4 64x

the other thing is   I cant find any line where it says   SECURITY   in the samba.conf   file    

[/COLOR][COLOR=#000000]is says [/COLOR]


[LIST]
[*]First, edit the following key/value pairs in the *[global]* section of /etc/samba/smb.conf: 
workgroup = EXAMPLE
...
security = user
[/LIST]
[COLOR=#000000]

Do U see where it says   [/COLOR][COLOR=#000000]security = user    ????    I dont have   security   there fore i cant add that Line ;)
[/COLOR][COLOR=#000000]
thank u 
[/COLOR]

---

### Post by TheFu on 2014-08-03
I've asked for a few thing to help you solve the issue(s). These have not been provided. I will try again in the simplest English I know.

Add the missing line to the file, if that is the setting you want. How?  
* Edit the file with elevated privileges (sudo nano /etc/samba/smb,conf)
* Create an empty line somewhere inside the [Global] section
* type in "security = user" without the quotes.
* save the file
* exit the editor

Now the line exists inside the file.  Of course, you can use any CLI editor you like - do not use a GUI editor with sudo. There are reasons and for someone so new to Linux, fixing any problems it causes will be too hard. 

However, the last message says "something got to be wrong" - but does NOT provide any clue. Why not?  What are the errors? Please copy/paste them or we cannot help. What do the log files say?

BTW - you never provided a link to the "how-to" you were using.  I'd ask how you expect us to know what might have gone wrong without that slight detail?

---

### Post by Morbius1 on 2014-08-03
>  BTW - you never provided a link to the "how-to" you were using.  I'd ask  how you expect us to know what might have gone wrong without that  slight detail?                 
I might be able to help with that part ;)

Of all the HowTo's out there on samba the one that was chosen was the worst: [https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)

---

### Post by firas2 on 2014-08-03
@TheFu  thank u sir for taking the extra time and effort to help me out 

i did as u asked as far as editing the file    but still no luck  

i have been reading and reading and searching for a good 2 days   I really cant find the TUT that i had problems with 

any way I have don a fresh install of KUBUNTU   after some other members explained to me what I am missing 

please take a fast look here , this might make u understand my Confusion 

 [http://ubuntuforums.org/showthread.php?t=2237629&p=13089607#post13089607](http://ubuntuforums.org/showthread.php?t=2237629&p=13089607#post13089607)

many thanks TheFu   and also since i have a fresh install of KUBUNTU  I did not add any thing or tried any thing yet

please if u have any recommendations  or advices that i can use on my new  journey    with  ubuntu/kubuntu    your help is much appreciated

---

### Post by firas2 on 2014-08-03
Yes thats the one yes thank u

---

### Post by firas2 on 2014-08-03
> **Morbius1 said:**
> I might be able to help with that part ;)

Of all the HowTo's out there on samba the one that was chosen was the worst: [https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html](https://help.ubuntu.com/10.04/serverguide/samba-fileserver.html)


[COLOR=#000000]Yes thats the one yes thank u[/COLOR]

---

### Post by TheFu on 2014-08-03
So I read that other thread - I'm understanding more of where you are coming from.  Most people new to Linux start simple, stay simple, learn the basics for 3+ months before doing the things you seem to be trying.  Doing new things is a way to learn, but starting with the basics is important.

Fewer people run KDE than Unity, so there will be fewer people able to respond to any questions that are KDE specific. Since you are new, you won't be able to tell which is specific or not. I don't use either, so when it comes to new-GUI questions, I'm useless. OTOH, I was an X/Windows programmer for 3 yrs, so for old-school GUI questions I can help.

There is no shortcut that I know to knowledge, but reading from hundreds of different sources can be confusing. Even the online how-tos here can be out of date, but that normally relates to the GUI versions only. The CLI (shell or command line) versions generally do not change much over years. I have scripts originally written for AIX, HP-UX, Solaris, SunOS, Iris, OSF/1 that work unchanged on Linux and Ubuntu.  This is the main reason that I prefer the CLI solutions over the point-n-click ones, which change every year or so.

I've been using/running/administrating Linux since 1993. The way I learned was hard-won effort and reading the manpages.  In the old days, manpages had examples that were useful, then the UNIX world decided to end that practice, since many new users were copy/pasting these examples without understanding and trashing their systems. That is still a danger with how-to guides today. People blindly copy/paste without understand. That is careless and can be dangerous.

So, now it is up to you to determine if customizing the desktop now is the path you wish to take or if learning the basics is where to start.

I think a book on Ubuntu and starting with the common GUI is smart for you at this stage.  Here is a link to a 1-page version of the [Ubuntu Desktop Guide]("http://ubuntuguide.org/wiki/Ubuntu:Trusty"). Save it do your desktop and start from the beginning - skim every page to learn what it covers - so you know what is possible and get a feel for how things are accomplished. There is a section on samba in there too, but based on the failures previous, it is doubtful this will work on your system either.

Last, be wary of any "download this .deb file" instructions.  Installation in that manner can break package management dependencies and will lock specific versions of other packages on the system. Eventually, it will be "bad." If not in a week, in a month or year. Your system will not be update-able. Try to use the official versions in the repos first, then go to a PPA next. Only as a last resort, but full knowledge of the future issues should you install from .deb files - plus you will be required to manually maintain that software going forward ... or not.  This leads to be in "rpm hell" or "apt hell" - and is common.  "*With great power comes great responsibility.*"

If you still want to get samba working and the other guides (how-to geek and ubuntu guide) don't work, we can start fresh. Run **testparm** and post the output please.

---

### Post by firas2 on 2014-08-03
WOW TheFu  Now we are talking   many thanks for this perfect explanation  I am starting to understand what ur talking about , Much better ,  all I wanted from Samba was to make it easy for me  to Transfer Files FROm  ubuntu on my Virtual machine to my physical machine ,,,,   after all this going back and forth  , I learned that i can just copy and past any file I want on My Physical Machine  :) 

*for now I am playing  with Kubuntu   I like the desktop  *:p   
[I]
I will defiantly be asking u about some more Questions as they come along  ,, If that is ok with u ,,

[/I]:P

---

### Post by TheFu on 2014-08-03
a) If this is solved, please mark the thread as solved. I cannot tell from your replies. Clear statements are needed.

b) Please do NOT PM me unless it is for paid support. I try to respond here to subjects that I know something about, as my time allows.  You can definitely ask questions in these forums, but I hope you will start with that book I linked above.

---

### Post by firas2 on 2014-08-03
Ok i will mark it as solved 

2 i did not pm U all i did is add u to my contacts   if u like u can remove it 

3 yes thank u for the link   i will get to it very soon 

thanks

---

