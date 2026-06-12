---
title: "New to Linux but already in love"
date: 2010-11-01
forum: The Cafe
---

### Post by the-noob on 2010-11-01
Hi, my first post just to say hello!

Having used Microsoft since windows 95 I have finally moved over to Linux, more so Ubuntu 10.10.
Vista really put a bad taste in my mouth and while Windows 7 was a big improvement.. i have finally got sick of Microsoft bloat-ware and made the move.

What prompted the move was buying a Acer Aspire Revo R3610 Desktop fpr the home, not exactly a power house of a machine but it's wired up to the TV via HDMI and is solely used for browing the web and streaming movies... pre-installed win7 and it was absolutely sh*t. 3 months i lived with it and hated it. Thought i'd give Linux a bash having last used Linux when i was at uni in 2000.

I first installed it to test on my old gaming computer which was last used in 2005: 
2Ghz AMD single core
2gb DDR1
40GB HDD  
and it runs fast than XP ever used to!!

I then decided to install it on the Acer... BRILLIANT... fast as lightening, all features work.. all drivers automatically found!.. I LOVE IT

I run small web development / design company and I have spent all week replacing the systems here with Ubuntu 10:10... the only minor problem was configuring the high end machines to get the dual monitors to work using ATI Raedeon HD 4800 cards. All it took was letting Ubuntu take over, find, download and install the drivers and everything works great!!!

only two minor negatives, both of which are not Ubuntu's fault
1) no Notepad++
2) no sage50

Sadly negative number 2 means there will always be one machine in the office with windoz to run Sage, until Sage develop for Linux :(

If anyone knows of any good alternatives.. please let me know!

oh and the PS3 at home cant see the Ubuntu powered acer, but im sure there is a work around.. not had time to research... not that it matters as all my media is on a network HDD.

Thanks
M
( i know the title says 'new'.. but i last used Red Hat in 2000... so pretty much new to linux.. or as good as)

---

### Post by Lancro on 2010-11-01
Theres is no notepad++ but there is Bluefish, give it a try.

---

### Post by the-noob on 2010-11-01
great.. will give it a bash.. thanks

---

### Post by CraigPaleo on 2010-11-01
> oh and the PS3 at home cant see the Ubuntu powered acer, but im sure there is a work around.. not had time to research... not that it matters as all my media is on a network HDD.

pms-linux should solve this. It's not in the repos but there are instructions here. [https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

---

### Post by kaldor on 2010-11-01
Instead of Notepad++, try Kate. It's a pretty advanced editor.

Remember this is Linux. We have editor wars :)

---

### Post by Spice Weasel on 2010-11-01
Notepad++...

Loads of alternatives!

Kate, Geaney, Vi, Vim, Nano, Emacs, Joe, etc.

---

### Post by Oxwivi on 2010-11-02
Don't use 10.10 at your company, better use 10.04 LTS, bit safer and less likely to get broken than 10.10.

---

### Post by mips on 2010-11-02
> **the-noob said:**
> 

only two minor negatives, both of which are not Ubuntu's fault
1) no Notepad++
2) no sage50

Sadly negative number 2 means there will always be one machine in the office with windoz to run Sage, until Sage develop for Linux :(

You don't say where you are from but I'm assuming UK as you mention Sage 50 and 'uni'.

Sage does have some products that run on Linux so maybe give them a call and see what's on offer. Here is one example [http://www.sageproerp.com/products/linux/](http://www.sageproerp.com/products/linux/)

Alternatively you could try running it in WINE [http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

Another option is to install VirtualBox, install a Windows guest OS and then install Sage on that and you can then run it in Seamless Mode so you don't even see the windows desktop.

---

### Post by Oxwivi on 2010-11-02
Can you please tell me more about this 'Seamless Mode'?

---

### Post by Oxwivi on 2010-11-02
Ah, just Googled Seamless Mode. It'd be great minus the taskbar.

---

### Post by Johnsie on 2010-11-02
I agree with you about Vista and 7. They are not fun to use.  I think Windows XP is the best Desktop operating system ever. I don't understand why they had to ruin that with Vista and 7.

---

### Post by mips on 2010-11-02
> **Oxwivi said:**
> Ah, just Googled Seamless Mode. It'd be great minus the taskbar.

You can hide the task bar using the auto hide function and access the menu with ctrl-esc.

Virtualbox also supports a headless mode but I'm not sure how that works.

---

### Post by undecim on 2010-11-02
> **mips said:**
> You can hide the task bar using the auto hide function and access the menu with ctrl-esc.

Virtualbox also supports a headless mode but I'm not sure how that works.

It wouldn't work with GUI apps. Headless means no mouse, no keyboard, and no monitor.

If the taskbar is a problem, you can always install an alternate shell on the guest machine. I'm there is a minimalist one out there that does what you need.

---

### Post by mamamia88 on 2010-11-02
PS3 media server for the ps3.  don't even need to install it just download the tarball extract and run it

---

### Post by Hells_Dark on 2010-11-02
> **CraigPaleo said:**
> pms-linux should solve this. It's not in the repos but there are instructions here. [https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

+++
I'm in love with my Ubuntu/PS3/Pms-linux installation !
So easy, so usefull, so effective.

---

### Post by TheAnachron on 2010-11-02
Use jEdit. You will love it.

---

### Post by the-noob on 2010-11-02
wow... thanks for the replies and advice on editors, the PS3 and using 10.4 not 10.10. 
Why is 10.04 safe/more stable than 10.10?

and yes, im from the uk ;-)

Cheers

---

### Post by Oxwivi on 2010-11-02
10.04 is a LTS version, Long Term Support -  that is to say it's an extra stable version of Ubuntu with the features of older versions polished and debugged, to be used on the long term.

Hmm... okay, I don't think I am fit to explain this properly. Let me dig us some link you can refer to for a better understanding...

Start reading at the second section of this article: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

Basically, there's more quality assurance from LTS. While the latest releases has the best and latest things, LTS has best  and most stable of the things out there.

---

### Post by the-noob on 2010-11-02
cheers for the link! I think i understand..

10.4LTS is a version that is tried and tested, solid and most reliable and the one recommended for a stable home  and office environment

10.10 is based on 10.4 but with a few more bells and whistles. But these new sexy features are not as tried and tested and may cause reliability and security issues?... 

*or am i wrong?*

in other words, 10.10 for the home to mess about with and brows the web
10.4LTS at work for serious stuff? lol

I will use 10.4LTS  at work then, Thanks for the tip!!

I have started searching for a good alternative to winmerge... i have a lot of playing to do with editors and compare software! LOL

Anyone got any good links to accounting software / CRM software for Linux?
Will have a bash at using WINE but im new so would like to try some things designed for Linux. couldnt find anything form Sage on their website for LInux.. I have emailed tho

thanks to all once again!
M

---

### Post by Oxwivi on 2010-11-03
Yep. that's just what LTS is for. Later releases are more up to date with the latest technology, unlike LTS, but you wouldn't play around with latest technology at work will you? :P

Speaking of changing the work computers to Ubuntu, did you get a refund for the previous Windows OS? I'm not sure if it's possible with older systems, but I heard vendors are entitled to give you refunds for the Windows license in case you decide not to use it. Worth looking into it, since it's business after all.

Sorry, I can't help with the rest of your queries.

---

### Post by TNT1 on 2010-11-03
> **kaldor said:**
> 

Remember this is Linux. We have editor wars :)

Ah, right, permission to say LaTex?

---

### Post by C0derBear on 2010-11-03
> **the-noob said:**
> Will have a bash at using WINE but im new so would like to try some things designed for Linux.

For my un-asked-for 2c, I'd say use VirtualBox with XP installed into it for the must-be Windows apps. Run it full-screen on a secondary workspace and it ought to work out reasonably well. Depends on how display-intensive the apps are I guess, but in theory VirtualBox supports both 2D and 3D accelerated video drivers for Windows.

Regards.

---

### Post by the-noob on 2010-11-03
Seems i have hit my first Linux brick wall

While trying to download Gimp via Applications>Ubuntu Software Centre

i get the following warning 
"Requires installation of untrusted packages
The action would require the installation of packages from unauthenticated sources.

Then it fails... After further testing it Ubuntu Software Centre returns the same warning for anything i try to install.

I did find this page after searching
[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)
But it means nothing to me... if it tells you how to over come this problem.. then the solution goes over my head.

Can anyone help?

---

### Post by Oxwivi on 2010-11-03
Try to download from the Terminal (Ctrl + Alt + T or Applications -> Accessories -> Terminal) and paste this line:```
sudo apt-get install gimp
```
If it installs, all is fine, but if it doesn't, post the output in the Terminal. You can highlight and copy over there.

---

### Post by the-noob on 2010-11-03
Brilliant... installed in seconds
lol, that took me back to the 90's with MS-DOS style command window.. lol

Gimp works great.. Cheers

---

### Post by Oxwivi on 2010-11-03
Wowza, if that worked, I can't think of any problem at all - however, I am new as well, just taken up Ubuntu full time this year.

Dunno about MS DOS, didn't have the privilege (or misfortune) to use it. But the universal solution to any problem in Linux is the command line. :P

---

### Post by the-noob on 2010-11-03
learning curves... the steeper they are, the more fun they are ;-)

---

### Post by Oxwivi on 2010-11-03
Indeed it is - unless it's goes beyond steep into a wall without a platform. :P

Oh, and you'd do well to keep in mind, that you're not likely to get much support in the Community Cafe, for this is just the general discussion area of the forums. For best results post in the relevant section of the support forums. I say that, but it's nice to come here once in a while, since it's more popular if you know what I mean. ;)

---

