---
title: "FireStarter is ... a joke?"
date: 2005-11-23
forum: Server Platforms
---

### Post by SuSUntu on 2005-11-23
Why does FireStarter seem to be so well regarded?

By design, it is a GUI to be left active in the tray so you can easily monitor firewall activity / traffic. Fine.

The problem is that the same GUI that allows you to monitor traffic (and therefore is likely to be running in the tray) also is the GUI that allows you to modify policy. No further authorization is required to access the policy rules once the GUI is launched ... it's just wide open. Separating the monitoring features from the policy editing features would be reasonable as a start to securing FireStarter, but that is not how it currently functions. Though odd for such a product, the documentation even discusses the hassles of having to use passwords and offers instructions for workarounds.   

So why, if one considers all the things Linux is supposed to be security wise, would anybody be promoting such an insecurely designed "security"  application?
 
It is very early in the morning (I have been up for almost 24-hours :) ), and I just installed FireStarter, so please forgive me if I have overlooked the obvious. However, at first blush, this app seems extremely vulnerable and could easily be used to maliciously (or otherwise) delete or modify underlying firewall settings.

---

### Post by Pablo_Escobar on 2005-11-23
Heh, IMHO - if You leave Your PC not locked and allow someone to fiddle with Firestarter GUI and applying the security policy that's Your fault.
Firestarter asks for a root password at startup - good thing then when Your in front of Your PC.
When Your not in front of PC -> Lock the screen.
If You let someone use Your PC - switch the GUI off -> simple :)

---

### Post by SuSUntu on 2005-11-23
[QUOTE=Pablo_Escobar]Heh, IMHO - if You leave Your PC not locked and allow someone to fiddle with Firestarter GUI and applying the security policy that's Your fault.
Firestarter asks for a root password at startup - good thing then when Your in front of Your PC.
When Your not in front of PC -> Lock the screen.
If You let someone use Your PC - switch the GUI off -> simple :)[/QUOTE]

Thanks for the reply.

But that is not an answer. The software is poorly designed.

---

### Post by 23meg on 2005-11-23
It's not a joke but a frontend, to iptables. You don't need its GUI on all the time. Once you've configured everything with it, shut it down. 

```
sudo /etc/firestarter/firestarter.sh status
```shows you the status of firestarter.
```
sudo /etc/firestarter/firestarter.sh stop
```  or ```
sudo firestarter --stop
``` stops firestarter.
```
sudo /etc/firestarter/firestarter.sh start
``` or ```
sudo firestarter --start
``` starts the fire.

---

### Post by SuSUntu on 2005-11-23
[QUOTE=23meg]It's not a joke but a frontend, to iptables. You don't need it on all the time. Once you've configured everything with it, shut it down. 

/etc/firestarter/firestarter.sh --> shows you the status
/etc/firestarter/firestarter.sh stop --> stops firestarter
/etc/firestarter/firestarter.sh start --> guess what[/QUOTE]

Minor correction to the above:
/etc/firestarter/firestarter.sh status --> shows you the status

Anyway ...

I understand what can be done with it and what should be done with it.

The problem is the design and the way it is promoted. If it is unsafe to be left in the tray (and it is), it should have never had that as a feature. As it stands:

1. The documentation promotes leaving it in the tray (and why wouldn't it ... it was designed to do so);

2. The documentation further discounts security by offering options on how to start up without requiring a password, thus making it more convenient to run in the tray;

3. I have seen several threads in this forum giving instructions on how to start the GUI up without requiring a password, further promoting the "start-it-and-leave-it-on" philosophy;

4. Ad infinitum;

It would have been very simple to design it so those users who like the tray candy could safely monitor traffic without diminishing security.    

As it stands, the software is poorly designed. It cannot be disputed.


-----

I see now you have corrected your original post. But, you have also gone further to imply that my opinion must somehow be related to ignorance, thus your itemization of the FireStarter commands. This isn't about my knowledge or lack thereof. 

Again, the software is poorly designed. Whether I'm brilliant or an imbecile does not change that fact. :)

---

### Post by migo on 2005-11-23
> 3. I have seen several threads in this forum giving instructions on how to start the GUI up without requiring a password, further promoting the "start-it-and-leave-it-on" philosophy;

clearly showing that's what people want, meaning the software isn't poorly designed because it does what people want

---

### Post by SuSUntu on 2005-11-23
As I review this thread, I can see that what I thought would spawn a legitimate and relevant discussion about the insecurity of a supposed "security" application will not accomplish anything other than to offend the people who really like FireStarter.

In my naivete, I thought Linux people would be in agreement with my stance rather than trying to defend insecure implementations. Guess I was wrong.

Sorry to have offended.

---

### Post by Pablo_Escobar on 2005-11-23
I'm a Firestarter user, and I do not feel offended. 
You have made some valid points, and I didn't look at Firestarter as a security flaw.
I have a custom of locking up my comp, when I'm not using it (taken from regulations at work), so the GUIs security in my case is not a problem :)

One thing bothers me in Firestarter -> if You are hit multiple times, and this hits are blocked. Firestarted is using more and more resources. Once it hit 95% of CPU, connected with Bittorent activity. Once I switched the GUI of the system was perfectly operational. That is more of a concern to me.

---

### Post by 23meg on 2005-11-23
> **SuSUntu]
The problem is the design and the way it is promoted. If it is unsafe to be left in the tray (and it is), it should have never had that as a feature. [/QUOTE]
Software developers are not responsible from your computer's physical security said:**
> 
As it stands:

1. The documentation promotes leaving it in the tray (and why wouldn't it ... it was designed to do so);
I haven't seen it promoted, but it can be promoted, as you say, since securing your computer is your job, not Firestarter's. I'm quoting the documentation on "Quitting the program":
> A frequently asked is question is, what happens when you quit the program. The answer is that the firewall will keep functioning. If you are running Firestarter as a system service, which is automatically set up for you when installing Firestarter from a binary package, the firewall is in many cases even running before you start the program. 

> **SuSUntu]
2. The documentation further discounts security by offering options on how to start up without requiring a password, thus making it more convenient to run in the tray said:**
> Again, why not? As long as you know what you're doing and you've physically secured your computer, you can.
[QUOTE=SuSUntu]3. I have seen several threads in this forum giving instructions on how to start the GUI up without requiring a password, further promoting the "start-it-and-leave-it-on" philosophy;
Unofficial documentation / help does not concern the software author / maintainer / official documenter. It's the posters' problem.
> **SuSUntu]
It would have been very simple to design it so those users who like the tray candy could safely monitor traffic without diminishing security.    [/QUOTE]
If you have ideas on how to implement this, submit them as bugs or reports to the developers said:**
> 
As it stands, the software is poorly designed. It cannot be disputed.
Not at all. Maybe at most, a bit inappropriately documented for some.

[QUOTE=SuSUntu]
I see now you have corrected your original post. But, you have also gone further to imply that my opinion must somehow be related to ignorance, thus your itemization of the FireStarter commands. This isn't about my knowledge or lack thereof. [/QUOTE]
I did not "correct" my post; I have only added one word that I've omitted to the script commands, which was "status" that should be passed to the script to display the status. Should I not have done that? Except that all I did was wrap CODE tags around the commands, which is the standard formatting used for commands in this forum, and add command line options as well as script links. I always do this, and everyone else does, for the sake of easy readibility. I really don't understand how you relate this to my belittling of your knowledge, which isn't the case. That said, if you had studied the documentation in enough detail (or even looked at the manpage), and understood the *nix security and permissions paradigm that puts you, the user, in the sense of both the physical body and the decision making mechanism in the driver's seat, above all software features, you wouldn't be so harsh and unsparing in your criticism of an application you first used an hour ago.

---

### Post by 23meg on 2005-11-23
I think I'll have to elaborate with my humble knowledge on the *nix security paradigm a bit. Please don't take this as belittling of your own knowledge; noone knows everything. We're all here to help each other by sharing what little knowledge we have, and that's what I'm trying to do, both in this post and the former one. 

In UNIX-like systems all the operations of the OS are divided into two main parts: kernel and userspace. Any bit of code running in the kernel has full access to the system it's running on. On the contrary, code running in userspace has only restricted access, limited by the user ID (UID) it's running under. This division of the computing space ensures that in most cases, userspace security risks can only compromise the userspace, not the whole system.

Here comes the point you seem to be missing: firestarter is not a standalone security application that runs in userspace and puts its own policies on IP traffic; it's merely a frontend to iptables, which manages the tables of IP packet filter rules that are in the kernel. IPv4 routing is done by the Linux kernel, in the kernel space. The advantages and disadvantages of this have been discussed millions of times, and since Linux has a reputation for its security, perhaps the advantages outweigh the disadvantages. To intervene in matters going on in kernel space, you need superuser privileges. This is why the firestarter GUI and start/stop commands have to be run as root. All they do is modify the kernel traffic rules via iptables and quit. They do not directly perform any operations on incoming traffic.

The *nix paradigm also assumes that any user granted with the appropriate privileges, namely those of sudoing and being in the "admin" group (this is the case for Ubuntu; different distros can configure this in different ways), can become root. Root is not a person, a body; it's a temporary status the users can elevate to (as the alternative term "superuser" illustrates). If the system owner has given you the right to become root under certain conditions, you can have governing rights on the system, within those conditions only. In the case of Linux installations on personal computers, say a typical Ubuntu installation, you are both the owner and the user, so you are granted full sudo rights, which means you can become root whenever you want by entering your password. This puts you, the physical body who owns the computer and has installed the OS, in a position of governance above both the userspace and the kernel. You are "in the driver's seat" as the term goes; you can manipulate everything to your heart's content, but since you are the system owner as well, you have system owner responsibilities as well. And these include physical security of your computer. Software can only act in the domains it is programmed to act in; in *nix, this is kernel and userspace. It cannot step out of its binary existence and intervene in physical matters.

The above paragraph tries to summarize how the *nix paradigm that was originally intended for a multi-user environment scales down to a single user one. There are probably lots documents out there that describe this much better; a google search should bring up most of them.

---

### Post by lerrup on 2005-11-23
I think what he is trying to say is that a legitimate user other than the admin can play with the firewall.

If this is so, this is poor design and could be solved by having a gui monitor that launched a sudo password request if you needed to modify it.

Why is that such a stupid comment?

---

### Post by Cyril on 2005-11-23
I do not believe anyone said it was a stupid comment.

---

### Post by 23meg on 2005-11-23
[QUOTE=lerrup]I think what he is trying to say is that a legitimate user other than the admin can play with the firewall.

If this is so, this is poor design and could be solved by having a gui monitor that launched a sudo password request if you needed to modify it.

Why is that such a stupid comment?[/QUOTE]
Who said it's a stupid comment? I don't understand all this harsh attitude; can you point to where the original poster's opinion was belittled? 

Read [my last post]("http://www.ubuntuforums.org/showpost.php?p=514215&postcount=10") for info on why it's not the software's responsibility who plays with it. And about the separate GUI design: to the best of my knowledge it's not possible. iptables works directly with the kernel and resides in /sbin which is reserved for administration commands, so to extract information from it on its current status would also require superuser access.

---

### Post by SuSUntu on 2005-11-23
I really don't know how to respond, 23meg. I don't have time to break down your lengthy posts as mostly they skirt the main and simple point I was making by focusing on:

1. Users of FireStarter being at fault for the flaw that I pointed out;

2. My knowledge or lack of knowledge about purely tangential issues. 

As for Item #1: users do stupid things, but a software developer should not make it easier for them to do so, especially if the software falls into the "security" category.

As for Item #2: I do not fall into the category of users who would be caught off guard by the poor design of FireStarter; it was me afterall who pointed out the flaw (whether you acknowledge it as such) in the first place. And though I have tried to focus the debate on a software design-flaw so basic that it does not require a prerequisite knowledge of permissions or MasterLocks, I will tell you, if you must know, that I have a complete grasp of everything you posted and then some. But who cares. It does not matter a bit in a case where the flaw is so elementary. 

By the way, I did read the documentation before posting and actually used the software to be as sure as my pea-brain would allow me to be about my position before posting any comments. You seem to think that this issue is rocket science. It is not. Any security conscious individual should immediately see red flashing lights here. 
---------------------------

And finally, it is obvious that this has gotten personally offensive to you as you are reading into my comments things that aren't there. I did not criticize you for correcting your original post (the missing "status" parameter) nor did I think you shouldn't have corrected it nor did I make a judgement on how egregious (or not) the mistake happened to be. I was simply pointing out to you and other readers that they should ignore the correction I had made since you obviously had caught it yourself (we apparently were typing responses at the same time , and I did not see your edit until after I had already posted). That's all. Go back and re-read it ... you will, hopefully, see it for what it is.

---

### Post by lerrup on 2005-11-23
Happy to retract the stupid bit.

I would say that, however, that it is software designers responsibility who plays with it; especially if it is system or security software.  This is after all why we have the use of an admin account/sudo, etc.

See synaptic for the sort of behaviour I would expect before altering a firewall.

---

### Post by 23meg on 2005-11-23
> **SuSUntu]I really don't know how to respond, 23meg. I don't have time to break down your lengthy posts as mostly they skirt the main and simple point I was making by focusing on
1. Users of FireStarter being at fault for the flaw that I pointed out said:**
> If you have no intent to look into matters in depth, your complaints will always end up being superficial. What I wrote does not skirt your point; on the very contrary, it describes an issue that is not tangential but that **lies at the very heart of **your complaints. If you had full knowledge of it beforehand like you stated, or simply took time to give it a good read, and accepted your lack of knowledge on the subject rather than turn this into a personal debate, you'd understand the issue and stand corrected.

And I must state again; I have not made a single condemning claim about your knowledge. Your existing knowledge is yours; I merely tried to help you by enhanching it, since from your superficial complaint I deducted that it was incomplete regarding this matter. I do this on a daily basis, and people thank me for it. And I thank others for it. But your unwillingness to accept that you missed a critical point here led to you making this personal. I don't take it as a personal matter at all; I've made my technical explanation with what knowledge I have, and all I can hope for is that you and others have benefited from it. 

[QUOTE=SuSUntu]As for Item #1: users do stupid things, but a software developer should not make it easier for them to do so, especially if the software falls into the "security" category.
I can't help but float the classical quote: > "UNIX was not designed to stop its users from doing stupid things, as that would also stop them from doing clever things." --Doug Gwyn
> **SuSUntu]As for Item #2: I do not fall into the category of users who would be caught off guard by the poor design of FireStarter said:**
> I don't mind what category you fall in; it's your main case that interests me. The issue that you see as a flaw here does indeed require a prerequisite knowledge of the UNIX paradigm; this is not up for debate. The "flaw" isn't elementary; the problem preventing what you want from being implemented lies deeper than where you think it does. Read again, do your research and you'll understand. 
[QUOTE=SuSUntu]By the way, I did read the documentation before postingThere lies a contradiction. If you had read the documentation before posting, you wouldn't ask the original question at all. I'm not saying you have to read every bit of doc there is before asking something about a piece of software, but when you don't, what you're doing is asking for the information that already exists in the doc in a different form, from different people. This is not a RTFM kind of community. We have a well deserved reputation for patiently answering even immature questions, multiple times. When we do, people are grateful for the help they get, and leave satisfied. It seems this was not the case for you, in spite of the detailed, well reasoned and polite replies you got. I'll once again refrain from making a personal judgement on you and leave it to you to consider the reason behind this.  
> **SuSUntu]and actually used the software to be as sure as my pea-brain would allow me to be about my position before posting any comments. You seem to think that this issue is rocket science. It is not. Any security conscious individual should immediately see red flashing lights here. [/QUOTE]Noone called you a pea-brain. You took this attitude all by yourself, so I have nothing more to say about this. Rocket science? You bet. Do some research or read my posts and you'll see why. The issue is deeper than you think said:**
> And finally, it is obvious that this has gotten personally offensive to you as you are reading into my comments things that aren't there. I did not criticize you for correcting your original post (the missing "status" parameter) nor did I think you shouldn't have corrected it nor did I make a judgement on how egregious (or not) the mistake happened to be. I was simply pointing out to you and other readers that they should ignore the correction I had made since you obviously had caught it yourself (we apparently were typing responses at the same time , and I did not see your edit until after I had already posted). That's all. Go back and re-read it ... you will, hopefully, see it for what it is.
I may have seen things incorrectly; it's hard to deduce the correct meaning from hastily written text on the internet sometimes, it happens to all of us. This still doesn't seem to be the case to me but the posts are out there for all to see, and since as I said I'm not taking anything personally at all, I'm not offended at all. 

All I'm hoping for is that people look a bit deeper into issues before complaining in a harsh tone about them. This isn't specific to you; I've said the same thing to another forum member two days ago. You can do a search for proof of this if interested. This attitude has started to become more common on the forums, and where I see it, I just take it as my duty to clear up the confusion by modestly pointing to the facts.

---

### Post by Gustav on 2005-11-23
I think the tray option for firestarter is a bad idea since it is compareble with having a tray option for a root terminal. No administrative tasks should be able to be run without typing your password. This is why Ubuntu uses sudo instead of su.

Just my opinion.

---

### Post by 23meg on 2005-11-23
[QUOTE=Gustav]I think the tray option for firestarter is a bad idea since it is compareble with having a tray option for a root terminal. No administrative tasks should be able to be run without typing your password. This is why Ubuntu uses sudo instead of su.

Just my opinion.[/QUOTE]
The notification area option has no necessary connection with running firestarter without a password. Just because you can do something doesn't mean you have to do it. It's presented to you merely as an option. If you're very security conscious, you won't enable this behaviour anyway, so security-wise it's a nonissue. And the firestarter doc clearly warns you about the potential danger:
> **Giving the user permission to launch Firestarter without the root password**
In order for a regular user to be able to launch Firestarter, the user must be given additional privileges. Edit your /etc/sudoers file in your favorite text editor and add the following line at the end:
```
username ALL= NOPASSWD: /usr/bin/firestarter

```
Note: Debian users should replace /usr/bin/firestarter with /usr/sbin/firestarter in the above line.

Simply replace username with whatever your login is. The specified user is now able to launch Firestarter without being prompted for a password using the command sudo firestarter.

A note on the security aspects:** This method makes a trade off in local security for convenience. If your user account becomes compromised the attacker will be able to control the firewall. **However this method is preferable to having a shared root user password in a multiuser setting. It is also preferable if the alternative is not to run Firestarter at all. The bottom line is that you have to know what you're doing before you enable this behavior. It takes root privileges to add a line to /etc/sudoers, and the general rule of thumb is that when you become root, you're making system-wide changes and must know what you're doing.

---

### Post by LordHunter317 on 2005-11-23
[QUOTE=SuSUntu]But that is not an answer. The software is poorly designed.[/QUOTE]It is, but not for the reason you suggest.

The software isn't responsible for your phyiscal security policy.

> It would have been very simple to design it so those users who like the tray candy could safely monitor traffic without diminishing security.

As it stands, the software is poorly designed. It cannot be disputed.No, it's actually not.  Any operation related to iptables very well may require privilege, including the monitoring.

> As for Item #1: users do stupid things, but a software developer should not make it easier for them to do so, especially if the software falls into the "security" category.What is firestarter supposed to do to make thigns more secure?

We can presume you want it to ask for the password all the time.  It stands to reason two things:[list][*]If the user isn't security-minded enough to not lock their machine when they walk away from it, they won't mind giving out the firestarter password either[*]If the attacker can bypass the screensaver, they can bypass the firestarter password as well[/list]

So what would you have them do?  There's no solution that will definetely add security--think the scenarios through for a bit.

> And though I have tried to focus the debate on a software design-flaw so basic that it does not require a prerequisite knowledge of permissions or MasterLocks, I will tell you, if you must know, that I have a complete grasp of everything you posted and then some. But who cares. It does not matter a bit in a case where the flaw is so elementary.You've failed to demonstrate both:[list][*]How this flaw is "elementary" :rolleyes:[*]How firestarter could even defend against it[/list]

> Any security conscious individual should immediately see red flashing lights here. People infintely smarter than you and I do not, so no, you're quite wrong.

[quote=lerrup]I think what he is trying to say is that a legitimate user other than the admin can play with the firewall.[/quote]Only if, you know, you let them sit at your terminal and play, which is why firestarter doesn't do anything about it.

Just like konqueror doesn't bother asking who you are before happily trashing all your files.

---

### Post by lerrup on 2005-11-23
[QUOTE=LordHunter317]
Only if, you know, you let them sit at your terminal and play, which is why firestarter doesn't do anything about it.

Just like konqueror doesn't bother asking who you are before happily trashing all your files.[/QUOTE]

But if you do that it only trashes your /home folder but not the system folders unless you have root priviliges.  This is how it should be.

My point is that changing the iprules and the way a firewall operates is equivilent to changing the system from a security point of view.  Therefore to do this it should ask for your root password via gksudo.

If this is such a non-sensible way to proceed why do so many other apps use the same model?

---

### Post by 23meg on 2005-11-23
[QUOTE=lerrup]
My point is that changing the iprules and the way a firewall operates is equivilent to changing the system from a security point of view.  Therefore to do this it should ask for your root password via gksudo.[/QUOTE]
And my point has been, and the simple fact is, that it does, unless you *explicitly* tell it not to, *by becoming root *and modifying a system wide setting. You could do the same for any app. You could launch a nautilus window or a script that *deletes your /boot folder on startup *if you set the permissions accordingly, exactly the way you do with firestarter. This is not a firestarter design issue, it's the *nix security model at work. If you find that model insecure, this thread would be the wrong place to complain.

---

### Post by LordHunter317 on 2005-11-23
[QUOTE=lerrup]But if you do that it only trashes your /home folder but not the system folders unless you have root priviliges.  This is how it should be.[/quote]And if you're logged into the GUI as root, it doesn't ask if you're root in the least.

> My point is that changing the iprules and the way a firewall operates is equivilent to changing the system from a security point of view.  Therefore to do this it should ask for your root password via gksudo.Yes, the first time, to elevate privilege.  But once you've proven you're capable of being root, why should it ask you every time?  That makes no sense: as I said, if an attacker gets a user's screensaver password, they'd also (likely trivially) be able of getting the password used to give firestarter root.

> If this is such a non-sensible way to proceed why do so many other apps use the same model?They don't.  Zonealarm, Kerio, et al. on Windows don't do this unles you specifically make them.  Windows firewall doesn't, and can't.

---

### Post by artnay on 2005-11-24
I'm with SuSUntu. Clicking the tray icon should bring a window that has information on logged events of firewall engine by parsing (or passing to another file) wanted messages from /var/log/messages (or equivalent), comparing them to the rules that have been set and then putting the alerts to different categories. This shouldn't require user to be root. 

User should be able to make a decision how the GUI should show the events. All the events could be inside one window (no alerts shown) or maybe it could pop-up a warning window for the events that user wants to see, like metamonitor does ([http://www.kde-apps.org/content/show.php?content=30603)](http://www.kde-apps.org/content/show.php?content=30603)). 

Yeah, it's not firestarter's job to prevent wrong user to access computer physically. Still the GUI should at least try to prevent user from changing the rules without password. Maybe there should be "Modify rules" button that would call gksudo. Heck, I guess you could do this with Windows programs by locking the engine to be read-only or something.

You can't deny the problem, even if it's in the design on unics-like systems or in firestarter itself. I haven't used firestarter for ages so maybe I'm not the right people to give a comment on this.

---

### Post by 23meg on 2005-11-24
[quote=artnay]
Yeah, it's not firestarter's job to prevent wrong user to access computer physically. Still the GUI should at least try to prevent user from changing the rules without password. Maybe there should be "Modify rules" button that would call gksudo. Heck, I guess you could do this with Windows programs by locking the engine to be read-only or something.
[/quote]Obviously you're not reading carefully enough; what's being said here is that it doesn't seem possible to get information from iptables without root access. Thus a split GUI scheme that will resort to sudo/gksudo only to modify the settings doesn't seem possible. This is beyond a Firestarter design thing; it's a condition brought by the *nix structure. And this has been stated multiple times. Please stop making comparisons to Windows software; we're not talking about a standalone firewall app but an interface to a kernel function here. If you want a split GUI, go ahead and recode iptables and the kernel IPv4 routing functions, noone is keeping you from that. This is the *nix world and we're bound by the *nix architechture, like it or not.

---

### Post by artnay on 2005-11-24
[QUOTE=23meg]Obviously you're not reading carefully enough; what's being said here is that it doesn't seem possible to get information from iptables without root access. Thus a split GUI scheme that will resort to sudo/gksudo only to modify the settings doesn't seem possible. This is beyond a Firestarter design thing; it's a condition brought by the *nix structure. And this has been stated multiple times. Please stop making comparisons to Windows software; we're not talking about a standalone firewall app but an interface to a kernel function here. If you want a split GUI, go ahead and recode iptables and the kernel IPv4 routing functions, noone is keeping you from that. This is the *nix world and we're bound by the *nix architechture, like it or not.[/QUOTE]

I just compared firestarter's functions to Windows equivalents as I guess many of them provide a choice to lock the rules table, although they might not run in kernelspace.

Maybe the rules set by firestarter should be exported to read-only file that only firestarter has an access, although that would bypass the rules set by iptables or other GUIs. That way rules could be compared to logs. Iptables is just a CLI to the firewall engine. Well, I guess some more tech-savvy (expert) should tell what's preventing this to happen. For me it's my coding skills and the lack of knowledge. ;)

And yes, I did read all the replies quite carefully. Therefore I wrote this sentence to my first message: "You can't deny the problem, even if it's in the design on unics-like systems or in firestarter itself."

---

### Post by 23meg on 2005-11-24
The reason non-*nix firewall software can lock their rules should be that they're not interfacing directly with a kernel function. I and others have told what's preventing what you want from happening in previous posts.
[quote=artnay]
Iptables is just a CLI to the firewall engine.[/quote]The fact is that the kernel handles IP traffic routing, so whatever userspace way of setting the tables you find, it will have to interface with the kernel. This isn't specific to iptables + Firestarter.

In terms of **local security**, it makes sense that you can't see the status of iptables without being root; if this were made possible, in the case of your local account being physically or digitally compromised, the attacker could view the routing policy of your interface, even though they may not be able to immediately modify it if your local account isn't given sudo privilege. The *nix model considers the viewing of the policy as a breaching of security as well.

If you read the replies and acknowledge that this isn't a Firestarter issue, I fail to understand why you keep making suggestions as to how Firestarter should be designed to accomodate separate functions of viewing and modifying iptables.

---

### Post by nocturn on 2005-11-24
[QUOTE=SuSUntu]As I review this thread, I can see that what I thought would spawn a legitimate and relevant discussion about the insecurity of a supposed "security" application will not accomplish anything other than to offend the people who really like FireStarter.

In my naivete, I thought Linux people would be in agreement with my stance rather than trying to defend insecure implementations. Guess I was wrong.

Sorry to have offended.[/QUOTE]

Ok, I just read this thread, and I do think you have a legitimate concern about firestarter (which I haven't used myself).

However, calling FireStarter a joke in the thread title sort of ruins any chance of a dialog with both the FireStarter fans and it's developers.

It is a Free Software application, developed by people who donate their time freely to help others.  If you find bugs or design flaws in it, it is a courtesy to communicate these to them so they can be handled.  Calling a program a joke will not do much to better the situation.

Your remarks on these issues are important though, and to get something constructive from this discussion, would you consider filing this issue here: [http://www.fs-security.com/contact.php](http://www.fs-security.com/contact.php)

---

### Post by nocturn on 2005-11-24
[QUOTE=23meg]Software developers are not responsible from your computer's physical security; even security software developers aren't. If you leave Firestarter in your notification area, it's your responsibility to secure it. [/QUOTE]

I disagree with this.  Any program should always run with the least privileges possible.  While it is OK for firestarter to show it's status to anyone clicking the icon, it would be a good idea to ask for a passwords to change the policy.

Look at update-notifier, it warns of updates all the time, but asks your password to install them.

---

### Post by 23meg on 2005-11-24
[quote=nocturn]I disagree with this.  Any program should always run with the least privileges possible.  While it is OK for firestarter to show it's status to anyone clicking the icon, it would be a good idea to ask for a passwords to change the policy.

Look at update-notifier, it warns of updates all the time, but asks your password to install them.[/quote]I feel like I'm repeating myself but Firestarter runs with the least privileges possible, and it does ask for passwords to change the policy. Update provider queries the apt database, which is in userspace and isn't locked by the kernel, that's why it can only ask for the password before making modifications. However, Firestarter interfaces with iptables, which in turn interfaces directly with the kernel, and this is why you can't just view its current status without being root.

---

### Post by nocturn on 2005-11-24
[QUOTE=23meg]so to extract information from it on its current status would also require superuser access.[/QUOTE]

It probably does (which is not a problem).  But, even when FireStarter is running with UID 0, it can perform a password validation at any point.  

It would add to the security off your system if FireStarter required a password for changing policies, so I think it would be a good design decision to implement this.

---

### Post by nocturn on 2005-11-24
[QUOTE=23meg]Firestarter interfaces with iptables, which in turn interfaces directly with the kernel, and this is why you can't just view its current status without being root.[/QUOTE]

I think you misunderstand me.  I'm not questioning the fact that FireStarter runs as root.  But it is quite possible to have it re-ask the root (or sudo) password before chaning the policies, not to elevate it's own privileges, but to verify if the user is doing the modifications.

I agree with being responsible for physical security (locking your screen), no argument here, but It is still a good idea to limit the damage when someone doesn't do that AND it also protects against automated attacks.

It should be possible to write a program that emulates mouseclicks/keyboard shortcuts to control the FireStarter GUI.

---

### Post by nocturn on 2005-11-24
> I feel like I'm repeating myself but Firestarter runs with the least privileges possible

Where is FireStarting getting its status information?  Is it coming from the iptables command or is it comming from a log file?

In the second case, it would be safer to just grant it read access to the log file, while requiring the root/sudo passwd for modifying policy...

---

### Post by 23meg on 2005-11-24
[quote=nocturn]It probably does (which is not a problem).  But, even when FireStarter is running with UID 0, it can perform a password validation at any point.  

It would add to the security off your system if FireStarter required a password for changing policies, so I think it would be a good design decision to implement this.[/quote]If it's running with UID 0, it can't reauthenticate with the root password. And introducing another password to an app running as root just isn't necessary and would undermine the *nix security model; it would render the root privilege  to a secondary necessity. An app running  with root privileges does not need any further authentication, period. The whole point of having root is that if you can run something as root, you can use it for system-wide operations. I must repeat that y*ou can only make firestarter launch without entering a password on boot if you already can become root*, because you need to edit /etc/sudoers to do it. And reasking for a password when already running as root isn't theoretically possible AFAIK, and even if it were possible, it would shake the foundation root authentication is based on.

---

### Post by 23meg on 2005-11-24
[quote=nocturn]Where is FireStarting getting its status information?  Is it coming from the iptables command or is it comming from a log file?

In the second case, it would be safer to just grant it read access to the log file, while requiring the root/sudo passwd for modifying policy...[/quote]A log file would be too insecure. It comes direct from iptables, thus the kernel.

---

### Post by nocturn on 2005-11-24
[QUOTE=23meg]If it's running with UID 0, it can't reauthenticate with the root password. [/QUOTE]

Yes, it can.  I have seen programs re-require the password of the active account to run (the Unix/LDAP/Kerberos one, not a seperate one).

---

### Post by SickTwist on 2005-11-24
While I agree that the ability to run any program with root priviledges in the system tray might encourage bad security habits, I am surprised that nobody here has suggested that perhaps the real issue is not with Firestarter, but with the Linux kernel. Firestarter's design seems to be governed a great deal by the limitations of iptables. Perhaps it is time that the functionality of this piece of the kernel is extended.

Why couldn't the kernel give feedback about iptables via a file in /proc? That would allow the Firestarter devs to create two separate interfaces--one that runs with root access to modify the rules for iptables and another interface to be run by any user which displays the status of iptables by pulling that information from the appropriate file in /proc.

---

### Post by 23meg on 2005-11-24
Possible with a regular user account, but not root, AFAIK. I'll investigate this, but any case it's not required. The fact that you are able to run the app as root in the first place means that you're entitled to full access to it in the duration of your present session without any further restrictions. Maybe SELinux and other security extensions to the basic *nix have different sets of rules, but with the Linux defaults, this is the case.

---

### Post by 23meg on 2005-11-24
[quote=SickTwist]While I agree that the ability to run any program with root priviledges in the system tray might encourage bad security habits, I am surprised that nobody here has suggested that perhaps the real issue is not with Firestarter, but with the Linux kernel. Firestarter's design seems to be governed a great deal by the limitations of iptables. Perhaps it is time that the functionality of this piece of the kernel is extended. 

Why couldn't the kernel give feedback about iptables via a file in /proc? That would allow the Firestarter devs to create two separate interfaces--one that runs with root access to modify the rules for iptables and another interface to be run by any user which displays the status of iptables by pulling that information from the appropriate file in /proc.[/quote]This has been acknowledged multiple times on this thread. And the enhanchements you speak of are most likely already possible with security extensions such as SELinux.

Maybe the kernel can be configured in compile time to report the status of iptables and other kernelspace services without any extensions as well, I'm not sure of this, but making this a default behaviour on stock kernels would be insecure, and popular software such as Firestarter can't rely on such specialized methods; it has to stick to the most general and widely usable methods possible.

---

### Post by LordHunter317 on 2005-11-24
[QUOTE=artnay] Clicking the tray icon should bring a window that has information on logged events of firewall engine by parsing (or passing to another file) wanted messages from /var/log/messages (or equivalent), comparing them to the rules that have been set and then putting the alerts to different categories. This shouldn't require user to be root. [/quote]So you want **everyone** to be able to read /var/log/messages and potentially see important diagonstic and security-related information?

No, I don't think so.  So either you make the log accessible to a certain group and the firestarter GUI usuable only by those users, or you make firestarter run as root.  

Of the two options, only the latter is a valid decision for the firestarter authors.  The Ubuntu packagers could package it to do the former, if they really desired.

> Still the GUI should at least try to prevent user from changing the rules without password.Why?  You **have** to enter a password **to start the application**.   It's more than safe to assume that if the user entered the password to start the application, they can enter the password at any point during it's runtime.

> You can't deny the problem, even if it's in the design on unics-like systems or in firestarter itself.No, but you can ignore it because it's effectively a non-solvable problem.

[quote=nocturn]I disagree with this. Any program should always run with the least privileges possible.[/quote]***And root IS THE LEAST AMOUNT OF PRIVILEGES POSSIBLE.***.  Anyone who posts after this and doesn't understand that is likely to get flammed far worse.

Seriously, if you can't understand the ramifications of that sentence, please just don't post, as the discussion is above your level of technical expertise.  Just accept that by design, firestarter must run as root and that's life.

[quote=23meg]If it's running with UID 0, it can't reauthenticate with the root password. [/quote]Rather, even if it could in some manner, there's no need because by definition it could bypass the authentication check.

[quote=SickTwist]I am surprised that nobody here has suggested that perhaps the real issue is not with Firestarter, but with the Linux kernel. [/quote]There is no issue here or there.

> Why couldn't the kernel give feedback about iptables via a file in /proc?Because giving out information about the firewall to *any* untrusted user is a security compromise.  If there was a hole in the firewall rules, you just gave it away to them.

> Maybe SELinux and other security extensions to the basic *nix have different sets of rules, but with the Linux defaults, this is the case.Yes, since they implement MAC and not DAC.

---

### Post by lerrup on 2005-11-24
I am going to risk putting my head above the parapet as you seem to have missed the point I, and I think others, were making.

A firewall needs to run as root.  Fine, don't have a problem with that.  A firewall will usually start at boot time with no user interaction and so this is not difficult to do.   I have never started my firestarter with a password as it does so at boot time.

A lot of things need to run as root as well, but users can't modify the way they work, only someone with admin priviliges can.  Now, if you are saying it is not possible to split a firewall program into modules; the actual firewall, the pretty gui display and a modify rules module then why not?

---

### Post by LordHunter317 on 2005-11-24
[QUOTE=lerrup]Now, if you are saying it is not possible to split a firewall program into modules; the actual firewall, the pretty gui display and a modify rules module then why not?[/QUOTE]Because ***ALL PARTS MUST BE ROOT.***

You want to just read the rules?  You must be root.  Showing the rules to an untrusted user (which, under UNIX DAC, is everyone but root) is a security risk.  Hence, iptables requires you to be root.

Modifying the rules?  Obviously requires you to be root?

Displaying the rules and stuff in the GUI?  Requires privileges to get the information, hence must be root.

It would be possible to privilege seperate the GUI so the actual GUI code wouldn't run as root.  That increases security by minimizing the amount of code that could be potentially expolited to gain root access.

But it wouldn't remove the requirement to enter a root password on GUI startup.  Nor would it suddenly require a need to enter the password all the time, which makes no sense and adds no security.  Which was the original complaint.

---

### Post by lerrup on 2005-11-24
[QUOTE=LordHunter317]Because ***ALL PARTS MUST BE ROOT.***

You want to just read the rules?  You must be root.  Showing the rules to an untrusted user (which, under UNIX DAC, is everyone but root) is a security risk.  Hence, iptables requires you to be root.

Modifying the rules?  Obviously requires you to be root?

Displaying the rules and stuff in the GUI?  Requires privileges to get the information, hence must be root.

It would be possible to privilege seperate the GUI so the actual GUI code wouldn't run as root.  That increases security by minimizing the amount of code that could be potentially expolited to gain root access.

But it wouldn't remove the requirement to enter a root password on GUI startup.  Nor would it suddenly require a need to enter the password all the time, which makes no sense and adds no security.  Which was the original complaint.[/QUOTE]

Which would be fair enough, but I am not talking about seeing rules in the gui!  All I am talking about is activity which does not need to show the rules that iptables applies.  All it would show is the same as the status tag in the firestarter gui at present.

Is that info a security risk?

---

### Post by LordHunter317 on 2005-11-24
[QUOTE=lerrup]All I am talking about is activity which does not need to show the rules that iptables applies.[/quote]What activity? ***ALL ACTIVITY MENTIONED THUS FAR IN THE THREAD REQURIES ROOT ACCESS***.  Viewing intrusion logs requires root access, and with good cause.  So do hit counters.  So does active connections.

So what activity are you talking about, then?

> All it would show is the same as the status tag in the firestarter gui at present.You mean the tab?  Yes, that information requires root access to acquire.

> Is that info a security risk?Yes.

Just accept it.  It requires root for all it's actions.  You'll have to enter the root password, even if it were privileged seperated.  And having it periodically ask during the running of the application is of very dubious security value.  I'd argue in most situations firestarter is used, it's not of any value, in fact.

---

### Post by 23meg on 2005-11-24
Thanks LordHunter317 for restating my point; as I've stated before, reasking for passwords would not just add only a trivial amount of "extra security" at the cost of major possible annoyances. It would undermine the security model that all apps abide by, including security apps, and asking for a separate password would detriment the value of having the root password, thus isn't acceptable for an app like Firestarter. If there is a security risk introduced by Firestarter, it's the one resulting from your possible misuse of it. [B]

Why do people need Firestarter in the notification area all the time in the first place? [/B]Do you make changes to your IP traffic rules every five minutes? Every half hour? The fact is that most typically you **DON'T.** **So don't set up Firestarter to start its GUI on Gnome startup, that's it.** This is the default behavior anyway;** even if you don't start its GUI, Firestarter will start protecting you on boot the way you specified the last time you launched the GUI**. That's the thing the typical security conscious Linux user would do. [B]

Anyone who thinks they need to see the Firestarter notification area (it's not called "tray" BTW) icon to make sure it's running, as is usually the case with Windows "firewall" apps, is clearly MISINFORMED and is putting themselves into a possible security risk in the case that their computer is physically compromised. [/B]

---

### Post by LordHunter317 on 2005-11-24
Or, you know, don't be dumb and just lock your computer when you walk away from it, and don't use an easily guessable password like "sam" :p

(I'm jesting 23meg a little, but in all honesty, I've never understood why people can't accept that as a solution).

---

### Post by 23meg on 2005-11-24
I've assigned the Windows key on my keyboard to locking the screen. Thankfully it's stashed to the upper right corner in my keyboard and it's not easy to accidentally press it. I tap it every time I leave my laptop working alone.

Anyone noticed the security update to iptables yesterday in the middle of the heat here? See, the devs are at work. The backend is secured. Just keep your frontends secured as well by adopting good security practices, getting informed on basic facts and not swallowing FUD.

---

### Post by SuSUntu on 2005-11-24
There seems to be a lot of histrionics about what requires root access and what doesn't. A lot of talk about security philosophy, the Linux model, "the tray" isn't the tray (oops, it's the notification area); a lot of talk that seems self-congratulatory and mocking at this point without addressing the issue.  

We will all agree that modifying iptables requires root access...and should.

However, it appears from the FireStarter source (as I suspected and as some other less vocal readers here may have suspected) that FireStarter is getting its Event Tab information from parsing the "syslog". Viewing the contents of the "syslog" does not require root priveleges by default (do Menu -> System Tools -> System Logs). The source code most relevant to this can be found in FireStarter's source files "util.c" and "logread.c" (although less obvious references can be found elsewhere):

From util.c
```
 
if (path == NULL) {
			error_dialog (g_strconcat (
				"<span weight=\"bold\" size=\"larger\">",
				_("Failed to open the system log\n\n"),
				"</span>",
				_("No realtime hit information will be available. "
				"Please make sure the syslog daemon is running."),
				NULL));		
		}

```

From logread.c
```

/* [ poll_log_timeout ]
 * Polls the logfile every 500ms for change, if change, parse lines
 */
static int
poll_log_timeout (gpointer file)
{

```

To test, I added some block rules to FireStarter, checked my syslog after the event, and the iptables blocked events are indeed there for all to see. You can recreate the same by adding "--log-level info" to your non-FireStarter-created iptables' rules.

Whether you think this is secure or not, the fact is that "intrusion logs" requiring "root" priveleges (as LordHunter so forcefully, and erroneously stated) are not used. FireStarter sets the iptables rules it creates (via its configuration file) to LOGging level "info". See the "/etc/firestarter/configuration" file.

I have not checked the source thoroughly enough yet, but I suspect that FireStarter is getting its Status tab information from parsing netstat info (or /proc/net/* or similar) which does not require root priveleges either (note: netstat DOES require root priveleges to view the Program (PID) info of processes spawned by other users; otherwise, info is freely accessible without "root". For an example in the extreme, if you were to browse in "sudo firefox" and viewed the "netstat -vetp" results in a terminal, you would see all the current activity for that connection, but the PID column would not list the program. If you viewed the same activity with "sudo netstat -vetp", the Program info would be listed. All user PIDs would be visible regardless.)  

So, it appears (though the netstat issue isn't confirmed) that the program is only requiring a password at GUI startup because the iptables modification functionality is included. Removing the following items would leave only an informational tray GUI, separate and apart from any control over the firewall / iptables:

REMOVE:
1. Start, Stop, & Lock buttons;
2. Preferences GUI;
3. iptables modification functionality, including context menu functionality in the Events tab (the context menu allows the user to modify the iptables based on the contents of the selected event);
4. Maybe I overlooked something, but you get the idea.

If that were done, the tray GUI is simply a two tab (Status & Events tabs), non-iptable-interactive information source. Startup would not, by default, require higher priveleges. Access to the iptables functionality could be activated by an additional button, and at that point, root priveleges would be required.  

I don't really need any of these changes as I don't use FireStarter, and I hesitated to even participate in this thread again. However, I thought I'd clear some things up as this thread is a very good example of individuals playing the "look how much I know game", and ultimately losing site of the the original issue.

Edit:
I originally suggested in Item #1 (above) to leave the Lock button, but that of course wouldn't work as "Locking" requires access to iptables (essentially, the Lock Button removes rules and sets Policy of INPUT, FORWARD & OUTPUT to DROP).

---

### Post by 23meg on 2005-11-25
> **SuSUntu]a lot of talk that seems self-congratulatory and mocking at this point  [/quote] Mocking and self-congratulatory.. Let's see..
[quote=23meg]I really don't understand how you relate this to my belittling of your knowledge, which isn't the case. 
[/quote][quote=23meg]Please don't take this as belittling of your own knowledge said:**
> [quote=23meg]I don't take it as a personal matter at all; I've made my technical explanation with what knowledge I have, and all I can hope for is that you and others have benefited from it.> **23meg]I don't mind what category you fall in said:**
>  [quote=23meg]I'll once again refrain from making a personal judgement on you I will not comment further on this non-matter. Your offending comments on my announcedly modest and refrained presentation of information is there for all to see. If you must [whine on forums instead of making a difference]("http://www.ubuntuforums.org/showthread.php?t=78741"), go and find a more welcoming, more polite and less cocky forum that responds in a softer tone to prejudiced, hastily written bashing comments on software.
> **SuSUntu]
it appears from the FireStarter source (as I suspected and as some other less vocal readers here may have suspected) that FireStarter is getting its Event Tab information from parsing the "syslog". [/quote]If some less vocal readers or posters had suspected this, they'd post their doubts to the thread in an appropriate, non-bashing manner. Since they didn't, noone should talk in their name.

I stand corrected on a point raised by a less vocal and more polite poster on whether Firestarter parses a log file or queries iptables directly said:**
> Ultimately, I don't really need any of this, and I hesitated to even participate in this thread again. However, I thought I'd clear some things up as this thread is a very good example of individuals playing the "look how much I know game", and ultimately losing site of the the original issue.I don't need any of this either. And I didn't write my "*nix security" post in order to just inform you on the issue or show off my knowledge, and I made this explicit in the first paragraph of the post. I wrote it so that others who may or may not be fooled by your rushed judgement (you acknowledged that it might be rushed in your very first post) that Firestarer has an "elementary flaw" can gain a bit deeper insight into the matter as well. 

I can still be wrong. You may still be able to debase my points, but if you do so, and if you decide to keep making personal attacks by posting on this thread instead of taking this to the developers, just know that I don't see any reason in taking any further part in this discussion. I'm not a Firestarter developer or advocate, or even a Firestarter user. I'm merely someone who saw your post and tried to point to you some facts that you, admit it, weren't aware of in the first place. You only looked deeper into iptables and kernel message logging and the Firestarter code because your initial harsh statements were debased on the superficial grounds that they laid. And only then did you agree to actually talk on a technical basis rather than a "who will beat whom with wordplay" basis. If you still have ideas on how to "improve" Firestarter according to your liking, take them to the developers, or elsewhere.

This is the whole point of discussion and dialectics (do a google search on where the word "forum" comes from if you will). This is why we have online technical discussion of all sorts; if someone is misinformed or uninformed about an issue, you correct them or reinforce their knowledge and they acknowledge this, and move on. But when they come up with flames coming out of their mouth and furthermore, can't take to heart the fact that they've been corrected in their statements, there's nothing one can do. You should be grateful that you were taken as seriously as you were with such a post title and such initial arguments. 

Yours is not the first and it seems won't be the last of such hasty software bashing, so I have to declare that from now on, I won't take seriously anyone who comes up with a blind bashing attitude on any piece of software or policy and I won't respond to them. And I encourage everyone who's read and abides by the CoC to do so. If anyone wants to be taken seriously, they should make their case in the proper manner.

---

### Post by LordHunter317 on 2005-11-25
[QUOTE=SuSUntu]However, it appears from the FireStarter source (as I suspected and as some other less vocal readers here may have suspected) that FireStarter is getting its Event Tab information from parsing the "syslog". [/quote]***WHICH *SUPRISE*, STILL REQUIRES ROOT ACCESS TO VIEW.***

> Whether you think this is secure or not, the fact is that "intrusion logs" requiring "root" priveleges (as LordHunter so forcefully, and erroneously stated) are not used.If it can view the system logs without root privileges then Ubuntu is shipping logs with very poor default access permissions.  Everyone else requires root access to view anything logged via syslog by default.  All my debian boxes require root.  All my RHEL ones do as well.  Well, or group adm access.

> So, it appears (though the netstat issue isn't confirmed) that the program is only requiring a password at GUI startup because the iptables modification functionality is included.Nope, viewing the logs requires privilege.

> However, I thought I'd clear some things up as this thread is a very good example of individuals playing the "look how much I know game", and ultimately losing site of the the original issue.:rolleyes: That's real cute coming from you, since you're the one here's who's trying to narrowly apply some nugget you gleaned from obscure place in ways it doesn't function.  Like posting the source code.  Wow, I knew it got the data from what iptables logs via sysklogd.  You told us something that everyone here already knew, but did it in the most condescending way possible.

---

### Post by LordHunter317 on 2005-11-25
[quote=SusUntu]However, it appears from the FireStarter source (as I suspected and as some other less vocal readers here may have suspected) that FireStarter is getting its Event Tab information from parsing the "syslog". Viewing the contents of the "syslog" does not require root priveleges by default (do Menu -> System Tools -> System Logs).[/quote]Nope, wrong.  Viewing the logs requires to be root or a member of the 'adm' group.  I don't know what command that runs but I suspect gksudo is part of it at some point.

---

### Post by SuSUntu on 2005-11-25
Hello, LordHunter317.

You are correct about the narrow focus of my demonstration regarding syslog access. 
Ubuntu, by default sets the first created user to have "read" access to syslog ("write" privileges are still restricted to "root"). Other distributions I use / have used don't even allow "read" access by default (Centos 4.x for example, and Suse, if I recall correctly). I believe the latter to be the correct way to do things, forcing the administrator to explicitly assign even "read" privileges.

[quote=LordHunter317]

> 
Originally Posted by SusUntu
However, it appears from the FireStarter source (as I suspected and as some other less vocal readers here may have suspected) that FireStarter is getting its Event Tab information from parsing the "syslog". Viewing the contents of the "syslog" does not require root priveleges by default (do Menu -> System Tools -> System Logs).

Nope, wrong. Viewing the logs requires to be root or a member of the 'adm' group. I don't know what command that runs but I suspect gksudo is part of it at some point.
[/quote]
To address your comments about Ubuntu and Syslog more directly, the "Menu -> System Tools -> System Logs" item is not connected to "gksudo" in Ubuntu. The underlying menu item command is "gnome-system-log". Syslog permissions are set to:
-rw-r----- : Owner - root /  Group - adm. I checked again on an untouched, fresh Ubuntu install, and those permissions as I stated are present. If others have a different experience with the default installation, please comment. By the way, since this is an Ubuntu forum. I'm somewhat surprised to learn that you evidently are not running Ubuntu and / or don't have access to an Ubuntu installation based on your comments? It doesn't really matter, but I still find that interesting if that is the case.

All that aside, and much more importantly, I was trying to demonstrate in my previous post that FireStarter used different processes to fulfill requirements of the various GUI components: syslog for Events, netstats (maybe) for Status, and iptables for Policy, each of which could be independently set for privileges.

With that knowledge in mind (and yes you were likely not surprised by this), it lessens the absoluteness to which you responded to Lerrup in post #43 and to which 23MEG agreed in post #44. Independent utilities providing the functionality allows the GUI to easily be divided into the components while providing finer grained control over access to each one; it doesn't need to be an all or nothing proposition.

And, even if syslog was off limits to a user (whether by default or explicit settings), the Events tab would simply not get populated (that's what happens in Ubuntu if you explicitly deny user "read" access to syslog - the Gnome-System-Log applet opens without complaining, but it simply is not populated). The FireStarter source code indicates error trapping for systems on which it can't read the syslog (likely from path issues or the daemon not running), but regardless, it is apparent that a test for read access is made, and if read access failed, a nice, polite message could be printed on the Events Tab in the GUI stating, "Event Information Not Available". 

We probably agree on a lot of issues, though it hasn't been as apparent as I would have liked based on this thread. And if nothing else, can we agree that it would be nice to have total control over what access is granted in FireStarter's GUI since it seems to be possible? I understand and appreciate alternate methodologies such as locking your desktop, but perhaps there might be a desire to allow another user access to the FireStarter information without having to grant that user full privileges to iptables just to see the Status and / or Events tabs? 


-----------------

Since we are discussing, to some extent, permissions and Ubuntu, could you take a look at this thread I posted a few days ago (before this thread was started):

[http://ubuntuforums.org/showthread.php?t=93657](http://ubuntuforums.org/showthread.php?t=93657)

I am very curious about it, but it has had very few views and no responses. It shouldn't come across as controversial, but I didn't think this thread shoud be either. :)

Thank you.

---

### Post by LordHunter317 on 2005-11-25
> **SuSUntu]Ubuntu, by default sets the first created user to have "read" access to syslog ("write" privileges are still restricted to "root"). Other distributions I use / have used don't even allow "read" access by default (Centos 4.x for example, and Suse, if I recall correctly). I believe the latter to be the correct way to do things, forcing the administrator to explicitly assign even "read" privileges.[/quote]Right, therefore, firestarter's GUI must be root for all operations.

> By the way, since this is an Ubuntu forum. I'm somewhat surprised to learn that you evidently are not running Ubuntu and / or don't have access to an Ubuntu installation based on your comments?I'm at home for thanksgiving and the only Linux box in the house is a 2yr-old Debian router/fileserver.  My laptop runs Windows and Windows-only currently for a laundry-list of reasons that aren't really important.

> All that aside, and much more importantly, I was trying to demonstrate in my previous post that FireStarter used different processes to fulfill requirements of the various GUI components: syslog for Events, netstats (maybe) for Status, and iptables for Policy, each of which could be independently set for privileges.Right, but all those privilege levels are the same: root, and with damn good cause.  So even if they could be different, they're not, which is what's important.  In any case, firestarter's written for the general, most-common case.

> Independent utilities providing the functionality allows the GUI to easily be divided into the components while providing finer grained control over access to each one said:**
> But in this case, it doesn't gain you anything.  And it would be stupid and unnecessarly complicated to privilege seperate into multiple sections--that just makes no sense.  You privilege seperate into what needs root, and what doesn't.  That would be everything else, and the GUI code (i.e., the GTK calls and such), respectively.  

[quote]And, even if syslog was off limits to a user (whether by default or explicit settings), the Events tab would simply not get populated (that's what happens in Ubuntu if you explicitly deny user "read" access to syslog - the Gnome-System-Log applet opens without complaining, but it simply is not populated).Which makes having a seperate event notification tool (which is what you complained about not having) totally useless.  It might as well refuse to run if it can't read syslog.

The expectation that root access will be required for firestarter to do anything hasn't been lessened by this discovery.  In any case, I doubt the Ubuntu developers are going to go through the massive patchwork necessary to make it a reality for a questionable gain.

[quote]And if nothing else, can we agree that it would be nice to have total control over what access is granted in FireStarter's GUI since it seems to be possible?No.  The GUI requires root for all actions.  It's senseless to provide any functionality, even through a seperate application, that doesn't.  Because the only thing you could get is the netstat output, which is rather useless on it's own.

> but perhaps there might be a desire to allow another user access to the FireStarter information without having to grant that user full privileges to iptables just to see the Status and / or Events tabs? Doubtful.  I can't imagine any situation where I'd be using firestarter and I'd want someone to be able to see what's hitting the firewall but not actually change it.

---

### Post by Danielle on 2005-11-29
has anyone used this?
[http://gtk-iptables.sourceforge.net/index.html](http://gtk-iptables.sourceforge.net/index.html)

---

### Post by mcduck on 2005-11-29
[QUOTE=LordHunter317]
Doubtful.  I can't imagine any situation where I'd be using firestarter and I'd want someone to be able to see what's hitting the firewall but not actually change it.[/QUOTE]
Well, some people seem to want to monitor what their firewall is doing, and are even ready to make firestarter GUI to start automaticly with Gnome (without asking for password) to get what they want. I do see the benefit of running a panel applet to monitor firewall messages from syslog instead of compromising your firewall by making it's configuration tool to run without password..

That kind of panel applet is not impossible to do in Ubuntu, as syslog can be viewed. The applet would give people what they want, with much smaller risk to their systems security than the way how people do this now. From two bad options a separate applet to monitor firewall would be the less bad one.

(No, I don't need such a thing. I don't need to anything to tell me that my firewall is continuously blocking stuff from internet. Still, if I could, I'd do such an applet for those who need one. I can even now easily do 'tail -f /var/log/syslog' to get all information needed, and I doubt that separating all firewall-related stuff to display in this applet, and changing applet's icon when new log entrys appear would be too hard a job for anybody who actually can program applets for gnome's panels..)

---

### Post by LordHunter317 on 2005-11-29
[QUOTE=mcduck]Well, some people seem to want to monitor what their firewall is doing, and are even ready to make firestarter GUI to start automaticly with Gnome (without asking for password) to get what they want.[/quote]Yes, but those people have root access and a password to elevate privilege.


The point is: the number of situations where firestarter is used and someone with privilege wants to give someone without privilege the ability to *monitor only* are small enough to be ignored.


> I do see the benefit of running a panel applet to monitor firewall messages from syslog instead of compromising your firewall by making it's configuration tool to run without password..But both require root access, so it's no less of a compromise.  But it's not a compromise at all.  

> That kind of panel applet is not impossible to do in Ubuntu, as syslog can be viewed.***Not without privilege, we've been over this***.


> The applet would give people what they want, with much smaller risk to their systems security than the way how people do this now.There is no real risk now.  The only risk is user error.

> From two bad options a separate applet to monitor firewall would be the less bad one.It's no less bad, as the applet to monitor must be privileged as well.  ***Seperation in this manner doesn't gain you a thing.  If you can't understand that, please don't post.***

---

### Post by mcduck on 2005-11-29
[QUOTE=LordHunter317]
The point is: the number of situations where firestarter is used and someone with privilege wants to give someone without privilege the ability to *monitor only* are small enough to be ignored.[/QUOTE]True, but quite a part of Ubuntu systems aren't multiuser systems but desktops where the only one who wants to monitor firewall is the first user in system, and he already has the privilege to monitor syslogs. So there is no need to give anybody any extra privileges.

> 
But both require root access, so it's no less of a compromise.  But it's not a compromise at all.  

***Not without privilege, we've been over this***.
But that's a privilege that you already have, with no need for anything. First (and on a basic desktop, the only) user on Ubuntu system doesn't need sudo to view the log.

> 
There is no real risk now.  The only risk is user error.
As is with root account. Still, it's disabled. User error is a risk, and when possible, that risk should be minimised.

> 
It's no less bad, as the applet to monitor must be privileged as well.  ***Seperation in this manner doesn't gain you a thing.  If you can't understand that, please don't post.***
Thank you for your kind words. I'm not willing to start a flame war here, but you seem to ignore the point. Such applet would not need any privilege that people don't already have in their Ubuntu systems. Without root password. And sure continuously running a firewall config tool with root privileges is not a good thing. Still you say that not doing so wouldn't benefit anything.

**edit: I just tested this, and even other users (with no right to use sudo) can view /var/log/syslog.**

---

### Post by LordHunter317 on 2005-11-29
[QUOTE=mcduck]True, but quite a part of Ubuntu systems aren't multiuser systems but desktops where the only one who wants to monitor firewall is the first user in system, and he already has the privilege to monitor syslogs. So there is no need to give anybody any extra privileges.[/quote]Which is a Ubuntu specific thing.  Firestarter can't assume that, and Ubuntu is the clear-case exception, not the rule.

Meaning someone would have to write a Ubuntu specific package to accomplish this feat, and then intergrate it with firestarter.  Which is infinitely more work than desirable.

> And sure continuously running a firewall config tool with root privileges is not a good thing.If it's properly privileged seperated, it's no real risk at all.  I doubt firestarter is, but that's a tangential issue.

> **edit: I just tested this, and even other users (with no right to use sudo) can view /var/log/syslog.**If you use the GNOME tool, it gives him the privileges.  The 'Desktop' account in Ubuntu isn actually somewhat privileged.  Giving out the ability to view logs is misguided in my mind for an unprivileged account.

At any rate, while I stand corrected on the privilege thing (I didn't realize Ubuntu added to group adm), the fact still stands that Firestarter can't assume this sort of behavior, it's unique, and the work to make this a reality for Ubuntu would be substantial, unless it was a standalone application.

---

### Post by mcduck on 2005-11-29
I tried it in CLI, with simple 'less /var/log/syslog', on a user account with no sudo privileges.

And yes, I didn't mean that such applet should be part of Firestarter, but that it could be done as a simple separate program.

Now, I'm not much of a programmer, but all information needed is in syslog, and all that one would need to do is parse syslog to get all firewall messages separated, and output them to a window. And of course change the applets icon when new log entries appear. I'd do it myself for all those who want to monitor their firewalls on Ubuntu, but I only have very little programming experience, and we'll be using Ubuntu 8.10 before I've learned how to make Gnome panel applets ;)

---

### Post by LordHunter317 on 2005-11-29
[QUOTE=mcduck]I tried it in CLI, with simple 'less /var/log/syslog', on a user account with no sudo privileges.[/quote]Look at the 'Advanced' or 'Privileges' tab in the GNOME add user application: you gave the account some privilege, you just didn't use it.  I can assure you an account added via 'sudo adduser' can't do any such thing.

---

### Post by mcduck on 2005-11-29
[QUOTE=LordHunter317]Look at the 'Advanced' or 'Privileges' tab in the GNOME add user application: you gave the account some privilege, you just didn't use it.  I can assure you an account added via 'sudo adduser' can't do any such thing.[/QUOTE]
Alright, youre right on that one. It's interesting that new users get such privilege by default.. 

But that makes no difference, as users with default privileges have access to syslog. At least as long as new users are created with Gnome's tool, and the privilege to view logs is not taken away from them. And anyway, as I pointed in my previous post, most people who wish to monitor their firewall are propably the ones who get this privilege by default, as the first user gets all these rights anyway..

---

### Post by LordHunter317 on 2005-11-29
[QUOTE=mcduck]But that makes no difference, as users with default privileges have access to syslog.[/quote]No, they don't. The GNOME Add User tool is going above and beyond default, which was my whole point (poorly stated).  Moreover, even if it was a systemwide default, it's nonstandard.

---

### Post by fct on 2005-11-30
Normal user:

```
$ cat /var/log/syslog
cat: /var/log/syslog: Permission denied
$ iptables -L
FATAL: Error inserting ip_tables (/lib/modules/2.6.12-10-386/kernel/net/ipv4/netfilter/ip_tables.ko): Operation not permitted
iptables v1.3.1: can't initialize iptables table `filter': Permission denied (you must be root)
Perhaps iptables or your kernel needs to be upgraded.
$
```

Firestarter is not a joke. It's a nice GUI to set up iptables and monitor the configuration **with root privileges**.

If you are oblivious enough to leave your graphical session open to malicious users, the last thing you should worry about is someone playing with your firewall settings. Your data can be lost with a simple "rm -fr ~".

So forget about advanced security discussion if you're ignoring the basics.

---

### Post by 23meg on 2005-11-30
Bottom line: 

Do you want your kernel IP routing messages hidden completely? Don't run syslogd and klogd with privileges.

Do you want your kernel IP routing messages available but not shown all the time? Leave things as default and run the Firestarter GUI only when you need to configure iptables.

Do you want to constantly monitor your IP routing stats and still be able to adjust the rules with password authentication? Tail the syslog and run the Firestarter GUI only when you need to adjust iptables.

Do you not find a terminal tail handsome enough? Make a [transparent terminal]("http://www.ubuntuforums.org/showthread.php?t=81727") for it, or code an Ubuntu-specific GTK app yourself.

---

### Post by anil_robo on 2005-12-03
Please have a look at the attached image, and tell me what does it mean?:confused:
[ATTACH]4090[/ATTACH]

---

### Post by fct on 2005-12-03
Someone from the specified IP tried to connect to the specified port on your computer using the TCP protocol.

---

### Post by Othersider on 2005-12-03
[QUOTE=anil_robo]Please have a look at the attached image, and tell me what does it mean?[/QUOTE]

In this case, looks like you received packets from a Northwestern University server.

---

### Post by anil_robo on 2005-12-05
Okay, I got it - someone was trying to establish a connection with my computer, and firestarter interrupted it. SInce I'm a noob, I'd like to ask something simple:
1. Is what I showed in my screenshot above dangerous?
2. SHould I "do something" about it?
3. If yes, what should I do about it?

---

### Post by fct on 2005-12-06
Since firestarter blocked it, it's not dangerous at all.

You'll probably get more alerts like that, from bots that are scanning computers on the net to check if they are infected by a trojan that allows them to take control of the computer. But it's mostly Windows machines that are affected.

---

### Post by prizrak on 2005-12-06
There is this huge war over Firestarter GUI being POSSIBLY insecure. People are completely ignoring the fact that your user password is used for root functionality which makes things less secure since someone who intercepts your user password will have full access to the system. Additionally the GUI tool cannot be compromised remotely without having your user password (or a way to get around it) which means that on a default Ubuntu install (not sure if you could create a separate sudo password) they will have access to your entire system anyways. If someone has physical access to your computer with bad intentions you are screwed, you can lock your screensaver but I can hard shutdown your box boot from a Knoppix CD copy all your files or delete them. I can take a bat to your CPU and make it completely unbootable, so I think the little icon running next to your clock is the LEAST of your worries.

---

