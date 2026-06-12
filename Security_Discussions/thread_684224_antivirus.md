---
title: "antivirus"
date: 2008-01-31
forum: Security Discussions
---

### Post by majikhotline on 2008-01-31
do i need to install an antivirus if i do alot of downloading?
and if so which is the best to have for ubuntu and what about adware and spyware for ubuntu?

thanks

---

### Post by PinkFloyd102489 on 2008-01-31
Here's the beauty of Ubuntu. Nothing. ;-)


No spyware, no adware, no viruses. Only 20 known viruses are known for Linux and they arent even in the wild. The only reason you would need anti-virus is if you are on a network with Windows computers.

---

### Post by aysiu on 2008-01-31
You don't need to worry about that stuff.

Read this for more details:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

---

### Post by jleaker01z on 2008-01-31
> **majikhotline said:**
> do i need to install an antivirus if i do alot of downloading?
and if so which is the best to have for ubuntu and what about adware and spyware for ubuntu?

thanks

Not really.  But if you want one you can install ClamAV or AVG.

Dont have to worry about adware/spyware. All thats Windows specific.

---

### Post by sunseeker888 on 2008-02-01
Bloody hell, I was doing my goolies looking anti spyware anti virus for ubuntu. Wow no need, I tried to downlad avg but it says wrong architecure i386. anyone have a clue

---

### Post by SunnyRabbiera on 2008-02-01
eh just stick to packages in the repository, it will suit you fine for the most part.

---

### Post by aysiu on 2008-02-01
> **sunseeker888 said:**
> Bloody hell, I was doing my goolies looking anti spyware anti virus for ubuntu. Wow no need, I tried to downlad avg but it says wrong architecure i386. anyone have a clue
Are you running Ubuntu as a mail server?

---

### Post by billgoldberg on 2008-02-19
Really, there is no need to run anti virus.

Those anti-virus programs for linux search for windows viruses.

---

### Post by Shippou on 2008-02-19
I installed Klamav... But then it does not do anything... Does not detect anything...

But then I'm not saying it's a failure. I'm just saying that it is unneeded.

If you really don't want to have viruses or other malware in your computer, I advise the following: (Disclaimer: I'm not an expert to this, just sharing my opinions)

1. Don't just accept cookies. Take time to review them, especially when coming from untrusted source. I'm not saying read them, but inspect them.
2. Don't visit porn sites, crack sites, keygen sites... the like. There is really nothing to crack or pirate on Linux.
3. Disable autoplay, even on CD ROMs. Portable media are a good source of malware (even during the time floppy disks are still popular). I once got the imgkulot virus on my computer because of autoplay (when I'm still Windows). But then, don't worry if you got a Windows virus in your computer. Even if you CLICK on it, it won't run. Just DON'T COMPILE ITS SOURCE CODE (if any) or run it in terminal.
4. Don't log in as root; use sudo instead.
5. Don't just download and download software; inspect it. In windows, freeware and shareware are the best sources of programs that contain malicious code. But then in Linux, it think the only programmers who will include malicious code in their applications are PARANOID.
6. If you want, you can disable automount.
7. You can also set multiple partitions. In my case, I set up a separate partition of 3GB for the root. I know this is kind of small; but then, who cares? :lol: Well, if you got a lot of partitions, you can reformat only a specific partition if something goes wrong without reformatting the whole drive (keep backups of your data, of course).
8. Lastly, read about malware. Why malware? Most people know only viruses as malicious software, but then there are many others, including spyware and trojans; also worms and rootkits too. A good reference is [www.viruslist.com](www.viruslist.com).

Just enjoy your Linux experience; don't worry about malware. Well in the first place it all depends on the user if he/she will get malware on his/her computer... :)

---

### Post by OrangeCrate on 2008-02-19
> **majikhotline said:**
> 
do i need to install an antivirus if i do alot of downloading?
and if so which is the best to have for ubuntu and what about adware and spyware for ubuntu?


In addition to aysiu's sound advice (and others), here's another good read on the need for an antivirus program on Ubuntu:

**The Truth About Linux and Viruses**

> 1. If you run Linux and only Linux, you do not need antivirus software. In its efforts to make Windows easier to use, Microsoft simplified the process of running executables under its operating system many years ago. Not only can a user launch a program by clicking an e-mail attachment, but it's possible for an executable to launch automatically just by hitting the preview pane of some email packages, including older versions of Outlook and Outlook Express. Scot's Newsletter Forums member Nathan Williams has provided an excellent FAQ for the All Things Linux forum explaining why Linux when used alone does not need antivirus protection.

Under Linux the steps for launching an executable from an e-mail are separate, discrete steps. A user would have to read the email, save the attachment, give the attachment executable permissions, and then run the executable. And to be truly damaging, the latter two would have to be done as root &#8212; not something informed users would allow. (For more information see Ch- Ch- Changing File Permissions.)

2. If you dual boot Linux and Windows and get a virus-infected mail in Linux, it can NOT jump to your Windows partition. Nor can it spread over the local network to other systems. You can even store the attachment in your /home directory and open the zip or click the file, and it will be dead in the water. Windows executables won't run under Linux. Linux files need to be granted permission to become executable. And even then, it can't spread beyond the home folder. (This is also why Linux AV programs do not have a "live guard" module in them &#8212; the virus does not execute or move.) You could even leave a virus executable there as long as you wanted to without risk. Windows will not get infected, unless you deliberately copy the virus to your Windows partition.

3. If you dual boot, however, you better get a good antivirus program for Windows. Microsoft's operating system and its bundled applications, Outlook and Internet Explorer, offer users powerful functionality in their attempts to be easy to use and easy to update. As a result, it's all too easy for virus writers to exploit the same functionality in a malicious way. Don't leave them an opening. Install an antivirus program and keep it updated.

4. The only time you'll need a Linux antivirus program is if you're running a mail server. And that's just good social behavior. It's not to protect your Linux server or client computer so much as to make sure you don't pass a virus on to a Windows system.

Think about it this way: If you have two warehouses, and you use the first one to store cheese, are you going to place mouse-traps in the second one where you only store stainless steel? I mean, be reasonable, mice do not eat stainless steel! So don't let antivirus vendors make you unnecessarily paranoid.

[http://www.linuxclues.com/articles/21.htm](http://www.linuxclues.com/articles/21.htm)

---

### Post by -random on 2008-02-19
Even if you run a virus in ubuntu (via wine) the implications are minimal, at worst case scenario only a waste of a litte cpu time :P

this link put me to ease: [http://www.linux.com/articles/42031](http://www.linux.com/articles/42031) :popcorn:

---

