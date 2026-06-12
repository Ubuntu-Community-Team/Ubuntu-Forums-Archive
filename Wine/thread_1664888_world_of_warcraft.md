---
title: "world of warcraft"
date: 2011-01-11
forum: Wine
---

### Post by bradenmast on 2011-01-11
good day all I am running 10.10 I have my right drivers installed I dual boot vista and ubuntu so I already have the game installed I go to launch and the launcher pops up, I pos play and a black screen with the gauntlet  curser appears with sounds but that is it I'm in class right now but if  yall have any ideas it would be much appreciated yall have a nice day and thanks!

---

### Post by cwwilson721 on 2011-01-11
Read the stickys.> Things you should try before asking for help:
[COLOR="Red"]Use the proprietary drivers for your video card[/COLOR] - many graphics issues in Wine are due to missing features in the free drivers for various video cards. Try enabling the proprietary drivers for your video card, if available, using System->Administration->Additional Drivers.
[COLOR="Red"]Check AppDB [/COLOR]- Wine's Application Database is one of the best sources for help with running apps in Wine. First and foremost, it will tell you when an application is not worth trying at all. Secondly, but almost as important, an application's AppDB entry may include how-to information on a working way to install and run your application.
Never run Wine with sudo - Do not run Wine as root or by using sudo. Doing so doesn't help anything and will break your fake Windows installation entirely.
[COLOR="Red"]Do not try and install DirectX[/COLOR] - Wine already has its own implementation of DirectX, and attempting to install the Windows version might break some things. Cancel or skip the install if an application prompts you.
Reinstalling Wine won't help - Reinstalling the same Wine package in Synaptic or Software Center won't do anything - your virtual Windows drive and applications will be just the same unless you manually remove them. What you probably wanted to do is erase your fake Windows install entirely; to do this, you must remove (or rename) the hidden .wine folder in your home directory (view->show hidden files). This will erase all Windows applications you've installed with Wine and let you start fresh. Note that you'll still have (nonworking) start menu entries for the removed apps in Applications->Wine unless you first removed them with Wine's uninstaller.
Update Wine - Unless you have specific information that the latest version of Wine won't work, you should try updating to the most current version of Wine. Each update includes many bugfixes that can correct your issue. However, it is important to note that an update could include new bugs or regressions that will cause problems with some applications. If you are manually selecting versions, please note that they are two digit numbers: Wine 1.1.10 is newer than 1.1.9.
[COLOR="Red"]***_Search the forums_***[/COLOR] - There are many, many posts on running specific applications in Wine already. Chances are really good that someone has already asked the same question you have.
Try different Windows versions - Much like Windows itself, Wine supports different "compatibility modes" for different versions of Windows.
Check the terminal output - Perhaps I should say "Use the terminal" first. When run from the terminal, Wine outputs any error messages to the terminal window, which may tell you exactly what is wrong. This is especially useful for identifying when a DLL is missing and using winetricks may be needed. Check the output for details like that and anything else that may identify where your error is occurring.


Search the forum.

Answers are there.

I don't want to sound like this, but if you would do this FIRST, the people who check/help these forums wouldn't get a headache from trying to read your non-punctuated book that you posted, on a subject that has been asked and answered MULTIPLE TIMES before.

---

