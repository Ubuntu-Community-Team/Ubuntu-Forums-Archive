---
title: "Suspicious file - .png.scr"
date: 2022-04-04
forum: Security
---

### Post by ras00998 on 2022-04-04
Hello. 

First sorry if I am posting in the wrong place - also sorry I am a Ubuntu user but a beginner with zero command line skills. 

I am very concerned today because yesterday I was silly enough to download a zipped file, use a password to open, and clicked on a png.scr file. (nothing happened)
(I then sent the file to our other windows computer and tried to open there also nothing happened)

I uploaded the file today to virustotat(dot)com and it shows 6 red alerts for trojans etc.. 

We have disconnected windows machine from internet and wont be using it again, but is this Ubuntu machine also at risk? What should I do?

Thank you for all help and advice, 

(Ps, File was downloaded because our visual artist twitter page was contacted by someone looking for a commissioned art work, and they wanted to send reference images,  we were stupid enough to download, enter password to unzip.. )

( zip file contained the png.scr file, 6 pngs and 1 jpg )
We are on Ubuntu 20.04.4 LTS

---

### Post by TheFu on 2022-04-04
Run the 'file' command against it. What does that say?

On Unix-like OSes, the extension doesn't matter.  For example, PDF files don't have to end in .pdf to be valid. Extensions are for humans. Humans lie.

```
$ file /path/to/png.scr
```
What does that say?  Obviously, you'll need to use the correct path to the file. It can be absolute or relative - doesn't matter.

I could make all sorts of assumptions based on .scr, but that would just make an ass-u-me.  <--- good lesson from my engineering classes.

---

### Post by ras00998 on 2022-04-04
Many thanks for the input, 
Does not seem to work? I get this - 

$ file /path/to/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr
/path/to/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr: cannot open `/path/to/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr' (No such file or directory)

---

### Post by deadflowr on 2022-04-04
Replace the /path/to part with the actual path to the file.
Something like /home/you/png.scr
Replace you with whatever the username is or whatever the correct path name is.

Do you know where the file is located,
like is it in the Pictures folder or somewhere like that?

---

### Post by ras00998 on 2022-04-04
thank you!, it is on desktop in a folder titled A

(sorry I thought the 'correct' path' from ordinal poster meant the full file title)

I am looking into how to how to write the correct path now..

---

### Post by ras00998 on 2022-04-04
I am still doing something wrong -
Here,

```
$ file /home/kepa/desktop/A/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr
/home/kepa/desktop/A/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr: cannot open `/home/kepa/desktop/A/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr' (No such file or directory)

```

See attached screenshot, I think I am adding the right path?

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290215&stc=1[/IMG]

---

### Post by deadflowr on 2022-04-04
Desktop is capitalized.
Try it like
```
file /home/kepa/**D**esktop/A/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr
```

---

### Post by ras00998 on 2022-04-04
Thank you :) 
See below, I hope this means it is only a threat for Windows?

```
file /home/kepa/Desktop/A/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr
/home/kepa/Desktop/A/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr: PE32 executable (GUI) Intel 80386, for MS Windows



```

---

### Post by TheFu on 2022-04-04
Yep, but if you have WINE installed, some MS-Windows viruses do work under WINE too.  32-bit?  That's pretty old.

---

### Post by ras00998 on 2022-04-04
Thank you very much - 
I am unsure if I have WINE installed, how would I check do you know?

---

### Post by TheFu on 2022-04-04
Type 'wine<enter>' for starters.

---

### Post by ras00998 on 2022-04-04
Thanks, 

Like this? 

```
$ wine<enter>
bash: syntax error near unexpected token `newline'

```

---

### Post by The Cog on 2022-04-04
Try to run it from the command line like this:
```
~$ wine

Command 'wine' not found, but can be installed with:

sudo apt install wine              # version 5.0-3ubuntu1, or
sudo apt install wine-development  # version 5.5-3ubuntu1
```

---

### Post by ras00998 on 2022-04-05
Thank you - I get the same response 'not found'
I feel some relief now about the whole thing.

Everyone here has been so helpful - thank you all. Your help has been much appreciated.

---

### Post by SeijiSensei on 2022-04-05
I run the excellent [MailScanner]("https://www.mailscanner.info/") on my mail server. It has many rules to block dangerous files. Ones with .scr extensions are in that category.
```
# These are very dangerous and have been used to hide viruses
deny    \.scr$      Possible virus hidden in a screensaver                     

```
Also files with multiple different extensions like .png.scr are almost always dangerous.
```
# Deny all other double file extensions. This catches any hidden filenames.
deny    \.[a-z][a-z0-9]{2,3}\s*\.[a-z0-9]{3}$    Attempt to hide real filename extension 
```

(The rules use "[regular expressions]("https://www.regular-expressions.info/")" to match filenames.)

---

### Post by ras00998 on 2022-04-05
Very interesting thank you. I will avoid .png.scr files like the plague evermore  
:-)

---

### Post by Shibblet on 2022-04-07
Are we going too far here?  Is it a .PNG file with and added .SCR extension (Windows.)

Have you tried opening it up with Gwenview or GIMP?

---

### Post by DuckHook on 2022-04-07
> **Shibblet said:**
> Are we going too far here?  Is it a .PNG file with and added .SCR extension (Windows.)
Not going too far. Whenever something is suspicious, it's better to be safe than sorry.
> Have you tried opening it up with Gwenview or GIMP?
Not such a good idea if it is already a suspect file. Malware can leverage the execute privileges of apps to do lots of bad stuff. There is a way to do so relatively safely, but it involves spinning up a VM, snapshotting it, opening up the suspect file within the VM, then rolling the VM back to an earlier safe state right afterwards.

---

### Post by #&amp;thj^% on 2022-04-07
> **DuckHook said:**
> Not going too far. Whenever something is suspicious, it's better to be safe than sorry.

Not such a good idea if it is already a suspect file. Malware can leverage the execute privileges of apps to do lots of bad stuff. There is a way to do so relatively safely, but it involves spinning up a VM, snapshotting it, opening up the suspect file within the VM, then rolling the VM back to an earlier safe state right afterwards.

Ya just can't argue that wisdom... :)

---

### Post by DuckHook on 2022-04-07
> **1fallen said:**
> Ya just can't argue that wisdom... :)
Thanks, but I can't take credit for this. It's standard safety protocol for suspect files. It's much harder to do in proprietary OSes because of cost considerations. I don't know if Windows allows a second copy to run in a VM without paying for another licence. With Apple, I doubt it's even possible. They are notorious for crippling their OS so that it only runs on their bare metal, so VMs are out.

But we live in the Linux-verse. We can run as many copies as we like in VMs, containers or multi-boots. We can go nuts. My own feeling is that *everyone* should have at least one Linux VM installed, for things like the OP's concerns, but also for so much else. Leverage the full power and flexibility of Linux. After all, that's why we use it, isn't it?

---

### Post by TheFu on 2022-04-07
> **Shibblet said:**
> Are we going too far here?  Is it a .PNG file with and added .SCR extension (Windows.)

Have you tried opening it up with Gwenview or GIMP?

It is NOT an image file with the wrong extension. But humans do lie.  OTOH, the _**file**_ command doesn't look at the extension. It looks at the internal header to decide what type of file something is.

```
file /home/kepa/Desktop/A/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr
/home/kepa/Desktop/A/ERTCBCC-75FA-4318-90B3-B656D3D9ABBE.png.scr: PE32 executable (GUI) Intel 80386, for MS Windows

```
That proves it. It is a Windows binary.  scr could be a Windows screensaver extension and was very commonly used for malware and virus distribution. 

Delete it and contact the person you go it from (don't email them a copy) using an out of band communication method (voice call on a phone). Once I let a friend who sent me a virus (100% certain it was accidental) know that he'd sent a virus to me via email.  That ISP blocked my email server for over 5 yrs. They were THE major ISP in my region of the country, so I was unable to email **anyone** at their domain.  I used to work at that company and knew 5 of their email people, but they couldn't remove my domain from their block list. Everything related to that was automatic, they claimed.  Every year, I'd try to use their automatic "I fixed my email domain" webpage to get removed from their malware domain list.

---

### Post by ras00998 on 2022-04-09
Thank you everyone - 
Not being an expert by any means, I am reluctant to attempt opening this in any other programs. 

Appreciate all the input, hope I am doing the right thing.

---

### Post by DuckHook on 2022-04-09
> **ras00998 said:**
> Thank you everyone - 
Not being an expert by any means, I am reluctant to attempt opening this in any other programs. 
Yours is only good security instincts, whether expert or not. If you keep up that sort of guard, malware will have a hard time infecting your system.
> Appreciate all the input, hope I am doing the right thing.
You did the right thing by asking for advice on this forum.

---

### Post by ras00998 on 2022-04-10
Thank you :)  
Will keep an eye on this forum

---

