---
title: "Multiple apts running at the same time...."
date: 2007-10-18
forum: Ubuntu Brainstorm
---

### Post by notna01 on 2007-10-18
Multiple apts running at the same time....
You should be able to make ubuntu run multiple apts at the same time, cause I am used to installing alto of programs at the same time... And it gets really annoying having to wait for the first program to download, then install, then start the next downloading....

---

### Post by Steveway on 2007-10-18
Running multiple instances of apt is not wise and can fsck up your system.
If you want to install several programs at once then do this:
sudo apt-get install programname1 programname2 programname3 ...

---

### Post by jlacroix on 2007-10-18
This could be done. The safest way to implement this is to lock packages, not apt. For example, say you need to install packageA, which requires packages B,C,D and E.

Apt could lock changes to programs A-E but allow changes to any other package.

---

### Post by Zdravko on 2007-10-18
Bad idea.

---

### Post by Lord Illidan on 2007-10-18
I agree that this is a bad idea. Ideally, you should install 1 application at a time. And, I don't see what the fuss is all about. All you have to do is type :

apt-get install programX programY programZ to download them and install them in a batch or else use Synaptic and select a load of programs.

---

### Post by Zdravko on 2007-10-18
[Lord Illidan]("http://ubuntuforums.org/member.php?u=27500") is right.

---

### Post by jlacroix on 2007-10-18
Bad idea or not, not being able to multitask software installation is EXTREMELY sad. Windows users have been able to do that since Windows 95.

---

### Post by elvis on 2007-10-18
> **jlacroix said:**
> Bad idea or not, not being able to multitask software installation is EXTREMELY sad. Windows users have been able to do that since Windows 95.

1) It is not sad.  It is the way APT works, which would be apparent if you read the documentation.

2) APT contains the functionality to install many programs at once.  This "problem" is not a limitation in APT, this is a limitation of the user's education if they can't figure out how to use APT properly

3) Linux is not Windows.  Comparing them is pointless.  You say "Windows users have been able to install multiple applications since Win95", and I say "Windows is 20 years old and still doesn't have a software installation and management system anywhere near as good as APT".

This idea is a bad idea.  The solution here is for the user to learn how to use APT properly, and not to change APT to exhibit more dangerous behaviour to compensate for users who can't read documentation properly.

---

### Post by bethaviv on 2007-10-18
> **jlacroix said:**
> Bad idea or not, not being able to multitask software installation is EXTREMELY sad. Windows users have been able to do that since Windows 95.

Actually there are times when Windows does NOT let you install 2 things at once. Trust me... after all the re-installs and installations of Windows I've done, it will say that there is already a set up running and to let the other one finish. This is true in every version of Windows... right up to Vista.

---

### Post by jlacroix on 2007-10-18
> **bethaviv said:**
> Actually there are times when Windows does NOT let you install 2 things at once. Trust me... after all the re-installs and installations of Windows I've done, it will say that there is already a set up running and to let the other one finish. This is true in every version of Windows... right up to Vista.
Yeah but it's not that often though.

Don't get me wrong, I love the debian system. I really do. I just think it could be improved upon.

One way of doing it would be to have an "install queue" for the users that click on multiple packages, and each one you click on would add to a list and then you click "begin" to install them.

---

### Post by VRWarper on 2007-10-18
What I would like to see is download and installation running in parallel. Download the packages with no additional dependencies first,  then unpack and install them. Of course, while they're unpacking and installing, keep downloading the other packages.

---

### Post by bethaviv on 2007-10-18
> **jlacroix said:**
> One way of doing it would be to have an "install queue" for the users that click on multiple packages, and each one you click on would add to a list and then you click "begin" to install them.

Erm... Doesn't Add/Remove, Synaptics, etc already do this? You check the ones you want to install and tell it to go?

---

### Post by mrvertigo on 2007-10-18
Yes, locking individual packages is possible, and locking their dependencies that are being upgraded, problem is a its dangerous, will most likely not work properly for many releases, may result in major breakage, and much more!

There is also the issue brought up by someone, someone mentioned reading the APT  man pages... lets face it guys, Beginner and casual users don't want or feel they need to have a technical understanding of how this or that works, its SAD that well meaning people are told every day to "read the man pages N00B" come on guys you all know this to be true! 

APT synaptic etc already have great "chaining" features that work Very Nicely, This may not be a feasible idea, that dosen't make it a bad one!

Wheres my coffee?

---

### Post by Zdravko on 2007-10-19
> **bethaviv said:**
> Erm... Doesn't Add/Remove, Synaptics, etc already do this? You check the ones you want to install and tell it to go?
Yepp.

---

### Post by mrvertigo on 2007-10-19
it dosent run them side by side, it runs them consecttively, the initial post was sugesting a way to run 2 apts concurently in parallel witch is bad juju I say we stick with the consecutive system

---

### Post by Zdravko on 2007-10-19
Yepp. The current version is ok.

---

### Post by frup on 2007-10-19
I like the install que idea, the amount of times I have opened say synaptic and run an installation to turn round 30 seconds later and decide I want something else, then having to wait say 5 minutes for synaptic to finish. Sometimes I get distracted and forget.

---

### Post by Zdravko on 2007-10-19
Use pencil and notes to write down what you may forget.

---

### Post by bethaviv on 2007-10-19
Being able to run 2 apts (or installs in Windows' case) is one of the things that makes Windows poorly designed. For someone who doesn't know what they're doing they could break the OS and (unfortunately) Linux is more sensitive than Windows is to that. It's protection for the unexperienced Linux people, but might be a hinderance on the more experienced crowd.

The queue idea is nice, but maybe have it as it's own seperate program and not something that is built in.

---

### Post by Zdravko on 2007-10-19
Yes, That is right.

---

### Post by notna01 on 2007-10-20
I wasn't talking about "installing at the same time", I was talking about downloading multiple ideas at once, then installing one by one....

---

### Post by Kamilion on 2007-10-20
Perhaps a better way of expressing this:
Separate the UI from the installation queue.

You should be able to open as many package manager windows as you wish and independently control them. When you execute an installation from any of them, they should be fed into a global queue.

Basically what should happen is say you're installing XEvil. XEvil has no deps. You click install. It starts fetching and installing the package.
Meanwhile, that package manager is now locked and effectively useless, because it's currently keeping track of that install and not allowing you to select anything else to install.

If someone were to open a second package manager window and select nethack to install, it should *ADD NETHACK TO THE BOTTOM OF THE GLOBAL QUEUE* instead of attempting to install them in parallel.

Alternately to the above example, the package manager UI does not actually need to be locked while a package is installing, simply add additional packages and deps to the queue dynamically.

Solves the problem quite elegantly and removes all the hassle and unnecessary warnings.

The only problem is dependency resolution, for example, adding a package that depends on a newer version of a library that's already installed, and an install higher in the queue is still trying to link against the old version. Bad Mojo there. But if properly planned and executed, it would most likely operate just fine.

Just my two cents. :)

---

### Post by slavik on 2007-10-20
APT has a database which is what gets locked (standard database altering procedure).

In Windows you cannot run 2 install processes at the same time (if they use MSI packaging)

EDIT: A neat idea would be to queue up packages while apt/synaptic is running.

---

### Post by Zdravko on 2007-10-20
[slavik]("http://ubuntuforums.org/member.php?u=67597") is right.

---

