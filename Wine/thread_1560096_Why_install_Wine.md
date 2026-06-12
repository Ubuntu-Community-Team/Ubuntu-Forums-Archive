---
title: "Why install Wine?"
date: 2010-08-24
forum: Wine
---

### Post by TUA85550 on 2010-08-24
I am a little bit skeptical of this Wine project. I understand that if you install Wine, your system is vulnerable to Windows viruses and could potentially infect your system. My question is if all I am using Wine for is Gaming and Microsoft Office, could I still get a virus? For example, if I load up FireFox (which is installed by default on Ubuntu) and go to a web site that has a virus, would I automatically become infected or the only way to get a virus is to load up the Wine version of FireFox (the windows version) from wine which would auto go straight into my wine directory.

The whole purpose (at least from my point of view) of switching from Windows to Linux is that you don't have to worry about getting viruses. When you download and enable Wine, your Linux system is vulnerable and can become infected with Windows viruses and do horrible damage to your Linux Operating System. So I ask you this, what's the point in getting Wine than?  I am a little confused and would love some clarification.

---

### Post by bowens44 on 2010-08-24
> **TUA85550 said:**
>  When you download and enable Wine, your Linux system is vulnerable and can become infected with Windows viruses and do horrible damage to your Linux Operating System. So I ask you this, what's the point in getting Wine than?  I am a little confused and would love some clarification.

Your linux system is not vulnerable to windows viruses. At worst, your wine install be messed up.

---

### Post by kostkon on 2010-08-24
Wine is not running all the time (as a background process), it loads only when you try to run a windows application.

---

### Post by anaconda on 2010-08-24
> **bowens44 said:**
> Your linux system is not vulnerable to windows viruses. At worst, your wine install be messed up.

not entirely true...

with default settings wine has read/write access to "/" so a windows virus can write copies of itself to your home directory, or add itself to files you have on your home directory.

Luckily most windows viruses dont try to write files to folder /home/username

but I have heard some viruses do run in wine.... and they do make copies of themselves...

---

### Post by TUA85550 on 2010-08-24
> **kostkon said:**
> Wine is not running all the time (as a background process), it loads only when you try to run a windows application.

In windows, you go to a web site that contains a virus and your virus scanner blocks the virus from downloading and executing itself.  However, sometimes the virus scanner does not catch brand new viruses and the virus and now auto executing itself and causing havoc to your computer.  How is Wine different if it can run windows programs including viruses?  You say it only runs when running a window program, well isn&#8217;t a windows virus technically a windows program?

---

### Post by JBAlaska on 2010-08-24
Not this againnn:(

---

### Post by hikaricore on 2010-08-24
> **anaconda said:**
> 
but I have heard some viruses do run in wine.... and they do make copies of themselves...

And they have a plan..

---

### Post by mocoloco on 2010-08-24
> For example, if I load up FireFox (which is installed by default on Ubuntu) and go to a web site that has a virus, would I automatically become infected or the only way to get a virus is to load up the Wine version of FireFox (the windows version) from wine which would auto go straight into my wine directory. 

> 
In windows, you go to a web site that contains a virus and your virus scanner blocks the virus from downloading and executing itself. However, sometimes the virus scanner does not catch brand new viruses and the virus and now auto executing itself and causing havoc to your computer.

You're got a misunderstanding of how viruses get downloaded and executed. Most virues and other malware do not "automatically" download, and instead use social engineering tactics like claiming to be screen savers or being bundled with useless toolbars.  These have to be downloaded by the user and executed manually.  The exception and the real danger of automatic access to the whole system comes from ActiveX, which only works in IE (and is less of an issue in newer version of IE).  So to answer your question, if you downloaded an untrusted .exe file it wouldn't matter if you used Firefox for Linux or the Windows version via Wine, if you then executed that file using Wine then yes it could potentially affect your system.

> The whole purpose (at least from my point of view) of switching from Windows to Linux is that you don't have to worry about getting viruses. When you download and enable Wine, your Linux system is vulnerable and can become infected with Windows viruses and do horrible damage to your Linux Operating System. So I ask you this, what's the point in getting Wine than? I am a little confused and would love some clarification.


The point is that there are tons of applications written only for Windows.  If 99% of your needs are met with native software then why should you reboot to run a simple medical diagnostic app or so that your kids can run Windows 98 games?  The tradeoff is that yes, you then have to take the same precautions when executing code.  You can't use Wine because it runs Windows programs (your app) and then be upset because it can run Windows programs (viruses).

This is one of the reasons for the move in Ubuntu 10.04 to not allow execution of exe files in Wine without the user setting the "executable" attribute on the file.  [This move has been controversial]("http://www.workswithu.com/2010/06/11/running-windows-files-in-ubuntu-10-04-the-wrong-approach/"), and the debate goes on for where we draw the line between convenience and security.

---

### Post by handy on 2010-08-25
The only reason that we use Wine on Linux or OS X, is that we have NO alternative.

Why on earth else would we stuff around with an interpreter if we could just plain speak the language?

---

### Post by beew on 2010-08-25
Looking at the bright side most windows programs don't run very well in wine. Apart from some games (yeah, what else, games are the only game in WINE, almost) and very outdated versions of MS Office and a few odd items here and there many programs get garbage or bronze rating on the WINE list. That should cut down a lot of viable viruses in WINE unless you can run them as games. If you have a virus that runs in WINE maybe you should rate it as gold or platinum and put it on their list. :)

---

