---
title: "to internet security or no??"
date: 2011-01-04
forum: Security
---

### Post by HappyLinux on 2011-01-04
OK, this question has been done to death, but the answers are direct and don't give the required answer.

In Linux, when dual-booting a system with Windows, or Mac for that matter, do you need an Internet security suite or individual packages?

I know Linux is relatively immune to Viruses, malware and spyware, but I do know that you need a firewall.

There are 2 things here.

What firewall is best under Linux?

Even though Linux is immune to Viruses, it can still be a carrier. Is there an AV program to check for viruses before they reach Windows/Mac?

---

### Post by mail2345 on 2011-01-04
Uncomplicated firewall is a good starting firewall.
[https://help.ubuntu.com/community/UFW](https://help.ubuntu.com/community/UFW)
The command line interface isn't that hard.

As for an antivirus to scan for win/mac viruses, see this wiki page:
[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

---

### Post by nomko on 2011-01-04
> **HappyLinux said:**
> OK, this question has been done to death, but the answers are direct and don't give the required answer.
 
In Linux, when dual-booting a system with Windows, or Mac for that matter, do you need an Internet security suite or individual packages?
 
I know Linux is relatively immune to Viruses, malware and spyware, but I do know that you need a firewall.
 
There are 2 things here.
 
What firewall is best under Linux?
 
Even though Linux is immune to Viruses, it can still be a carrier. Is there an AV program to check for viruses before they reach Windows/Mac?
 
I don't believe a firewall is the issue here. Looking at your post i believe there's a higher need for an anti-virus application like clamav (with clamtk for the GUI). If you do have a dualboot system with Windows and the Windows partition is mounted in Ubuntu, all virusses have free access to that partition. It is true that Linux is immune to Windows virusses, it does not free you from virusses. When you receive an email from a Windows users and it contains an attachement holding a virus, the virus will not effect your Linux/Ubuntu system, but the virus is present! When you forward that email, you not only forward the text but also the attachment holding the virus. 
 
But what happens when you save the attachment? It could infect the Windows partition when you open the attachment later under Windows. Even so, it could infect your Windows partition when the virus itself is actively seeking for a Windows partition. And there's the danger for Linux users. When you send/receive email which holds a virus, if you're running a fileserver or mailserver, exchanging files with Windows users. As a Linux user you will never know if a file is holding a virus since Linux is immune to Windows virusses, there's no noticeable effect. No program which tells you there's a virus on your system of in some file.
 
It's recommended to use a anti-virus application when you exchange files with Windows systems and/or users. Not only to protect your own mailtraffic or file exchange, but also to protect the Windows users for getting infected files and/or mails from you.
 
Also MacOS is immune for Windows virusses since MacOS is a Unix operating system and Linux is a Unix-based operating system.
 
On my personal site there's a whole page about anti-virus applications. Only it's in the Dutch language. But it gives you some idea's about which applications are available for Linux.

---

### Post by handy on 2011-01-04
You only need to use anti-virus software if you are serving to Windows machines.

I believe that Ubuntu comes with the firewall preconfigured, so you can just use it & forget about security problems.

If you need to or want to for the fun of it you can set up a dedicated 24/7 firewall/router machine. I use an old PIII, though a PII will cost less than the $54-/year that the headless PIII does.

IPCop is my choice, it works faultlessly for me, there are other options that a search will bring up for you if you are interested.

---

### Post by HermanAB on 2011-01-04
Howdy,

Linux != Windows

There is no need to install third party junkware as a band-aid over security problems the way one has to do with Windows.

Relax and enjoy your Linux system.

---

### Post by HappyLinux on 2011-01-04
The Ubuntu Uncompicated Firewall actually looks complicated. I'm no techie when it comes to command line.

As for ClamAV, dang, another command line program.

---

### Post by nomko on 2011-01-04
> **HappyLinux said:**
> The Ubuntu Uncompicated Firewall actually looks complicated. I'm no techie when it comes to command line.
 
As for ClamAV, dang, another command line program.
 
Yes and no ;)
Without **clamtk **it is a command line program.
With **clamtk** you have a GUI.

---

### Post by bodhi.zazen on 2011-01-04
As has been pointed out, this is not Windows and you do not need any of those things (antivirus or firewall).

ufw is trivial, open a terminal and enter

```
sudo ufw enable
```

I personally do not subscribe to the theory that you should run antivirus on LInux "just because" you might be a "carrier". These tools typically only yield false positives and I do not believe you can in any way protect windows users without educating them on how to secure Windows.

And please read the security sticky, it answers all your questions in more detail with references.

---

### Post by nomko on 2011-01-05
> **bodhi.zazen said:**
> As has been pointed out, this is not Windows and you do not need any of those things (antivirus or firewall).
 
ufw is trivial, open a terminal and enter
 
```
sudo ufw enable
```
 
I personally do not subscribe to the theory that you should run antivirus on LInux "just because" you might be a "carrier". These tools typically only yield false positives and I do not believe you can in any way protect windows users without educating them on how to secure Windows.
 
And please read the security sticky, it answers all your questions in more detail with references.
 
Maybe not for personal use, but if you have a file server or a mailserver, you better need a anti-virus tool. Even so if you exchange a lot of files with Windows users it might be very usefull.
 
However, it's your own choice not using a anti-virus or a firewall. But remember and don't forget, a firewall will never stop virusses because it can't stop or block virusses! It only prevents unwanted access to your system.

---

### Post by bodhi.zazen on 2011-01-05
> **nomko said:**
> Maybe not for personal use, but if you have a file server or a mailserver, you better need a anti-virus tool. Even so if you exchange a lot of files with Windows users it might be very usefull.

I never claimed there was no use for antivirus scanning and I agree with your two user cases. Another user case would be if you are running wine.

But that is not the same thing as running antivirus on a Linus Desktop simply because you might be a carrier. I have seen nothing but false positives with this latter behavior.

My point is this is Linux, not Windows, and IMO antivirus not relevant to the vast majority of people running an Ubuntu Desktop.

These are tools and one need to understand how to use them. Do you drive your car with a parachute "just in case" you drive off a cliff ? How about a life vest just in case you drive into a large body of water ? Those tools would be appropriate in a plane or boat mind you  =)

---

### Post by chrisx on 2011-01-05
Myself, I have never run anti-virus on a personal Linux machine. Though this has recently changed because the best anti-virus program in the world, Eset NOD32, is beta-testing their new Linux version, with downloads here: **[http://beta.eset.com/linux/]("http://beta.eset.com/linux/")**.

Installation is a snap, just download and ...

```

chmod u+x  ueav.i386.en.linux
sudo ./ueav.i386.en.linux
sudo reboot
```

It scans files in real time (when mail reaches the file system), but I can also ask it to scan my Windows partition for "regular" threats, but also for ADS, or alternative data streams, which can be used by some root kits to hide from Windows itself. Very nice. I can also plug in a hard drive from another Windows computer and scan it with NOD32, using a **[Bytecc gadget]("http://www.byteccusa.com/product/adapter/BT-300/BT-300.htm")**.

I'm in Linux all the time; Windows is installed just so that, from time to time, I can use software that came with Windows-centric consumer electronics devices like old camcorders, for iTunes, for some games, etc.. Yet, I fix computers, too. So, NOD32 on Linux is great for me.

If it's a mail server, you can extend the mail server's role by installing anti-spam and anti-virus protection. A really easy method to accomplish everything with a little headache as possible is to use **[Zimbra]("http://www.zimbra.com/products/secure-email-anti-spam.html")** for a mail server. Or you can do it yourself for any reason, expecting to encounter increased complication for yourself.

As for the firewall, I have also never run one on a personal Linux  machine. There is a four-port router between my ISP router and my computer, so I'm using NAT or IP Masquerading. The device has firewall functionality, but I have no need to use it. But even if you do have have services running on a public IP address, you can usually secure them without a firewall. For example, you can increase SSH security with denyhosts.

```

sudo apt-get install denyhosts openssl-blacklist
sudo vim /etc/denyhosts.conf
```

Read though the denyhosts.conf file and tweak it to taste.

---

### Post by HappyLinux on 2011-01-05
Eset NOD32 on Linux... sounds good.

I will be buying NOD32 Internet security for 3 computers soon. I use the 3 user licence because I install it on 3 computers, mine, dad's and sister's machines.

Currently we're running Webroot, but it's got just over 60 days (as of this posting) left of registration.

I agree that I don't really think that I need an AV program under Linux, even if I will be dual-booting with Win7. I'm too cautious on what websites I go too. The thing is, that no matter which Security program you're running, and no matter how careful you are, something will always slip by.

I remember years ago. I got woken up at 3am to sort out my dad's computer. He couldn't do anything whilst Outlook Express was mass mailing a dozen infected emails to each person in his address book.

He had got infected by a virus that hit the internet not 2 hours before hand. It took 2 days for AV companies to create definitions against it.

I had to physically disconnect the modem cable to stop it and finally gain control.

One downside is, that I may actually open an account on Facebook. That would mean that I become more open to viruses and malware from Facebook alone. The amount of times I have to clean out viruses/malware from my dad and sis' computers due to facebook is stupid. something like 1 a month.

So I guess that explains why I'm just wanting to take precautions.

---

### Post by chrisx on 2011-01-05
I understand.

I great combination I use for my family's computers is NOD32 and the purchased version of Malwarebytes Anti-malware. Both of them update themselves and scan in real time. They work in Windows Safe Mode, too.

Many peaceful years have passed without having to remove malware from my family's Windows computers.

:)

Chris

---

### Post by carlo bolzonello on 2011-01-06
Hi All,

Just my few cents here, don't be to complacent with the fact that you are using Linux or a non windows operating system, malware is now becoming something that is targeting everyone, irrespective of OS, just a fact for you, the most compromised web servers are all running Apache on them. All-ways remember that we no longer work only with a specific OS, we share data via usb devices etc and you can infect widows or mac machines, so just a word of caution, don't be complacent, you do need to secure your device using Anti-Virus and firewalls guys, i have seen Linux devices severely compromised.

Just my few pennies

---

### Post by HappyLinux on 2011-01-06
> **carlo bolzonello said:**
> Hi All,

Just my few cents here, don't be to complacent with the fact that you are using Linux or a non windows operating system, malware is now becoming something that is targeting everyone, irrespective of OS, just a fact for you, the most compromised web servers are all running Apache on them. All-ways remember that we no longer work only with a specific OS, we share data via usb devices etc and you can infect widows or mac machines, so just a word of caution, don't be complacent, you do need to secure your device using Anti-Virus and firewalls guys, i have seen Linux devices severely compromised.

Just my few pennies

I was wondering whether to mention that sort of thing.

When Microsoft brought out Vista, the popularity of Windows dropped, and people were shifting more towards Linux and Macs. Although Win7 has recovered some of the losses from the Vista fiasco, it may take a while to completely recover.

Yes, I agree. Viruses/malware/etc are becoming more OS broad-baring, and sophisticated. That is one of the reasons why I was asking about protection under Linux.

---

### Post by HugoSerrano on 2011-01-06
Best protection for the machine it's user education.
Like bodhi.zazen[[COLOR=#980101]****[/COLOR]]("http://ubuntuforums.org/member.php?u=89054") says, theres no need to use AV software in your desktop. 

For Firewall... you may try firestarter. It's a easy gui for iptables.

---

### Post by spynappels on 2011-01-06
> **HugoSerrano said:**
> For Firewall... you may try firestarter. It's a easy gui for iptables.

Just be careful as Firestarter is no longer maintained, for normal firewall use UFW or GUFW if you want a graphical front-end is fine. Definitely do NOT try to use UFW and Firestarter together as they mess each other up.

---

### Post by HappyLinux on 2011-01-08
That's ok, I'm no good with IPs anyway.

---

### Post by markcoronado on 2011-01-10
> **chrisx said:**
> Myself, I have never run anti-virus on a personal Linux machine. Though this has recently changed because the best anti-virus program in the world, Eset NOD32, is beta-testing their new Linux version, with downloads here: **[http://beta.eset.com/linux/](http://beta.eset.com/linux/)**.

Installation is a snap, just download and ...

```

chmod u+x  ueav.i386.en.linux
sudo ./ueav.i386.en.linux
sudo reboot
```It scans files in real time (when mail reaches the file system), but I can also ask it to scan my Windows partition for "regular" threats, but also for ADS, or alternative data streams, which can be used by some root kits to hide from Windows itself. Very nice. I can also plug in a hard drive from another Windows computer and scan it with NOD32, using a **[Bytecc gadget]("http://www.byteccusa.com/product/adapter/BT-300/BT-300.htm")**.

I'm in Linux all the time; Windows is installed just so that, from time to time, I can use software that came with Windows-centric consumer electronics devices like old camcorders, for iTunes, for some games, etc.. Yet, I fix computers, too. So, NOD32 on Linux is great for me.

If it's a mail server, you can extend the mail server's role by installing anti-spam and anti-virus protection. A really easy method to accomplish everything with a little headache as possible is to use **[Zimbra]("http://www.zimbra.com/products/secure-email-anti-spam.html")** for a mail server. Or you can do it yourself for any reason, expecting to encounter increased complication for yourself.

As for the firewall, I have also never run one on a personal Linux  machine. There is a four-port router between my ISP router and my computer, so I'm using NAT or IP Masquerading. The device has firewall functionality, but I have no need to use it. But even if you do have have services running on a public IP address, you can usually secure them without a firewall. For example, you can increase SSH security with denyhosts.

```

sudo apt-get install denyhosts openssl-blacklist
sudo vim /etc/denyhosts.conf
```Read though the denyhosts.conf file and tweak it to taste.

I'm using Ubuntu 10.04 and I downloaded the beta Nod32 to my download folder & I'm having problems getting it to install.

I ran your codes & here are my results.

mark@mark-laptop:~$ chmod u+x  ueav.i386.en.linux
chmod: cannot access `ueav.i386.en.linux': No such file or directory
mark@mark-laptop:~$ sudo ./ueav.i386.en.linux
[sudo] password for mark: 
sudo: ./ueav.i386.en.linux: command not found
mark@mark-laptop:~$ 

Does anyone know what I'm doing wrong?

---

### Post by bodhi.zazen on 2011-01-10
cd ~/Download

---

### Post by markcoronado on 2011-01-10
> **bodhi.zazen said:**
> cd ~/Download

I'm sorry but I don't understand your response, cd ~/Download

I'm new to Ubuntu so I need an answer for dummies.

---

### Post by bodhi.zazen on 2011-01-10
You need to 'cd' or change directory into the location you downloaded the file.

[http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by uRock on 2011-01-10
Edit: Was 10 seconds too late.

---

### Post by markcoronado on 2011-01-10
> **bodhi.zazen said:**
> You need to 'cd' or change directory into the location you downloaded the file.

[http://linuxcommand.org/](http://linuxcommand.org/)

Lets see if I understand you correctly.

chmod u+x  ueav.i386.en.linux
sudo ./ueav.i386.en.linux

Do I need to change linux to Downloads since that is where I downloaded the file to?

---

### Post by bodhi.zazen on 2011-01-10
> **markcoronado said:**
> Do I need to change linux to Downloads since that is where I downloaded the file to?

yes, you need to cd into the directory where your downloaded the file, then run those commands.

Since you are new to Linux I should remind you you almost certainly do NOT need antivirus, this is not Windows, and I have run Linux for a long long time without ever encountering a virus.

---

### Post by markcoronado on 2011-01-10
> **bodhi.zazen said:**
> yes, you need to cd into the directory where your downloaded the file, then run those commands.

Since you are new to Linux I should remind you you almost certainly do NOT need antivirus, this is not Windows, and I have run Linux for a long long time without ever encountering a virus.

I guess I'm doing something wrong.

Here is my results when trying to cd

mark@mark-laptop:~$ cd ~/Download
bash: cd: /home/mark/Download: No such file or directory
mark@mark-laptop:~$

Looks like I missed the s in Downloads.
New results are.

mark@mark-laptop:~$ cd ~/Downloads
mark@mark-laptop:~/Downloads$ chmod u+x  ueav.i386.en.linux
chmod: cannot access `ueav.i386.en.linux': No such file or directory
mark@mark-laptop:~/Downloads$ sudo ./ueav.i386.en.linux
[sudo] password for mark: 
sudo: ./ueav.i386.en.linux: command not found
mark@mark-laptop:~/Downloads$

---

### Post by cariboo on 2011-01-10
Are you sure the file is in the Downloads directory? you can use ls, or dir to list the files in the directory. If the file is in the directory, you may be mistyping the name. What I learned a long time ago, was to highlight the complete file name with my mouse, then type the command, and then press the mouse wheel to paste the file name at the end of the line, instead of typing it out.

---

### Post by uRock on 2011-01-10
If you know where the file downloaded to, then it may be easier to just move it to your home folder. Once in the home folder you will not have to change directories to find the file.

---

### Post by markcoronado on 2011-01-11
> **uRock said:**
> If you know where the file downloaded to, then it may be easier to just move it to your home folder. Once in the home folder you will not have to change directories to find the file.


I moved the file from the downloads folder to the home folder, then I c&p the file name like cariboo 907 suggested & ran these commands in terminal.

chmod u+x  /home/mark/ueav.x86_64.en.linux
sudo ./home/mark/ueav.x86_64.en.linux

Results are,
mark@mark-laptop:~$ chmod u+x  /home/mark/ueav.x86_64.en.linux
mark@mark-laptop:~$ sudo ./home/mark/ueav.x86_64.en.linux
[sudo] password for mark: 
sudo: ./home/mark/ueav.x86_64.en.linux: command not found


I must still be doing something wrong.

---

### Post by bodhi.zazen on 2011-01-11
> **markcoronado said:**
> I moved the file from the downloads folder to the home folder, then I c&p the file name like cariboo 907 suggested & ran these commands in terminal.

chmod u+x  /home/mark/ueav.x86_64.en.linux
sudo ./home/mark/ueav.x86_64.en.linux

Results are,
mark@mark-laptop:~$ chmod u+x  /home/mark/ueav.x86_64.en.linux
mark@mark-laptop:~$ sudo ./home/mark/ueav.x86_64.en.linux
[sudo] password for mark: 
sudo: ./home/mark/ueav.x86_64.en.linux: command not found


I must still be doing something wrong.

No offense, but I highly suggest you read this link:

[http://linuxcommand.org/](http://linuxcommand.org/)

As it goes through the basics of the bash shell.

There is a difference between ./home/.... and /home

Try again without the leading .

For further information, see the link I gave you.

Again, I will also tell you, this is not Windows and you do not need antivirus scanning.

---

### Post by markcoronado on 2011-01-11
> **bodhi.zazen said:**
> No offense, but I highly suggest you read this link:

[http://linuxcommand.org/](http://linuxcommand.org/)

As it goes through the basics of the bash shell.

There is a difference between ./home/.... and /home

Try again without the leading .

For further information, see the link I gave you.

Again, I will also tell you, this is not Windows and you do not need antivirus scanning.


Thanks for your help bodhi.zazen & everyone else that pitched in.

Removing the . worked.

I didn't install it yet & would like to know why I don't need it.
I here some say you do need AV & some say you don't (it's confusing)
I'm used to windows & like to be protected.
I just want to be sure no one can get my passwords ( I use Skipper) or other info like account or credit card info if I were to use my Ubuntu partition for purchasing or banking purposes.
I guess without AV I feel like the door is left open.
I do have the Firewall activated.

One more question.
Every time I need to install a program will I need to use the same process?
Is there a way to do it like in windows by clicking on the installer icon?

---

### Post by bodhi.zazen on 2011-01-11
> **markcoronado said:**
> Thanks for your help bodhi.zazen & everyone else that pitched in.

Removing the . worked.

I didn't install it yet & would like to know why I don't need it.
I here some say you do need AV & some say you don't (it's confusing)
I'm used to windows & like to be protected.
I just want to be sure no one can get my passwords ( I use Skipper) or other info like account or credit card info if I were to use my Ubuntu partition for purchasing or banking purposes.
I guess without AV I feel like the door is left open.
I do have the Firewall activated.

One more question.
Every time I need to install a program will I need to use the same process?
Is there a way to do it like in windows by clicking on the installer icon?

You do not need antivirus because Linux is not windows.

There are no know active viruses in Linux. In Linux, the fix to viruses is a patch to the code, thus your system was patched to the known viruses long ago.

This is not the case in Windows where the code goes unpatched, thus in Windows you need a third party product.

99.99 % of those advocating antivirus for Linux are either:
[list][*]New Linux users[*]Antivirus marketing companies[/list]

The antivirus companies are selling you a product, and what you installed is a trial product. They are playing on your fears and do not provide any education.

Experienced users do no use antivirus scanning on a Desktop.

If you feel you need antivirus, you should stay with AVG which is in the repos.

"valid" user cases for linux antivirus would be those running mail servers or file sharing (Samba) with Windows clients.

I suggest you read:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://ubuntuforums.org/showthread.php?t=1477662](http://ubuntuforums.org/showthread.php?t=1477662)

[http://ubuntuforums.org/showpost.php?p=9265657&postcount=9](http://ubuntuforums.org/showpost.php?p=9265657&postcount=9)

Those posts are all stickies for a reason.

---

### Post by markcoronado on 2011-01-11
Thanks for the info bodhi.zazen.
I check out the links you recommended.

---

### Post by HappyLinux on 2011-01-20
Because this thread has now moved on, I've now marked it as solved as there is no longer any need to continue adding towards it. If anyone would like to mention anything more, then by all means, proceed.

---

### Post by HappyLinux on 2011-01-20
Because this thread has now moved on, I've now marked it as solved as there is no longer any need to continue adding towards it. If anyone would like to mention anything more, then by all means, proceed.

---

