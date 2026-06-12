---
title: "Guide how to change WPS Office for Linux(Kingsoft Office Chinese ver.) to English"
date: 2013-03-03
forum: The Cafe
---

### Post by PANGERAN on 2013-03-03
I love Kingsoft office application, and i'm using it on my office's win os computer and android because for my opinion, this office more compatible with ms office 2003/2007 than openoffice / libreoffice.

Unfortunately, Kingoffice for linux (yes, Linux native, not Windows version with Wine! ;) )only available for chinese version (called: WPS Office for Linux, beta version and only available for ubuntu (deb) rpm packages and tar when i'm writing this thread)

Searching with google, finally we can change to english version (with easy steps):

1. First of course we must download WPS office for ubuntu / debian from [here]("http://community.wps.cn/download/") and double click to install it.

2. Open the application to make sure it works well on our ubuntu's laptop/pc (just what i did :D )

3. Close the application

4. Open terminal (ctrl + alt + t)

5. Type:
```
cd /opt/kingsoft/wps-office/office6/2052
```

6 Type:
```
sudo rm qt.qm wps.qm wpp.qm et.qm
```

Now, open the application again, and thank's God... the UI changes to english version :popcorn:

(Tested with ubuntu 11.04, and make sure this application works well on your ubuntu before you follow this steps)

Thank you ):P

---

### Post by Sayanvala on 2013-03-04
Thanks! This works really well! 

Just one thing... In your WPS, are you able to Insert>Equation or is the button also greyed out for you?

---

### Post by PANGERAN on 2013-03-04
Unfortunately, yes... :(
Data Chart and Equation menu greyed out...
Hmm... interesting...
Ok, I will check Kingsoft office for win os if those menus (Data Chart and Equation) greyed out too or not...

Update:
Yes, in Kingsoft office for windows, equation menu available (not greyed out), but, not build-in (uses third party equation editor).

---

### Post by Jinchuan Tang on 2013-03-16
They are researching on it by using the third party equation editor to support the Linux version, and they got some problems right now.

That response was posted by the developer Mr. jinchizhong of that company in *2013-3-15 19:00* .

His Chinese answer to this problem can be found on webpage:'http://bbs.wps.cn/thread-22361606-1-1.html'

If u guys have some ideas to make it possible, u can post it to me, i can send it to them to make this software much more better.

Also u may find it could not show the equation correctly. This is because of the font copyright.

U can install mtextra.ttf symbol.ttf webdings.ttf wingding.ttf wingding2.ttf wingding3.ttf to solve this problem.

The latest version can be downloaded from [http://community.wps.cn/download/](http://community.wps.cn/download/).

By the way, this software is very famous in China (it can be traced to late 1980s), based on their developing log, they have used Qt to redesign the GUI since 2010.They used GDI before.

I'm just a user.

---

### Post by PANGERAN on 2013-03-17
I'm wondering why official Kingsoft Office available for windows and android version BUT it doesn't make a linux version?? :confused:

---

### Post by Jinchuan Tang on 2013-03-18
I'm using opensuse 12.3 64 bits. It works fine. I installed the rpm one.

---

### Post by ibm450 on 2013-03-26
could someone post a simple way to install the missing ms fonts (wingdings etc) required by wps please. i have already installed the ms font installer for 12.04 but wps still reporting missing fonts

---

### Post by haaglin on 2013-03-28
> **ibm450 said:**
> could someone post a simple way to install the missing ms fonts (wingdings etc) required by wps please. i have already installed the ms font installer for 12.04 but wps still reporting missing fonts


Extract zip [ATTACH]240635[/ATTACH] to ~/.fonts

---

### Post by Tres99 on 2013-03-29
I've installed WPS 8.1.0 in Ubuntu 12.10, 32bit and 64bit. It only install Writer only, and Presentation and Spreadsheet fail to install.
Could someone advise how to resolve? Thanks.

---

### Post by yahyablora on 2013-03-30
Thanks dude..

---

### Post by Tres99 on 2013-03-30
Sorry forget it.
I've realized the Presentation and Spreadsheet were already installed, the problem is these two application do not appear in Ubuntu lense after installation.
They appears after typing Sp and Pre...:sad::sad:

---

### Post by PANGERAN on 2013-04-02
Before you install, it better you uninstall previous WPS :)

---

### Post by BigCityCat on 2013-04-02
Is this freeware or shareware? Is this a free trial that expires? Do you need a key for this if when it expires?

[http://en.wikipedia.org/wiki/Kingsoft_Office](http://en.wikipedia.org/wiki/Kingsoft_Office)

> In 2007, another edition was released, Kingsoft Office 2007, which is available in Chinese, English, and Japanese interface. The personal edition is available for 30-day trial (with the license key available for free by request), the next version will be available in 100-day trial and free version.

---

### Post by ghoracek on 2013-04-04
> **haaglin said:**
> Extract zip [ATTACH]240635[/ATTACH] to ~/.fonts

I've got the fonts downloaded and I understand I have to extract them.  Done that.  Where do I put them?  I'm sorry ~/.fonts is meaningless to me.  This must be a hidden fonts directory, but where is it?  I know how to unhide directories, but I still can't find one named .fonts.  

glh

---

### Post by maya4u on 2013-04-05
Thanks. That worked. Still there are portions that are in chinese(eg. function list). Looks like a replica of MS-O.
- the Maya

---

### Post by cloyd on 2013-04-06
I've followed all the instructions and still get a little Chinese on page. I know what is supposed to go there, so it doesn't seem to be a big deal. Now, why would I want to change from Libre Office? My android tabled has WPS, and it would be nice to use the same app on computer and android (I know it will never be exactly the same). The second reason is that a superficial glance at the UI seems to be very logical. It seems to me that Libre Office (and Open Office) stuck some things in some strange places. I'd like to try this and see if it works for me. I am intrigued, but not ready to make a full switch.

---

### Post by PieterJ6 on 2013-04-07
> **ghoracek said:**
> I've got the fonts downloaded and I understand I have to extract them.  Done that.  Where do I put them?  I'm sorry ~/.fonts is meaningless to me.  This must be a hidden fonts directory, but where is it?  I know how to unhide directories, but I still can't find one named .fonts.  

glh

@ghoracek, the '~/' (wave) refers to your home directory and the '.' (dot) show that it is a hidden directory (like you said). So ~/.fonts will refer to the hidden fonts directory in your home directory. But I couldn't find a .fonts in my home directory, so I just created one and pasted them there - this worked. Hope this will help you.

---

### Post by cvnmjs on 2013-04-07
Thanks! wish there was an amd64 build.

---

### Post by jonask on 2013-04-09
How do you uninstall it?

---

### Post by mamamia88 on 2013-04-09
> **jonask said:**
> How do you uninstall it?

Didn't try it but guessing search for the name of the package in synaptic with the same name of the deb file.

---

### Post by rs99cool on 2013-04-10
I'm getting these error messages in terminal, but it might be because I just remembered that I tried your solution a few weeks ago to get WPS into English and these messages might be because the fix has already been done.

rm: cannot remove `qt.qm': No such file or directory
rm: cannot remove `wps.qm': No such file or directory
rm: cannot remove `wpp.qm': No such file or directory
rm: cannot remove `et.qm': No such file or directory

So, here's my problem ... yes, instead of everything being in Chinese, it's a LOT better.  Thanks!  But about half of the program is in Chinese and half in English.  For example, the fonts are in Chinese unless you mouse over the font selection box and then most of them are in English.  It's like that all over. It would really be nice if everything was in English, like it appears to be in the Windows version.  Is there a later Linux download than this one? wps-office_8.1.0.3724~b1p2_i386.deb

---

### Post by ianni67 on 2013-04-11
Did anyone test macros compatibility? 
What about presentations?

thank you very much for any information
ianni67

---

### Post by rs99cool on 2013-04-12
You have been extremely helpful, thanks very much!  I would love to try using WPS Office, and I've used the change to get it into English, but now instead of everything being in Chinese, about half of the program is in Chinese and half in English. For example, the fonts are in Chinese unless you mouse over the font selection box and then most of them are in English. It's like that all over. The same problem with the other apps.  This is from the top left corner of the Writer screen.  

  [IMG]https://mail.google.com/mail/?ui=2&ik=21bf9c5206&view=att&th=13dfe0b90e380644&attid=0.1&disp=emb&realattid=ii_13dfe0b46f52d7e3&zw&atsh=1[/IMG]

It would really be nice if everything was in English, like it appears to be in the Windows version. Is there a later Linux download than this one? wps-office_8.1.0.3724~b1p2_i386.deb

---

### Post by Jinchuan Tang on 2013-04-19
It's free for personal windows version in China since 2010(or maybe earlier?) but not free for enterprise. 

Like its android app, they offered the app called Kingsoft office with good quality and free of charge, no key or expire date required for linux one right now.

They are going to offer the alpha 10 version(now is a9) with default English support in the future.

The link is :[http://bbs.wps.cn/thread-22368421-1-1.html](http://bbs.wps.cn/thread-22368421-1-1.html)

---

### Post by alokmahor on 2013-04-22
what are these .qm files?

---

### Post by leopoldbirkholm on 2013-04-28
Thank you. It works fine now.

---

### Post by Masateru KUWATA on 2013-05-07
Dear Sir,

I was trying to access to the web site of [http://community.wps.cn/download/](http://community.wps.cn/download/), but it looks like no longer available??

Can you please advise where to find the latest link?

Regards

---

### Post by alokmahor on 2013-05-07
you can download from the link given in [http://www.omgubuntu.co.uk/2013/03/wps-office-for-linux-looks-like-microsoft-office-but-isnt](http://www.omgubuntu.co.uk/2013/03/wps-office-for-linux-looks-like-microsoft-office-but-isnt)

---

### Post by Masateru KUWATA on 2013-05-08
> **alokmahor said:**
> you can download from the link given in [http://www.omgubuntu.co.uk/2013/03/wps-office-for-linux-looks-like-microsoft-office-but-isnt](http://www.omgubuntu.co.uk/2013/03/wps-office-for-linux-looks-like-microsoft-office-but-isnt)

Hi, I tried to download from that link, but it was timed out.
Any idea to solve this problem?

Rgds:confused:

---

### Post by Masateru KUWATA on 2013-05-08
> **alokmahor said:**
> you can download from the link given in [http://www.omgubuntu.co.uk/2013/03/wps-office-for-linux-looks-like-microsoft-office-but-isnt](http://www.omgubuntu.co.uk/2013/03/wps-office-for-linux-looks-like-microsoft-office-but-isnt)

Dear Sir, 

I tried to download from the above link, but it was still timed out.
Then I set up the vpn using Tunnelbear and tried again, now it works although it is slow.

Thanks for your support.

Regards

---

### Post by chrisinleedsuk on 2013-05-14
Looks good, very good compatibility with MS files and more stylish than Libre et al. Has anyone got an equation editor working with it yet?

---

### Post by lin73 on 2013-05-23
Actually, it is quite good, but spreadsheet is more or less useless without the charts, pivot tables and macros. They're all disabled.

---

### Post by Enkouyami on 2013-09-12
Here's a much faster link: [**[www.iloveubuntu.com/files/wps-office_8.1.0.3724~b1p2_i386.deb](www.iloveubuntu.com/files/wps-office_8.1.0.3724~b1p2_i386.deb)**]("http://www.iloveubuntu.com/files/wps-office_8.1.0.3724~b1p2_i386.deb")

---

### Post by marc_cowen on 2013-10-08
> **haaglin said:**
> Extract zip [ATTACH]240635[/ATTACH] to ~/.fonts

Thanks a lot bro. sorted mine out doing it this way :)

---

### Post by Hadi_G on 2014-06-26
Anyway, right now Kingsoft Office for linux (WPS) has fully english language supported, you can download from [here]("http://wps-community.org/download.html")

---

