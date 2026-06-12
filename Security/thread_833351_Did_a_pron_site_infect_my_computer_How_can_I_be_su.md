---
title: "Did a pron site infect my computer? How can I be sure?"
date: 2008-06-18
forum: Security
---

### Post by ConanCimmerian on 2008-06-18
Hi first post. I went to a website(not a pron site), but it ended up opening another window that did contain a pron site. *sigh* and one of teh pron videos did catch my eye (mega hawt chick), and I clixd on it....
At least, I think I remember clicking on the video.

I know...I know... but I didn't expect anything malicious! Just maybe teh pron video or at worst, some other obnoxious popup or browswer window.

But then firefox gives me this error message which essentially said that I couldn't open the file and at this point I was pretty okay with that. Then another firefox message pops up asking if I want to download some setup.exe file, and of course I try to cancel. I *try* to cancel. But it won't let me. And I sure as hell wasn't going to click "ok". So I hit alt+f2 and ran xkill and killed the browser session. Hopefully teh pron site didn't give my computer anything. How can I know?

I'm trying to have a sense of humor about this, but this is a serious question and I am genuinely concerned. I am worried about spyware,keyloggers,trojans,virii, or any other ungodly internet STD I could have got from there. So let me know what I should do at this point.

Thanks

Conan

P.S. I'm running Gutsy Gibbon with firefox 2.0.0.14

---

### Post by pytheas22 on 2008-06-18
An .exe file is not going to infect your Linux computer.  In the worst case it could set itself up in wine, where it probably wouldn't work anyway.  If you're worried about it just apt-get remove --purge wine and reinstall it.

Successful exploitation of browser vulnerabilities is also extremely unlikely if you're running Firefox on Ubuntu.

Linux right now is not susceptible to malware and viruses and all the other junk aimed at Windows desktops; it just won't run on Linux because it's completely different than the environment that these exploits expect.  When people attack Linux machines, they're usually after servers, so the exploits focus on vulnerabilities in stuff like Apache, ssh, ftp and so on.  On a desktop, you're not running any of that, so you don't need to worry.

---

### Post by ConanCimmerian on 2008-06-18
Thanks pytheas. I feel quite better now. I'm still a bit worried, but I'm going to let the information sink in through my dense skull for a while. I may post another reply asking one or two simple(read: stupid) questions regarding this matter. But I am very relieved after reading your post. Thanks again for your help.

---

### Post by pytheas22 on 2008-06-18
No problem for the help.  As I should have mentioned earlier, if you're really worried you can install chkrootkit and rkhunter via Synaptic to scan your system (for Linux rootkits, which are a threat, but which don't come in .exe's).  But I guarantee you--and I don't make guarantees very often--that it's impossible for malware designed for Windows and delivered via an .exe to touch your computer, beyond what it could do in wine, which isn't much and which would be limited to your user account anyway.  If you have any more questions though, feel free to ask.

---

### Post by ConanCimmerian on 2008-06-18
I took your advice and installed chkrootkit and rkhunter, but I do not know how to run them because I'm a newb. Although I should know more than I do. If a program doesn't show up in the menu options, chances are, I'm too stupid to run it unless someone tells me the commands to use.

And I should have remembered that a .exe can't run under Linux. Maybe I was thinking that it was a fake file name or something. But it's more likely that I just forgot .exe's can't run on Linux, or that I didn't know in the first place. lol

Are there any Linux tutorials that you recommend? What is the simplest, most straight-forward, readable, best organized, beginning Linux tutorial that you know of? Websites and books are both okay. If I am going to become a serious, literate, long-term user of Linux, I had better start educating myself better.

Thanks again.

Conan

---

### Post by pytheas22 on 2008-06-18
I actually can't really point you to any Ubuntu/Linux tutorial.  I'm sure they exist, but I didn't learn it that way myself so I don't know.  Mostly I just learned by experience over the last two years.  I also took an introduction-to-Unix class at my university, which was useful for understanding the basics of how Linux works--file permissions, shell commands and so on.  If you're near a university you might want to look into sitting in on a class like that.

I know that there is an [Ubuntu book]("http://www.amazon.com/Official-Ubuntu-Book-Benjamin-Mako/dp/0132435942") that might be useful, although I've never seen so I can't offer any personal evaluation.  Otherwise there's plenty of information available online if you search for something like "introduction to Linux."  [This site]("http://tldp.org/LDP/intro-linux/html/") in particular seems to line up pretty evenly with what was covered in my course.  I think it's old, but if you're looking to understand how to use the shell and how the system is designed, old might actually be better.

But keep in mind that you don't necessarily need to be a Unix guru to use Ubuntu.  It helps to have a simple understanding of stuff like file permissions and some bash-shell basics, but most of the time, you don't really need to know how the system is working or what's happening in the background to be able to use Ubuntu effectively.

EDIT: as for the rootkit programs, they both need to be run in a terminal (found in the Applications>Accessories menu).  I recall there being a GUI for chkrootkit, but I forget its name.  Just type:

```
sudo chkrootkit
sudo rkhunter --check
```

and they'll run their checks and let you know if anything is found.

Also keep in mind that if you ever don't know how to use a program, you can open a terminal and type "man" + the name of the program (e.g. "man rkhunter") and you'll get a page explaining how to use the program.

---

### Post by ConanCimmerian on 2008-06-19
I ran chkrootkit and the vast majority of the results were essentially "not infected", "nothing found"...etc. But as I was scrolling back up through the output in the terminal, after the test was completed I found this:

> Searching for suspicious files and dirs, it may take a while... 
/usr/lib/firefox/.autoreg
/lib/linux-restricted-modules/.nvidia_new_installed
/lib/modules/2.6.22-14-generic/volatile/.mounted

Instead of saying "not infected" it just said the above. Does that mean that those files or directories are suspect? That nVidia driver should be clean because I opted to have it installed, but it's a proprietary driver, so maybe that is the reason it wasn't recognized? But why are the other two listed like that? Do I have any reason to suspect any of the above files/directories as being infected or malicious?

Thanks
-Conan

edit:
This turned up too. I included some of the text before and after the questionable output. The output of interest, I have highlighted in bold.

> Searching for T.R.K... nothing found
Searching for Mithra... nothing found
[b]Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security[/b]
Searching for LOC rootkit... nothing found
Searching for Romanian rootkit... nothing found
Searching for Suckit rootkit... nothing found
It makes it seem like it was searching for "OBSD rk vl" and subsequently found it in the specified location. I wish these things would just say "0" infected files found or "5 files have been infected, here they are...".

---

### Post by pytheas22 on 2008-06-19
The message about the OKBD rootkit seems to be a false alarm...take a look at this [thread]("http://ubuntuforums.org/showthread.php?t=422455").  I think there's no reason to worry; it's just something related to java.

As for the "suspicious files and dirs" message: I googled a little bit and I also don't think it's anything to worry about.  A lot of other people have reported getting the same output from chkrootkit, and no one has linked it to malicious activity.  On the other hand, I didn't find anything (although I didn't search exhaustively) explaining what those hidden directories are for...no one seemed to have a definitive answer.  But my guess is that since a lot of other people have similar results when running chkrootkit, it would definitely be clear if this were indicative of a trojan.  Since that's not the case, I don't think you need to worry.  I'm guessing that the only reason chkrootkit is worried about those files is that they're hidden directories at locations where it doesn't expect there to be hidden directories, but that doesn't necessarily mean there's a problem.  If chkrootkit found hidden processes, that would be something to worry about.

If you want to remove those directories, try:
```

sudo rm -r /usr/lib/firefox/.autoreg /lib/linux-restricted-modules/.nvidia_new_installed /lib/modules/2.6.22-14-generic/volatile/.mounted
```

but again, I don't think this is necessary.  The kind of rootkits you get on Linux are not like the trojans and other malware that bombard a Windows box.  To get a rootkit on Linux, you have to do something really dumb, or somebody has to really want to attack you, which is probably not the case if you're just a casual desktop user. The biggest reason is that when you're logged in to your Ubuntu desktop, you don't have root privileges, so anything that touches you while you're browsing the web or reading email--the biggest entry points for malware--can't actually affect the system, even if it somehow could work on Linux (and all the hidden directories above were found in places where you can't write to without being root, so it's very improbable that any of them are related to your pr0n event).  This isn't the case in Windows (at least up to XP; I hear that Vista locks down regular accounts but I don't know as I've never used it).

If you're really concerned about security, you might want to take a look at [OSSEC]("http://ossec.net").  It basically watches your system constantly and tells you when it notices suspicious changes or suspicious log entries.  It's going to be some work to set it up, but if you're really into security it could be worth it for you.

---

### Post by ConanCimmerian on 2008-06-19
Thanks again pytheas. I didn't mean for you to go through the trouble of doing searches. I probably should have done that first. Sorry about that. I guess I thought you'd be able to tell right away by looking at it. 

[quote=pytheas22]As for the "suspicious files and dirs" message: I googled a little bit and I also don't think it's anything to worry about. A lot of other people have reported getting the same output from chkrootkit, and no one has linked it to malicious activity.[/quote]
Are you saying that your research turned up other users who've had the same(or similar) nVidia directory turn up in chkrootkit?

[quote=pytheas22]But my guess is that since a lot of other people have similar results when running chkrootkit, it would definitely be clear if this were indicative of a trojan.[/quote]
So basically if it were a trojan, then word would have already been out in the linux community?

> If chkrootkit found hidden processes, that would be something to worry about.
I'm pretty sure it did not find any hidden processes. I hope it didn't. Much of the output was indicative of something not being infected, or something not being found, and what I posted were the only exceptions. I may give the log another look though, as it is possible I may have overlooked something else.

> If you want to remove those directories, try:
I'm afraid it would mess up my display. Else wise, I would probably do it. Do you think it would affect my display or the display driver?
edit: forgot about the firefox directory on there too. Do you think I could safely remove that one?

> To get a rootkit on Linux, you have to do something really dumb,...
lol, well that makes me feel better! Because I never do anything dumb! 

> The biggest reason is that when you're logged in to your Ubuntu desktop, you don't have root privileges,
So this is always true? Even if I enter my login password(the same one I use at startup) to authorize something? How exactly does one log in as root? Not that I plan on doing that until possibly some day in the distant future when I may have some idea as to what I am doing.

> (and all the hidden directories above were found in places where you can't write to without being root, so it's very improbable that any of them are related to your pr0n event)
So how did the nVidia directory get written onto my harddrive exactly if I wasn't logged in as root? I did authorize the restricted drivers to be installed, and I did use my login password to do that. Was that effectively me operating as "root"? 

> I hear that Vista locks down regular accounts but I don't know as I've never used it).
You're not missing out on anything good by not using Vista. Vista is why I switched to Linux. The feature you're referring to is the User Account Control. I think that's what it's called. It is infamously obnoxious.

---

### Post by pytheas22 on 2008-06-19
> I probably should have done that first. Sorry about that. I guess I thought you'd be able to tell right away by looking at it.

It's alright; it only took a few seconds to do the searches.  As you get more familiar with Linux you'll get good at using Google effectively to find answers yourself, but I know from experience that it can be hard when you're not very familiar with which search terms to use.

> Are you saying that your research turned up other users who've had the same(or similar) nVidia directory turn up in chkrootkit?


Not in chkrootkit output exactly, but if you search for "/lib/linux-restricted-modules/.nvidia_new_installed" you'll get lots of hits and no mention of malware, just of the nvidia driver.  If it were related to malware, it wouldn't stay under the radar very long.

> So basically if it were a trojan, then word would have already been out in the linux community?


Yeah, the threads I found about it were over a year old, so again, if it were a legitimate threat everyone would have heard about it and the problems would have been patched away long ago.  This is one of the major strengths of open-source platforms: since anyone can read and modify the source code, anyone can find and fix vulnerabilities very quickly; no need to wait until Microsoft or Apple decides to disclose a vulnerablity and release a patch.

> Do you think it would affect my display or the display driver?
edit: forgot about the firefox directory on there too. Do you think I could safely remove that one?

It could break the card, depending on what's in that directory.  I don't have an nvidia card so I don't know.  If the kernel modules for nvidia are in that directory (they end in .ko), then it would break the card.  I think you could get rid of the Firefox directory without a problem.

> So this is always true? Even if I enter my login password(the same one I use at startup) to authorize something? How exactly does one log in as root? Not that I plan on doing that until possibly some day in the distant future when I may have some idea as to what I am doing.


The short answer: whenever you're logged in graphically, you're a normal user without root privileges.  When you enter your password, your privileges are temporarily elevated so that one specific command may be run "as root," but only the command for which you entered the password...after it's run, you go back to being a normal user.  So when you installed the nvidia driver, you provided your password to allow it to modify the system.  But unless you specifically enter your password, you can't touch anything outside of your /home directory.  That's why you don't have to worry about malware coming in through Firefox, because even if it got that far, it's still separated from the vital parts of the system.

In reality it's a bit more complicated than this, especially on Ubuntu, which doesn't really have a root account...instead we use "sudo" to "do" something as the "Super User."  Because of this, you actually can't log in to Gnome as root on Ubuntu unless you hack a lot of stuff (this feature is unique to Ubuntu); you can only run individual commands as root.  You can read more about it online or in the manual pages to get the full story.

So in other words, Linux security works like a castle with two sets of walls.  If the enemy gets inside the first wall, he still can't take down the castle until he manages to breach the second set.

And anyway, since Linux has such a small market share on the desktop, it doesn't have very many enemies in the first place...it just doesn't make economic sense to bother trying to attack Linux desktops.  Linux servers, which do have a significant market share, are another story, but as I said earlier, the way that they get attacked is by going after services that you don't run on a desktop.

---

### Post by ConanCimmerian on 2008-06-19
Thanks pytheas. I learned a lot from your reply.

---

