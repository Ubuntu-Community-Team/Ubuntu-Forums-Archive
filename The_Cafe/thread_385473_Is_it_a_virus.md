---
title: "Is it a virus?"
date: 2007-03-15
forum: The Cafe
---

### Post by thomasaaron on 2007-03-15
So, I got this email with a link in it to pick up a greeting card sent by a family member.

I clicked the link expecting to be sent to an e-card website, but instead my download manager came up with the name of a file to be downloaded called picture.exe.

I was thinking that some spammer was trying to mangle Windows boxes, so I downloaded it onto my Ubuntu desktop. The properties say it is an x-ms-dos executable file. It appears to be a binary file.

I pulled up IDLE to open and read it line by line, but I got nothing but gibberish.

Is there a way to further examine it? (Other than forward it to my wife's PC? :guitar:  )

Best,
Tom

---

### Post by karellen on 2007-03-15
picture.exe...:lolflag: yes, it's probably a virus

---

### Post by Trebuchet on 2007-03-15
Sounds like the Storm worm, which usually uses any number of innocent-sounding subjects with an .exe extension. While it might not infect a Mac or Linux system, you probably shouldn't send it to anyone you know with a Windows machine who doesn't practice safe computing.

There is no valid reason for a greeting card to have an .exe extension. I've received many of them and most of them use Flash animation. I would delete it, then ask the person you ostensibly got it from if he actually sent it.

---

### Post by kerry_s on 2007-03-15
Maybe try using wine?

---

### Post by Trebuchet on 2007-03-15
Storm Worm is actually a trojan horse. It's a couple months old; I'm surprised anyone is still trying this. 

[http://news.com.com/Storm+Worm+rages+across+the+globe/2100-7349_3-6151414.html](http://news.com.com/Storm+Worm+rages+across+the+globe/2100-7349_3-6151414.html)

Delete with extreme prejudice.

---

### Post by Quillz on 2007-03-15
> **thomasaaron said:**
> So, I got this email with a link in it to pick up a greeting card sent by a family member.

I clicked the link expecting to be sent to an e-card website, but instead my download manager came up with the name of a file to be downloaded called picture.exe.

I was thinking that some spammer was trying to mangle Windows boxes, so I downloaded it onto my Ubuntu desktop. The properties say it is an x-ms-dos executable file. It appears to be a binary file.

I pulled up IDLE to open and read it line by line, but I got nothing but gibberish.

Is there a way to further examine it? (Other than forward it to my wife's PC? :guitar:  )

Best,
Tom
Yes, it's more than likely a virus. A real e-card wouldn't be a .exe.

---

### Post by Choad on 2007-03-15
open it in wine for funsies

---

### Post by The Noble on 2007-03-15
> **Choad said:**
> open it in **ROOT** wine for funsies 

For added fun let wine see your / and /home directories. Mount all drives while you are at it. :popcorn:

---

### Post by prizrak on 2007-03-15
Grabm ClamAV for Linux and scan it. If it's a virus it will most likely pick it up.

---

### Post by WalmartSniperLX on 2007-03-16
By the nature of it, it looks to me like a Trojan Horse. Usually the "Cracker" will use generic names for the server script, such as "install.exe" or "setup.exe". When you click it, depending on how it was made, it may dissapear to your system32 folder and override a gerneric windows32 host file. We all know what happens after that :P It loads up into your registry/processes, opens ports, and connects to a host where it sends back and forth information and allows the "Cracker (who calls themself a hacker)" to remotely control your system.

---

### Post by Keith_Dreamz on 2007-03-18
Hey guys check this out.... my story is something different.......Yesterday i saw my some of my file were getting copied on my my desktop....i didnt saw any "copying"window.......but files were getting copied like they use to copy in general.....could this be a virus???????and ya few days back i saw my computer with a new user name "LogMeInremote user...with no "Password"i tried every possible way to remove the user name but was not able to......this "stranger" Username comes again n again...What can b the problem?????Please help me out....m new to this Forum......:popcorn:

---

### Post by Trebuchet on 2007-03-18
Sounds like you might have a virus or trojan (I'd suspect the latter, although it might just be someone on your network mucking around.).

Do you run a firewall (hardware or software)? Do you have a spyware scanner and antivirus app? Run those as soon as possible.

In the meantime, I'd shut it down with Task Manager ASAP.

---

### Post by Keith_Dreamz on 2007-03-19
Hey thanks a ton for the reply....M using Avast Professional Edition on my system......i cam across one more thing that when i connect my usb to the computer....It automatically creates folder in it with the name of the album of the song.....Its so accurate that sometime i feel that somebody is accessing my computer and creating those folder....but how come on my IPOD??????and ya i cant see logmein in my task manager.........i have searched for the registry entries and deleted any entries related to the logmein.......

---

### Post by Keith_Dreamz on 2007-03-19
and ya my system is not at all connected in lan.....I mean there is no other pc connected with mine......

---

