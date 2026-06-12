---
title: "League of legends in wine, error."
date: 2010-07-16
forum: Wine
---

### Post by aloprot on 2010-07-16
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141](http://appdb.winehq.org/objectManager.php?sClass=version&iId=19141)

So as the title says I can not start the launcher of this game. I'm running ubuntu 10.04 32 bit version. I downloaded the wine source, applied the two patches, compiled it, in the terminal it says it's installed. I downloaded winetricks, chmod +x it, downloaded adobe air and all that i need to run this game. But when I double click it, it doesn't start.
I did wine LeagueofLegendsEUDownloader.exe &> log.txt in the terminal and I have received the following output in log.text, only 1 line :
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)
What can I do?
I went to #winehq but nobody knows what to do. I did run winecfg, selected windows xp. Have any suggestions? Thanks!

---

### Post by cogadh on 2010-07-16
There should be more to that error. Run the game from the terminal and copy/paste the full contents of the terminal output here. Use the forum CODE tags when you post, it will make the output easier to read.

---

### Post by aloprot on 2010-07-16
Hi, that's the only thing I get, I did wine LeagueofLegendsEUDownloaded.exe &> log.txt in the terminal and that's the only thing I got. Is there another way to get more debugging information? I'm a beginner when it comes to gnu/linux and wine.

---

### Post by cogadh on 2010-07-16
Don't bother sending it to the log.txt, you can copy/paste it right out of the terminal. Every time you use Wine it should produce a lot more error messages than what you saw in that log file, most of which can be completely ignored. That particular error should have been followed by a dump that may contain useful information.

---

### Post by kimano on 2010-07-27
I get that exact same error, and only that. Where would I find the dump to put on here?

The only thing in the terminal is:

[email]charles@Charles-Laptop:~/.wine[/email]/dosdevices/c:$ wine LeagueofLegends.exe 
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)
[email]charles@Charles-Laptop:~/.wine[/email]/dosdevices/c:$

---

### Post by cogadh on 2010-07-27
The dump should have appeared in the terminal, immediately following that unhandled exception error. Something definitely changed recently (possibly with the release candidate versions), it seems that Wine might not be producing the amount of detail it used to in the terminal. Question: is the executable actually sitting in the root of your Wine "C:" drive?

---

### Post by kimano on 2010-07-27
Yes. It's just the installer though, not the installed executable.

---

### Post by DieNacht on 2010-08-16
I'm having the same issue. I'm getting this error in the terminal:

```
pedro@pedro-laptop:~$ wine ~/Desktop/LeagueofLegends.exe
err:seh:setup_exception_record stack overflow 1532 bytes in thread 0009 eip 7bc3f5ce esp 00a80d34 stack 0xa80000-0xa81000-0xc80000
err:ntdll:RtlpWaitForCriticalSection section 0xa5eb00 "?" wait timed out in thread 001f, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0xa5eb00 "?" wait timed out in thread 001f, blocked by 0009, retrying (60 sec)

```

---

### Post by ravensqu on 2010-11-07
I notice that this thread is marked as [SOLVED], but in reading the thread, I see no possible solution to fixing this issue. 

I am running into the same ```
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr (nil)
``` issue when i try to run the downloader to download the install files. I am running Lucid x32.

Could whoever found the solution to this issue please post it? This is the only thread on this error i can find.

---

### Post by pandasRbears on 2011-06-12
I am able to get the program to install but not run.

Downloaded and saved the installer. Went to the application properties and told it to "allow executing file as program" then double clicked.

However after the installer went through I went to applications>wine>riot games> League of Legends> and click the launcher it does nothing just get the working mouse graphic for a moments then nothing.

---

