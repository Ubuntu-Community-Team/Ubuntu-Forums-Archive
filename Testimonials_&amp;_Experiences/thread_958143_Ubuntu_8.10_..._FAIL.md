---
title: "Ubuntu 8.10 ... FAIL"
date: 2008-10-25
forum: Testimonials &amp; Experiences
---

### Post by Geekkit on 2008-10-25
Here's what failed for me on a Toshiba Satellite A300:

- In two hours, system froze THREE times ... had to cold boot to get back. One freeze when synaptic downloading, two other times when just doing whatever
- Enable share (SAMBA), downloaded services, then it asks to restart session? Why? Didn't do that before
- Compiz doesn't work and no link to any sort of "restricted drivers"? I've seen others with Toshiba laptops with compiz before which seemed to work
- Google gadgets won't install anymore (did in 8.04) ... missing dependencies
- Rhythmbox keeps cutting out and just crashing/ disappearing for no reason (might be related to a below item)
- Share a folder (or more) but no menu item under System->Administration->Share folders menu item? So I can't see a listing of shared folders now? So very lame! Why on Earth did they remove this?!
- Rhythmbox has a bunch of links to shoutcast servers but half don't work
- Fade in/fade out is cool except when it's finished it shows memory garbage (random colors and characters) right after finishing this effect thus ruining the funkiness of it
- Xawtv freezes (with the web cam)
- Cheese freezes up too (with the web cam)
- Network connectivity is flaky ... keeps dropping for no apparent reason
- Synaptic package manager "quick search" does absolutely NOTHING. Seriously, what is this suppose to do?
- Synaptic package manager is BUGGY, yes you heard me. Sometimes regular search comes up with packages searched sometimes NOT. If it doesn't, restart synaptic package manager and try again, you'll see how this new "feature" works.
- Nothing about my hardware? Not even something accidentally not checked in the main menu? No "sysinfo" or "about my hardware"? :(
- Network settings? Where is the link to it, where do I check and configure stuff (i.e., computer name, etc.)?
- Attempting to go into another Ubuntu computer with shared files/folders and open its folders gives me the error message: "The folder contents could not be displayed" [folder name] could not be found. Perhaps it has recently been deleted." Other buntu versions don't seem to have a problem neither do Vista or XP. Rather funny actually because printing to the shared printer on that system seems to work.
- STILL had to do sudo gedit /etc/samba/smb.conf ... I mean come on.

I'll wait for 9.04. If it's the same as 8.10 (which is one step forward and five steps back), I'm getting off the buntu bus. I'm quite disappointed. I suspect you're going to see reviews in the coming weeks that tear this version apart.

Flame away ...

---

### Post by hyper_ch on 2008-10-25
> **Geekkit said:**
> I suspect you're going to see reviews in the coming weeks that tear this version apart.

And that would be different compared to all the other releases since dapper (maybe even before) in what way?

---

### Post by L815 on 2008-10-25
In my experience, 8.10 has worked better than any previous version (on my hardware). The only gripe I have left is video/flash tearing :/

---

### Post by Yashiro on 2008-10-25
[COLOR="Gray"]- In two hours, system froze THREE times ... had to cold boot to get back. One freeze when synaptic downloading, two other times when just doing whatever[/COLOR]
No idea. Sounds like your network driver is broken maybe.

[COLOR="Gray"]- Enable share (SAMBA), downloaded services, then it asks to restart session? Why? Didn't do that before[/COLOR]
Because it needs a relog to get the permissions working. It's a cheap workaround for a common 'my samba won't work' complaint.

[COLOR="Gray"]- Compiz doesn't work and no link to any sort of "restricted drivers"? I've seen others with Toshiba laptops with compiz before which seemed to work[/COLOR]
3d support is fubar with the new Xorg.

[COLOR="Gray"]- Google gadgets won't install anymore (did in 8.04) ... missing dependencies[/COLOR]
Needs updating then.

[COLOR="Gray"]- Rhythmbox keeps cutting out and just crashing/ disappearing for no reason (might be related to a below item)[/COLOR]
Badly coded.

[COLOR="Gray"]- Share a folder (or more) but no menu item under System->Administration->Share folders menu item? So I can't see a listing of shared folders now? So very lame! Why on Earth did they remove this?![/COLOR]
It doesn't exist by default in 8.04 either. Perhaps you mean places? Bad idea to remove that if so.

[COLOR="Gray"]- Rhythmbox has a bunch of links to shoutcast servers but half don't work[/COLOR]
Badly coded.

[COLOR="Gray"]- Fade in/fade out is cool except when it's finished it shows memory garbage (random colors and characters) right after finishing this effect thus ruining the funkiness of it[/COLOR]
Video is fubar with the new Xorg.

[COLOR="Gray"]- Xawtv freezes (with the web cam)[/COLOR]
Badly coded. Sounds like a driver error.

[COLOR="Gray"]- Cheese freezes up too (with the web cam)[/COLOR]
Badly coded. Sounds like a driver error.

[COLOR="Gray"]- Network connectivity is flaky ... keeps dropping for no apparent reason[/COLOR]
Badly coded. Sounds like a driver error.

[COLOR="Gray"]- Synaptic package manager "quick search" does absolutely NOTHING. Seriously, what is this suppose to do?[/COLOR]
Badly coded.

[COLOR="Gray"]- Synaptic package manager is BUGGY, yes you heard me. Sometimes regular search comes up with packages searched sometimes NOT. If it doesn't, restart synaptic package manager and try again, you'll see how this new "feature" works.[/COLOR]
Badly coded.

[COLOR="Gray"]- Nothing about my hardware? Not even something accidentally not checked in the main menu? No "sysinfo" or "about my hardware"?[/COLOR]
?

[COLOR="Gray"]- Network settings? Where is the link to it, where do I check and configure stuff (i.e., computer name, etc.)?[/COLOR]
System, Administration, Network.

[COLOR="Gray"]- Attempting to go into another Ubuntu computer with shared files/folders and open its folders gives me the error message: "The folder contents could not be displayed" [folder name] could not be found. Perhaps it has recently been deleted." Other buntu versions don't seem to have a problem neither do Vista or XP. Rather funny actually because printing to the shared printer on that system seems to work.[/COLOR]
Funky indeed.

[COLOR="Gray"]- STILL had to do sudo gedit /etc/samba/smb.conf ... I mean come on.[/COLOR]
Then change it's permissions. Or do you mean it should all be gui based?

---

### Post by NexusGS on 2008-10-25
hmmm, maybe you noticed that it's not the final version??? Or am i wrong??

---

### Post by Teamgeist on 2008-10-25
> **Geekkit said:**
> Here's what failed for me on a Toshiba Satellite A300:

- Compiz doesn't work and no link to any sort of "restricted drivers"? I've seen others with Toshiba laptops with compiz before which seemed to work
Go to System--> Administration--> Hardware Drivers
What kind of Video card do you have?
If it's an older NVIDIA: NVIDIA has not delivered any Xorg 7.4/XServer 1.5 compatible driver for those cards yet. Not Ubuntus fault.
> - Google gadgets won't install anymore (did in 8.04) ... missing dependencies
Tell Google to resolve the dependencies then. THEY coded it and made it prproetary. Not Ubuntus fault.
> - Rhythmbox keeps cutting out and just crashing/ disappearing for no reason (might be related to a below item)
- Rhythmbox has a bunch of links to shoutcast servers but half don't work
As much as I used to like Rhythmbox, I have settled with banshee. Far more active development. Maybe you wann give it a shot.
> - Xawtv freezes (with the web cam)
- Cheese freezes up too (with the web cam)
Known bug in gstreamer that is beeing worked on.
[https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918](https://bugs.launchpad.net/ubuntu/+source/libv4l/+bug/260918)

> - Synaptic package manager "quick search" does absolutely NOTHING. Seriously, what is this suppose to do?
No it's not. YOU just haven't figured out how to use it.
Do a regular search and if you get a lot of hits THEN try "quick search"

> I'll wait for 9.04. If it's the same as 8.10 (which is one step forward and five steps back), I'm getting off the buntu bus. I'm quite disappointed. No one forces you. Linux is FREE. Choose something (a distribution) that suits you better.

> I suspect you're going to see reviews in the coming weeks that tear this version apart.
As usual.
I'd like to see the comments of those poeple when they install Ubuntu (or Linux in general) on a machine with parts they thought over before they bought them. Making the right decisions in advance does not get you in trouble with unsupported Hardware (e.g. Wireless Adaptor) afterwards.

---

### Post by spawn. on 2008-10-25
You give up too easily.

---

### Post by Ripfox on 2008-10-25
Samba always needed a log-out log-in. It just tells you you need to now. Improvement! ;)

---

### Post by fiddledd on 2008-10-25
To the OP:

It's not the final release yet, maybe some or all of your problems will get fixed. Obviously you can file bug reports to help with the final release. But it's not unusual for some to have problems.

I've not used Ubuntu for a while, so I can't say whether you are alone in having problems. But as I said, it's not the final release yet, you might be lucky.:)

On a side note, how on earth did Windows and Vista get brought up. There are many things that might be causing the problems the OP is having, but I'm pretty sure none has anything to do with Microsoft.

---

### Post by phoenix_snake on 2008-10-25
> **fiddledd said:**
> 
On a side note, how on earth did Windows and Vista get brought up. There are many things that might be causing the problems the OP is having, but I'm pretty sure none has anything to do with Microsoft.

Exactly, the person who started it said

> Maybe I should cry on the windows forum about that and expect a solution to magically appear.

not only did he or she start of with windows but some of them are actually angry at posting a bad experience in a **testimonial** section....

what do you think of that? :p

---

### Post by wolfen69 on 2008-10-25
> **Geekkit said:**
> I suspect you're going to see reviews in the coming weeks that tear this version apart.



yeah, you're right. every single person in the world will have the same issues as you. as we all know, your computer is the gold standard by which all os's are judged. i bow down to you, oh wise one. i look forward to your next nuggets of wisdom.

---

### Post by overdrank on 2008-10-25
Thread closed for staff review and cooling off.

---

### Post by bapoumba on 2008-10-25
I've removed 9 posts from this thread.

---

### Post by bapoumba on 2008-10-25
The thread will remain closed for 24 hours. Thanks.

---

