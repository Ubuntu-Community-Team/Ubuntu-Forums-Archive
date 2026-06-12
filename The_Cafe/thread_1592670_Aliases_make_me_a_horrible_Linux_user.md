---
title: "Aliases make me a horrible Linux user"
date: 2010-10-10
forum: The Cafe
---

### Post by Legendary_Bibo on 2010-10-10
About a month ago I went through and wrote a bunch of Aliases in my bash file. I also wrote aliases for common commands so that they made sense to me (i.e. cd to goto, and several commands linked to shell scripts, etc.) Now when I go to help someone I have to open my bash file (through another alias to open in gedit). I don't know it makes me feel sloppy. I wish you could combine aliased commands sometimes, but that'll just make me worse. It makes me feel lazy.

---

### Post by Helkaluin on 2010-10-10
They are supposed to be a feature, and features are supposed to be used.

---

### Post by CharlesA on 2010-10-10
> **Helkaluin said:**
> They are supposed to be a feature, and features are supposed to be used.

+1. I love using aliases.

---

### Post by Legendary_Bibo on 2010-10-10
> **CharlesA said:**
> +1. I love using aliases.

I love them! but it's just that some of the older Linux users don't approve of it, but then again they don't even approve of the gui these days.

---

### Post by Lucradia on 2010-10-10
> **Legendary_Bibo said:**
> I love them! but it's just that some of the older Linux users don't approve of it, but then again they don't even approve of the gui these days.

I'm a new-er linux user (started with MEPIS or so)... and I love the GUI, but I don't know how to do aliases ^^ Nor do I think I need to use them.

---

### Post by Legendary_Bibo on 2010-10-11
> **Lucradia said:**
> I'm a new-er linux user (started with MEPIS or so)... and I love the GUI, but I don't know how to do aliases ^^ Nor do I think I need to use them.

Do you use the terminal often, or at all? I'm relatively new to Linux, but I actually like the terminal, (I actually tried learning DOS, but the commands are illogical, and pretty limited) and it can make doing several tasks much quicker, tired of long commands that you have to enter over and over? Put it as an alias in your bash file, it's easily customizable! I love it!

For instance I use Handbrake to rip DVDs, but for some reason using the GUI makes it slower to rip (also the menu confuses me). So how do I remember how to use the command line way of doing it? I don't! I learned it once, made an alias and I do it with one command. I know there's several profiles and stuff, then you have to direct to your disc drive, and something else...ugh. I don't ever have to change the options so I just made a command 'rip' and type in the DVD name. Bam! That's all there is to it.

I use it as my system monitor with top and htop, my temperature monitor, and because the software center, and synaptic can be slower to start up and I know the name of the program I want to install then I just install it through the terminal (which turned sudo apt-get install to just 'install'). You'll love the terminal once you have your aliases set up. Also because I make a lot of executable shell scripts, I get tired of typing in the command 'chmod u+x' just because of that dang plus sighn so my command is 'energize' why? I don't know! But I can just customize them any way I want! It's so awesome!!

---

### Post by toupeiro on 2010-10-11
aliases are a total lifesaver.  Very often, I have to use VPN or Citrix to connect into work.  I can't tell you how many times X11redirection gets lost between VPN concentrators or Citrix portals if you're publishing something like PuTTY..  Aliases save me a lot of environment setup to redirect X if I have to..

I also have aliases around the nmap command and other tools that are heavily switch oriented that save me lots of time.  Just the fact that they are aliases also helps me recall my syntax when I type: alias...

And older linux users shouldn't be complaining about using aliases, because aliases were around a whole lot longer than Linux has been around... :P  When they were incorporated into the csh and tcsh in the 70's and the 80's I am sure they weren't doing it because it was a bad practice...  By that logic, writing scripts will make you lazy too. :P

Shameless plug: tcsh is epic.

---

### Post by sarin_cv on 2010-10-11
> **Legendary_Bibo said:**
> 
For instance I use Handbrake to rip DVDs, but for some reason using the GUI makes it slower to rip (also the menu confuses me). So how do I remember how to use the command line way of doing it? I don't! I learned it once, made an alias and I do it with one command. I know there's several profiles and stuff, then you have to direct to your disc drive, and something else...ugh. I don't ever have to change the options so I just made a command 'rip' and type in the DVD name. Bam! That's all there is to it.


love that feature..... by the way can u plz post the above command mentioned? I have tried DVD rip for ripping dvd's but the ripped video has got many horizontal parallel lines in it....

---

### Post by aeiah on 2010-10-11
i never use aliases, because of the reason stated: when im on a different machine i end up typing complete rubbish.

im a sucker for using ```
history | grep keyword
``` though, and then doing ```
!123
``` to issue command number 123 from my history.

---

### Post by matthew.ball on 2010-10-11
This brings back bad memories.

I remember a while back, someone asked me how to make a complex command simple, and I showed him how to make a bash function call the command instead of telling him to use an alias. :(

Sorry little guy, if you're still out there.

---

### Post by t0p on 2010-10-11
I don't use aliases, even though I use the terminal a lot.  Typing in long commands can be a pain, but I find it disciplines my mind.  It focuses the mind on what each flag does.

---

### Post by nothingspecial on 2010-10-11
If I want punk I want punk now, not after a really long command
```

$ alias | grep punk
alias punk='mplayer -really-quiet http://65.60.32.242:8600 < /dev/null &'
```

When I type punk I get punk

And I know it should say -really-loud

---

### Post by Lucradia on 2010-10-11
> **Legendary_Bibo said:**
> Do you use the terminal often, or at all? I'm relatively new to Linux, but I actually like the terminal, (I actually tried learning DOS, but the commands are illogical, and pretty limited) and it can make doing several tasks much quicker, tired of long commands that you have to enter over and over? Put it as an alias in your bash file, it's easily customizable! I love it!

For instance I use Handbrake to rip DVDs, but for some reason using the GUI makes it slower to rip (also the menu confuses me). So how do I remember how to use the command line way of doing it? I don't! I learned it once, made an alias and I do it with one command. I know there's several profiles and stuff, then you have to direct to your disc drive, and something else...ugh. I don't ever have to change the options so I just made a command 'rip' and type in the DVD name. Bam! That's all there is to it.

I use it as my system monitor with top and htop, my temperature monitor, and because the software center, and synaptic can be slower to start up and I know the name of the program I want to install then I just install it through the terminal (which turned sudo apt-get install to just 'install'). You'll love the terminal once you have your aliases set up. Also because I make a lot of executable shell scripts, I get tired of typing in the command 'chmod u+x' just because of that dang plus sighn so my command is 'energize' why? I don't know! But I can just customize them any way I want! It's so awesome!!

I just use <commands>; <more_commands>; <even_more_commands> if I have to do more than one thing at once (since the semi-colon in bash allows you to do more than one command at once). If I use the pipe ( | ) then it's because I copy and paste terminal code from a site such as ubuntuforums ^^ so no, I don't use aliases, but I use the terminal semi-alot, not alot as some would like, as the GUI for most linux distributions is good enough to do so without terminal nowadays, even with Debian, etc. (after installing everything, obviously.)

---

### Post by kaldor on 2010-10-11
The only alias I use is "rm -i" for "rm". Whenever I *rm* a file, it'll prompt me just in case I mistyped.

---

### Post by koenn on 2010-10-11
> **Helkaluin said:**
> They are supposed to be a feature, and features are supposed to be used.


Nope, it's not because they're there that you have to use them. 
They're there in case you need them, in case they can make things easier.

But if they work against you, you better don't use them - as in the case where you often work on different machines where no or other aliases are set, and your dependency on your aliases undermines your skill.

One thing that will work, is maintaining  the same set of aliases across several machines, but that only works well if you have a sufficient level of control over all of them

---

### Post by PapaNerd on 2010-10-12
> **Legendary_Bibo said:**
> I love them! but it's just that some of the older Linux users don't approve of it, but then again they don't even approve of the gui these days.

I'm curious about your definition of "older" in this context.  Those to whom you refer must have been a strange offshoot of the mainstream *nix users.  The admins I know (with 20+ years of experience) use extensive aliases and scripts to make their jobs faster and more efficient.  Over the years, I've done several contract gigs where corporations have hired me to write custom scripts for their admins.  In larger scale operations, syncing scripts across many machines is quick and easy, and can be automated in a cron job.

---

### Post by limestone on 2010-10-12
what's wrong with cd? short for change directory...

---

### Post by CharlesA on 2010-10-12
> **pont.andersson said:**
> what's wrong with cd? short for change directory...

They are referring to user-created aliases. I didn't see anything mentioning cd specifically.

---

### Post by nothingspecial on 2010-10-12
.bashrc is a config file like any other that you edit to make an app behave how you want it to behave.

So does editing my .screenrc make me a bad screen user? 

another goodone btw

```
alias ran='mplayer -quiet -shuffle -playlist <(find ~/Music -type f) < /dev/null &'
```

That plays your Music library randomly.

I could type the whole thing out every time, or I could open up a music player, wait for it to load my library, click this, click that, boring boring clickety click.

Or I could just type ran

I think that makes me a good linux user.

---

### Post by koenn on 2010-10-12
> **CharlesA said:**
> They are referring to user-created aliases. I didn't see anything mentioning cd specifically.

someone said something about using 'goto' as an alias for 'cd'.
Can't seem to find it again, maybe it was edited out later.

---

### Post by CharlesA on 2010-10-12
> **koenn said:**
> someone said something about using 'goto' as an alias for 'cd'.
Can't seem to find it again, maybe it was edited out later.

You are right. It's in the OP.

---

### Post by koenn on 2010-10-12
> **CharlesA said:**
> You are right. 
happens a lot ...
:)

---

### Post by apmcd47 on 2010-10-12
> **kaldor said:**
> The only alias I use is "rm -i" for "rm". Whenever I *rm* a file, it'll prompt me just in case I mistyped.

So when I ask you to do something on my computer and you make a mistake and decide to delete a few files using 'rm fp*' how are you going to tell me you've just destroyed a long day's hard coding?

Make it "rmi" instead. When you type it on somebody else's session the worst you will get is "command not found"

Andrew

---

### Post by CharlesA on 2010-10-12
> **apmcd47 said:**
> So when I ask you to do something on my computer and you make a mistake and decide to delete a few files using 'rm fp*' how are you going to tell me you've just destroyed a long day's hard coding?

Make it "rmi" instead. When you type it on somebody else's session the worst you will get is "command not found"

Andrew

That's why I try to post the full command when helping people.

Also, it might be worth noting to check to see what a command might do before running it, just to be safe. :)

---

