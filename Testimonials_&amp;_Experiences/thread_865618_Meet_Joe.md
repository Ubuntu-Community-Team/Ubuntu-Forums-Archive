---
title: "Meet Joe"
date: 2008-07-20
forum: Testimonials &amp; Experiences
---

### Post by fd9_ on 2008-07-20
Joe is an aspiring programmer who really likes open source software. Mostly because it's free. But also because he's broke...and Joe wished that he was free too. Free like a bird.

On one fine day, Joe decided it would be cool to try out Ubuntu, since all of his friends are using it, and  he really couldn't afford Windows Vista or Visual Studio. Joe really likes Ubuntu right off the bat. The installation was super simple and the user interface was minimal and easy to use. It even recognized all of Joe's hardware so he didn't have to go searching for drivers. Awesome. Best of all, it was very responsive considering Joe hasn't updated his computer for 12 years. He's saving up the money to buy a new one though (with a better graphics card, of course).

Joe decided he needed an IDE for his all of his coding needs, since he wasn't comfortable with the command line and he was used to using VS where he wor &#8211; scratch that, Joe doesn't have a job. He's broke.

So anyway, Joe heard of this really slick IDE called codeblocks, so he decided to give it a try. It seemed to be a favorite among the community at ubuntuforums.org. Unfortunately for Joe, this particular program is not listed in the official repositories, so the only other way he knew to download software was to go to the official website (which he is used to anyway, since he recently converted from Windows). Luckily for Joe, there's a Ubuntu version sitting out there on the official website. As Joe anxiously waits for the download to finish, what he doesn't realize is that it's actually a tar.gz which contains about a half a dozen individual .deb files. Joe doesn't understand why he has to install half a dozen individual packages, since on Windows there was just one. "Hey, it's not that hard", Joe thinks, "I'll just go through and install each one." Coming from Windows, Joe is not comfortable yet with the command line and so he double clicks on each .deb file to install it.

Oops. After installing the third .deb file in a row, an error comes up telling him that some other library has to be installed first.

Joe is frustrated at this point, but he hasn't given up yet (he's a very determined user). After thinking about the error for a little bit he suddenly realizes that other packages need to be installed first. So Joe continues as he tries to figure out the proper order of package installations. 

Finally, Joe was able to crack the code and finished installing each package. Joe thought it was like a puzzle - but that's OK, since Joe likes puzzle games.
Joe boots up codeblocks. Nothing happens. He tries again. Nothing. No error, no warning message, nothing.

Joe has given up at this point. He doesn't understand what he is doing wrong, so he visits ubuntuforums.org (he's heard good things about the community) so that he can ask his question on the forums. Unfortunately, Joe forgot to use the "Search" feature of the forums, since this question has been asked several times already.

[http://ubuntuforums.org/showthread.php?p=5284955](http://ubuntuforums.org/showthread.php?p=5284955)

After reading a bit more and clicking through some links to other posts, he finds this guide that someone was nice enough to write:

[http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html](http://www.futuredesktop.org/codeblocks_on_ubuntu_8.04.html)

Boy, this sure is Joe's lucky day. Not only does he find instructions online specifically for installing codeblocks, but this guide is actually up to date for the current version of Ubuntu! Phew, that went smoothly.

Now my question to you guys:

Why doesn't the deb file do all of this automatically? I mean figure out which libraries need to be installed, etc?

My point is that any end-user, including people that have just installed Ubuntu, shouldn't even need to do a single google search to find out how to install a program, ANY program. Period.

Another problem is this: If you do a search on google for &#8220;how to install codeblocks on ubuntu&#8221;, guess what you get? A whole wide range of  random blogs and posts of different instructions for every different version of Ubuntu....it's just sad, because there are a lot of Joe's out there who are going to do exactly that.

---

### Post by L815 on 2008-07-20
I'm not really sure, and have wondered the same thing.

But, I have a few guesses:
1- It's an Open Source world, so many people include dependencies separate for individual tweaking.
2- It's much faster going through terminal and typing "sudo dpkg -i *.deb" rather than clicking through "next -> next -> finish" etc..
3- Maybe there are versions which people already have installed and only want to install certain features. This way he/she can choose specifically what to update.

I wonder if any of those are correct :confused:

---

### Post by fd9_ on 2008-07-21
> **L815 said:**
> I'm not really sure, and have wondered the same thing.

But, I have a few guesses:
1- It's an Open Source world, so many people include dependencies separate for individual tweaking.
2- It's much faster going through terminal and typing "sudo dpkg -i *.deb" rather than clicking through "next -> next -> finish" etc..
3- Maybe there are versions which people already have installed and only want to install certain features. This way he/she can choose specifically what to update.

I wonder if any of those are correct :confused:

You're forgetting that all three of those things can be done automatically. For example, when I open up the .deb, it should ask "hey, this program needs X, Y, and Z to run. But it looks like you already have Y and Z, so were just going to install X for you - yes or no?".

---

### Post by L815 on 2008-07-21
There's also a method to download dependencies that are missing without manually getting them.

When using terminal, if some dependencies are missing and causing the install to not finish, you can just run "sudo apt-get -f install".

But, for now there is no real GUI to do that to my knowledge. Ubuntu is striving more and more, and I'm sure eventually such a feature will be there.

But I must admit, coming from Windows and never touching cmd, I have begun to like using terminal somehow. It's fast, and efficient!

It's just strange for people new with Linux.
IMO, if you are willing to give Linux a try, then mentally each should be prepared not to do things "The Windows Way", rather the "GNU/Linux" way.

---

### Post by Canis familiaris on 2008-07-21
Actually Codeblocks is still under development phase and is not yet considered very stable (though I find it very stable), that is why I think it is not in the repos.

---

### Post by L815 on 2008-07-21
UPDATE: 
I just downloaded the .debs from the site and ran dpkg -i *.deb, and it ran just fine with one exception.

It would not build my code -_-

---

### Post by fd9_ on 2008-07-21
> **L815 said:**
> There's also a method to download dependencies that are missing without manually getting them.

When using terminal, if some dependencies are missing and causing the install to not finish, you can just run "sudo apt-get -f install".

But, for now there is no real GUI to do that to my knowledge. Ubuntu is striving more and more, and I'm sure eventually such a feature will be there.

But I must admit, coming from Windows and never touching cmd, I have begun to like using terminal somehow. It's fast, and efficient!

It's just strange for people new with Linux.
IMO, if you are willing to give Linux a try, then mentally each should be prepared not to do things "The Windows Way", rather the "GNU/Linux" way.

You might as well call it "The Mac Way" or better yet "The any OS besides Linux Way", because that's what it is. 

Some people like using the terminal, because for them it's more efficient. For others it's just the opposite. The user should be able to choose for themselves which way they want to interface. But for the most basic things (like installing a program) a GUI interface should be sufficient enough. Even something so simple as moving a file requires me to stop whatever I'm doing, open up a terminal, and type "sudo" so I can get root access. Is it really asking that much to provide a GUI prompting for the password?

I don't know, for an OS that's all about "choice", it sure seems like you're forcing the average Joe to use the command line an awful lot. Which in the end only makes it harder for the majority of newcomers.

What the Ubuntu developers need to realize is that they need to get the basics right. Installing software and moving files should not need the command line. I should be able to install programs without thinking. You need to strip away anything that is preventing the end-user from performing the most simplest of tasks. Once this is done, you can start competing with Windows IMO.

---

### Post by ShodanjoDM on 2008-07-21
> **fd9_ said:**
> For example, when I open up the .deb, it should ask "hey, this program needs X, Y, and Z to run. But it looks like you already have Y and Z, so were just going to install X for you - yes or no?".

gdebi

It comes both as a GUI and CLI tools. Preinstalled in Ubuntu.

---

### Post by armandh on 2008-07-21
for all the reasons you noted I found medibuntu the easiest [about 6 steps] cut and paste to the terminal CL to get DVDs working. this does not mean it will be the easiest @ 2010.04 leaping lemur. what I do know is that those searched for in the Ubuntu administration for down load have been easy, and light-scribe [HP I think] was easy too.

---

### Post by fd9_ on 2008-07-21
> **ShodanjoDM said:**
> gdebi

It comes both as a GUI and CLI tools. Preinstalled in Ubuntu.

Was already using it before I posted.

---

### Post by steveneddy on 2008-07-21
> **L815 said:**
> I'm not really sure, and have wondered the same thing.

But, I have a few guesses:
1- It's an Open Source world, so many people include dependencies separate for individual tweaking.
2- It's much faster going through terminal and typing "sudo dpkg -i *.deb" rather than clicking through "next -> next -> finish" etc..
3- Maybe there are versions which people already have installed and only want to install certain features. This way he/she can choose specifically what to update.

I wonder if any of those are correct :confused:

These are kinda the way I see it also.

---

### Post by 3rdalbum on 2008-07-22
That program is the exception to the rule. In fact, I'd like to personally give the packager of Codeblocks a virtual swift kick for making you jump through hoops :-)

Installing all packages simultaneously would have done the trick, but that's only accomplishable through the command-line. (I think?)

Gdebi (the GUI for installing Debian packages) does resolve dependencies automatically when the dependencies are in available software repositories.

Joes all around the world can complain about dependencies on Linux, but I'd rather have my disk space and system-wide bug-fixes and security patches. It's much better than the static-linking wasteage that is rampant with Windows programs.

---

