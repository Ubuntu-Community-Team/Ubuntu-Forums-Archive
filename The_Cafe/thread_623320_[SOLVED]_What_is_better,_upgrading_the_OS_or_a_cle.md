---
title: "[SOLVED] What is better, upgrading the OS or a clean install?"
date: 2007-11-25
forum: The Cafe
---

### Post by Bruce M. on 2007-11-25
I'm new to Linux, just under 5 months now. I started with 6.04 LTS (it's a long story) in July of this year, I read a lot and within a week I spent 14 hours upgrading to 6.01 and another night upgrading to 7.04.  I had nothing installed except the "clean install" programs at the time.  Since then I have added programs, done "some" tweaking, and saved a lot of HowTo's, Created a ZIM help file for terminal commands I have learned, linking in man pages, and examples from the forums and questions.

I'm running Feisty i386 Desktop (32bit), on a desktop, ***not a laptop***. It's an old PIII (800Mhz - 512MB RAM) on an Intel D815EEA motherboard, sound and video cards are built in. Works great right "out of the box" so to speak.

I get my programs from:
Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)/main
Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)/restricted
ar.archive.ubuntu.com/main
ar.archive.ubuntu.com/multiverse
ar.archive.ubuntu.com/restricted
ar.archive.ubuntu.com/universe
archive.ubuntu.com/multiverse
archive.ubuntu.com/universe
packages.medibuntu.org/main
packages.medibuntu.org/universe
security.ubuntu.com/main
security.ubuntu.com/multiverse
security.ubuntu.com/universe

Until I learn more about Linux I restrict myself to Ubuntu's repos.

For Gutsy I plan on downloading the "alternate" ISO CD or DVD but I don't know what the differences are.
Then I plan on ordering the "Live CD/DVD" to be delivered.

Do the DVDs comes with added features?

In System>Update Manager I can do a "live update" to 7.10. It will take me 12-14 hours to do that, I don't have a problem with the time.

If I do an "update" my installed programs remain and having done just that from 6.04, 6.10 and 7.04, I know it works.

I've been reading [http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007), where it seems that doing a "clean install" is the best way to go.

What happens to my installed programs with a clean install?

I am using System>Home User Backup weekly, keeping the three latest backups on a sparate HD.

Are these "backups" compatable with Gutsy?

If the "backups" are compatable with Gutsy I have three options.

...a. Use Update Manager and update to Gutsy
...b. Get the ISO, create the CD/DVD and do a "Clean Install"
...c. Upgrade via CD/DVD as mentioned here: [https://answers.launchpad.net/ubuntu/+question/5788](https://answers.launchpad.net/ubuntu/+question/5788)

Which, in your opinion is the best option?

-------------------------------------
I'll repeat just the questions:

1. Do the DVDs comes with added features?
2. What happens to my installed programs with a clean install? (educated guess: GONE!)
3. Are these "backups" compatable with Gutsy?
4. Which, in your opinion is the best option?

...a. Use Update Manager and update to Gutsy
...b. Get the ISO, create the CD/DVD and do a "Clean Install"
...c. Upgrade via CD/DVD as mentioned here: [https://answers.launchpad.net/ubuntu/+question/5788](https://answers.launchpad.net/ubuntu/+question/5788)

Thanks for your time.
Bruce Milmine

---

### Post by -grubby on 2007-11-25
with a clean install, you can guarantee none of your upgraded-ness will screw anything up

---

### Post by smartboyathome on 2007-11-25
You should just upgrade if you are running on Gutsy's repos.

---

### Post by p_quarles on 2007-11-25
If you do a clean install it will format your drive. If you have your home folder backed up to a separate drive, you'll be able to easily restore that. 

You can also "clone" your installation pretty easily by running this trick I found. These are copied from my notes, so I'll try to add some details:
```
sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_list
```
This creates a file called "package_list" which is simply a listing of all the names of packages you currently have installed. Save this file to another medium so you can get back to it after you've installed the system.

To use package_list to reinstall:
```
sudo apt-get update
cat package_list | xargs sudo apt-get install -y
```
This assumes that you have placed the package_list in your home directory, and have added any necessary third-party repos to /etc/apt/sources.list. 

The only complication here is that some files will be obsolete in the new version. This means that you'll have to spend a few minutes deleting obsolete package names from package_list. apt-get will tell you which ones can't be installed when you run it.

---

### Post by fuscia on 2007-11-25
i like clean installs. it's nice to have things unclutered.

---

### Post by rfruth on 2007-11-25
Like most I've done both, clean/fresh is best but it can be a pain :)

---

### Post by Bruce M. on 2007-11-25
> **nathangrubb said:**
> with a clean install, you can guarantee none of your upgraded-ness will screw anything up

> **fuscia said:**
> i like clean installs. it's nice to have things unclutered.

Clean install does't answer the question:
3. Are these "backups" compatable with Gutsy?
ie:  Are the backups made with Feisty's *Home User Backup* program compatable with Gutsy's *Home User Restore* Program.

> **smartboyathome said:**
> You should just upgrade if you are running on Gutsy's repos.

I'm running Feisty, so I can't be on Gutsy's repos.  Unless I'm missing something.

---

### Post by p_quarles on 2007-11-25
> **Bruce M. said:**
> Clean install does't answer the question:
3. Are these "backups" compatable with Gutsy?
ie:  Are the backups made with Feisty's *Home User Backup* program compatable with Gutsy's *Home User Restore* Program.
I doubt that many of us here use that program. Generally speaking, a backup program will store files in a common archive format (tar.gz, for instance), or will simply use a copying application like rsync. There shouldn't be any question of compatibility with any app like this, and if there is, I would recommend against using it.

Find out how Home User Backup works and that will answer the question.

---

### Post by Bruce M. on 2007-11-25
> **p_quarles said:**
> If you do a clean install it will format your drive. If you have your home folder backed up to a separate drive, you'll be able to easily restore that.

So Gutsy's Home User Restore estore program is compatable with Feisty's backups then?

> **p_quarles said:**
> You can also "clone" your installation pretty easily by running this trick I found. These are copied from my notes, so I'll try to add some details:
```
sudo dpkg --get-selections | grep '[[:space:]]install$' | awk '{print $1}' > package_list
```
This creates a file called "package_list" which is simply a listing of all the names of packages you currently have installed. Save this file to another medium so you can get back to it after you've installed the system.

Checking man pages:

       dpkg --get-selections [package-name-pattern...]
              Get list of package selections, and write it to stdout.  Without
              a pattern, packages marked with state purge will not be shown.

 | grep

       grep  searches the named input FILEs (or standard input if no files are
       named, or the file name - is given) for lines containing a match to the
       given PATTERN.  By default, grep prints the matching lines.

What do these do?

 '[[:space:]]install$'

 | awk

 '{print $1}' > package_list


> **p_quarles said:**
> To use package_list to reinstall:
```
sudo apt-get update
cat package_list | xargs sudo apt-get install -y
```
This assumes that you have placed the package_list in your home directory, and have added any necessary third-party repos to /etc/apt/sources.list.

I'll check the man pages later for these too.

At first look it looks very interesting.
Problem is I am not saving the packages after installing them.  I opted to save space.   :(

> **p_quarles said:**
> The only complication here is that some files will be obsolete in the new version. This means that you'll have to spend a few minutes deleting obsolete package names from package_list. apt-get will tell you which ones can't be installed when you run it.

I was thinking the same thing from my "backups".  If I restore them, I'll overwrite newer versions of programs.   :(

---

### Post by Bruce M. on 2007-11-25
> **p_quarles said:**
> I doubt that many of us here use that program. Generally speaking, a backup program will store files in a common archive format (tar.gz, for instance), or will simply use a copying application like rsync. There shouldn't be any question of compatibility with any app like this, and if there is, I would recommend against using it.

One of the pitfalls of being a newbie I guess.   :(
Any recommendation for a better program in Ubuntu's repos?

> **p_quarles said:**
> Find out how Home User Backup works and that will answer the question.

I'll definitely look into that.  And here I thought I was being safe.

---

### Post by p_quarles on 2007-11-25
> **Bruce M. said:**
> What do these do?

 '[[:space:]]install$'

 | awk

 '{print $1}' > package_list

The first one (following grep) is a regular expression which calls out only the packages that you actually have installed (as opposed to everything in your cache).

The "|" symbol is a "pipe," meaning that it transfers the output of the previous command into the next command.

"awk" is a programming language, and this command invokes the awk shell which is needed for the following command

'{print $1}' is an awk command that prints the variables created by the grep command.

> transfers the output of the previous command into text, and saves that text in the file name that follows.

package_list is that file name, and that can be changed to whatever you want. 

As for overwriting files: you said you backed up your home directory, correct? Linux doesn't keep any program files there, just configuration files. In *some *cases you will find that your old configurations will need minor tweaking with new program versions. Thunderbird was the only one I came across like that when I upgraded from Feisty > Gutsy.

EDIT: Oh, right -- the other commands.

cat = "concatenate" or print a text file
| = pipe
xargs = use the text output to build a command

apt-get you probably know.

---

### Post by Bruce M. on 2007-11-25
> **p_quarles said:**
> The first one (following grep) is a regular expression which calls out only the packages that you actually have installed (as opposed to everything in your cache).

The "|" symbol is a "pipe," meaning that it transfers the output of the previous command into the next command.

"awk" is a programming language, and this command invokes the awk shell which is needed for the following command

'{print $1}' is an awk command that prints the variables created by the grep command.

> transfers the output of the previous command into text, and saves that text in the file name that follows.

package_list is that file name, and that can be changed to whatever you want. 

As for overwriting files: you said you backed up your home directory, correct? Linux doesn't keep any program files there, just configuration files. In *some *cases you will find that your old configurations will need minor tweaking with new program versions. Thunderbird was the only one I came across like that when I upgraded from Feisty > Gutsy.

EDIT: Oh, right -- the other commands.

cat = "concatenate" or print a text file
| = pipe
xargs = use the text output to build a command

apt-get you probably know.

Thank you for this explanation.

> As for overwriting files: you said you backed up your home directory, correct?

Yea, but I see where my choice of programs may not have been the wisest.  Live and learn.  I'm going to look at "Mondo" now. Downloaded it, just can't find it.  Checked terminal and it's not there.  :(

---

### Post by p_quarles on 2007-11-25
> **Bruce M. said:**
> Yea, but I see where my choice of programs may not have been the wisest.  Live and learn.  I'm going to look at "Mondo" now. Downloaded it, just can't find it.  Checked terminal and it's not there.  :(
I think you may have misunderstood something I said earlier. When I said that probably not many people here use Home User Backup, that wasn't to imply it's a bad program, just that I don't know anything about it. I use rsync via the command line for my backups. 

Anyway, I just looked into it, and Home User Backup is a front-end for the "dar" application. I can think of no reason why it would fail to restore your files simply because you upgraded your OS. That would be a massive design flaw.

If you do have any concerns, though, you can always check out [flyback]("http://code.google.com/p/flyback/"). It's a python-based front-end for rsync, and has a decent UI. rsync is nice because it can store your backups on a number of file systems without changing anything. It's literally just a mirror of the directory you're backing up. (the Ubuntu CD and repository mirrors use this same application to keep up to date with the main servers).

---

### Post by Bruce M. on 2007-11-26
> **p_quarles said:**
> I think you may have misunderstood something I said earlier. When I said that probably not many people here use Home User Backup, that wasn't to imply it's a bad program, just that I don't know anything about it. I use rsync via the command line for my backups.

Thank you for your comment.  I feel a bit better, I also downloaded Mondo, someone mentioned it a while back.  But, simply put, I cannot find it on my system anywhere.  :(

tried terminal: mondo ... nada!

> **p_quarles said:**
> Anyway, I just looked into it, and Home User Backup is a front-end for the "dar" application. I can think of no reason why it would fail to restore your files simply because you upgraded your OS. That would be a massive design flaw.

Yea, I guess it would be,  I'll keep truckin' away with it for the time being.  It's easy to use and when I get more experience maybe I'll change if something better presents itself.

> **p_quarles said:**
> If you do have any concerns, though, you can always check out [flyback]("http://code.google.com/p/flyback/"). It's a python-based front-end for rsync, and has a decent UI. rsync is nice because it can store your backups on a number of file systems without changing anything. It's literally just a mirror of the directory you're backing up. (the Ubuntu CD and repository mirrors use this same application to keep up to date with the main servers).

Or, maybe I'll look at that now.  Not in Ubuntu's repos though   :(
But I'll save it to look at later.  (see above)

Thanks again

---

### Post by omns on 2007-11-26
I prefer clean with Ubuntu but it depends on how much tweaking and customising you do to a normal install. An upgrade can be time consuming and a pain in the butt in this case. I prefer progressive release distros for this reason. Then again they are not for everyone so I guess I'll come back to recommending a clean install :)

---

### Post by p_quarles on 2007-11-26
> **Bruce M. said:**
> Or, maybe I'll look at that now.  Not in Ubuntu's repos though   :(
But I'll save it to look at later.  (see above) 
Just FYI, Flyback is a Python script, so it doesn't need to be compiled -- you can run the source code directly. Once you installed the dependencies, you would run:
```
flyback.py
```

---

### Post by Andrew123123 on 2007-11-26
Clean install is better. I think some programs might have new configuration files that are not 100% compatible with the old ones, sometimes.

---

### Post by Bruce M. on 2007-11-27
> **p_quarles said:**
> Just FYI, Flyback is a Python script, so it doesn't need to be compiled -- you can run the source code directly. Once you installed the dependencies, you would run:
```
flyback.py
```

Ok, thanks.  I will definately look at it.  Thanks

---

### Post by p_quarles on 2007-11-27
Oops, just noticed a mistake. That command should be:
```
python flyback.py
```
It's on the site, as well, but I hate to leave an error like that standing.

---

### Post by infoseeker on 2007-11-27
I prefer clean installs, but as a habit I backup up my '/var/cache/apt/archives' directory every now and then.  I have only ever used this backup data once when a drive failed.  Saves me from having to download all the updates again (this is South Africa BTW :)).  I then copy this data back into the '/var/cache/apt/archives/partial' directory after the install and do the updates (a lot quicker).  I just need a quick and easy way to delete obsolete files from the backup drive :).

---

### Post by Ekril on 2007-11-27
I am not a guru but i wonder why don't you try to update just after a last backup. If it breaks something you will allways have a chance for a clean install . (Am i wrong?) 

I see that you are trying to learn Just as me  ( : ) ) but i prefer to learn by installing > breaking > reinstalling > rebreaking> reins... > rebre.. >.. . 

I know this is not a good habbit but i have so much spare time . 

(and sorry for my bad English..)

---

### Post by Bruce M. on 2007-11-28
> **p_quarles said:**
> Oops, just noticed a mistake. That command should be:
```
python flyback.py
```
It's on the site, as well, but I hate to leave an error like that standing.

Got it and edited ZIM.   Thanks.

---

### Post by Bruce M. on 2007-11-28
> **infoseeker said:**
> I prefer clean installs, but as a habit I backup up my '/var/cache/apt/archives' directory every now and then.  I have only ever used this backup data once when a drive failed.  Saves me from having to download all the updates again (this is South Africa BTW :)).  I then copy this data back into the '/var/cache/apt/archives/partial' directory after the install and do the updates (a lot quicker).  I just need a quick and easy way to delete obsolete files from the backup drive :).


That's interesting too.  Except my "/var/cache/apt/archives/partial is empty" because I have the "do not keep" option active, to save space.   :confused:

---

### Post by K.Mandla on 2007-11-28
> **Bruce M. said:**
> Which, in your opinion is the best option?
Clean install. The few times I've upgraded, I later wished I hadn't. Nothing went spectacularly wrong, but clean installs are much ... cleaner.

---

### Post by Bruce M. on 2007-11-28
> **Ekril said:**
> I am not a guru but i wonder why don't you try to update just after a last backup. If it breaks something you will allways have a chance for a clean install . (Am i wrong?)

I was planning on that until I read the post quoted in my original message.  That got me to thinking.  So I put it here to see what advice I'd get.  I'm learning a lot here.
and I don't think you are wrong.  I can always do a clean install and hope my home directory backup restores properly.  :)

> **Ekril said:**
> I see that you are trying to learn Just as me  ( : ) ) but i prefer to learn by installing > breaking > reinstalling > rebreaking> reins... > rebre.. >.. .

I've done that in the past but I'm not so free to do it now.  My wife wants her mail and files too.  I want to reduce the risk of loss.  I still backup stuff to CD's just to be safe.   :)

> **Ekril said:**
> I know this is not a good habbit but i have so much spare time .

Nothing wrong with what you are doing. It's like you said:No, y
> I prefer to learn by ....
We all learn by different means.

> **Ekril said:**
> (and sorry for my bad English..)

I hate to tell you but ... your English is not bad.
No!  Actually I'm glad to tell you that!

I just looked up hello in Turkish and got:

ünlem
1. Merhaba.
2. Alo.

so I don't even know how to say hello to you in your language.
Your English is just fine, my Turkish is bad!

Here is a hint though, when typing in the "message" box, right-click your mouse and you'll see:  Spell check this field.  Do this "before" you start typing and it will underline the words as you type if they are wrong.  It won't help with grammer, but that isn't your problem.  Trust me.

You will see that you made two spelling errors, underlined in red.  I wouldn't call "rebreaking" a spelling error because of how you meant it, although the spell checker does.  :)

1.  you will allways have = you will always have
2.  not a good habbit but = not a good habit but

In another thread I said:  You do nive work  (nive for nice), a typo, we do it all the time.  So relax and go with the flow.   :)

Now with that said I'd like to say two more things.

1.  Your English is better than "some" English native speakers.
2.  I hope you never use the phrase "and sorry for my bad English" again, you really don't need to.

Have a great day,
and thanks for your input
Bruce

---

### Post by Ekril on 2007-11-29
Thanks for your kind message. 
also i wonder what you decided.. a clean install or an update.

---

### Post by Bruce M. on 2007-11-29
> **Ekril said:**
> Thanks for your kind message. 
also i wonder what you decided.. a clean install or an update.

You're welcome.

I haven't decided yet.  Still looking at things, checking out a couple of backup programs.

Since I don't have a single program that isn't "Ubuntu" the **update** looks like a reasonable option.  If I decide to do that and it messes up, I'll have my backup, and the ability to do a clean install.  A lot of work, but it's only time.  I have to do something until the day I die, so why not this.

When I first tried Gutsy (update) it was in late beta stage, and did not work.  I was forced to do a clean install of Feisty again.  It was a bit of work getting everything back to the way I had things.  But since I had all my "critical" files on a CD, it was just getting personal stuff back in (email, images, documents).  At that point I told myself I was going to wait until January to get Gutsy.

Don't tell my wife, but I'm getting that "I want it now" feeling.  I'll probably fight that feeling off until late Dec.   :)

I think however I'm leaning towards:
   1. getting the "Live CD" and just booting with it to see if Gutsy has problems with my machine.
   2. then I'll download the "Alternate CD", this will give me both of the CDs.

At this point I have the option of, clean install, or "upgrade" from the CD, with the knowledge of whether or not Gutsy is compatible with my old P-III.  I have 512MB RAM so I'm OK in that respect, but by the time HH comes out I'll probably have to up that to a GIG.

The second last thing I do in Feisty will be to come here and post just how I'm going to do it, then I'll backup everything and run with it.

---

### Post by Tipo on 2007-11-29
I usually do a clean install.  I have often times had trouble with system files, like sound effects, etc when doing an upgrade.  System has worked flawlessly every time I've done a clean install.

---

### Post by Bruce M. on 2008-02-15
15 Feb 2008

Today was Install Gutsy Day.

Gutsy 7.10 now up and running after a some research, two of which are below:

[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=684783](http://ubuntuforums.org/showthread.php?t=684783)
[*][http://ubuntuforums.org/showthread.php?t=656530](http://ubuntuforums.org/showthread.php?t=656530)
[/LIST]

I chose the Alt CD and installed 7.10 over 7.04 keeping my /home (different partition) intact (had a backup though) and everything went fairly well.

The Alt CD checked out OK, so I put:

sda5 - / - reformat
sda7 - /home - kept data
sda6 - /swap

First attempt had a hiccup, it failed the "Select and install software", but gave me the chance to try agin starting at that point.  So I did.

Second attempt was successful.

186 security updates later and I was reinstalling some of my programs:

[LIST=1]
[*]Thunderbird - all mail available
[*]jPilot - data intact
[*]conky
[*]curl
[*]lm-sensors
[*]Thunar
[*]Inkscape, and my one and only game;
[*]Wesnoth
[/LIST]

I finally got Gutsy!

---

### Post by stevejesus on 2008-02-15
If you have a working internet connection then in the future you won't need to waste a CD.  You can use the update manager.

---

### Post by Bruce M. on 2008-02-15
> **stevejesus said:**
> If you have a working internet connection then in the future you won't need to waste a CD.  You can use the update manager.

Have always had a working internet connection, I was curious as to what was better "update" or re-install ... after researching the question along with results posted here - I chose to reinstall.

---

