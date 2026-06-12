---
title: "Discovered unexplained large encrypted folder, possible keylogger?"
date: 2015-03-27
forum: Security
---

### Post by konrad6 on 2015-03-27
Hi all,

I was going through my files today and discovered a very mysterious folder in Home, with a salted title and protected with encryption. I have no idea what it is and I'm the only person using this computer. 

When I tried deleting it, it told me that I don't have the privileges to do that (I know nautilus as root will solve this, but right now I am simply analyzing the folder), the owner is root. My system took about an hour to prepare to delete the files before even telling me that I can't, revealing that the folder contains hundreds of thousands of files.

Right now I'm using Ubuntu 14.04, although I've noticed the same exact phenomenon on previous installs of both Linux Mint and Ubuntu 14.04, with the difference being the location of the folder- it's been in root and somewhere else that I can't quite recall.

I'm thinking that this may be a keylogger, recording keystrokes in an encrypted format. Is there any other explanation that anyone has to offer?

Here's a screenshot of Home where I found it:

[ATTACH=CONFIG]260936[/ATTACH]

---

### Post by kurt18947 on 2015-03-27
No expert here - all all - but I wouldn't think something like a keylogger or spy program would store that many files on your machine nor be so easy to find. I have no clue what it might be, though. I have nothing similar on my machine.  I see you have a VPN folder, might it have something to do with that? VPN communications would be encrypted I believe.

---

### Post by bashiergui on 2015-03-27
How did you determine it's encrypted? See if you can open it as root.

---

### Post by deadflowr on 2015-03-28
Do you mean the folder with the lock in the corner? (M-nUAsomething?)
The lock means read-only, which is why it won't delete, deletion is a write privilege.
But you should be able to open it and view the contents, and see if anything is familiar to you.
And un-readable folder/file would have an X in the corner.

Have you sudo'd anything recently.
You would have needed to have run as root at some point, to get a root file or folder in your home folder.
Other examples of running as root would include installing apps from the software center or any other package installation methods.

I do agree with kurt19847 on the premise of someone wanting to put a keylogger on your system, would hide it far better...

---

### Post by konrad6 on 2015-03-28
It's definitely salted, which is essentially the same as encryption. I have opened it as root, it' just empty .txt files with titles like "nffearewtr2" or "qegrbvc132r," several hundred thousand of them.

---

### Post by konrad6 on 2015-03-28
I've used Bleachbit as root to wipe free space, would that be a possible answer?

I would think that a keylogger would indeed hide stored files in a more obscure folder than Home, but who knows...

---

### Post by bashiergui on 2015-03-29
> **konrad6 said:**
> It's definitely salted, which is essentially the same as encryption. I have opened it as root, it' just empty .txt files with titles like "nffearewtr2" or "qegrbvc132r," several hundred thousand of them.I'm too pedantic to let that go. Salting is something done when hashing passwords, not the same as encryption. If you can open the files then they're not encrypted. Definitions of encryption and hashing: 
[https://gooroo.io/GoorooTHINK/Article/13023/The-difference-between-encryption-hashing-and-salting/2085#.VRg254r3YaE](https://gooroo.io/GoorooTHINK/Article/13023/The-difference-between-encryption-hashing-and-salting/2085#.VRg254r3YaE)

You're not using the word salted in its defined way, so I'm not sure what you're seeing. Are you saying they're salted because the names of the files appear to be randomly generated?

I see no evidence to conclude this is a keylogger. The random names probably indicate the files are temporary. Some root process is generating temporary files that aren't getting deleted like they should, probably because they're not in the /tmp folder which the system occasionally clears out.

Make sure they're really text files. Pick one and type in a terminal ```
file /path/to/file
``` Tell us what the filetypes are. Then also sort the folder to determine the oldest file in it. Look in your applications to determine what might have gotten installed around the time of the oldest file in the folder.

---

### Post by Habitual on 2015-03-30
> **konrad6 said:**
> I've used Bleachbit as root to wipe free space, would that be a possible answer?
I suspect Bleachbit made that directory.

---

### Post by konrad6 on 2015-04-02
I can't even open the folder as root, it tries to load for about an hour but then freezes on me (and I have a 7200rpm drive + i5), I tried several times with the same result... I managed to open a similar folder under a previous installation, and saw as I said a massive number of empty text files with scrambled titles....

Has anybody else used Bleachbit as root with the same result?

---

### Post by cogset on 2015-04-03
When you say "I can't even open the folder as root", are you doing this from a terminal or using a graphical application like nautilus with gksu? Occasionally I've tried to use the latter and for some reason it can be so slow that it almost hangs, now everytime I want to see stuff like that I just use a terminal and **sudo ls -la** .

Alternatively, maybe can you use a live CD and try to read those folders?

---

### Post by dino99 on 2015-04-03
who own that folder ? (right click on the icon)
note that i've never seen bleachbit creating a folder, but skype could be the devil

---

### Post by bashiergui on 2015-04-03
> **konrad6 said:**
> I can't even open the folder as root, it tries to load for about an hour but then freezes on me (and I have a 7200rpm drive + i5), I tried several times with the same result... I managed to open a similar folder under a previous installation, and saw as I said a massive number of empty text files with scrambled titles....That's nice but we really need to know what's in _these_ files. Open a terminal and type ```
sudo su
cat /path/to/salted/file
``` Post back with what is in the file. Also post the date of the oldest text file in that folder.

---

### Post by n00b123 on 2015-04-03
What is the output of the command bellow??

```
ls -la $HOME/M-nUADxgcy | more 
```

---

### Post by leclerc65 on 2015-04-05
> **konrad6 said:**
> I can't even open the folder as root, it tries to load for about an hour but then freezes on me (and I have a 7200rpm drive + i5), I tried several times with the same result... I managed to open a similar folder under a previous installation, and saw as I said a massive number of empty text files with scrambled titles....

Has anybody else used Bleachbit as root with the same result?
I do use Bleachbit as root.
I had similar problem with different bizarre file names, the days I linked my home folders to my data partition formatted in NTFS. Names that I cannot remember now, because I deleted them all, but lot of them are
.AppleDouble, .rmtdbsdir... or something like that. Some that can be opened as root, some spew out encoding error when opened. I have since reformatted the partition as ext4, and the problem stopped.
For the life of me, I still cannot find out who put  these .Apple* folders on a Windows/Linux dual boot computer, I do own one iPad and one mini iPad.

---

### Post by cogset on 2015-04-05
> **leclerc65 said:**
> I do use Bleachbit as root.
For the life of me, I still cannot find out who put  these .Apple* folders on a Windows/Linux dual boot computer, I do own one iPad and one mini iPad.

Well... did you ever connect each of the two gizmos to your computer?

---

### Post by leclerc65 on 2015-04-05
Yes, I did authorize one iPad to print through the PC, that's not an excuse to put these folders in my computer, especially several of the folders contain just Informations, not media files like MP3, MP4...
It looks like somebody knew strategically where to put these files/folders (hidden - to boot).
I cleaned that iPad and reinstalled all apps.

---

### Post by konrad6 on 2015-04-06
> **n00b123 said:**
> What is the output of the command bellow??

```
ls -la $HOME/M-nUADxgcy | more 
```

> $ sudo ls -la $HOME/M-nUADxgcy | more
[sudo] password for user: 
total 3296336
drwxr-xr-x  2 root root 153202688 mar 24 21:45 .
drwx------ 32 user user     12288 apr  6 19:39 ..
-rw-------  1 root root         0 mar 24 21:38 000rBA                           
                                                                                
                
-rw-------  1 root root         0 mar 24 21:38 00225W                           
                                                                                
                
-rw-------  1 root root         0 mar 24 21:38 00_2Gu                           
                                                                                
                
-rw-------  1 root root         0 mar 24 21:44 002P9x                           
                                                                                
                
-rw-------  1 root root         0 mar 24 21:38 0033K2                           
                                                                                
                
-rw-------  1 root root         0 mar 24 21:42 003Dc5                           
                                                                                
                
-rw-------  1 root root         0 mar 24 21:38 003Om5                           
                                                                                
                
-rw-------  1 root root         0 mar 24 21:42 005Zbv                                                                                                   
                        
-rw-------  1 root root         0 mar 24 21:44 006Av6                                                                                                   
                        
-rw-------  1 root root         0 mar 24 21:43 0_06zq                                                                                                   
                        
-rw-------  1 root root         0 mar 24 21:39 007isY                                                                                                   
                        

And it keeps going long after that...

---

### Post by fugu2 on 2015-04-18
Have you done a file system check recently? It looks like something might be corrupted, maybe a mis-configured program, maybe a bad file system, maybe not. I think the command is e2fsck, but you might wanna read the man e2fsck before you run it, cause I'm not that familiar with it.

---

### Post by user_of_gnomes on 2015-04-19
What's the S.M.A.R.T-status on your hard drive?

---

### Post by konrad6 on 2015-04-20
> **fugu2 said:**
> Have you done a file system check recently? It looks like something might be corrupted, maybe a mis-configured program, maybe a bad file system, maybe not. I think the command is e2fsck, but you might wanna read the man e2fsck before you run it, cause I'm not that familiar with it.

I haven't and I can't run it on a mounted drive, and I don't think I could run it from a live boot either since I have both full disk encryption and encrypted home...

---

### Post by konrad6 on 2015-04-20
> **user_of_gnomes said:**
> What's the S.M.A.R.T-status on your hard drive?

Disk Utility says everything is OK, and the drive isn't very old, only been powered on for 11 months, never had any issues other than this

---

### Post by NoWayWin8 on 2015-06-09
> **konrad6 said:**
> I have both full disk encryption and encrypted home...  Well there's your answer.

---

### Post by Habitual on 2015-06-11
> **konrad6 said:**
> I've used Bleachbit as root to wipe free space, would that be a possible answer?IMNSHO it is the exact answer!
but an encrypted home? IDK what the result of that env would be.
bleachbit is useless</opinion>

but if is due to the encrypted home, wouldn't that folder be accessible to you? I think so.
> **konrad6 said:**
> I have opened it as root, it' just empty .txt files  with titles like "nffearewtr2" or "qegrbvc132r," several hundred  thousand of them. Bleachbit.

---

