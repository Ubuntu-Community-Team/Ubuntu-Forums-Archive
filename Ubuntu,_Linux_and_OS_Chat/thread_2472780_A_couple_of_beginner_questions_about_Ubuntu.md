---
title: "A couple of beginner questions about Ubuntu"
date: 2022-03-12
forum: Ubuntu, Linux and OS Chat
---

### Post by TheUninvited on 2022-03-12
[LIST=1]
[*]Why most of the time we use sudo apt update before installing any other app?
[*]In windows I used to check for windows updates , but how can we do that for ubuntu?
[*]Do you use antivirus ? If yes which one you recommend?
[*]**Problem:I** have the mouse g502 hero and apparently the go backward or forward a page in the browser is not working ? so basically what I am talking about is that my mouse has two buttons one to go forward a page or to go backward. I haven't seen the logitech to have support for ubuntu . I have this pipe app and what does it does is configured the mappings of the mouse and everything and even though the backward and forward is correct over there is not working I dont know why.
[*]Is there any way to copy a command and paste into terminal but using the shortcuts of ctrl + c and ctrl + v instead of using the mouse right click + paste ?
[*]Any tips for first time users?
[/LIST]

My ubuntu version is the last one 20.04

---

### Post by guiverc on 2022-03-12
The command `sudo apt update` tells your system to update it's software lists, ie. list of packages that are available for download. It does **not**  upgrade any packages; as that is done in a subsequent command (ie. `sudo apt upgrade` or `sudo apt full-upgrade`).

The reason you update software lists before a `sudo apt update` is to avoid errors, or installing older packages when a newer package is available; ie. ensure your boxes software lists are *up to date*.   

If you're going to execute multiple install commands; there is no need to re-run `sudo apt update` before each command, but if it's been awhile (*hours/days/unknown*) since the last software list was updated it's good practice to re-run `sudo apt update`.

I don't use anti-virus; viruses really are a windows issue & they're not very common anyway. Ubuntu however is impacted by other malware though just like windows; but if you've a Ubuntu server system that is storing files that are being served up to windows client(s); running a virus scanner is possibly a good idea for your windows boxes, you can read [https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

Ubuntu 20.04 LTS is the 2020-April release of Ubuntu; and is four releases ago, ie. Ubuntu releases uses a *year.month* format.

[Ubuntu 20.10 was the 2020-October release]("https://fridge.ubuntu.com/2020/10/22/ubuntu-20-10-groovy-gorilla-released/"); which was six months later; however it wasn't a LTS or *long-term-support* release so [is now EOL]("https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/")
[Ubuntu 21.04 was the 2021-April release]("https://fridge.ubuntu.com/2021/04/22/ubuntu-21-04-hirsute-hippo-released/") which was next after 20.10; again release six months after 20.10; but it wasn't a LTS release also and [is now EOL]("https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/")
[Ubuntu 21.10]("https://fridge.ubuntu.com/2021/10/14/ubuntu-21-10-impish-indri-released/") was the 2021-October release of Ubuntu and is the *latest stable* release of Ubuntu; the last before the next LTS which will be Ubuntu 22.04 LTS.

Ubuntu 20.04 LTS *is the **latest *LTS release of Ubuntu; but 3 releases have occurred since then.  Even if you include the *re-spins* of 20.04, eg. [Ubuntu 20.04.4 LTS]("https://fridge.ubuntu.com/2022/02/25/ubuntu-20-04-4-lts-released/") that is mostly the original 20.04 release with upgrades included on the ISO, plus software stack from *latest* release (ie. Ubuntu 21.10's kernel stack is included) but still contains the older software from 2020-April release (ie. 20.04).

The next re-spin of 20.04 will be 20.04.5 which will use the kernel stack from Ubuntu 22.04 LTS, thus will occur *after* the release of Ubuntu 22.04 LTS; and I don't think you'll want to call the Ubuntu 20.04.5 release a *later* release than Ubuntu 22.04 LTS.

---

### Post by ajgreeny on 2022-03-12
> **TheUninvited said:**
> [LIST=1]
[*]Why most of the time we use sudo apt update before installing any other app?
[*]In windows I used to check for windows updates , but how can we do that for ubuntu?
[*]Do you use antivirus ? If yes which one you recommend?
[*]**Problem:I** have the mouse g502 hero and apparently the go backward or forward a page in the browser is not working ? so basically what I am talking about is that my mouse has two buttons one to go forward a page or to go backward. I haven't seen the logitech to have support for ubuntu . I have this pipe app and what does it does is configured the mappings of the mouse and everything and even though the backward and forward is correct over there is not working I dont know why.
[*]Is there any way to copy a command and paste into terminal but using the shortcuts of ctrl + c and ctrl + v instead of using the mouse right click + paste ?
[*]Any tips for first time users?
[/LIST]

My ubuntu version is the last one 20.04
Hello TheUninvited.
Welcome to the forums.

[LIST=1]
[*]We use ***sudo apt update*** to ensure that the listing of the databse of packages and versions is fully up to date, thus making sure that the downloaded packages are also up to date.
[*]To check for updates you can run command ***sudo apt update && apt list --upgradable*** which first updates the database the lists alphabetically all packages that can be updated.  You then run command ***sudo apt full-upgrade*** which upgrades all in that list.  There are GUI applications which I do not use, eg **update-manager**.
[*]Antivirus is not necessary for Linux in general, many users simply using something if they have come from Windows because they find it hard to believe it is not needed. See [https://easylinuxtipsproject.blogspot.com/p/security.html#ID1.1](https://easylinuxtipsproject.blogspot.com/p/security.html#ID1.1) for a discussion of this in more detail.  I have not used antivirus since I started using Ubuntu in 2005, 17 years ago and I have never had any problems without it.
[*]No idea about the mouse problem but it is possible to change the way GUI's use the mouse buttons, though I have no experience of doing so.
[*]Ctrl-C in terminal closes the command being run so it can not be used for **copy** in terminal; for that you need **Ctrl+Shift+C** to copy and **Ctrl+Shift+V** to paste into terminal.
[*]You will find many versions of lists of the things you should do when you first start using Linux but they are only that one person's idea for him to achieve what he wants. Your needs will probably be very different so I recommend you ignore all such suggestions and simply use the OS, asking or searching when you need to.
[/LIST]

---

### Post by grahammechanical on 2022-03-12
In Ubuntu with the Gnome desktop you can click on Activities and type in the search panel "software." You will get a selection of applications relating to "software." Click on the icon for Software Updater and an application with a graphical user interface will run that will run the commands "apt update," "apt upgrade," and "apt autoremove." Should a package such as an updated Linux kernel be part of the upgrade you will get a dialog asking for authorisation. Type in your password.

Regards

---

### Post by TheUninvited on 2022-03-12
thank you everyone for your tips and your help ofcourse.

The only thing I am still trying to resolve is the issue with my mouse going forward and backwards.

---

### Post by TheFu on 2022-03-12
> Is there any way to copy a command and paste into terminal but using the shortcuts of ctrl + c and ctrl + v instead of using the mouse right click + paste ?

I use the X/buffer to select and paste. Much more efficient that using the keyboard.  
SELECT with the left mouse button - selecting text with a mouse automatically places it into the X/buffer.
PASTE with the middle mouse button.  
In theory, the X/buffer shouldn't clear until some other selection happens, but I've noticed that after 20-30 seconds, it is cleared. Don't know why.

> Any tips for first time users?
Linux isn't Windows or OSX.  Learn to use it as the fantastic OS it is.  

Be lazy with anything you do more than once. Create some automation to make those things you do daily happen automatically for you.  Unix systems are designed to make creating little tools easy for end-users.  That is a core philosophy for all Unix-like OSes.  Linux just happens to be the easiest to accomplish this with currently.

Learn the think the Unix way. Don't expect to use the same methods used on another OS on Linux. That is often the most inefficient way and will lead to frustration.

Don't fear the shell (CLI/terminal window).  Use it when it makes sense and don't use it when it doesn't make sense. A beginner's book, [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  If you spend the time to learn the first 10 chapters, then how the underlying OS actually works will become clearer and you won't be a point-n-click-only user.  Maybe do that after about 6 months just playing around with the system first. That will leaving your brain asking lots of questions that the beginning of the book will answer. The "aaaaaah" moments will be better then, as understanding clicks.

Almost anything you do in a GUI can be automated in a shell script, except reading.  A few times each day, I have my Linux system create a little magazine to be read with current topics/stories/articles that interest me. I don't have to visit 20 different websites to find them. They are pulled to my system for me, automatically. If I don't have time to read, I can mark them all read and move on. If I'm headed to a park and want to take some reading with me (offline), my tablet has a copy that gets updated automatically 2x a day.  Anything read by any client machine (phone, tablet, desktop, laptop) is marked read centrally, so the other clients don't show it to me.

Automation is great.

---

