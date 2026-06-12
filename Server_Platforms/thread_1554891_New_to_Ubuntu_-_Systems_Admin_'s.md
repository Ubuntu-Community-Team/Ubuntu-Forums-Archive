---
title: "New to Ubuntu - Systems Admin ?'s"
date: 2010-08-17
forum: Server Platforms
---

### Post by timberline1 on 2010-08-17
Howdy,
 
so currently we have a windows AD environment consisting of:
 
4 main locations across the city attached by VPN consisting of:
4 server2003 domain controllers
>DNS
>Active Directory
>DFS
>print servers
2 server2003 file servers
>proprietary software
3 server2003 backup servers
>backups only
250+ windows desktops
50+ windows laptops
 
use office 2003-2007
use microsoft forefront for security.
 
 
QUestions:
 
1. would it be feasable to change over to an Ubuntu environment without losing any functionality or security?
2. would it be wise to do so if possible?
3. how long would it take to do the change over, if possible?
>>** ALSO** I manage all of that by myself.
4. How do i go about getting the change over done? is there a location i can get a walkthru?
5. how hard would it be to learn Ubuntu sys admin?
 
thank you very much for your help,
 
Timberline tech

---

### Post by aeiah on 2010-08-17
your main issue is going to be with active directory. get a list of what you use active directory for and see if its supported in linux

if you're pretty new to linux and you're planning on single-handedly switching over such a large network make sure you do a lot of homework :p

to be honest, you'll probably find active directory support in linux isn't up to scratch for your uses. DNS, backup, printing etc will probably be easier than under windows though.

you'll still need an enterprise anti-virus solution and you'll probably find that has to be run on a windows server rather than a linux one.

all these things together mean that it might be best to fork over the cash for windows 2007, as much as it pains me to say. it just depends how much of a change to your current systems you're willing to go through

---

### Post by koenn on 2010-08-17
> **timberline1 said:**
>  
QUestions:
 
1. would it be feasable to change over to an Ubuntu environment without losing any functionality or security?
2. would it be wise to do so if possible?
3. how long would it take to do the change over, if possible?
>>** ALSO** I manage all of that by myself.
4. How do i go about getting the change over done? is there a location i can get a walkthru?
5. how hard would it be to learn Ubuntu sys admin?
 

Answers:

1- No
2- wrong question. What do you hope to achieve by changing over ?
3- depends on your skills or the skills of the people you hire to do this
4- if you need a walkthru for that sort of complete migration, you can't do it. Heck, if you even think there would exist a walkthru that describes how your unique, specific IT environment, you're the wrong person to be doing this. Ask Canonical, the probably have people that can handle this for you.
5- about as hard as learning Windows sysadmin. 

re Answer 1-
security shouldn't be a problem (provided you adequately deal with question 5)
for functionality, you mention AD, DFS and some undefined "proprietary software". If you're expecting drop-in replacements, forget about it. 
If you're capable of analysing your software needs while making abstraction of your current solutions, you  might find that you can cover those needs with linunx software.

---

### Post by timberline1 on 2010-08-17
1- No
2- wrong question. What do you hope to achieve by changing over ?
[COLOR=red]A friend has been preaching the wonders of Ubuntu so I thought i would check it out. ultimately i would like to free up more resources on our servers and work with a more secure/stable system than windows.[/COLOR]
3- depends on your skills or the skills of the people you hire to do this
4- if you need a walkthru for that sort of complete migration, you can't do it. Heck, if you even think there would exist a walkthru that describes how your unique, specific IT environment, you're the wrong person to be doing this. [COLOR=red]Ah thank you for being so friendly about it, let me clarify: is there a type of walk thru to migrate from a server 2003 system to an Ubuntu system? I did not think i would have to state the obvious that i was not looking for a  walkthru to replace our "unique, specific IT environment" with a cookie cutter replacement. stating that that does not exist is the same as stating the sun is bright. :P [/COLOR]Ask Canonical, the probably have people that can handle this for you.
5- about as hard as learning Windows sysadmin. [COLOR=red]hrmm.. my friend seemed to think that Ubuntu was a much easier system to learn, maintain, and administer.[/COLOR]

re Answer 1-
security shouldn't be a problem (provided you adequately deal with question 5)
for functionality, you mention AD, DFS and some undefined "proprietary software". If you're expecting drop-in replacements, forget about it. 
If you're capable of analysing your software needs while making abstraction of your current solutions, you might find that you can cover those needs with linunx software.

---

### Post by timberline1 on 2010-08-17
your main issue is going to be with active directory. get a list of what you use active directory for and see if its supported in linux [COLOR=red]Pretty much I use it for policy deployment and folder redirection. kind of like the central brain. all profiles are contained on the servers, no tlocally.[/COLOR]
 
if you're pretty new to linux and you're planning on single-handedly switching over such a large network make sure you do a lot of homework :p [COLOR=red]I am not sure that i am going to attempt this single handedly, lol. and this pretty much is me doing my homework, asking people who are more experienced than me on the subject.[/COLOR]
 
to be honest, you'll probably find active directory support in linux isn't up to scratch for your uses. [COLOR=red]I think i remember reading there is a package that works as active directory or something like that, any ideas on that? [/COLOR]DNS, backup, printing etc will probably be easier than under windows though. [COLOR=red]well that sounds good.[/COLOR]
 
you'll still need an enterprise anti-virus solution and you'll probably find that has to be run on a windows server rather than a linux one. [COLOR=red]there is not a linux antivirus solution?[/COLOR]
 
all these things together mean that it might be best to fork over the cash for windows 2007, as much as it pains me to say. it just depends how much of a change to your current systems you're willing to go through

---

### Post by arrrghhh on 2010-08-17
Hrm.  Not sure if I should jump into this or not :P

Basically there are things that Ubuntu does very well.  There are some things that Windows does very well.  It really depends on what you want to replace.

I would NOT recommend replacing a complete Active Directory domain if you use a lot of the policy features.  Basic authentication can be handled by an Ubuntu server tho.

Same with file & printer sharing - Ubuntu server can handle it, but the permissions are a little trickier.

As far as Ubuntu server administration being easier or harder than Windows administration... I'd say they're probably about the same as far as the learning curve goes - but with that said, they both take very different approaches, so a lot of the concepts on a Windows server will not translate directly to how the Ubuntu/Linux world does it.

Linux doesn't really have issues with viruses, but there is a great antivirus tool - which is used when sharing files with Windows machines, or if you're running a mail server that sends mail to Windows machines.  It's called "ClamAV".  I'd say the best antivirus solution for Linux, but there are not many.  I think Eset, Symantec and McAfee each have a Linux-based solution if you're willing to pay.

---

### Post by koenn on 2010-08-17
> **timberline1 said:**
> 1- No
[COLOR=red]A friend has been preaching the wonders of Ubuntu so I thought i would check it out. ultimately i would like to free up more resources on our servers and work with a more secure/stable system than windows.[/COLOR].
Is your friend a sysadmin with experience in at least small/medium sized environments ? Or someone who managed to click through an ubuntu installer and found that firefox in Gnome works the same as Firefox on Windows ?

> [COLOR=red]Ah thank you for being so friendly about it, ... I did not think i would have to state the obvious that i was not looking for a  walkthru to replace our "unique, specific IT environment" with a cookie cutter replacement. stating that that does not exist is the same as stating the sun is bright. :P [/COLOR] 
I was going for getting the message across rather than being friendly :)
You'd be surprised how many threads I've seen from would-be sysadmins who seem to think that linux is "something like Windows, but free" and expect that migrating their environment is something like moving from Internet Explorer to Firefox - install it, click "yes" when it asks to migrate settings, done. 

> 
let me clarify: is there a type of walk thru to migrate from a server 2003 system to an Ubuntu system? 
not that I know of. 
You could start with the server guide : [https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)
You'll find that it comes with some functionality  that Win Server 2k3 also offers (file sharing, dns, dhcp, web server, printing ...) but you'd have to actually recreate the functionality of the win2k3 on Ubuntu - using software that might resemble their Windouws counterparts, but is not identical to it and might behave different from what your Windows experience tells you. 
(and there's no "migrate settings" button :) )


> [COLOR=red]hrmm.. my friend seemed to think that Ubuntu was a much easier system to learn, maintain, and administer.[/COLOR]
system administration is not easy (if done right). Do you find system administration on Windows easy ? If so, you'll find it equally easy on Ubuntu, once you get used to the different environment, and to working with a text-based shell. 

Actually, I *do* find linux system administration easier. The way things are done in a linux system seems to agree with my way of thinking more than how Windows appears to be layed out. And automating stuff through shell scripts is a sysadmin's dream. 
But that's the sort of ease that only comes with time and experience, and YMMV.

---

### Post by timberline1 on 2010-08-17
Right on.
 
This is all pretty much what i was thinking. i do have to admit that i was secretly hoping that would be some magic pill and make managing this monstrosity easier. 
 
i can see a few things that linux might make easier but all in all i beleive you all are echoing what i am thinking ; it will be a lot more hassle to convert over to a linux environment than would be worth it, especially since i manage my whole domain alone.
 
well thank you peoples for the info. much appreciated.
 
:)
 
):P

---

### Post by koenn on 2010-08-17
> **timberline1 said:**
>  this monstrosity. 
it's not a monstrosity


> 
it will be a lot more hassle to convert over to a linux environment than would be worth it, especially since i manage my whole domain alone.

It will be a lot of hassle. Whether or not it's worth it, is a different matter. 
But given your lack of linux knowledge and the fact that you alone would be managing this environment, migrating to linux would probably not be the best choice.

---

