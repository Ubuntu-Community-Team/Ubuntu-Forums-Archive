---
title: "Sudo Permissions in startup..."
date: 2009-09-14
forum: Security
---

### Post by M!SF!TS on 2009-09-14
Hello, Ubuntu Forums!

I dont know if this is the right place to post this, but i figured maybe it was ? because it has to do with root permissions and a firewall...

I wrote a handy little start-up script. it runs my conkys, and my embedded terminal and cairo-dock when i when i start up my computer, to you know... do what computers are SUPPOSE to do, make life easier.

and in order to make my life even EASIER, i would like my firewall to start up with all my other neat little programs... but, in order to do that i need to beable to give it root permissions i tried this...

sudo firestarter &

but it didnt start up, and i believe it is because i need to give it the password... how would i do this in a startup script?

Thanks, -Nick

---

### Post by keplerspeed on 2009-09-14
Firestarter is just the GUI, iptables is always running. So your firewall will be running, after a reboot. For more info:

[http://ubuntuforums.org/showthread.php?t=542756](http://ubuntuforums.org/showthread.php?t=542756)
[http://ubuntuforums.org/showthread.php?t=110497](http://ubuntuforums.org/showthread.php?t=110497)

---

### Post by tlarkin on 2009-09-14
Can't you have init.d run a log in hook script as root?

---

### Post by lovinglinux on 2009-09-14
You don't need to run Firestarter at startup or even after. In fact you shouldn't even run it all the time, due to security reasons. You should use Firestarter to create the firewall rules, then close it and forget about it. As already mentioned, the real firewall will be running all the time in the background. Besides, is it very likely that you don't even need a firewall.

---

### Post by M!SF!TS on 2009-09-16
[SOLVED]

[http://ubuntuforums.org/showthread.php?t=1267472](http://ubuntuforums.org/showthread.php?t=1267472)

---

### Post by tlarkin on 2009-09-16
> **M!SF!TS said:**
> [SOLVED]

[http://ubuntuforums.org/showthread.php?t=1267472](http://ubuntuforums.org/showthread.php?t=1267472)

That seems like a lot of work and also a security hole.  That means any user or process can launch that with out any authentication.

I had suggested you use init.d to launch your script/app since init.d is basically the "brain" launchdaemon so to speak and it will launch all services at start up.

I googled a quick and dirty tutorial for you

[http://www.ubuntu-howto.info/howto/how-to-execute-a-command-program-or-script-at-startup-init-mini-howto](http://www.ubuntu-howto.info/howto/how-to-execute-a-command-program-or-script-at-startup-init-mini-howto)

Here is a thread from this forum that kind of out lines it.

[http://ubuntuforums.org/showthread.php?t=37830](http://ubuntuforums.org/showthread.php?t=37830)


init.d runs things as root, as system daemons and you can apply them to a user, or the system.  

If this were a production work environment of Linux boxes init.d would be the proper and more secure way of doing this.  Just a FYI for you.

---

### Post by M!SF!TS on 2009-09-16
Thanks, looks like will do that... how does it open a security hole tho? in order to open the Sudoers file, you need root privileges in the first place, and i only allowed 1 program...

---

### Post by M!SF!TS on 2009-09-16
WOW, your way or the "acceptable way" is WAAAAYYYYYY more complicated... my way requires 4 simple steps, and that's pretty much it, your way required a multitude of steps and is much more confusing to the the average newbie (myself) im not positive I could even do that with out a good solid 5 to 6 hours of "tinkering"

this is not the first time i had this issue, where the "accepted way" is MUCH MUCH more difficult, if it is more difficult why is it "accepted" computers are suppose to make life easier, not give you more work... at least it though... i guess....

---

### Post by cariboo on 2009-09-16
The problem is, that sometimes the easy way is the insecure way, Look at all the Windows systems that were cracked when MS made a web server easy to set up.

As has been said in this forum many times, security is like an onion, the more layers of security, the harder it is for someone to crack your system.

---

### Post by tlarkin on 2009-09-17
> **M!SF!TS said:**
> WOW, your way or the "acceptable way" is WAAAAYYYYYY more complicated... my way requires 4 simple steps, and that's pretty much it, your way required a multitude of steps and is much more confusing to the the average newbie (myself) im not positive I could even do that with out a good solid 5 to 6 hours of "tinkering"

this is not the first time i had this issue, where the "accepted way" is MUCH MUCH more difficult, if it is more difficult why is it "accepted" computers are suppose to make life easier, not give you more work... at least it though... i guess....

Sorry, I did not know you were a newbie.  That is OK, I was a newbie once too, and I am mostly an OS X user to be honest so I am use to using launch agents with launchd, but init.d is pretty much the same thing but for Linux.

All you need to do is give your script execute permissions, toss it in /etc/init.d/myscript.sh.  Next you just tell init.d to run your script according to the run level and frequency.  Really, my method is only a few steps as well.  

Anything that runs as root with no authentication can be a security hole.  Look at Windows, how every user/process runs as root and nothing requires authentication and look how secure it is.

---

### Post by M!SF!TS on 2009-09-17
So, is this a security hole then to ?

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

all the way at the bottom of the page it has a section that is common uses or something to the effect, where it shows you how to edit the Sudoers file so you dont have to enter a password to shutdown or reboot from the terminal

would that be a security hole then also ? or no because its not running a program, or something. ?

---

### Post by M!SF!TS on 2009-09-18
Well... it looks like im deleting the firestarter startup thing i created myself :(  i will just have to launch it manually until I get enough time to do it the right way...(damn it just when i though i could do something for myself and write a tutorial to help someone else... DAMN IT!!! lol...)

okay... lets hope work is slow this weekend.

im going to save this thread so i got a reference when i start "tinkering" thanks alot for your guy's help...

---

### Post by Leviathan88 on 2009-09-18
This thread appears to be marked as solved?  Anyway if one browses through the "security sticky" [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812).  Then one would encounter the how to firestarter link: [http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html).  It is from thereon pretty straightforward on how to enable firestarter during boot up.  I hope this helps?

---

### Post by tlarkin on 2009-09-18
I would just like to say, while your original method may not be the best practice for security, it is still a very valid method.  Also, if this is your personal computer and no one else uses it, it is probably going to be OK.

If there are other people using that computer they could maybe make an alias in their bash profile or something of the like to run a different command but run it as root.  

I have machine that need to connect to old versions of networking protocols that don't support encrypted passwords.  So, they send them in clear text.  I don't like doing this, but I have to because of some old legacy servers at my work that run older stuff.  Now, once they get replaced, that is a different story.

I was only trying to point out to you that there is probably a better more supported method of having init.d run it over editing config files and modifying the /etc/sudoers as well.

There are always many different ways to accomplish the same goal.

---

### Post by M!SF!TS on 2009-09-18
> **tlarkin said:**
> There are always many different ways to accomplish the same goal.

Yeah, live, & learn. Does anyone have a way to do this the proper way in easy to understand format. and i don't mean easy for YOU I mean easy for people who don't know what your talking about. honestly I kind of started out on a mission, I wrote 2 tutorials on simple things I know how to do. and tried to make them literally stupid proof... but one of them got jailed. I'm just sick of all this intermediate to advanced talk... and really no one talks like they would talk to a beginner, in a way it is pretty unattractive... for a couple reasons, 1. this is the only source of help a Linux user has, unlike Microsoft, or Mac, or any other Corporate business, people totally unfamiliar trying to learn new things, this is their life line... it actually did turn me off to Linux my first go around, I quit ubuntu, for a little less than a year i said F*&% it and reinstalled my factory image of Microsoft. I needed something reliable that i could use efficiently, but i came back because Microsoft gave me issues like they always has... Honestly in turn if Linux is to be successful its going to have to do what Microsoft don't do, and its already half way their. with providing a OS that is stable. the other thing, besides the sales aspect of getting people to take the plunge, is usability, ubuntu has made the best progress so far than any other distro, but honestly its still not quite their... and it all starts here. in the forums. this is ubuntu's Service & Support life line...

I'm actually challenging all of you...

I'm challenging you to take your knowledge of Linux, and start writing Tutorials. I'm a newbie and I already wrote 2. And I am also Challenging THIS Forum, to put all of the tutorials in a archive, with a easy search bar so people and finger threw them easily, find the issue they are having and being able to fix it. within a reasonable amount of time...


Here is the Challenge, Think of some basic knowledge, basic things you think every newbie should know about this system, COIN a good name for it (an example of a good name would be, if you was to google it, what would your write in the google search bar) and look to see if anyone on the Ubuntu Forums have done it before. (if it has been done before just not on the Ubuntu Forums... it don't count. and that could be a good first tutorial...) If yes, then think of something else, If no... their is your new project.

Who is up for the Challenge. And remember when your write it. it has to be written in a way it is easily understood. (just because you can understand it don't mean "Mr. Joe Newbie" understands it. "Mr. Joe Newbie" just came from using Microsoft for the last 15 or so years of his life and don't even know basic Terminal Commands because you don't use Terminal in Microsoft.(and if someone tries to argue about not using a terminal in Microsoft "its called a command prompt" I challenge you to play Russian roulette with a semi-auto)

Also, not everyone is as smart as you. so when you write a Tutorial, don't write it, to stroke your own EGO, like "Your so smart" "Your so cool" be down to earth with your audience, be humble, doctors do it... they don't use medical terms to family members, and if they do, they then explain it in as easy as English as they can... so when you write it, be real with it. no one cares how intelligent you are. because we are not and your impressing no one.(I had to add this part because if this catches on, trust me we will get a Weiner who will try and show-off, showing off is human nature, fight it)

if you think this will add real benefit visit this. and say something... maybe we can actually help someone instead of just confusing them...

[http://ubuntuforums.org/showthread.php?t=1011086](http://ubuntuforums.org/showthread.php?t=1011086)

---

