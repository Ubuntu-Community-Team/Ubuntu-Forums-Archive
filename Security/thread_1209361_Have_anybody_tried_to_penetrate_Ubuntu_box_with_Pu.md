---
title: "Have anybody tried to penetrate Ubuntu box with PulseAudio installed?"
date: 2009-07-10
forum: Security
---

### Post by igorzwx on 2009-07-10
If it is so buggy...
All the tools one may need are available in Ubuntu repositories.

---

### Post by igorzwx on 2009-07-11
Imagine "previously unknown vulnerability" in PulseAudio
which is buggy by definition, which is not even beta.

[http://www.theregister.co.uk/2008/03/29/ubuntu_left_standing/](http://www.theregister.co.uk/2008/03/29/ubuntu_left_standing/)
QUOTE:
Shane Macaulay, who played a hand [bringing down a Mac]("http://www.theregister.co.uk/2007/04/20/pwn-2-own_winner/") during last year's Pwn2Own contest, defeated the Vista machine using a previously unknown vulnerability in Adobe Flash. On final day of the CanSecWest conference in Vancouver, Macaulay spent the better part of four hours trying to get the exploit to work. (The delay prompted one spectator to playfully dub the difficulty "hacktile dysfunction.")

[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
QUOTE:
**Adding Users to the PulseAudio groups**

 Next we go to System -> Administration -> and click on Users and Groups. 
Click on Manage Groups, and scroll all the way to the bottom of the list where you will find: 

[LIST]
[*]pulse-access 
[*]pulse-rt 
[/LIST]
Make sure to highlight each, one at a time, and click Properties. Just put a check next to each user that you want to be able to have access to sound. For example, there's "ted" and "root" and "kamilion" listed, and you only want "kamilion" to have access to sound, that's the one to check, leave the other two blank. 
*Note:* The "pulse" group is for pulseaudio internal use, and normal users should not be added to this group. 
End of QUOTE

Just imagine

---

### Post by igorzwx on 2009-07-27
This question seems to be already answered (can be marked as solved):

[http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/](http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/)
**[Clever attack exploits fully-patched *Linux kernel* • The Register]("http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/")**

The exploit code was released Friday by *Brad Spengler* of grsecurity, **...** "Why is it that whenever there is an exploitable *vulnerability* in *Linux*, **...**
[www.theregister.co.uk/2009/07/17/](www.theregister.co.uk/2009/07/17/)**linux**_**kernel**_exploit/ - [Cached]("http://209.85.135.132/search?q=cache:wZBH3pYFhz0J:www.theregister.co.uk/2009/07/17/linux_kernel_exploit/+vulnerability+linux+kernel+PulseAudio+Brad+Spengler&cd=2&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.theregister.co.uk/2009/07/17/linux_kernel_exploit/")

---

### Post by igorzwx on 2009-07-28
[http://www.milw0rm.com/exploits/9208](http://www.milw0rm.com/exploits/9208)
**[PulseAudio (setuid) Priv. Escalation *Exploit* (ubu/9.04)(slack/12.2.0)]("http://www.milw0rm.com/exploits/9208")**

20 Jul 2009 **...** :p Tested with success on *Ubuntu* 9.04 (x86-64) and slackware 12.2.0 **...** groups=17(audio),100(users),104(*pulse*-rt) sh-3.1# uname -a Linux **...**
[www.milw0rm.com/](www.milw0rm.com/)**exploits**/9208 - [Cached]("http://209.85.129.132/search?q=cache:6FD4c7qzX2wJ:www.milw0rm.com/exploits/9208+ubuntu+pulse+exploit&cd=4&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:www.milw0rm.com/exploits/9208")

---

### Post by igorzwx on 2009-07-30
The paper - *[The Economics of Botnets]("http://www.viruslist.com/en/analysis?pubid=204792068")* 
[http://www.theregister.co.uk/2009/07/24/botnet_economics/](http://www.theregister.co.uk/2009/07/24/botnet_economics/)

---

### Post by cariboo on 2009-07-31
Instead of posting confusing links, you can keep track of security problems in Ubuntu by checking out [this]("http://ubuntuforums.org/forumdisplay.php?f=13") forum.

---

### Post by igorzwx on 2009-07-31
" you can keep track of security problems in Ubuntu by checking out [this]("http://ubuntuforums.org/forumdisplay.php?f=13") forum."

Thank you very much!
Very usefull link indeed.

People say that PulseAudio is a kind of network server.
Could you please enlighten me about such things too?

---

### Post by cariboo on 2009-07-31
[list]
[*][Pulseaudio.org]("http://www.pulseaudio.org/")
[*][Wikipedia]("http://en.wikipedia.org/wiki/PulseAudio")
[*] [Ubuntu Pulseaudio]("https://wiki.ubuntu.com/PulseAudio")
[/list]

---

### Post by igorzwx on 2009-07-31
I experted your recommendations about security of
this "network server".

Thanks for the likns.

---

### Post by igorzwx on 2009-07-31
O.K. Let us ask Google:
[http://www.google.com/search?q=security%20of%20pulseaudio&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=security%20of%20pulseaudio&ie=UTF-8&oe=UTF-8)

---

### Post by cariboo on 2009-08-01
You have to know what pulse can do before you start worrying about network security. As it is in a default installation the only port being listened to is 631, which only listens on localhost, and is the cups printing management interface.

If you want to know what is going over the network when the pulseaudio is used for remote listening, set it up and then use wireshark to have a look at the packets.

---

### Post by ridetheteapot on 2009-08-01
did you mean cheddar bay? you need a login for it anyway? and i dont think pulse is the only thing vulnerable.

---

### Post by igorzwx on 2009-08-01
"i dont think pulse is the only thing vulnerable."

This is exactly the point.

You have a lot of other security problems.
You have a web browser too, and you may really need it.
It might be buggy, or not so buggy, but you would not
run your web browser with root privileges.
You would rather do the opposite.

In fact, many people today have problem with sound.
And, not seldom, the pulse gurus propose this magic solution:
QUOTE:
 				 				**Re: Sound output only as root** 			
 			 			 		   		 		 		All you need to do is add youself and** root** to the following groups

pulse

pulse-access

pulse-rt

That is what that message is telling you to do.
End of QUOTE
see: **[COLOR=#980101][B][ubuntu]**[/COLOR] Sound output only as root  [/B]
[http://ubuntuforums.org/showthread.php?t=1221919&page=2](http://ubuntuforums.org/showthread.php?t=1221919&page=2)

Another solution is to remove (and purge) PulseAudio
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)
sudo killall pulseaudio

cp /etc/X11/Xsession.d/70pulseaudio ~/

sudo apt-get purge pulseaudio

If your hardware is supported by OSS4,
you can install OSS4 and enjoy the true sound.
If not, you have to fix ALSA, and this is not so easy to do.

What is PulseAudio?
One Fedora geek told me this:
"I don't think it is a 'bug' in pulse, it is the fact that 
pulse is a sound server and runs at a specific frame rate.  It has to 
move all sound streams to that frame rate in order to play through the 
sound device.  It uses on the fly rate conversion, and this introduces 
artifacts into the sound."

There are two points of view about PulseAudio:

1. The idea was correct, but it was applied in a wrong way.

2. The idea was fundamentally wrong, and the consequences were predictable.

What is true is already a theological problem. We do not need to go here in deep, but for those who are interested in such theological questions, I would propose to read these two works:

1.  Richard Feynman [Cargo Cult Science (pdf)]("http://calteches.library.caltech.edu/51/02/CargoCult.pdf") article with pictures as originally published in *Engineering and Science*, Volume 37:7, June 1974.
[http://calteches.library.caltech.edu/51/02/CargoCult.pdf](http://calteches.library.caltech.edu/51/02/CargoCult.pdf)

2. Mambu: A Study of Melanesian Cargo Movements and Their Social and Ideological Background by Kenelm Burridge (Paperback - 1970)
3 Used & new from $3.99
[http://www.amazon.com/Mambu-Melanesiancargo-Movements-Ideological-Background/dp/B000R3GQW6/ref=sr_1_6?ie=UTF8&qid=1249125382&sr=8-6](http://www.amazon.com/Mambu-Melanesiancargo-Movements-Ideological-Background/dp/B000R3GQW6/ref=sr_1_6?ie=UTF8&qid=1249125382&sr=8-6)

I do not know exactly what is going on, and, therefore, I ask questions here.
It looks like they hacked the Linux kernel to make PulseAudio work,
and this made the Linux kernel vulnerable to exploits.
I would be really grateful, if somebody would provide a
sensible explanation of all these strange things.

---

### Post by ridetheteapot on 2009-08-01
if your really worried about it, just don't use pulse - its not really worth it anyway.
if you miss the feature use jackd - but thats buggy too.

really though what reason is there to have untrusted users logging on remotely to a box that has pulseaudio installed?

---

### Post by cariboo on 2009-08-01
Have a look at this [blog post]("http://drowninginbugs.blogspot.com/2009/02/pulseaudio.html"), you are a little of base, it is a kernel problem, but alsa is the reason.

@igorzwx Your last 2 links really have nothing to do with the topic.

---

### Post by igorzwx on 2009-08-01
"just don't use pulse"

Right! I have already removed PulseAudio,
and installed OSS4.
If you want to try it too, this is the official guide:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Check if you hardware is supported by OSS4
[http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux](http://mercurial.opensound.com/?file/6bf18b4a87d6/devlists/Linux)

"it is a kernel problem, but alsa is the reason."

Thank you very much!!! 
This really a kind of explanation.
You see, pulse was suggested as a fix to ALSA.
ALSA means drivers, first of all,
that is, kernel modules.

---

### Post by igorzwx on 2009-08-01
And this is more technical explanation:
[http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/comments/](http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/comments/)
QUOTE:
"Linux is known to have a major security hole that is unlikely to be fixed in the near future"...
This 'exploit' requires the user to have root in the first place, to inject a setuid program into the system (which would be caught by the next run of tripwire and SELinux wouldn't let it run anyway, but let's not let facts get in the way of a good story).
End of QUOTE

About "setuid program" and all such techniques (in detail), one may read here:
**[*Practical UNIX* and *Internet Security* | O'Reilly Media]("http://oreilly.com/catalog/9781565921481/")** 

This second edition of the classic *Practical UNIX Security* is a complete rewrite of the original book. It's packed with twice the pages and offers even more **...**
oreilly.com/catalog/9781565921481/ - [Cached]("http://209.85.129.132/search?q=cache:S8ZqyAGhsCwJ:oreilly.com/catalog/9781565921481/+practical+internet+and+unix+security&cd=1&hl=en&ct=clnk") - [Similar]("http://www.google.com/search?hl=en&q=related:oreilly.com/catalog/9781565921481/")

---

### Post by ridetheteapot on 2009-08-01
after i decided to upgrade again, and use jaunty - i told myself ill try pulse out and keep it no matter what. It's basically because of a personal frustration i have with ubuntu's package choices on the default install - and i need to get over it or switch distro's - plus jack's stability has deteriorated for me.
as far as cheddar bay is concerned, there is a txt with the demo - theres not really any need to talkabout it here i dont think.

---

### Post by movieman on 2009-08-02
> **igorzwx said:**
> QUOTE:
"Linux is known to have a major security hole that is unlikely to be fixed in the near future"...


Which is, of course, nonsense: the operating system requires a way for non-administrator users to do things that should require administrator priviledges, or to do things as another user. That some programs are setuid without a good reason, or are poorly implemented so that the setuid status can be exploited, is not a 'security hole in Linux' any more than a bug in Firefox allowing people to install malware is a 'security hole in Windows'.

Similarly, the guy who posted this 'exploit' has his own competitor to SELinux, so he has a vested interest in trying to make it look worse than it really is. The whole thing was a dumb coding error, was quickly spotted, is trivial to fix and has been blown way out of proportion... the most interesting aspect is that so many SELinux policies allow programs to map page zero without requiring special priviledge, which is a bad idea which will hopefully soon be fixed.

---

### Post by igorzwx on 2009-08-02
O.K. a more exact quotation:
[http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/comments/](http://www.theregister.co.uk/2009/07/17/linux_kernel_exploit/comments/)
 **Major flaw? # **

 By GettinSadda Posted Saturday 18th July 2009 09:35 GMT
 [INDENT] [IMG]http://www.theregister.co.uk/Design/graphics/icons/comment/boffin_48.png[/IMG]> "Setuid is well-known as a chronic security hole," Rob Graham, CEO of
 > Errata Security wrote in an email. "Torvalds is right, it's not a kernel issue,
 > but it is a design 'flaw' that is inherited from Unix. There is no easy
 > solution to the problem, though, so it's going to be with us for many
 > years to come."
 Um, so doesn't his translate as "Linux is known to have a major security hole that is unlikely to be fixed in the near future"?
 [/INDENT] 
  **Torvalds is right, really # **

 By Tony Hoyle Posted Saturday 18th July 2009 10:07 GMT
 [INDENT] [IMG]http://www.theregister.co.uk/Design/graphics/icons/comment/stop_48.png[/IMG]This 'exploit' requires the user to have root in the first place, to inject a setuid program into the system (which would be caught by the next run of tripwire and SELinux wouldn't let it run anyway, but let's not let facts get in the way of a good story).
 If the bad guy gets root = game over. Anything else they do is just icing.. even SELinux isn't an absolute defence against this.
 I agree the optimisation flag on gcc is the real bug - it should be flagging these dereferences as errors not deleting the tests.
 [/INDENT]

---

### Post by igorzwx on 2009-08-02
just typed 3 words into google:
[http://www.google.com/search?q=linux%20security%20hole&ie=UTF-8&oe=UTF-8](http://www.google.com/search?q=linux%20security%20hole&ie=UTF-8&oe=UTF-8)

---

### Post by igorzwx on 2009-08-02
July 20, 2009 11:48 AM PDT              
                                 **Linux exploit gets around security barrier**

[http://news.cnet.com/8301-1009_3-10291022-83.html](http://news.cnet.com/8301-1009_3-10291022-83.html)
QUOTE:
"Having SELinux enabled actually weakens system security for these kinds of exploits," he wrote.

---

