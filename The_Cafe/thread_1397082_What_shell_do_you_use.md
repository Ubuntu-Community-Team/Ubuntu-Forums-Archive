---
title: "What shell do you use?"
date: 2010-02-02
forum: The Cafe
---

### Post by Diametric on 2010-02-02
I'm just curious what shell you folks use and why?  I use bash because it's the default shell and from the book I'm reading on it bash appears to be the most flexible. 
 
Anyone else?

---

### Post by ubudog on 2010-02-02
Bash.

---

### Post by NightwishFan on 2010-02-02
Bash, old habits die hard.

---

### Post by semi_fiction on 2010-02-02
Bash ftw

---

### Post by akshayy on 2010-02-02
bash by default, why do you ask ?

---

### Post by kaibob on 2010-02-02
When working in a terminal window, I use bash because it's the default. I use dash in most of my shell scripts because it's typically faster. I use bash in shell scripts only when I use an array or some other feature not supported by dash.

---

### Post by Diametric on 2010-02-02
I was curious as to why others used different shells.  I guess most use bash out of "it's there" but I noticed on post where someone used zsh.  Anyone use the cshell?

---

### Post by dcsoldschool53 on 2010-02-02
**I use the default, bash**

---

### Post by oupamster on 2010-02-03
bash.

---

### Post by Bachstelze on 2010-02-03
zsh for interactive shells, (d)ash for shell scripts.

---

### Post by mikkie on 2010-02-03
Zsh. Looks prettier and has better auto-completion than bash. A bit faster too.

---

### Post by Psumi on 2010-02-03
bash, because I don't know anything else, and it's the default.

---

### Post by RiceMonster on 2010-02-03
Zsh, but I write scrips with bash. Once you configure tab completion in Zsh, you'll see how nice it is.

---

### Post by Grenage on 2010-02-03
Bash; it's the default and I'm not advanced enough to look into others.

---

### Post by louieb on 2010-02-03
zsh -because someone suggested I check it out - now I'm hooked.

---

### Post by scouser73 on 2010-02-03
Bash

---

### Post by Tibuda on 2010-02-03
I have used zsh, but now I'm back to bash. It works for me.

---

### Post by CharlesA on 2010-02-03
Bash since I am too lazy to try other shells.

---

### Post by Simon17 on 2010-02-03
cmd

---

### Post by baizon on 2010-02-03
Bash :)

---

### Post by ssam on 2010-02-03
i have seen several posts/articles, saying that zsh has some great feature foo. but in every case bash seems to have the feature too.

has bash caught up with zsh? are there really things zsh does better?

---

### Post by ratcheer on 2010-02-03
I am using bash on Ubuntu because it is the default, but I have worked on numerous UNIX systems for many years and have almost always used Korn shell (ksh), in the past. I really don't see that much difference in the two.

If I felt a burning need to learn a newer shell, I think it would be zsh.

Tim

---

### Post by RiceMonster on 2010-02-03
> **ssam said:**
> has bash caught up with zsh?

No.
> are there really things zsh does better?

Yes, the tab completion is extremely powerful. I have case insensitive menu completion that will even complete man pages and user names. You can have it complete pids, and pretty much anything.

---

### Post by Barrucadu on 2010-02-03
Zsh, because it's wonderful.

---

### Post by blur xc on 2010-02-03
> **Barrucadu said:**
> Zsh, because it's wonderful.

If zsh is wonderful, why isn't it the default?  

BM

---

### Post by Icehuck on 2010-02-03
> **blur xc said:**
> If zsh is wonderful, why isn't it the default?  

BM

Probably because it's not GNU and uses an EVIL mit-like license.

---

### Post by Tibuda on 2010-02-03
> **blur xc said:**
> If zsh is wonderful, why isn't it the default?  

BM

bash works better out-of-the-box, while zsh is much better than bash after some tweaking. I think that's why it is not the default.

---

### Post by Hetor on 2010-02-03
Self-compilled bash4 on 9.04.

---

### Post by Simian Man on 2010-02-03
Zsh seriously kicks ***.  If you like the tab completion in bash, you will be blown away by zsh.

---

### Post by Barrucadu on 2010-02-03
> **blur xc said:**
> If zsh is wonderful, why isn't it the default?  

BM

Because bash is the traditional default, if it were *not* the default, CLI power-users would be confuzzled until they figure out the shell was &#8216;wrong&#8217;.

---

### Post by blur xc on 2010-02-03
> **Barrucadu said:**
> Because bash is the traditional default, if it were *not* the default, CLI power-users would be confuzzled until they figure out the shell was ‘wrong’.

now you guys got me all wondering about zsh.  I installed it, but there's no .zshrc file.  I googled it, and found a few tricked out .zshrc's...might be worth learnign.

Are all the same cli commands the same?  what about scripting?  I'm far from being a bash guru, but I saw a lot of {{ and }} in those rc files...  Does zsh use a different syntax?  I suppose I could just google that as well...

How do you make your gnome terminal pull up one shell or another?

BM

---

### Post by Tibuda on 2010-02-03
> **blur xc said:**
> now you guys got me all wondering about zsh.  I installed it, but there's no .zshrc file.  I googled it, and found a few tricked out .zshrc's...might be worth learnign.

Are all the same cli commands the same?  what about scripting?  I'm far from being a bash guru, but I saw a lot of {{ and }} in those rc files...  Does zsh use a different syntax?  I suppose I could just google that as well...
The syntax is very similar. If the cli commands are not embeded in the shell but binary executables (like aptitude), yes they are exactly the same. For scripting, you specify what shell to interpret the script changing the "#!" line.

> How do you make your gnome terminal pull up one shell or another?
if you are on bash, type "zsh", and it will open a zsh shell. type "exit" and you'll return to the bash shell. to change the default shell to zsh, run "chsh -s /bin/zsh".

---

### Post by blur xc on 2010-02-03
> **danielrmt said:**
> The syntax is very similar. If the cli commands are not embeded in the shell but binary executables (like aptitude), yes they are exactly the same. For scripting, you specify what shell to interpret the script changing the "#!" line.


if you are on bash, type "zsh", and it will open a zsh shell. type "exit" and you'll return to the bash shell. to change the default shell to zsh, run "chsh -s /bin/zsh".

yeah- wow, thanks for the info.  I dl'd this [.zshrc]("http://stuff.mit.edu/%7Ejdong/misc/zshrc") and read this [page]("http://http://friedcpu.wordpress.com/2007/07/24/zsh-the-last-shell-youll-ever-need/").  I'm quite impressed...

The tab completion by itself is amazing.  I did a sudo aptitude install fire<tab> and BAM!  A list of all packages in the repos that start w/ fire...  amazing.

BM

---

### Post by ssam on 2010-02-03
> **ssam said:**
> i have seen several posts/articles, saying that zsh has some great feature foo. but in every case bash seems to have the feature too.

has bash caught up with zsh? are there really things zsh does better?

> **RiceMonster said:**
> No.

Yes, the tab completion is extremely powerful. I have case insensitive menu completion that will even complete man pages and user names. You can have it complete pids, and pretty much anything.

bash can do case insensitive completion
[http://www.cyberciti.biz/faq/bash-shell-setup-filename-tab-completion-case-insensitive/](http://www.cyberciti.biz/faq/bash-shell-setup-filename-tab-completion-case-insensitive/)

bash (as configured in ubuntu) will tab complete many things
*man pages
*usernames (in chown, su)
*package names in apt-get
*pids in kill
*processnames in killall
*common sub commands (eg sudo apt-get in[tab] gives install)
etc

---

### Post by Bachstelze on 2010-02-03
> **Barrucadu said:**
> Because bash is the traditional default, if it were *not* the default, CLI power-users would be confuzzled until they figure out the shell was ‘wrong’.

Someone who is confused just by seeing another shell does not qualify as a "CLI power-user" to me. Also lol @ "traditional default". Traditional in GNU-based systems, maybe, but you do know UNIX existed long before that, right?

---

### Post by Barrucadu on 2010-02-03
> **Bachstelze said:**
> lol @ "traditional default". Traditional in GNU-based systems, maybe, but you do know UNIX existed long before that, right?

I'd say being the default shell in (more or less) every Linux distro for 20 years (ish) makes Bash the &#8216;traditional&#8217; Linux shell :p

---

### Post by Bachstelze on 2010-02-03
> **Barrucadu said:**
> I'd say being the default shell in (more or less) every Linux distro for 20 years (ish) makes Bash the ‘traditional’ Linux shell :p

That's exactly what I said, but not what you said in your previous post.

---

### Post by FuturePilot on 2010-02-03
Zsh > *

---

### Post by Barrucadu on 2010-02-03
> **Bachstelze said:**
> That's exactly what I said, but not what you said in your previous post.

I thought that, being on a Linux forum, it was fairly obvious that's what I was referring to, not previous flavours of UNIX.

---

### Post by Simian Man on 2010-02-03
> **ssam said:**
> i have seen several posts/articles, saying that zsh has some great feature foo. but in every case bash seems to have the feature too.

has bash caught up with zsh? are there really things zsh does better?

I've heard before that bash supports tab completion like Zsh.  If you enable that, does bash then allow you to "tab through" the possibilities like zsh does?  Because that is one feature I can't live without now.  I hated typing 1 character at a time until bash would complete the whole thing.

Zsh also has "less" built in by typing "<"filename, and better support for regular expressions than bash does by default.

Maybe bash can be made to behave like zsh in all of these things, but even still I'd rather use the one that has the features first and works mostly the way I like by default than try to hack bash into being something nice.

---

### Post by FuturePilot on 2010-02-03
> **ssam said:**
> i have seen several posts/articles, saying that zsh has some great feature foo. but in every case bash seems to have the feature too.

has bash caught up with zsh? are there really things zsh does better?

In most cases Bash only has $FEATURE if you do some crazy hacking in your bashrc. Zsh does most of this stuff out of the box.

---

### Post by ratcheer on 2010-02-03
> **Barrucadu said:**
> Because bash is the traditional default, if it were *not* the default, CLI power-users would be confuzzled until they figure out the shell was ‘wrong’.

Yep. That used to happen all the time at my last job. Everybody in the shop wrote everything in ksh, except this one Taiwanese guy who insisted on writing all of his stuff in Bourne shell, the old sh. Anytime you had to work on his stuff, it was subtly different. It was always a pain.

Tim

---

### Post by kk0sse54 on 2010-02-03
ksh93

---

### Post by Grifulkin on 2010-02-03
I just switched to zsh based on this thread.

---

### Post by sudoer541 on 2010-02-04
I use turtle shell :p

---

### Post by RiceMonster on 2010-02-04
> **sudoer541 said:**
> i use turtle shell :p

[font="system"]............................................________
....................................,.-‘”...................``~.,
.............................,.-”...................................“-.,
.........................,/...............................................”:,
.....................,?......................................................\,
.................../...........................................................,}
................./......................................................,:`^`..}
.............../...................................................,:”........./
..............?.....__.........................................:`.........../
............./__.(.....“~-,_..............................,:`........../
.........../(_....”~,_........“~,_....................,:`........_/
..........{.._$;_......”=,_.......“-,_.......,.-~-,},.~”;/....}
...........((.....*~_.......”=-._......“;,,./`..../”............../
...,,,___.\`~,......“~.,....................`.....}............../
............(....`=-,,.......`........................(......;_,,-”
............/.`~,......`-...............................\....../\
.............\`~.*-,.....................................|,./.....\,__
,,_..........}.>-._\...................................|..............`=~-,
.....`=~-,_\_......`\,.................................\
...................`=~-,,.\,...............................\
................................`:,,...........................`\..............__
.....................................`=-,...................,%`>--==``
........................................_\..........._,-%.......`\
...................................,<`.._|_,-&``................`\[/font]

---

### Post by sudoer541 on 2010-02-04
> **RiceMonster said:**
> [FONT=system]............................................________
....................................,.-‘”...................``~.,
.............................,.-”...................................“-.,
.........................,/...............................................”:,
.....................,?......................................................\,
.................../...........................................................,}
................./......................................................,:`^`..}
.............../...................................................,:”........./
..............?.....__.........................................:`.........../
............./__.(.....“~-,_..............................,:`........../
.........../(_....”~,_........“~,_....................,:`........_/
..........{.._$;_......”=,_.......“-,_.......,.-~-,},.~”;/....}
...........((.....*~_.......”=-._......“;,,./`..../”............../
...,,,___.\`~,......“~.,....................`.....}............../
............(....`=-,,.......`........................(......;_,,-”
............/.`~,......`-...............................\....../\
.............\`~.*-,.....................................|,./.....\,__
,,_..........}.>-._\...................................|..............`=~-,
.....`=~-,_\_......`\,.................................\
...................`=~-,,.\,...............................\
................................`:,,...........................`\..............__
.....................................`=-,...................,%`>--==``
........................................_\..........._,-%.......`\
...................................,<`.._|_,-&``................`\[/FONT]




thats cool...you're cool!!! L0L!:p

---

### Post by Eisenwinter on 2010-02-04
> **blur xc said:**
> If zsh is wonderful, why isn't it the default?  

BM
According to your argument, Linux should be the "default" OS on computers.

Why isn't it?

---

### Post by Barriehie on 2010-02-04
BASH, I've still got about 2000+ commands to go...

---

### Post by Diametric on 2010-02-04
Can someone confirm if the "tab auto-complete" feature is available in bash, please?

---

### Post by NoaHall on 2010-02-04
> **Diametric said:**
> Can someone confirm if the "tab auto-complete" feature is available in bash, please?

Yes. But not to the extent of zsh.

---

### Post by oldos2er on 2010-02-04
> **Diametric said:**
> Can someone confirm if the "tab auto-complete" feature is available in bash, please?

Yes, of course. It's very configurable too, see [http://www.hypexr.org/bash_tutorial.php#completion](http://www.hypexr.org/bash_tutorial.php#completion)

I like zsh also.

---

### Post by RATM_Owns on 2010-02-04
I use zsh.

---

### Post by chris200x9 on 2010-02-04
I use bash, I never thought of moving it does what I need.

---

### Post by Mr. Picklesworth on 2010-02-05
> **Diametric said:**
> I'm just curious what shell you folks use and why?  I use bash because it's the default shell and from the book I'm reading on it bash appears to be the most flexible. 
 
Anyone else?

Zsh if I'm in a traditional terminal.

Hotwire if I feel like indulging myself with something awesome. It's kind of a GUI-oriented reinvention of the shell, with some similarities to Microsoft's Powershell (except significantly more awesome). Being totally modern and really abstract, it doesn't block when a program is running (you can still input more commands), and you can flip back to previous commands to see their results. Neat for testing software!

---

### Post by cariboo on 2010-02-05
Gnome-shell, :) other wise, bash.

---

