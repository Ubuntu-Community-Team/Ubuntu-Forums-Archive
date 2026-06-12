---
title: "how can i scan a second computer."
date: 2008-10-11
forum: Security
---

### Post by Fertech on 2008-10-11
I have a computer that got a virus. i don't want to reinstall windows. the other computer is good. first of all is it safe for me to install the hard drive that got a virus to the other computer if will it get infected too. second how can i scan the second hard drive (SLAVE) with Linux Ubuntu from the terminal. i went to Microcenter they told me to back up my files and reinstall the OS, i told Microcenter, so every time i get hit i am going to reinstall windows, and told him what about if i back up the virus too. some people just don't get it. so can some one help me.

---

### Post by pietjanjaap on 2008-10-11
Search with google for a bootcd, bootable cd, then you find up to date virusscanners on these cd's, then you can scan the harddisk.


If a pc is infected then it is not a good idea, not to do a fresh install.


Learn how to protect your windows pc, a firewall and virusscanner is not enough, so search for site's about this, and learn, then you do not have to this what you are now doing.

---

### Post by Kinstonian on 2008-10-11
What kind of "virus" do you have?  pietjanjaap's suggestion about using a LiveCD with AV software installed is a good one.

You recognized that if you backup your files you could also be backing up the virus.  You should also recognize that if you try to recover without reformatting, you might miss something like a backdoor or other file infected with the virus, and still be infected.

The decision on whether to reformat should be made after understanding the pros and cons, and be based on your ability to recover from an incident.

---

### Post by cariboo on 2008-10-11
To answer your question, yes you can put the hard drive in your Ubuntu computer and scan it for viruses, As you may have found out Windows programs generally don't work with Linux so you don't have to worry about infecting it.

You can install clamav and clamtk if you prefer a gui and scan the drive for viruses. Run frshclam before you scan,as you will have to update the virus signatures. to run freshclam open a terminal and type:

```
sudo freshclam
```

Jim

---

### Post by randy78 on 2008-10-11
Kinstonian is right... We need to know what kind of virus you have (what does it do, can you boot etc...) and after we have some more information, we can come up with a plan that is tailored for you.

The Ultimate Boot CD [http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/") is an awesome free boot disk that comes with several anti-virus applications pre-installed, just download the iso, burn it, insert it into your CD/DVD drive and reboot.

The main thing to remember is that most anti-virus applications rely on blacklists to check against. If you are infected with a virus that isn't listed in the blacklist, then you're still going to have trouble.

Bottom line is that once you've been infected, you can never be 100% sure that your anti-virus has found everything. 

When I'm doing recovery for clients who have been infected, I transfer their data (documents, music, pictures, etc.) to an external hard drive.

Then I boot into a computer that has Ubuntu installed and scan each file with Clam before I transfer them back to the Windows partition.
Please note that after I get all of their important data off of the Windows drive, I wipe it using DBAN (quick wipe) and re-install Windows.
This way I know that the threat has been neutralized.
(If you are using a dual boot setup, then it's as easy as scanning that partition with Clam from within Ubuntu)

Take Care

---

### Post by Fertech on 2008-10-14
I don't no what kind of virus i have, but all i know all this popups keep on popping out and i can't seem to close some of them. one of the popups says that my computer is infected and to scan my computer with there scanner. but they want me to pay to scan my computer. i reject that offer i did think about when i back up my files, i might back up the virus, and another thing is that with windows i have the restore and the virus can copy it self to the restore, so if i scan my pc then restore i can infected my computer again. if i find out what kind of virus i have i will let you know.

---

### Post by Fertech on 2008-10-14
how do i use the clam scanner. i have in my computer 2 operating system ubuntu and windows xp. i want to scan this computer too, but both os.

---

### Post by Kinstonian on 2008-10-14
Fertech, it sounds like spyware to me.  This isn't really a Windows help forum, so I recommend you post HijackThis logs on the [Security Forums](http://www.security-forums.com/viewforum.php?f=48).  The people there are very familiar with spyware, and should be able to help you recover from this without reformating.

---

### Post by stinger30au on 2008-10-14
first thing i owuld be doing is running smitfraudfix over it

[http://siri.geekstogo.com/SmitfraudFix.php](http://siri.geekstogo.com/SmitfraudFix.php)

---

### Post by Fertech on 2008-10-14
yes i know some code rm stands for remove. i was reading about that, some people don't know and they type rm and what they do is delete dir files, but thanks anyways

---

### Post by DirtDawg on 2008-10-14
I have scanned my Windows drive from Ubuntu before using [Avast virus scanner]("http://www.avast.com/eng/avast-for-linux-workstation.html"). You will need to register, but otherwise it's free for personal use. I find ClamAV to be painfully slow, unintuitive, and I have read that their lack of paid staff can mean stale virus definitions. 

Of course, the hardest part might be getting your Ubuntu box to see and connect to your Windows box. But once you do, you should be able to scan the Windows box like a normal hard drive. 

My experience with Avast has been good. I ran it on my Windows hard drive and it found viruses my Norton could not find and Windows Explorer couldn't even see! I had to erase the virus files using Ubuntu. Who knows how many months, or years, they had been hiding out undetected.

Good luck

---

### Post by WWSmith36 on 2008-10-14
The best CD I own is the Ulitmate Boot CD for Windows.  It has all the tool you would ever need to fix a windows machine.  Unfortunately you just can´t download it, you have to build it with BartPE, its easy to do and totally worth it.  

You will have to run not only AV but SpyBot S&D as well to remove that web hijacker.  After you discover what it is, google it, and you may find that you have to repair some damage it may have caused.

Hope this helps

---

### Post by randy78 on 2008-10-15
I second the smitfraudfix, as well as SpyBot S&D...

I wrote a tutorial a ways back on installing Avast in Ubuntu:
[http://ubuntuforums.org/showthread.php?t=685514]("http://ubuntuforums.org/showthread.php?t=685514")

Good Luck!

---

