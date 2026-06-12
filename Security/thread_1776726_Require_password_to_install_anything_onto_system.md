---
title: "Require password to install anything onto system?"
date: 2011-06-06
forum: Security
---

### Post by toolmania1 on 2011-06-06
[FONT=Calibri]Is there any way torequire a password for anything to be installed onto my computer?  For example, lately, I clicked on an image in googleimages that ended up installing something onto my pc.  If a password was required for any installation, this would not have happened.  [/FONT]

---

### Post by Dave_L on 2011-06-06
What exactly was "installed"?

If you're using firefox for browsing, the Noscript add-on is highly recommended.

---

### Post by CandidMan on 2011-06-06
If you have a typical 'buntu setup, then unless you came across a tailored exploit nothing will have been 'installed' any higher than /home/username/
That's not to say you didn't actually came across an exploit.

Apparmor is the de facto protection for 'buntu. I noticed in your previous post you're using SELINUX. If I remember rightly it only separates system and user processes, so anything your browser has full reign over your home folder.

---

### Post by doas777 on 2011-06-06
I have to agree with the others, apparmor is your best bet.

the rest of your system (everything outside your home) should be safe by default, as only root is allowed write access, and would require sudo/gksu to install, and the installer would have to have the ability to set permissions to enable the execute bit.
that means the only location the browser can write to is within your /home/user directory.

apparmor restricts your browser to only have access to resources it requires to function, and thus limits any potential damage to those specific locations.

in the long run, that is the best you can do. a browser by definition needs the ability to download files from the internet and write them to disk. in the case of executable content (flash/java) it must also be able to execute files it writes.

---

### Post by toolmania1 on 2011-06-06
Yes, I use the NoScript add on.  I actually found through an RSS Feed I get from a security web site that there was a flash vulnerability just fixed the other day for cross site scripting.  Guess what google is written in?  

Anyways, thanks for the advice.  No script is pretty awesome.  I use Ghostery as well.  They are kinda similar.

Also, I don't know what was installed.  Another user in my house told me what happened.  I did not even boot the pc up in Ubuntu to find out.  I just stuck the install cd back in and wiped it.

> **Dave_L said:**
> What exactly was "installed"?

If you're using firefox for browsing, the Noscript add-on is highly recommended.

---

### Post by toolmania1 on 2011-06-06
I am going to install app armor tonight I believe.  I read some nice things on it.  Thanks for the info.  I thought that nothing would get installed any higher than that.  But, you never know when the first big outbreak could occur.

> **CandidMan said:**
> If you have a typical 'buntu setup, then unless you came across a tailored exploit nothing will have been 'installed' any higher than /home/username/
That's not to say you didn't actually came across an exploit.

Apparmor is the de facto protection for 'buntu. I noticed in your previous post you're using SELINUX. If I remember rightly it only separates system and user processes, so anything your browser has full reign over your home folder.

---

### Post by toolmania1 on 2011-06-06
Sounds good.  Thanks for the info.

Like I posted above, I am going to set up app armor right now :-)

> **doas777 said:**
> I have to agree with the others, apparmor is your best bet.

the rest of your system (everything outside your home) should be safe by default, as only root is allowed write access, and would require sudo/gksu to install, and the installer would have to have the ability to set permissions to enable the execute bit.
that means the only location the browser can write to is within your /home/user directory.

apparmor restricts your browser to only have access to resources it requires to function, and thus limits any potential damage to those specific locations.

in the long run, that is the best you can do. a browser by definition needs the ability to download files from the internet and write them to disk. in the case of executable content (flash/java) it must also be able to execute files it writes.

---

### Post by toolmania1 on 2011-06-07
So, just to make sure I understand, there is no way to require a password to be set for any installation on the system, correct?

I see passwords being required when I use sudo, when I go through the Ubuntu Software Center to install programs, and when I use Synaptic to install things.  But, when I install items from the internet myself, I am not prompted for a password in all cases ( cannot remember specific ones at this moment, but can add later when I find an example ).

I would think that requiring password confirmation on every single thing that gets installed onto a system would cut down on a lot of malware issues.  Although, it may get annoying in instances like airport security, but maybe it could be configured as on or off.

---

### Post by doas777 on 2011-06-07
keep in mind, there isn;t really such a thing as "installing" in the context of which you speak.
yes, anything "installed" via dpkg (apt-get/synaptic/softwarecenter) requires a password, but you do not need to use dpkg to write an executable file to your cache, mark it to allow execution and running it. as such this is not an "installation". in fact, the only reason dpkg requires a password is because teh file permissions in the location it wishes to install the file require root to write. since /home/user/ is writable by your user, installing a package into it would not require a password.

there is an old unix command "install". all it does is copy the executable to the folder specified, and sets the execute bit. 

so there really is no differance between writing a file to your disk (temp internet files, cookies, content pages, etc) and installing a program to run from /home/user/

---

### Post by CharlesA on 2011-06-07
> **toolmania1 said:**
> Yes, I use the NoScript add on.  I actually found through an RSS Feed I get from a security web site that there was a flash vulnerability just fixed the other day for cross site scripting.  Guess what google is written in? 

Google has been using HTML5 for a while now hasn't it?

---

### Post by tgm4883 on 2011-06-07
> **toolmania1 said:**
> Guess what google is written in?

Javascript?

---

### Post by doas777 on 2011-06-07
> **tgm4883 said:**
> Javascript?
that was my guess.

---

### Post by CharlesA on 2011-06-07
> **tgm4883 said:**
> Javascript?
I was thinking html5 with php (but javascript is likely as well)

---

### Post by toolmania1 on 2011-06-07
Maybe.  I knew it was using flash.  Well, if that is the case now, maybe there is another bug.  Yikes!


> **CharlesA said:**
> Google has been using HTML5 for a while now hasn't it?

---

### Post by tgm4883 on 2011-06-07
> **toolmania1 said:**
> Maybe.  I knew it was using flash.  Well, if that is the case now, maybe there is another bug.  Yikes!

I don't think google images has ever used flash

---

### Post by toolmania1 on 2011-06-07
Regarding:


"since /home/user/ is writable by your user, installing a package into it would not require a password."


If we cannot require a password then can we change this so that /home/user is not always writable until we want it to be? You guys know what I am getting at.  Without knit picking at details, is there anything similar so that the OS can stop any outside installations until I tell it to.  I know I am already telling it to.  But I want everything brought to my attention is the key.  A password would do this on every single thing that was being installed onto a computer.  Does this make sense what I am asking?



> **doas777 said:**
> keep in mind, there isn;t really such a thing as "installing" in the context of which you speak.
yes, anything "installed" via dpkg (apt-get/synaptic/softwarecenter) requires a password, but you do not need to use dpkg to write an executable file to your cache, mark it to allow execution and running it. as such this is not an "installation". in fact, the only reason dpkg requires a password is because teh file permissions in the location it wishes to install the file require root to write. since /home/user/ is writable by your user, installing a package into it would not require a password.
 
there is an old unix command "install". all it does is copy the executable to the folder specified, and sets the execute bit. 
 
so there really is no differance between writing a file to your disk (temp internet files, cookies, content pages, etc) and installing a program to run from /home/user/

---

### Post by toolmania1 on 2011-06-07
Ok.  Well, regardless, there was a redirect and something was installed onto my computer.



> **tgm4883 said:**
> I don't think google images has ever used flash

---

### Post by toolmania1 on 2011-06-07
Ok.  I am going with AppArmor later today.  Thanks!


> **doas777 said:**
> I have to agree with the others, apparmor is your best bet.
 
the rest of your system (everything outside your home) should be safe by default, as only root is allowed write access, and would require sudo/gksu to install, and the installer would have to have the ability to set permissions to enable the execute bit.
that means the only location the browser can write to is within your /home/user directory.
 
apparmor restricts your browser to only have access to resources it requires to function, and thus limits any potential damage to those specific locations.
 
in the long run, that is the best you can do. a browser by definition needs the ability to download files from the internet and write them to disk. in the case of executable content (flash/java) it must also be able to execute files it writes.

---

### Post by tgm4883 on 2011-06-07
> **toolmania1 said:**
> Ok.  Well, regardless, there was a redirect and something was installed onto my computer.

"Installed" has a certain connotation, nothing was "Installed" to your system without a password. Downloaded perhaps, but not installed. 

You still really haven't given any details about what happened. What was downloaded, did it run, etc. Without any specifics some people might write you off and say you are a troll. 

My recommendation:
Install and configure AppArmor and be done with it.

---

### Post by toolmania1 on 2011-06-07
Ya, good point.  If I am a troll, I am a troll.  I realize I did not get the information so that people could check it out.  I did not mean to cause any confusion.  I did not want to open up my system again to find out.  I honestly wasn't the user in front of the pc.  When I got home, the pc was turned off.  I stuck the Ubuntu cd in and installed from scratch.  So, sorry, I don't have more info.  I am going to mark this as closed.  I don't want to offend anyone.  You're right.  Thanks everyone for your help.  I will learn to make sure and have more information next time.  Later!


> **tgm4883 said:**
> "Installed" has a certain connotation, nothing was "Installed" to your system without a password. Downloaded perhaps, but not installed. 
 
You still really haven't given any details about what happened. What was downloaded, did it run, etc. Without any specifics some people might write you off and say you are a troll. 
 
My recommendation:
Install and configure AppArmor and be done with it.

---

### Post by bodhi.zazen on 2011-06-07
> **toolmania1 said:**
> Guess what google is written in?  

[LOLCODE](http://lolcode.com/) ?

[img]http://lolcode.com/lib/tpl/minima/images/header_medium_green.jpg[/img]

---

### Post by JKyleOKC on 2011-06-08
> **toolmania1 said:**
> Ya, good point.  If I am a troll, I am a troll.  I realize I did not get the information so that people could check it out.  I did not mean to cause any confusion.  I did not want to open up my system again to find out.  I honestly wasn't the user in front of the pc.  When I got home, the PC was turned off.  I stuck the Ubuntu CD in and installed from scratch.  So, sorry, I don't have more info.  I am going to mark this as closed.  I don't want to offend anyone.  You're right.  Thanks everyone for your help.  I will learn to make sure and have more information next time.  Later!The simplest way to protect your system from such things is to create a second user for it, with a blank password, and if you have automatic login enabled, set it to log in as that second user. The second user will NOT have the ability to install anything, although it will be able to clobber its own home directory. Your home directory, however, will be safe, and if someone else does the same thing again and clobbers the restricted home directory you'll be able to clear it up easily without any damage to your own data or to the system. Then log out of your user id any time that you leave the system. Anyone else will only be able to get to the new user account.

I'd guess that what happened was probably similar to something that happened to me a few weeks ago. I received an email purporting to be from a cousin, and opened it. There was nothing inside but a link, and against all security principles I clicked on it. When nothing happened immediately, I shut down the mail program and opened a browser -- and sure enough got a pop-up message that an automatic virus scan was running and had detected more than a hundred baddies on my system!

Fortunately the mail program and browser were running in a virtual machine that was pretty well locked down, and some quick work with a couple of cleaning programs got rid of the offending single scareware package that had been installed by the fake message when I clicked on its link.

These scareware programs are, for the most part, written in JavaScript to look as if they were actual programs, and their goal is to trick you into downloading still larger trojans and thus conscript your machine into a bot-net without your knowledge. However, their downloads are Windows executable files, and won't run at all under Linux unless you install them within Wine -- and so far as I can tell they are not smart enough to do so themselves. Thus even though you were told that something had been installed, the odds are good that nothing really had been.

Still, your immediate re-install was probably the best thing you could do at the time anyway. I hope you didn't lose any important date from it...

---

### Post by toolmania1 on 2011-06-08
No, I did not lose important data.  I keep that backed up off line.  



You are right.  The funniest thing the other user noticed was that it said we had windows viruses...lol.  Uh, we're not on windows, lol.  Ya, I have been studying a little bit about cross site scripting and things of that nature.  That is why I reinstalled.  I will look into this other user thing too.  You may be onto something.

Thanks!a



> **JKyleOKC said:**
> The simplest way to protect your system from such things is to create a second user for it, with a blank password, and if you have automatic login enabled, set it to log in as that second user. The second user will NOT have the ability to install anything, although it will be able to clobber its own home directory. Your home directory, however, will be safe, and if someone else does the same thing again and clobbers the restricted home directory you'll be able to clear it up easily without any damage to your own data or to the system. Then log out of your user id any time that you leave the system. Anyone else will only be able to get to the new user account.
 
I'd guess that what happened was probably similar to something that happened to me a few weeks ago. I received an email purporting to be from a cousin, and opened it. There was nothing inside but a link, and against all security principles I clicked on it. When nothing happened immediately, I shut down the mail program and opened a browser -- and sure enough got a pop-up message that an automatic virus scan was running and had detected more than a hundred baddies on my system!
 
Fortunately the mail program and browser were running in a virtual machine that was pretty well locked down, and some quick work with a couple of cleaning programs got rid of the offending single scareware package that had been installed by the fake message when I clicked on its link.
 
These scareware programs are, for the most part, written in JavaScript to look as if they were actual programs, and their goal is to trick you into downloading still larger trojans and thus conscript your machine into a bot-net without your knowledge. However, their downloads are Windows executable files, and won't run at all under Linux unless you install them within Wine -- and so far as I can tell they are not smart enough to do so themselves. Thus even though you were told that something had been installed, the odds are good that nothing really had been.
 
Still, your immediate re-install was probably the best thing you could do at the time anyway. I hope you didn't lose any important date from it...

---

### Post by doas777 on 2011-06-08
> **toolmania1 said:**
> No, I did not lose important data.  I keep that backed up off line.  



You are right.  The funniest thing the other user noticed was that it said we had windows viruses...lol.  Uh, we're not on windows, lol.  Ya, I have been studying a little bit about cross site scripting and things of that nature.  That is why I reinstalled.  I will look into this other user thing too.  You may be onto something.

Thanks!a
just remember, XSS/CSS is a web based attack used to attack a site or user of a site, not an attack on your host. there would be no need to rebuild your system after falling prey to xss, but changing the password on the web page account that was attacked would be a good place to start.

---

